---
title: Emitir certificados Symantec PKCS com o Microsoft Intune
titleSuffix: ''
description: Instale e configure o Intune Certificate Connector para emitir certificados PKCS a partir do Serviço Web Symantec PKI Manager para dispositivos geridos pelo Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/22/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: da57b14f8196251ee8c77de3ffcd48f5b586a12f
ms.sourcegitcommit: 1cae690ca2ac6cc97bbcdf656f54b31878297ae8
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/22/2019
ms.locfileid: "59900048"
---
# <a name="set-up-intune-certificate-connector-for-symantec-pki-manager-web-service"></a>Configurar o Intune Certificate Connector para o Serviço Web Symantec PKI Manager

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Este artigo mostra como instalar e configurar o Intune Certificate Connector para emitir Certificados PKCS a partir de um Serviço Web Symantec PKI Manager para dispositivos geridos pelo Intune.

O Serviço Web Symantec PKI Manager é referido como AC da Symantec ao longo deste artigo. Se já tiver configurado o Intune Certificate Connector para emitir Certificados PKCS e Certificados SCEP da Autoridade de Certificação (AC) da Microsoft, poderá utilizar o mesmo Conector para configurar e emitir Certificados PKCS a partir de uma AC da Symantec. Neste caso, o Intune Certificate Connector pode emitir os seguintes certificados:

* Certificados PKCS de uma AC da Microsoft
* Certificados SCEP de uma AC da Microsoft
* Certificados PKCS de uma AC da Symantec

Se quiser utilizar o Intune Certificate Connector para a AC da Microsoft e a AC da Symantec, tem de concluir primeiro a configuração do Intune Certificate Connector para a AC da Microsoft e seguir estes passos para o configurar para a AC da Symantec.  Para obter mais detalhes sobre como configurar o Intune Certificate Connector para uma AC da Microsoft, veja [Como configurar certificados no Microsoft Intune](certificates-configure.md).

## <a name="prepare-to-install-intune-certificate-connector"></a>Preparar-se para instalar o Intune Certificate Connector

Se já estiver a utilizar o Intune Certificate Connector para uma AC da Microsoft existente e quiser adicionar o suporte de ACs da Symantec, ignore este passo e continue os restantes passos depois de instalar o Intune Certificate Connector mais recente a partir do Portal de administração do Intune. Este passo serve apenas quando quiser utilizar o Intune Certificate Connector para uma AC da Symantec autónoma.

1. Escolha uma das versões do Sistema Operativo Windows na seguinte lista e instale-a num computador:
   * Windows Server 2012 R2 Datacenter
   * Windows Server 2012 R2 Standard
   * Windows Server 2016 Datacenter
   * Windows Server 2016 Standard

2. Crie um utilizador com privilégios administrativos e utilize-o para realizar os passos seguintes.

3. Obtenha e instale as Atualizações do Windows mais recentes e instale-as, se estiverem disponíveis.

   > [!IMPORTANT]
   > Depois de instalar as Atualizações do Windows, reinicie o computador.

4. Instale o .NET Framework 3.5:

    a. Abra o **Painel de Controlo** > **Programas e Funcionalidades** > **Ativar ou desativar funcionalidades do Windows**.

    b. Selecione o **.NET Framework 3.5** e instale-o.

## <a name="install-the-symantec-registration-authorization-certificate"></a>Instalar o Certificado de Autorização de Registo da Symantec

Utilize os seguintes passos para obter o certificado de Autoridade de Registo (AR) da AC da Symantec. Tem de ter uma subscrição ativa na AC da Symantec para obter o certificado de RA.

1. Guarde o seguinte fragmento de código num ficheiro denominado **certreq.ini** e atualize conforme necessário (por exemplo: *Nome do requerente no formato CN*).

   ```
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
   ```

2. Abra uma linha de comandos elevada e gere o conteúdo CSR através do seguinte comando:

   `Certreq.exe -new certreq.ini request.csr`

3. Abra o ficheiro request.csr no Bloco de notas e copie o conteúdo CSR no seguinte formato:

    ```
    -----BEGIN NEW CERTIFICATE REQUEST-----
    MIID8TCCAtkCAQAwbTEMMAoGA1UEBhMDVVNBMQswCQYDVQQIDAJXQTEQMA4GA1UE
    …
    …
    fzpeAWo=
    -----END NEW CERTIFICATE REQUEST-----
    ```

4. Inicie sessão na AC da Symantec e navegue para **Obter um Certificado de RA** a partir das tarefas.

   a. Forneça o conteúdo CSR do Passo 3 na caixa de texto designada.

   b. Indique o Nome Amigável do Certificado na caixa de texto designada.

   c. Clique em **Continuar**.

      Esta ação mostra-lhe uma ligação transferível do Certificado de RA.

   d. Transfira o certificado de RA para o computador local.

5. Importe o Certificado de RA para o arquivo de Certificados do Windows:

    a. Abra uma consola MMC.

    b. Clique em **Ficheiro** > **Adicionar ou Remover Snap-ins** > **Certificado** > e clique em **Adicionar**.

    c. Selecione **Conta de Computador** > e clique em **Seguinte**.

    d. Selecione **Computador Local** > e clique em **Concluir**.

    e. Clique em **OK**, na janela **Adicionar ou Remover Snap-ins**. Expanda **Certificados (Computador Local)** > **Pessoal** > **Certificados**.

    f. Clique com o botão direito do rato no nó **Certificados** e selecione **Todas as Tarefas** > **Importar**.

    g. Selecione a localização do Certificado de RA que transferiu da AC da Symantec e clique em **Seguinte**.

    h. Selecione **Arquivo de Certificados Pessoais** e clique em **Seguinte**.

    i. Clique em **Concluir**. Esta ação importa o Certificado de RA para o arquivo Pessoal do Computador Local, juntamente com a chave privada.  

6. Exporte e importe o certificado de chave privada:

    a. Expanda **Certificados (Computador Local)** > **Pessoal** > **Certificados**.

    b. Selecione o certificado importado no passo anterior.

    c. Clique com o botão direito do rato e escolha **Todas as Tarefas** > **Exportar**.

    d. Clique em **Seguinte** e escreva a palavra-passe.

    e. Selecione a localização para onde exportar e clique em **Concluir**.

    f. Siga o mesmo procedimento no Passo 5 para importar o certificado de chave privada para o arquivo Pessoal do Computador Local.

7. Copie o thumbprint do Certificado de RA sem quaisquer espaços.  Exemplo de um thumbprint:

   ```
   RA Cert Thumbprint: “EA7A4E0CD1A4F81CF0740527C31A57F6020C17C5”
   ```


   > [!NOTE]
   > Se houver algum problema ao obter o Certificado de RA da AC da Symantec, contacte o Suporte técnico da Symantec.

## <a name="install-intune-certificate-connector"></a>Instalar o Intune Certificate Connector

Se já estiver a utilizar o Intune Certificate Connector mais recente para uma AC da Microsoft existente e quiser adicionar o suporte de ACs da Symantec, ignore este passo. Caso contrário, transfira o Intune Certificate Connector mais recente a partir do portal de administração do Intune e siga estas instruções.

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços** > **Intune**. O Intune encontra-se na secção **Monitorização + Gestão**.
3. No painel **Intune**, selecione **Configuração do dispositivo**.
4. No painel **Configuração do dispositivo**, selecione **Autoridade de Certificação**.
5. Clique em **Adicionar** e selecione **Transferir o ficheiro de conector**. Guarde a transferência numa localização a que possa aceder a partir do servidor onde irá instalá-la. 
3. Execute o NDESConnectorSetup.exe com privilégios elevados.

    a. No ecrã **Opções de Instalação**, selecione **PFX Distribution**, conforme mostrado na seguinte captura de ecrã.  Conclua a restante configuração com as seleções predefinidas.

   > [!IMPORTANT]
   > Se quiser configurar o Intune Certificate Connector para emitir certificados a partir de uma AC da Microsoft e de uma AC da Symantec, selecione **SCEP e PFX Profile Distribution**. Conclua a restante configuração com as seleções predefinidas.

   ![InstallConnector][InstallConnector]
 
## <a name="configure-intune-certificate-connector"></a>Configurar o Intune Certificate Connector

Por predefinição, o Intune Certificate Connector é instalado em `%ProgramFiles%\Microsoft Intune`.

1. Abra o ficheiro %ProgramFiles%\Microsoft Intune\NDESConnectorSvc\NDESConnector.exe.config no Bloco de notas.

    a. Atualize o valor da chave RACertThumbprint com o valor do thumbprint de certificado que copiou na secção anterior.  Exemplo:

   ```
   <add key="RACertThumbprint"
   value="EA7A4E0CD1A4F81CF0740527C31A57F6020C17C5"/>
   ```

    b. Guarde e feche o ficheiro.

2. Abra o services.msc.

    a. Selecione **Intune Connector Service**.

    b. Pare o serviço e, em seguida, inicie-o.

    c. Feche a janela Serviços.

## <a name="setup-the-intune-administrator-account"></a>Configurar a conta de administrador do Intune

Se já estiver a utilizar o Intune Certificate Connector para uma AC da Microsoft existente e quiser adicionar o suporte de ACs da Symantec, ignore este passo e continue com os passos restantes. 

1. Iniciar a interface de utilizador do Conector do NDES a partir de ` %ProgramFiles%\Microsoft Intune\NDESConnectorUI\NDESConnectorUI.exe `

    a. Clique no separador **Inscrição** e, em seguida, em **Iniciar Sessão**.

    b. Indique as credenciais de administrador de inquilino do Intune nas caixas de texto designadas.

    c. Clique em **Iniciar Sessão**.  Será apresentada uma caixa de diálogo de confirmação com a mensagem **Inscrito com êxito**, conforme mostrado na captura de ecrã seguinte.
2. Feche a interface de utilizador do Conector do NDES.

![ConfigureConnector][ConfigureConnector]
 
## <a name="create-a-trusted-certificate-profile"></a>Criar um Perfil de Certificado Fidedigno

Os Certificados PKCS implementados nos dispositivos geridos do Intune têm de estar ligados com um Certificado de Raiz Fidedigna. Para o fazer, é preciso criar um Perfil de Certificado Fidedigno do Intune com o certificado de raiz obtido da AC da Symantec.

1. Obter um Certificado de Raiz Fidedigna da AC da Symantec:

    a. Inicie sessão no Portal de administração da AC da Symantec.

    b. Clique em Gerir ACs em Tarefas:

    c. Selecione a AC adequada na lista de ACs.

    d. Clique em Transferir o certificado de raiz para transferir o Certificado de Raiz Fidedigna.

2. Crie um Perfil de Certificado Fidedigno no portal de administração do Intune:

    a. Inicie sessão no [portal do Azure](https://portal.azure.com) com as credenciais de administrador de inquilino do Intune e pesquise os recursos do Intune.

    b. Crie um perfil de Certificado Fidedigno em **Microsoft Intune** > **Configuração do dispositivo** > **Perfis** > **Criar perfil**.

    c. Indique as informações necessárias nos campos **Nome** e **Descrição** e, em seguida, selecione a plataforma de destino. 

    d. Selecione o perfil de certificado fidedigno da lista pendente Tipo de perfil.

    e. Carregue o Certificado de Raiz Fidedigna que obteve da AC da Symantec no passo anterior.

    f. Conclua os passos restantes na criação do perfil. 

    g. Clique em **Atribuições** e selecione o grupo adequado.  Pelo menos um utilizador ou dispositivo tem de fazer parte do grupo atribuído.

## <a name="get-the-certificate-profile-oid"></a>Obter o OID do Perfil de Certificado

O OID do Perfil de Certificado está associado a um modelo de Perfil de Certificado na AC da Symantec.  Para criar um perfil de Certificado PKCS no portal de administração do Intune, o nome do modelo do certificado tem de ser indicado no formato de um OID do Perfil de Certificado associado a um modelo de Certificado na AC da Symantec.

1. Inicie sessão no Portal de administração da AC da Symantec.
2. Clique em Gerir Perfis de Certificado.
3. Selecione o Perfil de Certificado que quer utilizar.
4. Copie o OID do Perfil de Certificado. É semelhante ao seguinte exemplo:

   ```
   Certificate Profile OID = 2.16.840.1.113733.1.16.1.2.3.1.1.47196109 
   ```

   > [!NOTE]
   > Se existirem quaisquer problemas ao obter o OID do Perfil de Certificado, contacte o Suporte ao Cliente da Symantec.

## <a name="create-a-pkcs-certificate-profile"></a>Criar um Perfil de Certificado PKCS

1. Inicie sessão no [portal do Azure](https://portal.azure.com) com as credenciais de administrador de inquilino do Intune e pesquise os recursos do Intune.
2. Crie um perfil de Certificado PKCS em **Microsoft Intune** > **Configuração do dispositivo > Perfis** > **Criar perfil**.

    a. Indique as informações necessárias nos campos **Nome** e **Descrição** e, em seguida, selecione a plataforma de destino.

    b. Selecione o **Perfil de certificado PKCS** na lista pendente **Tipo de perfil**.  

    c. Conclua os passos restantes para criar o perfil.

   ![ConfigureProfile][ConfigureProfile]

   > [!IMPORTANT]
   > Os seguintes parâmetros do Perfil de Certificado PKCS têm de ser configurados com os valores especificados na tabela seguinte, conforme mostrado na captura de ecrã para emitir Certificados PKCS através do Intune Certificate Connector da AC da Symantec. 

    |Parâmetro de Certificado PKCS | Valor | Descrição |
    | --- | --- | --- |
    | Autoridade de certificação | pki-ws.symauth.com | Este valor tem de ser o FQDN de serviço base da AC da Symantec sem barras à direita.  Se não tiver a certeza se este é o FQDN de serviço base correto para a sua subscrição da AC da Symantec, contacte o Suporte ao cliente da Symantec. <br><br> Se este FQDN estiver incorreto, o Intune Certificate Connector não emitirá Certificados PKCS da AC da Symantec.| 
    | Nome da autoridade de certificação | Symantec | Este valor tem de ser a cadeia **Symantec**. <br><br> Se este valor for alterado, o Intune Certificate Connector não emitirá Certificados PKCS da AC da Symantec.|
    | Nome do modelo de certificado | OID do Perfil de Certificado da AC da Symantec. <br><br> Por exemplo: `2.16.840.1.113733.1.16.1.2.3.1.1.61904612`| Este valor tem de ser um OID do Perfil de Certificado obtido na secção anterior do modelo de Perfil de Certificado da AC da Symantec. <br><br> Se o Intune Certificate Connector não conseguir localizar um modelo de certificado associado a este OID do Perfil de Certificado na AC da Symantec, não emitirá certificados PKCS da AC da Symantec.|

   > [!NOTE]
   > Os perfis de Certificado PKCS para plataformas Windows não têm de associar um perfil de Certificado Fidedigno. No entanto, é preciso fazê-lo para perfis de plataformas não Windows como o Android.

3. Clique em **Atribuições** e selecione o grupo adequado.  Pelo menos um utilizador ou dispositivo tem de fazer parte do grupo atribuído.
 
Depois de concluir os passos anteriores, o Intune Certificate Connector emitirá Certificados PKCS da AC da Symantec para dispositivos geridos pelo Intune no grupo atribuído. Estes certificados estarão disponíveis no arquivo Pessoal do arquivo de certificados do Utilizador Atual no dispositivo gerido pelo Intune.

### <a name="pkcs-certificate-profile-supported-attributes"></a>Atributos suportados pelo Perfil de Certificado PKCS

|Atributo | Formatos Suportados pelo Intune | Formatos Suportados pela AC da Symantec Cloud | Resultado |
| --- | --- | --- | --- |
| Nome do Requerente |O Intune suporta o nome do requerente apenas nos seguintes três formatos: <br><br> 1. Nome Comum <br> 2. Nome Comum, incluindo o e-mail <br> 3. Nome Comum como e-mail <br><br> Exemplo: <br><br> `CN = IWUser0 <br><br> E = IWUser0@samplendes.onmicrosoft.com` | A AC da Symantec suporta atributos adicionais.  Se quiser selecionar atributos adicionais, estes terão de ser definidos com valores fixos no modelo de Perfil de Certificado da Symantec.| Utilizamos o Nome Comum ou o e-mail no pedido de Certificado PKCS. <br><br> Qualquer erro de correspondência na seleção de atributos entre o Perfil de Certificado do Intune e o modelo de Perfil de Certificado da Symantec resultará na não emissão de certificados emitidos a partir da AC da Symantec.|
| SAN | O Intune suporta apenas os valores de campo de SAN seguintes: <br><br> AltNameTypeEmail <br><br> AltNameTypeUpn <br><br> AltNameTypeOtherName (valor codificado) | A AC da Symantec Cloud também suporta estes parâmetros. Se quiser selecionar atributos adicionais, estes terão de ser definidos com valores fixos no modelo de Perfil de Certificado da Symantec. <br><br> AltNameTypeEmail: se este tipo não se encontrar no SAN, utilizará o valor de AltNameTypeUpn.  Se AltNameTypeUpn também não for encontrado no SAN, utilizará o valor do Nome do Requerente, caso esteja no formato de e-mail.  Se continuar a não ser encontrado, o Intune Certificate Connector não conseguirá emitir os certificados. <br><br> Por exemplo: `RFC822 Name=IWUser0@ndesvenkatb.onmicrosoft.com`  <br><br> AltNameTypeUpn: se este tipo não se encontrar no SAN, utilizará o valor de AltNameTypeEmail. Se AltNameTypeEmail também não for encontrado no SAN, utilizará o valor do Nome do Requerente, caso esteja no formato de e-mail.  Se continuar a não ser encontrado, o Intune Certificate Connector não conseguirá emitir os certificados.  <br><br> Por exemplo: `Other Name: Principal Name=IWUser0@ndesvenkatb.onmicrosoft.com` <br><br> AltNameTypeOtherName: se este tipo não se encontrar no SAN, o Intune Certificate Connector não conseguirá emitir os certificados. <br><br> Por exemplo: `Other Name: DS Object Guid=04 12 b8 ba 65 41 f2 d4 07 41 a9 f7 47 08 f3 e4 28 5c ef 2c` <br><br>  **Nota Importante:** o valor deste campo é apenas suportado no formato codificado (valor hexadecimal) pela AC da Symantec. Por isso, para qualquer valor neste campo, o Intune Certificate Connector converte-o para a base 64 codificada antes de enviar o pedido de certificado. **O Intune Certificate Connector não será validado quer este valor esteja codificado ou não.** | Nenhum |

## <a name="troubleshooting"></a>Resolução de Problemas

Estão disponíveis registos do Serviço do Intune Certificate Connector em `%ProgramFiles%\Microsoft Intune\NDESConnectorSvc\Logs\Logs` no computador do Conector do NDES. Abra os registos no [SvcTraceViewer](https://docs.microsoft.com/dotnet/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe) e procure mensagens de erro ou de exceção.

| Mensagem de Erro/Problema | Passos de resolução |
| --- | --- |
| Não é possível Iniciar sessão com a conta de administrador de inquilino do Intune na IU do Conector do NDES | Este problema pode ocorrer quando o Certificate Connector no local não está ativado no portal de administração do Intune. Para resolver este problema, execute os seguintes passos: <br><br> Na IU do SilverLight: <br> 1. Inicie sessão no [portal de administração do Intune](https://admin.manage.microsoft.com) <br> 2. Clique em ADMIN <br> 3. Selecione Gestão de Dispositivos Móveis > Certificate Connector <br> 4. Clique em **Configurar Certificate Connector no Local** <br> 5. Selecione a caixa de verificação **Ativar Certificate Connector** <br> 6. Clique em **OK**. <br><br>Ou <br><br> Na IU do portal do Azure: <br> 1. Inicie sessão no [portal do Azure](https://portal.azure.com) <br> 2. Aceda ao Microsoft Intune <br> 3. Selecione **Configuração do Dispositivo** > **Autoridade de Certificação** <br> 4. Clique em **Ativar**. <br><br> Depois de concluir os passos anteriores da IU do Silverlight ou do portal do Azure, tente iniciar sessão com a mesma conta de administrador de inquilino do Intune na IU do Conector do NDES. |
| Não foi possível encontrar o certificado do Conector do NDES. <br><br> System.ArgumentNullException: o valor não pode ser nulo. | O Intune Certificate Connector mostrará este erro se a conta de administrador de inquilino do Intune nunca tiver iniciado sessão na IU do Conector do NDES. <br><br> Se este erro persistir, reinicie o Intune Service Connector. <br><br> 1. Abra o services.msc <br> 2. Selecione **Intune Connector Service**. <br> 3. Clique com o botão direito do rato e selecione **Reiniciar**.|
| Conector do NDES – IssuePfx – Exceção Genérica: <br> System.NullReferenceException: a referência do objeto não foi definida para uma instância de um objeto. | Este erro é transitório. Reinicie o Intune Service Connector. <br><br> 1. Abra o services.msc <br> 2. Selecione o **Intune Connector Service** <br> 3. Clique com o botão direito do rato e selecione **Reiniciar**. |
| Fornecedor da Symantec – Falha ao obter a política da Symantec “A operação excedeu o tempo limite” | O Intune Certificate Connector recebeu o erro de tempo limite excedido da operação ao comunicar com a AC da Symantec. Se este erro continuar a ocorrer, aumente o valor de tempo limite da ligação e tente novamente. <br><br> Para aumentar tempo limite de ligação: <br> 1. Aceda ao computador do Conector do NDES. <br>2. Abra o ficheiro `%ProgramFiles%\Microsoft Intune\NDESConnectorSvc\NDESConnector.exe.config` no Bloco de Notas. <br> 3. Aumente o valor de tempo limite do seguinte parâmetro: <br><br> `CloudCAConnTimeoutInMilliseconds` <br><br> 4. Reinicie o Intune Connector Service. <br><br> Se o problema persistir, contacte o suporte ao cliente da Symantec. |
| Fornecedor da Symantec – Falha ao obter o certificado de cliente | O Intune Certificate Connector não conseguiu obter o Certificado de Autorização do Recurso do arquivo de certificados Pessoal do Computador Local. Para resolver este problema, verifique se instala o Certificado de Autorização do Recurso no arquivo de certificados Pessoal do Computador Local, juntamente com a chave privada. <br><br> **Nota:** o Certificado de autorização do Recurso deve ser obtido a partir da AC da Symantec. Para obter mais detalhes, contacte o suporte ao cliente da Symantec. | 
| Fornecedor da Symantec – Falha ao obter a política da Symantec “Pedido abortado: não foi possível criar um canal seguro SSL/TLS.” | Este erro ocorre nos seguintes cenários: <br><br> 1. O serviço do Intune Certificate Connector não tem permissões suficientes para ler o certificado de Autorização do Recurso, juntamente com a chave privada do arquivo de certificados Pessoal do Computador Local. Para resolver este problema, verifique a conta de contexto em execução no serviço Connector no services.msc. O serviço Connector tem de ser executado no contexto NT AUTHORITY\SYSTEM. <br><br> 2. O perfil de Certificados PKCS no portal de administração do Intune pode ser configurado com um FQDN de serviço base da AC da Symantec inválido. O FQDN é semelhante a `pki-ws.symauth.com`. Para resolver este problema, contacte o suporte ao cliente da Symantec para saber se o URL está correto para a sua subscrição. <br><br> 3. O Intune Certificate Connector não consegue autenticar com a AC da Symantec com o certificado de Autorização do Recurso porque não consegue obter a chave privada. Para resolver este problema, verifique se instala o certificado de Autorização do Recurso no arquivo de certificados Pessoal do Computador Local, juntamente com a chave privada. <br><br> Se o problema persistir, contacte o suporte ao cliente da Symantec. |
| Fornecedor da Symantec – Falha ao obter a política da Symantec “Um elemento de pedido não foi compreendido”. | O Intune Certificate Connector não conseguiu obter o modelo do Perfil de Certificado da Symantec, porque o OID do Perfil de Cliente não corresponde ao Perfil de Certificado do Intune. Noutro caso, o Intune Certificate Connector não consegue localizar o modelo de perfil de certificado associado ao OID do Perfil de Cliente especificado na AC da Symantec. <br><br> Para resolver este problema, verifique se obtém o OID do Perfil de Cliente correto a partir do modelo de Certificado da Symantec na AC da Symantec. Em seguida, atualize o perfil do Certificado PKCS no portal de administração do Intune. <br><br> Obtenha o OID do Perfil de Cliente da AC da Symantec: <br> 1. Inicie sessão no Portal de administração da AC da Symantec. <br> 2. Clique em Gerir Perfis de Certificado. <br> 3. Selecione o Perfil de Certificado que quer utilizar. <br> 4. Obtenha o OID do Perfil de Certificado. É semelhante ao seguinte exemplo: <br> `Certificate Profile OID = 2.16.840.1.113733.1.16.1.2.3.1.1.47196109` <br><br> Atualize o Perfil de Certificado PKCS com o OID do Perfil de Certificado correto: <br>1. Inicie sessão no portal de administração do Intune. <br> 2. Aceda ao Perfil de Certificado PKCS e clique em **Editar**. <br> 3. Atualize o OID do Perfil de Certificado na atualização no campo de nome do Modelo de Certificado. <br> 4. Guarde o Perfil de Certificado PKCS. |
| Fornecedor da Symantec – Falha na Verificação da Política. <br><br> O atributo não se enquadra na lista de atributos do modelo de Certificado suportados | A AC da Symantec mostra esta mensagem quando há discrepância entre o modelo de Perfil de Certificado da Symantec e o Perfil de Certificado do Intune. É provável que este problema tenha ocorrido devido a um erro de correspondência de atributos em SubjectName ou SubjectAltName. <br><br> Para resolver este problema, verifique se seleciona os atributos suportados pelo Intune para SubjectName e SubjectAltName no modelo de Perfil de Certificado da Symantec. Para obter mais informações, veja os Atributos suportados pelo Intune na secção Parâmetros de Certificado. |
| Alguns Dispositivos do utilizador não estão a receber certificados PKCS da AC da Symantec. | Este problema ocorre quando o UPN do Utilizador contém carateres especiais, como um caráter de sublinhado (por exemplo: `global_admin@intune.onmicrosoft.com`). <br><br> A AC da Symantec não suporta carateres especiais em mail_firstname e mail_lastname. <br><br> Os passos seguintes ajudam a resolver este problema: <br><br> 1.   Inicie sessão no Portal de administração da AC da Symantec. <br> 2. Aceda a Gerir Perfis de Certificado. <br> 3.   Clique no Perfil de Certificado utilizado para o Intune. <br> 4.  Clique na ligação Personalizar opções. <br> 5.   Clique no botão Opções avançadas. <br> 6.  Nos campos do Certificado – DN do Requerente, adicione o campo Nome Comum (CN) e elimine o campo Nome Comum (CN) existente. A adição e a eliminação têm de ser realizadas em conjunto. <br> 7.    Clique em Guardar. <br><br> Com a alteração anterior, o perfil de Certificado da Symantec solicita “CN =<upn>” em vez de mail_firstname e mail_lastname. |
| O utilizador eliminado manualmente já implementou o certificado do dispositivo. | O Intune reimplementa o mesmo certificado durante o próximo registo ou imposição de políticas. Neste caso, o Conector do NDES não recebe um pedido de Certificado PKCS. |

## <a name="next-steps"></a>Próximos passos

- Utilize as informações fornecidas neste artigo, além das informações em [O que são os perfis de dispositivos do Microsoft Intune?](device-profiles.md) para gerir os dispositivos da sua organização e os certificados nos mesmos.

[InstallConnector]:  ./media/certificates-symantec-connector-install.png "Instalar o Intune Certificate Connector e selecionar PFX Distribution"
[ConfigureConnector]: ./media/certificates-symantec-configure-connector-configure.png "Configurar o Intune Certificate Connector"
[ConfigureProfile]: ./media/certificates-symantec-pkcs-example.png "Criar o perfil de certificado PKCS no portal do Azure"
