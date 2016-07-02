---
title: "Proteger aplicações e dados | Microsoft Intune"
description: 
keywords: 
author: karthikaraman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5c46e188-87eb-4ce2-b184-24809e8bf783
ms.reviewer: chrisgre
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ded7bd6c971a9448ad6e6492ebc5e42dfcb5d76e
ms.openlocfilehash: 9445b4b171eb2102d73cf0e866e85b535274eee2


---

# Proteger aplicações e dados com o Microsoft Intune


O Intune protege os dados da empresa através de várias camadas de tecnologia.  Na camada de identidade, o acesso condicional protege o acesso aos serviços ao permitir apenas o acesso a partir de dispositivos geridos e conformes.  Na camada de aplicação de cliente, a gestão de aplicações móveis (MAM) protege a perda de dados ao impedir que os dados sejam movidos para aplicações não protegidas ou localizações de armazenamento e ao apagar dados em caso de perda ou roubo de um dispositivo.  Estas duas camadas de proteção devem ser utilizadas em conjunto para proteger os dados enquanto mantém a sua força de trabalho móvel produtiva.

Um primeiro passo importante para proteger os dados da empresa é implementar o acesso condicional ao assegurar que os dispositivos utilizados para aceder a esses dados estão a utilizar proteções de segurança como palavra-passe segura, encriptação e não têm jailbreak. O Microsoft Intune permite definir as condições que os dispositivos têm de cumprir antes de serem autorizados a aceder ao e-mail e aos dados da empresa.

O [acesso condicional](restrict-access-to-email-and-o365-services-with-microsoft-intune.md) é determinado por dois tipos de políticas que pode definir no Intune:
- As [políticas de conformidade](introduction-to-device-compliance-policies-in-microsoft-intune.md) determinam a conformidade de um dispositivo. Avaliam definições e condições como:
  - PINs e palavras-passe: pode criar regras para a solicitação de palavras-passe antes de desbloquear um dispositivo, os requisitos de complexidade da palavra-passe e outras definições de palavra-passe.
  - Encriptação: pode restringir o acesso a dispositivos encriptados.
  - O dispositivo não tem jailbreak nem root: o Intune pode detetar se um dispositivo inscrito tem jailbreak e pode definir a política para bloquear o acesso nesses dispositivos.
- As [políticas de acesso condicional](restrict-access-to-email-and-o365-services-with-microsoft-intune.md) estão configuradas para um determinado serviço como o Exchange Online ou o SharePoint Online. Para cada serviço, pode definir a que grupos de utilizadores estas políticas devem ser aplicadas. Por exemplo, pode certificar-se de que todos os membros do departamento financeiro apenas podem aceder ao e-mail da empresa a partir de dispositivos inscritos e conformes.

Proteger o acesso aos recursos da empresa é apenas o primeiro passo para proteger os dados da empresa. Ainda precisa de proteger os dados assim que tiverem sido acedidos no dispositivo. Os dados podem agora ser copiados, movidos, guardados numa localização diferente ou partilhados. O Intune resolve este problema ao permitir restringir o movimento de dados através da criação de um conjunto de regras como:
- Bloquear operações copiar e colar ou impedir a transferência de dados fora do contexto de trabalho.
- Impedir cópias de segurança para armazenamento pessoal na nuvem, impedindo o Guardar como.
- Proteger o acesso às aplicações exigindo um PIN/código de acesso ou credenciais empresariais.
- Fazer com que todas as ligações Web abram no Intune Managed Browser.

Este conjunto de regras é denominado [políticas de gestão de aplicações móveis (MAM)](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md).  As políticas de MAM podem ser aplicadas às aplicações em execução nos dispositivos que podem ou não ser geridos por si.  Pode proteger os dados da empresa através de políticas de MAM para dispositivos inscritos no Intune, dispositivos inscritos e geridos por outro MDM de terceiros ou um dispositivo que não pode ser gerido por si, como os dispositivos pertencentes aos empregados.

Para associar uma aplicação a uma política de MAM, a aplicação tem de incorporar o Microsoft Intune App Software Development Kit (SDK) ou utilizar a ferramenta de encapsulamento de aplicações.

Aplicações como as do Microsoft Office têm o SDK da Aplicação incorporado. A lista completa de aplicações suportadas pode ser encontrada na [galeria de aplicações móveis do Microsoft Intune](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx), na página de parceiros de aplicações do Microsoft Intune. Escolha a aplicação para ver os cenários suportados, as plataformas e se pretende ou não que a aplicação suporte várias identidades.

Também pode [ativar as suas aplicações de linha de negócios personalizadas incorporadas](decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune.md) para utilizar com políticas de MAM.

Além de restringir o movimento de dados, se um dispositivo se perder ou for roubado, ou se o utilizador já não estiver a trabalhar na sua empresa, pode [apagar seletivamente os dados da empresa](wipe-managed-company-app-data-with-microsoft-intune.md), deixando apenas os dados pessoais.



<!--HONumber=Jun16_HO4-->


