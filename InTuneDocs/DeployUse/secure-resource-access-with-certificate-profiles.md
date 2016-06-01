---
# required metadata

title: Permitir o acesso a recursos da empresa através de perfis de certificados com o Microsoft Intune | Microsoft Intune
description:
keywords:
author: Nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 8cbb8499-611d-4217-a7b4-e9b864785dd0

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Proteger o acesso a recursos com perfis de certificados no Microsoft Intune
Quando ativar o acesso aos recursos da empresa através de VPN, Wi-Fi ou perfis de e-mail, pode optar por proteger esse acesso com um certificado instalado em cada dispositivo do utilizador. Como funciona:

1. Certifique-se de que tem a infraestrutura de certificados certa, conforme descrito em [Configure certificate infrastructure (Configurar a infraestrutura de certificados)](configure-certificate-infrastructure.md)

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
> A configuração de todos estes certificados está descrita no tópico [Configure certificate infrastructure (Configurar a infraestrutura de certificados)](configure-certificate-infrastructure.md)

### Passos seguintes
- [Configurar a infraestrutura de certificados](configure-certificate-infrastructure.md)
- [Configurar perfis de certificado do Intune](configure-intune-certificate-profiles.md)



<!--HONumber=May16_HO2-->


