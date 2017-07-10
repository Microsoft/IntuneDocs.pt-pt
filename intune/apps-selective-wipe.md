---
title: "Como eliminar apenas os dados empresariais das aplicações"
titleSuffix: Intune on Azure
description: "Saiba como realizar a eliminação seletiva de aplicações com o Microsoft Intune.\""
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 02/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 42605e6e-5b84-44ff-b86e-346ea123b53e
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: bfebc391997ac4e63466eb3a09044318cf807dbc
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/01/2017
---
# <a name="how-to-wipe-only-corporate-data-from-intune-managed-apps"></a>Como eliminar apenas dados empresariais de aplicações geridas pelo Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Quando um dispositivo se perde ou é roubado ou se o funcionário sair da sua empresa, quer ter a certeza de que os dados empresariais da aplicação são removidos do dispositivo. No entanto, poderá não querer remover os dados pessoais do dispositivo, especialmente se o dispositivo pertencer ao funcionário.

Para remover seletivamente os dados de aplicações da empresa, utilize os passos neste tópico para criar um pedido de eliminação de dados. Depois de concluir o pedido, da próxima vez que a aplicação for executada no dispositivo, os dados da empresa são removidos da aplicação.

>[!IMPORTANT]
> Os contactos sincronizados diretamente da aplicação para o livro de endereços nativo são removidos. Não é possível limpar contactos sincronizados do livro de endereços nativo para outra origem externa. Atualmente, é aplicável apenas à aplicação Microsoft Outlook.

## <a name="create-a-wipe-request"></a>Criar um pedido de eliminação

1.  Inicie sessão no [portal do Azure](https://portal.azure.com).

2.  Escolha **Mais Serviços**, introduza **Intune** na caixa de texto de filtro e selecione **Intune**. Quando for apresentado o painel do Intune, escolha o painel **Gerir aplicações**.

    ![Captura de ecrã do painel Novo pedido de eliminação](./media/intune-azure-preview-blade.png)

3.  No painel **Aplicações Móveis**, escolha **Novo pedido de apagamento**. É aberto o painel **Novo pedido de eliminação**.

4.  Selecione **Novo pedido de eliminação**. É aberto o painel **Novo pedido de eliminação**.

    ![Captura de ecrã do painel Novo pedido de eliminação](./media/AzurePortal_MAM_NewWipeRequest.png)

5.  Selecione **Utilizador** para abrir o painel **Utilizador** e selecione o utilizador cujos dados da aplicação quer apagar.

6.  Escolha **Dispositivo**. Esta ação abre o painel **Dispositivo**, que apresenta uma lista com todos os dispositivos associados ao utilizador selecionado e também disponibiliza duas colunas: o nome do dispositivo, que é um nome amigável definido pelo utilizador, e o tipo de dispositivo, a plataforma do dispositivo. Selecione o dispositivo que pretende eliminar.

7.  Está agora novamente no painel **Novo pedido de eliminação**. Escolha **Ok** para fazer um pedido de eliminação. 

O serviço cria e controla um pedido de eliminação separado para cada aplicação protegida no dispositivo, bem como o utilizador associado ao pedido de eliminação.

## <a name="monitor-your-wipe-requests"></a>Monitorizar os pedidos de eliminação

Pode obter um relatório resumido que mostra o estado geral do pedido de eliminação e inclui o número de pedidos pendentes e de falhas. Para obter mais detalhes, siga estes passos:

1.  No painel **Aplicações Móveis – Eliminação Seletiva de Aplicações**, pode ver a lista dos pedidos agrupados por utilizadores. Uma vez que o sistema cria um pedido de eliminação para cada aplicação protegida em execução no dispositivo, poderá ver múltiplos pedidos para um utilizador. O estado indica se um pedido de eliminação está **pendente**, **falhou** ou se teve **êxito**.

    ![Captura de ecrã do painel Novo pedido de eliminação](./media/wipe-request-status-1.png)

Além disso, poderá ver o nome do dispositivo e o respetivo tipo de dispositivo, o que pode ser útil durante a leitura dos relatórios.

>[!IMPORTANT]
> O utilizador tem de abrir a aplicação para que a eliminação ocorra. Após efetuar o pedido, a eliminação pode durar até 30 minutos.

## <a name="delete-a-wipe-request"></a>Eliminar um pedido de eliminação

As eliminações em estado pendente são apresentadas até que as elimine manualmente.  Para eliminar manualmente um pedido de eliminação:

1.  No painel **Pedido de eliminação**, selecione o mosaico **Pedido de eliminação** para abrir o painel **Pedido de eliminação**.

2.  Clique com o botão direito do rato no pedido de eliminação que quer eliminar e, em seguida, escolha **Eliminar pedido de eliminação**.

    ![Captura de ecrã do painel Novo pedido de eliminação](./media/delete-wipe-request.png)

3.  Quando lhe for pedido para confirmar a eliminação, escolha **Sim** ou **Não** e, em seguida, clique em **OK**.

### <a name="see-also"></a>Veja também
[O que é uma política de proteção de aplicações](app-protection-policy.md)

[O que é a gestão de aplicações](app-management.md)