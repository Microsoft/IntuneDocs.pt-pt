---
title: Gerir a associação utilizador-dispositivo para PCs Windows
titleSuffix: Microsoft Intune
description: Como associar um utilizador a um PC Windows gerido pelo Intune.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/01/2018
ms.topic: archived
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 53c99d63-c312-442a-8a71-de1b10fcd39b
ms.reviewer: owenyen
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic-keep
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9ef14d8ed3b1635fba183134b0d457ddc82ae329
ms.sourcegitcommit: 484a898d54f5386fdbce300225aaa3495cecd6b0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/01/2019
ms.locfileid: "58799236"
---
# <a name="manage-user-device-linking-for-windows-pcs"></a>Gerir a associação utilizador-dispositivo para PCs Windows

[!INCLUDE [classic-portal](includes/classic-portal.md)]

As informações neste tópico aplicam-se apenas a computadores Windows que está a gerir como PCs através do cliente de software do Intune. 

Antes de poder implementar software para um utilizador, tem de associar o utilizador a um PC. Pode associar um utilizador a múltiplos PCs, mas cada PC só pode ser associado a um utilizador. Os utilizadores são automaticamente associados a quaisquer PCs que inscrevam no Intune através do portal da empresa.

Para associar um utilizador a um PC:

1. Na [consola de administração do Microsoft Intune](https://manage.microsoft.com/), selecione **Grupos** &gt; **Todos os Dispositivos** (ou outro grupo que contenha o PC que pretende associar a um utilizador).

2. Selecione o PC que pretende associar a um utilizador e, em seguida, selecione **Associar Utilizador**.

   A caixa de diálogo **Associar Utilizador** apresenta uma lista de utilizadores disponíveis com os respetivos nomes a apresentar, IDs de utilizador e o número de PCs a que cada utilizador está atualmente associado. Se um utilizador já estiver associado ao PC selecionado, o ID de utilizador e o nome desse utilizador serão apresentados em **Utilizador atual**. Se o PC não estiver associado a nenhum utilizador, o texto **Sem Utilizador** aparecerá em **Utilizador Atual**.

3. Efetue uma das seguintes ações:

   - Para deixar o PC associado ao utilizador atual, se existir um, selecione **Cancelar**.

   - Para remover a associação ao utilizador atual, se existir um, escolha <strong>remover associação **&gt;** OK</strong>.

   - Para associar o PC a um novo utilizador, selecione um utilizador na lista **Todos os utilizadores**. Confirme que os dados do utilizador estão corretos e, em seguida, escolha **OK**.

> [!TIP]
> Se pretender restringir a capacidade dos próprios utilizadores finais se ligarem a PCs, ative a opção **Restringir a capacidade dos próprios utilizadores se ligarem a PCs** na política **Definições de Agente do Microsoft Intune**.

### <a name="see-also"></a>Consulte também

[Tarefas de gestão comuns de PCs Windows com o cliente de software do Intune](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)
