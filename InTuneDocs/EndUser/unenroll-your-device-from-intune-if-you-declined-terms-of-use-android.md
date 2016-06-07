---
# required metadata

title: Terminar a inscrição do seu dispositivo do Intune caso tenha recusado os Termos de Utilização | Microsoft Intune
description:
keywords:
author: staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 4278f000-0258-4de5-93a1-195b48e5061e

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# Terminar a inscrição do seu dispositivo do Intune caso tenha recusado os Termos de Utilização

A melhor forma de anular a inscrição do dispositivo Android é aceitar os Termos de Utilização, iniciar sessão na aplicação do Portal da Empresa e, em seguida, utilize [estas instruções](unenroll-your-device-from-intune-android.md) para anular a inscrição. No entanto, se recusou os Termos de Utilização ao tentar iniciar sessão na aplicação Portal da Empresa, será impedido de iniciar sessão na mesma em futuras tentativas, por isso terá de utilizar estas instruções de "solução" para anular a inscrição do seu dispositivo.

Ao desinstalar a aplicação do Portal da Empresa, também está a anular a inscrição do dispositivo do Intune, o que significa que o dispositivo já não poderá aceder a recursos da empresa.  Para obter mais informações sobre o que acontece quando anula a inscrição, veja [O que acontece se anular a inscrição do seu dispositivo no Intune?](what-happens-if-you-unenroll-your-device-from-intune-android.md).

Antes de poder desinstalar a aplicação do Portal da Empresa, terá de aceder à definição **Administradores de dispositivos** e desativar o **Portal da Empresa**. Os passos poderão variar um pouco, consoante o seu dispositivo Android.

Para terminar a inscrição do seu dispositivo no Intune e desinstalar a aplicação do Portal da Empresa:

1.  Aceda a **Definições** &gt; **Segurança &amp; Bloqueio de Ecrã** &gt; **Administradores de dispositivos**

    A conclusão deste passo anula imediatamente a inscrição do seu dispositivo.

2.  Desmarque a caixa de verificação ao lado ou desative o **Portal da Empresa**

    Já pode desinstalar a aplicação do portal da Empresa.


### Consulte também
[Utilizar o dispositivo Android com o Intune](using-your-android-device-with-intune.md)

<!--HONumber=May16_HO2-->

