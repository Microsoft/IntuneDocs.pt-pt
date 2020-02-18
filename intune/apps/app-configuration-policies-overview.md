---
title: Políticas de configuração de aplicações para o Microsoft Intune
titleSuffix: ''
description: Saiba como utilizar as políticas de configuração de aplicações num iOS/iPadOS ou dispositivo Android no Microsoft Intune.
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
ms.openlocfilehash: a2cf53b26c1617ca7fc493c837e57823c23781bc
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/17/2020
ms.locfileid: "77414846"
---
# <a name="app-configuration-policies-for-microsoft-intune"></a>Políticas de configuração de aplicações para o Microsoft Intune

As políticas de configuração de aplicações podem ajudá-lo a eliminar problemas de configuração de aplicações, permitindo-lhe atribuir definições de configuração a uma política que é atribuída aos utilizadores finais antes de executar a aplicação. As definições são então fornecidas automaticamente quando a aplicação está configurada no dispositivo de utilizadores finais, e os utilizadores finais não precisam de tomar medidas. As definições de configuração são únicas para cada aplicação. 

Pode criar e utilizar políticas de configuração de apps para fornecer configurações de configuração tanto para aplicações iOS/iPadOS como Android. Estas configurações de configuração permitem que uma aplicação seja personalizada utilizando a configuração e a gestão da aplicação. As definições de política de configuração são utilizadas quando a aplicação verifica estas definições, tipicamente a primeira vez que a aplicação é executada. 

Uma definição de configuração da aplicação, por exemplo, pode exigir que especifique qualquer um dos seguintes detalhes:

- Um número de porta personalizado
- Definições de idioma
- Definições de segurança
- Definições de imagem corporativa tal como um logótipo de empresa

Se os utilizadores finais introduzirem estas definições, poderiam fazê-lo incorretamente. As políticas de configuração de aplicações podem ajudar a fornecer consistência em uma empresa e reduzir as chamadas de helpdesk de utilizadores finais tentando configurar configurações por si só. Ao utilizar políticas de configuração de aplicações, a adoção de novas aplicações pode ser mais fácil e rápida.

Os parâmetros de configuração disponíveis são, em última análise, decididos pelos desenvolvedores da app. A documentação do fornecedor de aplicações deve ser revista para ver se uma aplicação suporta a configuração e quais as configurações disponíveis. Para algumas aplicações, intune preencherá as configurações de configuração disponíveis. 

> [!NOTE]
> Na Managed Google Play Store, as aplicações que suportam a configuração serão marcadas como tal:
> 
> ![Screenshot de uma aplicação configurada](./media/app-configuration-policies-overview/configured-app.png)
>
> Só irá ver aplicações da [loja Managed Google Play](https://play.google.com/work), não da loja Google [Play](https://play.google.com/store/apps), quando utilizar dispositivos geridos como o Tipo de Inscrição para dispositivos Android. Gerido si mesmo google Play Store, que também pode conhecer como Android for Work (AfW) e Android Enterprise, são as aplicações no Perfil de Trabalho que contêm as versões da aplicação que suportam a configuração da aplicação.

Pode atribuir uma política de configuração de aplicações a um grupo de utilizadores finais e dispositivos, utilizando uma combinação de [atribuições de incluir e excluir](apps-inc-exl-assignments.md). Depois de adicionar uma política de configuração da aplicação, pode definir as atribuições dessa política. Ao definir as atribuições para a apólice, pode optar por incluir e excluir os [grupos](../fundamentals/groups-add.md) de utilizadores finais para os quais a apólice se aplica. Quando escolher incluir um ou mais grupos, poderá optar por selecionar grupos específicos para incluir ou selecionar grupos incorporados. Os grupos incorporados incluem **Todos os Utilizadores**, **Todos os Dispositivos** e **Todos os Utilizadores + Todos os Dispositivos**.

Tem duas opções para utilizar políticas de configuração de aplicações com intune:
- **Dispositivos geridos** – o dispositivo é gerido pelo Intune como o fornecedor de gestão de dispositivos móveis (MDM). A aplicação deve ser concebida para suportar a configuração da aplicação.
- **Aplicativos geridos** - Uma aplicação que foi desenvolvida para integrar o Intune App SDK. Isto é conhecido como Gestão de Aplicações Móveis sem inscrição[(MAM-WE).](app-management.md#mobile-application-management-mam-basics) Também pode embrulhar uma aplicação para implementar e apoiar o Intune App SDK. Para obter mais informações sobre o embrulho de uma aplicação, consulte [Prepare aplicações de linha de negócio para políticas de proteção de aplicações.](../developer/apps-prepare-mobile-application-management.md)

    > [!NOTE]
    > As aplicações geridas intune irão fazer o check-in com um intervalo de 30 minutos para o estado da Política de Configuração de Aplicações Intune, quando implementadas em conjunto com uma Política de Proteção de Aplicações Intune. Se uma Política de Proteção de Aplicações Intune não for atribuída ao utilizador, o intervalo de check-in da Política de Configuração de Aplicações Intune está definido para 720 minutos.

## <a name="apps-that-support-app-configuration"></a>Aplicações que suportam a configuração de aplicações

### <a name="managed-devices"></a>Dispositivos geridos
Pode utilizar políticas de configuração de aplicações para apps que o suportem. Para suportar a configuração da aplicação no Intune, as aplicações devem ser escritas para suportar a utilização de configurações de aplicações definidas pelo OS. Consulte o fornecedor da sua aplicação para obter detalhes sobre as chaves de config da aplicação que suportam.

### <a name="managed-apps"></a>Aplicações geridas
Pode preparar as suas aplicações de linha de negócio, incorporando o [Intune App SDK](../developer/app-sdk.md) na aplicação, ou envolvendo a app depois de ser desenvolvida utilizando a Ferramenta de Embrulho de [Aplicações Intune](../developer/apps-prepare-mobile-application-management.md). O Intune App SDK esforça-se por minimizar a quantidade de alterações de código exigidas pelo desenvolvedor da aplicação. Para obter mais informações, veja [Descrição geral do SDK da Aplicação Intune](../developer/app-sdk.md). Para uma comparação entre o Intune App SDK e a Ferramenta de Embrulho de Aplicações Intune, consulte [prepare aplicações de linha de negócio para políticas de proteção](../developer/apps-prepare-mobile-application-management.md#feature-comparison)de aplicações .

Selecionar **aplicações geridas** como o Tipo de Inscrição de **Dispositivos** refere-se especificamente a aplicações configuradas por políticas de configuração Intune num dispositivo que não está inscrito na gestão de dispositivos, enquanto **dispositivos geridos** se aplicam a aplicações implementadas através do canal MDM e são assim geridos pela Intune. Selecione a escolha adequada com base nestas descrições. 

![Tipo de inscrição do dispositivo](./media/app-configuration-policies-overview/device-enrollment-type.png)

> [!NOTE]
> Para aplicações multi-identidade, como o Microsoft Outlook, as preferências dos utilizadores podem ser consideradas. A Caixa de Entrada Focada, por exemplo, respeitará a definição do utilizador e não alterará a configuração. Outros parâmetros permitem controlar se um utilizador pode ou não alterar a definição. Para mais informações, consulte [o Outlook de Implementação para as definições de configuração de aplicações iOS/iPadOS e Android](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-configuration-with-microsoft-intune).

## <a name="validate-the-applied-app-configuration-policy"></a>Validar a política de configuração de aplicações aplicadas

Pode validar a política de configuração da aplicação utilizando os seguintes três métodos:

   1. Visivelmente no dispositivo. A aplicação direcionada exibe o comportamento aplicado na política de configuração de aplicações?
   2. Através de Registos de Diagnóstico (consulte a secção de Registos de Diagnóstico abaixo).
   3. No Portal Intune. A secção **monitora** de uma política pode fornecer o estatuto relevante:

      ![Primeira imagem do estado de instalação do dispositivo](./media/app-configuration-policies-overview/device-install-status-1.png)

      ![Segunda imagem do estado de instalação do dispositivo](./media/app-configuration-policies-overview/device-install-status-2.png)

      Além disso, em **Intune** -> **Dispositivos** -> **Todos os Dispositivos** do lado esquerdo do ecrã, a opção configuração da **aplicação** apresentará todas as políticas atribuídas e o seu estado:

      ![Screenshot da configuração da aplicação](./media/app-configuration-policies-overview/app-configuration.png)

## <a name="diagnostic-logs"></a>Registos de Diagnóstico

### <a name="ios-configuration-on-unmanaged-devices"></a>configuração do iOS em dispositivos não geridos

Pode validar a configuração do iOS/iPadOS com o **Intune Diagnostic Log** em dispositivos não geridos para configuração de aplicações geridas. Além dos passos abaixo, pode aceder a registos de aplicações geridos através do Microsoft Edge. Para mais informações, consulte [Use Microsoft Edge no iOS/iPadOS para aceder a registos de aplicações geridos](~/apps/manage-microsoft-edge.md#use-microsoft-edge-on-ios-to-access-managed-app-logs).

1. Caso ainda não estivesse instalado no dispositivo, descarregue e instale o **Microsoft Edge** a partir da App Store. Para mais informações, consulte [as aplicações protegidas microsoft Intune](apps-supported-intune-apps.md).
2. Lance o **Microsoft Edge** e selecione **cerca** de > **insonize a** partir da barra de navegação.
3. Clique em **Começar**.
4. Clique em **Registos de Partilha**.
5. Utilize a aplicação de correio à sua escolha para enviar o registo para si mesmo para que possam ser vistos no seu PC. 
6. Reveja **IntuneMAMDiagnostics.txt** no seu visualizador de ficheiros de texto.
7. Procure as `ApplicationConfiguration`. Os resultados serão os seguintes:

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

Os detalhes de configuração da sua aplicação devem corresponder às políticas de configuração da aplicação configuradas para o seu inquilino. 

![Config de aplicativo direcionado](./media/app-configuration-policies-overview/targeted-app-configuration-3.png)

### <a name="ios-configuration-on-managed-devices"></a>configuração do iOS em dispositivos geridos

Pode validar a configuração do iOS/iPadOS com o **Intune Diagnostic Log** em dispositivos geridos para a configuração da aplicação gerida.

1. Caso ainda não estivesse instalado no dispositivo, descarregue e instale o **Microsoft Edge** a partir da App Store. Para mais informações, consulte [as aplicações protegidas microsoft Intune](apps-supported-intune-apps.md).
2. Lance **o Microsoft Edge** e selecione **cerca** de > **insintonização** da barra de navegação.
3. Clique em **Começar**.
4. Clique em **Registos de Partilha**.
5. Utilize a aplicação de correio à sua escolha para enviar o registo para si mesmo para que possam ser vistos no seu PC. 
6. Reveja **IntuneMAMDiagnostics.txt** no seu visualizador de ficheiros de texto.
7. Procure as `AppConfig`. Os seus resultados devem corresponder às políticas de configuração da aplicação configuradas para o seu inquilino.

### <a name="android-configuration-on-managed-devices"></a>Configuração do Android em dispositivos geridos

Pode validar a configuração do iOS/iPadOS com o **Intune Diagnostic Log** em dispositivos geridos para a configuração da aplicação gerida.

Para recolher registos de um dispositivo Android, você ou o utilizador final devem descarregar os registos do dispositivo através de uma ligação USB (ou o equivalente do **File Explorer** no dispositivo). Eis os passos:

1. Ligue o dispositivo Android ao seu computador com o cabo USB.
2. No computador, procure um diretório com o nome do seu dispositivo. Nesse diretório, encontre `Android Device\Phone\Android\data\com.microsoft.windowsintune.companyportal`.
3. Na pasta `com.microsoft.windowsintune.companyportal`, abra a pasta Ficheiros e abra `OMADMLog_0`.
3. Procure `AppConfigHelper` para encontrar mensagens relacionadas com a configuração da aplicação. Os resultados serão semelhantes ao seguinte bloco de dados:

    `2019-06-17T20:09:29.1970000       INFO   AppConfigHelper     10888  02256  Returning app config JSON [{"ApplicationConfiguration":[{"Name":"com.microsoft.intune.mam.managedbrowser.BlockListURLs","Value":"https:\/\/www.aol.com"},{"Name":"com.microsoft.intune.mam.managedbrowser.bookmarks","Value":"Outlook Web|https:\/\/outlook.office.com||Bing|https:\/\/www.bing.com"},{"Name":"com.microsoft.intune.mam.managedbrowser.homepage","Value":"https:\/\/www.arstechnica.com"}]},{"ApplicationConfiguration":[{"Name":"IntuneMAMUPN","Value":"AdeleV@M365x935807.OnMicrosoft.com"},{"Name":"com.microsoft.outlook.Mail.NotificationsEnabled","Value":"false"},{"Name":"com.microsoft.outlook.Mail.NotificationsEnabled.UserChangeAllowed","Value":"false"}]}] for user User-875363642`
    
## <a name="graph-api-support-for-app-configuration"></a>Suporte da Graph API para configuração de aplicações

Pode utilizar a API do Graph para realizar tarefas de configuração de aplicações. Para mais detalhes, consulte [Graph API Reference MAM Targeted Config](https://docs.microsoft.com/graph/api/resources/intune-shared-targetedmanagedappconfiguration?view=graph-rest-beta). Para obter mais informações sobre Intune e Graph, consulte [Trabalhar com Intune no Microsoft Graph](https://docs.microsoft.com/graph/api/resources/intune-graph-overview?view=graph-rest-beta).

## <a name="troubleshooting"></a>Resolução de Problemas

### <a name="using-logs-to-show-a-configuration-parameter"></a>Usando registos para mostrar um parâmetro de configuração
Quando os registos mostram um parâmetro de configuração que se confirma estar a ser aplicado mas que não parece funcionar, pode haver um problema com a implementação da configuração pelo desenvolvedor da aplicação. Chegar primeiro a esse desenvolvedor de aplicações, ou verificar a sua base de conhecimentos, pode poupar-lhe uma chamada de suporte com a Microsoft. Se for um problema com a forma como a configuração está a ser tratada dentro de uma aplicação, teria de ser abordada numa futura versão atualizada dessa aplicação.

## <a name="next-steps"></a>Próximos passos

### <a name="managed-devices"></a>Dispositivos geridos

- Saiba como utilizar a configuração da aplicação com os seus dispositivos iOS/iPadOS.  Ver Adicionar políticas de configuração de [aplicativos para dispositivos iOS/iPadOS geridos](app-configuration-policies-use-ios.md).
- Saiba como utilizar a configuração de aplicações com os seus dispositivos Android.  Veja [Adicionar políticas de configuração de aplicações para dispositivos Android geridos](app-configuration-policies-use-android.md).

### <a name="managed-apps"></a>Aplicações geridas

- Saiba como utilizar a configuração de aplicações com aplicações geridas. Veja [Add app configuration policies for managed apps without device enrollment (Adicionar políticas de configuração de aplicações para aplicações geridas sem inscrição de dispositivos)](app-configuration-policies-managed-app.md).
