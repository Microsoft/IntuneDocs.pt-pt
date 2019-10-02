---
title: Gerenciar aplicativos VPP do Microsoft Store for Business
titleSuffix: Microsoft Intune
description: Saiba como você pode sincronizar aplicativos no Intune por meio do Microsoft Store para empresas.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/12/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 2ed5d3f0-2749-45cd-b6bf-fd8c7c08bc1b
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure, seoapril2019
ms.collection: M365-identity-device-management
ms.openlocfilehash: 94c8c1570eb70686b269da2e47046947024181e0
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71730952"
---
# <a name="how-to-manage-volume-purchased-apps-from-the-microsoft-store-for-business-with-microsoft-intune"></a>Como gerenciar aplicativos comprados por volume da Microsoft Store para empresas com o Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Na [Loja Microsoft para Empresas](https://www.microsoft.com/business-store) pode encontrar e adquirir aplicações para a sua organização, individualmente ou em volume. Ao ligar a loja ao Microsoft Intune, pode gerir as aplicações compradas em volume a partir do portal do Azure. Por exemplo:
* Você pode sincronizar a lista de aplicativos que comprou (ou que são gratuitos) da loja com o Intune.
* As aplicações que são sincronizadas aparecem na consola de administração do Intune. Pode atribuí-las como todas as outras aplicações.
* As versões licenciadas online e offline dos aplicativos são sincronizadas com o Intune. Os nomes de aplicativo serão anexados a "online" ou "offline" no Portal.
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
1. Certifique-se de entrar no [Microsoft Store para negócios](https://www.microsoft.com/business-store) usando a mesma conta de locatário usada para entrar no Intune.
2. Na loja de negócios, escolha a guia **gerenciar** , selecione **configurações**e escolha a guia **distribuir** .
3. Se você não tiver especificamente **Microsoft Intune** disponível como uma ferramenta de gerenciamento de dispositivo móvel, escolha **Adicionar ferramenta de gerenciamento** para adicionar **Microsoft Intune**. Se você não tiver **Microsoft Intune** ativado como sua ferramenta de gerenciamento de dispositivo móvel, clique em **Ativar** ao lado de **Microsoft Intune**. Observe que você deve ativar **Microsoft Intune** em vez de **Microsoft Intune registro**.

> [!NOTE]
> Anteriormente, só podia associar uma ferramenta de gestão para atribuir aplicações com a Loja Microsoft para Empresas. Agora, pode associar várias ferramentas de gestão com a loja, como o Intune e o Configuration Manager. 

Agora, pode continuar e configurar a sincronização na consola do Intune.

## <a name="configure-synchronization"></a>Configurar a sincronização

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. No painel **Intune**, selecione **Aplicações do cliente**.
1. No painel **Aplicações do cliente**, selecione **Configurar** > **Microsoft Store para Empresas**.
2. Clique em **Ativar**.
3. Se ainda não o fez, clique na ligação para se inscrever na Loja Microsoft para Empresas e associe a sua conta conforme explicado anteriormente.
5. Na lista pendente **Idioma**, selecione o idioma no qual as aplicações da Microsoft Store para Empresas são apresentadas no portal do Azure. Independentemente do idioma em que são apresentadas, serão instaladas no idioma do utilizador final, se estiver disponível.
6. Clique em **Sincronização** para obter as aplicações que comprou na Loja Microsoft para o Intune.

## <a name="synchronize-apps"></a>Sincronizar aplicações

1. Na carga de trabalho **Aplicações do cliente**, selecione **Configurar** > **Microsoft Store para Empresas**.
2. Clique em **Sincronização** para obter as aplicações que comprou na Loja Microsoft para o Intune.

> [!NOTE]
> Não há suporte para aplicativos com pacotes de aplicativos criptografados no momento e eles não serão sincronizados com o Intune.

## <a name="assign-apps"></a>Atribuir aplicações

As aplicações da loja são atribuídas da mesma forma que atribui qualquer outra aplicação Intune. Para obter mais informações, veja [Como atribuir aplicações a grupos com o Microsoft Intune](apps-deploy.md). 

As aplicações offline podem ser direcionadas para grupos de utilizadores, grupos de dispositivos ou grupo com utilizadores e dispositivos.
As aplicações offline podem ser instaladas para um utilizador específico num dispositivo ou para todos os utilizadores num dispositivo. 


Quando atribui uma aplicação da Loja Microsoft para Empresas, é utilizada uma licença por cada utilizador que instalar a aplicação. Se utilizar todas as licenças disponíveis para uma aplicação atribuída, não poderá atribuir mais cópias. Efetue uma das seguintes ações:
* Desinstale a aplicação de dispositivos.
* Reduza o âmbito da atribuição atual, segmentando apenas os utilizadores para os quais tem licenças suficientes.
* Compre mais cópias da aplicação na Loja Microsoft para Empresas.

## <a name="remove-apps"></a>Remover aplicações

Para remover uma aplicação sincronizada a partir da Microsoft Store para Empresas, tem de iniciar sessão na Microsoft Store para Empresas e reembolsar a aplicação. O processo é o mesmo se o aplicativo é gratuito ou não. Para um aplicativo gratuito, a loja receberá o reembolso de $0. O exemplo a seguir mostra um reembolso para um aplicativo gratuito. 

![Captura de ecrã a mostrar os detalhes da remoção da aplicação](./media/windows-store-for-business/microsoft-store-for-business-01.png)

> [!NOTE]
> Remover a visibilidade de um aplicativo no armazenamento privado não impedirá que o Intune Sincronize o aplicativo. Você deve reembolsar o aplicativo para remover totalmente o aplicativo.

## <a name="next-steps"></a>Passos seguintes

- [Gerir aplicações e livros comprados em grandes volumes com o Microsoft Intune](../vpp-apps.md)
