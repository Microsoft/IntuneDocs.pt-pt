---
title: Como utilizar as categorias de dispositivos no Intune
titleSuffix: Intune on Azure
description: Saiba como utilizar categorias de dispositivos que os utilizadores podem escolher quando inscrevem os dispositivos deles no Intune."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 08/09/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7b668c37-40b9-4c69-8334-5d8344e78c24
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 6c5d97499545d0ad3899f28ed4e88eb4dc1fe734
ms.sourcegitcommit: ee7f69efe9f32a1d6bdeb1fab73d03dbfe1ae58c
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/09/2017
---
# <a name="map-device-groups"></a>Mapear grupos de dispositivos


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Utilize categorias de dispositivos do Microsoft Intune para adicionar automaticamente dispositivos a grupos com base nas categorias que definir, para facilitar a gestão desses dispositivos.

As categorias de dispositivos utilizam o fluxo de trabalho seguinte:
1. Criar categorias que os utilizadores escolhem quando inscrevem o respetivo dispositivo
3. Quando os utilizadores finais de dispositivos iOS e Android inscreverem os dispositivos, têm de escolher uma categoria na lista de categorias que configurou. Para atribuir uma categoria a um dispositivo Windows, os utilizadores finais devem utilizar o site do Portal da Empresa (veja **Após configurar grupos de dispositivos** neste tópico para obter mais detalhes).
4. Nessa altura, pode implementar políticas e aplicações a estes grupos.

Pode criar as categorias de dispositivo que pretender, por exemplo:
- Dispositivo de ponto de venda
- Dispositivo de demonstração
- Vendas
- Contabilidade
- Gestor

## <a name="how-to-configure-device-categories"></a>Como configurar as categorias de dispositivos

### <a name="step-1---create-device-categories-in-the-intune-blade-of-the-azure-portal"></a>Passo 1– Criar categorias de dispositivos no painel do Intune do portal do Azure
1. No portal do Azure, selecione **Mais Serviços** > **Monitorização + Gestão** > **Intune**.
3. No painel **Intune**, selecione **Inscrição de Dispositivos**.
3. No painel **Inscrição de Dispositivos**, selecione **Categorias de Dispositivos**.
4. Na página **Categorias de Dispositivos**, escolha **Criar** para adicionar uma nova categoria.
5. No painel seguinte, introduza um **Nome** para a nova categoria e uma **Descrição** opcional.
6. Quando terminar, clique em **Criar**. Verá a categoria que acabou de criar na lista de categorias.

Irá utilizar o nome de categoria de dispositivo quando criar grupos de segurança do Azure Active Directory no Passo 2.

### <a name="step-2---create-azure-active-directory-security-groups"></a>Passo 2 – crie grupos de segurança do Azure Active Directory
Neste passo irá criar grupos dinâmicos no portal do Azure com base na categoria de dispositivo e no nome da categoria de dispositivo.

Para continuar, consulte o artigo [Using attributes to create advanced rules (Utilizar atributos para criar regras avançadas – em inglês)](https://azure.microsoft.com/documentation/articles/active-directory-accessmanagement-groups-with-advanced-rules/#using-attributes-to-create-rules-for-device-objects) na documentação do Azure Active Directory. 

Utilize as informações nesta secção para criar um grupo de dispositivos com uma regra avançada através do atributo **deviceCategory**. Por exemplo (**device.deviceCategory -eq** “*<the device category name you got from the Intune portal>*”)

Depois de configurar os grupos de dispositivos e os utilizadores inscreverem o dispositivo deles, é-lhes apresentada uma lista das categorias que configurou. Após escolherem uma categoria e terminarem a inscrição, o dispositivo deles é adicionado ao grupo de segurança do Active Directory que corresponde à categoria que escolheram.

### <a name="how-to-view-the-categories-of-devices-you-manage"></a>Como ver as categorias de dispositivos que gere

1.  No portal do Azure, selecione **Mais Serviços** > **Monitorização + Gestão** > **Intune**.

2. No painel do Intune do portal do Azure, escolha **Dispositivos e Grupos**.

3.  Em **Gerir**, clique em **Todos os dispositivos**.

4.  Na lista de dispositivos, examine a coluna **Categoria**.

Se a coluna **Categoria** não for apresentada, clique em **Colunas**, escolha **Categoria** na lista e, em seguida, clique em **Aplicar**.

### <a name="to-change-the-category-of-a-device"></a>Para alterar a categoria de um dispositivo

1. No portal do Azure, selecione **Mais Serviços** > **Monitorização + Gestão** > **Intune**.
3. No painel **Intune**, escolha **Dispositivos e Grupos**.
4. No painel **Dispositivos e Grupos**, escolha **Gerir** > **Todos os dispositivos**.
5. Na lista de dispositivos, selecione o dispositivo que pretende e, em seguida, no painel de propriedades do dispositivo, escolha **Gerir** > **Propriedades**.
6. No painel seguinte, pode alterar a **Categoria de dispositivo** do dispositivo selecionado para qualquer um dos nomes de categoria que configurou anteriormente.

## <a name="after-you-configure-device-groups"></a>Após configurar grupos de dispositivos

Quando os utilizadores finais de dispositivos iOS e Android inscreverem os dispositivos, têm de escolher uma categoria na lista de categorias que configurou. Após escolherem uma categoria e terminarem a inscrição, o respetivo dispositivo é adicionado ao grupo de dispositivos do Intune ou ao grupo de segurança do Active Directory que corresponde à categoria que escolheram.

Para atribuir uma categoria a um dispositivo Windows, os utilizadores finais devem utilizar o site do Portal da Empresa (portal.manage.microsoft.com) após a inscrição do dispositivo. Num dispositivo Windows, aceda ao site e vá para **Menu** > **Os Meus Dispositivos**. Escolha um dispositivo inscrito listado na página e, em seguida, selecione uma categoria. 

Após escolher uma categoria, o dispositivo é automaticamente adicionado ao grupo criado correspondente. Se um dispositivo já estiver inscrito antes de configurar as categorias, o utilizador final verá uma notificação sobre o dispositivo no site do Portal da Empresa e ser-lhe-á pedido para selecionar uma categoria na próxima vez que aceder à aplicação Portal da Empresa num dispositivo iOS ou Android.

## <a name="further-information"></a>Informações adicionais
- Pode editar uma categoria de dispositivo no Portal do Azure, mas se o fizer, tem de atualizar manualmente todos os grupos de segurança do Azure Active Directory que mencionam esta categoria.

- Se eliminar uma categoria, quaisquer dispositivos que lhe tenham sido atribuídos apresentarão subsequentemente o nome da categoria **Não atribuído**.


