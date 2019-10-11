---
title: Configurar o Google Chrome para dispositivos Android usando o Intune
titleSuffix: Microsoft Intune
description: Use as políticas de configuração do Intune com o Google Chrome para dispositivos Android.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/07/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 35f52e80f83426c076ac7925d308daacf4595f88
ms.sourcegitcommit: b1e97211db7cb949eb39be6776b3a11d434fdab0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/10/2019
ms.locfileid: "72251500"
---
# <a name="configure-google-chrome-for-android-devices-using-intune"></a>Configurar o Google Chrome para dispositivos Android usando o Intune 

Você pode usar uma política de configuração de aplicativo do Intune para configurar o Google Chrome para dispositivos Android. As configurações para o aplicativo podem ser aplicadas automaticamente. Por exemplo, você pode definir especificamente os indicadores e as URLs que deseja bloquear ou permitir.

## <a name="prerequisites"></a>Pré-requisitos

- O dispositivo Android Enterprise do usuário deve ser registrado no Intune. Para obter mais informações, consulte [Configurar o registro de dispositivos de perfil de trabalho do Android Enterprise](~/enrollment/android-work-profile-enroll.md).
- O Google Chrome é adicionado como um aplicativo Google Play gerenciado. Para obter mais informações sobre Google Play gerenciados, consulte [conectar sua conta do Intune à sua conta de Google Play gerenciada](~/enrollment/connect-intune-android-enterprise.md).

## <a name="add-the-google-chrome-app-to-intune"></a>Adicionar o aplicativo Google Chrome ao Intune

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. No painel **Intune** , selecione **aplicativos cliente** > **aplicativos** > **Adicionar** e adicionar o aplicativo **Google Play gerenciado** .
3. Vá para Google Play gerenciados, pesquise com o **Google Chrome** e aprove.

    ![Pesquisar e aprovar o Google Chrome](~/apps/media/apps-configure-chrome-android/search.png)

4. Atribua o Google Chrome a um grupo de usuários como um tipo de aplicativo necessário. O Google Chrome será implantado automaticamente quando o dispositivo for registrado no Intune.

Para obter detalhes adicionais sobre como adicionar um aplicativo Google Play gerenciado ao Intune, consulte [aplicativos gerenciados da store Google Play](~/apps/apps-add-android-for-work.md#managed-google-play-store-apps).

## <a name="add-an-app-configuration-policy-for-managed-android-enterprise-devices"></a>Adicionar uma política de configuração de aplicativo para dispositivos Android Enterprise gerenciados

1. No painel [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) , selecione **políticas de configuração de aplicativo** > **Adicionar**.
2. Adicione o nome da política, escolha **dispositivos gerenciados** em tipo de registro de dispositivo e **Android** em plataforma.

    ![Adicionar política de configuração do Google Chrome](~/apps/media/apps-configure-chrome-android/add-policy.png)

3. Clique em **aplicativo associado** e selecione **Google Chrome**.

    ![Selecionar Google Chrome em aplicativo associado](~/apps/media/apps-configure-chrome-android/associated-app.png)

4. Clique em **definições de configuração**, selecione usar o designer de **configuração**e clique em **Adicionar** para selecionar as chaves de configuração.

    ![Adicionar usar o designer de configuração](~/apps/media/apps-configure-chrome-android/configuration.png)

    Veja abaixo o exemplo das configurações comuns:
    - **Bloquear o acesso a uma lista de URLs**: `["*"]`
    - **Permitir acesso a uma lista de URLs**: `["baidu.com", "yahoo.com", "chrome://*"]`
    - **Indicadores gerenciados**: `[{"toplevel_name": "My managed bookmarks folder"  },  {"url": "baidu.com",   "name": "Baidu"},  {"url": "youtube.com", "name": "Youtube"},  {"name": "Chrome links",  "children": [{"url": "chromium.org", "name": "Chromium"},    {"url": "dev.chromium.org", "name": "Chromium Developers"}]}]`
    - **Disponibilidade do modo de Incognito**: `Incognito mode disabled`

    Depois que as definições de configuração forem adicionadas usando o designer de configuração, elas serão listadas em uma tabela. 

    ![Configurações comuns](~/apps/media/apps-configure-chrome-android/common-settings.png)

    As configurações acima criam indicadores e permitem o acesso a todos os sites, exceto `baidu.com`, `yahoo.com` e `chrome://`.

5. Clique em **OK** e **adicione** para adicionar sua política de configuração ao Intune.
6. Atribua essa política de configuração a um grupo de usuários. Para obter mais informações, consulte [atribuir aplicativos a grupos com Microsoft Intune](~/apps/apps-deploy.md). 

## <a name="verify-the-device-settings"></a>Verificar as configurações do dispositivo

Depois que o dispositivo Android for registrado no Android Enterprise, o aplicativo Google Chrome gerenciado com o ícone de portfólio será implantado automaticamente.
 
   <img alt="Managed Google Chrome with the portfolio icon" src="~/apps/media/apps-configure-chrome-android/chrome-icon.png" width="350">

Inicie o Google Chrome e você encontrará as configurações aplicadas.

   Indicadores<br>
   <img alt="Bookmarks" src="~/apps/media/apps-configure-chrome-android/bookmarks.png" width="350">

   URL bloqueada:<br>
   <img alt="Blocked URL" src="~/apps/media/apps-configure-chrome-android/blocked-url.png" width="350">

   Permitir URL:<br>
   <img alt="Allow URL" src="~/apps/media/apps-configure-chrome-android/allowed-url.png" width="350">

   Guia Incognito:<br>
   <img alt="Incognito tab" src="~/apps/media/apps-configure-chrome-android/incognito-tab.png" width="350">

## <a name="troubleshooting"></a>Resolução de problemas

1. Verifique o portal do Intune para monitorar o status de implantação da política.

    ![Monitorar o status de implantação da política](~/apps/media/apps-configure-chrome-android/monitor-status.png)

2. Inicie o Google Chrome e visite **Chrome://Policy**. Podemos confirmar se as configurações foram aplicadas com êxito.

    ![Confirmar que as configurações foram aplicadas com êxito](~/apps/media/apps-configure-chrome-android/confirm.png)

## <a name="additional-information"></a>Informação adicional

- [Adicionar políticas de configuração de aplicativo para dispositivos Android Enterprise gerenciados](~/app-configuration-policies-use-android.md)
- [Lista de políticas do Chrome Enterprise](https://cloud.google.com/docs/chrome-enterprise/policies/)

## <a name="next-steps"></a>Passos seguintes

- Para obter mais informações sobre dispositivos Android Enterprise totalmente gerenciados, consulte [Configurar o registro do Intune do Android Enterprise gerenciar totalmente os dispositivos](~/enrollment/android-fully-managed-enroll.md).
