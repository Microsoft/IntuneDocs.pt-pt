---
title: "Como adicionar aplicações da loja iOS ao Intune | Microsoft Docs"
titlesuffix: Azure portal
description: "Saiba mais sobre como adicionar aplicações da loja iOS ao Intune.\""
keywords: Intune
author: Erikre
ms.author: erikre
manager: angrobe
ms.date: 09/18/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c59514d7-1256-4576-9380-e7a0b85a0378
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 7dcb857127b3c36d2b90208aac9b8ad901e31d89
ms.sourcegitcommit: 833b1921ced35be140f0107d0b4205ecacd2753b
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/04/2018
---
# <a name="how-to-add-ios-store-apps-to-microsoft-intune"></a>Como adicionar aplicações da loja iOS ao Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]


Utilize as informações neste tópico para ajudá-lo a adicionar aplicações da loja iOS ao Intune.

>[!NOTE]
>Apesar de os utilizadores de dispositivos iOS poderem remover algumas aplicações iOS incorporadas, tal como Bolsa e Mapas, não pode utilizar o Intune para implementar novamente essas aplicações. Se os utilizadores finais eliminarem essas aplicações, têm de aceder à App Store e reinstalar manualmente.

## <a name="before-you-start"></a>Antes de começar

Só poderá atribuir aplicações com este método se forem gratuitas na app store. Se pretender atribuir aplicações pagas com o Intune, considere utilizar o [programa de compra em volume do iOS](vpp-apps-ios.md).


## <a name="step-1---search-for-the-app-in-the-store"></a>Passo 1 – Procurar a aplicação na loja

1. Inicie sessão no portal do Azure.
2. Escolha **Mais Serviços** > **Monitorização + Gestão** > **Intune**.
3. No painel **Intune**, escolha **Gerir aplicações**.
4. Na carga de trabalho **Aplicações móveis**, escolha **Gerir** > Aplicações.
5. Acima da lista de aplicações, escolha **Adicionar**.
6. No painel **Adicionar Aplicação**, escolha **Procurar na App Store**.
7. No painel **Apple App Store**, selecione a região/país onde se encontra a utilizar a App Store.
8. Escreva o nome (ou parte do mesmo) na caixa de pesquisa. O Intune procura na loja e apresenta uma lista de resultados relevantes.
9. Na lista, selecione a aplicação que quer e, em seguida, clique em **OK**.

## <a name="step-2---configure-app-information"></a>Passo 2 – Configurar as informações da aplicação

1. No painel **Adicionar Aplicação**, escolha **Informações da Aplicação**.
2. No painel **Editar Aplicação**, configure as informações da aplicação. Quando tiver terminado, clique em **Adicionar**. Consoante a aplicação que tenha escolhido, alguns dos valores neste painel podem ter sido preenchidos automaticamente:
- **Nome** – escreva o nome da aplicação a apresentar no portal da empresa. Certifique-se de que todos os nomes de aplicações que utiliza são exclusivos. Se o mesmo nome de aplicação existir duas vezes, o portal da empresa só apresentará uma das aplicações aos utilizadores.
- **Descrição** – escreva uma descrição da aplicação a apresentar aos utilizadores no portal da empresa.
- **Publicador** - escreva o nome do publicador da aplicação.
- **URL da loja de aplicações** – escreva o URL da loja de aplicações da aplicação que pretende criar.
- **Região/país da App Store** – selecione o país/região em que está a utilizar a App Store.
- **Sistema operativo mínimo** – na lista, selecione a versão mínima do sistema operativo no qual a aplicação pode ser instalada. A aplicação não será instalada num dispositivo com um sistema operativo anterior.
- **Tipo de dispositivo aplicável** – a partir da lista, selecione os dispositivos utilizados pela aplicação.
- **Categoria** (opcional). Selecione uma ou mais categorias das aplicações incorporadas ou, em alternativa, uma categoria criada por si. As categorias permitem que os utilizadores encontrem a aplicação mais facilmente quando procurarem no portal da empresa.
- **Apresentar esta aplicação em destaque no Portal da Empresa** – apresentar a aplicação de forma destacada na página principal do portal da empresa quando os utilizadores procurarem aplicações.
- **URL de informações** – opcionalmente, escreva o URL de um site que contenha informações sobre esta aplicação. O URL é apresentado aos utilizadores no portal da empresa.
- **URL de Privacidade** – opcionalmente, escreva um URL para um site que contenha informações sobre a privacidade desta aplicação. O URL é apresentado aos utilizadores no portal da empresa.
- **Programador** – opcionalmente, escreva o nome do programador da aplicação. Este campo só é visível para o administrador e não estará visível aos utilizadores finais.
- **Proprietário** – opcionalmente, escreva um nome para o proprietário desta aplicação, por exemplo, **Departamento de RH**.  Este campo só é visível para o administrador e não estará visível aos utilizadores finais.
- **Notas** – escreva as notas que pretende associar esta aplicação. Este campo só é visível para o administrador e não estará visível aos utilizadores finais.
- **Logótipo** – carregue um ícone associado à aplicação. O ícone é apresentado com a aplicação quando os utilizadores procurarem no portal da empresa.
3. Quando terminar, no painel **Adicionar Aplicação**, selecione **OK**.

A aplicação que criou é apresentada na lista de aplicações, onde pode atribuí-la aos grupos que escolher. Para obter ajuda, veja [Como atribuir aplicações a grupos](apps-deploy.md).
