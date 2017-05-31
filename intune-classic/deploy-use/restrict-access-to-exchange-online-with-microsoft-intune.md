---
title: Proteger o e-mail no Exchange Online | Documentos da Microsoft
description: Proteja e controle o acesso ao e-mail da empresa no Exchange Online com o acesso condicional.
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 01/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 09c82f5d-531c-474d-add6-784c83f96d93
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 742a989744a11dbc1c9e17a25b70388e06dd5ae7
ms.contentlocale: pt-pt
ms.lasthandoff: 05/31/2017


---


# <a name="protect-email-access-to-exchange-online-and-new-exchange-online-dedicated-with-intune"></a>Proteger o acesso ao e-mail no Exchange Online e no novo Exchange Online Dedicado com o Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Com o Microsoft Intune, pode configurar o acesso condicional para o Exchange Online ou para o Exchange Online Dedicado. Para saber mais sobre como funciona o acesso condicional, leia o artigo [Proteger o acesso ao e-mail, ao Office 365 e a outros serviços](restrict-access-to-email-and-o365-services-with-microsoft-intune.md).

> [!NOTE]
>Se tiver um ambiente do Exchange Online Dedicado e precisar de saber se está na configuração nova ou legada, contacte o seu gestor de conta.

## <a name="before-you-begin"></a>Antes de começar

Para configurar o acesso condicional, tem de:

-   Ter uma **subscrição do Office 365 que inclua o Exchange Online (como o plano E3)** e os utilizadores têm de estar licenciados para o Exchange Online.

- Ter uma subscrição do **Enterprise Mobility + Security (EMS)** ou do **Azure Active Directory (Azure AD) Premium**  e os utilizadores têm de ter uma licença do EMS ou do Azure AD. Para saber mais detalhes, consulte a [página de preços do Enterprise Mobility](https://www.microsoft.com/cloud-platform/enterprise-mobility-pricing) ou a [página de preços do Azure Active Directory](https://azure.microsoft.com/pricing/details/active-directory/).

-  Pondere configurar o **Conector de serviços do Intune** opcional, que liga o Intune ao Exchange Online e o ajuda a gerir as informações dos dispositivos através da consola do Intune. Não tem de utilizar o conector para utilizar políticas de conformidade ou políticas de acesso condicional, mas é necessário executar relatórios que ajudam a avaliar o impacto do acesso condicional.
    -  Saiba mais sobre o [conector de serviços do Intune](intune-service-to-service-exchange-connector.md).

   > [!NOTE]
   > Não configure o conector de serviços do Intune se quiser utilizar o acesso condicional para o Exchange Online e para o Exchange no local.

### <a name="device-compliance-requirements"></a>Requisitos de conformidade do dispositivo

Quando configurar políticas de acesso condicional e direcioná-las para um utilizador, antes de um utilizador poder ligar ao respetivo e-mail, o **dispositivo** que utiliza tem de ser:

-   Um PC associado a um domínio ou **inscrito** no Intune.

-  **Registado no Azure Active Directory**. Esta situação ocorre automaticamente quando o dispositivo é inscrito no Intune. Além disso, o ID do Exchange ActiveSync do cliente tem de ser registado no Azure Active Directory.

  O serviço de Registos de Dispositivos do Azure Active Directory é ativado automaticamente para os clientes do Intune e do Office 365. Os clientes que já implementaram o serviço de Registos de Dispositivos do ADFS não verão dispositivos registados no Active Directory no local.

-   **Conforme** com todas as políticas de conformidade do Intune implementadas nesse dispositivo ou associado a um domínio no local.

### <a name="when-the-device-is-not-compliant"></a>Quando o dispositivo não é compatível

Se uma política de acesso condicional não for cumprida, o dispositivo será imediatamente colocado em quarentena e o utilizador receberá um e-mail onde verá uma das seguintes notificações de quarentena quando inicia sessão:

- Se o dispositivo não estiver inscrito no Intune ou se não estiver registado no Azure Active Directory, será apresentada uma mensagem com instruções sobre como instalar a aplicação Portal da Empresa, inscrever o dispositivo e ativar o e-mail. Este processo também associa o ID do Exchange ActiveSync do dispositivo ao registo no Azure Active Directory.

-   Se o dispositivo for avaliado como não conforme com as regras da política de conformidade, o utilizador será direcionado para o site do Portal da Empresa do Intune ou para a aplicação Portal da Empresa, onde poderá encontrar informações sobre o problema e como resolvê-lo.

### <a name="how-conditional-access-works-with-exchange-online"></a>Como o acesso condicional funciona com o Exchange Online

O seguinte diagrama ilustra o fluxo utilizado pelas políticas de acesso condicional para o Exchange Online.

![Diagrama que ilustra os pontos de decisão que determinam se o acesso ao dispositivo foi permitido ou bloqueado](../media/ConditionalAccess8-1.png)

## <a name="support-for-mobile-devices"></a>Suporte para dispositivos móveis
Pode proteger o acesso ao e-mail do Exchange Online a partir do **Outlook** e de outras **aplicações que utilizam autenticação moderna**. As seguintes versões são suportadas:

- Android 4.0 e posterior, Samsung Knox Standard 4.0 e posterior e Android for Work
- iOS 8.0 e posterior

A **autenticação moderna** proporciona um início de sessão baseado na ADAL (Active Directory Authentication Library) aos clientes do Microsoft Office.

-   A autenticação baseada na ADAL permite que os clientes do Office participem na autenticação baseada no browser (também conhecido como autenticação passiva). Para autenticar, o utilizador é direcionado para uma página Web de início de sessão.
-   Este novo método de início de sessão permite uma maior segurança, como a **autenticação multifator** e a **autenticação baseada em certificado**. Para obter informações mais detalhadas, veja [Como funciona a autenticação moderna](https://support.office.com/article/How-modern-authentication-works-for-Office-2013-and-Office-2016-client-apps-e4c45989-4b1a-462e-a81b-2a13191cf517). Pode configurar regras de afirmações do ADFS para bloquear protocolos de autenticação não moderna. São fornecidas instruções detalhadas no [Cenário 3: bloquear todo o acesso ao O365, exceto aplicações baseadas no browser](https://technet.microsoft.com/library/dn592182.aspx).

Pode proteger o acesso ao **Outlook Web Access (OWA)** no Exchange Online quando um utilizador aceder a partir de um browser em dispositivos **iOS** e **Android**. O acesso só é permitido aos browsers suportados em dispositivos compatíveis:

* Safari (iOS)
* Chrome (Android)
* Browser Gerido do Intune (iOS, Android 5.0 e posterior)

   > [!IMPORTANT]
   > **Os browsers não suportados são bloqueados**.

**A aplicação OWA para iOS e Android pode ser modificada de forma a não utilizar autenticação moderna e não é suportada. O acesso da aplicação OWA tem de ser bloqueado através de regras de afirmações do ADFS.**


Pode proteger o acesso ao e-mail do Exchange no **cliente de e-mail Exchange ActiveSync** incorporado nas seguintes plataformas:

- Android 4.0 e posterior, Samsung Knox Standard 4.0 e posterior

- iOS 8.0 e posterior

- Windows Phone 8.1 e posterior

## <a name="support-for-pcs"></a>Suporte de PCs

Pode configurar o acesso condicional para PCs que executem aplicações de ambiente de trabalho do Office para aceder ao **Exchange Online** e ao **SharePoint Online** para PCs que cumpram os requisitos seguintes:

-   O PC tem de executar o Windows 7.0, o Windows 8.1 ou o Windows 10.

  >[!NOTE]
  > Para utilizar o acesso condicional em PCs com o Windows 10, tem de atualizar esses mesmos PCs para a Atualização de Aniversário do Windows 10.

  O PC tem de estar associado a um domínio ou conforme com as regras da política de conformidade.

  Para ser considerado conforme, o PC tem de estar inscrito no Intune e em conformidade com as políticas.

  Para um PC associado a um domínio, tem de configurar o acesso condicional para [registar automaticamente o dispositivo](https://azure.microsoft.com/documentation/articles/active-directory-conditional-access-automatic-device-registration/) no Azure Active Directory.

  >[!NOTE]
    >O acesso condicional não é suportado em PCs que estão a executar o cliente de computador do Intune.

-   A [autenticação moderna do Office 365 tem de estar ativada](https://support.office.com/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a) e ter todas as atualizações mais recentes do Office.

    A autenticação moderna proporciona um início de sessão baseado na ADAL (Active Directory Authentication Library) aos clientes do Office 2013/Windows. Permite uma maior segurança, como a **autenticação multifator** e a **autenticação baseada em certificado**.

-   As regras de afirmações do ADFS são configuradas para bloquear protocolos de autenticação não moderna. São fornecidas instruções detalhadas no [Cenário 3: bloquear todo o acesso ao O365, exceto aplicações baseadas no browser](https://technet.microsoft.com/library/dn592182.aspx).

## <a name="configure-conditional-access"></a>Configurar o acesso condicional
### <a name="step-1-configure-and-deploy-a-compliance-policy"></a>Passo 1: Configurar e implementar uma política de conformidade
Certifique-se de que [cria](create-a-device-compliance-policy-in-microsoft-intune.md) e [implementa](deploy-and-monitor-a-device-compliance-policy-in-microsoft-intune.md) uma política de conformidade para os grupos de utilizadores que também irão receber a política de acesso condicional.


> [!IMPORTANT]
> Se não tiver implementado uma política de conformidade, os dispositivos são considerados conformes e têm permissão de acesso ao Exchange.

### <a name="step-2-evaluate-the-effect-of-the-conditional-access-policy"></a>Passo 2: Avaliar o efeito da política de acesso condicional
Pode utilizar os **Relatórios de Inventário de Dispositivos Móveis** para identificar os dispositivos que poderão ser impedidos de aceder ao Exchange após configurar a política de acesso condicional.

Para tal, configure uma ligação entre o Intune e o Exchange com o [Conector de serviços do Microsoft Intune](intune-service-to-service-exchange-connector.md).
1.  Navegue para **Relatórios** > **Relatórios de Inventário de Dispositivos Móveis**.
![Captura de ecrã da página do Relatório de Inventário de Dispositivos Móveis](../media/IntuneSA2bMobileDeviceInventoryReport.png)

2.  Nos parâmetros do relatório, selecione o grupo do Intune que pretende avaliar e, se necessário, as plataformas de dispositivos às quais será aplicada a política.
3.  Depois de selecionar os critérios que satisfazem as necessidades da sua organização, selecione **Ver Relatório**.
O Visualizador de Relatórios é aberto numa nova janela.
![Captura de ecrã de um Relatório de inventário de dispositivos móveis de exemplo](../media/IntuneSA2cViewReport.PNG)

Depois de executar o relatório, examine estas quatro colunas para determinar se um utilizador será bloqueado:

-   **Canal de Gestão**: indica se o dispositivo é gerido pelo Intune, pelo Exchange ActiveSync ou por ambos.

-   **Registado no AAD**: indica se o dispositivo está registado no Azure Active Directory (conhecido como Associação à Área de Trabalho).

-   **Conforme**: indica se o dispositivo está conforme com as políticas de conformidade implementadas.

-   **ID do Exchange ActiveSync**: é necessário que os dispositivos iOS e Android tenham o ID do Exchange ActiveSync associado ao registo do dispositivo no Azure Active Directory. Isto acontece quando o utilizador seleciona a ligação **Ativar E-mail** no e-mail de quarentena.

    > [!NOTE]
    > Os dispositivos Windows Phone apresentam sempre um valor nesta coluna.

Os dispositivos que fazem parte de um grupo visado são impedidos de aceder ao Exchange, exceto se os valores da coluna corresponderem aos listados na seguinte tabela:

--------------------------
|Canal de Gestão|Registado no AAD|Compatível|ID do Exchange ActiveSync|Ação resultante|
|----------------------|------------------|-------------|--------------------------|--------------------|
|**Gerido pelo Microsoft Intune e pelo Exchange ActiveSync**|Sim|Sim|É apresentado um valor|O acesso ao e-mail é permitido|
|Qualquer outro valor|Não|Não|Não é apresentado nenhum valor|O acesso ao e-mail é bloqueado|
----------------------
Pode exportar os conteúdos do relatório e utilizar a coluna **Endereço de E-mail** para informar os utilizadores de que serão bloqueados.

### <a name="step-3-configure-user-groups-for-the-conditional-access-policy"></a>Passo 3: Configurar grupos de utilizadores para a política de acesso condicional
As políticas de acesso condicional estão direcionadas para diferentes grupos de segurança de utilizadores do Azure Active Directory. Também pode excluir determinados grupos de utilizadores de uma política de acesso condicional. Quando um utilizador é visado por uma política, cada dispositivo que utiliza tem de estar em conformidade para poder aceder ao e-mail.

Pode configurar estes grupos no **centro de administração do Office 365**ou no **portal de contas do Intune**.

Pode especificar dois tipos de grupos em cada política:

-   **Grupos visados**: grupos de utilizadores aos quais é aplicada a política.

-   **Grupos excluídos**: grupos de utilizadores excluídos da política (opcional).

Se um utilizador estiver em ambos os grupos, significa que está excluído da política.

Apenas os grupos visados pela política de acesso condicional são avaliados.

### <a name="step-4-configure-the-conditional-access-policy"></a>Passo 4: Configurar a política de acesso condicional

>[!NOTE]
> Também pode criar uma política de acesso condicional na consola de gestão do Azure AD. A consola de gestão do Azure AD permite criar as políticas de acesso condicional a dispositivos do Intune (designadas como **políticas de acesso condicional com base no dispositivo** no Azure AD) além de outras políticas de acesso condicional, como a autenticação multifator.

>Também pode definir políticas de acesso condicional para aplicações empresariais de terceiros suportadas pelo Azure AD, como a Salesforce e a Box. Para obter mais detalhes, veja [Como definir a política de acesso condicional com base no dispositivo do Azure Active Directory para controlar o acesso a aplicações ligadas do Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-conditional-access-policy-connected-applications/).


1.  Na [consola de administração do Microsoft Intune](https://manage.microsoft.com), escolha **Policy** > **Conditional Access** > **Exchange Online Policy**.

2.  Na página **Política do Exchange Online**, selecione **Ativar política de acesso condicional no Exchange Online**.

    > [!NOTE]
    > Se não tiver implementado uma política de conformidade, os dispositivos serão tratados como conformes.
    >
    > Independentemente do estado de conformidade, todos os utilizadores visados pela política têm de inscrever os seus dispositivos no Intune.

3.  Em **Acesso da aplicação**, para as aplicações que utilizam autenticação moderna, tem duas formas de escolher quais as plataformas a que a política deve ser aplicada. As plataformas suportadas incluem Android, iOS, Windows e Windows Phone.

    -   **Todas as plataformas**

        Esta opção requer que todos os dispositivos utilizados para aceder ao **Exchange Online** estejam inscritos no Intune e em conformidade com as políticas. Qualquer aplicação cliente que utilize a **autenticação moderna** está sujeita à política de acesso condicional. Se a plataforma não for atualmente suportada pelo Intune, o acesso ao **Exchange Online** será bloqueado.

        Selecionar a opção **Todas as plataformas** significa que o Azure Active Directory aplica esta política a todos os pedidos de autenticação, independentemente da plataforma que é comunicada pela aplicação de cliente. Todas as plataformas têm de estar inscritas e conformes, exceto:
        *    Os dispositivos Windows terão de ser inscritos e estar em conformidade, o domínio deve estar associado ao Active Directory no local, ou ambos.
        * Plataformas não suportadas, como o Mac OS. No entanto, as aplicações que utilizam a autenticação moderna proveniente destas plataformas continuam a ser bloqueadas.

    -   **Plataformas específicas**

         A política de acesso condicional aplica-se a todas as aplicações cliente que utilizem a **autenticação moderna** nas plataformas de dispositivos que especificar.

4. Em **Outlook Web Access (OWA)**, pode optar por permitir acesso ao Exchange Online apenas através de browsers suportados: Safari (iOS) e o Chrome (Android). O acesso a partir de outros browsers é bloqueado. As restrições de plataforma que selecionou para o acesso pela aplicação do Outlook também se aplicam aqui.

  Nos dispositivos **Android**, os utilizadores têm de ativar o acesso ao browser. Para efetuar esta ação, o utilizador tem de ativar a opção **Ativar o Acesso ao Browser** no dispositivo inscrito da seguinte forma:
  1.    Abra a aplicação **Portal da Empresa**.
  2.    Aceda à página **Definições** a partir das reticências (…) ou do botão do menu de hardware.
  3.    Prima o botão **Ativar o Acesso ao Browser**.
  4.    No browser Chrome, termine a sessão no Office 365 e reinicie o Chrome.

  Nas plataformas **iOS** e **Android**, para identificar o dispositivo que serve para aceder ao serviço, o Azure Active Directory emite um certificado de Transport layer security (TLS) para o dispositivo. O dispositivo apresenta o certificado com uma linha de comandos para o utilizador para selecionar o certificado, conforme indicado nas seguintes capturas de ecrã. O utilizador tem de selecionar este certificado para poder continuar a utilizar o browser.

  **iOS**

  ![Captura de ecrã da linha de comandos do certificado num iPad](../media/mdm-browser-ca-ios-cert-prompt.png)

  **Android**

  ![captura de ecrã da linha de comandos do certificado num dispositivo Android](../media/mdm-browser-ca-android-cert-prompt.png)

5.  Em **Aplicações do Exchange ActiveSync**, pode optar por bloquear o acesso de dispositivos não conformes ao Exchange Online. Também pode selecionar se pretende permitir ou bloquear o acesso ao e-mail quando o dispositivo não está a executar uma plataforma suportada. As plataformas suportadas incluem Android, iOS, Windows e Windows Phone.

 Aplicações do Exchange Active Sync em dispositivos **Android for Work**:
 -  No **perfil de trabalho**, apenas as aplicações **Gmail** e **Nine Work** são suportadas em dispositivos Android for Work. Para obter acesso condicional ao seu trabalho em dispositivos Android for Work, tem de implementar um perfil de e-mail para a aplicação Gmail ou Nine Work, bem como implementar essas aplicações como uma instalação **obrigatória**.

6.  Em **Grupos Visados**, selecione os grupos de segurança do Active Directory dos utilizadores aos quais será aplicada a política. Pode optar por segmentar todos os utilizadores ou uma lista selecionada de grupos de utilizadores.
![Captura de ecrã da página de política de acesso condicional do Exchange Online, que mostra as opções de Grupos Visados e Excluídos](../media/IntuneSA5eTargetedExemptedGroups.PNG)
    > [!NOTE]
    > Para os utilizadores que estão nos **Grupos visados**, as políticas do Intune substituem as regras e as políticas do Exchange.
    >
    > O Exchange só irá impor permissões, bloqueios, regras de quarentena e políticas do Exchange se:
    >
    > -   Um utilizador não estiver licenciado para o Intune.
    > -   Um utilizador estiver licenciado para o Intune, mas não pertencer a quaisquer grupos de segurança visados pela política de acesso condicional.

6.  Em **Grupos Excluídos**, selecione os grupos de segurança do Active Directory dos utilizadores que estão excluídos desta política. Se um utilizador estiver em ambos os grupos, será excluído da política.

7.  Quando tiver terminado, escolha **Guardar**.

-   Não tem de implementar a política de acesso condicional, pois esta entra em vigor imediatamente.

-   Depois de um utilizador criar uma conta de e-mail, o dispositivo é bloqueado de imediato.

-   Se um utilizador bloqueado inscrever o dispositivo no Intune e corrigir todos os problemas de não conformidade, o acesso ao e-mail será desbloqueado dentro de dois minutos.

-   Se o utilizador anular a inscrição do dispositivo dele, o e-mail é bloqueado ao fim de, aproximadamente, seis horas.

**Para ver alguns cenários de exemplo de como poderia configurar a política de acesso condicional para proteger o acesso ao dispositivo**, veja [Cenários de exemplo da proteção de acesso ao e-mail](restrict-email-access-example-scenarios.md).

## <a name="monitor-the-compliance-and-conditional-access-policies"></a>Monitorizar a conformidade e as políticas de acesso condicional

#### <a name="to-view-devices-that-are-blocked-from-exchange"></a>Para ver os dispositivos bloqueados no Exchange

No dashboard do Intune, escolha o mosaico **Dispositivos Bloqueados no Exchange** para ver o número de dispositivos bloqueados e ligações para obter mais informações.
![Captura de ecrã do dashboard do Intune, que mostra o número de dispositivos que estão impedidos de aceder ao Exchange](../media/IntuneSA6BlockedDevices.PNG)

## <a name="next-steps"></a>Passos seguintes
- [Proteger o acesso ao SharePoint Online](restrict-access-to-sharepoint-online-with-microsoft-intune.md)

- [Proteger o acesso ao Skype para Empresas Online](restrict-access-to-skype-for-business-online-with-microsoft-intune.md)

