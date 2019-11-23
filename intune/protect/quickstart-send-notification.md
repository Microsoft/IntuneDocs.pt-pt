---
title: 'Guia de Início Rápido: enviar notificações para dispositivos não conformes'
titleSuffix: Microsoft Intune
description: In this quickstart, you use Microsoft Intune to send email notifications to noncompliant devices.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/21/2019
ms.topic: quickstart
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a1b89f2d-7937-46bb-926b-b05f6fa9c749
ms.reviewer: jinyoon
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6d89cfcafd5452b990509e0fa6fd431a614ee5c1
ms.sourcegitcommit: a7b479c84b3af5b85528db676594bdb3a1ff6ec6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/22/2019
ms.locfileid: "74410219"
---
# <a name="quickstart-send-notifications-to-noncompliant-devices"></a>Guia de Início Rápido: enviar notificações para dispositivos não conformes

In this quickstart, you'll use Microsoft Intune to send an email notification to the members of your workforce that have noncompliant devices.

Por predefinição, quando o Intune deteta um dispositivo não conforme, este marca imediatamente o dispositivo como não conforme. Azure Active Directory (Azure AD) [Conditional Access](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) then blocks the device. When a device isn't compliant, Intune allows you to add actions for noncompliance, which gives you flexibility to decide what to do. Por exemplo, pode conceder um período de tolerância aos utilizadores para que estes estejam em conformidade antes de bloquear dispositivos não conformes.

One action to take when a device doesn't meet compliance is to send email to the devices user. You can also customize an email notification before sending it. Mais concretamente, pode personalizar os destinatários, o assunto e o corpo da mensagem, incluindo o logótipo da empresa e as informações de contacto. Intune also includes details about the noncompliant device in the email notification.

Se não tiver uma subscrição do Intune, [inscreva-se numa conta de avaliação gratuita](../fundamentals/free-trial-sign-up.md).

## <a name="prerequisites"></a>Pré-requisitos

When using device compliance policies to block devices from corporate resources, Azure AD Conditional Access must be set up. If you've completed the [Create a device compliance policy](quickstart-set-password-length-android.md) quickstart, you're using Azure Active Directory. For more information about Azure AD, see [Conditional Access in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) and [common ways to use Conditional Access with Intune](../protect/conditional-access-intune-common-ways-use.md).

## <a name="sign-in-to-intune"></a>Iniciar sessão no Intune

Sign in to the [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) as a [Global administrator](../fundamentals/users-add.md#types-of-administrators) or an Intune [Service administrator](../fundamentals/users-add.md#types-of-administrators). If you've created an Intune Trial subscription, the account you created the subscription with is the Global administrator.

## <a name="create-a-notification-message-template"></a>Criar um modelo de mensagem de notificação

Para enviar um e-mail aos seus utilizadores, crie um modelo de mensagem de notificação. Quando um dispositivo não estiver em conformidade, os detalhes que introduzir no modelo são apresentados no e-mail enviado aos utilizadores.

1. In Intune, select **Devices** > **Compliance policies** > **Notifications** > **Create notification**.
2. Introduza as seguintes informações:

   - **Nome**: *Administrador da Contoso*
   - **Assunto**: *Conformidade do dispositivo*
   - **Message**: *Your device is currently not meeting our organization's compliance requirements.*
   - **Cabeçalho do e-mail – Incluir logótipo da empresa**: defina a opção como **Ativado** para mostrar o logótipo da sua organização.
   - **Rodapé do e-mail – Incluir nome da empresa**: defina a opção como **Ativado** para mostrar o nome da sua organização.
   - **Rodapé do e-mail – Incluir informações de contacto**: defina a opção como **Ativado** para mostrar as informações de contacto da sua organização.

   ![Exemplo de uma mensagem de notificação de conformidade no Intune](./media/quickstart-send-notification/quickstart-send-notification-01.png)

3. Select **Next** and review your notification. Select **Create** and the notification message template is ready to use.

   > [!NOTE]
   > Também pode editar um modelo de Notificação criado anteriormente.

For details about setting your company name, company contact information, and company logo, see the following articles:

- [Company information and privacy statement](../apps/company-portal-app.md#company-information-and-privacy-statement)
- [Support information](../apps/company-portal-app.md#support-information)
- [Company identity branding customization](../apps/company-portal-app.md#company-identity-branding-customization).

## <a name="add-a-noncompliance-policy"></a>Adicionar uma política de não conformidade

Quando cria uma política de conformidade do dispositivo, o Intune cria automaticamente uma ação de não conformidade. Intune then marks devices as noncompliant when they fail to meet your compliance policy. Pode personalizar o intervalo de tempo durante o qual o dispositivo está marcado como não conforme. Também pode adicionar outra ação quando criar uma política de conformidade ou atualizar uma política de conformidade existente.

Os seguintes passos descrevem como pode criar uma política de conformidade para dispositivos com o Windows 10.

1. In Intune, select **Devices** > **Compliance Policies** > **Create Policy**.

2. Introduza as seguintes informações:

   - **Nome**: *Política de conformidade do Windows 10*
   - **Descrição**: *Política de conformidade do Windows 10*
   - **Plataforma**: Windows 10 e posterior

3. Selecione **Definições** > **Segurança do Sistema** para apresentar as definições de segurança do dispositivo.

4. Configure the following options:

   - Defina a opção **Exigir uma palavra-passe para desbloquear os dispositivos móveis** para **Exigir**. Esta definição especifica quando deve ser exigido aos utilizadores que introduzam uma palavra-passe antes de ser concedido o acesso a informações nos respetivos dispositivos móveis.

   - Defina a opção **Comprimento mínimo da palavra-passe** para **6**. Esta definição especifica o número mínimo de dígitos ou carateres na palavra-passe.

   ![Definições de Segurança do Sistema para criar uma nova política de conformidade](./media/quickstart-send-notification/system-security-settings-01.png)

5. Select **OK** > **OK** > **Create** to create your compliance policy.

6. Selecione **Propriedades** > **Ações para não conformidade** > **Adicionar**.

7. Na caixa pendente **Ação**, confirme se a opção **Enviar mensagem de e-mail ao utilizador final** está selecionada.

8. Select **Message template**,  the template you created earlier in this article, and then **Select** to select the message template.

9. Select **ADD** > **OK** > **Save** to save your changes.

## <a name="assign-the-policy"></a>Atribuir a política

Pode atribuir a política de conformidade a um grupo específico de utilizadores ou a todos os utilizadores. When Intune recognizes that a device is noncompliant, the user is notified that they must update their device to meet the compliance policy. Use the following steps to assign the policy.

1. In Intune go to **Devices** > **Compliance Policies** and select the **Windows 10 compliance** policy that you created earlier.

2. Selecione **Atribuições**.

3. Na caixa pendente **Atribuir a**, selecione **Todos os Utilizadores**. Esta ação irá selecionar todos os utilizadores. Todos os utilizadores que tiverem um dispositivo com o **Windows 10 e posterior** que não cumpra esta política de conformidade serão notificados.

    > [!NOTE]
    > Pode incluir e excluir grupos ao atribuir políticas de conformidade.

4. Clique em **Guardar**.

When you've successfully created and saved the policy, it will appear in the list of **Compliance policies - Policies**. Repare se a opção **Atribuído** na lista está definida como **Sim**.

## <a name="next-steps"></a>Próximos passos

Neste guia de início rápido, utilizou o Intune para criar e atribuir uma política de conformidade aos dispositivos com o Windows 10 da sua força de trabalho para exigir uma palavra-passe de pelo menos seis carateres de comprimento. Para obter mais informações sobre como criar políticas de conformidade para dispositivos Windows, veja [Adicionar uma política de conformidade para dispositivos Windows no Intune](compliance-policy-create-windows.md).

Para seguir esta série de guias de início rápido do Intune, continue para o próximo guia de início rápido.

> [!div class="nextstepaction"]
> [Guia de Início Rápido: adicionar e atribuir uma aplicação cliente](../apps/quickstart-add-assign-app.md)
