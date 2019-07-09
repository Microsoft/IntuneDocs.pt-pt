---
title: Gerir o acesso à web com o Microsoft Edge com o Microsoft Intune
titleSuffix: ''
description: Utilize políticas de proteção de aplicações do Intune com o Microsoft Edge para garantir que os Web sites empresariais sempre são acedidos com as proteções in-loco.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 06/05/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 3fb2f050-ec94-42ab-be05-c3d4101148bb
ms.reviewer: ilwu
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 147547577615c6e74a9c5b3dd8b200ba387bad79
ms.sourcegitcommit: 1b7ee2164ac9490df4efa83c5479344622c181b5
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/08/2019
ms.locfileid: "67648474"
---
# <a name="manage-web-access-by-using-microsoft-edge-with-microsoft-intune"></a>Gerir o acesso à web com o Microsoft Edge com o Microsoft Intune

Utilizar políticas de proteção de aplicações do Intune com o Microsoft Edge ajuda a garantir que os Web sites empresariais são sempre acedidos com garantias in-loco. As seguintes funcionalidades de empresa do Microsoft Edge ativadas pelas políticas do Intune estão disponíveis:

- **Dual-Identity.** Os usuários podem adicionar uma conta profissional, bem como uma conta pessoal, para a navegação. Não há uma separação total entre as duas identidades, semelhante à arquitetura e à experiência no Office 365 e no Outlook. Os administradores do Intune, podem definir as políticas pretendidas para uma experiência de navegação protegida dentro da conta de trabalho.
- **Integração de política de proteção de aplicações de Intune.** Como o Microsoft Edge é integrado com o SDK do Intune, pode direcionar políticas de proteção de aplicações para proteger contra a perda de dados. Esses recursos incluem controle cortar, copiar e colar, as capturas de ecrã evitando e garantir que as ligações selecionados pelo usuário abertas apenas noutras aplicações geridas.
- **Integração de Proxy de aplicações do Azure.** Pode controlar o acesso a software como aplicações de serviço (SaaS) e aplicações web. Isto ajuda a garantir que os aplicativos baseados em navegador só são executados no browser Microsoft Edge seguro, se os utilizadores finais ligar a partir da rede empresarial ou ligar a partir da internet.
- **Configuração da aplicação.** Pode utilizar as definições de configuração de aplicações para fortalecer a postura de segurança da sua organização e configurar funcionalidades de Facilidade de utilização para os utilizadores finais. Por exemplo, pode definir indicadores, um atalho de home page, sites permitidos ou bloqueados e Proxy de aplicações do Azure Active Directory (Azure AD).

As políticas de proteção do Microsoft Intune para o Microsoft Edge ajudam a proteger os dados e os recursos da sua organização. Utilizar estas políticas com o Microsoft Edge garante que recursos da empresa estão protegidos não só em aplicativos instalados nativamente, mas também quando acedido através do browser.

## <a name="getting-started"></a>Introdução

E seus usuários finais pode transferir Microsoft Edge de lojas de aplicações públicas para utilização na sua organização. Os requisitos de sistema operativo para políticas de browser são um dos seguintes:
- Android 4 e posterior
- iOS 8.0 e posterior

## <a name="application-protection-policies-for-microsoft-edge"></a>Políticas de proteção de aplicações para o Microsoft Edge

Como o Microsoft Edge é integrado com o SDK do Intune, pode aplicar políticas de proteção de aplicações aos mesmos.

Pode aplicar estas definições a:
- Dispositivos que estão inscritos no Intune.
- Dispositivos inscritos com outro produto de gestão de dispositivos móveis.
- Dispositivos não geridos.

Se o Microsoft Edge não está direcionado com políticas do Intune, os utilizadores não é possível utilizá-lo para aceder aos dados de outras aplicações geridas pelo Intune, tais como aplicações do Office. 

## <a name="conditional-access-for-microsoft-edge"></a>Acesso condicional para o Microsoft Edge

Pode utilizar o acesso condicional do Azure AD para redirecionar os utilizadores acedam aos conteúdos empresariais apenas através do Microsoft Edge. Isso restringe o acesso de browser para dispositivos móveis para aplicações web do Azure AD-ligado para o Microsoft Edge protegido por políticas. Este bloqueia o acesso de outros browsers desprotegidos, como Safari ou Chrome. Pode aplicar acesso condicional aos recursos do Azure, como o Exchange Online e SharePoint Online, o Centro de administração do Microsoft 365 e até mesmo os sites no local que foram expostos a utilizadores externos através do [Proxy de aplicações do Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started).

Para restringir as aplicações web do Azure AD-ligado para utilizar o Microsoft Edge em iOS e Android:
1. Inicie sessão no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. No nó do Intune, selecione **acesso condicional** > **nova política**.
3. Selecione **concessão** partir a **controlos de acesso** seção do painel.
4. Selecione **Requer aplicação aprovada do cliente**.
5. Escolher **selecionar** sobre o **concessão** painel. Esta política tem de ser atribuída às aplicações na cloud que pretende que sejam acessíveis apenas a partir da aplicação Intune Managed Browser.

    ![Política de captura de ecrã de acesso condicional - concessão](./media/manage-microsoft-edge/manage-microsoft-edge-01.png)

6. Na secção de atribuições, selecione **condições** > **aplicações de cliente**. O **aplicações de cliente** é apresentado o painel.
7. Sob **configurar**, selecione **Sim** para aplicar a política a aplicações de cliente específico.
8. Certifique-se de que a opção **Browser** está selecionada como uma aplicação cliente.

    ![Política de captura de ecrã de acesso condicional - selecionar aplicações do cliente](./media/manage-microsoft-edge/manage-microsoft-edge-02.png)

    > [!NOTE]
    > Se quiser restringir as aplicações nativas (aplicações não baseadas no browser) que podem aceder a estas aplicações na cloud, também pode selecionar **Aplicações móveis e clientes de ambiente de trabalho**.

9. Na **atribuições** secção, selecione **utilizadores e grupos**e, em seguida, escolha os utilizadores ou grupos que pretende atribuir esta política.

    > [!NOTE]
    > Os utilizadores também devem ser visados com a política de Proteção de Aplicações do Intune para receber políticas de Configuração de Aplicações. Para obter mais informações sobre a criação de políticas de Proteção de Aplicações do Intune, veja [O que são as políticas de proteção de aplicações?](app-protection-policy.md).

10. Na secção **Atribuições**, selecione **Aplicações na cloud** para selecionar que aplicações quer proteger com esta política.

Depois da política acima estiver configurada, os usuários forem forçados a utilizar o Microsoft Edge para aceder às aplicações web do Azure AD-ligado que protegeu com esta política. Se os utilizadores tentarem utilizar um browser não gerido neste cenário, eles recebem uma mensagem que eles deverão usar o Microsoft Edge.

> [!TIP]
> Acesso condicional é uma tecnologia do Azure AD. O nó de acesso condicional acessado a partir do Intune é mesmo nó, acedido a partir do Azure AD.

## <a name="single-sign-on-to-azure-ad-connected-web-apps-in-policy-protected-browsers"></a>Início de sessão único para aplicações web do Azure AD-ligado em navegadores protegido por política

Microsoft Edge em dispositivos iOS e Android podem tirar partido do início de sessão único (SSO) para todas as aplicações web (SaaS e no local) que estão conectados ao AD do Azure. SSO permite aos utilizadores aceder a aplicações web do Azure AD-ligado através do Microsoft Edge, sem ter de reintroduzir as respetivas credenciais.

SSO exige que o dispositivo esteja registado pela aplicação Microsoft Authenticator para dispositivos iOS ou o Portal da empresa do Intune no Android. Quando os utilizadores têm um deles, é-lhes pedido para registar o seu dispositivo ao aceder a uma aplicação web do Azure AD conectados num navegador protegido por política. (Isso é apenas VERDADEIRO se o dispositivo não tiver já foi registado.) Depois do dispositivo está registado com a conta de utilizador gerenciada pelo Intune, essa conta tenha SSO ativado para as aplicações web do Azure AD-ligado.

> [!NOTE]
> O registo do dispositivo é uma simples verificação do serviço Azure AD. Ele não requer a inscrição do dispositivo completo e não dá IT privilégios adicionais no dispositivo.

## <a name="create-a-protected-browser-app-configuration"></a>Criar uma configuração da aplicação de browser protegido

As configurações de aplicações aplicar, o utilizador protegido do browser ou outra aplicação no dispositivo já tem de ser gerenciada pelos [política de proteção de aplicações do Intune](app-protection-policy.md).

Para criar a configuração de aplicações para o Microsoft Edge:

1. Inicie sessão no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Selecione **aplicações de cliente** > **políticas de configuração de aplicações** > **adicionar**.
3. No painel **Adicionar política de configuração**, introduza um **Nome** e uma **Descrição** opcional para as definições de configuração da aplicação.
4. Para o tipo de **Inscrição de dispositivos**, selecione **Aplicações geridas**.
5. Escolher **selecione a aplicação necessária**. Em seguida, no **aplicações de destino** painel, escolha a **Managed Browser** ou **Edge** para iOS, Android ou para ambos.
6. Selecione **OK** para voltar para o **Adicionar política de configuração** painel.
7. Selecione **Definições de configuração**. Sobre o **configuração** painel, define os pares de chave e valor para fornecer as configurações para o Microsoft Edge. Utilize as secções mais adiante neste artigo para saber mais sobre os diferentes pares de chave e valor que pode definir.

    > [!NOTE]
    > O Microsoft Edge utiliza os mesmos pares de chave e valor que o Managed Browser. 

8. Quando tiver terminado, selecione **OK**.
9. No painel **Adicionar política de configuração**, selecione **Adicionar**.<br>
    A nova configuração é criada e apresentada no **configuração da aplicação** painel.

## <a name="assign-the-configuration-settings-you-created"></a>Atribuir as definições de configuração que criou 

Atribuir as definições em grupos de utilizadores no Azure AD. Se esse utilizador tiver a aplicação de browser protegido de destino instalada, a aplicação será gerida pelas definições que especificou.

1. Sobre o **aplicações de cliente** painel do Intune aplicações móveis management dashboard, selecione **políticas de configuração de aplicação**.
2. Na lista de configurações de aplicações, selecione aquela que pretende atribuir.
3. No painel seguinte, selecione **atribuições**.
4. Sobre o **atribuições** painel, selecione o Azure AD grupo ao qual pretende atribuir a configuração de aplicação e, em seguida, selecione **OK**.

## <a name="direct-users-to-microsoft-edge-instead-of-the-intune-managed-browser"></a>Direcionar os utilizadores para o Microsoft Edge em vez do Intune Managed Browser 

O Browser gerido do Intune e o Microsoft Edge podem ser utilizado como navegadores protegido por política. Para garantir que os seus utilizadores estão a ser direcionados para utilizar a aplicação de browser correto, direcionar todas as suas aplicações geridas pelo Intune (por exemplo, Outlook, OneDrive e SharePoint) com a definição de configuração seguinte:

|    Chave    |    Value    |
|------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
|    `com.microsoft.intune.useEdge`    |    O valor `true` irá direcionar os utilizadores para transferir e utilizar o Microsoft Edge.<br>O valor `false` permitirá que os utilizadores a utilizar o Intune Managed Browser.    |

Se este valor de configuração de aplicação for **não** definido, a seguinte lógica irá definir o browser será utilizado para abrir ligações empresariais.

No Android:
- O Intune Managed Browser inicia se um utilizador tiver o Browser gerido do Intune e o Microsoft Edge transferido no seu dispositivo. 
- Microsoft Edge inicia se apenas o Microsoft Edge é transferido no dispositivo e destina-se com a política do Intune.
- Managed Browser inicia se apenas o Managed Browser está no dispositivo e destina-se com a política do Intune.

No iOS, para aplicações que integraram o SDK do Intune para iOS v. 9.0.9+:
- O Intune Managed Browser inicia se o Browser gerido e o Microsoft Edge no dispositivo.  
- Microsoft Edge inicia se apenas o Microsoft Edge está no dispositivo e destina-se com a política do Intune.
- Managed Browser inicia se apenas o Managed Browser está no dispositivo e destina-se com a política do Intune.

## <a name="configure-application-proxy-settings-for-microsoft-edge"></a>Configurar as definições de Proxy de aplicações para o Microsoft Edge

Pode utilizar o Microsoft Edge e [Proxy de aplicações do Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started) em conjunto para conceder aos utilizadores acesso a sites de intranet nos respetivos dispositivos móveis. 

Estes são alguns exemplos dos cenários de ativar o Proxy de aplicações do Azure AD: 

- Um utilizador está a utilizar a aplicação Outlook móveis que se encontra protegida pelo Intune. Eles, em seguida, clique num link para um site da intranet numa mensagem de e-mail e o Microsoft Edge reconhece que este site da intranet foi exposto ao utilizador através do Proxy de aplicações. O utilizador é encaminhado automaticamente através do Proxy de aplicações, para autenticar com qualquer autenticação multifator aplicável e o acesso condicional, antes de chegar ao site da intranet. O usuário agora é capaz de aceder a sites internos, até mesmo nos respetivos dispositivos móveis, e a ligação no Outlook funciona conforme esperado.
- Um utilizador abre o Microsoft Edge no seu dispositivo iOS ou Android. Se o Microsoft Edge está protegido com o Intune e o Proxy de aplicações está ativado, o usuário pode ir para um site da intranet, utilizando o URL interno que são utilizadas para. Microsoft Edge reconhece que este site da intranet foi exposto ao utilizador através do Proxy de aplicações. O utilizador é encaminhado automaticamente através do Proxy de aplicações, para autenticar antes de chegar ao site da intranet. 

### <a name="before-you-start"></a>Antes de começar

- Configure as suas aplicações internas através do Proxy de aplicações do Azure AD.
    - Para configurar o Proxy de Aplicações e publicar aplicações, veja a [documentação de configuração](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy).
- Tem de ter a aplicação do Microsoft Edge [política de proteção de aplicações do Intune](app-protection-policy.md) atribuído.

> [!NOTE]
> Os dados atualizados de redirecionamento do Proxy de Aplicações podem demorar até 24 horas a entrar em vigor no Managed Browser e no Microsoft Edge.

#### <a name="step-1-enable-automatic-redirection-to-microsoft-edge-from-outlook"></a>Passo 1: Ativar o redirecionamento automático do Outlook para o Microsoft Edge
Configurar o Outlook com uma política de proteção de aplicações que permite a definição **partilha de conteúdo web com a política de browsers geridos**.

![Política de proteção de captura de ecrã da aplicação - conteúdo da web com a política de partilha de browsers geridos](./media/manage-microsoft-edge/manage-microsoft-edge-03.png)

#### <a name="step-2-set-the-app-configuration-setting-to-enable-app-proxy"></a>Passo 2: Definir a definição de configuração de aplicação para ativar o proxy de aplicação
Destino Microsoft Edge com o seguinte par chave/valor, para ativar o Proxy de aplicação para o Microsoft Edge:

|    Chave    |    Value    |
|-------------------------------------------------------------------|-------------|
|    com.microsoft.intune.mam.managedbrowser.AppProxyRedirection    |    true    |

Para obter mais informações sobre como utilizar o Microsoft Edge e o Proxy de aplicações do Azure AD em conjunto para o acesso totalmente integrado (e protegido) para aplicações web no local, consulte [melhor juntos: Intune and Azure Active Directory team up to improve user access](https://cloudblogs.microsoft.com/enterprisemobility/2017/07/06/better-together-intune-and-azure-active-directory-team-up-to-improve-user-access) (Melhor em conjunto: o Intune e o Azure Active Directory juntam-se para melhorar o acesso do utilizador). Nesta postagem de blog referências o Intune Managed Browser, mas o conteúdo aplica-se a Microsoft Edge também.

## <a name="configure-a-homepage-shortcut-for-microsoft-edge"></a>Configurar um atalho de home page para o Microsoft Edge

Esta definição permite-lhe configurar um atalho de home page para o Microsoft Edge. Quando o utilizador abre um novo separador no Microsoft Edge, é apresentado o atalho de home page que configurar como o primeiro ícone abaixo da barra de pesquisa. O utilizador não é possível editar ou eliminar este atalho no seu contexto gerido. O atalho de home page apresenta o nome da sua organização para distingui-la. 

Utilize o seguinte par chave/valor para configurar um atalho de home page:

|    Chave    |    Valor    |
|-------------------------------------------------------------------|-------------|
|    com.microsoft.intune.mam.managedbrowser.homepage   |    Especifique um URL válido. Os URLs incorretos são bloqueados como medida de segurança.<br>**Exemplo:**  <`https://www.bing.com`>
    |

## <a name="configure-managed-bookmarks-for-microsoft-edge"></a>Configurar os marcadores geridos do Microsoft Edge

Para facilitar o acesso, pode configurar os marcadores que gostaria de ter os seus utilizadores ter disponível quando estão a utilizar Microsoft Edge. 

Aqui estão alguns detalhes:

- Estes marcadores aparecem apenas para os utilizadores quando estão a utilizar o modo de empresa do Microsoft Edge. 
- Estes marcadores não podem ser eliminados ou modificados por utilizadores.
- Estes marcadores são apresentados na parte superior da lista. Todos os marcadores criados pelos utilizadores são apresentados abaixo destes.
- Se tiver ativado o redirecionamento do Proxy de aplicações, pode adicionar aplicações do Proxy de aplicações web utilizando o respetivo URL interno ou externo.

Utilize o seguinte par chave/valor para configurar os marcadores geridos:

|    Chave    |    Value    |
|---------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    com.microsoft.intune.mam.managedbrowser.bookmarks    |    O valor para esta configuração é uma lista de marcadores. Cada marcador é constituído pelo título e o URL de marcador. Separe o título e o URL com o `|` caráter.      Exemplo:<br>`Microsoft Bing|https://www.bing.com`<br>Para configurar múltiplos marcadores, separe cada par com o caráter duplo `||`.<p>Exemplo:<br>`Microsoft Bing|https://www.bing.com||Contoso|https://www.contoso.com`    |

## <a name="display-myapps-within-microsoft-edge-bookmarks"></a>Apresentar MyApps dentro de marcadores do Microsoft Edge

Por predefinição, os utilizadores são apresentados os sites de My Apps que estão configurados para-los numa pasta dentro de marcadores do Microsoft Edge. A pasta está etiquetada com o nome da sua organização.

|    Chave    |    Value    |
|------------------------------------------------------|----------------------------------------------------------------------------------------------------------------|
|    com.microsoft.intune.mam.managedbrowser.MyApps    |    **Verdadeiro** mostra MyApps dentro os indicadores do Microsoft Edge.<p>**FALSO** oculta MyApps dentro do Microsoft Edge.    |

## <a name="specify-allowed-or-blocked-sites-list-for-microsoft-edge"></a>Especificar a lista de sites permitidos ou bloqueados para o Microsoft Edge
Pode utilizar a configuração de aplicações para definir os sites que os utilizadores podem aceder ao utilizar o seu perfil de trabalho. Se utilizar uma lista de permissões, os utilizadores só conseguem aceder aos sites que tiver de ser listados explicitamente. Se utilizar uma lista de bloqueados, os utilizadores podem aceder a todos os sites, exceto aqueles que já explicitamente bloqueado. Apenas deve impor um permitidos ou uma lista de bloqueados, não ambos. Se impor ambos, é honrada a lista de permitidos.  

Utilize os seguintes pares de chave/valor para configurar um uma lista de sites permitidos ou bloqueados para o Microsoft Edge. 

|    Chave    |    Valor    |
|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    Escolha entre:<p>1. Especificar URLs permitidos (apenas estes URLs são permitidos; não pode aceder a mais nenhum site):<br>`com.microsoft.intune.mam.managedbrowser.AllowListURLs`<p>2. Especificar URLs bloqueados (é possível aceder a todos os outros sites):<br>`com.microsoft.intune.mam.managedbrowser.BlockListURLs`    |    O valor correspondente da chave é uma lista de URLs. Introduza todos os URLs que pretende permitir ou bloquear como um único valor, separado por um pipe `|` caráter.<br>**Exemplos:**<br>`URL1|URL2|URL3`<br>`http://.contoso.com/|https://.bing.com/|https://expenses.contoso.com`  |

### <a name="url-formats-for-allowed-and-blocked-site-list"></a>Formatos de URL para permitidas e bloqueadas a lista de sites 
Pode usar vários formatos de URL para criar as suas listas de sites permitido/bloqueado. Estes permitido padrões são detalhados na seguinte tabela. Algumas notas antes de começar: 
- Certifique-se de que adiciona o prefixo **http** ou **https** a todos os URLs quando os introduzir na lista.
- Pode utilizar o símbolo de caráter universal (\*), de acordo com as regras na lista de padrões permitidos seguinte.
- Um caráter universal só pode corresponder a um componente inteiro do nome de anfitrião (separados por pontos) ou de partes inteiras do caminho (separados por barras). Por exemplo, `http://*contoso.com` é **não** suportado.
- Pode especificar os números da porta no endereço. Se não especificar um número da porta, os valores utilizados são:
    - Porta 80 para http
    - Porta 443 para https
- Utilização de carateres universais para o número da porta é **não** suportado. Por exemplo, `http://www.contoso.com:*` e `http://www.contoso.com:*/` não são suportados. 

    |    URL    |    Detalhes    |    Correspondências    |    Não corresponde    |
    |-------------------------------------------|--------------------------------------------------------|-------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------|
    |    `http://www.contoso.com`    |    Corresponde a uma única página    |    `www.contoso.com`    |    `host.contoso.com`<br>`www.contoso.com/images`<br>`contoso.com/`    |
    |    `http://contoso.com`    |    Corresponde a uma única página    |    `contoso.com/`    |    `host.contoso.com`<br>`www.contoso.com/images`<br>`www.contoso.com`    |
    |    `http://www.contoso.com/&#42;`   |    Corresponde a todos os URLs que começam com `www.contoso.com`    |    `www.contoso.com`<br>`www.contoso.com/images`<br>`www.contoso.com/videos/tvshows`    |    `host.contoso.com`<br>`host.contoso.com/images`    |
    |    `http://*.contoso.com/*`    |    Corresponde a todos os subdomínios em `contoso.com`    |    `developer.contoso.com/resources`<br>`news.contoso.com/images`<br>`news.contoso.com/videos`    |    `contoso.host.com`    |
    |    `http://www.contoso.com/images`    |    Corresponde a uma única pasta    |    `www.contoso.com/images`    |    `www.contoso.com/images/dogs`    |
    |    `http://www.contoso.com:80`    |    Corresponde a uma única página, ao utilizar um número de porta    |    `http://www.contoso.com:80`    |         |
    |    `https://www.contoso.com`    |    Corresponde a uma única página segura    |    `https://www.contoso.com`    |    `http://www.contoso.com`    |
    |    `http://www.contoso.com/images/*`    |    Corresponde a uma única pasta e a todas as subpastas    |    `www.contoso.com/images/dogs`<br>`www.contoso.com/images/cats`    |    `www.contoso.com/videos`    |
  
- Seguem-se exemplos de algumas entradas que não pode especificar:
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
  
## <a name="define-behavior-when-users-try-to-access-a-blocked-site"></a>Definir o comportamento quando os utilizadores tentam aceder um site bloqueado

Com o modelo de identidade dupla incorporado no Microsoft Edge, pode ativar uma experiência mais flexível para os utilizadores finais que era possível com o Intune Managed Browser. Quando os utilizadores aceder um site bloqueado no Microsoft Edge, pode pedi-las para abrir a ligação no seu contexto pessoal em vez de seu contexto de trabalho. Isto permite-lhes para se manterem protegidos, enquanto mantém a recursos da empresa seguros. Por exemplo, se um utilizador é enviado uma ligação para um artigo de notícias através do Outlook, eles podem abrir a ligação no seu contexto de pessoa ou numa guia InPrivate. Seu contexto de trabalho não permite que os Web sites de notícias. Por predefinição, são permitidas essas transições.

Utilize o seguinte par chave/valor para configurar se essas transições de forma recuperável são permitidas:

|    Chave    |    Value    |
|----------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    `com.microsoft.intune.mam.managedbrowser.AllowTransitionOnBlock`    |    **Verdadeiro** permite que o Microsoft Edge para os utilizadores de transição para seu contexto com pessoal para abrir sites bloqueados.<p>**Bloco** impede que o Microsoft Edge fazer a transição de utilizadores. Os utilizadores que é simplesmente Verão uma mensagem a indicar que o site que estão a tentar aceder está bloqueado.    |

## <a name="use-microsoft-edge-on-ios-to-access-managed-app-logs"></a>Utilizar o Microsoft Edge em dispositivos iOS para aceder aos registos de aplicação gerida 

Os utilizadores com o Microsoft Edge instalado nos respetivos dispositivos iOS podem ver o estado de gestão de todas as aplicações publicadas da Microsoft. Podem enviar registos para resolver problemas das respetivas aplicações iOS geridas. Eis como:
1. Abra o Microsoft Edge no seu dispositivo iOS.
2. Escreva `about:intunehelp` na caixa de endereço. 
3. Microsoft Edge inicia o modo de resolução de problemas.

Para obter uma lista das definições armazenados nos registos das aplicações, veja [Review app protection logs in the Managed Browser (Rever os registos de proteção das aplicações no Managed Browser)](app-protection-policy-settings-log.md).

Para ver como ver os registos em dispositivos Android, veja [enviar registos ao administrador de TI por e-mail](https://docs.microsoft.com/intune-user-help/send-logs-to-your-it-admin-by-email-android). 

## <a name="security-and-privacy-for-microsoft-edge"></a>Segurança e privacidade para o Microsoft Edge

Seguem-se as considerações adicionais de segurança e privacidade para o Microsoft Edge:

- Microsoft Edge não consome as definições que os utilizadores definidos para o navegador nativo nos respetivos dispositivos, porque o Microsoft Edge não é possível aceder a estas definições.
- Pode configurar a opção **exigir PIN simples para acesso** ou **exigir credenciais da empresa para obter acesso** numa política de proteção de aplicações associada com o Microsoft Edge. Se um usuário selecionar a ligação de ajuda na página de autenticação, pode procurar sites na internet, independentemente de terem sido adicionados a uma lista de bloqueados na política.
- Microsoft Edge só pode bloquear acesso a sites quando estes são acedidos diretamente. Ele não bloquear o acesso quando os utilizadores utilizam serviços intermédios (como um serviço de tradução) para aceder ao site.
- Para permitir a autenticação e acesso a documentação do Intune, * **. microsoft.com** está excluído das definições da lista de permissões ou de bloqueios. É sempre permitido.
- Os utilizadores podem desativar a recolha de dados. A Microsoft recolhe automaticamente dados anónimos sobre o desempenho e a utilização do Managed Browser para melhorar os produtos e serviços Microsoft. Os utilizadores podem desativar a recolha de dados com a definição **Dados de Utilização** nos respetivos dispositivos. OS utilizadores não têm controlo sobre a recolha destes dados. Em dispositivos iOS, Web sites que os utilizadores visitam que têm um certificado expirado ou não fidedigno não podem ser abertos.

## <a name="next-steps"></a>Passos Seguintes

- [O que são as políticas de proteção de aplicações?](app-protection-policy.md) 
