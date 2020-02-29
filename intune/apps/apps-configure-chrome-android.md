---
title: Configure o Google Chrome para dispositivos Android usando o Intune
titleSuffix: Microsoft Intune
description: Utilize políticas de configuração Intune com o Google Chrome para dispositivos Android.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/28/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 78e0e8560c64a1d6be4fa5e01aa9ce32b8a4c613
ms.sourcegitcommit: 9ee2401a2f01373a962749b0728c22385dbcba6d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/29/2020
ms.locfileid: "78181777"
---
# <a name="configure-google-chrome-for-android-devices-using-intune"></a>Configure o Google Chrome para dispositivos Android usando o Intune 

Pode utilizar uma política de configuração de aplicações Intune para configurar o Google Chrome para dispositivos Android. As definições da aplicação podem ser aplicadas automaticamente. Por exemplo, pode definir especificamente os marcadores e os URLs que gostaria de bloquear ou permitir.

## <a name="prerequisites"></a>Pré-requisitos

- O dispositivo Android Enterprise do utilizador deve ser matriculado no Intune. Para mais informações, consulte [Configurar a inscrição de dispositivos de perfil de trabalho Android Enterprise](~/enrollment/android-work-profile-enroll.md).
- O Google Chrome é adicionado como uma aplicação gerida pelo Google Play. Para obter mais informações sobre o Managed Google Play, consulte [Connect your Intune account to your Managed Google Play account](~/enrollment/connect-intune-android-enterprise.md).

## <a name="add-the-google-chrome-app-to-intune"></a>Adicione a aplicação do Google Chrome ao Intune

1. Inscreva-se no [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selecione **Apps** > **Todas as aplicações** > **Adicionar** e adicionar a aplicação **Managed Google Play.**
3. Vá ao Google Play gerido, procure no **Google Chrome** e aprove.

    ![Pesquisar e aprovar o Google Chrome](~/apps/media/apps-configure-chrome-android/search.png)

4. Atribuir o Google Chrome a um grupo de utilizadores como um tipo de aplicação necessário. O Google Chrome será implantado automaticamente quando o dispositivo estiver matriculado no Intune.

Para mais detalhes sobre a adição de uma aplicação gerida do Google Play ao Intune, consulte [aplicações geridas](~/apps/apps-add-android-for-work.md#managed-google-play-store-apps)da Google Play store .

## <a name="add-app-configuration-for-managed-ae-devices"></a>Adicione a configuração da aplicação para dispositivos AE geridos

1. A partir do centro de administração do [Microsoft Endpoint Manager,](https://go.microsoft.com/fwlink/?linkid=2109431)selecione **Apps** > políticas de **configuração** de apps > **adicionar** > **dispositivos geridos**.
2. Defina os seguintes detalhes:
    - **Nome** – o nome do perfil que é apresentado no portal do Azure.
    - **Descrição** – a descrição do perfil que é apresentada no portal do Azure.
    - Tipo de **inscrição do dispositivo** - Esta definição está definida para **dispositivos geridos**.
    - **Plataforma** - Selecione **Android**.

    ![Adicione a política de configuração do Google Chrome](~/apps/media/apps-configure-chrome-android/add-policy.png)

3. Clique na **aplicação Associada** para exibir o painel de **aplicações associado.** Encontre e selecione **o Google Chrome**. Esta lista contém [aplicações geridas do Google Play que aprovou e sincronizadas com o Intune](~/apps/apps-add-android-for-work.md).

    ![Selecione Google Chrome em app Associated](~/apps/media/apps-configure-chrome-android/associated-app.png)

4. Clique em configurações de **configuração,** selecione Utilize o designer de **configuração**e, em seguida, clique em **Adicionar** para selecionar as teclas de configuração.

    ![Adicionar designer de configuração use](~/apps/media/apps-configure-chrome-android/configuration.png)

    Abaixo está o exemplo das definições comuns:
    - **Bloquear o acesso a uma lista de URLs**: `["*"]`
    - **Permitir o acesso a uma lista de URLs**: `["baidu.com", "youtube.com", "chromium.org", "chrome://*"]`
    - **Marcadores geridos**: `[{"toplevel_name": "My managed bookmarks folder"  },  {"url": "baidu.com",   "name": "Baidu"},  {"url": "youtube.com", "name": "Youtube"},  {"name": "Chrome links",  "children": [{"url": "chromium.org", "name": "Chromium"},    {"url": "dev.chromium.org", "name": "Chromium Developers"}]}]`
    - **Disponibilidade do modo incógnito**: `Incognito mode disabled`

    Uma vez adicionadas as definições de configuração utilizando o designer de configuração, serão listadas numa tabela. 

    ![Definições comuns](~/apps/media/apps-configure-chrome-android/common-settings.png)

    As definições acima criam marcadores e bloqueiam o acesso a todos os URLs exceto `baidu.com`, `yahoo.com`, `chromium.org`e `chrome://`.

5. Clique em **OK** e **Adicione** para adicionar a sua política de configuração ao Intune.
6. Atribuir esta política de configuração a um grupo de utilizadores. Para obter mais informações, veja [Atribuir aplicações a grupos com o Microsoft Intune](~/apps/apps-deploy.md). 

## <a name="verify-the-device-settings"></a>Verifique as definições do dispositivo

Uma vez que o dispositivo Android esteja matriculado no Android Enterprise, a aplicação gerida do Google Chrome com o ícone do portfólio será implementada automaticamente.
 
   <img alt="Managed Google Chrome with the portfolio icon" src="~/apps/media/apps-configure-chrome-android/chrome-icon.png" width="350">

Lance o Google Chrome e encontrará as definições aplicadas.

   Marcadores:<br>
   <img alt="Bookmarks" src="~/apps/media/apps-configure-chrome-android/bookmarks.png" width="350">

   URL bloqueado:<br>
   <img alt="Blocked URL" src="~/apps/media/apps-configure-chrome-android/blocked-url.png" width="350">

   Permitir URL:<br>
   <img alt="Allow URL" src="~/apps/media/apps-configure-chrome-android/allowed-url.png" width="350">

   Separador incógnito:<br>
   <img alt="Incognito tab" src="~/apps/media/apps-configure-chrome-android/incognito-tab.png" width="350">

## <a name="troubleshooting"></a>Resolução de Problemas

1. Verifique o portal Intune para monitorizar o estado de implementação da política.

    ![Monitorizar o estado de implantação da política](~/apps/media/apps-configure-chrome-android/monitor-status.png)

2. Lance o Google Chrome e visite **chrome://policy**. Podemos confirmar se as definições são aplicadas com sucesso.

    ![Confirmar as definições são aplicadas com sucesso](~/apps/media/apps-configure-chrome-android/confirm.png)

## <a name="additional-information"></a>Informações adicionais

- [Adicione políticas de configuração de aplicativos para dispositivos Android Enterprise geridos](~/app-configuration-policies-use-android.md)
- [Lista de políticas da Empresa Chrome](https://cloud.google.com/docs/chrome-enterprise/policies/)

## <a name="next-steps"></a>Próximos passos

- Para obter mais informações sobre dispositivos geridos pelo Android Enterprise, consulte [a inscrição intune do Android Enterprise na sua plena gestão de dispositivos.](~/enrollment/android-fully-managed-enroll.md)
