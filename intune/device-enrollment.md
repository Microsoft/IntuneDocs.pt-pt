---
title: "O que é a inscrição de dispositivos do Microsoft Intune"
titleSuffix: Intune on Azure
description: "Saiba mais sobre a inscrição de dispositivos iOS, Android e Windows.\""
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 05/29/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6f67fcd2-5682-4f9c-8d74-d4ab69dc978c
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 927e2f21aad4ff39c9351bef68eb510e93410c37
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/01/2017
---
# <a name="what-is-device-enrollment"></a>O que é a inscrição de dispositivos?
[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Este tópico descreve a inscrição e indica as formas diferentes de inscrever dispositivos móveis na gestão do Intune.

Os dispositivos são inscritos no Intune para que os possa gerir. Esta capacidade é mencionada na documentação do Intune como gestão de dispositivos móveis (MDM). Quando os dispositivos são inscritos no Intune, é-lhes emitido um certificado MDM, que utilizam para comunicar com o serviço do Intune.

A forma como inscreve dispositivos depende do tipo de dispositivo, da propriedade e do nível de gestão de que precisa. A inscrição "Bring your own device" (BYOD) permite que os utilizadores inscrevam os seus telemóveis, tablets ou PCs pessoais. A inscrição de dispositivos pertencentes à empresa (COD) permite cenários de gestão, como a inscrição automática, dispositivos partilhados ou requisitos de inscrição previamente autorizados.

Se utilizar o Exchange ActiveSync, no local ou alojado na cloud, pode ativar a gestão simples do Intune sem inscrição (mais informações disponíveis em breve). Pode gerir PCs Windows como dispositivos móveis, que é o método recomendado descrito abaixo.


## <a name="overview-of-device-enrollment-methods"></a>Descrição geral dos métodos de inscrição para dispositivos

A tabela a seguir oferece uma descrição geral dos métodos de inscrição do Intune com as respetivas capacidades e requisitos descritos abaixo.
**Legenda**

- **Reposição obrigatória** – O dispositivo é reposto para fábrica durante a inscrição.
- **Afinidade de Utilizador** – Associa os dispositivos aos utilizadores. Para obter mais informações, veja [Afinidade do utilizador](device-enrollment-program-enroll-ios.md).
- **Bloqueado** – Impede os utilizadores de anular a inscrição de dispositivos.

**Métodos de inscrição do iOS**

| **Método** |  **Reposição obrigatória** |    **Afinidade de Utilizador**   |   **Bloqueado** | **Detalhes** |
|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | Não|    Sim |   Não | [Mais informações](./apple-mdm-push-certificate-get.md)|
|**[DEM](#dem)**|   Não |Não |Não  | [Mais informações](./device-enrollment-program-enroll-ios.md)|
|**[DEP](#dep)**|   Sim |   Opcional |  Opcional|[Mais informações](./device-enrollment-program-enroll-ios.md)|
|**[USB-SA](#usb-sa)**| Sim |   Opcional |  Não| [Mais informações](./apple-configurator-setup-assistant-enroll-ios.md)|
|**[USB-Direct](#usb-direct)**| Não |    Não  | Não|[Mais informações](./apple-configurator-direct-enroll-ios.md)|

**Métodos de inscrição do Windows**

| **Método** |  **Reposição obrigatória** |    **Afinidade de Utilizador**   |   **Bloqueado** | **Detalhes**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | Não |   Sim |   Não | [Mais informações](windows-enroll.md)|
|**[DEM](#dem)**|   Não |Não |Não  |[Mais informações](device-enrollment-manager-enroll.md)|
|**Inscrição automática** | Não |Sim |Não | [Mais informações](./windows-enroll.md#enable-windows-10-automatic-enrollment)|
|**Inscrição em massa** |Não |Não |Não | [Mais informações](./windows-bulk-enroll.md) |

**Métodos de inscrição do Android**

| **Método** |  **Reposição obrigatória** |    **Afinidade de Utilizador**   |   **Bloqueado** | **Detalhes**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | Não|    Sim |   Não | [Mais informações](./android-enroll.md)|
|**[DEM](#dem)**|   Não |Não |Não  |[Mais informações](./device-enrollment-program-enroll-ios.md)|
|**Android for Work**| Não | Sim | Não| [Mais informações](./android-enroll.md#enable-enrollment-of-android-for-work-devices) |


## <a name="byod"></a>BYOD
Os utilizadores da inscrição "Bring your own device" instalam e executam a aplicação Portal da Empresa para inscrever os respetivos dispositivos. Este programa permite aos utilizadores aceder aos recursos da empresa tais como o e-mail.

## <a name="corporate-owned-devices"></a>Dispositivos pertencentes à empresa
A seguir são apresentados cenários de inscrição de dispositivos empresariais (COD). Os dispositivos iOS podem ser inscritos diretamente através das ferramentas fornecidas pela Apple. Todos os tipos de dispositivos podem ser inscritos por um administrador ou gestor utilizando o gestor de inscrição de dispositivos. Os dispositivos com um número IMEI também podem ser identificados e marcados como pertencentes à empresa para ativar cenários COD.

### <a name="dem"></a>DEM
A gestão de inscrição de dispositivos (DEM) é uma conta especial do utilizador que serve para inscrever e gerir múltiplos dispositivos pertencentes à empresa. Os gestores podem instalar o Portal da Empresa e inscrever muitos dispositivos sem utilizador. Saiba mais sobre o [DEM](./device-enrollment-manager-enroll.md).

### <a name="dep"></a>DEP
A gestão do Programa de Inscrição de Dispositivos (DEP) da Apple permite-lhe criar e implementar a política "over the air" em dispositivos iOS comprados e geridos com DEP. O dispositivo é inscrito quando os utilizadores ligarem o dispositivo pela primeira vez e executarem o Assistente de Configuração do iOS. Este método suporta o modo **iOS Supervisionado** que, por sua vez, ativa a seguinte funcionalidade:

  - Inscrição bloqueada
  - Modo de Local Público e outras restrições e configurações avançadas

Saiba mais sobre a inscrição do DEP para iOS:

- [Escolher como inscrever dispositivos iOS](enrollment-method-choose-ios.md)
- [Inscrever dispositivos iOS com o Programa de Inscrição de Dispositivos](device-enrollment-program-enroll-ios.md)

### <a name="usb-sa"></a>USB-SA
Os administradores de TI utilizam o Apple Configurator, através de USB, para preparar manualmente cada dispositivo pertencente à empresa para inscrição com o Assistente de Configuração. O administrador de TI cria um perfil de inscrição e exporta-o para o Apple Configurator. Quando os utilizadores recebem os seus dispositivos, é-lhes pedido que executem o Assistente de Configuração para inscreverem os seus dispositivos. Este método suporta o modo **iOS Supervisionado** que, por sua vez, ativa as seguintes funcionalidades:
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
