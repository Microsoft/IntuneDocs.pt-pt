---
title: Mensagem de não conformidade e ações com o Microsoft Intune – Azure | Microsoft Docs
description: Crie um e-mail de notificação para enviar para os dispositivos não conformes. Adicione ações depois de um dispositivo ser marcado como não conforme, tais como adicionar um período de tolerância para obter conformidade, ou crie um agendamento para bloquear o acesso até o dispositivo ficar em conformidade. Faça isto com o Microsoft Intune no Azure.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/07/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 3c8bc523f2796f8af7cb4801cdb13a60b7e2eb5d
ms.sourcegitcommit: 98b444468df3fb2a6e8977ce5eb9d238610d4398
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/07/2018
ms.locfileid: "37905738"
---
# <a name="automate-email-and-add-actions-for-noncompliant-devices---intune"></a>Automatizar o e-mail e adicionar ações para dispositivos não conformes – Intune

Existe uma funcionalidade de **Ações de não conformidade** que permite configurar uma sequência de ações ordenada cronologicamente. Estas ações aplicam-se aos dispositivos que não cumprem a sua política de conformidade. 

## <a name="overview"></a>Descrição geral
Por predefinição, quando o Intune deteta um dispositivo não conforme, este marca imediatamente o dispositivo como não conforme. O [acesso condicional](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) do Azure Active Directory (AD) bloqueia então o dispositivo. Quando um dispositivo não está conforme, as **ações de não conformidade** dão-lhe mais flexibilidade para decidir o que fazer. Por exemplo, não bloqueie o dispositivo de imediato e dê ao utilizador um período de tolerância para ficar conforme.

Existem dois tipos de ações:

- **Notificar os utilizadores finais por e-mail**: pode personalizar uma notificação por e-mail antes de a enviar para o utilizador final. Pode personalizar os destinatários, o assunto e o corpo da mensagem, incluindo o logótipo da empresa e as informações de contacto.

    Além disso, o Intune inclui detalhes sobre o dispositivo não conforme na notificação por e-mail.

- **Marcar dispositivos como não conformes**: crie um agendamento (ao nível do número de dias) após o dispositivo ser marcado como não conforme. Pode configurar a ação para entrar em vigor imediatamente ou dar ao utilizador um período de tolerância para este ficar em conformidade.

## <a name="before-you-begin"></a>Antes de começar

- Para configurar as ações de não conformidade, tem de ter pelo menos uma política de conformidade de dispositivos. Para criar uma política de conformidade de dispositivos, veja as seguintes plataformas:

  - [Android](compliance-policy-create-android.md)
  - [Perfis de trabalho do Android](compliance-policy-create-android-for-work.md)
  - [iOS](compliance-policy-create-ios.md)
  - [macOS](compliance-policy-create-mac-os.md)
  - [Windows](compliance-policy-create-windows.md)

- Quando utilizar políticas de conformidade do dispositivo para bloquear dispositivos dos recursos empresariais, tem de configurar o acesso condicional do Azure AD. Veja [Acesso condicional no Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) para obter orientações.

- Tem de criar um modelo de mensagem de notificação. Para enviar mensagens de e-mail para os seus utilizadores, utiliza-se este modelo para criar ações de não conformidade.

## <a name="create-a-notification-message-template"></a>Criar um modelo de mensagem de notificação

1. Inicie sessão no [portal do Azure](https://portal.azure.com) com as suas credenciais do Intune. 
2. Selecione **Todos os serviços**, filtre por **Intune** e selecione **Microsoft Intune**.
3. Selecione **Conformidade do dispositivo** e, em seguida, selecione **Notificações**. 
4. Selecione **Criar notificação** e introduza as seguintes informações:

   - Nome
   - Assunto
   - Mensagem
   - Cabeçalho do e-mail – incluir o logótipo da empresa
   - Rodapé do e-mail – incluir o nome da empresa
   - Rodapé do e-mail – incluir informações de contacto

   ![Exemplo de uma mensagem de notificação de conformidade no Intune](./media/actionsfornoncompliance-1.PNG)

Quando terminar de adicionar as informações, selecione **Criar**. O Modelo de mensagem de notificação está pronto para ser utilizado.

> [!NOTE]
> Também pode editar um Modelo de notificação criado anteriormente.

## <a name="add-actions-for-noncompliance"></a>Adicionar ações de não conformidade

Por predefinição, o Intune cria automaticamente uma ação de não conformidade. Quando um dispositivo não está a cumprir a política de conformidade, esta ação marca o dispositivo como não conforme. Pode personalizar o intervalo de tempo durante o qual o dispositivo está marcado como não conforme. Esta ação não pode ser removida.

Pode adicionar uma ação quando criar uma nova política de conformidade ou atualizar uma política de conformidade existente. 

1. No [portal do Azure](https://portal.azure.com), abra **Microsoft Intune** e selecione **Conformidade do dispositivo**.
2. Selecione **Políticas**, selecione uma das suas políticas e, em seguida, selecione **Propriedades**. 

  Ainda não tem uma política? Crie uma política para [Android](compliance-policy-create-android.md), [iOS](compliance-policy-create-ios.md), [Windows](compliance-policy-create-windows.md) ou para outra plataforma.
  
  > [!NOTE]
  > Os dispositivos JAMF e dispositivos visados com grupos de dispositivos não conseguem receber ações de conformidade neste momento.

3. Selecione **Ações de não conformidade** e, em seguida, selecione **Adicionar** para introduzir os parâmetros de ação. Pode escolher o modelo de mensagem criado anteriormente, adicionar outros destinatários e atualizar o agendamento do período de tolerância. Pode introduzir o número de dias (0 a 365) na agenda e, em seguida, pode impor as políticas de acesso condicional. Se introduzir **0** número de dias, o acesso condicional bloqueia **imediatamente** o acesso aos recursos empresariais.

4. Quando terminar, selecione **Adicionar** > **OK** para guardar as alterações.

## <a name="next-steps"></a>Próximos passos
Monitorize a atividade de conformidade do dispositivo através da execução de relatórios. Para obter orientações, veja [Como monitorizar a conformidade do dispositivo com o Intune](device-compliance-monitor.md).
