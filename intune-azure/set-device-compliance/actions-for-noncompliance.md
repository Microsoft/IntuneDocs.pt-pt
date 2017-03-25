---
title: "Ações de não conformidade"
titleSuffix: Intune Azure preview
description: "Pré-visualização do Azure no Intune: saiba como criar ações de não conformidade para dispositivos de não conformidade"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/13/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6d0e0c4b-a562-44f3-82a4-80eb688d4733
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: deea78dcea9ade031441bf12b388a862235a8e9c
ms.openlocfilehash: 16da087e741e335144266c838c0a91050bd7d520
ms.lasthandoff: 03/15/2017


---

# <a name="create-actions-for-non-compliance"></a>Criar Ações de não conformidade

As **Ações de não conformidade** permitem-lhe configurar uma sequência cronológica de ações que são aplicadas aos dispositivos que deixaram de estar em conformidade. Por exemplo, pode notificar os utilizadores dos dispositivos não conformes por e-mail ou bloquear o acesso destes dispositivos a recursos da empresa através do acesso condicional.

## <a name="use-case-scenario"></a>Cenário de caso de utilização

Por predefinição, assim que um dispositivo for reportado como não conforme por uma política de conformidade do dispositivo do Intune, o acesso condicional imediatamente bloqueia esse dispositivo e o utilizador recebe um e-mail com instruções para ficar conforme. As **Ações de não conformidade** dão-lhe mais flexibilidade para decidir o que fazer quando um dispositivo não está conforme. Por exemplo, pode decidir não bloquear o dispositivo de imediato e, em seguida, dar ao utilizador um período de tolerância para ficar conforme.

Existem dois tipos de ações:

-   Notificar o utilizador por e-mail

-   Bloquear o acesso a recursos da empresa através do acesso condicional

## <a name="notify-the-user-via-email"></a>Notificar o utilizador por e-mail

Pode escolher a partir de modelos de e-mail predefinidos pré-criados ou criar uma notificação de e-mail totalmente personalizada. Permitimos-lhe personalizar o assunto, o corpo de mensagem, incluindo o logótipo da empresa, as informações de contacto e os destinatários adicionais.

## <a name="block-corporate-resource-access-through-conditional-access"></a>Bloquear o acesso a recursos da empresa através do acesso condicional

Pode determinar um agendamento ao nível do número de dias em que o dispositivo deve estar impedido de aceder a recursos empresariais. Pode fazê-lo imediatamente, mas também pode dar ao utilizador um período de tolerância para este ficar em conformidade com as políticas de conformidade do dispositivo.

## <a name="before-you-begin"></a>Antes de começar

Tem de ter, pelo menos, uma política de conformidade do dispositivo criada para configurar as ações de não conformidade.

-   Aprenda a criar uma política de conformidade do dispositivo para:

    -   [Android](https://docs.microsoft.com/intune-azure/set-device-compliance/create-a-compliance-policy-for-android)

    -   [Android for Work](https://docs.microsoft.com/intune-azure/set-device-compliance/create-a-compliance-policy-for-android-for-work)

    -   [iOS](https://docs.microsoft.com/intune-azure/set-device-compliance/create-a-compliance-policy-for-ios)

    -   [Windows](https://docs.microsoft.com/intune-azure/set-device-compliance/create-a-compliance-policy-for-windows)

Tem de ter a configuração do acesso condicional de EMS pronta quando estiver a planear utilizar políticas de conformidade do dispositivo para bloquear a utilização dos recursos empresariais pelos dispositivos.

- Aprenda a [configurar o acesso condicional de EMS](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access).

Além disso, tem de ter um modelo de mensagem de notificação criado. O modelo de mensagem de notificação é utilizado mais tarde no processo de criação de ações de não conformidade para enviar e-mails aos seus utilizadores.

### <a name="to-add-a-notification-message-template"></a>Para adicionar um modelo de mensagem de notificação

No painel **Políticas de conformidade do dispositivo**:

1.  Em **Gerir**, escolha **Notificações**. É apresentado o painel Modelos de mensagem de notificação.

    ![Como adicionar um modelo de notificação](../media/afnc-1.png)

2.  Escolha **Adicionar** e, em seguida, terá de definir o seguinte:

    a.  Descrição

    b.  De

    c.  Assunto

    d.  Mensagem

    e.  Cabeçalho do e-mail – incluir o logótipo da empresa

    f.  Rodapé do e-mail – incluir o nome da empresa

    g.  Rodapé do e-mail – incluir informações de contacto

     ![O modelo de mensagem de notificação](../media/afnc-2.png)

Depois de adicionar as informações, pode clicar em **Criar**. O Modelo de mensagem de notificação está disponível para ser utilizado.

> [!NOTE] 
> Também pode editar um Modelo de notificação criado anteriormente.

## <a name="to-create-actions-for-non-compliance"></a>Para criar ações de não conformidade

Pode adicionar uma ação quando estiver a criar uma nova política de conformidade do dispositivo ou ao editar uma política de conformidade do dispositivo existente.

1.  No painel **Políticas de conformidade do dispositivo**, em **Gerir**, escolha **Políticas**.

2.  Escolha uma política de conformidade do dispositivo ao clicar nela.

    ![Políticas de conformidade](../media/afnc-3.png)

3.  É apresentado o painel **propriedades da política de conformidade do dispositivo**, escolha **Ações de não conformidade**.

4.  É apresentado o painel Ações de não conformidade, escolha **Adicionar** para especificar os parâmetros da ação.

    ![Painel Ações de não conformidade](../media/afnc-4.png)

Ações de não conformidade:

-   **Impor uma política de acesso condicional**

-   **Enviar e-mail ao utilizador final**

### <a name="enforce-conditional-access-policy"></a>Impor uma política de acesso condicional

Para adicionar esta ação de não conformidade:

1.  No painel **Ações de não conformidade**, escolha **Adicionar**.

2.  No painel **Parâmetros de ação**, selecione **Impor uma política de acesso condicional** na lista pendente Ação.

3.  Em **Agenda**, pode especificar o número de dias (0 a 255) para impor a política de acesso condicional. Se especificar **0** dias, significa que o acesso condicional terá de bloquear **imediatamente** o acesso aos recursos empresariais quando os dispositivos não estivem conformes com as políticas de conformidade do dispositivo.

    ![Agendar Ações de não conformidade](../media/afnc-5.png)

4.  Escolha **Adicionar** e, em seguida, escolha **OK** no painel **Ações**.

5.  No painel **Propriedades da política de conformidade do dispositivo**, escolha **Guardar**.

### <a name="send-e-mail-to-end-user"></a>Enviar e-mail ao utilizador final

Pode utilizar um modelo de e-mail para enviar aos utilizadores não conformes. Estes e-mails ajudam a impulsionar a conformidade do dispositivo em toda a organização.

Para adicionar esta ação de não conformidade:

1.  No painel **Ações de não conformidade**, escolha **Adicionar**.

2.  No painel **Parâmetros de ação**, selecione **Enviar e-mail ao utilizador final** na lista pendente Ação.

3.  Escolha um modelo de mensagem criado anteriormente, ao clicar no **Modelo de mensagem**. Pode ver o conteúdo do Modelo de mensagem e, em seguida, escolha **Selecionar**.

    ![Modelo de mensagem](../media/afnc-6.png)

> [!NOTE] 
> Pode ver o modelo de mensagem, mas não pode editá-lo. Se quiser editar o Modelo de mensagem, terá de voltar ao painel **Notificações**.

1.  Em **Agenda**, ao verificar uma não conformidade, introduza o número de dias após os quais o e-mail deve ser enviado aos utilizadores. Se especificar **0** dias, significa que o e-mail será enviado **imediatamente**.

2.  Escolha **Adicionar** e, em seguida, escolha **OK** no painel **Ações**.

3.  No painel **Propriedades da política de conformidade do dispositivo**, escolha **Guardar**.

