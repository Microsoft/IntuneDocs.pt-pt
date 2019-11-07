---
title: Repor o código de acesso nos dispositivos Windows com o Microsoft Intune – Azure | Microsoft Docs
description: Para repor o código de acesso nos dispositivos Windows, instale o Serviço de Reposição do PIN da Microsoft e o Cliente de Reposição do PIN da Microsoft, crie uma política de dispositivo com o seu ID de Diretório do Azure Active Directory e, em seguida, reponha o código de acesso no portal do Azure através do Microsoft Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/07/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5027d012-d6c2-4971-a9ac-217f91d67d87
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1b2390462376c88129435de30eb98020563f3878
ms.sourcegitcommit: 28622c5455adfbce25a404de4d0437fa2b5370be
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/07/2019
ms.locfileid: "73713095"
---
# <a name="reset-the-passcode-on-windows-devices-using-intune"></a>Repor o código de acesso nos dispositivos Windows com o Intune

Pode repor o código de acesso dos dispositivos Windows. A funcionalidade de reposição do código de acesso utiliza o Serviço de Reposição do PIN da Microsoft para gerar um novo código de acesso para dispositivos com o Windows 10 Mobile. 

## <a name="supported-platforms"></a>Plataformas suportadas

- Atualização para Criadores do Windows 10 Mobile e posterior (associada ao Azure AD).

As seguintes plataformas **não** são suportadas:
- Windows
- iOS
- macOS
- Android

## <a name="authorize-the-pin-reset-services"></a>Autorizar os serviços de reposição do PIN

Para repor o código de acesso nos dispositivos Windows, carregue o serviço de reposição do PIN para o seu inquilino do Intune.

1. Aceda à [produção do Serviço de Reposição do PIN da Microsoft](https://login.windows.net/common/oauth2/authorize?response_type=code&client_id=b8456c59-1230-44c7-a4a2-99b085333e84&resource=https%3A%2F%2Fgraph.windows.net&redirect_uri=https%3A%2F%2Fcred.microsoft.com&state=e9191523-6c2f-4f1d-a4f9-c36f26f89df0&prompt=admin_consent) e inicie sessão com a conta de administrador inquilino.
2. Clique em **Aceitar** para permitir que o serviço de reposição do PIN aceda à sua conta: ![Aceitar o pedido do Servidor de Reposição do PIN para permissões](./media/device-windows-pin-reset/pin-reset-service-home-screen.png)
3. Aceda à [produção do Cliente de Reposição do PIN da Microsoft](https://login.windows.net/common/oauth2/authorize?response_type=code&client_id=9115dd05-fad5-4f9c-acc7-305d08b1b04e&resource=https%3A%2F%2Fcred.microsoft.com%2F&redirect_uri=ms-appx-web%3A%2F%2FMicrosoft.AAD.BrokerPlugin%2F9115dd05-fad5-4f9c-acc7-305d08b1b04e&state=6765f8c5-f4a7-4029-b667-46a6776ad611&prompt=admin_consent) e inicie sessão com a conta de administrador inquilino. Clique em **Aceitar** para permitir que o cliente de reposição do PIN aceda à sua conta.
4. No [portal do Azure](https://portal.azure.com), confirme se os serviços de reposição do PIN estão listados nas aplicações Empresariais (Todas as aplicações): ![Página de permissões do serviço de reposição do PIN](./media/device-windows-pin-reset/pin-reset-service-application.png)

> [!NOTE]
> Depois de Aceitar os pedidos de reposição do PIN, poderá receber a mensagem `Page not found` ou poderá parecer que nada aconteceu. Este comportamento é normal. Lembre-se de confirmar se as duas aplicações de Reposição do PIN estão listadas para o seu inquilino.

## <a name="configure-windows-devices-to-use-pin-reset"></a>Configurar dispositivos Windows para utilizar a reposição do PIN

Para configurar a reposição do PIN nos dispositivos Windows geridos por si, utilize uma [política de dispositivo personalizada do Windows 10 do Intune](../configuration/custom-settings-windows-10.md). Configure a política através do seguinte fornecedor do serviço de configuração de política do Windows (CSP):

**Utilizar a política de dispositivo** - `./Device/Vendor/MSFT/PassportForWork/*tenant ID*/Policies/EnablePinRecovery`

Substitua o *ID de inquilino* pelo seu ID de Diretório do Azure AD, que está listado nas **Propriedades** do Azure Active Directory no [portal do Azure](https://portal.azure.com).

Defina o valor deste CSP para **Verdadeiro**.

> [!TIP]
> Depois de criar a política, atribua-a (ou implemente-a) a um grupo. A política pode ser atribuída a grupos de utilizadores ou a grupos de dispositivos. Se optar por atribuí-la a um grupo de utilizadores, o grupo poderá incluir utilizadores que tenham outros dispositivos, como iOS. Tecnicamente, a política não é aplicada, mas estes dispositivos continuam a ser incluídos nos detalhes do estado.

## <a name="reset-the-passcode"></a>Repor o código de acesso

1. Entre no centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431). 
2. Selecione **Dispositivos** e, em seguida, selecione **Todos os dispositivos**.
3. Selecione o dispositivo cujo código de acesso quer repor. Nas propriedades do dispositivo, selecione **Novo código de acesso**.
4. Selecione **Sim** para confirmar. O código de acesso é gerado e apresentado no portal durante os sete dias seguintes.

## <a name="next-step"></a>Passo seguinte

Se a reposição do código de acesso falhar, será fornecida uma ligação no portal que lhe dará mais detalhes.
