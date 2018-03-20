---
title: "Definições de restrição de dispositivos no Microsoft Intune para dispositivos macOS"
titlesuffix: 
description: "Saiba que definições do Intune pode utilizar para controlar as definições e funcionalidades em dispositivos macOS."
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/6/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 72c9036bd6062e719d55876d77f44123fe2af392
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/08/2018
---
# <a name="microsoft-intune-macos-device-restriction-settings"></a>Definições de restrição de dispositivos macOS no Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Este artigo mostra-lhe as definições de restrições de dispositivos do Microsoft Intune que pode configurar para dispositivos macOS.

## <a name="password"></a>Palavra-passe
-   **Palavra-passe** – exija que o utilizador final introduza uma palavra-passe para aceder ao dispositivo.
    -   **Tipo obrigatório de palavra-passe** – Especifique se a palavra-passe pode ser só Numérica ou se tem de ser Alfanumérica (conter letras e números). Esta definição só é suportada na versão 10.10.3 do Mac OS X e posterior.
    -   **Número de carateres não-alfanuméricos na palavra-passe** – Especifique o número de carateres complexos obrigatórios na palavra-passe (**0** a **4**).<br>Um caráter complexo é um símbolo, por exemplo "**?**".
    -   **Comprimento mínimo da palavra-passe** –Introduza o comprimento mínimo da palavra-passe que um utilizador tem de configurar (entre **4** e **16** carateres).
    -   **Palavras-passes simples** – Permita a utilização de palavras-passe simples, como **0000** ou **1234**.
    -   **Máximo de minutos após o bloqueio de ecrã até ao pedido de palavra-passe** – Especifique durante quanto tempo o computador tem de estar inativo até uma palavra-passe ser pedida para o desbloquear.
    -   **Máximo de minutos de inatividade até o ecrã bloquear** – Especifique o período de tempo durante o qual o computador tem de estar inativo até o ecrã bloquear.
    -   **Expiração da palavra-passe (dias)** – Especifique o número de dias que decorrem antes de o utilizador ter de alterar a palavra-passe (de **1** a **255** dias).
    -   **Impedir reutilização de palavras-passe anteriores** – Especifique o número de palavras-passe utilizadas anteriormente que não podem ser reutilizadas (**1** a **24**).

## <a name="restricted-apps"></a>Aplicações restritas

Na lista de aplicações restritas, pode configurar uma das seguintes listas:

- Uma lista de **Aplicações proibidas** – Indique as aplicações (não geridas pelo Intune) que os utilizadores não têm permissão para instalar e executar. Os utilizadores não são impedidos de instalar uma aplicação proibida, mas se o fizerem, esta ação ser-lhe-á comunicada.
- Uma lista de **Aplicações aprovadas** – Indique as aplicações que os utilizadores têm permissão para instalar. Os utilizadores não podem instalar aplicações que não estejam listadas. As aplicações geridas pelo Intune são automaticamente permitidas. Os utilizadores não são impedidos de instalar aplicações que não se encontrem na lista de aprovações, mas se o fizerem, esta ação ser-lhe-á comunicada.

Para configurar a lista, clique em **Adicionar** e, em seguida, especifique um nome à sua escolha, opcionalmente, o publicador da aplicação e o ID do grupo da aplicação (por exemplo, *com.apple.calculator*).

## <a name="domains"></a>Domínios

### <a name="unmarked-email-domains"></a>Domínios de e-mail não marcados

No campo **URL de Domínio de E-mail**, adicione um ou mais URLs à lista. Quando os utilizadores recebem um e-mail de um domínio não configurado, o e-mail é marcado como não fidedigno na aplicação Mail do iOS.

