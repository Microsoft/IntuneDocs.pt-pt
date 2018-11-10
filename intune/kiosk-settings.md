---
title: Definições de quiosque para Windows 10 no Microsoft Intune – Azure | Microsoft Docs
description: Configure os seus dispositivos com o Windows 10 (e posterior) como quiosques de uma aplicação e de várias aplicações, incluindo personalizar o menu Iniciar, adicionar aplicações e a barra de tarefas e configurar um browser. Configure também os dispositivos com o Windows Holographic for Business como quiosques de várias aplicações no Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/17/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: b3de4d79e6121505718a75ffe64102bb1bc18347
ms.sourcegitcommit: 244456907e3ab4a4389d32d06060606a9591cfba
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/01/2018
ms.locfileid: "50751648"
---
# <a name="kiosk-settings-for-windows-10-and-later-in-intune"></a>Definições de quiosque para Windows 10 (e posterior) no Intune

Em dispositivos Windows 10, pode utilizar o Intune para executar estes dispositivos como um quiosque. O quiosque pode executar uma ou muitas aplicações. Também pode mostrar e personalizar um menu Iniciar, adicionar aplicações diferentes, incluindo aplicações Win32, adicionar uma home page específica para um browser e muito mais. 

Utilize os passos neste artigo para criar um quiosque de uma ou de várias aplicações no Intune.

O Intune suporta um perfil de quiosque por dispositivo. Se precisar de vários perfis de quiosque num só dispositivo, poderá utilizar um [OMA-URI personalizado](custom-settings-windows-10.md).

## <a name="kiosk-settings"></a>Definições de quiosque

1. No [portal do Azure](https://portal.azure.com), selecione **Todos os Serviços**, filtre o **Intune** e selecione **Microsoft Intune**.
2. Selecione **Configuração do dispositivo** > **Perfis** > **Criar Perfil**.
3. Introduza as seguintes propriedades:

   - **Nome**: introduza um nome descritivo para o novo perfil.
   - **Descrição:** introduza uma descrição para o perfil. Esta definição é opcional, mas recomendada.
   - **Plataforma**: selecione **Windows 10 e posterior**
   - **Tipo de perfil**: selecione **Quiosque (Pré-visualização)**

4. Selecione um **modo de quiosque**. O **modo de quiosque** identifica o tipo de modo de quiosque suportado pela política. As opções incluem:

    - **Não configurado** (predefinição): a política não ativa o modo de quiosque.
    - **Quiosque de uma aplicação de ecrã inteiro**: o dispositivo é executado como uma única conta de utilizador e bloqueia-a para uma única aplicação da Loja. Quando o utilizador inicia sessão, é iniciada uma aplicação específica. Este modo também impede que o utilizador abra novas aplicações ou mude a aplicação em execução.
    - **Quiosque de várias aplicações**: o dispositivo executa várias aplicações da Loja, aplicações Win32 ou aplicações do Windows da caixa de entrada através do ID do Modelo de Utilizador da Aplicação (AUMID). Apenas as aplicações que adicionar estarão disponíveis no dispositivo.

        A vantagem de um quiosque de várias aplicações ou dispositivos de objetivo fixo é o facto de proporcionar uma experiência fácil de compreender pelos utilizadores através do acesso às aplicações de que precisam. Além disso, também não lhes permite ver as aplicações de que não precisam.

## <a name="single-full-screen-app-kiosks"></a>Quiosques de uma aplicação em ecrã inteiro
Ao escolher o modo de quiosque de uma aplicação, introduza as seguintes definições:

- **Tipo de início de sessão do utilizador**: as aplicações que adicionar são executadas como a conta de utilizador que introduzir. As opções são:

  - **Início de sessão automático (Windows 10 versão 1803 e posterior)**: para quiosques em ambientes direcionados para o público que não exigem que o utilizador inicie sessão, semelhante a uma conta de convidado. Esta definição utiliza o [CSP AssignedAccess](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp).
  - **Conta de utilizador local**: introduza a conta de utilizador local (para o dispositivo). A conta que introduzir serve para iniciar sessão no quiosque.

- **Tipo de aplicação**: selecione **Aplicação da Loja**.

- **Aplicação a executar no modo de quiosque**: escolha **Adicionar uma aplicação da loja** e selecione uma aplicação na lista.

    Não tem aplicações listadas? Adicione algumas através dos passos indicados em [Aplicações de Cliente](apps-add.md).

    Selecione **OK** para guardar as alterações.

- **Definições do browser do quiosque**: estas definições controlam uma aplicação de browser no quiosque. Garanta que obtém a [aplicação de browser do quiosque](https://businessstore.microsoft.com/store/details/kiosk-browser/9NGB5S5XG2KP) na Loja, adicione-a ao Intune como uma [Aplicação de Cliente](apps-add.md) e, em seguida, atribua a aplicação aos dispositivos de quiosque.

  Introduza as seguintes definições:

  - **URL da home page predefinido**: introduza o URL predefinido mostrado quando o browser do quiosque abre ou quando o browser é reiniciado. Por exemplo, introduza: `http://bing.com` ou `http://www.contoso.com`.

  - **Botão de início**: **mostre** ou **oculte** o botão de início do browser do quiosque. Por predefinição, o botão não é mostrado.

  - **Botões de navegação**: **mostre** ou **oculte** os botões voltar e avançar. Por predefinição, os botões de navegação não são mostrados.

  - **Botão de terminar sessão**: **mostre** ou **oculte** o botão de terminar sessão. Quando o botão é apresentado, o utilizador seleciona-o e a aplicação pede para terminar a sessão. Ao confirmar, o browser limpa todos os dados de navegação (cookies, cache, etc.) e abre o URL predefinido. Por predefinição, o botão não é mostrado.

  - **Atualizar o browser após um tempo de inatividade**: introduza o período de tempo de inatividade (1-1440 minutos) necessário antes de o browser do quiosque reiniciar num estado novo. O tempo de inatividade é o número de minutos decorridos desde a última interação do utilizador. Por predefinição, o valor está vazio ou em branco, o que significa que não existe nenhum tempo limite de inatividade.

  - **Sites permitidos**: utilize esta definição para permitir que determinados sites sejam abertos. Por outras palavras, utilize esta funcionalidade para restringir ou impedir determinados sites no dispositivo. Por exemplo, pode permitir que todos os sites em `http://contoso.com*` sejam abertos. Por predefinição, todos os sites são permitidos.

    Para permitir sites específicos, carregue um ficheiro .csv que inclua uma lista dos sites permitidos. Se não adicionar um ficheiro .csv, todos os sites serão permitidos. O Intune suporta o * (asterisco) como um caráter universal.

  Selecione **OK** para guardar as alterações.

## <a name="multi-app-kiosks"></a>Quiosques de várias aplicações

As aplicações neste modo estão disponíveis no menu Iniciar. Estas aplicações são as únicas aplicações que o utilizador pode abrir.

Ao escolher o modo de quiosque de várias aplicações, introduza as seguintes definições:

- **Dispositivos Windows 10 no modo S de destino**: escolha **Sim** para permitir as aplicações da loja e as aplicações AUMID (excluindo as aplicações Win32) no perfil de quiosque. Escolha **Não** para permitir as aplicações da loja, as aplicações Win32 e as aplicações AUMID no perfil de quiosque. Quando escolhe **Não**, este perfil de quiosque não é implementado em dispositivos no modo S.

- **Tipo de início de sessão do utilizador**: as aplicações que adicionar são executadas como a conta de utilizador que introduzir. As opções são:

  - **Início de sessão automático (Windows 10 versão 1803 e posterior)**: para quiosques em ambientes direcionados para o público que não exigem que o utilizador inicie sessão, semelhante a uma conta de convidado. Esta definição utiliza o [CSP AssignedAccess](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp).
  - **Conta de utilizador local**: **adicione** a conta de utilizador local (para o dispositivo). A conta que introduzir serve para iniciar sessão no quiosque.
  - **Utilizador ou grupo do Microsoft Azure AD (Windows 10 versão 1803 e posterior)**: selecione **Adicionar** para escolher os utilizadores ou grupos do Microsoft Azure AD na lista. Pode selecionar vários utilizadores e grupos. Escolha **Selecionar** para guardar as alterações.
  - **Visitante do HoloLens**: A conta de visitante é uma conta de convidado que não necessita de credenciais ou de autenticação do utilizador, como está descrito em [Shared PC mode concepts (Conceitos de modo de PC partilhado)](https://docs.microsoft.com/windows/configuration/set-up-shared-or-guest-pc#shared-pc-mode-concepts).

- **Aplicações**: adicione as aplicações que quer executar no dispositivo de quiosque. Lembre-se de que pode adicionar várias aplicações.

  - **Adicionar aplicação da loja**: adicione uma aplicação na Microsoft Store para Empresas. Se não tiver aplicações listadas, poderá obter aplicações e [adicioná-las ao Intune](store-apps-windows.md). Por exemplo, pode adicionar o Browser do Quiosque, Excel, OneNote e muito mais.

  - **Adicionar Aplicação Win32**: uma aplicação Win32 é uma aplicação de ambiente de trabalho tradicional, como o Visual Studio Code ou o Google Chrome. Introduza as seguintes propriedades:

    - **Nome da aplicação**: obrigatório. Introduza um nome para a aplicação.
    - **Caminho local**: obrigatório. Introduza o caminho para o executável, tal como `C:\Program Files (x86)\Microsoft VS Code\Code.exe` ou `C:\Program Files (x86)\Google\Chrome\Application\chrome.exe`.
    - **ID do modelo de utilizador da aplicação (AUMID)**: introduza o ID do modelo de utilizador da aplicação (AUMID) da aplicação Win32. Esta definição determina o esquema de início do mosaico na área de trabalho. Para obter este ID, veja [Find the Application User Model ID of an installed app](https://docs.microsoft.com/powershell/module/startlayout/get-startapps?view=win10-ps) (Localizar o ID do Modelo de Utilizador da Aplicação de uma aplicação instalada).
    - **Tamanho do mosaico**: obrigatório. Escolha um tamanho de mosaico da aplicação: Pequeno, Médio, Largo ou Grande.
  
  - **Adicionar por AUMID**: utilize esta opção para adicionar aplicações do Windows de caixa de entrada, como o Bloco de notas ou a Calculadora. Introduza as seguintes propriedades: 

    - **Nome da aplicação**: obrigatório. Introduza um nome para a aplicação.
    - **ID do modelo de utilizador da aplicação (AUMID)**: obrigatório. Introduza o ID do modelo de utilizador da aplicação (AUMID) da aplicação Windows. Para obter este ID, veja [Find the Application User Model ID of an installed app](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app) (Localizar o ID do Modelo de Utilizador da Aplicação de uma aplicação instalada).
    - **Tamanho do mosaico**: obrigatório. Escolha um tamanho de mosaico da aplicação: Pequeno, Médio, Largo ou Grande.

  > [!TIP]
  > Depois de adicionar todas as aplicações, pode alterar a ordem de apresentação ao clicar e arrastar as aplicações na lista.  

  Selecione **OK** para guardar as alterações.

- **Definições do browser do quiosque**: estas definições controlam uma aplicação de browser no quiosque. Garanta que implementa uma aplicação de browser para os dispositivos de quiosque com as [Aplicações de Cliente](apps-add.md).

  Introduza as seguintes definições:

  - **URL da home page predefinido**: introduza o URL predefinido mostrado quando o browser do quiosque abre ou quando o browser é reiniciado. Por exemplo, introduza: `http://bing.com` ou `http://www.contoso.com`.

  - **Botão de início**: **mostre** ou **oculte** o botão de início do browser do quiosque. Por predefinição, o botão não é mostrado.

  - **Botões de navegação**: **mostre** ou **oculte** os botões voltar e avançar. Por predefinição, os botões de navegação não são mostrados.

  - **Botão de terminar sessão**: **mostre** ou **oculte** o botão de terminar sessão. Quando o botão é apresentado, o utilizador seleciona-o e a aplicação pede para terminar a sessão. Ao confirmar, o browser limpa todos os dados de navegação (cookies, cache, etc.) e abre o URL predefinido. Por predefinição, o botão não é mostrado.

  - **Atualizar o browser após um tempo de inatividade**: introduza o período de tempo de inatividade (1-1440 minutos) necessário antes de o browser do quiosque reiniciar num estado novo. O tempo de inatividade é o número de minutos decorridos desde a última interação do utilizador. Por predefinição, o valor está vazio ou em branco, o que significa que não existe nenhum tempo limite de inatividade.

  - **Sites permitidos**: utilize esta definição para permitir que determinados sites sejam abertos. Por outras palavras, utilize esta funcionalidade para restringir ou impedir determinados sites no dispositivo. Por exemplo, pode permitir que todos os sites em `contoso.com*` sejam abertos. Por predefinição, todos os sites são permitidos.

    Para permitir sites específicos, carregue um ficheiro .csv que inclua uma lista dos sites permitidos. Se não adicionar um ficheiro .csv, todos os sites serão permitidos.

  Selecione **OK** para guardar as alterações.

- **Utilizar o esquema do menu Iniciar alternativo**: escolha **Sim** para introduzir um ficheiro XML que descreva como as aplicações são apresentadas no menu Iniciar, incluindo a ordem das aplicações. Utilize esta opção se precisar de uma personalização adicional no menu Iniciar. O artigo [Customize and export Start layout (Personalizar e exportar o esquema do menu Iniciar)](https://docs.microsoft.com/windows/configuration/customize-and-export-start-layout) fornece algumas orientações e um ficheiro XML de exemplo.

- **Barra de tarefas do Windows**: escolha **Mostrar** ou **Ocultar** a barra de tarefas. Por predefinição, a barra de tarefas não é mostrada.

## <a name="windows-holographic-for-business"></a>Windows Holographic for Business

Em dispositivos com o Windows Holographic for Business, pode configurar estes dispositivos para serem executados em modo de quiosque de uma aplicação ou modo de quiosque de várias aplicações. Algumas funcionalidades não são suportadas no Windows Holographic for Business.

#### <a name="single-full-screen-app-kiosks"></a>Quiosques de uma aplicação em ecrã inteiro
Ao escolher o modo de quiosque de uma aplicação, introduza as seguintes definições:

- **Tipo de início de sessão de utilizador**: selecione **Conta de utilizador local** para introduzir a conta de utilizador local (no dispositivo) ou a Conta Microsoft associada à aplicação de quiosque. Os tipos de conta de utilizador de **início de sessão automático** não são suportados pelo Windows Holographic for Business.

- **Tipo de aplicação**: selecione **Aplicação da Loja**.

- **Aplicação a executar no modo de quiosque**: escolha **Adicionar uma aplicação da loja** e selecione uma aplicação na lista.

    Não tem aplicações listadas? Adicione algumas através dos passos indicados em [Aplicações de Cliente](apps-add.md).

    Selecione **OK** para guardar as alterações.

#### <a name="multi-app-kiosks"></a>Quiosques de várias aplicações
As aplicações neste modo estão disponíveis no menu Iniciar. Estas aplicações são as únicas aplicações que o utilizador pode abrir. Ao escolher o modo de quiosque de várias aplicações, introduza as seguintes definições:

- **Dispositivos Windows 10 no modo S de destino**: escolha **Não**. O modo S não é suportado no Windows Holographic for Business.

- **Tipo de início de sessão do utilizador**: adicione uma ou mais contas de utilizador que poderão utilizar as aplicações que adicionar. As opções são: 

  - **Início de sessão automático**: não suportado no Windows Holographic for Business.
  - **Contas de utilizador local**: **adicione** a conta de utilizador local (para o dispositivo). A conta que introduzir serve para iniciar sessão no quiosque.
  - **Utilizador ou grupo do Microsoft Azure AD (Windows 10, versão 1803 e posterior)**: requer credenciais de utilizador para iniciar sessão no dispositivo. Selecione **Adicionar** para escolher os utilizadores ou grupos do Microsoft Azure AD na lista. Pode selecionar vários utilizadores e grupos. Escolha **Selecionar** para guardar as alterações.
  - **Visitante do HoloLens**: A conta de visitante é uma conta de convidado que não necessita de credenciais ou de autenticação do utilizador, como está descrito em [Shared PC mode concepts (Conceitos de modo de PC partilhado)](https://docs.microsoft.com/windows/configuration/set-up-shared-or-guest-pc#shared-pc-mode-concepts).

- **Aplicações**: adicione as aplicações que quer executar no dispositivo de quiosque. Lembre-se de que pode adicionar várias aplicações.

  - **Adicionar aplicações da Loja**: selecione uma aplicação existente que tenha adicionado com [Aplicações de Cliente](apps-add.md). Se não tiver aplicações listadas, poderá obter aplicações e [adicioná-las ao Intune](store-apps-windows.md).
  - **Adicionar aplicação Win32**: não suportado no Windows Holographic for Business.
  - **Adicionar por AUMID**: utilize esta opção para adicionar aplicações do Windows de caixa de entrada. Introduza as seguintes propriedades: 

    - **Nome da aplicação**: obrigatório. Introduza um nome para a aplicação.
    - **ID do modelo de utilizador da aplicação (AUMID)**: obrigatório. Introduza o ID do modelo de utilizador da aplicação (AUMID) da aplicação Windows. Para obter este ID, veja [Find the Application User Model ID of an installed app](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app) (Localizar o ID do Modelo de Utilizador da Aplicação de uma aplicação instalada).
    - **Tamanho do mosaico**: obrigatório. Escolha um tamanho de mosaico da aplicação: Pequeno, Médio, Largo ou Grande.

- **Definições do browser do quiosque**: não suportado no Windows Holographic for Business.

- **Utilizar o esquema do menu Iniciar alternativo**: escolha **Sim** para introduzir um ficheiro XML que descreva como as aplicações são apresentadas no menu Iniciar, incluindo a ordem das aplicações. Utilize esta opção se precisar de uma personalização adicional no menu Iniciar. O artigo [Customize and export start layout (Personalizar e exportar o esquema do menu Iniciar)](https://docs.microsoft.com/hololens/hololens-kiosk#start-layout-for-hololens) dá algumas orientações e inclui um ficheiro XML específico para dispositivos com o Windows Holographic for Business.

- **Barra de tarefas do Windows**: não suportada no Windows Holographic for Business.



## <a name="next-steps"></a>Próximos passos
[Atribua o perfil](device-profile-assign.md) e [monitorize o respetivo estado](device-profile-monitor.md).
