---
title: "Bloquear aplicações sem autenticação moderna | Microsoft Intune"
description: 
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 10/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 098b652c-01e0-45d1-a731-620b0d3dc7c1
ms.reviewer: chrisgre
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 0f78ece8bbaf813c0082e6b764d174cf25bcb618
ms.openlocfilehash: 89f0bc5dd10c173718f9698e6e0342b5eb8c56e8


---

# Bloquear aplicações que não utilizam autenticação moderna (ADAL)
O acesso condicional para aplicações com políticas de MAM (MAM CA) depende de aplicações que utilizam uma [autenticação moderna](https://support.office.com/en-US/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a), ou seja, uma implementação de OAuth2. A maioria das aplicações modernas do Office para ambiente de trabalho e para dispositivos móveis utilizam autenticação moderna, no entanto, existem aplicações de terceiros e aplicações do Office mais antigas que utilizam outros métodos de autenticação como a autenticação básica e a autenticação baseada em formulários.

Para bloquear o acesso a estas aplicações, recomendamos que efetue o seguinte:

* Configure regras de afirmações do ADFS para bloquear protocolos de autenticação não moderna. São fornecidas instruções detalhadas no cenário 3 – [bloquear todo o acesso ao O365, exceto aplicações baseadas no browser](https://technet.microsoft.com/library/dn592182.aspx).

### Consulte também
[Permitir que apenas aplicações suportadas pelo Intune acedam aos serviços do O365](allow-policy-managed-apps-access-to-o365.md)



<!--HONumber=Oct16_HO2-->


