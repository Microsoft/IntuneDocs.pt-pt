---
title: Configurar definições de proteção de ponto final no Microsoft Intune – Azure | Microsoft Docs
description: Crie definições de proteção de ponto final ao criar um perfil de dispositivo com o Windows 10 ou macOS no Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 5/17/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
mr.reviewer: karthib
ms.openlocfilehash: c13c5d71d1ff631d7a3c84cd3f62037569757917
ms.sourcegitcommit: bc5e4dff18f5f9b79077a888f8a58dcc490708c0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/21/2019
ms.locfileid: "65975768"
---
# <a name="add-endpoint-protection-settings-in-intune"></a>Adicionar definições de proteção de ponto final no Intune

Com o Intune, pode utilizar perfis de configuração de dispositivos para gerir recursos de segurança do endpoint protection comuns em dispositivos, incluindo:
- Firewall 
- BitLocker
- Permitir e bloquear aplicações  
- O Windows Defender e encriptação

Por exemplo, pode criar um perfil de proteção de ponto final que apenas permita aos utilizadores do macOS instalarem aplicações a partir da Mac App Store. Em alternativa, ative o Windows SmartScreen ao executar aplicações em dispositivos com o Windows 10.

Antes de criar um perfil, reveja os artigos seguintes esse detalhe que as definições de proteção de ponto final Intune podem gerir para cada plataforma suportada: 
   - [Definições do macOS](endpoint-protection-macos.md)
   - [Definições do Windows 10](endpoint-protection-windows-10.md)

## <a name="create-a-device-profile-containing-endpoint-protection-settings"></a>Criar um perfil de dispositivo com as definições de proteção de ponto final

1. Inicie sessão no [Intune](https://go.microsoft.com/fwlink/?linkid=20909).
3. Selecione **Configuração do dispositivo** > **Perfis** > **Criar perfil**.
4. Introduza um **Nome** e uma **Descrição** para o perfil de proteção de ponto final.
5. Na lista pendente **Plataforma**, selecione a plataforma do dispositivo à qual pretende aplicar as definições personalizadas. Atualmente, pode escolher uma das seguintes plataformas para definições de restrição de dispositivos:
   - **macOS**
   - **Windows 10 e posterior**
6. Na lista pendente **Tipo de perfil**, selecione **Proteção de ponto final**. 
7. Consoante a plataforma que escolheu, as definições que pode configurar variam. Consulte:
   - [Definições do macOS](endpoint-protection-macos.md)
   - [Definições do Windows 10](endpoint-protection-windows-10.md)  

8. Depois de configurar as definições aplicáveis, selecione **Create** sobre o **criar perfil** página.

   O perfil é criado e apresentado na página da lista de perfis. Para atribuir este perfil a grupos, veja [atribuir perfis de dispositivo](device-profile-assign.md).


## <a name="next-steps"></a>Passos Seguintes  

Para atribuir um perfil a grupos, veja [atribuir perfis de dispositivo](device-profile-assign.md).
