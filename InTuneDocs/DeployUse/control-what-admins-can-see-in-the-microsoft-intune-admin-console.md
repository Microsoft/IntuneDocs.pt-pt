---
title: "Personalizar vistas da consola para funções de administrador | Microsoft Intune"
description: 
keywords: 
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e0783eaa-67dc-410e-9e80-4d3aa72f36d8
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 779127bfd39145010f0d9b6609286aaf4dedfdc8
ms.openlocfilehash: 52a77e50b3dde24ba270766d4472bdd6176cc415


---

# Personalizar vistas da consola do Intune de acordo com funções de administrador
Pode filtrar a vista da consola de administração do Microsoft Intune para permitir que os seus administradores vejam apenas os itens que precisam de ver para desempenharem a sua função. Por exemplo, pode permitir que apenas os operadores da consola de administração atualizem definições de software maligno ou redefinam o código de acesso nos dispositivos. Esta filtragem é executada através de **designações** predefinidas que são atribuídas a utilizadores específicos. Quando estes utilizadores acedem à consola de administração, veem apenas itens específicos para as designações deles.

## Como criar uma vista personalizada

1.  Na [consola de administração do Microsoft Intune](https://manage.microsoft.com), selecione **Admin** &gt; **Administradores do Serviço**.

2.  Na lista de administradores do serviço, escolha o utilizador cuja designação pretende alterar e, em seguida, escolha **Gerir Acesso**.

3.  Na caixa de diálogo **Gerir Acesso** , escolha o nível de acesso que pretende dar ao utilizador selecionado. Pode escolher entre:

    -   **Acesso total**
    -   **Acesso só de leitura**
    -   **Suporte técnico - nó Grupos**

    O acesso total e o acesso só de leitura são facilmente compreensíveis. <!--- **Helpdesk - Groups Node** allows users to choose from one of the following designations that provide custom levels of access to the [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] admin console:--->

    **Suporte técnico - nó Grupos** restringe o que o administrador pode ver e fazer ao seguinte:

    -   Ver listas de utilizadores e dispositivos. O administrador não pode utilizar filtros para modificar a vista. No entanto, pode utilizar a filtragem de grupos para modificar o que ele conseguirá ver. Para obter mais informações, consulte [Utilizar grupos para gerir utilizadores e dispositivos com o Microsoft Intune](use-groups-to-manage-users-and-devices-with-microsoft-intune.md).

    -   Imprimir a lista de utilizadores e dispositivos

    -   Exportar a lista de utilizadores e dispositivos

    -   Ver as propriedades de um utilizador ou dispositivo

    -   Efetuar as seguintes tarefas remotas:

        -   Executar uma análise completa de malware

        -   Executar uma análise rápida de malware

        -   Reiniciar um computador

        -   Atualizar definições de software maligno

        -   Atualizar políticas

        -   Atualizar inventário

        -   Bloquear remotamente um dispositivo

        -   Repor código de acesso

Da próxima vez que o administrador configurado abrir a consola de administração do Intune, ser-lhe-á concedido o nível de acesso que lhe tiver designado.



<!--HONumber=Jun16_HO4-->


