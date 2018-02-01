---
title: Como criar perfis VPN personalizados com o Microsoft Intune
titleSuffix: Azure portal
description: "Utilize configurações personalizadas para criar perfis de VPN no Intune."
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 06/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4c0bd439-3b58-420b-9a9a-282886986786
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 70af9ce41efa7f52987e1103b89493b4cf200091
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/25/2018
---
# <a name="how-to-create-custom-vpn-profiles-in-microsoft-intune"></a>Como criar perfis VPN no Microsoft Intune

## <a name="create-a-custom-configuration"></a>Criar uma configuração personalizada
Pode utilizar políticas de configuração personalizada do Intune para criar perfis VPN para:

* Dispositivos a executar o Android 4 e posterior
* Dispositivos inscritos com Windows 8.1 e posterior
* Dispositivos a executar o Windows Phone 8.1 e posterior
* Computadores inscritos com o Windows 10 
* Dispositivos com o Windows 10 Mobile

Este tipo de política pode ser útil quando as políticas de VPN do Intune padrão não contêm as definições que pretende utilizar.

## <a name="to-create-a-custom-configuration-policy"></a>Para criar uma política de configuração personalizada:

1. Inicie sessão no portal do Azure.
2. Escolha **Mais Serviços** > **Monitorização + Gestão** > **Intune**.
3. No painel **Intune**, escolha **Configuração do dispositivo**.
4. No painel **Configuração do Dispositivo**, escolha **Gerir** > **Perfis**.
5. No painel de perfis, escolha **Criar Perfil**.
6. No painel **Criar Perfil**, introduza um **Nome** e uma **Descrição** para o perfil de VPN.
7. Na lista pendente **Plataforma**, selecione a plataforma do dispositivo à qual pretende aplicar as definições de VPN. Atualmente, pode escolher uma das seguintes plataformas para as definições personalizadas dos dispositivos:
    - **Android**
    - **iOS** (configurado através de um ficheiro que exportou a partir do Apple Configurator).
    - **macOS** (configurado através de um ficheiro que exportou a partir do Apple Configurator).
    - **Windows Phone 8.1**
    - **Windows 10 e posterior**
6. Na lista pendente **Tipo de perfil**, escolha **Personalizado**.
7. No painel **Definições OMA-URI Personalizada**, para cada definição URI que pretende especificar, escolha **Adicionar**, indique as informações pedidas e, em seguida, escolha **OK**. Segue-se um exemplo:

   ![Caixa de diálogo de configuração personalizada de perfil VPN](./media/Intune_Add_VPN_URI.png)

4.  Após introduzir todas as definições URI de que precisa, escolha **OK** e, em seguida, no painel **Criar Perfil**, escolha **Criar**.

O perfil será criado e é apresentado no painel da lista de perfis.
Se quiser continuar e atribuir este perfil a grupos, veja [Como atribuir perfis de dispositivo](device-profile-assign.md).




