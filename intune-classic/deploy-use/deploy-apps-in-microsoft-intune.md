---
title: Como implementar aplicações
description: Utilize as informações neste tópico para obter ajuda para implementar aplicações com o Microsoft Intune.
keywords: ''
author: mattbriggs
ms.author: mabrigg
manager: dougeby
ms.date: 12/27/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 3b42019e-73da-4538-a496-212f11d5bf9b
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: ed098a22da1def82c90fbb159d54be9b1a369ba8
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2018
---
# <a name="deploy-apps-in-microsoft-intune"></a>Implementar aplicações no Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Utilize as informações neste tópico para obter ajuda para implementar aplicações com o Microsoft Intune.


## <a name="deploy-an-app"></a>Implementar uma aplicação
Neste procedimento, vai implementar uma aplicação em grupos de utilizadores ou dispositivos selecionados.

### <a name="to-deploy-an-app"></a>Para implementar uma aplicação

1. Na [consola de administração do Microsoft Intune](https://manage.microsoft.com), clique em **Aplicações** &gt; **Aplicações** para ver a lista de aplicações geridas por si.

2.  Selecione a aplicação que quer implementar e, sem seguida, clique em **Gerir Implementação**.

3.  Na caixa de diálogo *&lt;nome da aplicação&gt;*, na página **Selecionar Grupos**, escolha os grupos de utilizadores ou dispositivos nos quais pretende implementar a aplicação.

4.  Na página **Ação de Implementação**, configure o seguinte:

    - **Aprovação** – escolha se a implementação é:
        - **Obrigatória** (instalação obrigatória)
        - **Disponível** (os utilizadores instalam a partir do portal da empresa a pedido)
        - **Não Aplicável** (a aplicação não é instalada nem apresentada no portal da empresa)
        - **Desinstalar** (a aplicação é desinstalada dos dispositivos segmentados)
    - **Prazo** – em instalações necessárias, escolha quando implementar a aplicação. Pode escolher entre os valores predefinidos ou pode selecionar **Personalizado** para configurar o seu próprio prazo.

5. Se for possível configurar a aplicação que está a implementar através de uma política de gestão de aplicações móveis, é apresentada a página **Gestão de Aplicações Móveis**. Nesta página, escolha a política de gestão de aplicações móveis que pretende associar a esta aplicação.

    [Veja que aplicações da Microsoft são compatíveis com as políticas de gestão de aplicações móveis.](https://www.microsoft.com/server-cloud/products/microsoft-intune/partners.aspx)

6. Se a aplicação que está a implementar for compatível com perfis da VPN do Intune, a página **Perfil da VPN** é apresentada. Nesta página, pode optar por associar as aplicações iOS a um perfil da VPN que tenha implementado. A ligação à VPN é aberta automaticamente quando a aplicação for iniciada. Para disponibilizar um perfil da VPN, este deve ter ativada a definição de perfil **Por VPN de aplicação**.
 Para obter informações sobre como configurar perfis VPN, incluindo informações sobre como associar perfis a aplicações, consulte [Ligações VPN no Microsoft Intune](vpn-connections-in-microsoft-intune.md).

<!---
>[!TIP]
>If an end user previously installed an iOS app and you now deploy it with a deployment action of **Available**, Intune will automatically begin to manage that app with no further action required by you, or the end-user.
--->

## <a name="example"></a>Exemplo

Neste exemplo, implementou a aplicação como **Disponível** num dispositivo iOS.
A aplicação apresenta-se nos dispositivos dos utilizadores no portal da empresa, a partir do qual os utilizadores a podem instalar.

Por exemplo, nesta captura de ecrã, a aplicação Bing para iOS foi implementada com o tipo de instalação de **ligação externa** com um ícone personalizado. Foi selecionada opção **Apresentar como uma aplicação em destaque e realçá-la no portal da empresa**.  
![Aplicação iOS disponível](./media/available-install-on-iOS.png)

Se implementou a aplicação como **Obrigatória** num dispositivo iOS, o utilizador irá receber uma notificação a indicar que uma aplicação está pronta para ser instalada. Por exemplo, nesta captura de ecrã, a aplicação Pastas de Trabalho para iOS foi implementada ao utilizar **Aplicação iOS gerida da loja de aplicações** para implementar a aplicação Pastas de Trabalho para iOS.  
![Aplicação iOS necessária](./media/iOS-Required-install.PNG)

## <a name="next-steps"></a>Próximos passos

Depois de implementar uma aplicação, poderá ser útil monitorizar o progresso da mesma. Para mais informações, consulte [Monitorizar aplicações no Microsoft Intune](monitor-apps-in-microsoft-intune.md).
