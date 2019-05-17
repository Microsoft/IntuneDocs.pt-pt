---
title: O que é a inscrição de dispositivos do Microsoft Intune
titleSuffix: Microsoft Intune
description: Saiba mais sobre a inscrição de dispositivos iOS, Android e Windows.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 4/24/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 6f67fcd2-5682-4f9c-8d74-d4ab69dc978c
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 68f5fad9d05787b6e79792d594480547ce10cf81
ms.sourcegitcommit: b0cf661145ccc6e3518db620af199786a623a0d9
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/28/2019
ms.locfileid: "64764907"
---
# <a name="what-is-device-enrollment"></a>O que é a inscrição de dispositivos?
[!INCLUDE [azure_portal](./includes/azure_portal.md)]

O Intune permite-lhe gerir os dispositivos e as aplicações da sua força de trabalho e a forma como acedem aos dados da empresa. Para utilizar esta gestão de dispositivos móveis (MDM), deve primeiro inscrever os dispositivos no serviço Intune. Quando um dispositivo é inscrito, é emitido um certificado MDM. Este certificado é utilizado para comunicar com o serviço Intune.

Como pode constatar nas tabelas seguintes, existem vários métodos para inscrever os dispositivos da força de trabalho. Cada método depende da propriedade do dispositivo (pessoal ou empresarial), do tipo de dispositivo (iOS, Windows, Android) e dos requisitos de gestão (reposições, afinidade, bloqueio).

Por predefinição, os dispositivos para todas as plataformas têm permissão para serem inscritos no Intune. No entanto, pode [restringir os dispositivos por plataforma](enrollment-restrictions-set.md#set-device-type-restrictions).

## <a name="ios-enrollment-methods"></a>Métodos de inscrição do iOS

| **Método** |  **Reposição obrigatória** |    [**Afinidade do Utilizador**](device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile) |   **Bloqueado** | **Detalhes** |
|:---:|:---:|:---:|:---:|:---:|
| | Os dispositivos são apagados durante a inscrição. |  Associa cada dispositivo a um utilizador.| Os utilizadores não conseguem anular a inscrição dos dispositivos.  | |
|**[BYOD](#bring-your-own-device)** | Não|   Sim |   Não | [Mais informações](./apple-mdm-push-certificate-get.md)|
|**[DEM](#device-enrollment-manager)**| Não |Não |Não  | [Mais informações](./device-enrollment-program-enroll-ios.md)|
|**[DEP](#apple-device-enrollment-program)**|   Sim |   Opcional |  Opcional|[Mais informações](./device-enrollment-program-enroll-ios.md)|
|**[USB-SA](#usb-sa)**| Sim |   Opcional |  Não| [Mais informações](./apple-configurator-setup-assistant-enroll-ios.md)|
|**[USB-Direct](#usb-direct)**| Não |    Não  | Não|[Mais informações](./apple-configurator-direct-enroll-ios.md)|

## <a name="macos-enrollment-methods"></a>Métodos de inscrição do macOS
| **Método** |  **Reposição obrigatória** |  **Afinidade de Utilizador** | **Bloqueado** | **Detalhes**|
|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#bring-your-own-device)** | Não| Sim | Não | [Mais informações](./macos-enroll.md)|
|**[DEM](#device-enrollment-manager)**| Não |Não |Não  | [Mais informações](./device-enrollment-manager-enroll.md)|
|**[DEP](#apple-device-enrollment-program)**|   Sim |   Opcional |  Opcional|[Mais informações](./device-enrollment-program-enroll-macos.md)|


## <a name="windows-enrollment-methods"></a>Métodos de inscrição do Windows

| **Método** |  **Reposição obrigatória** |    **Afinidade de Utilizador**   |   **Bloqueado** | **Detalhes**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#bring-your-own-device)** | Não |  Sim |   Não | [Mais informações](windows-enroll.md)|
|**[DEM](#device-enrollment-manager)**| Não |Não |Não  |[Mais informações](device-enrollment-manager-enroll.md)|
|**Inscrição automática** | Não |Sim |Não | [Mais informações](./windows-enroll.md#enable-windows-10-automatic-enrollment)|
|**Autopilot** |Sim |Sim |Não | [Mais informações](enrollment-autopilot.md)
|**Inscrição em massa** |Não |Não |Não | [Mais informações](./windows-bulk-enroll.md) |
|**Cogestão** |Não |Sim |Não | [Mais informações](https://docs.microsoft.com/sccm/core/clients/manage/co-management-overview)
|**GPO** |Não |Sim |Não | [Mais informações](https://docs.microsoft.com/windows/client-management/mdm/enroll-a-windows-10-device-automatically-using-group-policy)


## <a name="android-enrollment-methods"></a>Métodos de inscrição do Android

| **Pessoal** | **Métodos de inscrição** | **Reposição obrigatória** | **Afinidade de Utilizador** | **Bloqueado** | **Detalhes**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**Administrador de dispositivo Android**|**Utilizador iniciado no Portal da empresa** | Não | Sim | Não | [Mais informações](https://docs.microsoft.com/intune-user-help/enroll-device-android-company-portal)|
|**Perfil de trabalho do Android Enterprise**|**Utilizador iniciado no Portal da empresa**| Não | Sim | Não | [Mais informações](./android-work-profile-enroll.md)|


| **Empresarial** | **Métodos de inscrição** | **Reposição obrigatória** | **Afinidade de Utilizador** | **Bloqueado** | **Detalhes**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**Administrador de dispositivo Android**|**[DEM](#device-enrollment-manager) iniciada através do Portal da empresa**| Não | Não | Não |[Mais informações](./device-enrollment-manager-enroll.md)|
|**Administrador de dispositivo Android**|**(Pré-declarado IMEI ou SN) Utilizador iniciado no Portal da empresa**| Não | Sim | Não | [Mais informações](./corporate-identifiers-add.md)|
|**Administrador de dispositivo Android com as riscas das extensões de mobilidade**|**Utilizador ou [DEM](#device-enrollment-manager) iniciada através do Portal da empresa**| Não | Sim se iniciada pelo utilizador, não se [DEM](#device-enrollment-manager) iniciada | Não | [Mais informações](./android-zebra-mx-overview.md)|
|**Android Enterprise dedicado**|**NFC, Token, o código QR, Zero Touch**| Sim | Não | Configurável por meio da diretiva | [Mais informações](./android-kiosk-enroll.md)|
|**Android empresarial totalmente gerida (pré-visualização)**|**NFC, Token, o código QR, Zero Touch**| Sim | Sim | Configurável por meio da diretiva | [Mais informações](./android-dedicated-devices-fully-managed-enroll.md)|


## <a name="bring-your-own-device"></a>Traga o seu próprio dispositivo
Traga os seus próprios dispositivos (BYOD) inclui os telemóveis, os tablets e os PCs pessoais. Os utilizadores instalam e executam a aplicação Portal da Empresa para inscrever BYODs. Este programa permite aos utilizadores aceder aos recursos da empresa tais como o e-mail.

## <a name="corporate-owned-device"></a>Dispositivo pertencentes à empresa
Os [dispositivos pertencentes à empresa (COD)](corporate-identifiers-add.md) incluem telemóveis, tablets e PCs pertencentes à organização e distribuídos pela força de trabalho. A inscrição COD suporta cenários de gestão, como inscrição automática, dispositivos partilhados ou requisitos de inscrição previamente autorizados. Uma forma habitual de inscrever CODs passa pela utilização do gestor de inscrição de dispositivos (DEM) por parte do administrador ou do gestor. Os dispositivos iOS podem ser inscritos diretamente através das ferramentas do Programa de Registo de Aparelho (DEP) fornecidas pela Apple. Os dispositivos com um número IMEI também podem ser identificados e marcados como pertencentes à organização.

### <a name="device-enrollment-manager"></a>Gestor de inscrição de dispositivos
A gestão de inscrição de dispositivos (DEM) é uma conta especial do utilizador que serve para inscrever e gerir múltiplos dispositivos pertencentes à empresa. Os gestores podem instalar o Portal da Empresa e inscrever muitos dispositivos sem utilizador. Estes tipos de dispositivo são ideais, por exemplo, para aplicações de utilitários ou ponto de venda, mas não para utilizadores que necessitem de aceder a recursos de e-mail ou da empresa. Saiba mais sobre o [DEM](./device-enrollment-manager-enroll.md). 

### <a name="apple-device-enrollment-program"></a>Programa de Inscrição de Dispositivos da Apple
A gestão do Programa de Registo de Aparelho (DEP) da Apple permite-lhe criar e implementar a política “através do ar” em dispositivos iOS e macOS comprados e geridos com DEP. O dispositivo é inscrito quando os utilizadores ligarem o dispositivo pela primeira vez e executarem o Assistente de Configuração. Este método suporta o modo supervisionado do iOS, que permite que um dispositivo seja configurado com funcionalidades específicas.

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
Para a inscrição direta, o administrador tem de inscrever cada dispositivo manualmente através da criação de uma política de inscrição e exportá-lo para o Apple Configurator. Os dispositivos ligados por USB pertencentes à empresa são inscritos diretamente e não necessitam de ser apagados. Os dispositivos são geridos como dispositivos sem utilizador. Estes não estão bloqueados nem são supervisionados e não suportam acesso condicional, deteção de jailbreak ou gestão de aplicações móveis.

Para obter mais informações sobre a inscrição do iOS, veja:

- [Decidir como inscrever dispositivos iOS](enrollment-method-choose-ios.md)
- [Inscrever dispositivos iOS com o Configurator e a inscrição direta](apple-configurator-direct-enroll-ios.md)

## <a name="mobile-device-cleanup-after-mdm-certificate-expiration"></a>Limpeza de dispositivos móveis após a expiração do certificado MDM

O certificado MDM é renovado automaticamente quando os dispositivos móveis estão a comunicar com o serviço do Intune. Se os dispositivos móveis forem eliminados ou não conseguirem comunicar com o serviço do Intune durante um determinado período de tempo, o certificado MDM não será renovado. O dispositivo é removido do portal do Azure 180 dias depois da expiração do certificado MDM.
