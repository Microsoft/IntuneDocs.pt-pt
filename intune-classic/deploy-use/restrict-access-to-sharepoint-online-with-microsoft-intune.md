---
title: Proteger o SharePoint Online
description: Proteger e controlar o acesso ao e-mail da empresa no SharePoint Online com o acesso condicional.
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 01/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b088e5a0-fd4a-4fe7-aa49-cb9c8cfb1585
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: e22686964df7415ece75361a645103006af43c51
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/01/2017
---
# <a name="protect-access-to-sharepoint-online-with-microsoft-intune"></a>Proteger o acesso ao SharePoint Online com o Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Utilize o acesso condicional do Microsoft Intune para controlar o acesso aos ficheiros que estão localizados no SharePoint Online.
O acesso condicional tem dois componentes:
- Uma política de conformidade de dispositivos que o dispositivo tem de cumprir para ser considerado compatível.
- Uma política de acesso condicional onde especifica as condições que o dispositivo tem de cumprir para poder aceder ao serviço.
Para saber mais sobre como funciona o acesso condicional, leia o tópico [Proteger o acesso ao e-mail, ao Office 365 e a outros serviços](restrict-access-to-email-and-o365-services-with-microsoft-intune.md).

Pode implementar as políticas de conformidade e de acesso condicional aos utilizadores. Qualquer dispositivo que o utilizador utilize para aceder aos serviços é analisado relativamente à conformidade com as políticas.

Quando um utilizador se tentar ligar a um ficheiro através de uma aplicação suportada, como o OneDrive, no respetivo dispositivo, ocorre a seguinte avaliação:

![Diagrama que mostra os pontos de decisão para determinar se um dispositivo tem permissão de acesso ao SharePoint ou está bloqueado](../media/ConditionalAccess8-6.png)


**Antes de** configurar uma política de acesso condicional para o Skype para o SharePoint Online, tem de:
- Ter uma **subscrição do SharePoint Online** e os utilizadores têm de estar licenciados para o SharePoint Online.
- Ter uma subscrição do **Enterprise Mobility + Security (EMS)** ou do **Azure Active Directory (Azure AD) Premium**  e os utilizadores têm de ter uma licença do EMS ou do Azure AD. Para saber mais detalhes, consulte a [página de preços do Enterprise Mobility](https://www.microsoft.com/cloud-platform/enterprise-mobility-pricing) ou a [página de preços do Azure Active Directory](https://azure.microsoft.com/pricing/details/active-directory/).


  Para ligar aos ficheiros obrigatórios, o dispositivo tem de estar:
-   **Inscrito** no Intune ou ser um PC associado a um domínio.

-   **Registado** no Azure Active Directory (esse registo ocorre automaticamente quando o dispositivo é inscrito no Intune).


-   Ser **compatível** com todas políticas de conformidade do Intune implementadas.

O estado do dispositivo é armazenado no Azure Active Directory, o qual concede ou bloqueia o acesso aos ficheiros, com base nas condições que especificar.

Se não for cumprida uma condição, o utilizador vê uma das duas mensagens seguintes quando iniciar sessão:

-   Se o dispositivo não estiver inscrito no Intune ou não estiver registado no Azure Active Directory, será apresentada uma mensagem com instruções sobre como instalar a aplicação Portal da Empresa e inscrevê-la.

-   Se o dispositivo não estiver conforme, será apresentada uma mensagem que direciona o utilizador para o site do Portal da Empresa do Intune, onde poderá encontrar informações sobre o problema e como resolvê-lo.

**O acesso condicional não se aplica à partilha externa**. Para saber como impedir a partilha externa no seu inquilino ou numa coleção de sites, veja [Gerir a partilha externa para o seu ambiente do SharePoint Online](https://support.office.com/article/Manage-external-sharing-for-your-SharePoint-Online-environment-C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85).

>[!NOTE]
>Se ativar o acesso condicional para o SharePoint Online, recomendamos que desative o domínio na lista, conforme descrito no tópico [Remove-SPOTenantSyncClientRestriction](https://technet.microsoft.com/library/dn917451.aspx).  

## <a name="support-for-mobile-devices"></a>Suporte para dispositivos móveis
As seguintes versões são suportadas:
- iOS 8.0 e posterior
- Android 4.0 e posterior, Samsung Knox Standard 4.0 ou posterior
- Windows Phone 8.1 e posterior

Pode proteger o acesso ao SharePoint Online quando os dispositivos **iOS** e **Android** acedem a partir de um browser. O acesso só é permitido aos browsers suportados em dispositivos compatíveis:
* Safari (iOS)
* Chrome (Android)
* Browser Gerido do Intune (iOS e Android 5.0 e posteriores)

**Os browsers não suportados são bloqueados**.

## <a name="support-for-pcs"></a>Suporte de PCs
As seguintes versões são suportadas:
- Windows 8.1 e posterior (quando os PCs estão inscritos com o Intune)
- Windows 7.0, Windows 8.1 ou Windows 10 (quando os PCs estão associado a um domínio),
> [!NOTE]
>Para utilizar o acesso condicional em PCs com o Windows 10, tem de atualizar esses mesmos PCs para a Atualização de Aniversário do Windows 10.

  - Deve configurar os PCs associados a um domínio para serem [registados automaticamente](https://azure.microsoft.com/documentation/articles/active-directory-conditional-access-automatic-device-registration/) no Azure Active Directory. O serviço de Registos de Dispositivos do Azure AD será automaticamente ativado para os clientes do Intune e do Office 365. Os clientes que já implementaram o serviço de Registos de Dispositivos do ADFS não verão dispositivos registados no Active Directory no local.

  - Se a política estiver definida para exigir a associação a um domínio e o PC não estiver associado a um domínio, é apresentada uma mensagem para contactar o administrador de TI.

  - Se a política estiver definida para exigir a associação a um domínio ou estar em conformidade, e o PC não cumprir nenhum dos requisitos, é apresentada uma mensagem com instruções sobre como instalar a aplicação Portal da Empresa e inscrevê-lo.
  >[!NOTE]
  >O acesso condicional não é suportado em PCs que estão a executar o cliente de computador do Intune.

A [autenticação moderna do Office 365 tem de estar ativada](https://support.office.com/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a) e ter todas as atualizações mais recentes do Office.

A autenticação moderna inclui o início de sessão baseado na Active Directory Authentication Library (ADAL) para clientes do Office 2013 Windows e permite uma maior segurança como **autenticação multifator** e **autenticação baseada em certificado**.


## <a name="configure-conditional-access-for-sharepoint-online"></a>Configurar o acesso condicional para o SharePoint Online

### <a name="step-1-configure-active-directory-security-groups"></a>Passo 1: configurar grupos de segurança do Active Directory
Antes de começar, configure grupos de segurança do Azure Active Directory para a política de acesso condicional. Pode configurar estes grupos no **centro de administração do Office 365**ou no **portal de contas do Intune**. Pode utilizar estes grupos para adicionar ou excluir os utilizadores da política. Quando um utilizador é direcionado por uma política, cada dispositivo que utiliza tem de estar em conformidade para poder aceder aos recursos.

Pode especificar dois tipos de grupos numa política do SharePoint Online:

-   **Grupos visados**: contém os grupos de utilizadores aos quais se aplica a política.

-   **Grupos excluídos**: contém os grupos de utilizadores excluídos da política.

Se um utilizador estiver em ambos os grupos, significa que está excluído da política.

### <a name="step-2-configure-and-deploy-a-compliance-policy"></a>Passo 2: configurar e implementar uma política de conformidade
Se ainda não o fez, crie uma política de conformidade e implemente-a para os utilizadores visados pela política do SharePoint Online.

> [!NOTE]
> Enquanto as políticas de conformidade são implementadas nos grupos do Intune, as políticas de acesso condicional são direcionadas para os grupos de segurança do Azure Active Directory.

Para obter detalhes sobre como configurar a política de conformidade, veja [Criar uma política de conformidade](create-a-device-compliance-policy-in-microsoft-intune.md).

> [!IMPORTANT]
> Se não tiver implementado uma política de conformidade, os dispositivos são tratados como conformes.

Quando estiver pronto, avance para o **Passo 3**.

### <a name="step-3-configure-the-sharepoint-online-policy"></a>Passo 3: configurar a política do SharePoint Online
Em seguida, configure a política para exigir que apenas os dispositivos geridos e conformes podem aceder ao SharePoint Online. Esta política é armazenada no Azure Active Directory.

#### <a name="bkmk_spopolicy"></a>

>[!NOTE]
> Também pode criar uma política de acesso condicional para dispositivos Intune na consola de gestão do Azure AD (a política é referida como **política de acesso condicional baseada no dispositivo** no Azure AD). Além disso, pode criar outras políticas de acesso condicional, como a autenticação multifator. Também pode definir políticas de acesso condicional para aplicações empresariais de terceiros suportadas pelo Azure AD, como a Salesforce e a Box. Para obter mais detalhes, consulte [Como definir a política de acesso condicional com base no dispositivo do Azure Active Directory para controlar o acesso a aplicações ligadas do Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-conditional-access-policy-connected-applications/).


1.  Na [consola de administração do Microsoft Intune](https://manage.microsoft.com), clique em **Política** > **Acesso Condicional** > **Política do SharePoint Online**.
![Captura de ecrã da página Política do SharePoint Online](../media/mdm-ca-spo-policy-configuration.png)

2.  Selecione **Ativar política de acesso condicional do SharePoint Online**.

3.  Em **Acesso da aplicação**, pode optar por aplicar a política de acesso condicional a:

    -   **Todas as plataformas**

        Esta opção requer que todos os dispositivos que servem para aceder ao **SharePoint Online** estejam inscritos no Intune e estejam em conformidade com as políticas. Qualquer aplicação cliente que utilize a **autenticação moderna** está sujeita à política de acesso condicional. Se a plataforma não for atualmente suportada pelo Intune, o acesso ao **SharePoint Online** está bloqueado.

        Selecionar a opção **Todas as plataformas** significa que o Azure Active Directory aplica esta política a todos os pedidos de autenticação, independentemente da plataforma que é comunicada pela aplicação de cliente. Todas as plataformas terão de estar inscritas e compatíveis, exceto:
        *   Os dispositivos Windows terão de ser inscritos e estar em conformidade, o domínio deve estar associado ao Active Directory no local, ou ambos.
        * Plataformas não suportadas, como Mac. No entanto, as aplicações que utilizam autenticação moderna proveniente destas plataformas continuarão a ser bloqueadas.

    -   **Plataformas específicas**

         A política de acesso condicional aplica-se a todas as aplicações cliente que utilizem a autenticação moderna nas plataformas que especificar.

     Para PCs Windows, o PC tem de estar associado a um domínio ou inscrito no Intune e estar em conformidade. Pode definir os seguintes requisitos:

     -   **Os dispositivos têm de estar associados a um domínio ou em conformidade.** Escolha esta opção para exigir que os PCs estejam associados a um domínio ou em conformidade com as políticas que estão definidas no Intune. Se um PC não cumprir nenhum destes requisitos, será pedido ao utilizador que inscreva o dispositivo no Intune.

     -   **Os dispositivos têm de estar em conformidade.** Escolha esta opção para exigir que os PCs sejam inscritos no Intune e estejam em conformidade. Se um PC não estiver inscrito, será apresentada uma mensagem com instruções sobre como inscrevê-lo.

4.   Em **Acesso pelo Browser** ao SharePoint Online e OneDrive para Empresas, pode optar por permitir acesso ao Exchange Online apenas através de browsers suportados: Safari (iOS) e o Chrome (Android). O acesso a partir de outros browsers é bloqueado. As restrições de plataforma que selecionou para o acesso pela aplicação do OneDrive também se aplicam aqui.

  Nos dispositivos **Android**, os utilizadores têm de ativar o acesso ao browser. Para fazê-lo, o utilizador tem de ativar a opção **Ativar o Acesso ao Browser** no dispositivo inscrito da seguinte forma:
  1.    Abra a aplicação **Portal da Empresa**.
  2.    Aceda à página **Definições** a partir das reticências (…) ou do botão do menu de hardware.
  3.    Prima o botão **Ativar o Acesso ao Browser**.
  4.    No browser Chrome, termine a sessão no Office 365 e reinicie o Chrome.

  Nas plataformas **iOS** e **Android**, para identificar o dispositivo que serve para aceder ao serviço, o Azure Active Directory emite um certificado de Transport layer security (TLS) para o dispositivo. O dispositivo apresenta o certificado com uma linha de comandos para o utilizador para selecionar o certificado, conforme indicado nas seguintes capturas de ecrã. O utilizador tem de selecionar este certificado para poder utilizar o browser.

  **iOS**

  ![Captura de ecrã da linha de comandos do certificado num iPad](../media/mdm-browser-ca-ios-cert-prompt.png)

  **Android**

  ![Captura de ecrã da linha de comandos do certificado num dispositivo Android](../media/mdm-browser-ca-android-cert-prompt.png)
5.  Em **Grupos Visados**, escolha **Modificar** para selecionar os grupos de segurança do Azure Active Directory aos quais se aplica a política. Pode optar por direcionar esta opção a todos os utilizadores ou apenas a um grupo de utilizadores específico.

6.  Como opção, em **Grupos Excluídos**, selecione **Modificar** para selecionar os grupos de segurança do Azure Active Directory que estão excluídos desta política.

7.  Quando tiver terminado, escolha **Guardar**.

Não tem de implementar a política de acesso condicional, pois esta entra em vigor imediatamente.

### <a name="step-4-monitor-the-compliance-and-conditional-access-policies"></a>Passo 4: Monitorizar a conformidade e as políticas de acesso condicional
Na área de trabalho **Grupos**, pode ver o estado dos seus dispositivos.

Selecione qualquer grupo de dispositivos móveis. Em seguida, no separador **Dispositivos**, escolha um dos seguintes **Filtros**:

-   **Dispositivos não registados com o AAD**. Estes dispositivos são bloqueados no SharePoint Online.

-   **Dispositivos que não são compatíveis**. Estes dispositivos são bloqueados no SharePoint Online.

-   **Dispositivos registados com o AAD e que são compatíveis**. Estes dispositivos podem aceder ao SharePoint Online.

### <a name="see-also"></a>Consulte também
[Proteger o acesso ao e-mail e aos serviços do O365 com o Microsoft Intune](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)
