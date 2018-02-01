---
title: "Ações de não conformidade com o Intune"
titleSuffix: Intune on Azure
description: "Saiba como criar ações de não conformidade com o Intune"
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 01/05/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6d0e0c4b-a562-44f3-82a4-80eb688d4733
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 4e45f5d3836fc33851c650703f713c03204df792
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/25/2018
---
# <a name="automate-actions-for-noncompliance"></a>Ações automáticas de não conformidade

As **ações de não conformidade** permitem-lhe configurar uma sequência cronológica de ações que são aplicadas aos dispositivos que não cumprem os critérios da política de conformidade. Por predefinição, quando é detetado que um dispositivo não cumpre os critérios da política de conformidade, o Intune marca-o imediatamente como não conforme e o Acesso Condicional do Azure AD bloqueia o dispositivo. As **ações de não conformidade** dão-lhe mais flexibilidade para decidir o que fazer quando um dispositivo não está conforme. Por exemplo, pode decidir não bloquear o dispositivo de imediato e, em seguida, dar ao utilizador um período de tolerância para ficar conforme.

Existem dois tipos de ações:

-   **Notificar os utilizadores finais por e-mail**: pode personalizar a sua notificação por e-mail antes de enviar para o utilizador final. O Intune permite personalizar os destinatários, o assunto e o corpo da mensagem, incluindo o logótipo da empresa, e as informações de contacto.
-   **Marcar dispositivos como não conformes**: pode determinar um agendamento ao nível do número de dias após os quais o dispositivo é marcado como não conforme. Pode configurar a ação para entrar em vigor imediatamente ou dar ao utilizador um período de tolerância para este ficar em conformidade com as políticas de conformidade do dispositivo.

## <a name="before-you-begin"></a>Antes de começar

- Tem de ter, pelo menos, uma política de conformidade do dispositivo criada para configurar as ações de não conformidade. Saiba como criar uma política de conformidade de dispositivos para as seguintes plataformas:

    -   [Android](compliance-policy-create-android.md)
    -   [Android for Work](compliance-policy-create-android-for-work.md)
    -   [iOS](compliance-policy-create-ios.md)
    -   [macOS](compliance-policy-create-mac-os.md)
    -   [Windows](compliance-policy-create-windows.md)

- Tem de ter a configuração do acesso condicional do Azure AD pronta quando estiver a planear utilizar políticas de conformidade do dispositivo para bloquear a utilização dos recursos empresariais pelos dispositivos. Aprenda a [configurar o acesso condicional de EMS](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access).

- Tem de ter um modelo de mensagem de notificação criado. O modelo de mensagem de notificação é utilizado mais tarde no processo de criação de ações de não conformidade para enviar e-mails aos seus utilizadores.

- Terá de configurar o Exchange Online para aceitar e-mails de *IntuneNotificationService@microsoft.com*, para permitir que o Intune envie a notificação de e-mail. Para obter mais informações, veja [Configure message delivery restrictions for a mailbox (Configurar restrições de entrega da mensagem para uma caixa de correio)](https://technet.microsoft.com/library/bb397214(v=exchg.160).aspx).

### <a name="to-create-a-notification-message-template"></a>Para criar um modelo de mensagem de notificação

1. Aceda ao [Intune no portal do Azure](https://portal.azure.com) e inicie sessão com as suas credenciais do Intune.
2. Selecione **Mais serviços** no menu à esquerda e, em seguida, escreva **Intune** no filtro da caixa de texto.
3. Selecione **Intune**
4. Selecione **Conformidade do dispositivo** e, em seguida, selecione **Notificações** na secção **Gerir**.
5. Escolha **Criar notificação** e introduza as seguintes informações:
    - Nome
    - Assunto
    - Mensagem
    - Cabeçalho do e-mail – incluir o logótipo da empresa
    - Rodapé do e-mail – incluir o nome da empresa
    - Rodapé do e-mail – incluir informações de contacto

   ![exemplo de modelo de mensagem de notificação](./media/actionsfornoncompliance-1.PNG)

Quando terminar de adicionar as informações, selecione **Criar**. O Modelo de mensagem de notificação está disponível para ser utilizado.

> [!NOTE] 
> Também pode editar um Modelo de notificação criado anteriormente.

## <a name="to-create-actions-for-non-compliance"></a>Para criar ações de não conformidade

> [!TIP]
> Por predefinição, o Intune fornece uma ação predefinida na secção de ações de não conformidade. Esta ação marca o dispositivo como não conforme após ser detetado que não cumpre os critérios da política de conformidade do dispositivo. Pode personalizar quando é que o dispositivo é marcado como não conforme após a deteção. Esta ação não pode ser removida.

Pode adicionar uma ação quando estiver a criar uma nova política de conformidade do dispositivo ou ao editar uma política de conformidade do dispositivo existente.

1.  Na carga de trabalho do Intune, no painel **Políticas de conformidade do dispositivo**, selecione **Políticas** na secção **Gerir**.
2.  Selecione uma política de conformidade do dispositivo ao clicar na mesma e, em seguida, selecione **Propriedades** na secção **Gerir**.
3.  No painel **propriedades da política de conformidade do dispositivo**, escolha **Ações de não conformidade**.
4.  No painel **Ações de não conformidade**, escolha **Adicionar** para especificar os parâmetros da ação. Pode escolher o modelo de mensagem criado anteriormente, os destinatários adicionais e o período de tolerância. Pode especificar o número de dias (0 a 365) na agenda e, em seguida, pode impor as políticas de acesso condicional. Se especificar **0** dias, o acesso condicional bloqueia **imediatamente** o acesso aos recursos empresariais quando os dispositivos não estivem conformes com as políticas de conformidade do dispositivo.
5.  Quando terminar de adicionar as suas informações, selecione **Adicionar** e, em seguida, **OK**.

## <a name="next-steps"></a>Próximos passos
Pode monitorizar a atividade de conformidade do dispositivo ao executar os relatórios disponíveis no painel Conformidade do dispositivo. Para obter mais informações, veja [Como monitorizar a conformidade do dispositivo com o Intune](device-compliance-monitor.md).

