---
title: Gerir o acesso à Web com a aplicação Managed Browser
titlesuffix: Microsoft Intune
description: Implemente a aplicação Managed Browser para restringir a navegação na Web e a transferência de dados da Web para outras aplicações.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/14/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 1feca24f-9212-4d5d-afa9-7c171c5e8525
ms.reviewer: maxles
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 742173c1ef53337dab35694c0c04cbca60dbb07c
ms.sourcegitcommit: 54fc806036f84a8667cf8f74086358bccd30aa7d
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/20/2018
---
# <a name="manage-internet-access-using-managed-browser-policies-with-microsoft-intune"></a>Gerir o acesso à Internet através de políticas do Managed Browser com o Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

O Managed Browser é uma aplicação de navegação na Web que pode transferir a partir de lojas de aplicações públicas para utilização na sua organização. Quando configurado com o Intune, o Managed Browser pode ser:
- Utilizado para aceder a sites empresariais e aplicações SaaS com o Início de Sessão Único através do serviço MyApps enquanto mantém os dados da Web protegidos.
- Pré-configurado com uma lista de URLs e domínios para restringir os sites para os quais o utilizador pode navegar no contexto empresarial.
- Pré-configurado com uma home page e os marcadores que especificar.

Uma vez que esta aplicação tem integração com o SDK do Intune, também pode aplicar políticas de proteção de aplicações à mesma, incluindo:
- Controlar a utilização dos comandos Cortar, Copiar e Colar
- Impedir as capturas de ecrã
- Garantir que as ligações para conteúdos selecionados pelos utilizadores só podem ser abertas noutras aplicações geridas.

Para obter detalhes, veja [O que são as políticas de proteção de aplicações?](/intune/app-protection-policy.md)

Pode aplicar estas definições a:

- Dispositivos que estão inscritos no Intune
- Dispositivos que estão inscritos noutro produto MDM
- Dispositivos não geridos

Caso os utilizadores instalem o Managed Browser a partir da loja de aplicações e o mesmo não seja gerido pelo Intune, aquele pode ser utilizado como um browser básico, com suporte para Início de Sessão Único através do site Microsoft MyApps. Os utilizadores são diretamente direcionados para o site MyApps, onde podem ver todas as suas aplicações SaaS aprovisionadas.
Enquanto o Managed Browser não for gerido pelo Intune, não poderá aceder a dados de outras aplicações geridas com o Intune. 

O Managed Browser não suporta o protocolo criptográfico do Secure Sockets Layer versão 3 (SSLv3).

Pode criar políticas de Managed Browser para os seguintes tipos de dispositivos:

-   Dispositivos a executar o Android 4 e posterior

-   Dispositivos com iOS 8.0 ou posterior

>[!IMPORTANT]
>A partir de outubro de 2017, a aplicação Intune Managed Browser no Android irá suportar apenas dispositivos com o Android 4.4 e posterior. A aplicação Intune Managed Browser no iOS irá suportar apenas dispositivos a executar o iOS 9.0 e posterior.
>As versões anteriores do Android e iOS poderão continuar a utilizar o Managed Browser, mas não poderão instalar novas versões da aplicação e poderão não conseguir aceder a todas as funcionalidades da aplicação. Aconselhamos que atualize estes dispositivos para uma versão do sistema operativo suportada.


O Intune Managed Browser suporta a abertura de conteúdos da Web de [Parceiros de aplicações do Microsoft Intune](https://www.microsoft.com/cloud-platform/microsoft-intune-apps).

## <a name="conditional-access-for-the-intune-managed-browser"></a>Acesso Condicional para o Intune Managed Browser

O Managed Browser é agora uma aplicação aprovada do cliente para Acesso Condicional. Isto significa que pode restringir o acesso móvel através do browser às aplicações Web ligadas ao Azure AD em que os utilizadores apenas podem utilizar o Managed Browser e o acesso a partir de outros browsers desprotegidos, como o Safari ou o Chrome, é bloqueado. Esta proteção pode ser aplicada a recursos do Azure, como o Exchange Online e o SharePoint Online, o portal do Office e sites no local que foram expostos a utilizadores externos através do [Proxy de Aplicações do Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started). 

Para restringir as aplicações Web ligadas ao Azure AD à utilização do Intune Managed Browser em plataformas móveis, pode criar uma política de Acesso Condicional do Azure AD que requeira aplicações do cliente aprovadas. 

1. No portal do Azure, selecione **Azure Active Directory** > **Aplicações empresariais** > **Acesso condicional** > **Nova política**. 
2. Em seguida, selecione **Conceder** na secção **Controlos de acesso** do painel. 
3. Clique em **Requer aplicação aprovada do cliente**. 
4. Clique em **Selecionar** no painel **Conceder**. Esta política tem de ser atribuída às aplicações na cloud que pretende que sejam acessíveis apenas a partir da aplicação Intune Managed Browser.

    ![Azure AD – política de acesso condicional do Managed Browser](./media/managed-browser-conditional-access-01.png)

5. Na secção **Atribuições**, selecione **Condições** > **Aplicações do cliente**. O painel **Aplicações do cliente** é apresentado.
6. Clique em **Sim** em **Configurar** para aplicar a política a aplicações do cliente específicas.
7. Certifique-se de que a opção **Browser** está selecionada como uma aplicação do cliente.

    ![Azure AD – Managed Browser – selecionar aplicações do cliente](./media/managed-browser-conditional-access-02.png)

    > [!NOTE]
    > Se quiser restringir as aplicações nativas (aplicações não baseadas no browser) que podem aceder a estas aplicações na cloud, também pode selecionar **Aplicações móveis e clientes de ambiente de trabalho**.

8. Na secção **Atribuições**, selecione **Utilizadores e grupos** e, em seguida, selecione os utilizadores e grupos aos quais pretende atribuir esta política. 

    > [!NOTE]
    > Os utilizadores também têm de ser visados pela política de Proteção de Aplicações do Intune. Para obter mais informações sobre a criação de políticas de Proteção de Aplicações do Intune, veja [O que são as políticas de proteção de aplicações?](app-protection-policy.md).

9. Na secção **Atribuições**, selecione **Aplicações na cloud** para selecionar que aplicações quer proteger com esta política.

Quando a política acima estiver configurada, os utilizadores serão obrigados a utilizar o Intune Managed Browser para aceder às aplicações Web ligadas ao Azure AD que protegeu com esta política. Se os utilizadores tentarem utilizar um browser não gerido neste cenário, verão um aviso a informá-los que têm de utilizar o Intune Managed Browser.

##  <a name="single-sign-on-to-azure-ad-connected-web-apps-in-the-intune-managed-browser"></a>Início de Sessão Único nas aplicações Web ligadas ao Azure AD no Intune Managed Browser

A aplicação Intune Managed Browser em dispositivos iOS e Android pode agora tirar partido do SSO em todas as aplicações Web (SaaS e no local) ligadas ao Azure AD. Quando a aplicação Microsoft Authenticator está presente num dispositivo iOS ou a aplicação Portal da Empresa do Intune num dispositivo Android, os utilizadores do Intune Managed Browser poderão aceder às aplicações Web ligadas ao Azure AD sem terem de reintroduzir as respetivas credenciais.

O SSO no Intune Managed Browser requer que o seu dispositivo esteja registado pela aplicação Microsoft Authenticator em dispositivos iOS ou pelo Portal da Empresa do Intune em dispositivos Android. Será pedido aos utilizadores com a aplicação Authenticator ou Portal da Empresa do Intune que registem o respetivo dispositivo quando navegarem para uma aplicação Web ligada ao Azure AD no Intune Managed Browser, se o respetivo dispositivo ainda não tiver sido registado por outra aplicação. Assim que o dispositivo estiver registado com a conta gerida pelo Intune, essa conta terá o SSO ativado para as aplicações Web ligadas ao Azure AD. 

> [!NOTE]
> O registo do dispositivo é uma simples verificação do serviço Azure AD. Não requer a inscrição total do dispositivo e não fornece privilégios adicionais à equipa de TI no dispositivo.

## <a name="create-a-managed-browser-app-configuration"></a>Criar uma configuração da aplicação Managed Browser

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços** > **Intune**. O Intune encontra-se na secção **Monitorização + Gestão**.
3.  No painel **Aplicações móveis** da lista Gestão, selecione **Políticas de configuração de aplicações**.
4.  No painel **Políticas de configuração de aplicações**, escolha **Adicionar**.
5.  No painel **Adicionar política de configuração**, introduza um **Nome** e uma **Descrição** opcional para as definições de configuração da aplicação.
6.  Para o tipo de **Inscrição de dispositivos**, selecione **Aplicações geridas**.
7.  Selecione **Selecionar a aplicação necessária** e, em seguida, no painel **Aplicações de destino**, selecione o **Managed Browser** para iOS, Android ou para ambos.
8.  Selecione **OK** para regressar ao painel **Política de configuração da aplicação**.
9.  Selecione **Definições de configuração**. No painel **Configuração**, define os pares de chave e valor para fornecer as configurações para o Managed Browser. Utilize as secções mais adiante neste artigo para saber mais sobre os diferentes pares de chave e valor que pode definir.
10. Quando tiver terminado, escolha **OK**.
11. No painel **Adicionar política de configuração**, selecione **Adicionar**.
12. A nova configuração é criada e apresentada no painel **Configuração de aplicações**.

>[!IMPORTANT]
>Atualmente, o Managed Browser depende da inscrição automática. Para aplicar as configurações de aplicações, tem de existir outra aplicação no dispositivo já gerida pelas políticas de proteção de aplicações do Intune.

## <a name="assign-the-configuration-settings-you-created"></a>Atribuir as definições de configuração que criou

Atribua as definições a grupos de utilizadores do Azure AD. Se esse utilizador tiver a aplicação Managed Browser instalada, a aplicação será gerida pelas definições que especificou.

1. No painel **Aplicações móveis** do dashboard de gestão de aplicações móveis do Intune, selecione **Políticas de configuração de aplicações**.
2. Na lista de configurações de aplicações, selecione aquela que pretende atribuir.
3. No painel seguinte, selecione **Atribuições**.
4. No painel **Atribuições**, selecione o grupo do Azure AD ao qual pretende atribuir a configuração da aplicação e, em seguida, selecione **OK**.


## <a name="how-to-configure-application-proxy-settings-for-the-managed-browser"></a>Como configurar as definições de Proxy de Aplicações do Managed Browser

O Intune Managed Browser e o [Proxy de Aplicações do Azure AD]( https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started) podem ser utilizados em conjunto para suportar os seguintes cenários para utilizadores de dispositivos iOS e Android:

- Um utilizador transfere e inicia sessão na aplicação Microsoft Outlook. As políticas de proteção de aplicações do Intune são aplicadas automaticamente. Encriptam os dados guardados e impedem que o utilizador transfira ficheiros empresariais para aplicações ou localizações não geridas no dispositivo. Quando o utilizador clica numa ligação para um site da intranet no Outlook, pode especificar se a ligação é aberta na aplicação Managed Browser, em vez de noutro browser. O Managed Browser reconhece que este site da intranet foi exposto ao utilizador através do Proxy de Aplicações. O utilizador é encaminhado automaticamente através do Proxy de Aplicações para se autenticar com qualquer autenticação multifator e acesso condicional aplicáveis antes de chegar ao site da intranet. Este site, que anteriormente não podia ser encontrado por utilizadores remotos, está agora acessível e a ligação no Outlook funciona como esperado.
- Um utilizador remoto abre a aplicação Managed Browser e navega para um site da intranet através do URL interno. O Managed Browser reconhece que este site da intranet foi exposto ao utilizador através do Proxy de Aplicações. O utilizador é encaminhado automaticamente através do Proxy de Aplicações para se autenticar com qualquer autenticação multifator e acesso condicional aplicáveis antes de chegar ao site da intranet. Este site, que anteriormente os utilizadores remotos não podiam encontrar, está agora acessível.

### <a name="before-you-start"></a>Antes de começar

- Configure as suas aplicações internas através do Proxy de Aplicações do Azure AD.
    - Para configurar o Proxy de Aplicações e publicar aplicações, veja a [documentação de configuração]( https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started#how-to-get-started). 
- Tem de utilizar a versão mínima da aplicação Managed Browser 1.2.0.
- Os utilizadores da aplicação Managed Browser têm uma [política de proteção de aplicações do Intune]( app-protection-policy.md) atribuída à aplicação.

    > [!NOTE]
    > Os dados atualizados de redirecionamento do Proxy de Aplicações podem demorar até 24 horas a entrar em vigor no Managed Browser.


#### <a name="step-1-enable-automatic-redirection-to-the-managed-browser-from-outlook"></a>Passo 1: ativar o redirecionamento automático para o Managed Browser a partir do Outlook
O Outlook tem de estar configurado com uma política de proteção de aplicações que ative a definição **Restringir o conteúdo Web a apresentar no Managed Browser**.

#### <a name="step-2-assign-an-app-configuration-policy-assigned-for-the-managed-browser"></a>Passo 2: atribuir uma política de configuração de aplicações que atribuiu ao Managed Browser.
Este procedimento configura a aplicação Managed Browser para utilizar o redirecionamento do proxy de aplicações. Ao utilizar o procedimento para criar uma configuração da aplicação Managed Browser, forneça o seguinte par de chave e valor:

|||
|-|-|
|Chave|Valor|
|**com.microsoft.intune.mam.managedbrowser.AppProxyRedirection**|**verdadeiro**|

Para obter mais informações sobre como o Managed Browser e o Proxy de Aplicações do Azure AD podem ser utilizados em conjunto para um acesso fácil (e seguro) a aplicações Web no local, veja a mensagem de blogue do Enterprise Mobility + Security [Better together: Intune and Azure Active Directory team up to improve user access](https://cloudblogs.microsoft.com/enterprisemobility/2017/07/06/better-together-intune-and-azure-active-directory-team-up-to-improve-user-access) (Melhor em conjunto: o Intune e o Azure Active Directory juntam-se para melhorar o acesso do utilizador).

## <a name="how-to-configure-the-homepage-for-the-managed-browser"></a>Como configurar a home page do Managed Browser

Esta definição permite-lhe configurar a home page que os utilizadores veem ao iniciar o Managed Browser ou ao criar um novo separador. Ao utilizar o procedimento para criar uma configuração da aplicação Managed Browser, forneça o seguinte par de chave e valor:

|||
|-|-|
|Chave|Valor|
|**com.microsoft.intune.mam.managedbrowser.homepage**|Especifique um URL válido. Os URLs incorretos são bloqueados como medida de segurança.<br>Exemplo: **https://www.bing.com**|


## <a name="how-to-configure-bookmarks-for-the-managed-browser"></a>Como configurar os marcadores do Managed Browser

Esta definição permite-lhe configurar um conjunto de marcadores disponível para os utilizadores do Managed Browser.

- Estes marcadores não podem ser eliminados ou modificados pelos utilizadores
- Estes marcadores são apresentados no início da lista. Todos os marcadores criados pelos utilizadores serão apresentados abaixo destes.
- Se já ativou o redirecionamento do Proxy de Aplicações, pode adicionar aplicações Web do Proxy de Aplicações através do respetivo URL interno ou externo.

Ao utilizar o procedimento para criar uma configuração da aplicação Managed Browser, forneça o seguinte par de chave e valor:

|||
|-|-|
|Chave|Valor|
|**com.microsoft.intune.mam.managedbrowser.bookmarks**|O valor desta configuração é uma lista de marcadores. Cada marcador é constituído pelo título e URL do marcador. Separe o título e o URL com o caráter **&#124;**.<br><br>Exemplo: **Microsoft Bing&#124;https://www.bing.com**<br><br>Para configurar múltiplos marcadores, separe cada par com o caráter duplo **&#124;&#124;**<br><br>Exemplo: **Bing&#124;https://www.bing.com&#124;&#124;Contoso&#124;https://www.contoso.com**|

## <a name="how-to-specify-allowed-and-blocked-urls-for-the-managed-browser"></a>Como especificar URLs permitidos e bloqueados para o Managed Browser

Ao utilizar o procedimento para criar uma configuração da aplicação Managed Browser, forneça o seguinte par de chave e valor:

|||
|-|-|
|Chave|Valor|
|Escolha entre:<br><br>– Especificar URLs permitidos (apenas esses URLs são permitidos; nenhum outro site pode ser acedido): **com.microsoft.intune.mam.managedbrowser.AllowListURLs**<br><br>– Especificar URLs bloqueados (é possível aceder a todos os outros sites): <br><br>**com.microsoft.intune.mam.managedbrowser.BlockListURLs**|O valor correspondente da chave é uma lista de URLs. Introduza todos os URLs que pretende permitir ou bloquear como um único valor, separado por um caráter de pipe **&#124;**.<br><br>Exemplos:<br><br>**URL1&#124;URL2&#124;URL3**<br>**http://*.contoso.com/*&#124;https://*.bing.com/*&#124;https://expenses.contoso.com**|

>[!IMPORTANT]
>Não especifique ambas as chaves. Se as duas chaves forem direcionadas para o mesmo utilizador, a chave de permissão é utilizada, uma vez que é a opção mais restritiva.
>Além disso, confirme que não bloqueia páginas importantes tais como os sites da empresa.

### <a name="url-format-for-allowed-and-blocked-urls"></a>Formato do URL para URLs permitidos e bloqueados
Utilize as informações seguinte para saber mais sobre os formatos permitidos e os carateres universais que pode utilizar ao especificar os URLs na lista de permissões e bloqueios:

-   Pode utilizar o símbolo de caráter universal (**&#42;**) de acordo com as regras na lista de padrões permitidos seguinte:

-   Certifique-se de que adiciona o prefixo **http** ou **https** a todos os URLs quando os introduzir na lista.

-   Pode especificar os números da porta no endereço. Se não especificar um número da porta, os valores utilizados são:

    -   Porta 80 para http

    -   Porta 443 para https

    Não é suportado utilizar carateres universais para o número de porta. Por exemplo, **http&colon;//www&period;contoso&period;com:*** e **http&colon;//www&period;contoso&period;com: /*;** não são suportados.

-   Utilize a tabela seguinte para saber mais sobre os padrões permitidos que pode utilizar ao especificar URLs:

|URL|Detalhes|Correspondências|Não corresponde|
|-------|---------------|-----------|------------------|
|http://www.contoso.com|Corresponde a uma única página|www.contoso.com|host.contoso.com<br /><br />www.contoso.com/images<br /><br />contoso.com/|
|http://contoso.com|Corresponde a uma única página|contoso.com/|host.contoso.com<br /><br />www.contoso.com/images<br /><br />www.contoso.com|
|http://www.contoso.com/&#42;|Corresponde a todos os URLs que começam com www.contoso.com|www.contoso.com<br /><br />www.contoso.com/images<br /><br />www.contoso.com/videos/tvshows|host.contoso.com<br /><br />host.contoso.com/images|
|http://&#42;.contoso.com/&#42;|Corresponde a todos os subdomínios em contoso.com|developer.contoso.com/resources<br /><br />news.contoso.com/images<br /><br />news.contoso.com/videos|contoso.host.com|
|http://www.contoso.com/images|Corresponde a uma única pasta|www.contoso.com/images|www.contoso.com/images/dogs|
|http://www.contoso.com:80|Corresponde a uma única página, ao utilizar um número de porta|http://www.contoso.com:80|
|https://www.contoso.com|Corresponde a uma única página segura|https://www.contoso.com|http://www.contoso.com|
|http://www.contoso.com/images/&#42;|Corresponde a uma única pasta e a todas as subpastas|www.contoso.com/images/dogs<br /><br />www.contoso.com/images/cats|www.contoso.com/videos|

-   Seguem-se exemplos de algumas entradas que não pode especificar:

    -   &#42;.com

    -   &#42;.contoso/&#42;

    -   www.contoso.com/&#42;images

    -   www.contoso.com/&#42;images&#42;pigs

    -   www.contoso.com/page&#42;

    -   Endereços IP

    -   https://&#42;

    -   http://&#42;

    -   http://www.contoso.com:&#42;

    -   http://www.contoso.com: /&#42;

## <a name="how-to-access-to-managed-app-logs-using-the-managed-browser-on-ios"></a>Como aceder aos registos da aplicação gerida através do Managed Browser no iOS

Os utilizadores finais com o Managed Browser instalado nos respetivos dispositivos iOS podem ver o estado de gestão de todas as aplicações publicadas da Microsoft. Podem enviar registos para resolver problemas das respetivas aplicações iOS geridas.

1. Abra as **Definições** do iOS.
2. Selecione as definições da aplicação **Managed Browser**.
3. Ative/Desative a opção **Ativar o Diagnóstico do Intune** para definir o browser para o modo de resolução de problemas.
4. Abra o **Managed Browser**. Clique em **Ver Estado da Aplicação do Intune** para consultar as definições de política de aplicações individuais.
5. Prima **Começar** e **Partilhar Registos** ou **Enviar Registos para a Microsoft** para enviar os registos de resolução de problemas para o seu administrador de TI ou para a Microsoft.

Também pode abrir o Browser no modo de resolução de problemas a partir da aplicação.

1. Abra o Managed Browser.
2. Escreva `about:intunehelp` na caixa de endereço.
O Browser inicia o modo de resolução de problemas.

Para obter uma lista das definições armazenadas nos registos das aplicações, veja [Review app protection logs in the Managed Browser (Rever os registos de proteção das aplicações no Managed Browser)](app-protection-policy-settings-log.md).

## <a name="security-and-privacy-for-the-managed-browser"></a>Segurança e privacidade do Managed Browser

-   O Managed Browser não utiliza as definições que os utilizadores criam para o browser incorporado nos seus dispositivos. O Managed Browser não consegue aceder a estas definições.

-   Se configurar a opção **Exigir PIN simples para o acesso** ou **Exigir credenciais de empresa para o acesso** numa política de proteção de aplicações associada ao Managed Browser e um utilizador selecionar a ligação de ajuda na página de autenticação, este pode procurar sites na Internet independentemente de terem sido adicionados a uma lista de bloqueios na política.

-   O Managed Browser só pode bloquear o acesso a sites quando estes são acedidos diretamente. Não bloqueia o acesso quando são utilizados serviços intermédios (como um serviço de tradução) para aceder ao site.

-   Para permitir a autenticação e aceder à documentação do Intune, **&#42;.microsoft.com** está excluído das definições da lista de permissões ou de bloqueios. É sempre permitido.

### <a name="turn-off-usage-data"></a>Desativar dados de utilização
A Microsoft recolhe automaticamente dados anónimos sobre o desempenho e a utilização do Managed Browser para melhorar os produtos e serviços Microsoft. Os utilizadores podem desativar a recolha de dados com a definição **Dados de Utilização** nos respetivos dispositivos. OS utilizadores não têm controlo sobre a recolha destes dados.


-   Em dispositivos iOS, os sites que os utilizadores visitam que têm um certificado expirado ou não fidedigno não podem ser abertos.
-   O Managed Browser não utiliza as definições que os utilizadores criam para o browser incorporado nos seus dispositivos. O Managed Browser não consegue aceder a estas definições.

-   Se configurar a opção **Exigir PIN simples para o acesso** ou **Exigir credenciais de empresa para o acesso** numa política de proteção de aplicações associada ao Managed Browser e um utilizador selecionar a ligação de ajuda na página de autenticação, este pode procurar sites na Internet independentemente de terem sido adicionados a uma lista de bloqueios na política.

-   O Managed Browser só pode bloquear o acesso a sites quando estes são acedidos diretamente. Não bloqueia o acesso quando são utilizados serviços intermédios (como um serviço de tradução) para aceder ao site.

-   Para permitir a autenticação e aceder à documentação do Intune, **&#42;.microsoft.com** está excluído das definições da lista de permissões ou de bloqueios. É sempre permitido.

### <a name="turn-off-usage-data"></a>Desativar dados de utilização
A Microsoft recolhe automaticamente dados anónimos sobre o desempenho e a utilização do Managed Browser para melhorar os produtos e serviços Microsoft. Os utilizadores podem desativar a recolha de dados com a definição **Dados de Utilização** nos respetivos dispositivos. OS utilizadores não têm controlo sobre a recolha destes dados.

## <a name="next-steps"></a>Próximos passos

- [O que são as políticas de proteção de aplicações?](app-protection-policy.md)