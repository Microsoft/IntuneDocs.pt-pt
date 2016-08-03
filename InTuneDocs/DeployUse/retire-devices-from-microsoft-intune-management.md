---
title: Extinguir dispositivos | Microsoft Intune
description: "O Intune suporta uma eliminação seletiva e uma eliminação completa para remover o dispositivo da gestão do Intune, removendo as respetivas políticas e o portal da empresa."
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/25/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3dbec400-5d8a-47be-b892-7745811d9de2
ms.reviewer: chrisgre
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: e9cbf5858cc4e860b540f421b6d463b8e7a429cf
ms.openlocfilehash: 42b723f99c34f03060140e5f280b87287d108ae1


---

# Extinguir dispositivos da gestão do Intune

Independentemente de os dispositivos serem da empresa ou pessoais, chega uma altura em que os dispositivos geridos têm de ser extintos da gestão no Intune. A extinção de dispositivos é relativamente simples. Pode efetuar uma eliminação seletiva ou uma eliminação completa.
## Eliminar dados e aplicações dos dispositivos
Tanto a eliminação seletiva como a eliminação completa extinguem o dispositivo da gestão do Intune ao remover a política e o portal da empresa, o que significa que o dispositivo deixa de ter as credenciais necessárias para iniciar sessão nos recursos da empresa, como o Microsoft SharePoint, o e-mail ou o Office 365.

A [limpeza seletiva](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md#selective-wipe) é a ação preferencial para os empregados que inscreveram os dispositivos pessoais no Intune, porque não afeta as informações pessoais do dispositivo. Só são removidos os dados empresariais.

Para os dispositivos pertencentes à empresa, também pode utilizar uma [eliminação completa](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md#full-wipe), que repõe as definições de fábrica do dispositivo.

## Revogar o acesso à rede da empresa
Caso esteja a extinguir um dispositivo porque o empregado que o utilizava saiu da empresa e não devolveu o hardware pertencente à empresa, também pode [bloquear remotamente](use-remote-lock-and-passcode-reset-in-microsoft-intune.md) o dispositivo. Este procedimento impede que as informações e o hardware da empresa sejam utilizados indevidamente, embora poderá ter de identificar o dispositivo como perdido.

Também deve revogar a licença da conta de utilizador do Intune do empregado. Esta ação liberta a licença e pode atribuí-la a uma nova conta de utilizador.

## Extinguir hardware
Por vezes, é o próprio dispositivo que atinge o respetivo fim de vida. Nestes casos, [repor as definições de fábrica](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md) com uma limpeza completa remove todos os dados e retira o dispositivo do Intune. Em seguida, pode eliminar o hardware de acordo com a política da sua empresa.

### Consulte também
[Ajudar a proteger os dados com a eliminação completa ou seletiva](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md)



<!--HONumber=Jul16_HO4-->


