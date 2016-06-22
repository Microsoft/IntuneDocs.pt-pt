---
# required metadata

title: Inscrever dispositivos | Microsoft Intune
description:
keywords:
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 8fc415f7-0053-4aa5-8d2b-03202eca4b87

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: damionw
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Inscrever dispositivos para gestão no Intune
A gestão de dispositivos móveis (MDM) do Microsoft Intune utiliza a inscrição para trazer dispositivos para gestão e permitir o acesso aos recursos. A forma como irá inscrever dispositivos depende do tipo de dispositivo, da propriedade e do nível de gestão necessário. Os cenários de "Bring your own device" (BYOD) e de dispositivos pertencentes à empresa (COD) necessitam de um processo de inscrição. As organizações que utilizem o Exchange ActiveSync, no local ou alojado na nuvem, podem tornar a gestão mais leve sem requisitos de inscrição. Os PCs Windows também podem ser geridos com o software de cliente do Intune.

###  Plataformas de dispositivos suportadas

O Intune pode gerir as seguintes plataformas de dispositivos:

[!INCLUDE[mdm-supported-devices](../includes/mdm-supported-devices.md)]

## Ativar a inscrição de dispositivos  
 A inscrição permite que os utilizadores acedam aos recursos da empresa nos respetivos dispositivos pessoais e permite que o administrador assegure que os dispositivos cumprem as políticas que protegem os recursos da empresa. Esta é a melhor forma de ativar os cenários "bring your own device" no Intune. O administrador tem de ativar a inscrição na consola do Intune, o que pode requerer a criação de uma relação de confiança com o dispositivo e a atribuição de licenças aos utilizadores. Em seguida, o dispositivo é inscrito, normalmente por utilizadores que introduzem as respetivas credenciais profissionais ou escolares. O dispositivo recebe então a política do Intune e obtém acesso aos recursos.

[Preparar-se para inscrever dispositivos no Intune](get-ready-to-enroll-devices-in-microsoft-intune.md)

## Inscrever dispositivos pertencentes à empresa
Os dispositivos pertencentes à empresa (COD) podem ser geridos com a consola do Intune. Os dispositivos iOS podem ser inscritos diretamente através das ferramentas fornecidas pela Apple. Todos os tipos de dispositivos podem ser inscritos por um administrador ou gestor utilizando o gestor de inscrição de dispositivos. Os dispositivos com um número IMEI também podem ser identificados e marcados como pertencentes à empresa para ativar cenários COD.

[Inscrever dispositivos pertencentes à empresa](manage-corporate-owned-devices.md)

## Gestão de dispositivos móveis com o Exchange ActiveSync e o Intune
Os dispositivos móveis que não estão inscritos, mas que se ligam ao Exchange ActiveSync (EAS), podem ser geridos pelo Intune utilizando a política de MDM do EAS. O Intune utiliza um Exchange Connector para comunicar com o EAS, no local e alojado na nuvem.



[Gestão de dispositivos móveis com o Exchange ActiveSync e o Intune](mobile-device-management-with-exchange-activesync-and-microsoft-intune.md)


## Gerir Computadores com Windows com o Intune  
Também pode utilizar o Microsoft Intune para gerir PCs Windows utilizando o software de cliente do PC Windows do Intune. Os PCs geridos com o cliente do Intune podem:

 - Reportar inventários de software e hardware
 - Instalar aplicações de ambiente de trabalho (por exemplo, ficheiros .exe e .msi)
 - Definições de firewall

Os computadores geridos com o software de cliente do Intune não podem ser apagados seletivamente nem extintos e não podem tirar partido das inúmeras funcionalidades de gestão do Intune, como o acesso condicional, as definições de VPN e Wi-Fi ou a implementação de certificados e configurações de e-mail.

[Gerir Computadores com Windows com o Intune](manage-windows-pcs-with-microsoft-intune.md)


<!--HONumber=Jun16_HO2-->


