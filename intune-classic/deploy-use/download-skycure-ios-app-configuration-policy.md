---
title: "Transferir a política de configuração de aplicações iOS do Skycure | Documentos da Microsoft"
description: "Transfira a política de configuração de aplicações iOS do Skycure para utilizar com a aplicação iOS do Skycure implementada para os utilizadores finais."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/16/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d211b876-4d3a-473c-999f-843c0a16cd22
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: a8e46960a5d469093052148eb457140b3c235d3a
ms.contentlocale: pt-pt
ms.lasthandoff: 05/23/2017


---

# <a name="download-skycure-ios-app-configuration-policy"></a>Transferir a política de configuração de aplicações iOS do Skycure

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

##<a name="before-you-begin"></a>Antes de começar

Tem de iniciar sessão na Consola de Gestão do Skycure para realizar os passos seguintes.

> [!TIP] 
> Se utilizar o Microsoft Internet Explorer 11 ou o Edge, poderá ter de abrir a consola de Gestão do Skycure através do modo privado.

## <a name="to-download-the-ios-app-configuration-policy"></a>Para transferir a política de configuração de aplicações iOS

1.  Aceda à [Consola de Gestão do Skycure](https://aad.skycure.com).

2.  Introduza as **Credenciais de administrador do Skycure** e, em seguida, clique em **Continuar**.

    ![Início de sessão na consola de Gestão do Skycure](../media/mtp/skycure-ios-app-1.png)

    > [!IMPORTANT] 
    > O nome de utilizador do administrador do Skycure é uma conta de e-mail que tem de ser uma conta de utilizador válida no Azure Active Directory. Caso contrário, o início de sessão falhará. O Skycure utiliza o Azure Active Directory para autenticar o nome de utilizador do administrador através do Início de Sessão Único (SSO).

3.  Aceda a **Definições** &gt; **Integrações da Gestão de Dispositivos** &gt; **Seleção da Integração de EMM**, escolha **Microsoft Intune** e, em seguida, guarde a sua seleção.

2.  Clique na ligação **Ficheiros de configuração de integração** e guarde o ficheiro \*.zip gerado. O ficheiro .zip contém o ficheiro **skycure\_configuration.plist**, que servirá para criar a política de configuração de aplicações iOS na consola clássica do Intune.

![Ficheiros de configuração de integração do Skycure](../media/mtp/skycure-ios-app-2.png)

## <a name="next-steps"></a>Próximos passos

[Adicionar aplicações do Skycure, a aplicação Microsoft Authenticator e a política de configuração de aplicações iOS](/intune-classic/deploy-use/add-skycure-apps-microsoft-authenticator-and-ios-app-configuration-policy)

