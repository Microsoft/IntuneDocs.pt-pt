---
title: Inscrever dispositivos | Microsoft Intune
description: "A gestão de dispositivos móveis (MDM) utiliza a inscrição para trazer dispositivos para gestão e permitir o acesso aos recursos."
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 09/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8fc415f7-0053-4aa5-8d2b-03202eca4b87
ms.reviewer: damionw
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 3f28cce75626df1115283dc98547adcb97ee1cb4
ms.openlocfilehash: d880123a9b4d4afd74e9941ce0590f5dae554667


---

# <a name="enroll-devices-for-management-in-intune"></a>Inscrever dispositivos para gestão no Intune
Pode inscrever dispositivos, incluindo PCs Windows, para ativar a gestão de dispositivos móveis (MDM) com o Microsoft Intune. Este tópico descreve formas diferentes de inscrever dispositivos móveis na gestão do Intune. A forma como inscreve dispositivos depende do tipo de dispositivo, da propriedade e do nível de gestão necessário. A inscrição "Bring your own device" (BYOD) permite que os utilizadores inscrevam os seus telemóveis, tablets ou PCs pessoais. A inscrição Dispositivos pertencentes à empresa (COD) permite cenários de gestão como eliminação remota, dispositivos partilhados ou afinidade de utilizador para um dispositivo.

Se utilizar o [Exchange ActiveSync](#mobile-device-management-with-exchange-activesync-and-intune), no local ou alojado na cloud, pode ativar a gestão simples do Intune sem inscrição. Os PCs Windows também podem ser geridos com o [software de cliente do Intune](#manage-windows-pcs-with-intune).

## <a name="overview-of-device-enrollment-methods"></a>Descrição geral dos métodos de inscrição para dispositivos

A seguinte tabela mostra métodos de inscrição do Intune, bem como as funcionalidades suportadas e os requisitos de cada método. As funcionalidades e os requisitos encontram-se descritos abaixo.

- **Apagar** – indica se o dispositivo tem de ser apagado antes de os utilizadores poderem inscrever o dispositivo. O termo "apagar" significa uma reposição de fábrica do dispositivo, a qual remove todos os dados. Para obter mais informações, consulte [Extinguir dispositivos](retire-devices-from-microsoft-intune-management.md).
- **Afinidade** – associa dispositivos a utilizadores. Necessário para gestão de aplicações móveis (MAM) e acesso condicional a dados da empresa. Para obter mais informações, consulte [Afinidade do utilizador](enroll-corporate-owned-ios-devices-in-microsoft-intune.md#using-company-portal-on-dep-or-apple-configurator-enrolled-devices).
- **Bloquear** – impede os utilizadores de remover o dispositivo da gestão. Os dispositivos iOS necessitam do modo supervisionado para Bloquear. Para obter mais informações, consulte [Bloqueio remoto](retire-devices-from-microsoft-intune-management.md#block-access-a-device).

**Métodos de inscrição do iOS**

| **Método** |  **Eliminação necessária?** |    **Afinidade**    |   **Bloqueio** | **Detalhes** |
|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | Não|    Sim |   Não | [Mais informações](prerequisites-for-enrollment.md#set-up-device-management)|
|**[DEM](#dem)**|   Não |Não |Não  | [Mais informações](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)|
|**[DEP](#dep)**|   Sim |   Opcional |  Opcional|[Mais informações](ios-device-enrollment-program-in-microsoft-intune.md)|
|**[USB-SA](#usb-sa)**| Sim |   Opcional |  Não| [Mais informações](ios-setup-assistant-enrollment-in-microsoft-intune.md)|
|**[USB-Direct](#usb-direct)**| Não |    Não  | Não|[Mais informações](ios-direct-enrollment-in-microsoft-intune.md)|

**Métodos de inscrição do Windows**

| **Método** |  **Eliminação necessária?** |    **Afinidade**    |   **Bloqueio** | **Detalhes**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | Sim|   Sim |   Não | [Mais informações](prerequisites-for-enrollment.md#set-up-device-management)|
|**[DEM](#dem)**|   Não |Não |Não  |[Mais informações](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)|

**Métodos de inscrição do Android**

| **Método** |  **Eliminação necessária?** |    **Afinidade**    |   **Bloqueio** | **Detalhes**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | Não|    Sim |   Não | [Mais informações](prerequisites-for-enrollment.md#set-up-device-management)|
|**[DEM](#dem)**|   Não |Não |Não  |[Mais informações](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)|

Para ver uma série de perguntas que o ajudem a encontrar o método correto, consulte [Escolher como inscrever dispositivos](/intune/get-started/choose-how-to-enroll-devices1).

## <a name="byod"></a>BYOD
Os utilizadores da inscrição "Bring your own device" instalam a aplicação Portal da Empresa e inscrevem o respetivo dispositivo. Isto permite que os utilizadores se liguem à rede da empresa e adiram ao domínio ou ao Azure Active Directory. Para a maioria das plataformas, tem de ativar a inscrição BYOD para vários cenários COD. Para obter mais informações, consulte [Pré-requisitos para inscrição de dispositivos](prerequisites-for-enrollment.md). ([Voltar à tabela](#overview-of-device-enrollment-methods))

## <a name="corporate-owned-devices"></a>Dispositivos pertencentes à empresa
Os dispositivos pertencentes à empresa (COD) podem ser geridos com a consola do Intune. Os dispositivos iOS podem ser inscritos diretamente através das ferramentas fornecidas pela Apple. Todos os tipos de dispositivos podem ser inscritos por um administrador ou gestor utilizando o gestor de inscrição de dispositivos. Os dispositivos com um número IMEI também podem ser identificados e marcados como pertencentes à empresa para ativar cenários COD.

Para mais informações, consulte [Inscrever dispositivos pertencentes à empresa](manage-corporate-owned-devices.md).

### <a name="dem"></a>DEM
A gestão de inscrição de dispositivos (DEM) é uma conta especial do Intune utilizada para inscrever e gerir múltiplos dispositivos pertencentes à empresa. Os gestores podem instalar o Portal da Empresa e inscrever muitos dispositivos sem utilizador. Saiba mais sobre o [DEM](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md). ([Voltar à tabela](#overview-of-device-enrollment-methods))

### <a name="dep"></a>DEP
A gestão do Programa de Inscrição de Dispositivos (DEP) da Apple permite-lhe criar e implementar a política "over the air" em dispositivos iOS comprados e geridos com DEP. O dispositivo é inscrito quando os utilizadores ligarem o dispositivo pela primeira vez e executarem o Assistente de Configuração do iOS. Este método suporta o modo **iOS Supervisionado** que, por sua vez, permite:
  - Inscrição bloqueada
  - Acesso condicional
  - Deteção de jailbreak
  - Gestão de aplicações móveis

Saiba mais sobre o [DEP](ios-device-enrollment-program-in-microsoft-intune.md). ([Voltar à tabela](#overview-of-device-enrollment-methods))

### <a name="usb-sa"></a>USB-SA
Estão preparados dispositivos ligados por USB pertencentes à empresa com política do Intune. Para a inscrição através do Assistente de Configuração, o administrador cria esta política do Intune e exporta-a para o Configurador da Apple. O administrador tem de inscrever cada dispositivo manualmente. Os utilizadores recebem os respetivos dispositivos e executam o Assistente de Configuração, inscrevendo os dispositivos. Este método suporta o modo **iOS Supervisionado** que, por sua vez, permite:
  - Acesso condicional
  - Deteção de jailbreak
  - Gestão de aplicações móveis

Saiba mais sobre [inscrição através do Assistente de Configuração com o Configurador da Apple](ios-setup-assistant-enrollment-in-microsoft-intune.md). ([Voltar à tabela](#overview-of-device-enrollment-methods))

### <a name="usb-direct"></a>USB-Direct
Para a inscrição direta, o administrador cria uma política do Intune e exporta-a para o Configurador da Apple. Os dispositivos ligados por USB pertencentes à empresa são inscritos diretamente e não necessitam de uma reposição de fábrica. O administrador tem de inscrever cada dispositivo manualmente. Os dispositivos são geridos como dispositivos sem utilizador. Estes não estão bloqueados nem são supervisionados e não suportam acesso condicional, deteção de jailbreak ou gestão de aplicações móveis. Saiba mais sobre [inscrição direta com o Configurador da Apple](ios-direct-enrollment-in-microsoft-intune.md). ([Voltar à tabela](#overview-of-device-enrollment-methods))

## <a name="mobile-device-management-with-exchange-activesync-and-intune"></a>Gestão de dispositivos móveis com o Exchange ActiveSync e o Intune
Os dispositivos móveis que não estão inscritos, mas que se ligam ao Exchange ActiveSync (EAS), podem ser geridos pelo Intune utilizando a política de MDM do EAS. O Intune utiliza um Exchange Connector para comunicar com o EAS, no local ou alojado na cloud.

Para obter mais informações, consulte [Gestão de dispositivos móveis com o Exchange ActiveSync e o Intune](mobile-device-management-with-exchange-activesync-and-microsoft-intune.md).


## <a name="windows-pc-management-with-intune"></a>Gestão de PCs Windows com o Intune  
Também pode utilizar o Microsoft Intune para gerir PCs Windows com o software de cliente do Intune. Os PCs geridos com o cliente do Intune podem:

 - Reportar inventários de software e hardware
 - Instalar aplicações de ambiente de trabalho (por exemplo, ficheiros .exe e .msi)
 - Gerir as definições da firewall

Não é possível eliminar completamente os PCs geridos com o software de cliente do Intune, embora a eliminação seletiva esteja disponível. Os PCs geridos com o software de cliente do Intune não podem tirar partido de muitas funcionalidades de gestão do Intune, tal como o acesso condicional, as definições de VPN e Wi-Fi ou a implementação de certificados e a configuração de e-mail.

Para mais informações, consulte [Gerir PCs Windows com o Intune](manage-windows-pcs-with-microsoft-intune.md).

## <a name="supported-device-platforms"></a>Plataformas de dispositivos suportadas

O Intune pode gerir as seguintes plataformas de dispositivos:

[!INCLUDE[mdm-supported-devices](../includes/mdm-supported-devices.md)]

## <a name="next-steps"></a>Passos seguintes
- [Pré-requisitos para a inscrição de dispositivos](prerequisites-for-enrollment.md)
- [Gerir dispositivos pertencentes à empresa](manage-corporate-owned-devices.md)
- [Dispositivos móveis e computadores suportados](../get-started/supported-mobile-devices-and-computers.md)



<!--HONumber=Nov16_HO3-->


