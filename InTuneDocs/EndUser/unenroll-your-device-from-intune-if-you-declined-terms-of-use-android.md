---
title: "Terminar a inscrição do seu dispositivo do Intune caso tenha recusado os Termos de Utilização | Microsoft Intune"
description: "Descreve como anular a inscrição de dispositivos Android no Intune se tiver recusado os Termos de Utilização e não conseguir iniciar sessão na aplicação do Portal da Empresa"
keywords: 
author: staciebarker
manager: angrobe
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4278f000-0258-4de5-93a1-195b48e5061e
ms.reviewer: chrisbal
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 618e2abda642c3b9b2e813824dfd4235c9309faa
ms.openlocfilehash: 82cc94eb37b11251343706d60a45fb78458cab7e


---


# Terminar a inscrição do seu dispositivo do Intune caso tenha recusado os Termos de Utilização

A melhor forma de anular a inscrição do dispositivo Android é aceitar os Termos de Utilização, iniciar sessão na aplicação do Portal da Empresa e, em seguida, utilize [estas instruções](unenroll-your-device-from-intune-android.md) para anular a inscrição. No entanto, se recusou os Termos de Utilização ao tentar iniciar sessão na aplicação Portal da Empresa, será impedido de iniciar sessão na mesma em futuras tentativas, por isso terá de utilizar estas instruções de "solução" para anular a inscrição do seu dispositivo.

Ao desinstalar a aplicação do Portal da Empresa, também está a anular a inscrição do dispositivo do Intune, o que significa que o dispositivo já não poderá aceder a recursos da empresa.  Para obter mais informações sobre o que acontece quando anula a inscrição, veja [What happens if you unenroll your device from Intune? (O que acontece se anular a inscrição do seu dispositivo no Intune?)](what-happens-if-you-unenroll-your-device-from-intune-android.md).

Antes de poder desinstalar a aplicação do Portal da Empresa, terá de aceder à definição **Administradores de dispositivos** e desativar o **Portal da Empresa**. Os passos poderão variar um pouco, consoante o seu dispositivo Android.

Para terminar a inscrição do seu dispositivo no Intune e desinstalar a aplicação do Portal da Empresa:

1.  Aceda a **Definições** &gt; **Segurança &amp; Bloqueio de Ecrã** &gt; **Administradores de dispositivos**.

    A conclusão deste passo anula imediatamente a inscrição do seu dispositivo.

2.  Desmarque a caixa de verificação junto a **Portal da Empresa** ou desative-o.

    Já pode desinstalar a aplicação do portal da Empresa.

Ainda precisa de ajuda? Contacte o se administrador de TI (verifique as informações de contacto no [Web site do Portal da Empresa](http://portal.manage.microsoft.com)) ou escreva para a equipa do Microsoft Android, através do endereço wintunedroidfbk@microsoft.com.


### Consulte também
[Utilizar o dispositivo Android com o Intune](using-your-android-device-with-intune.md)



<!--HONumber=Jul16_HO4-->


