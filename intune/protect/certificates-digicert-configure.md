---
title: Emitir certificados PKCS DigiCert com Microsoft Intune
titleSuffix: Microsoft Intune
description: Instale e configure o Intune Certificate Connector para emitir certificados PKCS da plataforma DigiCert PKI para dispositivos gerenciados pelo Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/19/2019
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
ms.openlocfilehash: dc0194bfaf1ec5e3120b6bd30eb6b2eb82c6ec2d
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72504725"
---
# <a name="set-up-intune-certificate-connector-for-digicert-pki-platform"></a>Configurar o conector de certificado do Intune para a plataforma de PKI DigiCert  

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Use o Intune Certificate Connector para emitir certificados PKCS da plataforma DigiCert PKI para dispositivos gerenciados pelo Intune. Você pode usar o conector com apenas uma autoridade de certificação (CA) DigiCert ou com uma CA DigiCert e uma AC da Microsoft.  
> [!TIP]  
> A DigiCert adquiriu a segurança do site da Symantec e a empresa de soluções de PKI relacionadas. Para obter mais informações sobre essa alteração, consulte o [artigo de suporte técnico da Symantec](https://support.symantec.com/en_US/article.INFO4722.html).

Se você já usa o conector de certificado do Intune para emitir certificados de uma AC da Microsoft usando o PKCS ou o System Center Endpoint Protection, você pode usar esse mesmo conector para configurar e emitir certificados PKCS de uma AC DigiCert. Depois de concluir a configuração para dar suporte à AC do DigiCert, o Intune Certificate Connector pode emitir os seguintes certificados:

* Certificados PKCS de uma AC da Microsoft
* Certificados PKCS de uma AC DigiCert
* Endpoint Protection certificados de uma AC da Microsoft

Se você não tiver o conector instalado, mas planeja usá-lo para uma AC da Microsoft e uma AC DigiCert, conclua primeiro a configuração do conector para a autoridade de certificação da Microsoft. Em seguida, retorne a este artigo para configurá-lo para também dar suporte a DigiCert. Para obter mais informações sobre perfis de certificado e o conector, consulte [configurar um perfil de certificado para seus dispositivos no Microsoft Intune](certificates-configure.md).  

Se você usar o conector somente com a AC DigiCert, poderá usar as instruções neste artigo para instalar e configurar o conector. 

## <a name="prerequisites"></a>Pré-requisitos  
- **Uma assinatura ativa na AC DigiCert**: a assinatura é necessária para obter um certificado de ra (autoridade de registro) da AC DigiCert.

## <a name="install-the-digicert-ra-certificate"></a>Instalar o certificado DigiCert RA  
 
1. Salve o seguinte trecho de código como em um arquivo chamado **Certreq. ini** e atualize-o conforme necessário (por exemplo: *nome da entidade no formato CN*).
 
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

2. Abra um prompt de comando com privilégios elevados e gere uma solicitação de assinatura de certificado (CSR) usando o seguinte comando:

   `Certreq.exe -new certreq.ini request.csr`

3. Abra o arquivo request. CSR no bloco de notas e copie o conteúdo do CSR que está no seguinte formato:


        -----BEGIN NEW CERTIFICATE REQUEST-----
        MIID8TCCAtkCAQAwbTEMMAoGA1UEBhMDVVNBMQswCQYDVQQIDAJXQTEQMA4GA1UE
        …
        …
        fzpeAWo=
        -----END NEW CERTIFICATE REQUEST-----


4. Entre na AC do DigiCert e navegue para **obter um certificado ra** das tarefas.

   a. Na caixa de texto, forneça o conteúdo do CSR da etapa 3. 

   b. Forneça um nome amigável para o certificado.

   c. Selecione **continuar**. 

   d. Use o link fornecido para baixar o certificado RA para o computador local.

5. Importe o certificado RA para o repositório de certificados do Windows:

   a. Abra uma consola MMC.

   b. Selecione **arquivo** > **Adicionar ou Remover Snap-ins** > **certificado** > **Adicionar**. 

   c. Selecione **conta de computador** > **Avançar**.

   d. Selecione **computador Local** > **concluir**. 

   e. Selecione **OK** na janela **Adicionar ou remover snap-ins** . Expanda **certificados (computador local)**  > **certificados** **pessoais** > .

   f. Clique com o botão direito do rato no nó **Certificados** e selecione **Todas as Tarefas** > **Importar**.  

   g. Selecione o local do certificado RA que você baixou da AC DigiCert e, em seguida, selecione **Avançar**.

   t. Selecione **repositório de certificados pessoais** > **Avançar**. 

   i. Selecione **concluir** para importar o certificado ra e sua chave privada para o repositório **pessoal do computador local** .  

6. Exporte e importe o certificado de chave privada: 

   a. Expanda **Certificados (Computador Local)**  > **Pessoal** > **Certificados**.

   b. Selecione o certificado importado no passo anterior.

   c. Clique com o botão direito do mouse no certificado e selecione **todas as tarefas** > **Exportar**.

   d. Selecione **Avançar**e digite a senha.

   e. Selecione o local para o qual exportar e, em seguida, selecione **concluir**.

   f. Use o procedimento da etapa 5 para importar o certificado de chave privada para o repositório **pessoal do computador local** .

   g. Registre uma cópia da impressão digital do certificado RA sem espaços. Veja a seguir um exemplo de impressão digital: 

        RA Cert Thumbprint: “EA7A4E0CD1A4F81CF0740527C31A57F6020C17C5”
    
    > [!NOTE]
    > Para obter ajuda para obter o certificado RA da AC DigiCert, entre em contato com o [suporte ao cliente do DigiCert](mailto:enterprise-pkisupport@digicert.com).  

## <a name="prepare-to-install-intune-certificate-connector"></a>Preparar-se para instalar o Intune Certificate Connector
> [!TIP]  
> Esta seção se aplicará se você usar o conector de certificado do Intune com apenas uma AC DigiCert. Se você usar o conector de certificado do Intune com uma AC da Microsoft e quiser adicionar o suporte de AC DigiCert, pule para [Configurar o conector para dar suporte ao DigiCert](#configure-the-connector-to-support-digicert).  

1. Escolha uma das versões do sistema operacional Windows na lista a seguir e instale-a em um computador:
   * Windows Server 2012 R2 Datacenter
   * Windows Server 2012 R2 Standard
   * Windows Server 2016 datacenter
   * Windows Server 2016 Standard

2. Crie um utilizador com privilégios administrativos e utilize-o para realizar os passos seguintes.

3. Verifique as atualizações mais recentes do Windows e instale-as, se disponíveis. Depois de instalar as atualizações do Windows, reinicie o computador.

4. Instale o .NET Framework 3.5:

   a. Abra o **painel de controle** > **programas e recursos** > **Ativar ou desativar recursos do Windows**.

   b. Selecione o **.NET Framework 3.5** e instale-o.  

## <a name="install-intune-certificate-connector-for-use-with-digicert"></a>Instalar o Intune Certificate Connector para uso com DigiCert  

> [!TIP]  
> Se você usar o conector de certificado do Intune com uma AC da Microsoft e quiser adicionar o suporte de AC DigiCert, pule para [Configurar o conector para dar suporte ao DigiCert](#configure-the-connector-to-support-digicert).  

Baixe a versão mais recente do Intune Certificate Connector no portal de administração do Intune e siga estas instruções.

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).  

2. Selecione **configuração do dispositivo** > **conectores de certificado** >  **+ Adicionar**.  

3. Selecione **baixar o software do conector de certificado**. Salve o software em um local onde você possa acessá-lo do servidor no qual você vai instalá-lo.  

   ![Baixar o software do conector](./media/certificates-digicert-configure/connector-download.png)
   
4. No servidor em que você deseja instalar o conector, execute **NDESConnectorSetup. exe** com privilégios elevados. 

5. Na página **Opções de instalação** , selecione **distribuição pfx**.  
   
   ![Selecionar distribuição PFX](./media/certificates-digicert-configure/digicert-ca-connector-install.png)

   > [!IMPORTANT]
   > Se você usar o conector de certificado do Intune para emitir certificados de uma AC da Microsoft e de uma AC DigiCert, selecione **distribuição de perfil SCEP e pfx**. 

6. Use as seleções padrão para concluir a configuração do conector.

## <a name="configure-the-connector-to-support-digicert"></a>Configurar o conector para dar suporte a DigiCert

Por padrão, o Intune Certificate Connector é instalado em **%ProgramFiles%\Microsoft Intune\NDESConnectorSvc**.

1. Na pasta **NDESConnectorSvc** , abra o arquivo **NDESConnector. exe. config** no bloco de notas.

   a. Atualize o valor da chave `RACertThumbprint` com o valor de impressão digital do certificado que você copiou na seção anterior. Por exemplo:

        <add key="RACertThumbprint"
        value="EA7A4E0CD1A4F81CF0740527C31A57F6020C17C5"/>
   
   b. Salve e feche o arquivo.

2. Abra **Services. msc**:

   a. Selecione **Intune Connector Service**.

   b. Pare o serviço e, em seguida, inicie-o.

   c. Feche a janela do serviço.

## <a name="set-up-the-intune-administrator-account"></a>Configurar a conta de administrador do Intune  

> [!TIP]  
> Se você usar o conector de certificado do Intune com uma AC da Microsoft e quiser adicionar o suporte de AC DigiCert, pule para [criar um perfil de certificado confiável](#create-a-trusted-certificate-profile).   
 
1. Abra a interface de usuário do conector NDES de **%ProgramFiles%\Microsoft Intune\NDESConnectorUI\NDESConnectorUI.exe**.  

2. Na guia **registro** , selecione **entrar**.

3. Forneça suas credenciais de administrador de locatário do Intune.

4. Selecione **entrar**e, em seguida, selecione **OK** para confirmar um registro bem-sucedido. Em seguida, você pode fechar a interface do usuário do conector NDES.
   
   ![A interface do conector NDES com a mensagem "registrado com êxito"](./media/certificates-digicert-configure/certificates-digicert-configure-connector-configure.png)



## <a name="create-a-trusted-certificate-profile"></a>Criar um perfil de certificado fidedigno

Os certificados PKCS que você implantará para dispositivos gerenciados pelo Intune devem ser encadeados com um certificado raiz confiável. Para estabelecer essa cadeia, crie um perfil de certificado confiável do Intune com o certificado raiz da AC DigiCert.

1. Obtenha um certificado raiz confiável da AC DigiCert:

    a. Entre no portal de administração da AC do DigiCert.

    b. Selecione **gerenciar CAS** em **tarefas**. 

    c. Selecione a autoridade de certificação apropriada na lista.  

    d. Selecione **baixar certificado raiz** para baixar o certificado raiz confiável.

2. Criar um perfil de certificado confiável no portal do Intune:

   a. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).

   b. Selecione **Configuração do dispositivo** > **Gerir** > **Perfis** > **Criar perfil**.

   c. Insira os detalhes de **nome** e **Descrição** para o perfil de certificado confiável.

   d. Na lista pendente **Plataforma**, selecione a plataforma do dispositivo para este certificado fidedigno.

   e. Na lista suspensa **tipo de perfil** , selecione **certificado confiável**.

   f. Navegue até o arquivo. cer da AC raiz confiável que você obteve na autoridade de certificação DigiCert na etapa anterior e selecione **OK**.

   g. Somente para dispositivos Windows 8.1 e Windows 10, selecione o repositório de destino do certificado confiável de:    
      - **Arquivo de certificados no computador – Raiz**  
      - **Arquivo de certificados no computador – Intermédio**  
      - **Armazenamento de certificados de utilizador – Intermédio** 

   t. Quando tiver terminado, selecione **OK**, volte ao painel **Criar perfil** e selecione **Criar**.  
 
O perfil aparece na lista de perfis no painel **configuração do dispositivo – perfis** , com um tipo de perfil de **certificado confiável**.  Certifique-se de atribuir esse perfil a dispositivos que receberão certificados. Para atribuir o perfil a grupos, consulte [atribuir perfis de dispositivo](../configuration/device-profile-assign.md).


## <a name="get-the-certificate-profile-oid"></a>Obter o OID do perfil de certificado  

O OID do perfil de certificado está associado a um modelo de perfil de certificado na AC DigiCert. Para criar um perfil de certificado PKCS no Intune, o nome do modelo de certificado deve estar na forma de um OID de perfil de certificado associado a um modelo de certificado na autoridade de certificação DigiCert.

1. Entre no portal de administração da AC do DigiCert.
2. Selecione **gerenciar perfis de certificado**.
3. Selecione o perfil de certificado que você deseja usar.
4. Copie o OID do perfil de certificado. É semelhante ao seguinte exemplo:

 
       Certificate Profile OID = 2.16.840.1.113733.1.16.1.2.3.1.1.47196109 
 

> [!NOTE]
> Se você precisar de ajuda para obter o OID do perfil de certificado, entre em contato com o [suporte ao cliente do DigiCert](mailto:enterprise-pkisupport@digicert.com).

## <a name="create-a-pkcs-certificate-profile"></a>Criar um perfil de certificado PKCS

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).  

2. Vá para **configuração do dispositivo** >  **perfis**e selecione **Criar perfil**.

3. Insira os detalhes de **nome** e **Descrição** para o perfil de certificado PKCS.  

4. Na lista suspensa **plataforma** , selecione uma plataforma de dispositivo com suporte.

5. Na lista suspensa **tipo de perfil** , selecione **certificado PKCS**.
 
6. No painel **certificado PKCS** , configure os parâmetros com os valores da tabela a seguir. Esses valores são necessários para emitir certificados PKCS de uma AC DigiCert, por meio do Intune Certificate Connector. 

   |Parâmetro de certificado PKCS | Valor | Description |
   | --- | --- | --- |
   | Autoridade de certificação | pki-ws.symauth.com | Esse valor deve ser o FQDN do serviço base da AC DigiCert sem barras à direita. Se você não tiver certeza se esse é o FQDN de serviço base correto para sua assinatura de AC DigiCert, entre em contato com o suporte ao cliente do DigiCert. <br><br>*Com a alteração do Symantec para DigiCert, essa URL permanece inalterada*. <br><br> Se esse FQDN estiver incorreto, o Intune Certificate Connector não emitirá Certificados PKCS da AC DigiCert.| 
   | Nome da autoridade de certificação | Symantec | Este valor tem de ser a cadeia **Symantec**. <br><br> Se houver qualquer alteração nesse valor, o Intune Certificate Connector não emitirá Certificados PKCS da AC DigiCert.|
   | Nome do modelo de certificado | OID do perfil de certificado da AC DigiCert. Por exemplo: **2.16.840.1.113733.1.16.1.2.3.1.1.61904612**| Esse valor deve ser um OID de perfil de certificado [obtido na seção anterior](#get-the-certificate-profile-oid) do modelo de perfil de certificado de autoridade de certificação DigiCert. <br><br> Se o Intune Certificate Connector não conseguir localizar um modelo de certificado associado a esse OID do perfil de certificado na AC DigiCert, ele não emitirá Certificados PKCS da AC DigiCert.|  

   ![Seleções para modelo de autoridade de certificação e certificado](./media/certificates-digicert-configure/certificates-digicert-pkcs-example.png)  

   > [!NOTE]
   > O perfil de certificado PKCS para plataformas Windows não precisa ser associado a um perfil de certificado confiável. No entanto, é preciso fazê-lo para perfis de plataformas não Windows como o Android.
7. Conclua a configuração do perfil para atender às suas necessidades de negócios e, em seguida, selecione **OK** para salvar o perfil. 

8. Selecione **atribuições** e configure um grupo apropriado que receberá esse perfil. Pelo menos um utilizador ou dispositivo tem de fazer parte do grupo atribuído.
 
Depois de concluir as etapas anteriores, o Intune Certificate Connector emitirá Certificados PKCS da AC DigiCert para dispositivos gerenciados pelo Intune no grupo atribuído. Esses certificados estarão disponíveis no repositório **pessoal** do repositório de certificados do **usuário atual** no dispositivo gerenciado pelo Intune.

### <a name="supported-attributes-for-the-pkcs-certificate-profile"></a>Atributos com suporte para o perfil de certificado PKCS

|Atributo | Formatos com suporte do Intune | Formatos compatíveis com a AC do DigiCert Cloud | result |
| --- | --- | --- | --- |
| Nome da entidade |O Intune suporta o nome do requerente apenas nos seguintes três formatos: <br><br> 1. nome comum <br> 2. nome comum que inclui email <br> 3. nome comum como email <br><br> Por exemplo: <br><br> `CN = IWUser0 <br><br> E = IWUser0@samplendes.onmicrosoft.com` | A AC DigiCert dá suporte a mais atributos.  Se você quiser selecionar mais atributos, eles deverão ser definidos com valores fixos no modelo de perfil de certificado DigiCert.| Usamos o nome comum ou o email da solicitação de certificado PKCS. <br><br> Qualquer incompatibilidade na seleção de atributo entre o perfil de certificado do Intune e o modelo de perfil de certificado DigiCert resulta em nenhum certificado emitido da AC DigiCert.|
| SAN | O Intune suporta apenas os valores de campo de SAN seguintes: <br><br> **AltNameTypeEmail** <br> **AltNameTypeUpn** <br> **AltNameTypeOtherName** (valor codificado) | A AC de nuvem do DigiCert também dá suporte a esses parâmetros. Se você quiser selecionar mais atributos, eles deverão ser definidos com valores fixos no modelo de perfil de certificado DigiCert. <br><br> **AltNameTypeEmail**: se esse tipo não for encontrado na San, o Intune Certificate Connector usará o valor de **AltNameTypeUpn**.  Se **AltNameTypeUpn** também não for encontrado na San, o Intune Certificate Connector usará o valor do nome da entidade se ele estiver no formato de email.  Se o tipo ainda não for encontrado, o Intune Certificate Connector não emitirá os certificados. <br><br> Exemplo: `RFC822 Name=IWUser0@ndesvenkatb.onmicrosoft.com`  <br><br> **AltNameTypeUpn**: se esse tipo não for encontrado na San, o Intune Certificate Connector usará o valor de **AltNameTypeEmail**. Se **AltNameTypeEmail** também não for encontrado na San, o conector de certificado do Intune usará o valor do nome da entidade se ele estiver no formato de email. Se o tipo ainda não for encontrado, o Intune Certificate Connector não emitirá os certificados.  <br><br> Exemplo: `Other Name: Principal Name=IWUser0@ndesvenkatb.onmicrosoft.com` <br><br> **AltNameTypeOtherName**: se esse tipo não for encontrado na San, o Intune Certificate Connector não emitirá os certificados. <br><br> Exemplo: `Other Name: DS Object Guid=04 12 b8 ba 65 41 f2 d4 07 41 a9 f7 47 08 f3 e4 28 5c ef 2c` <br><br>  Observe que o valor desse campo tem suporte apenas no formato codificado (valor hexadecimal) pela AC DigiCert. Para qualquer valor neste campo, o Intune Certificate Connector converte-o em codificação Base64 antes de enviar a solicitação de certificado. *O Intune Certificate Connector não será validado quer este valor esteja codificado ou não.* | Nenhum |

## <a name="troubleshooting"></a>Resolução de Problemas

Os logs do serviço do conector de certificado do Intune estão disponíveis em **%ProgramFiles%\Microsoft Intune\NDESConnectorSvc\Logs\Logs** no computador do conector NDES. Abra os logs em [SvcTraceViewer](https://docs.microsoft.com/dotnet/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe) e procure exceções ou mensagens de erro.

| Problema/mensagem de erro | Etapas de resolução |
| --- | --- |
| Não é possível entrar com a conta do administrador de locatário do Intune na interface do usuário do conector NDES. | Isso pode acontecer quando o conector de certificado local não está habilitado no portal de administração do Intune. Para resolver esse problema, use um dos seguintes procedimentos: <br><br> Na interface do usuário do Silverlight: <br> 1. entre no portal de [Administração do Intune](https://admin.manage.microsoft.com). <br> 2. Selecione **admin**. <br> 3. Selecione **Gerenciamento de dispositivo móvel** > **conector de certificado**. <br> 4. Selecione **Configurar o conector de certificado local**. <br> 5. Marque a caixa de seleção **habilitar o conector de certificado** . <br> 6. Selecione **OK**. <br><br> Na IU do portal do Azure: <br> 1. entre no [portal do Azure](https://portal.azure.com). <br> 2. vá para Microsoft Intune. <br> 3. Selecione **configuração do dispositivo** > **autoridade de certificação**. <br> 4. Selecione **habilitar**. <br><br> Depois de concluir as etapas anteriores da interface do usuário do Silverlight ou da portal do Azure, tente entrar com a mesma conta do administrador de locatários do Intune na interface do usuário do conector NDES. |
| Não foi possível encontrar o certificado do Conector do NDES. <br><br> System. ArgumentNullException: o valor não pode ser nulo. | O Intune Certificate Connector mostrará este erro se a conta de administrador de inquilino do Intune nunca tiver iniciado sessão na IU do Conector do NDES. <br><br> Se esse erro persistir, reinicie o conector de serviço do Intune. <br><br> 1. abra **Services. msc**. <br> 2. Selecione o **serviço do conector do Intune**. <br> 3. Clique com o botão direito do mouse e selecione **reiniciar**.|
| Conector do NDES – IssuePfx – Exceção Genérica: <br> System.NullReferenceException: a referência do objeto não foi definida para uma instância de um objeto. | Este erro é transitório. Reinicie o conector de serviço do Intune. <br><br> 1. abra **Services. msc**. <br> 2. Selecione o **serviço do conector do Intune**. <br> 3. Clique com o botão direito do mouse e selecione **reiniciar**. |
| Provedor de DigiCert-falha ao obter a política de DigiCert. <br><br>"A operação atingiu o tempo limite." | O Intune Certificate Connector recebeu um erro de tempo limite de operação ao se comunicar com a AC DigiCert. Se esse erro continuar a ocorrer, aumente o valor de tempo limite de conexão e tente novamente. <br><br> Para aumentar o tempo limite da conexão: <br> 1. vá para o computador do conector NDES. <br>2. Abra o arquivo **%ProgramFiles%\Microsoft Intune\NDESConnectorSvc\NDESConnector.exe.config** no bloco de notas. <br> 3. Aumente o valor de tempo limite para o seguinte parâmetro: <br><br> `CloudCAConnTimeoutInMilliseconds` <br><br> 4. Reinicie o serviço do Intune Certificate Connector. <br><br> Se o problema persistir, entre em contato com o suporte ao cliente do DigiCert. |
| Provedor DigiCert-falha ao obter o certificado do cliente. | O Intune Certificate Connector não conseguiu recuperar o certificado de autorização de recursos do repositório de certificados pessoal do computador local. Para resolver esse problema, instale o certificado de autorização de recursos no repositório de certificados pessoais do computador local junto com sua chave privada. <br><br> O certificado de autorização de recursos deve ser obtido da AC DigiCert. Para obter mais detalhes, entre em contato com o suporte ao cliente do DigiCert. | 
| Provedor de DigiCert-falha ao obter a política de DigiCert. <br><br>"A solicitação foi anulada: não foi possível criar o canal seguro de SSL/TLS." | Este erro ocorre nos seguintes cenários: <br><br> 1. o serviço do conector de certificado do Intune não tem permissões para ler o certificado de autorização de recursos junto com sua chave privada do repositório de certificados pessoais do computador local. Para resolver esse problema, verifique a conta de contexto em execução do serviço do conector em Services. msc. O serviço do conector deve ser executado no contexto NT AUTHORITY\SYSTEM. <br><br> 2. o perfil de certificado PKCS no portal de administração do Intune pode ser configurado com um FQDN de serviço base inválido para a AC DigiCert. O FQDN é semelhante a **PKI-WS.symauth.com**. Para resolver esse problema, verifique com o suporte ao cliente do DigiCert se a URL está correta para sua assinatura. <br><br> 3. o Intune Certificate Connector não consegue se autenticar com a AC DigiCert por meio do certificado de autorização de recursos porque não consegue recuperar a chave privada. Para resolver esse problema, instale o certificado de autorização de recursos junto com sua chave privada no repositório de certificados pessoais do computador local. <br><br> Se o problema persistir, entre em contato com o suporte ao cliente do DigiCert. |
| Provedor de DigiCert-falha ao obter a política de DigiCert. <br><br>"Um elemento de solicitação não é compreendido". | O Intune Certificate Connector não conseguiu obter o modelo de perfil de certificado DigiCert, pois o OID do perfil do cliente não corresponde ao perfil de certificado do Intune. Em outro caso, o Intune Certificate Connector não consegue localizar o modelo de perfil de certificado associado ao OID do perfil do cliente na autoridade de certificação DigiCert. <br><br> Para resolver esse problema, obtenha o OID do perfil de cliente correto do modelo de certificado DigiCert na AC DigiCert. Em seguida, atualize o perfil de certificado PKCS no portal de administração do Intune. <br><br> Obtenha o OID do perfil de cliente da AC DigiCert: <br> 1. entre no portal de administração de AC do DigiCert. <br> 2. Selecione **gerenciar perfis de certificado**. <br> 3. Selecione o perfil de certificado que você deseja usar. <br> 4. Obtenha o OID do perfil de certificado. É semelhante ao seguinte exemplo: <br> `Certificate Profile OID = 2.16.840.1.113733.1.16.1.2.3.1.1.47196109` <br><br> Atualize o perfil de certificado PKCS com o OID do perfil de certificado correto: <br>1. entre no portal de administração do Intune. <br> 2. vá para o perfil de certificado PKCS e selecione **Editar**. <br> 3. atualize o OID do perfil de certificado no campo para o nome do modelo de certificado. <br> 4. Salve o perfil de certificado PKCS. |
| Provedor DigiCert-falha na verificação de política. <br><br> O atributo não se enquadra na lista de atributos do modelo de certificado com suporte DigiCert. | A AC DigiCert mostra essa mensagem quando há uma discrepância entre o modelo de perfil de certificado DigiCert e o perfil de certificado do Intune. Esse problema provavelmente aconteceu devido à incompatibilidade de atributo em **SubjectName** ou **SubjectAltName**. <br><br> Para resolver esse problema, selecione os atributos com suporte do Intune para **SubjectName** e **SubjectAltName** no modelo de perfil de certificado DigiCert. Para obter mais informações, consulte os atributos com suporte do Intune na seção **parâmetros de certificado** . |
| Alguns dispositivos de usuário não estão recebendo Certificados PKCS da AC DigiCert. | Esse problema ocorre quando o UPN do usuário contém caracteres especiais, como um sublinhado (exemplo: `global_admin@intune.onmicrosoft.com`). <br><br> A AC DigiCert não dá suporte a caracteres especiais em **mail_firstname** e **mail_lastname**. <br><br> Os passos seguintes ajudam a resolver este problema: <br><br> 1. entre no portal de administração de AC do DigiCert. <br> 2. vá para **gerenciar perfis de certificado**. <br> 3. Selecione o perfil de certificado usado para o Intune. <br> 4. Selecione o link **Personalizar opções** . <br> 5. Selecione o botão **Opções avançadas** . <br> 6. em **campos de certificado – DN de assunto**, adicione um campo de **nome comum (CN)** e exclua o campo **CN (nome comum)** existente. As operações de adição e exclusão devem ser executadas juntas. <br> 7. Selecione **salvar**. <br><br> Com a alteração anterior, o perfil de certificado DigiCert solicita **"CN = <upn>"** em vez de **mail_firstname** e **mail_lastname**. |
| O utilizador eliminado manualmente já implementou o certificado do dispositivo. | O Intune reimplanta o mesmo certificado durante o próximo check-in ou imposição de políticas. Nesse caso, o conector NDES não recebe uma solicitação de certificado PKCS. |

## <a name="next-steps"></a>Próximos passos

Use as informações neste artigo além das informações em [o que são Microsoft Intune perfis de dispositivo?](../configuration/device-profiles.md) para gerenciar os dispositivos de sua organização e os certificados neles.

