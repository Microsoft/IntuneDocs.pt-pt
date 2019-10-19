---
title: Cenário guiado – implantar o Microsoft Edge para dispositivos móveis
titleSuffix: Microsoft Intune
description: Saiba mais sobre o cenário guiado para implantar o Microsoft Edge para dispositivos móveis no portal de gerenciamento de dispositivos Microsoft 365.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e86f3a469169e7a805cb3f56e570ba4d3a90e925
ms.sourcegitcommit: 0be25b59c8e386f972a855712fc6ec3deccede86
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72585889"
---
# <a name="guided-scenario---deploy-microsoft-edge-for-mobile"></a>Cenário guiado – implantar o Microsoft Edge para dispositivos móveis 

Seguindo este [cenário guiado](~/fundamentals/guided-scenarios-overview.md), você pode atribuir o aplicativo Microsoft Edge a seus usuários em dispositivos IOS ou Android na sua organização. A atribuição desse aplicativo permitirá que os usuários procurem conteúdo diretamente usando seus dispositivos corporativos. 

O Microsoft Edge permite que os usuários passem pela desordem da Web com recursos internos que os ajudam a consolidar, organizar e gerenciar o conteúdo do trabalho. Os usuários de dispositivos iOS e Android que entram com suas contas corporativas do Azure AD no aplicativo Microsoft Edge encontrarão seu navegador pré-carregado com os **favoritos** e os filtros de site que você definir.

> [!NOTE]
> Se você tiver bloqueado os usuários de registrar dispositivos iOS ou Android, esse cenário não habilitará o registro e os usuários precisarão instalar o Edge para si mesmos.
Os seguintes recursos do Microsoft Edge Enterprise que são habilitados pelas políticas do Intune incluem: 

- **Identidade Dupla** – os utilizadores podem adicionar uma conta profissional e conta pessoal para navegação. Não há uma separação total entre as duas identidades, semelhante à arquitetura e à experiência no Office 365 e no Outlook. Os administradores do Intune poderão definir as políticas pretendidas para uma experiência de navegação protegida na conta profissional. 
- **Integração de políticas de proteção de aplicações do Intune** – os administradores agora podem aplicar políticas de proteção de aplicações ao Microsoft Edge, incluindo o controlo das ações de cortar, copiar e colar, ao impedir as capturas de ecrã e ao garantir que as ligações selecionadas pelo utilizador abrem apenas noutras aplicações geridas.
- **Integração do Proxy de Aplicações do Azure** – os administradores podem controlar o acesso a aplicações SaaS e aplicações Web, ao ajudar a garantir que as aplicações baseadas no browser são executadas apenas no browser Microsoft Edge seguro, quer os utilizadores finais se liguem a partir da rede empresarial ou a partir da Internet. 
- **Favoritos Geridos e atalhos da Home Page** – Para facilidade de acesso, os administradores podem definir URLs para serem apresentadas nos Favoritos quando os utilizadores finais estão no contexto empresarial. Os administradores podem definir um atalho de home page, que será mostrado como atalho primário quando o utilizador empresarial abre uma nova página ou um novo separador no Microsoft Edge.

## <a name="prerequisites"></a>Pré-requisitos

- [Definir a autoridade de MDM para o Intune](mdm-authority-set.md#set-mdm-authority-to-intune) – a configuração de autoridade de gerenciamento de dispositivo móvel (MDM) determina como você gerencia seus dispositivos. Como administrador de TI, tem de definir uma autoridade de MDM antes de os utilizadores poderem inscrever dispositivos para gestão.
- Permissões de administrador do Intune necessárias:
    - Aplicativos gerenciados ler, criar, excluir e atribuir permissões
    - Aplicativos móveis ler, criar e atribuir permissões
    - Política define permissões de leitura, criação e atribuição
    - Leitura da organização, permissão de atualização

## <a name="step-1---introduction"></a>Etapa 1-Introdução

Seguindo o cenário **de implantação do Microsoft Edge para dispositivos móveis** , você configurará uma implantação básica do Microsoft Edge para um grupo selecionado de usuários do IOS e Android. Essa implantação implementará **a identidade dupla** e os **atalhos gerenciados e a página inicial**. Além disso, os dispositivos registrados pelos usuários selecionados terão automaticamente o aplicativo Microsoft Edge instalado pelo Intune. Essa instalação automática ocorrerá em todos os tipos de registro controlados pelo usuário, que incluem: 
- registro do iOS por meio do aplicativo Portal da Empresa 
- registro de afinidade de usuário do iOS por meio do Apple Business Manager 
- Registro do Android herdado por meio do aplicativo Portal da Empresa 

Esse cenário guiado habilitará automaticamente **myapps** a aparecer nos favoritos do Microsoft Edge e configurará o navegador com a mesma identidade visual que você definiu para o aplicativo portal da empresa do Intune. 

### <a name="what-you-will-need-to-continue"></a>O que será necessário para continuar
Perguntaremos sobre os favoritos do local de trabalho de que seus usuários precisam e os filtros necessários para a navegação na Web. Certifique-se de concluir as seguintes tarefas antes de continuar:

- Adicionar usuários aos grupos do Azure AD. Para obter mais informações, consulte [criar um grupo básico e adicionar membros usando Azure Active Directory](https://go.microsoft.com/fwlink/?linkid=2102458).
- Registrar dispositivos iOS ou Android no Intune. Para obter mais informações, consulte [registro de dispositivo](https://go.microsoft.com/fwlink/?linkid=2102547).
- Reúna uma lista de favoritos do local de trabalho a serem adicionados ao Microsoft Edge.
- Reúna uma lista de filtros do site para impor no Microsoft Edge.

## <a name="step-2---basics"></a>Etapa 2-noções básicas

Nesta etapa, você deve inserir um nome e uma descrição para as novas políticas do Microsoft Edge. Essas políticas poderão ser referenciadas posteriormente se você precisar alterar as atribuições e as configurações. O cenário guiado adicionará e atribuirá um aplicativo iOS do Microsoft Edge para seus dispositivos iOS e um aplicativo Android do Microsoft Edge para seus dispositivos Android. Além disso, esta etapa criará políticas de configuração para esses aplicativos.

## <a name="step-3---configuration"></a>Etapa 3-configuração

Nesta etapa, o cenário guiado configurará o Microsoft Edge para mostrar todos os outros aplicativos atribuídos aos usuários por meio do Intune e compartilhará a mesma identidade visual do aplicativo Portal da Empresa Microsoft Intune. Você pode configurar o Microsoft Edge com uma **URL de atalho de Home Page**, uma lista de **indicadores gerenciados**e uma lista de **URLs bloqueadas**. A **URL de atalho da Home Page** aparecerá para os usuários como o primeiro ícone abaixo da barra de pesquisa quando abrirem uma nova guia no Microsoft Edge em seu dispositivo. Os **indicadores gerenciados** são uma lista de URLs favoritas para que os usuários tenham disponibilidade ao usar o Microsoft Edge em seu contexto de trabalho. As **URLs bloqueadas** especificam os sites que são bloqueados para seus usuários enquanto estiverem em seu contexto de trabalho. Todos os outros sites serão permitidos. 

## <a name="step-4---assignments"></a>Etapa 4-atribuições

Nesta etapa, você pode escolher os grupos de usuários que deseja incluir para que o Microsoft Edge Mobile seja configurado para o trabalho. O Microsoft Edge também será instalado em todos os dispositivos iOS e Android registrados por esses usuários.

## <a name="step-5---review--create"></a>Etapa 5-examinar + criar

A etapa final permite que você examine um resumo das configurações que você configurou. Depois de revisar suas escolhas, clique em **criar** para concluir o cenário guiado. 

> [!NOTE]
> A borda pode levar até 12 horas para receber a configuração. Para obter mais informações, consulte [políticas de configuração de aplicativo para Microsoft Intune](~/apps/app-configuration-policies-overview.md).

> [!IMPORTANT]
> Depois que o cenário guiado for concluído, ele exibirá um resumo. Você pode modificar os recursos listados no resumo posteriormente, no entanto, a tabela que está exibindo esses recurso não será salva.

## <a name="next-steps"></a>Próximos passos

- Aprimore a segurança do uso do Microsoft Edge Configurando a integração da política de proteção de aplicativo do Intune. Para obter mais informações, consulte [políticas de proteção de aplicativo para o Microsoft Edge](~/apps/manage-microsoft-edge.md#application-protection-policies-for-microsoft-edge).
- Se você tiver sites de intranet para incluir, explore a proteção de acesso com Aplicativo Azure integração de proxy. Para obter mais informações, consulte [definir configurações de proxy de aplicativo para o Microsoft Edge](~/apps/manage-microsoft-edge.md#configure-application-proxy-settings-for-microsoft-edge).

