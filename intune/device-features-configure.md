---
title: "Configurar as definições das funcionalidades dos dispositivos no Intune"
titleSuffix: Azure portal
description: Saiba como utilizar o Intune para configurar funcionalidades nos dispositivos que gere."
keywords: 
author: vhorne
ms.author: victorh
manager: angrobe
ms.date: 12/7/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 42f9b104-c1f6-4dfc-8aa4-1d33e1eaf61f
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ea280ac6858485aa4e3d64d11835f002c5bb35ca
ms.sourcegitcommit: 3b397b1dcb780e2f82a3d8fba693773f1a9fcde1
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/12/2017
---
# <a name="how-to-configure-device-feature-settings-in-microsoft-intune"></a>Como configurar as definições das funcionalidades dos dispositivos no Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

As restrições do dispositivo permitem-lhe controlar as funcionalidades nos dispositivos iOS e macOS como configurações de dispositivos partilhados, notificações e AirPrint.

Utilize as informações deste tópico para conhecer as noções básicas sobre como configurar perfis de funcionalidades de dispositivos e, em seguida, leia os tópicos de cada plataforma para saber mais sobre as especificações dos dispositivos.

## <a name="create-a-device-profile-containing-device-restriction-settings"></a>Criar um perfil de dispositivo com as definições de restrição de dispositivos

1. Inicie sessão no portal do Azure.
2. Escolha **Mais Serviços** > **Monitorização + Gestão** > **Intune**.
3. No painel **Intune**, escolha **Configuração do dispositivo**.
2. No painel **Configuração do Dispositivo**, escolha **Gerir** > **Perfis**.
3. No painel de perfis, escolha **Criar Perfil**.
4. No painel **Criar Perfil**, introduza um **Nome** e uma **Descrição** para o perfil de funcionalidades de dispositivos.
5. Na lista pendente **Plataforma**, selecione a plataforma do dispositivo à qual pretende aplicar as definições. Atualmente, pode escolher uma das seguintes plataformas para as funcionalidades de dispositivos:
    - **iOS**
    - **macOS**
6. Na lista pendente **Tipo de perfil**,selecione **Funcionalidades de dispositivos**. 
7. As definições que pode configurar diferem consoante a plataforma que escolheu. Aceda a um dos seguintes tópicos para definições detalhadas para cada plataforma:
    - [Definições do AirPrint para iOS e MacOS](air-print-settings-ios-macos.md)
    - [Definições do AirPlay para iOS](airplay-settings-ios.md)
    - [Definições de esquema do ecrã principal para iOS](home-screen-settings-ios.md)
    - [Definições de notificação das aplicações para iOS](app-notification-settings-ios.md)
    - [Definições de configuração de dispositivos partilhados para iOS](shared-device-settings-ios.md)
    - [Configurar o Intune para o Início de Sessão Único em dispositivos iOS](sso-ios.md)
    - [Definições de filtros de conteúdo Web para iOS](web-content-filter-settings-ios.md)

8. Quando tiver terminado, volte ao painel **Criar Perfil** e clique em **Criar**.

O perfil é criado e apresentado no painel da lista de perfis.
Se quiser continuar e atribuir este perfil a grupos, veja [Como atribuir perfis de dispositivo](device-profile-assign.md).



