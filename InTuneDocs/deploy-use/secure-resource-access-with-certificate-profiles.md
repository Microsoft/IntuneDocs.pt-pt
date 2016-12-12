---
title: Perfis de certificado para acesso a recursos | Microsoft Intune
description: Proteja o acesos a VPN, Wi-Fi e e-mail com um certificado instalado no dispositivo de cada utilizador.
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 11/23/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8cbb8499-611d-4217-a7b4-e9b864785dd0
ms.reviewer: kmyrup
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 35d08100b4332cc63667a401143c17972225a908
ms.openlocfilehash: b64260fd44e5c3fd0fb80e0dab4d75bd5c4eb305


---

# <a name="secure-resource-access-with-certificate-profiles-in-microsoft-intune"></a>Proteger o acesso a recursos com perfis de certificados no Microsoft Intune
Quando concede aos utilizadores acesso aos recursos da empresa através de VPN, Wi-Fi ou perfis de e-mail, pode proteger o acesso através de um certificado instalado em cada dispositivo do utilizador. Como funciona:

1. Certifique-se de que tem a infraestrutura de certificados certa, conforme descrito em [Configurar a infraestrutura de certificados para SCEP](configure-certificate-infrastructure-for-scep.md) e [Configurar a infraestrutura de certificados para PFX](configure-certificate-infrastructure-for-pfx.md).

2. Instale um certificado de raiz ou um certificado de Autoridade de Certificação (AC) intermediária em cada dispositivo, para que estes reconheçam a legitimidade da sua AC. Para tal, crie e implemente um **Perfil de Certificado Fidedigno**. Ao implementar este perfil, os dispositivos que gere com o Intune irão pedir e receber o certificado de raiz. Tem de criar um perfil separado para cada plataforma. O **Perfil de Certificado Fidedigno** está disponível para estas plataformas:
 -  iOS 8.0 e posterior
 -  Mac OS X 10.9 e posterior
 -  Android 4.0 e posterior
 -  Android for Work
 -  Windows 8.1 e posterior
 -  Windows Phone 8.1 e posterior

[!INCLUDE[wit_nextref](../includes/afw_rollout_disclaimer.md)]

3. Crie perfis de certificados para que os dispositivos solicitem a utilização de um certificado para autenticação do acesso a VPN, Wi-Fi e e-mail, conforme descrito em [Configurar perfis de certificados do Intune](configure-intune-certificate-profiles.md). Pode criar e implementar um **Perfil de Certificado PKCS #12 (.PFX)** *ou* um **Perfil de Certificado SCEP** em dispositivos que executam as plataformas seguintes:

  -  iOS 8.0 e posterior
  -  Android 4.0 e posterior
  -  Android for Work
  -  Windows 10 (Desktop e Mobile) e posterior

  Utilize um **Perfil de Certificado SCEP** para os dispositivos que executam as seguintes plataformas:
    -   Mac OS X 10.9 e posterior
    -   Windows Phone 8.1 

Tem de criar um perfil separado para cada plataforma. Ao criar o perfil, associe-o ao **Perfil de Certificado de Raiz Fidedigna** criado.

> [!NOTE]           
> - Se não tiver uma Autoridade de Certificação Empresarial, tem de criar uma.
>- Se decidir, com base nas suas plataformas de dispositivos, utilizar o perfil de protocolo SCEP (Simple Certificate Enrollment Protocol), terá também de configurar um servidor do Serviço de Inscrição de Dispositivos de Rede (NDES).
>-  Se planear utilizar o SCEP ou os perfis .PFX, terá de transferir e configurar o Microsoft Intune Certificate Connector.
>-  Saiba como configurar todos os serviços obrigatórios em [Configurar a infraestrutura de certificados para SCEP](configure-certificate-infrastructure-for-scep.md) ou [Configurar a infraestrutura de certificados para PFX](configure-certificate-infrastructure-for-pfx.md).

### <a name="next-steps"></a>Passos seguintes
- [Configurar a infraestrutura de certificados para SCEP](configure-certificate-infrastructure-for-scep.md)
- [Configurar a infraestrutura de certificados para PFX](configure-certificate-infrastructure-for-pfx.md)
- [Configurar perfis de certificado do Intune](configure-intune-certificate-profiles.md)



<!--HONumber=Nov16_HO4-->

