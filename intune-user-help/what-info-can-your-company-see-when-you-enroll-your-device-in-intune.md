---
title: Que informações é que a sua empresa pode ver quando inscreve o seu dispositivo?
description: Explica o que o departamento de TI pode e não pode ver no seu dispositivo gerido.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 12/17/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 12655728-a1af-4d89-97bc-925fe36c0dc4
searchScope:
- User help
ROBOTS: ''
ms.reviewer: esmich
ms.suite: ems
ms.openlocfilehash: 7ede43a78e762548608149b428d963150ed65e84
ms.sourcegitcommit: 4e69a8664c289263490daa4c02bc6b81c33196e5
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/20/2018
ms.locfileid: "53642443"
---
# <a name="what-information-can-my-organization-see-when-i-enroll-my-device"></a>Que informações é que a minha organização pode ver quando inscrevo o meu dispositivo?

Quando inscreve um dispositivo no Microsoft Intune, a sua organização não consegue ver as suas informações pessoais. Ao inscrever um dispositivo, dá permissão à sua organização para ver partes de informações do seu dispositivo, tal como o modelo e o número de série. A sua organização utiliza estas informações para ajudar a proteger os dados empresariais no dispositivo.

**O que a sua organização nunca conseguirá ver:**

- Histórico de chamadas e navegação na Web
- Mensagens de e-mail e texto
- Contactos
- Calendário
-   Palavras-passe
- Imagens, incluindo o que está na aplicação de fotografias ou câmara
- Ficheiros

**O que a sua organização conseguirá sempre ver:**

- Modelo do dispositivo, como o Google Pixel
- Fabricante do dispositivo, como Microsoft
- Sistema operativo e versão, por exemplo iOS 12.0.1
- Nomes de aplicações, como o Microsoft Word: Nos dispositivos pessoais, sua organização só pode ver o inventário da aplicação gerida. Nos dispositivos pertencentes à empresa, a sua organização consegue ver todo o seu inventário de aplicações.
- Proprietário do dispositivo
- Nome do dispositivo
- Número de série do dispositivo
- IMEI

**Informações que a sua organização poderá conseguir ver:**

-  Número de telefone: Para **empresariais**-dispositivos pertencentes à empresa, pode ser visto o número de telefone completo. Nos dispositivos **pessoais**, apenas os últimos quatro dígitos do número de telefone estarão visíveis. Pode ver o **Tipo de Propriedade** de cada dispositivo individual. Para tal, abra a página **Detalhes do Dispositivo** do dispositivo.
- Espaço de armazenamento do dispositivo: Se não é possível instalar uma aplicação necessária, a sua organização poderá parecer no espaço de armazenamento do seu dispositivo para descobrir se o espaço está demasiado baixo.  
-  Localização: Sua organização nunca pode ver a localização do dispositivo, a menos que precisa de recuperar um dispositivo iOS perdido, supervisionado. Visite o [documentação de iOS da Apple](https://go.microsoft.com/fwlink/?linkid=853816) para saber mais sobre dispositivos supervisionados.  
- Inventário de aplicações: Se a sua organização utiliza Mobile Threat Defense, poderão ver os detalhes sobre as aplicações que estão no seu dispositivo iOS. Saiba mais sobre a [Defesa Contra Ameaças para Dispositivos Móveis](you-are-prompted-to-install-mtd-ios.md).
- Informações de rede: Algumas informações sobre ligações de rede para dispositivos Android podem estar disponíveis para o suporte da sua organização. Por exemplo, se a sua organização precisar que os dispositivos permaneçam num determinado edifício, o dispositivo identificará a rede à qual está ligado. 
