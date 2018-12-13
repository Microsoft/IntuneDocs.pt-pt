---
title: Utilizar certificados SCEP com o Microsoft Intune – Azure | Microsoft Docs
description: Para utilizar certificados SCEP no Microsoft Intune, configure o seu domínio do AD no local, crie uma autoridade de certificação, configure o servidor do NDES e instale o Intune Certificate Connector. Depois, crie um perfil de certificado SCEP e, em seguida, atribua este perfil a grupos. Além disso, veja os IDs de evento diferentes e as respetivas descrições e os códigos de diagnóstico para o serviço de conector do Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/6/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: kmyrup
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 49e80c364c02902a185b85c7aed09a292ad9c6c8
ms.sourcegitcommit: 874d9a00cc4666920069d54f99c6c2e687fa34a6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/13/2018
ms.locfileid: "53325114"
---
# <a name="configure-and-use-scep-certificates-with-intune"></a>Configurar e utilizar certificados SCEP com o Intune

Este artigo mostra como configurar a sua infraestrutura e, em seguida, criar e atribuir perfis de certificado SCEP (Simple Certificate Enrollment Protocol) com o Intune.

## <a name="configure-on-premises-infrastructure"></a>Configurar a infraestrutura no local

- **Domínio do Active Directory**: Todos os servidores indicados nesta secção (exceto o Servidor de Proxy de Aplicações Web) têm de ser associados ao seu domínio do Active Directory.

- **Autoridade de certificação** (AC): Tem de ser um Microsoft Enterprise autoridade de certificação (AC) que é executada numa edição Enterprise do Windows Server 2008 R2 ou posterior. Não é suportada uma AC Autónoma. Para obter mais detalhes, veja [Instalar a Autoridade de Certificação](http://technet.microsoft.com/library/jj125375.aspx).
    Se a sua AC for executada no Windows Server 2008 R2, tem de [instalar a correção de KB2483564](http://support.microsoft.com/kb/2483564/).

- **Servidor do NDES**: No Windows Server 2012 R2 ou posterior, configure a função de servidor do serviço de inscrição de dispositivos de rede (NDES). O Intune não suporta a utilização do NDES num servidor que também execute a AC Empresarial. Veja a [Documentação de Orientação do Serviço de Inscrição de Dispositivos de Rede](http://technet.microsoft.com/library/hh831498.aspx) para obter instruções sobre como configurar o Windows Server 2012 R2 para alojar o NDES.
O servidor do NDES tem de ser associado a um domínio que esteja na mesma floresta da AC Empresarial. Estão disponíveis mais informações sobre a implementação do servidor do NDES numa floresta separada, numa rede isolada ou num domínio interno em [Utilizar um Módulo de Política com o Serviço de Inscrição de Dispositivos de Rede](https://technet.microsoft.com/library/dn473016.aspx).

- **Microsoft Intune Certificate Connector**: Transfira o **Certificate Connector** instalador (**NDESConnectorSetup.exe**) do portal de administração do Intune. Irá executar este instalador no servidor com a função NDES.  

  - O Certificate Connector do NDES também suporta o modo Federal Information Processing Standard (FIPS). O FIPS não é obrigatório, mas pode emitir e revogar certificados quando está ativado.

- **Servidor de Proxy de aplicações Web** (opcional): Utilizar um servidor que executa o Windows Server 2012 R2 ou posterior como um servidor de Proxy de aplicações Web (WAP). Esta configuração:
  - Permite aos dispositivos receberem certificados através de uma ligação à Internet.
  - É uma recomendação de segurança quando os dispositivos se ligam através da Internet para receber e renovar certificados.
  
- **Proxy de aplicações do Azure AD** (opcional): O Proxy de aplicações do Azure AD pode ser utilizado em vez de um servidor de Proxy de aplicações Web (WAP) dedicado para publicar o servidor do NDES na Internet. Para mais informações, consulte [How to provide secure remote access to on-premises applications (Como fornecer acesso remoto seguro a aplicações no local)](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy).

#### <a name="additional"></a>Adicionais

- O servidor que aloja o WAP [tem de instalar uma atualização](http://blogs.technet.com/b/ems/archive/2014/12/11/hotfix-large-uri-request-in-web-application-proxy-on-windows-server-2012-r2.aspx) que ativa o suporte para os URLs longos que são utilizados pelo Serviço de Inscrição de Dispositivos de Rede. Esta atualização está incluída no [rollup da atualização de dezembro de 2014](http://support.microsoft.com/kb/3013769)ou individualmente a partir do [KB3011135](http://support.microsoft.com/kb/3011135).
- O servidor WAP tem de ter um certificado SSL que corresponda ao nome que está a ser publicado em clientes externos e de confiar no certificado SSL utilizado no servidor do NDES. Estes certificados permitem ao servidor do WAP terminar a ligação SSL de clientes e criar uma nova ligação SSL ao servidor do NDES.

Para obter mais informações, veja [Plan certificates for WAP](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn383650(v=ws.11)#plan-certificates) (Planear certificados para o WAP) e as [informações gerais sobre os servidores WAP](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn584113(v=ws.11)).

### <a name="network-requirements"></a>Requisitos da rede

Se não utilizar um proxy inverso, tal como o WAP ou o Proxy de Aplicações do Azure AD, permita o tráfego TCP na porta 443 de todos os anfitriões/endereços IP na Internet para o servidor do NDES.

Autorize todas as portas e protocolos necessários entre o servidor do NDES e as infraestruturas de suporte. Por exemplo, o servidor do NDES tem de comunicar com a AC, os servidores DNS, os servidores do Configuration Manager, os controladores de domínio e, eventualmente, com outros serviços no seu ambiente.

Recomendamos vivamente a publicação do servidor do NDES através de um proxy inverso, tal como o [proxy de aplicações do Azure AD](https://azure.microsoft.com/documentation/articles/active-directory-application-proxy-publish/), o [Proxy de Acesso Web](https://technet.microsoft.com/library/dn584107.aspx) ou um proxy de terceiros.

### <a name="certificates-and-templates"></a>Certificados e modelos  

|Objeto|Detalhes|
|----------|-----------|
|**Modelo de Certificado**|Configura este modelo na sua AC emissora.|
|**Certificado de autenticação de cliente**|Pedido pela sua AC emissora ou AC pública; instala este certificado no Servidor do NDES.|
|**Certificado de autenticação do servidor**|Pedido pela sua AC emissora ou a AC pública; instala e vincula este certificado SSL no IIS no servidor do NDES. Se o certificado tiver o conjunto de utilizações de chave de autenticação de cliente e servidor (**Utilizações de Chave Avançadas**), pode utilizar o mesmo certificado.|
|**Certificado da AC de Raiz Fidedigna**|Irá exportar este certificado como um ficheiro **.cer** a partir da AC de raiz ou de qualquer dispositivo que confie na AC de raiz. Em seguida, atribuí-la a utilizadores, dispositivos ou ambos os com o perfil de certificado de AC fidedigna.<br /><b>Nota:<b />quando é atribuído um perfil de certificado SCEP, certifique-se de que atribuir o perfil de certificado de raiz fidedigna referenciado no seu perfil de certificado SCEP no mesmo grupo de utilizadores ou dispositivos.<br /><br />Utiliza apenas um certificado da AC de Raiz Fidedigna por cada plataforma de sistema operativo e associa-o a cada perfil de Certificado de Raiz Fidedigna que criar.<br /><br />Pode utilizar certificados da AC de Raiz Fidedigna adicionais quando necessário. Por exemplo, pode fazê-lo para conceder um estatuto de fidedignidade a uma AC que assina os certificados de autenticação do servidor para os seus pontos de acesso Wi-Fi.|

### <a name="accounts"></a>Contas

|Nome|Detalhes|
|--------|-----------|
|**Conta do serviço do NDES**|Introduza uma conta de utilizador de domínio para utilizar como conta do Serviço do NDES. |

## <a name="configure-your-infrastructure"></a>Configurar a sua infraestrutura
Para poder configurar perfis de certificados, conclua os passos seguintes. Estes passos exigem o conhecimento do Windows Server 2012 R2 ou posterior e dos Serviços de Certificados do Active Directory (ADCS):

#### <a name="step-1---create-an-ndes-service-account"></a>Passo 1 – Criar uma conta do serviço do NDES

Criar uma conta de utilizador de domínio para utilizar como conta do serviço do NDES. Introduza esta conta quando configurar os modelos na AC emissora antes de instalar e configurar o NDES. Verifique se o utilizador tem os direitos predefinidos para **Iniciar Sessão Localmente**, **Iniciar Sessão como um Serviço** e **Iniciar Sessão como Tarefa Batch**. Algumas organizações têm políticas de proteção que desativam estes direitos.

#### <a name="step-2---configure-certificate-templates-on-the-certification-authority"></a>Passo 2 – Configurar modelos de certificado na autoridade de certificação
Neste passo, irá:

- Configurar um modelo de certificados para o NDES
- Publicar o modelo de certificado para o NDES

##### <a name="configure-the-certification-authority"></a>Configurar a autoridade de certificação

1. Inicie sessão como administrador da empresa.

2. Na AC emissora, utilize o snap-in Modelos de Certificado para criar um novo modelo personalizado. Também pode copiar um modelo existente e, em seguida, atualizá-lo (como o Modelo de utilizador) para utilizar com o NDES.

   >[!NOTE]
   > O modelo de certificado NDES tem de se basear num Modelo de Certificado v2 (com a compatibilidade do Windows 2003).

   O modelo tem de ter as seguintes configurações:

   - Em **Geral**:
   
       - Confirme que a propriedade **Publicar certificado no Active Directory** **não** está selecionada.
       - Introduza um **Nome a apresentar do modelo** amigável.

   - Em **Nome do Requerente**, selecione **Fornecer no pedido**. (A segurança é imposta pelo módulo de política do Intune para o NDES).

   - Em **Extensões** confirme se a **Descrição das Políticas de Aplicações** inclui a **Autenticação de Cliente**.

     > [!IMPORTANT]
     > Para os modelos de certificado iOS e macOS, no separador **Extensões**, edite **Utilização de Chave** e confirme que a opção **A assinatura é uma prova de origem** não está selecionada.

   - Em **Segurança**, adicione a conta de serviço do NDES e conceda-lhe permissões de **Inscrição** no modelo. Os administradores do Intune que criam perfis SCEP precisam de direitos de **Leitura** para poderem navegar para o modelo ao criarem perfis de SCEP.

     > [!NOTE]
     > Para revogar certificados, a conta de serviço do NDES necessita de direitos para *Emitir e Gerir Certificados* para cada modelo de certificado utilizado por um perfil de certificado.

3. Reveja o separador **Período de validade** no separador **Geral** do modelo. Por predefinição, o Intune utiliza o valor configurado no modelo. Contudo, pode configurar a AC para permitir que o autor do pedido introduza um valor diferente que pode, posteriormente, configurar a partir da Consola do administrador do Intune. Se quiser utilizar sempre o valor no modelo, ignore o resto deste passo.

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
   Selecione o nó **Modelos de certificado**, clique em **Ação** > **Novo** > **Modelo de certificado a emitir** e, em seguida, selecione o modelo que criou no passo 2.

3. Valide o modelo publicado ao visualizá-lo na pasta **Modelos de Certificado**.

#### <a name="step-3---configure-prerequisites-on-the-ndes-server"></a>Passo 3 – Configurar pré-requisitos no servidor do NDES
Neste passo, irá:

- Adicionar o NDES a um Windows Server e configurar ISS para suportar o NDES
- Adicione a conta do Serviço do NDES ao grupo ISS_IUSR
- Definir um nome do principal do serviço (SPN) para a conta do Serviço do NDES

1. No servidor que aloja o NDES, inicie sessão como **Administrador de Empresa** e, em seguida, utilize o [Assistente para Adicionar Funções e Funcionalidades](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831809(v=ws.11)) para instalar o NDES:

   1. No Assistente, selecione **Serviços de Certificados do Active Directory** para obter acesso aos Serviços de Função AD CS. Selecione o **Serviço de Inscrição de Dispositivos de Rede**, desmarque **Autoridade de Certificação**e, em seguida, conclua o assistente.

      > [!TIP]
      > Em **Progresso da Instalação**, não selecione **Fechar**. Em alternativa, selecione a ligação para **Configurar os Serviços de Certificados do Active Directory no servidor de destino**. O assistente de **Configuração de AD CS** que utilizará no próximo passo abre-se. Após a Configuração de AD CS abrir, pode fechar o assistente para Adicionar Funções e Funcionalidades.

   2. Quando o NDES é adicionado ao servidor, o assistente também instala o IIS. Confirme que o IIS está configurado da seguinte forma:

       - **Servidor Web** > **Segurança** > **Filtragem de Pedidos**

       - **Servidor Web** > **Desenvolvimento de Aplicações** > **ASP.NET 3.5** 

            A instalação do ASP.NET 3.5 instala o .NET Framework 3.5. Ao instalar o .NET Framework 3.5, instala tanto a funcionalidade **.NET Framework 3.5** principal como a **Ativação HTTP**.

       - **Servidor Web** > **Desenvolvimento de Aplicações** > **ASP.NET 4.5** 

            A instalação do ASP.NET 4.5 instala o .NET Framework 4.5. Ao instalar o .NET Framework 4.5, instale a funcionalidade **.NET Framework 4.5** principal, o **ASP.NET 4.5** e a funcionalidade **Serviços do WCF** > **Ativação HTTP**.

       - **Ferramentas de Gestão** > **Compatibilidade de Gestão do IIS 6** > **Compatibilidade com Metabase do IIS 6**

       - **Ferramentas de Gestão** > **Compatibilidade de Gestão do IIS 6** > **Compatibilidade com WMI do IIS 6**

       - No servidor, adicione a conta do serviço do NDES como membro do grupo local **IIS_IUSR**.

2. Numa linha de comandos elevada, execute o seguinte comando para configurar o SPN da conta do Serviço do NDES:

    `setspn -s http/<DNS name of NDES Server> <Domain name>\<NDES Service account name>`

    Por exemplo, se o seu Servidor do NDES se chamar **Servidor01**, o seu domínio for **Contoso.com**e a conta do serviço for **ServiçoDoNDES**utilize:

    `setspn –s http/Server01.contoso.com contoso\NDESService`

#### <a name="step-4---configure-ndes-for-use-with-intune"></a>Passo 4 – Configurar o NDES para ser utilizado com o Intune
Neste passo, irá:

- Configurar o NDES para ser utilizado com a AC emissora
- Vincular o certificado de autenticação do servidor (SSL) no IIS
- Configurar a Filtragem de Pedidos no IIS

1. No Servidor do NDES, abra o assistente de Configuração de AD CS e, em seguida, faça as seguintes atualizações:

    > [!TIP]
    > Caso tenha clicado na ligação no passo anterior, este assistente já estará aberto. Caso contrário, abra o Gestor de Servidores para aceder à configuração pós-implementação dos Serviços de Certificados do Active Directory.

   - Em **Serviços de Função**, selecione o **Serviço de Inscrição de Dispositivos de Rede**
   - Em **Conta do Serviço do NDES** introduza a Conta do Serviço do NDES
   - Em **AC para NDES**, clique em **Selecionar** e, em seguida, clique na AC emissora na qual configurou o modelo de certificado
   - Em **Criptografia para NDES** defina o comprimento da chave para corresponder aos requisitos da sua empresa.
   - Em **Confirmação**, selecione **Configurar** para concluir o assistente.

2. Após o assistente ser concluído, atualize a seguinte chave de registo no Servidor do NDES:

    `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Cryptography\MSCEP\`

    Para atualizar esta chave, identifique o **Objetivo** do modelo de certificado (que se encontra no respetivo separador **Processamento de Pedidos**). Em seguida, atualize a entrada de registo correspondente ao substituir os dados existentes pelo nome do modelo de certificado (não o nome a apresentar do modelo) que especificou no Passo 2. A seguinte tabela mapeia o objetivo do modelo de certificado para os valores do registo:

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

5. Reinicie o servidor. Não utilize **iisreset** porque as alterações não ficarão finalizadas.
6. Navegue para `http://*FQDN*/certsrv/mscep/mscep.dll`. Deverá ver uma página do NDES semelhante à seguinte:

    ![Testar NDES](./media/SCEP_NDES_URL.png)

    Se obtiver **503 Serviço indisponível**, verifique o visualizador de eventos. É provável que o conjunto aplicacional esteja parado devido a um direito em falta para o utilizador do NDES. Esses direitos estão descritos no Passo 1.

##### <a name="install-and-bind-certificates-on-the-ndes-server"></a>Instalar e vincular certificados no Servidor do NDES

1. No seu Servidor do NDES, peça e instale um certificado de **autenticação de servidor** à sua AC interna ou pública. Em seguida, deve vincular este certificado SSL no IIS.

    > [!TIP]
    > Após vincular o certificado SSL no IIS, instale um certificado de autenticação de cliente. Este certificado pode ser emitido por qualquer AC que seja considerada fidedigna pelo Servidor do NDES. É possível utilizar o mesmo certificado se este tiver o conjunto de utilizações de chave de autenticação de cliente e servidor (**Utilizações de Chave Avançadas**). Reveja os seguintes passos para obter informações sobre estes certificados de autenticação.

   1. Depois de obter o certificado de autenticação de servidor, abra o **Gestor de IIS** e selecione o **Site Predefinido**. No painel **Ações**, selecione **Enlaces**.

   2. Selecione **Adicionar**, defina o **Tipo** para **https** e, em seguida, confirme que a porta é **443**. O Intune autónomo só suporta a porta 443.

   3. Para o **certificado SSL**, introduza o certificado de autenticação de servidor.

      > [!NOTE]
      > Se o servidor do NDES utilizar um nome externo e interno para um único endereço de rede, o certificado de autenticação de servidor terá de ter:
      > - Um **Nome do Requerente** com um nome de servidor público externo
      > - Um **Nome Alternativo do Requerente** que inclua o nome de servidor interno

2. No seu Servidor do NDES, peça e instale um certificado de **autenticação de cliente** à sua AC interna ou a uma autoridade de certificado pública. Pode ser o mesmo certificado que o certificado de autenticação de servidor caso esse certificado contenha ambas funcionalidades.

    O certificado de autenticação de cliente tem de ter as seguintes propriedades:

    - **Utilização de chave avançada**: Este valor tem de incluir **autenticação de cliente**

    - **Nome do requerente**: O valor tem de ser igual ao nome DNS do servidor em que estiver a instalar o certificado (o servidor do NDES)

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
Neste passo, irá:

- Ativar o suporte para o NDES no Intune.
- Transferir, instalar e configurar o Certificate Connector no servidor que aloja a função Serviço de Inscrição de Dispositivos de Rede (NDES), um servidor no seu ambiente. Para aumentar a dimensão da implementação do NDES na sua organização, pode instalar múltiplos servidores do NDES com um Microsoft Intune Certificate Connector em cada servidor do NDES.

##### <a name="download-install-and-configure-the-certificate-connector"></a>Transferir, instalar e configurar o Certificate Connector

> [!IMPORTANT] 
> O Microsoft Intune Certificate Connector **tem** de ser instalado num servidor Windows separado. Não pode ser instalado na Autoridade de Certificação (AC) emissora. Também **tem** de estar instalado no mesmo servidor que a função Serviço de Inscrição de Dispositivos de Rede (NDES).

1. No [portal do Azure](https://portal.azure.com), selecione **Todos os serviços**, filtre o **Intune** e selecione **Microsoft Intune**.
2. Selecione **Configuração do dispositivo** > **Autoridade de Certificação** > **Adicionar**
3. Transfira e guarde o ficheiro de conector. Guarde-o numa localização acessível a partir do servidor onde vai instalar o conector.

    ![ConnectorDownload](./media/certificates-download-connector.png)

4. Quando a transferência for concluída, aceda ao servidor que aloja a função Serviço de Inscrição de Dispositivos de Rede (NDES). Em seguida:

    1. Certifique-se de que o .NET 4.5 Framework está instalado, pois o Certificate Connector do NDES precisa dele. O .NET 4.5 Framework vem incluído automaticamente com o Windows Server 2012 R2 e versões mais recentes.
    2. Execute o instalador **NDESConnectorSetup.exe**. Este instalador também instala o módulo de políticas para NDES e o Serviço Web CRP. O Serviço Web CRP, CertificateRegistrationSvc, é executado como uma aplicação no IIS.

    > [!NOTE]
    > Ao instalar o NDES para o Intune autónomo, o serviço CRP é instalado automaticamente com o Certificate Connector. Quando utiliza o Intune com o Configuration Manager, instala o Ponto de Registo de Certificados como uma função do sistema de sites à parte.

5. Quando lhe for pedido o certificado de cliente do Certificate Connector, selecione **Selecionar** e o certificado de **autenticação de cliente** que instalou no Servidor NDES no Passo 4.

    Após selecionar o certificado de autenticação de cliente, é encaminhado para a superfície do **Certificado de Cliente do Microsoft Intune Certificate Connector** . Embora o certificado que selecionou não seja apresentado, selecione **Seguinte** para ver as propriedades do certificado. Selecione **Seguinte** e, em seguida, **Instalar**.

    > [!IMPORTANT]
    > A Configuração de Segurança Avançada do Internet Explorer [tem de estar desativada no servidor do NDES](https://technet.microsoft.com/library/cc775800(v=WS.10).aspx) que aloja o Intune Certificate Connector.

6. Após o assistente ser concluído, mas antes de o fechar, selecione a opção para **Iniciar a IU do Certificate Connector**.

    > [!TIP]
    > Se fechar o assistente antes de iniciar a IU do Certificate Connector, pode abri-lo novamente ao executar o seguinte comando:
    >
    > \NDESConnectorUI\NDESConnectorUI.exe < install_Path >

7. Na IU do **Certificate Connector** :

    Selecione **Iniciar Sessão** e introduza as suas credenciais de administrador do serviço Intune ou as credenciais de administrador inquilino com a permissão de administração global. Depois de iniciar sessão, o Intune Certificate Connector transfere um certificado a partir do Intune. Este certificado é utilizado para efeitos de autenticação entre o conector e o Intune.

    > [!IMPORTANT]
    > A conta de utilizador tem de ser atribuída a uma licença válida do Intune. Se a conta de utilizador não tiver uma licença válida do Intune, o ficheiro NDESConnectorUI.exe irá falhar.

    Se a sua organização utilizar um servidor proxy e o proxy for necessário para o servidor do NDES aceder à Internet, selecione **Utilizar servidor proxy**. Em seguida, introduza o nome do servidor proxy, a porta e as credenciais de conta para ligar.

    Selecione o separador **Avançadas** e, em seguida, introduza as credenciais para uma conta que tenha permissão para **Emitir e Gerir Certificados** na sua Autoridade de Certificados emissora. **Aplique** as suas alterações.

    Agora, pode fechar a IU do Certificate Connector.

8. Abra uma linha de comandos, introduza **services.msc** e, em seguida, prima **Enter**. Clique com o botão direito do rato em **Intune Connector Service** > **Reiniciar**.

Para se certificar de que o serviço está em execução, abra um browser e introduza o seguinte URL. O mesmo deverá devolver um erro **403**:

`http://<FQDN_of_your_NDES_server>/certsrv/mscep/mscep.dll`

> [!NOTE]
> É incluído suporte para o TLS 1.2 com o Certificate Connector do NDES. Assim, se o servidor com o Certificate Connector do NDES instalado suportar o TLS 1.2, será utilizado o TLS 1.2. Se o servidor não suportar o TLS 1.2, será utilizado o TLS 1.1. Atualmente, é utilizado o TLS 1.1 para a autenticação entre os dispositivos e o servidor.

## <a name="create-a-scep-certificate-profile"></a>Criar um perfil de certificado SCEP

1. No [portal do Azure](https://portal.azure.com), selecione **Todos os serviços**, filtre o **Intune** e selecione **Microsoft Intune**.
2. Selecione **Configuração do dispositivo** > **Perfis** > **Criar perfil**.
3. Introduza um **Nome** e uma **Descrição** para o perfil de certificado SCEP.
4. Na lista pendente **Plataforma**, selecione a plataforma do dispositivo para este certificado SCEP. Atualmente, pode selecionar uma das seguintes plataformas para definições de restrição de dispositivos:
   - **Android**
   - **Android Enterprise**
   - **iOS**
   - **macOS**
   - **Windows Phone 8.1**
   - **Windows 8.1 e posterior**
   - **Windows 10 e posterior**
5. Na lista pendente **Tipo de perfil**, selecione **Certificado SCEP**.
6. Introduza as seguintes definições:

   - **Tipo de certificado**: Escolher **utilizador** para certificados de utilizador. Selecione **Dispositivo** para dispositivos sem utilizador, como quiosques. Os certificados de **Dispositivo** estão disponíveis para as seguintes plataformas:  
     - iOS
     - Windows 8.1 e posterior
     - Windows 10 e posterior
     - Android Enterprise

   - **Formato de nome de requerente**: Selecione como o Intune cria automaticamente o nome do requerente no pedido de certificado. As opções variam se selecionar o tipo de certificado **Utilizador** ou **Dispositivo**. 

        **Tipo de certificado Utilizador**  

        Pode incluir o endereço de e-mail do utilizador no nome do requerente. Escolha entre:

        - **Não configurado**
        - **Nome comum**
        - **Nome comum, incluindo o e-mail**
        - **Nome comum como e-mail**
        - **Identidade Internacional do Equipamento Móvel (IMEI)**
        - **Número de série**
        - **Custom**: Quando seleciona esta opção, uma **personalizado** também é apresentada a caixa de texto. Utilize este campo para introduzir um formato de nome de requerente personalizado, incluindo variáveis. Formato personalizado suporta duas variáveis: **Nome comum (CN)** e **E-Mail (E)**. O **Nome Comum (CN)** pode ser definido para qualquer uma das seguintes variáveis:

            - **CN = {{UserName}}**: O nome do principal de utilizador do utilizador, por exemplo, janedoe@contoso.com
            - **CN = {{AAD_Device_ID}}**: Um ID atribuído ao registar um dispositivo no Azure Active Directory (AD). Este ID é normalmente utilizado na autenticação com o Azure AD.
            - **CN = {{SERIALNUMBER}}**: Número de série exclusivo (SN) normalmente utilizado pelo fabricante para identificar um dispositivo
            - **CN = {{IMEINumber}}**: O número exclusivo de identidade internacional de equipamento a móvel (IMEI) utilizado para identificar um telemóvel
            - **CN = {{OnPrem_Distinguished_Name}}**: Uma sequência de nomes únicos relativos separados por vírgula, por exemplo `CN=Jane Doe,OU=UserAccounts,DC=corp,DC=contoso,DC=com`

                Para utilizar a variável `{{OnPrem_Distinguished_Name}}`, não se esqueça de sincronizar o atributo de utilizador `onpremisesdistingishedname` com o [Azure AD Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) com o seu Azure AD.

            - **CN = {{onPremisesSamAccountName}}**: Os administradores podem sincronizar o atributo samAccountName do Active Directory para o Azure AD com o Azure AD connect para um atributo chamado `onPremisesSamAccountName`. O Intune pode substituir essa variável como parte de um pedido de emissão de certificado no requerente de um certificado SCEP.  O atributo samAccountName é o nome de início de sessão de utilizador utilizado para suportar clientes e servidores de uma versão anterior do Windows (anterior ao Windows 2000). O formato do nome de início de sessão do utilizador é: `DomainName\testUser` ou apenas `testUser`.

                Para utilizar a variável `{{onPremisesSamAccountName}}`, não se esqueça de sincronizar o atributo de utilizador `onPremisesSamAccountName` com o [Azure AD Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) com o seu Azure AD.

            Através de uma combinação de uma ou várias destas variáveis e cadeias estáticas, pode criar um formato de nome de requerente personalizado, como o seguinte:  

            **CN={{UserName}},E={{EmailAddress}},OU=Mobile,O=Finance Group,L=Redmond,ST=Washington,C=US**

            Neste exemplo, criou um formato de nome de requerente que, além das variáveis CN e E, utiliza cadeias para os valores Unidade Organizacional, Organização, Localização, Estado e País. O artigo [função CertStrToName](https://msdn.microsoft.com/library/windows/desktop/aa377160.aspx) descreve esta função e as cadeias suportadas da mesma.

        **Tipo de certificado Dispositivo**  

        Ao utilizar o tipo de certificado **Dispositivo**, também pode utilizar as seguintes variáveis de certificado de dispositivo para o valor:  

        ```
        "{{AAD_Device_ID}}",
        "{{Device_Serial}}",
        "{{Device_IMEI}}",
        "{{SerialNumber}}",
        "{{IMEINumber}}",
        "{{AzureADDeviceId}}",
        "{{WiFiMacAddress}}",
        "{{IMEI}}",
        "{{DeviceName}}",
        "{{FullyQualifiedDomainName}}",
        "{{MEID}}",
        ```

        Estas variáveis podem ser adicionadas com texto estático numa caixa de texto de valor personalizado. Por exemplo, o nome comum pode ser adicionado como `CN = {{DeviceName}}text`.

        > [!IMPORTANT]
        >  - No texto estático do requerente, as chavetas **{ }** que não incluírem uma variável resultarão num erro. 
        >  - Ao utilizar uma variável de certificado de dispositivo, coloque a variável entre chavetas **{ }**.
        >  - `{{FullyQualifiedDomainName}}` só funciona em dispositivos com Windows e dispositivos associados a um domínio. 
        >  -  Ao utilizar as propriedades do dispositivo, tais como o IMEI, o Número de Série e o Nome de Domínio Completamente Qualificado, no requerente ou no SAN de um certificado de dispositivo, tenha em atenção que estas propriedades podem ser falsificadas por uma pessoa que tenha acesso ao dispositivo.
        >  - O perfil não será instalado no dispositivo se as variáveis do dispositivo especificadas não forem suportadas. Por exemplo, se {{IMEI}} for utilizado no nome do requerente do perfil SCEP atribuído a um dispositivo que não tenha um número IMEI, a instalação do perfil irá falhar. 


   - **Nome alternativo do requerente**: Introduza a forma como o Intune cria automaticamente os valores para o nome alternativo do requerente (SAN) no pedido de certificado. As opções variam se selecionar o tipo de certificado **Utilizador** ou **Dispositivo**. 

        **Tipo de certificado Utilizador**  

        Estão disponíveis os seguintes atributos:

        - Endereço de e-mail
        - Nome principal de utilizador (UPN)

            Por exemplo, se selecionar um tipo de certificado de utilizador, pode incluir o nome principal de utilizador (UPN) no nome alternativo do requerente. Se um certificado de cliente for utilizado para autenticar um Servidor de Políticas de Rede, defina o nome alternativo do requerente como UPN. 

        **Tipo de certificado Dispositivo**  

        Uma caixa de texto em formato de tabela que pode personalizar. Estão disponíveis os seguintes atributos:

        - DNS

        Com o tipo de certificado **Dispositivo**, pode utilizar as seguintes variáveis de certificado de dispositivo para o valor:  

        ```
        "{{AAD_Device_ID}}",
        "{{Device_Serial}}",
        "{{Device_IMEI}}",
        "{{SerialNumber}}",
        "{{IMEINumber}}",
        "{{AzureADDeviceId}}",
        "{{WiFiMacAddress}}",
        "{{IMEI}}",
        "{{DeviceName}}",
        "{{FullyQualifiedDomainName}}",
        "{{MEID}}",
        ```

        Estas variáveis podem ser adicionadas com texto estático na caixa de texto de valor personalizado. Por exemplo, o atributo de DNS pode ser adicionado como `DNS name = {{AzureADDeviceId}}.domain.com`.

        > [!IMPORTANT]
        >  - No texto estático do SAN, as chavetas **{ }**, as barras verticais **|** e os pontos e vírgulas **;** não funcionam. 
        >  - Ao utilizar uma variável de certificado de dispositivo, coloque a variável entre chavetas **{ }**.
        >  - `{{FullyQualifiedDomainName}}` só funciona em dispositivos com Windows e dispositivos associados a um domínio. 
        >  -  Ao utilizar as propriedades do dispositivo, tais como o IMEI, o Número de Série e o Nome de Domínio Completamente Qualificado, no requerente ou no SAN de um certificado de dispositivo, tenha em atenção que estas propriedades podem ser falsificadas por uma pessoa que tenha acesso ao dispositivo.
        >  - O perfil não será instalado no dispositivo se as variáveis do dispositivo especificadas não forem suportadas. Por exemplo, se {{IMEI}} for utilizado no nome do requerente do perfil SCEP atribuído a um dispositivo que não tenha um número IMEI, a instalação do perfil irá falhar.  

   - **Período de validade do certificado**: Se tiver executado o `certutil - setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE` comando emissora AC, o que permite um período de validade personalizado, pode introduzir a quantidade de tempo restante até o certificado expirar.<br>Pode introduzir um valor inferior ao período de validade do modelo de certificado, mas não superior. Por exemplo, se o período de validade do certificado no modelo de certificado for dois anos, pode introduzir um valor de um ano, mas não um valor de cinco anos. O valor deve também ser inferior ao período de validade restante do certificado da AC emissora. 
   - **Fornecedor de armazenamento de chaves (KSP)** (Windows Phone 8.1, Windows 8.1, Windows 10): Introduza onde está armazenada a chave do certificado. Escolha um dos seguintes valores:
     - **Inscrever em KSP de Trusted Platform Module (TPM) se estiver presente, caso contrário, KSP de Software**
     - **Inscrever em KSP de Trusted Platform Module (TPM), caso contrário, ocorre uma falha**
     - **Inscrever em Passport, caso contrário, ocorre uma falha (Windows 10 e posterior)**
     - **Inscrever em KSP de Software**

   - **Utilização de chave**: Introduza as opções de utilização de chave para o certificado. As opções são:
     - **Cifragem de chaves**: Permitir a troca de chaves apenas quando a chave for encriptada
     - **Assinatura digital**: Permitir a troca de chaves apenas quando uma assinatura digital ajudar a proteger a chave
   - **Tamanho da chave (bits)**: Selecione o número de bits que está contido na chave
   - **Algoritmo hash** (Android, Windows Phone 8.1, Windows 8.1, Windows 10): Selecione um dos tipos de algoritmo hash disponíveis para utilizar com este certificado. Selecione o maior nível de segurança que os dispositivos de ligação suportam.
   - **Certificado de raiz**: Selecione um perfil de certificado de AC configurado anteriormente e atribuído para o utilizador e/ou o dispositivo de raiz. Este certificado da AC tem de ser o certificado de raiz da AC que emite o certificado que está a configurar neste perfil de certificado. Certifique-se de que atribuir este perfil de certificado de raiz fidedigna para o mesmo grupo atribuído no perfil de certificado SCEP.
   - **Utilização alargada da chave**: **Adicionar** objetivo de valores para o certificado. Na maioria dos casos, o certificado exige a **Autenticação de Cliente** para o utilizador ou dispositivo poder ser autenticado num servidor. Contudo, pode adicionar mais utilizações de chave conforme necessário.
   - **Definições de Inscrição**
     - **Limiar de renovação (%)**: Introduza a percentagem da duração do certificado que permanece antes do dispositivo pedir renovação do certificado.
     - **URLs do servidor SCEP**: Introduza um ou mais URLs para os servidores NDES que emitem certificados através de SCEP. Por exemplo, digite algo semelhante a `https://ndes.contoso.com/certsrv/mscep/mscep.dll`.
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

Para obter informações sobre como atribuir perfis, veja [Atribuir perfis de dispositivos](device-profile-assign.md).

## <a name="intune-connector-setup-verification-and-troubleshooting"></a>Verificação e resolução de problemas de configuração do Intune Connector

Para resolver problemas e verificar a configuração do Intune Connector, veja [Certificate Authority script samples](https://aka.ms/intuneconnectorverificationscript) (Exemplos de script da Autoridade de Certificação)

## <a name="intune-connector-events-and-diagnostic-codes"></a>Códigos de diagnóstico e eventos do Intune Connector

A partir da versão 6.1806.X.X, o Serviço do Intune Connector regista eventos no **Visualizador de Eventos** (**Registos de Aplicações e Serviços** > **Microsoft Intune Connector**). Utilize estes eventos para o ajudar a resolver potenciais problemas na configuração do Intune Connector. Estes eventos registam sucessos e falhas de uma operação e também contêm códigos de diagnóstico com mensagens que ajudam o administrador de TI a resolver problemas.

### <a name="event-ids-and-descriptions"></a>IDs e descrições do evento

> [!NOTE]
> Para obter detalhes sobre os Códigos de Diagnóstico Relacionados para cada evento, utilize a tabela **Códigos de diagnóstico** (neste artigo).

| ID do Evento      | Nome do Evento    | Descrição do Evento | Códigos de Diagnóstico Relacionados |
| ------------- | ------------- | -------------     | -------------            |
| 10010 | StartedConnectorService  | Serviço de conector iniciado | 0x00000000, 0x0FFFFFFF |
| 10020 | StoppedConnectorService  | Serviço de conector parado | 0x00000000, 0x0FFFFFFF |
| 10100 | CertificateRenewal_Success  | Certificado de inscrição do conector renovado com êxito | 0x00000000, 0x0FFFFFFF |
| 10102 | CertificateRenewal_Failure  | Não foi possível renovar o certificado de inscrição do conector. Reinstale o conector. | 0x00000000, 0x00000405, 0x0FFFFFFF |
| 10302 | RetrieveCertificate_Error  | Falha ao obter o certificado de inscrição do conector do registo. Reveja os detalhes do evento para o thumbprint do certificado relacionado com este evento. | 0x00000000, 0x00000404, 0x0FFFFFFF |
| 10301 | RetrieveCertificate_Warning  | Verifique as informações de diagnóstico nos detalhes do evento. | 0x00000000, 0x00000403, 0x0FFFFFFF |
| 20100 | PkcsCertIssue_Success  | Certificado PKCS emitido com êxito. Reveja os detalhes do evento para obter o ID do dispositivo, o ID do utilizador, o nome CA, o nome do modelo de certificado e o thumbprint do certificado relacionados com este evento. | 0x00000000, 0x0FFFFFFF |
| 20102 | PkcsCertIssue_Failure  | Falha ao emitir um certificado PKCS. Reveja os detalhes do evento para obter o ID do dispositivo, o ID do utilizador, o nome CA, o nome do modelo de certificado e o thumbprint do certificado relacionados com este evento. | 0x00000000, 0x00000400, 0x00000401, 0x0FFFFFFF |
| 20200 | RevokeCert_Success  | Certificado revogado com êxito. Reveja os detalhes do evento para o ID do dispositivo, o ID do utilizador, o nome CA e o número de série do certificado relacionados com este evento. | 0x00000000, 0x0FFFFFFF |
| 20202 | RevokeCert_Failure | Falha ao revogar o certificado. Reveja os detalhes do evento para o ID do dispositivo, o ID do utilizador, o nome CA e o número de série do certificado relacionados com este evento. Para obter mais informações, veja os Registos NDES SVC.   | 0x00000000, 0x00000402, 0x0FFFFFFF |
| 20300 | Upload_Success | Os dados de pedido ou revogação do certificado foram carregados com êxito. Reveja os detalhes do evento para obter os detalhes do carregamento. | 0x00000000, 0x0FFFFFFF |
| 20302 | Upload_Failure | Falha ao carregar os dados de pedido ou revogação do certificado. Reveja os detalhes do evento > Estado de Carregamento para determinar o ponto de falha.| 0x00000000, 0x0FFFFFFF |
| 20400 | Download_Success | Foi transferido com êxito o pedido para assinar um certificado, transferir um certificado de cliente ou revogar um certificado. Reveja os detalhes do evento para obter os detalhes da transferência.  | 0x00000000, 0x0FFFFFFF |
| 20402 | Download_Failure | Falha ao transferir o pedido para assinar um certificado, transferir um certificado de cliente ou revogar um certificado. Reveja os detalhes do evento para obter os detalhes da transferência. | 0x00000000, 0x0FFFFFFF |
| 20500 | CRPVerifyMetric_Success  | Ponto de Registo de Certificados verificou com êxito um desafio de cliente | 0x00000000, 0x0FFFFFFF |
| 20501 | CRPVerifyMetric_Warning  | O Ponto de Registo de Certificados foi concluído, mas rejeitou o pedido. Consulte o código de diagnóstico e a mensagem para obter mais detalhes. | 0x00000000, 0x00000411, 0x0FFFFFFF |
| 20502 | CRPVerifyMetric_Failure  | Falha do Ponto de Registo de Certificados ao verificar um desafio de cliente. Consulte o código de diagnóstico e a mensagem para obter mais detalhes. Veja os detalhes da mensagem do evento para obter o ID de Dispositivo que corresponde ao desafio. | 0x00000000, 0x00000408, 0x00000409, 0x00000410, 0x0FFFFFFF |
| 20600 | CRPNotifyMetric_Success  | O Ponto de Registo de Certificados concluiu com êxito o processo de notificação e enviou o certificado para o dispositivo cliente. | 0x00000000, 0x0FFFFFFF |
| 20602 | CRPNotifyMetric_Failure  | O Ponto de Registo de Certificados não conseguiu concluir o processo de notificação. Veja os detalhes da mensagem do evento para obter informações sobre o pedido. Verifique a ligação entre o servidor do NDES e a AC. | 0x00000000, 0x0FFFFFFF |

### <a name="diagnostic-codes"></a>Códigos de diagnóstico

| Código de Diagnóstico | Nome do Diagnóstico | Mensagem de Diagnóstico |
| -------------   | -------------   | -------------      |
| 0x00000000 | Êxito  | Êxito |
| 0x00000400 | PKCS_Issue_CA_Unavailable  | A autoridade de certificação não é válida ou está inacessível. Verifique se a autoridade de certificação está disponível e se o servidor consegue comunicar com a mesma. |
| 0x00000401 | Symantec_ClientAuthCertNotFound  | O certificado Symantec Client Auth não foi encontrado no arquivo de certificados local. Veja o artigo [Instalar o certificado de autorização de registo da Symantec](https://docs.microsoft.com/intune/certificates-symantec-configure#install-the-symantec-registration-authorization-certificate) para obter mais informações.  |
| 0x00000402 | RevokeCert_AccessDenied  | A conta especificada não tem permissões para revogar um certificado de AC. Veja o campo Nome da AC nos detalhes da mensagem de evento para determinar a AC emissora.  |
| 0x00000403 | CertThumbprint_NotFound  | Não foi possível localizar um certificado que corresponda à sua pesquisa. Inscreva o conector do certificado e tente novamente. |
| 0x00000404 | Certificate_NotFound  | Não foi possível localizar um certificado que corresponda às informações fornecidas. Volte a inscrever o conector do certificado e tente novamente. |
| 0x00000405 | Certificate_Expired  | Um certificado expirou. Volte a inscrever o conector do certificado para renovar o certificado e tente novamente. |
| 0x00000408 | CRPSCEPCert_NotFound  | Não foi possível encontrar o certificado de Encriptação CRP. Verifique se o NDES e o Intune Connector estão configurados corretamente. |
| 0x00000409 | CRPSCEPSigningCert_NotFound  | Não foi possível obter o certificado de assinatura. Verifique se o Serviço do Intune Connector está configurado corretamente e se está em execução. Verifique também se os eventos de transferência de certificado foram efetuados com êxito. |
| 0x00000410 | CRPSCEPDeserialize_Failed  | Falha ao anular a serialização do pedido de desafio SCEP. Verifique se o NDES e o Conector do Intune estão configurados corretamente. |
| 0x00000411 | CRPSCEPChallenge_Expired  | Pedido recusado devido a um desafio de certificado expirado. O dispositivo cliente pode tentar novamente depois de obter um novo desafio do servidor de gestão. |
| 0x0FFFFFFFF | Unknown_Error  | Não conseguimos concluir o pedido porque ocorreu um erro do lado do servidor. Tente novamente. |

## <a name="next-steps"></a>Passos Seguintes

- [Utilizar certificados PKCS](certficates-pfx-configure.md) ou [emitir certificados PKCS de um serviço Web de gestão de PKI da Symantec](certificates-symantec-configure.md)
- [Adicionar um CA de terceiros para utilizar o SCEP com o Intune](certificate-authority-add-scep-overview.md)
