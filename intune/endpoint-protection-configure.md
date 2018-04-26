---
title: Configurar definições de proteção de ponto final no Microsoft Intune – Azure | Microsoft Docs
description: Crie definições de proteção de ponto final ao criar um perfil de dispositivo com o Windows 10 ou macOS no Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/27/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: b960b837cef5941fac829eeb878eb520b0274fba
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/16/2018
---
# <a name="add-endpoint-protection-settings-in-intune"></a>Adicionar definições de proteção de ponto final no Intune

A proteção de ponto final permite-lhe controlar as diferentes funcionalidades de segurança nos seus dispositivos, incluindo a firewall, o BitLocker, permitir e bloquear aplicações, o Windows Defender, encriptação e mais. Pode configurar estas definições no Microsoft Intune através de perfis de dispositivo.

Por exemplo, pode criar um perfil de proteção de ponto final que apenas permita aos utilizadores do macOS instalarem aplicações a partir da Mac App Store. Em alternativa, ative o Windows SmartScreen ao executar aplicações em dispositivos com o Windows 10.

Este artigo mostra-lhe como criar um perfil. Em seguida, selecione a sua plataforma de dispositivo para obter mais detalhes sobre as definições disponíveis.

## <a name="create-a-device-profile-containing-endpoint-protection-settings"></a>Criar um perfil de dispositivo com as definições de proteção de ponto final

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços**, filtre por **Intune** e selecione **Microsoft Intune**.
3. Selecione **Configuração do dispositivo** > **Perfis** > **Criar perfil**.
4. Introduza um **Nome** e uma **Descrição** para o perfil de proteção de ponto final.
5. Na lista pendente **Plataforma**, selecione a plataforma do dispositivo à qual pretende aplicar as definições personalizadas. Atualmente, pode escolher uma das seguintes plataformas para definições de restrição de dispositivos:
   - **macOS**
   - **Windows 10 e posterior**
6. Na lista pendente **Tipo de perfil**, selecione **Proteção de ponto final**. 
7. Consoante a plataforma que escolheu, as definições que pode configurar variam. Aceda a um dos seguintes tópicos para definições detalhadas para cada plataforma:
   - [Definições do macOS](endpoint-protection-macos.md)
   - [Definições do Windows 10](endpoint-protection-windows-10.md)
8. Quando terminar, regresse à página **Criar perfil** e clique em **Criar**.

O perfil é criado e apresentado na página da lista de perfis. Para atribuir este perfil a grupos, veja [atribuir perfis de dispositivo](device-profile-assign.md).

## <a name="next-steps"></a>Próximos passos
Para atribuir um perfil a grupos, veja [atribuir perfis de dispositivo](device-profile-assign.md).