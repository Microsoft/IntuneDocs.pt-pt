---
title: "Como adicionar aplicações da loja Android ao Microsoft Intune"
titleSuffix: 
description: "Saiba mais sobre como adicionar aplicações da loja Android ao Microsoft Intune."
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/26/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4433000a-23e9-4cad-a818-48c28eedc1f5
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 87fea551dea1f80ee071fe6b477b84729e000874
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/08/2018
---
# <a name="how-to-add-android-store-apps-to-microsoft-intune"></a>Como adicionar aplicações da loja Android ao Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Antes de atribuir uma aplicação a um dispositivo ou grupo de utilizadores, tem de primeiro adicionar a aplicação ao Microsoft Intune. Os passos seguintes permitem-lhe adicionar uma aplicação da loja Android ao Intune a partir do portal do Azure.

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços** > **Intune**. O Intune encontra-se na secção **Monitorização + Gestão**.
3. No painel **Intune**, selecione **Aplicações móveis**.
4. Na carga de trabalho **Aplicações móveis**, selecione **Aplicações** na secção **Gerir**.
5. Acima da lista de aplicações, escolha **Adicionar**.
6. No painel **Adicionar Aplicação**, selecione **Android** nos tipos de **Aplicações da loja** disponíveis.
7. Selecione **Configurar** para configurar as seguintes informações da aplicação (consoante a aplicação que tenha selecionado, alguns dos valores neste painel podem ter sido preenchidos automaticamente):
    - **Nome** - Introduza o nome da aplicação tal como será apresentado no portal da empresa. Certifique-se de que todos os nomes de aplicações que utiliza são exclusivos. Se existir o mesmo nome duas vezes, só é apresentada uma das aplicações aos utilizadores no portal da empresa.
    - **Descrição** - Introduza uma descrição para a aplicação. A descrição será apresentada aos utilizadores no portal da empresa.
    - **Publicador** – Introduza o nome do publicador da aplicação.
    - **URL da loja de aplicações** – introduza o URL da loja de aplicações da aplicação que pretende criar.
    - **Sistema operativo mínimo** – na lista, selecione a versão mínima do sistema operativo no qual a aplicação pode ser instalada. Se atribuir a aplicação a um dispositivo com um sistema operativo anterior, não será instalada.
    - **Categoria** (opcional) – Selecione uma ou mais categorias das aplicações incorporadas ou, em alternativa, uma categoria criada por si. Isto irá permitir que os utilizadores encontrem a aplicação mais facilmente quando procurarem no portal da empresa.
    - **Apresentar esta aplicação em destaque no Portal da Empresa** – Apresente a aplicação de forma destacada na página principal do portal da empresa quando os utilizadores procurarem aplicações.
    - **URL de informações** (opcional) – introduza o URL de um site que contenha informações sobre esta aplicação. O URL será apresentado aos utilizadores no portal da empresa.
    - **URL de privacidade** (opcional) – introduza um URL para um site que contenha informações sobre a privacidade desta aplicação. O URL será apresentado aos utilizadores no portal da empresa.
    - **Programador** (opcional) – introduza o nome do programador da aplicação.
    - **Proprietário** (opcional) – introduza o nome do proprietário desta aplicação. Por exemplo, **Departamento de RH**.
    - **Notas** (opcional) – introduza quaisquer notas que pretenda associar esta aplicação.
    - **Logótipo** (opcional) – carregue um ícone que será associado à aplicação. Este ícone é apresentado com a aplicação quando os utilizadores procurarem no portal da empresa.
8. Clique em **OK** depois de adicionar as informações à aplicação.
9. Clique em **Adicionar** para adicionar a aplicação.

A aplicação que criou será apresentada na lista de aplicações, onde a pode atribuir aos grupos que escolher. 

##<a name="next-steps"></a>Próximos passos

- [Como atribuir aplicações a grupos](apps-deploy.md)