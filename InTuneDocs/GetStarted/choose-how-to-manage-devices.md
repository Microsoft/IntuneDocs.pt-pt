---
title: Escolher como gerir dispositivos | Microsoft Intune
description: "Saiba mais sobre as várias formas de inscrever e gerir dispositivos."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 11/22/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 770aad50-fd7a-4cf1-a793-f95fe47fc3f8
ms.reviewer: angrobe
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 29b6e5a3d319c741482fcc2b600842e2e42b96e2
ms.openlocfilehash: fccdf689868dbb181a171328fb7a8d186b9cb309


---

# <a name="choose-how-to-manage-devices"></a>Escolher como gerir dispositivos

Para tirar partido das várias funcionalidades que o Intune oferece, como a implementação de aplicações e o controlo das definições do dispositivo, os dispositivos têm de ser *geridos*. O método de gestão de dispositivos depende das capacidades do Intune que pretende utilizar.
Este tópico irá ajudá-lo a escolher o método adequado às suas necessidades.

Para gerir dispositivos que executam iOS, Mac OS X, Android e Windows Phone, terá de os *inscrever*.

Para gerir PCs Windows, tem duas opções:

1. Inscrever o dispositivo **ou**
2. Instalar o *cliente de software do Intune*.

## <a name="decide-which-method-to-use"></a>Escolher o método a utilizar
Utilize este fluxo de decisões para decidir como pretende gerir os seus dispositivos.

![Fluxo de decisões para decidir como pretende gerir os seus dispositivos.](./media/choose-manage-method.png)

Inscreva PCs Windows para obter máxima funcionalidade. No entanto, o cliente de software do Intune poderá ser mais adequado às suas necessidades quando:

- O PC está a executar o Windows 7
- Pretender gerir atualizações de software e a utilização de licenças do Windows
- Pretender gerir software maligno com o Endpoint Protection e a Firewall do Windows
- Pretender fornecer assistência remota aos utilizadores com o software TeamViewer


Para obter uma lista detalhada das capacidades de gestão obtidas com cada método, veja [Capacidades de gestão de dispositivos móveis](mobile-device-management-capabilities-in-microsoft-intune.md) e [Capacidades de cliente de software de PCs do Intune](windows-pc-management-capabilities-in-microsoft-intune.md).
Para obter informações sobre os dispositivos e os PCs que o Intune suporta, veja [Dispositivos móveis e computadores suportados](/intune/get-started/supported-mobile-devices-and-computers)


## <a name="exchange-activesync-management"></a>Gestão do Exchange ActiveSync
Para além de inscrever um dispositivo ou instalar o cliente de software do Intune, também pode gerir dispositivos [com o Exchange ActiveSync](/intune/deploy-use/mobile-device-management-with-exchange-activesync-and-microsoft-intune). Este método requer a instalação do Conector No Local ou a utilização do Conector de Serviços incorporado para ligar ao seu Exchange Server.
Embora esta seja uma terceira opção para gerir dispositivos, fornece um conjunto limitado de capacidades de gestão, em comparação com os outros métodos.


## <a name="next-steps"></a>Passos seguintes

- [Escolher como inscrever dispositivos móveis](/intune/get-started/choose-how-to-enroll-devices1)
- [Gerir PCs Windows com o software de cliente do Intune para PC](/intune/deploy-use/manage-windows-pcs-with-microsoft-intune)



- [Gestão de dispositivos móveis do Exchange ActiveSync com o Microsoft Intune](/intune/deploy-use/mobile-device-management-with-exchange-activesync-and-microsoft-intune).



<!--HONumber=Nov16_HO4-->


