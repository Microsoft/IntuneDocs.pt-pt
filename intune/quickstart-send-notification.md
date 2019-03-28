---
title: 'Guia de Início Rápido: enviar notificações para dispositivos não conformes'
titlesuffix: Microsoft Intune
description: Neste guia de início rápido, irá utilizar o Microsoft Intune para enviar notificações por e-mail para dispositivos não conformes.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/26/2019
ms.topic: quickstart
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a1b89f2d-7937-46bb-926b-b05f6fa9c749
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c35f16eef9d7e62d5148cce7bd772703d6581d7d
ms.sourcegitcommit: d38ca1bf44e17211097aea481e00b6c1e87effae
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/27/2019
ms.locfileid: "58514323"
---
# <a name="quickstart-send-notifications-to-noncompliant-devices"></a>Início rápido: Send notifications to noncompliant devices (Enviar notificações para dispositivos que não estejam em conformidade)

Neste guia de início rápido, irá utilizar o Microsoft Intune para enviar uma notificação por e-mail para os membros da sua força de trabalho que tiverem dispositivos não conformes.

Por predefinição, quando o Intune deteta um dispositivo não conforme, este marca imediatamente o dispositivo como não conforme. O [acesso condicional](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) do Azure Active Directory (AAD) bloqueia então o dispositivo. Quando um dispositivo não está conforme, o Intune permite-lhe adicionar ações de não conformidade que lhe dão maior flexibilidade para decidir o que fazer. Por exemplo, pode conceder um período de tolerância aos utilizadores para que estes estejam em conformidade antes de bloquear dispositivos não conformes.

Uma das ações que pode tomar quando os dispositivos não estão em conformidade é enviar um e-mail para esses utilizadores finais. Também pode personalizar uma notificação por e-mail antes de a enviar para os utilizadores finais. Mais concretamente, pode personalizar os destinatários, o assunto e o corpo da mensagem, incluindo o logótipo da empresa e as informações de contacto. O Intune também incluirá detalhes sobre o dispositivo não conforme na notificação por e-mail.

Se não tiver uma subscrição do Intune, [inscreva-se numa conta de avaliação gratuita](free-trial-sign-up.md).

## <a name="prerequisites"></a>Pré-requisitos
- Quando utilizar políticas de conformidade do dispositivo para bloquear dispositivos dos recursos empresariais, tem de configurar o acesso condicional do AAD. Se já concluiu o guia de início rápido [Criar uma política de conformidade de dispositivo](quickstart-set-password-length-android.md), está a utilizar o Azure Active Directory. Para obter mais informações sobre o AAD, veja os artigos [Acesso condicional no Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) e [Formas comuns de utilizar o acesso condicional com o Intune](conditional-access-intune-common-ways-use.md).

## <a name="sign-in-to-intune"></a>Iniciar sessão no Intune

Inicie sessão no portal do [Intune](https://aka.ms/intuneportal) como [Administrador global](users-add.md#types-of-administrators) ou um [Administrador do Serviço](users-add.md#types-of-administrators) do Intune. 

## <a name="create-a-notification-message-template"></a>Criar um modelo de mensagem de notificação

Para enviar um e-mail aos seus utilizadores, crie um modelo de mensagem de notificação. Quando um dispositivo não estiver em conformidade, os detalhes que introduzir no modelo são apresentados no e-mail enviado aos utilizadores.

1. No Intune, selecione **Conformidade do dispositivo** > **Notificações** > **Criar notificação**. 
2. Introduza as seguintes informações:

   - **Nome**: *Administrador da Contoso*
   - **Assunto**: *Conformidade do dispositivo*
   - **Mensagem**: *O dispositivo não está atualmente a cumprir nossos requisitos de conformidade de organizações.*
   - **Cabeçalho do e-mail – incluir o logótipo da empresa**: Defina como **ativado** para mostrar o logótipo da sua organização.
   - **Rodapé do e-mail – incluir o nome da empresa**: Defina como **ativado** para mostrar o nome da sua organização.
   - **Rodapé do e-mail – incluir informações de contacto**: Defina como **ativado** para mostrar informações de contacto da sua organização.

   ![Exemplo de uma mensagem de notificação de conformidade no Intune](./media/quickstart-send-notification-01.png)

3. Quando terminar de adicionar as informações, selecione **Criar**. O Modelo de mensagem de notificação está pronto para ser utilizado.

    > [!NOTE]
    > Também pode editar um modelo de Notificação criado anteriormente.

Para obter detalhes sobre como definir o nome, as informações de contacto e o logótipo da sua empresa, veja [Informações e declaração de privacidade da empresa](company-portal-app.md#company-information-and-privacy-statement), [Informações de suporte](company-portal-app.md#support-information) e [Personalização da imagem corporativa da identidade da empresa](company-portal-app.md#company-identity-branding-customization). 

## <a name="add-a-noncompliance-policy"></a>Adicionar uma política de não conformidade

Quando cria uma política de conformidade do dispositivo, o Intune cria automaticamente uma ação de não conformidade. Quando um dispositivo não está a cumprir a política de conformidade, o Intune marca automaticamente o dispositivo como não conforme. Pode personalizar o intervalo de tempo durante o qual o dispositivo está marcado como não conforme. Também pode adicionar outra ação quando criar uma política de conformidade ou atualizar uma política de conformidade existente. 

Os seguintes passos descrevem como pode criar uma política de conformidade para dispositivos com o Windows 10.

1. No Intune, selecione **Conformidade do dispositivo**.
2. Selecione **Políticas** > **Criar Política**.
3. Introduza as seguintes informações:

   - **Nome**: *Conformidade do Windows 10*
   - **Descrição**: *Política de conformidade do Windows 10*
   - **Plataforma**: Windows 10 e posterior

4. Selecione **Definições** > **Segurança do Sistema** para apresentar as definições de segurança do dispositivo.
5. Defina a opção **Exigir uma palavra-passe para desbloquear os dispositivos móveis** para **Exigir**. Esta definição especifica quando deve ser exigido aos utilizadores que introduzam uma palavra-passe antes de ser concedido o acesso a informações nos respetivos dispositivos móveis. 
6. Defina a opção **Comprimento mínimo da palavra-passe** para **6**. Esta definição especifica o número mínimo de dígitos ou carateres na palavra-passe.

    ![Definições de Segurança do Sistema para criar uma nova política de conformidade](./media/quickstart-send-notification-02.png) 

7. Clique em **OK**, **OK** e **Criar** para criar a política de conformidade.
8. Selecione o nome da sua nova política: **Conformidade do Windows 10**.
9. Selecione **Propriedades** > **Ações para não conformidade** > **Adicionar**.
10. Na caixa pendente **Ação**, confirme se a opção **Enviar mensagem de e-mail ao utilizador final** está selecionada.
11. Selecione **Modelo de mensagem** > **Administrador da Contoso** > **Selecionar** para selecionar o modelo de mensagem que criou anteriormente neste tópico.
12. Selecione **OK** > **OK** > **Guardar** para guardar as alterações.

## <a name="assign-the-policy"></a>Atribuir a política

Pode atribuir a política de conformidade a um grupo específico de utilizadores ou a todos os utilizadores. Quando o Intune reconhecer que um dispositivo não é conforme, o utilizador será notificado de que terá de atualizar o dispositivo de modo a cumprir a política de conformidade. Os seguintes passos permitir-lhe-ão atribuir a política.

1. Selecione a política **Conformidade do Windows 10** que criou anteriormente.
2. Selecione **Atribuições**.
3. Na caixa pendente **Atribuir a**, selecione **Todos os Utilizadores**. Esta ação irá selecionar todos os utilizadores. Todos os utilizadores que tiverem um dispositivo com o **Windows 10 e posterior** que não cumpra esta política de conformidade serão notificados.

    > [!NOTE]
    > Pode incluir e excluir grupos ao atribuir políticas de conformidade.

4. Clique em **Guardar**.

Quando tiver criado e guardado a política com êxito, será apresentada na lista de **Conformidade do dispositivo – Políticas**. Repare se a opção **Atribuído** na lista está definida como **Sim**.

## <a name="next-steps"></a>Passos Seguintes

Neste guia de início rápido, utilizou o Intune para criar e atribuir uma política de conformidade aos dispositivos com o Windows 10 da sua força de trabalho para exigir uma palavra-passe de pelo menos seis carateres de comprimento. Para obter mais informações sobre como criar políticas de conformidade para dispositivos Windows, veja [Adicionar uma política de conformidade para dispositivos Windows no Intune](compliance-policy-create-windows.md).

Para seguir esta série de guias de início rápido do Intune, continue para o próximo guia de início rápido.

> [!div class="nextstepaction"]
> [Início rápido: Adicionar e atribuir uma aplicação de cliente](quickstart-add-assign-app.md)
