---
title: "Transferir a política de configuração de aplicações iOS do Skycure para utilizar com o Intune"
titleSuffix: Intune on Azure
description: "Transfira a política de configuração de aplicações iOS do Skycure para utilizar com o Intune."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/21/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1bdc2ecf-32d0-4b6a-80b4-dbcdb9909010
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ffe1027e90203d4e300a2446f15e72cc5bf53973
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/01/2017
---
# <a name="download-skycure-ios-app-configuration-policy"></a>Transferir a política de configuração de aplicações iOS do Skycure

## <a name="before-you-begin"></a>Antes de começar

Tem de iniciar sessão na Consola de Gestão do Skycure para realizar os passos seguintes.

> [!TIP] 
> Se utilizar o Microsoft Internet Explorer 11 ou o Edge, poderá ter de abrir a consola de Gestão do Skycure através do modo privado.

## <a name="to-download-the-ios-app-configuration-policy"></a>Para transferir a política de configuração de aplicações iOS

1.  Aceda à [Consola de Gestão do Skycure](https://aad.skycure.com).

2.  Introduza as **Credenciais de administrador do Skycure** e, em seguida, clique em **Continuar**.

    ![Início de sessão na consola de Gestão do Skycure](./media/skycure-ios-app-1.png)

    > [!IMPORTANT] 
    > O nome de utilizador do administrador do Skycure é uma conta de e-mail que tem de ser uma conta de utilizador válida no Azure Active Directory. Caso contrário, o início de sessão falhará. O Skycure utiliza o Azure Active Directory para autenticar o nome de utilizador do administrador através do Início de Sessão Único (SSO).

3.  Aceda a **Definições** &gt; **Integrações da Gestão de Dispositivos** &gt; **Seleção da Integração de EMM**, escolha **Microsoft Intune** e, em seguida, guarde a sua seleção.

4.  Clique na ligação **Ficheiros de configuração de integração** e guarde o ficheiro \*.zip gerado. O ficheiro .zip contém o ficheiro **skycure\_configuration.plist**, que servirá para criar a política de configuração de aplicações iOS na consola clássica do Intune.

![Ficheiros de configuração de integração do Skycure](./media/skycure-ios-app-2.png)

## <a name="next-steps"></a>Passos seguintes

[Adicionar e atribuir aplicações do Skycure, a aplicação Microsoft Authenticator e a política de configuração de aplicações iOS](mtd-apps-ios-app-configuration-policy-add-assign.md)
