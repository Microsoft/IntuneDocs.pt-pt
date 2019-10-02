---
title: Mensagem de não conformidade e ações com o Microsoft Intune – Azure | Microsoft Docs
description: Crie um e-mail de notificação para enviar para os dispositivos não conformes. Adicione ações depois de um dispositivo ser marcado como não conforme, tais como adicionar um período de tolerância para obter conformidade, ou crie um agendamento para bloquear o acesso até o dispositivo ficar em conformidade. Faça isto com o Microsoft Intune no Azure.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7fabc475e1ae05e6ef3fe70e8a507a15bee456cb
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71732344"
---
# <a name="automate-email-and-add-actions-for-noncompliant-devices-in-intune"></a>Automatizar email e adicionar ações para dispositivos não compatíveis no Intune

Para dispositivos que não atendem às políticas ou regras de conformidade, você pode adicionar **ações de não conformidade**. Esse recurso configura uma sequência de ações ordenadas por tempo, como enviar por email ao usuário final e muito mais.

## <a name="overview"></a>Descrição geral

Por predefinição, quando o Intune deteta um dispositivo não conforme, este marca imediatamente o dispositivo como não conforme. O [acesso condicional](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) do Azure Active Directory (AD) bloqueia o dispositivo. Quando um dispositivo não está em conformidade, a **ação de não conformidade** também oferece flexibilidade para decidir o que fazer. Por exemplo, não bloqueie o dispositivo de imediato e dê ao utilizador um período de tolerância para ficar conforme.

Existem vários tipos de ação:

- **Enviar email para o usuário final**: Personalize uma notificação por email antes de enviá-la ao usuário final. Pode personalizar os destinatários, o assunto e o corpo da mensagem, incluindo o logótipo da empresa e as informações de contacto.

    Além disso, o Intune inclui detalhes sobre o dispositivo não conforme na notificação por e-mail.

- **Bloquear remotamente o dispositivo não compatível**: Para dispositivos que não são compatíveis, você pode emitir um bloqueio remoto. Em seguida, é pedido ao utilizador um PIN ou palavra-passe para desbloquear o dispositivo. Saiba mais sobre a funcionalidade [Bloqueio Remoto](../remote-actions/device-remote-lock.md). 

- **Marcar dispositivo como não compatível**: Crie uma agenda (em número de dias) depois que o dispositivo for marcado como não compatível. Pode configurar a ação para entrar em vigor imediatamente ou dar ao utilizador um período de tolerância para este ficar em conformidade.

Este artigo mostra-lhe como:

- Criar um modelo de notificação por mensagem
- Criar uma ação de não conformidade, como enviar um e-mail ou bloquear um dispositivo remotamente


## <a name="before-you-begin"></a>Antes de começar

- Para configurar as ações de não conformidade, tem de ter pelo menos uma política de conformidade de dispositivos. Para criar uma política de conformidade de dispositivos, veja as seguintes plataformas:

  - [Android](compliance-policy-create-android.md)
  - [Perfis de trabalho do Android](compliance-policy-create-android-for-work.md)
  - [iOS](compliance-policy-create-ios.md)
  - [macOS](compliance-policy-create-mac-os.md)
  - [Windows](compliance-policy-create-windows.md)

- Ao usar políticas de conformidade do dispositivo para bloquear dispositivos de recursos corporativos, o acesso condicional do Azure AD deve ser configurado. Consulte [acesso condicional em Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) ou [maneiras comuns de usar o acesso condicional com o Intune](conditional-access-intune-common-ways-use.md) para obter diretrizes.

## <a name="create-a-notification-message-template"></a>Criar um modelo de mensagem de notificação

Para enviar um e-mail aos seus utilizadores, crie um modelo de mensagem de notificação. Quando um dispositivo não estiver em conformidade, os detalhes que introduzir no modelo são apresentados no e-mail enviado aos utilizadores.

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Selecione **Conformidade do dispositivo** > **Notificações**.
3. Selecione **Criar notificação**. Introduza as seguintes informações:

   - **Name**
   - **Subject**
   - **Mensagem**
   - **Cabeçalho do e-mail – incluir o logótipo da empresa**
   - **Rodapé do e-mail – incluir o nome da empresa**
   - **Rodapé do e-mail – incluir informações de contacto**

   ![Exemplo de uma mensagem de notificação de conformidade no Intune](./media/actions-for-noncompliance/actionsfornoncompliance-1.PNG)

4. Quando terminar de adicionar as informações, selecione **Criar**. O Modelo de mensagem de notificação está pronto para ser utilizado. O logotipo que você carrega como parte da marca de Portal da Empresa é usado para modelos de email. Para obter mais informações sobre a imagem corporativa do Portal da Empresa, veja [Personalização da imagem corporativa da empresa](../apps/company-portal-app.md#company-identity-branding-customization).

> [!NOTE]
> Você também pode alterar ou atualizar um modelo de notificação existente que você criou anteriormente.

## <a name="add-actions-for-noncompliance"></a>Adicionar ações de não conformidade

Quando cria uma política de conformidade do dispositivo, o Intune cria automaticamente uma ação de não conformidade. Se um dispositivo não estiver atendendo à sua política de conformidade, essa ação marcará o dispositivo como não compatível. Pode personalizar o intervalo de tempo durante o qual o dispositivo está marcado como não conforme. Esta ação não pode ser removida.

Também pode adicionar outra ação quando criar uma política de conformidade ou atualizar uma política existente. 

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) e selecione **conformidade do dispositivo**.
2. Selecione **Políticas**, selecione uma das suas políticas e, em seguida, selecione **Propriedades**. 

    Ainda não tem uma política? Crie uma política para [Android](compliance-policy-create-android.md), [iOS](compliance-policy-create-ios.md), [Windows](compliance-policy-create-windows.md) ou para outra plataforma.
  
    > [!NOTE]
    > Os dispositivos JAMF e dispositivos visados com grupos de dispositivos não conseguem receber ações de conformidade neste momento.

3. Selecione **Ações para não conformidade** > **Adicionar**.
4. Selecione a sua **Ação**: 

    - **Enviar email para os usuários finais**: Quando o dispositivo não estiver em conformidade, escolha enviar email ao usuário. Além disso: 
    
         - Selecione o **Modelo de mensagem** que criou anteriormente
         - Introduza **Destinatários adicionais** ao selecionar grupos
    
    - **Bloquear remotamente o dispositivo não compatível**: Quando o dispositivo não estiver em conformidade, bloqueie o dispositivo. Essa ação força o usuário a inserir um PIN ou senha para desbloquear o dispositivo. 
    
5. Configurar uma **agenda**: Insira o número de dias (0 a 365) após a não conformidade para disparar a ação nos dispositivos dos usuários. Após esse período de carência, você pode impor uma política de [acesso condicional](conditional-access-intune-common-ways-use.md) . Se você inserir **0** (zero) número de dias, o acesso condicional entrará em vigor **imediatamente**. Por exemplo, se um dispositivo não for compatível, use o acesso condicional para bloquear o acesso ao email, ao SharePoint e a outros recursos da organização imediatamente.

    Quando você cria uma política de conformidade, a ação **Marcar dispositivo não compatível** é criada automaticamente e definida automaticamente como **0** dias (imediatamente). Com essa ação, quando o dispositivo faz check-in, o dispositivo é avaliado como não compatível imediatamente. Se também estiver usando o acesso condicional, o acesso condicional é ativado imediatamente. Se você quiser permitir um período de carência, altere o **agendamento** na ação **Marcar dispositivo** em não conformidade.
    
    Em sua política de conformidade, por exemplo, você também deseja notificar o usuário. Você pode adicionar a ação **Enviar email para o usuário final** . Nessa ação **Enviar email** , você define o **agendamento** como 2 dias. Se o dispositivo ou usuário final ainda for avaliado como não compatível no dia 2, seu email será enviado no dia 2. Se você quiser enviar um email ao usuário novamente no dia 5 de não conformidade, adicione outra ação e defina o **agendamento** como 5 dias.

    Para obter mais informações sobre conformidade e as ações internas, consulte a [visão geral de conformidade](device-compliance-get-started.md).

6. Quando terminar, selecione **Adicionar** > **OK** para guardar as alterações.

## <a name="next-steps"></a>Passos seguintes

[Monitorizar as políticas](compliance-policy-monitor.md).
