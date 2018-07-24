---
title: Resolver problemas com a instalação de aplicações
titlesuffix: Microsoft Intune
description: Utilize o painel de resolução de problemas do Microsoft Intune para o ajudar a resolver problemas com a instalação de aplicações.
keywords: ''
author: ErikRe
ms.author: erikre
manager: dougeby
ms.date: 07/18/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: b613f364-0150-401f-b9b8-2b09470b34f4
ms.reviewer: mghadial
ms.custom: intune-azure
ms.openlocfilehash: c1c2a37103f8fedc09a70b4387aae3f472dfb636
ms.sourcegitcommit: dc8b6f802cca7895a19ec38bec283d4b3150d213
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/19/2018
ms.locfileid: "39138684"
---
# <a name="troubleshoot-app-installation-issues"></a>Resolver problemas com a instalação de aplicações

Por vezes, a instalação de aplicações em dispositivos geridos por MDM do Microsoft Intune pode falhar. Quando uma instalação de aplicações falha, pode ser difícil compreender o motivo da falha ou resolver o problema. O Microsoft Intune disponibiliza detalhes da falha na instalação da aplicação que permitem que os operadores de suporte técnico e os administradores do Intune vejam informações da aplicação para resolver pedidos de ajuda do utilizador. O painel de resolução de problemas no Intune proporciona os detalhes da falha, incluindo detalhes sobre as aplicações geridas no dispositivo de um utilizador. São disponibilizados detalhes sobre o ciclo de vida ponto a ponto de uma aplicação em cada dispositivo individual no painel **Aplicações Geridas**. Pode ver os problemas de instalação, como quando a aplicação foi criada, modificada, direcionada e entregue a um dispositivo. 

## <a name="to-review-app-troubleshooting-details"></a>Para rever os detalhes da resolução de problemas com a aplicação

O Intune proporciona detalhes da resolução de problemas com a aplicação com base nas aplicações instaladas no dispositivo de um utilizador específico.

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços** > **Intune**. O Intune encontra-se na secção **Monitorização + Gestão**.
3. No painel **Intune**, selecione **Resolução de problemas**.
4. Clique em **Selecionar utilizador** para selecionar um utilizador para o qual quer executar a resolução de problemas. O painel **Selecionar utilizadores** será apresentado.
5. Selecione um utilizador ao escrever o nome ou endereço de e-mail. Clique em **Selecionar** na parte inferior do painel. As informações de resolução de problemas do utilizador são apresentadas no painel **Resolução de problemas**. 
6. Selecione o dispositivo com o qual quer resolver problemas na lista **Dispositivos**.
    ![O painel de Resolução de Problemas do Intune.](media/troubleshoot-app-install-01.png)
7. Selecione **Aplicações Geridas** a partir do painel do dispositivo selecionado. É apresentada uma lista de aplicações geridas.
    ![Detalhes de um dispositivo específico gerido pelo Intune.](media/troubleshoot-app-install-02.png)
8. Selecione uma aplicação na lista onde o **Estado da Instalação** indicar uma falha.
    ![Uma aplicação selecionada que mostra detalhes da falha na instalação.](media/troubleshoot-app-install-03.png)

    > [!Note]  
    > A mesma aplicação pode ser atribuída a vários grupos, mas com diferentes ações pretendidas (intenções) para a aplicação. Por exemplo, uma intenção resolvida para uma aplicação apresentará a indicação **excluída** se a aplicação estiver excluída para um utilizador durante a atribuição de aplicações. Para obter mais informações, veja [Como são resolvidos conflitos entre intenções de aplicações](apps-deploy.md#how-conflicts-between-app-intents-are-resolved).<br><br>
    > Atualmente, o Intune não filtra as aplicações com base na plataforma do SO.

Os detalhes do erro da instalação da aplicação irão indicar o problema. Pode usar estes detalhes para determinar a melhor ação a tomar para resolver o problema. Para obter mais informações sobre como resolver problemas de instalação da aplicação, veja [Códigos de Erro para Resolver Problemas de Instalação da Aplicação](https://blogs.technet.microsoft.com/intunesupport/2018/05/15/error-codes-for-troubleshooting-app-installation-issues).

> [!Note]  
> Também pode aceder ao painel **Resolução de problemas** ao apontar o seu browser para: [https://aka.ms/intunetroubleshooting](https://aka.ms/intunetroubleshooting).

## <a name="next-steps"></a>Próximos passos

- Para obter informações adicionais de resolução de problemas, veja [Utilizar o portal de resolução de problemas para ajudar os utilizadores na sua empresa](help-desk-operators.md). 
- Saiba mais sobre os problemas conhecidos no Microsoft Intune. Para obter mais informações, veja [Problemas conhecidos no Microsoft Intune](known-issues.md).
- Precisa de ajuda adicional? Veja [Como obter suporte para o Microsoft Intune](get-support.md).
