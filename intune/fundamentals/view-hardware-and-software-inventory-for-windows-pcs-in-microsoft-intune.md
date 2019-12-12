---
title: Ver o inventário de hardware e software dos PCs Windows
titleSuffix: Microsoft Intune
description: Como ver as informações de hardware e software dos computadores com Windows que gere como PCs com o cliente de software do Intune
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 06/26/2019
ms.topic: archived
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 3c10f4c9-520b-4864-92fc-a45a9f640ad4
ms.reviewer: owenyen
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic-keep
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1ea74904657ec5457454e4371fb956648c74c422
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72504791"
---
# <a name="view-hardware-and-software-inventory-for-windows-pcs"></a>Ver o inventário de hardware e software dos PCs Windows

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

> [!NOTE]
> As informações neste tópico aplicam-se apenas a computadores Windows que está a gerir como PCs através do cliente de software do Intune. Se você quiser exibir o inventário de computadores Windows registrados como dispositivos móveis, consulte [Exibir detalhes do dispositivo no Intune](../remote-actions/device-inventory.md).

O Intune coleta informações detalhadas sobre o hardware e o software para desktops gerenciados como PCs usando o cliente de software do Intune. Utilize as informações nos seguintes procedimentos para saber como criar:

- Um relatório que lista as informações sobre as capacidades de hardware dos PCs que gere.

- Um relatório que lista o software instalado em cada PC.

- Como atualizar o inventário de um PC para garantir que os dados no relatório sejam atuais.

## <a name="to-display-information-about-pcs-you-manage"></a>Para apresentar informações sobre os PCs que gere

1. Na [consola de administração do Microsoft Intune](https://manage.microsoft.com/), escolha **Relatórios** &gt; **Relatórios de Inventário de Computadores**.

2. Na página **Criar Novo Relatório**, aceite os valores predefinidos ou personalize-os para filtrar os resultados que serão devolvidos pelo relatório. Por exemplo, você pode selecionar que somente os computadores que executam Windows 8.1 são exibidos no relatório.

3. Escolha **Ver Relatório** para abrir o **Relatório de Inventários de Computadores** numa nova janela.

    Pode ordenar o relatório por qualquer uma das colunas, como **Nome**, **Tipo de Chassis** ou **Fabricante**, selecionando o cabeçalho de cada coluna.

## <a name="to-display-software-installed-on-pcs-you-manage"></a>Para apresentar o software instalado nos PCs que gere

1. Na [consola de administração do Microsoft Intune](https://manage.microsoft.com/), escolha **Relatórios** &gt; **Relatórios de Software Detetado**.

2. Na página **Criar Novo Relatório**, aceite os valores predefinidos ou personalize-os para filtrar os resultados que serão devolvidos pelo relatório. Por exemplo, pode selecionar para que apenas o software publicado pela Microsoft seja apresentado no relatório.

3. Escolha **Ver Relatório** para abrir o **Relatório de Software Detetado** numa nova janela.

    Pode ordenar o relatório por qualquer uma das colunas, como **Nome**, **Publicador** ou **Categoria**, selecionando o cabeçalho de cada coluna. Pode expandir as atualizações na lista para mostrar mais detalhes (como os PCs em que estão instaladas) ao selecionar a seta direcional junto ao item da lista.

## <a name="to-refresh-computer-inventory-to-ensure-it-is-current"></a>Para atualizar o inventário dos computadores e certificar-se de que está atualizado

1. Na [consola de administração do Microsoft Intune](https://manage.microsoft.com/), selecione **Grupos** &gt; **Todos os Dispositivos** (ou outro grupo que contenha o PC cujo inventário quer atualizar).

2. Selecione um PC ou prima a tecla **Ctrl** sem soltar para selecionar múltiplos PCs.

3. Na barra de tarefas, escolha **Tarefas Remotas** &gt; **Atualizar Inventário**.

4. Para ver o estado da tarefa, escolha **Tarefas Remotas** no canto inferior direito da página.

    É apresentada a caixa de diálogo **Estado da Tarefa**, que mostra as tarefas remotas atuais, o estado das tarefas, o nome do dispositivo e todos os erros comunicados e fornece uma ligação para informações de resolução de problemas.

## <a name="see-also"></a>Consulte também

[Tarefas de gestão comuns de PCs Windows com o cliente de software do Intune](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)
