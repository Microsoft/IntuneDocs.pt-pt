---
title: Definições de quiosque para Windows 10 no Microsoft Intune – Azure | Microsoft Docs
description: Configurar os dispositivos do Windows 10 (e posteriores) como quiosques de aplicação única e várias aplicações, personalizar o menu Iniciar, adicionar aplicações, mostrar a barra de tarefas e configurar um navegador da web no Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/11/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: a80e4cf4e68235ef9e88943a8b62121e0cfb6623
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/23/2019
ms.locfileid: "66046963"
---
# <a name="windows-10-and-later-device-settings-to-run-as-a-kiosk-in-intune"></a>Windows 10 e posteriores definições do dispositivo para ser executado como um quiosque no Intune

No Windows 10 e dispositivos posteriores, pode configurar estes dispositivos a executar no modo de local público de aplicação única ou modo de local público de várias aplicações.

Este artigo apresenta e descreve as diferentes definições que pode controlar no Windows 10 e dispositivos posteriores. Como parte da sua solução de gestão (MDM) de dispositivos móveis, utilize estas definições para configurar o Windows 10 e dispositivos posteriores para ser executado no modo de local público.

Enquanto administrador do Intune, pode criar e atribuir estas definições para os seus dispositivos.

Para saber mais sobre a funcionalidade de quiosque do Windows no Intune, veja [configurar definições de local público](kiosk-settings.md).

## <a name="before-you-begin"></a>Antes de começar

- [Criar o perfil](kiosk-settings.md#create-the-profile).

- Este perfil de local público está diretamente relacionada com o perfil de restrições de dispositivos que criar com o [definições de local público do Microsoft Edge](device-restrictions-windows-10.md#microsoft-edge-browser). Para resumir:

  1. Crie este perfil de local público para executar o dispositivo no modo de local público.
  2. Criar a [perfil de restrições de dispositivo](device-restrictions-windows-10.md#microsoft-edge-browser)e configurar recursos específicos e as definições de permissão no Microsoft Edge.

> [!IMPORTANT] 
> Certifique-se de que atribuir este perfil de local público para os mesmos dispositivos como sua [perfil do Microsoft Edge](device-restrictions-windows-10.md#microsoft-edge-browser).

## <a name="single-full-screen-app-kiosks"></a>Quiosques de uma aplicação em ecrã inteiro

É executado apenas uma aplicação no dispositivo.

- **Selecione um modo de local público**: Escolher **única aplicação, quiosque de ecrã inteiro**.

- **Tipo de início de sessão do utilizador**: As aplicações que adicionar conta run as a utilizador que introduzir. As opções são:

  - **Início de sessão automático (Windows 10 versão 1803 e posterior)**: Utilizar quiosques em ambientes destinados ao público, que não exigem o utilizador iniciar sessão, semelhante a uma conta de convidado. Esta definição utiliza o [CSP AssignedAccess](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp).
  - **Conta de utilizador local**: Introduza a conta de utilizador local (para o dispositivo). A conta que introduzir inicia sessão para o local público.

- **Tipo de aplicação**: Selecione o tipo de aplicação. As opções são:

  - **Adicionar o browser Microsoft Edge**: Selecione **browser Microsoft Edge**e escolha o **tipo de modo de quiosque de borda**:

    - **Digital/Interactive signage**: Abre uma tela inteira de URL e mostra apenas o conteúdo nesse Web site. [Configurar sinais digital](https://docs.microsoft.com/windows/configuration/setup-digital-signage) fornece mais informações sobre esta funcionalidade.
    - **Público, navegar (InPrivate)**: Executa uma versão de separador multi limitada do Microsoft Edge. Os utilizadores podem procurar publicamente ou terminar a sessão de navegação.

    Para obter mais informações sobre estas opções, consulte [modo de local público de implementar o Microsoft Edge](https://docs.microsoft.com/microsoft-edge/deploy/microsoft-edge-kiosk-mode-deploy#supported-configuration-types).

    > [!NOTE]
    > Esta definição permite que o browser Microsoft Edge no dispositivo. Para configurar as definições específicas do Microsoft Edge, criar um perfil de configuração do dispositivo (**configuração do dispositivo** > **perfis** > **criar perfil**  >  **Windows 10** para a plataforma > **restrições de dispositivos** >  **Browser do Microsoft Edge**). [Browser Microsoft Edge](device-restrictions-windows-10.md#microsoft-edge-browser) apresenta e descreve as definições disponíveis.

    Selecione **OK** para guardar as alterações.

  - **Adicionar o browser do quiosque**: Selecione **definições do browser de local público**. Estas definições controlam uma aplicação de browser no quiosque. Certifique-se de que obtém o [aplicação de browser do quiosque](https://businessstore.microsoft.com/store/details/kiosk-browser/9NGB5S5XG2KP) da Store, adicione-o para o Intune como um [aplicação de cliente](apps-add.md)e, em seguida, atribuir a aplicação para os dispositivos de local público.

    Introduza as seguintes definições:

    - **Padrão de URL da home page**: Introduza o URL predefinido mostrado quando se abre o browser de local público ou quando reinicia o browser. Por exemplo, introduza: `http://bing.com` ou `http://www.contoso.com`.

    - **Botão início**: **Mostrar** ou **ocultar** botão de início do browser de local público. Por predefinição, o botão não é mostrado.

    - **Botões de navegação**: **Mostrar** ou **ocultar** os botões voltar e avançar. Por predefinição, os botões de navegação não são mostrados.

    - **Botão de sessão final**: **Mostrar** ou **ocultar** no botão de sessão final. Quando o botão é apresentado, o utilizador seleciona-o e a aplicação pede para terminar a sessão. Ao confirmar, o browser limpa todos os dados de navegação (cookies, cache, etc.) e abre o URL predefinido. Por predefinição, o botão não é mostrado.

    - **Atualize o browser após o tempo de inatividade**: Introduza a quantidade de tempo de inatividade (1-1440 minutos) até que o browser do quiosque reinicia um novo Estado. O tempo de inatividade é o número de minutos decorridos desde a última interação do utilizador. Por predefinição, o valor está vazio ou em branco, o que significa que não existe nenhum tempo limite de inatividade.

    - **Permissão de Web sites**: Utilize esta definição para permitir que os sites específicos abrir. Por outras palavras, utilize esta funcionalidade para restringir ou impedir determinados sites no dispositivo. Por exemplo, pode permitir que todos os sites em `http://contoso.com*` sejam abertos. Por predefinição, todos os sites são permitidos.

      Para permitir sites específicos, carregue um ficheiro que inclua uma lista dos sites permitidos em linhas separadas. Se não adicionar um ficheiro, todos os sites serão permitidos. O Intune suporta `*` (asterisco) como um caráter universal.

      O seu ficheiro de exemplo deve ser semelhante à seguinte lista:

      `http://bing.com`  
      `https://bing.com`  
      `http://contoso.com/*`  
      `https://contoso.com/*`  

    Selecione **OK** para guardar as alterações.

  - **Adicionar aplicação Store**: Selecione **adicionar uma aplicação da loja**e selecione uma aplicação a partir da lista.

    Não tem aplicações listadas? Adicione algumas através dos passos indicados em [Aplicações de Cliente](apps-add.md).

  Selecione **OK** para guardar as alterações.

## <a name="multi-app-kiosks"></a>Quiosques de várias aplicações

As aplicações neste modo estão disponíveis no menu Iniciar. Estas aplicações são as únicas aplicações que o utilizador pode abrir. Se uma aplicação tem uma dependência no outro aplicativo, ambos têm de ser incluídas na lista de aplicações permitidas. Por exemplo, o Internet Explorer 64 bits tem uma dependência no Internet Explorer 32 bits, pelo que tem de permitir "C:\Program Files\internet explorer\iexplore.exe" e "C:\Program Files (x86) \Internet". 

- **Selecione um modo de local público**: Escolher **quiosque de várias aplicações**.

- **O destino do Windows 10 no dispositivos de modo S**:
  - **Sim**: Permite que aplicações da loja e aplicações AUMID (exclui as aplicações Win32), no perfil de local público.
  - **Não**: Permite que aplicações da loja, aplicações de Win32 e AUMID aplicações no perfil de local público. Este perfil de local público não está implementada em dispositivos de modo S.

- **Tipo de início de sessão do utilizador**: As aplicações que adicionar conta run as a utilizador que introduzir. As opções são:

  - **Início de sessão automático (Windows 10 versão 1803 e posterior)**: Utilizar quiosques em ambientes destinados ao público, que não exigem o utilizador iniciar sessão, semelhante a uma conta de convidado. Esta definição utiliza o [CSP AssignedAccess](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp).
  - **Conta de utilizador local**: **Adicionar** a conta de utilizador local (para o dispositivo). A conta que introduzir inicia sessão para o local público.
  - **Utilizador do AD do Azure ou de grupo (Windows 10 versão 1803 e posterior)**: Selecione **adicionar**e escolha os utilizadores do Azure AD ou grupos da lista. Pode selecionar vários utilizadores e grupos. Escolha **Selecionar** para guardar as alterações.
  - **Visitante do HoloLens**: A conta do visitante é uma conta de convidado que não requer credenciais de utilizador ou a autenticação, conforme descrito em [partilhados conceitos de modo de PC](https://docs.microsoft.com/windows/configuration/set-up-shared-or-guest-pc#shared-pc-mode-concepts).

- **Aplicativos de navegador e**: Adicione as aplicações para executar no dispositivo local público. Lembre-se de que pode adicionar várias aplicações.

  - **Browsers**

    - **Adicionar o Microsoft Edge**: Microsoft Edge é adicionado à grelha de aplicação e todos os aplicativos podem executar em desse quiosque. Escolha o **tipo de modo de quiosque do Microsoft Edge**:

      - **Modo normal (versão completa do Microsoft Edge)**: Executa uma versão completa do Microsoft Edge com todas as funcionalidades de navegação. Dados de utilizador e de estado são salvas entre sessões.
      - **Público, navegar (InPrivate)**: Executa uma versão de separador multi do InPrivate do Microsoft Edge com uma experiência personalizada para quiosques que são executados em modo de ecrã inteiro.

      Para obter mais informações sobre estas opções, consulte [modo de local público de implementar o Microsoft Edge](https://docs.microsoft.com/microsoft-edge/deploy/microsoft-edge-kiosk-mode-deploy#supported-configuration-types).

      > [!NOTE]
      > Esta definição permite que o browser Microsoft Edge no dispositivo. Para configurar as definições específicas do Microsoft Edge, criar um perfil de configuração do dispositivo (**configuração do dispositivo** > **perfis** > **criar perfil**  >  **Windows 10** para a plataforma > **restrições de dispositivos** >  **Browser do Microsoft Edge**). [Browser Microsoft Edge](device-restrictions-windows-10.md#microsoft-edge-browser) apresenta e descreve as definições disponíveis.

      Selecione **OK** para guardar as alterações.

    - **Adicionar o browser do quiosque**: Estas definições controlam uma aplicação de browser no quiosque. Garanta que implementa uma aplicação de browser para os dispositivos de quiosque com as [Aplicações de Cliente](apps-add.md).

      Introduza as seguintes definições:

      - **Padrão de URL da home page**: Introduza o URL predefinido mostrado quando se abre o browser de local público ou quando reinicia o browser. Por exemplo, introduza: `http://bing.com` ou `http://www.contoso.com`.

      - **Botão início**: **Mostrar** ou **ocultar** botão de início do browser de local público. Por predefinição, o botão não é mostrado.

      - **Botões de navegação**: **Mostrar** ou **ocultar** os botões voltar e avançar. Por predefinição, os botões de navegação não são mostrados.

      - **Botão de sessão final**: **Mostrar** ou **ocultar** no botão de sessão final. Quando o botão é apresentado, o utilizador seleciona-o e a aplicação pede para terminar a sessão. Ao confirmar, o browser limpa todos os dados de navegação (cookies, cache, etc.) e abre o URL predefinido. Por predefinição, o botão não é mostrado.

      - **Atualize o browser após o tempo de inatividade**: Introduza a quantidade de tempo de inatividade (1-1440 minutos) até que o browser do quiosque reinicia um novo Estado. O tempo de inatividade é o número de minutos decorridos desde a última interação do utilizador. Por predefinição, o valor está vazio ou em branco, o que significa que não existe nenhum tempo limite de inatividade.

      - **Permissão de Web sites**: Utilize esta definição para permitir que os sites específicos abrir. Por outras palavras, utilize esta funcionalidade para restringir ou impedir determinados sites no dispositivo. Por exemplo, pode permitir que todos os sites em `contoso.com*` sejam abertos. Por predefinição, todos os sites são permitidos.

        Para permitir sites específicos, carregue um ficheiro .csv que inclua uma lista dos sites permitidos. Se não adicionar um ficheiro .csv, todos os sites serão permitidos.

      Selecione **OK** para guardar as alterações.

  - **Aplicações**

    - **Adicionar aplicação da loja**: Adicione uma aplicação a partir da Microsoft Store para empresas. Se não tiver aplicações listadas, poderá obter aplicações e [adicioná-las ao Intune](store-apps-windows.md). Por exemplo, pode adicionar o Browser do Quiosque, Excel, OneNote e muito mais.

      Selecione **OK** para guardar as alterações.

    - **Adicionar aplicação Win32**: Uma aplicação de Win32 é uma aplicação de ambiente de trabalho tradicional, como o Visual Studio Code ou o Google Chrome. Introduza as seguintes propriedades:

      - **Nome da aplicação**: Necessário. Introduza um nome para a aplicação.
      - **Caminho local**: Necessário. Introduza o caminho para o executável, tal como `C:\Program Files (x86)\Microsoft VS Code\Code.exe` ou `C:\Program Files (x86)\Google\Chrome\Application\chrome.exe`.
      - **O modelo de utilizador de aplicação ID (AUMID)**: Introduza o ID do modelo de utilizador da aplicação (AUMID) da aplicação Win32. Esta definição determina o esquema de início do mosaico na área de trabalho. Para obter este ID, consulte [Get-StartApps](https://docs.microsoft.com/powershell/module/startlayout/get-startapps?view=win10-ps).

      Selecione **OK** para guardar as alterações.

    - **Adicionar por AUMID**: Utilize esta opção para adicionar aplicações de Windows de caixa de entrada, como o bloco de notas ou Calculadora. Introduza as seguintes propriedades:

      - **Nome da aplicação**: Necessário. Introduza um nome para a aplicação.
      - **O modelo de utilizador de aplicação ID (AUMID)**: Necessário. Introduza o ID do modelo de utilizador da aplicação (AUMID) da aplicação Windows. Para obter este ID, veja [Find the Application User Model ID of an installed app](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app) (Localizar o ID do Modelo de Utilizador da Aplicação de uma aplicação instalada).

      Selecione **OK** para guardar as alterações.

    - **AutoLaunch**: Opcional. Escolha uma aplicação para AutoLaunch quando o utilizador inicia sessão. Apenas um único aplicativo pode ser AutoLaunched.
    - **Mosaico tamanho**: Necessário. Escolha um tamanho de mosaico da aplicação: Pequeno, Médio, Largo ou Grande.

  > [!TIP]
  > Depois de adicionar todas as aplicações, pode alterar a ordem de apresentação ao clicar e arrastar as aplicações na lista.  

- **Esquema de iniciar alternativa utilize**: Escolher **Sim** para introduzir um arquivo XML que descreve a forma como as aplicações são apresentadas no menu Iniciar, incluindo a ordem das aplicações. Utilize esta opção se precisar de uma personalização adicional no menu Iniciar. O artigo [Customize and export Start layout (Personalizar e exportar o esquema do menu Iniciar)](https://docs.microsoft.com/windows/configuration/customize-and-export-start-layout) fornece algumas orientações e um ficheiro XML de exemplo.

- **Barra de tarefas do Windows**: Optar por **mostrar** ou **ocultar** a barra de tarefas. Por predefinição, a barra de tarefas não é mostrada. Ícones, por exemplo, o ícone de Wi-Fi, são apresentados, mas as definições não podem ser alteradas pelos usuários finais.

- **Permitir o acesso à pasta transferências**: Escolher **Sim** para permitir que os utilizadores aceder à pasta de transferências no Windows Explorer. Por predefinição, o acesso para a pasta de transferências está desativado. Esta funcionalidade é frequentemente utilizada para os utilizadores finais para aceder aos itens transferidos a partir de um browser.

Selecione **OK** para guardar as alterações.

## <a name="next-steps"></a>Passos Seguintes

[Atribua o perfil](device-profile-assign.md) e [monitorize o respetivo estado](device-profile-monitor.md).

Também pode criar perfis de local público para [Android](device-restrictions-android.md#kiosk), [Android Enterprise](device-restrictions-android-for-work.md#dedicated-device-settings), e [Windows Holographic for Business](kiosk-settings-holographic.md) dispositivos.
