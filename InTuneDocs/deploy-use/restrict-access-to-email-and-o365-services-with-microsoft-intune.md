---
title: "Restringir o acesso ao e-mail e aos serviços do Office 365 | Microsoft Intune"
description: "Este tópico descreve como pode utilizar o acesso condicional para permitir que apenas dispositivos compatíveis acedam ao e-mail e aos dados da empresa no SharePoint online e noutros serviços."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 11/14/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c564d292-b83b-440d-bf08-3f5b299b7a5e
ms.reviewer: chrisgre
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 87e37cd8334ddb9331c0662b691545cd0ab0553a
ms.openlocfilehash: 5665ca431eb186d4378953b7047228e07ae9dc60


---

# <a name="restrict-access-to-email-office-365-and-other-services-with-microsoft-intune"></a>Restringir o acesso ao e-mail, ao Office 365 e a outros serviços com o Microsoft Intune
Pode restringir o acesso ao e-mail da empresa, ao Office 365 e a outros serviços com o acesso condicional do Intune. A capacidade de acesso condicional do Intune permite assegurar que o acesso ao e-mail da empresa e aos serviços do Office 365 é restringido aos dispositivos que estão em conformidade com as regras definidas.
## <a name="how-does-conditional-access-work"></a>Como funciona o acesso condicional?
Pode utilizar as definições de política de conformidade para avaliar a conformidade de um dispositivo. Uma política de acesso condicional utiliza a avaliação para restringir ou permitir o acesso a um serviço específico. Quando utiliza uma política de acesso condicional em combinação com uma política de conformidade, apenas os dispositivos conformes têm permissão para aceder ao serviço. A política de conformidade e a política de acesso condicional são implementadas no utilizador. Qualquer dispositivo que o utilizador utilize para aceder aos serviços é analisado relativamente à conformidade com as políticas.

Tenha em atenção que o utilizador que está a utilizar o dispositivo tem de ter uma política de conformidade implementada para que o dispositivo seja avaliado em termos de conformidade.
Se não estiver implementada nenhuma política de conformidade para o utilizador, o dispositivo é tratado como conforme e não são aplicadas restrições de acesso.

Quando os dispositivos não cumprem as condições definidas nas políticas, o utilizador final é orientado através do processo de inscrição do dispositivo e da correção do problema que impede o dispositivo de estar conforme.

Fluxo típico de acesso condicional:

![Diagrama que mostra os pontos de decisão que são utilizados para determinar se um dispositivo tem permissão de acesso a um serviço ou se está bloqueado](../media/ConditionalAccess4.png)

## <a name="how-to-configure-conditional-access"></a>Como configurar o acesso condicional
Utilize o acesso condicional para gerir o acesso ao Microsoft **Exchange No Local**, **Exchange Online**, **Exchange Online Dedicado**, **SharePoint Online** e **Skype para Empresas Online**.

Para configurar o acesso condicional, configure uma política de conformidade de dispositivos e uma política de acesso condicional.

A política de conformidade inclui definições como código de acesso, encriptação e se o dispositivo tem ou não jailbreak. O dispositivo tem de cumprir estas regras para ser considerado conforme.

Pode definir uma política de acesso condicional para restringir o acesso com base:
- No estado de conformidade do dispositivo.
- Na plataforma que está em execução no dispositivo.
- No tipo de aplicações que são utilizadas para aceder aos serviços.

Ao contrário de outras políticas do Intune, não precisa implementar políticas de acesso condicional. Em vez disso, depois de configurar a política e selecionar os utilizadores que devem ter a política, esta é aplicada a todos os utilizadores visados. Quando um utilizador é direcionado por uma política, cada dispositivo que utiliza tem de estar em conformidade para que possam aceder aos recursos.


## <a name="next-steps"></a>Próximos passos
1. [Saiba mais sobre a política de conformidade de dispositivos e como funciona](introduction-to-device-compliance-policies-in-microsoft-intune.md).

2. [Criar uma política de conformidade](create-a-device-compliance-policy-in-microsoft-intune.md).

2.  Crie uma política de acesso condicional para um dos seguintes:
> [!div class="op_single_selector"]
  - [Criar uma política de acesso condicional para o Exchange Online](restrict-access-to-exchange-online-with-microsoft-intune.md)
  - [Criar uma política de acesso condicional para o Exchange No Local](restrict-access-to-exchange-onpremises-with-microsoft-intune.md)
  - [Criar uma política de acesso condicional para o novo Exchange Online Dedicado](restrict-access-to-exchange-online-with-microsoft-intune.md)
  - [Criar uma política de acesso condicional para o Exchange Online Dedicado legado](restrict-access-to-exchange-onpremises-with-microsoft-intune.md)
  - [Criar uma política de acesso condicional para o SharePoint Online](restrict-access-to-sharepoint-online-with-microsoft-intune.md)
  - [Criar uma política de acesso condicional para o Skype para Empresas Online](restrict-access-to-skype-for-business-online-with-microsoft-intune.md)
  - [Criar uma política de acesso condicional para o Dynamics CRM Online](restrict-access-to-dynamics-crm-online-with-microsoft-intune.md)



<!--HONumber=Dec16_HO2-->


