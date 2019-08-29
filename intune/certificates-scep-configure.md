---
title: Configurar a infraestrutura para dar suporte a perfis de certificado SCEP com o Microsoft Intune-Azure | Microsoft Docs
description: Para usar o SCEP no Microsoft Intune, configure seu domínio do AD local, crie uma autoridade de certificação, configure o servidor NDES e instale o conector de certificado do Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 08/28/2019
ms.topic: article
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 76cd6084815a9f63e653a63d36ba8265a7a0fbd6
ms.sourcegitcommit: cf40f641af4746a1e34edd980dc6ec96fd040126
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/28/2019
ms.locfileid: "70122493"
---
# <a name="configure-infrastructure-to-support-scep-with-intune"></a>Configurar a infraestrutura para dar suporte ao SCEP com o Intune  
  
O Intune dá suporte ao uso do protocolo SCEP (SCEP) para [autenticar conexões com seus aplicativos e recursos corporativos](certificates-configure.md). O SCEP usa o certificado de autoridade de certificação (CA) para proteger a troca de mensagens da CSR (solicitação de assinatura de certificado). Quando sua infraestrutura oferece suporte a SCEP, você pode usar perfis de *certificado SCEP* do Intune (um tipo de perfil de dispositivo no Intune) para implantar os certificados em seus dispositivos. O Microsoft Intune Certificate Connector é necessário para usar perfis de certificado SCEP com o Intune ao usar uma autoridade de certificação de serviços de certificados Active Directory. O conector não é necessário ao usar [autoridades de certificação de terceiros](certificate-authority-add-scep-overview.md#set-up-third-party-ca-integration).  

As informações neste artigo podem ajudá-lo a configurar sua infraestrutura para dar suporte ao SCEP ao usar os serviços de certificados Active Directory. Depois que sua infraestrutura estiver configurada, você poderá [criar e implantar perfis de certificado SCEP](certificates-profile-scep.md) com o Intune.  

> [!TIP]  
> O Intune também dá suporte ao uso de [padrões de criptografia de chave pública #12 certificados](certficates-pfx-configure.md).  


## <a name="prerequisites-for-using-scep-for-certificates"></a>Pré-requisitos para usar o SCEP para certificados  
Antes de prosseguir, certifique-se de ter [criado e implantado um perfil de *certificado confiável* ](certificates-configure.md#export-the-trusted-root-ca-certificate) para dispositivos que USARÃO perfis de certificado SCEP. Os perfis de certificado SCEP referenciam diretamente o perfil de certificado confiável que você usa para provisionar dispositivos com um certificado de autoridade de certificação raiz confiável.  

### <a name="servers-and-server-roles"></a>Servidores e funções de servidor  
A seguinte infraestrutura local deve ser executada em servidores que ingressaram no domínio em seu Active Directory, com exceção do servidor proxy de aplicativo Web.  
- **Autoridade de certificação** – use uma AC (autoridade de certificação) corporativa dos serviços de certificados do Microsoft Active Directory que é executada em uma edição Enterprise do Windows Server 2008 R2 com o Service Pack 1 ou posterior. A versão do Windows Server que você usa deve permanecer em suporte pela Microsoft. Não é suportada uma AC Autónoma. Para obter mais informações, consulte [instalar a autoridade de certificação](http://technet.microsoft.com/library/jj125375.aspx). Se a sua AC executar o Windows Server 2008 R2 SP1, você deverá [instalar o hotfix em KB2483564](http://support.microsoft.com/kb/2483564/).  

- **Função de servidor NDES** – você deve configurar uma função de servidor NDES (serviço de registro de dispositivo de rede) no Windows Server 2012 R2 ou posterior. Em uma seção posterior deste artigo, orientaremos você na [instalação do NDES](#set-up-ndes).  

  - O servidor que hospeda o NDES deve estar ingressado no domínio e na mesma floresta que a autoridade de certificação corporativa.  
  - Você não pode usar o NDES instalado no servidor que hospeda a AC corporativa.  
  - Você instalará o Microsoft Intune o conector de certificado no mesmo servidor que hospeda o NDES.  

  Para saber mais sobre o NDES, consulte [diretrizes de serviço de registro de dispositivo de rede](http://technet.microsoft.com/library/hh831498.aspx) na documentação do Windows Server e [usando um módulo de política com o serviço de registro de dispositivo de rede](https://technet.microsoft.com/library/dn473016.aspx).  

- **Microsoft Intune Certificate Connector** – o Microsoft Intune Certificate Connector é necessário para usar perfis de certificado SCEP com o Intune. Este artigo o orientará durante a [instalação desse conector](#install-the-intune-certificate-connector).  

  O conector dá suporte ao modo de padrão FIPS (FIPS). O FIPS não é necessário, mas quando está habilitado, você pode emitir e revogar certificados.  
  - O conector deve ser executado no mesmo servidor que a função de servidor NDES, um servidor que executa o Windows Server 2012 R2 ou posterior.  
  - A estrutura do .NET 4,5 é exigida pelo conector do e é incluída automaticamente com o Windows Server 2012 R2.  
  - A configuração de segurança reforçada do Internet Explorer [deve ser desabilitada no servidor que hospeda o NDES](https://technet.microsoft.com/library/cc775800(v=WS.10).aspx) e o Microsoft Intune Certificate Connector.  

A seguinte infraestrutura local é opcional:  
  Para permitir que os dispositivos na Internet obtenham certificados, você precisa publicar sua URL de NDES externamente em sua rede corporativa. Você pode usar o Proxy de Aplicativo do AD do Azure, o servidor proxy de aplicativo Web ou outro proxy reverso.
  
- **Proxy de aplicativo do AD do Azure** (opcional) – você pode usar o Proxy de Aplicativo do AD do Azure em vez de um servidor de proxy de aplicativo Web (WAP) dedicado para publicar a URL de NDES na Internet. Isso permite que os dispositivos voltados para a intranet e para a Internet obtenham certificados. Para mais informações, consulte [How to provide secure remote access to on-premises applications (Como fornecer acesso remoto seguro a aplicações no local)](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy). 

- **Servidor proxy de aplicativo Web** (opcional)-Use um servidor que executa o Windows Server 2012 R2 ou posterior como um servidor de proxy de aplicativo Web (WAP) para publicar sua URL de NDES na Internet.  Isso permite que os dispositivos voltados para a intranet e para a Internet obtenham certificados.

  O servidor que aloja o WAP [tem de instalar uma atualização](http://blogs.technet.com/b/ems/archive/2014/12/11/hotfix-large-uri-request-in-web-application-proxy-on-windows-server-2012-r2.aspx) que ativa o suporte para os URLs longos que são utilizados pelo Serviço de Inscrição de Dispositivos de Rede. Esta atualização está incluída no [rollup da atualização de dezembro de 2014](http://support.microsoft.com/kb/3013769)ou individualmente a partir do [KB3011135](http://support.microsoft.com/kb/3011135).  

  O servidor WAP deve ter um certificado SSL que corresponda ao nome que é publicado em clientes externos e confia no certificado SSL que é usado no computador que hospeda o serviço de NDES. Esses certificados permitem que o servidor WAP encerre a conexão SSL de clientes e crie uma nova conexão SSL com o serviço NDES.  

  Para obter mais informações, veja [Plan certificates for WAP](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn383650(v=ws.11)#plan-certificates) (Planear certificados para o WAP) e as [informações gerais sobre os servidores WAP](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn584113(v=ws.11)).

### <a name="accounts"></a>Contas   
- **Conta de serviço de NDES** -antes de configurar o NDES, identifique uma conta de usuário de domínio para usar como a conta de serviço de NDES. Você especificará essa conta ao configurar modelos em sua AC emissora, antes de configurar o NDES.  

  Essa conta deve ter os seguintes direitos no servidor que hospeda o NDES:  
  - **Logon local**  
  - **Fazer logon como um serviço**  
  - **Fazer logon como um trabalho em lotes**  

  Para obter mais informações, consulte [criar uma conta de usuário de domínio para atuar como a conta de serviço de NDES](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831498(v=ws.11)#to-create-a-domain-user-account-to-act-as-the-ndes-service-account). 
- **Acesso ao computador que hospeda o serviço de NDES** – você precisará de uma conta de usuário de domínio com permissões para instalar e configurar funções do Windows Server no servidor onde você instala o NDES.  

- **Acesso à autoridade de certificação** -você precisará de uma conta de usuário de domínio que tenha direitos para gerenciar sua autoridade de certificação.  

### <a name="network-requirements"></a>Requisitos da rede

É recomendável publicar o serviço de NDES por meio de um proxy reverso, como o [proxy de aplicativo do Azure AD, o proxy de acesso via Web](https://azure.microsoft.com/documentation/articles/active-directory-application-proxy-publish/)ou um proxy de terceiros. Se você não usar um proxy reverso, permita o tráfego TCP na porta 443 de todos os hosts e endereços IP na Internet para o serviço de NDES.  

Permitir todas as portas e protocolos necessários para a comunicação entre o serviço NDES e qualquer infraestrutura de suporte em seu ambiente. Por exemplo, o computador que hospeda o serviço de NDES precisa se comunicar com a AC, os servidores DNS, os controladores de domínio e, possivelmente, outros serviços ou servidores em seu ambiente, como Configuration Manager.

### <a name="certificates-and-templates"></a>Certificados e modelos

Os seguintes certificados e modelos são usados quando você usa o SCEP.

|Objeto    |Detalhes    |
|----------|-----------|
|**Modelo de certificado SCEP**         |Modelo que você configurará em sua AC emissora usada para fullfilr as solicitações de SCEP de dispositivos. |
|**Certificado de autenticação de cliente** |Solicitado da AC emissora ou da AC pública.<br /> Você instala esse certificado no computador que hospeda o serviço de NDES e é usado pelo conector de certificado do Intune.<br /> Se o certificado tiver os usos de chave de *autenticação* de *cliente* e de servidor definidos (**usos avançados de chave**) no modelo de autoridade de certificação que você usa para emitir esse certificado. Você pode usar o mesmo certificado para autenticação de servidor e cliente. |
|**Certificado de autenticação do servidor** |Certificado do servidor Web solicitado da AC emissora ou da AC pública.<br /> Você instala e associa esse certificado SSL no IIS no computador que hospeda o NDES.<br />Se o certificado tiver os usos de chave de *autenticação* de *cliente* e de servidor definidos (**usos avançados de chave**) no modelo de autoridade de certificação que você usa para emitir esse certificado. Você pode usar o mesmo certificado para autenticação de servidor e cliente. |
|**Certificado da AC de Raiz Fidedigna**       |Para usar um perfil de certificado SCEP, os dispositivos devem confiar em sua AC (autoridade de certificação) raiz confiável. Use um *perfil de certificado confiável* no Intune para provisionar o certificado de AC raiz confiável para usuários e dispositivos. <br/><br/> **-** Use um único certificado de autoridade de certificação raiz confiável por plataforma de sistema operacional e associe esse certificado a cada perfil de certificado confiável que você criar. <br /><br /> **-** Você pode usar certificados de autoridade de certificação raiz confiáveis adicionais quando necessário. Por exemplo, você pode usar certificados adicionais para fornecer uma relação de confiança a uma AC que assina os certificados de autenticação de servidor para seus pontos de acesso Wi-Fi. Crie certificados de autoridade de certificação raiz confiáveis adicionais para a emissão de CAs.  No perfil de certificado SCEP criado no Intune, certifique-se de especificar o perfil de AC raiz confiável para a AC emissora.<br/><br/> Para obter informações sobre o perfil de certificado confiável, consulte [exportar o certificado de AC raiz confiável](certificates-configure.md#export-the-trusted-root-ca-certificate) e [criar perfis de certificado confiável](certificates-configure.md#create-trusted-certificate-profiles) em *usar certificados para autenticação no Intune*. |

## <a name="configure-the-certification-authority"></a>Configurar a autoridade de certificação

Nas seções a seguir, você vai:
- Configure e publique o modelo necessário para o NDES. 
- Defina as permissões necessárias para revogação de certificado. 

As seções a seguir exigem conhecimento do Windows Server 2012 R2 ou posterior e dos serviços de certificados Active Directory (AD CS).  

### <a name="access-your-issuing-ca"></a>Acessar sua AC emissora

1. Entre em sua AC emissora com uma conta de domínio com direitos suficientes para gerenciar a autoridade de certificação.  
2. Abra o MMC (console de gerenciamento Microsoft) da autoridade de certificação. **Execute** ' certsrv. msc ' ou, em **Gerenciador do servidor**, clique em **ferramentas**e, em seguida, clique em **autoridade de certificação**.
3. Selecione o nó **modelos de certificado** e clique em **ação** > **gerenciar**.

### <a name="create-the-scep-certificate-template"></a>Criar o modelo de certificado SCEP

1. Crie um modelo de certificado v2 (com a compatibilidade do Windows 2003) para uso como o modelo de certificado SCEP. Pode:  
   - Use o snap-in de *modelos de certificado* para criar um novo modelo personalizado.  
   - Copie um modelo existente (como o modelo de usuário) e, em seguida, atualize a cópia para usar como modelo NDES.
 
2. Defina as seguintes configurações nas guias especificadas do modelo:
   - **Geral**:
     - Desmarque **publicar certificado em Active Directory**.
     - Especifique um **nome de exibição de modelo** amigável para que você possa identificar esse modelo mais tarde.  

   - **Nome da entidade**:  
     - Selecione **fornecer na solicitação**. A segurança é imposta pelo módulo de política do Intune para NDES.  

     ![Modelo, separador nome do requerente](./media/certificates-scep-configure/scep-ndes-subject-name.jpg)
   - **Extensões**:  
     - Verifique se a **Descrição das políticas de aplicativo** inclui a **autenticação de cliente**.  
       > [!IMPORTANT]  
       > Adicione apenas as políticas de aplicativo que você precisa. Confirme as escolhas com os administradores de segurança.
 
     - Para modelos de certificado iOS e macOS, edite também o **uso da chave** e verifique se a **assinatura é a prova de origem** não está selecionada.

     ![Modelo, separador extensões](./media/certificates-scep-configure/scep-ndes-extensions.jpg)  

   - **Segurança**:  
     - Adicione a **conta de serviço de NDES**. Esta conta requer permissões de **leitura** e **registro** para este modelo.

     - Adicione contas adicionais para administradores do Intune que criarão perfis SCEP. Essas contas exigem permissões de **leitura** para o modelo para permitir que esses administradores naveguem até esse modelo durante a criação de perfis SCEP.  

     ![Modelo, separador segurança](./media/certificates-scep-configure/scep-ndes-security.jpg)  

   - **Tratamento de solicitação**:  
      A imagem a seguir é um exemplo. Sua configuração pode variar.  

     ![Modelo, separador processamento de pedidos](./media/certificates-scep-configure/scep-ndes-request-handling.png) 

   - **Requisitos de emissão**:  
     A imagem a seguir é um exemplo. Sua configuração pode variar.  

     ![Modelo, separador requisitos de emissão](./media/certificates-scep-configure/scep-ndes-issuance-reqs.jpg)  

3. Salve o modelo de certificado.  

### <a name="create-the-client-certificate-template"></a>Criar o modelo de certificado do cliente

O conector de certificado do Intune requer um certificado com o uso avançado de chave de *autenticação de cliente* e o nome da entidade igual ao FQDN do computador em que o conector está instalado. É necessário um modelo com as seguintes propriedades:

-  > **Políticas de aplicativo** de extensões devem conter **autenticação de cliente**
- **Nome da entidade** **fornecido na solicitação.**  > 

Se você já tiver um modelo que inclui essas propriedades, poderá reutilizá-lo; caso contrário, crie um novo modelo duplicando um existente ou criando um modelo personalizado.

### <a name="create-the-server-certificate-template"></a>Criar o modelo de certificado do servidor

As comunicações entre os dispositivos gerenciados e o IIS no servidor NDES usam HTTPS, o que requer o uso de um certificado. Você pode usar o modelo de certificado do **servidor Web** para emitir esse certificado. Ou, se você preferir ter um modelo dedicado, as seguintes propriedades serão necessárias:

-  > **Políticas de aplicativo** de extensões devem conter **autenticação de servidor**
- **Nome da entidade** **fornecido na solicitação.**  > 

> [!NOTE]  
> Se você tiver um certificado que satisfaça os dois requisitos dos modelos de certificado do cliente e do servidor, poderá usar um único certificado para o IIS e o conector de certificado do Intune.

### <a name="grant-permissions-for-certificate-revocation"></a>Conceder permissões para revogação de certificado

Para que o Intune possa revogar certificados que não são mais necessários, você deve conceder permissões na autoridade de certificação. 

No conector de certificado do Intune, você pode usar a conta do **sistema** de servidor NDES ou uma conta específica, como a **conta de serviço de NDES**.

1. No console da autoridade de certificação, clique com o botão direito do mouse no nome da autoridade de certificação e selecione **Propriedades**.
2. Na guia **segurança** , clique em **Adicionar**.
3. Permissão para **emitir e gerenciar certificados** :
   - Se você optar por usar a conta do **sistema**de servidor de NDES, forneça as permissões para o servidor NDES.
   - Se você optar por usar a **conta de serviço de NDES**, forneça permissões para essa conta em vez disso.

### <a name="modify-the-validity-period-of-the-certificate-template"></a>Modificar o período de validade do modelo de certificado

É opcional modificar o período de validade do modelo de certificado.  

Depois [de criar o modelo de certificado SCEP](#create-the-scep-certificate-template), você pode editar o modelo para examinar o **período de validade** na guia **geral** .  

Por predefinição, o Intune utiliza o valor configurado no modelo. No entanto, você pode configurar a AC para permitir que o solicitante Insira um valor diferente, e esse valor pode ser definido de dentro do console do Intune.  

> [!IMPORTANT]  
> Para iOS e macOS, sempre use um valor definido no modelo.  

#### <a name="to-configure-a-value-that-can-be-set-from-within-the-intune-console"></a>Para configurar um valor que pode ser definido no console do Intune  
1. Na AC, execute os seguintes comandos:  
   -**certutil-setreg Policy\EditFlags + EDITF_ATTRIBUTEENDDATE**  
   -**net stop certsvc**  
   -**net start certsvc**  

2. Na AC emissora, utilize o snap-in Autoridade de Certificação para publicar o modelo de certificado. Selecione o **nó modelos de certificado** , selecione **ação** > **novo** > **modelo de certificado a ser emitido**e, em seguida, selecione o modelo de certificado que você criou na seção anterior.  

3. Valide se o modelo foi publicado exibindo-o na pasta **modelos de certificado** .  

## <a name="set-up-ndes"></a>Configurar o NDES  
Os procedimentos a seguir podem ajudá-lo a configurar o NDES (serviço de registro de dispositivo de rede) para uso com o Intune. Para obter mais informações sobre o NDES, consulte [diretrizes de serviço de registro de dispositivo de rede](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831498(v%3dws.11)).  

### <a name="install-the-ndes-service"></a>Instalar o serviço de NDES  
1. No servidor que hospedará seu serviço de NDES, entre como um **administrador corporativo**e, em seguida, use o [Assistente para adicionar funções e recursos](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831809(v=ws.11)) para instalar o NDES:

   1. No Assistente, selecione **Serviços de Certificados do Active Directory** para obter acesso aos Serviços de Função AD CS. Selecione **serviço de registro de dispositivo de rede**, desmarque **autoridade de certificação**e conclua o assistente.  

      > [!TIP]  
      > Em **andamento da instalação**, não selecione **fechar**. Em alternativa, selecione a ligação para **Configurar os Serviços de Certificados do Active Directory no servidor de destino**. O assistente de **configuração do AD CS** é aberto, que você usa para o próximo procedimento neste artigo, *Configurar o serviço de NDES*. Após a Configuração de AD CS abrir, pode fechar o assistente para Adicionar Funções e Funcionalidades.  

   2. Quando o NDES é adicionado ao servidor, o assistente também instala o IIS. Confirme se o IIS tem as seguintes configurações:  

      - **Servidor Web** > **Segurança** > **Filtragem de Pedidos**  
      - **Servidor Web** > **Desenvolvimento de Aplicações** > **ASP.NET 3.5**  

        A instalação do ASP.NET 3.5 instala o .NET Framework 3.5. Ao instalar o .NET Framework 3.5, instala tanto a funcionalidade **.NET Framework 3.5** principal como a **Ativação HTTP**.  
      - **Servidor Web** > **Desenvolvimento de Aplicações** > **ASP.NET 4.5**  

        A instalação do ASP.NET 4.5 instala o .NET Framework 4.5. Ao instalar o .NET Framework 4.5, instale a funcionalidade **.NET Framework 4.5** principal, o **ASP.NET 4.5** e a funcionalidade **Serviços do WCF** > **Ativação HTTP**.  

      - **Ferramentas de Gestão** > **Compatibilidade de Gestão do IIS 6** > **Compatibilidade com Metabase do IIS 6**  
      - **Ferramentas de Gestão** > **Compatibilidade de Gestão do IIS 6** > **Compatibilidade com WMI do IIS 6**  
      - No servidor, adicione a conta do serviço do NDES como membro do grupo local **IIS_IUSR**.  

2. No computador que hospeda o serviço NDES, execute o seguinte comando em um prompt de comando com privilégios elevados. O comando a seguir define o SPN da conta de serviço de NDES:  

   `setspn -s http/<DNS name of the computer that hosts the NDES service> <Domain name>\<NDES Service account name>`
   
   Por exemplo, se o computador que hospeda o serviço de NDES for nomeado **SERVER01**, seu domínio for **contoso.com**e a conta de serviço for **NDESService**, use:  

   `setspn –s http/Server01.contoso.com contoso\NDESService`  

### <a name="configure-the-ndes-service"></a>Configurar o serviço de NDES  

1. No computador que hospeda o serviço de NDES, abra o assistente de **configuração do AD CS** e faça as seguintes atualizações:  

   > [!TIP]  
   > Se você estiver continuando no último procedimento e clicou no link **configurar Active Directory serviços de certificados no servidor de destino** , esse assistente já deve estar aberto. Caso contrário, abra o Gestor de Servidores para aceder à configuração pós-implementação dos Serviços de Certificados do Active Directory.  

   - Em **serviços de função**, selecione o **serviço de registro de dispositivo de rede**.
   - Em **conta de serviço para NDES**, especifique a conta de serviço de NDES.
   - Em **AC para NDES**, clique em **selecionar**e selecione a AC emissora em que você configurou o modelo de certificado.
   - Em **Criptografia para NDES** defina o comprimento da chave para corresponder aos requisitos da sua empresa.
   - Em **Confirmação**, selecione **Configurar** para concluir o assistente.

2. Depois que o assistente for concluído, atualize a seguinte chave do registro no computador que hospeda o serviço de NDES:  
   `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Cryptography\MSCEP\`  

   Para atualizar essa chave, identifique a **finalidade** dos modelos de certificado (encontrada em sua guia **tratamento de solicitação** ). Em seguida, atualize a entrada de registro correspondente substituindo os dados existentes pelo nome do modelo de certificado (não o nome de exibição do modelo) que você especificou quando [criou o modelo de certificado](#create-the-scep-certificate-template).  

   A seguinte tabela mapeia o objetivo do modelo de certificado para os valores do registo:
   
   |Objetivo do modelo de certificado (no separador Manipulação de Pedidos)|Valor do registo a editar|Valor visto na consola de administração do Intune para o perfil SCEP|
   |------------------------|-------------------------|---|
   |Assinatura               |SignatureTemplate        |Assinatura Digital |
   |Encriptação              |EncryptionTemplate       |Cifragem de Chaves  |
   |Assinatura e encriptação|GeneralPurposeTemplate   |Cifragem de Chaves<br/>Assinatura Digital |  

   Por exemplo, se o Objetivo do seu modelo de certificado for **Encriptação**, edite o valor **EncryptionTemplate** para que tenha o mesmo nome do modelo de certificado.  

3. Configure a filtragem de solicitações do IIS para adicionar suporte no IIS para as URLs longas (consultas) que o serviço de NDES recebe.
   1. No Gerenciador do IIS, selecione a**configuração do recurso Editar** **filtragem** > de solicitação de **site** > padrão para abrir a página **Editar configurações de filtragem de solicitações** .  

   2. Configure as seguintes definições:  
      - **Tamanho máximo da URL (bytes)** = 65534  
      - **Cadeia de caracteres de consulta máxima (bytes)** = 65534  
   3. Selecione **OK** para salvar essa configuração e fechar o Gerenciador do IIS.  
   4. Valide essa configuração exibindo a seguinte chave do registro para confirmar se ela tem os valores indicados:  

      `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\HTTP\Parameters`    

      Os seguintes valores são definidos como entradas DWORD:  
      - Nome: **MaxFieldLength**, com um valor decimal de **65534**  
      - Nome: **MaxRequestBytes**, com um valor decimal de **65534**  
4. Reinicie o servidor que hospeda o serviço de NDES. Não use **iisreset**; iireset não conclui as alterações necessárias.  

5. Navegue até *http://* Server_FQDN */certsrv/MSCEP/MSCEP.dll*. Você deverá ver uma página de NDES semelhante à imagem a seguir:  

   ![Testar NDES](./media/certificates-scep-configure/scep-ndes-url.png)
  
   Se o endereço da Web retornar um **serviço 503 indisponível**, verifique o Visualizador de eventos dos computadores. Esse erro geralmente ocorre quando o pool de aplicativos é interrompido devido a uma [permissão ausente para a conta de serviço de NDES](#accounts).  
  
### <a name="install-and-bind-certificates-on-the-server-that-hosts-ndes"></a>Instalar e associar certificados no servidor que hospeda NDES  
> [!TIP]  
> No procedimento a seguir, você pode usar um único certificado para *autenticação de servidor* e *autenticação de cliente* quando esse certificado é configurado para atender aos critérios de ambos os usos. Os critérios para cada uso são descritos nas etapas 1 e 3 do procedimento a seguir.  

1. Solicite um certificado de **autenticação de servidor** da autoridade de certificação interna ou pública e, em seguida, instale o certificado no servidor.  

   Se o servidor usar um nome interno e externo para um único endereço de rede, o certificado de autenticação do servidor deverá ter:  

   - Um **nome de entidade** com um nome de servidor público externo.
   - Um **nome alternativo da entidade** que inclui o nome do servidor interno.  

2. Associar o certificado de autenticação de servidor no IIS:  
  
   1. Depois de instalar o certificado de autenticação de servidor, abra o **Gerenciador do IIS**e selecione o **site da Web padrão**. No painel **Ações**, selecione **Enlaces**.  
   1. Selecione **Adicionar**, defina o **Tipo** para **https** e, em seguida, confirme que a porta é **443**.  
   1. Para o **certificado SSL**, especifique o certificado de autenticação de servidor.  
 
3. No seu Servidor do NDES, peça e instale um certificado de **autenticação de cliente** à sua AC interna ou a uma autoridade de certificado pública.  

   O certificado de autenticação de cliente tem de ter as seguintes propriedades:  
   - **Uso avançado de chave**: Esse valor deve incluir a **autenticação do cliente**.  
   - **Nome da entidade**: O valor deve ser igual ao nome DNS do servidor em que você está instalando o certificado (o servidor de NDES).  

4. O servidor que hospeda o serviço de NDES agora está pronto para dar suporte ao conector de certificado do Intune.  

## <a name="install-the-intune-certificate-connector"></a>Instalar o conector de certificado do Intune  
O Microsoft Intune Certificate Connector é instalado no servidor que executa seu serviço de NDES. Não há suporte para usar o NDES ou o Intune Certificate Connector no mesmo servidor que a CA (autoridade de certificação) emissora.  

Para instalar o conector de certificado:  
1. Entre no portal do [Intune](https://aka.ms/intuneportal) com uma conta que tenha direitos para o Intune.  

2. Selecione **Configuração do dispositivo** > **Autoridade de Certificação** > **Adicionar**.  

3. Baixe e salve o conector para o arquivo SCEP. Guarde-o numa localização acessível a partir do servidor onde vai instalar o conector.

   ![ConnectorDownload](./media/certificates-scep-configure/download-certificates-connector.png)

4. Quando a transferência for concluída, aceda ao servidor que aloja a função Serviço de Inscrição de Dispositivos de Rede (NDES). Em seguida:  

   1. Confirme se o .NET 4,5 Framework está instalado, pois ele é exigido pelo conector de certificado do Intune. A estrutura do .NET 4,5 é incluída automaticamente com o Windows Server 2012 R2 e versões mais recentes.  
   2. Execute o instalador **NDESConnectorSetup.exe**. O instalador também instala o módulo de política para NDES e o serviço Web do CRP (ponto de registro de certificado) do IIS. O serviço Web do CRP, *CertificateRegistrationSvc*, é executado como um aplicativo no IIS.  

      - Ao instalar o NDES para o Intune autónomo, o serviço CRP é instalado automaticamente com o Certificate Connector. 
      - Ao usar o Intune com Configuration Manager, você instala o ponto de registro de certificado como uma função de sistema de site do Configuration Manager.  
5. Quando for solicitado o certificado do cliente para o conector de certificado, escolha **selecionar**e selecione o certificado de **autenticação de cliente** que você instalou em seu servidor NDES durante a etapa #3 do procedimento [instalar e associar certificados no servidor que hospeda o NDES](#install-and-bind-certificates-on-the-server-that-hosts-ndes) anteriormente neste artigo.  

   Depois de selecionar o certificado de autenticação de cliente, você será devolvido ao **certificado do cliente para Microsoft Intune Certificate Connector** superfície. Embora o certificado selecionado não seja mostrado, selecione **Avançar** para exibir as propriedades desse certificado. Selecione **Seguinte** e, em seguida, **Instalar**.

6. Após o assistente ser concluído, mas antes de o fechar, selecione a opção para **Iniciar a IU do Certificate Connector**.  

   Se você fechar o assistente antes de iniciar a interface do usuário do conector de certificado, poderá reabri-lo executando o seguinte comando: *< install_Path > \NDESConnectorUI\NDESConnectorUI.exe*

7. Na IU do **Certificate Connector** :  
   1. Selecione **Iniciar Sessão** e introduza as suas credenciais de administrador do serviço Intune ou as credenciais de administrador inquilino com a permissão de administração global.  
   2. A conta usada deve ser atribuída a uma licença válida do Intune.  
   3. Depois de entrar, o conector de certificado do Intune baixa um certificado do Intune. Este certificado é utilizado para efeitos de autenticação entre o conector e o Intune. Se a conta usada não tiver uma licença do Intune, o conector (NDESConnectorUI. exe) falhará ao obter o certificado do Intune.  

      Se a sua organização utilizar um servidor proxy e o proxy for necessário para o servidor do NDES aceder à Internet, selecione **Utilizar servidor proxy**. Em seguida, introduza o nome do servidor proxy, a porta e as credenciais de conta para ligar.  

    4. Selecione o separador **Avançadas** e, em seguida, introduza as credenciais para uma conta que tenha permissão para **Emitir e Gerir Certificados** na sua Autoridade de Certificados emissora. **Aplique** as suas alterações.  

    5. Agora, pode fechar a IU do Certificate Connector.  

8. Abra uma linha de comandos, introduza **services.msc** e, em seguida, prima **Enter**. Clique com o botão direito do rato em **Intune Connector Service** > **Reiniciar**.


Para se certificar de que o serviço está em execução, abra um browser e introduza o seguinte URL. Ele deve retornar um erro **403** :`http://<FQDN_of_your_NDES_server>/certsrv/mscep/mscep.dll`  

> [!NOTE]  
> O conector de certificado do Intune dá suporte a TLS 1,2. Se o servidor que hospeda o conector oferecer suporte a TLS 1,2, o TLS 1,2 será usado. Se o servidor não suportar o TLS 1.2, será utilizado o TLS 1.1. Atualmente, é utilizado o TLS 1.1 para a autenticação entre os dispositivos e o servidor.

## <a name="next-steps"></a>Passos Seguintes

[Criar um perfil de certificado SCEP](certificates-profile-scep.md)  
[Solucionar problemas do conector de certificado do Intune](troubleshoot-certificate-connector-events.md)
