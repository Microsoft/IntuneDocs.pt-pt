---
title: Emitir certificados DigiCert PKCS com microsoft Intune
titleSuffix: Microsoft Intune
description: Instale e configure o Conector de Certificado Intune para emitir certificados PKCS da Plataforma DigiCert PKI para dispositivos geridos por Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/07/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: ca76ffe0c8fa42f1c2cf24fcdefd287140231220
ms.sourcegitcommit: 25e4847ead0f56c269cfefe1e01c1b9106a28cf1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/05/2020
ms.locfileid: "78370084"
---
# <a name="set-up-intune-certificate-connector-for-digicert-pki-platform"></a>Configurar conector de certificado intune para a plataforma DigiCert PKI

Utilize o Conector de Certificado Intune para emitir certificados PKCS da Plataforma DigiCert PKI para dispositivos geridos por Intune. Pode utilizar o conector apenas com uma autoridade de certificação DigiCert (CA), ou com um DigiCert CA e um Microsoft CA.

> [!TIP]
> A DigiCert adquiriu o website Security da Symantec e o negócio relacionado com a PKI Solutions. Para mais informações sobre esta alteração, consulte o [artigo de suporte técnico da Symantec.](https://support.symantec.com/en_US/article.INFO4722.html)

Se já utilizar o Conector de Certificado Intune para emitir certificados a partir de um Ca da Microsoft utilizando o PKCS ou o System Center Endpoint Protection, pode utilizar esse mesmo conector para configurar e emitir certificados PKCS a partir de um DigiCert CA. Depois de completar a configuração para suportar o DigiCert CA, o Conector de Certificado Intune pode emitir os seguintes certificados:

* Certificados PKCS de um Microsoft CA
* Certificados PKCS de um DigiCert CA
* Certificados de proteção de pontofinal de um Ca microsoft

Se não tiver o conector instalado, mas planeie utilizá-lo tanto para um Microsoft CA como para um DigiCert CA, complete primeiro a configuração do conector para o Microsoft CA. Em seguida, volte a este artigo para configurá-lo também para apoiar DigiCert. Para obter mais informações sobre os perfis de certificado e o conector, consulte configurar um perfil de [certificado para os seus dispositivos no Microsoft Intune](certificates-configure.md).  

Se utilizar o conector apenas com o DigiCert CA, pode utilizar as instruções deste artigo para instalar e, em seguida, configurar o conector.

## <a name="prerequisites"></a>Pré-requisitos

- **Uma subscrição ativa no DigiCert CA**: A subscrição é necessária para obter um certificado de autoridade de registo (RA) do DigiCert CA.

## <a name="install-the-digicert-ra-certificate"></a>Instale o certificado DigiCert RA

1. Guarde o seguinte código snippet como num ficheiro chamado **certreq.ini** e atualize-o conforme necessário (por exemplo: *Nome do assunto no formato NC*).

        [Version] 
        Signature="$Windows NT$" 
        
        [NewRequest] 
        ;Change to your,country code, company name and common name 
        Subject = "Subject Name in CN format"
        
        KeySpec = 1 
        KeyLength = 2048 
        Exportable = TRUE 
        MachineKeySet = TRUE 
        SMIME = False 
        PrivateKeyArchive = FALSE 
        UserProtected = FALSE 
        UseExistingKeySet = FALSE 
        ProviderName = "Microsoft RSA SChannel Cryptographic Provider" 
        ProviderType = 12 
        RequestType = PKCS10 
        KeyUsage = 0xa0 
        
        [EnhancedKeyUsageExtension] 
        OID=1.3.6.1.5.5.7.3.2 ; Client Authentication  // Uncomment if you need a mutual TLS authentication
        
        ;----------------------------------------------- 

2. Abra um pedido de comando elevado e gere um pedido de assinatura de certificado (RSE) utilizando o seguinte comando:

   `Certreq.exe -new certreq.ini request.csr`

3. Abra o ficheiro request.cSR no Bloco de Notas e copie o conteúdo cSR que se insere no seguinte formato:

        -----BEGIN NEW CERTIFICATE REQUEST-----
        MIID8TCCAtkCAQAwbTEMMAoGA1UEBhMDVVNBMQswCQYDVQQIDAJXQTEQMA4GA1UE
        …
        …
        fzpeAWo=
        -----END NEW CERTIFICATE REQUEST-----


4. Inscreva-se na DigiCert CA e navegue para **obter um RA Cert** das tarefas.

   a. Na caixa de texto, forneça o conteúdo da RSE a partir do passo 3.

   b. Forneça um nome amigável para o certificado.

   c. Selecione **Continuar**.

   d. Utilize o link fornecido para transferir o certificado RA para o seu computador local.

5. Importar o certificado RA para a loja de certificados Windows:

   a. Abra uma consola MMC.

   b. Selecione **File** > **Adicionar ou remover snap-ins** > **Certificado** > **Adicionar**.

   c. Selecione **conta de computador** > **Seguinte**.

   d. Selecione **Local Computer** > **Finish**.

   e. Selecione **OK** na janela **Adicionar ou Remover snap-ins.** Expandir **Certificados (Computador Local)**  > **Certificados**de > **Pessoais** .

   f. Clique com o botão direito do rato no nó **Certificados** e selecione **Todas as Tarefas** > **Importar**.

   g. Selecione a localização do certificado RA que descarregou a partir do DigiCert CA e, em seguida, selecione **Next**.

   h. Selecione **Loja de Certificados Pessoais** > **Seguinte**.

   i. Selecione **Finish** para importar o certificado RA e a sua chave privada para a loja **Local Machine-Personal.**

6. Exporte e importe o certificado de chave privada:

   a. Expanda **Certificados (Computador Local)**  > **Pessoal** > **Certificados**.

   b. Selecione o certificado importado no passo anterior.

   c. Clique no certificado e selecione **Todas as tarefas** > **Exportação**.

   d. Selecione **Em seguida,** e introduza a palavra-passe.

   e. Selecione a localização para exportar e, em seguida, selecione **Terminar**.

   f. Utilize o procedimento desde o passo 5 para importar o certificado de chave privada para a loja **Local Computer-Personal.**

   g. Grave uma cópia da impressão digital do certificado RA sem espaços. Segue-se um exemplo da impressão digital:

        RA Cert Thumbprint: “EA7A4E0CD1A4F81CF0740527C31A57F6020C17C5”

    > [!NOTE]
    > Para obter o certificado RA da DigiCert CA, contacte o [apoio ao cliente da DigiCert.](mailto:enterprise-pkisupport@digicert.com)

## <a name="prepare-to-install-intune-certificate-connector"></a>Preparar-se para instalar o Intune Certificate Connector

> [!TIP]
> Esta secção aplica-se se utilizar o Conector de Certificado Intune apenas com um DigiCert CA. Se utilizar o Conector de Certificado Intune com um Microsoft CA e pretender adicionar suporte DigiCert CA, salte para a frente para [configurar o conector para suportar digiCert](#configure-the-connector-to-support-digicert).

1. Escolha uma das versões do sistema operativo Windows na lista seguinte e instale-a num computador:
   * Windows Server 2012 R2 Datacenter
   * Windows Server 2012 R2 Standard
   * Windows Server 2016 Datacenter
   * Windows Server 2016 Standard

2. Crie um utilizador com privilégios administrativos e utilize-o para realizar os passos seguintes.

3. Verifique as mais recentes atualizações do Windows e instale-as se estiver disponível. Depois de instalar as atualizações do Windows, reinicie o computador.

4. Instale o .NET Framework 3.5:

   a. Os programas **e funcionalidades** > **do Painel de Controlo** Aberto > ligar ou desligar as **funcionalidades**do Windows .

   b. Selecione o **.NET Framework 3.5** e instale-o.

## <a name="install-intune-certificate-connector-for-use-with-digicert"></a>Instale conector de certificado intune para utilização com digiCert

> [!TIP]
> Se utilizar o Conector de Certificado Intune com um Microsoft CA e pretender adicionar suporte DigiCert CA, salte para a frente para [configurar o conector para suportar digiCert](#configure-the-connector-to-support-digicert).

Descarregue a mais recente versão do Intune Certificate Connector do portal de administração Intune e siga estas instruções.

1. Inscreva-se no [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Selecione **a administração do Inquilino** > **Conectores e fichas** > **Conectores** de Certificado >  **+ Adicionar**.

3. Clique em *Baixar o software de conector* do certificado para o conector para pKCS #12 e guarde o ficheiro para um local a que possa aceder a partir do servidor onde vai instalar o conector.

   ![Descarregue o software do conector](./media/certificates-digicert-configure/connector-download.png)

4. No servidor onde pretende instalar o conector, execute **o NDESConnectorSetup.exe** com privilégios elevados.

5. Na página Opções de **Instalação,** selecione **Distribuição PFX**.

   ![Selecione Distribuição PFX](./media/certificates-digicert-configure/digicert-ca-connector-install.png)

   > [!IMPORTANT]
   > Se utilizar o Conector de Certificado Intune para emitir certificados de um Ca Microsoft e um DigiCert CA, selecione **SCEP e PFX Profile Distribution**.

6. Utilize as seleções predefinidas para terminar a configuração do conector.

## <a name="configure-the-connector-to-support-digicert"></a>Configure o conector para apoiar digiCert

Por predefinição, o Conector de Certificado Intune é instalado em **%ProgramFiles%\Microsoft Intune\NDESConnectorSvc**.

1. Na pasta **NDESConnectorSvc,** abra o ficheiro **NDESConnector.exe.config** no Bloco de Notas.

   a. Atualize o valor-chave `RACertThumbprint` com o valor de impressão digital do certificado que copiou na secção anterior. Por exemplo:

        <add key="RACertThumbprint"
        value="EA7A4E0CD1A4F81CF0740527C31A57F6020C17C5"/>

   b. Guarde e feche o ficheiro.

2. Serviços **abertos.msc:**

   a. Selecione **Intune Connector Service**.

   b. Pare o serviço e, em seguida, inicie-o.

   c. Feche a janela do serviço.

## <a name="set-up-the-intune-administrator-account"></a>Configurar a conta de administrador Intune  

> [!TIP]
> Se utilizar o Conector de Certificado Intune com um Microsoft CA e quiser adicionar suporte digiCert CA, salte para a frente para Criar um perfil de [certificado fidedigno](#create-a-trusted-certificate-profile).
 
1. Abra a interface de utilizador do Conector NDES a partir de **%ProgramFiles%\Microsoft Intune\NDESConnectorUI\NDESConnectorUI.exe**.

2. No separador **'Inscrição',** selecione **Iniciar sessão**.

3. Forneça as suas credenciais de administrador intune.

4. Selecione **Iniciar seleção**e, em seguida, selecione **OK** para confirmar uma inscrição bem sucedida. Em seguida, pode fechar a interface de utilizador do Conector NDES.

   ![Interface do Conector NDES com mensagem "com sucesso"](./media/certificates-digicert-configure/certificates-digicert-configure-connector-configure.png)

## <a name="create-a-trusted-certificate-profile"></a>Criar um perfil de certificado fidedigno

Os certificados PKCS que irá implantar para dispositivos geridos intune devem ser acorrentados com um certificado de raiz fidedigno. Para estabelecer esta cadeia, crie um perfil de certificado fidedigno intune com o certificado raiz da DigiCert CA.

1. Obtenha um certificado de raiz fidedigno da DigiCert CA:

   a. Inscreva-se no portal de administração digiCert CA.

   b. Selecione **Gerir Os CAs** a partir de **Tarefas**.

   c. Selecione o CA apropriado da lista.

   d. Selecione **descarregue** o certificado raiz de download para descarregar o certificado de raiz fidedigno.

2. Criar um perfil de certificado fidedigno no portal Intune:

   a. Inscreva-se no [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).

   b. Selecione **Dispositivos** > Perfis de **Configuração** > **Criar perfil**.

   c. Introduza as seguintes propriedades:

      - O **Nome** do perfil
      - Definir opcionalmente uma **Descrição**
      - A **Plataforma** na qual vai implementar o perfil
      - Defina o **Tipo de perfil** como **Certificado fidedigno**

   d. Selecione **Definições,** e, em seguida, navegue para o certificado CA de raiz fidedigno .cer file que exportou para uso com este perfil de certificado e, em seguida, selecione **OK**.

   e. Apenas para os dispositivos Windows 8.1 e Windows 10, selecione o **Arquivo de Destino** do certificado fidedigno em:
      - **Arquivo de certificados no computador – Raiz**
      - **Arquivo de certificados no computador – Intermédio**
      - **Armazenamento de certificados de utilizador – Intermédio**

   f. Quando tiver terminado, selecione **OK**, volte ao painel **Criar perfil** e selecione **Criar**.  

  O perfil aparece na lista de perfis na **configuração** do Dispositivo – Painel de perfis, com um tipo de perfil de **certificado Fidedigno**.  Certifique-se de atribuir este perfil a dispositivos que receberão certificados. Para atribuir o perfil a grupos, consulte os perfis do [dispositivo Atribuir](../configuration/device-profile-assign.md).


## <a name="get-the-certificate-profile-oid"></a>Obtenha o perfil de certificado OID  

O perfil do certificado OID está associado a um modelo de perfil de certificado no DigiCert CA. Para criar um perfil de certificado PKCS no Intune, o nome do modelo de certificado deve estar sob a forma de um OID de perfil de certificado que esteja associado a um modelo de certificado no DigiCert CA.

1. Inscreva-se no portal de administração digiCert CA.
2. Selecione **Gerir perfis de certificado**.
3. Selecione o perfil do certificado que pretende utilizar.
4. Copie o perfil do certificado OID. É semelhante ao seguinte exemplo:

       Certificate Profile OID = 2.16.840.1.113733.1.16.1.2.3.1.1.47196109 

> [!NOTE]
> Se precisar de ajuda para obter o perfil do certificado OID, contacte o [apoio ao cliente da DigiCert](mailto:enterprise-pkisupport@digicert.com).

## <a name="create-a-pkcs-certificate-profile"></a>Criar um perfil de certificado PKCS

1. Inscreva-se no [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Selecione **Dispositivos** > Perfis de **Configuração** > **Criar perfil**.

3. Introduza as seguintes propriedades:

   - O **Nome** do perfil
   - Definir opcionalmente uma **Descrição**
   - A **Plataforma** na qual vai implementar o perfil
   - Defina o **Tipo de perfil** como **Certificado PKCS**

4. No painel de **certificados PKCS,** configure os parâmetros com os valores da tabela seguinte. Estes valores são obrigados a emitir certificados PKCS de um DigiCert CA, através do Conector de CertificadoIno.

   |Parâmetro de certificado PKCS | Valor | Description |
   | --- | --- | --- |
   | Autoridade de certificação | pki-ws.symauth.com | Este valor deve ser o serviço base DigiCert CA FQDN sem cortes de rasto. Se não tiver a certeza se este é o serviço base correto FQDN para a sua subscrição DigiCert CA, contacte o suporte ao cliente da DigiCert. <br><br>*Com a mudança de Symantec para DigiCert, este URL permanece inalterado*. <br><br> Se este FQDN estiver incorreto, o Intune Certificate Connector não emitirá certificados PKCS da DigiCert CA.| 
   | Nome da autoridade de certificação | Symantec | Este valor tem de ser a cadeia **Symantec**. <br><br> Se houver alguma alteração a este valor, o Intune Certificate Connector não emitirá certificados PKCS da DigiCert CA.|
   | Nome do modelo de certificado | Perfil de certificado OID da DigiCert CA. Por exemplo: **2.16.840.1.113733.1.16.1.2.3.1.1.61904612**| Este valor deve ser um OID de perfil de certificado [obtido na secção anterior](#get-the-certificate-profile-oid) a partir do modelo de perfil de certificado DigiCert CA. <br><br> Se o Conector de Certificado Intune não encontrar um modelo de certificado associado a este perfil de certificado OID no DigiCert CA, não emitirá certificados PKCS da DigiCert CA.|

   ![Seleções para CA e modelo de certificado](./media/certificates-digicert-configure/certificates-digicert-pkcs-example.png)

   > [!NOTE]
   > O perfil de certificado PKCS para plataformas Windows não precisa de se associar a um perfil de certificado fidedigno. No entanto, é preciso fazê-lo para perfis de plataformas não Windows como o Android.

5. Complete a configuração do perfil para atender às necessidades do seu negócio e, em seguida, selecione **Criar** para salvar o perfil.

6. Na página *de visão geral* do novo perfil, selecione **Atribuições** e configure um grupo apropriado que receberá este perfil. Pelo menos um utilizador ou dispositivo tem de fazer parte do grupo atribuído.
 
Depois de completar as etapas anteriores, o Intune Certificate Connector emitirá certificados PKCS da DigiCert CA para dispositivos geridos por Intune no grupo designado. Estes certificados estarão disponíveis na loja **pessoal** da loja de certificados **Utilizador Atual** no dispositivo gerido por Intune.

### <a name="supported-attributes-for-the-pkcs-certificate-profile"></a>Atributos suportados para o perfil de certificado PKCS

|Atributo | Formatos suportados intune | Formatos suportados digiCert Cloud CA | result |
| --- | --- | --- | --- |
| Nome do requerente |O Intune suporta o nome do requerente apenas nos seguintes três formatos: <br><br> 1. Nome comum <br> 2. Nome comum que inclui e-mail <br> 3. Nome comum como e-mail <br><br> Por exemplo: <br><br> `CN = IWUser0 <br><br> E = IWUser0@samplendes.onmicrosoft.com` | O DigiCert CA suporta mais atributos.  Se quiser selecionar mais atributos, devem ser definidos com valores fixos no modelo de perfil do certificado DigiCert.| Utilizamos o nome comum ou o e-mail do pedido de certificado PKCS. <br><br> Qualquer incompatibilidade na seleção de atributos entre o perfil do certificado Intune e o modelo de perfil de certificado DigiCert não resulta em certificados emitidos pela DigiCert CA.|
| SAN | O Intune suporta apenas os valores de campo de SAN seguintes: <br><br> **AltNameTypeEmail** <br> **AltNameTypeUpn** <br> **AltNameTypeOtherName** (valor codificado) | O DigiCert Cloud CA também suporta estes parâmetros. Se quiser selecionar mais atributos, devem ser definidos com valores fixos no modelo de perfil do certificado DigiCert. <br><br> **AltNameTypeEmail**: Se este tipo não for encontrado no SAN, o Conector de Certificado Intune utiliza o valor de **AltNameTypeUpn**.  Se o **AltNameTypeUpn** também não for encontrado no SAN, então o Conector de Certificado Intune utiliza o valor a partir do nome do assunto se estiver em formato de e-mail.  Se o tipo ainda não for encontrado, o Conector de Certificado Intune não emite os certificados. <br><br> Exemplo: `RFC822 Name=IWUser0@ndesvenkatb.onmicrosoft.com`  <br><br> **AltNameTypeUpn**: Se este tipo não for encontrado no SAN, o Conector de Certificado Intune utiliza o valor do **AltNameTypeEmail**. Se o **AltNameTypeEmail** também não for encontrado no SAN, então o Conector de Certificado Intune utiliza o valor a partir do nome do assunto se estiver em formato de e-mail. Se o tipo ainda não for encontrado, o Conector de Certificado Intune não emite os certificados.  <br><br> Exemplo: `Other Name: Principal Name=IWUser0@ndesvenkatb.onmicrosoft.com` <br><br> **AltNameTypeOtherName**: Se este tipo não for encontrado no SAN, o Conector de Certificado Intune não emite os certificados. <br><br> Exemplo: `Other Name: DS Object Guid=04 12 b8 ba 65 41 f2 d4 07 41 a9 f7 47 08 f3 e4 28 5c ef 2c` <br><br>  O valor deste campo é suportado apenas em formato codificado (valor hexadecimal) pelo DigiCert CA. Por qualquer valor neste campo, o Conector de Certificado Intune converte-o em codificação base64 antes de submeter o pedido de certificado. *O Intune Certificate Connector não será validado quer este valor esteja codificado ou não.* | Nenhum |

## <a name="troubleshooting"></a>Resolução de Problemas

Os registos de serviço do Conector de Certificado Intune estão disponíveis em **%ProgramFiles%\Microsoft Intune\NDESConnectorSvc\Logs\Logs** na máquina de conector NDES. Abra os registos no [SvcTraceViewer](https://docs.microsoft.com/dotnet/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe) e procure exceções ou mensagens de erro.

| Mensagem de problema/erro | Passos de resolução |
| --- | --- |
| Incapaz de assinar com a conta de administrador intune no NDES Connector UI. | Isto pode acontecer quando o conector de certificados no local não está ativado no Microsoft Endpoint Manager Admin Center. Para resolver esta questão: <br><br> 1. Inscreva-se no [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431). <br> 2. Selecione **a administração do inquilino** > **Conectores e fichas** > **conectores**de certificados . <br> 3. Localize o conector do certificado e certifique-se de que está ativado. <br><br> Depois de completar os passos anteriores, tente iniciar sessão com a mesma conta de administrador intune no NDES Connector UI. |
| Não foi possível encontrar o certificado do Conector do NDES. <br><br> System.ArgumentNullException: O valor não pode ser nulo. | O Intune Certificate Connector mostrará este erro se a conta de administrador de inquilino do Intune nunca tiver iniciado sessão na IU do Conector do NDES. <br><br> Se este erro persistir, reinicie o Conector de Serviço Intune. <br><br> 1. **Serviços abertos.msc**. <br> 2. Selecione o serviço de **conector intune**. <br> 3. Clique à direita e selecione **Reiniciar**.|
| Conector do NDES – IssuePfx – Exceção Genérica: <br> System.NullReferenceException: a referência do objeto não foi definida para uma instância de um objeto. | Este erro é transitório. Reiniciar o Conector de Serviço Intune. <br><br> 1. **Serviços abertos.msc**. <br> 2. Selecione o serviço de **conector intune**. <br> 3. Clique à direita e selecione **Reiniciar**. |
| Provedor de DigiCert - Falhou na política da DigiCert. <br><br>"A operação tem esgotado." | O Conector de Certificado Intune recebeu um erro de tempo de funcionamento enquanto comunicava com o DigiCert CA. Se este erro continuar a ocorrer, aumente o valor de tempo de ligação e tente novamente. <br><br> Para aumentar o tempo de ligação: <br> 1. Vá ao computador DoConector NDES. <br>2. Abra o ficheiro **%ProgramFiles%\Microsoft Intune\NDESConnectorSvc\NDESConnector.exe.config** file in Notepad. <br> 3. Aumente o valor de tempo para o seguinte parâmetro: <br><br> `CloudCAConnTimeoutInMilliseconds` <br><br> 4. Reiniciar o serviço de conector de certificado intune. <br><br> Se o problema persistir, contacte o apoio ao cliente da DigiCert. |
| Provedor de DigiCert - Não conseguiu obter o certificado de cliente. | O Conector de Certificado Intune não conseguiu recuperar o certificado de autorização de recursos da loja de certificados Local Machine-Personal. Para resolver este problema, instale o certificado de autorização de recursos na loja de certificados Local Machine-Personal, juntamente com a sua chave privada. <br><br> O certificado de autorização de recurso deve ser obtido a partir da DigiCert CA. Para mais detalhes, contacte o apoio ao cliente da DigiCert. | 
| Provedor de DigiCert - Falhou na política da DigiCert. <br><br>"O pedido foi abortado: não podia criar um canal seguro SSL/TLS." | Este erro ocorre nos seguintes cenários: <br><br> 1. O serviço Intune Certificate Connector não tem permissões para ler o certificado de autorização de recursos, juntamente com a sua chave privada da loja de certificados Local Machine-Personal. Para resolver este problema, verifique a conta de contexto de funcionamento do serviço de conector em serviços.msc. O serviço de conector deve ser executado sob o contexto NT AUTHORITY\SYSTEM. <br><br> 2. O perfil de certificado PKCS no portal de administração Intune pode ser configurado com um serviço base inválido FQDN para o DigiCert CA. O FQDN é semelhante ao **pki-ws.symauth.com**. Para resolver este problema, verifique com o suporte ao cliente da DigiCert se o URL está correto para a sua subscrição. <br><br> 3. O Conector de Certificado Intune não autentica com o DigiCert CA através do certificado de autorização de recurso porque não consegue recuperar a chave privada. Para resolver este problema, instale o certificado de autorização de recursos juntamente com a sua chave privada na loja de certificados Local Machine-Personal. <br><br> Se o problema persistir, contacte o apoio ao cliente da DigiCert. |
| Provedor de DigiCert - Falhou na política da DigiCert. <br><br>"Um elemento de pedido não é compreendido." | O Conector de Certificado Intune não conseguiu obter o modelo de perfil de certificado DigiCert, porque o perfil do cliente OID não corresponde ao perfil do certificado Intune. Noutro caso, o Intune Certificate Connector não consegue encontrar o modelo de perfil do certificado associado ao perfil do cliente OID no DigiCert CA. <br><br> Para resolver este problema, obtenha o OID de perfil de cliente correto a partir do modelo de Certificado DigiCert no DigiCert CA. Em seguida, atualize o perfil de certificado PKCS no portal de administração Intune. <br><br> Obtenha o perfil do cliente OID da DigiCert CA: <br> 1. Inscreva-se no portal de administração digiCert CA. <br> 2. Selecione **Gerir perfis de certificado**. <br> 3. Selecione o perfil do certificado que pretende utilizar. <br> 4. Obtenha o perfil de certificado OID. É semelhante ao seguinte exemplo: <br> `Certificate Profile OID = 2.16.840.1.113733.1.16.1.2.3.1.1.47196109` <br><br> Atualize o perfil do certificado PKCS com o perfil correto OID: <br>1. Inscreva-se no portal de administração Intune. <br> 2. Vá ao perfil do certificado PKCS e **selecione Editar**. <br> 3. Atualize o perfil do certificado OID no campo para o nome do modelo de certificado. <br> 4. Guarde o perfil do certificado PKCS. |
| Provedor de DigiCert - Verificação de política falhou. <br><br> O atributo não se enquadra na lista de atributos de modelo de certificado suportado digiCert. | O DigiCert CA mostra esta mensagem quando há uma discrepância entre o modelo de perfil de certificado DigiCert e o perfil de certificado Intune. Este problema provavelmente aconteceu devido à incompatibilidade de atributos no **Nome do Assunto** ou no **SubsujeitoAltName**. <br><br> Para resolver este problema, selecione atributos suportados por Intune para **O Nome subjetivo** e **subnome** no modelo de perfil do certificado DigiCert. Para mais informações, consulte os atributos suportados intune na secção Parâmetros de **Certificado.** |
| Alguns dispositivos de utilizador não estão a receber certificados PKCS da DigiCert CA. | Este problema acontece quando o utilizador UPN contém caracteres especiais como um sublinhado (exemplo: `global_admin@intune.onmicrosoft.com`). <br><br> A DigiCert CA não suporta personagens especiais em **mail_firstname** e **mail_lastname.** <br><br> Os passos seguintes ajudam a resolver este problema: <br><br> 1. Inscreva-se no portal de administração digiCert CA. <br> 2. Ir gerir perfis de **certificados**. <br> 3. Selecione o perfil do certificado utilizado para o Intune. <br> 4. Selecione o link **Personalizar opções.** <br> 5. Selecione o botão **opções Avançadas.** <br> 6. Nos termos dos **campos de certificados – Objeto DN,** adicione um campo **de nome comum (CN)** e elimine o campo de **Nome Comum (CN)** existente. Adicionar e eliminar as operações devem ser efetuadas em conjunto. <br> 7. Selecione **Guardar**. <br><br> Com a alteração anterior, o perfil do certificado DigiCert solicita **"CN=<upn>"** em vez de **mail_firstname** e **mail_lastname**. |
| O utilizador eliminado manualmente já implementou o certificado do dispositivo. | Intune reimplanta o mesmo certificado durante o próximo check-in ou aplicação da política. Neste caso, o Conector NDES não recebe um pedido de certificado PKCS. |

## <a name="next-steps"></a>Próximos passos

Utilize as informações deste artigo para além das informações nos perfis do [dispositivo Microsoft Intune?](../configuration/device-profiles.md)
