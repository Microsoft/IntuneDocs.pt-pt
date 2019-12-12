---
title: 'Guia de Início Rápido: enviar notificações para dispositivos não conformes'
titleSuffix: Microsoft Intune
description: Neste guia de início rápido, você usa Microsoft Intune para enviar notificações por email para dispositivos não compatíveis.
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
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/05/2019
ms.locfileid: "74410219"
---
# <a name="quickstart-send-notifications-to-noncompliant-devices"></a>Guia de Início Rápido: enviar notificações para dispositivos não conformes

Neste guia de início rápido, você usará Microsoft Intune para enviar uma notificação por email aos membros de sua força de equipe que têm dispositivos não compatíveis.

Por predefinição, quando o Intune deteta um dispositivo não conforme, este marca imediatamente o dispositivo como não conforme. O [acesso condicional](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) do Azure Active Directory (AD do Azure) bloqueia o dispositivo. Quando um dispositivo não está em conformidade, o Intune permite que você adicione ações de não conformidade, o que oferece flexibilidade para decidir o que fazer. Por exemplo, pode conceder um período de tolerância aos utilizadores para que estes estejam em conformidade antes de bloquear dispositivos não conformes.

Uma ação a ser tomada quando um dispositivo não atende à conformidade é enviar email para o usuário dos dispositivos. Você também pode personalizar uma notificação por email antes de enviá-la. Mais concretamente, pode personalizar os destinatários, o assunto e o corpo da mensagem, incluindo o logótipo da empresa e as informações de contacto. O Intune também inclui detalhes sobre o dispositivo não compatível na notificação por email.

Se não tiver uma subscrição do Intune, [inscreva-se numa conta de avaliação gratuita](../fundamentals/free-trial-sign-up.md).

## <a name="prerequisites"></a>Pré-requisitos

Ao usar políticas de conformidade do dispositivo para bloquear dispositivos de recursos corporativos, o acesso condicional do Azure AD deve ser configurado. Se você tiver concluído o guia de início rápido [criar uma política de conformidade do dispositivo](quickstart-set-password-length-android.md) , você está usando Azure Active Directory. Para obter mais informações sobre o Azure AD, consulte [acesso condicional em Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) e [maneiras comuns de usar o acesso condicional com o Intune](../protect/conditional-access-intune-common-ways-use.md).

## <a name="sign-in-to-intune"></a>Iniciar sessão no Intune

Entre no centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) como um [administrador global](../fundamentals/users-add.md#types-of-administrators) ou um [administrador de serviços](../fundamentals/users-add.md#types-of-administrators)do Intune. Se você tiver criado uma assinatura de avaliação do Intune, a conta com a qual você criou a assinatura será o administrador global.

## <a name="create-a-notification-message-template"></a>Criar um modelo de mensagem de notificação

Para enviar um e-mail aos seus utilizadores, crie um modelo de mensagem de notificação. Quando um dispositivo não estiver em conformidade, os detalhes que introduzir no modelo são apresentados no e-mail enviado aos utilizadores.

1. No Intune, selecione **dispositivos** > **políticas de conformidade** > **notificações** > **criar notificação**.
2. Introduza as seguintes informações:

   - **Nome**: *Administrador da Contoso*
   - **Assunto**: *Conformidade do dispositivo*
   - **Mensagem**: *o dispositivo não atende aos requisitos de conformidade de nossa organização no momento.*
   - **Cabeçalho do e-mail – Incluir logótipo da empresa**: defina a opção como **Ativado** para mostrar o logótipo da sua organização.
   - **Rodapé do e-mail – Incluir nome da empresa**: defina a opção como **Ativado** para mostrar o nome da sua organização.
   - **Rodapé do e-mail – Incluir informações de contacto**: defina a opção como **Ativado** para mostrar as informações de contacto da sua organização.

   ![Exemplo de uma mensagem de notificação de conformidade no Intune](./media/quickstart-send-notification/quickstart-send-notification-01.png)

3. Selecione **Avançar** e reveja sua notificação. Selecione **criar** e o modelo de mensagem de notificação está pronto para uso.

   > [!NOTE]
   > Também pode editar um modelo de Notificação criado anteriormente.

Para obter detalhes sobre como definir o nome da empresa, as informações de contato da empresa e o logotipo da empresa, consulte os seguintes artigos:

- [Informações da empresa e política de privacidade](../apps/company-portal-app.md#company-information-and-privacy-statement)
- [Informações de suporte](../apps/company-portal-app.md#support-information)
- [Personalização da marca da identidade da empresa](../apps/company-portal-app.md#company-identity-branding-customization).

## <a name="add-a-noncompliance-policy"></a>Adicionar uma política de não conformidade

Quando cria uma política de conformidade do dispositivo, o Intune cria automaticamente uma ação de não conformidade. O Intune marca os dispositivos como não compatíveis quando eles falham ao atender à sua política de conformidade. Pode personalizar o intervalo de tempo durante o qual o dispositivo está marcado como não conforme. Também pode adicionar outra ação quando criar uma política de conformidade ou atualizar uma política de conformidade existente.

Os seguintes passos descrevem como pode criar uma política de conformidade para dispositivos com o Windows 10.

1. No Intune, selecione **dispositivos** > **políticas de conformidade** > **criar política**.

2. Introduza as seguintes informações:

   - **Nome**: *Política de conformidade do Windows 10*
   - **Descrição**: *Política de conformidade do Windows 10*
   - **Plataforma**: Windows 10 e posterior

3. Selecione **Definições** > **Segurança do Sistema** para apresentar as definições de segurança do dispositivo.

4. Configure as seguintes opções:

   - Defina a opção **Exigir uma palavra-passe para desbloquear os dispositivos móveis** para **Exigir**. Esta definição especifica quando deve ser exigido aos utilizadores que introduzam uma palavra-passe antes de ser concedido o acesso a informações nos respetivos dispositivos móveis.

   - Defina a opção **Comprimento mínimo da palavra-passe** para **6**. Esta definição especifica o número mínimo de dígitos ou carateres na palavra-passe.

   ![Definições de Segurança do Sistema para criar uma nova política de conformidade](./media/quickstart-send-notification/system-security-settings-01.png)

5. Selecione **ok** > **OK** > **criar** para criar sua política de conformidade.

6. Selecione **Propriedades** > **Ações para não conformidade** > **Adicionar**.

7. Na caixa pendente **Ação**, confirme se a opção **Enviar mensagem de e-mail ao utilizador final** está selecionada.

8. Selecione **modelo de mensagem**, o modelo que você criou anteriormente neste artigo e **selecione** para selecionar o modelo de mensagem.

9. Selecione **adicionar** > **OK** > **salvar** para salvar as alterações.

## <a name="assign-the-policy"></a>Atribuir a política

Pode atribuir a política de conformidade a um grupo específico de utilizadores ou a todos os utilizadores. Quando o Intune reconhece que um dispositivo não está em conformidade, o usuário é notificado de que ele deve atualizar seu dispositivo para atender à política de conformidade. Use as etapas a seguir para atribuir a política.

1. No Intune, acesse **dispositivos** > **políticas de conformidade** e selecione a política de **conformidade do Windows 10** que você criou anteriormente.

2. Selecione **Atribuições**.

3. Na caixa pendente **Atribuir a**, selecione **Todos os Utilizadores**. Esta ação irá selecionar todos os utilizadores. Todos os utilizadores que tiverem um dispositivo com o **Windows 10 e posterior** que não cumpra esta política de conformidade serão notificados.

    > [!NOTE]
    > Pode incluir e excluir grupos ao atribuir políticas de conformidade.

4. Clique em **Guardar**.

Quando você tiver criado e salvo a política com êxito, ela será exibida na lista de **políticas de conformidade – políticas**. Repare se a opção **Atribuído** na lista está definida como **Sim**.

## <a name="next-steps"></a>Próximos passos

Neste guia de início rápido, utilizou o Intune para criar e atribuir uma política de conformidade aos dispositivos com o Windows 10 da sua força de trabalho para exigir uma palavra-passe de pelo menos seis carateres de comprimento. Para obter mais informações sobre como criar políticas de conformidade para dispositivos Windows, veja [Adicionar uma política de conformidade para dispositivos Windows no Intune](compliance-policy-create-windows.md).

Para seguir esta série de guias de início rápido do Intune, continue para o próximo guia de início rápido.

> [!div class="nextstepaction"]
> [Guia de Início Rápido: adicionar e atribuir uma aplicação cliente](../apps/quickstart-add-assign-app.md)
