---
title: Gerir o acesso web usando o Microsoft Edge com o Microsoft Intune
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
ms.openlocfilehash: 1ad8a3298a801b07e021b84bd5eea9c91f01f1a2
ms.sourcegitcommit: 4b83697de8add3b90675c576202ef2ecb49d80b2
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/13/2019
ms.locfileid: "67044873"
---
# <a name="manage-web-access-using-microsoft-edge-with-microsoft-intune"></a>Gerir o acesso web usando o Microsoft Edge com o Microsoft Intune

Utilizar políticas de proteção de aplicações do Intune com o Microsoft Edge pode garantir a Web sites empresariais sempre acedidos com as proteções in-loco. Estão disponíveis as seguintes funcionalidades empresariais do Microsoft Edge ativadas por políticas do Intune. Estas funcionalidades empresariais incluem:

1.  **Identidade Dupla** – os utilizadores podem adicionar uma conta profissional e conta pessoal para navegação. Não há uma separação total entre as duas identidades, semelhante à arquitetura e à experiência no Office 365 e no Outlook. Os administradores do Intune poderão definir as políticas pretendidas para uma experiência de navegação protegida na conta profissional.
2.  **Integração de política de proteção de aplicações do Intune** – Microsoft Edge, uma vez que está integrado com o SDK do Intune, pode direcionar políticas de proteção de aplicações para garantir a proteção de perda de dados. Esses recursos incluem o controle de cortar, copiar e colar, impedir o ecrã captura e garantir que as ligações selecionados pelo usuário abertas apenas noutras aplicações geridas.
3.  **Integração de Proxy de aplicações do Azure** – pode controlar o acesso às aplicações SaaS e aplicações web, ajudando a garantir que as aplicações baseadas no browser executado no browser Microsoft Edge seguro, se os utilizadores finais ligar a partir da rede empresarial ou ligar a partir da Internet .
4.  **Configuração da aplicação** – pode tirar partido das definições de configuração de aplicações para fortalecer a sua postura de segurança de organizações e configurar funcionalidades de Facilidade de utilização para os utilizadores finais. Por exemplo, pode definir indicadores, um atalho de home page, permitiu/bloqueou a sites, o Proxy de aplicações do Azure e muito mais.
As políticas de proteção do Microsoft Intune para o Microsoft Edge ajudam a proteger os dados e os recursos da sua organização. Utilizar estas políticas com o Microsoft Edge garante que recursos da empresa estão protegidos não só em aplicativos instalados nativamente, mas também quando acedido através do browser.

## <a name="getting-started"></a>Introdução

E seus usuários finais pode transferir Microsoft Edge de lojas de aplicações públicas para utilização na sua organização. Requisitos de sistema operativo para políticas de browser:
- Android 4 e posterior ou
- iOS 8.0 e posterior

## <a name="application-protection-policies-for-microsoft-edge"></a>Políticas de proteção de aplicações para o Microsoft Edge

Como o Microsoft Edge é integrado com o SDK do Intune, pode aplicar políticas de proteção de aplicações para os mesmos, incluindo:
- Controlar a utilização dos comandos Cortar, Copiar e Colar.
- Impedir as capturas de ecrã.
- Garantir que as ligações empresariais só são abertas em browsers e aplicações geridos.

Para obter detalhes, veja o que são políticas de proteção de aplicações?
Pode aplicar estas definições a:
- Dispositivos que estão inscritos no Intune
- Dispositivos que estão inscritos noutro produto MDM
- Dispositivos não geridos

Se o Microsoft Edge não está direcionado com políticas do Intune, os utilizadores não é possível utilizá-lo para aceder aos dados de outras aplicações geridas pelo Intune, tais como aplicações do Office. 

## <a name="conditional-access-for-microsoft-edge"></a>Acesso condicional para o Microsoft Edge

Pode aproveitar o acesso condicional do Azure AD para redirecionar os utilizadores acedam aos conteúdos empresariais apenas através do Microsoft Edge. Isso seria a restringir o acesso do browser para dispositivos móveis para aplicações web do Azure AD-ligado para o Microsoft Edge protegido por política, e isso seria a bloquear o acesso a partir de outros browsers desprotegidos, como Safari ou Chrome. Acesso condicional pode ser aplicado aos recursos do Azure, como o Exchange Online e SharePoint Online, o Centro de administração do Microsoft 365 e até mesmo os sites no local que foram expostos a utilizadores externos através do [Proxy de aplicações do Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started).

Para restringir as aplicações web do Azure AD-ligado para utilizar o Microsoft Edge em iOS e Android, siga os passos abaixo:
1. Inicie sessão no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. No nó do Intune, selecione **acesso condicional** > **nova política**.
3. Em seguida, selecione **Conceder** na secção **Controlos de acesso** do painel.
4. Clique em **Requer aplicação aprovada do cliente**.
5. Clique em **Selecionar** no painel **Conceder**. Esta política tem de ser atribuída às aplicações na cloud que pretende que sejam acessíveis apenas a partir da aplicação Intune Managed Browser.

    ![Política de acesso condicional - concessão](./media/manage-microsoft-edge/manage-microsoft-edge-01.png)

6. Na secção de atribuições, selecione condições > aplicações de cliente. É apresentado o painel de aplicações de cliente.
7. Clique em Sim em configurar para aplicar a política a aplicações de cliente específico.
8. Certifique-se de que o navegador está selecionado como uma aplicação de cliente.

    ![Política de acesso condicional - selecionar aplicações do cliente](./media/manage-microsoft-edge/manage-microsoft-edge-02.png)

    > [!NOTE]
    > Se quiser restringir as aplicações nativas (aplicações não baseadas no browser) que podem aceder a estas aplicações na cloud, também pode selecionar **Aplicações móveis e clientes de ambiente de trabalho**.

9. Na secção **Atribuições**, selecione **Utilizadores e grupos** e, em seguida, selecione os utilizadores e grupos aos quais pretende atribuir esta política.

    > [!NOTE]
    > Os utilizadores também devem ser visados com a política de Proteção de Aplicações do Intune para receber políticas de Configuração de Aplicações. Para obter mais informações sobre a criação de políticas de Proteção de Aplicações do Intune, veja [O que são as políticas de proteção de aplicações?](app-protection-policy.md)

10. Na secção **Atribuições**, selecione **Aplicações na cloud** para selecionar que aplicações quer proteger com esta política.

Assim que a política acima estiver configurada, os utilizadores serão forçados a utilizar o Microsoft Edge para aceder às aplicações web do Azure AD-ligado que protegeu com esta política. Se os utilizadores tentarem utilizar um browser não gerido neste cenário, verá uma mensagem que eles deverão usar o Microsoft Edge.

> [!TIP]
> O Acesso Condicional é uma tecnologia do Azure Active Directory (Azure AD). O nó de acesso condicional acessado a partir do Intune é mesmo nó, acedido a partir do Azure AD.

## <a name="single-sign-on-to-azure-ad-connected-web-apps-in-policy-protected-browsers"></a>Início de Sessão Único nas aplicações Web ligadas ao Azure AD em browsers protegidos por política

Microsoft Edge em dispositivos iOS e Android podem tirar partido do SSO para todas as aplicações web (SaaS e no local) que estão conectados ao AD do Azure. SSO permite aos utilizadores aceder a aplicações web do Azure AD-ligado através do Microsoft Edge sem ter de reintroduzir as respetivas credenciais.

SSO exige que o dispositivo esteja registado pela aplicação Microsoft Authenticator para dispositivos iOS ou o Portal da empresa do Intune no Android. Quando os utilizadores têm a aplicação Authenticator ou Portal da empresa do Intune, serão solicitados para registar o seu dispositivo quando navegarem para aplicações do Azure AD-ligado web num browser protegido por política, se o dispositivo não já foi registado ainda. Depois do dispositivo está registado com a conta de utilizador gerenciada pelo Intune, essa conta terá o SSO ativado para aplicações web do Azure AD-ligado.

> [!NOTE]
> O registo do dispositivo é uma simples verificação do serviço Azure AD. Não requer a inscrição total do dispositivo e não fornece privilégios adicionais à equipa de TI no dispositivo.

## <a name="create-a-protected-browser-app-configuration"></a>Criar uma configuração da aplicação de browser protegido

As configurações de aplicações aplicar, o utilizador protegido do browser ou outra aplicação no dispositivo já tem de ser gerenciada pelo [política de proteção de aplicações do Intune](app-protection-policy.md).

Os passos seguintes são utilizados para criar uma configuração de aplicação de browser protegido:

1. Inicie sessão no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Selecione **aplicações de cliente** > **políticas de configuração de aplicações** > **adicionar**.
3. No painel **Adicionar política de configuração**, introduza um **Nome** e uma **Descrição** opcional para as definições de configuração da aplicação.
4. Para o tipo de **Inscrição de dispositivos**, selecione **Aplicações geridas**.
5. Selecione **Selecionar a aplicação necessária** e, em seguida, no painel **Aplicações de destino**, selecione o **Managed Browser** e/ou o **Microsoft Edge** para iOS, Android ou para ambos.
6. Selecione **OK** para regressar ao painel **Política de configuração da aplicação**.
7. Selecione **Definições de configuração**. Sobre o **configuração** painel, define os pares de chave e valor para fornecer as configurações para o Microsoft Edge. Utilize as secções mais adiante neste artigo para saber mais sobre os diferentes pares de chave e valor que pode definir.

    > [!NOTE]
    > O Microsoft Edge utiliza os mesmos pares de chave e valor que o Managed Browser. 

8.  Quando tiver terminado, clique em **OK**.
9.  No painel **Adicionar política de configuração**, selecione **Adicionar**.<br>
    A nova configuração é criada e apresentada no **configuração da aplicação** painel.

## <a name="assign-the-configuration-settings-you-created"></a>Atribuir as definições de configuração que criou 

Atribua as definições a grupos de utilizadores do Azure AD. Se esse utilizador tiver a aplicação de browser protegido de destino instalada, a aplicação será gerida pelas definições que especificou.

1. No painel **Aplicações do cliente** do dashboard de gestão de aplicações móveis do Intune, selecione **Políticas de configuração de aplicações**.
2. Na lista de configurações de aplicações, selecione aquela que pretende atribuir.
3. No painel seguinte, selecione **Atribuições**.
4. No painel **Atribuições**, selecione o grupo do Azure AD ao qual pretende atribuir a configuração da aplicação e, em seguida, selecione **OK**.

## <a name="how-to-configure-application-proxy-settings-for-protected-browsers"></a>Como configurar as definições de Proxy de Aplicações para browsers protegidos

Microsoft Edge e [Proxy de aplicações do Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started) pode ser utilizado em conjunto para conceder aos utilizadores acesso a sites de intranet nos respetivos dispositivos móveis. 

Estes são alguns exemplos dos cenários de ativar o Proxy de aplicações do AD: 

- Um utilizador está a utilizar a aplicação Outlook móveis que se encontra protegida pelo Intune. Eles, em seguida, clique num link para um site da intranet numa mensagem de e-mail e o Microsoft Edge reconhece que este site da intranet foi exposto ao utilizador através do Proxy de aplicações. O utilizador é encaminhado automaticamente através do Proxy de aplicações para se autenticar com qualquer autenticação multifator aplicável e o acesso condicional, antes de chegar ao site da intranet. Os utilizadores podem agora aceder a sites internos mesmo nos respetivos dispositivos móveis e a ligação no Outlook funciona conforme esperado.
- Um utilizador abre o Microsoft Edge no seu dispositivo iOS ou Android. Se o Microsoft Edge está protegido com o Intune e o proxy de aplicações está ativado, o utilizador pode navegar para um site da intranet através do URL interno que são utilizadas para. Microsoft Edge reconhece que este site da intranet foi exposto ao utilizador através do Proxy de aplicações e o utilizador é encaminhado automaticamente através do Proxy de aplicações, para autenticar antes de chegar ao site da intranet. 

### <a name="before-you-start"></a>Antes de começar

- Configure as suas aplicações internas através do Proxy de Aplicações do Azure AD.
    - Para configurar o Proxy de Aplicações e publicar aplicações, veja a [documentação de configuração](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy).
- Aplicação do Microsoft Edge tem de ter [política de proteção de aplicações do Intune](app-protection-policy.md) atribuído.

> [!NOTE]
> Os dados atualizados de redirecionamento do Proxy de Aplicações podem demorar até 24 horas a entrar em vigor no Managed Browser e no Microsoft Edge.

#### <a name="step-1-enable-automatic-redirection-to-a-protected-browser-from-outlook"></a>Passo 1: ativar o redirecionamento automático para um browser protegido a partir do Outlook
Outlook tem de ser configurado com uma política de proteção de aplicações que permite a definição **partilha de conteúdo web com a política de browsers geridos**.

![Política de proteção de aplicações - conteúdo da web com a política de partilha de browsers geridos](./media/manage-microsoft-edge/manage-microsoft-edge-03.png)

#### <a name="step-2-set-the-app-configuration-setting-to-enable-app-proxy"></a>Passo 2: Definir a definição de configuração de aplicação para ativar o proxy de aplicação
Direcionar o Microsoft Edge com o abaixo par chave/valor para ativar o proxy de aplicação para o Microsoft Edge:

|    Chave    |    Value    |
|-------------------------------------------------------------------|-------------|
|    com.microsoft.intune.mam.managedbrowser.AppProxyRedirection    |    true    |

Para obter mais informações sobre como Microsoft Edge e Proxy de aplicações do Azure AD podem ser utilizados em conjunto para o acesso totalmente integrado (e protegido) para aplicações web no local, consulte a mensagem de blogue de segurança do Enterprise Mobility + [melhor juntos: Intune and Azure Active Directory team up to improve user access](https://cloudblogs.microsoft.com/enterprisemobility/2017/07/06/better-together-intune-and-azure-active-directory-team-up-to-improve-user-access) (Melhor em conjunto: o Intune e o Azure Active Directory juntam-se para melhorar o acesso do utilizador). Nesta postagem de blog referências o Intune Managed Browser, mas o conteúdo aplica-se a Microsoft Edge também.

## <a name="how-to-configure-a-homepage-shortcut-for-microsoft-edge"></a>Como configurar um atalho de home page para o Microsoft Edge

Esta definição permite-lhe configurar um atalho de home page para o Microsoft Edge.  O atalho de home page que configurar aparece como o primeiro ícone abaixo da barra de pesquisa quando abrem um novo separador no Microsoft Edge. O utilizador não será capaz de editar ou eliminar este atalho no seu contexto gerido. O atalho para a home page irá apresentar o nome da sua organização para poder distingui-lo. 

Utilize o abaixo par chave/valor para configurar um atalho de home page:

|    Chave    |    Value    |
|-------------------------------------------------------------------|-------------|
|    com.microsoft.intune.mam.managedbrowser.homepage   |    Especifique um URL válido. Os URLs incorretos são bloqueados como medida de segurança.<br>**Exemplo:** `<https://www.bing.com`>
    |

## <a name="how-to-configure-managed-bookmarks-for-microsoft-edge"></a>Como configurar indicadores geridos para o Microsoft Edge

Para facilitar o acesso, pode configurar os marcadores que gostaria de ter os seus utilizadores ter disponível quando estão a utilizar Microsoft Edge. Aqui estão alguns detalhes:

- Estes marcadores apenas serão apresentada aos utilizadores quando estão a utilizar o modo de empresa do Microsoft Edge. 
- Estes marcadores não podem ser eliminados ou modificados por utilizadores.
- Estes marcadores são apresentados no início da lista. Todos os marcadores criados pelos utilizadores serão apresentados abaixo destes.
- Se já ativou o redirecionamento do Proxy de Aplicações, pode adicionar aplicações Web do Proxy de Aplicações através do respetivo URL interno ou externo.

Utilize o seguinte par chave/valor para configurar os marcadores geridos:

|    Chave    |    Value    |
|---------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    com.microsoft.intune.mam.managedbrowser.bookmarks    |    O valor para esta configuração é uma lista de marcadores. Cada marcador é constituído pelo título e o URL de marcador. Separe o título e o URL com o `|` caráter.      **Example:**<br>`Microsoft Bing|https://www.bing.com`<p>Para configurar múltiplos marcadores, separe cada par com o caráter duplo `||`.<p>**Example:**<br>`Microsoft Bing|https://www.bing.com||Contoso|https://www.contoso.com`    |

## <a name="how-to-display-myapps-within-microsoft-edge-bookmarks"></a>Como exibir MyApps dentro de marcadores do Microsoft Edge

Por predefinição, os utilizadores serão apresentados os sites de My Apps que estão configurados para-los numa pasta dentro de marcadores do Microsoft Edge. A pasta serão identificados como com o nome da sua organização.

|    Chave    |    Valor    |
|------------------------------------------------------|----------------------------------------------------------------------------------------------------------------|
|    com.microsoft.intune.mam.managedbrowser.MyApps    |    **Verdadeiro** mostra MyApps dentro os indicadores do Microsoft Edge.<p>**FALSO** oculta MyApps dentro do Microsoft Edge.    |

## <a name="how-to-specify-allowed-or-blocked-sites-list-for-microsoft-edge"></a>Como especificar a lista de sites permitidos ou bloqueados para o Microsoft Edge
Pode utilizar a configuração de aplicações para definir os sites que os utilizadores podem aceder ao utilizar o seu perfil de trabalho. Se utilizar uma lista de permissões, os usuários apenas de ser capazes de aceder aos sites que tiver de ser listados explicitamente. Se utilizar uma lista de bloqueados, os utilizadores serão capazes de aceder a todos os sites, exceto para os sites que já explicitamente bloqueado. Apenas deve impor qualquer um de um permitidos ou bloquear a lista, não ambos. Se ambos forem direcionadas para o dispositivo, a lista de permissões será cumprida.  

Pode utilizar o abaixo pares chave/valor para configurar uma lista de sites permitidos ou bloqueados para o Microsoft Edge. Continue a ler para obter mais informações sobre formatos de URL válidos. 

|    Chave    |    Value    |
|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    Escolha entre:<p>1. Especificar URLs permitidos (apenas estes URLs são permitidos; não pode aceder a mais nenhum site):<br>`com.microsoft.intune.mam.managedbrowser.AllowListURLs`<p>2. Especificar URLs bloqueados (é possível aceder a todos os outros sites):<br>`com.microsoft.intune.mam.managedbrowser.BlockListURLs`    |    O valor correspondente da chave é uma lista de URLs. Introduza todos os URLs que pretende permitir ou bloquear como um único valor, separado por um pipe `|` caráter.<p>**Exemplos:**<br>`URL1|URL2|URL3`<br>`http://.contoso.com/|https://.bing.com/|https://expenses.contoso.com`  |

### <a name="url-formats-for-allowed-and-blocked-site-list"></a>Formatos de URL para permitidas e bloqueadas a lista de sites 
Pode usar vários formatos de URL para criar as suas listas de sites permitido/bloqueado. Esses padrões permitidos são detalhados na tabela abaixo. Algumas notas antes de começar: 
- Certifique-se de que adiciona o prefixo **http** ou **https** a todos os URLs quando os introduzir na lista.
- Pode utilizar o símbolo de caráter universal (*), de acordo com as regras na lista de padrões permitidos seguinte.
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
    |    `http://www.contoso.com:80`    |    Corresponde a uma única página, ao utilizar um número de porta    |    http://www.contoso.com:80    |         |
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
    - `http://www.contoso.com:*`
    - `http://www.contoso.com: /*`
  
## <a name="defining-behavior-when-users-try-to-access-a-blocked-site"></a>Definir o comportamento quando os utilizadores tentam aceder um site bloqueado

Com o modelo de identidade dupla incorporado no Microsoft Edge, pode ativar uma experiência mais flexível para os utilizadores finais que não era possível com o Intune Managed Browser. Quando os utilizadores aceder um site bloqueado no Microsoft Edge, pode ser pedidos para abrir a ligação no seu contexto pessoal em vez de seu contexto de trabalho, o qual permite que sejam se manterem protegidos, enquanto mantém a recursos da empresa seguros. Por exemplo, se um utilizador é enviado uma ligação para um artigo de notícias através do respetivo Outlook, poderão abrir a ligação no seu contexto de pessoa ou numa guia InPrivate em vez de seu contexto de trabalho, que permite que os Web sites de notícias. Por predefinição, são permitidas essas transições.

Utilize o abaixo par chave/valor para configurar se essas transições de forma recuperável são permitidas:

|    Chave    |    Value    |
|----------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    `com.microsoft.intune.mam.managedbrowser.AllowTransitionOnBlock`    |    **Verdadeiro** permite que o Microsoft Edge para os utilizadores de transição para seu contexto com pessoal para abrir sites bloqueados<p>**Bloco** impede que o Microsoft Edge fazer a transição de usuários, e os usuários simplesmente serão apresentados uma mensagem a indicar que o site que estão a tentar aceder está bloqueado.    |

## <a name="directing-users-to-microsoft-edge-instead-of-the-intune-managed-browser"></a>Direcionar os utilizadores para o Microsoft Edge em vez do Intune Managed Browser 

O Intune Managed Browser e o Microsoft Edge são agora podem ser utilizados como navegadores protegido por políticas. Para garantir que os seus utilizadores estão a ser direcionados para utilizar a aplicação de browser correto, direcionar todas as aplicações geridas do Intune (por exemplo, o Outlook e o OneDrive) com a definição de configuração seguinte:

|    Chave    |    Value    |
|------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
|    `com.microsoft.intune.useEdge`    |    O valor `true` irá direcionar os utilizadores a utilizar o Microsoft Edge.<p>O valor `false` direcionará os seus utilizadores para utilizarem o Intune Managed Browser.    |

Se este valor de configuração de aplicação não estiver definido, a seguinte lógica irá definir o browser será utilizado para abrir ligações empresariais.

No Android:
- O Intune Managed Browser será iniciado se um utilizador tiver o Browser gerido do Intune e o Microsoft Edge transferido no seu dispositivo. 
- Microsoft Edge irá abrir se apenas o Microsoft Edge é transferido no dispositivo e destina-se com a política do Intune.
- Managed Browser será aberto se apenas o Managed Browser está no dispositivo e destina-se com a política do Intune.

No iOS, para aplicações que integraram o SDK do Intune para iOS v. 9.0.9+:
- O Intune Managed Browser será iniciado se o Browser gerido e o Microsoft Edge no dispositivo.  
- Microsoft Edge irá iniciar se apenas o Microsoft Edge está no dispositivo e destina-se com a política do Intune.
- Browser gerido se apenas o Managed Browser está no dispositivo e destina-se com a política do Intune.

## <a name="using-microsoft-edge-on-ios-to-access-managed-app-logs"></a>Usando o Microsoft Edge em dispositivos iOS para aceder aos registos de aplicação gerida 

Os utilizadores finais com o Microsoft Edge instalado nos respetivos dispositivos iOS podem ver o estado de gestão de todas as aplicações publicadas da Microsoft. Podem enviar registos para resolver problemas das respetivas aplicações iOS geridas.
1. Abra o Microsoft Edge no seu dispositivo iOS.
2. Escreva `about:intunehelp` na caixa de endereço. 
3. Modo de resolução de problemas irá ser executada a partir do Microsoft Edge.

Para obter uma lista das definições armazenados nos registos das aplicações, veja [Review app protection logs in the Managed Browser (Rever os registos de proteção das aplicações no Managed Browser)](app-protection-policy-settings-log.md).

Para ver como ver os registos em dispositivos Android, veja [enviar registos ao administrador de TI por e-mail](https://docs.microsoft.com/intune-user-help/send-logs-to-your-it-admin-by-email-android). 

## <a name="security-and-privacy-for-microsoft-edge"></a>Segurança e privacidade para o Microsoft Edge

Segurança e privacidade considerações adicionais para o Microsoft Edge:

- Microsoft Edge não consome as definições que os utilizadores definidos para o navegador nativo nos respetivos dispositivos, porque o Microsoft Edge não é possível aceder a estas definições.
- Se configurar a opção **exigir PIN simples para acesso** ou **exigir credenciais da empresa para obter acesso** numa aplicação associado à política de proteção com o Microsoft Edge e um utilizador seleciona a ligação de ajuda sobre o página de autenticação, pode procurar sites na Internet independentemente de terem sido adicionados a uma lista de bloqueios na política.
- Microsoft Edge só pode bloquear acesso a sites quando estes são acedidos diretamente. Não bloqueia o acesso quando são utilizados serviços intermédios (como um serviço de tradução) para aceder ao site.
- Para permitir a autenticação e acesso a documentação do Intune, ***. microsoft.com** está excluído das definições da lista de permissões ou de bloqueios. É sempre permitido.
Desative a dados de utilização do Microsoft automaticamente recolhe dados anónimos sobre o desempenho e a utilização do Browser gerido para melhorar os produtos e serviços Microsoft. Os utilizadores podem desativar a recolha de dados com a definição **Dados de Utilização** nos respetivos dispositivos. OS utilizadores não têm controlo sobre a recolha destes dados. Em dispositivos iOS, os sites que os utilizadores visitam que têm um certificado expirado ou não fidedigno não podem ser abertos.

## <a name="next-steps"></a>Passos Seguintes

- [O que são as políticas de proteção de aplicações?](app-protection-policy.md) 
