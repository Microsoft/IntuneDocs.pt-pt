---
title: "Gerir dispositivos pertencentes à empresa | Microsoft Intune"
description: "Os dispositivos pertencentes à empresa (COD) podem ser colocados em gestão de variadas formas, consoante o dispositivo, a forma como foi comprado e as necessidades da sua organização."
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/20/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2b60bbff-25e6-489b-9621-c71b4275fa06
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ecfeb73efed4a47256275120c52de232c556adfe
ms.openlocfilehash: 58efadf2f9fc34a31070aff93e86083583630caa


---

# Inscrever dispositivos pertencentes à empresa com o Microsoft Intune
Os dispositivos pertencentes à empresa (COD) ou à organização podem ser colocados em gestão pelo Intune de variadas formas consoante o dispositivo, de como foi comprado e das necessidades da organização. Os dispositivos pertencentes à empresa também podem ser inscritos e geridos através da instalação da aplicação Portal da Empresa, tal como nos cenários "bring your own device" (BYOD).

## Dispositivos iOS pertencentes à empresa
Estes métodos de inscrição são ideais para cenários "Choose your own device" (CYOD), em que a organização compra os dispositivos para os utilizadores, mas pretende manter a gestão dos mesmos. Se a sua organização tiver comprado dispositivos iOS, pode pré-configurar a inscrição para que o dispositivo seja gerido desde a primeira vez que o respetivo utilizador o ligar. O Intune suporta a inscrição através do [Programa de Registo de Dispositivos da Apple (DEP)](ios-device-enrollment-program-in-microsoft-intune.md) ou da ferramenta Apple Configurator em execução num computador Mac para inscrição [direta](ios-direct-enrollment-in-microsoft-intune.md) ou com o [Assistente de Configuração](ios-setup-assistant-enrollment-in-microsoft-intune.md).

[Inscrever dispositivos iOS pertencentes à empresa](enroll-corporate-owned-ios-devices-in-microsoft-intune.md)

## Gestor de inscrição de dispositivos
As organizações podem utilizar o Intune para gerir um grande número de dispositivos móveis com uma única conta de utilizador, denominada conta do gestor de inscrição de dispositivos. Após a criação de uma conta de gestor de inscrição de dispositivos, essa conta pode ser utilizada por um gestor para inscrever mais do que os cinco dispositivos padrão permitidos por predefinição para os utilizadores normais. A inscrição de dispositivos com um gestor de inscrição de dispositivos funciona apenas para dispositivos que não sejam utilizados por um utilizador específico. Estes dispositivos são ideais para aplicações de ponto de venda ou utilitários, mas inadequados para utilizadores que necessitem de aceder ao e-mail ou aos recursos da empresa.

[Inscrever dispositivos pertencentes à empresa com o gestor de inscrição de dispositivos](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)

## Inscrever dispositivos Windows 10 pertencentes à empresa

Se a sua organização tiver o Azure Active Directory Premium (AADP) ou o Enterprise Management Suite (EMS), pode [inscrever o Windows 10 para empresas](https://docs.microsoft.com/active-directory/active-directory-azureadjoin-windows10-devices-overview) e os dispositivos serão automaticamente assinalados como “pertencentes à empresas” quando os utilizadores adicionam as contas escolares ou profissionais deles.

## Identificar os dispositivos como pertencentes à empresa

Os dispositivos pertencentes à empresa são listados como **Empresa** em **Propriedade**, nas listas de dispositivos. Os dispositivos podem ser identificados como pertencentes à empresa das seguintes formas:

 - [Inscritos com o gestor de inscrição de dispositivos (DEM)](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)
 - Inscritos com o [Programa de Inscrição de Dispositivos (DEP)](ios-device-enrollment-program-in-microsoft-intune.md) ou o [Apple Configurator](ios-setup-assistant-enrollment-in-microsoft-intune.md) da Apple
 - [Pré-declarar dispositivos com números IMEI](specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers.md)
 - [Registo de dispositivos Windows 10 do Azure Active Directory/Enterprise Management Suite](https://docs.microsoft.com/active-directory/active-directory-azureadjoin-windows10-devices-overview)

### Identidade internacional do equipamento móvel (IMEI)

Os números de identidade internacional do equipamento móvel (IMEI) exclusivos são uma propriedade de dispositivo comum para inúmeros fabricantes de dispositivos móveis. Os administradores do Intune podem importar os números IMEI para os dispositivos pertencentes à empresa. Quando o dispositivo ficar gerido pelo Intune, é identificado como dispositivo pertencente à empresa.

[Especifique os dispositivos da empresa com os números de identidade internacional do equipamento móvel (IMEI)](specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers.md)



<!--HONumber=Jul16_HO4-->


