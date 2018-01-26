---
title: "O que é a inscrição de dispositivos do Microsoft Intune"
titlesuffix: Azure portal
description: "Saiba mais sobre a inscrição de dispositivos iOS, Android e Windows."
keywords: 
author: ErikjeMS
ms.author: erikje
manager: angrobe
ms.date: 12/29/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6f67fcd2-5682-4f9c-8d74-d4ab69dc978c
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: dc0105bb786d8b1e569b11898b0d3757feba406a
ms.sourcegitcommit: a55a7119a15836b6941fdd5b32b9076139093693
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/10/2018
---
# <a name="what-is-device-enrollment"></a>O que é a inscrição de dispositivos?
[!INCLUDE[azure_portal](./includes/azure_portal.md)]

O Intune permite-lhe gerir os dispositivos e as aplicações da sua força de trabalho e a forma como acedem aos dados da empresa. Para utilizar esta gestão de dispositivos móveis (MDM), deve primeiro inscrever os dispositivos no serviço Intune. Quando um dispositivo é inscrito, é emitido um certificado MDM. Este certificado é utilizado para comunicar com o serviço Intune.

Como pode constatar nas tabelas seguintes, existem vários métodos para inscrever os dispositivos da força de trabalho. Cada método depende da propriedade do dispositivo (pessoal ou empresarial), do tipo de dispositivo (iOS, Windows, Android) e dos requisitos de gestão (reposições, afinidade, bloqueio).

## <a name="ios-enrollment-methods"></a>Métodos de inscrição do iOS

| **Método** |  **Reposição obrigatória** |    [**Afinidade do Utilizador**](device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile) |   **Bloqueado** | **Detalhes** |
|:---:|:---:|:---:|:---:|:---:|
| | Durante a inscrição, é feita a reposição de fábrica dos dispositivos. |  Associa cada dispositivo a um utilizador.| Os utilizadores não conseguem anular a inscrição dos dispositivos.  | |
|**[BYOD](#bring-your-own-device)** | Não|   Sim |   Não | [Mais informações](./apple-mdm-push-certificate-get.md)|
|**[DEM](#device-enrollment-manager)**| Não |Não |Não  | [Mais informações](./device-enrollment-program-enroll-ios.md)|
|**[DEP](#apple-device-enrollment-program)**|   Sim |   Opcional |  Opcional|[Mais informações](./device-enrollment-program-enroll-ios.md)|
|**[USB-SA](#usb-sa)**| Sim |   Opcional |  Não| [Mais informações](./apple-configurator-setup-assistant-enroll-ios.md)|
|**[USB-Direct](#usb-direct)**| Não |    Não  | Não|[Mais informações](./apple-configurator-direct-enroll-ios.md)|

## <a name="windows-enrollment-methods"></a>Métodos de inscrição do Windows

| **Método** |  **Reposição obrigatória** |    **Afinidade de Utilizador**   |   **Bloqueado** | **Detalhes**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#bring-your-own-device)** | Não |  Sim |   Não | [Mais informações](windows-enroll.md)|
|**[DEM](#device-enrollment-manager)**| Não |Não |Não  |[Mais informações](device-enrollment-manager-enroll.md)|
|**Inscrição automática** | Não |Sim |Não | [Mais informações](./windows-enroll.md#enable-windows-10-automatic-enrollment)|
|**Inscrição em massa** |Não |Não |Não | [Mais informações](./windows-bulk-enroll.md) |

## <a name="android-enrollment-methods"></a>Métodos de inscrição do Android

| **Método** |  **Reposição obrigatória** |    **Afinidade de Utilizador**   |   **Bloqueado** | **Detalhes**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#bring-your-own-device)** | Não|   Sim |   Não | [Mais informações](./android-enroll.md)|
|**[DEM](#device-enrollment-manager)**| Não |Não |Não  |[Mais informações](./device-enrollment-manager-enroll.md)|
|**Android for Work**| Não | Sim | Não| [Mais informações](./android-enroll.md#enable-enrollment-of-android-for-work-devices) |


## <a name="bring-your-own-device"></a>Traga o seu próprio dispositivo
Traga os seus próprios dispositivos (BYOD) inclui os telemóveis, os tablets e os PCs pessoais. Os utilizadores instalam e executam a aplicação Portal da Empresa para inscrever BYODs. Este programa permite aos utilizadores aceder aos recursos da empresa tais como o e-mail.

## <a name="corporate-owned-device"></a>Dispositivo pertencentes à empresa
Os dispositivos pertencentes à empresa (COD) incluem telemóveis, tablets e PCs pertencentes à organização e distribuídos pela força de trabalho. A inscrição COD suporta cenários de gestão, como inscrição automática, dispositivos partilhados ou requisitos de inscrição previamente autorizados. Uma forma habitual de inscrever CODs passa pela utilização do gestor de inscrição de dispositivos (DEM) por parte do administrador ou do gestor. Os dispositivos iOS podem ser inscritos diretamente através das ferramentas do Programa de Registo de Aparelho (DEP) fornecidas pela Apple. Os dispositivos com um número IMEI também podem ser identificados e marcados como pertencentes à empresa.

### <a name="device-enrollment-manager"></a>Gestor de inscrição de dispositivos
A gestão de inscrição de dispositivos (DEM) é uma conta especial do utilizador que serve para inscrever e gerir múltiplos dispositivos pertencentes à empresa. Os gestores podem instalar o Portal da Empresa e inscrever muitos dispositivos sem utilizador. Saiba mais sobre o [DEM](./device-enrollment-manager-enroll.md).

### <a name="apple-device-enrollment-program"></a>Programa de Inscrição de Dispositivos da Apple
A gestão do Programa de Inscrição de Dispositivos (DEP) da Apple permite-lhe criar e implementar a política “over the air” em dispositivos iOS comprados e geridos com DEP. O dispositivo é inscrito quando os utilizadores ligarem o dispositivo pela primeira vez e executarem o Assistente de Configuração do iOS. Este método suporta o modo supervisionado do iOS, que permite que um dispositivo seja configurado com funcionalidades específicas.

Saiba mais sobre a inscrição do DEP para iOS:

- [Escolher como inscrever dispositivos iOS](ios-enroll.md)
- [Inscrever dispositivos iOS com o Programa de Inscrição de Dispositivos](https://docs.microsoft.com/intune/device-restrictions-ios#device-enrollment-program)

### <a name="usb-sa"></a>USB-SA
Os administradores de TI utilizam o Apple Configurator, através de USB, para preparar manualmente cada dispositivo pertencente à empresa para inscrição com o Assistente de Configuração. O administrador de TI cria um perfil de inscrição e exporta-o para o Apple Configurator. Quando os utilizadores recebem os seus dispositivos, é-lhes pedido que executem o Assistente de Configuração para inscreverem os seus dispositivos. Este método suporta o modo **iOS supervisionado** que, por sua vez, ativa as seguintes funcionalidades:
  - Inscrição bloqueada
  - Modo de Local Público e outras restrições e configurações avançadas

Saiba mais sobre a inscrição do iOS Apple Configurator com o Assistente de Configuração:

- [Decidir como inscrever dispositivos iOS](enrollment-method-choose-ios.md)
- [Inscrever dispositivos iOS com o Configurator e o Assistente de Configuração](apple-configurator-setup-assistant-enroll-ios.md)

### <a name="usb-direct"></a>USB-Direct
Para a inscrição direta, o administrador tem de inscrever cada dispositivo manualmente através da criação de uma política de inscrição e exportá-lo para o Apple Configurator. Os dispositivos ligados por USB pertencentes à empresa são inscritos diretamente e não necessitam de uma reposição de fábrica. Os dispositivos são geridos como dispositivos sem utilizador. Estes não estão bloqueados nem são supervisionados e não suportam acesso condicional, deteção de jailbreak ou gestão de aplicações móveis.

Para obter mais informações sobre a inscrição do iOS, veja:

- [Decidir como inscrever dispositivos iOS](enrollment-method-choose-ios.md)
- [Inscrever dispositivos iOS com o Configurator e a inscrição direta](apple-configurator-direct-enroll-ios.md)

## <a name="mobile-device-management-with-exchange-activesync-and-intune"></a>Gestão de dispositivos móveis com o Exchange ActiveSync e o Intune
Os dispositivos móveis que não estão inscritos, mas que se ligam ao Exchange ActiveSync (EAS), podem ser geridos pelo Intune utilizando a política de MDM do EAS. O Intune utiliza um Exchange Connector para comunicar com o EAS, no local ou alojado na cloud. Mais informações disponíveis em breve.

## <a name="mobile-device-cleanup-after-mdm-certificate-expiration"></a>Limpeza de dispositivos móveis após a expiração do certificado MDM

O certificado MDM é renovado automaticamente quando os dispositivos móveis estão a comunicar com o serviço do Intune. Se os dispositivos móveis forem eliminados ou não conseguirem comunicar com o serviço do Intune durante um determinado período de tempo, o certificado MDM não será renovado. O dispositivo é removido do portal do Azure 180 dias depois da expiração do certificado MDM.
