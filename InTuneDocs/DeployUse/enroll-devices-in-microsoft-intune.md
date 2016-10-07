---
title: Inscrever dispositivos | Microsoft Intune
description: "A gestão de dispositivos móveis (MDM) utiliza a inscrição para trazer dispositivos para gestão e permitir o acesso aos recursos."
keywords: 
author: NathBarn
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
ms.sourcegitcommit: c880bd9dfb998355a18e78af898a96d4cee393f7
ms.openlocfilehash: 145d373edd65d7ba01c696c3b851692a13831dad


---

# Inscrever dispositivos para gestão no Intune
Pode inscrever dispositivos, incluindo PCs Windows, para ativar a gestão de dispositivos móveis (MDM) com o Microsoft Intune. Este tópico descreve formas diferentes de inscrever dispositivos móveis na gestão do Intune. A forma como os dispositivos inscrevem outros dispositivos depende do tipo de dispositivo, da propriedade e do nível de gestão necessário. A inscrição "Bring your own device" (BYOD) permite que os utilizadores inscrevam os seus telemóveis, tablets ou PCs pessoais. A inscrição Dispositivos pertencentes à empresa (COD) permite cenários de gestão como eliminação remota, dispositivos partilhados ou afinidade de utilizador para um dispositivo.

Se utilizar o [Exchange ActiveSync](#mobile-device-management-with-exchange-activesync-and-intune), no local ou alojado na nuvem, pode ativar a gestão simples do Intune sem inscrição. Os PCs Windows também podem ser geridos com o [software de cliente do Intune](#manage-windows-pcs-with-intune).

## Descrição geral dos métodos de inscrição para dispositivos

A seguinte tabela mostra os métodos de inscrição do Intune com as respetivas funcionalidades suportadas. Estas funcionalidades incluem:
- **Eliminação** – reposição de fábrica do dispositivo, removendo todos os dados. [Extinguir dispositivos](retire-devices-from-microsoft-intune-management.md)
- **Afinidade** – associa dispositivos a utilizadores. Necessário para gestão de aplicações móveis (MAM) e acesso condicional a dados da empresa. [Afinidade de Utilizador](enroll-corporate-owned-ios-devices-in-microsoft-intune.md#using-company-portal-on-dep-or-apple-configurator-enrolled-devices)
- **Bloquear** – impede os utilizadores de remover o dispositivo da gestão. Os dispositivos iOS necessitam do modo supervisionado para Bloquear. [Bloqueio remoto](retire-devices-from-microsoft-intune-management.md#block-access-a-device)

**Métodos de inscrição do iOS**

| **Método** |  **Eliminação** |  **Afinidade**    |   **Bloquear** | **Detalhes** |
|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | Não|    Sim |   Não | [mais](prerequisites-for-enrollment.md#set-up-device-management)|
|**[DEM](#dem)**|   Não |Não |Não  | [mais](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)|
|**[DEP](#dep)**|   Sim |   Opcional |  Opcional|[mais](ios-device-enrollment-program-in-microsoft-intune.md)|
|**[USB-SA](#usb-sa)**| Sim |   Opcional |  Não| [mais](ios-setup-assistant-enrollment-in-microsoft-intune.md)|
|**[USB-Direct](#usb-direct)**| Não |    Não  | Não|[mais](ios-direct-enrollment-in-microsoft-intune.md)|

**Métodos de inscrição do Windows**

| **Método** |  **Eliminação** |  **Afinidade**    |   **Bloquear** | **Detalhes**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | Sim|   Sim |   Não | [mais](prerequisites-for-enrollment.md#set-up-device-management)|
|**[DEM](#dem)**|   Não |Não |Não  |[mais](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)|

**Métodos de inscrição do Android**

| **Método** |  **Eliminação** |  **Afinidade**    |   **Bloquear** | **Detalhes**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | Não|    Sim |   Não | [mais](prerequisites-for-enrollment.md#set-up-device-management)|
|**[DEM](#dem)**|   Não |Não |Não  |[mais](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)|

Para obter uma série de perguntas que o ajudam a encontrar o método correto, consulte [Escolher como inscrever dispositivos](/intune/get-started/choose-how-to-enroll-devices1).

## BYOD
Os utilizadores da inscrição "Bring your own device" instalam a aplicação Portal da Empresa e inscrevem o respetivo dispositivo. Isto permite que os utilizadores se liguem à rede da empresa e adiram ao domínio ou Azure Active Directory. Ativar a inscrição BYOD é um pré-requisito para muitos cenários COD na maioria das plataformas. Consulte [Pré-requisitos para a inscrição de dispositivos](prerequisites-for-enrollment.md). ([Voltar à tabela](#overview-of-device-enrollment-methods))

## Dispositivos pertencentes à empresa
Os dispositivos pertencentes à empresa (COD) podem ser geridos com a consola do Intune. Os dispositivos iOS podem ser inscritos diretamente através das ferramentas fornecidas pela Apple. Todos os tipos de dispositivos podem ser inscritos por um administrador ou gestor utilizando o gestor de inscrição de dispositivos. Os dispositivos com um número IMEI também podem ser identificados e marcados como pertencentes à empresa para ativar cenários COD.

[Inscrever dispositivos pertencentes à empresa](manage-corporate-owned-devices.md)

### DEM
A gestão de inscrição de dispositivos é uma conta especial do Intune utilizada para inscrever e gerir múltiplos dispositivos pertencentes à empresa. Os gestores podem instalar o Portal da Empresa e inscrever muitos dispositivos sem utilizador. Saiba mais sobre o [DEM](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md). ([Voltar à tabela](#overview-of-device-enrollment-methods))

### DEP
A gestão do Programa de Inscrição de Dispositivos (DEP) da Apple permite-lhe criar e implementar a política "over the air" em dispositivos iOS comprados e geridos com DEP. O dispositivo é inscrito quando o utilizador ativa o dispositivo pela primeira vez e executa o Assistente de Configuração do iOS. Este método suporta o modo **iOS Supervisionado**, que, por sua vez, permite:
  - Inscrição bloqueada
  - Acesso condicional
  - Deteção de jailbreak
  - Gestão de aplicações móveis

Saiba mais sobre o [DEP](ios-device-enrollment-program-in-microsoft-intune.md). ([Voltar à tabela](#overview-of-device-enrollment-methods))

### USB-SA
Ligado por USB, inscrição através do Assistente de Configuração. O administrador cria uma política do Intune e exporta-a para o Apple Configurator. Estão preparados dispositivos ligados por USB pertencentes à empresa com política do Intune. O administrador tem de inscrever cada dispositivo manualmente. Os utilizadores recebem os respetivos dispositivos e executam o Assistente de Configuração, inscrevendo os dispositivos. Este método suporta o modo **iOS Supervisionado**, que, por sua vez, permite:
  - Acesso condicional
  - Deteção de jailbreak
  - Gestão de aplicações móveis

Saiba mais sobre [inscrição através do Assistente de Configuração com o Apple Configurator](ios-setup-assistant-enrollment-in-microsoft-intune.md). ([Voltar à tabela](#overview-of-device-enrollment-methods))

### USB-Direct
Inscrição direta. O administrador cria uma política do Intune e exporta-a para o Apple Configurator. Os dispositivos ligados por USB pertencentes à empresa são inscritos diretamente, sem necessidade de uma reposição de fábrica. O administrador tem de inscrever cada dispositivo manualmente. Os dispositivos são geridos como dispositivos sem utilizador. Estes não estão bloqueados nem são supervisionados e não suportam acesso condicional, deteção de jailbreak nem gestão de aplicações móveis. Saiba mais sobre [inscrição direta com o Apple Configurator](ios-direct-enrollment-in-microsoft-intune.md). ([Voltar à tabela](#overview-of-device-enrollment-methods))

## Gestão de dispositivos móveis com o Exchange ActiveSync e o Intune
Os dispositivos móveis que não estão inscritos, mas que se ligam ao Exchange ActiveSync (EAS), podem ser geridos pelo Intune utilizando a política de MDM do EAS. O Intune utiliza um Exchange Connector para comunicar com o EAS, no local e alojado na nuvem.

[Gestão de dispositivos móveis com o Exchange ActiveSync e o Intune](mobile-device-management-with-exchange-activesync-and-microsoft-intune.md)


## Gerir Computadores com Windows com o Intune  
Também pode utilizar o Microsoft Intune para gerir PCs Windows com o software de cliente do Intune. Os PCs geridos com o cliente do Intune podem:

 - Reportar inventários de software e hardware
 - Instalar aplicações de ambiente de trabalho (por exemplo, ficheiros .exe e .msi)
 - Definições de firewall

Os PCs geridos com o software de cliente do Intune não podem ser eliminados e não podem tirar partido de muitas funcionalidades de gestão do Intune, tal como o acesso condicional, as definições de VPN e Wi-Fi ou a implementação de certificados e a configuração de e-mail.

[Gerir Computadores com Windows com o Intune](manage-windows-pcs-with-microsoft-intune.md)

##  Plataformas de dispositivos suportadas

O Intune pode gerir as seguintes plataformas de dispositivos:

[!INCLUDE[mdm-supported-devices](../includes/mdm-supported-devices.md)]

## Passos seguintes
- [Pré-requisitos para a inscrição de dispositivos](prerequisites-for-enrollment.md)
- [Gerir dispositivos pertencentes à empresa](manage-corporate-owned-devices.md)
- [Dispositivos móveis e computadores suportados](../get-started/supported-mobile-devices-and-computers.md)



<!--HONumber=Sep16_HO4-->


