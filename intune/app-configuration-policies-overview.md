---
title: Políticas de configuração de aplicações para o Microsoft Intune
titleSuffix: ''
description: Saiba como utilizar políticas de configuração de aplicações num dispositivo iOS ou Android no Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/28/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 834B4557-80A9-48C0-A72C-C98F6AF79708
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: cda0453009855d96e7c13e170ba908479a0773ea
ms.sourcegitcommit: 513e805bbea8bf652c2901dfc5460e34946077df
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/29/2019
ms.locfileid: "70160516"
---
# <a name="app-configuration-policies-for-microsoft-intune"></a>Políticas de configuração de aplicações para o Microsoft Intune

As políticas de configuração de aplicativo podem ajudá-lo a eliminar problemas de configuração de aplicativo, permitindo que você atribua definições de configuração a uma política atribuída aos usuários finais antes de executar o aplicativo. As configurações são então fornecidas automaticamente quando o aplicativo é configurado no dispositivo dos usuários finais e os usuários finais não precisam tomar medidas de ação. As definições de configuração são exclusivas para cada aplicativo. 

Você pode criar e usar políticas de configuração de aplicativo para fornecer definições de configuração para aplicativos iOS ou Android. Essas definições de configuração permitem que um aplicativo seja personalizado usando uma [abordagem padrão do setor](https://www.appconfig.org/) para configuração e gerenciamento de aplicativos. As definições de política de configuração são usadas quando o aplicativo verifica essas configurações, normalmente na primeira vez em que o aplicativo é executado. 

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
> ![Captura de tela de um aplicativo configurado](./media/app-configuration-policy-overview/configured-app.png)
>
> Você só verá aplicativos do [repositório de Google Play gerenciado](https://play.google.com/work), não do [armazenamento de Google Play](https://play.google.com/store/apps), ao usar dispositivos gerenciados como o tipo de registro para dispositivos Android. Google Play Store gerenciados, que você também pode saber como Android for Work (AfW) e Android Enterprise, são os aplicativos no perfil de trabalho que contêm as versões do aplicativo que dão suporte à configuração do aplicativo.

Você pode atribuir uma política de configuração de aplicativo a um grupo de usuários e dispositivos finais usando uma combinação de [atribuições de inclusão e exclusão](apps-inc-exl-assignments.md). Depois de adicionar uma política de configuração da aplicação, pode definir as atribuições dessa política. Ao definir as atribuições para a política, você pode optar por incluir e excluir os [grupos](groups-add.md) de usuários finais aos quais a política se aplica. Quando escolher incluir um ou mais grupos, poderá optar por selecionar grupos específicos para incluir ou selecionar grupos incorporados. Os grupos incorporados incluem **Todos os Utilizadores**, **Todos os Dispositivos** e **Todos os Utilizadores + Todos os Dispositivos**.

Você tem duas opções para usar as políticas de configuração de aplicativo com o Intune:
- **Dispositivos geridos** – o dispositivo é gerido pelo Intune como o fornecedor de gestão de dispositivos móveis (MDM). O aplicativo deve ser projetado para dar suporte à configuração do aplicativo.
- **Aplicativos gerenciados** – um aplicativo que foi desenvolvido para integrar o SDK de aplicativos do Intune. Isso é conhecido como gerenciamento de aplicativo móvel sem registro ([Mam-nós](app-management.md#mobile-application-management-mam-basics)). Você também pode encapsular um aplicativo para implementar e dar suporte ao SDK de aplicativos do Intune. Para obter mais informações sobre como encapsular um aplicativo, consulte [preparar aplicativos de linha de negócios para políticas de proteção de aplicativo](apps-prepare-mobile-application-management.md).

    > [!NOTE]
    > Os aplicativos gerenciados do Intune irão fazer check-in com um intervalo de 30 minutos para o status da política de configuração de aplicativo do Intune, quando implantado em conjunto com uma política de Proteção de Aplicativo do Intune. Se uma política de Proteção de Aplicativo do Intune não for atribuída ao usuário, o intervalo de check-in da política de configuração de aplicativo do Intune será definido como 720 minutos.

## <a name="apps-that-support-app-configuration"></a>Aplicações que suportam a configuração de aplicações

### <a name="managed-devices"></a>Dispositivos geridos
Você pode usar políticas de configuração de aplicativo para aplicativos que dão suporte a ela. Para dar suporte à configuração de aplicativo no Intune, os aplicativos devem ser escritos para dar suporte ao uso de configurações de aplicativo conforme definido pela [comunidade AppConfig](https://www.appconfig.org/members). Consulte o seu fornecedor de aplicações para obter detalhes.

### <a name="managed-apps"></a>Aplicações geridas
Você pode preparar seus aplicativos de linha de negócios incorporando o SDK do aplicativo do [Intune](app-sdk.md) no aplicativo ou encapsulando o aplicativo após ele ser desenvolvido usando a [ferramenta de disposição do aplicativo do Intune](apps-prepare-mobile-application-management.md). O SDK do aplicativo do Intune se esforça para minimizar a quantidade de alterações de código necessárias do desenvolvedor do aplicativo. Para obter mais informações, veja [Descrição geral do SDK da Aplicação Intune](app-sdk.md). Para obter uma comparação entre o SDK de aplicativo do Intune e a ferramenta de encapsulamento de aplicativos do Intune, consulte [preparar aplicativos de linha de negócios para políticas de proteção de aplicativo](apps-prepare-mobile-application-management.md#feature-comparison).

A seleção de **aplicativos gerenciados** como o **tipo de registro de dispositivo** se refere especificamente a aplicativos configurados pelas políticas de configuração do Intune em um dispositivo que não está registrado no gerenciamento de dispositivos, enquanto os **dispositivos gerenciados** se aplicam a aplicativos implantados por meio do canal MDM e, portanto, são gerenciados pelo Intune. Selecione a opção apropriada com base nessas descrições. 

![Tipo de registro do dispositivo](./media/app-configuration-policy-overview/device-enrollment-type.png)

> [!NOTE]
> Para aplicativos de várias identidades, como o Microsoft Outlook, as preferências do usuário podem ser consideradas. A caixa de entrada focada, por exemplo, respeitará a configuração do usuário e não alterará a configuração. Outros parâmetros permitem controlar se um usuário pode ou não alterar a configuração. Para obter mais informações, consulte Implantando [definições de configuração de aplicativo do Outlook para IOS e Android](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-configuration-with-microsoft-intune).

## <a name="validate-the-applied-app-configuration-policy"></a>Validar a política de configuração de aplicativo aplicada

Você pode validar a política de configuração de aplicativo usando os três métodos a seguir:

   1. Visivelmente no dispositivo. O aplicativo de destino está apresentando o comportamento aplicado na política de configuração de aplicativo?
   2. Por meio dos logs de diagnóstico (consulte a seção logs de diagnóstico abaixo).
   3. No portal do Intune. A seção **Monitor** de uma política pode fornecer o status relevante:

      ![Primeira captura de tela do status de instalação do dispositivo](./media/app-configuration-policy-overview/device-install-status-1.png)

      ![Segunda captura de tela do status de instalação do dispositivo](./media/app-configuration-policy-overview/device-install-status-2.png)

      Além disso, em**dispositivos** -> do **Intune** -> **todos os dispositivos** no lado esquerdo da tela, a opção de **configuração de aplicativo** exibirá todas as políticas atribuídas e seu estado:

      ![Captura de tela da configuração do aplicativo](./media/app-configuration-policy-overview/app-configuration.png)

## <a name="graph-api-support-for-app-configuration"></a>Suporte da Graph API para configuração de aplicações

Você pode usar API do Graph para realizar tarefas de configuração de aplicativo. Para obter mais detalhes, veja [Graph API Reference MAM Targeted Config (Configuração de MAM Direcionada de Referência para Graph API)](https://graph.microsoft.io/docs/api-reference/beta/api/intune_mam_targetedmanagedappconfiguration_create).

## <a name="troubleshooting"></a>Resolução de problemas

### <a name="using-logs-to-show-a-configuration-parameter"></a>Usando logs para mostrar um parâmetro de configuração
Quando os logs mostram um parâmetro de configuração que é confirmado para ser aplicado, mas não parece funcionar, pode haver um problema com a implementação da configuração pelo desenvolvedor do aplicativo. Entrar em contato com esse desenvolvedor de aplicativos primeiro ou verificar sua base de dados de conhecimento pode poupar a você uma chamada de suporte com a Microsoft. Se for um problema de como a configuração está sendo tratada em um aplicativo, ele precisaria ser resolvido em uma versão atualizada futura do aplicativo.

## <a name="next-steps"></a>Passos Seguintes

### <a name="managed-devices"></a>Dispositivos geridos

- Saiba como utilizar a configuração de aplicações com os seus dispositivos iOS.  Consulte [Adicionar políticas de configuração de aplicativo para dispositivos IOS gerenciados](app-configuration-policies-use-ios.md).
- Saiba como utilizar a configuração de aplicações com os seus dispositivos Android.  Veja [Adicionar políticas de configuração de aplicações para dispositivos Android geridos](app-configuration-policies-use-android.md).

### <a name="managed-apps"></a>Aplicações geridas

- Saiba como utilizar a configuração de aplicações com aplicações geridas. Veja [Add app configuration policies for managed apps without device enrollment (Adicionar políticas de configuração de aplicações para aplicações geridas sem inscrição de dispositivos)](app-configuration-policies-managed-app.md).
