---
title: Definições de quiosque para Windows 10 no Microsoft Intune – Azure | Microsoft Docs
description: Saiba que definições do Intune pode utilizar para controlar as definições e funcionalidades em dispositivos a executar o Windows 10.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 5/24/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 897ff48253961d6e1aa83bf36113c362d4548fbf
ms.sourcegitcommit: 97b9f966f23895495b4c8a685f1397b78cc01d57
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34745180"
---
# <a name="kiosk-settings-for-windows-10-and-later-in-intune"></a>Definições de quiosque para Windows 10 (e posterior) no Intune

Os perfis de quiosque podem ser utilizados para configurar dispositivos com o Windows 10 para executar uma aplicação ou múltiplas aplicações. Quando configura um perfil de quiosque, também pode optar por apresentar um menu Iniciar, instalar um browser e outras opções.

## <a name="kiosk-settings"></a>Definições de quiosque

1. Selecione **Adicionar** para criar um ambiente de quiosque.
2. Introduza o **Nome da configuração do quiosque** para o seu quiosque. Este nome identifica um grupo de aplicações, o esquema destas aplicações no menu Iniciar e os utilizadores que estão atribuídos a esta configuração de quiosque.
3. Selecione o **Modo de quiosque**. **Modo de quiosque**: identifica o tipo de modo de quiosque suportado pela política. As opções incluem:

  - **Não configurado** (predefinição): a política não ativa um modo de quiosque.
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

  - **Mostrar botão Início**: mostre (**Exigir**) ou oculte (**Não configurado**) o botão Início do browser do quiosque. Por predefinição, o botão não está configurado.

  - **Mostrar botões de navegação**: mostre (**Exigir**) ou oculte (**Não configurado**) os botões para retroceder e avançar. Por predefinição, os botões de navegação não estão configurados.

  - **Atualize o browser quando o utilizador excede o limite de tempo de inatividade**: introduza o período de tempo de inatividade de sessão em minutos até o browser do quiosque reiniciar num estado novo. O valor deve estar compreendido entre 1 e 1440 minutos. Por predefinição, o valor está vazio ou em branco, o que significa que não existe nenhum limite de tempo de inatividade.

  - **Sites bloqueados**: lista de URLs de sites bloqueados (com suporte de carateres universais). Utilize esta definição para impedir que o browser abra sites específicos. Também pode **Importar** um ficheiro .csv que contenha uma lista. Em alternativa, pode criar um ficheiro .csv (**Exportar**) que contenha os sites a adicionar.

  - **Exceções de site**: lista de exceções dos URLs de sites bloqueados (com suporte de carateres universais). Utilize esta definição para permitir que o browser abra sites específicos. Estas exceções são um subconjunto dos URLs bloqueados. Se um URL estiver na lista de sites bloqueados e na lista de exceções de sites, a exceção tem precedência.

    Também pode **Importar** um ficheiro .csv que contenha uma lista. Em alternativa, pode criar um ficheiro .csv (**Exportar**) que contenha os sites a adicionar.

2. Selecione **OK** para guardar as alterações.

## <a name="next-steps"></a>Próximos passos
[Atribua o perfil](device-profile-assign.md) e [monitorize o respetivo estado](device-profile-monitor.md).