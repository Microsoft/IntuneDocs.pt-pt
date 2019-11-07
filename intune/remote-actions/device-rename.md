---
title: Renomear um dispositivo com Microsoft Intune-Azure | Microsoft Docs
description: Renomear um dispositivo usando Microsoft Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/05/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0f5ee9a0fe27c3cf9de758fd7155dbd127fb1e5e
ms.sourcegitcommit: 28622c5455adfbce25a404de4d0437fa2b5370be
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/07/2019
ms.locfileid: "73712216"
---
# <a name="rename-a-device-in-intune"></a>Renomear um dispositivo no Intune

A ação **renomear dispositivo** permite renomear um dispositivo registrado no Intune. O nome do dispositivo é alterado no Intune e no dispositivo.

Você pode renomear os seguintes tipos de dispositivos:
- Janelas de propriedade corporativa 
- supervisionado do iOS
- MacOS 10 de propriedade corporativa

No momento, esse recurso não dá suporte à renomeação de dispositivos Windows do Azure AD híbridos.

## <a name="rename-a-device"></a>Renomear um dispositivo

1. Entre no centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
3. Escolha **dispositivos** > **todos os dispositivos** > escolha um dispositivo > **mais** > **renomear dispositivo**.
4. Na folha **renomear dispositivo** , digite o novo nome na caixa de texto. Você pode usar letras, números e hifens. O nome deve conter pelo menos uma letra ou hífen.
5. Se você quiser reiniciar o dispositivo depois de renomeá-lo, escolha **Sim** avançar para **reiniciar após a renomeação**.
6. Escolha **renomear**.

## <a name="windows-device-rename-rules"></a>Regras de renomeação de dispositivo do Windows
Ao renomear um dispositivo Windows, o novo nome deve seguir estas regras:
- 15 caracteres ou menos (deve ser menor ou igual a 63 bytes, não incluindo nulo à direita)
- Não nulo ou uma cadeia de caracteres vazia
- ASCII permitido: letras (a-z, A-Z), números (0-9) e hifens
- Unicode permitidos: caracteres > = 0x80, deve ser um UTF8 válido, deve ser IDN-mapeável (ou seja, RtlIdnToNameprepUnicode tem sucesso; consulte RFC 3492)
- Os nomes não devem conter apenas números
- Nenhum espaço no nome
- Caracteres não permitidos: {|} ~ [\] ^ ':; < = >? & @! " # $ % ` ( ) + / , . _ *)


## <a name="next-steps"></a>Próximos passos

Para ver o status da ação **renomear** dispositivo, verifique a página **visão geral** do dispositivo.
