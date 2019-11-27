---
title: Usar o OEMConfig em dispositivos Android Enterprise no Microsoft Intune – Azure | Microsoft Docs
description: Use Microsoft Intune para gerenciar e usar dispositivos que executam o Android Enterprise com o OEMConfig. Consulte todas as etapas, incluindo uma visão geral, consulte os pré-requisitos, criar o perfil de configuração no Intune e ver uma lista de aplicativos OEMConfig com suporte.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: ''
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 075e7a99f72de30e83447a2869154859e33356b9
ms.sourcegitcommit: 2fddb293d37453736ffa54692d03eca642f3ab58
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/22/2019
ms.locfileid: "74390845"
---
# <a name="use-and-manage-android-enterprise-devices-with-oemconfig-in-microsoft-intune"></a>Usar e gerenciar dispositivos Android Enterprise com o OEMConfig no Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

No Microsoft Intune, você pode usar o OEMConfig para adicionar, criar e personalizar configurações específicas de OEM para dispositivos Android Enterprise. OEMConfig normalmente é usado para definir configurações que não são internas no Intune. Fabricantes de equipamento original (OEM) diferentes incluem configurações diferentes. As configurações disponíveis dependem do que o OEM inclui em seu aplicativo OEMConfig.

Esta funcionalidade aplica-se a:  

- Android Enterprise

Este artigo descreve o OEMConfig, lista os pré-requisitos, mostra como criar um perfil de configuração e lista os aplicativos OEMConfig com suporte no Intune.

## <a name="overview"></a>Descrição geral

As políticas de OEMConfig são um tipo especial de política de configuração de dispositivo semelhante à [política de configuração de aplicativo](../apps/app-configuration-policies-overview.md). OEMConfig é um padrão definido pelo Google que aproveita a configuração de aplicativo no Android para enviar configurações de dispositivo para aplicativos escritos por OEMs (fabricantes originais de equipamento). Esse padrão permite que OEMs e EMMs (gerenciamento de mobilidade empresarial) criem e ofereçam suporte a recursos específicos de OEM de forma padronizada. [Saiba mais sobre o OEMConfig](https://blog.google/products/android-enterprise/oemconfig-supports-enterprise-device-features/).

Historicamente, o EMMs, como o Intune, cria manualmente suporte para recursos específicos do OEM depois que eles são introduzidos pelo OEM. Essa abordagem leva a esforços duplicados e a adoção lenta.

Com o OEMConfig, um OEM cria um esquema que define os recursos de gerenciamento específicos do OEM. O OEM insere o esquema em um aplicativo e, em seguida, coloca esse aplicativo em Google Play. O EMM lê o esquema do aplicativo e expõe o esquema no console do administrador do EMM. O console permite que os administradores do Intune definam as configurações no esquema.

Quando o aplicativo OEMConfig é instalado em um dispositivo, ele usa as configurações definidas no console do administrador do EMM para gerenciar o dispositivo. As configurações no dispositivo são executadas pelo aplicativo OEMConfig, em vez de um agente MDM criado pelo EMM.

Quando o OEM adiciona e melhora os recursos de gerenciamento, o OEM também atualiza o aplicativo no Google Play. Como administrador, você obtém esses novos recursos e atualizações (incluindo correções) sem esperar que o EMMs inclua essas atualizações.

> [!TIP]
> Você só pode usar OEMConfig com dispositivos que dão suporte a esse recurso e ter um aplicativo OEMConfig correspondente. Consulte seu OEM para obter detalhes específicos.

## <a name="before-you-begin"></a>Antes de começar

Ao usar o OEMConfig, esteja ciente das seguintes informações:

- O Intune expõe o esquema do aplicativo OEMConfig para que você possa configurá-lo. O Intune não valida nem altera o esquema fornecido pelo aplicativo. Portanto, se o esquema estiver incorreto ou tiver dados imprecisos, esses dados ainda serão enviados aos dispositivos. Se você encontrar um problema originado no esquema, entre em contato com o OEM para obter orientação.
- O Intune não influencia nem controla o conteúdo do esquema do aplicativo. Por exemplo, o Intune não tem nenhum controle sobre cadeias de caracteres, linguagem, as ações permitidas e assim por diante. Recomendamos entrar em contato com o OEM para obter detalhes e práticas recomendadas para gerenciar seus dispositivos com o OEMConfig.
- A qualquer momento, os OEMs podem atualizar seus recursos e esquemas com suporte e carregar um novo aplicativo para Google Play. O Intune sempre sincroniza a versão mais recente do aplicativo OEMConfig de Google Play. O Intune não mantém versões mais antigas do esquema nem do aplicativo. Se você encontrar conflitos de versão, recomendamos entrar em contato com o OEM para obter mais informações.
- Atribua um perfil OEMConfig a um dispositivo. Se vários perfis forem atribuídos ao mesmo dispositivo, você poderá ver um comportamento inconsistente. O modelo OEMConfig dá suporte apenas a uma única política por dispositivo.

## <a name="prerequisites"></a>Pré-requisitos

Para usar o OEMConfig em seus dispositivos, certifique-se de ter os seguintes requisitos:

- Um dispositivo Android Enterprise registrado no Intune.
- Um aplicativo OEMConfig criado pelo OEM e carregado para Google Play. Se não estiver em Google Play, entre em contato com o OEM para obter mais informações.
- O administrador do Intune tem permissões de RBAC (controle de acesso baseado em função) para **aplicativos móveis**, **configurações de dispositivo**e a permissão de "leitura" no **Android for Work**. Essas permissões são necessárias porque os perfis OEMConfig usam configurações de aplicativo gerenciado para gerenciar as configurações do dispositivo.

## <a name="prepare-the-oemconfig-app"></a>Preparar o aplicativo OEMConfig

Verifique se o dispositivo dá suporte a OEMConfig, se o aplicativo OEMConfig correto foi adicionado ao Intune e se o aplicativo está instalado no dispositivo. Contate o OEM para obter essas informações.

> [!TIP] 
> Os aplicativos OEMConfig são específicos para o OEM. Por exemplo, um aplicativo Sony OEMConfig instalado em um dispositivo pretas Technologies não faz nada.

1. Obtenha o aplicativo OEMConfig do Google Play Store gerenciado. [Adicionar aplicativos Google Play gerenciados a dispositivos Android Enterprise](../apps/apps-add-android-for-work.md) lista as etapas.
2. Alguns OEMs podem enviar dispositivos com o aplicativo OEMConfig pré-instalado. Se o aplicativo não estiver pré-instalado, use o Intune para [Adicionar e implantar o aplicativo em dispositivos](../apps/apps-deploy.md).

## <a name="create-an-oemconfig-profile"></a>Criar um perfil do OEMConfig

1. Entre no centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selecione **dispositivos** > **perfis de configuração** > **Criar perfil**.
3. Introduza as seguintes propriedades:

    - **Nome**: introduza um nome descritivo para o novo perfil.
    - **Descrição:** introduza uma descrição para o perfil. Esta definição é opcional, mas recomendada.
    - **Plataforma**: selecione **Android Enterprise**.
    - **Tipo de perfil**: selecione **OEMConfig**.

4. Selecione **aplicativo associado**, selecione um aplicativo OEMConfig existente que você adicionou anteriormente > **OK**. Certifique-se de escolher o aplicativo OEMConfig correto para os dispositivos para os quais você está atribuindo a política.

    Se você não vir nenhum aplicativo listado, configure o Google Play gerenciado e obtenha aplicativos do repositório de Google Play gerenciado. [Adicionar aplicativos Google Play gerenciados a dispositivos Android Enterprise](../apps/apps-add-android-for-work.md) lista as etapas.

    > [!IMPORTANT]
    > Se você adicionou um aplicativo OEMConfig e o sincronizou para Google Play, mas ele não está listado como um **aplicativo associado**, talvez seja necessário entrar em contato com o Intune para carregar o aplicativo. Consulte [adicionando um novo aplicativo](#supported-oemconfig-apps) (neste artigo).

5. Em **definir configurações com**, escolha usar o **Designer de configuração** ou o **Editor de JSON**:

    > [!TIP]
    > Leia a documentação do OEM para certificar-se de que você está configurando as propriedades corretamente. Essas propriedades de aplicativo são incluídas pelo OEM, não pelo Intune. O Intune faz a validação mínima das propriedades ou o que você insere. Por exemplo, se você inserir `abcd` para um número de porta, o perfil salvará no estado em que se encontra e será implantado em seus dispositivos com os valores que você configurar. Certifique-se de inserir as informações corretas.

    - **Designer de configuração**: quando você seleciona essa opção, as propriedades disponíveis no esquema do aplicativo são mostradas para você configurar.

      - Menus de contexto no designer de configuração indicam que mais opções estão disponíveis. Por exemplo, o menu de contexto pode permitir que você adicione, exclua e reordene as configurações. Essas opções são incluídas pelo OEM. Certifique-se de ler a documentação do aplicativo OEM para saber como essas opções devem ser usadas para criar perfis.

      - Muitas configurações têm valores padrão fornecidos pelo OEM. Para ver se há um valor padrão, passe o mouse sobre o ícone de informações ao lado da configuração. Uma dica de ferramenta mostra os valores padrão para essa configuração (se aplicável) e mais detalhes fornecidos pelo OEM.

      - Clicar em **limpar** exclui uma configuração do perfil. Se uma configuração não estiver no perfil, seu valor no dispositivo não será alterado quando o perfil for aplicado.

      - Se você criar um pacote vazio (não configurado) no designer de configuração, ele será excluído ao alternar para o editor de JSON.

    - **Editor de JSON**: quando você seleciona essa opção, um editor de JSON é aberto com um modelo para o esquema de configuração completo inserido no aplicativo. No editor, personalize o modelo com valores para as diferentes configurações. Se você usar o **Designer de configuração** para alterar seus valores, o editor de JSON substituirá o modelo por valores do designer de configuração.

      - Se você estiver atualizando um perfil existente, o editor de JSON mostrará as configurações que foram salvas pela última vez com o perfil.

      - Os esquemas OEMConfig podem ser grandes e complexos. Se preferir atualizar essas configurações usando um editor diferente, selecione o botão **baixar modelo JSON** . Use um editor de sua escolha para adicionar seus valores de configuração ao modelo. Em seguida, copie e cole o JSON atualizado no para a propriedade do **Editor JSON** .

      - Você pode usar o editor de JSON para criar um backup de sua configuração. Depois de definir as configurações, use esse recurso para obter as configurações de JSON com seus valores. Copie e cole o JSON em um arquivo e salve-o. Agora você tem um arquivo de backup.

    Todas as alterações feitas no designer de configuração também são feitas automaticamente no editor de JSON. Da mesma forma, todas as alterações feitas no editor de JSON são feitas automaticamente no designer de configuração. Se sua entrada contiver valores inválidos, você não poderá alternar entre o designer de configuração e o editor de JSON até corrigir os problemas.

6. Selecione **OK** > **Adicionar** para salvar as alterações. A política é criada e apresentada na lista.

Certifique-se de [atribuir o perfil](device-profile-assign.md) e [monitorar seu status](device-profile-monitor.md).

 > [!NOTE]
 > Atribua um perfil a cada dispositivo. O modelo OEMConfig dá suporte apenas a uma política por dispositivo.

Na próxima vez que o dispositivo verificar se há atualizações de configuração, as configurações específicas do OEM que você configurou serão aplicadas ao aplicativo OEMConfig.

> [!NOTE]
> O padrão OEMConfig atualmente não inclui o relatório de status. Portanto, por padrão, os perfis mostram um status **pendente** .

## <a name="supported-oemconfig-apps"></a>Aplicativos OEMConfig com suporte

Em comparação com os aplicativos padrão, os aplicativos OEMConfig expandem os privilégios de configurações gerenciadas concedidos pelo Google para dar suporte a esquemas mais complexos. Atualmente, o Intune dá suporte aos seguintes aplicativos OEMConfig:

-----------------

| OEM | ID do Pacote | Documentação do OEM (se disponível) |
| --- | --- | ---|
| Samsung | com.samsung.android.knox.kpu | [Guia de administração do plug-in do Knox Service](https://docs.samsungknox.com/knox-service-plugin/admin-guide/index.htm) |
| Tecnologias pretas | com. pretas. oemconfig. Common | [Visão geral do pretas OEMConfig](http://techdocs.zebra.com/oemconfig ) |
| Datalogic | com. Datalogic. oemconfig | [Documentação do usuário para Datalogic OEMConfig](https://datalogic.github.io/oemconfig/) |
| Honeywell | com. Honeywell. oemconfig |  |
| Kyocera | JP. Kyocera. enterprisedeviceconfig |  |
| SpectraLink-códigos de barras | com. spectralink. Barcode. Service |  |
| SpectraLink-botões | com. spectralink. Buttons |  |
| SpectraLink-dispositivo | com. spectralink. slnkdevicesettings  |  |
| SpectraLink-registro em log | com. spectralink. slnklogger |  |
| Spectralink - VQO | com. spectralink. slnkvqo |  |

-----------------

Se um aplicativo OEMConfig existir para seu dispositivo, mas não estiver na tabela acima ou não estiver aparecendo no console do Intune, envie um email `IntuneOEMConfig@microsoft.com`.

> [!NOTE]
> Os aplicativos OEMConfig devem ser integrados pelo Intune antes que possam ser configurados com perfis OEMConfig. Quando um aplicativo tem suporte, você não precisa entrar em contato com a Microsoft sobre como configurá-lo em seu locatário. Basta seguir as instruções nesta página.

## <a name="next-steps"></a>Passos Seguintes

- [Atribua o perfil](device-profile-assign.md) e [monitorize o respetivo estado](device-profile-monitor.md).
