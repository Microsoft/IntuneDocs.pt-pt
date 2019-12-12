---
title: Que informações é que a sua empresa pode ver quando inscreve o seu dispositivo?
description: Explica o que o departamento de TI pode e não pode ver no seu dispositivo gerido.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/31/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: 12655728-a1af-4d89-97bc-925fe36c0dc4
searchScope:
- User help
ROBOTS: ''
ms.reviewer: esmich
ms.suite: ems
ms.collection: M365-identity-device-management
ms.openlocfilehash: fc50f48afbd527f3c6d82cc0c71a166b0356ab9e
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/05/2019
ms.locfileid: "73801467"
---
# <a name="what-information-can-my-organization-see-when-i-enroll-my-device"></a>Que informações é que a minha organização pode ver quando inscrevo o meu dispositivo?

Quando inscreve um dispositivo no Microsoft Intune, a sua organização não consegue ver as suas informações pessoais. Ao inscrever um dispositivo, dá permissão à sua organização para ver partes de informações do seu dispositivo, tal como o modelo e o número de série. A sua organização utiliza estas informações para ajudar a proteger os dados empresariais no dispositivo.

**O que a sua organização nunca conseguirá ver:**

- Histórico de chamadas e navegação na Web
- Mensagens de e-mail e texto
- Contactos
- Calendário
- Palavras-passe
- Imagens, incluindo o que está na aplicação de fotografias ou câmara
- Ficheiros

**O que a sua organização conseguirá sempre ver:**

- Modelo do dispositivo, como o Google Pixel
- Fabricante do dispositivo, como Microsoft
- Sistema operativo e versão, por exemplo iOS 12.0.1
- Inventário de aplicativo e nomes de aplicativo, como o Microsoft Word. Em dispositivos pessoais, sua organização só pode ver o inventário de aplicativos gerenciados. Nos dispositivos pertencentes à empresa, a sua organização consegue ver todo o seu inventário de aplicações.
- Proprietário do dispositivo
- Nome do dispositivo
- Número de série do dispositivo
- IMEI

**Informações que a sua organização poderá conseguir ver:**

- Número de telefone: para dispositivos de propriedade corporativa, seu número de telefone completo pode ser visto. Para dispositivos pessoais, apenas os últimos quatro dígitos do seu número de telefone são visíveis para sua organização. Você pode ver o tipo de propriedade para cada dispositivo individual na página de **detalhes do dispositivo** .
- Espaço de armazenamento do dispositivo: se não conseguir instalar uma aplicação necessária, a sua organização poderá ver o espaço de armazenamento do seu dispositivo para verificar se o espaço é insuficiente.  
- Local: sua organização nunca pode ver o local do seu dispositivo, a menos que você precise recuperar um dispositivo iOS perdido e supervisionado. Visite a [documentação do Apple Ios](https://go.microsoft.com/fwlink/?linkid=853816) para saber mais sobre os dispositivos supervisionados.  
- Detalhes do inventário de aplicativos: se sua organização usa a defesa contra ameaças móveis, ela poderá exibir detalhes sobre os aplicativos que estão em seu dispositivo iOS. Saiba mais sobre a [Defesa Contra Ameaças para Dispositivos Móveis](you-are-prompted-to-install-mtd-ios.md). Se você tiver um dispositivo pessoal, sua organização só poderá ver o inventário de aplicativos gerenciados. Se você tiver um dispositivo de propriedade corporativa, sua organização poderá ver todo o inventário de seu aplicativo.
- Informações de rede: algumas informações sobre ligações de rede para dispositivos Android podem estar disponíveis para o suporte da sua organização. Por exemplo, se a sua organização precisar que os dispositivos permaneçam num determinado edifício, o dispositivo identificará a rede à qual está ligado. 
