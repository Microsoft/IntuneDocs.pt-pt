---
title: Utilizar OEMConfig em dispositivos Android Enterprise no Microsoft Intune – Azure | Documentos da Microsoft
description: Utilize o Microsoft Intune para gerir e utilizar dispositivos que executam o Android Enterprise com OEMConfig. Ver todas as etapas, incluindo uma descrição geral, consulte os pré-requisitos, criar o perfil de configuração no Intune e ver uma lista de aplicações de OEMConfig suportadas.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/17/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: ''
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 022bbcf98a5e00888f33e22941515ca03c5f6995
ms.sourcegitcommit: 1cae690ca2ac6cc97bbcdf656f54b31878297ae8
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/22/2019
ms.locfileid: "59901798"
---
# <a name="use-and-manage-android-enterprise-devices-with-oemconfig-in-microsoft-intune"></a>Utilizar e gerir dispositivos Android Enterprise com OEMConfig no Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

No Microsoft Intune, pode utilizar OEMConfig para adicionar, criar e personalizar as definições de OEM específico para dispositivos Android Enterprise. OEMConfig é normalmente utilizado para configurar as definições que não estão incorporadas no Intune. Diferentes OEMs incluem configurações diferentes. Por isso, as definições disponíveis dependerão o que inclui o OEM na respetiva aplicação OEMConfig.

Esta funcionalidade aplica-se a:  

- Android Enterprise

Este artigo descreve OEMConfig, o que ele faz, lista os pré-requisitos, mostra como criar um perfil de configuração e apresenta uma lista de aplicações suportadas OEMConfig no Intune.

## <a name="overview"></a>Descrição geral

As políticas de OEMConfig são um tipo especial de política de configuração de dispositivo muito semelhante à [política de configuração de aplicação](app-configuration-policies-overview.md). OEMConfig é um padrão definido pelos [Comunidade de AppConfig](https://www.appconfig.org/android-oemconfig/) (abre-se outro web site) que permite que os OEMs (fabricantes originais do equipamento) e EMMs (gestão de mobilidade empresarial) criar e oferecer suporte a recursos específicos de OEM num forma normalizada. Historicamente, o EMMs, como o Intune, crie manualmente suporte para recursos específicos do OEM depois que estes são introduzidos pelo OEM. Essa abordagem leva à esforços duplicados e a adoção lenta.

Com OEMConfig, um OEM cria um esquema que define as funcionalidades de gestão específicos de OEM. O OEM incorpora o esquema numa aplicação e, em seguida, coloca esta aplicação no Google Play. O EMM lê o esquema da aplicação e expõe o esquema na consola do administrador EMM. O console permite que os administradores do Intune configurar as definições no esquema.

Quando a aplicação de OEMConfig é instalada num dispositivo, ele pode utilizar as definições configuradas na consola do administrador EMM para gerir o dispositivo. Definições do dispositivo são executadas pela aplicação OEMConfig, em vez de um agente MDM criado pelo EMM.

Quando o OEM adiciona e melhora a funcionalidades de gestão, o OEM também atualiza a aplicação na Google Play. Como administrador, obtém esses novos recursos e atualizações (incluindo correções) sem aguardar EMMs incluir estas atualizações.

> [!TIP]
> Só pode utilizar OEMConfig com dispositivos que suportam esta funcionalidade e tem uma aplicação de OEMConfig correspondente. Para obter detalhes específicos, consulte o seu OEM.

## <a name="before-you-begin"></a>Antes de começar

Quando utilizar OEMConfig, tenha em atenção as seguintes informações:

- Intune expõe o esquema da aplicação OEMConfig para que pode configurá-lo. Intune não validar ou alterar o esquema fornecido pela aplicação. Portanto, se o esquema está incorreto, ou se tiver dados incorretos, estes dados ainda são enviados aos dispositivos. Se encontrar um problema que tem origem no esquema, contacte o OEM para obter orientações.
- Intune não influenciam ou controlar o conteúdo do esquema de aplicação. Por exemplo, o Intune não tem nenhum controle sobre cadeias de caracteres, idioma, as ações permitidas e assim por diante. Recomendamos entrar em contato com o OEM para obter detalhes e melhores práticas para gestão dos seus dispositivos com OEMConfig.
- Em qualquer altura, os OEMs podem atualizar seus recursos suportados e os esquemas e carregar uma nova aplicação para o Google Play. O Intune sincroniza sempre a versão mais recente da aplicação OEMConfig na Google Play. Intune não manter versões mais antigas do esquema ou a aplicação. Caso se depare com conflitos de versão, recomendamos entrar em contato com o OEM para obter mais informações.
- Só deverá atribuir um perfil de OEMConfig num dispositivo. Se vários perfis são atribuídos ao mesmo dispositivo, poderá ver o comportamento inconsistente. O modelo de OEMConfig suporta apenas uma única política por dispositivo.

## <a name="prerequisites"></a>Pré-requisitos

Para utilizar OEMConfig nos seus dispositivos, certifique-se de que tem os seguintes requisitos:

- Um dispositivo Android Enterprise inscritos no Intune.
- Uma aplicação de OEMConfig criada pelo OEM e carregados para o Google Play. Se não estiver no Google Play, contacte o OEM para obter mais informações.
- O administrador do Intune tem permissões de controlo (RBAC) de acesso baseado em funções para **aplicações móveis** e **configurações dos dispositivos**. Isto acontece porque OEMConfig perfis tornam a utilização de configurações de aplicação gerida para gerir configurações de dispositivos.

## <a name="prepare-the-oemconfig-app"></a>Preparar a aplicação de OEMConfig

Certifique-se de que o dispositivo suporta OEMConfig, que a aplicação de OEMConfig correta foi adicionada ao Intune e de que a aplicação está instalada no dispositivo. Entre em contato com o OEM para obter estas informações.

> [!TIP] 
> Aplicações de OEMConfig são específicas para o OEM. Por exemplo, uma aplicação de Sony OEMConfig instalada num dispositivo as riscas das tecnologias não faz nada.

1. Obter a aplicação de OEMConfig no gerida Play Store da Google. [Adicionar aplicações da Google Play gerido ao dispositivos empresariais Android](apps-add-android-for-work.md) lista os passos.
2. Alguns OEMs podem enviar dispositivos com a aplicação de OEMConfig pré-instalado. Se a aplicação não está pré-instalado, utilizar o Intune para [adicionar e implementar a aplicação em dispositivos](apps-deploy.md).

## <a name="create-an-oemconfig-profile"></a>Criar um perfil de OEMConfig

1. Na [portal do Azure](https://portal.azure.com), selecione **todos os serviços** > Filtrar **Intune** > selecione **Intune**.
2. Selecione **Configuração do Dispositivo** > **Perfis** > **Criar perfil**.
3. Introduza as seguintes propriedades:

    - **Nome**: Introduza um nome descritivo para o novo perfil.
    - **Descrição**: Introduza uma descrição para o perfil. Esta definição é opcional, mas recomendada.
    - **Plataforma**: Selecione **Android enterprise**.
    - **Tipo de perfil**: Selecione **OEMConfig**.

4. Selecione **aplicação associada**e selecione uma aplicação existente de OEMConfig foi adicionado anteriormente. Certifique-se de que escolha a aplicação de OEMConfig correta para os dispositivos que está a atribuir a política.

    Se não ver todas as aplicações listadas, em seguida, configurar o Google Play gerido e obter aplicações da loja Google Play gerido. [Adicionar aplicações da Google Play gerido ao dispositivos empresariais Android](apps-add-android-for-work.md) lista os passos.

    > [!IMPORTANT]
    > Se adicionar uma aplicação de OEMConfig e sincronizados-lo para o Google Play, mas não estiver listado como um **aplicação associada**, poderá ter de contactar o Intune para carregar a aplicação. Ver [adicionando uma nova aplicação](#supported-oemconfig-apps) (neste artigo).

5. Selecione o separador **Configuration** (Configuração).

    Um editor de JSON é aberto com um modelo para o esquema de configuração incorporado na aplicação. No editor, personalize o modelo com valores para as definições de configuração diferente. 
    
    Uma vez que os esquemas de OEMConfig podem ser grandes e complexos, pode utilizar o **transferir modelo JSON** botão para obter o modelo como um ficheiro. Configurar o arquivo de modelo num editor à sua escolha, em seguida, copie o conteúdo para o console de administração do Intune.

6. Selecione **OK** > **Add** para guardar as alterações. A política é criada e apresentada na lista.

Não se esqueça [atribuir o perfil](device-profile-assign.md) e [monitorizar o estado](device-profile-monitor.md).
    
 > [!NOTE]
 > Atribua um perfil para cada dispositivo. O modelo de OEMConfig suporta apenas uma política de por dispositivo.

Da próxima vez que o dispositivo verifica a existência de atualizações de configuração, as definições específicas do OEM configuradas são aplicadas à aplicação OEMConfig.

## <a name="supported-oemconfig-apps"></a>Aplicações de OEMConfig suportados

Em comparação com as aplicações padrão, aplicações de OEMConfig expanda os privilégios de configurações geridas concedidos pela Google para oferecer suporte a esquemas mais complexas. Atualmente, o Intune suporta as seguintes aplicações OEMConfig:

-----------------

| OEM | ID do Pacote |
| --- | --- |
| Samsung | com.samsung.android.knox.kpu |

-----------------

Para pedir uma nova aplicação de OEMConfig ser integrado, envie um e-mail `IntuneOEMConfig@microsoft.com`.

> [!NOTE]
> Aplicações de OEMConfig tem de ser integrado pelo Intune antes de pode ser configurados com perfis de OEMConfig.

## <a name="next-steps"></a>Passos Seguintes

- [Atribua o perfil](device-profile-assign.md) e [monitorize o respetivo estado](device-profile-monitor.md).
