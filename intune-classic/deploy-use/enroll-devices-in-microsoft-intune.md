---
title: Inscrever dispositivos
description: "A gestão de dispositivos móveis (MDM) utiliza a inscrição para trazer dispositivos para gestão e permitir o acesso aos recursos."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 03/10/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8fc415f7-0053-4aa5-8d2b-03202eca4b87
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: df3c42d8b52d1a01ddab82727e707639d5f77c16
ms.openlocfilehash: c7c4390629178256728c55e47f06bffae043a729
ms.contentlocale: pt-pt
ms.lasthandoff: 06/08/2017


---

# <a name="enroll-devices-for-management-in-intune"></a>Inscrever dispositivos para gestão no Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Pode inscrever dispositivos, incluindo PCs Windows, para ativar a gestão de dispositivos móveis (MDM) com o Microsoft Intune. Este tópico descreve formas diferentes de inscrever dispositivos móveis na gestão do Intune. A forma como inscreve dispositivos depende do tipo de dispositivo, da propriedade e do nível de gestão necessário. A inscrição "Bring your own device" (BYOD) permite que os utilizadores inscrevam os seus telemóveis, tablets ou PCs pessoais. A inscrição de dispositivos pertencentes à empresa (COD) permite cenários de gestão, como a inscrição automática, dispositivos partilhados ou requisitos de inscrição previamente autorizados.

Se utilizar o [Exchange ActiveSync](#mobile-device-management-with-exchange-activesync-and-intune), no local ou alojado na cloud, pode ativar a gestão simples do Intune sem inscrição. Os PCs Windows também podem ser geridos com o [software de cliente do Intune](#manage-windows-pcs-with-intune).

Por predefinição, os dispositivos para todas as plataformas têm permissão para serem inscritos no Intune. Para bloquear a inscrição de dispositivos, inicie sessão no [Portal de administração do Microsoft Intune](https://manage.microsoft.com) com as suas credenciais de administrador. Selecione **Admin** > **Gestão de Dispositivos Móveis** > **Regras de Inscrição** e, em seguida, desmarque as caixas de verificação aplicáveis às plataformas que quer bloquear.

## <a name="overview-of-device-enrollment-methods"></a>Descrição geral dos métodos de inscrição para dispositivos

A seguinte tabela mostra métodos de inscrição do Intune, bem como as funcionalidades suportadas e os requisitos de cada método. As funcionalidades e os requisitos encontram-se descritos abaixo.

- **Apagar** – indica se o dispositivo tem de ser apagado antes de os utilizadores poderem inscrever o dispositivo. O termo "apagar" significa uma reposição de fábrica do dispositivo, a qual remove todos os dados. Para obter mais informações, veja [Extinguir dispositivos](retire-devices-from-microsoft-intune-management.md).
- **Afinidade** – associa dispositivos a utilizadores. Necessário para gestão de aplicações móveis (MAM) e acesso condicional a dados da empresa. Para obter mais informações, veja [Afinidade do utilizador](enroll-corporate-owned-ios-devices-in-microsoft-intune.md#use-the-company-portal-on-dep-enrolled-or-apple-configurator-enrolled-devices).
- **Bloquear** – indica se os utilizadores estão impedidos de anular a inscrição dos seus dispositivos através dos menus do sistema operativo nativo. Os utilizadores podem anular a inscrição dos seus dispositivos em todas as plataformas ao utilizar a aplicação Portal da Empresa.

**Métodos de inscrição do iOS**

| **Método** |  **Eliminação necessária?** |    **Afinidade**    |   **Bloqueio** | **Detalhes** |
|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | Não|    Sim |   Não | [Mais informações](prerequisites-for-enrollment.md)|
|**[DEM](#dem)**|   Não |Não |Não  | [Mais informações](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)|
|**[DEP](#dep)**|   Sim |   Opcional |  Opcional|[Mais informações](ios-device-enrollment-program-in-microsoft-intune.md)|
|**[USB-SA](#usb-sa)**| Sim |   Opcional |  Não| [Mais informações](ios-setup-assistant-enrollment-in-microsoft-intune.md)|
|**[USB-Direct](#usb-direct)**| Não |    Não  | Não|[Mais informações](ios-direct-enrollment-in-microsoft-intune.md)|

**Métodos de inscrição do Windows**

| **Método** |  **Eliminação necessária?** |    **Afinidade**    |   **Bloqueio** | **Detalhes**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | Não|    Sim |   Não | [Mais informações](prerequisites-for-enrollment.md)|
|**[DEM](#dem)**|   Não |Não |Não  |[Mais informações](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)|

**Métodos de inscrição do Android**

| **Método** |  **Eliminação necessária?** |    **Afinidade**    |   **Bloqueio** | **Detalhes**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | Não|    Sim |   Não | [Mais informações](prerequisites-for-enrollment.md)|
|**[DEM](#dem)**|   Não |Não |Não  |[Mais informações](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)|

**Métodos de inscrição do Android for Work**

| **Método** |  **Eliminação necessária?** |    **Afinidade**    |   **Bloqueio** | **Detalhes**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | Não|    Sim |   Não | [Mais informações](prerequisites-for-enrollment.md)|
|**[DEM](#dem)**|   Não |Não |Não  |[Mais informações](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)|

**Métodos de inscrição do macOS**

| **Método** |  **Eliminação necessária?** |    **Afinidade**    |   **Bloqueio** | **Detalhes**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | Não|    Sim |   Não | [Mais informações](prerequisites-for-enrollment.md)|


Para ver uma série de perguntas que o ajudem a encontrar o método correto, veja [Escolher como inscrever dispositivos](/intune-classic/get-started/choose-how-to-enroll-devices1).

## <a name="byod"></a>BYOD
Os utilizadores da inscrição "Bring your own device" instalam a aplicação Portal da Empresa e inscrevem o respetivo dispositivo. Isto permite que os utilizadores se liguem à rede da empresa e adiram ao domínio ou ao Azure Active Directory. Para a maioria das plataformas, tem de ativar a inscrição BYOD para vários cenários COD. Para obter mais informações, veja [Pré-requisitos para inscrição de dispositivos](prerequisites-for-enrollment.md). ([Voltar à tabela](#overview-of-device-enrollment-methods))

## <a name="corporate-owned-devices"></a>Dispositivos pertencentes à empresa
Os dispositivos pertencentes à empresa (COD) podem ser geridos com a consola do Intune. Os dispositivos iOS podem ser inscritos diretamente através das ferramentas fornecidas pela Apple. Todos os tipos de dispositivos podem ser inscritos por um administrador ou gestor utilizando o gestor de inscrição de dispositivos. Os dispositivos com um número IMEI também podem ser identificados e marcados como pertencentes à empresa para ativar cenários COD.

Para obter mais informações, veja [Inscrever dispositivos pertencentes à empresa](manage-corporate-owned-devices.md).

### <a name="dem"></a>DEM
O gestor de inscrição de dispositivos (DEM) é uma conta especial do Intune utilizada para inscrever e gerir múltiplos dispositivos pertencentes à empresa. Os gestores podem instalar o Portal da Empresa e inscrever muitos dispositivos sem utilizador. Saiba mais sobre o [DEM](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md). ([Voltar à tabela](#overview-of-device-enrollment-methods))

### <a name="dep"></a>DEP
A gestão do Programa de Inscrição de Dispositivos (DEP) da Apple permite-lhe criar e implementar a política "over the air" em dispositivos iOS comprados e geridos com DEP. O dispositivo é inscrito quando os utilizadores ligarem o dispositivo pela primeira vez e executarem o Assistente de Configuração do iOS. Este método suporta o modo **iOS Supervisionado** que, por sua vez, permite:
  - Inscrição bloqueada
  - Modo de Local Público e outras restrições e configurações avançadas

Saiba mais sobre o [DEP](ios-device-enrollment-program-in-microsoft-intune.md). ([Voltar à tabela](#overview-of-device-enrollment-methods))

### <a name="usb-sa"></a>USB-SA
Os administradores de TI utilizam o Apple Configurator, através de USB, para preparar manualmente cada dispositivo pertencente à empresa para inscrição com o Assistente de Configuração. O administrador de TI cria um perfil de inscrição e exporta-o para o Apple Configurator. Quando os utilizadores recebem os seus dispositivos, é-lhes pedido que executem o Assistente de Configuração para inscreverem os seus dispositivos. Este método suporta o modo **iOS Supervisionado** que, por sua vez, permite:
  - Inscrição bloqueada
  - Modo de Local Público e outras restrições e configurações avançadas

Saiba mais sobre [inscrição através do Assistente de Configuração com o Apple Configurator](ios-setup-assistant-enrollment-in-microsoft-intune.md). ([Voltar à tabela](#overview-of-device-enrollment-methods))

### <a name="usb-direct"></a>USB-Direct
Para a inscrição direta, o administrador tem de inscrever cada dispositivo manualmente através da criação de uma política de inscrição e exportá-lo para o Apple Configurator. Os dispositivos ligados por USB pertencentes à empresa são inscritos diretamente e não necessitam de uma reposição de fábrica. Os dispositivos são geridos como dispositivos sem utilizador. Estes não estão bloqueados nem são supervisionados e não suportam acesso condicional, deteção de jailbreak ou gestão de aplicações móveis.  Saiba mais sobre [inscrição direta com o Apple Configurator](ios-direct-enrollment-in-microsoft-intune.md). ([Voltar à tabela](#overview-of-device-enrollment-methods))

## <a name="mobile-device-management-with-exchange-activesync-and-intune"></a>Gestão de dispositivos móveis com o Exchange ActiveSync e o Intune
Os dispositivos móveis que não estão inscritos, mas que se ligam ao Exchange ActiveSync (EAS), podem ser geridos pelo Intune utilizando a política de MDM do EAS. O Intune utiliza um Exchange Connector para comunicar com o EAS, no local ou alojado na cloud. Para obter mais informações, veja [Gestão de dispositivos móveis com o Exchange ActiveSync e o Intune](mobile-device-management-with-exchange-activesync-and-microsoft-intune.md).


## <a name="windows-pc-management-with-intune"></a>Gestão de PCs Windows com o Intune  
Também pode utilizar o Microsoft Intune para gerir PCs Windows com o software de cliente do Intune. Os PCs geridos com o cliente do Intune podem:

 - Reportar inventários de software e hardware
 - Instalar aplicações de ambiente de trabalho (por exemplo, ficheiros .exe e .msi)
 - Gerir as definições da firewall

Não é possível eliminar completamente os PCs geridos com o software de cliente do Intune, embora a eliminação seletiva esteja disponível. Os PCs geridos com o software de cliente do Intune não podem tirar partido de muitas funcionalidades de gestão do Intune, tal como o acesso condicional, as definições de VPN e Wi-Fi ou a implementação de certificados e a configuração de e-mail. Para obter mais informações, veja [Gerir PCs Windows com o Intune](manage-windows-pcs-with-microsoft-intune.md).

## <a name="supported-device-platforms"></a>Plataformas de dispositivos suportadas

O Intune pode gerir as seguintes plataformas de dispositivos:

[!INCLUDE[mdm-supported-devices](../includes/mdm-supported-devices.md)]

## <a name="next-steps"></a>Passos seguintes
- [Pré-requisitos para a inscrição de dispositivos](prerequisites-for-enrollment.md)
- [Gerir dispositivos pertencentes à empresa](manage-corporate-owned-devices.md)
- [Dispositivos móveis e computadores suportados](/intune/supported-devices-browsers#intune-supported-devices)
