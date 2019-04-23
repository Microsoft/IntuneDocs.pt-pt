---
title: Adicionar proteção de ponto final ao macOS no Microsoft Intune – Azure | Microsoft Docs
description: Em dispositivos macOS, utilize o controlador de chamadas para determinar onde as aplicações podem ser instaladas, incluindo a Mac App Store. Ativar ou configurar uma firewall permite aplicações específicas, bloqueia aplicações específicas, utiliza o modo invisível e até bloqueia determinados tipos de ligações de entrada com o Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/27/2018
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c2c3a33b996a68263550fc05d3af853c263c930a
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "61512926"
---
# <a name="macos-endpoint-protection-settings-in-intune"></a>Definições de proteção de ponto final do macOS no Intune

Este artigo mostra-lhe as definições de proteção de ponto final que pode configurar para dispositivos macOS. Estas definições incluem definições de firewall e controlador de chamadas nestes dispositivos e podem ser configuradas com um perfil de dispositivos no Microsoft Intune.

## <a name="gatekeeper"></a>Controlador de chamadas

- **Permitir aplicações transferidas a partir destas localizações**: Limite as aplicações dependendo de onde as aplicações foram transferidas. A intenção é proteger dispositivos de software maligno e permitir apenas aplicações de origens em que confia. As opções para permitir: 
  - **Mac App Store**
  - **Mac App Store e programadores identificados**
  - **Em qualquer lugar**

- **Utilizador pode ignorar o controlador de chamadas**: Impede os utilizadores de substituir o controlador de chamadas a definição e impede que os utilizadores cliquem para instalar uma aplicação. Quando estiver ativado, os utilizadores podem manter a tecla Ctrl premida e clicar em qualquer aplicação e instalá-la.

## <a name="firewall"></a>Firewall

Utilize a firewall para controlar ligações por aplicação e não por porta. Utilizar definições por aplicação torna mais fácil obter as vantagens de proteção da firewall. Também ajuda a impedir que aplicações indesejáveis controlem as portas da rede que estão abertas para as aplicações legítimas.

- **Utilize a firewall para proteger dispositivos de acessos de rede não autorizados ao controlar ligações numa base por aplicação.**
  - **Firewall**: Ativar a Firewall configurar ligações de entrada como são processadas no seu ambiente.
  - **Ligações de entrada**: Bloquear todas as ligações recebidas, exceto as ligações necessárias para serviços básicos de Internet, como DHCP, Bonjour e IPSec. Esta funcionalidade também bloqueia todos os serviços de partilha, tal como a Partilha de Ficheiros e a Partilha de Ecrãs. Se estiver a utilizar serviços de partilha, mantenha esta definição como **Não configurado**.

- **Permitir ou bloquear ligações de entrada para aplicações específicas**
  - **Aplicações com permissão**: Selecione as aplicações que têm permissão explícita para receber ligações de entrada.
  - **Aplicações bloqueadas**: Selecione as aplicações que devem bloquear ligações de entrada.
  - **O modo invisível**: Para impedir que o computador responda aos pedidos de pesquisa, ative o modo invisível. O dispositivo continua a responder a pedidos recebidos de aplicações autorizadas. São ignorados pedidos inesperados, tais como o protocolo ICMP (ping).
