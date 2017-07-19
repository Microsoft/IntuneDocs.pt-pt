---
title: "Como adicionar aplicações ao Microsoft Intune"
titleSuffix: Intune on Azure
description: "Estes procedimentos ajudam-no a preparar as suas aplicações no Intune para serem atribuídas a utilizadores e dispositivos. \""
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 06/28/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a1ded457-0ecf-4f9c-a2d2-857d57f8d30a
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 6a4dfa9e0066a2ac6f410aa9f8e4d77a40484ea5
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/01/2017
---
# <a name="how-to-add-an-app-to-microsoft-intune"></a>Como adicionar uma aplicação ao Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Para poder gerir e atribuir aplicações aos utilizadores, tem de adicioná-las ao Intune. O Intune suporta uma vasta gama de tipos de aplicações diferentes, pelo que as opções podem ser diferentes consoante o tipo.

O Intune permite-lhe adicionar e atribuir estes tipos de aplicação:

![Tipos de aplicação suportados pelo Intune](./media/app-types.png)

São suportadas as seguintes plataformas.

- Aplicações da loja Android
- Aplicações de linha de negócio (LOB) Android
- Aplicações da loja iOS
- Aplicações de linha de negócio (LOB) iOS
- Aplicações Web
- Aplicações da loja Windows Phone 8.1
- Aplicações de linha de negócio do Windows Phone (ficheiros .xap)
- Aplicações da loja Windows
- Aplicações de linha de negócio do Windows (apenas ficheiros .msi)

>[!TIP]
> Uma aplicação de linha de negócio (ou LOB) é instalada a partir do ficheiro de instalação da aplicação em vez de uma loja de aplicações. Por exemplo, para instalar uma aplicação LOB iOS, adicione o ficheiro de arquivo da aplicação (com a extensão .ipa). Normalmente, são aplicações criadas internamente.

## <a name="before-you-start"></a>Antes de começar

Considere os seguintes pontos antes de começar a adicionar e a atribuir as aplicações.

- Quando adicionar e atribuir uma aplicação a partir de uma loja, os utilizadores finais têm de ter uma conta nessa loja para conseguir instalar a aplicação.
- Algumas aplicações ou itens que atribuir poderão estar dependentes de aplicações iOS incorporadas. Por exemplo, se atribuir um livro a partir da loja iOS, a aplicação iBooks terá de estar presente no dispositivo. Se tiver removido a aplicação iBooks incorporada, não poderá utilizar o Intune para a restabelecer.

## <a name="cloud-storage-space"></a>Espaço de armazenamento na cloud
Todas as aplicações que criar com o tipo de instalação do instalador de software (por exemplo, uma aplicação de linha de negócio) são empacotadas e carregadas para o armazenamento na cloud do Intune. Uma subscrição de avaliação do Intune inclui 2 gigabytes (GB) de armazenamento baseado na cloud, o qual é utilizado para armazenar aplicações e atualizações geridas. Uma subscrição completa inclui 20 GB de espaço de armazenamento.

Pode comprar armazenamento adicional para o Intune com o seu método de compra original.  Se tiver pago através de fatura ou cartão de crédito, visite o [Portal de Gestão de Subscrições](https://portal.office.com/adminportal/home?switchtomodern=true#/subscriptions).  Caso contrário, contacte o seu parceiro ou representante de vendas.

Requisitos de espaço de armazenamento na cloud:

-   Todos os ficheiros de instalação da aplicação têm de estar na mesma pasta.
-   O tamanho máximo para qualquer ficheiro que carregar é de 2 GB.

## <a name="how-to-create-and-edit-categories-for-apps"></a>Como criar e editar categorias para as aplicações

As categorias de aplicações podem ser utilizadas para o ajudar a ordenar as aplicações de modo a serem mais fáceis de encontrar por parte dos utilizadores no portal da empresa. Pode atribuir uma ou mais categorias a uma aplicação, por exemplo, **Aplicações de programador** ou **Aplicações de comunicação**.
Quando adiciona uma aplicação ao Intune, é-lhe dada a opção de selecionar a categoria que quiser. Utilize os tópicos das plataformas específicas para adicionar uma aplicação e atribuir categorias. Para criar e editar as suas próprias categorias, utilize o seguinte procedimento:

1. Inicie sessão no portal do Azure.
2. Escolha **Mais Serviços** > **Monitorização + Gestão** > **Intune**.
3. No painel **Intune**, escolha **Aplicações móveis**.
4. Na carga de trabalho **Aplicações móveis**, escolha **Configuração** > **Categorias de aplicações**.
5. No painel **Categorias aplicações**, é apresentada uma lista das categorias atuais. Escolha uma das seguintes ações:
    - **Criar uma categoria** – No painel **Criar categoria**, introduza um nome para a nova categoria. Os nomes podem ser introduzidos em apenas um idioma e não são traduzidos pelo Intune. Quando terminar, clique em **Criar**.
    - **Editar uma categoria** – Para qualquer categoria na lista, escolha “**...**”. No painel **Propriedades**, pode introduzir um novo nome para a categoria ou eliminá-la.


## <a name="apps-added-automatically-by-intune"></a>Aplicações adicionadas automaticamente pelo Intune

As seguintes aplicações publicadas pela Microsoft estão incorporadas no Intune e estão prontas a ser atribuídas:

|||
|-|-|
|Nome|Plataforma|Tipo de aplicação|
|Azure Information Protection|Android|Aplicação da loja Android gerida|
|Dynamics CRM para Telemóveis|Android|Aplicação da loja Android gerida|
|Dynamics CRM para Tablets|Android|Aplicação da loja Android gerida|
|Excel|iOS|Aplicação da loja iOS gerida|
|Excel|Android|Aplicação da loja Android gerida|
|Browser Gerido|Android|Aplicação da loja Android gerida|
|Browser Gerido|iOS|Aplicação da loja iOS gerida|
|Microsoft Dynamics CRM em Telemóveis|iOS|Aplicação da loja iOS gerida|
|Microsoft Dynamics CRM em Tablets|iOS|Aplicação da loja iOS gerida|
|Microsoft Power BI|iOS|Aplicação da loja iOS gerida|
|Microsoft Power BI|Android|Aplicação da loja Android gerida|
|Microsoft SharePoint|iOS|Aplicação da loja iOS gerida|
|Microsoft SharePoint|Android|Aplicação da loja Android gerida|
|Microsoft Teams|Android|Aplicação da loja Android gerida|
|Microsoft Teams|iOS|Aplicação da loja iOS gerida|
|OneDrive para Empresas|iOS|Aplicação da loja iOS gerida|
|OneDrive para Empresas|Android|Aplicação da loja Android gerida|
|OneNote|iOS|Aplicação da loja iOS gerida|
|Outlook|Android|Aplicação da loja Android gerida|
|Outlook|iOS|Aplicação da loja iOS gerida|
|Grupos do Outlook|Android|Aplicação da loja Android gerida|
|Grupos do Outlook|iOS|Aplicação da loja iOS gerida|
|PowerPoint|iOS|Aplicação da loja iOS gerida|

## <a name="next-steps"></a>Passos Seguintes

Escolha um dos seguintes tópicos para saber como adicionar aplicações para cada plataforma ao Intune:

- [Aplicações da loja Android](store-apps-android.md)
- [Aplicações LOB Android](lob-apps-android.md)
- [Aplicações da loja iOS](store-apps-ios.md)
- [Aplicações LOB iOS](lob-apps-ios.md)
- [Aplicações Web (para todas as plataformas)](web-app.md)
- [Aplicações da loja Windows Phone 8.1](store-apps-windows-phone-8-1.md)
- [Aplicações LOB para Windows Phone](lob-apps-windows-phone.md)
- [Aplicações da loja Windows](store-apps-windows.md)
- [Aplicação LOB do Windows](lob-apps-windows.md)

