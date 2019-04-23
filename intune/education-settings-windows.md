---
title: Definições de educação do Windows 10 no Microsoft Intune – Azure | Documentos da Microsoft
description: Ver uma lista de todas as definições de educação para dispositivos Windows 10. Utilize estas definições no perfil de configuração de dispositivo com a fazer uma aplicação de teste, escolha como os utilizadores ou os estudantes iniciam sessão no monitor de tela durante o teste e mais no Intune.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 01/22/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 6f4de4bd-3dde-4a8d-8e22-46c5d06c3eea
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 206bc3276f3c175fe61852f235c722b835ad60b4
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "61513278"
---
# <a name="configure-the-take-a-test-app-on-windows-10-devices-using-intune"></a>Configurar o aplicação fazer um teste em dispositivos Windows 10 com o Intune

Este artigo mostra-lhe todo o Microsoft Intune education aplicação fazer um teste definições que pode configurar em dispositivos com Windows 10 e posterior. Utilizar esta aplicação, os estudantes podem iniciar sessão num dispositivo e fazer um teste.

Estas definições são adicionadas a um perfil de configuração do dispositivo e, em seguida, atribuídas ou implementadas nos seus dispositivos com o Microsoft Intune.

[Aplicação fazer um teste no Intune](education-settings-configure.md) fornece mais informações sobre esta funcionalidade.

## <a name="before-you-begin"></a>Antes de começar

[Criar um perfil de configuração do dispositivo](education-settings-configure.md#create-a-device-profile).

## <a name="take-a-test-settings"></a>Fazer um teste definições

- **Tipo de conta**: Escolha como os utilizadores iniciam sessão para o teste. As opções são:
  - Conta do Azure AD
  - Conta de domínio
  - Conta local
- **Nome da conta de utilizador**: Introduza o utilizador nome da conta utilizada com a fazer uma aplicação de teste. Pode introduzir contas no seguinte formato:
  - `user@contoso.com`
  - `domain\username`
  - `user@contoso.com`
  - `computerName\username`
- **URL de avaliação**: Introduza o URL de teste que quer que os usuários tirem. Para obter mais informações sobre como obter o URL, consulte a [tirar uma documentação de teste](https://docs.microsoft.com/education/windows/take-tests-in-windows-10).
- **Monitorização de ecrãs**: Escolher **permitir** para monitorizar a atividade do ecrã enquanto os utilizadores estão a fazer um teste. **Não configurado** impede a monitorização do ecrã durante o teste.
- **Sugestão de texto**: Escolher **permitir** para teste takers podem ver sugestões de texto. **Não configurado** bloqueia sugestões de texto enquanto os utilizadores estão a fazer um teste.

## <a name="next-steps"></a>Passos Seguintes

O perfil é criado, mas ele pode não fazer nada ainda. Não se esqueça [atribuir o perfil](device-profile-assign.md), e [monitorizar o estado](device-profile-monitor.md).
