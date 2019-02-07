---
title: Como eliminar apenas os dados empresariais das aplicações
titleSuffix: Microsoft Intune
description: Saiba como eliminar seletivamente apenas dados empresariais de aplicações geridas do Intune com o Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/24/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 42605e6e-5b84-44ff-b86e-346ea123b53e
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: c79f3db99f1023acee189b6e7a49f26d8d3fdd4c
ms.sourcegitcommit: 01d6832978cb7ca23049000950696b300a87abd4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/06/2019
ms.locfileid: "55760927"
---
# <a name="how-to-wipe-only-corporate-data-from-intune-managed-apps"></a>Como eliminar apenas dados empresariais de aplicações geridas pelo Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Quando um dispositivo se perde ou é roubado ou se o funcionário sair da sua empresa, quer ter a certeza de que os dados empresariais da aplicação são removidos do dispositivo. No entanto, é recomendável não remover os dados pessoais do dispositivo, especialmente se o dispositivo pertencer ao funcionário.

>[!NOTE]
> O iOS, Android e Windows 10 plataformas são as únicas plataformas atualmente suportadas para eliminar os dados empresariais das aplicações geridas pelo Intune. Intune as aplicações geridas são aplicações que incluem o SDK da aplicação Intune e tem uma conta de usuário licenciado para a sua organização. Implementação de políticas de proteção de aplicações não são necessários para ativar a eliminação seletiva de aplicações.

Para remover seletivamente os dados de aplicações da empresa, utilize os passos neste tópico para criar um pedido de eliminação de dados. Depois de concluir o pedido, da próxima vez que a aplicação for executada no dispositivo, os dados da empresa são removidos da aplicação. Para além de criar um pedido de eliminação, pode configurar uma eliminação seletiva dos dados da sua organização como uma nova ação, caso as definições de Acesso de Políticas de Proteção de Aplicações (APP) não sejam cumpridas. Esta funcionalidade ajuda-o a proteger e remover automaticamente dados confidenciais da organização de aplicações com base em critérios pré-configurados.

>[!IMPORTANT]
> Os contactos sincronizados diretamente da aplicação para o livro de endereços nativo são removidos. Não é possível eliminar contactos que sejam sincronizados do livro de endereços nativo para outra origem externa. Atualmente, é aplicável apenas à aplicação Microsoft Outlook.

## <a name="deployed-wip-policies-without-user-enrollment"></a>Políticas implementadas do WIP sem inscrição de utilizadores
Políticas de Windows Information Protection (WIP) podem ser implementadas sem a necessidade dos utilizadores MDM inscrever o dispositivo Windows 10. Esta configuração permite que as empresas protejam os seus documentos empresariais com base na configuração do WIP, o que permite que o utilizador mantenha a gestão dos seus próprios dispositivos Windows. Assim que os documentos estiverem protegidos com uma política WIP, os dados protegidos poderão ser eliminados seletivamente por um administrador do Intune. Ao selecionar o utilizador e o dispositivo, e ao enviar um pedido de eliminação de dados, todos os dados protegidos através da política WIP ficarão inutilizáveis. A partir do Intune no portal do Azure, selecione **aplicação de cliente** > **eliminação seletiva de aplicações**. Para obter mais informações, veja [Criar e implementar a política de proteção de aplicações do Windows Information Protection (WIP) com o Intune](windows-information-protection-policy-create.md).

## <a name="create-a-wipe-request"></a>Criar um pedido de eliminação

1.  Inicie sessão no [portal do Azure](https://portal.azure.com).

2.  Selecione **Todos os serviços**, introduza **Intune** na caixa de texto de filtro e selecione **Intune**. Quando o painel Intune for aberto, selecione o painel **Aplicações do cliente**.

    ![Captura de ecrã a mostrar o painel Microsoft Intune](./media/apps-selective-wipe01.png)

3.  No **painel Aplicações cliente**, selecione **Eliminação seletiva da aplicação**.

4.  Selecione **Novo pedido de eliminação**. É aberta a página **Novo pedido de eliminação**.

    ![Captura de ecrã da página Novo pedido de eliminação](./media/AzurePortal_MAM_NewWipeRequest.png)

5.  Selecione um utilizador e, em seguida, selecione **Selecionar** para selecionar um utilizador cujos dados da aplicação quer apagar.

6.  Em seguida, selecione **Dispositivo** no painel **Novo pedido de apagamento**. Esta ação abre o painel **Selecionar Dispositivo**, que apresenta uma lista com todos os dispositivos associados ao utilizador selecionado e também disponibiliza duas colunas: o nome do dispositivo, que é um nome amigável definido pelo utilizador, e o tipo de dispositivo, a plataforma do dispositivo. Selecione o dispositivo que pretende eliminar.

7.  Está agora novamente no painel **Novo pedido de apagamento**. Selecione **OK** para fazer um pedido de apagamento.

O serviço cria e controla um pedido de eliminação separado para cada aplicação protegida no dispositivo, bem como o utilizador associado ao pedido de eliminação.

## <a name="monitor-your-wipe-requests"></a>Monitorizar os pedidos de eliminação

Pode obter um relatório resumido que mostra o estado geral do pedido de eliminação e inclui o número de pedidos pendentes e de falhas. Para obter mais detalhes, siga estes passos:

1.  No painel **Aplicações Cliente – Eliminação seletiva da aplicação**, pode ver a lista dos pedidos agrupados por utilizadores. Uma vez que o sistema cria um pedido de eliminação para cada aplicação protegida em execução no dispositivo, poderá ver múltiplos pedidos para um utilizador. O estado indica se um pedido de eliminação está **pendente**, **falhou** ou se teve **êxito**.

    ![Captura de ecrã do estado do pedido de eliminação no painel Eliminação seletiva de aplicações](./media/wipe-request-status-1.png)

Além disso, pode ver o nome do dispositivo e o respetivo tipo de dispositivo, o que pode ser útil durante a leitura dos relatórios.

>[!IMPORTANT]
> O utilizador tem de abrir a aplicação para que a eliminação ocorra. Após efetuar o pedido, a eliminação pode durar até 30 minutos.

## <a name="delete-a-wipe-request"></a>Eliminar um pedido de eliminação

As eliminações em estado pendente são apresentadas até que as elimine manualmente. Para eliminar manualmente um pedido de eliminação:

1.  No painel **Aplicações Cliente – Eliminação seletiva da aplicação**.

2.  Na lista, clique com o botão direito do rato no pedido de eliminação que pretende eliminar e, em seguida, selecione **Eliminar pedido de eliminação**.

    ![Captura de ecrã da lista do pedido de eliminação no painel Eliminação seletiva de aplicações](./media/delete-wipe-request.png)

3.  Quando lhe for pedido para confirmar a eliminação, escolha **Sim** ou **Não** e, em seguida, clique em **OK**.

### <a name="see-also"></a>Consulte também
[O que é uma política de proteção de aplicações](app-protection-policy.md)

[O que é a gestão de aplicações](app-management.md)
