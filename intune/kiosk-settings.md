---
title: Definições de quiosque para Windows 10 no Microsoft Intune – Azure | Microsoft Docs
description: Configure os seus dispositivos com o Windows 10 (e posterior) como quiosques de uma aplicação e várias aplicações ao personalizar o menu Iniciar, adicionar aplicações e a barra de tarefas e configurar um browser. Configure também os dispositivos com o Windows Holographic for Business como quiosques de várias aplicações no Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 8/2/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 6db58b1b1f19f789a2163f497c1f0da4c7c034a5
ms.sourcegitcommit: 5f6117b83f96f7d93dde3685c2ff2b67ae53740b
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/03/2018
ms.locfileid: "39481126"
---
# <a name="kiosk-settings-for-windows-10-and-later-in-intune"></a>Definições de quiosque para Windows 10 (e posterior) no Intune

Os perfis de quiosque são utilizados para configurar dispositivos com o Windows 10 para executar uma aplicação ou múltiplas aplicações. Quando cria um perfil de quiosque, também pode optar por apresentar um menu Iniciar, instalar um browser e mais.

## <a name="kiosk-settings"></a>Definições de quiosque

1. No [portal do Azure](https://portal.azure.com), selecione **Todos os Serviços**, filtre o **Intune** e selecione **Microsoft Intune**.
2. Selecione **Configuração do dispositivo** > **Perfis** > **Criar Perfil**.
3. Introduza as seguintes propriedades:

   - **Nome**: introduza um nome descritivo para o novo perfil.
   - **Descrição:** introduza uma descrição para o perfil. A descrição é opcional, mas recomendada.
   - **Plataforma**: selecione **Windows 10 e posterior**
   - **Tipo de perfil**: selecione **Quiosque (Pré-visualização)**
   
4. Selecione **Quiosque** > **Adicionar**.
5. Introduza o **Nome da configuração do quiosque** para o seu quiosque. Este nome identifica um grupo de aplicações, o esquema destas aplicações no menu Iniciar e os utilizadores que estão atribuídos a esta configuração de quiosque.
6. Selecione o **Modo de quiosque**. O **modo de quiosque** identifica o tipo de modo de quiosque suportado pela política. As opções incluem:

    - **Não configurado** (predefinição): a política não ativa o modo de quiosque.
    - **Quiosque de uma aplicação em ecrã inteiro**: o perfil permite que o dispositivo seja executado como uma única conta de utilizador e só permite a execução de uma única aplicação da Plataforma Universal do Windows (UWP). Quando o utilizador inicia sessão, é iniciada uma aplicação específica. Este modo também impede que o utilizador abra novas aplicações ou mude a aplicação em execução.
    - **Quiosque de várias aplicações**: o perfil permite que o dispositivo execute múltiplas aplicações da Plataforma Universal do Windows (UWP) ou aplicações Win32. Também pode atribuir diferentes aplicações a contas de utilizador diferentes. Apenas as aplicações que adicionar estarão disponíveis para os utilizadores. A vantagem de um quiosque de várias aplicações ou dispositivos de objetivo fixo é o facto de proporcionar uma experiência fácil de compreender pelos utilizadores através do acesso às aplicações de que precisam. Além disso, também não lhes permite ver as aplicações de que não precisam.

#### <a name="single-full-screen-app-kiosks"></a>Quiosques de uma aplicação em ecrã inteiro
Introduza as seguintes definições:

- **Identificador de aplicação de Plataforma Universal do Windows (UWP)**: introduza o **ID do modelo do utilizador (AUMID)** da aplicação de quiosque. Também pode selecionar uma aplicação gerida existente que tenha adicionado com das [Aplicações Móveis](apps-add.md).

    Veja [Find the Application User Model ID of an installed app](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app) (Localizar o ID de Modelo do Utilizador da Aplicação de uma aplicação instalada).

- **Tipo de conta de utilizador**: as suas opções:

  - **Início de sessão automático**: para ambientes de quiosque com início de sessão automático ativado, deve ser utilizado um utilizador com o menor privilégio (tal como a conta de utilizador padrão local). Para configurar uma conta do Azure Active Directory (AD) para o modo de quiosque, utilize o formato `AzureAD\user@contoso.com`.
  - **Conta de utilizador local**: introduza a conta de utilizador local (no dispositivo) ou o início de sessão de conta do Azure AD associado à aplicação de quiosque. Para contas associadas a domínios do Azure AD, introduza a conta com o formato `domain\username@tenant.org`.

#### <a name="multi-app-kiosks"></a>Quiosques de várias aplicações
As aplicações neste modo estão disponíveis no menu Iniciar. Estas aplicações são as únicas aplicações que o utilizador pode abrir. 

Os [quiosques de várias aplicações](https://docs.microsoft.com/windows/configuration/lock-down-windows-10-to-specific-apps#configure-a-kiosk-in-microsoft-intune) utilizam uma configuração de quiosque que apresenta uma lista de aplicações permitidas e outras definições.

Introduza as seguintes definições:

- **Adicionar aplicação Win32**: uma aplicação Win32 é uma aplicação de ambiente de trabalho tradicional. Introduza o **Nome da aplicação**, e o **Identificador**. O **Identificador** é o nome do caminho absoluto do ficheiro executável, relativamente ao dispositivo.
- **Adicionar aplicações geridas**: selecione uma aplicação gerida existente que tenha adicionado com as [Aplicações Móveis no Intune](apps-add.md).
- **Adicionar aplicação por AUMID**: introduza o [AUMID da aplicação](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app) (aplicações da UWP).
- **Barra de tarefas** – selecione a opção para **Ativar** (mostrar) a barra de tarefas ou mantenha-a definida como **Não configurado** (ocultar) no quiosque.
- **Esquema do menu Iniciar**: introduza um ficheiro XML que descreva como as aplicações são apresentadas no menu Iniciar, incluindo a ordem das aplicações. O artigo [Customize and export Start layout (Personalizar e exportar o esquema do menu Iniciar)](https://docs.microsoft.com/windows/configuration/customize-and-export-start-layout) fornece algumas orientações e um ficheiro XML de exemplo.

  O artigo [Create a Windows 10 kiosk that runs multiple apps (Criar um quiosque do Windows 10 que execute várias aplicações)](https://docs.microsoft.com/windows/configuration/lock-down-windows-10-to-specific-apps#create-xml-file) fornece mais detalhes sobre como utilizar e criar ficheiros XML.

- **Tipo de conta de utilizador**: adicione uma ou mais contas de utilizador que poderão utilizar as aplicações que adicionar. Quando a conta iniciar sessão, apenas as aplicações definidas na configuração estarão disponíveis. A conta para o dispositivo pode ser local ou um início de sessão de conta do Azure AD associado à aplicação de local público.

    Para ambientes de quiosque com início de sessão automático ativado, deve ser utilizado um tipo de utilizador com o menor privilégio (tal como a conta de utilizador padrão local). Para configurar uma conta do Azure Active Directory (AD) para o modo de quiosque, utilize o formato `domain\user@tenant.com`.

## <a name="kiosk-web-browser-settings"></a>Definições do browser do quiosque

Estas definições controlam uma aplicação de browser no quiosque. Certifique-se de que implementou uma aplicação de browser para os dispositivos de quiosque com as [Aplicações Móveis](apps-add.md).

1. Introduza as seguintes definições:

    - **URL da home page predefinido**: introduza o URL predefinido que o browser do quiosque abre quando o browser é aberto ou reiniciado.

    - **Botão de início**: mostra (**Permitir**) ou oculta (**Não configurado**) o botão Início do browser do quiosque. Por predefinição, o botão não está configurado.

    - **Botão de navegação**: mostra (**Permitir**) ou oculta (**Não configurado**) os botões para retroceder e avançar. Por predefinição, os botões de navegação não estão configurados.

    - **Botão de terminar sessão**: mostra (**Permitir**) ou oculta (**Não configurado**) o botão para terminar a sessão. Quando o botão é apresentado, o utilizador seleciona-o e a aplicação pede para terminar a sessão. Ao confirmar, o browser limpa todos os dados de navegação (cookies, cache, etc.) e regressa ao URL predefinido. Por predefinição, o botão não está configurado. 

    - **Atualize o browser quando o utilizador excede o limite de tempo de inatividade**: introduza o período de tempo de inatividade de sessão em minutos até o browser do quiosque reiniciar num estado novo. O valor deve estar compreendido entre 1 e 1440 minutos. Por predefinição, o valor está vazio ou em branco, o que significa que não existe nenhum limite de tempo de inatividade.

    - **Sites bloqueados**: lista de URLs de sites bloqueados (com suporte de carateres universais). Utilize esta definição para impedir que o browser abra sites específicos. Também pode **Importar** um ficheiro .csv que contenha uma lista. Em alternativa, pode criar um ficheiro .csv (**Exportar**) que contenha os sites a adicionar.

    - **Exceções de site**: lista de exceções dos URLs de sites bloqueados (com suporte de carateres universais). Utilize esta definição para permitir que o browser abra sites específicos. Estas exceções são um subconjunto dos URLs bloqueados. Se um URL estiver na lista de sites bloqueados e na lista de exceções de sites, a exceção tem precedência.

    Também pode **Importar** um ficheiro .csv que contenha uma lista. Em alternativa, pode criar um ficheiro .csv (**Exportar**) que contenha os sites a adicionar.

2. Selecione **OK** para guardar as alterações.

## <a name="windows-holographic-for-business"></a>Windows Holographic for Business

Em dispositivos com o Windows Holographic for Business, pode configurar estes dispositivos para serem executados em modo de quiosque de uma aplicação ou modo de quiosque de várias aplicações. 

#### <a name="single-full-screen-app-kiosks"></a>Quiosques de uma aplicação em ecrã inteiro
Introduza as seguintes definições:

- **Identificador de aplicação de Plataforma Universal do Windows (UWP)**: introduza o **ID do modelo do utilizador (AUMID)** da aplicação de quiosque. Também pode selecionar uma aplicação gerida existente que tenha adicionado com das [Aplicações Móveis](apps-add.md).

    Veja [Find the Application User Model ID of an installed app (Localizar o ID de Modelo do Utilizador da Aplicação de uma aplicação instalada)](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app) para obter o ID.

- **Tipo de conta de utilizador**: Selecione **Conta de utilizador local** para introduzir a conta de utilizador local (no dispositivo) ou a conta Microsoft associada à aplicação de quiosque. Os tipos de conta de utilizador de **início de sessão automático** não são suportados pelo Windows Holographic for Business.

#### <a name="multi-app-kiosks"></a>Quiosques de várias aplicações
As aplicações neste modo estão disponíveis no menu Iniciar. Estas aplicações são as únicas aplicações que o utilizador pode abrir.

Introduza as seguintes definições:

- **Adicionar aplicações geridas**: selecione uma aplicação gerida existente que tenha adicionado com as [Aplicações Móveis no Intune](apps-add.md).
- **Adicionar aplicação por AUMID**: introduza o [AUMID da aplicação](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app) (aplicações da UWP).
- **Esquema do menu Iniciar**: introduza um ficheiro XML que descreva como as aplicações são apresentadas no menu Iniciar, incluindo a ordem das aplicações. O artigo [Customize and export start layout (Personalizar e exportar o esquema do menu Iniciar)](https://docs.microsoft.com/hololens/hololens-kiosk#start-layout-for-hololens) dá algumas orientações e inclui um ficheiro XML específico para dispositivos com o Windows Holographic for Business.
- **Tipo de conta de utilizador**: adicione uma ou mais contas de utilizador que poderão utilizar as aplicações que adicionar. As opções suportadas são as seguintes: 
  - **Visitante do HoloLens**: A conta de visitante é uma conta de convidado que não necessita de credenciais ou de autenticação do utilizador, como está descrito em [Shared PC mode concepts (Conceitos de modo de PC partilhado)](https://docs.microsoft.com/windows/configuration/set-up-shared-or-guest-pc#shared-pc-mode-concepts).
  - **Utilizadores do Azure AD**: São necessárias credenciais de utilizador para iniciar sessão no dispositivo. Utilize o formato `domain\user@tenant.com`.
  - **Contas de Utilizador Local**: são necessárias credenciais de utilizador para iniciar sessão no dispositivo. 

Quando a conta iniciar sessão, apenas as aplicações definidas na configuração estarão disponíveis.

## <a name="next-steps"></a>Próximos passos
[Atribua o perfil](device-profile-assign.md) e [monitorize o respetivo estado](device-profile-monitor.md).
