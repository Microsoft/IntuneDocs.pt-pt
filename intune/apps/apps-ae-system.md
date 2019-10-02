---
title: Adicionar aplicativos do Android Enterprise System ao Microsoft Intune
titleSuffix: ''
description: Saiba como adicionar aplicativos do sistema corporativo ao Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: priyar
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7ffc99b34016eba6511f63d1df2184abc3cae858
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71731252"
---
# <a name="add-android-enterprise-system-apps-to-microsoft-intune"></a>Adicionar aplicativos do Android Enterprise System ao Microsoft Intune

Antes de atribuir uma aplicação a um dispositivo ou grupo de utilizadores, tem de primeiro adicionar a aplicação ao Microsoft Intune. Os aplicativos do sistema têm suporte em dispositivos Android Enterprise. Você pode habilitar um aplicativo de sistema para [dispositivos Android Enterprise dedicados](../enrollment/android-kiosk-enroll.md) ou [dispositivos totalmente gerenciados](../enrollment/android-fully-managed-enroll.md).

## <a name="add-the-app"></a>Adicionar a aplicação

Você pode adicionar um aplicativo Android Enterprise System ao Intune por meio do portal do Azure fazendo o seguinte:

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. No painel **Intune**, selecione **Aplicações do cliente** > **Aplicações** > **Adicionar**.
3. No painel **Adicionar aplicativo** , sob os **outros** tipos disponíveis, selecione **aplicativo Android Enterprise System**.
4. Para configurar as informações do aplicativo, selecione **Configurar**e forneça as seguintes informações:
    - **Nome do aplicativo**: Insira o nome do aplicativo.
    - **Publicador**: Introduza o nome do publicador da aplicação.  
    - **Nome do pacote**: Insira um nome de pacote. O Intune validará se o nome do pacote é válido.
5. Selecione **OK**.
6. Selecione **Adicionar**.

A aplicação criada é apresentada na lista de aplicações, onde a pode atribuir aos grupos que selecionar. 

Os aplicativos do Android Enterprise System habilitarão ou desabilitarão aplicativos que já fazem parte da plataforma. Para habilitar um aplicativo, atribua o aplicativo do sistema conforme **necessário**. Para desabilitar um aplicativo, atribua o aplicativo do sistema como **desinstalação**. Os aplicativos do sistema não podem ser atribuídos como disponíveis para um usuário.

## <a name="next-steps"></a>Passos seguintes

- [Atribuir aplicações a grupos](apps-deploy.md)
