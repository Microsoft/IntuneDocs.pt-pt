---
# required metadata

title: Inscrever dispositivos iOS pertencentes à empresa no Microsoft Intune | Microsoft Intune
description:
keywords:
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 2d3ca4ab-f20c-4d56-9413-f8ef19cf0722

# optional metadata

ROBOTS: noindex,nofollow
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Inscrever dispositivos iOS pertencentes à empresa no Microsoft Intune
O Microsoft Intune suporta a inscrição de dispositivos iOS pertencentes à empresa através do Programa de registo de dispositivos da Apple (DEP) ou da ferramenta [Apple Configurator](http://go.microsoft.com/fwlink/?LinkId=518017) em execução num computador Mac.

Pode inscrever dispositivos iOS pertencentes à empresa de três formas diferentes:

-   **Inscrição com o Assistente de Configuração** - repõe o dispositivo para as definições de fábrica e prepara-o para a configuração por parte do novo utilizador do dispositivo. Este método requer que o administrador ligue o dispositivo iOS por USB ao computador Mac que está a executar o Apple Configurator para pré-configurar a inscrição. Os dispositivos são, depois, entregues aos utilizadores, que executam o processo Assistente de configuração, configurando os dispositivos com as credenciais escolares ou profissionais e concluindo o processo de inscrição. [Inscrever dispositivos iOS com o Apple Configurator e o Assistente de configuração](ios-setup-assistant-enrollment-in-microsoft-intune.md)

-   **Inscrição Direta** - cria um ficheiro compatível com o Apple Configurator para utilização durante a preparação do dispositivo. Não é efetuada a reposição do dispositivos para as definições de fábrica mas não existe uma afiliação a utilizadores. Este método requer que o administrador ligue o dispositivo iOS por USB ao computador Mac que está a executar o Apple Configurator para o inscrever. [Inscrever dispositivos iOS com o Apple Configurator e a Inscrição Direta](ios-direct-enrollment-in-microsoft-intune.md)

-   **Programa de inscrição de dispositivos (DEP)** – implementa um perfil de inscrição por ondas eletromagnéticas em dispositivos comprados através do Programa de inscrição de dispositivos da Apple. Quando o utilizador executa o Assistente de configuração no dispositivo, este é inscrito no Intune.  Os utilizadores não podem anular a inscrição de dispositivos inscritos através do DEP. [Inscrição de dispositivos iOS do Programa de inscrição de dispositivos](ios-device-enrollment-program-in-microsoft-intune.md)




### Consulte também
[Prepare-se para inscrever dispositivos no Microsoft Intune](get-ready-to-enroll-devices-in-microsoft-intune.md)


<!--HONumber=May16_HO2-->


