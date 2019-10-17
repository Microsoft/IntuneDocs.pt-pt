---
title: Gerir o acesso Web empresarial com um browser protegido por políticas
titleSuffix: Microsoft Intune
description: Utilize um browser protegido por políticas atribuído pelo Intune para gerir a navegação Web empresarial e a transferência de dados da Web.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/27/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 1feca24f-9212-4d5d-afa9-7c171c5e8525
ms.reviewer: ilwu
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure, seoapril2019
ms.collection: M365-identity-device-management
ms.openlocfilehash: 57ae1b5a51533bf14d4299fcf0248564562289f7
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72507563"
---
# <a name="manage-web-access-using-a-microsoft-intune-policy-protected-browser"></a>Gerir o acesso Web através de um browser protegido por políticas do Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Ao utilizar um browser protegido com a política do Intune (Microsoft Edge ou Intune Managed Browser), pode garantir que os sites empresariais são sempre acedidos com as proteções ativas.  Quando configurados com o Intune, os browsers protegidos podem tirar partido do seguinte:

- Políticas de proteção de aplicações
- Conditional Access
- Logon único
- Definições de configuração de aplicações
- Integração do proxy de aplicações do Azure

## <a name="microsoft-edge-support"></a>Suporte ao Microsoft Edge

Pode utilizar o Microsoft Edge para cenários empresariais em dispositivos iOS e Android. O Microsoft Edge dá suporte a todos os cenários de gestão que o Intune Managed Browser com a adição de melhorias na experiência dos utilizadores finais. Os seguintes recursos do Microsoft Edge Enterprise que são habilitados pelas políticas do Intune incluem:

- **Identidade Dupla** – os utilizadores podem adicionar uma conta profissional e conta pessoal para navegação. Não há uma separação total entre as duas identidades, semelhante à arquitetura e à experiência no Office 365 e no Outlook. Os administradores do Intune poderão definir as políticas pretendidas para uma experiência de navegação protegida na conta profissional. 
- **Integração de políticas de proteção de aplicações do Intune** – os administradores agora podem aplicar políticas de proteção de aplicações ao Microsoft Edge, incluindo o controlo das ações de cortar, copiar e colar, ao impedir as capturas de ecrã e ao garantir que as ligações selecionadas pelo utilizador abrem apenas noutras aplicações geridas.
- **Integração do Proxy de Aplicações do Azure** – os administradores podem controlar o acesso a aplicações SaaS e aplicações Web, ao ajudar a garantir que as aplicações baseadas no browser são executadas apenas no browser Microsoft Edge seguro, quer os utilizadores finais se liguem a partir da rede empresarial ou a partir da Internet. 
- **Favoritos Geridos e atalhos da Home Page** – Para facilidade de acesso, os administradores podem definir URLs para serem apresentadas nos Favoritos quando os utilizadores finais estão no contexto empresarial. Os administradores podem definir um atalho de home page, que será mostrado como atalho primário quando o utilizador empresarial abre uma nova página ou um novo separador no Microsoft Edge.

As políticas de proteção do Microsoft Intune para o Microsoft Edge ajudam a proteger os dados e os recursos da sua organização. O Microsoft Edge protegido pelo Intune garante que os recursos da empresa estão protegidos, não só nas aplicações instaladas nativamente como também quando acedidos através do browser.

## <a name="getting-started"></a>Introdução

O Microsoft Edge e o Intune Managed Browser são aplicações de browser que você e os seus utilizadores finais podem transferir a partir de lojas de aplicações públicas para utilização na sua organização. 

Requisitos de sistema operativo para políticas de browser:
- Android 4 e posterior ou
- iOS 8.0 e posterior.

As versões anteriores do Android e iOS poderão continuar a utilizar o Managed Browser, mas não poderão instalar novas versões da aplicação e poderão não conseguir aceder a todas as funcionalidades da aplicação. Aconselhamos que atualize estes dispositivos para uma versão do sistema operativo suportada.

>[!NOTE]
>O Managed Browser não suporta o protocolo criptográfico do Secure Sockets Layer versão 3 (SSLv3).


## <a name="application-protection-policies-for-protected-browsers"></a>Políticas de proteção de aplicações para browsers protegidos

Uma vez que o Microsoft Edge e o Managed Browser têm integração com o SDK do Intune, também pode aplicar políticas de proteção de aplicações aos mesmos, incluindo:
- Controlar a utilização dos comandos Cortar, Copiar e Colar.
- Impedir as capturas de ecrã.
- Garantir que as ligações empresariais só são abertas em browsers e aplicações geridos.

Para obter detalhes, veja [O que são as políticas de proteção de aplicações?](app-protection-policy.md)

Pode aplicar estas definições a:

- Dispositivos que estão inscritos no Intune
- Dispositivos que estão inscritos noutro produto MDM
- Dispositivos não geridos

>[!NOTE]
>Caso os utilizadores instalem o Managed Browser a partir da loja de aplicações e o mesmo não seja gerido pelo Intune, aquele pode ser utilizado como um browser básico, com suporte para Início de Sessão Único através do site Microsoft MyApps. Os utilizadores são diretamente direcionados para o site MyApps, onde podem ver todas as suas aplicações SaaS aprovisionadas.
Enquanto o Managed Browser ou o Microsoft Edge não for gerido pelo Intune, não poderá aceder a dados de outras aplicações geridas com o Intune. 


## <a name="conditional-access-for-protected-browsers"></a>Acesso Condicional para browsers protegidos

O Managed Browser é agora uma aplicação aprovada do cliente para Acesso Condicional. Isto significa que pode restringir o acesso móvel através do browser às aplicações Web ligadas ao Azure AD em que os utilizadores apenas podem utilizar o Managed Browser e o acesso a partir de outros browsers desprotegidos, como o Safari ou o Chrome, é bloqueado. Esta proteção pode ser aplicada a recursos do Azure, como o Exchange Online e o SharePoint Online, o centro de administração do Microsoft 365 e sites no local que foram expostos a utilizadores externos através do [Proxy de Aplicações do Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started). 

Para impedir que as aplicações Web ligadas ao Azure AD utilizem o Intune Managed Browser em plataformas móveis, pode criar uma política de Acesso Condicional que exija aplicações cliente aprovadas. 

> [!TIP]  
> O Acesso Condicional é uma tecnologia do Azure Active Directory (Azure AD). O nó de Acesso Condicional acedido a partir do *Intune* é o mesmo nó acedido a partir do *Azure AD*.  


1. No portal do Intune, selecione **acesso condicional** > **nova política**. 
2. Em seguida, selecione **Conceder** na secção **Controlos de acesso** do painel. 
3. Clique em **Requer aplicação aprovada do cliente**. 
4. Clique em **Selecionar** no painel **Conceder**. Esta política tem de ser atribuída às aplicações na cloud que pretende que sejam acessíveis apenas a partir da aplicação Intune Managed Browser.

    ![Azure AD-Managed Browser política de acesso condicional](./media/app-configuration-managed-browser/managed-browser-conditional-access-01.png)

5. Na secção **Atribuições**, selecione **Condições** > **Aplicações do cliente**. O painel **Aplicações do cliente** é apresentado.
6. Clique em **Sim** em **Configurar** para aplicar a política a aplicações do cliente específicas.
7. Certifique-se de que a opção **Browser** está selecionada como uma aplicação cliente.

    ![Azure AD – Managed Browser – selecionar aplicações do cliente](./media/app-configuration-managed-browser/managed-browser-conditional-access-02.png)

    > [!NOTE]
    > Se quiser restringir as aplicações nativas (aplicações não baseadas no browser) que podem aceder a estas aplicações na cloud, também pode selecionar **Aplicações móveis e clientes de ambiente de trabalho**.

8. Na secção **Atribuições**, selecione **Utilizadores e grupos** e, em seguida, selecione os utilizadores e grupos aos quais pretende atribuir esta política. 

    > [!NOTE]
    > Os utilizadores também devem ser visados com a política de Proteção de Aplicações do Intune para receber políticas de Configuração de Aplicações. Para obter mais informações sobre a criação de políticas de Proteção de Aplicações do Intune, veja [O que são as políticas de proteção de aplicações?](app-protection-policy.md)

9. Na secção **Atribuições**, selecione **Aplicações na cloud** para selecionar que aplicações quer proteger com esta política.

Quando a política acima estiver configurada, os utilizadores serão obrigados a utilizar o Intune Managed Browser para aceder às aplicações Web ligadas ao Azure AD que protegeu com esta política. Se os utilizadores tentarem utilizar um browser não gerido neste cenário, verão um aviso a informá-los que têm de utilizar o Intune Managed Browser.

O Managed Browser não suporta políticas de Acesso Condicional clássicas. Para obter mais informações, veja [Migrate classic policies in the Azure portal](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-migration) (Migrar políticas clássicas no portal do Azure).

## <a name="single-sign-on-to-azure-ad-connected-web-apps-in-policy-protected-browsers"></a>Início de Sessão Único nas aplicações Web ligadas ao Azure AD em browsers protegidos por política

O Microsoft Edge e o Intune Managed Browser no iOS e no Android podem tirar partido do SSO em todas as aplicações Web (SaaS e no local) ligadas ao Azure AD. Se a aplicação Microsoft Authenticator estiver presente no iOS ou a aplicação Portal da Empresa do Intune no Android, os utilizadores de um browser protegido por política poderão aceder às aplicações Web ligadas ao Azure AD sem terem de reintroduzir as respetivas credenciais.

O SSO exige que o seu dispositivo seja registado pela aplicação Microsoft Authenticator no iOS ou pelo Portal da Empresa do Intune no Android. Será pedido aos utilizadores com a aplicação Authenticator ou o Portal da Empresa do Intune que registem o respetivo dispositivo quando navegarem para uma aplicação Web ligada ao Azure AD num browser protegido por política, se o respetivo dispositivo ainda não tiver sido registado por outra aplicação. Assim que o dispositivo estiver registado com a conta gerida pelo Intune, essa conta terá o SSO ativado para as aplicações Web ligadas ao Azure AD. 

> [!NOTE]
> O registo do dispositivo é uma simples verificação do serviço Azure AD. Não requer a inscrição total do dispositivo e não fornece privilégios adicionais à equipa de TI no dispositivo.

## <a name="create-a-protected-browser-app-configuration"></a>Criar uma configuração da aplicação de browser protegido

>[!IMPORTANT]
>Para aplicar as configurações de aplicações, o browser protegido do utilizador ou outra aplicação no dispositivo já tem de ser gerido pela [política de proteção de aplicações do Intune]( ../app-protection-policy.md).

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. No painel **Aplicações do cliente** da lista Gestão, selecione **Políticas de configuração de aplicações**.
4. No painel **Políticas de configuração de aplicações**, escolha **Adicionar**.
5. No painel **Adicionar política de configuração**, introduza um **Nome** e uma **Descrição** opcional para as definições de configuração da aplicação.
6. Para o tipo de **Inscrição de dispositivos**, selecione **Aplicações geridas**.
7. Selecione **Selecionar a aplicação necessária** e, em seguida, no painel **Aplicações de destino**, selecione o **Managed Browser** e/ou o **Microsoft Edge** para iOS, Android ou para ambos.
8. Selecione **OK** para regressar ao painel **Política de configuração da aplicação**.
9. Selecione **Definições de configuração**. No painel **Configuração**, define os pares de chave e valor para fornecer as configurações para o Managed Browser. Utilize as secções mais adiante neste artigo para saber mais sobre os diferentes pares de chave e valor que pode definir.
10. Quando tiver terminado, escolha **OK**.
11. No painel **Adicionar política de configuração**, selecione **Adicionar**.
12. A nova configuração é criada e apresentada no painel **Configuração de aplicações**.


## <a name="assign-the-configuration-settings-you-created"></a>Atribuir as definições de configuração que criou

Atribua as definições a grupos de utilizadores do Azure AD. Se esse utilizador tiver a aplicação de browser protegido de destino instalada, a aplicação será gerida pelas definições que especificou.

1. No painel **Aplicações do cliente** do dashboard de gestão de aplicações móveis do Intune, selecione **Políticas de configuração de aplicações**.
2. Na lista de configurações de aplicações, selecione aquela que pretende atribuir.
3. No painel seguinte, selecione **Atribuições**.
4. No painel **Atribuições**, selecione o grupo do Azure AD ao qual pretende atribuir a configuração da aplicação e, em seguida, selecione **OK**.

## <a name="how-to-set-microsoft-edge-as-the-protected-browser-for-your-organization"></a>Como definir o Microsoft Edge como o navegador protegido para sua organização

Essa configuração permite que você configure se os usuários serão direcionados para o Microsoft Edge ou para o Intune Managed Browser, supondo que ambos os navegadores sejam direcionados à política de proteção do aplicativo. **Essa configuração de política de configuração de aplicativo deve ser destinada aos aplicativos gerenciados do Intune do qual o link da Web é aberto.** 

Se essa configuração for definida como "true":

- Os usuários serão direcionados para o Microsoft Edge ao abrir links de aplicativos gerenciados do Intune direcionados a essa configuração. 
- Se eles ainda não tiverem o aplicativo, eles serão solicitados a baixar o Microsoft Edge da loja, independentemente de terem o Intune Managed Browser baixado.

Se essa configuração for definida como "false":

- Se os usuários tiverem o Managed Browser e o Microsoft Edge baixados **, o Managed browser** será iniciado. 
- Se **os usuários tiverem o** Managed browser **ou** o Microsoft Edge baixado, esse aplicativo de navegador será iniciado. 
- Se os usuários não tiverem o aplicativo de navegador baixado, eles serão solicitados a baixar o Managed Browser.

Usando o procedimento acima para criar uma configuração de aplicativo do Microsoft Edge. Forneça o seguinte par de chave e valor ao selecionar os **parâmetros de configuração** na folha **configuração** (etapa 9):

| Chave                              |  Valor   |
|----------------------------------|----------|
| **com. Microsoft. Intune. useEdge** | **verdadeiro** |

> [!NOTE]
> Na política de proteção de aplicativo que gerencia o Microsoft Edge e os aplicativos associados especificados na configuração do aplicativo, verifique se as seguintes configurações de política de proteção de dados estão definidas:
> - Enviar dados da organização para outros aplicativos: **aplicativos gerenciados pela política**
> - Compartilhar conteúdo da Web com navegadores gerenciados por política: **exigir**

## <a name="how-to-configure-application-proxy-settings-for-protected-browsers"></a>Como configurar as definições de Proxy de Aplicações para browsers protegidos

O Microsoft Edge, o Intune Managed Browser e o [Proxy de Aplicações do Azure AD]( https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started) podem ser utilizados em conjunto para suportar os seguintes cenários para utilizadores de dispositivos iOS e Android:

- Um utilizador transfere e inicia sessão na aplicação Microsoft Outlook. As políticas de proteção de aplicações do Intune são aplicadas automaticamente. Encriptam os dados guardados e impedem que o utilizador transfira ficheiros empresariais para aplicações ou localizações não geridas no dispositivo. Quando o utilizador clica numa ligação para um site da intranet no Outlook, pode especificar se a ligação é aberta na aplicação de browser protegido, em vez de noutro browser. O browser protegido reconhece que este site da intranet foi exposto ao utilizador através do Proxy de Aplicações. O usuário é encaminhado automaticamente pelo proxy de aplicativo, para autenticar com qualquer autenticação multifator aplicável e acesso condicional antes de acessar o site da intranet. Este site, que anteriormente não podia ser encontrado por utilizadores remotos, está agora acessível e a ligação no Outlook funciona como esperado.
- Um utilizador remoto abre a aplicação de browser protegido e navega para um site da intranet através do URL interno. O browser protegido reconhece que este site da intranet foi exposto ao utilizador através do Proxy de Aplicações. O usuário é encaminhado automaticamente pelo proxy de aplicativo, para autenticar com qualquer autenticação multifator aplicável e acesso condicional antes de acessar o site da intranet. Este site, que anteriormente os utilizadores remotos não podiam encontrar, está agora acessível.

### <a name="before-you-start"></a>Antes de começar

- Configure as suas aplicações internas através do Proxy de Aplicações do Azure AD.
  - Para configurar o Proxy de Aplicações e publicar aplicações, veja a [documentação de configuração](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy). 
  - [Os usuários devem ser atribuídos](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy-add-on-premises-application#add-a-user-for-testing) ao aplicativo empresarial para o qual o redirecionamento deve ocorrer. Isso deve ser feito mesmo se o aplicativo estiver definido como modo de passagem para pré-autenticação e se o requisito de atribuição de usuário tiver sido desativado nas configurações de proxy de aplicativo.
- Tem de utilizar a versão mínima da aplicação Managed Browser 1.2.0.
- Os utilizadores da aplicação Managed Browser ou Microsoft Edge têm uma [política de proteção de aplicações do Intune](app-protection-policy.md) atribuída à aplicação.

    > [!NOTE]
    > Os dados atualizados de redirecionamento do Proxy de Aplicações podem demorar até 24 horas a entrar em vigor no Managed Browser e no Microsoft Edge.


#### <a name="step-1-enable-automatic-redirection-to-a-protected-browser-from-outlook"></a>Passo 1: ativar o redirecionamento automático para um browser protegido a partir do Outlook
O Outlook tem de estar configurado com uma política de proteção de aplicações que ative a definição **Restringir o conteúdo Web a apresentar no Managed Browser**.

#### <a name="step-2-assign-an-app-configuration-policy-assigned-for-the-protected-browser"></a>Etapa 2: atribuir uma política de configuração de aplicativo atribuída para o navegador protegido
Este procedimento configura a aplicação Managed Browser ou Microsoft Edge para utilizar o redirecionamento do proxy de aplicações. 

Abra a guia **borda** nas definições de configuração da política e selecione **habilitar** para o valor de redirecionamento de proxy de aplicativo. Habilitar essa configuração permitirá que os usuários acessem links corporativos e aplicativos Web locais publicados por meio do proxy de aplicativo do Azure.

Para obter mais informações sobre como o Managed Browser, o Microsoft Edge e o Proxy de Aplicações do Azure AD podem ser utilizados em conjunto para um acesso fácil (e seguro) a aplicações Web no local, veja a mensagem de blogue do Enterprise Mobility + Security [Better together: Intune and Azure Active Directory team up to improve user access](https://cloudblogs.microsoft.com/enterprisemobility/2017/07/06/better-together-intune-and-azure-active-directory-team-up-to-improve-user-access) (Melhor em conjunto: o Intune e o Azure Active Directory juntam-se para melhorar o acesso do utilizador).

## <a name="how-to-configure-the-homepage-for-a-protected-browser"></a>Como configurar a home page de um browser protegido

Esta definição permite-lhe configurar a home page que os utilizadores veem ao iniciar um browser protegido ou ao criar um novo separador. 
- Esta definição irá mostrar a página Web no Managed Browser.  O Microsoft Edge irá apresentar um atalho para a home page.
- O ícone do atalho para a home page é apresentado por baixo do controlo de pesquisa.  Não pode ser editado nem eliminado.
- O atalho para a home page irá apresentar o nome da sua organização para poder distingui-lo.  Será sempre apresentado como o primeiro ícone.

Quando utilizar o procedimento para criar uma configuração da aplicação Managed Browser ou Microsoft Edge, forneça o seguinte par de chave e valor:

|                                Chave                                |                                                           Valor                                                            |
|-------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------|
| <strong>com.microsoft.intune.mam.managedbrowser.homepage</strong> | Especifique um URL válido. Os URLs incorretos são bloqueados como medida de segurança.<br>Exemplo: `https://www.bing.com` |

## <a name="how-to-configure-bookmarks-for-a-protected-browser"></a>Como configurar os marcadores de um browser protegido

Esta definição permite-lhe configurar um conjunto de marcadores disponível para os utilizadores do Microsoft Edge ou do Managed Browser.

- Estes marcadores não podem ser eliminados ou modificados pelos utilizadores
- Estes marcadores são apresentados no início da lista. Todos os marcadores criados pelos utilizadores serão apresentados abaixo destes.
- Se já ativou o redirecionamento do Proxy de Aplicações, pode adicionar aplicações Web do Proxy de Aplicações através do respetivo URL interno ou externo.

Quando utilizar o procedimento para criar uma configuração da aplicação Managed Browser ou Microsoft Edge, forneça o seguinte par de chave e valor:

|                                Chave                                 |                                                                                                                                                                                                                                                         Valor                                                                                                                                                                                                                                                          |
|--------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <strong>com.microsoft.intune.mam.managedbrowser.bookmarks</strong> | O valor desta configuração é uma lista de marcadores. Cada marcador é constituído pelo título e URL do marcador. Separe o título e o URL com o caráter <strong>&#124;</strong>.<br><br>Exemplo:<br> <code>Microsoft Bing&#124;https://www.bing.com</code><br><br>Para configurar múltiplos marcadores, separe cada par com o caráter duplo <strong>&#124;&#124;</strong><br><br>Exemplo:<br> <code>Bing&#124;https://www.bing.com&#124;&#124;Contoso&#124;https://www.contoso.com</code> |

## <a name="how-to-specify-allowed-and-blocked-urls-for-a-protected-browser"></a>Como especificar URLs permitidos e bloqueados para um browser protegido

Quando utilizar o procedimento para criar uma configuração da aplicação Managed Browser ou Microsoft Edge, forneça o seguinte par de chave e valor:

|Chave|Valor|
|-|-|
|Escolha entre:<br><ul><li>Especificar URLs permitidos (apenas estes URLs são permitidos; não pode aceder a mais nenhum site):<br> **com.microsoft.intune.mam.managedbrowser.AllowListURLs**<br><br></li><li>Especificar URLs bloqueados (é possível aceder a todos os outros sites):<br>**com.microsoft.intune.mam.managedbrowser.BlockListURLs**</li></ul>|O valor correspondente da chave é uma lista de URLs. Introduza todos os URLs que pretende permitir ou bloquear como um único valor, separado por um caráter de pipe **&#124;** .<br><br>Exemplos:<br><br><code>URL1&#124;URL2&#124;URL3</code><br><code>http://*.contoso.com/*&#124;https://*.bing.com/*&#124;https://expenses.contoso.com</code>|

>[!IMPORTANT]
>Não especifique ambas as chaves. Se as duas chaves forem direcionadas para o mesmo utilizador, a chave de permissão é utilizada, uma vez que é a opção mais restritiva.
>Além disso, confirme que não bloqueia páginas importantes tais como os sites da empresa.

### <a name="url-format-for-allowed-and-blocked-urls"></a>Formato do URL para URLs permitidos e bloqueados
Utilize as informações seguinte para saber mais sobre os formatos permitidos e os carateres universais que pode utilizar ao especificar os URLs na lista de permissões e bloqueios:

- Pode utilizar o símbolo de caráter universal ( **&#42;** ) de acordo com as regras na lista de padrões permitidos seguinte:

- Certifique-se de que adiciona o prefixo **http** ou **https** a todos os URLs quando os introduzir na lista.

- Pode especificar os números da porta no endereço. Se não especificar um número da porta, os valores utilizados são:

  - Porta 80 para http

  - Porta 443 para https

  Não é suportado utilizar carateres universais para o número de porta. Por exemplo, `http://www.contoso.com:;` e `http://www.contoso.com: /;` não são suportados.

- Utilize a tabela seguinte para saber mais sobre os padrões permitidos que pode utilizar ao especificar URLs:

|                  URL                  |                     Details                      |                                                Correspondências                                                |                                Não corresponde                                 |
|---------------------------------------|--------------------------------------------------|-------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------|
|        `http://www.contoso.com`         |              Corresponde a uma única página               |                                            `www.contoso.com`                                            |  `host.contoso.com`<br /><br />`www.contoso.com/images`<br /><br />`contoso.com`/   |
|          `http://contoso.com`           |              Corresponde a uma única página               |                                             `contoso.com/`                                              | `host.contoso.com`<br /><br />`www.contoso.com/images`<br /><br />`www.contoso.com` |
|    `http://www.contoso.com/&#42;`     | Corresponde a todos os URLs que começam com `www.contoso.com` |      `www.contoso.com`<br /><br />`www.contoso.com/images`<br /><br />`www.contoso.com/videos/tvshows`      |              `host.contoso.com`<br /><br />`host.contoso.com/images`              |
|    `http://*.contoso.com/*`     |     Corresponde a todos os subdomínios em contoso.com     | `developer.contoso.com/resources`<br /><br />`news.contoso.com/images`<br /><br />`news.contoso.com/videos` |                               `contoso.host.com`                                |
|     `http://www.contoso.com/images`     |             Corresponde a uma única pasta              |                                        `www.contoso.com/images`                                         |                          `www.contoso.com/images/dogs`                          |
|       `http://www.contoso.com:80`       |  Corresponde a uma única página, ao utilizar um número de porta   |                                       `http://www.contoso.com:80`                                       |                                                                               |
|        `https://www.contoso.com`        |          Corresponde a uma única página segura           |                                        `https://www.contoso.com`                                        |                            `http://www.contoso.com`                             |
| `http://www.contoso.com/images/&#42;` |    Corresponde a uma única pasta e a todas as subpastas    |                  `www.contoso.com/images/dogs`<br /><br />`www.contoso.com/images/cats`                   |                            `www.contoso.com/videos`                             |

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
  
## <a name="soft-transitions-from-work-to-personal-accounts"></a>Transições suaves do trabalho para contas pessoais

A base da experiência do Microsoft Edge Mobile Enterprise é o modelo de duas identidades, o que significa que o Microsoft Edge dá suporte a identidades de trabalho e pessoais. Assim como acontece com os aplicativos do Office 365 e do Outlook, esse modelo de identidade dupla permite que os usuários finais usem o Microsoft Edge para todas as necessidades de navegação e se movimentem facilmente entre as duas experiências com base nas políticas de conteúdo definidas pelo administrador. A navegação no contexto pessoal não é afetada e as informações corporativas são mantidas completamente contidas no contexto de trabalho no Microsoft Edge. 

Um dos benefícios desse modelo é que quando os usuários tentam abrir um link (como um artigo de jornal, etc.) para um site que não é permitido pela sua organização, eles são capazes de fazer isso em seu contexto pessoal, que é mantido totalmente separado do seu contexto de trabalho. Essas transições suaves do são habilitadas por padrão. 

Quando utilizar o procedimento para criar uma configuração da aplicação Managed Browser ou Microsoft Edge, forneça o seguinte par de chave e valor:

| Chave                                                                | Valor                                                 |
|--------------------------------------------------------------------|-------------------------------------------------------|
| **com. Microsoft. Intune. Mam. managedbrowser. AllowTransitionOnBlock** | **False** bloqueia a ocorrência dessas transições suaves |

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

Para obter uma lista das definições armazenados nos registos das aplicações, veja [Review app protection logs in the Managed Browser (Rever os registos de proteção das aplicações no Managed Browser)](app-protection-policy-settings-log.md).

## <a name="security-and-privacy-for-the-managed-browser"></a>Segurança e privacidade do Managed Browser

- O Managed Browser não utiliza as definições que os utilizadores criam para o browser incorporado nos seus dispositivos. O Managed Browser não consegue aceder a estas definições.

- Se configurar a opção **Exigir PIN simples para o acesso** ou **Exigir credenciais de empresa para o acesso** numa política de proteção de aplicações associada ao Managed Browser e um utilizador selecionar a ligação de ajuda na página de autenticação, este pode procurar sites na Internet independentemente de terem sido adicionados a uma lista de bloqueios na política.

- O Managed Browser só pode bloquear o acesso a sites quando estes são acedidos diretamente. Não bloqueia o acesso quando são utilizados serviços intermédios (como um serviço de tradução) para aceder ao site.

- Para permitir a autenticação e aceder à documentação do Intune, **&#42;.microsoft.com** está excluído das definições da lista de permissões ou de bloqueios. É sempre permitido.

### <a name="turn-off-usage-data"></a>Desativar dados de utilização
A Microsoft recolhe automaticamente dados anónimos sobre o desempenho e a utilização do Managed Browser para melhorar os produtos e serviços Microsoft. Os utilizadores podem desativar a recolha de dados com a definição **Dados de Utilização** nos respetivos dispositivos. OS utilizadores não têm controlo sobre a recolha destes dados.

- Em dispositivos iOS, os sites que os utilizadores visitam que têm um certificado expirado ou não fidedigno não podem ser abertos.

## <a name="next-steps"></a>Próximos passos

- [O que são as políticas de proteção de aplicações?](app-protection-policy.md) 
