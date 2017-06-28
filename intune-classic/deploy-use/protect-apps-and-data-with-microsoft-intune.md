---
title: "Proteger aplicações e dados"
description: "Este tópico descreve as várias funcionalidades e capacidades do Intune que estão disponíveis para que possa ajudar a proteger os dados e aplicações da sua empresa."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5c46e188-87eb-4ce2-b184-24809e8bf783
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: df3c42d8b52d1a01ddab82727e707639d5f77c16
ms.openlocfilehash: 09b7a1d4901a52845719e8d7094f665b12b91ab4
ms.contentlocale: pt-pt
ms.lasthandoff: 06/08/2017


---

# <a name="protect-apps-and-data-with-microsoft-intune"></a>Proteger aplicações e dados com o Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

O Intune protege os dados da empresa através de várias camadas de tecnologia. Na camada de identidade, o acesso condicional protege o acesso aos serviços ao permitir apenas o acesso a partir de dispositivos geridos e conformes. Na camada de aplicação de cliente, a gestão de aplicações móveis (MAM) protege a perda de dados ao impedir que os dados sejam movidos para aplicações não protegidas ou localizações de armazenamento e ao apagar dados em caso de perda ou roubo de um dispositivo. Recomendamos a utilização destas duas camadas de proteção em conjunto para ajudar a proteger os dados enquanto mantém a sua força de trabalho móvel produtiva.

Um primeiro passo importante para proteger os dados da empresa passa por implementar um acesso condicional. Pode fazê-lo ao verificar se os dispositivos utilizados para aceder a esses dados estão a utilizar proteções de segurança, como palavras-passe seguras e encriptação e não estão desbloqueados por jailbreak. O Intune permite definir as condições que os dispositivos têm de cumprir antes de serem autorizados a aceder ao e-mail e aos dados da empresa.

O [acesso condicional](restrict-access-to-email-and-o365-services-with-microsoft-intune.md) é determinado por dois tipos de políticas que pode definir no Intune:
- Pode utilizar as [políticas de conformidade](introduction-to-device-compliance-policies-in-microsoft-intune.md) para determinar a conformidade de um dispositivo. Avaliam definições e condições como:
  - PINs e palavras-passe: pode criar regras para a solicitação de palavras-passe para desbloquear um dispositivo, para os requisitos de complexidade da palavra-passe e para outras definições de palavra-passe.
  - Encriptação: pode restringir o acesso a dispositivos encriptados.
  - Quando um dispositivo não tem jailbreak nem root: o Intune pode detetar se um dispositivo inscrito tem jailbreak. Pode definir a política para bloquear o acesso em tais dispositivos.
- Pode configurar [políticas de acesso condicional](restrict-access-to-email-and-o365-services-with-microsoft-intune.md) para um determinado serviço, como o Exchange Online ou o SharePoint Online. Para cada serviço, pode definir a que grupos de utilizadores estas políticas devem ser aplicadas. Por exemplo, pode certificar-se de que todos os membros do departamento financeiro apenas podem aceder ao e-mail da empresa a partir de dispositivos inscritos e conformes.

Proteger o acesso aos recursos da empresa é apenas o primeiro passo para proteger os dados da empresa. Ainda precisa de proteger os dados depois de terem sido acedidos no dispositivo. Os dados podem agora ser copiados, movidos, guardados numa localização diferente ou partilhados. O Intune resolve este problema ao permitir restringir o movimento de dados através da criação de um conjunto de regras como:
- Bloquear operações copiar e colar ou impedir a transferência de dados fora do contexto de trabalho.
- Impedir cópias de segurança para o armazenamento pessoal na cloud e impedir operações “Guardar como”.
- Proteger o acesso às aplicações ao exigir um PIN/código de acesso ou credenciais empresariais.
- Fazer com que todas as ligações Web abram no Browser Gerido do Intune.

Este conjunto de regras é denominado [políticas de gestão de aplicações móveis (MAM)](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md). Pode aplicar políticas de MAM às aplicações em execução nos dispositivos que podem ou não ser geridos por si.  

Pode proteger os dados da empresa através de políticas de MAM para dispositivos **inscritos no Intune**, dispositivos **inscritos e geridos por uma solução de gestão de dispositivos móveis (MDM) de terceiros** ou dispositivos que **não estão inscritos em nenhuma solução de MDM**, como os dispositivos pertencentes aos empregados.

Para associar uma aplicação a uma política de MAM, a aplicação tem de incorporar o Software Development Kit (SDK) da Aplicação do Microsoft Intune ou pode utilizar a Ferramenta de Encapsulamento de Aplicações.

Aplicações como as do Microsoft Office têm o SDK da Aplicação Intune incorporado. Pode ver a lista completa de aplicações suportadas na [Galeria de aplicações móveis do Microsoft Intune](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) na página de parceiros de aplicações do Microsoft Intune. Escolha a aplicação para ver os cenários e as plataformas suportados e se a aplicação suporta várias identidades.

Também pode [ativar as suas aplicações de linha de negócios personalizadas incorporadas](/intune/apps-prepare-mobile-application-management) para utilizar com políticas de MAM.

Além de restringir o movimento de dados, se um dispositivo se perder ou for roubado ou se o utilizador já não estiver a trabalhar na sua empresa, pode [apagar seletivamente os dados da empresa](wipe-managed-company-app-data-with-microsoft-intune.md), deixando apenas os dados pessoais.

