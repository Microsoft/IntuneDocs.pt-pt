---
title: Instalar o Office 365 em dispositivos macOS através do Microsoft Intune
titleSuffix: ''
description: Saiba como pode utilizar o Microsoft Intune para instalar as aplicações do Office 365 em dispositivos macOS.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/28/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 2372332a-7e3a-4a9c-91a9-86654e0fabe2
ms.reviewer: aiwang
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1ac752c503f523ab7f55db38488fdf31f8d886fa
ms.sourcegitcommit: 7315fe72b7e55c5dcffc6d87f185f3c2cded9028
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/02/2019
ms.locfileid: "67527433"
---
# <a name="assign-office-365-to-macos-devices-with-microsoft-intune"></a>Atribuir o Office 365 a dispositivos macOS com o Microsoft Intune

Com este tipo de aplicação, é mais fácil atribuir aplicações da versão 2016 do Office 365 a dispositivos macOS. Ao utilizar este tipo de aplicações, pode instalar o Word, Excel, PowerPoint, Outlook e OneNote. Para ajudar a manter as aplicações mais protegidas e atualizadas, as aplicações vêm com Microsoft AutoUpdate (MAU). As aplicações que quer são mostradas como uma aplicação na lista de aplicações na consola do Intune.


## <a name="before-you-start"></a>Antes de começar

Antes de começar a adicionar o Office 365 a dispositivos macOS, compreenda os seguintes detalhes:

- Os dispositivos em que pretende implementar estas aplicações têm de ter o macOS 10.10 ou posterior em execução.
- O Intune suporta apenas a adição de aplicações do Office que são incluídas com o Office 2016 apenas suite de Mac.
- Se estiverem abertas aplicações do Office quando o Intune instalar o conjunto de aplicações, os utilizadores poderão perder os dados dos ficheiros não guardados.

## <a name="create-and-configure-the-app-suite"></a>Criar e configurar o conjunto de aplicações

Adicionar o Office 365 a partir do painel **Aplicações**.
1. Inicie sessão no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. No painel **Intune**, selecione **Aplicações do cliente**.
4. No painel da carga de trabalho **Aplicações do cliente**, em **Gerir**, selecione **Aplicações**. 
5. Selecione **Adicionar**.
6. Na lista **Tipo de aplicação**, no grupo **Conjunto de Aplicações do Office 365**, selecione **macOS**.
7. Para obter informações sobre o conjunto de aplicações, selecione **Informações do Conjunto de Aplicações**.  
    Estas informações ajudam-no a identificar o conjunto de aplicações no Intune e também ajuda os utilizadores a encontrá-la no portal da empresa.
8. Introduza as seguintes informações:
    - **Nome do pacote**: Introduza o nome do conjunto de aplicações, tal como é apresentado no portal da empresa. Confirme que todos os nomes de conjuntos de aplicações que utiliza são exclusivos. Se o nome de um conjunto de aplicações existir em duplicado, apenas uma das aplicações será apresentada aos utilizadores no portal da empresa.
    - **Descrição do conjunto**: Introduza uma descrição para o conjunto de aplicações.
    - **Publicador**: Microsoft aparece como o publicador.
    - **Categoria**: Selecione uma ou mais categorias das aplicações incorporadas ou, em alternativa, uma categoria criada por si. Esta definição irá permitir que os utilizadores encontrem o conjunto de aplicações mais facilmente quando procurarem no portal da empresa.
    - **Apresentar como aplicação em destaque no Portal da Empresa**: selecione esta opção para apresentar a aplicação de forma bem visível na página principal do portal da empresa quando os utilizadores procurarem aplicações.
    - **URL de informações**: Opcionalmente, introduza o URL de um site que contenha informações sobre esta aplicação. O URL é apresentado aos utilizadores no portal da empresa.
    - **URL de privacidade**: Opcionalmente, introduza o URL de um site que contenha informações sobre a privacidade desta aplicação. O URL é apresentado aos utilizadores no portal da empresa.
    - **Programador**: Microsoft aparece como o programador.
    - **Proprietário**: Microsoft aparece como o proprietário.
    - **Notas**: opcionalmente, introduza quaisquer notas que queira associar a esta aplicação.
    - **Logótipo**: O logótipo do Office 365 é apresentado com a aplicação quando os utilizadores procurarem no portal da empresa.
9. Selecione **OK**.
10. No painel **Adicionar aplicação**, selecione **Adicionar**.  
    O conjunto é apresentado na lista de aplicações como uma única entrada.

## <a name="configure-app-assignments"></a>Configurar atribuições de aplicações

Neste passo, configure as atribuições do conjunto de aplicações. 

1. Na lista de aplicações, selecione o conjunto de aplicações **Office 365** para exibir o painel de descrição geral do **Office 365**.
2. No painel do **Office 365**, selecione **Atribuições**.
3. Para adicionar um grupo que vá utilizar o conjunto de aplicações, selecione **Adicionar grupo**.  
    O painel **Adicionar grupo** é apresentado.
4. Defina o **Tipo de atribuição** para **Necessário** ou **Disponível**.
5. Atribua o conjunto aos grupos que selecionou. Para obter mais informações, veja [Atribuir aplicações a grupos com o Microsoft Intune](apps-deploy.md).

    >[!Note]
    > Não é possível desinstalar o conjunto de aplicações do Office 365 através do Intune.

5. No painel **Atribuir**, selecione **OK**.
6. No painel **Adicionar grupo**, selecione **OK**.
7. Para consolidar as suas atribuições, selecione **Guardar**.

## <a name="next-steps"></a>Passos Seguintes

- Para saber mais sobre a adição de aplicações do Office 365 a dispositivos Windows 10, veja [Atribuir aplicações do Office 365 ProPlus 2016 para dispositivos Windows 10 com o Microsoft Intune](apps-add-office365.md).
- Para saber mais sobre como incluir e excluir atribuições de aplicações a partir de grupos de utilizadores, veja [Incluir e excluir atribuições de aplicações](apps-inc-exl-assignments.md).
