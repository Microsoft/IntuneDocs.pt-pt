---
title: "Instalar o Office 365 em dispositivos macOS através do Intune"
titlesuffix: Azure portal
description: "Saiba como pode utilizar o Intune para facilitar a instalação das aplicações do Office 365 em dispositivos macOS."
keywords: 
author: erikre
ms.author: erikre
manager: dougeby
ms.date: 12/13/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2372332a-7e3a-4a9c-91a9-86654e0fabe2
ms.reviewer: aiwang
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 1573a6a2ca78489df46c9e08ebbfe9a16b0731c7
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/25/2018
---
# <a name="how-to-assign-office-365-to-macos-devices-with-microsoft-intune"></a>Como atribuir o Office 365 a dispositivos macOS com o Microsoft Intune

Com este tipo de aplicação, é mais fácil atribuir aplicações do Office 365 a dispositivos macOS. Este novo tipo de aplicação permite-lhe instalar o Word, Excel, PowerPoint, Outlook e OneNote. Estas aplicações também vêm com o Microsoft AutoUpdate (MAU) para ajudar a manter as aplicações mais protegidas e atualizadas. As aplicações que pretende são apresentadas como uma aplicação na lista de aplicações na consola do Intune.


## <a name="before-you-start"></a>Antes de começar

- Os dispositivos em que pretende implementar estas aplicações têm de ter o macOS 10.10 ou posterior em execução.
- O Intune apenas suporta a adição de aplicações do Office incluídas no conjunto de aplicações do Office 2016 para Mac.
- Se estiverem abertas aplicações do Office quando o Intune instalar o conjunto de aplicações, os utilizadores finais poderão perder os dados dos ficheiros não guardados.


## <a name="get-started"></a>Introdução
Adicione o Office 365 através do painel **Aplicações**.
1.  Inicie sessão no portal do Azure.
2.  Escolha **Mais Serviços** > **Monitorização + Gestão** > **Intune**.
3.  No painel **Intune**, escolha **Aplicações móveis**.
4.  Na carga de trabalho **Aplicações móveis**, selecione **Aplicações** no grupo **Gerir**. Selecione **Adicionar**.
5.  No painel **Adicionar Aplicação**, escolha **Office 365** > **macOS**.
6.  Selecione **Adicionar**.

## <a name="configure-the-app-suite"></a>Configurar o conjunto de aplicações

Forneça informações acerca do conjunto de aplicações. Estas informações ajudam-no a identificar o conjunto no Intune e também ajudam os utilizadores a encontrá-lo na aplicação Portal da Empresa.

1.  No painel **Adicionar Aplicação**, selecione **Informações do Conjunto de Aplicações**.
2.  Especifique as seguintes informações:
    - **Nome do Conjunto** – introduza o nome do conjunto de aplicações tal como será apresentado no portal da empresa. Certifique-se de que todos os nomes de conjuntos de aplicações que utiliza são exclusivos. Se o nome de um conjunto de aplicações existir em duplicado, apenas uma das aplicações será apresentada aos utilizadores no portal da empresa.
    - **Descrição do Conjunto** – introduza uma descrição para o conjunto de aplicações.
    - **Publicador** – a Microsoft aparece como o publicador.
    - **Categoria** – em alternativa, selecione uma ou mais categorias de aplicações incorporadas ou uma categoria criada por si. Isto irá permitir que os utilizadores encontrem o conjunto de aplicações mais facilmente quando procurarem no portal da empresa.
    - **Apresentar como aplicação em destaque no Portal da Empresa** – esta opção apresenta o conjunto de aplicações em destaque na página principal do portal da empresa quando os utilizadores procurarem aplicações.
    - **URL de Informações** – Opcionalmente, introduza o URL de um site que contenha informações sobre esta aplicação. O URL é apresentado aos utilizadores no portal da empresa.
    - **URL de Privacidade** – Opcionalmente, introduza um URL para um site que contenha informações sobre a privacidade desta aplicação. O URL é apresentado aos utilizadores no portal da empresa.
    - **Programador** – a Microsoft aparece como o programador.
    - **Proprietário** – a Microsoft aparece como o proprietário.
    - **Notas** – Introduza quaisquer notas que pretenda associar esta aplicação.
    - **Carregar Ícone** – carregue um ícone que será apresentado para a aplicação quando os utilizadores procurarem no portal da empresa.
3.  Selecione **OK**. O conjunto é apresentado na lista de aplicações como uma única entrada.

## <a name="configure-app-assignments"></a>Configurar atribuições de aplicações

Neste passo, configure as atribuições do conjunto de aplicações. Tenha em atenção que o tipo de aplicação estará disponível brevemente.

1.  Selecione o conjunto de aplicações na lista de aplicações e selecione **Atribuições**.
2.  Escolha **Selecionar grupos**.
3.  Atribua o conjunto de aplicações aos grupos que escolher. Para obter mais informações, veja [Como atribuir aplicações a grupos com o Microsoft Intune](/intune/apps-deploy).
4.  Para cada grupo, selecione **Exigir Instalação**.
        >[!Note]
        > You cannot uninstall Office 365 through Intune.

5. Selecione **Guardar** para consolidar as atribuições.

## <a name="next-steps"></a>Próximos passos

Para saber mais sobre a adição de aplicações do Office 365 a dispositivos Windows 10, veja [Como atribuir aplicações do Office 365 ProPlus 2016 a dispositivos Windows 10 com o Microsoft Intune](/intune/apps-add-office365).
