---
title: "Definições de política de termos e condições | Documentos da Microsoft"
description: "Pode implementar termos e condições do Intune para grupos de utilizadores para explicar como a inscrição, o acesso a recursos de trabalho e a utilização da aplicação Portal da Empresa afetam os dispositivos e os utilizadores."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 07/11/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6edf0ac1-4f46-4543-a9e5-f484ac37e9a5
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 8b2bd3ecba0b597bc742ea08872ffe8fc58155cf
ms.openlocfilehash: 177485a0b09a2b0213a293914799a34a3bfa1136
ms.lasthandoff: 04/24/2017


---

# <a name="terms-and-condition-policy-settings-in-microsoft-intune"></a>Definições de política de termos e condições no Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Pode implementar termos e condições do Intune para grupos de utilizadores para explicar como a inscrição, o acesso a recursos de trabalho e a aplicação Portal da Empresa afetam os dispositivos e os utilizadores. Os utilizadores têm de aceitar os termos e condições antes de poderem utilizar o Portal da Empresa para inscrever e aceder ao seu trabalho.

Pode criar e implementar diversas políticas que contêm diferentes termos e condições. Pode também produzir versões dos mesmos termos e condições em idiomas diferentes e, em seguida, implementá-los nos grupos adequados.

## <a name="create-a-terms-and-conditions-policy"></a>Criar uma política de termos e condições

1.  Na [consola de administração do Microsoft Intune](https://manage.microsoft.com) clique em **Política** &gt; **Termos e Condições**.

    ![Captura de ecrã da política de termos e condições](./media/pol-sa-terms-conditions.png)

2.  Clique em **Adicionar** para criar uma nova política de termos e condições.

    Também pode **Editar** ou **Eliminar** uma política existente.

3.  Na página **Criar Termos e Condições**, especifique as seguintes informações:

    -   **Nome**&mdash;um nome exclusivo da política apresentado na consola do Intune.

    -   **Descrição**&mdash;detalhes que o ajudam a identificar a política na consola do Intune.

    -   **Título**&mdash;o título que os utilizadores veem no portal da empresa.

    -   **Texto a explicar o que significa se o utilizador aceita**&mdash;etiqueta que os utilizadores veem sobre a aceitação. Por exemplo, "Concordo com os termos e condições".

4.  Quando terminar, clique em **Guardar**. A nova política é apresentada no nó **Termos e Condições** da área de trabalho **Política**.

## <a name="deploy-a-terms-and-conditions-policy"></a>Implementar uma política de termos e condições

1.  Na [consola de administração do Microsoft Intune](https://manage.microsoft.com), clique em **Política** &gt; **Termos e Condições**.

2.  Na lista **Políticas dos Termos e Condições**, selecione a política que pretende implementar e, em seguida, clique em **Gerir Implementação**.

3.  Na caixa de diálogo **Gerir a Implementação**, selecione os grupos de utilizadores nos quais irá implementar a política e clique em **OK**.

    Quando os utilizadores abrangidos acedem ao portal da empresa, o Intune apresenta os termos e condições implementadas. Os utilizadores têm de aceitar estes termos antes de terem acesso aos recursos da empresa.

## <a name="monitor-a-terms-and-conditions-policy"></a>Monitorizar uma política de termos e condições

1.  Na [consola de administração do Microsoft Intune](https://manage.microsoft.com), clique em **Política** &gt; **Termos e Condições**.

2.  Na janela **Criar Novo Relatório**, clique em **Ver Relatório**. O relatório irá abrir com detalhes sobre quais os utilizadores aceitaram os termos e condições implementados.

### <a name="updates-and-version-control-for-terms-and-conditions"></a>Atualizações e controlo de versão para termos e condições
Ao editar uma política de termos e condições existentes, pode escolher que comportamento ocorre ao implementar a política. Utilize o procedimento seguinte para ajudar a atualizar os termos existentes e as políticas de condições.

## <a name="work-with-multiple-versions-of-terms-and-conditions"></a>Trabalhar com múltiplas versões de termos e condições

1.  Na [consola de administração do Microsoft Intune](https://manage.microsoft.com), clique em **Política** &gt; **Termos e Condições**.

2.  Selecione a política de termos e condições que pretende editar e, em seguida, clique em **Editar**.

3.  Na página **Editar Termos e Condições**, efetue as edições necessárias e, em seguida, especifique se esta nova versão necessita que todos os utilizadores aceitem os termos e condições ou se apenas os novos utilizadores irão ver a nova versão.

    Recomendamos que aumente o número da versão e solicite a aceitação sempre que efetua alterações significativas na sua política de termos e condições. Mantenha o número da versão atual se, por exemplo, estiver a corrigir erros de digitação ou a alterar a formatação.

### <a name="see-also"></a>Consulte também
[Gerir definições e funcionalidades nos seus dispositivos com as políticas do Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)

