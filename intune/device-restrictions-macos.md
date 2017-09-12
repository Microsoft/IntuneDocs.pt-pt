---
title: "Definições de restrição de dispositivos no Intune para dispositivos macOS"
titlesuffix: Azure portal
description: "Saiba quais são as definições do Intune que pode utilizar para controlar as definições dos dispositivos e a funcionalidade em dispositivos Mac OS.\""
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 08/01/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3129cbaf-96c2-4837-8907-ca87a605a496
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 978430ded8d2e6da36ce49cd9351c9d44789e2b0
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/09/2017
---
# <a name="macos-device-restriction-settings-in-microsoft-intune"></a>Definições de restrição de dispositivos macOS no Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Utilize estas definições para gerir dispositivos macOS num perfil de restrição de dispositivos.

## <a name="password"></a>Palavra-passe
-   **Palavra-passe** – exija que o utilizador final introduza uma palavra-passe para aceder ao dispositivo.
    -   **Tipo obrigatório de palavra-passe** – Especifique se a palavra-passe pode ser só Numérica ou se tem de ser Alfanumérica (conter letras e números). Esta definição só é suportada na versão 10.10.3 do Mac OS X e posterior.
    -   **Número de carateres não-alfanuméricos na palavra-passe** – Especifique o número de carateres complexos obrigatórios na palavra-passe (**0** a **4**).<br>Um caráter complexo é um símbolo, como **?**
    -   **Comprimento mínimo da palavra-passe** –Introduza o comprimento mínimo da palavra-passe que um utilizador tem de configurar (entre **4** e **16** carateres).
    -   **Palavras-passes simples** – Permita a utilização de palavras-passe simples, como **0000** ou **1234**.
    -   **Máximo de minutos após o bloqueio de ecrã até ao pedido de palavra-passe** – Especifique durante quanto tempo o computador tem de estar inativo até uma palavra-passe ser pedida para o desbloquear.
    -   **Máximo de minutos de inatividade até o ecrã bloquear** – Especifique o período de tempo durante o qual o computador tem de estar inativo até o ecrã bloquear.
    -   **Expiração da palavra-passe (dias)** – Especifique o número de dias que decorrem antes de o utilizador ter de alterar a palavra-passe (de **1** a **255** dias).
    -   **Impedir reutilização de palavras-passe anteriores** – Especifique o número de palavras-passe utilizadas anteriormente que não podem ser reutilizadas (**1** a **24**).

## <a name="restricted-apps"></a>Aplicações restritas

Na lista de aplicações restritas, pode configurar uma das seguintes listas:

Uma lista de **Aplicações proibidas** – Indique as aplicações (não geridas pelo Intune) que os utilizadores não têm permissão para instalar e executar.
Uma lista de **Aplicações aprovadas** – Indique as aplicações que os utilizadores têm permissão para instalar. Para permanecerem compatíveis, os utilizadores não têm de instalar aplicações que não estejam listadas. As aplicações geridas pelo Intune são automaticamente permitidas.

Para configurar a lista, clique em **Adicionar** e, em seguida, especifique um nome à sua escolha, opcionalmente, o publicador da aplicação e o ID do grupo da aplicação (por exemplo, *com.apple.calculator*).

## <a name="domains"></a>Domínios

### <a name="unmarked-email-domains"></a>Domínios de e-mail não marcados

No campo **URL de Domínio de E-mail**, adicione um ou mais URLs à lista. Quando os utilizadores finais recebem um e-mail de um domínio não configurado, o e-mail é marcado como não fidedigno na aplicação Mail do iOS.

