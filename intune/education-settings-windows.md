---
title: Configurações de educação do Windows 10 no Microsoft Intune – Azure | Microsoft Docs
description: Consulte uma lista de todas as configurações de educação para dispositivos Windows 10. Use essas configurações em um perfil de configuração de dispositivo com o aplicativo fazer um teste, escolha como os usuários ou alunos entram, monitore a tela durante o teste e muito mais no Intune.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 01/22/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 6f4de4bd-3dde-4a8d-8e22-46c5d06c3eea
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d5c78f72e7ffc580cce6cfec7237a3efe3ceb3e5
ms.sourcegitcommit: fd2499df5123758ecb093b4cdd486e35f713b040
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/16/2019
ms.locfileid: "68230104"
---
# <a name="configure-the-take-a-test-app-on-windows-10-devices-using-intune"></a>Configurar o aplicativo fazer um teste em dispositivos Windows 10 usando o Intune

Este artigo mostra todas as configurações da educação de Microsoft Intune fazer um teste de aplicativo que você pode configurar em dispositivos que executam o Windows 10 e posterior. Usando esse aplicativo, os alunos podem entrar em um dispositivo e fazer um teste.

Essas configurações são adicionadas a um perfil de configuração de dispositivo e, em seguida, atribuídas ou implantadas em seus dispositivos usando Microsoft Intune.

[Fazer um aplicativo de teste no Intune](education-settings-configure.md) fornece mais informações sobre esse recurso.

## <a name="before-you-begin"></a>Antes de começar

[Criar um perfil de configuração do dispositivo](education-settings-configure.md#create-a-device-profile).

## <a name="take-a-test-settings"></a>Fazer uma configuração de teste  

- **Tipo de conta**: Escolha como os usuários entram no teste. As opções são:
  - Conta do Azure AD
  - Conta de domínio
  - Conta local
- **Nome de usuário da conta**: Insira o nome de usuário da conta usada com o aplicativo fazer um teste. Você pode inserir contas no seguinte formato:
  - `user@contoso.com`
  - `domain\username`
  - `user@contoso.com`
  - `computerName\username`
- **URL de avaliação**: Insira a URL do teste que você deseja que os usuários executem. Para obter mais informações sobre como obter a URL, consulte a [documentação de fazer um teste](https://docs.microsoft.com/education/windows/take-tests-in-windows-10).
- **Monitoramento de tela**: Escolha **permitir** para monitorar a atividade de tela enquanto os usuários estão fazendo um teste. **Não configurado** impede que você monitore a tela durante o teste.
- **Sugestão de texto**: Escolha **permitir** para que o teste Takers possa ver sugestões de texto. **Não configurado** bloqueia sugestões de texto enquanto os usuários estão fazendo um teste.

## <a name="next-steps"></a>Passos Seguintes

O perfil é criado, mas talvez ainda não esteja fazendo nada. Certifique-se de [atribuir o perfil](device-profile-assign.md)e [monitore seu status](device-profile-monitor.md).
