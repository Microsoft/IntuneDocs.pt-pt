---
title: Ver o inventário de hardware e software dos PCs Windows
titleSuffix: Microsoft Intune
description: Como ver as informações de hardware e software dos computadores com Windows que gere como PCs com o cliente de software do Intune
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/01/2018
ms.topic: archived
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 3c10f4c9-520b-4864-92fc-a45a9f640ad4
ms.reviewer: owenyen
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic-keep
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5e24e72951d473c2e7e49d5ae62b39df18635c16
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/23/2019
ms.locfileid: "66040279"
---
# <a name="view-hardware-and-software-inventory-for-windows-pcs"></a>Ver o inventário de hardware e software dos PCs Windows

[!INCLUDE [classic-portal](includes/classic-portal.md)]

O Intune recolhe informações detalhadas sobre o hardware e software dos computadores que gere como PCs com o cliente de software do Intune. Utilize as informações nos seguintes procedimentos para saber como criar:

-   Um relatório que lista as informações sobre as capacidades de hardware dos PCs que gere.

-   Um relatório que lista o software instalado em cada PC.

-   Como atualizar o inventário de um PC para se certificar de que os dados do relatório estão atualizados.

## <a name="to-display-information-about-pcs-you-manage"></a>Para apresentar informações sobre os PCs que gere

1.  Na [consola de administração do Microsoft Intune](https://manage.microsoft.com/), escolha **Relatórios** &gt; **Relatórios de Inventário de Computadores**.

2.  Na página **Criar Novo Relatório**, aceite os valores predefinidos ou personalize-os para filtrar os resultados que serão devolvidos pelo relatório. Por exemplo, pode selecionar apenas os PCs que executam o Windows 8.1 para serem apresentados no relatório.

3.  Escolha **Ver Relatório** para abrir o **Relatório de Inventários de Computadores** numa nova janela.

    Pode ordenar o relatório por qualquer uma das colunas, como **Nome**, **Tipo de Chassis** ou **Fabricante**, selecionando o cabeçalho de cada coluna.

## <a name="to-display-software-installed-on-pcs-you-manage"></a>Para apresentar o software instalado nos PCs que gere

1.  Na [consola de administração do Microsoft Intune](https://manage.microsoft.com/), escolha **Relatórios** &gt; **Relatórios de Software Detetado**.

2.  Na página **Criar Novo Relatório**, aceite os valores predefinidos ou personalize-os para filtrar os resultados que serão devolvidos pelo relatório. Por exemplo, pode selecionar para que apenas o software publicado pela Microsoft seja apresentado no relatório.

3.  Escolha **Ver Relatório** para abrir o **Relatório de Software Detetado** numa nova janela.

    Pode ordenar o relatório por qualquer uma das colunas, como **Nome**, **Publicador** ou **Categoria**, selecionando o cabeçalho de cada coluna. Pode expandir as atualizações na lista para mostrar mais detalhes (como os PCs em que estão instaladas) ao selecionar a seta direcional junto ao item da lista.

## <a name="to-refresh-computer-inventory-to-ensure-it-is-current"></a>Para atualizar o inventário dos computadores e certificar-se de que está atualizado

1.  Na [consola de administração do Microsoft Intune](https://manage.microsoft.com/), selecione **Grupos** &gt; **Todos os Dispositivos** (ou outro grupo que contenha o PC cujo inventário quer atualizar).

2.  Selecione um PC ou prima a tecla **Ctrl** sem soltar para selecionar múltiplos PCs.

3.  Na barra de tarefas, escolha **Tarefas Remotas** &gt; **Atualizar Inventário**.

4.  Para ver o estado da tarefa, escolha **Tarefas Remotas** no canto inferior direito da página.

    É apresentada a caixa de diálogo **Estado da Tarefa**, que mostra as tarefas remotas atuais, o estado das tarefas, o nome do dispositivo e todos os erros comunicados e fornece uma ligação para informações de resolução de problemas.

### <a name="see-also"></a>Consulte também

[Tarefas de gestão comuns de PCs Windows com o cliente de software do Intune](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)
