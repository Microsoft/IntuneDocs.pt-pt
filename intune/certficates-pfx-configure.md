---
title: Usar certificados de chave pública e privada no Microsoft Intune-Azure | Microsoft Docs
description: Adicionar ou criar certificados PKCS (padrões de criptografia de chave pública) com o Microsoft Intune, incluindo as etapas para exportar um certificado raiz, configurar o modelo de certificado, baixar e instalar o NDES (conector de certificado do Intune), criar um dispositivo Perfil de configuração e criar um perfil de certificado PKCS no Azure e sua autoridade de certificação.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 08/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 064377ea05319242da087862b4d2b3a721b0caef
ms.sourcegitcommit: 3db8af810b95c3a6ed3f8cc00f6ce79076ebb9db
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/16/2019
ms.locfileid: "71012470"
---
# <a name="configure-and-use-pkcs-certificates-with-intune"></a>Configurar e utilizar certificados PKCS com o Intune

O Intune dá suporte ao uso de certificados PKCS e privados (par de chaves públicas). Este artigo pode ajudá-lo a configurar a infraestrutura necessária como conectores de certificado locais, exportar um certificado PKCS e, em seguida, adicionar o certificado a um perfil de configuração de dispositivo do Intune.

Microsoft Intune inclui configurações internas para usar certificados PKCS para acesso e autenticação aos recursos de sua organização. Os certificados autenticam e protegem o acesso aos recursos corporativos, como uma VPN ou uma rede WiFi. Implante essas configurações em dispositivos usando perfis de configuração de dispositivo no Intune.

Para obter informações sobre como usar certificados PKCS importados, consulte [certificados PFX importados](certificates-imported-pfx-configure.md).


## <a name="requirements"></a>Requisitos

Para usar certificados PKCS com o Intune, você precisará da seguinte infraestrutura:

- **Active Directory domínio**:  
  Todos os servidores listados nesta seção devem ser associados ao seu domínio de Active Directory.

  Para obter mais informações sobre como instalar e configurar Active Directory Domain Services (AD DS), consulte [AD DS design e planejamento](https://docs.microsoft.com/windows-server/identity/ad-ds/plan/ad-ds-design-and-planning).

- **Autoridade de certificação**:  
   Uma AC (autoridade de certificação) corporativa.

  Para obter informações sobre como instalar e configurar Active Directory serviços de certificados (AD CS), consulte [Active Directory guia passo a passo dos serviços de certificados](https://technet.microsoft.com/library/cc772393).

  > [!WARNING]  
  > O Intune requer a execução do AD CS com uma Autoridade de Certificação (AC) Empresarial e não uma AC Autónoma.

- **Um cliente**:  
  Para se conectar à AC corporativa.

- **Certificado raiz**:  
  Uma cópia exportada do certificado de raiz da AC Empresarial.

- **Microsoft Intune Certificate Connector** (também chamado de *conector de certificado NDES*):  
  No portal do Intune, vá para **configuração** > do dispositivo**conectores** > de certificado**Adicionar**e siga as *etapas para instalar o conector para #12 PKCS*. Use o link de download no portal para iniciar o download do instalador do conector de certificado **NDESConnectorSetup. exe**.  

  O Intune dá suporte a até 100 instâncias desse conector por locatário, com cada instância em um Windows Server separado. Você pode instalar uma instância desse conector no mesmo servidor que uma instância do conector de certificado PFX para Microsoft Intune. Quando você usa vários conectores, a infraestrutura do conector dá suporte à alta disponibilidade e ao balanceamento de carga, uma vez que qualquer instância de conector disponível pode processar suas solicitações de certificado PKCS. 

  Esse conector processa as solicitações de certificado PKCS usadas para autenticação ou assinatura de email S/MIME.

  O Microsoft Intune Certificate Connector também dá suporte ao modo padrão FIPS (FIPS). O FIPS não é obrigatório, mas pode emitir e revogar certificados quando está ativado.

- **Conector de certificado pfx para Microsoft Intune**:  
  Se você planeja usar a criptografia de email S/MIME, use o portal do Intune para baixar o *conector de certificado pfx* que dá suporte à importação de certificados PFX.  Vá para **configuração** > do dispositivo**conectores** > de certificado**Adicionar**e siga as *etapas para instalar o conector para certificados PFX importados*. Use o link de download no portal para iniciar o download do instalador **PfxCertificateConnectorBootstrapper. exe**. 

  Cada locatário do Intune dá suporte a uma única instância desse conector. Você pode instalar esse conector no mesmo servidor que uma instância do conector de certificado Microsoft Intune.

  Esse conector lida com solicitações para arquivos PFX importados para o Intune para criptografia de email S/MIME para um usuário específico.  

  Esse conector pode se atualizar automaticamente quando novas versões forem disponibilizadas. Para usar o recurso de atualização, você deve:
  - Instale o conector de certificado PFX para Microsoft Intune em seu servidor.  
  - Para receber atualizações importantes automaticamente, verifique se os firewalls estão abertos e permita que o conector entre em contato com o **AutoUpdate.msappproxy.net** na porta **443**.   

  Para obter mais informações sobre pontos de extremidade de rede que o Intune e o conector devem ser capazes de acessar, consulte [pontos de extremidade de rede para Microsoft Intune](intune-endpoints.md).

- **Windows Server**:  
  Você usa um Windows Server para hospedar:

  - Microsoft Intune Certificate Connector-para autenticação e cenários de assinatura de email S/MIME
  - Conector de certificado PFX para Microsoft Intune-para cenários de criptografia de email S/MIME.

  O Intune dá suporte à instalação do *conector de certificado pfx* no mesmo servidor que o *Microsoft Intune Certificate Connector*.
  
## <a name="export-the-root-certificate-from-the-enterprise-ca"></a>Exportar o certificado de raiz da AC Empresarial

Para autenticar um dispositivo com VPN, WiFi ou outros recursos, um dispositivo precisa de um certificado de autoridade de certificação raiz ou intermediária. Os passos seguintes explicam como obter o certificado necessário a partir da AC Empresarial.

**Use uma linha de comando**:  
1. Faça logon no servidor de autoridade de certificação raiz com a conta de administrador.
 
2. Vá para **Iniciar** > **execução**e digite **cmd** para abrir o prompt de comando. 
    
3. Especifique **certutil-ca. cert CA_Name. cer** para exportar o certificado raiz como um arquivo chamado *CA_Name. cer*.



## <a name="configure-certificate-templates-on-the-ca"></a>Configurar modelos de certificado na autoridade de certificação

1. Inicie sessão na AC Empresarial com uma conta que tenha privilégios administrativos.
2. Abra a consola **Autoridade de Certificação**, clique com o botão direito do rato em **Modelos de Certificado** e selecione **Gerir**.
3. Localize o modelo de certificado de **Utilizador**, clique com o botão direito do rato nele e escolha **Duplicar Modelo**. As **Propriedades de Novo Modelo** são abertas.

    > [!NOTE]
    > Para cenários de encriptação e assinaturas de e-mail com S/MIME, muitos administradores utilizam certificados separados para assinar e encriptar. Se estiver a utilizar os Serviços de Certificados do Microsoft Active Directory, pode utilizar o modelo **Apenas Assinatura do Exchange** para certificados de assinaturas de e-mail S/MIME e o modelo **Utilizador do Exchange** para certificados de encriptação S/MIME.  Se você estiver usando uma autoridade de certificação de terceiros, é recomendável revisar suas diretrizes para configurar modelos de assinatura e criptografia.

4. No separador **Compatibilidade**:

    - Defina **Autoridade de Certificação** como **Windows Server 2008 R2**
    - Defina **Destinatário do certificado** como **Windows 7/Server 2008 R2**

5. No separador **Geral**, defina o **Nome a apresentar do modelo** para algo que seja relevante para si.

    > [!WARNING]
    > Por predefinição, o **Nome do modelo** é igual ao **Nome a apresentar do modelo** *sem espaços*. Anote o nome do modelo, irá precisar dele mais tarde.

6. Em **Processamento de Pedidos**, selecione **Permitir que a chave privada seja exportada**.
7. Em **Criptografia**, confirme se o **Tamanho mínimo da chave** está definido como 2048.
8. Em **Nome do Requerente**, selecione **Fornecer no pedido**.
9. Em **Extensões**, confirme se vê o Sistema de Encriptação de Ficheiros, Proteger o E-mail e Autenticação de Cliente em **Políticas de Aplicações**.

    > [!IMPORTANT]
    > Para os modelos de certificado iOS, aceda ao separador **Extensões**, atualize a **Utilização de Chaves** e confirme que a opção **A assinatura é uma prova de origem** não está selecionada.

10. Em **Segurança**, adicione a Conta de Computador do servidor no local onde irá instalar o Microsoft Intune Certificate Connector. Conceda a esta conta as permissões **Ler** e **Inscrever**.
11. Selecione **Aplicar** > **OK** para guardar o modelo de certificado. Feche a **Consola de Modelos de Certificado**.
12. Na consola **Autoridade de Certificação**, clique com o botão direito do rato em **Modelos de Certificado** > **Novo** > **Modelo de Certificado a Emitir**. Selecione o modelo criado nos passos anteriores. Selecione **OK**.
13. Para o servidor gerenciar certificados para dispositivos e usuários registrados, use as seguintes etapas:

    1. Clique com o botão direito do rato na Autoridade de Certificação e escolha **Propriedades**.
    2. No separador Segurança, adicione a conta do Computador do servidor onde executa os conectores (**Microsoft Intune Certificate Connector** ou **PFX Certificate Connector for Microsoft Intune**). 
    3. Conceda as permissões **Emitir e Gerir Certificados** e **Pedir Certificados** à conta de computador.

14. Termine a sessão na AC Empresarial.

## <a name="download-install-and-configure-the-microsoft-intune-certificate-connector"></a>Baixar, instalar e configurar o Microsoft Intune Certificate Connector

> [!IMPORTANT]  
> O Microsoft Intune Certificate Connector não pode ser instalado na autoridade de certificação emissora (CA) e, em vez disso, deve ser instalado em um servidor Windows separado.  

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Selecione **configuração** > do dispositivo**conectores** > de certificação**Adicionar**.
3. Baixe e salve o arquivo do conector em um local que você possa acessar do servidor no qual você vai instalar o conector.

    ![Download de Microsoft Intune Certificate Connector](media/certificates-pfx-configure/download-ndes-connector.png)
 

4. Após a transferência ser concluída, inicie sessão no servidor. Em seguida:

    1. Certifique-se de que o .NET 4.5 Framework ou superior está instalado, pois é necessário para o Certificate Connector do NDES. O .NET 4.5 Framework vem incluído automaticamente com o Windows Server 2012 R2 e versões mais recentes.
    2. Execute o instalador (NDESConnectorSetup.exe) e aceite a localização predefinida. O conector é instalado em `\Program Files\Microsoft Intune\NDESConnectorUI`. Nas Opções do Instalador, selecione **PFX Distribution** (Distribuição PFX). Continue para concluir a instalação.
    3. Por predefinição, o serviço do conector é executado na conta do sistema local. Se for necessário um proxy para aceder à Internet, confirme que a conta do serviço local consegue aceder às definições de proxy no servidor.

5. O Microsoft Intune Certificate Connector abre a guia **registro** . Para ativar a ligação ao Intune, selecione **Sign In** (Iniciar Sessão) e introduza uma conta com permissões administrativas globais.
6. No separador **Avançadas**, recomendamos que deixe a opção **Utilizar a conta SYSTEM deste computador (predefinição)** selecionada.
7. **Aplicar** > **Fechar**
8. Volte para o portal do Intune (**conectores de certificação**de**configuração** > de dispositivo do**Intune** > ). Após alguns instantes, uma marca de seleção verde é mostrada e o **status da conexão** é **ativo**. Agora o servidor do conector pode comunicar com o Intune.
9. Se você tiver um proxy Web no seu ambiente de rede, talvez precise de configurações adicionais para permitir que o conector funcione. Para obter mais informações, consulte [trabalhar com servidores proxy locais existentes](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy-configure-connectors-with-proxy-servers) na documentação do Azure Active Directory.

> [!NOTE]  
> O Microsoft Intune Certificate Connector dá suporte a TLS 1,2. Se o TLS 1,2 estiver instalado no servidor que hospeda o conector, o conector usará o TLS 1,2. Caso contrário, o TLS 1,1 será usado. Atualmente, é utilizado o TLS 1.1 para a autenticação entre os dispositivos e o servidor.

## <a name="create-a-trusted-certificate-profile"></a>Criar um perfil de certificado fidedigno

1. No [portal do Azure](https://portal.azure.com), aceda a **Intune** > **Configuração do dispositivo** > **Perfis** > **Criar perfil**.
    ![Navegue até o Intune e crie um novo perfil para um certificado confiável](media/certificates-pfx-configure/certificates-pfx-configure-profile-new.png)

2. Introduza as seguintes propriedades:

    - O **Nome** do perfil
    - Opcionalmente, defina uma descrição
    - A **Plataforma** na qual vai implementar o perfil
    - Defina o **Tipo de perfil** como **Certificado fidedigno**

3. Aceda às **Definições** e introduza o ficheiro .cer do Certificado da AC de Raiz que exportou anteriormente.

   > [!NOTE]
   > Dependendo da plataforma escolhida na **etapa 2**, você pode ou não ter a opção de escolher o **repositório de destino** para o certificado.

   ![Criar um perfil e carregar um certificado confiável](media/certificates-pfx-configure/certificates-pfx-configure-profile-fill.png) 

4. Selecione **OK** > **Criar** para guardar o perfil.
5. Para atribuir o novo perfil a um ou mais dispositivos, veja [Atribuir perfis de dispositivo no Microsoft Intune](device-profile-assign.md).

## <a name="create-a-pkcs-certificate-profile"></a>Criar um perfil de certificado PKCS

1. No [portal do Azure](https://portal.azure.com), aceda a **Intune** > **Configuração do dispositivo** > **Perfis** > **Criar perfil**.
2. Introduza as seguintes propriedades:

    - O **Nome** do perfil
    - Opcionalmente, defina uma descrição
    - A **Plataforma** na qual vai implementar o perfil
    - Defina o **Tipo de perfil** como **Certificado PKCS**

3. Aceda a **Definições** e introduza as seguintes propriedades:

    - **Limite de renovação (%)** : O recomendado é de 20%.
    - **Período de validade do certificado**: Se você não alterou o modelo de certificado, essa opção pode ser definida como um ano.
    - **Provedor de armazenamento de chaves (KSP)** : Para o Windows, selecione onde armazenar as chaves no dispositivo.
    - **Autoridade de certificação**: Exibe o FQDN (nome de domínio totalmente qualificado) interno da sua autoridade de certificação corporativa.
    - **Nome da autoridade de certificação**: Lista o nome de sua autoridade de certificação corporativa, como "autoridade de certificação contoso".
    - **Nome do modelo de certificado**: O nome do modelo criado anteriormente. Nota: por predefinição, o **Nome do modelo** é igual ao **Nome a apresentar do modelo** *sem espaços*.
    - **Formato do nome da entidade**: Defina essa opção como **nome comum** , a menos que seja necessário.
    - **Nome alternativo da entidade**: Defina essa opção como **nome principal do usuário (UPN)** , a menos que seja necessário.

4. Selecione **OK** > **Criar** para guardar o perfil.
5. Para atribuir o novo perfil a um ou mais dispositivos, veja [Atribuir perfis de dispositivo no Microsoft Intune](device-profile-assign.md).

   > [!NOTE]
   > Em dispositivos com um perfil do Android Enterprise, os certificados instalados usando um perfil de certificado PKCS não são visíveis no dispositivo. Para confirmar a implantação de certificado bem-sucedida, verifique o status do perfil no console do Intune.

## <a name="whats-new-for-connectors"></a>O que há de novo para conectores
As atualizações para os dois conectores de certificado são liberadas periodicamente. Quando atualizamos um conector, você pode ler sobre as alterações aqui. 

O *conector de certificados PFX para Microsoft Intune* [dá suporte a atualizações automáticas](#requirements), enquanto o *conector de certificado do Intune* é atualizado manualmente.

### <a name="may-17-2019"></a>17 de maio de 2019  
- **Conector de certificados PFX para 6.1905.0.404 de versão de Microsoft Intune**  
  Alterações nesta versão:  
  - Corrigido um problema em que os certificados PFX existentes continuam a ser reprocessados, o que faz com que o conector pare de processar novas solicitações. 

### <a name="may-6-2019"></a>6 de maio de 2019  
- **Conector de certificados PFX para 6.1905.0.402 de versão de Microsoft Intune**  
  Alterações nesta versão:  
  - O intervalo de sondagem para o conector é reduzido de 5 minutos a 30 segundos.
 
### <a name="april-2-2019"></a>2 de abril de 2019  
- **Conector de certificado do Intune – versão 6.1904.1.0**  
  Alterações nesta versão:  
  - Corrigido um problema em que o conector pode falhar ao se registrar no Intune depois de entrar no conector com uma conta de administrador global.  
  - Inclui correções de confiabilidade para revogação de certificado.  
  - Inclui correções de desempenho para aumentar a rapidez com que as solicitações de certificado PKCS são processadas.  

- **Conector de certificados PFX para 6.1904.0.401 de versão de Microsoft Intune**
  > [!NOTE]  
  > A atualização automática para esta versão do conector PFX não estará disponível até 11 de abril de 2019.  

  Alterações nesta versão:  
  - Corrigido um problema em que o conector pode falhar ao se registrar no Intune depois de entrar no conector com uma conta de administrador global.  


## <a name="next-steps"></a>Passos Seguintes

O perfil está criado, mas ainda não está ativo. Em seguida, [atribua o perfil](device-profile-assign.md) e [monitorize o estado](device-profile-monitor.md).

[Use o SCEP para certificados](certificates-scep-configure.md)ou [emita certificados PKCS de um serviço Web Symantec PKI Manager](certificates-symantec-configure.md).

