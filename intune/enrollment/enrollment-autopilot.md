---
title: Inscrever dispositivos através do Windows Autopilot
titleSuffix: Microsoft Intune
description: Saiba como inscrever dispositivos com o Windows 10 através do Windows Autopilot.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/23/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a2dc5594-a373-48dc-ba3d-27aff0c3f944
ms.reviewer: spshumwa
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5066afdaf303a1cef20f80d3134f2382f718d86b
ms.sourcegitcommit: 2fddb293d37453736ffa54692d03eca642f3ab58
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/22/2019
ms.locfileid: "74390740"
---
# <a name="enroll-windows-devices-in-intune-by-using-the-windows-autopilot"></a>Enroll Windows devices in Intune by using the Windows Autopilot  
The Windows Autopilot simplifies enrolling devices in Intune. A criação e manutenção de imagens personalizadas do sistema operativo são um processo moroso. Também poderá demorar a aplicar estas imagens personalizadas do sistema operativo a novos dispositivos para as preparar para utilização antes de as disponibilizar aos seus utilizadores finais. Com o Microsoft Intune e o Autopilot, pode fornecer novos dispositivos aos seus utilizadores finais sem ter de criar, manter e aplicar imagens de sistema operativo personalizadas aos dispositivos. Ao utilizar o Intune para gerir dispositivos do Autopilot, pode gerir políticas, perfis, aplicações, entre outros, após estes serem inscritos. Para uma descrição geral das vantagens, cenários e pré-requisitos, veja [Descrição geral do Windows Autopilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-10-autopilot).

There are four types of Autopilot deployment:
- [Self Deploying Mode](https://docs.microsoft.com/windows/deployment/windows-autopilot/self-deploying) for kiosks, digital signage, or a shared device
- [White Glove](https://docs.microsoft.com/windows/deployment/windows-autopilot/white-glove) enables partners or IT staff to pre-provision a Windows 10 PC so that it's fully configured and business-ready -[Autopilot for existing devices](https://docs.microsoft.com/windows/deployment/windows-autopilot/existing-devices) enables you to easily deploy the latest version of Windows 10 to your existing devices
- [User Driven Mode](https://docs.microsoft.com/windows/deployment/windows-autopilot/user-driven) for traditional users. 


## <a name="prerequisites"></a>Pré-requisitos
- [Intune subscription](../fundamentals/licenses.md)
- [A Inscrição automática no Windows tem de estar ativada](windows-enroll.md#enable-windows-10-automatic-enrollment)
- [Azure Active Directory Premium subscription](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) <!--&#40;[trial subscription](http://go.microsoft.com/fwlink/?LinkID=816845)&#41;-->

## <a name="how-to-get-the-csv-for-import-in-intune"></a>How to get the CSV for Import in Intune

For more information, see the understanding powershell cmdlet.

- [Get-WindowsAutoPilotInfo](https://www.powershellgallery.com/packages/Get-WindowsAutoPilotInfo)

## <a name="add-devices"></a>Adicionar dispositivos

Pode adicionar dispositivos Windows Autopilot ao importar um ficheiro CSV com as informações dos dispositivos.

1. In the [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431), choose **Device enrollment** > **Windows enrollment** > **Devices** > **Import**.

    ![Captura de ecrã dos dispositivos Windows Autopilot](./media/enrollment-autopilot/autopilot-import-device.png)

2. Em **Adicionar Dispositivos do Windows Autopilot**, procure um ficheiro CSV que liste os dispositivos que pretende adicionar. The CSV file should list the serial numbers, Windows product IDs, hardware hashes, optional group tags, and optional assigned user. You can have up to 500 rows in the list. Use the header and line format shown below:

    `Device Serial Number,Windows Product ID,Hardware Hash,Group Tag,Assigned User`</br>
    `<serialNumber>,<ProductID>,<hardwareHash>,<optionalGroupTag>,<optionalAssignedUser>`

    ![Captura de ecrã de Adicionar dispositivos Windows Autopilot](./media/enrollment-autopilot/autopilot-import-device2.png)

    >[!IMPORTANT]
    > When you use CSV upload to assign a user, make sure that you assign valid UPNs. If you assign an invalid UPN (incorrect username), your device may be inaccessible until you remove the invalid assignment. During CSV upload the only validation we perform on the **Assigned User** column is to check that the domain name is valid. We're unable to perform individual UPN validation to ensure that you're assigning an existing or correct user.

3. Escolha **Importar** para iniciar a importação das informações do dispositivo. A importação poderá demorar alguns minutos.

4. After import is complete, choose **Device enrollment** > **Windows enrollment** > **Windows Autopilot** > **Devices** > **Sync**. A message displays that the synchronization is in progress. O processo poderá demorar alguns minutos a concluir, consoante o número de dispositivos em sincronização.

5. Atualize a vista para ver os novos dispositivos.

## <a name="create-an-autopilot-device-group"></a>Criar um grupo de dispositivos do Autopilot

1. In the [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431), choose **Groups** > **New group**.
2. No painel **Grupo**:
    1. Para **Tipo de grupo**, selecione **Segurança**.
    2. Introduza um **Nome do grupo** e uma **Descrição do grupo**.
    3. Para **Tipo de associação**, selecione **Atribuído** ou **Dispositivo Dinâmico**.
3. Se optou por **Atribuído** para o **Tipo de associação** no passo anterior, no painel **Grupo**, selecione **Membros** e adicione dispositivos do Autopilot ao grupo.
    Os dispositivos Autopilot que ainda não estão inscritos são dispositivos em que o nome é igual ao número de série do dispositivo.
4. Se acima optou por **Dispositivo Dinâmico** para o **Tipo de associação**, no painel **Grupo**, selecione **Membros de dispositivo dinâmicos** e escreva o seguinte código na caixa **Regra avançada**. Only Autopilot devices are gathered by these rules, because they target attributes that are only possessed by Autopilot devices. Creating a group based off non-autopilot attributes won't guarantee that devices included in the group are actually registered to Autopilot.
    - If you want to create a group that includes all of your Autopilot devices, type: `(device.devicePhysicalIDs -any _ -contains "[ZTDId]")`
    - Intune's group tag field maps to the OrderID attribute on Azure AD devices. If you want to create a group that includes all of your Autopilot devices with a specific group tag (the Azure AD device OrderID), you must type: `(device.devicePhysicalIds -any _ -eq "[OrderID]:179887111881")`
    - Se quiser criar um grupo que inclua todos os seus dispositivos do Autopilot com um ID de Nota de Encomenda específico, escreva `(device.devicePhysicalIds -any _ -eq "[PurchaseOrderId]:76222342342")`
    
    Depois de adicionar o código da **Regra avançada**, selecione **Guardar**.
5. Selecione **Criar**.  

## <a name="create-an-autopilot-deployment-profile"></a>Criar um perfil de implementação do Autopilot
Os perfis de implementação do Autopilot são utilizados para configurar os dispositivos do Autopilot. You can create up to 350 profiles per tenant.
1. In the [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431), choose **Device enrollment** > **Windows enrollment** > **Deployment Profiles** > **Create Profile**.
2. On the **Basics** page, type a **Name** and optional **Description**.

    ![Screenshot of Basics page](./media/enrollment-autopilot/create-profile-basics.png)

3. Se pretender que todos os dispositivos nos grupos atribuídos sejam convertidos automaticamente no Autopilot, defina **Converter todos os dispositivos visados para o Piloto Automático** para **Sim**. All corporate owned, non-Autopilot devices in assigned groups will register with the Autopilot deployment service. Personally owned devices will not be converted to Autopilot. O processo de registo demora até 48 horas, pelo que deverá aguardar. Quando a inscrição do dispositivo for anulada e o dispositivo for reposto, o Autopilot irá inscrevê-lo. Após registar um dispositivo desta forma, desativar esta opção ou remover a atribuição de perfil não irá remover o dispositivo do serviço de implementação do Autopilot. Em alternativa, tem de [remover o dispositivo diretamente](enrollment-autopilot.md#delete-autopilot-devices).
4. Selecione **Seguinte**.
5. On the **Out-of-box experience (OOBE)** page, for **Deployment mode**, choose one of these two options:
    - **Orientado pelo utilizador**: os dispositivos com este perfil são associados ao utilizador que inscreve o dispositivo. Precisa de credenciais de utilizador para inscrever o dispositivo.
    - **Self-deploying (preview)** : (requires Windows 10, version 1809 or later) Devices with this profile aren't associated with the user enrolling the device. Não são necessárias credenciais de utilizador para inscrever o dispositivo. When a device has no user associated with it, user-based compliance policies don't apply to it. When using self-deploying mode, only compliance policies targeting the device will be applied.

    ![Screenshot of OOBE page](./media/enrollment-autopilot/create-profile-outofbox.png)

6. Na caixa **Aderir ao Azure AD como**, selecione **Associado ao Azure AD**.
7. Configure the following options:
    - **Contrato de licença do utilizador final (EULA)** : (Versão 1709 ou posterior do Windows 10) selecione se pretende ou não apresentar o EULA aos utilizadores.
    - **Definições de privacidade**: selecione se pretende apresentar definições de privacidade aos utilizadores.
    >[!IMPORTANT]
    >The default value for the Diagnostic Data setting varies between Windows versions. For devices running Windows 10, version 1903, the default value is set to Full during the out-of-box experience. For more information, see [Windows Diagnostics Data](https://docs.microsoft.com/windows/privacy/windows-diagnostic-data) <br>
    
    - **Hide change account options (requires Windows 10, version 1809 or later)** : Choose **Hide** to prevent change account options from displaying on the company sign-in and domain error pages. Esta opção requer a [configuração da imagem corporativa da empresa no Azure Active Directory](https://docs.microsoft.com/azure/active-directory/fundamentals/customize-branding).
    - **Tipo de conta de utilizador**: selecione o tipo de conta de utilizador (**Administrador** ou utilizador **Padrão**). We allow the user joining the device to be a local Administrator by adding them to the local Admin group. We don't enable the user as the default administrator on the device.
    - **Allow White Glove OOBE** (requires Windows 10, version 1903 or later; [additional physical requirements](https://docs.microsoft.com/windows/deployment/windows-autopilot/white-glove#prerequisites)): Choose **Yes** to allow white glove support.
    - **Apply device name template** (requires Windows 10, version 1809 or later, and Azure AD join type): Choose **Yes** to create a template to use when naming a device during enrollment. Os nomes têm de ter 15 carateres ou menos e podem conter letras, números e hífenes. Não podem conter apenas números. Utilize a [macro %SERIAL%](https://docs.microsoft.com/windows/client-management/mdm/accounts-csp) para adicionar um número de série específico de hardware. Em alternativa, utilize a [macro %RAND:x%](https://docs.microsoft.com/windows/client-management/mdm/accounts-csp) para adicionar uma cadeia de números aleatória na qual x corresponde ao número de dígitos a adicionar. You can only provide a pre-fix for hybrid devices in a [domain join profile](windows-autopilot-hybrid.md#create-and-assign-a-domain-join-profile). 
    - **Idioma (Região)** \*: selecione o idioma a utilizar para o dispositivo. Esta opção só está disponível se tiver optado pela **Implementação personalizada** no **Modo de implementação**.
    - **Automatically configure keyboard**\*: If a **Language (Region)** is selected, choose **Yes** to skip the keyboard selection page. Esta opção só está disponível se tiver optado pela **Implementação personalizada** no **Modo de implementação**.
8. Selecione **Seguinte**.
9. On the **Scope tags** page, optionally add the scope tags you want to apply to this profile. For more information about scope tags, see [Use role-based access control and scope tags for distributed IT](../fundamentals/scope-tags.md).
10. Selecione **Seguinte**.
11. On the **Assignments** page, choose **Selected groups** for **Assign to**.

    ![Screenshot of Assignments page](./media/enrollment-autopilot/create-profile-assignments.png)

12. Choose **Select groups to include**, and choose the groups you want to include in this profile.
13. If you want to exclude any groups, choose **Select groups to exclude**, and choose the groups you want to exclude.
14. Selecione **Seguinte**.
15. On the **Review + Create** page, choose **Create** to create the profile.

    ![Screenshot of Review page](./media/enrollment-autopilot/create-profile-review.png)

> [!NOTE]
> Intune will periodically check for new devices in the assigned groups, and then begin the process of assigning profiles to those devices. This process can take several minutes to complete. Before deploying a device, ensure that this process has completed.  You can check under **Device enrollment** > **Windows enrollment** > **Devices** where you should see the profile status change from "Unassigned" to "Assigning" and finally to "Assigned."

## <a name="edit-an-autopilot-deployment-profile"></a>Editar um perfil de implementação do Autopilot
Após ter criado um perfil de implementação do Autopilot, poderá editar determinadas partes do perfil de implementação.   

1. In the [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431), choose **Device enrollment**.
2. Em **Inscrição no Windows**, na secção **Windows Autopilot**, selecione **Perfis de Implementação**.
3. Selecione o perfil que pretende editar.
4. À esquerda, clique em **Propriedades** para alterar o nome ou a descrição do perfil de implementação. Após ter efetuado as alterações, clique em **Guardar**.
5. Clique em **Definições** para efetuar alterações às definições da OOBE. Após ter efetuado as alterações, clique em **Guardar**.

> [!NOTE]
> As alterações ao perfil são aplicadas aos dispositivos atribuídos a esse perfil. No entanto, o perfil atualizado não será aplicado a um dispositivo já inscrito no Intune até que o dispositivo tenha sido reposto e reinscrito.

## <a name="edit-autopilot-device-attributes"></a>Edit Autopilot device attributes
After you've uploaded an Autopilot device, you can edit certain attributes of the device.

1. In Intune in the Azure portal, choose **Device enrollment**.
2. Under **Windows enrollment**, in the **Windows Autopilot** section, choose **Devices**.
3. Select the device you want to edit.
4. In the pane on the right of the screen, you can edit the device name, group tag, or User Friendly Name (if you've assigned a user).
5. Selecione **Guardar**.

> [!NOTE]
> Device names can be configured for all devices, but are ignored in Hybrid Azure AD joined deployments. Device name still comes from the domain join profile for Hybrid Azure AD devices.

## <a name="alerts-for-windows-autopilot-unassigned-devices-----163236---"></a>Alerts for Windows Autopilot unassigned devices  <!-- 163236 -->  

Os alertas irão indicar quantos dispositivos do programa Autopilot não têm perfis de implementação do Autopilot. Utilize as informações no alerta para criar perfis e atribui-los aos dispositivos não atribuídos. Quando clica no alerta, é-lhe apresentada uma lista completa dos dispositivos Windows Autopilot e informações detalhadas sobre os mesmos.

Para ver alertas de dispositivos não atribuídos, no [Intune no portal do Azure](https://aka.ms/intuneportal), selecione **Inscrição de dispositivos** > **Descrição geral** > **Dispositivos não atribuídos**.  

## <a name="assign-a-user-to-a-specific-autopilot-device"></a>Atribuir um utilizador a um dispositivo do Autopilot específico

Pode atribuir um utilizador a um dispositivo do Autopilot específico. Esta atribuição preenche previamente um utilizador do Azure Active Directory na página de início de sessão [empresarial](https://docs.microsoft.com/azure/active-directory/fundamentals/customize-branding) durante a configuração do Windows. Também permite definir um nome de saudação personalizado. Esta ação não preenche previamente nem modifica o início de sessão do Windows. Os utilizadores licenciados do Intune são os únicos que podem ser atribuídos desta forma.

Prerequisites: Azure Active Directory Company Portal has been configured and Windows 10, version 1809 or later.

1. In the [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431), choose **Device enrollment** > **Windows enrollment** > **Devices** > choose the device > **Assign user**.

    ![Captura de ecrã de Atribuir utilizador](./media/enrollment-autopilot/assign-user.png)

2. Selecione um utilizador licenciado do Azure para utilizar o Intune e selecione **Selecionar**.

    ![Captura de ecrã da seleção do utilizador](./media/enrollment-autopilot/select-user.png)

3. Na caixa **Nome amigável de utilizador**, escreva um nome amigável ou aceite simplesmente o nome predefinido. Esta cadeia é o nome amigável que é apresentado quando o utilizador inicia sessão durante a configuração do Windows.

    ![Captura de ecrã do nome amigável](./media/enrollment-autopilot/friendly-name.png)

4. Selecione **OK**.

## <a name="autopilot-deployments-report"></a>Autopilot deployments report
You can see details on each device deployed through Windows Autopilot.
To see the report, go to **Intune** and, under **Monitor**, choose **Autopilot deployments**.
The data is available for 30 days after deployment.


## <a name="delete-autopilot-devices"></a>Eliminar dispositivos Autopilot

You can delete Windows Autopilot devices that aren't enrolled into Intune:

- Delete the devices from Windows Autopilot at **Device enrollment** > **Windows enrollment** > **Devices**. Choose the devices you want to delete, then choose **Delete**. Windows Autopilot device deletion can take a few minutes to complete.

Completely removing a device from your tenant requires you to delete the Intune device, the Azure Active Directory device, and the Windows Autopilot device records. This can all be done from Intune:

1. If the devices are enrolled in Intune, you must first [delete them from the Intune All devices blade](../remote-actions/devices-wipe.md#delete-devices-from-the-azure-active-directory-portal).

2. Delete the devices in Azure Active Directory devices at **Devices** > **Azure AD devices**.

3. Delete the devices from Windows Autopilot at **Device enrollment** > **Windows enrollment** > **Devices**. Choose the devices you want to delete, then choose **Delete**. Windows Autopilot device deletion can take a few minutes to complete.

## <a name="using-autopilot-in-other-portals"></a>Utilizar o Autopilot noutros portais
Se não estiver interessado na gestão de dispositivos móveis, pode utilizar o Autopilot noutros portais. Embora a utilização de outros portais seja uma opção, recomendamos-lhe que apenas utilize o Intune para gerir as suas implementações do Autopilot. Se utilizar o Intune e outro portal, o Intune não será capaz de:  

- Apresentar alterações aos perfis criados no Intune que tenham sido editados noutro portal
- Sincronizar perfis criados noutro portal
- Apresentar alterações a atribuições de perfil efetuadas noutro portal
- Sincronizar atribuições de perfil efetuadas noutro portal
- Apresentar as alterações à lista de dispositivos que foram feitas noutro portal

## <a name="windows-autopilot-for-existing-devices"></a>Windows Autopilot para dispositivos existentes

Pode agrupar dispositivos Windows por um ID de correlacionador ao inscrevê-los com o [Autopilot para dispositivos existentes](https://techcommunity.microsoft.com/t5/Windows-IT-Pro-Blog/New-Windows-Autopilot-capabilities-and-expanded-partner-support/ba-p/260430), através do Configuration Manager. O ID de correlacionador é um parâmetro do ficheiro de configuração do Autopilot. O [atributo enrollmentProfileName de dispositivos do Azure AD](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership#rules-for-devices) é automaticamente definido para ser igual a "OfflineAutopilotprofile-\<correlator ID\>". Isto permite que sejam criados grupos dinâmicos do Azure AD arbitrários com base no ID de correlacionador ao utilizar o atributo enrollmentprofileName.

>[!WARNING] 
> Como o ID de correlacionador não está listado previamente no Intune, o dispositivo pode comunicar qualquer ID de correlacionador. Se o utilizador criar um ID de correlacionador que corresponda a um nome de perfil do Autopilot ou DEP da Apple, o dispositivo será adicionado a qualquer grupo de dispositivos dinâmico do Azure Active Directory com base no atributo enrollmentProfileName. Para impedir este conflito:
> - Crie sempre regras de grupos dinâmico que correspondam a *todo* o valor enrollmentProfileName
> - Nunca crie um nome para perfis de Autopilot ou DEP da Apple começado por "OfflineAutopilotprofile-".

## <a name="next-steps"></a>Próximos passos
Após ter configurado o Windows Autopilot para dispositivos Windows 10 registados, saiba como gerir esses dispositivos. Para obter mais informações, veja [O que é a gestão de dispositivos do Microsoft Intune?](../remote-actions/device-management.md)
