---
title: Adicionar políticas de configuração da aplicação para dispositivos Android geridos
titlesuffix: Microsoft Intune
description: Utilize políticas de configuração da aplicação no Microsoft Intune para disponibilizar definições quando os utilizadores executarem uma aplicação com perfil de trabalho do Android.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/21/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d0b6f3fe-2bd4-4518-a6fe-b9fd115ed5e0
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 599b31a30d1a2ab05e8a8c00e0ad704d2dd38b6c
ms.sourcegitcommit: 430b290474b11f9df87785b01edc178e6bae2049
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/05/2019
ms.locfileid: "57400085"
---
# <a name="add-app-configuration-policies-for-managed-android-devices"></a>Adicionar políticas de configuração da aplicação para dispositivos Android geridos

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Utilize políticas de configuração da aplicação no Microsoft Intune para disponibilizar definições para aplicações com perfil de trabalho do Android. O programador da aplicação tem de apresentar as definições de configuração de aplicações Android geridas para poder especificar as definições de configuração para a aplicação. Atribua a política de configuração de aplicações ao grupo de utilizadores para o qual pretende que as definições se apliquem.  As definições de política são utilizadas quando a aplicação as verificar, normalmente a primeira vez em que for executada.

> [!Note]  
> Nem todas as aplicações suportam a configuração de aplicações. Verifique junto do programador da aplicação para saber se este criou a aplicação de forma a suportar políticas de configuração da aplicação.

1. Inicie sessão no [Portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços** > **Intune**. O Intune encontra-se na secção **Monitorização + Gestão**.
3. Selecione a carga de trabalho **Aplicações do cliente**.
4. Selecione **Políticas de configuração da aplicação** no grupo **Gerir** e, em seguida, selecione **Adicionar**.
5. Defina os seguintes detalhes:
    - **Nome** – o nome do perfil que será apresentado no portal do Azure.
    - **Descrição** – a descrição do perfil que será apresentada no portal do Azure.
    - **Tipo de inscrição do dispositivo** – selecione **Dispositivos geridos**.
6. Selecione **Android** em **Plataforma**.
7. Selecione **Aplicação Associada** para escolher a aplicação para a qual pretende definir uma política de configuração da aplicação. Selecionar na lista de aplicações com perfil de trabalho do Android que aprovou e sincronizou com o Intune.
8. Selecione **Permissões**. Pode definir configurações com:
    - [Estruturador de configuração](#use-the-configuration-designer)
    - [Editor de JSON](#enter-the-json-editor)
9. Selecione **OK** e, em seguida, **Adicionar**.

## <a name="use-the-configuration-designer"></a>Utilizar o estruturador de configuração

Pode utilizar o estruturador de configuração para aplicações Android quando a aplicação foi projetada para oferecer suporte a definições de configuração. A configuração será aplicada aos dispositivos inscritos no Intune. O estruturador permite-lhe configurar valores de configuração específicos para as definições que uma aplicação apresenta.

Selecione **Adicionar** para selecionar a lista de definições de configuração que pretende especificar para a aplicação.  
Para cada chave e valor na configuração, defina:

  - **Tipo de valor**  
    O tipo de dados do valor de configuração. Para os tipos de valor Cadeia, pode optar por selecionar um perfil de certificado ou variável como o tipo de valor.
  - **Valor de configuração**  
    O valor da configuração. Se selecionar variável ou certificado como o tipo de valor, pode escolher a partir de uma lista de perfis de certificado ou variáveis na lista pendente do valor de configuração.  Se selecionar um certificado, o alias de certificado do certificado implementado no dispositivo será preenchido durante a execução.
    
### <a name="supported-variables-for-configuration-values"></a>Variáveis suportadas para valores de configuração

Pode escolher as seguintes opções, se selecionar a variável como o tipo de valor:

| Opção | Exemplo |
|----|----|
| Correio | john@contoso.com |
| Nome Principal de utilizador | john@contoso.com |
| UPN parcial | John |
| Domain | contoso.com |
| Nome de utilizador | John Doe |
| ID de conta | fc0dc142-71d8-4b12-bbea-bae2a8514c81 |
| ID de utilizador | 3ec2c00f-b125-4519-acf0-302ac3761822 |
| ID do dispositivo | b9841cd9-9843-405f-be28-b2265c59ef97 |

### <a name="allow-only-configured-organization-accounts-in-multi-identity-apps"></a>Permitir apenas contas de organização configuradas nas aplicações de várias identidades 

Para os dispositivos Android, utilize os seguintes pares chave/valor:

| **Chave** | com.microsoft.intune.mam.AllowedAccountUPNs |
|--------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Valores** | <ul><li>Um ou mais UPNs delimitados por <code>;</code>.</li><li>Apenas conta(s) permitidas são as contas de utilizador geridas definidas por esta chave.</li><li> Para os dispositivos inscritos no Intune, o token <code>{{userprincipalname}}</code> pode ser utilizado para representar a conta de utilizador inscrito.</li></ul> |

   > [!NOTE]
   > Tem de utilizar o Outlook para Android 2.2.222 ou posterior ao permitir apenas contas de organização configuradas com multi-identidade.<p></p>
   > Enquanto administrador do Microsoft Intune, pode controlar as contas de utilizadores que são adicionadas a aplicações do Microsoft Office em dispositivos geridos. Pode limitar o acesso exclusivamente a contas de utilizadores autorizadas e bloquear contas pessoais em dispositivos inscritos. As aplicações de apoio processam a configuração da aplicação e removem e bloqueiam contas não aprovadas.<p></p>
   > Para o Microsoft Word, Microsoft Excel, Microsoft PowerPoint, tem de utilizar a versão da aplicação 16.0.9327.1000 e posterior. 

## <a name="enter-the-json-editor"></a>Entrar no editor de JSON

Algumas definições de configuração em aplicações (tais como aquelas com tipos de Pacote) não podem ser configuradas com o estruturador de configuração. Tem de utilizar o editor de JSON para esses valores. As definições são fornecidas para aplicações automaticamente quando a aplicação é instalada.

1. Para o **Formato das definições de configuração**, selecione **Entrar no editor de JSON**.
2. No editor, pode definir valores JSON para as definições de configuração. Pode escolher **Transferir modelo JSON** para transferir um ficheiro de exemplo que pode configurar.
3. Selecione **OK** e, em seguida, **Adicionar**.

A política é criada e apresentada no painel da lista de políticas.

Quando a aplicação atribuída é executada num dispositivo, a mesma é executada com as definições que configurou na política de configuração de aplicações.

## <a name="preconfigure-the-permissions-grant-state-for-apps"></a>Pré-configurar o estado de concessão de permissões para aplicações

Também pode pré-configurar uma permissão para que as aplicações acedam às funcionalidades do dispositivo Android. Por predefinição, as aplicações Android que requerem permissões de dispositivos, tal como o acesso à localização ou à câmara do dispositivo, pedem aos utilizadores que aceitem ou neguem as permissões. Por exemplo, se uma aplicação utilizar o microfone do dispositivo, é pedido ao utilizador que conceda à aplicação permissão para utilizar o microfone.

1. Inicie sessão no [Portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços** > **Intune**. O Intune encontra-se na secção **Monitorização + Gestão**.
3. Selecione **Aplicações do cliente**.
3. Em **Gerir**, selecione **Políticas de configuração da aplicação** e, em seguida, selecione **Adicionar**.
4. Defina os seguintes detalhes:
    - **Nome**. O nome do perfil que será apresentado no portal do Azure.
    - **Descrição**. A descrição do perfil que será apresentada no portal do Azure.
    - **Tipo de inscrição do dispositivo**. Selecione **Dispositivos geridos**.
    - **Plataforma**. Selecione **Android**.
5. Selecione **Aplicação Associada** para escolher a aplicação para a qual pretende definir uma política de configuração. Selecionar na lista de aplicações com perfil de trabalho do Android que aprovou e sincronizou com o Intune.
6. Selecione **Permissões** e, em seguida, escolha **Adicionar**.
7. Selecione na lista de permissões de aplicações disponíveis e, em seguida, escolha **OK**.
8. Selecione uma opção para cada permissão a conceder com esta política:
    - **Pedido de confirmação**. Solicitar o utilizador a aceitar ou recusar.
    - **Conceder automaticamente**. Aprovar automaticamente sem notificar o utilizador.
    - **Negar automaticamente**. Negar automaticamente sem notificar o utilizador.
9. Para atribuir a política de configuração de aplicações, selecione a política de configuração de aplicações, **Atribuição** e, em seguida, **Selecionar grupos**.
10. Selecione os grupos de utilizadores a atribuir e, em seguida, escolha **Selecionar**.
11. Escolha **Guardar** para atribuir a política.

## <a name="next-steps"></a>Passos Seguintes

Continue a [atribuir](apps-deploy.md) e [monitorizar](apps-monitor.md) a aplicação.

