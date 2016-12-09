---
title: "Gerir a associação utilizador-dispositivo para PCs Windows | Microsoft Intune"
description: Como associar um utilizador a um PC Windows gerido pelo Intune.
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 08/04/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 53c99d63-c312-442a-8a71-de1b10fcd39b
ms.reviewer: owenyen
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: eeb85a28ea6f99a0123ec5df3b0d476a678b85cb
ms.openlocfilehash: 39fec6a2ea8d8c0f4b6ea1460c76a8a6c652d614


---

# <a name="manage-user-device-linking-for-windows-pcs"></a>Gerir a associação utilizador-dispositivo para PCs Windows
Antes de poder implementar software para um utilizador, tem de associar o utilizador a um computador. Pode associar um utilizador a múltiplos computadores, mas cada computador só pode ser associado a um utilizador. Os utilizadores são automaticamente associados a qualquer computador que inscrevam no Intune através do portal da empresa.

Para associar um utilizador a um computador:

1.  Na [consola de administração do Microsoft Intune](https://manage.microsoft.com/), escolha **Grupos** &gt; **Todos os Dispositivos** (ou outro grupo que contenha o computador que pretende associar a um utilizador).

2.  Selecione o computador que pretende associar a um utilizador e, em seguida, escolha **Associar Utilizador**.

    A caixa de diálogo **Associar Utilizador** apresenta uma lista de utilizadores disponíveis com os respetivos nomes a apresentar, IDs de utilizador e o número de computadores a que cada utilizador está atualmente associado. Se um utilizador já estiver associado ao computador selecionado, o ID de utilizador e o nome desse utilizador serão apresentados em **Utilizador atual**. Se o computador não estiver associado a nenhum utilizador, o texto **Sem Utilizador** aparecerá em **Utilizador Atual**.

3.  Efetue uma das seguintes ações:

    -   Para deixar o computador associado ao utilizador atual, se existir um, escolha **Cancelar**.

    -   Para remover a associação ao utilizador atual, se existir um, escolha **Remover associação** &gt; **OK**.

    -   Para associar o computador a um novo utilizador, selecione um utilizador na lista **Todos os utilizadores** . Confirme que os dados do utilizador estão corretos e, em seguida, escolha **OK**.

> [!TIP]
> Se pretender restringir a capacidade dos próprios utilizadores finais se ligarem a computadores, ative a opção **Restringir a capacidade dos próprios utilizadores se ligarem a computadores** na política **Definições de Agente do Microsoft Intune**.

### <a name="see-also"></a>Consulte também

[Tarefas de gestão comuns de PCs Windows com o cliente de software do Intune](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)


<!--HONumber=Nov16_HO4-->


