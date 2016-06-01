---
# required metadata

title: Configurar a infraestrutura de certificados | Microsoft Intune
description:
keywords:
author: nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 3a435650-3891-4754-8abc-4bbac244f33b

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Configurar a infraestrutura de certificados
Este tópico descreve o que precisa para criar e implementar perfis de certificado.

Para efetuar qualquer autenticação baseada em certificado na sua organização, é necessário uma Autoridade de Certificação Empresarial.

Para utilizar perfis de certificado SCEP, para além da Autoridade de Certificação Empresarial, também é necessário:

-   Um servidor que executa o Serviço de Inscrição de Dispositivos de Rede

-   O Intune Certificate Connector, que é instalado no servidor do Windows Server 2012 R2 que executa o NDES

Para utilizar perfis de certificado .PFX, para além da Autoridade de Certificação Empresarial, também é necessário:

-  Um computador que possa comunicar com a Autoridade de Certificação ou utilizar o próprio computador da Autoridade de Certificação.

-  O Intune Certificate Connector, que é executado no computador que pode comunicar com a Autoridade de Certificação.

## Infraestrutura no local


-    **Domínio do Active Directory**: todos os servidores indicados nesta secção (exceto o Servidor de Proxy de Aplicações Web) têm de ser associados ao seu domínio do Active Directory.

-  **Autoridade de Certificação** (AC): uma Autoridade de Certificação (AC) Empresarial que seja executada numa edição Enterprise do Windows Server 2008 R2 ou posterior. Não é suportada uma AC Autónoma. Para obter instruções sobre como configurar uma Autoridade de Certificação, consulte [Instalar a autoridade de certificação](http://technet.microsoft.com/library/jj125375.aspx)
    Se a sua AC for executada no Windows Server 2008 R2, tem de [instalar a correção de KB2483564](http://support.microsoft.com/kb/2483564/)

-  **Servidor do NDES** (apenas SCEP): num servidor com o Windows Server 2012 R2 ou posterior, tem de configurar o Serviço de Inscrição de Dispositivos de Rede (NDES). O Intune não suporta a utilização do NDES quando este é executado num servidor que também execute a AC Empresarial. Consulte a [Documentação de Orientação do Serviço de Inscrição de Dispositivos de Rede](http://technet.microsoft.com/library/hh831498.aspx) para obter instruções sobre como configurar o Windows Server 2012 R2 para alojar o Serviço de Inscrição de Dispositivos de Rede.
-  **Um computador que possa comunicar com a Autoridade de Certificação** (apenas .PFX): em alternativa, utilize o próprio computador da Autoridade de Certificação.
-  **Microsoft Intune Certificate Connector**: utilize a consola de administração do Intune para transferir o instalador do **Certificate Connector** (**ndesconnectorssetup.exe**). Em seguida, pode executar **ndesconnectorssetup.exe** no computador onde pretende instalar o Certificate Connector. Para perfis de certificado .PFX, instale o Certificate Connector no computador que comunica com a Autoridade de Certificação.
-  **Servidor de Proxy de Aplicações Web** (opcional): pode utilizar um servidor com o Windows Server 2012 R2 ou posterior como um servidor de Proxy de Aplicações Web (WAP). Esta configuração:
    -  Permite aos dispositivos receberem certificados através de uma ligação à Internet.
    -  É uma recomendação de segurança quando os dispositivos se ligam através da Internet para receber e renovar certificados.

> [!NOTE]           
> -    O servidor que aloja o WAP [tem de instalar uma atualização](http://blogs.technet.com/b/ems/archive/2014/12/11/hotfix-large-uri-request-in-web-application-proxy-on-windows-server-2012-r2.aspx) que ativa o suporte para os URLs longos que são utilizados pelo Serviço de Inscrição de Dispositivos de Rede. Esta atualização está incluída no [rollup da atualização de dezembro de 2014](http://support.microsoft.com/kb/3013769) ou individualmente a partir de [KB3011135](http://support.microsoft.com/kb/3011135)
>-  Além disso, o servidor que aloja o WAP tem de ter um certificado SSL que corresponda ao nome que está a ser publicado em clientes externos, e tem de confiar no certificado SSL utilizado no servidor do NDES. Estes certificados permitem ao servidor do WAP terminar a ligação SSL de clientes e criar uma nova ligação SSL ao servidor do NDES.
    Para obter informações sobre certificados para o WAP, consulte a secção **Planear os certificados** do artigo [Planear a Publicação de Aplicações Através do Proxy de Aplicações Web](https://technet.microsoft.com/library/dn383650.aspx). Para obter informações gerais sobre os servidores do WAP, consulte [Trabalhar com o Proxy de Aplicações Web](http://technet.microsoft.com/library/dn584113.aspx)


### Certificados e Modelos

|Objeto|Detalhes|
|----------|-----------|
|**Modelo de Certificado**|Configura este modelo na sua AC emissora.|
|**Certificado de autenticação de cliente**|Pedido pela sua AC emissora ou AC pública, instala este certificado no Servidor do NDES.|
|**Certificado de autenticação do servidor**|Pedido pela sua AC emissora ou a AC pública, instala e vincula este certificado SLL no IIS no servidor do NDES.|
|**Certificado da AC de Raiz Fidedigna**|Exporta-o como um ficheiro **.cer** a partir da AC emissora ou qualquer dispositivo que confia na AC emissora e implementa-o em dispositivos com o perfil de certificado da AC Fidedigna.<br /><br />Utiliza apenas um certificado da AC de Raiz Fidedigna por cada plataforma de sistema operativo e associa-o a cada perfil de Certificado de Raiz Fidedigna que criar.<br /><br />Pode utilizar certificados da AC de Raiz Fidedigna adicionais quando necessário. Por exemplo, pode fazê-lo para conceder um estatuto de fidedignidade a uma AC que assina os certificados de autenticação do servidor para os seus pontos de acesso Wi-Fi.|

### Contas

|Nome|Detalhes|
|--------|-----------|
|**Conta do serviço do NDES**|Especifica uma conta de utilizador de domínio para utilizar como conta do Serviço do NDES.|

## Configurar a sua infraestrutura
Antes de poder configurar perfis de certificado, tem de concluir as seguintes tarefas, o que requer conhecimento do Windows Server 2012 R2 e dos Serviços de Certificados do Active Directory (ADCS):

**Tarefa 1** - configurar modelos de certificado na autoridade de certificação

**Tarefa 2**, apenas para perfis SCEP - configurar pré-requisitos no servidor do NDES

**Tarefa 3**, apenas para perfis SCEP - configurar o NDES para utilização no Intune

**Tarefa 4** - ativar, instalar e configurar o Intune Certificate Connector

## Tarefa 1 - configurar modelos de certificado na autoridade de certificação
Nesta tarefa irá:

-   Criar uma conta do serviço do NDES

    > Para revogar certificados, a conta de serviço do NDES necessita de direitos para *Emitir e Gerir Certificados* para cada modelo de certificado utilizado por um perfil de certificado.

-   Configurar um modelo de certificados para o NDES

-   Publicar o modelo de certificado para o NDES

##### Para configurar a autoridade de certificação

1.  Criar uma conta de utilizador de domínio para utilizar como conta do serviço do NDES. Irá especificar esta conta quando configurar os modelos na AC emissora antes de instalar e configurar o NDES.

2.  Na AC emissora, utilize o snap-in Modelos de Certificado para criar um novo modelo personalizado ou copie um modelo existente, em seguida, edite um modelo existente (como o Modelo de Utilizador) para utilizar com o NDES.

    O modelo tem de ter as seguintes configurações:

    -   Especifique um **Nome a apresentar do modelo** amigável.

    -   No separador **Nome do Requerente** , selecione **Fornecer no pedido**. (A segurança é imposta pelo módulo de política do Intune para o NDES).

    -   No separador **Extensões**, certifique-se de que a **Descrição das Políticas de Aplicações** inclui a **Autenticação do Cliente**

        > Para os modelos de certificado iOS e Mac OS X, no separador **Extensões**, edite **Utilização de Chaves** e certifique-se de que a opção **A assinatura é uma prova de origem** não está selecionada.

    -   No separador **Segurança**, adicione a conta de serviço do NDES e conceda-lhe permissões de **Inscrição** no modelo.

3.  Reveja o separador **Período de validade** no separador **Geral** do modelo. Por predefinição, o Intune utiliza o valor configurado no modelo. Contudo, tem a opção de configurar a AC para permitir que o autor do pedido especifique um valor diferente que pode, posteriormente, configurar a partir da Consola de administração do Intune. Se pretender utilizar sempre o valor no modelo, ignore o resto deste passo.

    > As plataformas iOS e Mac OS X utilizam sempre o conjunto de valores no modelo, independentemente de outras configurações que efetuar.

    Para configurar a AC de modo a que permita ao autor do pedido especificar o período de validade, execute os seguintes comandos na AC:

    1.  **certutil -setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE**

    2.  **net stop certsvc**

    3.  **net start certsvc**

4.  Na AC emissora, utilize o snap-in Autoridade de Certificação para publicar o modelo de certificado.

    1.  Selecione o nó **Modelos de certificado**, clique em **Ação**-&gt; **Novo** &gt; **Modelo de certificado a emitir** e, em seguida, selecione o modelo que criou no passo 2.

    2.  Valide o modelo publicado ao visualizá-lo na pasta **Modelos de Certificado** .

5.  Para perfis .PFX: no computador da AC, certifique-se de que o computador que aloja o Intune Certificate Connector tem permissão de inscrição, para que possa aceder ao modelo que foi utilizado na criação do perfil .PFX. Defina essa permissão no separador **Segurança** das propriedades do computador da AC.

## Tarefa 2 (apenas para perfis SCEP) - configurar os pré-requisitos no servidor do NDES
Nesta tarefa irá:

-   Adicionar o NDES a um Windows Server e configurar ISS para suportar o NDES

-   Adicione a conta do Serviço do NDES ao grupo ISS_IUSR

-   Configure o SPN para a conta do Serviço do NDES

##### Para configurar os pré-requisitos para o Servidor do NDES

1.  No servidor que irá alojar o NDES, tem de iniciar sessão como **Administrador de Empresa**e, em seguida, utilizar o [Assistente para Adicionar Funções e Funcionalidades](https://technet.microsoft.com/library/hh831809.aspx) para instalar o NDES:

    1.  No Assistente, selecione **Serviços de Certificados do Active Directory** para obter acesso aos Serviços de Função AD CS. Selecione o **Serviço de Inscrição de Dispositivos de Rede**, desmarque **Autoridade de Certificação**e, em seguida, conclua o assistente.

        > [!TIP]
        > Na página **Progresso da Instalação** do assistente, não clique em **Fechar**. Em alternativa, clique na ligação para **Configurar os Serviços de Certificados do Active Directory no servidor de destino**. Esta ação abre o assistente de **Configuração de AD CS** que utiliza na próxima tarefa. Após a Configuração de AD CS abrir, pode fechar o assistente para Adicionar Funções e Funcionalidades.

    2.  Quando o NDES é adicionado ao servidor, o assistente também instala o IIS. Certifique-se de que o IIS tem as seguintes configurações:

        -   **Servidor Web** &gt; **Segurança** &gt; **Filtragem de Pedidos**

        -   **Servidor Web** &gt; **Desenvolvimento de Aplicações** &gt; **ASP.NET 3.5**. A instalação do ASP.NET 3.5 irá instalar o .NET Framework 3.5. Ao instalar o .NET Framework 3.5, instala tanto a funcionalidade **.NET Framework 3.5** principal como a **Ativação HTTP**

        -   **Servidor Web** &gt; **Desenvolvimento de Aplicações** &gt; **ASP.NET 4.5**. A instalação do ASP.NET 4.5 irá instalar o .NET Framework 4.5. Ao instalar o .NET Framework 4.5, instale a funcionalidade **.NET Framework 4.5** principal, o **ASP.NET 4.5** e a funcionalidade **Serviços do WCF** &gt; **Ativação HTTP**.

        -   **Ferramentas de Gestão** &gt; **Compatibilidade de Gestão do IIS 6** &gt; **Compatibilidade com Metabase do IIS 6**

        -   **Ferramentas de Gestão** &gt; **Compatibilidade de Gestão do IIS 6** &gt; **Compatibilidade WMI do IIS 6**

2.  No servidor, adicione a conta do serviço do NDES como membro do grupo **IIS_IUSR**.

3.  Execute o seguinte comando para configurar o SPN da conta do Serviço do NDES:

    -   **setspn -s http/&lt;Nome DNS do Servidor do NDES&gt; &lt;Nome de domínio&gt;\&lt;Nome da conta de Serviço do NDES&gt;**

    Por exemplo, se o seu Servidor do NDES se chamar **Servidor01**, o seu domínio for **Contoso.com**e a conta do serviço for **ServiçoDoNDES**utilize:

    -   **setspn –s http/Servidor01.contoso.com contoso\ServiçoDoNDES**

## Tarefa 3 (apenas para perfis SCEP) - configurar o NDES para utilização no Microsoft Intune 
Nesta tarefa irá:

-   Configurar o NDES para ser utilizado com a AC emissora

-   Vincular o certificado de autenticação do servidor (SSL) no IIS

-   Configurar a Filtragem de Pedidos no IIS

##### Para configurar o NDES para ser utilizado com o Intune

1.  No Servidor do NDES, abra o assistente de Configuração de AD CS e, em seguida, efetue as seguintes configurações.

    > [!TIP]
    > Caso tenha clicado na ligação na tarefa anterior, este assistente já estará aberto. Caso contrário, abra o Gestor de Servidores para aceder à configuração pós-implementação dos Serviços de Certificados do Active Directory.

    -   Na página **Serviços de Função**, selecione o **Serviço de Inscrição de Dispositivos de Rede**

    -   Na página **Conta do Serviço do NDES** especifique a Conta do Serviço do NDES.

    -   Na página **AC para NDES** , clique em **Selecionar**e, em seguida, clique na AC emissora na qual configurou o modelo de certificado.

    -   Na página **Criptografia para NDES** defina o comprimento da chave para corresponder aos requisitos da sua empresa.

    Na página **Confirmação** , clique em **Configurar** para concluir o assistente.

2.  Após o assistente ser concluído, edite a seguinte chave de registo no Servidor do NDES:

    -   **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Cryptography\MSCEP\*\**

    Para editar esta chave, identifique o **Objetivo** do modelo de certificado, conforme apresentado no respetivo separador **Processamento de Pedidos**, e edite a entrada correspondente no registo ao substituir os dados existentes pelo nome do modelo de certificado (não o nome a apresentar do modelo) que especificou na Tarefa 1. A seguinte tabela mapeia o objetivo do modelo de certificado para os valores do registo:

    |Objetivo do modelo de certificado (no separador Manipulação de Pedidos)|Valor do registo a editar|Valor visto na consola de administração do Intune para o perfil SCEP|
    |--------------------------------------------------------------|--------------------------|------------------------------------------------------------------------------------------------------------|
    |Assinatura|SignatureTemplate|Assinatura Digital|
    |Encriptação|EncryptionTemplate|Cifragem de Chaves|
    |Assinatura e encriptação|GeneralPurposeTemplate|Cifragem de Chaves<br /><br />Assinatura Digital|
    Por exemplo, se o Objetivo do seu modelo de certificado for **Encriptação**, edite o valor **EncryptionTemplate** para que tenha o mesmo nome do modelo de certificado.

3.  Após editar o registo, execute o **iisreset** no servidor para forçar o servidor a detetar as alterações recentes à configuração.

##### Para Instalar e vincular certificados no Servidor do NDES

1.  No seu Servidor do NDES, peça e instale um certificado de **autenticação de servidor** à sua AC interna ou pública. Irá, em seguida, vincular este certificado SSL no IIS.

    > [!TIP]
    > Após vincular o certificado SSL no IIS, irá também instalar um certificado de autenticação de cliente. Este certificado pode ser emitido por qualquer AC que seja considerada fidedigna pelo Servidor do NDES. Embora não seja a melhor prática, pode utilizar o mesmo certificado tanto para autenticação de servidores como de clientes desde que o certificado tenha ambas as Utilizações de Chave Avançadas (EKUs). Reveja os seguintes passos para obter informações sobre estes certificados de autenticação.

    1.  Após obter o certificado de autenticação de servidor, abra o **Gestor de IIS**, selecione o **Site Predefinido** no painel **Ligações** e, em seguida, clique em **Vínculos** no painel **Ações** .

    2.  Clique em **Adicionar**, configure o **Tipo** para **https**e, em seguida, certifique-se de que a porta é **443**. (O Intune autónomo só suporta a porta 443).

    3.  Para o **certificado SSL**, especifique o certificado de autenticação de servidor.

        > Se o servidor do NDES utilizar tanto um nome externo como interno para um único endereço de rede, o certificado de autenticação de servidor tem de ter um **Nome do Requerente** com um nome de servidor público externo e um **Nome Alternativo do Requerente** que inclua o nome de servidor interno.

2.  No seu Servidor do NDES, peça e instale um certificado de **autenticação de cliente** à sua AC interna ou a uma autoridade de certificado pública. Este pode ser o mesmo certificado que o certificado de autenticação de servidor caso esse certificado contenha ambas funcionalidades.

    O certificado de autenticação de cliente tem de ter as seguintes propriedades:

    **Utilização de Chave Avançada** - tem de incluir **Autenticação de Cliente**

    **Nome do Requerente** - tem de ser igual ao nome DNS do servidor no qual está a instalar o certificado (o Servidor do NDES).

##### Para configurar a Filtragem de Pedidos no IIS

1.  No Servidor do NDES, abra o **Gestor de IIS**, selecione o **Web Site Predefinido** no painel **Ligações** e, em seguida, abra a **Filtragem de Pedidos**

2.  Clique em **Editar Definições de Funcionalidades**e, em seguida, configure o seguinte:

    **cadeia de consulta (Bytes)** = **65534**

    **Comprimento máximo do URL (Bytes)** = **65534**

3.  Reveja a seguinte chave de registo:

    **HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\HTTP\Parameters**

    Certifique-se de os seguintes valores estão definidos como entradas DWORD:

    Nome: **MaxFieldLength**, com um valor decimal de **65534**

    Nome: **MaxRequestBytes**, com um valor decimal de **65534**

4.  Reinicie o servidor do NDES. O servidor está agora pronto para suportar o Certificate Connector.

## Tarefa 4 - ativar, instalar e configurar o Intune Certificate Connector - para certificados SCEP e .PFX.
Nesta tarefa irá:

Ativar o suporte para o NDES no Intune

Transferir, instalar e configurar o Certificate Connector no Servidor do NDES

##### Para ativar o suporte do Certificate Connector

1.  Abra a [consola de administração do Intune](https://manage.microsoft.com), clique em **Administração** &gt; **Certificate Connector**

2.  Clique em **Configurar Certificate Connector no Local**

3.  Selecione **Ativar Certificate Connector** e, em seguida, clique em **OK**

##### Para transferir, instalar e configurar o Certificate Connector

1.  Abra a [consola de administração do Intune](https://manage.microsoft.com) e, em seguida, clique em **Administração** &gt; **Gestão de Dispositivos Móveis** &gt; **Certificate Connector** &gt; **Transferir Certificate Connector**

2.  Após a conclusão da transferência, execute o instalador transferido (**ndesconnectorssetup.exe**):

    -   Para certificados .PFX, execute o instalador no computador com capacidade para ligar à Autoridade de Certificação. Escolha a opção .PFX Distribution e clique em Instalar. Após a conclusão da instalação, continue criando um perfil de certificado, conforme descrito em [Configurar perfis de certificado](configure-intune-certificate-profiles.md)

    -   Para certificados SCEP, execute o instalador num servidor do Windows Server 2012 R2

    Para a opção SCEP, o instalador também instala o módulo de políticas para NDES e o Serviço Web CRP. (O Serviço Web CRP, CertificateRegistrationSvc, é executado como uma aplicação no IIS.)

    > [!NOTE]
    > Ao instalar o NDES para o Intune autónomo, o serviço CRP é instalado automaticamente com o Certificate Connector. Quando utiliza o Intune com o Configuration Manager, instala o Ponto de Registo de Certificados como uma função do sistema de sites à parte.

3.  Quando lhe for pedido o certificado de cliente para o Certificate Connector, clique em **Selecionar**e selecione o certificado de **autenticação de cliente** que instalou no Servidor do NDES na Tarefa 3.

    Após selecionar o certificado de autenticação de cliente, é encaminhado para a superfície do **Certificado de Cliente do Microsoft Intune Certificate Connector** . Embora o certificado que selecionou não seja apresentado, clique em **Seguinte** para ver as propriedades do certificado. Em seguida, clique em **Seguinte** e clique em **Instalar**

4.  Após o assistente ser concluído, mas antes de o fechar, clique em **Iniciar a IU do Certificate Connector**

    > Se fechar o assistente antes de iniciar a IU do Certificate Connector, pode abri-lo novamente ao executar o seguinte comando:
    >
    > **&lt;install_Path&gt;\NDESConnectorUI\NDESConnectorUI.exe**

5.  Na IU do **Certificate Connector** :

    Clique em **Iniciar Sessão** e introduza as suas credenciais de administrador do serviço Intune ou as credenciais de administrador inquilino com a permissão de administração global.

    Se a sua organização utilizar um servidor proxy e o proxy for necessário para o servidor do NDES aceder à Internet, clique em **Utilizar servidor proxy** e, em seguida, forneça o nome do servidor proxy, porta e credenciais de conta para ligar.

    Selecione o separador **Avançadas** e, em seguida, forneça credenciais para uma conta que tenha permissão para **Emitir e Gerir Certificados** na sua Autoridade de Certificação e, em seguida, clique em **Aplicar**

    Agora, pode fechar a IU do Certificate Connector.

6.  Abra uma linha de comandos e introduza **services.msc**, prima **Enter**, clique com o botão direito do rato no **Serviço Certificate Connector** e, em seguida, clique em **Reiniciar**

Para se certificar de que o serviço está em execução, abra um browser e introduza o seguinte URL que deverá devolver um erro **403** :

**http:// &lt;FQDN_of_your_NDES_server&gt;/certsrv/mscep/mscep.dll**

### Passos seguintes
Está agora pronto para configurar perfis de certificado, conforme descrito em [Configurar perfis de certificado](configure-intune-certificate-profiles.md)


<!--HONumber=May16_HO2-->


