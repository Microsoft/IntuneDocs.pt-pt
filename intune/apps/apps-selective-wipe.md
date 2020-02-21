---
title: Como eliminar apenas os dados empresariais das aplicações
titleSuffix: Microsoft Intune
description: Aprenda a limpar seletivamente apenas dados corporativos de aplicações geridas por Intune com o Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 42605e6e-5b84-44ff-b86e-346ea123b53e
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1f6992aa93e1ca5a095b1e92a16a07bd0eb1c2f5
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/20/2020
ms.locfileid: "77513644"
---
# <a name="how-to-wipe-only-corporate-data-from-intune-managed-apps"></a>Como eliminar apenas dados empresariais de aplicações geridas pelo Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Quando um dispositivo se perde ou é roubado ou se o funcionário sair da sua empresa, quer ter a certeza de que os dados empresariais da aplicação são removidos do dispositivo. No entanto, é recomendável não remover os dados pessoais do dispositivo, especialmente se o dispositivo pertencer ao funcionário.

>[!NOTE]
> As plataformas iOS/iPadOS, Android e Windows 10 são as únicas plataformas atualmente suportadas para limpar dados corporativos de aplicações geridas pela Intune. As aplicações geridas intune são aplicações que incluem o Intune APP SDK e têm uma conta de utilizador licenciada para a sua organização. A implementação de políticas de proteção de aplicações não é necessária para permitir a limpeza seletiva da aplicação.

Para remover seletivamente os dados de aplicações da empresa, utilize os passos neste tópico para criar um pedido de eliminação de dados. Depois de concluir o pedido, da próxima vez que a aplicação for executada no dispositivo, os dados da empresa são removidos da aplicação. Para além de criar um pedido de eliminação, pode configurar uma eliminação seletiva dos dados da sua organização como uma nova ação, caso as definições de Acesso de Políticas de Proteção de Aplicações (APP) não sejam cumpridas. Esta funcionalidade ajuda-o a proteger e remover automaticamente dados confidenciais da organização de aplicações com base em critérios pré-configurados.

>[!IMPORTANT]
> Os contactos sincronizados diretamente da aplicação para o livro de endereços nativo são removidos. Não é possível eliminar contactos que sejam sincronizados do livro de endereços nativo para outra origem externa. Atualmente, é aplicável apenas à aplicação Microsoft Outlook.

## <a name="deployed-wip-policies-without-user-enrollment"></a>Políticas de WiP implementadas sem inscrição de utilizadores
As políticas de Proteção de Informação do Windows (WIP) podem ser implementadas sem exigir que os utilizadores de MDM insuem o seu dispositivo Windows 10. Esta configuração permite que as empresas protejam os seus documentos empresariais com base na configuração do WIP, o que permite que o utilizador mantenha a gestão dos seus próprios dispositivos Windows. Assim que os documentos estiverem protegidos com uma política WIP, os dados protegidos poderão ser eliminados seletivamente por um administrador do Intune. Ao selecionar o utilizador e o dispositivo, e ao enviar um pedido de eliminação de dados, todos os dados protegidos através da política WIP ficarão inutilizáveis. A partir do Intune no portal Azure, selecione **app cliente** > app de limpeza seletiva da **App**. Para obter mais informações, veja [Criar e implementar a política de proteção de aplicações do Windows Information Protection (WIP) com o Intune](windows-information-protection-policy-create.md).

## <a name="create-a-wipe-request"></a>Criar um pedido de apagamento

1. Inscreva-se no [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selecione **Apps** > **app limpeza seletiva** > Criar pedido de **limpeza**.<br>
   O painel de pedido de **limpeza Create** é apresentado.
3. Clique em **Selecionar utilizador,** escolha o utilizador cujos dados da aplicação pretende limpar e clique em **Selecionar** na parte inferior do painel de **utilizadores Select.**

    ![Screenshot do painel 'Select user'](./media/apps-selective-wipe/apps-selective-wipe-01.png)

4. Clique **Em Selecione o dispositivo,** escolha o dispositivo e clique em **Selecionar** na parte inferior do painel **Select Device.**

    ![Screenshot do painel 'Create wipe request' onde o dispositivo é selecionado](./media/apps-selective-wipe/apps-selective-wipe-02.png)

5. Clique em **Criar** para fazer um pedido de limpeza.

O serviço cria e controla um pedido de eliminação separado para cada aplicação protegida no dispositivo, bem como o utilizador associado ao pedido de eliminação.

   ![Screenshot de 'Aplicativos cliente - App selective wipe' pane](./media/apps-selective-wipe/apps-selective-wipe-03.png)

## <a name="monitor-your-wipe-requests"></a>Monitorizar os pedidos de eliminação

Pode obter um relatório resumido que mostra o estado geral do pedido de eliminação e inclui o número de pedidos pendentes e de falhas. Para obter mais detalhes, siga estes passos:

1. No painel de limpeza seletivo da App ** > ** **Apps,** pode ver a lista dos seus pedidos agrupados pelos utilizadores. Uma vez que o sistema cria um pedido de eliminação para cada aplicação protegida em execução no dispositivo, poderá ver múltiplos pedidos para um utilizador. O estado indica se um pedido de eliminação está **pendente**, **falhou** ou se teve **êxito**.

    ![Captura de ecrã do estado do pedido de eliminação no painel Eliminação seletiva de aplicações](./media/apps-selective-wipe/wipe-request-status-1.png)

Além disso, pode ver o nome do dispositivo e o respetivo tipo de dispositivo, o que pode ser útil durante a leitura dos relatórios.

>[!IMPORTANT]
> O utilizador tem de abrir a aplicação para que a eliminação ocorra. Após efetuar o pedido, a eliminação pode durar até 30 minutos.

## <a name="delete-a-wipe-request"></a>Eliminar um pedido de eliminação

As eliminações em estado pendente são apresentadas até que as elimine manualmente. Para eliminar manualmente um pedido de eliminação:

1. No painel **Aplicações Cliente – Eliminação seletiva da aplicação**.

2. Na lista, clique com o botão direito do rato no pedido de eliminação que pretende eliminar e, em seguida, selecione **Eliminar pedido de eliminação**.

    ![Captura de ecrã da lista do pedido de eliminação no painel Eliminação seletiva de aplicações](./media/apps-selective-wipe/delete-wipe-request.png)

3. Quando lhe for pedido para confirmar a eliminação, escolha **Sim** ou **Não** e, em seguida, clique em **OK**.

## <a name="see-also"></a>Veja também
[O que é uma política de proteção de aplicações](app-protection-policy.md)

[O que é a gestão de aplicações](app-management.md)
