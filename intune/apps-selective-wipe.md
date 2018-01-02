---
title: "Como eliminar apenas os dados empresariais das aplicações"
titleSuffix: Azure portal
description: "Saiba como realizar a eliminação seletiva de aplicações com o Microsoft Intune.\""
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/05/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 42605e6e-5b84-44ff-b86e-346ea123b53e
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 206aef4185934448418d7b080ab94af94e792e74
ms.sourcegitcommit: ad97d658682bf563638521856931e2709e40e14b
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/09/2017
---
# <a name="how-to-wipe-only-corporate-data-from-intune-managed-apps"></a>Como eliminar apenas dados empresariais de aplicações geridas pelo Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Quando um dispositivo se perde ou é roubado ou se o funcionário sair da sua empresa, quer ter a certeza de que os dados empresariais da aplicação são removidos do dispositivo. No entanto, poderá não querer remover os dados pessoais do dispositivo, especialmente se o dispositivo pertencer ao funcionário.

>[!NOTE]
> As plataformas iOS e Android são as duas plataformas atualmente suportadas para eliminar dados empresariais das aplicações geridas pelo Intune.

Para remover seletivamente os dados de aplicações da empresa, utilize os passos neste tópico para criar um pedido de eliminação de dados. Depois de concluir o pedido, da próxima vez que a aplicação for executada no dispositivo, os dados da empresa são removidos da aplicação.

>[!IMPORTANT]
> Os contactos sincronizados diretamente da aplicação para o livro de endereços nativo são removidos. Não é possível limpar contactos sincronizados do livro de endereços nativo para outra origem externa. Atualmente, é aplicável apenas à aplicação Microsoft Outlook.

## <a name="create-a-wipe-request"></a>Criar um pedido de eliminação

1.  Inicie sessão no [portal do Azure](https://portal.azure.com).

2.  Escolha **Mais Serviços**, introduza **Intune** na caixa de texto de filtro e selecione **Intune**. Quando for apresentado o painel do Intune, selecione o painel **Aplicações móveis**.

    ![Captura de ecrã a mostrar o painel do Microsoft Intune](./media/apps-selective-wipe01.png)

3.  No **painel Aplicações móveis**, selecione **Eliminação seletiva de aplicações**.

4.  Selecione **Novo pedido de eliminação**. É aberto o painel **Novo pedido de eliminação**.

    ![Captura de ecrã do painel Novo pedido de eliminação](./media/AzurePortal_MAM_NewWipeRequest.png)

5.  Selecione **Utilizador** para abrir o painel **Utilizador** e selecione o utilizador cujos dados da aplicação quer apagar.

6.  Em seguida, selecione **Dispositivo** no painel **Novo pedido de eliminação**. Esta ação abre o painel **Selecionar Dispositivo**, que apresenta uma lista com todos os dispositivos associados ao utilizador selecionado e também disponibiliza duas colunas: o nome do dispositivo, que é um nome amigável definido pelo utilizador, e o tipo de dispositivo, a plataforma do dispositivo. Selecione o dispositivo que pretende eliminar.

7.  Está agora novamente no painel **Novo pedido de eliminação**. Escolha **Ok** para fazer um pedido de eliminação.

O serviço cria e controla um pedido de eliminação separado para cada aplicação protegida no dispositivo, bem como o utilizador associado ao pedido de eliminação.

## <a name="monitor-your-wipe-requests"></a>Monitorizar os pedidos de eliminação

Pode obter um relatório resumido que mostra o estado geral do pedido de eliminação e inclui o número de pedidos pendentes e de falhas. Para obter mais detalhes, siga estes passos:

1.  No painel **Aplicações Móveis – Eliminação seletiva de aplicações**, pode ver a lista dos pedidos agrupados por utilizadores. Uma vez que o sistema cria um pedido de eliminação para cada aplicação protegida em execução no dispositivo, poderá ver múltiplos pedidos para um utilizador. O estado indica se um pedido de eliminação está **pendente**, **falhou** ou se teve **êxito**.

    ![Captura de ecrã a mostrar o estado do pedido de eliminação no painel Eliminação seletiva de aplicações](./media/wipe-request-status-1.png)

Além disso, poderá ver o nome do dispositivo e o respetivo tipo de dispositivo, o que pode ser útil durante a leitura dos relatórios.

>[!IMPORTANT]
> O utilizador tem de abrir a aplicação para que a eliminação ocorra. Após efetuar o pedido, a eliminação pode durar até 30 minutos.

## <a name="delete-a-wipe-request"></a>Eliminar um pedido de eliminação

As eliminações em estado pendente são apresentadas até que as elimine manualmente.  Para eliminar manualmente um pedido de eliminação:

1.  No painel **Aplicações Móveis – Eliminação seletiva de aplicações**.

2.  Na lista, clique com o botão direito do rato no pedido de eliminação que pretende eliminar e, em seguida, selecione **Eliminar pedido de eliminação**.

    ![Captura de ecrã a mostrar a lista do pedido de eliminação no painel Eliminação seletiva de aplicações](./media/delete-wipe-request.png)

3.  Quando lhe for pedido para confirmar a eliminação, escolha **Sim** ou **Não** e, em seguida, clique em **OK**.

### <a name="see-also"></a>Veja também
[O que é uma política de proteção de aplicações](app-protection-policy.md)

[O que é a gestão de aplicações](app-management.md)
