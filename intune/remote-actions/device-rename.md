---
title: Mude o nome de um dispositivo com microsoft Intune - Azure Microsoft Docs
description: Mude o nome de um dispositivo utilizando o Microsoft Intune.
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
ms.openlocfilehash: 11b339a3e94e60db43e8237d9f3d2c729b48a57d
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/17/2020
ms.locfileid: "77413616"
---
# <a name="rename-a-device-in-intune"></a>Mude o nome de um dispositivo em Intune

A ação do **dispositivo Rename** permite-lhe renomear um dispositivo que está matriculado em Intune. O nome do dispositivo é alterado em Intune e no dispositivo.

Pode renomear os seguintes tipos de dispositivos:
- Windows corporativo 
- iOS/iPadOS supervisionado
- MacOS 10 de propriedade corporativa

Esta funcionalidade não suporta atualmente renomear dispositivos híbridos Azure AD Windows.

## <a name="rename-a-device"></a>Mude o nome de um dispositivo

1. Inscreva-se no [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).
3. Escolha **Dispositivos** > **Todos os dispositivos** > escolha um dispositivo > **Mais** > **Rename**.
4. Na lâmina do **dispositivo Rename,** digite o novo nome na caixa de texto. Pode usar letras, números e hífenes. O nome deve conter pelo menos uma letra ou hífen.
5. Se pretender reiniciar o dispositivo depois de o renomear, escolha **Sim** ao lado do **Restart após o renome .**
6. Escolha **Mudar o nome**.

## <a name="windows-device-rename-rules"></a>Regras de renome do dispositivo Windows
Ao renomear um dispositivo Windows, o novo nome deve seguir estas regras:
- 15 caracteres ou menos (deve ser inferior ou igual a 63 bytes, sem incluir o nulo de rasto)
- Não é nulo ou uma corda vazia
- ASCII permitido: Letras (a-z, A-Z), números (0-9) e hífenes
- Unicode permitido: caracteres >= 0x80, devem ser uTF8 válidos, devem ser idn-mappable (isto é, RtlIdnToNameprepUnicode sucede; ver RFC 3492)
- Os nomes não devem conter apenas números
- Sem espaços no nome
- Caracteres proibidos: { ~ ~ [ ] [ ] [ ] < = > E @ ! " # $ % ` ( ) + / , . _ *)


## <a name="next-steps"></a>Próximos passos

Para ver o estado da ação do dispositivo **Renomear,** verifique a página **'Visão Geral'** do dispositivo.
