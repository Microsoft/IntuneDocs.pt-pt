---
title: Categorizar dispositivos em grupos no Intune
titleSuffix: Microsoft Intune
description: Saiba como categorizar dispositivos em grupos para uma gestão mais fácil.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 7b668c37-40b9-4c69-8334-5d8344e78c24
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: f2b02e840e787cd44e087c38503cbaa1fb4b084f
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/14/2019
ms.locfileid: "57389152"
---
# <a name="categorize-devices-into-groups"></a>Categorizar dispositivos em grupos

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Para facilitar a gestão de dispositivos, pode utilizar categorias de dispositivos do Microsoft Intune para adicionar automaticamente dispositivos a grupos com base nas categorias que definir.

As categorias de dispositivos utilizam o fluxo de trabalho seguinte:
1. Crie categorias para os utilizadores escolherem quando inscrevem o dispositivo.
2. Quando os utilizadores de dispositivos iOS e Android inscreverem um dispositivo, têm de escolher uma categoria na lista de categorias que configurou. Os utilizadores podem utilizar o site do Portal da Empresa para atribuir uma categoria a um dispositivo Windows.
3. Nessa altura, pode implementar políticas e aplicações a estes grupos.

Pode criar as categorias de dispositivo que pretender. Por exemplo:
- Dispositivo de ponto de venda
- Dispositivo de demonstração
- Vendas
- Contabilidade
- Gestor

## <a name="how-to-configure-device-categories"></a>Como configurar as categorias de dispositivos

### <a name="step-1-create-device-categories-on-the-intune-blade-of-the-azure-portal"></a>Passo 1: Criar categorias de dispositivos no painel Intune do portal do Azure
1. No [Intune, no portal do Azure](https://aka.ms/intuneportal), selecione **Inscrição de dispositivos**.
2. No painel **Inscrição de dispositivos**, selecione **Categorias de dispositivos**.
3. Na página **Categorias de dispositivos**, selecione **Criar** para adicionar uma nova categoria.
4. No painel **Criar categoria de dispositivo**, introduza um **Nome** para a nova categoria e uma **Descrição** opcional.
5. Quando tiver terminado, selecione **Criar**. Agora, pode ver a nova categoria na lista de categorias.

Irá utilizar o nome da categoria de dispositivo quando criar grupos de segurança do Azure Active Directory (Azure AD) no passo 2.

### <a name="step-2-create-azure-active-directory-security-groups"></a>Passo 2: Criar grupos de segurança do Azure Active Directory
Neste passo irá criar grupos dinâmicos no portal do Azure com base na categoria de dispositivo e no nome da categoria de dispositivo.

Para continuar, consulte [Using attributes to create advanced rules (Utilizar atributos para criar regras avançadas)](https://azure.microsoft.com/documentation/articles/active-directory-accessmanagement-groups-with-advanced-rules/#using-attributes-to-create-rules-for-device-objects) na documentação do Azure AD.

Utilize as informações nesta secção para criar um grupo de dispositivos com uma regra avançada através do atributo **deviceCategory**. Por exemplo: **device.deviceCategory -eq** "*o nome de categoria do dispositivo que obteve no Portal do Azure*".

Depois de configurar os grupos de dispositivos e os utilizadores inscreverem o dispositivo deles, é-lhes apresentada uma lista das categorias que configurou. Após escolherem uma categoria e terminarem a inscrição, o dispositivo deles é adicionado ao grupo de segurança do Active Directory que corresponde à categoria que escolheram.

### <a name="view-the-categories-of-devices-that-you-manage"></a>Ver as categorias de dispositivos que gere

1.  No [Intune, no portal do Azure](https://aka.ms/intuneportal), selecione **Dispositivos**.

2.  Em **Gerir**, selecione **Todos os dispositivos**.

3.  Na lista de dispositivos, examine a coluna **Categoria de dispositivo**.

Se a coluna **Categoria de dispositivos** não for apresentada, selecione **Colunas**. Selecione **Categoria de dispositivos** na lista e, em seguida, selecione **Aplicar**.

### <a name="change-the-category-of-a-device"></a>Alterar a categoria de um dispositivo

1. No [Intune, no portal do Azure](https://aka.ms/intuneportal), selecione **Dispositivos**.
2. No painel **Dispositivos**, na secção **Gerir**, selecione **Todos os dispositivos**.
3. Na lista de dispositivos, selecione o dispositivo que pretende. Em seguida, no painel de propriedades do dispositivo, na secção **Gerir**, selecione **Propriedades**.
4. No painel seguinte, pode alterar a **Categoria de dispositivo** do dispositivo selecionado para qualquer um dos nomes de categoria que configurou anteriormente.

## <a name="after-you-configure-device-groups"></a>Após configurar grupos de dispositivos

Quando os utilizadores de dispositivos iOS e Android inscreverem os dispositivos, têm de escolher uma categoria na lista de categorias que configurou. Após escolherem uma categoria e terminarem a inscrição, o respetivo dispositivo é adicionado ao grupo de dispositivos do Intune ou ao grupo de segurança do Active Directory que corresponder à categoria que escolheram.

Os utilizadores do Windows devem utilizar o site do Portal da Empresa para selecionar uma categoria.

Independentemente da plataforma, os seus utilizadores podem sempre aceder a portal.manage.microsoft.com após inscreverem o dispositivo. Peça ao utilizador que aceda ao site do Portal da Empresa e aceda a **Os Meus Dispositivos**. O utilizador pode escolher um dispositivo inscrito listado na página e, em seguida, selecionar uma categoria.

Após escolher uma categoria, o dispositivo é automaticamente adicionado ao grupo criado correspondente. Se um dispositivo já estiver inscrito antes de configurar as categorias, o utilizador verá uma notificação sobre o dispositivo no site do Portal da Empresa. Esta notificação informa o utilizador de que tem de selecionar uma categoria da próxima vez que aceder à aplicação Portal da Empresa no iOS ou Android.

## <a name="further-information"></a>Informações adicionais
- Pode editar uma categoria de dispositivos no portal do Azure, mas tem de atualizar manualmente todos os grupos de segurança do Azure AD que mencionam esta categoria.

- Se eliminar uma categoria, os dispositivos que lhe tenham sido atribuídos apresentarão o nome da categoria **Não atribuído**.
