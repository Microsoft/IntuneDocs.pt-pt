---
title: "Adicionar aplicações incorporadas a dispositivos móveis com o Intune"
titlesuffix: Azure portal
description: "Saiba como pode utilizar o Intune para facilitar a instalação de aplicações incorporadas em dispositivos móveis."
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/26/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0ec8de66-5a0f-4c8d-afbf-c2becc7d6eec
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 90bec6442084e46f499c57cf128e6ef57fe1ce9c
ms.sourcegitcommit: 0a5f424a8f683daa919b13b5c363173040d561c8
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/14/2018
---
# <a name="how-to-add-built-in-apps-to-microsoft-intune"></a>Como adicionar aplicações incorporadas ao Microsoft Intune

As aplicações **incorporadas** permitem-lhe atribuir facilmente aplicações geridas organizadas, como aplicações do Office 365, a dispositivos iOS e Android. Pode atribuir aplicações específicas a este tipo de aplicação, como o Excel, Power BI, SharePoint, Teams, OneDrive, Outlook, Skype, entre outras. Depois de adicionar uma aplicação, verá o tipo da aplicação como **Aplicação iOS incorporada** ou **Aplicação Android incorporada**. Ao utilizar o tipo de aplicação incorporada, pode escolher quais destas aplicações específicas irá publicar para os utilizadores dos dispositivos.

 Nas edições anteriores da consola do Intune, o Intune fornecia várias aplicações geridas do Office 365 predefinidas, como o Outlook e o OneDrive. O tipo de aplicação destas aplicações geridas era identificado como "Aplicação da loja iOS gerida" ou "Aplicação Android gerida". Recomendamos que utilize os tipos de aplicações incorporadas em vez de "Aplicação da loja iOS gerida" ou "Aplicação Android gerida", pois o tipo de aplicação incorporada proporciona uma maior flexibilidade para editar e eliminar aplicações do Office 365.

>[!NOTE]
>As aplicações do Office 365 predefinidas identificadas como "Aplicação da loja iOS gerida" e "Aplicação Android gerida" serão removidas da lista de aplicações quando todas as tarefas forem eliminadas para esta aplicação.

## <a name="add-built-in-app"></a>Adicionar uma aplicação incorporada

Os seguintes passos permitem-lhe adicionar uma aplicação incorporada às suas aplicações disponíveis no Microsoft Intune.
1.  Inicie sessão no portal do Azure.
2.  Apresente o painel do Microsoft Intune ao selecionar **Mais Serviços** > **Monitorização + Gestão** > **Intune**.
3.  No painel **Intune**, escolha **Aplicações móveis**.
4.  No painel **Aplicações móveis**, selecione **Aplicações** no grupo **Gerir**.
5.  Selecione **Adicionar** para adicionar uma nova aplicação.
6.  No painel **Adicionar aplicação**, selecione **Aplicação incorporada** a partir da lista **a**.
7.  Clique em **Selecionar aplicação** para escolher as aplicações incorporadas a incluir.
8.  No painel Aplicação incorporada, selecione as aplicações a incluir.
9.  No painel **Adicionar aplicação**, clique em **Adicionar** para incluir as aplicações.


## <a name="configure-app-information"></a>Configurar as informações da aplicação

Pode modificar as informações da aplicação incorporada. Estas informações ajudam-no a identificar a aplicação no Intune e também ajudam os utilizadores a encontrá-la na aplicação Portal da Empresa.
1.  No painel **Aplicações móveis – Aplicações**, selecione a aplicação incorporada que pretende modificar. É apresentado um painel para a aplicação incorporada.
2.  Selecione a opção **Propriedades** no grupo **Gerir**.
3.  Selecione a opção **Configurar** para modificar as informações da aplicação incorporada.
4.  No painel **Informações da aplicação**, pode modificar as seguintes informações:
    -   **Nome** – introduza o nome da aplicação incorporada tal como será apresentado no portal da empresa. Certifique-se de que todos os nomes que utiliza são exclusivos. Se existir o mesmo nome duas vezes, só é apresentada uma das aplicações aos utilizadores no portal da empresa.
    -   **Descrição** - Introduza uma descrição para a aplicação. 
    -   **Publicador** – Introduza o nome do publicador da aplicação.
    -   **Categoria** – opcionalmente, selecione uma ou mais das categorias de aplicações incorporadas. Esta opção permite que os utilizadores encontrem a aplicação mais facilmente quando procurarem no portal da empresa.
    -   **Apresentar esta aplicação em destaque no Portal da Empresa** – Apresente a aplicação de forma destacada na página principal do portal da empresa quando os utilizadores procurarem aplicações.
    -   **URL de Informações** – Opcionalmente, introduza o URL de um site que contenha informações sobre esta aplicação. O URL é apresentado aos utilizadores no portal da empresa.
    -   **URL de Privacidade** – Opcionalmente, introduza um URL para um site que contenha informações sobre a privacidade desta aplicação. O URL é apresentado aos utilizadores no portal da empresa.
    -   **Programador** – opcionalmente, introduza o nome do programador da aplicação.
    -   **Proprietário** – opcionalmente, introduza o nome do proprietário desta aplicação, por exemplo, Departamento de RH.
    -   **Notas** – Introduza quaisquer notas que pretenda associar esta aplicação.
    -   **Carregar Ícone** – carregue um ícone que será apresentado para a aplicação quando os utilizadores procurarem no portal da empresa.
3.  Quando terminar, clique em **OK** no painel **Informações da aplicação**.
4.  Clique em **Guardar** no painel **Propriedades**.

## <a name="next-steps"></a>Próximos passos

Agora pode atribuir as aplicações aos grupos que escolher. Para obter ajuda, veja [Como atribuir aplicações a grupos](apps-deploy.md).
