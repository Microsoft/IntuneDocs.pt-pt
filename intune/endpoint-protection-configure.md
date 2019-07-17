---
title: Configurar definições de proteção de ponto final no Microsoft Intune – Azure | Microsoft Docs
description: Crie definições de proteção de ponto final ao criar um perfil de dispositivo com o Windows 10 ou macOS no Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 5/17/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
mr.reviewer: karthib
ms.openlocfilehash: 1a5cd898545bae51395352d5cf1e7b1ee9bd22dd
ms.sourcegitcommit: 7c251948811b8b817e9fe590b77f23aed95b2d4e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/15/2019
ms.locfileid: "67883254"
---
# <a name="add-endpoint-protection-settings-in-intune"></a>Adicionar definições de proteção de ponto final no Intune

Com o Intune, você pode usar perfis de configuração de dispositivo para gerenciar recursos comuns de segurança do Endpoint Protection em dispositivos, incluindo:
- Firewall 
- BitLocker
- Permitindo e bloqueando aplicativos  
- Windows Defender e criptografia

Por exemplo, pode criar um perfil de proteção de ponto final que apenas permita aos utilizadores do macOS instalarem aplicações a partir da Mac App Store. Em alternativa, ative o Windows SmartScreen ao executar aplicações em dispositivos com o Windows 10.

Antes de criar um perfil, examine os seguintes artigos que detalham as configurações do Endpoint Protection que o Intune pode gerenciar para cada plataforma com suporte: 
- [Definições do macOS](endpoint-protection-macos.md)
- [Definições do Windows 10](endpoint-protection-windows-10.md)

## <a name="create-a-device-profile-containing-endpoint-protection-settings"></a>Criar um perfil de dispositivo com as definições de proteção de ponto final

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. Selecione **Configuração do dispositivo** > **Perfis** > **Criar perfil**.
4. Introduza um **Nome** e uma **Descrição** para o perfil de proteção de ponto final.
5. Na lista pendente **Plataforma**, selecione a plataforma do dispositivo à qual pretende aplicar as definições personalizadas. Atualmente, pode escolher uma das seguintes plataformas para definições de restrição de dispositivos:
   - **macOS**
   - **Windows 10 e posterior**
6. Na lista pendente **Tipo de perfil**, selecione **Proteção de ponto final**. 
7. Consoante a plataforma que escolheu, as definições que pode configurar variam. Consulte:
   - [Definições do macOS](endpoint-protection-macos.md)
   - [Definições do Windows 10](endpoint-protection-windows-10.md)  

8. Depois de definir as configurações aplicáveis, selecione **criar** na página **Criar perfil** .

   O perfil é criado e apresentado na página da lista de perfis. Para atribuir este perfil a grupos, veja [atribuir perfis de dispositivo](device-profile-assign.md).


## <a name="next-steps"></a>Passos Seguintes  

Para atribuir um perfil a grupos, veja [atribuir perfis de dispositivo](device-profile-assign.md).
