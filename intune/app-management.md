---
title: O que é a gestão de aplicações no Microsoft Intune?
titleSuffix: ''
description: Saiba mais sobre as capacidades de gestão de aplicações de cliente pela plataforma do Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/03/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 1975a2dc-3a14-4cb9-9afb-e2ba01a1c51b
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 34807edabf99a107c259fdfae5e43db18084fb67
ms.sourcegitcommit: 219bbbfb44eba70ac2b751970d8b4b778cd28416
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/04/2019
ms.locfileid: "58920250"
---
# <a name="what-is-microsoft-intune-app-management"></a>O que é a gestão de aplicações do Microsoft Intune?


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Enquanto administrador de TI, pode utilizar o Microsoft Intune para gerir as aplicações cliente utilizadas pela força de trabalho da sua empresa. Esta funcionalidade complementa a gestão de dispositivos e proteção de dados. Uma das prioridades de um administrador é garantir que os utilizadores finais têm acesso às aplicações que precisam para trabalhar. Este objetivo pode ser um desafio porque:
- Existe uma grande variedade de plataformas de dispositivos e de tipos de aplicações.
- Poderá ter de gerir as aplicações nos dispositivos da empresa e nos dispositivos pessoais dos utilizadores.
- Tem de garantir que a sua rede e os seus dados permanecem seguros.

Além disso, pode querer atribuir e gerir aplicações em dispositivos que não estão inscritos no Intune.

O Intune oferece várias funcionalidades para o ajudar a obter as aplicações de que precisa, nos dispositivos nos quais quer executá-las. A seguinte tabela mostra um resumo das funcionalidades de gestão de aplicações: 

## <a name="app-management-capabilities-by-platform"></a>Capacidades de gestão de aplicações por plataforma

|  | Android | iOS | macOS | Windows 10 | Windows Phone 8.1 |
|-------------------------------------------------------------------------------------|---------|-----|-------|------------|-------------------|
| Adicionar e atribuir aplicações a dispositivos e utilizadores | Sim | Sim | Sim | Sim | Sim |
| Atribuir aplicações a dispositivos não inscritos no Intune | Sim | Sim | Não | Não | Não |
| Utilizar políticas de configuração de aplicações para controlar o comportamento de arranque das aplicações | Sim | Sim | Não | Não | Não |
| Utilizar políticas de aprovisionamento de aplicações móveis para renovar aplicações expiradas | Não | Sim | Não | Não | Não |
| Proteger dados da empresa em aplicações com políticas de proteção | Sim | Sim | Não | Não1 | Não |
| Remover apenas dados empresariais a partir de uma aplicação instalada (eliminação seletiva de aplicações) | Sim | Sim | Não | Sim | Sim |
| Monitorizar atribuições de aplicações | Sim | Sim | Sim | Sim | Sim |
| Atribuir e controlar aplicações compradas em volume a partir de uma loja de aplicações | Não | Não | Não | Sim | Não |
| Instalação obrigatória de aplicações em dispositivos (obrigatório)2 | Sim | Sim | Sim | Sim | Sim |
| Instalação opcional em dispositivos a partir do Portal da Empresa (instalação disponível) | Sim | Sim | Sim | Sim | Sim |
| Instalar um atalho para uma aplicação na Web (ligação da Web) | Sim | Sim | Sim | Sim | Sim |
| Aplicações internas (linha de negócios) | Sim | Sim | Sim | Sim | Não |
| Aplicações de uma loja | Sim | Sim | Não | Sim | Sim |
| Atualizar aplicações | Sim | Sim | Não | Sim | Sim |

<sup>1</sup> Considere a utilização do [Windows Information Protection](windows-information-protection-configure.md) para proteger aplicações em dispositivos com o Windows 10.

<sup>2</sup> Aplica-se apenas a dispositivos geridos pelo Intune.

## <a name="get-started"></a>Introdução

Pode encontrar a maior parte das informações relacionadas com aplicações na carga de trabalho **Aplicações do Cliente**, à qual pode aceder da seguinte forma:

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços** > **Intune**.  
    O Intune encontra-se na secção **Monitorização + Gestão**.
3. No painel **Microsoft Intune**, selecione **Aplicações do cliente**.

    ![O painel da carga de trabalho "Aplicações do cliente"](./media/apps-workload.png)

As próximas quatro secções descrevem as opções disponíveis no painel **Aplicações do cliente**.

### <a name="manage"></a>Gerir o Endpoint Protection do
- **Aplicações**: Selecione esta opção para adicionar, ver, atribuir e monitorizar as aplicações que utiliza a sua força de trabalho. Para obter mais informações, consulte:
    - [Adicionar aplicações](apps-add.md).
    - [Atribuir aplicações](apps-deploy.md).
    - [Monitorizar aplicações](apps-monitor.md).
- **Políticas de configuração de aplicação**: Selecione esta opção para disponibilizar definições que poderão ser necessárias quando um utilizador executar uma aplicação. Para obter mais informações, consulte:
    - [Políticas de configuração de aplicações do Intune](app-configuration-policies-overview.md).
        - [Políticas de configuração de aplicações iOS](app-configuration-policies-use-ios.md).
        - [Políticas de configuração de aplicações Android](app-configuration-policies-use-android.md).
- **Políticas de proteção de aplicações**: Selecione esta opção para associar definições a uma aplicação e ajudar a proteger os dados da empresa que utiliza. Por exemplo, pode restringir as capacidades de uma aplicação para comunicar com outras aplicações ou exigir que o utilizador introduza um PIN para aceder a uma aplicação da empresa. Para obter mais informações, consulte:
    - [Políticas de proteção de aplicações ](app-protection-policies.md).
- **Eliminação seletiva de aplicações**: Selecione esta opção para remover apenas os dados empresariais do dispositivo do utilizador selecionado. Para obter mais informações, consulte:
    - [Eliminação seletiva de aplicações](apps-selective-wipe.md).
- **Perfis de aprovisionamento de aplicações iOS**: as aplicações iOS incluem um perfil de aprovisionamento e um código assinado por um certificado. Quando o certificado expirar, a aplicação já não poderá ser executada. O Intune proporciona-lhe as ferramentas para atribuir proativamente uma nova política de perfil de aprovisionamento a dispositivos que tenham aplicações prestes a expirar. Para obter mais informações, consulte:
    - [Perfis de aprovisionamento de aplicações iOS](app-provisioning-profile-ios.md).

Para obter mais informações sobre esta secção, veja [Gerir aplicações](app-management.md).

### <a name="monitor"></a>Monitorizar
- **Licenças de aplicações**: Ver, atribuir e monitorizar aplicações compradas em volume lojas de aplicações. Para obter mais informações, consulte:
    - [Aplicações iOS do programa de compras em volume (VPP)](vpp-apps-ios.md).
    - [Aplicações compradas em volume na Microsoft Store para Empresas](windows-store-for-business.md).
- **Aplicações detetadas**: Ver as aplicações que foram atribuídas pelo Intune ou instaladas num dispositivo. Para obter mais informações, veja [Ver os detalhes do dispositivo com o Microsoft Intune](device-inventory.md).
- **Estado de instalação da aplicação**: Ver o estado de uma atribuição de aplicação que criou. Para obter mais informações, veja [Como monitorizar informações e atribuições da aplicação com o Microsoft Intune](apps-monitor.md#device-and-user-status-graphs).
- **Estado de proteção de aplicações**: Ver o estado de uma política de proteção de aplicações para um utilizador que selecionar.
- **Registos de auditoria**: Ver a atividade de relacionada com a aplicação do Intune de todos os administradores de TI.

Para obter mais informações sobre esta secção, veja [Monitorizar aplicações](apps-monitor.md).

### <a name="set-up"></a>Configurar
- **tokens VPP do iOS**: Aplique e veja as suas licenças de Volume Purchase Program (VPP) iOS. Para obter mais informações, consulte:
    - [aplicações iOS compradas em volume](vpp-apps-ios.md)
- **Certificado empresarial do Windows**: Aplique ou veja o estado de um certificado de assinatura de código que é utilizado para distribuir aplicações de linha de negócio nos dispositivos Windows geridos.
- **Certificado da Symantec do Windows**: Aplique ou veja o estado de um certificado de assinatura de código da Symantec, que é preciso para distribuir ficheiros appx XAP e WP8.x aos dispositivos Windows 10 Mobile.
- **Microsoft Store para empresas**: Configure a integração da Microsoft Store para empresas. Em seguida, pode sincronizar com o Intune as aplicações compradas, atribuí-las e controlar a utilização das suas licenças. Para obter mais informações, consulte:
    - [Aplicações compradas em volume na Microsoft Store para Empresas](windows-store-for-business.md).
- **Chaves de sideload de Windows**: Adicione uma chave de sideload do Windows que pode ser utilizada para instalar uma aplicação diretamente nos dispositivos em vez de publicar e transferir a aplicação da loja Windows. Para obter mais informações, consulte:
    - [Fazer sideload de uma aplicação Windows](app-sideload-windows.md).
- **Imagem corporativa de Portal da empresa**: Personalize o Portal da empresa para dar a ele a marca da empresa. Para obter mais informações, consulte:
    - [Configuração do Portal da Empresa](company-portal-app.md).
- **Categorias de aplicações**: Adicionar, pin e elimine nomes de categorias de aplicação.
- **Perfil de trabalho Android**: Aprove e sincronize as aplicações que aprovou para a sua empresa. Para obter mais informações, consulte:
    - [Aplicações do perfil de trabalho do Android](apps-add-android-for-work.md).

### <a name="help-and-support"></a>Ajuda e suporte
- **Ajuda e suporte**: Resolução de problemas, peça suporte ou ver o estado do Intune. Para obter mais informações, consulte:
    - [Resolver problemas](help-desk-operators.md).

## <a name="next-steps"></a>Passos Seguintes

- [Adicionar uma aplicação ao Microsoft Intune](apps-add.md)
