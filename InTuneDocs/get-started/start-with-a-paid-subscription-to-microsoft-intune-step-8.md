---
title: "Ativar a inscrição de dispositivos | Documentos da Microsoft"
description: "Definir autoridade MDM e ativar a inscrição de dispositivos iOS, Mac, Android e Windows."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 02/14/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5d3215e7-0a5c-44bd-afb0-aeafce98c43f
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: ad13897fe7bbe4fe13167bb4ce7f558b436a7a90
ms.openlocfilehash: c4ef429722f5e33092473641839b59de3bee1c1c


---

# <a name="enable-enrollment-for-mobile-devices"></a>Ativar a inscrição de dispositivos móveis

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Este tópico descreve como um administrador do Intune pode ativar a inscrição de dispositivos móveis. Para obter ajuda sobre como utilizar o Intune no seu telemóvel, veja [Utilizar dispositivos geridos para trabalhar](https://docs.microsoft.com/intune/enduser/company-portal-frequently-asked-questions). 

Para configurar a gestão de dispositivos móveis com o Intune, primeiro, tem de definir a *autoridade de gestão de dispositivos móveis*, que identifica o serviço que pode gerir dispositivos associados à sua conta. Esta orientação assume que irá utilizar o serviço Intune em vez do System Center Configuration Manager. Assim que a autoridade de MDM seja definida, pode ativar a gestão para plataformas de dispositivos e inscrever os seus dispositivos com a aplicação Portal da Empresa.

## <a name="enable-device-enrollment"></a>Ativar a inscrição de dispositivos

1. **Tornar o Intune a autoridade de gestão de dispositivos móveis**
    Na [consola de administração do Intune](https://manage.microsoft.com/), escolha **Administração** > **Gestão de Dispositivos Móveis** e escolha **Definir Autoridade MDM**, em **Tarefas**.  

2. Escolha **Sim** na caixa de diálogo Autoridade de MDM.

    ![Consola de administração. Definir MDM para o Intune](./media/mdmAuthority.png)

## <a name="choose-how-to-enroll-devices"></a>Escolher como inscrever dispositivos

O Intune pode gerir dispositivos numa variedade de modos consoante os requisitos da sua empresa. "Traga o seu próprio dispositivo" (BYOD), dispositivos pertencentes à empresa, "escolha o seu próprio dispositivo" (CYOD) e dispositivos no modo local público são apenas alguns cenários de inscrição disponíveis.

Siga estes passos para [Escolher como inscrever dispositivos](choose-how-to-enroll-devices1.md).

## <a name="enable-mdm-for-your-device-platform"></a>Ativar MDM na plataforma de dispositivos
A inscrição tem de estar ativada para dispositivos iOS, Mac e Android for Work a estabelecer uma relação entre o fornecedor da plataforma e o seu inquilino do Intune. Os dispositivos Windows e Android não precisam de passos adicionais, contudo, pode simplificar a inscrição de dispositivos Windows para os seus utilizadores com a criação de uma entrada de registo DNS especial.

Ative a gestão de dispositivos na plataforma de dispositivos que pretende gerir. Dependendo da sua plataforma, são necessários requisitos diferentes:

-  [iOS e macOS](https://docs.microsoft.com/intune/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune)
-  [Window PC](https://docs.microsoft.com/intune/deploy-use/set-up-windows-device-management-with-microsoft-intune)
-  [Windows 10 Mobile e Windows Phone](https://docs.microsoft.com/intune/deploy-use/set-up-windows-phone-management-with-microsoft-intune)
- [Android for Work](https://docs.microsoft.com/intune/deploy-use/set-up-android-for-work)

Depois de a inscrição estar ativada, os utilizadores podem transferir a aplicação Portal da Empresa para o respetivo dispositivo e concluir o processo de inscrição do dispositivo.

### <a name="enable-company-owned-device-enrollment"></a>Ativar a inscrição de dispositivos pertencentes à empresa
Também pode ativar uma variedade de cenários de [inscrição de dispositivos pertencentes à empresa](https://docs.microsoft.com/intune/deploy-use/manage-corporate-owned-devices), incluindo:
- [Programa de Inscrição de Dispositivos da Apple](https://docs.microsoft.com/intune/deploy-use/ios-device-enrollment-program-in-microsoft-intune)
- [Inscrição do Assistente de Configuração do Apple Configurator](https://docs.microsoft.com/intune/deploy-use/ios-setup-assistant-enrollment-in-microsoft-intune)
- [Inscrição do Assistente de Configuração do Apple Configurator](https://docs.microsoft.com/intune/deploy-use/ios-direct-enrollment-in-microsoft-intune)
- [Gestor de Inscrição de Dispositivos](https://docs.microsoft.com/intune/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune)

### <a name="next-steps"></a>Passos seguintes
Parabéns! Acabou de concluir o último passo do *Guia de introdução do Intune*. Agora que a configuração inicial está concluída, pode considerar a ativação da funcionalidade MDM adicional.

>[!div class="step-by-step"]

>[&larr;**Inscrever dispositivos**](.\start-with-a-paid-subscription-to-microsoft-intune-step-8.md)     [**Tarefas de pós-configuração**&rarr;](.\post-configuration-tasks.md)  



<!--HONumber=Feb17_HO3-->


