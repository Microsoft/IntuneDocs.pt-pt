---
title: "Como implementar aplicações | Microsoft Intune"
description: "Utilize as informações neste tópico para obter ajuda para implementar aplicações com o Microsoft Intune."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 07/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3b42019e-73da-4538-a496-212f11d5bf9b
ms.reviewer: mghadial
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 6716a3d1fb53dc3de0189f637d5664d0a2023d05
ms.openlocfilehash: f3a8492532f01c576b1abf3c3228ba99dbd0d547

---
# Implementar aplicações no Microsoft Intune

Utilize as informações neste tópico para obter ajuda para implementar aplicações com o Microsoft Intune.


## Implementar uma aplicação
Neste procedimento, vai implementar a aplicação em grupos de utilizadores ou dispositivos selecionados.

### Para implementar uma aplicação

1. Na [consola do administrador do Microsoft Intune](https://manage.microsoft.com), clique em **Aplicações** &gt; **Aplicações** para ver a lista de aplicações geridas por si.

2.  Selecione a aplicação que quer implementar e, sem seguida, clique em **Gerir Implementação**.

3.  Na caixa de diálogo *&lt;nome da aplicação&gt;*, na página **Selecionar Grupos**, escolha os grupos de utilizadores ou dispositivos nos quais pretende implementar a aplicação.

4.  Na página **Ação de Implementação**, configure o seguinte:

    - **Aprovação** - escolha se a implementação é:
        - **Obrigatória** (instalação obrigatória)
        - **Disponível** (os utilizadores instalam a partir do portal da empresa a pedido)
        - **Não Aplicável** (a aplicação não é instalada nem apresentada no portal da empresa)
        - **Desinstalar** (a aplicação será desinstalada dos dispositivos segmentados).
    - **Prazo** - em instalações necessárias, escolha quando serão implementadas. Pode escolher entre os valores predefinidos ou selecionar **Personalizado** para configurar o seu próprio prazo.

5. Se for possível configurar a aplicação que está a implementar através de uma política de gestão de aplicações móveis, é apresentada a página **Gestão de Aplicações Móveis**. Nesta página, escolha a política de gestão de aplicações móveis que pretende associar a esta aplicação.

    [Veja que aplicações da Microsoft são compatíveis com as políticas de gestão de aplicações móveis.](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx)

6. Se a aplicação que está a implementar for compatível com perfis da VPN do Intune, a página **Perfil da VPN** é apresentada. Nesta página, pode optar por associar as aplicações iOS a um perfil da VPN que tenha implementado. A ligação à VPN será aberta automaticamente quando a aplicação for iniciada. Para disponibilizar um perfil da VPN, este deve ter ativada a definição de perfil **Por VPN de aplicação**.
 Para informações sobre como configurar perfis de VPN, incluindo suporte para associar perfis a aplicações, consulte [Ajudar os utilizadores a estabelecer uma ligação com o respetivo trabalho através de perfis de VPN com o Microsoft Intune](vpn-connections-in-microsoft-intune.md).

## Exemplo

Neste exemplo, implementou a aplicação como **Disponível** num dispositivo iOS.
A aplicação será apresentada no portal da empresa nos dispositivos dos utilizadores, de onde podem instalá-la. Por exemplo, nesta captura de ecrã, foi utilizado o tipo de instalação **Ligação externa** para implementar a aplicação Bing para iOS, com um ícone personalizado, e a opção **Apresentar esta aplicação como uma aplicação em destaque e destacá-la no portal da empresa** foi selecionada.  
![Aplicação iOS disponível](./media/available-install-on-iOS.png)

Se implementou a aplicação como **Obrigatória** num dispositivo iOS, o utilizador irá receber uma notificação a indicar que uma aplicação está pronta para ser instalada. Por exemplo, nesta captura de ecrã, foi utilizado o tipo de instalação **Aplicação iOS gerida da loja de aplicações** para implementar a aplicação Pastas de Trabalho para iOS.  
![Aplicação iOS obrigatória](./media/iOS-Required-install.PNG)

## Passos seguintes

Depois de implementar uma aplicação, poderá ser útil monitorizar o progresso da mesma. Para mais informações, consulte [Monitorizar aplicações no Microsoft Intune](monitor-apps-in-microsoft-intune.md).



<!--HONumber=Jul16_HO4-->


