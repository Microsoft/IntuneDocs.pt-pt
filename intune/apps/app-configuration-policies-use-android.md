---
title: Adicionar políticas de configuração de aplicativo para dispositivos Android Enterprise gerenciados
titleSuffix: Microsoft Intune
description: Use as políticas de configuração de aplicativo no Microsoft Intune para fornecer configurações quando os usuários executam um aplicativo de Google Play gerenciado.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d0b6f3fe-2bd4-4518-a6fe-b9fd115ed5e0
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 59d93bed7bae2b757a4bd1e7b1dffc814629f6a1
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71731436"
---
# <a name="add-app-configuration-policies-for-managed-android-enterprise-devices"></a>Adicionar políticas de configuração de aplicativo para dispositivos Android Enterprise gerenciados

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

As políticas de configuração de aplicativo no Microsoft Intune fornecem configurações para aplicativos gerenciados Google Play em dispositivos Android Enterprise gerenciados. O desenvolvedor do aplicativo expõe as definições de configuração de aplicativo gerenciado por Android. O Intune usa essas configurações expostas para permitir que o administrador configure recursos para o aplicativo. A política de configuração de aplicativo é atribuída aos seus grupos de usuários. As configurações de política são usadas quando o aplicativo as verifica, normalmente na primeira vez em que o aplicativo é executado.

> [!NOTE]  
> Nem todas as aplicações suportam a configuração de aplicações. Consulte o desenvolvedor do aplicativo para ver se seu aplicativo dá suporte a políticas de configuração de aplicativo.

1. No [Intune](https://go.microsoft.com/fwlink/?linkid=2090973), selecione **aplicativos** > cliente**políticas** >  de configuração de aplicativo**Adicionar**.
2. Introduza as seguintes propriedades:

    - **Nome**: introduza um nome descritivo para a política. Atribua nomes às políticas de forma que possa identificá-las facilmente mais tarde. Por exemplo, um bom nome de política é a **política de aplicativo de trabalho do Android Enterprise nove para toda a empresa**.
    - **Descrição**: introduza uma descrição para o perfil. Esta definição é opcional, mas recomendada.
    - **Tipo de registro do dispositivo**: Selecione **Dispositivos geridos**.
    - **Plataforma**: Selecione **Android**.

3. Selecione **aplicativo associado**. Escolha o aplicativo para o qual você deseja definir uma política de configuração de aplicativo. Selecione na lista de aplicativos Google Play gerenciados que você aprovou e sincronizou com o Intune.
4. Selecione **Permissões**. Pode definir configurações com:

    - [Estruturador de configuração](#use-the-configuration-designer)
    - [Editor de JSON](#enter-the-json-editor)

5. Selecione **OK** > **Adicionar**.

## <a name="use-the-configuration-designer"></a>Utilizar o estruturador de configuração

Você pode usar o designer de configuração para aplicativos Google Play gerenciados quando o aplicativo é projetado para dar suporte a definições de configuração. A configuração se aplica a dispositivos registrados no Intune. O designer permite que você defina valores de configuração específicos para as configurações expostas pelo aplicativo.

1. Selecione **Adicionar**. Escolha a lista de definições de configuração que você deseja inserir para o aplicativo.

    Se você estiver usando o GMail ou nove trabalhos para seu aplicativo de email, consulte [configurações de dispositivo do Android Enterprise para configurar o email](../email-settings-android-enterprise.md) para obter mais informações sobre essas configurações.

2. Para cada chave e valor na configuração, defina:

    - **Tipo de valor**: O tipo de dados do valor de configuração. Para os tipos de valor Cadeia, pode optar por selecionar um perfil de certificado ou variável como o tipo de valor.
    - **Valor de configuração**: O valor da configuração. Se você selecionar variável ou certificado para o **tipo de valor**, escolha em uma lista de variáveis ou perfis de certificado. Se você escolher um certificado, o alias de certificado do certificado implantado no dispositivo será preenchido no tempo de execução.

### <a name="supported-variables-for-configuration-values"></a>Variáveis suportadas para valores de configuração

Pode escolher as seguintes opções, se selecionar a variável como o tipo de valor:

| Opção | Exemplo |
|----|----|
| Correio | john@contoso.com |
| Nome Principal de utilizador | john@contoso.com |
| UPN Parcial | joão |
| Domain | Contoso.com |
| Nome de utilizador | João Silva |
| ID de conta | fc0dc142-71d8-4b12-bbea-bae2a8514c81 |
| ID de utilizador | 3ec2c00f-b125-4519-acf0-302ac3761822 |
| ID do dispositivo | b9841cd9-9843-405f-be28-b2265c59ef97 |

### <a name="allow-only-configured-organization-accounts-in-multi-identity-apps"></a>Permitir apenas contas de organização configuradas nas aplicações de várias identidades 

Para os dispositivos Android, utilize os seguintes pares chave/valor:

| **Chave** | com.microsoft.intune.mam.AllowedAccountUPNs |
|---|---|
| **Valores** | <ul><li>Um ou mais UPNs delimitados por <code>;</code>.</li><li>Apenas conta(s) permitidas são as contas de utilizador geridas definidas por esta chave.</li><li> Para os dispositivos inscritos no Intune, o token <code>{{userprincipalname}}</code> pode ser utilizado para representar a conta de utilizador inscrito.</li></ul> |

   > [!NOTE]
   > Tem de utilizar o Outlook para Android 2.2.222 ou posterior ao permitir apenas contas de organização configuradas com multi-identidade.<p></p>
   > Como administrador de Microsoft Intune, você pode controlar quais contas de usuário são adicionadas a Microsoft Office aplicativos em dispositivos gerenciados. Pode limitar o acesso exclusivamente a contas de utilizadores autorizadas e bloquear contas pessoais em dispositivos inscritos. As aplicações de apoio processam a configuração da aplicação e removem e bloqueiam contas não aprovadas.<p></p>
   > Para o Microsoft Word, Microsoft Excel, Microsoft PowerPoint, tem de utilizar a versão da aplicação 16.0.9327.1000 e posterior. 

## <a name="enter-the-json-editor"></a>Entrar no editor de JSON

Algumas definições de configuração em aplicativos (como aplicativos com tipos de pacote) não podem ser configuradas com o designer de configuração. Use o editor de JSON para esses valores. As definições são fornecidas para aplicações automaticamente quando a aplicação é instalada.

1. Para o **Formato das definições de configuração**, selecione **Entrar no editor de JSON**.
2. No editor, pode definir valores JSON para as definições de configuração. Pode escolher **Transferir modelo JSON** para transferir um ficheiro de exemplo que pode configurar.
3. Selecione **OK** e, em seguida, **Adicionar**.

A política é criada e apresentada na lista.

Quando a aplicação atribuída é executada num dispositivo, a mesma é executada com as definições que configurou na política de configuração de aplicações.

## <a name="preconfigure-the-permissions-grant-state-for-apps"></a>Pré-configurar o estado de concessão de permissões para aplicações

Você também pode pré-configurar as permissões de aplicativo para acessar recursos do dispositivo Android. Por padrão, os aplicativos Android que exigem permissões de dispositivo, como o acesso ao local ou à câmera do dispositivo, solicitam que os usuários aceitem ou neguem permissões.

Por exemplo, um aplicativo usa o microfone do dispositivo. O usuário é solicitado a conceder a permissão do aplicativo para usar o microfone.

1. No [Intune](https://go.microsoft.com/fwlink/?linkid=2090973), selecione **aplicativos** > cliente**políticas** >  de configuração de aplicativo**Adicionar**.
2. Introduza as seguintes propriedades:

    - **Nome**: introduza um nome descritivo para a política. Atribua nomes às políticas de forma que possa identificá-las facilmente mais tarde. Por exemplo, um bom nome de política é a **política de aplicativo de permissões de prompt do Android Enterprise para toda a empresa**.
    - **Descrição**. introduza uma descrição para o perfil. Esta definição é opcional, mas recomendada.
    - **Tipo de registro do dispositivo**: Selecione **Dispositivos geridos**.
    - **Plataforma**: Selecione **Android**.

3. Selecione **aplicativo associado**. Escolha o aplicativo para o qual você deseja definir uma política de configuração. Selecione na lista de aplicativos de perfil de trabalho do Android que você aprovou e sincronizou com o Intune.
4. Selecione **permissões** > **Adicionar**. Na lista, selecione as permissões de aplicativo disponíveis > **OK**.
5. Selecione uma opção para cada permissão a conceder com esta política:
    - **Pedido de confirmação**. Solicitar o utilizador a aceitar ou recusar.
    - **Conceder automaticamente**. Aprovar automaticamente sem notificar o utilizador.
    - **Negar automaticamente**. Negar automaticamente sem notificar o utilizador.
6. Para atribuir a política de configuração de aplicativo, selecione a política de configuração de aplicativo > **atribuição** > **Selecionar grupos**. Escolha os grupos de usuários a serem atribuídos > **selecione**.
7. Escolha **Guardar** para atribuir a política.

## <a name="additional-information"></a>Informações adicionais

- [Atribuindo um aplicativo Google Play gerenciado para dispositivos Android Enterprise](apps-add-android-for-work.md#assigning-a-managed-google-play-app-to-android-enterprise-work-profile-devices)
- [Implantando definições de configuração de aplicativo do Outlook para iOS e Android](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-configuration-with-microsoft-intune)

## <a name="next-steps"></a>Passos seguintes

Continue a [atribuir](apps-deploy.md) e [monitorizar](apps-monitor.md) a aplicação.
