---
title: "Repor códigos de acesso em dispositivos Windows com o Intune"
titleSuffix: Intune on Azure
description: "Saiba como utilizar o Intune para repor o código de acesso em dispositivos Windows integrados com o \"Serviço de Reposição do PIN da Microsoft\"."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 07/05/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5027d012-d6c2-4971-a9ac-217f91d67d87
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 3688eef68fc9dcfced976db02c8d50126fa30da8
ms.sourcegitcommit: fd5b7aa26446d2fa92c21638cb29371e43fe169f
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/06/2017
---
# <a name="reset-the-passcode-on-windows-devices-integrated-with-the-microsoft-pin-reset-service-using-intune"></a>Repor o código de acesso em dispositivos Windows integrados com o Serviço de Reposição do PIN da Microsoft através do Intune

A funcionalidade de reposição de código de acesso para dispositivos Windows tem integração com o Serviço de Reposição do PIN da Microsoft para permitir gerar um novo código de acesso para dispositivos que executem o Windows 10 Mobile. Os dispositivos têm de ter a Atualização para Criativos do Windows 10 ou posterior.


## <a name="before-you-start"></a>Antes de começar

Antes de poder repor o código de acesso remotamente em dispositivos Windows que pode gerir, tem de integrar o serviço de reposição do PIN no seu inquilino do Intune e configurar os dispositivos que gere. Siga estas instruções para fazer essa configuração:

### <a name="connect-intune-with-the-pin-reset-service"></a>Ligar o Intune ao serviço de reposição do PIN

1. Visite o [site da Integração do Serviço de Reposição do PIN da Microsoft](https://login.windows.net/common/oauth2/authorize?response_type=code&client_id=b8456c59-1230-44c7-a4a2-99b085333e84&resource=https%3A%2F%2Fgraph.windows.net&redirect_uri=https%3A%2F%2Fcred.microsoft.com&state=e9191523-6c2f-4f1d-a4f9-c36f26f89df0&prompt=admin_consent), e inicie sessão com a conta de administrador do inquilino que utiliza para gerir o inquilino do Intune.
2. Depois de iniciar sessão, clique em **Aceitar** para dar consentimento ao serviço de reposição do PIN para aceder à sua conta.<br>
![Página de permissões do serviço de reposição do PIN](./media/pin-reset-service-application.png)
3. No portal do Azure, pode verificar que o Intune e o serviço de reposição do PIN foram integrados a partir das aplicações Empresariais. Todas as aplicações são apresentadas num painel como o da seguinte captura de ecrã:<br>
![Aplicação do serviço de reposição do PIN no Azure](./media/pin-reset-service-home-screen.png)
4. Inicie sessão [neste site](https://login.windows.net/common/oauth2/authorize?response_type=code&client_id=9115dd05-fad5-4f9c-acc7-305d08b1b04e&resource=https%3A%2F%2Fcred.microsoft.com%2F&redirect_uri=ms-appx-web%3A%2F%2FMicrosoft.AAD.BrokerPlugin%2F9115dd05-fad5-4f9c-acc7-305d08b1b04e&state=6765f8c5-f4a7-4029-b667-46a6776ad611&prompt=admin_consent) com as suas credenciais de administrador do inquilino do Intune e volte a selecionar **Aceitar** para dar consentimento ao serviço para aceder à sua conta.

### <a name="configure-windows-devices-to-use-pin-reset"></a>Configurar dispositivos Windows para utilizar a reposição do PIN

Para configurar a reposição do PIN nos dispositivos Windows que gere, utilize uma [política de dispositivo personalizada do Windows 10 do Intune](custom-settings-windows-10.md) para ativar a funcionalidade. Configure a política através dos seguintes fornecedores de serviços de configuração de políticas do Windows (CSPs):


- **Para utilizadores** - **./User/Vendor/MSFT/PassportForWork/<tenant ID>/Policies/EnablePinRecovery**
- **Para dispositivos** - **./Device/Vendor/MSFT/PassportForWork/<tenant ID>/Policies/EnablePinRecovery**

Ambos os valores destes CSPs têm de ser definidos como **Verdadeiro**.

## <a name="steps-to-reset-the-passcode"></a>Passos para repor o código de acesso

1. Inicie sessão no portal do Azure.
2. Escolha **Mais Serviços** > **Monitorização + Gestão** > **Intune**.
3. No painel **Intune**, escolha **Dispositivos**.
4. No painel **Dispositivos**, escolha **Gerir** > **Todos os dispositivos**.
5. Selecione o dispositivo para o qual pretende repor o código de acesso e, em seguida, no painel de propriedades do dispositivo, selecione **Novo código de acesso**.
6. Na página de confirmação que for apresentada, selecione **Sim**. O código de acesso é gerado e apresentado no portal durante os sete dias seguintes.

## <a name="next-steps"></a>Passos seguintes

Se a reposição do código de acesso falhar, será fornecida uma ligação no portal para obter mais informações.


