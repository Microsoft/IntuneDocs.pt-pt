---
title: "Gerir dispositivos pertencentes à empresa | Microsoft Intune"
description: "Inscreva dispositivos da empresa de várias formas com base no tipo de dispositivo, na forma como foi comprado e nas necessidades da organização."
keywords: 
author: staciebarker
ms.author: stabar
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
ms.sourcegitcommit: 9d44a6494bed0758b9768045bd204ea0eb481636
ms.openlocfilehash: 7577cbab528d88635e8551bf8de1ffd49becaa84


---

# <a name="enroll-corporateowned-devices-by-using-intune"></a>Inscrever dispositivos pertencentes à empresa através do Intune

Pode inscrever dispositivos pertencentes à empresa ou à organização para os gerir com o Intune de várias formas, consoante o tipo de dispositivo, como foi comprado e as necessidades da organização. Também pode instalar a aplicação do Portal da Empresa para gerir dispositivos da empresa, como num cenário "traga o seu próprio dispositivo" (BYOD).

## <a name="enroll-corporateowned-ios-devices"></a>Inscrever dispositivos iOS pertencentes à empresa

Os métodos de inscrição de dispositivos da empresa são uma boa opção para cenários "selecione o seu próprio dispositivo" (CYOD). Num ambiente CYOD, a organização paga um dispositivo que o utilizador seleciona e a organização gere o dispositivo.

Se oferecer aos utilizadores dispositivos iOS para escolha, pode pré-configurar a inscrição para que o dispositivo seja gerido com o Intune na primeira vez que o utilizador o ligar. O Intune suporta a inscrição através do [Programa de Registo de Dispositivos da Apple (DEP)](ios-device-enrollment-program-in-microsoft-intune.md) ou da ferramenta Apple Configurator num computador Mac para inscrição [direta](ios-direct-enrollment-in-microsoft-intune.md) ou com o [Assistente de Configuração](ios-setup-assistant-enrollment-in-microsoft-intune.md).

Saiba como [inscrever dispositivos iOS pertencentes à empresa](enroll-corporate-owned-ios-devices-in-microsoft-intune.md).

## <a name="create-a-device-enrollment-manager-account"></a>Criar uma conta de gestor de inscrição de dispositivos

Pode criar uma conta de gestor de inscrição de dispositivos (DEM) no Intune para gerir um grande número de dispositivos móveis para a sua organização. Após criar uma conta DEM, um gestor de conta designado pode inscrever mais de 15 dispositivos (que um utilizador padrão pode inscrever).

Pode utilizar uma conta DEM para inscrever apenas dispositivos não utilizados por um único utilizador específico. Estes tipos de dispositivo são bons, por exemplo, para aplicações de utilitários ou ponto de venda, mas não para utilizadores que necessitem de aceder a recursos de empresa ou e-mail.

Saiba como [inscrever dispositivos pertencentes à empresa ao utilizar uma conta DEM](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md).

## <a name="enroll-corporateowned-windows-10-enterprise-devices"></a>Inscrever dispositivos Windows 10 Enterprise pertencentes à empresa

Se utilizar o Azure Active Directory Premium ou o Microsoft Enterprise Mobility Suite na sua organização, pode [inscrever dispositivos com Windows 10 Enterprise](https://docs.microsoft.com/active-directory/active-directory-azureadjoin-windows10-devices-overview). Quando um utilizador adiciona uma conta escolar ou profissional a um dispositivo, este é automaticamente marcado como "pertencente à empresa".

## <a name="import-imei-numbers"></a>Importar números IMEI

Muitos fabricantes de dispositivos móveis utilizam um número exclusivo, denominado Identidade Internacional do Equipamento Móvel (IMEI) nos respetivos dispositivos. Pode importar números IMEI para dispositivos pertencentes à sua organização. Quando o dispositivo for gerido pelo Intune, é identificado como dispositivo pertencente à empresa.

Saiba como [identificar dispositivos pertencentes à empresa ao utilizar números IMEI](specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers.md).

## <a name="identify-a-device-as-corporateowned"></a>Identificar um dispositivo como pertencente à empresa

Numa lista de dispositivos, o valor de **Propriedade** é **Empresarial**. Um dispositivo pertencente à empresa tem uma das seguintes características:

 - O dispositivo foi [inscrito ao utilizar uma conta DEM](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md).
 - O dispositivo foi inscrito através do [Apple DEP](ios-device-enrollment-program-in-microsoft-intune.md) ou do [Apple Configurator](ios-setup-assistant-enrollment-in-microsoft-intune.md).
 - O fabricante do dispositivo [pré-declarou o dispositivo através de números IMEI](specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers.md).
 - O dispositivo está registado no [Azure Active Directory ou Enterprise Mobility Suite como um dispositivo Windows 10 Enterprise](https://docs.microsoft.com/active-directory/active-directory-azureadjoin-windows10-devices-overview).



<!--HONumber=Nov16_HO2-->


