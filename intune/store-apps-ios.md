---
title: Como adicionar aplicações da loja iOS ao Microsoft Intune
titlesuffix: ''
description: Saiba mais sobre como adicionar aplicações da loja iOS ao Microsoft Intune.
keywords: Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/06/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: c59514d7-1256-4576-9380-e7a0b85a0378
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 4eaa4b279ab98c6fe41482628937e0f2b0dc70a5
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-add-ios-store-apps-to-microsoft-intune"></a>Como adicionar aplicações da loja iOS ao Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Utilize as informações neste artigo para ajudá-lo a adicionar aplicações da loja iOS ao Microsoft Intune. As aplicações da loja iOS são aplicações que o Intune instala no dispositivo do utilizador. O utilizador faz parte da força de trabalho da sua empresa. As aplicações da loja iOS são atualizadas automaticamente.

>[!NOTE]
>Apesar de os utilizadores de dispositivos iOS poderem remover algumas aplicações iOS incorporadas, tal como Bolsa e Mapas, não pode utilizar o Intune para implementar novamente essas aplicações. Se os utilizadores finais eliminarem essas aplicações, têm de aceder à loja de aplicações e reinstalar manualmente.

## <a name="before-you-start"></a>Antes de começar

Só poderá atribuir aplicações com este método se forem gratuitas na app store. Se pretender atribuir aplicações pagas com o Intune, considere utilizar o [programa de compra em volume do iOS](vpp-apps-ios.md).

>[!NOTE]
>O Chrome e o Edge são os browsers recomendados ao trabalhar com o Microsoft Intune.

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços** > **Intune**. O Intune encontra-se na secção **Monitorização + Gestão**.
3. No painel **Intune**, escolha **Aplicações móveis**.
4. Na carga de trabalho **Aplicações móveis**, selecione **Aplicações** na secção **Gerir**.
5. Selecione **Adicionar** no lado direito do painel **Aplicações**.
6. Na lista **Tipo de aplicação**, selecione **iOS** nos tipos de **Aplicação da loja** disponíveis.
7. Selecione **Procurar na App Store**.
8. No painel **Procurar na App Store**, selecione a região da loja de aplicações.
9. Escreva o nome (ou parte do mesmo) na caixa de pesquisa. O Intune procura na loja e apresenta uma lista de resultados relevantes.
10. Na lista, selecione a aplicação que pretende e, em seguida, clique em **Selecionar**.
11. No painel **Adicionar aplicação**, selecione **Informações da aplicação** para configurar a aplicação.
12. No painel **Informações da aplicação**, adicione as informações da aplicação. Consoante a aplicação que tenha escolhido, alguns dos valores neste painel podem ter sido preenchidos automaticamente:
    - **Nome** – escreva o nome da aplicação a apresentar no portal da empresa. Certifique-se de que todos os nomes de aplicações que utiliza são exclusivos. Se o mesmo nome de aplicação existir duas vezes, o portal da empresa só apresentará uma das aplicações aos utilizadores.
    - **Descrição** – escreva uma descrição da aplicação a apresentar aos utilizadores no portal da empresa.
    - **Publicador** - escreva o nome do publicador da aplicação.
    - **URL da loja de aplicações** – escreva o URL da loja de aplicações da aplicação que pretende criar.
    - **Sistema operativo mínimo** – na lista, selecione a versão mínima do sistema operativo no qual a aplicação pode ser instalada. A aplicação não será instalada num dispositivo com um sistema operativo anterior.
    - **Tipo de dispositivo aplicável** – a partir da lista, selecione os dispositivos utilizados pela aplicação.
    - **Categoria** (opcional). Selecione uma ou mais categorias das aplicações incorporadas ou, em alternativa, uma categoria criada por si. As categorias permitem que os utilizadores encontrem a aplicação mais facilmente quando procurarem no portal da empresa.
    - **Apresentar esta aplicação em destaque no Portal da Empresa** – apresentar a aplicação de forma destacada na página principal do portal da empresa quando os utilizadores procurarem aplicações.
    - **URL de informações** – opcionalmente, escreva o URL de um site que contenha informações sobre esta aplicação. O URL é apresentado aos utilizadores no portal da empresa.
    - **URL de Privacidade** – opcionalmente, escreva um URL para um site que contenha informações sobre a privacidade desta aplicação. O URL é apresentado aos utilizadores no portal da empresa.
    - **Programador** – opcionalmente, escreva o nome do programador da aplicação. Este campo só é visível para o administrador e não estará visível para os utilizadores finais.
    - **Proprietário** – opcionalmente, escreva um nome para o proprietário desta aplicação, por exemplo, **Departamento de RH**.  Este campo só é visível para o administrador e não estará visível para os utilizadores finais.
    - **Notas** – escreva as notas que pretende associar esta aplicação. Este campo só é visível para o administrador e não estará visível para os utilizadores finais.
    - **Logótipo** – carregue um ícone associado à aplicação. O ícone é apresentado com a aplicação quando os utilizadores procurarem no portal da empresa.
13. Quando tiver terminado, clique em **OK** no painel **Adicionar informações**.
14. Clique em **Adicionar** no painel **Adicionar aplicação**.

A aplicação que criou é apresentada na lista de aplicações, onde pode atribuí-la aos grupos que escolher.

## <a name="next-steps"></a>Próximos passos

- [Como atribuir aplicações a grupos](apps-deploy.md)
