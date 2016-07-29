---
title: Perfis de certificado para acesso a recursos | Microsoft Intune
description: Proteja o acesos a VPN, Wi-Fi e e-mail com um certificado instalado no dispositivo de cada utilizador.
keywords: 
author: Nbigman
manager: angrobe
ms.date: 07/21/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8cbb8499-611d-4217-a7b4-e9b864785dd0
ms.reviewer: kmyrup
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 300df17fd5844589a1e81552d2d590aee5615897
ms.openlocfilehash: 98c32f924b60734d9a592ebdd7e00429dc32af26


---

# Proteger o acesso a recursos com perfis de certificados no Microsoft Intune
Quando ativar o acesso aos recursos da empresa através de VPN, Wi-Fi ou perfis de e-mail, pode optar por proteger esse acesso com um certificado instalado em cada dispositivo do utilizador. Como funciona:

1. Certifique-se de que tem a infraestrutura de certificados certa, conforme descrito em [Configurar a infraestrutura de certificados para SCEP](configure-certificate-infrastructure-for-scep.md) ou [Configurar a infraestrutura de certificados para PFX](configure-certificate-infrastructure-for-pfx.md).

2. Instale um certificado de raiz (ou certificado de AC intermediária) em cada dispositivo, para que estes reconheçam a legitimidade da sua Autoridade de Certificação. Pode fazê-lo ao criar e implementar um **Perfil de Certificado Fidedigno**. Ao implementar este perfil, os dispositivos que gere com o Intune irão pedir e receber o certificado de raiz. Tem de criar um perfil separado para cada plataforma. O **Perfil de Certificado Fidedigno** está disponível para estas plataformas:
 -  iOS 7.1 e posterior
 -  Mac OS X 10.9 e posterior
 -  Android 4.0 e posterior
 -  Windows 8.1 e posterior
 -  Windows Phone 8.1 e posterior

3. Faça com que cada dispositivo peça a utilização de um certificado para autenticação de e-mail, VPN e acesso a Wi-Fi, conforme descrito em [Configure intune certificate profiles (Configurar perfis de certificados do Intune)](configure-intune-certificate-profiles.md). Pode criar e implementar um **Perfil de Certificado PKCS #12 (.PFX)** ou um **Perfil de Certificado SCEP** em dispositivos nas plataformas seguintes.

-  Android 4.0 e posterior
-  iOS 7.1 e posterior
-  Windows 10 (Desktop e Mobile) e posterior

Utilize o **Perfil de Certificado SCEP** em:
-   Mac OS X 10.9 e posterior
-   Windows Phone 8.1 e posterior

Tem de criar um perfil separado para cada plataforma. Ao criar o perfil irá associá-lo ao **perfil de Certificado de Raiz Fidedigna** que já criou.

> [!NOTE]           
> -    Se não tiver uma autoridade de certificação empresarial, tem de criar uma.
>- Se decidir, com base nas suas plataformas de dispositivos, utilizar o perfil de protocolo SCEP (Simple Certificate Enrollment Protocol), terá também de configurar um servidor do Serviço de Inscrição de Dispositivos de Rede (NDES).
>-  Se planeia utilizar o SCEP ou perfis .PFX, tem de transferir e configurar o Microsoft Intune Certificate Connector.
> Todas estas configurações estão descritas em [Configurar a infraestrutura de certificados para SCEP](configure-certificate-infrastructure-for-scep.md) e [Configurar a infraestrutura de certificados para PFX](configure-certificate-infrastructure-for-pfx.md).

### Passos seguintes
- [Configurar a infraestrutura de certificados para SCEP](configure-certificate-infrastructure-for-scep.md)
- [Configurar a infraestrutura de certificados para PFX](configure-certificate-infrastructure-for-pfx.md)
- [Configurar perfis de certificado do Intune](configure-intune-certificate-profiles.md)



<!--HONumber=Jul16_HO4-->


