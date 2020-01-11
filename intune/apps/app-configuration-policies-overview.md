---
title: Políticas de configuração de aplicações para o Microsoft Intune
titleSuffix: ''
description: Saiba como utilizar políticas de configuração de aplicações num dispositivo iOS ou Android no Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/06/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 834B4557-80A9-48C0-A72C-C98F6AF79708
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 800193921e608a0d0c29dad5cf85b8781e715441
ms.sourcegitcommit: 2506cdbfccefd42587a76f14ee50c3849dad1708
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/11/2020
ms.locfileid: "75885794"
---
# <a name="app-configuration-policies-for-microsoft-intune"></a>Políticas de configuração de aplicações para o Microsoft Intune

As políticas de configuração de aplicativo podem ajudá-lo a eliminar problemas de configuração de aplicativo, permitindo que você atribua definições de configuração a uma política atribuída aos usuários finais antes de executar o aplicativo. As configurações são então fornecidas automaticamente quando o aplicativo é configurado no dispositivo dos usuários finais e os usuários finais não precisam tomar medidas de ação. As definições de configuração são exclusivas para cada aplicativo. 

Você pode criar e usar políticas de configuração de aplicativo para fornecer definições de configuração para aplicativos iOS ou Android. Essas definições de configuração permitem que um aplicativo seja personalizado usando a configuração e o gerenciamento de aplicativos. As definições de política de configuração são usadas quando o aplicativo verifica essas configurações, normalmente na primeira vez em que o aplicativo é executado. 

Uma configuração de aplicativo, por exemplo, pode exigir que você especifique qualquer um dos seguintes detalhes:

- Um número de porta personalizado
- Definições de idioma
- Definições de segurança
- Definições de imagem corporativa tal como um logótipo de empresa

Se os usuários finais inserirem essas configurações em vez disso, eles poderão fazer isso incorretamente. As políticas de configuração de aplicativo podem ajudar a fornecer consistência em toda a empresa e a reduzir as chamadas de assistência técnica dos usuários finais que tentam definir as configurações por conta própria. Usando as políticas de configuração de aplicativo, a adoção de novos aplicativos pode ser mais fácil e rápida.

Os parâmetros de configuração disponíveis são, por fim, decididos pelos desenvolvedores do aplicativo. A documentação do fornecedor do aplicativo deve ser revisada para ver se um aplicativo dá suporte à configuração e quais configurações estão disponíveis. Para alguns aplicativos, o Intune preencherá as definições de configuração disponíveis. 

> [!NOTE]
> No Google Play Store gerenciado, os aplicativos que dão suporte à configuração serão marcados como tal:
> 
> ![Captura de tela de um aplicativo configurado](./media/app-configuration-policies-overview/configured-app.png)
>
> Você só verá aplicativos do [repositório de Google Play gerenciado](https://play.google.com/work), não do [armazenamento de Google Play](https://play.google.com/store/apps), ao usar dispositivos gerenciados como o tipo de registro para dispositivos Android. Google Play Store gerenciados, que você também pode saber como Android for Work (AfW) e Android Enterprise, são os aplicativos no perfil de trabalho que contêm as versões do aplicativo que dão suporte à configuração do aplicativo.

Você pode atribuir uma política de configuração de aplicativo a um grupo de usuários e dispositivos finais usando uma combinação de [atribuições de inclusão e exclusão](apps-inc-exl-assignments.md). Depois de adicionar uma política de configuração da aplicação, pode definir as atribuições dessa política. Ao definir as atribuições para a política, você pode optar por incluir e excluir os [grupos](../fundamentals/groups-add.md) de usuários finais aos quais a política se aplica. Quando escolher incluir um ou mais grupos, poderá optar por selecionar grupos específicos para incluir ou selecionar grupos incorporados. Os grupos incorporados incluem **Todos os Utilizadores**, **Todos os Dispositivos** e **Todos os Utilizadores + Todos os Dispositivos**.

Você tem duas opções para usar as políticas de configuração de aplicativo com o Intune:
- **Dispositivos geridos** – o dispositivo é gerido pelo Intune como o fornecedor de gestão de dispositivos móveis (MDM). O aplicativo deve ser projetado para dar suporte à configuração do aplicativo.
- **Aplicativos gerenciados** – um aplicativo que foi desenvolvido para integrar o SDK de aplicativos do Intune. Isso é conhecido como gerenciamento de aplicativo móvel sem registro ([Mam-nós](app-management.md#mobile-application-management-mam-basics)). Você também pode encapsular um aplicativo para implementar e dar suporte ao SDK de aplicativos do Intune. Para obter mais informações sobre como encapsular um aplicativo, consulte [preparar aplicativos de linha de negócios para políticas de proteção de aplicativo](../developer/apps-prepare-mobile-application-management.md).

    > [!NOTE]
    > Os aplicativos gerenciados do Intune irão fazer check-in com um intervalo de 30 minutos para o status da política de configuração de aplicativo do Intune, quando implantado em conjunto com uma política de Proteção de Aplicativo do Intune. Se uma política de Proteção de Aplicativo do Intune não for atribuída ao usuário, o intervalo de check-in da política de configuração de aplicativo do Intune será definido como 720 minutos.

## <a name="apps-that-support-app-configuration"></a>Aplicações que suportam a configuração de aplicações

### <a name="managed-devices"></a>Dispositivos geridos
Você pode usar políticas de configuração de aplicativo para aplicativos que dão suporte a ela. Para dar suporte à configuração de aplicativo no Intune, os aplicativos devem ser escritos para dar suporte ao uso de configurações de aplicativo, conforme definido pelo sistema operacional. Consulte o fornecedor do aplicativo para obter detalhes sobre quais chaves de configuração de aplicativo dão suporte.

### <a name="managed-apps"></a>Aplicações geridas
Você pode preparar seus aplicativos de linha de negócios incorporando o SDK do aplicativo do [Intune](../developer/app-sdk.md) no aplicativo ou encapsulando o aplicativo após ele ser desenvolvido usando a [ferramenta de disposição do aplicativo do Intune](../developer/apps-prepare-mobile-application-management.md). O SDK do aplicativo do Intune se esforça para minimizar a quantidade de alterações de código necessárias do desenvolvedor do aplicativo. Para obter mais informações, veja [Descrição geral do SDK da Aplicação Intune](../developer/app-sdk.md). Para obter uma comparação entre o SDK de aplicativo do Intune e a ferramenta de encapsulamento de aplicativos do Intune, consulte [preparar aplicativos de linha de negócios para políticas de proteção de aplicativo](../developer/apps-prepare-mobile-application-management.md#feature-comparison).

A seleção de **aplicativos gerenciados** como o **tipo de registro de dispositivo** se refere especificamente a aplicativos configurados pelas políticas de configuração do Intune em um dispositivo que não está registrado no gerenciamento de dispositivos, enquanto os **dispositivos gerenciados** se aplicam a aplicativos implantados por meio do canal MDM e, portanto, são gerenciados pelo Intune. Selecione a opção apropriada com base nessas descrições. 

![Tipo de registro do dispositivo](./media/app-configuration-policies-overview/device-enrollment-type.png)

> [!NOTE]
> Para aplicativos de várias identidades, como o Microsoft Outlook, as preferências do usuário podem ser consideradas. A caixa de entrada focada, por exemplo, respeitará a configuração do usuário e não alterará a configuração. Outros parâmetros permitem controlar se um usuário pode ou não alterar a configuração. Para obter mais informações, consulte [implantando definições de configuração de aplicativo do Outlook para IOS e Android](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-configuration-with-microsoft-intune).

## <a name="validate-the-applied-app-configuration-policy"></a>Validar a política de configuração de aplicativo aplicada

Você pode validar a política de configuração de aplicativo usando os três métodos a seguir:

   1. Visivelmente no dispositivo. O aplicativo de destino está apresentando o comportamento aplicado na política de configuração de aplicativo?
   2. Por meio dos logs de diagnóstico (consulte a seção logs de diagnóstico abaixo).
   3. No portal do Intune. A seção **Monitor** de uma política pode fornecer o status relevante:

      ![Primeira captura de tela do status de instalação do dispositivo](./media/app-configuration-policies-overview/device-install-status-1.png)

      ![Segunda captura de tela do status de instalação do dispositivo](./media/app-configuration-policies-overview/device-install-status-2.png)

      Além disso, em **dispositivos** -> do **Intune** -> **todos os dispositivos** no lado esquerdo da tela, a opção de **configuração de aplicativo** exibirá todas as políticas atribuídas e seu estado:

      ![Captura de tela da configuração do aplicativo](./media/app-configuration-policies-overview/app-configuration.png)

## <a name="diagnostic-logs"></a>Registos de diagnóstico

### <a name="ios-configuration-on-unmanaged-devices"></a>configuração do iOS em dispositivos não gerenciados

Você pode validar a configuração do iOS com o **log de diagnóstico do Intune** em dispositivos não gerenciados para a configuração do aplicativo gerenciado. Além das etapas a seguir, você pode acessar logs de aplicativo gerenciado usando o Microsoft Edge. Para obter mais informações, consulte [usar o Microsoft Edge no Ios para acessar logs de aplicativo gerenciado](~/apps/manage-microsoft-edge.md#use-microsoft-edge-on-ios-to-access-managed-app-logs).

1. Se ainda não estiver instalado no dispositivo, baixe e instale o **Intune Managed browser** da loja de aplicativos. Para obter mais informações, consulte [Microsoft Intune aplicativos protegidos](apps-supported-intune-apps.md).
2. Inicie o **Intune Managed browser** e selecione **cerca** de > **intunehelp** na barra de navegação.
3. Clique em **Get Started** (Começar).
4. Clique em **compartilhar logs**.
5. Use o aplicativo de email de sua escolha para enviar o log para você mesmo para que eles possam ser exibidos em seu computador. 
6. Examine o **IntuneMAMDiagnostics. txt** no Visualizador de arquivos de texto.
7. Procure as `ApplicationConfiguration`. Os resultados se parecerão com o seguinte:

    ``` JSON
        {
            (
                {
                    Name = "com.microsoft.intune.mam.managedbrowser.BlockListURLs";
                    Value = "https://www.aol.com";
                },
                {
                    Name = "com.microsoft.intune.mam.managedbrowser.bookmarks";
                    Value = "Outlook Web|https://outlook.office.com||Bing|https://www.bing.com";
                }
            );
        },
        {
            ApplicationConfiguration =             
            (
                {
                Name = IntuneMAMUPN;
                Value = "CMARScrubbedM:13c45c42712a47a1739577e5c92b5bc86c3b44fd9a27aeec3f32857f69ddef79cbb988a92f8241af6df8b3ced7d5ce06e2d23c33639ddc2ca8ad8d9947385f8a";
                },
                {
                Name = "com.microsoft.outlook.Mail.NotificationsEnabled";
                Value = false;
                }
            );
        }
    ```

Os detalhes de configuração do aplicativo devem corresponder às políticas de configuração de aplicativo configuradas para seu locatário. 

![Configuração do aplicativo de destino](./media/app-configuration-policies-overview/targeted-app-configuration-3.png)

### <a name="ios-configuration-on-managed-devices"></a>configuração do iOS em dispositivos gerenciados

Você pode validar a configuração do iOS com o **log de diagnóstico do Intune** em dispositivos gerenciados para a configuração do aplicativo gerenciado.

1. Se ainda não estiver instalado no dispositivo, baixe e instale o **Intune Managed browser** da loja de aplicativos. Para obter mais informações, consulte [Microsoft Intune aplicativos protegidos](apps-supported-intune-apps.md).
2. Inicie o **Intune Managed browser** e selecione **cerca** de > **intunehelp** na barra de navegação.
3. Clique em **Get Started** (Começar).
4. Clique em **compartilhar logs**.
5. Use o aplicativo de email de sua escolha para enviar o log para você mesmo para que eles possam ser exibidos em seu computador. 
6. Examine o **IntuneMAMDiagnostics. txt** no Visualizador de arquivos de texto.
7. Procure as `AppConfig`. Os resultados devem corresponder às políticas de configuração de aplicativo configuradas para seu locatário.

### <a name="android-configuration-on-managed-devices"></a>Configuração do Android em dispositivos gerenciados

Você pode validar a configuração do iOS com o **log de diagnóstico do Intune** em dispositivos gerenciados para a configuração do aplicativo gerenciado.

Para coletar logs de um dispositivo Android, você ou o usuário final deve baixar os logs do dispositivo por meio de uma conexão USB (ou o **Explorador de arquivos** equivalente no dispositivo). Eis os passos:

1. Conecte o dispositivo Android ao computador com o cabo USB.
2. No computador, procure um diretório com o nome do seu dispositivo. Nesse diretório, localize `Android Device\Phone\Android\data\com.microsoft.windowsintune.companyportal`.
3. Na pasta `com.microsoft.windowsintune.companyportal`, abra a pasta arquivos e abra `OMADMLog_0`.
3. Pesquise `AppConfigHelper` para localizar mensagens relacionadas à configuração do aplicativo. Os resultados serão semelhantes ao seguinte bloco de dados:

    `2019-06-17T20:09:29.1970000       INFO   AppConfigHelper     10888  02256  Returning app config JSON [{"ApplicationConfiguration":[{"Name":"com.microsoft.intune.mam.managedbrowser.BlockListURLs","Value":"https:\/\/www.aol.com"},{"Name":"com.microsoft.intune.mam.managedbrowser.bookmarks","Value":"Outlook Web|https:\/\/outlook.office.com||Bing|https:\/\/www.bing.com"},{"Name":"com.microsoft.intune.mam.managedbrowser.homepage","Value":"https:\/\/www.arstechnica.com"}]},{"ApplicationConfiguration":[{"Name":"IntuneMAMUPN","Value":"AdeleV@M365x935807.OnMicrosoft.com"},{"Name":"com.microsoft.outlook.Mail.NotificationsEnabled","Value":"false"},{"Name":"com.microsoft.outlook.Mail.NotificationsEnabled.UserChangeAllowed","Value":"false"}]}] for user User-875363642`
    
## <a name="graph-api-support-for-app-configuration"></a>Suporte da Graph API para configuração de aplicações

Você pode usar API do Graph para realizar tarefas de configuração de aplicativo. Para obter detalhes, consulte [configuração de destino de Mam de API do Graph de referência](https://docs.microsoft.com/graph/api/resources/intune-shared-targetedmanagedappconfiguration?view=graph-rest-beta). Para obter mais informações sobre o Intune e o Graph, consulte [trabalhando com o Intune no Microsoft Graph](https://docs.microsoft.com/graph/api/resources/intune-graph-overview?view=graph-rest-beta).

## <a name="troubleshooting"></a>Resolução de Problemas

### <a name="using-logs-to-show-a-configuration-parameter"></a>Usando logs para mostrar um parâmetro de configuração
Quando os logs mostram um parâmetro de configuração que é confirmado para ser aplicado, mas não parece funcionar, pode haver um problema com a implementação da configuração pelo desenvolvedor do aplicativo. Entrar em contato com esse desenvolvedor de aplicativos primeiro ou verificar sua base de dados de conhecimento pode poupar a você uma chamada de suporte com a Microsoft. Se for um problema de como a configuração está sendo tratada em um aplicativo, ele precisaria ser resolvido em uma versão atualizada futura do aplicativo.

## <a name="next-steps"></a>Próximos passos

### <a name="managed-devices"></a>Dispositivos geridos

- Saiba como utilizar a configuração de aplicações com os seus dispositivos iOS.  Consulte [Adicionar políticas de configuração de aplicativo para dispositivos IOS gerenciados](app-configuration-policies-use-ios.md).
- Saiba como utilizar a configuração de aplicações com os seus dispositivos Android.  Veja [Adicionar políticas de configuração de aplicações para dispositivos Android geridos](app-configuration-policies-use-android.md).

### <a name="managed-apps"></a>Aplicações geridas

- Saiba como utilizar a configuração de aplicações com aplicações geridas. Veja [Add app configuration policies for managed apps without device enrollment (Adicionar políticas de configuração de aplicações para aplicações geridas sem inscrição de dispositivos)](app-configuration-policies-managed-app.md).
