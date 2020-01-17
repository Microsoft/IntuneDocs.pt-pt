---
title: Gerenciar o Microsoft Edge para iOS e Android com o Intune
titleSuffix: ''
description: Use políticas de proteção de aplicativo do Intune com o Microsoft Edge para garantir que os sites corporativos sempre sejam acessados com as proteções em vigor.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 3fb2f050-ec94-42ab-be05-c3d4101148bb
ms.reviewer: ilwu
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d1131eec2894aa8c7135b2f931a50ab85200e7e3
ms.sourcegitcommit: 822a70c61f5d644216ccc401b8e8949bc39e8d4a
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/16/2020
ms.locfileid: "76125281"
---
# <a name="manage-web-access-by-using-microsoft-edge-with-microsoft-intune"></a>Gerenciar o acesso via Web usando o Microsoft Edge com o Microsoft Intune

O uso de políticas de proteção de aplicativo do Intune com o Microsoft Edge ajuda a garantir que os sites corporativos sempre sejam acessados com as proteções em vigor. Os seguintes recursos do Microsoft Edge Enterprise habilitados pelas políticas do Intune estão disponíveis:

- **Identidade dupla.** Os usuários podem adicionar uma conta corporativa, bem como uma conta pessoal, para navegação. Não há uma separação total entre as duas identidades, semelhante à arquitetura e à experiência no Office 365 e no Outlook. Os administradores do Intune podem definir as políticas desejadas para uma experiência de navegação protegida dentro da conta corporativa.
- **Integração de política de proteção de aplicativo do Intune.** Como o Microsoft Edge é integrado ao SDK do Intune, você pode direcionar as políticas de proteção de aplicativo para proteger contra perda de dados. Esses recursos incluem controlar recortar, copiar e colar, impedir capturas de tela e garantir que os links selecionados pelo usuário sejam abertos somente em outros aplicativos gerenciados.
- **Integração de proxy do Aplicativo Azure.** Você pode controlar o acesso a aplicativos de software como serviço (SaaS) e aplicativos Web. Isso ajuda a garantir que os aplicativos baseados em navegador sejam executados somente no navegador seguro do Microsoft Edge, se os usuários finais se conectam da rede corporativa ou se conectam da Internet.
- **Configuração do aplicativo.** Você pode usar as definições de configuração do aplicativo para fortalecer a postura de segurança da sua organização e configurar recursos de facilidade de uso para seus usuários finais. Por exemplo, você pode definir indicadores, um atalho de Home Page, sites permitidos ou bloqueados e o proxy de aplicativo Azure Active Directory (Azure AD).

As políticas de proteção do Microsoft Intune para o Microsoft Edge ajudam a proteger os dados e os recursos da sua organização. Usar essas políticas com o Microsoft Edge garante que os recursos da sua empresa sejam protegidos não apenas em aplicativos instalados nativamente, mas também quando acessados por meio do navegador da Web.

## <a name="getting-started"></a>Introdução

Você e seus usuários finais podem baixar o Microsoft Edge de lojas de aplicativos públicos para uso em suas organizações. Os requisitos do sistema operacional para políticas de navegador são os seguintes:
- Android 4 e posterior
- iOS 8.0 e posterior

## <a name="application-protection-policies-for-microsoft-edge"></a>Políticas de proteção de aplicativo para o Microsoft Edge

Como o Microsoft Edge é integrado ao SDK do Intune, você pode aplicar políticas de proteção de aplicativo a eles.

Pode aplicar estas definições a:
- Dispositivos registrados no Intune.
- Dispositivos registrados com outro produto de gerenciamento de dispositivo móvel.
- Dispositivos não gerenciados.

Se o Microsoft Edge não for direcionado à política do Intune, os usuários não poderão usá-lo para acessar dados de outros aplicativos gerenciados pelo Intune, como aplicativos do Office. 

## <a name="conditional-access-for-microsoft-edge"></a>Acesso condicional para o Microsoft Edge

Você pode usar o acesso condicional do Azure AD para redirecionar os usuários para acessar o conteúdo corporativo somente por meio do Microsoft Edge. Isso restringe o acesso do navegador móvel a aplicativos Web conectados ao Azure AD ao Microsoft Edge protegido por política. Isso bloqueia o acesso de outros navegadores desprotegidos, como Safari ou Chrome. Você pode aplicar o acesso condicional aos recursos do Azure, como o Exchange Online e o SharePoint Online, o centro de administração Microsoft 365 e até mesmo sites locais que você expôs a usuários externos por meio da [proxy de aplicativo do AD do Azure](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started).

Para restringir os aplicativos Web conectados ao Azure AD para usar o Microsoft Edge no iOS e no Android:
1. Entre no centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. No nó Intune, selecione **acesso condicional** > **nova política**.
3. Selecione **conceder** na seção **controles de acesso** do painel.
4. Selecione **Requer aplicação aprovada do cliente**.
5. Escolha **selecionar** no painel **conceder** . Esta política tem de ser atribuída às aplicações na cloud que pretende que sejam acessíveis apenas a partir da aplicação Intune Managed Browser.

    ![Captura de tela da política de acesso condicional-concessão](./media/manage-microsoft-edge/manage-microsoft-edge-01.png)

6. Na seção atribuições, selecione **condições** > **aplicativos**. O painel **aplicativos** é exibido.
7. Em **Configurar**, selecione **Sim** para aplicar a política a aplicativos cliente específicos.
8. Certifique-se de que a opção **Browser** está selecionada como uma aplicação cliente.

    ![Captura de tela da política de acesso condicional – selecionar aplicativos cliente](./media/manage-microsoft-edge/manage-microsoft-edge-02.png)

    > [!NOTE]
    > Se quiser restringir as aplicações nativas (aplicações não baseadas no browser) que podem aceder a estas aplicações na cloud, também pode selecionar **Aplicações móveis e clientes de ambiente de trabalho**.

9. Na seção **atribuições** , selecione **usuários e grupos**e, em seguida, escolha os usuários ou grupos aos quais você deseja atribuir essa política.

10. Na secção **Atribuições**, selecione **Aplicações na cloud** para selecionar que aplicações quer proteger com esta política.

Depois que a política acima é configurada, os usuários são forçados a usar o Microsoft Edge para acessar os aplicativos Web conectados ao Azure AD que você protegeu com essa política. Se os usuários tentarem usar um navegador não gerenciado nesse cenário, eles receberão uma mensagem de que eles devem usar o Microsoft Edge.

> [!TIP]
> O acesso condicional é uma tecnologia do Azure AD. O nó de acesso condicional acessado do Intune é o mesmo nó acessado do Azure AD.

## <a name="single-sign-on-to-azure-ad-connected-web-apps-in-policy-protected-browsers"></a>Logon único para aplicativos Web conectados ao Azure AD em navegadores protegidos por política

O Microsoft Edge no iOS e no Android pode aproveitar o SSO (logon único) para todos os aplicativos Web (SaaS e locais) que são conectados ao Azure AD. O SSO permite que os usuários acessem aplicativos Web conectados ao Azure AD por meio do Microsoft Edge, sem precisar inserir novamente suas credenciais.

O SSO exige que seu dispositivo seja registrado pelo aplicativo Microsoft Authenticator para dispositivos iOS ou pelo Portal da Empresa do Intune no Android. Quando os usuários têm um deles, eles são solicitados a registrar seu dispositivo quando acessarem um aplicativo Web conectado ao Azure AD em um navegador protegido por política. (Isso só será verdadeiro se seu dispositivo ainda não tiver sido registrado.) Depois que o dispositivo é registrado com a conta do usuário gerenciada pelo Intune, essa conta tem o SSO habilitado para aplicativos Web conectados ao Azure AD.

> [!NOTE]
> O registo do dispositivo é uma simples verificação do serviço Azure AD. Ele não requer registro completo do dispositivo e não dá a ele nenhum privilégio adicional no dispositivo.

## <a name="create-a-protected-browser-app-configuration"></a>Criar uma configuração da aplicação de browser protegido

Para criar a configuração de aplicativo para o Microsoft Edge:

1. Entre no centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selecione **aplicativos** > **políticas de configuração de aplicativo** > **Adicionar**.
3. No painel **Adicionar política de configuração** , insira um **nome** e uma **Descrição** opcional para as definições de configuração do aplicativo.
4. Para o tipo de **Inscrição de dispositivos**, selecione **Aplicações geridas**.
5. Escolha **selecionar o aplicativo necessário**. Em seguida, no painel **aplicativos de destino** , escolha o **Managed browser** ou o **Edge** para IOS, para Android ou para ambos.
6. Selecione **OK** para retornar ao painel **Adicionar política de configuração** .
7. Selecione **Definições de configuração**. No painel de **configuração** , você define os pares de chave e valor para fornecer configurações para o Microsoft Edge. Utilize as secções mais adiante neste artigo para saber mais sobre os diferentes pares de chave e valor que pode definir.

    > [!NOTE]
    > O Microsoft Edge utiliza os mesmos pares de chave e valor que o Managed Browser. No Android, o Microsoft Edge deve ser direcionado às políticas de proteção de aplicativo para que as políticas de configuração de aplicativo entrem em vigor.

8. Quando tiver terminado, selecione **OK**.
9. No painel **Adicionar política de configuração** , escolha **Adicionar**.<br>
    A nova configuração é criada e exibida no painel de **configuração do aplicativo** .

## <a name="assign-the-configuration-settings-you-created"></a>Atribuir as definições de configuração que criou 

Você atribui as configurações a grupos de usuários no Azure AD. Se esse utilizador tiver a aplicação de browser protegido de destino instalada, a aplicação será gerida pelas definições que especificou.

1. No painel **aplicativos** do painel de gerenciamento de aplicativos móveis do Intune, selecione **políticas de configuração de aplicativo**.
2. Na lista de configurações de aplicações, selecione aquela que pretende atribuir.
3. No próximo painel, selecione **atribuições**.
4. No painel **atribuições** , selecione o grupo do Azure AD ao qual você deseja atribuir a configuração do aplicativo e, em seguida, selecione **OK**.

## <a name="direct-users-to-microsoft-edge-instead-of-the-intune-managed-browser"></a>Direcionar usuários para o Microsoft Edge em vez do Intune Managed Browser 

O Intune Managed Browser e o Microsoft Edge podem ser usados como navegadores protegidos por política. Para garantir que os usuários estejam sendo direcionados para usar o aplicativo de navegador correto, direcione todos os seus aplicativos gerenciados pelo Intune (por exemplo, Outlook, OneDrive e SharePoint) com a seguinte definição de configuração:

|    Chave    |    Valor    |
|------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
|    `com.microsoft.intune.useEdge`    |    O valor `true` orientará os usuários a baixarem e usarem o Microsoft Edge.<br>O valor `false` permitirá que os usuários usem o Intune Managed Browser.    |

Se esse valor de configuração de aplicativo **não** for definido, a lógica a seguir definirá qual navegador será usado para abrir links corporativos.

No Android:
- O Intune Managed Browser será iniciado se um usuário tiver o Intune Managed Browser e o Microsoft Edge baixados em seu dispositivo. 
- O Microsoft Edge será iniciado se apenas o Microsoft Edge for baixado no dispositivo e for direcionado com a política do Intune.
- Managed Browser será iniciado se apenas Managed Browser estiver no dispositivo e for direcionado com a política do Intune.

No iOS, para aplicações que integraram o SDK do Intune para iOS v. 9.0.9+:
- O Intune Managed Browser será iniciado se o Managed Browser e o Microsoft Edge estiverem no dispositivo.  
- O Microsoft Edge será iniciado se apenas o Microsoft Edge estiver no dispositivo e for direcionado com a política do Intune.
- Managed Browser será iniciado se apenas Managed Browser estiver no dispositivo e for direcionado com a política do Intune.

## <a name="configure-application-proxy-settings-for-microsoft-edge"></a>Definir configurações de proxy de aplicativo para o Microsoft Edge

Você pode usar o Microsoft Edge e o [Azure proxy de aplicativo do AD](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started) em conjunto para conceder aos usuários acesso a sites de intranet em seus dispositivos móveis. 

Estes são alguns exemplos dos cenários que o Azure Proxy de Aplicativo do AD habilitar: 

- Um usuário está usando o aplicativo móvel do Outlook, que é protegido pelo Intune. Em seguida, eles clicam em um link para um site de intranet em um email, e o Microsoft Edge reconhece que esse site da intranet foi exposto ao usuário por meio do proxy de aplicativo. O usuário é roteado automaticamente pelo proxy de aplicativo, para autenticar com qualquer autenticação multifator e acesso condicional aplicável, antes de acessar o site da intranet. O usuário agora pode acessar sites internos, mesmo em seus dispositivos móveis, e o link no Outlook funciona conforme o esperado.
- Um usuário abre o Microsoft Edge em seu dispositivo iOS ou Android. Se o Microsoft Edge estiver protegido com o Intune e o proxy de aplicativo estiver habilitado, o usuário poderá ir para um site de intranet usando a URL interna para a qual eles estão acostumados. O Microsoft Edge reconhece que esse site da intranet foi exposto ao usuário por meio do proxy de aplicativo. O usuário é roteado automaticamente pelo proxy de aplicativo, para autenticar antes de acessar o site da intranet. 

### <a name="before-you-start"></a>Antes de começar

- Configure seus aplicativos internos por meio do Azure Proxy de Aplicativo do AD.
  - Para configurar o Proxy de Aplicações e publicar aplicações, veja a [documentação de configuração](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy).
- O aplicativo Microsoft Edge deve ter a [política de proteção de aplicativo do Intune](app-protection-policy.md) atribuída.

> [!NOTE]
> Os dados atualizados de redirecionamento do Proxy de Aplicações podem demorar até 24 horas a entrar em vigor no Managed Browser e no Microsoft Edge.

#### <a name="step-1-enable-automatic-redirection-to-microsoft-edge-from-outlook"></a>Etapa 1: habilitar o redirecionamento automático para o Microsoft Edge a partir do Outlook
Configure o Outlook com uma política de proteção de aplicativo que habilita a configuração **compartilhar conteúdo da Web com navegadores gerenciados por política**.

![Captura de tela da política de proteção do aplicativo – compartilhar conteúdo da Web com navegadores gerenciados por política](./media/manage-microsoft-edge/manage-microsoft-edge-03.png)

#### <a name="step-2-set-the-app-configuration-setting-to-enable-app-proxy"></a>Etapa 2: definir a configuração de aplicativo para habilitar o proxy de aplicativo
Direcione o Microsoft Edge com o seguinte par de chave/valor, para habilitar o proxy de aplicativo para o Microsoft Edge:

|    Chave    |    Valor    |
|-------------------------------------------------------------------|-------------|
|    com.microsoft.intune.mam.managedbrowser.AppProxyRedirection    |    true    |

Para obter mais informações sobre como usar o Microsoft Edge e o Azure Proxy de Aplicativo do AD em tandem para acesso contínuo (e protegido) a aplicativos Web locais, consulte [melhor juntos: Intune e Azure Active Directory equipe para melhorar o acesso do usuário](https://cloudblogs.microsoft.com/enterprisemobility/2017/07/06/better-together-intune-and-azure-active-directory-team-up-to-improve-user-access). Esta postagem de blog faz referência à Intune Managed Browser, mas o conteúdo também se aplica ao Microsoft Edge.

## <a name="configure-a-homepage-shortcut-for-microsoft-edge"></a>Configurar um atalho de Home Page para o Microsoft Edge

Essa configuração permite que você configure um atalho de Home Page para o Microsoft Edge. O atalho de Home Page que você configura aparece como o primeiro ícone abaixo da barra de pesquisa quando o usuário abre uma nova guia no Microsoft Edge. O usuário não pode editar ou excluir este atalho em seu contexto gerenciado. O atalho da Home Page exibe o nome da sua organização para distingui-lo. 

Use o seguinte par de chave/valor para configurar um atalho de Home Page:

|    Chave    |    Valor    |
|-------------------------------------------------------------------|-------------|
|    com.microsoft.intune.mam.managedbrowser.homepage   |    Especifique um URL válido. Os URLs incorretos são bloqueados como medida de segurança.<br>**Exemplo:**  <`https://www.bing.com`>

## <a name="configure-your-organizations-logo-and-brand-color-for-new-tab-pages-in-microsoft-edge"></a>Configurar o logotipo e a cor da marca da sua organização para novas páginas de guias no Microsoft Edge

Essas configurações permitem que você personalize a nova página da guia do Microsoft Edge para exibir o logotipo e a cor da marca da sua organização como o plano de fundo da página.

Para carregar o logotipo e a cor da sua organização, primeiro conclua as seguintes etapas:
- No portal do Azure, navegue até Intune-> aplicativos cliente-> identidade visual e personalização > identidade visual da empresa
- Para definir o logotipo da sua marca, em "exibir", escolha "somente logotipo da empresa". São recomendados logotipos de plano de fundo transparentes. 
- Para definir a cor do plano de fundo da marca, em "exibir", escolha "cor do tema". O Microsoft Edge aplica uma tonalidade mais clara da cor na página da nova guia, o que garante que a página tenha alta legibilidade. 

Em seguida, use os seguintes pares de chave/valor para extrair a identidade visual da sua organização no Microsoft Edge:

|    Chave    |    Valor    |
|--------------------------------------------------------------------|------------|
|    com. Microsoft. Intune. Mam. managedbrowser. NewTabPage. BrandLogo    |    Verdadeiro    |
|    com. Microsoft. Intune. Mam. managedbrowser. NewTabPage. BrandColor    |    Verdadeiro    |

## <a name="display-relevant-industry-news-on-new-tab-pages"></a>Exibir notícias relevantes do setor em novas páginas de guias

Você pode configurar a nova experiência de página de guia no Microsoft Edge Mobile para exibir notícias do setor relevantes para sua organização. Quando você habilita esse recurso, o Microsoft Edge Mobile usa o nome de domínio da sua organização para agregar notícias da Web sobre sua organização, setor da organização e comeptitors, para que os usuários possam encontrar notícias externas relevantes no centeralized novo páginas de guias no Microsoft Edge. As notícias do setor são desligadas por padrão e você pode usá-las para sua organização. 

|    Chave    |    Valor    |
|------------------------------------------------------|----------------------------------------------------------------------------------------------------------------|
|    ' com. Microsoft. Intune. SohwIndustryNews '    |    **Verdadeiro** mostrará as notícias do setor na página de nova guia do Microsoft Edge Mobile.<p>**False** (padrão) ocultará as notícias do setor da nova página da guia.    |

## <a name="configure-managed-bookmarks-for-microsoft-edge"></a>Configurar indicadores gerenciados para o Microsoft Edge

Para facilitar o acesso, você pode configurar indicadores que você gostaria que os usuários estivessem disponíveis quando estiverem usando o Microsoft Edge. 

Aqui estão alguns detalhes:

- Esses indicadores só aparecem para usuários quando estão usando o [modo corporativo](https://docs.microsoft.com/intune/apps/app-configuration-managed-browser#how-to-configure-bookmarks-for-a-protected-browser) do Microsoft Edge. 
- Esses indicadores não podem ser excluídos nem modificados pelos usuários.
- Esses indicadores aparecem na parte superior da lista. Todos os indicadores que os usuários criam aparecem abaixo desses indicadores.
- Se você habilitou o redirecionamento de proxy de aplicativo, poderá adicionar aplicativos Web de proxy de aplicativo usando a URL interna ou externa.
- Certifique-se de prefixar todas as URLs com **http://** ou **https://** ao inseri-las na lista.

Use o seguinte par de chave/valor para configurar indicadores gerenciados:

|    Chave    |    Valor    |
|---------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    com.microsoft.intune.mam.managedbrowser.bookmarks    |    O valor dessa configuração é uma lista de indicadores. Cada indicador consiste no título do indicador e na URL do indicador. Separe o título e a URL com o caractere de `|`.      Exemplo:<br>`Microsoft Bing|https://www.bing.com`<br>Para configurar vários indicadores, separe cada par com o caractere duplo `||`.<p>Exemplo:<br>`Microsoft Bing|https://www.bing.com||Contoso|https://www.contoso.com`    |

## <a name="display-myapps-within-microsoft-edge-bookmarks"></a>Exibir myapps nos indicadores do Microsoft Edge

Por padrão, os usuários são exibidos nos sites do myapps que estão configurados para eles dentro de uma pasta dentro de indicadores do Microsoft Edge. A pasta é rotulada com o nome da sua organização.

|    Chave    |    Valor    |
|------------------------------------------------------|----------------------------------------------------------------------------------------------------------------|
|    com.microsoft.intune.mam.managedbrowser.MyApps    |    **Verdadeiro** mostra myapps nos marcadores do Microsoft Edge.<p>**False** oculta myapps no Microsoft Edge.    |

## <a name="specify-allowed-or-blocked-sites-list-for-microsoft-edge"></a>Especificar a lista de sites permitidos ou bloqueados para o Microsoft Edge
Você pode usar a configuração de aplicativo para definir quais sites os usuários podem acessar ao usar seu perfil de trabalho. Se você usar uma lista de permissões, os usuários só poderão acessar os sites que você listou explicitamente. Se você usar uma lista bloqueada, os usuários poderão acessar todos os sites, exceto aqueles que você bloqueou explicitamente. Você só deve impor uma lista de permissão ou de bloqueio, não ambos. Se você impor ambos, a lista de permissões será respeitada.  

Use os seguintes pares de chave/valor para configurar uma lista de sites permitidos ou bloqueados para o Microsoft Edge. 

|    Chave    |    Valor    |
|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    Escolha entre:<p>1. Especifique as URLs permitidas (somente essas URLs são permitidas; nenhum outro site pode ser acessado):<br>`com.microsoft.intune.mam.managedbrowser.AllowListURLs`<p>2. especificar URLs bloqueadas (todos os outros sites podem ser acessados):<br>`com.microsoft.intune.mam.managedbrowser.BlockListURLs`    |    O valor correspondente da chave é uma lista de URLs. Você insere todas as URLs que deseja permitir ou bloquear como um único valor, separados por um `|` caractere de pipe.<br>**Exemplos:**<br>`URL1|URL2|URL3`<br>`http://.contoso.com/|https://.bing.com/|https://expenses.contoso.com`  |

### <a name="url-formats-for-allowed-and-blocked-site-list"></a>Formatos de URL para a lista de sites permitidos e bloqueados 
Você pode usar vários formatos de URL para criar suas listas de sites permitidos/bloqueados. Esses padrões permitidos são detalhados na tabela a seguir. Algumas observações antes de começar: 
- Certifique-se de prefixar todas as URLs com **http://** ou **https://** ao inseri-las na lista.
- Você pode usar o símbolo curinga (\*) de acordo com as regras na lista de padrões permitidos a seguir.
- Um curinga só pode corresponder a um componente inteiro do nome do host (separado por pontos) ou a partes inteiras do caminho (separados por barras "/"). Por exemplo, **não** há suporte para `http://*contoso.com`.
- Pode especificar os números da porta no endereço. Se não especificar um número da porta, os valores utilizados são:
  - Porta 80 para http
  - Porta 443 para https
- **Não** há suporte para o uso de caracteres curinga para o número da porta. Por exemplo, `http://www.contoso.com:*` e `http://www.contoso.com:*/` não são suportados. 

    |    URL    |    Details    |    Correspondências    |    Não corresponde    |
    |-------------------------------------------|--------------------------------------------------------|-------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------|
    |    `http://www.contoso.com`    |    Corresponde a uma única página    |    `www.contoso.com`    |    `host.contoso.com`<br>`www.contoso.com/images`<br>`contoso.com/`    |
    |    `http://contoso.com`    |    Corresponde a uma única página    |    `contoso.com/`    |    `host.contoso.com`<br>`www.contoso.com/images`<br>`www.contoso.com`    |
    |    `http://www.contoso.com/*;`   |    Corresponde a todos os URLs que começam com `www.contoso.com`    |    `www.contoso.com`<br>`www.contoso.com/images`<br>`www.contoso.com/videos/tvshows`    |    `host.contoso.com`<br>`host.contoso.com/images`    |
    |    `http://*.contoso.com/*`    |    Corresponde a todos os subdomínios em `contoso.com`    |    `developer.contoso.com/resources`<br>`news.contoso.com/images`<br>`news.contoso.com/videos`    |    `contoso.host.com`
    |    `http://*contoso.com/*`    |    Corresponde a todos os subdomínios que terminam com `contoso.com/`    |    `http://news-contoso.com`<br>`http://news-contoso.com.com/daily`    |    `http://news-contoso.host.com`    |
    `http://www.contoso.com/images`    |    Corresponde a uma única pasta    |    `www.contoso.com/images`    |    `www.contoso.com/images/dogs`    |
    |    `http://www.contoso.com:80`    |    Corresponde a uma única página, usando um número de porta    |    `http://www.contoso.com:80`    |         |
    |    `https://www.contoso.com`    |    Corresponde a uma única página segura    |    `https://www.contoso.com`    |    `http://www.contoso.com`    |
    |    `http://www.contoso.com/images/*`    |    Corresponde a uma única pasta e a todas as subpastas    |    `www.contoso.com/images/dogs`<br>`www.contoso.com/images/cats`    |    `www.contoso.com/videos`    |
  
- Veja a seguir exemplos de algumas das entradas que você não pode especificar:
  - `*.com`
  - `*.contoso/*`
  - `www.contoso.com/*images`
  - `www.contoso.com/*images*pigs`
  - `www.contoso.com/page*`
  - Endereços IP
  - `https://*`
  - `http://*`
  - `https://*contoso.com`
  - `http://www.contoso.com:*`
  - `http://www.contoso.com: /*`

## <a name="transition-users-to-their-personal-context-when-trying-to-access-a-blocked-site"></a>Fazer a transição de usuários para seu contexto pessoal ao tentar acessar um site bloqueado

Com o modelo de identidade dupla incorporado ao Microsoft Edge, você pode habilitar uma experiência mais flexível para seus usuários finais do que era possível com o Intune Managed Browser. Quando os usuários visitam um site bloqueado no Microsoft Edge, você pode solicitar que eles abram o link em seu contexto pessoal, em vez de seu contexto de trabalho. Isso permite que eles permaneçam protegidos, mantendo os recursos corporativos seguros. Por exemplo, se um usuário receber um link para um artigo de notícias por meio do Outlook, ele poderá abrir o link em seu contexto pessoal ou em uma guia InPrivate. Seu contexto de trabalho não permite sites de notícias. Por padrão, essas transições são permitidas.

Use o seguinte par de chave/valor para configurar se essas transições suaves são permitidas:

|    Chave    |    Valor    |
|----------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    ' com. Microsoft. Intune. Mam. managedbrowser. openInPrivateIfBlock '    |    **True** fará com que os links restritos sejam abertos diretamente na navegação InPrivate.<p>**False** (padrão) apresentará aos usuários uma opção para abrir um link restrito com a navegação InPrivate ou com sua conta pessoal (MSA).    |

## <a name="open-restricted-links-directly-in-inprivate-tab-pages"></a>Abrir links restritos diretamente em páginas da guia InPrivate

Você pode configurar se os links restritos devem ser abertos diretamente na navegação InPrivate, o que fornece aos usuários uma experiência de navegação mais direta. Isso economizaria os usuários da etapa de fazer a transição para seu contexto pessoal para exibir um site. A navegação InPrivate é considerada não gerenciada, portanto os usuários não poderão acessar ao usar o modo de navegação InPrivate. 

|    Chave    |    Valor    |
|----------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    `com.microsoft.intune.mam.managedbrowser.AllowTransitionOnBlock`    |    **Verdadeiro** permite que o Microsoft Edge migre usuários para seu contexto pessoal para abrir sites bloqueados.<p>**Bloquear** impede que o Microsoft Edge migre usuários. Os usuários simplesmente mostram uma mensagem informando que o site que ele está tentando acessar está bloqueado.    |


## <a name="use-microsoft-edge-on-ios-to-access-managed-app-logs"></a>Usar o Microsoft Edge no iOS para acessar logs de aplicativos gerenciados 

Os usuários com o Microsoft Edge instalado em seu dispositivo iOS podem exibir o status de gerenciamento de todos os aplicativos publicados da Microsoft. Podem enviar registos para resolver problemas das respetivas aplicações iOS geridas. Eis como:
1. Abra o Microsoft Edge em seu dispositivo iOS.
2. Escreva `about:intunehelp` na caixa de endereço. 
3. O Microsoft Edge inicia o modo de solução de problemas.

Para obter uma lista das definições armazenados nos registos das aplicações, veja [Review app protection logs in the Managed Browser (Rever os registos de proteção das aplicações no Managed Browser)](app-protection-policy-settings-log.md).

Para ver como exibir logs em dispositivos Android, consulte [enviar logs para o administrador de ti por email](https://docs.microsoft.com/intune-user-help/send-logs-to-your-it-admin-by-email-android). 

## <a name="security-and-privacy-for-microsoft-edge"></a>Segurança e privacidade do Microsoft Edge

A seguir estão considerações adicionais de segurança e privacidade para o Microsoft Edge:

- O Microsoft Edge não consome configurações definidas pelos usuários para o navegador nativo em seus dispositivos, porque o Microsoft Edge não pode acessar essas configurações.
- Você pode configurar a opção **exigir PIN simples para acesso** ou **exigir credenciais corporativas para acesso** em uma política de proteção de aplicativo associada ao Microsoft Edge. Se um usuário selecionar o link de ajuda na página de autenticação, ele poderá navegar por qualquer site da Internet, independentemente de ter sido adicionado a uma lista bloqueada na política.
- O Microsoft Edge pode bloquear o acesso a sites somente quando eles são acessados diretamente. Ele não bloqueia o acesso quando os usuários usam serviços intermediários (como um serviço de tradução) para acessar o site.
- Para permitir a autenticação e o acesso à documentação do Intune, * **. Microsoft.com** é isento das configurações de lista de permissões ou de bloqueios. Sempre é permitido.
- Os usuários podem desativar a coleta de dados. A Microsoft recolhe automaticamente dados anónimos sobre o desempenho e a utilização do Managed Browser para melhorar os produtos e serviços Microsoft. Os utilizadores podem desativar a recolha de dados com a definição **Dados de Utilização** nos respetivos dispositivos. OS utilizadores não têm controlo sobre a recolha destes dados. Em dispositivos iOS, os sites visitados por usuários que têm um certificado expirado ou não confiável não podem ser abertos.

## <a name="next-steps"></a>Próximos passos

- [O que são as políticas de proteção de aplicações?](app-protection-policy.md) 
