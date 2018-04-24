---
title: Como criar perfis VPN personalizados com o Microsoft Intune
titleSuffix: ''
description: Utilize configurações personalizadas para criar perfis de VPN no Intune.
keywords: ''
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/6/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ec9b959d086051985287a62f7d10fe8d4cbad7e9
ms.sourcegitcommit: 28ed8902a11500b195fff839d59b90c16af6e743
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/29/2018
---
# <a name="how-to-create-custom-vpn-profiles-in-microsoft-intune"></a>Como criar perfis VPN no Microsoft Intune

Pode utilizar políticas de configuração personalizada do Intune para criar perfis VPN para as seguintes plataformas:

* Android 4 e posterior
* Dispositivos inscritos com Windows 8.1 e posterior
* Windows Phone 8.1 e posterior
* Computadores inscritos com o Windows 10 
* Windows 10 Mobile

Este tipo de política pode ser útil quando as políticas de VPN do Intune padrão não têm as definições que pretende utilizar.

## <a name="to-create-a-custom-configuration-policy"></a>Para criar uma política de configuração personalizada:

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços** > **Intune**. O Intune encontra-se na secção **Monitorização + Gestão**.
3. No painel **Intune**, selecione **Configuração do dispositivo**.
2. No painel **Configuração do dispositivo**, na secção **Gerir**, selecione **Perfis**.
5. No painel Perfis, selecione **Criar perfil**.
6. No painel **Criar perfil**, introduza um **Nome** e uma **Descrição** para o perfil de VPN.
7. Na lista pendente **Plataforma**, selecione a plataforma do dispositivo à qual pretende aplicar as definições de VPN. Atualmente, pode escolher uma das seguintes plataformas para as definições personalizadas dos dispositivos:
    - **Android**
    - **Android for Work**
    - **iOS** (configurado através de um ficheiro que exportou a partir do Apple Configurator).
    - **macOS** (configurado através de um ficheiro que exportou a partir do Apple Configurator).
    - **Windows Phone 8.1**
    - **Windows 8.1 e posterior**
    - **Windows 10 e posterior**
6. Na lista pendente **Tipo de perfil**, escolha **Personalizado**.
7. No painel **Definições OMA-URI Personalizadas**, para cada definição URI que pretende especificar, selecione **Adicionar**, forneça as informações pedidas e, em seguida, selecione **OK**. Segue-se um exemplo:

   ![Caixa de diálogo de configuração personalizada de perfil VPN](./media/Intune_Add_VPN_URI.png)

4.  Após introduzir todas as definições URI de que precisa, selecione **OK** e, em seguida, no painel **Criar perfil**, selecione **Criar**.

O perfil será criado e apresentado no painel Lista de perfis.
Se quiser continuar e atribuir este perfil a grupos, veja [Como atribuir perfis de dispositivo](device-profile-assign.md).




