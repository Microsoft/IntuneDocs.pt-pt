---
title: Cenário guiado - Implementar Microsoft Edge para Mobile
titleSuffix: Microsoft Intune
description: Conheça o cenário orientado para implementar o Microsoft Edge para Mobile a partir do portal de Gestão de Dispositivos Microsoft 365.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/09/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9afb8f431ae301fe74f420c11205a7ed2637434b
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514630"
---
# <a name="guided-scenario---deploy-microsoft-edge-for-mobile"></a>Cenário guiado - Implementar Microsoft Edge para Mobile 

Seguindo este [cenário guiado,](~/fundamentals/guided-scenarios-overview.md)pode atribuir a aplicação Microsoft Edge aos seus utilizadores em dispositivos iOS/iPadOS ou Android na sua organização. A atribuição desta aplicação permitirá aos seus utilizadores navegar em perfeitas condições através dos seus dispositivos corporativos. 

O Microsoft Edge permite que os utilizadores cortem a confusão da web com funcionalidades incorporadas que os ajudam a consolidar, organizar e gerir conteúdos de trabalho. Os utilizadores de dispositivos iOS/iPadOS e Android que se inscrevam nas suas contas ad's corporativas Azure na aplicação Microsoft Edge encontrarão o seu navegador pré-carregado com **os favoritos** e filtros do site que define.

> [!NOTE]
> Se tiver impedido os utilizadores de inscreverem dispositivos iOS/iPadOS ou Android, este cenário não permitirá a inscrição e os utilizadores terão de instalar o Edge para si próprios.
As seguintes funcionalidades da empresa Microsoft Edge que são ativadas pelas políticas intune incluem: 

- **Identidade Dupla** – os utilizadores podem adicionar uma conta profissional e conta pessoal para navegação. Não há uma separação total entre as duas identidades, semelhante à arquitetura e à experiência no Office 365 e no Outlook. Os administradores do Intune poderão definir as políticas pretendidas para uma experiência de navegação protegida na conta profissional. 
- **Integração de políticas de proteção de aplicações do Intune** – os administradores agora podem aplicar políticas de proteção de aplicações ao Microsoft Edge, incluindo o controlo das ações de cortar, copiar e colar, ao impedir as capturas de ecrã e ao garantir que as ligações selecionadas pelo utilizador abrem apenas noutras aplicações geridas.
- **Integração do Proxy de Aplicações do Azure** – os administradores podem controlar o acesso a aplicações SaaS e aplicações Web, ao ajudar a garantir que as aplicações baseadas no browser são executadas apenas no browser Microsoft Edge seguro, quer os utilizadores finais se liguem a partir da rede empresarial ou a partir da Internet. 
- **Favoritos Geridos e atalhos da Home Page** – Para facilidade de acesso, os administradores podem definir URLs para serem apresentadas nos Favoritos quando os utilizadores finais estão no contexto empresarial. Os administradores podem definir um atalho de home page, que será mostrado como atalho primário quando o utilizador empresarial abre uma nova página ou um novo separador no Microsoft Edge.

## <a name="prerequisites"></a>Pré-requisitos

- [Defina a autoridade do MDM para Intune](mdm-authority-set.md#set-mdm-authority-to-intune) - A definição de autoridade de gestão de dispositivos móveis (MDM) determina como gere os seus dispositivos. Como administrador de TI, tem de definir uma autoridade de MDM antes de os utilizadores poderem inscrever dispositivos para gestão.
- Permissões intonantes da Administração necessárias:
    - Aplicações geridas lêem, criam, eliminam e atribuem permissões
    - Aplicativos móveis lêem, criam e atribuem permissões
    - Conjuntos de políticas ler, criar e atribuir permissões
    - Organização ler, atualizar permissão

## <a name="step-1---introduction"></a>Passo 1 - Introdução

Ao seguir o cenário guiado pela Implementação do **Microsoft Edge para mobile,** irá configurar uma implementação básica do Microsoft Edge para um grupo selecionado de utilizadores iOS/iPadOS e Android. Esta implementação implementará os favoritos de **dupla identidade** e **geridos e atalhos de página inicial.** Além disso, os dispositivos matriculados pelos utilizadores selecionados terão automaticamente a aplicação Microsoft Edge instalada pela Intune. Esta instalação automática ocorrerá em todos os tipos de inscrições orientados pelo utilizador, que incluem: 
- inscrição iOS/iPadOS através da aplicação Portal da Empresa 
- inscrição iOS/iPadOS de afinidade de utilizadores através do Apple Business Manager 
- Inscrição do Legacy Android através da App Portal da Empresa 

Este cenário guiado permitirá automaticamente que o **MyApps** apareça nos favoritos do Microsoft Edge e configure o navegador com a mesma marca que definiu para a aplicação Intune Company Portal. 

### <a name="what-you-will-need-to-continue"></a>O que precisa para continuar
Vamos perguntar-lhe sobre os favoritos do local de trabalho que os seus utilizadores precisam, e os filtros que você precisa para navegar na web. Certifique-se de que completa as seguintes tarefas antes de continuar:

- Adicione utilizadores a grupos De AD Azure. Para mais informações, consulte [Criar um grupo básico e adicionar membros usando o Diretório Ativo Azure](https://go.microsoft.com/fwlink/?linkid=2102458).
- Inscreva dispositivos iOS/iPadOS ou Android no Intune. Para mais informações, consulte a [inscrição do Dispositivo.](https://go.microsoft.com/fwlink/?linkid=2102547)
- Reúna uma lista de favoritos no local de trabalho para adicionar no Microsoft Edge.
- Reúna uma lista de filtros do site para impor no Microsoft Edge.

## <a name="step-2---basics"></a>Passo 2 - Básicos

Neste passo, deve introduzir um nome e descrição para as suas novas políticas do Microsoft Edge. Estas políticas podem ser referenciadas mais tarde se precisar de alterar as atribuições e configurações. O cenário guiado irá adicionar e atribuir tanto uma aplicação Microsoft Edge iOS/iPadOS para os seus dispositivos iOS/iPadOS e uma aplicação Microsoft Edge Android para os seus dispositivos Android. Além disso, este passo irá criar políticas de configuração para estas aplicações.

## <a name="step-3---configuration"></a>Passo 3 - Configuração

Neste passo, o cenário guiado configurará o Microsoft Edge para mostrar todas as outras aplicações atribuídas aos utilizadores através do Intune e partilhar a mesma marca que a aplicação Microsoft Intune Company Portal. Pode configurar ainda mais o Microsoft Edge com um URL de atalho de **página inicial,** uma lista de **marcadores geridos**e uma lista de **URLs Bloqueados**. O URL de **atalho** da página inicial aparecerá para os utilizadores como o primeiro ícone por baixo da barra de pesquisa quando abrirem um novo separador no Microsoft Edge no seu dispositivo. Os **Bookmarks Geridos** são uma lista de URLs favoritos para os seus utilizadores terem disponível quando utilizarem o Microsoft Edge no seu contexto de trabalho. Os **URLs Bloqueados** especificam os sites que estão bloqueados para os seus utilizadores durante o seu contexto de trabalho. Todos os outros sites serão permitidos. 

## <a name="step-4---assignments"></a>Passo 4 - Atribuições

Neste passo, pode escolher os grupos de utilizadores que pretende incluir para ter o Microsoft Edge móvel configurado para o trabalho. O Microsoft Edge também será instalado em todos os dispositivos iOS/iPadOS e Android matriculados por estes utilizadores.

## <a name="step-5---review--create"></a>Passo 5 - Rever + criar

O passo final permite-lhe rever um resumo das definições configuradas. Depois de ter revisto as suas escolhas clique **em Criar** para completar o cenário guiado. 

> [!NOTE]
> A borda pode demorar até 12 horas para receber a configuração. Para mais informações, consulte as políticas de [configuração da App para o Microsoft Intune](~/apps/app-configuration-policies-overview.md).

> [!IMPORTANT]
> Uma vez concluído o cenário guiado, apresentará um resumo. Pode modificar os recursos listados no resumo mais tarde, no entanto a tabela que exibe estas resouces não será guardada.

## <a name="next-steps"></a>Próximos passos

- Aumente a segurança da utilização do Microsoft Edge, criando a integração da política de proteção de aplicações Intune. Para mais informações, consulte as políticas de [proteção de aplicações para o Microsoft Edge](~/apps/manage-microsoft-edge.md#application-protection-policies-for-microsoft-edge).
- Se tiver sites intranet para incluir, explore a proteção do acesso com a integração do Proxy de Aplicação Azure. Para mais informações, consulte as definições de Proxy de [Aplicação Configurada para o Microsoft Edge](~/apps/manage-microsoft-edge.md#configure-application-proxy-settings-for-microsoft-edge).

