---
title: "Instalar o Office 365 em dispositivos macOS através do Microsoft Intune"
titlesuffix: 
description: "Saiba como pode utilizar o Microsoft Intune para instalar as aplicações do Office 365 em dispositivos macOS."
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/02/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2372332a-7e3a-4a9c-91a9-86654e0fabe2
ms.reviewer: aiwang
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8de14184c4d23adc79d5b519fdcf272f0d7f6804
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/08/2018
---
# <a name="how-to-assign-office-365-to-macos-devices-with-microsoft-intune"></a>Como atribuir o Office 365 a dispositivos macOS com o Microsoft Intune

O tipo de **aplicação da Loja** facilita a atribuição de aplicações do Office 365 a dispositivos macOS. Este tipo de aplicação permite-lhe instalar o Word, Excel, PowerPoint, Outlook e OneNote. Estas aplicações também vêm com o Microsoft AutoUpdate (MAU) para ajudar a manter as aplicações mais protegidas e atualizadas. As aplicações que pretende são apresentadas como uma aplicação na lista de aplicações na consola do Intune.


## <a name="before-you-start"></a>Antes de começar

Antes de começar a adicionar o Office 365 a dispositivos macOS, tem de compreender os seguintes detalhes:

- Os dispositivos em que pretende implementar estas aplicações têm de ter o macOS 10.10 ou posterior em execução.
- O Intune apenas suporta a adição de aplicações do Office incluídas no conjunto de aplicações do Office 2016 para Mac.
- Se estiverem abertas aplicações do Office quando o Intune instalar o conjunto de aplicações, os utilizadores finais poderão perder os dados dos ficheiros não guardados.

## <a name="create-and-configure-the-app-suite"></a>Criar e configurar o conjunto de aplicações

Adicione o Office 365 através do painel **Aplicações**.
1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os Serviços** > **Monitorização + Gestão** > **Intune**.
3. Selecione **Aplicações móveis**, no painel **Intune**.
4. Na carga de trabalho **Aplicações móveis**, selecione **Aplicações** na secção **Gerir**. 
5. Selecione **Adicionar** para apresentar o painel **Adicionar aplicação**.
6. Na lista **Tipo de aplicação**, selecione **macOS** no grupo **Conjunto de Aplicações do Office 365**.
7. Selecione **Informações do Conjunto de Aplicações** para fornecer informações sobre o conjunto de aplicações. Estas informações ajudam-no a identificar o conjunto de aplicações no Intune e também ajudam os utilizadores a encontrá-lo na aplicação Portal da Empresa.
8.  Especifique as seguintes informações:
    - **Nome do Conjunto** – introduza o nome do conjunto de aplicações tal como será apresentado no portal da empresa. Certifique-se de que todos os nomes de conjuntos de aplicações que utiliza são exclusivos. Se o nome de um conjunto de aplicações existir em duplicado, apenas uma das aplicações será apresentada aos utilizadores no portal da empresa.
    - **Descrição do Conjunto** – introduza uma descrição para o conjunto de aplicações.
    - **Publicador** – a Microsoft aparece como o publicador.
    - **Categoria** – selecione uma ou mais categorias das aplicações incorporadas ou, em alternativa, uma categoria criada por si. Esta definição irá permitir que os utilizadores encontrem o conjunto de aplicações mais facilmente quando procurarem no portal da empresa.
    - **Apresentar como aplicação em destaque no Portal da Empresa** – esta definição irá apresentar o conjunto de aplicações em destaque na página principal do portal da empresa quando os utilizadores procurarem aplicações.
    - **URL de informações** (opcional) – introduza o URL de um site que contenha informações sobre esta aplicação. O URL é apresentado aos utilizadores no portal da empresa.
    - **URL de privacidade** (opcional) – introduza um URL para um site que contenha informações sobre a privacidade desta aplicação. O URL é apresentado aos utilizadores no portal da empresa.
    - **Programador** – a Microsoft aparece como o programador.
    - **Proprietário** – a Microsoft aparece como o proprietário.
    - **Notas** (opcional) – introduza quaisquer notas que pretenda associar esta aplicação.
    - **Logótipo** – o logótipo do Office 365 é apresentado com a aplicação quando os utilizadores procuram no portal da empresa.
9.  Clique em **OK** no painel **Informações da aplicação**.
10. Clique em **Adicionar** no painel **Adicionar aplicação**.
    O conjunto é apresentado na lista de aplicações como uma única entrada.

## <a name="configure-app-assignments"></a>Configurar atribuições de aplicações

Neste passo, configure as atribuições do conjunto de aplicações. 

1. Selecione o conjunto de aplicações do **Office 365** na lista de aplicações para apresentar o painel **Office 365**.
2. Clique em **Atribuições** no painel **Office 365**.
3. Clique em **Adicionar grupo** para adicionar um grupo para utilizar o conjunto de aplicações. O painel **Adicionar grupo** é apresentado.
3. Defina o **Tipo de atribuição** como **Necessário**.
4. Atribua o conjunto de aplicações aos grupos que escolher. Para obter mais informações, veja [Como atribuir aplicações a grupos com o Microsoft Intune](apps-deploy.md).

    >[!Note]
    > Para os grupos para os quais o conjunto de aplicações do Office 365 é necessário, não pode desinstalá-lo através do Microsoft Intune.

5. Selecione **OK** no painel **Atribuir**.
6. Selecione **OK** no painel **Adicionar grupo**.
7. Selecione **Guardar** para consolidar as atribuições.

## <a name="next-steps"></a>Próximos passos

- Para saber mais sobre a adição de aplicações do Office 365 a dispositivos Windows 10, veja [Como atribuir aplicações do Office 365 ProPlus 2016 a dispositivos Windows 10 com o Microsoft Intune](apps-add-office365.md).
- Para saber mais sobre como incluir e excluir atribuições de aplicações a grupos de utilizadores, veja [Incluir e excluir atribuições de aplicações](apps-inc-exl-assignments.md).
