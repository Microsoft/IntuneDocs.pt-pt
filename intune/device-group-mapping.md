---
title: Como categorizar dispositivos em grupos no Intune
titleSuffix: Microsoft Intune
description: "Saiba como categorizar dispositivos em grupos para uma gestão mais fácil."
keywords: 
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 12/11/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7b668c37-40b9-4c69-8334-5d8344e78c24
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 416ce4fb671494efabf805595426f25d027d256e
ms.sourcegitcommit: aafed032492c1b5861d7097a335f9bbb29ce3221
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/02/2018
---
# <a name="categorize-devices-into-groups-for-easier-management"></a>Categorizar dispositivos em grupos para uma gestão mais fácil

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Utilize categorias de dispositivos do Microsoft Intune para adicionar automaticamente dispositivos a grupos com base nas categorias que definir, para facilitar a gestão desses dispositivos.

As categorias de dispositivos utilizam o fluxo de trabalho seguinte:
1. Crie categorias para os utilizadores escolherem quando inscrevem o dispositivo.
2. Quando os utilizadores finais de dispositivos iOS e Android inscreverem os dispositivos, têm de escolher uma categoria na lista de categorias que configurou. Para atribuir uma categoria a um dispositivo Windows, os utilizadores finais têm de utilizar o site do Portal da Empresa (para obter mais informações, veja **Após configurar grupos de dispositivos** neste artigo).
3. Nessa altura, pode implementar políticas e aplicações a estes grupos.

Pode criar as categorias de dispositivo que pretender, por exemplo:
- Dispositivo de ponto de venda
- Dispositivo de demonstração
- Vendas
- Contabilidade
- Gestor

## <a name="how-to-configure-device-categories"></a>Como configurar as categorias de dispositivos

### <a name="step-1---create-device-categories-in-the-intune-blade-of-the-azure-portal"></a>Passo 1– Criar categorias de dispositivos no painel do Intune do portal do Azure
1. No [portal do Azure](https://portal.azure.com), selecione **Todos os serviços** > **Intune**. O Intune encontra-se na secção **Monitorização + Gestão**.
3. No painel **Intune**, selecione **Inscrição de dispositivos**.
3. No painel **Inscrição de dispositivos**, selecione **Categorias de dispositivos**.
4. Na página **Categorias de dispositivos**, selecione **Criar** para adicionar uma nova categoria.
5. No painel **Criar categoria de dispositivo**, introduza um **Nome** para a nova categoria e uma **Descrição** opcional.
6. Quando terminar, clique em **Criar**. Agora, pode ver a nova categoria na lista de categorias.

Irá utilizar o nome de categoria de dispositivo quando criar grupos de segurança do Azure Active Directory no Passo 2.

### <a name="step-2---create-azure-active-directory-security-groups"></a>Passo 2 – crie grupos de segurança do Azure Active Directory
Neste passo irá criar grupos dinâmicos no portal do Azure com base na categoria de dispositivo e no nome da categoria de dispositivo.

Para continuar, veja o artigo [Utilizar atributos para criar regras avançadas](https://azure.microsoft.com/documentation/articles/active-directory-accessmanagement-groups-with-advanced-rules/#using-attributes-to-create-rules-for-device-objects) na documentação do Azure Active Directory.

Utilize as informações nesta secção para criar um grupo de dispositivos com uma regra avançada através do atributo **deviceCategory**. Por exemplo, (**device.deviceCategory -eq** "*<the device category name you got from the Azure portal>*")

Depois de configurar os grupos de dispositivos e os utilizadores inscreverem o dispositivo deles, é-lhes apresentada uma lista das categorias que configurou. Após escolherem uma categoria e terminarem a inscrição, o dispositivo deles é adicionado ao grupo de segurança do Active Directory que corresponde à categoria que escolheram.

### <a name="how-to-view-the-categories-of-devices-you-manage"></a>Como ver as categorias de dispositivos que gere

1.  No [portal do Azure](https://portal.azure.com), selecione **Todos os serviços** > **Intune**. O Intune encontra-se na secção **Monitorização + Gestão**.

2. No painel do Intune do portal do Azure, selecione **Dispositivos**.

3.  Em **Gerir**, clique em **Todos os dispositivos**.

4.  Na lista de dispositivos, examine a coluna **Categoria de dispositivo**.

Se a coluna **Categoria de dispositivo** não for apresentada, clique em **Colunas**, selecione **Categoria de dispositivo** na lista e, em seguida, clique em **Aplicar**.

### <a name="to-change-the-category-of-a-device"></a>Para alterar a categoria de um dispositivo

1. No [portal do Azure](https://portal.azure.com), selecione **Todos os serviços** > **Intune**. O Intune encontra-se na secção **Monitorização + Gestão**.
3. No painel **Intune**, escolha **Dispositivos**.
4. No painel **Dispositivos**, na secção **Gerir**, selecione **Todos os dispositivos**.
5. Na lista de dispositivos, selecione o que pretende e, em seguida, no painel de propriedades do dispositivo, na secção **Gerir**, selecione **Propriedades**.
6. No painel seguinte, pode alterar a **Categoria de dispositivo** do dispositivo selecionado para qualquer um dos nomes de categoria que configurou anteriormente.

## <a name="after-you-configure-device-groups"></a>Após configurar grupos de dispositivos

Quando os utilizadores finais de dispositivos iOS e Android inscreverem os dispositivos, têm de escolher uma categoria na lista de categorias que configurou. Após escolherem uma categoria e terminarem a inscrição, o respetivo dispositivo é adicionado ao grupo de dispositivos do Intune ou ao grupo de segurança do Active Directory que corresponde à categoria que escolheram.

Os utilizadores finais em dispositivos Windows devem utilizar o site Portal da Empresa para selecionar uma categoria.

Independentemente da plataforma, os seus utilizadores podem sempre aceder a portal.manage.microsoft.com após inscreverem o dispositivo. Peça ao utilizador que aceda ao site do Portal da Empresa e aceda a **Os Meus Dispositivos**. Podem escolher um dispositivo inscrito listado na página e, em seguida, selecionar uma categoria.

Após escolher uma categoria, o dispositivo é automaticamente adicionado ao grupo criado correspondente. Se um dispositivo já estiver inscrito antes de configurar as categorias, o utilizador final verá uma notificação sobre o dispositivo no site do Portal da Empresa e ser-lhe-á pedido para selecionar uma categoria na próxima vez que aceder à aplicação Portal da Empresa num dispositivo iOS ou Android.

## <a name="further-information"></a>Informações adicionais
- Pode editar uma categoria de dispositivos no portal do Azure, mas tem de atualizar manualmente todos os Grupos de segurança do Azure Active Directory que mencionam esta categoria.

- Se eliminar uma categoria, os dispositivos que lhe tenham sido atribuídos apresentarão o nome da categoria **Não atribuído**.
