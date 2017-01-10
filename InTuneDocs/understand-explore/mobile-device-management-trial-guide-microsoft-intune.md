---
title: "Avaliar a gestão de dispositivos móveis no Microsoft Intune | Documentos da Microsoft"
description: "Avalie a MDM na sua versão de avaliação gratuita do Intune."
keywords: 
author: lindavr
ms.author: lindavr
manager: angrobe
ms.date: 11/29/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 47806f69-303d-41d9-9b0e-9b9445ea24ac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: eeb85a28ea6f99a0123ec5df3b0d476a678b85cb
ms.openlocfilehash: 4133c64d283682f0be37cd6ac69164ef872a5026


---

# <a name="evaluate-mobile-device-management-in-microsoft-intune"></a>Avaliar a gestão de dispositivos móveis no Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Este guia de avaliação irá mostrar como funciona a gestão de dispositivos móveis no Intune. Deverá:
- Inscrever um dispositivo para ser gerido pelo Intune.
- Criar grupos para organizar utilizadores e dispositivos.
- Criar e implementar algumas políticas de gestão de dispositivos para os grupos.
- Publicar uma aplicação para que os utilizadores com dispositivos inscritos a possam instalar nos respetivos dispositivos.
<!--- - Monitor the device? View a report of compliant devices?--->
<!--- - Remove the device from management--->

## <a name="assumptions"></a>Pressupostos
Este guia de avaliação assume que está a utilizar a versão de avaliação apenas para o fim destinado e pretende começar com um ambiente limpo na altura da subscrição.

Para facilitar a introdução à utilização da versão de avaliação, estamos a configurar um ambiente muito simples que utiliza apenas o Intune e assume que este será a sua autoridade de gestão de dispositivos móveis. No entanto, no decorrer do guia, iremos destacar conteúdo técnico mais aprofundado, se pretender explorar mais.

A versão de avaliação permite-lhe fazer tudo o que normalmente faria numa versão de subscrição, a única diferença é que a versão de avaliação está limitada a 100 contas de utilizador.

## <a name="whats-not-covered"></a>O que não é abrangido
|Se estiver interessado em |Leia isto |
|------------------------|----------|
|MDM num ambiente não destinado a teste | [Introdução](https://docs.microsoft.com/en-us/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune) |
|MDM com Intune e System Center Configuration Manager | [Gestão híbrida de dispositivos móveis](https://docs.microsoft.com/en-us/sccm/mdm/understand/hybrid-mobile-device-management) |

Uma vez que os guias acima ajudam-no a configurar o Intune em ambientes de produção, esses são maiores e têm muitos mais pontos de decisão que precisa de percorrer do que no guia de avaliação.

Para se familiarizar rapidamente com o Intune, sugerimos que comece com o guia de avaliação e, em seguida, avance para os outros guias.

## <a name="prerequisites-for-this-evaluation"></a>Pré-requisitos para esta avaliação
- Internet Explorer 10 ou posterior
- Um dispositivo para testar a forma como os utilizadores do Intune irão inscrever e gerir os respetivos dispositivos através do Portal da Empresa. Estamos a utilizar um iPad e um telemóvel Android para este guia.
- Para gerir o iPad ou outro dispositivo iOS, precisará de um [certificado de serviço Apple Push Notification](https://docs.microsoft.com/intune/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune).
- Uma [subscrição de avaliação do Intune](sign-up-for-30-day-trial-microsoft-intune.md)

## <a name="set-your-mdm-authority"></a>Definir a autoridade de MDM
O primeiro passo para gerir dispositivos móveis com o Intune passa por definir a **autoridade de gestão de dispositivos móveis (MDM)**.

Se estiver a utilizar o Intune autónomo, como esta versão de avaliação assume que está, ou se estiver a utilizar o Intune como parte de uma subscrição Enterprise Mobility + Security (EMS), precisará de configurar o Intune para ser a sua autoridade de gestão de dispositivos móveis. Isto é, designa o Intune para ser o serviço que utiliza para gerir dispositivos móveis na sua organização.

Os clientes que pretendem utilizar o Intune com o System Center Configuration Manager para gerir dispositivos móveis têm de decidir se vão utilizar o Intune ou o Configuration Manager como a respetiva autoridade de gestão de dispositivos móveis. Esta é uma decisão importante num ambiente de produção porque atualmente é muito difícil alterar a definição uma vez estabelecida, mas isso está fora do âmbito deste guia de avaliação. Para saber mais sobre as implicações da configuração do Intune ou do Configuration Manager como a sua autoridade de MDM, veja [Choose between standalone Intune and hybrid mobile device management (Escolher entre o Intune autónomo e a gestão híbrida de dispositivos móveis)](https://docs.microsoft.com/en-us/sccm/mdm/understand/choose-between-standalone-intune-and-hybrid-mobile-device-management).

Vamos definir o Intune como a autoridade de MDM na versão de avaliação. Tal não afetará o ambiente de produção, exceto se optar por utilizar a versão de avaliação para o seu ambiente de produção.

1. Na [consola de administração do Microsoft Intune](https://manage.microsoft.com/), selecione **Administração** &gt; **Gestão de Dispositivos Móveis**.
2. Na lista **Tarefas**, escolha **Definir Autoridade de MDM**. A caixa de diálogo **Definir Autoridade de Gestão de Dispositivos Móveis** é aberta. <!---screen shot--->
3. O Intune pede a confirmação de que pretende o Intune como a sua autoridade MDM. Selecione a caixa de verificação e, em seguida, escolha **Sim** para utilizar o Intune para gerir dispositivos móveis.

## <a name="enroll-your-test-devices-into-intune"></a>Inscrever dispositivos de teste no Intune

Para este guia, iremos inscrever um telemóvel Android e um iPad da Apple, mas forneceremos ligações para [saber mais sobre a inscrição de dispositivos no Intune](#Learn-more-about-device-enrollment) no final desta secção.
### <a name="android"></a>Android
Instale a aplicação **Portal da Empresa do Intune** da Microsoft Corporation, disponível no [Google Play](http://go.microsoft.com/fwlink/p/?LinkId=386612), e inicie sessão com as [credenciais de utilizador do Intune que criou](sign-up-for-30-day-trial-microsoft-intune.md#add-users) quando se inscreveu para a avaliação gratuita.

### <a name="ios"></a>iOS
Antes de os utilizadores poderem inscrever os respetivos dispositivos iOS, terá de configurar o Intune para gerir esses dispositivos.

1. **Obter um pedido de assinatura do certificado**<br/>
Inicie sessão no Intune com a sua conta de administrador e aceda a **Administração** > **Gestão de Dispositivos Móveis** > **iOS e Mac OS X** > **Carregar Certificado APNs** e selecione **Transferir pedido de certificado APNs**. Guarde o ficheiro de pedido de assinatura de certificado (.csr) localmente. O ficheiro .csr é utilizado para pedir um certificado de relação de confiança do Portal de Certificados Apple Push. <!--- screen shot--->
2.  **Obter um certificado do serviço Apple Push Notification**<BR/>
Vá para o [Portal Apple Push Certificates](https://idmsa.apple.com/IDMSWebAuth/login?appIdKey=3fbfc9ad8dfedeb78be1d37f6458e72adc3160d1ad5b323a9e5c5eb2f8e7e3e2&rv=2) e inicie sessão com o ID Apple da sua empresa para criar o certificado de APNs através do ficheiro .csr. Após escolher **Carregar no Portal de Certificados Push da Apple**, receberá um ficheiro .json que não pode ser utilizado para o APNs. Conclua a transferência, regresse ao Portal de Certificados Push da Apple para obter Certificados para Servidores de Terceiros e, em seguida, escolha **Transferir**.

 Transfira o certificado de APNs (.pem) e guarde o ficheiro localmente. Este ID Apple tem de ser utilizado posteriormente para renovar o certificado APNs.
3.  **Adicionar o certificado APNs ao Intune**<BR/>
Na consola de administração do Microsoft Intune, aceda a **Administração** > **Gestão de Dispositivos Móveis** > **iOS e Mac OS X** > **Carregar Certificado APNs** e, em seguida, escolha **Carregar Certificado APNs**. Aceda ao ficheiro de certificado (.pem), selecione **Abrir** e, em seguida, introduza o seu ID Apple. Com o certificado APNs. O Intune pode inscrever e gerir dispositivos iOS ao enviar políticas para dispositivos móveis inscritos.
4.  **Indique aos utilizadores como devem inscrever os respetivos dispositivos para poderem aceder aos recursos da empresa.**<br/>
Para obter instruções sobre a inscrição do utilizador final, veja [Inscrever o dispositivo iOS no Intune](https://docs.microsoft.com/en-us/Intune/enduser/enroll-your-device-in-intune-ios) e [Inscrever o dispositivo Mac OS X no Intune](https://docs.microsoft.com/en-us/Intune/enduser/enroll-your-device-in-intune-mac-os-x). O processo de inscrição informa os utilizadores sobre o que podem esperar e o que os administradores de TI podem e não podem ver nos respetivos dispositivos.


### <a name="learn-more-about-device-enrollment"></a>Saiba mais sobre a inscrição de dispositivos

O Intune suporta as seguintes plataformas de dispositivos:

[!INCLUDE[mdm-supported-devices](../includes/mdm-supported-devices.md)]

Os requisitos para ativar a gestão de dispositivos dependem das plataformas que pretende gerir.
- Os dispositivos móveis **Android** permitem aos utilizadores [realizar a inscrição com a aplicação do Portal da Empresa](/intune/deploy-use/set-up-android-management-with-microsoft-intune), disponível no Google Play. Não é necessária nenhuma configuração adicional no Intune.
- [Requisitos de configuração para **iOS e Mac OS X**](/intune/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune)
- [Requisitos de configuração para **Windows Phone**](/intune/deploy-use/set-up-windows-phone-management-with-microsoft-intune).

<!--- ## Verify enrollment--->
<!--- START HERE

### iOS and Mac OS X
Install the **Microsoft Intune Company Portal** app from Microsoft Corporation available in the App Store and sign in with Intune user credentials added above. View **Enrolled devices** to add your device.



### Windows Phone 8.1
Users install the **Company Portal** app from Microsoft Corporation, available in the Windows Phone store, and sign in with the Intune user credentials added above.  View **Enrolled devices** to add your device.

## Install the previously deployed app
Open the Company Portal on the mobile device, choose **Apps**, and then install **Microsoft Skype**.--->



## <a name="next-steps"></a>Passos seguintes
[Criar grupos para organizar utilizadores e dispositivos](get-started-with-a-30-day-trial-of-microsoft-intune-step-3.md)



<!--HONumber=Jan17_HO1-->


