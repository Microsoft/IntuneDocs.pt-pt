---
title: "Eliminar dados de aplicações geridas pela empresa"
description: Saiba como pode remover de forma seletiva dados da empresa de dispositivos remotamente.
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 01/25/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2742e1d5-d2d5-42cd-b719-665dd6e0a0e9
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: df3c42d8b52d1a01ddab82727e707639d5f77c16
ms.openlocfilehash: 7025bdd5d89e52f1c99f9cd834232daf324f3285
ms.contentlocale: pt-pt
ms.lasthandoff: 06/08/2017


---

# <a name="wipe-company-app-data-with-intune-mam"></a>Eliminar dados da aplicação da empresa com o Intune MAM

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Quando um dispositivo se perde ou é roubado ou se o funcionário sair da sua empresa, quer ter a certeza de que os dados empresariais da aplicação são removidos do dispositivo. No entanto, poderá não querer remover os dados pessoais do dispositivo, especialmente se o dispositivo pertencer ao funcionário.

Para remover seletivamente os dados de aplicações da empresa, utilize os passos neste tópico para criar um pedido de eliminação de dados. Depois de concluir o pedido, da próxima vez que a aplicação for executada no dispositivo, os dados da empresa são removidos da aplicação.

>[!IMPORTANT]
> Os contactos sincronizados diretamente da aplicação para o livro de endereços nativo são removidos. Não é possível limpar contactos sincronizados do livro de endereços nativo para outra origem externa. Atualmente, é aplicável apenas à aplicação Microsoft Outlook.

## <a name="create-a-wipe-request"></a>Criar um pedido de eliminação

1.  Inicie sessão no [portal do Azure](https://portal.azure.com).

2.  Escolha **Mais Serviços**, introduza **Intune**, na caixa de texto do filtro, e selecione **Intune App Protection**. O painel de gestão de aplicações móveis do Intune abre-se.

    ![Captura de ecrã do painel Novo pedido de eliminação](../media/AppManagement/wipe-request-mam-main-blade.png)

2.  No painel **Definições**, escolha **Pedidos de eliminação**.

3.  Selecione **Novo pedido de eliminação**. É aberto o painel **Novo pedido de eliminação**.

    ![Captura de ecrã do painel Novo pedido de eliminação](../media/AppManagement/AzurePortal_MAM_NewWipeRequest.png)

4.  Selecione **Utilizador** para abrir o painel **Utilizador** e selecione o utilizador cujos dados da aplicação quer apagar.

5.  Escolha **Dispositivo**. Esta ação abre o painel **Dispositivo**, que apresenta uma lista com todos os dispositivos associados ao utilizador selecionado e também disponibiliza duas colunas: o nome do dispositivo, que é um nome amigável definido pelo utilizador, e o tipo de dispositivo, a plataforma do dispositivo. Selecione o dispositivo que pretende eliminar.

6.  Está agora novamente no painel **Novo pedido de eliminação**. Escolha **Ok** para fazer um pedido de eliminação. 

O serviço cria e controla um pedido de eliminação separado para cada aplicação protegida no dispositivo, bem como o utilizador associado ao pedido de eliminação.

>[!NOTE]
> Também pode criar **Pedidos de eliminação** ao clicar no **Mosaico de pedido de eliminação**, no painel de gestão de aplicações móveis do Intune.

## <a name="monitor-your-wipe-requests"></a>Monitorizar os pedidos de eliminação

Pode obter um relatório resumido que mostra o estado geral do pedido de eliminação e inclui o número de pedidos pendentes e de falhas. Para obter mais detalhes, siga estes passos:

1.  No painel de gestão de aplicações móveis do Intune, clique no mosaico **Pedidos de eliminação**.

2.  No painel **Pedido de eliminação**, selecione o mosaico **Pedido de eliminação** para abrir o painel **Pedido de eliminação**.

3.  No painel **Pedido de eliminação**, pode ver a lista dos pedidos agrupados por utilizadores. Uma vez que o sistema cria um pedido de eliminação para cada aplicação protegida em execução no dispositivo, poderá ver múltiplos pedidos para um utilizador. O estado indica se um pedido de eliminação está **pendente**, **falhou** ou se teve **êxito**.

    ![Captura de ecrã do painel Novo pedido de eliminação](../media/AppManagement/wipe-request-status-1.png)

Além disso, poderá ver o nome do dispositivo e o respetivo tipo de dispositivo, o que pode ser útil durante a leitura dos relatórios.

>[!IMPORTANT]
> O utilizador tem de abrir a aplicação para que a eliminação ocorra. Após efetuar o pedido, a eliminação pode durar até 30 minutos.

## <a name="delete-a-wipe-request"></a>Eliminar um pedido de eliminação

As eliminações em estado pendente são apresentadas até que as elimine manualmente.  Para eliminar manualmente um pedido de eliminação

1.  No painel de gestão de aplicações móveis do Intune, clique no mosaico **Pedidos de eliminação**.

2.  No painel **Pedido de eliminação**, selecione o mosaico **Pedido de eliminação** para abrir o painel **Pedido de eliminação**.

3.  Clique com o botão direito do rato no pedido de eliminação que quer eliminar e, em seguida, escolha **Eliminar pedido de eliminação**.

    ![Captura de ecrã do painel Novo pedido de eliminação](../media/AppManagement/delete-wipe-request.png)

4.  Quando lhe for pedido para confirmar a eliminação, escolha **Sim** ou **Não** e, em seguida, clique em **OK**.


### <a name="see-also"></a>Consulte também
[Proteger dados de aplicações através de políticas de gestão de aplicações móveis](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)

[Utilizar o portal do Azure](azure-portal-for-microsoft-intune-mam-policies.md)

