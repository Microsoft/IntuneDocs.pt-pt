---
title: O que é a gestão de aplicações no Microsoft Intune?
titleSuffix: ''
description: Saiba mais sobre as capacidades de gestão de aplicações cliente da plataforma do Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/27/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 1975a2dc-3a14-4cb9-9afb-e2ba01a1c51b
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: c22fafce6583dd1e58d61e3fa8e6077b70998588
ms.sourcegitcommit: 045ca42cad6f86024af9a38a380535f42a6b4bef
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/28/2020
ms.locfileid: "77781786"
---
# <a name="what-is-microsoft-intune-app-management"></a>O que é a gestão de aplicações do Microsoft Intune?


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Enquanto administrador de TI, pode utilizar o Microsoft Intune para gerir as aplicações cliente utilizadas pela força de trabalho da sua empresa. Esta funcionalidade complementa a gestão de dispositivos e proteção de dados. Uma das prioridades de um administrador é garantir que os utilizadores finais têm acesso às aplicações que precisam para trabalhar. Este objetivo pode ser um desafio porque:
- Existe uma grande variedade de plataformas de dispositivos e de tipos de aplicações.
- Poderá ter de gerir as aplicações nos dispositivos da empresa e nos dispositivos pessoais dos utilizadores.
- Tem de garantir que a sua rede e os seus dados permanecem seguros.

Além disso, pode querer atribuir e gerir aplicações em dispositivos que não estão inscritos no Intune.

## <a name="mobile-application-management-mam-basics"></a>Bases básicas de Gestão de Aplicações Móveis (MAM)

A [gestão de aplicações móveis do Intune](app-lifecycle.md) refere-se ao conjunto de funcionalidades de gestão do Intune que lhe permite publicar, emitir via push, configurar, proteger, monitorizar e atualizar aplicações móveis para os seus utilizadores.

A MAM permite-lhe gerir e proteger os dados da sua organização dentro de uma aplicação. Com a **MAM sem matrícula** (MAM-WE), uma aplicação relacionada com trabalho ou escola que contenha dados sensíveis pode ser gerida em quase todos os [dispositivos](app-management.md#app-management-capabilities-by-platform), incluindo dispositivos pessoais em cenários de **bring-your-own-device** (BYOD). Muitas aplicações de produtividade, como as aplicações do Microsoft Office, podem ser geridas pela MAM do Intune. Consulte a lista oficial de [aplicações protegidas](apps-supported-intune-apps.md) microsoft Intune disponíveis para uso público.

A MAM do Intune suporta dois tipos de configurações:
- **Intune MDM + MAM**: os administradores de TI só podem gerir as aplicações através da MAM e das políticas de proteção de aplicações em dispositivos que estejam inscritos na gestão de dispositivos móveis do Intune (MDM). Para gerir aplicações com a MDM + MAM, os clientes devem utilizar a consola do Intune no portal do Azure em https://portal.azure.com.
- **MAM sem inscrição de dispositivos**: a MAM sem inscrição de dispositivos, ou MAM-WE, permite aos administradores de TI gerir as aplicações com a MAM e as políticas de proteção de aplicações nos dispositivos que não estejam inscritos na MDM do Intune. Isto significa que as aplicações podem ser geridas pelo Intune em dispositivos inscritos em fornecedores de EMM terceiros. Para gerir aplicações com a MAM-WE, os clientes devem utilizar a consola do Intune no portal do Azure em https://portal.azure.com. Além disso, as aplicações podem ser geridas pelo Intune nos dispositivos inscritos em fornecedores de Gestão de Mobilidade da Empresa (EMM) de terceiros ou não inscritos numa MDM. Para obter mais informações sobre o BYOD e o EMS da Microsoft, consulte [as decisões tecnológicas para permitir o BYOD com a Microsoft Enterprise Mobility + Security (EMS)](../fundamentals/byod-technology-decisions.md).

## <a name="app-management-capabilities-by-platform"></a>Capacidades de gestão de aplicações por plataforma

O Intune oferece várias funcionalidades para o ajudar a obter as aplicações de que precisa, nos dispositivos nos quais quer executá-las. A seguinte tabela mostra um resumo das funcionalidades de gestão de aplicações.

|  | Android/Android Enterprise | iOS/iPadOS | macOS | Windows 10 | Windows Phone 8.1 |
|-------------------------------------------------------------------------------------|---------|-----|-------|------------|-------------------|
| Adicionar e atribuir aplicações a dispositivos e utilizadores | Sim | Sim | Sim | Sim | Sim |
| Atribuir aplicações a dispositivos não inscritos no Intune | Sim | Sim | Não | Não | Não |
| Utilizar políticas de configuração de aplicações para controlar o comportamento de arranque das aplicações | Sim | Sim | Não | Não | Não |
| Utilizar políticas de aprovisionamento de aplicações móveis para renovar aplicações expiradas | Não | Sim | Não | Não | Não |
| Proteger dados da empresa em aplicações com políticas de proteção | Sim | Sim | Não | Não <sup>1</sup> | Não |
| Remover apenas dados empresariais a partir de uma aplicação instalada (eliminação seletiva de aplicações) | Sim | Sim | Não | Sim | Sim |
| Monitorizar atribuições de aplicações | Sim | Sim | Sim | Sim | Sim |
| Atribuir e controlar aplicações compradas em volume a partir de uma loja de aplicações | Não | Não | Não | Sim | Não |
| Instalação obrigatória de aplicações em dispositivos (obrigatório) <sup>2</sup> | Sim | Sim | Sim | Sim | Sim |
| Instalação opcional em dispositivos a partir do Portal da Empresa (instalação disponível) | Sim <sup>3</sup> | Sim | Sim | Sim | Sim |
| Instalar um atalho para uma aplicação na Web (ligação da Web) | Sim <sup>4</sup> | Sim | Sim | Sim | Sim |
| Aplicações internas (linha de negócios) | Sim | Sim | Sim | Sim | Não |
| Aplicações de uma loja | Sim | Sim | Não | Sim | Sim |
| Atualizar aplicações | Sim | Sim | Não | Sim | Sim |

<sup>1</sup> Considere a utilização do [Windows Information Protection](../protect/windows-information-protection-configure.md) para proteger aplicações em dispositivos com o Windows 10.<br>
<sup>2</sup> Aplica-se apenas a dispositivos geridos pelo Intune.<br>
<sup>3</sup> O Intune suporta as aplicações disponíveis na loja do Managed Google Play em dispositivos Android Enterprise.<br>
<sup>4</sup> O Intune não permite a instalação de um atalho para aplicações como uma ligação Web em dispositivos padrão do Android Enterprise. No entanto, o suporte da ligação Web é fornecido para [vários dispositivos dedicados de várias aplicações do Android Enterprise](../configuration/device-restrictions-android-for-work.md#dedicated-device-settings). 


## <a name="get-started"></a>Introdução

Pode encontrar a maioria das informações relacionadas com aplicações na carga de trabalho das **Apps,** às quais pode aceder fazendo o seguinte:

1. Inscreva-se no [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).
3. Selecione **Apps**.

    ![O painel de trabalho das Apps](./media/app-management/apps-workload.png)

As próximas quatro secções descrevem as opções disponíveis no painel **apps.**

### <a name="manage"></a>Gerir o Endpoint Protection do
- **Aplicações**: selecione esta opção para adicionar, ver, atribuir e monitorizar as aplicações que a sua força de trabalho utiliza. Para obter mais informações, consulte:
  - [Adicionar aplicações](apps-add.md).
  - [Atribuir aplicações](apps-deploy.md).
  - [Monitorizar aplicações](apps-monitor.md).
- **Políticas de configuração de aplicações**: selecione esta opção para disponibilizar definições que poderão ser necessárias quando o utilizador executar uma aplicação. Para obter mais informações, consulte:
  - [Políticas de configuração de aplicações do Intune](app-configuration-policies-overview.md).
    - Políticas de configuração de [aplicações iOS/iPadOS.](app-configuration-policies-use-ios.md)
    - [Políticas de configuração de aplicações Android](app-configuration-policies-use-android.md).
- **Políticas de proteção de aplicações**: selecione esta opção para associar definições a uma aplicação e ajudar a proteger os dados da empresa que utiliza. Por exemplo, pode restringir as capacidades de uma aplicação para comunicar com outras aplicações ou exigir que o utilizador introduza um PIN para aceder a uma aplicação da empresa. Para obter mais informações, consulte:
  - [Políticas de proteção de aplicações ](app-protection-policies.md).
- **Eliminação seletiva de aplicações**: selecione esta opção para remover apenas os dados empresariais do dispositivo de um utilizador selecionado. Para obter mais informações, consulte:
  - [Eliminação seletiva de aplicações](apps-selective-wipe.md).
- Perfis de fornecimento de **aplicações iOS**: as aplicações iOS/iPadOS incluem um perfil de provisionamento e código que é assinado por um certificado. Quando o certificado expirar, a aplicação já não poderá ser executada. O Intune proporciona-lhe as ferramentas para atribuir proativamente uma nova política de perfil de aprovisionamento a dispositivos que tenham aplicações prestes a expirar. Para obter mais informações, consulte:
  - Perfis de fornecimento de [aplicações iOS/iPadOS.](app-provisioning-profile-ios.md)

Para obter mais informações sobre esta secção, veja [Gerir aplicações](app-management.md).

### <a name="monitor"></a>Monitor
- **Licenças de aplicações**: veja, atribua e monitorize as aplicações compradas em volume nas lojas de aplicações. Para obter mais informações, consulte:
  - aplicações de programa adquirido em [volume iOS/iPadOS (VPP).](vpp-apps-ios.md)
  - [Aplicações compradas em volume na Microsoft Store para Empresas](windows-store-for-business.md).
- **Aplicações Detetadas**: veja as aplicações que foram atribuídas pelo Intune ou instaladas num dispositivo. Para mais informações, consulte [intune aplicações descobertas.](app-discovered-apps.md)
- **Estado da Instalação da Aplicação**: veja o estado da atribuição de uma aplicação que criou. Para obter mais informações, veja [Como monitorizar informações e atribuições da aplicação com o Microsoft Intune](apps-monitor.md#device-and-user-status-graphs).
- **Estado da proteção da aplicação**: veja o estado da política de proteção de uma aplicação de um utilizador selecionado.
- **Registos de auditoria**: veja a atividade relacionada com a aplicação do Intune realizada por todos os administradores de TI.

Para obter mais informações sobre esta secção, veja [Monitorizar aplicações](apps-monitor.md).

### <a name="set-up"></a>Configurar
- **iOS Fichas VPP**: Aplicar e ver as suas licenças iOS/iPadOS Volume Purchase Program (VPP). Para obter mais informações, consulte:
  - [aplicações iOS/iPadOS compradas em volume](vpp-apps-ios.md)
- **Certificado empresarial do Windows**: aplique ou veja o estado de um certificado de assinatura de código que serve para distribuir aplicações de linha de negócio nos dispositivos Windows geridos.
- **Certificado da Symantec do Windows**: aplique ou veja o estado de um certificado de assinatura de código da Symantec, que é preciso para distribuir ficheiros appx de XAP e WP8.x aos dispositivos Windows 10 Mobile.
- **Microsoft Store para Empresas**: configure a integração na Microsoft Store para Empresas. Em seguida, pode sincronizar com o Intune as aplicações compradas, atribuí-las e controlar a utilização das suas licenças. Para obter mais informações, consulte:
  - [Aplicações compradas em volume na Microsoft Store para Empresas](windows-store-for-business.md).
- **Chaves de sideloading do Windows**: adicione uma chave de sideloading do Windows que pode utilizar para instalar uma aplicação diretamente nos dispositivos, em vez de publicar e transferir a aplicação da Loja Windows. Para obter mais informações, consulte:
  - [Fazer sideload de uma aplicação Windows](app-sideload-windows.md).
- **Imagem corporativa do Portal da Empresa**: personalize o Portal da Empresa para lhe dar a imagem corporativa da sua empresa. Para obter mais informações, consulte:
  - [Configuração do Portal da Empresa](company-portal-app.md).
- **Categorias de aplicações**: adicione, afixe e elimine nomes de categorias de aplicações.
- **Perfil de trabalho do Android**: aprove e sincronize as aplicações que aprovou para a sua empresa. Para obter mais informações, consulte:
  - [Aplicações do perfil de trabalho do Android](apps-add-android-for-work.md).

### <a name="help-and-support"></a>Ajuda e suporte
- **Ajuda e suporte**: resolva problemas, peça suporte ou veja o estado do Intune. Para obter mais informações, consulte:
  - [Resolver problemas](../fundamentals/help-desk-operators.md).

## <a name="next-steps"></a>Próximos passos

- [Adicionar uma aplicação ao Microsoft Intune](apps-add.md)
