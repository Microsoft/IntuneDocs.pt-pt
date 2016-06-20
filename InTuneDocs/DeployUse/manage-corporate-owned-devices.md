---
# required metadata

title: Gerir dispositivos pertencentes à empresa | Microsoft Intune
description:
keywords:
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 2b60bbff-25e6-489b-9621-c71b4275fa06

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Inscrever dispositivos pertencentes à empresa com o Microsoft Intune
Os dispositivos pertencentes à empresa (COD) ou à organização podem ser colocados em gestão pelo Intune de variadas formas consoante o dispositivo, de como foi comprado e das necessidades da organização.

## Dispositivos iOS pertencentes à empresa
Estes métodos de inscrição são ideais para cenários "Choose your own device" (CYOD), em que a organização compra os dispositivos para os utilizadores, mas pretende manter a gestão dos mesmos. Se a sua organização tiver comprado dispositivos iOS, pode pré-configurar a inscrição para que o dispositivo seja gerido desde a primeira vez que o respetivo utilizador o ligar. O Intune suporta a inscrição através do [Programa de Registo de Dispositivos da Apple (DEP)](ios-device-enrollment-program-in-microsoft-intune.md) ou da ferramenta Apple Configurator em execução num computador Mac para inscrição [direta](ios-direct-enrollment-in-microsoft-intune.md) ou com o [Assistente de Configuração](ios-setup-assistant-enrollment-in-microsoft-intune.md).

[Inscrever dispositivos iOS pertencentes à empresa](enroll-corporate-owned-ios-devices-in-microsoft-intune.md)

## Gestor de inscrição de dispositivos
As organizações podem utilizar o Intune para gerir um grande número de dispositivos móveis com uma única conta de utilizador, denominada conta do gestor de inscrição de dispositivos. Após a criação de uma conta de gestor de inscrição de dispositivos, essa conta pode ser utilizada por um gestor para inscrever mais do que os cinco dispositivos padrão permitidos por predefinição para os utilizadores normais. A inscrição de dispositivos com um gestor de inscrição de dispositivos funciona apenas para dispositivos que não sejam utilizados por um utilizador específico. Estes dispositivos são ideais para aplicações de ponto de venda ou utilitários, mas inadequados para utilizadores que necessitem de aceder ao e-mail ou aos recursos da empresa.

[Inscrever dispositivos pertencentes à empresa com o gestor de inscrição de dispositivos](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)

## Identidade internacional do equipamento móvel (IMEI)
Os números de identidade internacional do equipamento móvel (IMEI) exclusivos são uma propriedade de dispositivo comum para inúmeros fabricantes de dispositivos móveis. Os administradores do Intune podem importar os números IMEI para os dispositivos pertencentes à empresa. Quando o dispositivo ficar gerido pelo Intune, pode ser marcado como um dispositivo pertencente à empresa e visado pela política adequada.

[Especifique os dispositivos da empresa com os números de identidade internacional do equipamento móvel (IMEI)](specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers)

## Descrição geral dos métodos de inscrição para dispositivos pertencentes à empresa

A tabela seguinte mostra os métodos de inscrição para dispositivos pertencentes à empresa, com os seus benefícios.

**Métodos de inscrição do iOS**

| **Método** |  **[Reiniciar](#Reset)** |   **[Afinidade](#Affinity)**   |   **[Bloqueado](#Locked)** |
|:---:|:---:|:---:|:---:|
|**[BYOD](#BYOD)** | Não|    Sim |   Não |
|**[DEM](#DEM)**|   Não |Não |Não  |
|**[DEP](#DEP)**|   Sim |   Optar ativamente por participar |   Optar ativamente por participar|
|**[USB-SA](#USB-SA)**| Sim |   Optar ativamente por participar |   Não|
|**[USB-Direct](#USB-Direct)**| Não |    Não  | Não|

**Métodos de Inscrição de Windows e Android**

| **Método** |  **[Eliminação](#Wipe)** | **[Função do](#User)**   |   **[Bloqueado](#Locked)** |
|:---:|:---:|:---:|:---:|
|**[BYOD](#BYOD)** | Não|    Sim |   Não |
|**[DEM](#DEM)**|   Não |Não |Não  |

**Métodos de inscrição para dispositivos pertencentes à empresa**

### BYOD
“Bring Your Own Device.” Os utilizadores instalam a aplicação do Portal da Empresa e inscrevem o respetivo dispositivo. A inscrição de dispositivos no Portal da Empresa associa o dispositivo a uma área de trabalho. A inscrição de dispositivos iOS no Portal da Empresa requer um ID da Apple. BYOD não requer configuração adicional para dispositivos pertencentes à empresa. Ver os passos para [configurar a gestão de dispositivos](get-ready-to-enroll-devices-in-microsoft-intune#set-up-device-management.md). ([Voltar à tabela](#overview-of corporate-owned-device-enrollment-methods))

### DEM
Gestor de inscrição de dispositivos. O administrador cria contas DEM. Os gestores podem, então, instalar o Portal da Empresa e inscrever vários dispositivos sem utilizador. Saiba mais sobre o [DEM](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md). ([Voltar à tabela](#overview-of corporate-owned-device-enrollment-methods))

### DEP
Programa de registo de dispositivos da Apple. O administrador cria e implementa a política "por ondas eletromagnéticas" para dispositivos iOS adquiridos e geridos com o DEP. O dispositivo é inscrito quando o utilizador executa o Assistente de Configuração iOS. Este método suporta o modo **iOS Supervisionado**, que, por sua vez, permite:
  - Inscrição bloqueada
  - Acesso condicional
  - Deteção de jailbreak
  - Gestão de aplicações móveis

Saiba mais sobre o [DEP](ios-device-enrollment-program-in-microsoft-intune.md). ([Voltar à tabela](#overview-of corporate-owned-device-enrollment-methods))

### USB-SA
Ligado por USB, inscrição através do Assistente de Configuração. O administrador cria uma política do Intune e exporta-a para o Apple Configurator. Os dispositivos ligados por USB estão preparados com políticas do Intune. O administrador tem de inscrever cada dispositivo manualmente. Os utilizadores recebem os respetivos dispositivos e executam o Assistente de Configuração, inscrevendo os dispositivos. Este método suporta o modo **iOS Supervisionado**, que, por sua vez, permite:
  - Inscrição bloqueada
  - Acesso condicional
  - Deteção de jailbreak
  - Gestão de aplicações móveis

Saiba mais sobre a [inscrição através do Assistente de Configuração com o Apple Configurator](ios-setup-assistant-enrollment-in-microsoft-intune.md). ([Voltar à tabela](#overview-of corporate-owned-device-enrollment-methods))

### USB-Direct
Inscrição direta. O administrador cria uma política do Intune e exporta-a para o Apple Configurator. Os dispositivos ligados por USB são inscritos diretamente, sem necessidade de uma reposição de fábrica. O administrador tem de inscrever cada dispositivo manualmente. Os dispositivos são geridos como dispositivos sem utilizador. Não estão bloqueados nem são supervisionado e não suportam acesso condicional, deteção de jailbreak, gestão de aplicações móveis. Saiba mais sobre [inscrição direta com o Apple Configurator](ios-direct-enrollment-in-microsoft-intune.md). ([Voltar à tabela](#overview-of corporate-owned-device-enrollment-methods))

**Comportamento dos dispositivos móveis pertencentes à empresa**

### Reiniciar
Especifica se a inscrição do dispositivo requer que o dispositivo seja reposto para as definições de fábrica, removendo todos os dados e repondo-o para o estado original.
([Voltar à tabela](#overview-of corporate-owned-device-enrollment-methods))

### Afinidade
Especifica se o método de inscrição suporta “Afinidade do utilizador”, que liga um dispositivo a um utilizador específico. Os dispositivos que “Optam ativamente por participar” podem ser inscritos com ou sem afinidade de utilizador. A afinidade de utilizador é necessária para suportar o seguinte:
  - Aplicações de gestão de aplicações móveis (MAM)
  - Acesso condicional a e-mail e dados da empresa
  - Aplicação do Portal da Empresa

([Voltar à tabela](#overview-of corporate-owned-device-enrollment-methods))

### Bloquear
Especifica se o dispositivo pode ser bloqueado para impedir que o utilizador remova a política do Intune, removendo efetivamente o dispositivo da gestão. Em dispositivos iOS, o bloqueio do dispositivo requer que este esteja no modo Supervisionado.
([Voltar à tabela](#overview-of corporate-owned-device-enrollment-methods)) ([Voltar à tabela](#overview-of corporate-owned-device-enrollment-methods))


<!--HONumber=Jun16_HO1-->


