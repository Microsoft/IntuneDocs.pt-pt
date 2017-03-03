---
title: Configurar a infraestrutura de certificados para SCEP
titleSuffix: Intune Azure preview
description: "Pré-visualização do Azure no Intune: saiba como configurar a sua infraestrutura antes de criar e implementar perfis de certificado SCEP no Intune."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d567d85f-e4ee-458e-bef7-6e275467efce
ms.reviewer: kmyrup
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: 8f713769e0b8a13e91e6d9991e4e7415e1da22a2
ms.lasthandoff: 02/18/2017

---
# <a name="configure-certificate-infrastructure-for-scep-in-microsoft-intune"></a>Configurar a infraestrutura de certificados para SCEP no Microsoft Intune
[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Este tópico descreve a infraestrutura necessária para criar e implementar perfis de certificado SCEP.

### <a name="on-premises-infrastructure"></a>Infraestrutura no local

-    **Domínio do Active Directory**: todos os servidores indicados nesta secção (exceto o Servidor Proxy de Aplicações Web) têm de ser associados ao seu domínio do Active Directory.

-  **Autoridade de Certificação** (AC): uma Autoridade de Certificação (AC) Empresarial que seja executada numa edição Enterprise do Windows Server 2008 R2 ou posterior. Não é suportada uma AC Autónoma. Para obter instruções sobre como configurar uma Autoridade de Certificação, consulte [Instalar a Autoridade de Certificação](http://technet.microsoft.com/library/jj125375.aspx).
    Se a sua AC for executada no Windows Server 2008 R2, tem de [instalar a correção de KB2483564](http://support.microsoft.com/kb/2483564/).

-  **Servidor do NDES**: num servidor com o Windows Server 2012 R2 ou posterior, tem de configurar o Serviço de Inscrição de Dispositivos de Rede (NDES). O Intune não suporta a utilização do NDES quando este é executado num servidor que também execute a AC Empresarial. Consulte a [Documentação de Orientação do Serviço de Inscrição de Dispositivos de Rede](http://technet.microsoft.com/library/hh831498.aspx) para obter instruções sobre como configurar o Windows Server 2012 R2 para alojar o Serviço de Inscrição de Dispositivos de Rede. O servidor do NDES tem de estar associado ao domínio que aloja a AC e não pode estar no mesmo servidor da AC. Estão disponíveis mais informações sobre a implementação do servidor do NDES numa floresta separada, numa rede isolada ou num domínio interno em [Utilizar um Módulo de Política com o Serviço de Inscrição de Dispositivos de Rede](https://technet.microsoft.com/en-us/library/dn473016.aspx).

-  **Microsoft Intune Certificate Connector**: utilize a consola de administração do Intune para transferir o instalador do **Certificate Connector** (**ndesconnectorssetup.exe**). Em seguida, pode executar **ndesconnectorssetup.exe** no computador onde pretende instalar o Certificate Connector.
-  **Servidor Proxy de Aplicações Web** (opcional): pode utilizar um servidor com o Windows Server 2012 R2 ou posterior como um servidor Proxy de Aplicações Web (WAP). Esta configuração:
    -  Permite aos dispositivos receberem certificados através de uma ligação à Internet.
    -  É uma recomendação de segurança quando os dispositivos se ligam através da Internet para receber e renovar certificados.

 > [!NOTE]           
> -    O servidor que aloja o WAP [tem de instalar uma atualização](http://blogs.technet.com/b/ems/archive/2014/12/11/hotfix-large-uri-request-in-web-application-proxy-on-windows-server-2012-r2.aspx) que ativa o suporte para os URLs longos que são utilizados pelo Serviço de Inscrição de Dispositivos de Rede. Esta atualização está incluída no [rollup da atualização de dezembro de 2014](http://support.microsoft.com/kb/3013769)ou individualmente a partir do [KB3011135](http://support.microsoft.com/kb/3011135).
>-  Além disso, o servidor que aloja o WAP tem de ter um certificado SSL que corresponda ao nome que está a ser publicado em clientes externos, e tem de confiar no certificado SSL utilizado no servidor do NDES. Estes certificados permitem ao servidor do WAP terminar a ligação SSL de clientes e criar uma nova ligação SSL ao servidor do NDES.
    Para obter informações sobre certificados para o WAP, consulte a secção **Planear os certificados** do artigo [Planear a Publicação de Aplicações Através do Proxy de Aplicações Web](https://technet.microsoft.com/library/dn383650.aspx). Para obter informações gerais sobre os servidores WAP, veja [Trabalhar com o Proxy da Aplicação Web](http://technet.microsoft.com/library/dn584113.aspx).|

### <a name="network-requirements"></a>Requisitos de rede

Da Internet para a rede de perímetro, dê permissão à porta 443 a partir de todos os anfitriões/endereços IP na Internet para o servidor NDES.

A partir da rede de perímetro para uma rede fidedigna, permita todas as portas e protocolos necessários para acesso ao domínio do servidor do NDES associado a um domínio. O servidor do NDES precisa de acesso aos servidores de certificado, aos servidores DNS, aos servidores do Configuration Manager e aos controladores de domínio.

Recomendamos a publicação do servidor NDES através de um proxy, tal como o [proxy de aplicações do Azure AD](https://azure.microsoft.com/en-us/documentation/articles/active-directory-application-proxy-publish/), [Proxy de Acesso Web](https://technet.microsoft.com/en-us/library/dn584107.aspx) ou um proxy de terceiros.


### <a name="a-namebkmkcertsandtemplatesacertificates-and-templates"></a><a name="BKMK_CertsAndTemplates"></a>Certificados e Modelos

|Objeto|Detalhes|
|----------|-----------|
|**Modelo de Certificado**|Configura este modelo na sua AC emissora.|
|**Certificado de autenticação de cliente**|Pedido pela sua AC emissora ou AC pública, instala este certificado no Servidor do NDES.|
|**Certificado de autenticação do servidor**|Pedido pela sua AC emissora ou a AC pública, instala e vincula este certificado SLL no IIS no servidor do NDES.|
|**Certificado da AC de Raiz Fidedigna**|Exporta-o como um ficheiro **.cer** a partir da AC de raiz emissora ou de qualquer dispositivo que confie na AC de raiz emissora e implementa-o em dispositivos com o perfil de certificado da AC Fidedigna.<br /><br />Utiliza apenas um certificado da AC de Raiz Fidedigna por cada plataforma de sistema operativo e associa-o a cada perfil de Certificado de Raiz Fidedigna que criar.<br /><br />Pode utilizar certificados da AC de Raiz Fidedigna adicionais quando necessário. Por exemplo, pode fazê-lo para conceder um estatuto de fidedignidade a uma AC que assina os certificados de autenticação do servidor para os seus pontos de acesso Wi-Fi.|

### <a name="a-namebkmkaccountsaaccounts"></a><a name="BKMK_Accounts"></a>Contas

|Nome|Detalhes|
|--------|-----------|
|**Conta do serviço do NDES**|Especifica uma conta de utilizador de domínio para utilizar como conta do Serviço do NDES.|

## <a name="a-namebkmkconfigureinfrastructureaconfigure-your-infrastructure"></a><a name="BKMK_ConfigureInfrastructure"></a>Configurar a sua infraestrutura
Antes de poder configurar perfis de certificado, tem de concluir as seguintes tarefas, o que requer conhecimento do Windows Server 2012 R2 e dos Serviços de Certificados do Active Directory (ADCS):

**Tarefa 1**: criar uma conta do serviço do NDES

**Tarefa 2**: configurar modelos de certificado na autoridade de certificação

**Tarefa 3**: configurar pré-requisitos no servidor do NDES

**Tarefa 4**: configurar o NDES para ser utilizado com o Intune

**Tarefa 5**: ativar, instalar e configurar o Intune Certificate Connector

### <a name="task-1---create-an-ndes-service-account"></a>Tarefa 1 – criar uma conta do serviço do NDES

Criar uma conta de utilizador de domínio para utilizar como conta do serviço do NDES. Irá especificar esta conta quando configurar os modelos na AC emissora antes de instalar e configurar o NDES. Certifique-se de que o utilizador tem os direitos predefinidos para **Iniciar Sessão Local**, **Iniciar Sessão como um Serviço** e **Iniciar Sessão como Tarefa Batch**. Algumas organizações têm políticas de proteção que desativam estes direitos.

### <a name="task-2---configure-certificate-templates-on-the-certification-authority"></a>Tarefa 2 – configurar modelos de certificado na autoridade de certificação
Nesta tarefa irá:

-   Configurar um modelo de certificados para o NDES

-   Publicar o modelo de certificado para o NDES

#### <a name="to-configure-the-certification-authority"></a>Para configurar a autoridade de certificação

1.  Inicie sessão como administrador da empresa.

2.  Na AC emissora, utilize o snap-in Modelos de Certificado para criar um novo modelo personalizado ou copie um modelo existente, em seguida, edite um modelo existente (como o Modelo de Utilizador) para utilizar com o NDES.

    O modelo tem de ter as seguintes configurações:

    -   Especifique um **Nome a apresentar do modelo** amigável.

    -   No separador **Nome do Requerente**, selecione **Fornecer no pedido**. (A segurança é imposta pelo módulo de política do Intune para o NDES).

    -   No separador **Extensões** certifique-se de que a **Descrição das Políticas de Aplicações** inclui a **Autenticação do Cliente**.

        > [!IMPORTANT]
        > Para os modelos de certificado iOS e Mac OS X, no separador **Extensões**, edite **Utilização de Chaves** e certifique-se de que a opção **A assinatura é uma prova de origem** não está selecionada.

    -   No separador **Segurança**, adicione a conta de serviço do NDES e conceda-lhe permissões de **Inscrição** no modelo. Os administradores do Intune que irão criar perfis SCEP precisam de direitos de **Leitura** para poderem navegar para o modelo ao criarem perfis de SCEP.

    > [!NOTE]
    > Para revogar certificados, a conta de serviço do NDES necessita de direitos para *Emitir e Gerir Certificados* para cada modelo de certificado utilizado por um perfil de certificado.

3.  Reveja o separador **Período de validade** no separador **Geral** do modelo. Por predefinição, o Intune utiliza o valor configurado no modelo. Contudo, tem a opção de configurar a AC para permitir que o autor do pedido especifique um valor diferente que pode, posteriormente, configurar a partir da Consola de administração do Intune. Se pretender utilizar sempre o valor no modelo, ignore o resto deste passo.

    > [!IMPORTANT]
    > As plataformas iOS e Mac OS X utilizam sempre o conjunto de valores no modelo, independentemente de outras configurações que efetuar.

Seguem-se capturas de ecrã de um exemplo de configuração de modelo.

![Modelo, separador processamento de pedidos](.\media\scep_ndes_request_handling.png)

![Modelo, separador nome do requerente](.\media\scep_ndes_subject_name.jpg)

![Modelo, separador segurança](.\media\scep_ndes_security.jpg)

![Modelo, separador extensões](.\media\scep_ndes_extensions.jpg)

![Modelo, separador requisitos de emissão](.\media\scep_ndes_issuance_reqs.jpg)

>   [!IMPORTANT]
    > Em Políticas de Aplicações (na quarta captura de ecrã), adicione apenas as políticas de aplicações necessárias. Confirme as escolhas com os administradores de segurança.



Para configurar a AC de modo a que permita ao autor do pedido especificar o período de validade, execute os seguintes comandos na AC:

   1.  **certutil -setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE**
   2.  **net stop certsvc**
   3.  **net start certsvc**

4.  Na AC emissora, utilize o snap-in Autoridade de Certificação para publicar o modelo de certificado.

    1.  Selecione o nó **Modelos de Certificados**, clique em **Ação**-&gt; **Novo** &gt; **Modelo de certificado a emitir** e, em seguida, selecione o modelo que criou no passo 2.

    2.  Valide o modelo publicado ao visualizá-lo na pasta **Modelos de Certificado**.


### <a name="task-3---configure-prerequisites-on-the-ndes-server"></a>Tarefa 3 – configurar pré-requisitos no servidor do NDES
Nesta tarefa irá:

-   Adicionar o NDES a um Windows Server e configurar ISS para suportar o NDES

-   Adicione a conta do Serviço do NDES ao grupo ISS_IUSR

-   Configure o SPN para a conta do Serviço do NDES




   1.  No servidor que irá alojar o NDES, tem de iniciar sessão como **Administrador de Empresa**e, em seguida, utilizar o [Assistente para Adicionar Funções e Funcionalidades](https://technet.microsoft.com/library/hh831809.aspx) para instalar o NDES:

    1.  No Assistente, selecione **Serviços de Certificados do Active Directory** para obter acesso aos Serviços de Função AD CS. Selecione o **Serviço de Inscrição de Dispositivos de Rede**, desmarque **Autoridade de Certificação**e, em seguida, conclua o assistente.

        > [!TIP]
        > Na página **Progresso da Instalação** do assistente, não clique em **Fechar**. Em alternativa, clique na ligação para **Configurar os Serviços de Certificados do Active Directory no servidor de destino**. Esta ação abre o assistente de **Configuração de AD CS** que utiliza na próxima tarefa. Após a Configuração de AD CS abrir, pode fechar o assistente para Adicionar Funções e Funcionalidades.

    2.  Quando o NDES é adicionado ao servidor, o assistente também instala o IIS. Certifique-se de que o IIS tem as seguintes configurações:

        -   **Servidor Web** &gt; **Segurança** &gt; **Filtragem de Pedidos**

        -   **Servidor Web** &gt; **Programação de Aplicações** &gt; **ASP.NET 3.5**. A instalação do ASP.NET 3.5 irá instalar o .NET Framework 3.5. Ao instalar o .NET Framework 3.5, instala tanto a funcionalidade **.NET Framework 3.5** principal como a **Ativação HTTP**.

        -   **Servidor Web** &gt; **Programação de Aplicações** &gt; **ASP.NET 4.5**. A instalação do ASP.NET 4.5 irá instalar o .NET Framework 4.5. Ao instalar o .NET Framework 4.5, instale a funcionalidade **.NET Framework 4.5** principal, o **ASP.NET 4.5** e a funcionalidade **Serviços do WCF** &gt; **Ativação HTTP**.

        -   **Ferramentas de Gestão** &gt; **Compatibilidade de Gestão do IIS 6** &gt; **Compatibilidade com Metabase do IIS 6**

        -   **Ferramentas de Gestão** &gt; **Compatibilidade de Gestão do IIS 6** &gt; **Compatibilidade do WMI do IIS 6**

  2.  No servidor, adicione a conta do serviço do NDES como membro do grupo **IIS_IUSR**.

   3.  Numa linha de comandos elevada, execute o seguinte comando para configurar o SPN da conta do Serviço do NDES:

`**setspn -s http/&lt;DNS name of NDES Server&gt; &lt;Domain name&gt;\&lt;NDES Service account name&gt;**`

   Por exemplo, se o seu Servidor do NDES se chamar **Servidor01**, o seu domínio for **Contoso.com**e a conta do serviço for **ServiçoDoNDES**utilize:

`**setspn –s http/Server01.contoso.com contoso\NDESService**`

### <a name="task-4---configure-ndes-for-use-with-intune"></a>Tarefa 4 – configurar o NDES para ser utilizado com o Intune
Nesta tarefa irá:

-   Configurar o NDES para ser utilizado com a AC emissora

-   Vincular o certificado de autenticação do servidor (SSL) no IIS

-   Configurar a Filtragem de Pedidos no IIS

##### <a name="to-configure-ndes-for-use-with-intune"></a>Para configurar o NDES para ser utilizado com o Intune

1.  No Servidor do NDES, abra o assistente de Configuração de AD CS e, em seguida, efetue as seguintes configurações.

    > [!TIP]
    > Caso tenha clicado na ligação na tarefa anterior, este assistente já estará aberto. Caso contrário, abra o Gestor de Servidores para aceder à configuração pós-implementação dos Serviços de Certificados do Active Directory.

    -   Na página **Serviços de Função**, selecione o **Serviço de Inscrição de Dispositivos de Rede**.

    -   Na página **Conta do Serviço do NDES** especifique a Conta do Serviço do NDES.

    -   Na página **AC para NDES**, clique em **Selecionar**e, em seguida, clique na AC emissora na qual configurou o modelo de certificado.

    -   Na página **Criptografia para NDES** defina o comprimento da chave para corresponder aos requisitos da sua empresa.

    Na página **Confirmação**, clique em **Configurar** para concluir o assistente.

2.  Após o assistente ser concluído, edite a seguinte chave de registo no Servidor do NDES:

    -   **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Cryptography\MSCEP\**

    Para editar esta chave, identifique o **Objetivo** do modelo de certificado, conforme apresentado no respetivo separador **Processamento de Pedidos**, e edite a entrada correspondente no registo ao substituir os dados existentes pelo nome do modelo de certificado (não o nome a apresentar do modelo) que especificou na Tarefa 1. A seguinte tabela mapeia o objetivo do modelo de certificado para os valores do registo:

    |Objetivo do modelo de certificado (no separador Manipulação de Pedidos)|Valor do registo a editar|Valor visto na consola de administração do Intune para o perfil SCEP|
    |--------------------------------------------------------------|--------------------------|------------------------------------------------------------------------------------------------------------|
    |Assinatura|SignatureTemplate|Assinatura Digital|
    |Encriptação|EncryptionTemplate|Cifragem de Chaves|
    |Assinatura e encriptação|GeneralPurposeTemplate|Cifragem de Chaves<br /><br />Assinatura Digital|
    Por exemplo, se o Objetivo do seu modelo de certificado for **Encriptação**, edite o valor **EncryptionTemplate** para que tenha o mesmo nome do modelo de certificado.

3. O servidor do NDES receberá URLs muito extensos (consultas), que requerem a adição de duas entradas de registo:

    |Localização|Valor|Tipo|Dados|
    |-------|-----|----|----|
    |HKLM\SYSTEM\CurrentControlSet\Services\HTTP\Parameters|MaxFieldLength|DWORD|65534 (decimal)|
    |HKLM\SYSTEM\CurrentControlSet\Services\HTTP\Parameters|MaxRequestBytes|DWORD|65534 (decimal)|


4. No Gestor do IIS, escolha **Site Predefinido** -> **Filtragem de Pedidos** -> **Editar Definição de Funcionalidade** e altere o **Comprimento Máximo do URL** e a **Cadeia máxima de consulta** para *65534*, conforme mostrado.

    ![Comprimento máximo de URL e de consulta no IIS](.\media\SCEP_IIS_max_URL.png)

5.  Reinicie o servidor. Executar **iisreset** no servidor não será suficiente para finalizar estas alterações.
6. Navegue para http://*FQDN*/certsrv/mscep/mscep.dll. Deverá ver uma página NDES semelhante a esta:

    ![Testar NDES](.\media\SCEP_NDES_URL.png)

    Se obtiver **503 Serviço indisponível**, verifique o visualizador de eventos. É provável que o conjunto aplicacional esteja parado devido a um direito em falta para o utilizador do NDES. Esses direitos estão descritos na Tarefa 1.

##### <a name="to-install-and-bind-certificates-on-the-ndes-server"></a>Para Instalar e vincular certificados no Servidor do NDES

1.  No seu Servidor do NDES, peça e instale um certificado de **autenticação de servidor** à sua AC interna ou pública. Irá, em seguida, vincular este certificado SSL no IIS.

    > [!TIP]
    > Após vincular o certificado SSL no IIS, irá também instalar um certificado de autenticação de cliente. Este certificado pode ser emitido por qualquer AC que seja considerada fidedigna pelo Servidor do NDES. Embora não seja a melhor prática, pode utilizar o mesmo certificado tanto para autenticação de servidores como de clientes desde que o certificado tenha ambas as Utilizações de Chave Avançadas (EKUs). Reveja os seguintes passos para obter informações sobre estes certificados de autenticação.

    1.  Após obter o certificado de autenticação de servidor, abra o **Gestor de IIS**, selecione o **Site Predefinido** no painel **Ligações** e, em seguida, clique em **Vínculos** no painel **Ações** .

    2.  Clique em **Adicionar**, configure o **Tipo** para **https**e, em seguida, certifique-se de que a porta é **443**. (O Intune autónomo só suporta a porta 443).

    3.  Para o **certificado SSL**, especifique o certificado de autenticação de servidor.

        > [!NOTE]
        > Se o servidor do NDES utilizar tanto um nome externo como interno para um único endereço de rede, o certificado de autenticação de servidor tem de ter um **Nome do Requerente** com um nome de servidor público externo e um **Nome Alternativo do Requerente** que inclua o nome de servidor interno.

2.  No seu Servidor do NDES, peça e instale um certificado de **autenticação de cliente** à sua AC interna ou a uma autoridade de certificado pública. Este pode ser o mesmo certificado que o certificado de autenticação de servidor caso esse certificado contenha ambas funcionalidades.

    O certificado de autenticação de cliente tem de ter as seguintes propriedades:

    **Utilização de Chave Avançada** – tem de incluir **Autenticação de Cliente**.

    **Nome do Requerente** – tem de ser igual ao nome DNS do servidor no qual está a instalar o certificado (o Servidor do NDES).

##### <a name="to-configure-iis-request-filtering"></a>Para configurar a Filtragem de Pedidos no IIS

1.  No Servidor do NDES, abra o **Gestor de IIS**, selecione o **Site Predefinido** no painel **Ligações** e, em seguida, abra a **Filtragem de Pedidos**.

2.  Clique em **Editar Definições de Funcionalidades**e, em seguida, configure o seguinte:

    **cadeia de consulta (Bytes)** = **65534**

    **Comprimento máximo do URL (Bytes)** = **65534**

3.  Reveja a seguinte chave de registo:

    **HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\HTTP\Parameters**

    Certifique-se de os seguintes valores estão definidos como entradas DWORD:

    Nome: **MaxFieldLength**, com um valor decimal de **65534**

    Nome: **MaxRequestBytes**, com um valor decimal de **65534**

4.  Reinicie o servidor do NDES. O servidor está agora pronto para suportar o Certificate Connector.

### <a name="task-5---enable-install-and-configure-the-intune-certificate-connector"></a>Tarefa 5 – ativar, instalar e configurar o Intune Certificate Connector
Nesta tarefa irá:

Ativar o suporte para o NDES no Intune.

Transferir, instalar e configurar o Certificate Connector no Servidor do NDES.

##### <a name="to-enable-support-for-the-certificate-connector"></a>Para ativar o suporte do Certificate Connector

1. Inicie sessão no portal do Azure.
2. Escolha **Mais Serviços** > **Outros** > **Intune**.
3. No painel **Intune**, escolha **Configurar dispositivos**.
4. No painel **Configuração do Dispositivo**, escolha **Autoridade de Certificação**.
5.  Selecione **Ativar Certificate Connector**.

##### <a name="to-download-install-and-configure-the-certificate-connector"></a>Para transferir, instalar e configurar o Certificate Connector

1. Inicie sessão no portal do Azure.
2. Escolha **Mais Serviços** > **Outros** > **Intune**.
3. No painel **Intune**, escolha **Configurar dispositivos**.
4. No painel **Configuração do Dispositivo**, escolha **Autoridade de Certificação**.
5. Selecione **Transferir o Certificate Connector**.
6.  Após a conclusão da transferência, execute o instalador transferido (**ndesconnectorssetup.exe**) num servidor do Windows Server 2012 R2. Este instalador também instala o módulo de políticas para NDES e o Serviço Web CRP. (O Serviço Web CRP, CertificateRegistrationSvc, é executado como uma aplicação no IIS.)

    > [!NOTE]
    > Ao instalar o NDES para o Intune autónomo, o serviço CRP é instalado automaticamente com o Certificate Connector. Quando utiliza o Intune com o Configuration Manager, instala o Ponto de Registo de Certificados como uma função do sistema de sites à parte.

3.  Quando lhe for pedido o certificado de cliente do Certificate Connector, escolha **Selecionar**e selecione o certificado de **autenticação de cliente** que instalou no Servidor NDES na Tarefa 3.

    Após selecionar o certificado de autenticação de cliente, é encaminhado para a superfície do **Certificado de Cliente do Microsoft Intune Certificate Connector** . Embora o certificado que selecionou não seja apresentado, clique em **Seguinte** para ver as propriedades do certificado. Em seguida, clique em **Seguinte**e, em seguida, clique em **Instalar**.

4.  Após o assistente ser concluído, mas antes de o fechar, clique em **Iniciar a IU do Certificate Connector**.

    > [!TIP]
    > Se fechar o assistente antes de iniciar a IU do Certificate Connector, pode abri-lo novamente ao executar o seguinte comando:
    >
    > **&lt;install_Path&gt;\NDESConnectorUI\NDESConnectorUI.exe**

5.  Na IU do **Certificate Connector** :

    Clique em **Iniciar Sessão** e introduza as suas credenciais de administrador do serviço Intune ou as credenciais de administrador inquilino com a permissão de administração global.

    Se a sua organização utilizar um servidor proxy e o proxy for necessário para o servidor do NDES aceder à Internet, clique em **Utilizar servidor proxy** e, em seguida, forneça o nome do servidor proxy, porta e credenciais de conta para ligar.

    Selecione o separador **Avançadas** e, em seguida, forneça credenciais para uma conta que tenha permissão para **Emitir e Gerir Certificados** na sua Autoridade de Certificados e, em seguida, clique em **Aplicar**.

    Agora, pode fechar a IU do Certificate Connector.

6.  Abra uma linha de comandos e introduza **services.msc**, prima **Enter**, clique com o botão direito do rato no **Serviço Connector do Intune** e, em seguida, clique em **Reiniciar**.

Para se certificar de que o serviço está em execução, abra um browser e introduza o seguinte URL que deverá devolver um erro **403** :

**http:// &lt;FQDN_of_your_NDES_server&gt;/certsrv/mscep/mscep.dll**

## <a name="next-steps"></a>Passos seguintes
Está agora pronto para configurar perfis de certificado, conforme descrito em [Configure certificate profiles (Configurar perfis de certificado)](how-to-configure-certificates.md).

