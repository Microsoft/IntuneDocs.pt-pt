---
# required metadata

title: Gestão de dispositivos móveis com o Exchange ActiveSync e o Microsoft Intune | Microsoft Intune
description:
keywords:
author: nathbarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 14f5cf53-6764-4e22-a18b-fa750b3acd41

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Gestão de dispositivos móveis com o Exchange ActiveSync e o Microsoft Intune
Para o Microsoft Intune gerir diretamente os dispositivos móveis, os utilizadores terão de inscrever os mesmos no Intune. Para os dispositivos móveis não inscritos, pode ativar a gestão do Exchange ActiveSync (EAS) através do conector do Exchange. Os dispositivos podem ser geridos em servidores do Exchange no local e no Exchange alojado na nuvem no Microsoft Office 365.

## Regras de acesso ao Exchange para dispositivos móveis ##

O Exchange necessita de um conjunto de regras que defina o que acontece quando os dispositivos móveis tentam ligar ao EAS. Estas regras são geridas na consola de administração do Intune.

[Regras de acesso ao Exchange para dispositivos móveis](exchange-access-rules-for-mobile-devices.md)

## Instalar o conector do Exchange
O conector do Exchange permite gerir a sua implementação do Exchange na consola do Intune. Primeiro, tem de instalar e configurar o conector do Intune-para-Exchange adequado. Escolha a opção adequada consoante o seu servidor do Exchange esteja no local ou alojado como um serviço na nuvem:

-   [Instalar o conector do Intune para o Exchange no local](intune-on-premises-exchange-connector.md)
-   [Configurar o conector de serviços do Intune para o Exchange alojado](intune-service-to-service-exchange-connector.md)

## Aplicar política de dispositivos móveis geridos pelo Exchange
As definições de política podem ser aplicadas através da consola do Intune, consulte [Gerir definições e funcionalidades nos seus dispositivos com as políticas do Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md). Para uma lista das definições de política e funcionalidades do Exchange ActiveSync suportadas por dispositivos móveis específicos, consulte a [Tabela de Comparação do Cliente do Exchange ActiveSync](http://go.microsoft.com/fwlink/?LinkId=247270)

> Depois de ligar o Intune a um ambiente do Microsoft Exchange, a política EAS de todos os utilizadores geridos através do Intune será reposta para a política predefinida atual no servidor do Microsoft Exchange, a não ser que exista uma política mais específica definida no Intune.

## Apagar dados da empresa de dispositivos móveis
Por fim, pode [apagar dados da empresa dos dispositivos móveis geridos pelo EAS](wipe-for-exchange-managed-mobile-devices.md) quando já não estão em utilização ou em caso de perda ou roubo dos dispositivos.


<!--HONumber=May16_HO2-->


