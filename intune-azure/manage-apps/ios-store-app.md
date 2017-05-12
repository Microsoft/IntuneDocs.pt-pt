---
title: "Como adicionar aplicações da loja iOS ao Intune | Microsoft Docs"
titleSuffix: Intune Azure preview
description: "Pré-visualização do Azure no Intune: saiba mais sobre como adicionar aplicações da loja iOS ao Intune."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 05/04/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c59514d7-1256-4576-9380-e7a0b85a0378
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 3758df744311392528be01c826527c2a9d879975
ms.openlocfilehash: 011f33d1d8569a079f73baaca6ba2a665131691d
ms.contentlocale: pt-pt
ms.lasthandoff: 05/10/2017

---

# <a name="how-to-add-ios-store-apps-to-microsoft-intune"></a>Como adicionar aplicações da loja iOS ao Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

## <a name="before-you-start"></a>Antes de começar

Só poderá atribuir aplicações com este método se forem gratuitas na app store. Se pretender atribuir aplicações pagas com o Intune, considere utilizar o [programa de compra em volume do iOS](ios-vpp-apps.md).


## <a name="step-1---search-for-the-app-in-the-store"></a>Passo 1 – Procurar a aplicação na loja

1. Inicie sessão no portal do Azure.
2. Escolha **Mais Serviços** > **Monitorização + Gestão** > **Intune**.
3. No painel **Intune**, escolha **Gerir aplicações**.
4. Na carga de trabalho **Aplicações móveis**, escolha **Gerir** > Aplicações.
5. Acima da lista de aplicações, escolha **Adicionar**.
6. No painel **Adicionar Aplicação**, escolha **Procurar na App Store**.
7. No painel **Apple App Store**, introduza o nome (ou parte do nome) na caixa de pesquisa. O Intune procura na loja e devolve uma lista de resultados relevantes.
8. Na lista, selecione a aplicação que quer e, em seguida, clique em **OK**.

## <a name="step-2---configure-app-information"></a>Passo 2 – Configurar as informações da aplicação

1. No painel **Adicionar Aplicação**, escolha **Informações da Aplicação**.
2. No painel **Editar Aplicação**, configure as informações seguintes. Quando tiver terminado, clique em **Adicionar**. Consoante a aplicação que tenha escolhido, alguns dos valores neste painel podem ter sido preenchidos automaticamente:
- **Nome da Aplicação** – Introduza o nome da aplicação tal como será apresentado no portal da empresa. Certifique-se de que todos os nomes de aplicações que utiliza são exclusivos. Se o mesmo nome de aplicação existir duas vezes, apenas uma das aplicações será apresentada aos utilizadores no portal da empresa.
    - **Descrição da Aplicação** – Introduza uma descrição para a aplicação. A descrição será apresentada aos utilizadores no portal da empresa.
- **Publicador** - Introduza o nome do publicador da aplicação.
- **URL da loja de aplicações** – Introduza o URL da loja de aplicações da aplicação que pretende criar.
- **Sistema Operativo Mínimo** – Na lista, escolha a versão mínima do sistema operativo no qual a aplicação pode ser instalada. Se atribuir a aplicação a um dispositivo com um sistema operativo anterior, não será instalada.
- **Categoria** (opcional). Selecione uma ou mais categorias das aplicações incorporadas ou, em alternativa, uma categoria criada por si. Isto irá permitir que os utilizadores encontrem a aplicação mais facilmente quando procurarem no portal da empresa.
- **Apresentar esta aplicação em destaque no Portal da Empresa** – Apresente a aplicação de forma destacada na página principal do portal da empresa quando os utilizadores procurarem aplicações.
- **URL de Informações** – Opcionalmente, introduza o URL de um site que contenha informações sobre esta aplicação. O URL será apresentado aos utilizadores no portal da empresa.
- **URL de Privacidade** – Opcionalmente, introduza um URL para um site que contenha informações sobre a privacidade desta aplicação. O URL será apresentado aos utilizadores no portal da empresa.
- **Programador** – Opcionalmente, introduza o nome do programador da aplicação.
- **Proprietário** – Opcionalmente, introduza um nome para o proprietário desta aplicação, por exemplo, **Departamento de RH**.
- **Notas** – Introduza quaisquer notas que pretenda associar esta aplicação.
- **Carregar Ícone** – Carregue um ícone que será associado à aplicação. Este é o ícone que será apresentado com a aplicação quando os utilizadores procurarem no portal da empresa.
3. Quando terminar, no painel **Adicionar Aplicação**, escolha **Guardar**.

A aplicação que criou será apresentada na lista de aplicações onde a pode atribuir aos grupos que escolher. Para obter ajuda, veja [Como atribuir aplicações a grupos](deploy-apps.md).

