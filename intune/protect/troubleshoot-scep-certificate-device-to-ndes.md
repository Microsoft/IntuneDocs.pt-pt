---
title: Problemas geridos dispositivo para comunicação NDES em Microsoft Intune / Microsoft Docs
description: O dispositivo de resolução de problemas geriu o dispositivo para a comunicação do servidor NDES ao utilizar perfis de certificadoS SCEP para implementar certificados com o Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/30/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8c81fa9b521b0d950fb69c29f7625981e709863d
ms.sourcegitcommit: c46b0c2d4507be6a2786a4ea06009b2d5aafef85
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/01/2020
ms.locfileid: "76913269"
---
# <a name="troubleshoot-device-to-ndes-server-communication-for-scep-certificate-profiles-in-microsoft-intune"></a>Dispositivo de resolução de problemas para comunicação do servidor NDES para perfis de certificadoS SCEP no Microsoft Intune

Utilize as seguintes informações para determinar se um dispositivo que recebeu e processou um perfil de certificado de protocolo de inscrição de certificado simples intune (SCEP) pode contactar com sucesso o Serviço de Inscrição de Dispositivos de Rede (NDES) para apresentar um desafio. No dispositivo, é gerada uma chave privada e o Pedido de Assinatura de Certificado (CSR) e o desafio são transmitidos do dispositivo para o servidor NDES. Para contactar o servidor NDES, o dispositivo utiliza o URI a partir do perfil do certificado SCEP.

Este artigo refere-se à parte 2 da visão geral do fluxo de [comunicação scep](troubleshoot-scep-certificate-profiles.md).

## <a name="review-iis-logs-for-a-connection-from-the-device"></a>Reveja os registos IIS para uma ligação do dispositivo

Os registos IIS incluem o mesmo tipo de entradas para todas as plataformas.


1. No servidor NDES, abra o ficheiro de registo IIS mais recente encontrado na seguinte pasta: *%SystemDrive%\inetpub\logs\logfiles\w3svc1*

2. Procure no registo entradas semelhantes aos seguintes exemplos. Ambos os exemplos contêm um estado **200,** que aparece perto do fim:

   `fe80::f53d:89b8:c3e8:5fec%13 GET /certsrv/mscep/mscep.dll/pkiclient.exe operation=GetCACaps&message=default 80 - fe80::f53d:89b8:c3e8:5fec%13 Mozilla/4.0+(compatible;+Win32;+NDES+client) - 200 0 0 186 0.`

   E

   `fe80::f53d:89b8:c3e8:5fec%13 GET /certsrv/mscep/mscep.dll/pkiclient.exe operation=GetCACert&message=default 80 - fe80::f53d:89b8:c3e8:5fec%13 Mozilla/4.0+(compatible;+Win32;+NDES+client) - 200 0 0 3567 0`

3. Quando o dispositivo entra em contacto com o IIS, é registado um pedido http GET para mscep.dll.

   Reveja o código de estado perto do final deste pedido:
   - **Código de estado de 200**: Este estado indica que a ligação com o servidor NDES é bem sucedida.
   - **Código de estado de 500:** O grupo IIS_IURS pode não ter permissões corretas. Consulte o [Código de Estado 500,](#status-code-500)mais tarde neste artigo.
   - Se o código de estado não for de 200 ou 500:

     - Consulte [o Teste do URL do servidor SCEP](#test-the-scep-server-url) mais tarde neste artigo para ajudar a validar a configuração.

     - Consulte o código de [estado HTTP no IIS 7 e versões posteriores](https://support.microsoft.com/help/943891) para obter informações sobre códigos de erro menos comuns.

   Se o pedido de ligação não estiver registado, o contacto do dispositivo poderá estar bloqueado na rede entre o dispositivo e o servidor NDES.

## <a name="review-device-logs-for-connections-to-ndes"></a>Reveja os registos do dispositivo para ligações ao NDES

### <a name="android-devices"></a>Dispositivos Android

Reveja o [registo OMADM](troubleshoot-scep-certificate-profiles.md#logs-for-android-devices)dos dispositivos . Procure entradas que se assemelhem às seguintes, que são registadas quando o dispositivo se liga ao NDES:

```
2018-02-27T05:16:08.2500000  VERB  Event  com.microsoft.omadm.platforms.android.certmgr.CertificateEnrollmentManager  18327    10  There are 1 requests
2018-02-27T05:16:08.2500000  VERB  Event  com.microsoft.omadm.platforms.android.certmgr.CertificateEnrollmentManager  18327    10  Trying to enroll certificate request: ModelName=AC_51bad41f-3854-4eb5-a2f2-0f7a94034ee8%2FLogicalName_39907e78_e61b_4730_b9fa_d44a53e4111c;Hash=1677525787
2018-02-27T05:16:09.5530000  VERB  Event  org.jscep.transport.UrlConnectionGetTransport  18327    10  Sending GetCACaps(ca) to https://<server>.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACaps&message=ca
2018-02-27T05:16:14.6440000  VERB  Event  org.jscep.transport.UrlConnectionGetTransport  18327    10  Received '200 OK' when sending GetCACaps(ca) to https://<server>.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACaps&message=ca
2018-02-27T05:16:21.8220000  VERB  Event  org.jscep.message.PkiMessageEncoder  18327     10 Encoding message: org.jscep.message.PkcsReq@2b06f45f[messageData=org.<server>.pkcs.PKCS10CertificationRequest@699b3cd,messageType=PKCS_REQ,senderNonce=Nonce [D447AE9955E624A56A09D64E2B3AE76E],transId=251E592A777C82996C7CF96F3AAADCF996FC31FF]
2018-02-27T05:16:21.8790000  VERB  Event  org.jscep.message.PkiMessageEncoder  18327     10  Signing pkiMessage using key belonging to [dn=CN=<uesrname>; serial=1]
2018-02-27T05:16:21.9580000  VERB  Event  org.jscep.transaction.EnrollmentTransaction  18327     10  Sending org.<server>.cms.CMSSignedData@ad57775
```

As entradas-chave incluem as seguintes cadeias de texto da amostra:

- Há 1 pedidos
- Recebido '200 OK' ao enviar GetCACaps(ca) para https://\<servidor>.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACaps&message=ca
- Assinar pkiMessage utilizando a chave pertencente a [dn=CN=\<username>; serial=1]


A ligação também é registada pelo IIS na pasta %SystemDrive%\inetpub\logs\LogFiles\W3SVC1\ do servidor NDES. Exemplo:

```
fe80::f53d:89b8:c3e8:5fec%13 GET /certsrv/mscep/mscep.dll operation=GetCACert&message=ca 443 - 
fe80::f53d:89b8:c3e8:5fec%13 Dalvik/2.1.0+(Linux;+U;+Android+5.0;+P01M+Build/LRX21V) - 200 0 0 3909 0
fe80::f53d:89b8:c3e8:5fec%13 GET /certsrv/mscep/mscep.dll operation=GetCACaps&message=ca 443 - 
fe80::f53d:89b8:c3e8:5fec%13 Dalvik/2.1.0+(Linux;+U;+Android+5.0;+P01M+Build/LRX21V) - 200 0 0 421 
```

### <a name="ios-and-ipados-devices"></a>dispositivos iOS e iPadOS

Reveja o [registo de depuração](troubleshoot-scep-certificate-profiles.md#logs-for-ios-and-ipados-devices)dos dispositivos . Procure entradas que se assemelhem às seguintes, que são registadas quando o dispositivo se liga ao NDES:

```
debug    18:30:53.691033 -0500    profiled    Performing synchronous URL request: https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACert&message=SCEP%20Authority\ 
debug    18:30:54.640644 -0500    profiled    Performing synchronous URL request: https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACaps&message=SCEP%20Authority\ 
default    18:30:55.483977 -0500    profiled    Attempting to retrieve issued certificate...\ 
debug    18:30:55.487798 -0500    profiled    Sending CSR via GET.\  
debug    18:30:55.487908 -0500    profiled    Performing synchronous URL request: https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=PKIOperation&message=MIAGCSqGSIb3DQEHAqCAMIACAQExDzANBglghkgBZQMEAgMFADCABgkqhkiG9w0BBwGggCSABIIZfzCABgkqhkiG9w0BBwOggDCAAgEAMYIBgjCCAX4CAQAwZjBPMRUwEwYKCZImiZPyLGQBGRYFbG9jYWwxHDAaBgoJkiaJk/IsZAEZFgxmb3VydGhjb2ZmZWUxGDAWBgNVBAMTD0ZvdXJ0aENvZmZlZSBDQQITaAAAAAmaneVjEPlcTwAAAAAACTANBgkqhkiG9w0BAQEFAASCAQCqfsOYpuBToerQLkw/tl4tH9E+97TBTjGQN9NCjSgb78fF6edY0pNDU+PH4RB356wv3rfZi5IiNrVu5Od4k6uK4w0582ZM2n8NJFRY7KWSNHsmTIWlo/Vcr4laAtq5rw+CygaYcefptcaamkjdLj07e/Uk4KsetGo7ztPVjSEFwfRIfKv474dLDmPqp0ZwEWRQGZwmPoqFMbX3g85CJT8khPaqFW05yGDTPSX9YpuEE0Bmtht9EwOpOZe6O7sd77IhfFZVmHmwy5mIYN7K6mpx/4Cb5zcNmY3wmTBlKEkDQpZDRf5PpVQ3bmQ3we9XxeK1S4UsAXHVdYGD+bg/bCafMIAGCSqGSIb3DQEHATAUBggqhkiG9w0DBwQI5D5J2lwZS5OggASCF6jSG9iZA/EJ93fEvZYLV0v7GVo3JAsR11O7DlmkIqvkAg5iC6DQvXO1j88T/MS3wV+rqUbEhktr8Xyf4sAAPI4M6HMfVENCJTStJw1PzaGwUJHEasq39793nw4k268UV5XHXvzZoF3Os2OxUHSfHECOj
```

As entradas-chave incluem as seguintes cadeias de texto da amostra:

- operação=GetCACert
- Tentativa de recuperar certificado emitido
- Envio de CSR via GET
- operação=PKIOperation

### <a name="windows-devices"></a>Dispositivos Windows

Num dispositivo Windows que está a fazer uma ligação ao NDES, pode ver os dispositivos Windows Event Viewer e procurar indicações de uma ligação bem sucedida. As ligações são registadas como um evento ID **36** nos dispositivos *DispositivoS Gestão-Empresa-Diagnóstico-Fornecer* > registo **de administração.**

Para abrir o tronco:

1. No dispositivo, execute **eventvwr.msc** para abrir o Windows Event Viewer.

2. Expandir registos de **aplicações e serviços** > **Microsoft** > **Windows** > **DeviceManagement-Enterprise-Diagnostic-Provider** > **Admin**.

3. Procure o Evento **36**, que se assemelha ao seguinte exemplo, com a linha-chave do **SCEP: Pedido**de certificado gerado com sucesso:

   ```
   Event ID:      36
   Task Category: None
   Level:         Information
   Keywords:
   User:          <UserSid>
   Computer:      <Computer Name>
   Description:
   SCEP: Certificate request generated successfully. Enhanced Key Usage: (1.3.6.1.5.5.7.3.2), NDES URL: (https://<server>/certsrv/mscep/mscep.dll/pkiclient.exe), Container Name: (), KSP Setting: (0x2), Store Location: (0x1).
   ```

## <a name="troubleshoot-common-errors"></a>Erros comuns de resolução de problemas

As seguintes secções podem ajudar com problemas comuns de ligação de todas as plataformas do dispositivo para NDES.

### <a name="status-code-500"></a>Código de estado 500

As ligações que se assemelham ao seguinte exemplo, com um código de estado de 500, indicam que o *Personificar um cliente após* o direito do utilizador de autenticação não é atribuído ao grupo IIS_IURS no servidor NDES. O valor de estado de **500** aparece no final:

```
2017-08-08 20:22:16 IP_address GET /certsrv/mscep/mscep.dll operation=GetCACert&message=SCEP%20Authority 443 - 10.5.14.22 profiled/1.0+CFNetwork/811.5.4+Darwin/16.6.0 - 500 0 1346 31
```

**Para corrigir esta questão:**

1. No servidor NDES, execute **secpol.msc** para abrir a Política de Segurança Local.

2. Expandir **as Políticas Locais**e, em seguida, clicar em **Atribuição de Direitos de Utilizador**.

3. Clique duas vezes **em Personificar um cliente após a autenticação** no painel certo.

4. Clique em **Adicionar Utilizador ou Grupo...** **introduza IIS_IURS** os nomes do objeto para selecionar a **caixa**e, em seguida, clique em **OK**.

5. Clique em **OK**.

6. Reiniciar o computador e, em seguida, tentar a ligação do dispositivo novamente.

### <a name="test-the-scep-server-url"></a>Teste o URL do servidor SCEP

Utilize os seguintes passos para testar o URL especificado no perfil do certificado SCEP.

1. Em Intune, edite o seu perfil de certificado SCEP e copie o URL do Servidor. O URL deve assemelhar-se *a https://contoso.com/certsrv/mscep/msecp.dll* .

2. Abra um navegador web e, em seguida, navegue para o URL do servidor SCEP. O resultado deve ser: **HTTP Error 403.0 – Proibido**. Este resultado indica que o URL está a funcionar corretamente.

   Se não receber esse erro, selecione o link que se assemelha ao erro que vê para ver orientação específica para o problema:
   - [Recebo uma mensagem geral do Serviço de Inscrição de Dispositivos de Rede](#general-ndes-message)
   - [Recebo "HTTP Error 503. O serviço não está disponível"](#http-error-503)
   - [Recebo o erro "GatewayTimeout"](#gatewaytimeout)
   - [Recebo "HTTP 414 Request-URI Too Long"](#http-414-request-uri-too-long)
   - [Eu recebo "Esta página não pode ser exibida"](#this-page-cant-be-displayed)
   - [Recebo "500 - Erro interno do servidor"](#internal-server-error)

#### <a name="general-ndes-message"></a>Mensagem Geral NDES

Quando navega no URL do servidor SCEP, recebe a seguinte mensagem do Serviço de Inscrição de Dispositivos de Rede:

![URL do servidor do SCEP](../protect/media/troubleshoot-scep-certificate-device-to-ndes/ndes-server-url-message.png)

- **Causa**: Este problema é geralmente um problema com a instalação do Conector Intune da Microsoft.

  Mscep.dll é uma extensão ISAPI que interceta o pedido de entrada e exibe o erro HTTP 403 se estiver instalado corretamente.
  
  **Resolução**: Examine o ficheiro *SetupMsi.log* para determinar se o Microsoft Intune Connector está instalado com sucesso. No exemplo seguinte, *a Instalação concluída com sucesso* e o estado de erro de *instalação: 0* indicar uma instalação bem sucedida:

  ```
  MSI (c) (28:54) [16:13:11:905]: Product: Microsoft Intune Connector -- Installation completed successfully.
  MSI (c) (28:54) [16:13:11:999]: Windows Installer installed the product. Product Name: Microsoft Intune Connector. Product Version: 6.1711.4.0. Product Language: 1033. Manufacturer: Microsoft Corporation. Installation success or error status: 0.
  ```

  Se a instalação falhar, retire o Conector Intune da Microsoft e, em seguida, reinstale-o.

#### <a name="http-error-503"></a>Erro HTTP 503

Quando navega no URL do servidor SCEP, recebe o seguinte erro:

![Erro HTTP 503. O serviço não está disponível](../protect/media/troubleshoot-scep-certificate-device-to-ndes/service-unavailable.png)

Esta questão é geralmente porque o conjunto de aplicações **SCEP** no IIS não está iniciado. No servidor NDES, abra o **IIS Manager** e vá para **Application Pools**. Localize a piscina de aplicações **SCEP** e confirme que começou.

Se o conjunto de aplicações SCEP não estiver iniciado, verifique o registo do evento de aplicação no servidor:

1. No dispositivo, execute **eventvwr.msc** para abrir **o Espectador de Eventos** e ir ao **Windows Logs** > **Application**.

2. Procure um evento semelhante ao seguinte exemplo, o que significa que o pool de aplicações se despenha quando um pedido é recebido:

   ```
   Log Name:      Application
   Source:        Application Error
   Event ID:      1000
   Task Category: Application Crashing Events
   Level:         Error
   Keywords:      Classic
   Description: Faulting application name: w3wp.exe, version: 8.5.9600.16384, time stamp: 0x5215df96
   Faulting module name: ntdll.dll, version: 6.3.9600.18821, time stamp: 0x59ba86db
   Exception code: 0xc0000005
   ```

**Causas comuns para um acidente com piscina de aplicações:**

- **Causa 1:** Existem certificados ca intermédios (não auto-assinados) na loja de certificados trust Root Certification Authorities do servidor NDES.

  **Resolução**: Retire os certificados intermédios do certificado trust Root Certification Authorities e, em seguida, reinicie o servidor NDES.
  
  Para identificar todos os certificados intermédios na loja de certificados Trusted Root Certification Authorities, execute o seguinte cmdlet PowerShell: `Get-Childitem -Path cert:\LocalMachine\root -Recurse | Where-Object {$_.Issuer -ne $_.Subject}`

  Um certificado que tenha o mesmo **Emitido** e **Emitido por** valores, é um certificado de raiz. Caso contrário, é um certificado intermédio.

  Depois de remover os certificados e reiniciar o servidor, volte a executar o cmdlet PowerShell para confirmar que não existem certificados intermédios. Se houver, verifique se uma Política de Grupo empurra os certificados intermédios para o servidor NDES. Em caso afirmativo, exclua o servidor NDES da Política de Grupo e remova novamente os certificados intermédios.

- **Causa 2**: Os URLs na Lista de Revogação do Certificado (CRL) estão bloqueados ou inacessíveis para os certificados utilizados pelo Conector de Certificado Intune.

  **Resolução**: Permitir que o registo extrairindo adicional recolha mais informações:
  1. Abra o Espectador de Eventos, clique em **Visualizar,** certifique-se de que a opção **Debug Logs é** verificada.
  2. Aceda a Registos de **Aplicações e Serviços** > **Microsoft** > **o Windows** > **O CAPI2** > **Operacional,** clique no clique direito **Operacional,** em seguida, clique em **Ativar O Log**.
  3. Após a ativação da exploração madeireira CAPI2, reproduza o problema e examine o registo do evento para resolver o problema.

- **Causa 3**: A permissão IIS no **CertificateRegistrationSvc** tem **a autenticação** do Windows ativada.

  **Resolução**: Ativar a **autenticação anónima** e desativar a **autenticação do Windows**e, em seguida, reiniciar o servidor NDES.

  ![Permissões IIS](../protect/media/troubleshoot-scep-certificate-device-to-ndes/iis-permissions.png)

#### <a name="gatewaytimeout"></a>GatewayTimeout

Quando navega no URL do servidor SCEP, recebe o seguinte erro:

![Erro de saída de gateway](../protect/media/troubleshoot-scep-certificate-device-to-ndes/gateway-timeout.png)

- **Causa**: O serviço de **conector proxy de aplicação da Microsoft AAD** não foi iniciado.

  **Resolução**: Executar **serviços.msc,** e, em seguida, certifique-se de que o serviço de **conector proxy de aplicação da Microsoft AAD** está em execução e **o Tipo de Arranque** está definido para **Automático**.

#### <a name="http-414-request-uri-too-long"></a>HTTP 414 Request-URI Demasiado Tempo

Quando navega no URL do servidor SCEP, recebe o seguinte erro: `HTTP 414 Request-URI Too Long`

- **Causa**: A filtragem do pedido IIS não está configurada para suportar os URLs longos (consultas) que o serviço NDES recebe. Este suporte é configurado quando [configura o serviço NDES](certificates-scep-configure.md#configure-the-ndes-service) para utilização com a sua infraestrutura para SCEP.

- **Resolução**: Configure o suporte para URLs longos.

  1. No servidor NDES, abra o gestor IIS, selecione **o Web Site padrão** > solicitar **filtragem** > definição de funcionalidade de **edição** para abrir a página de Definições de Filtragem de Pedidos de **Edição.**

  2. Configure as seguintes definições:
     - **Comprimento máximo de URL (Bytes)** = 65534
     - **Corda de consulta máxima (Bytes)** = 65534

  3. Selecione **OK** para guardar esta configuração e fechar o gestor IIS.

  4. Valide esta configuração localizando a seguinte chave de registo para confirmar que tem os valores indicados:

     HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\HTTP\Parameters

     Os seguintes valores são definidos como entradas dWORD:
     - Nome: **MaxFieldLength**, com um valor decimal de **65534**
     - Nome: **MaxRequestBytes**, com um valor decimal de **65534**

  5. Reiniciar o servidor NDES.

#### <a name="this-page-cant-be-displayed"></a>Esta página não pode ser exibida

Tem o Proxy de Aplicação AD Azure configurado. Quando navega no URL do servidor SCEP, recebe o seguinte erro:

`This page can't be displayed`

- **Causa**: Este problema ocorre quando o URL externo do SCEP está incorreto na configuração do Proxy de Aplicação. Um exemplo deste URL é https://contoso.com/certsrv/mscep/mscep.dll.

  **Resolução**: Utilize o domínio predefinido de *yourtenant.msappproxy.net* para o URL externo scep na configuração proxy de aplicação.

#### <a name="internal-server-error"></a>500 - Erro interno do servidor

Quando navega no URL do servidor SCEP, recebe o seguinte erro:

![500 - Erro interno do servidor](../protect/media/troubleshoot-scep-certificate-device-to-ndes/500-internal-server-error.png)

- **Causa 1**: A conta de serviço NDES está bloqueada ou a sua palavra-passe expira.

  **Resolução**: Desbloquear a conta ou redefinir a palavra-passe.

- **Causa 2**: Os certificados MSCEP-RA caducam.

  **Resolução**: Se os certificados MSCEP-RA estiverem caducados, reinstale a função NDES ou solicite novos certificados de Encriptação cep e agente de inscrição de intercâmbio (pedido offline).

  Para solicitar novos certificados, siga estas etapas:

  1. Na Autoridade de Certificados (CA) ou na emissão de CA, abra os modelos de certificado MMC. Certifique-se de que o registo registado no utilizador e o servidor NDES têm permissões **de leitura** e **inscrição** para os modelos de certificados do Agente de Encriptação e Deposição (Pedido Offline) da CEP.

  2. Verifique os certificados expirados no servidor NDES, copie as informações do **Assunto** a partir do certificado.

  3. Abra os Certificados MMC para **a conta de computador.**

  4. Expandir **Certificados** **Pessoais,** cliques à direita e, em seguida, selecione **todas as tarefas** > **solicitar novo certificado**.

  5. Na página **do Certificado de Pedido,** selecione **Encriptação CEP,** clique em **Mais informações são necessárias para se inscrever para este certificado. Clique aqui para configurar as definições**.

     ![Selecione encriptação CEP](../protect/media/troubleshoot-scep-certificate-device-to-ndes/select-scep-encryption.png)

  6. No **Certificado Propriedades,** clique no separador **Assunto,** encha o **nome Assunto** com a informação que recolheu durante o passo 2, clique em **Adicionar,** em seguida, clique EM **OK**.

  7. Complete a inscrição do certificado.

  8. Abra os Certificados MMC para **a minha conta de utilizador.**

     Quando se inscreve para o certificado de agente de inscrição cambial (pedido offline), deve ser feito no contexto do utilizador. Porque o tipo de **assunto** deste modelo de certificado está definido para **o Utilizador**.

  9. Expandir **Certificados** **Pessoais,** cliques à direita e, em seguida, selecione **todas as tarefas** > **solicitar novo certificado**.

  10. Na página do **Certificado de Pedido,** selecione **Exchange Registration Agent (pedido offline)** e, em seguida, clique **Em Mais informações são necessárias para se inscrever para este certificado. Clique aqui para configurar as definições**.

      ![Selecione Agente de Inscrição de Intercâmbio](../protect/media/troubleshoot-scep-certificate-device-to-ndes/select-exchange-enrollment-agent.png)

  11. Nas **Propriedades do Certificado,** clique no separador **Assunto,** preencha o **nome Assunto** com a informação que recolheu durante o passo 2, clique em **Adicionar**.

      ![Propriedades de certificado](../protect/media/troubleshoot-scep-certificate-device-to-ndes/certificate-properties.png)

      Selecione o separador **Chave Privada,** selecione **Tornar a chave privada exportável**e, em seguida, clique **EM OK**.

      ![Chave privada](../protect/media/troubleshoot-scep-certificate-device-to-ndes/private-key.png)

  12. Complete a inscrição do certificado.

  13. Exportar o certificado do Agente de Inscrição cambial (pedido offline) da atual loja de certificados de utilizador. No Certificado De Saúde Exportadorde Certificado, selecione **Sim, exporte a chave privada**.

  14. Importar o certificado para a loja de certificados de máquinalocal.

  15. Nos certificados MMC, faça as seguintes ações para cada um dos novos certificados:

      Clique no certificado à direita, clique em **Todas as Tarefas** > **Gerir Chaves Privadas,** adicione a permissão **de leitura** na conta de serviço NDES.

  16. Executar o comando **iisreset** para reiniciar o IIS.

## <a name="next-steps"></a>Próximos passos

Se o dispositivo chegar com sucesso ao servidor NDES para apresentar o pedido de certificado, o próximo passo é rever o módulo de [política de Conectores de Certificado Intune](troubleshoot-scep-certificate-ndes-policy-module.md).
