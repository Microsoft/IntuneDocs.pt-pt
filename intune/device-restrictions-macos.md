---
title: "Definições de restrição de dispositivos no Intune para dispositivos macOS"
titleSuffix: Intune Azure preview
description: "Pré-visualização do Azure no Intune: saiba que definições do Intune pode utilizar para controlar as definições dos dispositivos e a funcionalidade em dispositivos macOS."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3129cbaf-96c2-4837-8907-ca87a605a496
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: c120c6af93234e153e4fb845942726a51bee98df
ms.contentlocale: pt-pt
ms.lasthandoff: 05/23/2017


---

# <a name="macos-device-restriction-settings-in-microsoft-intune"></a>Definições de restrição de dispositivos macOS no Microsoft Intune

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

## <a name="password"></a>Palavra-passe
-     **Palavra-passe obrigatória** – Exija que o utilizador final introduza uma palavra-passe para aceder ao dispositivo.
    -     **Tipo obrigatório de palavra-passe** – Especifique se a palavra-passe pode ser só Numérica ou se tem de ser Alfanumérica (conter letras e números). Esta definição só é suportada na versão 10.10.3 do Mac OS X e posterior.
    -     **Número de carateres não-alfanuméricos na palavra-passe** – Especifique o número de carateres complexos obrigatórios na palavra-passe (**0** a **4**).<br>Um caráter complexo é um símbolo, tal como **?**.
    -     **Comprimento mínimo da palavra-passe** –Introduza o comprimento mínimo da palavra-passe que um utilizador tem de configurar (entre **4** e **16** carateres).
    -     **Palavras-passes simples** – Permita a utilização de palavras-passe simples, como **0000** ou **1234**.
    -     **Máximo de minutos após o bloqueio de ecrã até ao pedido de palavra-passe** – Especifique durante quanto tempo o computador tem de estar inativo até uma palavra-passe ser pedida para o desbloquear.
    -     **Máximo de minutos de inatividade até o ecrã bloquear** – Especifique o período de tempo durante o qual o computador tem de estar inativo até o ecrã bloquear.
    -     **Expiração da palavra-passe (dias)** – Especifique o número de dias que decorrem antes de o utilizador ter de alterar a palavra-passe (de **1** a **255** dias).
    -     **Impedir reutilização de palavras-passe anteriores** – Especifique o número de palavras-passe utilizadas anteriormente que não podem ser reutilizadas (**1** a **24**).

## <a name="restricted-apps"></a>Aplicações restritas

Na lista de aplicações restritas, pode configurar uma das seguintes listas:

Uma lista de **Aplicações proibidas** – Indique as aplicações (não geridas pelo Intune) que os utilizadores não têm permissão para instalar e executar.
Uma lista de **Aplicações aprovadas** – Indique as aplicações que os utilizadores têm permissão para instalar. Para permanecerem compatíveis, os utilizadores não têm de instalar aplicações que não estejam listadas. As aplicações geridas pelo Intune são automaticamente permitidas.

Para configurar a lista, clique em **Adicionar** e, em seguida, especifique um nome à sua escolha, opcionalmente, o publicador da aplicação e o ID do grupo da aplicação (por exemplo, *com.apple.calculator*).



