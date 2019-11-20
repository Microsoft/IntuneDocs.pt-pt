---
title: Como configurar a aplicação do Portal da Empresa
titleSuffix: Microsoft Intune
description: Learn how you can apply company-specific branding to the Intune Company Portal app.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: dec6f258-ee1b-4824-bf66-29053051a1ae
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b750c09207b1950aa27a5f2cae1267503537b6e7
ms.sourcegitcommit: 01fb3d844958a0e66c7b87623160982868e675b0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/20/2019
ms.locfileid: "74199200"
---
# <a name="how-to-configure-the-microsoft-intune-company-portal-app"></a>Como configurar a aplicação Portal da Empresa do Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

O portal da empresa do Microsoft Intune é onde os utilizadores acedem aos dados da empresa e podem realizar tarefas comuns, como inscrever dispositivos, instalar aplicações e localizar informações de assistência do departamento de TI. Additionally, the company portal app allows user to securely access company resources. The company portal app provides several different pages, such as Home, Apps, App details, Devices, and Device details. To quickly find apps within the Company Portal, you can filter the apps on the Apps page.

> [!IMPORTANT]
> To support Google’s Firebase Cloud Messaging (FCM), you must update your Android Company Portal app to the latest version.  

> [!Tip]
> Quando personaliza o Portal da Empresa, as configurações aplicam-se tanto ao site do Portal da Empresa, como às aplicações do Portal da Empresa. Tenha em atenção que os utilizadores têm de ter uma licença do Intune atribuída para poderem aceder ao site do Portal da Empresa.

A personalização do Portal da Empresa ajuda a proporcionar uma experiência familiar e útil aos utilizadores finais. Para tal, no portal do Intune, selecione **Aplicações cliente** > **Marca e personalização** e, em seguida, configure as definições necessárias.

When a user is installing an iOS application from the Company Portal they will receive a prompt. This occurs when the iOS app is linked to the app store, linked to a volume-purchase program (VPP), or linked to a line-of-business (LOB) app. The prompt allows the users to accept the action or allow management of the app. The prompt will display your company name, or when your company name is unavailable, **Company Portal** will be displayed. 

> [!Note]
> Se estiver a utilizar o Azure Government, os registos de aplicações estão disponíveis para o utilizador final decidir como pretende partilhar ao iniciar o processo para obter ajuda com um problema. No entanto, se não estiver a utilizar o Azure Government, o Portal da Empresa para Windows 10 irá enviar registos de aplicações diretamente para a Microsoft quando o utilizador iniciar o processo para obter ajuda com um problema. O envio dos registos de aplicações para a Microsoft irá facilitar a resolução dos problemas. 

## <a name="company-information-and-privacy-statement"></a>Informações e declaração de privacidade da empresa
O nome da empresa é apresentado como o título do Portal da Empresa. A declaração de privacidade é apresentada quando um utilizador clica na ligação de privacidade.

| Nome do campo | Comprimento máximo | Mais informações |
|---|---|---|
|**Nome da empresa**| 40 | Este nome é apresentado como o título do Portal da Empresa e é apresentado como texto em toda a experiência de utilizador do Intune. |
| **URL de declaração de privacidade** |     79     | Pode especificar a sua declaração de privacidade da empresa que é apresentada quando os utilizadores clicam nas ligações de privacidade a partir do Portal da Empresa. Tem de introduzir um URL válido no formato `<https://www.contoso.com>`. |

> [!NOTE]
> Consistent with Microsoft and Apple policy, we do not sell any data collected by our service to any third parties for any reason.

## <a name="support-information"></a>Informações de suporte
Introduza as informações de suporte da sua empresa para que o colaborador tenha um contacto para questões relacionadas com o Intune.

|Nome do campo|Comprimento máximo|Mais informações|
|---|---|---|
|**Nome do contacto** | 40 | This name is displayed on the **Help and Support** page. |
|**Número de telefone** | 20 | This contact number is displayed on the **Help and Support** page to enable employees to contact you for support. |
|**Endereço de e-mail**| 40 | This contact address is displayed on the **Help and Support** page. Tem de inserir um endereço de e-mail válido no formato `alias@domainname.com`. |
|**Nome do site**| 40 | Este é o nome amigável apresentado no URL do site de suporte. If you specify a support website URL and no friendly name, then Go to IT website is displayed on the **Help and Support** page in the Company Portal. |
|**URL do Site**| 150 | Se tiver um site de suporte que pretende que os utilizadores usem, especifique o URL aqui. O URL tem de estar no formato `https://www.contoso.com`. If you don't specify a URL, nothing is displayed for the support website on the **Help and Support** page in the Company Portal. |
| **Informações adicionais**| 120 | Displayed on the **Help and Support** page. |


## <a name="company-identity-branding-customization"></a>Personalização da imagem corporativa da identidade da empresa
Pode personalizar o Portal da Empresa com o logótipo e o nome da empresa, a cor do tema e o fundo.

### <a name="theme-color-and-logo-in-the-company-portal"></a>Logótipo e cor do tema no Portal da Empresa
Aplique a cor do tema ao Portal da Empresa. Selecione uma cor padrão ou introduza um código hexadecimal de seis dígitos para obter uma cor personalizada.

|Nome do campo|Mais informações|
|---|---|
|**Selecionar uma cor padrão ou introduzir um código hexadecimal de seis dígitos**| Escolha **Padrão** para selecionar visualmente uma cor. Escolha **Personalizada** para selecionar uma cor específica com base num valor de código hexadecimal.|
|**Escolher a cor do tema**| Selecione a cor do tema que pretende aplicar ao Portal da Empresa. Pode escolher uma cor padrão ou introduzir um código hexadecimal específico. |
|**Apresentar**| Selecione se pretende apresentar o **Logótipo e o nome da empresa**, **Apenas o logótipo da empresa** ou **Apenas o nome da empresa**. |
|**Carregar o logótipo da empresa**|Pode carregar o logótipo da empresa para mostrar no Portal da Empresa. Tenha em atenção que a cor do texto será automaticamente escolhida para proporcionar o maior nível de contraste. Para obter o melhor aspeto, carregue um logótipo com um fundo transparente.<p><ul><li>Tamanho máximo da imagem: 400 x 400 px</li><li>Tamanho máximo do ficheiro: 750 KB</li><li>Tipo de ficheiro: PNG, JPG ou JPEG</li></ul>|

Depois de carregar o logótipo, a área de pré-visualização mostrará o logótipo com a cor do tema. Se optar por apresentar o nome da sua empresa, este será mostrado em preto ou branco no Portal da Empresa e será automaticamente escolhido para proporcionar o maior nível de contraste com base na cor do seu tema. A área de pré-visualização no ecrã não apresentará o nome da sua empresa. 

### <a name="logo-to-use-on-white-or-light-backgrounds"></a>Logótipo para utilizar em fundos brancos ou claros
Escolha o logótipo que ficará melhor em fundos brancos ou claros.

|Nome do campo|Mais informações|
|---|---|
|**Carregar o logótipo**| Esta opção está disponível se tiver optado por mostrar o logótipo da empresa. Para obter o melhor aspeto, carregue um logótipo com um fundo transparente.<p><ul><li>Tamanho máximo da imagem: 400 x 400 px</li><li>Tamanho máximo do ficheiro: 750 KB</li><li>Tipo de ficheiro: PNG, JPG ou JPEG</li></ul>|

### <a name="brand-image-for-company-portal"></a>Imagem de marca do Portal da Empresa

Apresente uma imagem de marca que reflita a marca da sua empresa. Depois de guardar as alterações, pode optar por **Pré-visualizar as definições** no Portal Web do Intune na parte superior do painel para ver qual será o aspeto das configurações. Tenha em atenção que só poderá pré-visualizar a imagem de marca num dispositivo iOS e não no Portal Web do Intune. 

|Nome do campo|Mais informações|
|---|---|
|**Carregar a imagem de marca**| Esta opção permite-lhe apresentar uma imagem de marca. No Portal da Empresa do iOS, é apresentada como uma imagem de fundo na página de perfil do utilizador.<p><ul><li>Recommended image width: Greater than 1125px (required to be at least 650 px)</li><li>Tamanho máximo da imagem: 1,3 MB</li><li>Tipo de ficheiro: PNG, JPG ou JPEG</li></ul>|

A imagem de marca correta pode melhorar a confiança do utilizador no Portal da Empresa ao apresentar uma imagem sólida da marca da sua empresa. Aqui estão algumas sugestões que poderá considerar para comprar, escolher e otimizar a imagem do Portal da Empresa. 

- Entre em contacto com o Departamento de Marketing ou de Artes Gráficas. Estes departamentos podem já ter um conjunto de imagens de marca aprovado. Também poderão ajudá-lo a otimizar as imagens conforme necessário. 

- Considere tanto a composição horizontal como a vertical. A imagem deve ter um fundo suficiente, de forma a envolver o ponto focal. A imagem pode ser recortada de forma diferente com base na orientação, no tamanho e na plataforma do dispositivo. 

- Evite utilizar uma imagem de stock genérica. A imagem deve refletir a marca da sua empresa e ser familiar aos utilizadores. Se não tiver uma, é melhor não utilizar uma imagem genérica que não faça sentido para o seu utilizador. 

- Remova os metadados desnecessários. O ficheiro de imagem pode vir com metadados, tais como o perfil da câmara, a geolocalização, o título, a legenda, etc. Utilize uma ferramenta de otimização de imagens para retirar estas informações para manter a qualidade e cumprir o limite de tamanho do ficheiro. 

Depois de uma imagem de marca ter sido adicionada ou alterada no Intune, o utilizador final poderá não ver a alteração nos dispositivos iOS, até que o Portal da Empresa reconheça a alteração no arranque e tenha sido reiniciado para apresentar a imagem de marca. 

### <a name="brand-image-examples"></a>Exemplos de imagem de marca

A imagem seguinte mostra um exemplo de imagem corporativa no iPad:

![Captura de ecrã de exemplo de imagem corporativa no iPhone](./media/company-portal-app/company-portal-app-03.png)

A imagem seguinte mostra um exemplo de imagem corporativa no iPhone:

![Captura de ecrã de exemplo de imagem corporativa no iPad](./media/company-portal-app/company-portal-app-02.png)

## <a name="privacy-statement-customization"></a>Privacy statement customization

You can customize the privacy statement that appears for your organization on managed iOS devices. This message lists the items that your organization can't see or do on managed iOS devices.

Under **Company Portal customization** > **Device management and privacy message**, you can:

- Accept the **Default** to use the list as shown, or
- Choose **Custom** to customize the the list of items that your organization can’t see or do on managed iOS devices. You can use [markdown](https://daringfireball.net/projects/markdown/) to add bullets, bolding, italics, and links.

## <a name="company-portal-derived-credentials-for-ios-devices"></a>Company Portal derived credentials for iOS devices
Intune supports Personal Identity Verification (PIV) and Common Access Card (CAC) Derived Credentials in partnership with credential providers DISA Purebred, Entrust Datacard, and Intercede. End users will go through additional steps post-enrollment of their iOS device to verify their identity in the Company Portal application. Derived Credentials will be enabled for users by first setting up a credential provider for your tenant, then targeting a profile that uses Derived Credentials to users or devices.

> [!NOTE]
> The user will see instructions about derived credentials based on the link that you have specified via Intune.

For more information about derived credentials for iOS devices, see [Use derived credentials in Microsoft Intune](~/protect/derived-credentials.md).

## <a name="dark-mode-for-ios-company-portal"></a>Dark Mode for iOS Company Portal

Dark Mode is available for the iOS Company Portal. Users can download company apps, manage their devices, and get IT support in the color scheme of their choice based on device settings. The iOS Company Portal will automatically match the end user's device settings for dark or light mode. 

## <a name="windows-company-portal-keyboard-shortcuts"></a>Atalhos de teclado do Portal da Empresa do Windows

Os utilizadores finais podem ativar ações de navegação, de aplicação e de dispositivo no Portal da Empresa do Windows com atalhos de teclado.

Os atalhos de teclado seguintes estão disponíveis na aplicação Portal da Empresa do Windows.

| Área | Description | Keyboard shortcut |
|:------------------:|:--------------:|:-----------------:|
| Menu de navegação | Navegação | Alt+M |
|  | Casa | Alt+H |
|  | Todas as aplicações | Alt+A |
|  | Aplicações instaladas | Alt+I |
|  | Enviar feedback | Alt+F |
|  | O meu perfil | Alt+U |
|  | Definições | Alt+T |
| Base – Mosaico Dispositivo | Mudar o nome | F2 |
|  | Remove | Ctrl+D ou Delete |
|  | Verificar o acesso | Ctrl+M ou F9 |
| Detalhes do dispositivo | Mudar o nome | F2 |
|  | Remove | Ctrl+D ou Delete |
|  | Verificar o acesso | Ctrl+M ou F9 |
| Detalhes da aplicação | Instalar | Ctrl+I |
| Dispositivos | Disponível | Ctrl+D |

Os utilizadores finais também poderão ver os atalhos disponíveis na aplicação Portal da Empresa no Windows.

![Captura de ecrã dos atalhos disponíveis no Portal da Empresa do Windows](./media/company-portal-app/company-portal-app-01.png)

## <a name="user-self-service-device-actions-from-the-company-portal"></a>User self-service device actions from the Company Portal

Users can perform actions on their local or remote devices via the Company Portal app or Website. The actions that a user can perform varies based on device platform and configuration. In all cases, the remote device actions can only be performed by device’s Primary User.
- **Retire** – Removes the device from Intune Management. In the company portal app and website, this shows as **Remove**.
- **Wipe** – This action initiates a device reset. In the company portal website this is shown as **Reset**, or **Factory Reset** in the iOS Company Portal App.
- **Rename** – This action changes the device name that the user can see in the Company Portal. It does not change the local device name, only the listing in the Company Portal.
- **Sync** – This action initiates a device check-in with the Intune service. This shows as **Check Status** in the Company Portal.
- **Remote Lock** – This locks the device, requiring a PIN to unlock it.
- **Reset Passcode** – This action is used to reset device passcode. On iOS devices the passcode will be removed and the end user will be required to enter a new code in settings. On supported Android devices, a new passcode is generated by Intune and temporarily displayed in the Company Portal.
- **Key Recovery** – This action is used to recover a personal recovery key for encrypted macOS devices from the Company Portal website. 

### <a name="self-service-actions"></a>Self Service Actions

Some platforms and configurations do not allow self-service device actions. This table below provides further details about self service actions:

|  | Windows 10<sup>(3)</sup> | iOS/iPadOS<sup>(3)</sup> | MacOS<sup>(3)</sup> | Android<sup>(3)</sup> |
|----------------------|--------------------------|-------------------|-----------------------------------|-------------------------|
| Extinguir | Available<sup>(1)</sup> | Disponível | Disponível | Available<sup>(7)</sup> |
| Eliminação | Disponível | Available<sup>(5)</sup> | NA | Available<sup>(7)</sup> |
| Rename<sup>(4)</sup> | Disponível | Disponível | Disponível | Disponível |
| Sync | Disponível | Disponível | Disponível | Disponível |
| Bloqueio Remoto | Windows Phone only | Disponível | Disponível | Disponível |
| Reset Passcode | Windows Phone only | Available<sup>(8)</sup> | NA | Available<sup>(6)</sup> |
| Key Recovery | NA | NA | Available<sup>(2)</sup> | NA |

<sup>(1)</sup> **Retire** is always blocked on Azure AD Joined Windows devices.<br>
<sup>(2)</sup> **Key Recovery** for MacOS is only available via the Web Portal.<br>
<sup>(3)</sup> All remote actions are disabled if using a Device Enrollment Manager enrollment.<br>
<sup>(4)</sup> **Rename** only changes the device name in the Company Portal app or Web Portal, not on the device.<br>
<sup>(5)</sup> **Wipe** is not available on User Enrolled iOS devices.<br>
<sup>(6)</sup> **Reset Passcode** is not supported on some Android and Android Enterprise configurations. For more information, see [Reset or remove a device passcode in Intune](../remote-actions/device-passcode-reset.md).<br>
<sup>(7)</sup> **Retire** and **Wipe** are not available on Android Enterprise Device Owner scenarios (COPE, COBO, COSU).<br> 
<sup>(8)</sup> **Reset Passcode** is not supported on User Enrolled iOS devices.

## <a name="next-steps"></a>Próximos passos

- [Adicionar manualmente a aplicação Portal da Empresa do Windows 10 através do Microsoft Intune](company-portal-app.md)
