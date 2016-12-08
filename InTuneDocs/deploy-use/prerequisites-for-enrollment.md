---
title: "Pré-requisitos para a inscrição de dispositivos móveis | Microsoft Intune"
description: "Configurar os pré-requisitos da gestão de dispositivos móveis (MDM) e preparar-se para inscrever sistemas operativos diferentes."
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 07/25/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 44fd4af0-f9b0-493a-b590-7825139d9d40
ms.reviewer: damionw
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: eeb85a28ea6f99a0123ec5df3b0d476a678b85cb
ms.openlocfilehash: 391612c35a7665073ca8a5c629169e5be967ab59


---

# <a name="prerequisites-for-mobile-device-management-in-intune"></a>Pré-requisitos para a gestão de dispositivos móveis no Intune
Para permitir que os seus funcionários inscrevam os respetivos dispositivos móveis no Intune, é necessário aplicar os passos que se seguem. Estes passos também são necessários para gerir dispositivos pertencentes à empresa.

|Passos|Detalhes|  
|-----------|-------------|  
|**Passo 1:** [ativar as ligações](#step-1-enable-connections)|Certifique-se de que o nome personalizado do seu domínio foi configurado e que as comunicações de rede estão prontas|  
|**Passo 2:** [definir a autoridade MDM](#step-2-set-mdm-authority)|A autoridade de gestão de dispositivos móveis define o serviço atribuído aos seus dispositivos|
|**Passo 3:** [criar grupos](#step-3-create-groups)|Configure as definições destinadas ao utilizador para a aplicação Portal da Empresa|  
|**Passo 4:** [configurar o Portal da Empresa](#step-4-configure-company-portal)|Configure as definições destinadas ao utilizador para a aplicação Portal da Empresa|  
|**Passo 5:** [atribuir licenças de utilizador](#step-5-assign-user-licenses)|Atribua licenças do Intune aos utilizadores para que estes possam inscrever dispositivos|
|**Passo 6:** [ativar a inscrição](#step-6-enable-enrollment)|Ative definições específicas da plataforma para a gestão de dispositivos iOS e Windows. Os dispositivos Android não precisam de configurações adicionais.|
|**Passo 7:** [passos seguintes](#step-7-next-steps)|Ative definições específicas da plataforma para a gestão de dispositivos iOS e Windows. Os dispositivos Android não precisam de configurações adicionais.|

Está à procura do Intune com o Configuration Manager?
> [!div class="button"]
[Ver documentos do SCCM >](https://docs.microsoft.com/sccm/mdm/deploy-use/setup-hybrid-mdm)

## <a name="step-1-enable-connections"></a>Passo 1: ativar as ligações

Antes de ativar a inscrição de dispositivos móveis, certifique-se de que efetuou os seguintes procedimentos:
- [Rever as portas e os URLs de rede necessários](../get-started/network-infrastructure-requirements-for-microsoft-intune)
- [Adicionar e verificar o seu nome de domínio](../get-started/domain-names-for-microsoft-intune)

## <a name="step-2-set-mdm-authority"></a>Passo 2: definir a autoridade MDM
A autoridade de MDM define o serviço de gestão que tem permissão para gerir um conjunto de dispositivos. As opções para a autoridade de MDM incluem o Intune autónomo e o Configuration Manager com o Intune. Se definir o Configuration Manager como autoridade de gestão, nenhum outro serviço pode ser utilizado para gestão de dispositivos móveis.

>[!IMPORTANT]
> Considere cuidadosamente se pretende gerir dispositivos móveis apenas com o Intune (serviço online) ou com o System Center Configuration Manager com o Intune (solução de software no local em conjunto com o serviço online). A definição da autoridade de gestão de dispositivos móveis não pode ser alterada.



1.  Na [consola do administração do Microsoft Intune](http://manage.microsoft.com), escolha **Admin** &gt; **Mobile Device Management**.

2.  Na lista **Tasks**, clique em **Set Mobile Device Management Authority**. A caixa de diálogo **Definir Autoridade de Gestão de Dispositivos Móveis** é aberta.

    ![Caixa de diálogo Definir autoridade de MDM](../media/intune-mdm-authority.png)

3.  O Intune pede a confirmação de que pretende o Intune como a sua autoridade MDM. Selecione a caixa de verificação e, em seguida, escolha **Sim** para utilizar o Microsoft Intune para gerir dispositivos móveis.

## <a name="step-3-create-groups"></a>Passo 3: criar grupos

Pode criar grupos de utilizadores e dispositivos para simplificar a gestão e melhorar a filtragem de aplicações, políticas e recursos da empresa implementados. [Saiba como criar grupos](use-groups-to-manage-users-and-devices-with-microsoft-intune.md#create-groups).

## <a name="step-4-configure-company-portal"></a>Passo 4: configurar o Portal da Empresa

O Portal da Empresa do Intune é onde os utilizadores acedem aos dados da empresa e podem realizar tarefas comuns, como inscrever dispositivos, instalar aplicações e localizar informações de assistência do departamento de TI.

> [!TIP]
> Quando personaliza o Portal da Empresa, as configurações aplicam-se tanto ao site do Portal da Empresa, como às aplicações do Portal da Empresa.

Personalizar o Portal da Empresa ajuda a proporcionar uma experiência familiar e útil aos utilizadores finais. Para tal, basta iniciar sessão na [consola de administrador do Microsoft Intune](https://manage.microsoft.com) como administrador de inquilinos ou de serviços, escolher **Administrador** &gt; **Portal da Empresa** e configurar as definições do Portal da Empresa.

![admin-console-admin-workspace-comp-portal-settings](../media/cp_sa_cpsetup.PNG)

### <a name="company-contact-information-and-privacy-statement"></a>Informações de contacto e declaração de privacidade da empresa

O nome da empresa é apresentado como o título do Portal da Empresa. Os detalhes e as informações de contacto são apresentados aos utilizadores no ecrã Contactar TI do Portal da Empresa. A declaração de privacidade é apresentada quando um utilizador clica na ligação de privacidade.

|Nome do campo|Comprimento máximo|Mais informações|
    |----------|------------------------|----------------|
    |Nome da empresa|40|Este nome é apresentado como o título do Portal da Empresa. **Nota**: apenas carateres alfanuméricos. Este campo não suporta carateres especiais.|
    |Nome do contacto do departamento de TI|40|Este nome é apresentado na página **Contactar TI**.|
    |Número de telefone do departamento de TI|20|Este número de contacto é apresentado na página **Contactar TI**.|
    |Endereço de e-mail do departamento de TI|40|Este endereço de contacto é apresentado na página **Contactar TI**. Tem de inserir um endereço de e-mail válido no formato **alias@domainname.com**.|
    |Informações adicionais|120|Estas informações são apresentadas na página **Contactar TI**.|
    |URL da declaração de privacidade da empresa|79|Pode especificar a sua declaração de privacidade da empresa que é apresentada quando os utilizadores clicam nas ligações de privacidade a partir do Portal da Empresa. Tem de introduzir um URL válido no formato https://www.contoso.com.|

### <a name="support-contacts"></a>Contactos de suporte
O site de suporte é apresentado para os utilizadores no Portal da Empresa para que possam aceder ao suporte online.

|Nome do campo|Comprimento máximo|Mais informações|
    |----------|------------------------|----------------|
    |URL do site de suporte|150|Se tiver um site de suporte que pretende que os utilizadores usem, especifique o URL aqui. O URL tem de estar no formato https://www.contoso.com. Se não especificar um URL, não será apresentado nada no site de suporte da página **Contactar TI** no Portal da Empresa.|
    |Nome do site|40|Este é o nome amigável apresentado no URL do site de suporte. Se especificar um URL do site de suporte, mas não especificar um nome amigável, a ligação **Aceder ao site de TI** será apresentada na página **Contactar TI** no Portal da Empresa.|


### <a name="company-branding-customization"></a>Personalização da imagem corporativa da empresa

Pode personalizar o Portal da Empresa com o logótipo e o nome da empresa, a cor do tema e o fundo.

|Nome do campo|Mais informações|
    |----------|----------------|
    |Cor do tema|Selecione a cor do tema que pretende aplicar ao Portal da Empresa.|
    |Incluir o logótipo da empresa|Quando ativa esta opção, pode carregar o logótipo da sua empresa que pretende que seja apresentado no Portal da Empresa. Pode carregar dois logótipos: um que é apresentado quando o fundo do Portal da Empresa é branco e outro que é apresentado quando o fundo do Portal da Empresa utiliza a cor do tema que selecionou. Cada logótipo tem de ser um ficheiro .png ou .jpg, ter uma resolução máxima de 400 x 100 píxeis e ter um tamanho de 750 KB ou menos.|
    |Selecionar um fundo para a aplicação Portal da Empresa|Esta definição afeta apenas o fundo da aplicação Portal da Empresa.|


Depois de guardar as alterações, pode utilizar as ligações fornecidas na parte inferior da página **Portal da Empresa** da consola de administração para ver o site do Portal da Empresa. Estas ligações não podem ser alteradas. Quando um utilizador inicia sessão, estas ligações apresentam as suas subscrições no Portal da Empresa.

## <a name="step-5-assign-user-licenses"></a>Passo 5: atribuir licenças de utilizador

Para adicionar manualmente utilizadores baseados na nuvem e atribuir licenças às contas de utilizador baseadas na nuvem e às contas sincronizadas do Active Directory no local com o Azure Active Directory (Azure AD), é utilizado o **portal de gestão do Office 365**. Pode [sincronizar utilizadores no local com o Azure AD](../get-started/domain-names-for-microsoft-intune#to-synchronize-on-premises-users-with-azure-ad.md).

1.  Inicie sessão no [portal de gestão do Office 365](https://portal.office.com/Admin/Default.aspx) com as suas credenciais de administrador de inquilino.

2.  Selecione a conta de utilizador à qual pretende atribuir uma licença de utilizador do Intune e selecione a caixa de verificação **Microsoft Intune** nas propriedades da conta de utilizador.

3.  A conta de utilizador será agora adicionada ao grupo de utilizadores do Microsoft Intune, que atribui as permissões de utilizador para utilizar o serviço e inscrever os respetivos dispositivos para gestão.

### <a name="to-synchronize-on-premises-users-with-azure-ad"></a>Sincronizar os utilizadores no local com o Azure AD

1. [Adicionar o sufixo UPN](https://technet.microsoft.com/en-us/library/cc772007.aspx) para o seu domínio personalizado no Active Directory no local.
2. Defina o sufixo UPN novo para os utilizadores no local que pretende importar.
3. Execute a [sincronização do Azure AD Connect](https://azure.microsoft.com/en-us/documentation/articles/active-directory-aadconnect/) para integrar os seus utilizadores no local com o Azure AD.
4. Assim que as informações de conta de utilizador forem sincronizadas com êxito, pode atribuir licenças do Microsoft Intune utilizando o [Portal de Gestão do Office 365](https://portal.office.com/Admin/Default.aspx).

## <a name="step-6-enable-enrollment"></a>Passo 6: ativar a inscrição
Depois de configurar a autoridade de MDM, tem de configurar a gestão de dispositivos nos sistemas operativos que a sua organização pretende suportar. Os passos necessários para configurar a gestão de dispositivos variam consoante o sistema operativo. Por exemplo, o SO Android não requer que efetue nenhuma ação na consola de administração do Intune. Por outro lado, o Windows e o iOS requerem uma relação de confiança entre os dispositivos e o Intune para permitir a gestão.

Configurar a gestão das seguintes plataformas:
- [iOS e Mac](set-up-ios-and-mac-management-with-microsoft-intune.md)
- [Android](set-up-android-management-with-microsoft-intune.md)
- [Android for Work](set-up-android-for-work.md)
- [PCs e Portáteis Windows](set-up-windows-device-management-with-microsoft-intune.md)
- [Windows 10 Mobile e Windows Phone](set-up-windows-phone-management-with-microsoft-intune.md)

Também pode ativar a [inscrição de dispositivos pertencentes à empresa](manage-corporate-owned-devices).

## <a name="step-7-next-steps"></a>Passo 7: passos seguintes

Agora que a inscrição está ativada, deve configurar a gestão para cumprir as necessidades da sua empresa. Eis algumas opções de gestão:

- [Implementar políticas que gerem definições e funcionalidades nos dispositivos](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)
- [Ativar o acesso aos recursos da empresa, como e-mail, Wi-Fi e VPN](enable-access-to-company-resources-with-microsoft-intune.md)
- [Adicionar aplicações](add-apps.md) e [implementar aplicações](deploy-apps.md) para dispositivos geridos
- [Criar políticas de conformidade de dispositivo](introduction-to-device-compliance-policies-in-microsoft-intune.md) e [restringir acesso com base na conformidade](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)



<!--HONumber=Nov16_HO1-->


