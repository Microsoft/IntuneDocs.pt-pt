---
title: Adicione políticas de configuração de aplicativos para dispositivos Android Enterprise geridos
titleSuffix: Microsoft Intune
description: Utilize as políticas de configuração de aplicações no Microsoft Intune para fornecer definições quando os utilizadores executam uma aplicação Gerida do Google Play.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/23/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d0b6f3fe-2bd4-4518-a6fe-b9fd115ed5e0
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 52c8d10f0b8d06d68d75450c3d708f910bc5ddd4
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/17/2020
ms.locfileid: "77415046"
---
# <a name="add-app-configuration-policies-for-managed-android-enterprise-devices"></a>Adicione políticas de configuração de aplicativos para dispositivos Android Enterprise geridos

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

As políticas de configuração de aplicações nas definições de fornecimento do Microsoft Intune para aplicações geridas do Google Play em dispositivos Android Enterprise geridos. O desenvolvedor de aplicações expõe as configurações de configuração de apps geridas pelo Android. Intune usa estas definições expostas para permitir que o administrador configure as funcionalidades para a aplicação. A política de configuração da aplicação é atribuída aos seus grupos de utilizadores. As definições de política são usadas quando a aplicação verifica as mesmas, tipicamente a primeira vez que a aplicação funciona.

> [!NOTE]  
> Nem todas as aplicações suportam a configuração de aplicações. Consulte o desenvolvedor de aplicações para ver se a sua aplicação suporta as políticas de configuração de aplicações.

1. Inscreva-se no centro de administração do [Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Escolha as **aplicações** > políticas de **configuração** de apps > **adicionar** > **dispositivos geridos**. Note que pode escolher entre **dispositivos geridos** e **aplicações geridas.** Para mais informações consulte apps que suportam a [configuração da aplicação](~/apps/app-configuration-policies-overview.md#apps-that-support-app-configuration).
3. Na página **Basics,** delineie os seguintes detalhes:
    - **Nome** – o nome do perfil que é apresentado no portal do Azure.
    - **Descrição** – a descrição do perfil que é apresentada no portal do Azure.
    - Tipo de **inscrição do dispositivo** - Esta definição está definida para **dispositivos geridos**.
4. Selecione **Android Enterprise** como **plataforma.**
5. Clique em **selecionar a aplicação** ao lado da **aplicação Targeted**. O painel de **aplicações Associado** é apresentado. 
6. No painel de **aplicações associado,** escolha a app gerida para se associar à política de configuração e clique EM **OK**.
7. Clique em **Seguir** para visualizar a página **Definições.**
8. Clique em **Adicionar** para exibir o painel de **permissões Adicionar.**
9. Clique nas permissões que pretende anular. As permissões concedidas anularão a política de "Permissões de aplicações padrão" para as aplicações selecionadas.
10. Detete o estado de **permissão** para cada permissão. Pode escolher entre **Prompt**, **auto grant**ou **Auto negar**. Para obter mais informações sobre permissões, consulte [as definições do Android Enterprise para marcar os dispositivos como conformes ou não conformes usando o Intune](~/protect/compliance-policy-create-android-for-work.md).
11. Na caixa de dropdown, selecione o formato de definições de **configuração**. Selecione um dos seguintes métodos para adicionar informações de configuração:
    - **Utilizar estruturador de configuração**
    - **Insira os dados da JSON**<br><br>
    Para obter detalhes sobre a utilização do estruturador de configuração, veja [Utilizar estruturador de configuração](#use-the-configuration-designer). Para mais detalhes sobre a introdução de dados XML, consulte [os dados do Enter JSON](#enter-json-data). 
12. Clique em **Seguir** para exibir a página **de Tarefas.**
13. Na caixa de dropdown ao lado da **Atribuição para**, selecione **grupos selecionados,** **Todos os utilizadores,** **Todos os dispositivos,** ou **todos os utilizadores e todas as pessoas se desloquem** para atribuir a política de configuração da aplicação.

    ![Captura de ecrã do separador Atribuições de política – Incluir](./media/app-configuration-policies-use-ios/app-config-policy01.png)

14. Selecione **todos os utilizadores** na caixa de dropdown.

    ![Captura de ecrã do menu pendente Atribuições de política – Todos os Utilizadores](./media/app-configuration-policies-use-ios/app-config-policy02.png)

15. Clique em **Selecionar grupos para excluir** para apresentar o painel relacionado.

    ![Screenshot de atribuições políticas - Selecione grupos para excluir o painel](./media/app-configuration-policies-use-ios/app-config-policy03.png)

16. Escolha os grupos que pretende excluir e, em seguida, clique em **Selecionar**.

    >[!NOTE]
    >Ao adicionar um grupo, se outro grupo já tiver sido incluído num determinado tipo de atribuição, o mesmo estará pré-selecionado e inalterável para outras atribuições de inclusão. Por conseguinte, esse grupo que foi utilizado não poderá ser utilizado como um grupo excluído.

17. Clique em **Seguir** para exibir a página **Review + criar.**
18. Clique **em Criar** para adicionar a política de configuração da aplicação ao Intune.

## <a name="use-the-configuration-designer"></a>Utilizar o estruturador de configuração

Pode utilizar o designer de configuração para aplicações geridas do Google Play quando a aplicação for concebida para suportar as definições de configuração. A configuração aplica-se aos dispositivos matriculados no Intune. O designer permite configurar valores de configuração específicos para as definições expostas pela aplicação.

1. Selecione **Adicionar**. Escolha a lista de definições de configuração que pretende introduzir para a aplicação.

    Se estiver a utilizar o GMail ou o Nine Work para a sua aplicação de e-mail, consulte [as definições do dispositivo Android Enterprise para configurar](../email-settings-android-enterprise.md) o email para obter mais informações sobre estas definições.

2. Para cada chave e valor na configuração, defina:

    - **Tipo de valor**: O tipo de dados do valor de configuração. Para os tipos de valor Cadeia, pode optar por selecionar um perfil de certificado ou variável como o tipo de valor.
    - Valor de **configuração**: O valor para a configuração. Se selecionar variável ou certificado para o **tipo Valor,** escolha entre uma lista de variáveis ou perfis de certificado. Se escolher um certificado, o pseudónimo do certificado implantado no dispositivo é povoado em tempo de execução.

### <a name="supported-variables-for-configuration-values"></a>Variáveis suportadas para valores de configuração

Pode escolher as seguintes opções, se selecionar a variável como o tipo de valor:

| Opção | Exemplo |
|----|----|
| Id do dispositivo AAD | dc0dc142-11d8-4b12-bfea-cae2a8514c82 |
| ID de conta | fc0dc142-71d8-4b12-bbea-bae2a8514c81 |
| ID de Dispositivo do Intune | b9841cd9-9843-405f-be28-b2265c59ef97 |
| Domain | contoso.com |
| Correio | john@contoso.com |
| UPN Parcial | joão |
| ID de Utilizador | 3ec2c00f-b125-4519-acf0-302ac3761822 |
| Nome de utilizador | João Silva |
| Nome Principal de utilizador | john@contoso.com |


### <a name="allow-only-configured-organization-accounts-in-multi-identity-apps"></a>Permitir apenas contas de organização configuradas nas aplicações de várias identidades 

Para os dispositivos Android, utilize os seguintes pares chave/valor:

| **Chave** | com.microsoft.intune.mam.AllowedAccountUPNs |
|---|---|
| **Valores** | <ul><li>Um ou mais UPNs delimitados por <code>;</code>.</li><li>Apenas conta(s) permitidas são as contas de utilizador geridas definidas por esta chave.</li><li> Para os dispositivos inscritos no Intune, o token <code>{{userprincipalname}}</code> pode ser utilizado para representar a conta de utilizador inscrito.</li></ul> |

   > [!NOTE]
   > Tem de utilizar o Outlook para Android 2.2.222 e, mais tarde, Word, Excel, PowerPoint para Android 16.0.9327.1000 e mais tarde ou OneDrive para Android 5.28 e mais tarde ao permitir apenas contas de organização configuradas com identidade multi-identidade.<p></p>
   > Como administrador da Microsoft Intune, pode controlar quais as contas de utilizador adicionadas às aplicações do Microsoft Office em dispositivos geridos. Pode limitar o acesso exclusivamente a contas de utilizadores autorizadas e bloquear contas pessoais em dispositivos inscritos. As aplicações de apoio processam a configuração da aplicação e removem e bloqueiam contas não aprovadas.<p></p>

## <a name="enter-json-data"></a>Insira os dados da JSON

Algumas configurações de configuração em apps (como apps com tipos de Bundle) não podem ser configuradas com o designer de configuração. Use o editor da JSON para esses valores. As definições são fornecidas para aplicações automaticamente quando a aplicação é instalada.

1. Para o **Formato das definições de configuração**, selecione **Entrar no editor de JSON**.
2. No editor, pode definir valores JSON para as definições de configuração. Pode escolher **Transferir modelo JSON** para transferir um ficheiro de exemplo que pode configurar.
3. Selecione **OK** e, em seguida, **Adicionar**.

A política é criada e apresentada na lista.

Quando a aplicação atribuída é executada num dispositivo, a mesma é executada com as definições que configurou na política de configuração de aplicações.

## <a name="preconfigure-the-permissions-grant-state-for-apps"></a>Pré-configurar o estado de concessão de permissões para aplicações

Também pode configurar permissões de aplicações para aceder às funcionalidades do dispositivo Android. Por padrão, as aplicações Android que requerem permissões de dispositivos, como o acesso à localização ou à câmara do dispositivo, levam os utilizadores a aceitar ou negar permissões.

Por exemplo, uma aplicação utiliza o microfone do dispositivo. O utilizador é solicitado a conceder a permissão da aplicação para usar o microfone.

1. No centro de administração do [Microsoft Endpoint Manager,](https://go.microsoft.com/fwlink/?linkid=2109431)selecione **Apps** > políticas de **configuração** de apps >  **adicionar** > **dispositivos geridos**.
2. Adicione as seguintes propriedades:

    - **Nome**: Introduza um nome descritivo para a apólice. Atribua nomes às políticas de forma que possa identificá-las facilmente mais tarde. Por exemplo, um bom nome de política é **Android Enterprise prontament e permissões políticas de aplicações para toda**a empresa .
    - **Descrição**. introduza uma descrição para o perfil. Esta definição é opcional, mas recomendada.
    - Tipo de **inscrição do dispositivo**: Esta definição está definida para **dispositivos geridos**.
    - **Plataforma**: Selecione **Android**.

3. Selecione **App Associada**. Escolha a aplicação que pretende definir uma política de configuração. Selecione na lista de aplicações de perfil de trabalho do Android que aprovou e sincronizou com intune.
4. Selecione **Permissões** > **Adicionar**. Na lista, selecione as permissões de aplicação disponíveis > **OK**.
5. Selecione uma opção para cada permissão a conceder com esta política:
    - **Pedido de confirmação**. Solicitar o utilizador a aceitar ou recusar.
    - **Conceder automaticamente**. Aprovar automaticamente sem notificar o utilizador.
    - **Negar automaticamente**. Negar automaticamente sem notificar o utilizador.
6. Para atribuir a política de configuração da aplicação, selecione a política de configuração da aplicação > **Assignment** > **Select groups**. Escolha os grupos de utilizador para atribuir > **Selecione**.
7. Escolha **Guardar** para atribuir a política.

## <a name="additional-information"></a>Informações adicionais

- [Atribuir uma aplicação gerida do Google Play a dispositivos Android Enterprise](apps-add-android-for-work.md#assigning-a-managed-google-play-app-to-android-enterprise-work-profile-devices)
- [Implementação de Outlook para configurações de configurações de aplicações iOS/iPadOS e Android](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-configuration-with-microsoft-intune)

## <a name="next-steps"></a>Próximos passos

Continue a [atribuir](apps-deploy.md) e [monitorizar](apps-monitor.md) a aplicação.
