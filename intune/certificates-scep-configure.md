---
title: Utilizar certificados SCEP com o Microsoft Intune – Azure | Microsoft Docs
description: Para utilizar certificados SCEP no Microsoft Intune, configure o seu domínio do AD no local, crie uma autoridade de certificação, configure o servidor do NDES e instale o Intune Certificate Connector. Depois, crie um perfil de certificado SCEP e, em seguida, atribua este perfil a grupos.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/23/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: kmyrup
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f67ccf1c2fb3b708916ef4ed4209bd3be07d9a5e
ms.sourcegitcommit: 6a9830de768dd97a0e95b366fd5d2f93980cee05
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/10/2018
---
# <a name="configure-and-use-scep-certificates-with-intune"></a>Configurar e utilizar certificados SCEP com o Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Este artigo mostra como configurar a sua infraestrutura e, em seguida, criar e atribuir perfis de certificado SCEP (Simple Certificate Enrollment Protocol) com o Intune.

## <a name="configure-on-premises-infrastructure"></a>Configurar a infraestrutura no local

- **Domínio do Active Directory**: todos os servidores indicados nesta secção (exceto o Servidor Proxy de Aplicações Web) têm de ser associados ao seu domínio do Active Directory.

- **Autoridade de Certificação** (AC): uma Autoridade de Certificação (AC) Empresarial que seja executada numa edição Enterprise do Windows Server 2008 R2 ou posterior. Não é suportada uma AC Autónoma. Para obter mais detalhes, veja [Instalar a Autoridade de Certificação](http://technet.microsoft.com/library/jj125375.aspx).
    Se a sua AC for executada no Windows Server 2008 R2, tem de [instalar a correção de KB2483564](http://support.microsoft.com/kb/2483564/).

- **Servidor do NDES**: num servidor com o Windows Server 2012 R2 ou posterior, tem de configurar o Serviço de Inscrição de Dispositivos de Rede (NDES). O Intune não suporta a utilização do NDES quando este é executado num servidor que também execute a AC Empresarial. Veja a [Documentação de Orientação do Serviço de Inscrição de Dispositivos de Rede](http://technet.microsoft.com/library/hh831498.aspx) para obter instruções sobre como configurar o Windows Server 2012 R2 para alojar o Serviço de Inscrição de Dispositivos de Rede.
O servidor do NDES tem de estar associado ao domínio que aloja a AC e não pode estar no mesmo servidor da AC. Estão disponíveis mais informações sobre a implementação do servidor do NDES numa floresta separada, numa rede isolada ou num domínio interno em [Utilizar um Módulo de Política com o Serviço de Inscrição de Dispositivos de Rede](https://technet.microsoft.com/library/dn473016.aspx).

- **Microsoft Intune Certificate Connector**: utilize o portal do Azure para transferir o instalador do **Certificate Connector** (**ndesconnectorssetup.exe**). Em seguida, pode executar o **ndesconnectorssetup.exe** no servidor que aloja a função Serviço de Inscrição de Dispositivos de Rede (NDES), onde quer instalar o Certificate Connector. 
- **Servidor Proxy de Aplicações Web** (opcional): utilize um servidor com o Windows Server 2012 R2 ou posterior como um servidor Proxy de Aplicações Web (WAP). Esta configuração:
  -  Permite aos dispositivos receberem certificados através de uma ligação à Internet.
  -  É uma recomendação de segurança quando os dispositivos se ligam através da Internet para receber e renovar certificados.

#### <a name="additional"></a>Adicionais
- O servidor que aloja o WAP [tem de instalar uma atualização](http://blogs.technet.com/b/ems/archive/2014/12/11/hotfix-large-uri-request-in-web-application-proxy-on-windows-server-2012-r2.aspx) que ativa o suporte para os URLs longos que são utilizados pelo Serviço de Inscrição de Dispositivos de Rede. Esta atualização está incluída no [rollup da atualização de dezembro de 2014](http://support.microsoft.com/kb/3013769)ou individualmente a partir do [KB3011135](http://support.microsoft.com/kb/3011135).
- O servidor WAP tem de ter um certificado SSL que corresponda ao nome que está a ser publicado em clientes externos e de confiar no certificado SSL utilizado no servidor do NDES. Estes certificados permitem ao servidor do WAP terminar a ligação SSL de clientes e criar uma nova ligação SSL ao servidor do NDES.

Para obter mais informações, veja [Plan certificates for WAP](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn383650(v=ws.11)#plan-certificates) (Planear certificados para o WAP) e as [informações gerais sobre os servidores WAP](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn584113(v=ws.11)).

### <a name="network-requirements"></a>Requisitos de rede

Da Internet para a rede de perímetro, dê permissão à porta 443 a partir de todos os anfitriões/endereços IP na Internet para o servidor NDES.

A partir da rede de perímetro para uma rede fidedigna, permita todas as portas e protocolos necessários para acesso ao domínio do servidor do NDES associado a um domínio. O servidor do NDES precisa de acesso aos servidores de certificado, aos servidores DNS, aos servidores do Configuration Manager e aos controladores de domínio.

Recomendamos a publicação do servidor NDES através de um proxy, tal como o [proxy de aplicações do Azure AD](https://azure.microsoft.com/documentation/articles/active-directory-application-proxy-publish/), [Proxy de Acesso Web](https://technet.microsoft.com/library/dn584107.aspx) ou um proxy de terceiros.

### <a name="certificates-and-templates"></a>Certificados e modelos

|Objeto|Detalhes|
|----------|-----------|
|**Modelo de Certificado**|Configura este modelo na sua AC emissora.|
|**Certificado de autenticação de cliente**|Pedido pela sua AC emissora ou AC pública; instala este certificado no Servidor do NDES.|
|**Certificado de autenticação do servidor**|Pedido pela sua AC emissora ou a AC pública; instala e vincula este certificado SSL no IIS no servidor do NDES.|
|**Certificado da AC de Raiz Fidedigna**|Exporta este certificado como um ficheiro **.cer** a partir da AC de raiz emissora ou de qualquer dispositivo que confie na AC de raiz e atribui-o a dispositivos com o perfil de certificado da AC Fidedigna.<br /><br />Utiliza apenas um certificado da AC de Raiz Fidedigna por cada plataforma de sistema operativo e associa-o a cada perfil de Certificado de Raiz Fidedigna que criar.<br /><br />Pode utilizar certificados da AC de Raiz Fidedigna adicionais quando necessário. Por exemplo, pode fazê-lo para conceder um estatuto de fidedignidade a uma AC que assina os certificados de autenticação do servidor para os seus pontos de acesso Wi-Fi.|

### <a name="accounts"></a>Contas

|Nome|Detalhes|
|--------|-----------|
|**Conta do serviço do NDES**|Introduza uma conta de utilizador de domínio para utilizar como conta do Serviço do NDES.|

## <a name="configure-your-infrastructure"></a>Configurar a sua infraestrutura
Antes de poder configurar perfis de certificados, conclua as tarefas seguintes. Estas tarefas requerem conhecimento do Windows Server 2012 R2 e dos Serviços de Certificados do Active Directory (ADCS):

**Passo 1**: Criar uma conta do serviço do NDES

**Passo 2**: Configurar modelos de certificado na autoridade de certificação

**Passo 3**: Configurar pré-requisitos no servidor do NDES

**Passo 4**: Configurar o NDES para ser utilizado com o Intune

**Passo 5**: Ativar, instalar e configurar o Intune Certificate Connector

#### <a name="step-1---create-an-ndes-service-account"></a>Passo 1 – Criar uma conta do serviço do NDES

Criar uma conta de utilizador de domínio para utilizar como conta do serviço do NDES. Introduza esta conta quando configurar os modelos na AC emissora antes de instalar e configurar o NDES. Verifique se o utilizador tem os direitos predefinidos para **Iniciar Sessão Localmente**, **Iniciar Sessão como um Serviço** e **Iniciar Sessão como Tarefa Batch**. Algumas organizações têm políticas de proteção que desativam estes direitos.

#### <a name="step-2---configure-certificate-templates-on-the-certification-authority"></a>Passo 2 – Configurar modelos de certificado na autoridade de certificação
Nesta tarefa irá:

- Configurar um modelo de certificados para o NDES
- Publicar o modelo de certificado para o NDES

##### <a name="configure-the-certification-authority"></a>Configurar a autoridade de certificação

1. Inicie sessão como administrador da empresa.

2. Na AC emissora, utilize o snap-in Modelos de Certificado para criar um novo modelo personalizado. Também pode copiar um modelo existente e, em seguida, atualizá-lo (como o Modelo de utilizador) para utilizar com o NDES.

   >[!NOTE]
   > O modelo de certificado NDES tem de se basear num Modelo de Certificado v2 (com a compatibilidade do Windows 2003).

   O modelo tem de ter as seguintes configurações:

   - Introduza um **Nome a apresentar do modelo** amigável.

   - Em **Nome do Requerente**, selecione **Fornecer no pedido**. (A segurança é imposta pelo módulo de política do Intune para o NDES).

   - Em **Extensões** confirme se a **Descrição das Políticas de Aplicações** inclui a **Autenticação de Cliente**.

     > [!IMPORTANT]
     > Para os modelos de certificado iOS e macOS, no separador **Extensões**, edite **Utilização de Chave** e confirme que a opção **A assinatura é uma prova de origem** não está selecionada.

   - Em **Segurança**, adicione a conta de serviço do NDES e conceda-lhe permissões de **Inscrição** no modelo. Os administradores do Intune que criam perfis SCEP precisam de direitos de **Leitura** para poderem navegar para o modelo ao criarem perfis de SCEP.

     > [!NOTE]
     > Para revogar certificados, a conta de serviço do NDES necessita de direitos para *Emitir e Gerir Certificados* para cada modelo de certificado utilizado por um perfil de certificado.

3. Reveja o separador **Período de validade** no separador **Geral** do modelo. Por predefinição, o Intune utiliza o valor configurado no modelo. Contudo, tem a opção de configurar a AC para permitir que o autor do pedido introduza um valor diferente que pode, posteriormente, configurar a partir da Consola do administrador do Intune. Se pretender utilizar sempre o valor no modelo, ignore o resto deste passo.

   > [!IMPORTANT]
   > O iOS e o macOS utilizam sempre o conjunto de valores no modelo, independentemente de outras configurações que realizar.

Configuração de modelos de exemplo:

![Modelo, separador processamento de pedidos](./media/scep_ndes_request_handling.png)

![Modelo, separador nome do requerente](./media/scep_ndes_subject_name.jpg)

![Modelo, separador segurança](./media/scep_ndes_security.jpg)

![Modelo, separador extensões](./media/scep_ndes_extensions.jpg)

![Modelo, separador requisitos de emissão](./media/scep_ndes_issuance_reqs.jpg)

> [!IMPORTANT]
> Em Políticas de Aplicações, adicione apenas as políticas de aplicações necessárias. Confirme as escolhas com os administradores de segurança.

Configure a AC para permitir que o autor do pedido introduza o período de validade:

1. Na AC, execute os seguintes comandos:
   - **certutil -setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE**
   - **net stop certsvc**
   - **net start certsvc**

2. Na AC emissora, utilize o snap-in Autoridade de Certificação para publicar o modelo de certificado.
   Selecione o nó **Modelos de Certificado**, clique em **Ação** > **Novo** > **Modelo de Certificado a Emitir** e, em seguida, selecione o modelo que criou no passo 2.

3. Valide o modelo publicado ao visualizá-lo na pasta **Modelos de Certificado**.

#### <a name="step-3---configure-prerequisites-on-the-ndes-server"></a>Passo 3 – Configurar pré-requisitos no servidor do NDES
Nesta tarefa irá:

- Adicionar o NDES a um Windows Server e configurar ISS para suportar o NDES
- Adicione a conta do Serviço do NDES ao grupo ISS_IUSR
- Configure o SPN para a conta do Serviço do NDES

1. No servidor que aloja o NDES, inicie sessão como **Administrador de Empresa** e, em seguida, utilize o [Assistente para Adicionar Funções e Funcionalidades](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831809(v=ws.11)) para instalar o NDES:

   1. No Assistente, selecione **Serviços de Certificados do Active Directory** para obter acesso aos Serviços de Função AD CS. Selecione o **Serviço de Inscrição de Dispositivos de Rede**, desmarque **Autoridade de Certificação**e, em seguida, conclua o assistente.

      > [!TIP]
      > Em **Progresso da Instalação**, não selecione **Fechar**. Em alternativa, selecione a ligação para **Configurar os Serviços de Certificados do Active Directory no servidor de destino**. É aberto o assistente de **Configuração de AD CS** que utilizará na próxima tarefa. Após a Configuração de AD CS abrir, pode fechar o assistente para Adicionar Funções e Funcionalidades.

   2. Quando o NDES é adicionado ao servidor, o assistente também instala o IIS. Certifique-se de que o IIS tem as seguintes configurações:

   3. **Servidor Web** > **Segurança** > **Filtragem de Pedidos**

   4. **Servidor Web** > **Desenvolvimento de Aplicações** > **ASP.NET 3.5**. A instalação do ASP.NET 3.5 instala o .NET Framework 3.5. Ao instalar o .NET Framework 3.5, instala tanto a funcionalidade **.NET Framework 3.5** principal como a **Ativação HTTP**.

   5. **Servidor Web** > **Desenvolvimento de Aplicações** > **ASP.NET 4.5**. A instalação do ASP.NET 4.5 instala o .NET Framework 4.5. Ao instalar o .NET Framework 4.5, instale a funcionalidade **.NET Framework 4.5** principal, o **ASP.NET 4.5** e a funcionalidade **Serviços do WCF** > **Ativação HTTP**.

   6. **Ferramentas de Gestão** > **Compatibilidade de Gestão do IIS 6** > **Compatibilidade com Metabase do IIS 6**

   7. **Ferramentas de Gestão** > **Compatibilidade de Gestão do IIS 6** > **Compatibilidade com WMI do IIS 6**

   8. No servidor, adicione a conta do serviço do NDES como membro do grupo **IIS_IUSR**.

2. Numa linha de comandos elevada, execute o seguinte comando para configurar o SPN da conta do Serviço do NDES:

    `setspn -s http/<DNS name of NDES Server> <Domain name>\<NDES Service account name>`

    Por exemplo, se o seu Servidor do NDES se chamar **Servidor01**, o seu domínio for **Contoso.com**e a conta do serviço for **ServiçoDoNDES**utilize:

    `setspn –s http/Server01.contoso.com contoso\NDESService`

#### <a name="step-4---configure-ndes-for-use-with-intune"></a>Passo 4 – Configurar o NDES para ser utilizado com o Intune
Nesta tarefa irá:

- Configurar o NDES para ser utilizado com a AC emissora
- Vincular o certificado de autenticação do servidor (SSL) no IIS
- Configurar a Filtragem de Pedidos no IIS

1. No Servidor do NDES, abra o assistente de Configuração de AD CS e, em seguida, faça as seguintes atualizações:

    > [!TIP]
    > Caso tenha clicado na ligação na tarefa anterior, este assistente já estará aberto. Caso contrário, abra o Gestor de Servidores para aceder à configuração pós-implementação dos Serviços de Certificados do Active Directory.

   - Em **Serviços de Função**, selecione o **Serviço de Inscrição de Dispositivos de Rede**
   - Em **Conta do Serviço do NDES** introduza a Conta do Serviço do NDES
   - Em **AC para NDES**, clique em **Selecionar** e, em seguida, clique na AC emissora na qual configurou o modelo de certificado
   - Em **Criptografia para NDES** defina o comprimento da chave para corresponder aos requisitos da sua empresa.
   - Em **Confirmação**, selecione **Configurar** para concluir o assistente.

2. Após o assistente ser concluído, atualize a seguinte chave de registo no Servidor do NDES:

    `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Cryptography\MSCEP\`

    Para atualizar esta chave, identifique o **Objetivo** do modelo de certificado (que se encontra no respetivo separador **Processamento de Pedidos**). Em seguida, atualize a entrada de registo correspondente ao substituir os dados existentes pelo nome do modelo de certificado (não o nome a apresentar do modelo) que especificou na Tarefa 1. A seguinte tabela mapeia o objetivo do modelo de certificado para os valores do registo:

    |Objetivo do modelo de certificado (no separador Manipulação de Pedidos)|Valor do registo a editar|Valor visto na consola de administração do Intune para o perfil SCEP|
    |---|---|---|
    |Assinatura|SignatureTemplate|Assinatura Digital|
    |Encriptação|EncryptionTemplate|Cifragem de Chaves|
    |Assinatura e encriptação|GeneralPurposeTemplate|Cifragem de Chaves<br/>Assinatura Digital|

    Por exemplo, se o Objetivo do seu modelo de certificado for **Encriptação**, edite o valor **EncryptionTemplate** para que tenha o mesmo nome do modelo de certificado.

3. O servidor do NDES recebe URLs extensos (consultas) que exigem a adição de duas entradas de registo:


   |                        Localização                        |      Valor      | Tipo  |      Dados       |
   |--------------------------------------------------------|-----------------|-------|-----------------|
   | HKLM\SYSTEM\CurrentControlSet\Services\HTTP\Parameters | MaxFieldLength  | DWORD | 65534 (decimal) |
   | HKLM\SYSTEM\CurrentControlSet\Services\HTTP\Parameters | MaxRequestBytes | DWORD | 65534 (decimal) |


4. No Gestor de IIS, selecione **Site Predefinido** > **Filtragem de Pedidos** > **Editar Definição de Funcionalidade**. Altere o **Comprimento máximo do URL** e **Cadeia máxima de consulta** para *65534*, conforme apresentado:

    ![Comprimento máximo de URL e de consulta no IIS](./media/SCEP_IIS_max_URL.png)

5. Reinicie o servidor. Executar **iisreset** no servidor não é suficiente para finalizar estas alterações.
6. Navegue para `http://*FQDN*/certsrv/mscep/mscep.dll`. Deverá ver uma página do NDES semelhante à seguinte:

    ![Testar NDES](./media/SCEP_NDES_URL.png)

    Se obtiver **503 Serviço indisponível**, verifique o visualizador de eventos. É provável que o conjunto aplicacional esteja parado devido a um direito em falta para o utilizador do NDES. Esses direitos estão descritos na Tarefa 1.

##### <a name="install-and-bind-certificates-on-the-ndes-server"></a>Instalar e vincular certificados no Servidor do NDES

1. No seu Servidor do NDES, peça e instale um certificado de **autenticação de servidor** à sua AC interna ou pública. Em seguida, deve vincular este certificado SSL no IIS.

    > [!TIP]
    > Após vincular o certificado SSL no IIS, instale um certificado de autenticação de cliente. Este certificado pode ser emitido por qualquer AC que seja considerada fidedigna pelo Servidor do NDES. Embora não seja a melhor prática, pode utilizar o mesmo certificado para autenticação de servidores e de clientes desde que o certificado tenha ambas as Utilizações de Chave Avançadas (EKUs). Reveja os seguintes passos para obter informações sobre estes certificados de autenticação.

   1. Depois de obter o certificado de autenticação de servidor, abra o **Gestor de IIS** e selecione o **Site Predefinido**. No painel **Ações**, selecione **Enlaces**.

   2. Selecione **Adicionar**, defina o **Tipo** para **https** e, em seguida, confirme que a porta é **443**. O Intune autónomo só suporta a porta 443.

   3. Para o **certificado SSL**, introduza o certificado de autenticação de servidor.

      > [!NOTE]
      > Se o servidor do NDES utilizar um nome externo e interno para um único endereço de rede, o certificado de autenticação de servidor terá de ter:
      > - Um **Nome do Requerente** com um nome de servidor público externo
      > - Um **Nome Alternativo do Requerente** que inclua o nome de servidor interno

2. No seu Servidor do NDES, peça e instale um certificado de **autenticação de cliente** à sua AC interna ou a uma autoridade de certificado pública. Este pode ser o mesmo certificado que o certificado de autenticação de servidor caso esse certificado contenha ambas funcionalidades.

    O certificado de autenticação de cliente tem de ter as seguintes propriedades:

    - **Utilização de Chave Avançada**: este valor tem de incluir **Autenticação de Cliente**

    - **Nome do Requerente**: este valor tem de ser igual ao nome DNS do servidor no qual está a instalar o certificado (o Servidor do NDES)

##### <a name="configure-iis-request-filtering"></a>Configurar a filtragem de pedidos no IIS

1. No Servidor do NDES, abra o **Gestor de IIS**, selecione o **Site Predefinido** no painel **Ligações** e, em seguida, abra a **Filtragem de Pedidos**.

2. Selecione **Editar Definições de Funcionalidade** e, em seguida, defina os seguintes valores:

    - **cadeia de consulta (Bytes)** = **65534**
    - **Comprimento máximo do URL (Bytes)** = **65534**

3. Reveja a seguinte chave de registo:

    `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\HTTP\Parameters`

    Confirme que os seguintes valores estão definidos como entradas DWORD:

    - Nome: **MaxFieldLength**, com um valor decimal de **65534**
    - Nome: **MaxRequestBytes**, com um valor decimal de **65534**

4. Reinicie o servidor do NDES. O servidor está agora pronto para suportar o Certificate Connector.

#### <a name="step-5---enable-install-and-configure-the-intune-certificate-connector"></a>Passo 5 – Ativar, instalar e configurar o Intune Certificate Connector
Nesta tarefa irá:

- Ativar o suporte para o NDES no Intune.
- Transferir, instalar e configurar o Certificate Connector no servidor que aloja a função Serviço de Inscrição de Dispositivos de Rede (NDES), um servidor no seu ambiente. Para aumentar a dimensão da implementação do NDES na sua organização, pode instalar múltiplos servidores do NDES com um Microsoft Intune Certificate Connector em cada servidor do NDES.

##### <a name="download-install-and-configure-the-certificate-connector"></a>Transferir, instalar e configurar o Certificate Connector
![ConnectorDownload](./media/certificates-download-connector.png)

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços**, filtre por **Intune** e selecione **Microsoft Intune**.
3. Selecione **Configuração do dispositivo** e, em seguida, selecione **Autoridade de Certificação**.
4. Selecione **Adicionar** e **Transferir o ficheiro de conector**. Guarde a transferência numa localização a que possa aceder a partir do servidor onde irá instalá-la.
5. Quando a transferência for concluída, execute o instalador que transferiu (**ndesconnectorssetup.exe**) no servidor que aloja a função Serviço de Inscrição de Dispositivos de Rede (NDES). Este instalador também instala o módulo de políticas para NDES e o Serviço Web CRP. (O Serviço Web CRP, CertificateRegistrationSvc, é executado como uma aplicação no IIS.)

    > [!NOTE]
    > Ao instalar o NDES para o Intune autónomo, o serviço CRP é instalado automaticamente com o Certificate Connector. Quando utiliza o Intune com o Configuration Manager, instala o Ponto de Registo de Certificados como uma função do sistema de sites à parte.

6. Quando lhe for pedido o certificado de cliente do Certificate Connector, escolha **Selecionar**e selecione o certificado de **autenticação de cliente** que instalou no Servidor NDES na Tarefa 3.

    Após selecionar o certificado de autenticação de cliente, é encaminhado para a superfície do **Certificado de Cliente do Microsoft Intune Certificate Connector** . Embora o certificado que selecionou não seja apresentado, selecione **Seguinte** para ver as propriedades do certificado. Selecione **Seguinte** e, em seguida, **Instalar**.
    
    > [!IMPORTANT]
    > O Intune Certificate Connector não pode ser inscrito num dispositivo com a Configuração de Segurança Avançada do Internet Explorer ativada. Para utilizar o Intune Certificate Connector, [desative a Configuração de segurança avançada do IE](https://technet.microsoft.com/library/cc775800(v=WS.10).aspx).

7. Após o assistente ser concluído, mas antes de o fechar, selecione a opção para **Iniciar a IU do Certificate Connector**.

    > [!TIP]
    > Se fechar o assistente antes de iniciar a IU do Certificate Connector, pode abri-lo novamente ao executar o seguinte comando:
    >
    > <caminho_de_Instalação>\NDESConnectorUI\NDESConnectorUI.exe

8. Na IU do **Certificate Connector**:

    Selecione **Iniciar Sessão** e introduza as suas credenciais de administrador do serviço Intune ou as credenciais de administrador inquilino com a permissão de administração global.

    > [!IMPORTANT]
    > A conta de utilizador tem de ser atribuída a uma licença válida do Intune. Se a conta de utilizador não tiver uma licença válida do Intune, o ficheiro NDESConnectorUI.exe irá falhar.

    Se a sua organização utilizar um servidor proxy e o proxy for necessário para o servidor do NDES aceder à Internet, selecione **Utilizar servidor proxy** e, em seguida, introduza o nome do servidor proxy, a porta e as credenciais de conta para ligar.

    Selecione o separador **Avançadas** e, em seguida, introduza as credenciais para uma conta que tenha permissão para **Emitir e Gerir Certificados** na sua Autoridade de Certificados emissora. **Aplique** as suas alterações.

    Agora, pode fechar a IU do Certificate Connector.

9. Abra uma linha de comandos, introduza **services.msc** e, em seguida, prima **Enter**. Clique com o botão direito do rato em **Intune Connector Service** e selecione **Reiniciar**.

Para se certificar de que o serviço está em execução, abra um browser e introduza o seguinte URL. O mesmo deverá devolver um erro **403**:

`http://<FQDN_of_your_NDES_server>/certsrv/mscep/mscep.dll`

## <a name="create-a-scep-certificate-profile"></a>Criar um perfil de certificado SCEP

1. No portal do Azure, abra o Microsoft Intune.
2. Selecione **Configuração do dispositivo** e selecione **Perfis** e **Criar perfil**.
3. Introduza um **Nome** e uma **Descrição** para o perfil de certificado SCEP.
4. Na lista pendente **Plataforma**, selecione a plataforma do dispositivo para este certificado SCEP. Atualmente, pode selecionar uma das seguintes plataformas para definições de restrição de dispositivos:
   - **Android**
   - **iOS**
   - **macOS**
   - **Windows Phone 8.1**
   - **Windows 8.1 e posterior**
   - **Windows 10 e posterior**
5. Na lista pendente **Tipo de perfil**, selecione **Certificado SCEP**.
6. No painel **Certificado SCEP**, configure as seguintes definições:

   - **Período de validade do certificado**: se tiver executado o comando `certutil - setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE` na AC emissora, que permite um período de validade personalizado, pode introduzir o tempo restante até o certificado expirar.<br>Pode introduzir um valor inferior ao período de validade do modelo de certificado, mas não superior. Por exemplo, se o período de validade do certificado no modelo de certificado for dois anos, pode introduzir um valor de um ano, mas não um valor de cinco anos. O valor deve também ser inferior ao período de validade restante do certificado da AC emissora. 
   - **Fornecedor de armazenamento de chaves (KSP)** (Windows Phone 8.1, Windows 8.1, Windows 10): introduza o local onde está armazenada a chave do certificado. Escolha um dos seguintes valores:
     - **Inscrever em KSP de Trusted Platform Module (TPM) se estiver presente, caso contrário, KSP de Software**
     - **Inscrever em KSP de Trusted Platform Module (TPM), caso contrário, ocorre uma falha**
     - **Inscrever em Passport, caso contrário, ocorre uma falha (Windows 10 e posterior)**
     - **Inscrever em KSP de Software**

   - **Formato do nome do requerente**: na lista, selecione de que forma o Intune cria automaticamente o nome do requerente no pedido de certificado. Se o certificado se destinar a um utilizador, pode também incluir o endereço de e-mail do utilizador no nome do requerente. Escolha entre:
     - **Não configurado**
     - **Nome comum**
     - **Nome comum, incluindo o e-mail**
     - **Nome comum como e-mail**
     - **Identidade Internacional do Equipamento Móvel (IMEI)**
     - **Número de série**
     - **Personalizado**: quando seleciona esta opção, é apresentado outro campo pendente. Utilize este campo para introduzir um formato de nome de requerente personalizado. O formato personalizado suporta duas variáveis: **Nome Comum (CN)** e **E-mail (E)**. O **Nome Comum (CN)** pode ser definido para qualquer uma das seguintes variáveis:
       - **CN={{UserName}}**: o nome principal de utilizador do utilizador, tal como janedoe@contoso.com
       - **CN={{AAD_Device_ID}}**: um ID atribuído ao registar um dispositivo no Azure Active Directory (AD). Este ID é normalmente utilizado na autenticação com o Azure AD.
       - **CN={{SERIALNUMBER}}**: o número de série exclusivo (SN) normalmente utilizado pelo fabricante para identificar um dispositivo
       - **CN={{IMEINumber}}**: o número exclusivo IMEI (Identidade Internacional do Equipamento Móvel) utilizado para identificar um telemóvel
       - **CN={{OnPrem_Distinguished_Name}}**: uma sequência de nomes únicos relativos separados por vírgulas, como `CN=Jane Doe,OU=UserAccounts,DC=corp,DC=contoso,DC=com`

          Para utilizar a variável `{{OnPrem_Distinguished_Name}}`, não se esqueça de sincronizar o atributo de utilizador `onpremisesdistingishedname` com o [Azure AD Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) com o seu Azure AD.

       - **CN={{onPremisesSamAccountName}}**: os administradores podem sincronizar o atributo samAccountName do Active Directory para o Azure AD através do Azure AD Connect para um atributo denominado `onPremisesSamAccountName`. O Intune pode substituir essa variável como parte de um pedido de emissão de certificado no requerente de um certificado SCEP.  O atributo samAccountName é o nome de início de sessão de utilizador utilizado para suportar clientes e servidores de uma versão anterior do Windows (anterior ao Windows 2000). O formato do nome de início de sessão do utilizador é: `DomainName\testUser` ou apenas `testUser`.

          Para utilizar a variável `{{onPremisesSamAccountName}}`, não se esqueça de sincronizar o atributo de utilizador `onPremisesSamAccountName` com o [Azure AD Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) com o seu Azure AD.

       Ao utilizar uma combinação de uma ou várias destas variáveis e cadeias estáticas, pode criar um formato de nome de requerente personalizado, tal como: **CN={{UserName}},E={{EmailAddress}},OU=Mobile,O=Finance Group,L=Redmond,ST=Washington,C=US**. <br/> Neste exemplo, criou um formato de nome de requerente que, além das variáveis CN e E, utiliza cadeias para os valores Unidade Organizacional, Organização, Localização, Estado e País. O artigo [função CertStrToName](https://msdn.microsoft.com/library/windows/desktop/aa377160.aspx) descreve esta função e as cadeias suportadas da mesma.

- **Nome alternativo do requerente**: introduza o modo como o Intune cria automaticamente os valores para o nome alternativo do requerente (SAN) no pedido de certificado. Por exemplo, se selecionar um tipo de certificado de utilizador, pode incluir o nome principal de utilizador (UPN) no nome alternativo do requerente. Se o certificado de cliente for utilizado para autenticar um Servidor de Políticas de Rede, terá de definir o nome alternativo do requerente com o UPN.
- **Utilização de chave**: introduza as opções de utilização de chave para este certificado. As opções são:
  - **Cifragem de chaves**: permita a troca de chaves apenas quando a chave for encriptada
  - **Assinatura digital**: permita a troca de chaves apenas quando uma assinatura digital ajudar a proteger a chave
- **Tamanho da chave (bits)**: selecione o número de bits que está contido na chave
- **Algoritmo hash** (Android, Windows Phone 8.1, Windows 8.1, Windows 10): selecione um dos tipos de algoritmo hash disponíveis para utilizar com este certificado. Selecione o maior nível de segurança que os dispositivos de ligação suportam.
- **Certificado de Raiz**: selecione um perfil de certificado da AC de raiz que tenha configurado anteriormente e atribuído ao utilizador ou dispositivo. Este certificado da AC tem de ser o certificado de raiz da AC que emite o certificado que está a configurar neste perfil de certificado.
- **Utilização da chave expandida**: **adicione** valores ao objetivo do certificado. Na maioria dos casos, o certificado exige a **Autenticação de Cliente** para o utilizador ou dispositivo poder ser autenticado num servidor. Contudo, pode adicionar mais utilizações de chave conforme necessário.
- **Definições de Inscrição**
  - **Limiar de renovação (%)**: introduza a percentagem da duração do certificado antes de o dispositivo pedir a renovação do certificado.
  - **URLs do Servidor SCEP**: introduza um ou mais URLs para os servidores do NDES que emitem os certificados através de SCEP.
  - Selecione **OK** e **crie** o seu perfil.

O perfil será criado e apresentado no painel Lista de perfis.

## <a name="assign-the-certificate-profile"></a>Atribuir o perfil de certificado

Antes de atribuir perfis de certificado a grupos, considere o seguinte:

- Ao atribuir perfis de certificado a grupos, o ficheiro de certificado do perfil de certificado da AC fidedigna é instalado no dispositivo. O dispositivo utiliza o perfil de certificado de SCEP para criar um pedido de certificado por parte do dispositivo.
- Os perfis de certificado são instalados apenas em dispositivos que executam a plataforma que utiliza quando criou o perfil.
- Pode atribuir perfis de certificado a coleções de utilizadores ou de dispositivos.
- Para publicar um certificado num dispositivo rapidamente após a inscrição do mesmo, atribua o perfil de certificado a um grupo de utilizadores, em vez de atribuir a um grupo de dispositivos. Se atribuir a um grupo de dispositivos, será preciso um registo do dispositivo completo antes de o dispositivo receber políticas.
- Apesar de atribuir cada perfil separadamente, também terá de atribuir a AC de Raiz Confiável e o perfil SCEP ou PKCS. Caso contrário, a política de certificados SCEP ou PKCS falha.

    > [!NOTE]
    > Para dispositivos iOS, deverá ver múltiplas cópias do certificado no perfil de gestão, se implementar múltiplos perfis de recursos que utilizem o mesmo perfil de certificado.
    
Para obter informações sobre como atribuir perfis, veja [Como atribuir perfis de dispositivo](device-profile-assign.md).
