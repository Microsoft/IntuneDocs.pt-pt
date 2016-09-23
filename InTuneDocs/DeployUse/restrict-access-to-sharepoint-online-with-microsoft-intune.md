---
title: Restringir o acesso ao SharePoint Online | Microsoft Intune
description: Proteja e controle o acesso ao e-mail da empresa no SharePoint Online com o acesso condicional.
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 07/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b088e5a0-fd4a-4fe7-aa49-cb9c8cfb1585
ms.reviewer: chrisgre
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 4f98937d7adfc0c1584625303da3350785af8169
ms.openlocfilehash: 84c9d355fde49fd18899a43ed0def0c801694291


---

# Restringir o acesso ao SharePoint Online com o Microsoft Intune
Utilize o acesso condicional do [!INCLUDE[wit_firstref](../includes/wit_firstref_md.md)] para controlar o acesso a ficheiros localizados no SharePoint Online.
O acesso condicional tem dois componentes:
- A política de conformidade de dispositivos que o dispositivo tem de cumprir para ser considerado conforme.
- A política de acesso condicional onde especifica as condições que o dispositivo tem de cumprir para poder aceder ao serviço.
Para saber mais sobre como funciona o acesso condicional, leia o tópico [Restringir o acesso ao e-mail, O365 e a outros serviços](restrict-access-to-email-and-o365-services-with-microsoft-intune.md).

As políticas de conformidade e de acesso condicional são implementadas no utilizador. Qualquer dispositivo que o utilizador utilize para aceder aos serviços é analisado relativamente à conformidade com as políticas.

Quando um utilizador se tentar ligar a um ficheiro através de uma aplicação suportada, como o OneDrive, no respetivo dispositivo, ocorre a seguinte avaliação:

![Diagrama que mostra os pontos de decisão para determinar se um dispositivo tem permissão de acesso ao SharePoint ou está bloqueado ](../media/ConditionalAccess8-6.png)

>[!IMPORTANT]
>O acesso condicional para PCs e dispositivos Windows 10 Mobile com aplicações que utilizam a autenticação moderna não está atualmente disponível para todos os clientes do Intune. Se já estiver a utilizar estas funcionalidades, não é necessário efetuar qualquer ação. Pode continuar a utilizá-las.

>Se não tiver criado políticas de acesso condicional para PCs ou Windows 10 Mobile para aplicações que utilizam autenticação moderna e pretender fazê-lo, inscreva-se na pré-visualização pública do Azure Active Directory que inclui o acesso condicional com base no dispositivo para dispositivos geridos pelo Intune ou PCs do Windows associados a um domínio. Leia [esta mensagem do blogue](https://blogs.technet.microsoft.com/enterprisemobility/2016/08/10/azuread-conditional-access-policies-for-ios-android-and-windows-are-in-preview/) para saber mais.

**Antes de** configurar uma política de acesso condicional para o Skype para o SharePoint Online, tem de:
- Ter uma **subscrição do SharePoint Online** e os utilizadores têm de estar licenciados para o SharePoint Online.
- Ter uma subscrição do **Enterprise Mobility Suite** ou do **Azure Active Directory Premium**.

  Para ligar aos ficheiros necessários, o dispositivo tem de:
-   Estar **inscrito** no [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] ou ser um PC associado a um domínio.

-   **Registar o dispositivo** no Azure Active Directory (isto ocorre automaticamente quando o dispositivo é inscrito no [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]).


-   Ser compatível com todas as políticas de conformidade do [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] implementadas

O estado do dispositivo é armazenado no Azure Active Directory, o qual concede ou bloqueia o acesso aos ficheiros, com base nas condições que especificar.

Se não for cumprida uma condição, é apresentada ao utilizador uma das duas mensagens seguintes quando iniciar sessão:

-   Se o dispositivo não estiver inscrito no [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] ou não estiver registado no Azure Active Directory, é apresentada uma mensagem com instruções sobre como instalar a aplicação Portal da Empresa e inscrevê-lo.

-   Se o dispositivo não for conforme, é apresentada uma mensagem que direciona o utilizador para o site do Portal da Empresa do [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)], onde poderá encontrar informações sobre o problema e como resolvê-lo.

**O acesso condicional é aplicado em todos os sites SharePoint e a partilha externa é bloqueada**

>[!NOTE]
>Se ativar o acesso condicional para o SharePoint Online, recomendamos que desative o domínio na lista, conforme descrito no tópico [Remove-SPOTenantSyncClientRestriction](https://technet.microsoft.com/en-us/library/dn917451.aspx).  
## Suporte para dispositivos móveis
- iOS 8.0 e posterior
- Android 4.0 e posterior, Samsung Knox Standard 4.0 ou posterior
- Windows Phone 8.1 e posterior

Pode restringir o acesso ao SharePoint Online quando acede a partir de um browser a partir de dispositivos **iOS** e **Android**.  O acesso só é permitido aos browsers suportados em dispositivos compatíveis:
* Safari (iOS)
* Chrome (Android)
* Browser gerido (iOS e Android)

**Os browsers não suportados serão bloqueados**.

## Suporte de PCs
- Windows 8.1 e posterior (quando inscrito com o Intune)
- Windows 7.0 ou Windows 8.1 (quando associado a um domínio)

  - Os PCs associados a um domínio têm de estar configurados para serem [registados automaticamente](https://azure.microsoft.com/en-us/documentation/articles/active-directory-conditional-access-automatic-device-registration/) no Azure Active Directory.
O AAD DRS será automaticamente ativado para os clientes do Intune e do Office 365. Os clientes que já implementaram o Serviço de Registos de Dispositivos do ADFS não verão dispositivos registados no respetivo Active Directory no local.

  - Se a política estiver definida para exigir a associação a um domínio e o PC não estiver associado a um domínio, é apresentada uma mensagem para contactar o administrador de TI.

  - Se a política estiver definida para exigir a associação a um domínio ou estar em conformidade, e o PC não cumprir nenhum dos requisitos, é apresentada uma mensagem com instruções sobre como instalar a aplicação Portal da Empresa e inscrevê-lo.
  >[!NOTE]
  >O acesso condicional não é suportado em PCs com o cliente de computador do Intune.

-    A[autenticação moderna do Office 365 tem de estar ativada](https://support.office.com/en-US/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a) e ter todas as atualizações mais recentes do Office.

    A autenticação moderna inclui o início de sessão baseado na Active Directory Authentication Library (ADAL) para clientes do Office 2013 Windows e permite uma maior segurança como **multi-factor authentication** e **autenticação baseada em certificado**.


## Configurar o acesso condicional para o SharePoint Online

### Passo 1: configurar grupos de segurança do Active Directory
Antes de começar, configure grupos de segurança do Azure Active Directory para a política de acesso condicional. Pode configurar estes grupos no **centro de administração do Office 365**ou no **portal de contas do Intune**. Estes grupos serão utilizados para visar ou excluir utilizadores da política. Quando um utilizador é direcionado por uma política, cada dispositivo que utiliza tem de estar em conformidade para poder aceder aos recursos.

Pode especificar dois tipos de grupos numa política do SharePoint Online:

-   **Grupos visados** – contém os grupos de utilizadores aos quais a política será aplicada.

-   **Grupos excluídos** – contém os grupos de utilizadores excluídos da política.

Se um utilizador estiver em ambos os grupos, estará excluído da política.

### Passo 2: configurar e implementar uma política de conformidade
Se ainda não o fez, crie e implemente uma política de conformidade para os utilizadores que a política do SharePoint Online irá visar.

> [!NOTE]
> Enquanto as políticas de conformidade são implementadas nos grupos do [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)], as políticas de acesso condicional são direcionadas para os grupos de segurança do Azure Active Directory.

Para obter detalhes sobre como configurar a política de conformidade, consulte [Criar uma política de conformidade](create-a-device-compliance-policy-in-microsoft-intune.md).

> [!IMPORTANT]
> Se não tiver implementado uma política de conformidade, os dispositivos serão tratados como conformes.

Quando estiver pronto, avance para o **Passo 3**.

### Passo 3: configurar a política do SharePoint Online
Em seguida, configure a política para exigir que apenas os dispositivos geridos e conformes podem aceder ao SharePoint Online. Esta política será armazenada no Azure Active Directory.

#### <a name="bkmk_spopolicy"></a>

1.  Na [consola de administração do Microsoft Intune](https://manage.microsoft.com), clique em **Política** > **Acesso Condicional** > **Política do SharePoint Online**.
![Captura de ecrã da página Política do SharePoint Online](../media/mdm-ca-spo-policy-configuration.png)

2.  Selecione **Ativar política de acesso condicional do SharePoint Online**.

3.  Em **Acesso da aplicação**, pode optar por aplicar a política de acesso condicional a:

    -   **Todas as plataformas**

        Esta opção requer que todos os dispositivos utilizados para aceder ao **SharePoint Online** estejam inscritos no Intune e em conformidade com as políticas.  Qualquer aplicação cliente que utilize a **autenticação moderna** está sujeita à política de acesso condicional. Se a plataforma não for atualmente suportada pelo Intune, o acesso ao **SharePoint Online** está bloqueado.

        Selecionar a opção **Todas as plataformas** significa que o Azure Active Directory irá aplicar a esta política a todos os pedidos de autenticação, independentemente da plataforma comunicada pela aplicação de cliente.  Todas as plataformas terão de estar inscritas e compatíveis, exceto:
        *   Os dispositivos Windows terão de ser inscritos e estar em conformidade, o domínio deve estar associado ao Active Directory no local, ou ambos
        * Plataformas não suportadas, como Mac.  No entanto, as aplicações que utilizam autenticação moderna proveniente destas plataformas continuarão a ser bloqueadas.
        >[!TIP]
        >Poderá não ver esta opção se ainda não estiver a utilizar o acesso condicional para PCs.  Em alternativa, utilize as **Plataformas específicas**. O acesso condicional para PCs não está atualmente disponível para todos os clientes do Intune.   Pode encontrar mais informações sobre como obter acesso a esta funcionalidade [nesta mensagem do blogue](https://blogs.technet.microsoft.com/enterprisemobility/2016/08/10/azuread-conditional-access-policies-for-ios-android-and-windows-are-in-preview/).

    -   **Plataformas específicas**

         A política de acesso condicional aplica-se a todas as aplicações cliente que utilizem a autenticação moderna nas plataformas que especificar.

     Para PCs Windows, o PC tem de estar associado a um domínio ou inscrito no [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] e estar em conformidade. Pode definir os seguintes requisitos:

     -   **Os dispositivos têm de estar associados a um domínio ou em conformidade.** Escolha esta opção se pretender que os dispositivos estejam associados a um domínio ou em conformidade com as políticas definidas no [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]. Se o PC não cumprir nenhum destes requisitos, é pedido ao utilizador que inscreva o dispositivo no [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)].

     -   **Os dispositivos têm de estar associados a um domínio.** Escolha esta opção para exigir que os PCs estejam associados a um domínio para aceder ao Exchange Online. Se o PC não estiver associado a um domínio, o acesso ao e-mail é bloqueado e é pedido ao utilizador que contacte o administrador de TI.

     -   **Os dispositivos têm de estar em conformidade.** Escolha esta opção para exigir que os PCs sejam inscritos no [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] e em conformidade. Se o PC não estiver inscrito, será apresentada uma mensagem com instruções sobre como inscrevê-lo.

4.   Em **Acesso pelo Browser** ao SharePoint Online e OneDrive para Empresas, pode optar por permitir acesso ao Exchange Online apenas através de browsers suportados: Safari (iOS) e o Chrome (Android). O acesso a partir de outros browsers será bloqueado.  As restrições de plataforma que selecionou para o acesso pela aplicação do OneDrive também se aplicam aqui.

  Nos dispositivos **Android**, os utilizadores têm de ativar o acesso ao browser.  Para efetuar esta ação, o utilizador final tem de ativar a opção "Ativar o Acesso ao Browser" no dispositivo inscrito da seguinte forma:
  1.    Inicie a aplicação **Portal da Empresa**.
  2.    Aceda à página **Definições** a partir das reticências (…) ou do botão do menu de hardware.
  3.    Prima o botão **Ativar o Acesso ao Browser**.
  4.  No browser Chrome, termine a sessão no Office 365 e reinicie o Chrome.

  Nas plataformas **iOS e Android**, para identificar o dispositivo utilizado para aceder ao serviço, o Azure Active Directory irá emitir um certificado de Transport layer security (TLS) para o dispositivo.  O dispositivo apresenta o certificado com uma linha de comandos para o utilizador final para selecionar o certificado, conforme indicado nas capturas de ecrã abaixo. O utilizador final tem de selecionar este certificado antes de este poder continuar a utilizar o browser.

  **iOS**

  ![captura de ecrã da linha de comandos do certificado num ipad](../media/mdm-browser-ca-ios-cert-prompt.png)

  **Android**

  ![captura de ecrã da linha de comandos do certificado num dispositivo Android](../media/mdm-browser-ca-android-cert-prompt.png)
5.  Em **Grupos Visados**, escolha **Modificar** para selecionar os grupos de segurança do Azure Active Directory aos quais será aplicada a política. Pode optar por direcionar esta opção a todos os utilizadores ou apenas a grupos de utilizadores específicos.

6.  Como opção, em **Grupos Excluídos**, selecione **Modificar** para selecionar os grupos de segurança do Azure Active Directory que estão excluídos desta política.

6.  Quando tiver terminado, escolha **Guardar**.

Não tem de implementar a política de acesso condicional, pois esta entra em vigor imediatamente.

### Passo 4: Monitorizar a conformidade e as políticas de acesso condicional
Na área de trabalho **Grupos**, pode ver o estado dos seus dispositivos.

Selecione qualquer grupo de dispositivos móveis e, em seguida, no separador **Dispositivos** , selecione um dos seguintes **Filtros**:

-   **Dispositivos não registados no AAD** – estes dispositivos estão bloqueados no SharePoint Online.

-   **Dispositivos não conformes** – estes dispositivos estão bloqueados no SharePoint Online.

-   **Dispositivos registados no AAD e conformes** – estes dispositivos podem aceder ao SharePoint Online.

### Consulte também
[Restringir o acesso ao e-mail e aos serviços do Office 365 com o Microsoft Intune](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)



<!--HONumber=Sep16_HO2-->


