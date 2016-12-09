---
title: "Ver o inventário de hardware e software dos PCs Windows | Microsoft Intune"
description: "Como ver as informações de hardware e software dos PCs Windows que gere com o Intune."
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 08/04/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3c10f4c9-520b-4864-92fc-a45a9f640ad4
ms.reviewer: owenyen
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: eeb85a28ea6f99a0123ec5df3b0d476a678b85cb
ms.openlocfilehash: 807599d4a6a979c88732ab969fdecb64552a83d5


---

# <a name="view-hardware-and-software-inventory-for-windows-pcs"></a>Ver o inventário de hardware e software dos PCs Windows

O Intune recolhe informações detalhadas sobre o hardware e o software de computadores geridos. Utilize as informações nos seguintes procedimentos para saber como criar:

-   Um relatório que lista as informações sobre as capacidades de hardware dos computadores que gere.

-   Um relatório que lista o software instalado em cada computador.

-   Como atualizar o inventário de um computador para se certificar de que os dados do relatório estão atualizados.

## <a name="to-display-information-about-computers-you-manage"></a>Para apresentar informações sobre os computadores que gere

1.  Na [consola de administração do Microsoft Intune](https://manage.microsoft.com/), escolha **Relatórios** &gt; **Relatórios de Inventário de Computadores**.

2.  Na página **Criar Novo Relatório**, aceite os valores predefinidos ou personalize-os para filtrar os resultados que serão devolvidos pelo relatório. Por exemplo, pode selecionar apenas os computadores que executam o Windows 8.1 para serem apresentados no relatório.

3.  Escolha **Ver Relatório** para abrir o **Relatório de Inventários de Computadores** numa nova janela.

    Pode ordenar o relatório por qualquer uma das colunas, como **Nome**, **Tipo de Chassis** ou **Fabricante**, selecionando o cabeçalho de cada coluna.

## <a name="to-display-software-installed-on-computers-you-manage"></a>Para apresentar o software instalado nos computadores que gere

1.  Na [consola de administração do Microsoft Intune](https://manage.microsoft.com/), escolha **Relatórios** &gt; **Relatórios de Software Detetado**.

2.  Na página **Criar Novo Relatório**, aceite os valores predefinidos ou personalize-os para filtrar os resultados que serão devolvidos pelo relatório. Por exemplo, pode selecionar para que apenas o software publicado pela Microsoft seja apresentado no relatório.

3.  Escolha **Ver Relatório** para abrir o **Relatório de Software Detetado** numa nova janela.

    Pode ordenar o relatório por qualquer uma das colunas, como **Nome**, **Publicador** ou **Categoria**, selecionando o cabeçalho de cada coluna. Pode expandir as atualizações na lista para mostrar mais detalhes (como os computadores em que estão instaladas) ao escolher a seta direcional junto ao item da lista.

## <a name="to-refresh-computer-inventory-to-ensure-it-is-current"></a>Para atualizar o inventário dos computadores e certificar-se de que está atualizado

1.  Na [consola de administração do Microsoft Intune](https://manage.microsoft.com/), escolha **Grupos** &gt; **Todos os Dispositivos** (ou outro grupo que contenha o computador cujo inventário quer atualizar).

2.  Selecione um computador ou prima se soltar a tecla **Ctrl** para selecionar múltiplos computadores.

3.  Na barra de tarefas, escolha **Tarefas Remotas** &gt; **Atualizar Inventário**.

4.  Para ver o estado da tarefa, escolha **Tarefas Remotas** no canto inferior direito da página.

    É apresentada a caixa de diálogo **Estado da Tarefa**, que mostra as tarefas remotas atuais, o estado das tarefas, o nome do dispositivo e todos os erros comunicados e fornece uma ligação para informações de resolução de problemas.

### <a name="see-also"></a>Consulte também

[Tarefas de gestão comuns de PCs Windows com o cliente de software do Intune](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)


<!--HONumber=Nov16_HO4-->


