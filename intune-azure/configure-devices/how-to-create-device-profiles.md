---
title: "Criar políticas de configuração de dispositivos do Intune | Pré-visualização do Azure no Intune | Documentos da Microsoft"
description: "Pré-visualização do Azure no Intune: saiba como criar perfis de configuração de dispositivos no Intune."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 01/08/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d98aceff-eb35-4e3e-8e40-5f300e7335cc
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 89afae81076d563f4ebba289f8fa82eaea6ab234
ms.openlocfilehash: 6c6ac8112a6b6413df635607a24d0d06466c0b88


---

# <a name="how-to-create-device-configuration-profiles"></a>Como criar perfis de configuração de dispositivos 

[!INCLUDE[azure_preview](../includes/azure_preview.md)]


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
        -  [Definições de restrição de dispositivos](/intune-azure/configure-devices/how-to-configure-device-restrictions)
        -  [Definições de e-mail](/intune-azure/configure-devices/how-to-configure-email-settings)
        -  [Definições de VPN](/intune-azure/configure-devices/how-to-configure-vpn-settings)
        -  [Definições de Wi-Fi](/intune-azure/configure-devices/how-to-configure-wi-fi-settings)
        -  [Definições de atualização da edição do Windows 10](/intune-azure/configure-devices/how-to-configure-windows-10-edition-upgrade)
        -  [Definições de certificado](/intune-azure/configure-devices/how-to-configure-certificates)
        -  [Definições do Windows Information Protection](/intune-azure/configure-devices/how-to-configure-windows-information-protection)
        -  [Definições de educação](/intune-azure/configure-devices/education-settings-for-ios.md)
        -  [Definições personalizadas](/intune-azure/configure-devices/how-to-configure-custom-settings)

    ![Criar perfil de dispositivo](./media/create-device-profile.png)
4. Quando tiver terminado de configurar as definições, no painel **Criar Perfil**, escolha **Criar**.

O perfil será criado e é apresentado no painel da lista de perfis.
Se quiser continuar e atribuir este perfil a grupos, veja [Como atribuir perfis de dispositivo](how-to-assign-device-profiles.md).


### <a name="next-steps"></a>Próximos passos
Para obter mais informações sobre como atribuir perfis de dispositivo, veja [Como atribuir perfis de dispositivo com o Microsoft Intune](/intune-azure/configure-devices/how-to-assign-device-profiles).



<!--HONumber=Feb17_HO1-->


