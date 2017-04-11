---
title: "Como adicionar aplicações ao Microsoft Intune"
titleSuffix: Intune Azure preview
description: "Pré-visualização do Azure no Intune: estes procedimentos ajudam-no a preparar as suas aplicações no Intune para serem atribuídas a utilizadores e dispositivos. "
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a1ded457-0ecf-4f9c-a2d2-857d57f8d30a
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: 296e7db9be18323b44cc79592c981f5d7241602f
ms.lasthandoff: 02/18/2017

---

# <a name="how-to-add-an-app-to-microsoft-intune"></a>Como adicionar uma aplicação ao Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Para poder gerir e atribuir aplicações aos utilizadores, tem de adicioná-las ao Intune. O Intune suporta uma vasta gama de tipos de aplicações diferentes, pelo que as opções podem ser diferentes consoante o tipo.

O Intune suporta a adição e atribuição destes tipos de aplicação:

![Tipos de aplicação suportados pelo Intune](./media/app-types.png)

São suportadas as seguintes plataformas. Clique num dos tópicos para obter mais informações sobre como adicionar cada tipo de aplicação.

- [Aplicações de linha de negócios Android](/intune-azure/manage-apps/android-lob-app)
- [Aplicações da loja Android](/intune-azure/manage-apps/android-store-app)
- [Aplicações de linha de negócios iOS](/intune-azure/manage-apps/ios-lob-app)
- [Aplicações da loja iOS](/intune-azure/manage-apps/ios-store-app)
- [Aplicações Web (para todas as plataformas)](/intune-azure/manage-apps/web-app)
- [Aplicações da loja Windows Phone 8.1](/intune-azure/manage-apps/windows-phone-8-1-store-app)
- [Aplicações da loja Windows](/intune-azure/manage-apps/windows-store-app)

> [!NOTE]
> Quando adicionar e implementar uma aplicação a partir de uma loja, os utilizadores finais têm de ter uma conta nessa loja para conseguir instalar a aplicação.

## <a name="cloud-storage-space"></a>Espaço de armazenamento na cloud
Todas as aplicações que criar com o tipo de instalação do instalador de software (por exemplo, uma aplicação de linha de negócio) são empacotadas e carregadas para o armazenamento na cloud do Microsoft Intune. Uma subscrição de avaliação do Intune inclui 2 gigabytes (GB) de armazenamento baseado na cloud, o qual é utilizado para armazenar aplicações e atualizações geridas. A subscrição completa inclui 20 GB de espaço de armazenamento.

Pode comprar armazenamento adicional para o Intune com o seu método de compra original.  Se tiver pago através de fatura ou cartão de crédito, visite o [Portal de Gestão de Subscrições](https://portal.office.com/adminportal/home?switchtomodern=true#/subscriptions).  Caso contrário, contacte o seu parceiro ou representante de vendas.

Requisitos de espaço de armazenamento na cloud:

-   Todos os ficheiros de instalação da aplicação têm de estar na mesma pasta.
-   O tamanho máximo para qualquer ficheiro que carregar é de 2 GB.

## <a name="how-to-create-and-edit-categories-for-apps"></a>Como criar e editar categorias para as aplicações 

As categorias de aplicações podem ser utilizadas para o ajudar a ordenar as aplicações de modo a serem mais fáceis de encontrar por parte dos utilizadores finais no portal da empresa. Pode atribuir uma ou mais categorias a uma aplicação, por exemplo, **Aplicações de programador** ou **Aplicações de comunicação**. Quando adiciona uma aplicação ao Intune, é-lhe dada a opção de selecionar a categoria que quiser. Utilize os tópicos das plataformas específicas para adicionar uma aplicação e atribuir categorias. Para criar e editar as suas próprias categorias, utilize o seguinte procedimento: 

1. Inicie sessão no portal do Azure. 
2. Escolha **Mais Serviços** > **Monitorização + Gestão** > **Intune**. 
3. No painel **Intune**, escolha **Gerir aplicações**. 
4. Na carga de trabalho **Aplicações móveis**, escolha **Configuração** > **Categorias de aplicações**. 
5. No painel **Categorias aplicações**, é apresentada uma lista das categorias atuais. Escolha uma das seguintes ações: 
    - **Criar uma categoria** – No painel **Criar categoria**, introduza um nome para a nova categoria. Os nomes podem ser introduzidos em apenas um idioma e não são traduzidos pelo Intune. Quando terminar, clique em **Criar**.
    - **Editar uma categoria** – Para qualquer categoria na lista, escolha “**...**”. No painel **Propriedades**, pode introduzir um novo nome para a categoria ou eliminá-la.




