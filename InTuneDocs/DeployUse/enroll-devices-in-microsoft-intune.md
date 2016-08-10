---
title: Inscrever dispositivos | Microsoft Intune
description: "A gestão de dispositivos móveis (MDM) utiliza a inscrição para trazer dispositivos para gestão e permitir o acesso aos recursos."
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/18/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8fc415f7-0053-4aa5-8d2b-03202eca4b87
ms.reviewer: damionw
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: d8e524b267622f91ed0c2ed854f931299f316312
ms.openlocfilehash: 15f4af1f870d619f4fd51e88d1aef91b0b45e66d


---

# Inscrever dispositivos para gestão no Intune
A gestão de dispositivos móveis (MDM) do Microsoft Intune utiliza a inscrição para trazer dispositivos para gestão e permitir o acesso aos recursos. A forma como irá inscrever dispositivos depende do tipo de dispositivo, da propriedade e do nível de gestão necessário. Os cenários de "Bring your own device" (BYOD) e de dispositivos pertencentes à empresa (COD) necessitam de um processo de inscrição. As organizações que utilizem o Exchange ActiveSync, no local ou alojado na nuvem, podem tornar a gestão mais leve sem requisitos de inscrição. Os PCs Windows também podem ser geridos com o software de cliente do Intune.

###  Plataformas de dispositivos suportadas

O Intune pode gerir as seguintes plataformas de dispositivos:

[!INCLUDE[mdm-supported-devices](../includes/mdm-supported-devices.md)]

## Descrição geral dos métodos de inscrição para dispositivos

A tabela seguinte mostra os métodos de inscrição para dispositivos pertencentes à empresa, com os seus benefícios.

**Métodos de Inscrição do iOS**

| **Método** |  **[Eliminação](#Wipe)** | **[Afinidade](#Affinity)**   |   **[Bloqueado](#Lock)** |
|:---:|:---:|:---:|:---:|
|**[BYOD](#BYOD)** | Não|    Sim |   Não |
|**[DEM](#DEM)**|   Não |Não |Não  |
|**[DEP](#DEP)**|   Sim |   Optar ativamente por participar |   Optar ativamente por participar|
|**[USB-SA](#USB-SA)**| Sim |   Optar ativamente por participar |   Não|
|**[USB-Direct](#USB-Direct)**| Não |    Não  | Não|

**Métodos de Inscrição do Windows e Android**

| **Método** |  **[Eliminação](#Wipe)** | **[Afinidade](#Affinity)**   |   **[Bloqueado](#Lock)** |
|:---:|:---:|:---:|:---:|
|**[BYOD](#BYOD)** | Não|    Sim |   Não |
|**[DEM](#DEM)**|   Não |Não |Não  |

**Métodos de inscrição para dispositivos pertencentes à empresa**

### BYOD
“Bring Your Own Device.” Os utilizadores instalam a aplicação do Portal da Empresa e inscrevem o respetivo dispositivo. A inscrição de dispositivos no Portal da Empresa associa o dispositivo a uma área de trabalho. A inscrição de dispositivos iOS no Portal da Empresa requer um ID Apple. BYOD não requer configuração adicional para dispositivos pertencentes à empresa. Ver os passos para [configurar a gestão de dispositivos](get-ready-to-enroll-devices-in-microsoft-intune.md#set-up-device-management). ([Voltar à tabela](#overview-of-device-enrollment-methods))

### DEM
Gestor de inscrição de dispositivos. O administrador cria contas DEM para gerir os dispositivos da empresa. Os gestores podem, então, instalar o Portal da Empresa e inscrever vários dispositivos sem utilizador. Saiba mais sobre o [DEM](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md). ([Voltar à tabela](#overview-of-device-enrollment-methods))

### DEP
Programa de registo de dispositivos da Apple. O administrador cria e implementa a política "por ondas eletromagnéticas" para dispositivos iOS adquiridos e geridos com o DEP. O dispositivo é inscrito quando o utilizador executa o Assistente de Configuração iOS. Este método suporta o modo **iOS Supervisionado**, que, por sua vez, permite:
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
Inscrição direta. O administrador cria uma política do Intune e exporta-a para o Apple Configurator. Os dispositivos ligados por USB pertencentes à empresa são inscritos diretamente, sem necessidade de uma reposição de fábrica. O administrador tem de inscrever cada dispositivo manualmente. Os dispositivos são geridos como dispositivos sem utilizador. Estes não estão bloqueados nem são supervisionados, e não suportam acesso condicional, deteção de jailbreak nem gestão de aplicações móveis. Saiba mais sobre [inscrição direta com o Apple Configurator](ios-direct-enrollment-in-microsoft-intune.md). ([Voltar à tabela](#overview-of-device-enrollment-methods))

**Comportamento dos dispositivos móveis pertencentes à empresa**

### Eliminação
Especifica se a inscrição do dispositivo requer a reposição de fábrica do dispositivo, removendo todos os dados do dispositivo e repondo-o para o estado original.
[Extinguir dispositivos](retire-devices-from-microsoft-intune-management.md) ([Voltar à tabela](#overview-of-device-enrollment-methods))

### Afinidade
Especifica se o método de inscrição suporta “Afinidade de utilizador”, que liga um dispositivo a um utilizador específico. Os dispositivos que “Optam ativamente por participar” podem ser inscritos com ou sem afinidade de utilizador. A afinidade de utilizador é necessária para suportar o seguinte:
  - Aplicações de gestão de aplicações móveis (MAM)
  - Acesso condicional a e-mail e dados da empresa
  - Aplicação do Portal da Empresa

[Afinidade de Utilizador](enroll-corporate-owned-ios-devices-in-microsoft-intune.md#using-company-portal-on-dep-or-apple-configurator-enrolled-devices) ([Voltar à tabela](#overview-of-device-enrollment-methods))

### Bloquear
Especifica se o dispositivo pode ser bloqueado para impedir que o utilizador remova a política do Intune, removendo efetivamente o dispositivo da gestão. Em dispositivos iOS, o bloqueio do dispositivo requer que este esteja no modo Supervisionado.
([Voltar à tabela](#overview-of-device-enrollment-methods))

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



<!--HONumber=Aug16_HO1-->


