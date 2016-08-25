---
title: Escolher como gerir dispositivos | Microsoft Intune
description: "Saiba mais sobre as várias formas de inscrever e gerir dispositivos."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 07/25/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 770aad50-fd7a-4cf1-a793-f95fe47fc3f8
ms.reviewer: angrobe
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: c329bd08aaf72ae2acaa03dcb12c911d84b46b4e
ms.openlocfilehash: cfd9df3814d0d306a254a5566155a91ce5d0ca16


---

# Escolher como gerir dispositivos
O Intune permite gerir uma vasta gama de dispositivos ao *inscrevê-los* no serviço. Os utilizadores podem utilizar um *portal da empresa* para efetuar várias operações, como inscrever os respetivos dispositivos, procurar e instalar aplicações, assegurar que o dispositivo está em conformidade com as políticas da empresa e contactar o respetivo suporte de TI.

## Formas de gerir dispositivos móveis
O Intune pode gerir as seguintes plataformas de dispositivos:

[!INCLUDE[mdm-supported-devices](../includes/mdm-supported-devices.md)]

> [!NOTE]
> Se tiver inscrito anteriormente dispositivos com uma versão anterior do iOS que a versão suportada acima, estes permanecerão inscritos. Consulte a documentação para confirmar se a funcionalidade suporta essa versão do iOS.

O Intune pode gerir dispositivos de utilizadores, conhecidos popularmente como "bring your own device" (BYOD). Também pode gerir dispositivos pertencentes à empresa, incluindo cenários em que a empresa fornece uma lista de dispositivos que os utilizadores poderão escolher, conhecido como "choose your own device" (CYOD).

### Inscrever dispositivos para gestão
Para sistemas operativos de dispositivos móveis, incluindo iOS, Android e Windows Phone, tem sempre de inscrever os dispositivos. A forma como inscreve os dispositivos depende das necessidades da sua organização:

|Tipo de inscrição|BYOD|CYOD|Dispositivo partilhado com conta de gestor|Dispositivo partilhado sem uma conta de utilizador|
|-------------------|--------|--------|--------------------------------------|----------------------------------------|
|**Descrição**|Dispositivo pessoal inscrito através do Microsoft Intune|Dispositivo que é propriedade da empresa para um único utilizador|Dispositivo que é propriedade da empresa gerido através de uma conta de gestor partilhada por vários utilizadores|Dispositivo sem utilizadores que é propriedade da empresa utilizado por vários utilizadores.|
|**Utilizador do dispositivo**|Proprietário|Utilizador atribuído|Nenhuma conta de utilizador específica|Nenhum utilizador específico|
|**Quem inscreve?**|Proprietário|Admistrador|Gestor de Dispositivos|Qualquer pessoa|
|**Quem cancela a inscrição?**|Proprietário ou administrador|Plataforma |Administrador ou utilizador|Administrador ou utilizador|
|**Quem pode redefinir?**|Proprietário ou administrador|Admistrador|Admistrador|Admistrador|

Para orientações adicionais, veja [Escolher como inscrever dispositivos móveis](/intune/get-started/choose-how-to-enroll-devices1).

> [!NOTE]
> Consulte [Capacidades de gestão de dispositivos móveis](mobile-device-management-capabilities-in-microsoft-intune.md) para obter uma lista completa das capacidades fornecidas pela inscrição de dispositivos.

## Formas de gerir PCs Windows
O Intune pode gerir o Windows Vista e PCs Windows posteriores utilizando o cliente do computador do Intune. No entanto, para PCs Windows, pode optar entre inscrevê-los ou instalar o software de cliente do PC Intune que disponibiliza algumas capacidades não disponíveis quando inscreve dispositivos. Na maioria dos cenários, irá inscrever o dispositivo Windows com o Intune, o que fornece um conjunto maior de capacidades que o computador cliente.

Considere utilizar o cliente do computador Intune quando pretender:

- Utilizar qualquer uma das capacidades ativadas para o cliente do computador do Microsoft Intune para gerir os seus PCs Windows
- Gerir um PC Windows com um sistema operativo não suportado para inscrição

> [!NOTE]
> Consulte [Capacidades de gestão de PCs Windows](windows-pc-management-capabilities-in-microsoft-intune.md) para obter uma lista completa das capacidades fornecidas pela instalação do cliente do computador do Intune em PCs Windows suportados.

## Gestão do Exchange ActiveSync
Também pode gerir dispositivos através do Exchange ActiveSync. Isto requer a instalação do Conector No Local ou a utilização do Conector de Serviços incorporado para ligar ao seu Exchange Server.

Para saber mais sobre os requisitos de hardware e software para instalar o Conector No Local, veja [Requisitos do Conector No Local](/intune/deploy-use/intune-on-premises-exchange-connector#requirements-for-the-on-premises-connector).

Para saber mais sobre como utilizar o Conetor No Local ou o Conetor de Serviços com o Exchange, veja [Gestão de dispositivos móveis com o Exchange ActiveSync e o Microsoft Intune](/intune/deploy-use/mobile-device-management-with-exchange-activesync-and-microsoft-intune).



## Passos seguintes
Agora já descobriu algumas das capacidades que pode utilizar quando inscrever os seus dispositivos com o [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]. Em seguida, terá de [inscrever os dispositivos](/intune/deploy-use/enroll-devices-in-microsoft-intune). Após ter inscrito os seus dispositivos, pode tirar partido de todas as capacidades que leu neste tópico. <!--lindavr: There's a logical flaw in our "get to know/get started" content. You can take the path in this topic or you can take the path in the What to know before your get started topic. And they don't cover the same ground. -->



<!--HONumber=Aug16_HO3-->


