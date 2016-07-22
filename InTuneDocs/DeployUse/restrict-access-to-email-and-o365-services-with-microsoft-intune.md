---
title: "Restringir o acesso ao e-mail e aos serviços do O365 | Microsoft Intune"
description: 
keywords: 
author: karthikaraman
manager: jeffgilb
ms.date: 06/16/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c564d292-b83b-440d-bf08-3f5b299b7a5e
ms.reviewer: chrisgre
ms.suite: ems
ms.sourcegitcommit: f770bdc312879d1c833e8861494ecd2204ea603a
ms.openlocfilehash: ebce26b0e09bb5282475cb1a39c8070a5d5b44aa


---

# Restringir o acesso ao e-mail, ao O365 e outros serviços com o Microsoft Intune
Pode restringir o acesso ao e-mail da empresa e aos serviços do O365 através do acesso condicional do Intune. A capacidade de acesso condicional do Intune permite assegurar que o acesso ao e-mail da empresa e aos serviços do O365 é restringido aos dispositivos que estão em conformidade com as regras que definir.
## Como funciona o acesso condicional?
As definições de política de conformidade são utilizadas para avaliar a conformidade do dispositivo. A política de acesso condicional utiliza a avaliação para restringir ou permitir o acesso a um serviço específico. Quando uma política de acesso condicional é utilizada em combinação com uma política de conformidade, apenas os dispositivos conformes terão permissão para aceder ao serviço.

Tenha em atenção que o utilizador que está a utilizar o dispositivo também tem de ter uma política de conformidade implementada para que o dispositivo seja avaliado em termos de conformidade.
Se não estiver implementada nenhuma política de conformidade no utilizador, o dispositivo é tratado como conforme e não serão aplicadas restrições de acesso.

Quando os dispositivos não cumprem as condições definidas nas políticas, o final utilizador é orientado através do processo de inscrição do dispositivo e da correção do problema que impede o dispositivo de ser conforme.

Fluxo típico de acesso condicional:

![O diagrama mostra os pontos de decisão utilizados para determinar se um dispositivo tem permissão de acesso a um serviço ou está bloqueado](../media/ConditionalAccess4.png)

## Como configurar o acesso condicional?
Utilize o acesso condicional para gerir o acesso ao Microsoft **Exchange No Local**, **Exchange Online**, **Exchange Online Dedicado**,  **SharePoint Online** e **Skype para Empresas Online**.

Para configurar o acesso condicional, configure uma política de conformidade de dispositivo e uma política de acesso condicional.

A política de conformidade inclui definições como código de acesso, encriptação e se o dispositivo tem ou não jailbreak. O dispositivo tem de cumprir estas regras para ser considerado conforme.

Pode definir uma política de acesso condicional para restringir o acesso com base:
- No estado de conformidade do dispositivo.
- Na plataforma em execução no dispositivo.
- No tipo de aplicações utilizadas para aceder aos serviços.

Ao contrário de outras políticas do Intune, não implementa políticas de acesso condicional. Em vez disso, depois de configurar a política e selecionar os utilizadores que devem ter a política, a política é aplicada a todos os utilizadores visados. Quando um utilizador é direcionado por uma política, cada dispositivo que utiliza tem de estar em conformidade para poder aceder aos recursos.


## Passos seguintes
1. [Saiba mais sobre a política de conformidade de dispositivo e como funciona ](introduction-to-device-compliance-policies-in-microsoft-intune.md)

2. [Criar uma política de conformidade](create-a-device-compliance-policy-in-microsoft-intune.md)

2.  Crie uma política de acesso condicional para um dos seguintes:
> [!div class="op_single_selector"]
  - [[!div class="op_single_selector"]](restrict-access-to-exchange-online-with-microsoft-intune.md)
  - [Criar uma política de acesso condicional para o Exchange Online](restrict-access-to-exchange-onpremises-with-microsoft-intune.md)
  - [Criar uma política de acesso condicional para o Exchange No Local](restrict-access-to-exchange-online-with-microsoft-intune.md)
  - [Criar uma política de acesso condicional para o Exchange Online Dedicado](restrict-access-to-exchange-onpremises-with-microsoft-intune.md)
  - [Criar uma política de acesso condicional para o Exchange Online Dedicado legado](restrict-access-to-sharepoint-online-with-microsoft-intune.md)
  - [Criar uma política de acesso condicional para o SharePoint Online](restrict-access-to-skype-for-business-online-with-microsoft-intune.md)
  - [Criar uma política de acesso condicional para o Skype para Empresas Online](restrict-access-to-dynamics-crm-online-with-microsoft-intune.md)



<!--HONumber=Jul16_HO2-->


