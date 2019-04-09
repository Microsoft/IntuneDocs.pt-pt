---
title: Gerir adquiridas em grandes volumes ou gratuitos aplicações da Microsoft Store para empresas
titleSuffix: Microsoft Intune
description: Saiba como pode sincronizar aplicações adquiridas (ou gratuitas) no Intune a partir da Microsoft Store para empresas.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/08/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 2ed5d3f0-2749-45cd-b6bf-fd8c7c08bc1b
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure, seoapril2019
ms.collection: M365-identity-device-management
ms.openlocfilehash: 895101f2102e019c291609915a4407d1dad4c81c
ms.sourcegitcommit: 364a7dbc7eaa414c7a9c39cf53eb4250e1ad3151
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2019
ms.locfileid: "59292283"
---
# <a name="how-to-manage-volume-purchased-or-free-apps-from-the-microsoft-store-for-business-with-microsoft-intune"></a>Como gerir aplicações de volume adquiridas (ou gratuitas) a partir da Microsoft Store para empresas com o Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Na [Loja Microsoft para Empresas](https://www.microsoft.com/business-store) pode encontrar e adquirir aplicações para a sua organização, individualmente ou em volume. Ao ligar a loja ao Microsoft Intune, pode gerir as aplicações compradas em volume a partir do portal do Azure. Por exemplo:
* Pode sincronizar a lista de aplicações que comprou (ou que são gratuitas) na loja com o Intune.
* As aplicações que são sincronizadas aparecem na consola de administração do Intune. Pode atribuí-las como todas as outras aplicações.
* Pode controlar quantas licenças estão disponíveis e quantas estão a ser utilizadas na consola de administração do Intune.
* O Intune bloqueará a atribuição e instalação de aplicações se tiver um número insuficiente de licenças disponíveis.
* As aplicações geridas pela Microsoft Store para Empresas revogam as licenças automaticamente quando um utilizador sai da empresa ou quando o administrador remove o utilizador e os dispositivos do mesmo.

## <a name="before-you-start"></a>Antes de começar

Antes de iniciar a sincronização e a atribuição de aplicações da Loja Microsoft para Empresas, reveja as seguintes informações:

- Configure o Intune como a autoridade de gestão de dispositivos móveis da sua organização.
- Tem de se ter inscrito numa conta na Loja Microsoft para Empresas.
- Após associar uma conta da Microsoft Store para Empresas, não pode mudar para uma conta diferente no futuro.
- As aplicações compradas na loja não podem ser adicionadas ou eliminadas manualmente do Intune. Só podem ser sincronizadas com a Loja Microsoft para Empresas.
- As aplicações licenciadas online e offline que comprou na Microsoft Store para Empresas são sincronizadas no portal do Intune. Poderá então implementar essas aplicações em grupos de dispositivos ou grupos de utilizadores. 
- As instalações de aplicações online são geridas pela loja.
- As aplicações offline gratuitas também podem ser sincronizadas com o Intune. Estas aplicações são instaladas pelo Intune e não pela loja.
- Para utilizar esta funcionalidade, os dispositivos têm de ser associados aos Active Directory Domain Services ou à área de trabalho.
- Os dispositivos inscritos têm de utilizar a versão 1511 do Windows 10 ou posterior.

Além disso, as aplicações Licenciadas Offline e os conjuntos relacionados sincronizados a partir da Microsoft Store para Empresas serão consolidados numa única entrada de aplicação na IU. Todos os detalhes da implementação dos pacotes individuais serão migrados para uma única entrada. Para ver os conjuntos relacionados no portal do Azure, selecione **Licenças de aplicação** no painel **Aplicações do cliente**.

## <a name="associate-your-microsoft-store-for-business-account-with-intune"></a>Associar a sua conta da Loja Microsoft para Empresas ao Intune
Antes de ativar a sincronização na consola do Intune, tem de configurar a conta da loja para utilizar o Intune como ferramenta de gestão:
1. Certifique-se de que inicia sessão para o [Microsoft Store para empresas](https://www.microsoft.com/business-store) usando a mesma conta de inquilino que utiliza para iniciar sessão no Intune.
2. No Store empresas, escolha o **Manage** separador, selecione **definições**e escolha o **distribuir** separador.
3. Se não tiver especificamente **Microsoft Intune** disponível como uma ferramenta de gerenciamento de dispositivo móvel, escolha **ferramenta de gerenciamento de Add** adicionar **Microsoft Intune**. Se não tiver **Microsoft Intune** ativado como sua ferramenta de gestão de dispositivos móveis, clique em **ativar** junto a **Microsoft Intune**. Tenha em atenção que deve ativar **Microsoft Intune** vez **inscrição do Microsoft Intune**.

> [!NOTE]
> Anteriormente, só podia associar uma ferramenta de gestão para atribuir aplicações com a Loja Microsoft para Empresas. Agora, pode associar várias ferramentas de gestão com a loja, como o Intune e o Configuration Manager. 

Agora, pode continuar e configurar a sincronização na consola do Intune.

## <a name="configure-synchronization"></a>Configurar a sincronização

1. Inicie sessão no [Portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços** > **Intune**. O Intune encontra-se na secção **Monitorização + Gestão**.
3. No painel **Intune**, selecione **Aplicações do cliente**.
1. No painel **Aplicações do cliente**, selecione **Configurar** > **Microsoft Store para Empresas**.
2. Clique em **Ativar**.
3. Se ainda não o fez, clique na ligação para se inscrever na Loja Microsoft para Empresas e associe a sua conta conforme explicado anteriormente.
5. Na lista pendente **Idioma**, selecione o idioma no qual as aplicações da Microsoft Store para Empresas são apresentadas no portal do Azure. Independentemente do idioma em que são apresentadas, serão instaladas no idioma do utilizador final, se estiver disponível.
6. Clique em **Sincronização** para obter as aplicações que comprou na Loja Microsoft para o Intune.

## <a name="synchronize-apps"></a>Sincronizar aplicações

1. Na carga de trabalho **Aplicações do cliente**, selecione **Configurar** > **Microsoft Store para Empresas**.
2. Clique em **Sincronização** para obter as aplicações que comprou na Loja Microsoft para o Intune.

## <a name="assign-apps"></a>Atribuir aplicações

As aplicações da loja são atribuídas da mesma forma que atribui qualquer outra aplicação Intune. Para obter mais informações, veja [Como atribuir aplicações a grupos com o Microsoft Intune](apps-deploy.md). 

As aplicações offline podem ser direcionadas para grupos de utilizadores, grupos de dispositivos ou grupo com utilizadores e dispositivos.
As aplicações offline podem ser instaladas para um utilizador específico num dispositivo ou para todos os utilizadores num dispositivo. 


Quando atribui uma aplicação da Loja Microsoft para Empresas, é utilizada uma licença por cada utilizador que instalar a aplicação. Se utilizar todas as licenças disponíveis para uma aplicação atribuída, não poderá atribuir mais cópias. Efetue uma das seguintes ações:
* Desinstale a aplicação de dispositivos.
* Reduza o âmbito da atribuição atual, segmentando apenas os utilizadores para os quais tem licenças suficientes.
* Compre mais cópias da aplicação na Loja Microsoft para Empresas.

## <a name="remove-apps"></a>Remover aplicações

Para remover uma aplicação sincronizada a partir da Microsoft Store para Empresas, tem de iniciar sessão na Microsoft Store para Empresas e reembolsar a aplicação. O processo é o mesmo se a aplicação é gratuita ou não. Para uma aplicação gratuita, o arquivo irão reembolsar a US $0. O exemplo abaixo mostra um reembolso de uma aplicação gratuita. 

![Captura de ecrã a mostrar os detalhes da remoção da aplicação](./media/microsoft-store-for-business-01.png)

> [!NOTE]
> A remover de visibilidade de uma aplicação da loja privada não manter Intune a sincronizar a aplicação. Tem de reembolso da aplicação para remover completamente a aplicação.

## <a name="next-steps"></a>Passos Seguintes

- [Gerir aplicações e livros comprados em grandes volumes com o Microsoft Intune](vpp-apps.md)
