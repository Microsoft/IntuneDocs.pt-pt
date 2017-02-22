---
title: "O que é a inscrição de dispositivos do Microsoft Intune | Pré-visualização do Azure no Intune | Documentos da Microsoft"
description: "Pré-visualização do Azure no Intune: saiba mais sobre a inscrição de dispositivos iOS, Android e Windows."
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 01/26/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6f67fcd2-5682-4f9c-8d74-d4ab69dc978c
ms.reviewer: 
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 10cf9980468eff912557747c31994747c17a3ab4
ms.openlocfilehash: 01bf32ef874385019ea4b0fb0ce278554459287d


---

# <a name="what-is-device-enrollment"></a>O que é a inscrição de dispositivos?
[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Este tópico descreve a inscrição e indica as formas diferentes de inscrever dispositivos móveis na gestão do Intune.

Os dispositivos, incluindo PCs Windows, são inscritos no Intune para que os possa gerir. Esta capacidade é mencionada na documentação do Intune como gestão de dispositivos móveis (MDM). Quando os dispositivos são inscritos como dispositivos móveis (e não como PCs), é-lhes emitido um certificado MDM, que utilizam para comunicar com o serviço do Intune. 

A forma como inscreve dispositivos depende do tipo de dispositivo, da propriedade e do nível de gestão de que precisa. A inscrição "Bring your own device" (BYOD) permite que os utilizadores inscrevam os seus telemóveis, tablets ou PCs pessoais. A inscrição de dispositivos pertencentes à empresa (COD) permite cenários de gestão, como a inscrição automática, dispositivos partilhados ou requisitos de inscrição previamente autorizados.

Se utilizar o Exchange ActiveSync, no local ou alojado na cloud, pode ativar a gestão simples do Intune sem inscrição (mais informações disponíveis em breve). Pode gerir PCs Windows como dispositivos móveis, que é o método recomendado descrito abaixo. Também pode geri-los como PCs através do [software de cliente do Intune](https://docs.microsoft.com/intune/deploy-use/manage-windows-pcs-with-microsoft-intune).


## <a name="overview-of-device-enrollment-methods"></a>Descrição geral dos métodos de inscrição para dispositivos

A seguinte tabela mostra métodos de inscrição do Intune, bem como as funcionalidades suportadas e os requisitos de cada método. As funcionalidades e os requisitos encontram-se descritos abaixo. Os termos seguintes são utilizados na tabela:

- **Apagar** – indica se o dispositivo tem de ser apagado antes de os utilizadores poderem inscrever o dispositivo. O termo "apagar" significa uma reposição de fábrica do dispositivo, a qual remove todos os dados. Para obter mais informações, veja [Utilizar a eliminação completa ou seletiva em dispositivos](/intune-azure/manage-devices/use-full-or-selective-wipe-on-devices-using-microsoft-intune).
- **Afinidade** – associa dispositivos a utilizadores. Necessário para gestão de aplicações móveis (MAM) e acesso condicional a dados da empresa. Para obter mais informações, veja [Afinidade do utilizador](enroll-ios-devices-using-device-enrollment-program.md).
- **Bloqueio** – indica se os utilizadores estão impedidos de anular a inscrição dos seus dispositivos na gestão. Os utilizadores podem anular a inscrição dos seus dispositivos em todas as plataformas ao utilizar a aplicação Portal da Empresa. Eles não podem utilizar os menus do sistema operativo nativo para anular a inscrição.


**Métodos de inscrição do iOS**

| **Método** |  **Eliminação necessária?** |    **Afinidade**    |   **Bloqueio** | **Detalhes** |
|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | Não|    Sim |   Não | Mais informações disponíveis em breve|
|**[DEM](#dem)**|   Não |Não |Não  | [Mais informações](enroll-ios-devices-using-device-enrollment-program.md)|
|**[DEP](#dep)**|   Sim |   Opcional |  Opcional|[Mais informações](enroll-ios-devices-using-device-enrollment-program.md)|
|**[USB-SA](#usb-sa)**| Sim |   Opcional |  Não| [Mais informações](enroll-ios-devices-with-apple-configurator-and-setup-assistant.md)|
|**[USB-Direct](#usb-direct)**| Não |    Não  | Não|[Mais informações](enroll-ios-devices-with-apple-configurator-and-direct-enrollment.md)|



**Métodos de inscrição do Windows**

| **Método** |  **Eliminação necessária?** |    **Afinidade**    |   **Bloqueio** | **Detalhes**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | Sim|   Sim |   Não | Mais informações disponíveis em breve|
|**[DEM](#dem)**|   Não |Não |Não  |[Mais informações](enroll-devices-using-device-enrollment-manager.md)|

**Métodos de inscrição do Android**

| **Método** |  **Eliminação necessária?** |    **Afinidade**    |   **Bloqueio** | **Detalhes**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | Não|    Sim |   Não | Mais informações disponíveis em breve|
|**[DEM](#dem)**|   Não |Não |Não  |[Mais informações](enroll-ios-devices-using-device-enrollment-program.md)|


## <a name="byod"></a>BYOD
Os utilizadores da inscrição "Bring your own device" instalam a aplicação Portal da Empresa e inscrevem o respetivo dispositivo. Isto permite que os utilizadores se liguem à rede da empresa e adiram ao domínio ou ao Azure Active Directory. Para a maioria das plataformas, tem de ativar a inscrição BYOD para vários cenários COD.

## <a name="corporate-owned-devices"></a>Dispositivos pertencentes à empresa
Os dispositivos pertencentes à empresa (COD) podem ser geridos com o portal do Azure. Os dispositivos iOS podem ser inscritos diretamente através das ferramentas fornecidas pela Apple. Todos os tipos de dispositivos podem ser inscritos por um administrador ou gestor utilizando o gestor de inscrição de dispositivos. Os dispositivos com um número IMEI também podem ser identificados e marcados como pertencentes à empresa para ativar cenários COD.

### <a name="dem"></a>DEM
A gestão de inscrição de dispositivos (DEM) é uma conta especial do utilizador que serve para inscrever e gerir múltiplos dispositivos pertencentes à empresa. Os gestores podem instalar o Portal da Empresa e inscrever muitos dispositivos sem utilizador. Saiba mais sobre o [DEM](enroll-devices-using-device-enrollment-manager.md). ([Voltar à tabela](#overview-of-device-enrollment-methods))

### <a name="dep"></a>DEP
A gestão do Programa de Inscrição de Dispositivos (DEP) da Apple permite-lhe criar e implementar a política "over the air" em dispositivos iOS comprados e geridos com DEP. O dispositivo é inscrito quando os utilizadores ligarem o dispositivo pela primeira vez e executarem o Assistente de Configuração do iOS. Este método suporta o modo **iOS Supervisionado** que, por sua vez, permite:

  - Inscrição bloqueada
  - Modo de Local Público e outras restrições e configurações avançadas

Para obter mais informações sobre a inscrição do iOS, veja:

- [Escolher como inscrever dispositivos iOS](choose-ios-enrollment-method.md)
- [Inscrever dispositivos iOS com o Programa de Inscrição de Dispositivos](enroll-ios-devices-using-device-enrollment-program.md). 
- [Voltar à tabela acima](#overview-of-device-enrollment-methods)

### <a name="usb-sa"></a>USB-SA
Os administradores de TI utilizam o Apple Configurator, através de USB, para preparar manualmente cada dispositivo pertencente à empresa para inscrição com o Assistente de Configuração. O administrador de TI cria um perfil de inscrição e exporta-o para o Apple Configurator. Quando os utilizadores recebem os seus dispositivos, é-lhes pedido que executem o Assistente de Configuração para inscreverem os seus dispositivos. Este método suporta o modo **iOS Supervisionado** que, por sua vez, permite:
  - Inscrição bloqueada
  - Modo de Local Público e outras restrições e configurações avançadas

Para obter mais informações sobre a inscrição do iOS, veja:

- [Decidir como inscrever dispositivos iOS](choose-ios-enrollment-method.md)
- [Inscrever dispositivos iOS com o Configurator e o Assistente de Configuração](enroll-ios-devices-with-apple-configurator-and-setup-assistant.md). 

### <a name="usb-direct"></a>USB-Direct
Para a inscrição direta, o administrador tem de inscrever cada dispositivo manualmente através da criação de uma política de inscrição e exportá-lo para o Apple Configurator. Os dispositivos ligados por USB pertencentes à empresa são inscritos diretamente e não necessitam de uma reposição de fábrica. Os dispositivos são geridos como dispositivos sem utilizador. Estes não estão bloqueados nem são supervisionados e não suportam acesso condicional, deteção de jailbreak ou gestão de aplicações móveis. 

Para obter mais informações sobre a inscrição do iOS, veja:

- [Decidir como inscrever dispositivos iOS](choose-ios-enrollment-method.md)
- [Inscrever dispositivos iOS com o Configurator e a inscrição direta](enroll-ios-devices-with-apple-configurator-and-direct-enrollment.md)

## <a name="mobile-device-management-with-exchange-activesync-and-intune"></a>Gestão de dispositivos móveis com o Exchange ActiveSync e o Intune
Os dispositivos móveis que não estão inscritos, mas que se ligam ao Exchange ActiveSync (EAS), podem ser geridos pelo Intune utilizando a política de MDM do EAS. O Intune utiliza um Exchange Connector para comunicar com o EAS, no local ou alojado na cloud. Mais informações disponíveis em breve.


## <a name="windows-pc-management-with-intune"></a>Gestão de PCs Windows com o Intune  
Também pode utilizar o Microsoft Intune para gerir PCs Windows com o software de cliente do Intune. Os PCs geridos com o cliente do Intune podem:

 - Reportar inventários de software e hardware
 - Instalar aplicações de ambiente de trabalho (por exemplo, ficheiros .exe e .msi)
 - Gerir as definições da firewall

Não é possível eliminar completamente os PCs geridos com o software de cliente do Intune, embora a eliminação seletiva esteja disponível. Os PCs geridos com o software de cliente do Intune não podem tirar partido de muitas funcionalidades de gestão do Intune, tal como o acesso condicional, as definições de VPN e Wi-Fi ou a implementação de certificados e a configuração de e-mail. Mais informações disponíveis em breve.

## <a name="supported-device-platforms-and-browsers"></a>Plataformas de dispositivos e browsers suportados

Veja [Dispositivos e browsers suportados pelo Intune](https://docs.microsoft.com/intune/get-started/supported-mobile-devices-and-computers)

## <a name="mobile-device-cleanup-after-mdm-certificate-expiration"></a>Limpeza de dispositivos móveis após a expiração do certificado MDM

O certificado MDM é renovado automaticamente quando os dispositivos móveis estão a comunicar com o serviço do Intune. Se os dispositivos móveis (não PCs) forem eliminados ou não conseguirem comunicar com o serviço do Intune durante um determinado período de tempo, o certificado MDM não será renovado. O dispositivo é removido do portal do Azure 180 dias depois da expiração do certificado MDM.



<!--HONumber=Feb17_HO1-->


