---
title: "Gerir aplicações a partir da Loja Microsoft para Empresas"
titlesuffix: Azure portal
description: "Saiba como pode sincronizar aplicações no Intune a partir da Loja Microsoft para Empresas e, em seguida, atribuir e controlá-las."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 06/28/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2ed5d3f0-2749-45cd-b6bf-fd8c7c08bc1b
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 649766b26a1061c4bce11235c04dcbe8570fcdc4
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/09/2017
---
# <a name="how-to-manage-apps-you-purchased-from-the-microsoft-store-for-business-with-microsoft-intune"></a>Como gerir aplicações compradas na Loja Microsoft para Empresas com o Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]


Na [Loja Microsoft para Empresas](https://www.microsoft.com/business-store) pode encontrar e adquirir aplicações para a sua organização, individualmente ou em volume. Ao ligar a loja ao Microsoft Intune, pode gerir as aplicações compradas em volume a partir do portal do Azure. Por exemplo:
* Pode sincronizar a lista de aplicações adquiridas na loja com o Intune.
* As aplicações que são sincronizadas aparecem na consola de administração do Intune. Pode atribuí-las como todas as outras aplicações.
* Pode controlar quantas licenças estão disponíveis e quantas estão a ser utilizadas na consola de administração do Intune.
* O Intune bloqueará a atribuição e instalação de aplicações se tiver um número insuficiente de licenças disponíveis.

## <a name="before-you-start"></a>Antes de começar

Antes de iniciar a sincronização e a atribuição de aplicações da Loja Microsoft para Empresas, reveja as seguintes informações:

- Configure o Intune como a autoridade de gestão de dispositivos móveis da sua organização.
- Tem de se ter inscrito numa conta na Loja Microsoft para Empresas.
- Assim que tiver associado uma conta da Loja Windows para Empresas, não pode mudar para uma conta diferente no futuro.
- As aplicações compradas na loja não podem ser adicionadas ou eliminadas manualmente do Intune. Só podem ser sincronizadas com a Loja Microsoft para Empresas.
- O Intune sincroniza as aplicações licenciadas online e offline que comprou na Loja Microsoft para Empresas.
- Só é possível sincronizar aplicações offline gratuitas com o Intune.
- Para utilizar esta funcionalidade, os dispositivos têm de ser associados aos Active Directory Domain Services ou à área de trabalho.
- Os dispositivos inscritos têm de utilizar a versão 1511 do Windows 10 ou posterior.

## <a name="associate-your-microsoft-store-for-business-account-with-intune"></a>Associar a sua conta da Loja Microsoft para Empresas ao Intune
Antes de ativar a sincronização na consola do Intune, tem de configurar a conta da loja para utilizar o Intune como ferramenta de gestão:
1. Certifique-se de que se regista na Loja para Empresas com a mesma conta de inquilino que utiliza para iniciar sessão no Intune.
2. Na Loja para Empresas, escolha **Definições** > **Ferramentas de gestão**.
3. Na página Ferramentas de gestão, escolha **Adicionar uma ferramenta de gestão** e **Microsoft Intune**.

> [!NOTE]
> Anteriormente, só podia associar uma ferramenta de gestão para atribuir aplicações com a Loja Microsoft para Empresas. Agora, pode associar várias ferramentas de gestão com a loja, como o Intune e o Configuration Manager.

Agora, pode continuar e configurar a sincronização na consola do Intune.

## <a name="configure-synchronization"></a>Configurar a sincronização

1. Inicie sessão no portal do Azure.
2. Escolha **Mais Serviços** > **Monitorização + Gestão** > **Intune**.
3. No painel **Intune**, escolha **Aplicações móveis**.
1. No painel **Aplicações Móveis**, selecione **Configuração** > **Loja Microsoft para Empresas**.
2. Clique em **Ativar**.
3. Se ainda não o fez, clique na ligação para se inscrever na Loja Microsoft para Empresas e associe a sua conta conforme explicado anteriormente.
5. Na lista pendente **Idioma**, selecione o idioma no qual as aplicações da Loja Microsoft para Empresas são apresentadas no portal do Azure. Independentemente do idioma em que são apresentadas, serão instaladas no idioma do utilizador final, se estiver disponível.
6. Clique em **Sincronização** para obter as aplicações que comprou na Loja Microsoft para o Intune.

## <a name="synchronize-apps"></a>Sincronizar aplicações

1. Na carga de trabalho **Aplicações móveis**, selecione **Configuração** > **Loja Microsoft para Empresas**.
2. Clique em **Sincronização** para obter as aplicações que comprou na Loja Microsoft para o Intune.

## <a name="assign-apps"></a>Atribuir aplicações

As aplicações da loja são atribuídas da mesma forma que atribui qualquer outra aplicação Intune. Para obter mais informações, veja [Como atribuir aplicações a grupos com o Microsoft Intune](apps-deploy.md). No entanto, em vez de atribuir aplicações a partir da página **Todas as Aplicações**, deve atribuí-las a partir da página **Aplicações Licenciadas**.

As aplicações offline podem ser direcionadas para grupos de utilizadores, grupos de dispositivos ou grupo com utilizadores e dispositivos.
As aplicações offline podem ser instaladas para um utilizador específico num dispositivo ou para todos os utilizadores num dispositivo. 


Quando atribui uma aplicação da Loja Microsoft para Empresas, é utilizada uma licença por cada utilizador que instalar a aplicação. Se utilizar todas as licenças disponíveis para uma aplicação atribuída, não poderá atribuir mais cópias. Efetue uma das seguintes ações:
* Desinstale a aplicação de dispositivos.
* Reduza o âmbito da atribuição atual, segmentando apenas os utilizadores para os quais tem licenças suficientes.
* Compre mais cópias da aplicação na Loja Microsoft para Empresas.


