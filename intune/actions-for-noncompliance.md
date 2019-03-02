---
title: Mensagem de não conformidade e ações com o Microsoft Intune – Azure | Microsoft Docs
description: Crie um e-mail de notificação para enviar para os dispositivos não conformes. Adicione ações depois de um dispositivo ser marcado como não conforme, tais como adicionar um período de tolerância para obter conformidade, ou crie um agendamento para bloquear o acesso até o dispositivo ficar em conformidade. Faça isto com o Microsoft Intune no Azure.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/01/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 67d34d3c5ee6f964caeecf9e657563c421054971
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/02/2019
ms.locfileid: "57231099"
---
# <a name="automate-email-and-add-actions-for-noncompliant-devices-in-intune"></a>Automatizar o e-mail e adicionar ações para dispositivos não conformes no Intune

Para dispositivos que não cumprem as políticas de conformidade ou regras, pode adicionar **ações de não conformidade**. Esta funcionalidade configura uma sequência cronológica de ações, como o envio por email o utilizador final e muito mais.

## <a name="overview"></a>Descrição geral

Por predefinição, quando o Intune deteta um dispositivo não conforme, este marca imediatamente o dispositivo como não conforme. O [acesso condicional](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) do Azure Active Directory (AD) bloqueia então o dispositivo. Quando um dispositivo não estiver em conformidade, **ações de não conformidade** também oferece flexibilidade para decidir o que fazer. Por exemplo, não bloqueie o dispositivo de imediato e dê ao utilizador um período de tolerância para ficar conforme.

Existem vários tipos de ação:

- **Enviar e-mail ao utilizador final**: Personalize uma notificação por e-mail antes de os enviar para o utilizador final. Pode personalizar os destinatários, o assunto e o corpo da mensagem, incluindo o logótipo da empresa e as informações de contacto.

    Além disso, o Intune inclui detalhes sobre o dispositivo não conforme na notificação por e-mail.

- **Bloquear remotamente o dispositivo não conforme**: Para dispositivos que não estão em conformidades, pode emitir um bloqueio remoto. Em seguida, é pedido ao utilizador um PIN ou palavra-passe para desbloquear o dispositivo. Saiba mais sobre a funcionalidade [Bloqueio Remoto](device-remote-lock.md). 

- **Marcar dispositivos como não conformes**: Criar uma agenda (num número de dias) após o dispositivo é marcado como não conforme. Pode configurar a ação para entrar em vigor imediatamente ou dar ao utilizador um período de tolerância para este ficar em conformidade.

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

- Quando utilizar políticas de conformidade do dispositivo para bloquear dispositivos dos recursos empresariais, tem de configurar o acesso condicional do Azure AD. Veja os artigos [Acesso condicional no Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) ou [Formas comuns de utilizar o acesso condicional com o Intune](conditional-access-intune-common-ways-use.md) para obter orientação.

## <a name="create-a-notification-message-template"></a>Criar um modelo de mensagem de notificação

Para enviar um e-mail aos seus utilizadores, crie um modelo de mensagem de notificação. Quando um dispositivo não estiver em conformidade, os detalhes que introduzir no modelo são apresentados no e-mail enviado aos utilizadores.

1. No [portal do Azure](https://portal.azure.com), selecione **Todos os serviços**, filtre o **Intune** e selecione **Microsoft Intune**.
2. Selecione **Conformidade do dispositivo** > **Notificações**.
3. Selecione **Criar notificação**. Introduza as seguintes informações:

   - **Nome**
   - **Assunto**
   - **Mensagem**
   - **Cabeçalho do e-mail – incluir o logótipo da empresa**
   - **Rodapé do e-mail – incluir o nome da empresa**
   - **Rodapé do e-mail – incluir informações de contacto**

   ![Exemplo de uma mensagem de notificação de conformidade no Intune](./media/actionsfornoncompliance-1.PNG)

4. Quando terminar de adicionar as informações, selecione **Criar**. O Modelo de mensagem de notificação está pronto para ser utilizado. O logótipo que carregar como parte da imagem corporativa do Portal da empresa é utilizado para modelos de e-mail. Para obter mais informações sobre a imagem corporativa do Portal da Empresa, veja [Personalização da imagem corporativa da empresa](company-portal-app.md#company-identity-branding-customization).

> [!NOTE]
> Também pode alterar ou atualizar um modelo de notificação existente que criou anteriormente.

## <a name="add-actions-for-noncompliance"></a>Adicionar ações de não conformidade

Quando cria uma política de conformidade do dispositivo, o Intune cria automaticamente uma ação de não conformidade. Se um dispositivo não está a cumprir a política de conformidade, esta ação marca o dispositivo como não conforme. Pode personalizar o intervalo de tempo durante o qual o dispositivo está marcado como não conforme. Esta ação não pode ser removida.

Também pode adicionar outra ação quando criar uma política de conformidade ou atualizar uma política existente. 

1. No [portal do Azure](https://portal.azure.com), abra **Microsoft Intune** > **Conformidade do dispositivo**.
2. Selecione **Políticas**, selecione uma das suas políticas e, em seguida, selecione **Propriedades**. 

    Ainda não tem uma política? Crie uma política para [Android](compliance-policy-create-android.md), [iOS](compliance-policy-create-ios.md), [Windows](compliance-policy-create-windows.md) ou para outra plataforma.
  
    > [!NOTE]
    > Os dispositivos JAMF e dispositivos visados com grupos de dispositivos não conseguem receber ações de conformidade neste momento.

3. Selecione **Ações para não conformidade** > **Adicionar**.
4. Selecione a sua **Ação**: 

    - **Envie um email para os utilizadores finais**: Quando o dispositivo não está em conformidade, optar por enviar um e-mail ao utilizador. Além disso: 
    
         - Selecione o **Modelo de mensagem** que criou anteriormente
         - Introduza **Destinatários adicionais** ao selecionar grupos
    
    - **Bloquear remotamente o dispositivo não conforme**: Quando o dispositivo está em conformidade, bloquear o dispositivo. Esta ação força o utilizador introduza um PIN ou código de acesso para desbloquear o dispositivo. 
    
    - **Agenda**: Introduza o número de dias (0 a 365) após a não conformidade para acionar a ação nos dispositivos dos utilizadores. Depois deste período de tolerância, pode impor uma política de acesso condicional. Se introduzir **0** (zero) número de dias, em seguida, acesso condicional entra em vigor **imediatamente**. Por exemplo, pode bloquear o acesso aos recursos empresariais imediatamente se um dispositivo não estiver em conformidade.

5. Quando terminar, selecione **Adicionar** > **OK** para guardar as alterações.

## <a name="next-steps"></a>Passos Seguintes

[Monitorizar as suas políticas](compliance-policy-monitor.md).
