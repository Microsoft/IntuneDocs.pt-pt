---
title: "Configurar a integração do Skycure com o Intune"
titlesuffix: Azure portal
description: "Configure a integração do Skycure com o Microsoft Intune."
keywords: 
author: arob98
ms.author: angrobe
manager: dougeby
ms.date: 12/21/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 359448d9-2384-42ac-a21c-a25148c20a7b
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: beaf027334ce4929e4ca824b2b7e199cea22a832
ms.sourcegitcommit: 468480b61110ca81f737582ebbefd4efda6fd667
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/30/2018
---
# <a name="set-up-the-skycure-integration-with-intune"></a>Configurar a integração do Skycure com o Intune

Tem de adicionar aplicações do Skycure ao Azure AD para ter capacidades de Início de Sessão Único.

## <a name="before-you-begin"></a>Antes de começar

### <a name="azure-ad-account-used-to-integrate-intune-and-skycure"></a>A conta do Azure AD utilizada para integrar o Intune e o Skycure

-   Confirme se configurou corretamente a conta do Azure AD na [consola de Gestão do Skycure](https://aad.skycure.com) antes de iniciar o processo de Configuração Básica do Skycure.

### <a name="full-integration-vs-read-only"></a>Integração total vs. Só de leitura

O Skycure suporta dois modos de integração com o Intune:

-   **Integração Só de leitura (Configuração básica):** apenas fará o inventário dos dispositivos do Azure Active Directory e preenche-os na consola do Skycure.
<br>
    -   Se as caixas **Comunicar o estado de funcionamento e o risco dos dispositivos ao Intune** e **Comunicar também incidentes de segurança ao Intune** não estiverem selecionadas na consola de Gestão do Skycure, a integração será só de leitura e, como tal, nunca irá alterar o estado dos dispositivos (conforme ou não conforme) no Intune.
<br></br>
-   **Integração total:** permite ao Skycure comunicar detalhes de incidentes de segurança e riscos dos dispositivos ao Intune, que cria uma comunicação bidirecional entre ambos os serviços cloud.

### <a name="how-the-skycure-apps-are-used-with-azure-ad-and-intune"></a>Como é que as aplicações do Skycure são utilizadas com o Azure AD e o Intune?

-   **Aplicação iOS:** permite que os utilizadores finais iniciem sessão no Azure AD com uma aplicação iOS.

-   **Aplicação Android:** permite que os utilizadores finais iniciem sessão no Azure AD com uma aplicação Android.

-   **Aplicação de gestão:** esta é a aplicação multi-inquilino do Azure AD do Skycure que permite a comunicação entre serviços com o Intune.

## <a name="to-set-up-the-read-only-integration-between-intune-and-skycure"></a>Para configurar a integração só de leitura entre o Intune e o Skycure

> [!IMPORTANT]
> As credenciais de administrador do Skycure são um e-mail que tem de pertencer a um utilizador válido no Azure Active Directory. Caso contrário, o início de sessão falhará. O Skycure utiliza o Azure Active Directory para autenticar o administrador através do Início de Sessão Único (SSO).

1.  Aceda à [Consola de Gestão do Skycure](https://aad.skycure.com).

2.  Introduza as **Credenciais de administrador do Skycure** e, em seguida, clique em **Continuar**.

3.  Aceda a **Definições** e escolha **Configuração Básica** em **Integração do Intune**.

4.  Na etiqueta **Aplicação iOS**, clique em **Adicionar ao Active Directory**.

    ![Aplicação iOS na consola de Gestão do Skycure](./media/skycure-setup-1.png)

5.  Quando for apresentada a página de início de sessão, introduza as suas credenciais do Intune e clique em **Aceitar**.

    ![Pedido de início de sessão do Intune na aplicação iOS](./media/skycure-setup-2.png)

6.  Depois de a aplicação ser adicionada ao Azure AD, poderá ver uma indicação de que a aplicação foi adicionada com êxito ao Azure AD na consola de Gestão do Skycure.

    ![Ecrã de conclusão da aplicação iOS](./media/skycure-setup-3.png)

> [!NOTE]
> Repita o mesmo processo para as aplicações **Skycure Android** e **Gestão**.

### <a name="add-an-azure-ad-security-group-into-skycure"></a>Adicionar um Grupo de segurança do Azure AD ao Skycure

Tem de adicionar um grupo de segurança do Azure AD que contenha todos os dispositivos que executam o Skycure.

1.  Introduza e selecione todos os grupos de segurança de dispositivos que executem o Skycure e, em seguida, clique em **Aplicar alterações**.

    ![Configurar a consola de Gestão do Skycure do grupo de segurança](./media/skycure-setup-4.png)

O Skycure sincroniza os dispositivos que executam o serviço Defesa Contra Ameaças para Dispositivos Móveis com os grupos de segurança do Azure AD.

![Configuração do grupo de segurança concluída na consola de gestão do Skycure](./media/skycure-setup-5.png)

## <a name="set-up-the-full-integration-between-intune-and-skycure"></a>Configurar a integração total entre o Intune e o Skycure

1.  Aceda à [Consola de Gestão do Skycure](https://aad.skycure.com).

2.  Introduza as **Credenciais de administrador do Skycure** e, em seguida, clique em **Continuar**.

3.  Aceda a **Definições** e escolha **Integração Total** em **Integração do Intune**.

4.  Marque as seguintes definições:

    a.  Comunicar o estado de funcionamento e o risco do dispositivo ao Intune

    b.  Comunicar também incidentes de segurança ao Intune

5.  Clique em **Aplicar alterações**.

    ![Integração total do Skycure concluída](./media/skycure-setup-6.png)

## <a name="next-steps"></a>Próximos passos

[Set up Skycure apps (Configurar aplicações do Skycure)](mtd-apps-ios-app-configuration-policy-add-assign.md)
