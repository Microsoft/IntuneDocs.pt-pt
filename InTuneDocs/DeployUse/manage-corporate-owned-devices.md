---
# required metadata

title: Gerir dispositivos pertencentes à empresa com o Microsoft Intune | Microsoft Intune
description:
keywords:
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 2b60bbff-25e6-489b-9621-c71b4275fa06

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Inscrever dispositivos pertencentes à empresa com o Microsoft Intune
Os dispositivos pertencentes à empresa (COD) ou à organização podem ser colocados em gestão de variadas formas consoante o dispositivo e como foi comprado.

## Dispositivos iOS pertencentes à empresa
Estes métodos de inscrição são ideais para cenários "Choose your own device" (CYOD), em que a organização compra os dispositivos para os utilizadores, mas pretende manter a gestão dos mesmos. Se a sua organização tiver comprado dispositivos iOS, pode pré-configurar a inscrição para que o dispositivo seja gerido desde a primeira vez que o respetivo utilizador o ligar. O Intune suporta a inscrição através do [Programa de Registo de Dispositivos da Apple (DEP)](ios-device-enrollment-program-in-microsoft-intune.md) ou da ferramenta Apple Configurator em execução num computador Mac para inscrição [direta](ios-direct-enrollment-in-microsoft-intune.md) ou com o [Assistente de Configuração](ios-setup-assistant-enrollment-in-microsoft-intune.md).

[Inscrever dispositivos iOS pertencentes à empresa](enroll-corporate-owned-ios-devices-in-microsoft-intune.md)

## Gestor de inscrição de dispositivos
As organizações podem utilizar o Intune para gerir um grande número de dispositivos móveis com uma única conta de utilizador, denominada conta do gestor de inscrição de dispositivos. Após a criação de uma conta de gestor de inscrição de dispositivos, essa conta pode ser utilizada por um gestor para inscrever mais do que os cinco dispositivos padrão permitidos por predefinição para os utilizadores normais. A inscrição de dispositivos com um gestor de inscrição de dispositivos funciona apenas para dispositivos que não sejam utilizados por um utilizador específico. Estes dispositivos são ideais para aplicações de ponto de venda ou utilitários, mas inadequados para utilizadores que necessitem de aceder ao e-mail ou aos recursos da empresa.

[Inscrever dispositivos pertencentes à empresa com o gestor de inscrição de dispositivos](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)

## Especifique os dispositivos da empresa com os números de identidade internacional do equipamento móvel (IMEI)
Os números de identidade internacional do equipamento móvel (IMEI) exclusivos são uma propriedade de dispositivo comum para inúmeros fabricantes de dispositivos móveis. Os administradores do Intune podem importar os números IMEI para os dispositivos pertencentes à empresa. Quando o dispositivo ficar gerido pelo Intune, pode ser marcado como um dispositivo pertencente à empresa e visado pela política adequada.

[Especifique os dispositivos da empresa com os números de identidade internacional do equipamento móvel (IMEI)](specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers.md)


<!--HONumber=May16_HO2-->


