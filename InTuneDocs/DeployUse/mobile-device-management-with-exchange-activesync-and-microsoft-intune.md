---
title: "Gestão de Dispositivos com o Exchange ActiveSync | Microsoft Intune"
description: "Gerir dispositivos móveis com a gestão do Exchange ActiveSync (EAS) com o conector do Exchange"
keywords: 
author: nathbarn
manager: angrobe
ms.date: 07/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 14f5cf53-6764-4e22-a18b-fa750b3acd41
ms.reviewer: chrisgre
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: c880bd9dfb998355a18e78af898a96d4cee393f7
ms.openlocfilehash: 9518381dfd967b8cbf8d01bf834d8148d2c2501b


---

# Gestão de dispositivos móveis do Exchange ActiveSync com Microsoft Intune
Para o Microsoft Intune gerir diretamente os dispositivos móveis, os dispositivos devem estar [inscritos no Intune](prerequisites-for-enrollment.md). Como alternativa, os administradores podem ativar uma solução de gestão mais limitada que utiliza a gestão do Exchange ActiveSync (EAS) com um conector do Exchange. Os dispositivos podem ser geridos em servidores do Exchange no local E NO Exchange Online com o Office 365. O Intune apenas suporta uma ligação de conector do Exchange de qualquer tipo por subscrição.

## Regras de acesso ao Exchange para dispositivos móveis ##

O Exchange necessita de um conjunto de regras que defina o que acontece quando os dispositivos móveis tentam ligar ao EAS. Estas regras são geridas na consola de administração do Intune.

[Regras de acesso ao Exchange para dispositivos móveis](exchange-access-rules-for-mobile-devices.md)

## Instalar o conector do Exchange
O conector do Exchange permite gerir a sua implementação do Exchange na consola do Intune. Primeiro, tem de instalar e configurar o conector do Intune-para-Exchange adequado. Escolha a opção adequada consoante o seu servidor do Exchange esteja no local ou alojado como um serviço na nuvem:

-   [Configurar o Intune para o Exchange Online ou novos ambientes Dedicados do Exchange Online](intune-service-to-service-exchange-connector.md)
-   [Instalar o conector do Intune para servidores do Exchange locais e ambientes legados dedicados do Exchange Online](intune-on-premises-exchange-connector.md)


## Aplicar política de dispositivos móveis geridos pelo Exchange
A consola do Intune pode ser utilizada para gerir as [definições de políticas EAS](exchange-activesync-policy-settings-in-microsoft-intune.md) e [restringir o acesso aos recursos da empresa](restrict-access-to-email-and-o365-services-with-microsoft-intune.md). Para obter uma lista das definições de política e funcionalidades do Exchange ActiveSync suportadas por dispositivos móveis específicos, veja a [Tabela de Comparação do Cliente do Exchange ActiveSync](http://go.microsoft.com/fwlink/?LinkId=247270).

> [!NOTE]
> Depois de ligar o Intune a um ambiente do Microsoft Exchange, a política EAS de todos os utilizadores geridos através do Intune será reposta para a política predefinida atual no servidor do Microsoft Exchange, a não ser que exista uma política mais específica definida no Intune.

## Apagar dados da empresa de dispositivos móveis
Por fim, pode [apagar dados da empresa dos dispositivos móveis geridos pelo EAS](wipe-for-exchange-managed-mobile-devices.md) quando já não estão em utilização ou em caso de perda ou roubo dos dispositivos.



<!--HONumber=Sep16_HO4-->


