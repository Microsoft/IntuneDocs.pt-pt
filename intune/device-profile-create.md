---
title: "Criar perfis de configuração de dispositivos do Intune | Pré-visualização do Azure no Intune"
titleSuffix: Intune Azure preview
description: "Pré-visualização do Azure no Intune: saiba como criar perfis de configuração de dispositivos no Intune."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 03/16/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d98aceff-eb35-4e3e-8e40-5f300e7335cc
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: a719b3f53076a55f1e888a9ddf8e98c7074dd25f
ms.contentlocale: pt-pt
ms.lasthandoff: 05/23/2017


---

# <a name="how-to-create-device-configuration-profiles-in-microsoft-intune"></a>Como criar perfis de configuração de dispositivos no Microsoft Intune

[!INCLUDE[azure_preview](./includes/azure_preview.md)]


1. Inicie sessão no portal do Azure.
2. Escolha **Mais Serviços** > **Monitorização + Gestão** > **Intune**.
3. No painel **Intune**, escolha **Configurar dispositivos**.
2. No painel **Configuração do Dispositivo**, escolha **Gerir** > **Perfis**.
2. No painel que mostra a lista de perfis, escolha **Criar Perfil**.
3. No painel **Criar Perfil**, especifique o seguinte:
    - **Nome** – Introduza um nome descritivo para o novo perfil.
    - **Descrição** – Introduza uma descrição opcional para o perfil.
    - **Plataforma** – Selecione o tipo de plataforma para o perfil que quer criar.
    - **Tipo de perfil** – Selecione o tipo de perfil que quer criar. A lista de tipos disponíveis varia consoante a plataforma que escolheu.
    - **Definições** – Veja os tópicos seguintes para obter mais informações sobre as definições para cada tipo de perfil:
        -  [Definições das funcionalidades de dispositivos](device-features-configure.md)
        -  [Definições de restrição de dispositivos](device-restrictions-configure.md)
        -  [Definições de e-mail](email-settings-configure.md)
        -  [Definições de VPN](vpn-settings-configure.md)
        -  [Definições de Wi-Fi](wi-fi-settings-configure.md)
        -  [Definições de atualização da edição do Windows 10](edition-upgrade-configure-windows-10.md)
        -  [Definições de certificado](certificates-configure.md)
        -  [Definições do Windows Information Protection](windows-information-protection-configure.md)
        -  [Definições de educação](education-settings-configure.md)
        -  [Definições personalizadas](custom-settings-configure.md)

    ![Criar perfil de dispositivo](./media/create-device-profile.png)
4. Quando tiver terminado de configurar as definições, no painel **Criar Perfil**, escolha **Criar**.

O perfil será criado e é apresentado no painel da lista de perfis.
Se quiser continuar e atribuir este perfil a grupos, veja [Como atribuir perfis de dispositivo](device-profile-assign.md).


### <a name="next-steps"></a>Passos seguintes
Para obter mais informações sobre como atribuir perfis de dispositivo, veja [Como atribuir perfis de dispositivo com o Microsoft Intune](device-profile-assign.md).

