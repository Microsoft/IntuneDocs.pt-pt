---
title: Definições de quiosque para Windows 10 no Microsoft Intune – Azure | Microsoft Docs
description: Configure seus dispositivos Windows 10 (e posterior) como quiosques de aplicativo único e vários aplicativos, personalize o menu Iniciar, adicione aplicativos, mostre a barra de tarefas e configure um navegador da Web no Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/15/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 17dce8f7c5aa55a2044e663f724a5784cee8b375
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72506691"
---
# <a name="windows-10-and-later-device-settings-to-run-as-a-kiosk-in-intune"></a>Configurações do dispositivo Windows 10 e posterior para execução como um quiosque no Intune

No Windows 10 e em dispositivos posteriores, você pode configurar esses dispositivos para serem executados no modo de quiosque de aplicativo único ou no modo de quiosque de vários aplicativos.

Este artigo lista e descreve as diferentes configurações que você pode controlar em dispositivos Windows 10 e posteriores. Como parte da sua solução de MDM (gerenciamento de dispositivo móvel), use essas configurações para configurar seus dispositivos Windows 10 e posteriores para serem executados no modo de quiosque.

Como administrador do Intune, você pode criar e atribuir essas configurações aos seus dispositivos.

Para saber mais sobre o recurso de quiosque do Windows no Intune, consulte [definir configurações de quiosque](../kiosk-settings.md).

## <a name="before-you-begin"></a>Antes de começar

- [Crie o perfil](kiosk-settings.md#create-the-profile).

- Esse perfil de quiosque está diretamente relacionado ao perfil de restrições de dispositivo que você cria usando as [configurações de quiosque do Microsoft Edge](device-restrictions-windows-10.md#microsoft-edge-browser). Para resumir:

  1. Crie este perfil de quiosque para executar o dispositivo no modo de quiosque.
  2. Crie o [perfil de restrições de dispositivo](device-restrictions-windows-10.md#microsoft-edge-browser)e configure recursos específicos e configurações permitidas no Microsoft Edge.

> [!IMPORTANT]
> Certifique-se de atribuir esse perfil de quiosque aos mesmos dispositivos que o seu [perfil do Microsoft Edge](device-restrictions-windows-10.md#microsoft-edge-browser).

## <a name="single-full-screen-app-kiosks"></a>Quiosques de uma aplicação em ecrã inteiro

Executa apenas um aplicativo no dispositivo.

- **Selecione um modo de quiosque**: escolha **aplicativo único, quiosque de tela inteira**.

- **Tipo de início de sessão do utilizador**: as aplicações que adicionar são executadas como a conta de utilizador que introduzir. As opções são:

  - **Logon automático (Windows 10 versão 1803 e posterior)** : Use em quiosques em ambientes voltados para o público que não exigem que o usuário entre, de forma semelhante a uma conta de convidado. Esta definição utiliza o [CSP AssignedAccess](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp).
  - **Conta de utilizador local**: introduza a conta de utilizador local (para o dispositivo). A conta que você digita entra no quiosque.

- **Tipo de aplicativo**: selecione o tipo de aplicativo. As opções são:

  - **Adicionar navegador Microsoft Edge**: selecione **navegador Microsoft Edge**e escolha o **tipo de modo de quiosque de borda**:

    - **Pôsteres digitais/interativos**: abre uma tela de URL inteira e mostra apenas o conteúdo nesse site. [Configurar sinais digitais](https://docs.microsoft.com/windows/configuration/setup-digital-signage) fornece mais informações sobre esse recurso.
    - **Navegação pública (InPrivate)** : executa uma versão limitada de várias guias do Microsoft Edge. Os usuários podem navegar publicamente ou terminar sua sessão de navegação.

    Para obter mais informações sobre essas opções, consulte [implantar o modo de quiosque do Microsoft Edge](https://docs.microsoft.com/microsoft-edge/deploy/microsoft-edge-kiosk-mode-deploy#supported-configuration-types).

    > [!NOTE]
    > Essa configuração habilita o navegador Microsoft Edge no dispositivo. Para definir configurações específicas do Microsoft Edge, crie um perfil de configuração de dispositivo (**configuração do dispositivo** > **perfis** > **Criar perfil** > **Windows 10** para plataforma > **restrições de dispositivo**  >  **navegador Microsoft Edge**). O [navegador Microsoft Edge](device-restrictions-windows-10.md#microsoft-edge-browser) lista e descreve as configurações disponíveis.

  - **Adicionar navegador de quiosque**: selecione **configurações do navegador de quiosque**. Estas definições controlam uma aplicação de browser no quiosque. Verifique se você obteve o [aplicativo de navegador de quiosque](https://businessstore.microsoft.com/store/details/kiosk-browser/9NGB5S5XG2KP) da loja, adicione-o ao Intune como um [aplicativo cliente](../apps/apps-add.md). Em seguida, atribua o aplicativo aos dispositivos de quiosque.

    Introduza as seguintes definições:

    - **URL da home page predefinido**: introduza o URL predefinido mostrado quando o browser do quiosque abre ou quando o browser é reiniciado. Por exemplo, introduza: `http://bing.com` ou `http://www.contoso.com`.

    - **Botão de início**: **mostre** ou **oculte** o botão de início do browser do quiosque. Por predefinição, o botão não é mostrado.

    - **Botões de navegação**: **mostre** ou **oculte** os botões voltar e avançar. Por predefinição, os botões de navegação não são mostrados.

    - **Botão de terminar sessão**: **mostre** ou **oculte** o botão de terminar sessão. Quando o botão é apresentado, o utilizador seleciona-o e a aplicação pede para terminar a sessão. Ao confirmar, o browser limpa todos os dados de navegação (cookies, cache, etc.) e abre o URL predefinido. Por predefinição, o botão não é mostrado.

    - **Atualizar o browser após um tempo de inatividade**: introduza o período de tempo de inatividade (1-1440 minutos) necessário antes de o browser do quiosque reiniciar num estado novo. O tempo de inatividade é o número de minutos decorridos desde a última interação do utilizador. Por predefinição, o valor está vazio ou em branco, o que significa que não existe nenhum tempo limite de inatividade.

    - **Sites permitidos**: utilize esta definição para permitir que determinados sites sejam abertos. Por outras palavras, utilize esta funcionalidade para restringir ou impedir determinados sites no dispositivo. Por exemplo, pode permitir que todos os sites em `http://contoso.com*` sejam abertos. Por predefinição, todos os sites são permitidos.

      Para permitir sites específicos, carregue um ficheiro que inclua uma lista dos sites permitidos em linhas separadas. Se não adicionar um ficheiro, todos os sites serão permitidos. O Intune dá suporte a `*` (asterisco) como um curinga.

      O seu ficheiro de exemplo deve ser semelhante à seguinte lista:

      `http://bing.com`  
      `https://bing.com`  
      `http://contoso.com/*`  
      `https://contoso.com/*`

    > [!NOTE]
    > Os quiosques do Windows 10 com o logon automático habilitado usando o navegador de quiosque da Microsoft devem usar uma licença offline da Microsoft Store para empresas. Esse requisito é porque o logon automático usa uma conta de usuário local sem credenciais de Azure Active Directory (AD). Portanto, as licenças online não podem ser avaliadas. Para obter mais informações, consulte [distribuir aplicativos offline](https://docs.microsoft.com/microsoft-store/distribute-offline-apps).

  - **Adicionar aplicativo da loja**: selecione **Adicionar um aplicativo da loja**e escolha um aplicativo na lista.

    Não tem aplicações listadas? Adicione algumas através dos passos indicados em [Aplicações de Cliente](../apps/apps-add.md).
    
 - **Especificar janela de manutenção para reinicializações de aplicativo**: o padrão é "não configurado", selecione "exigir" para verificar se há aplicativos que exigem uma reinicialização para concluir a instalação.
 
     Se estiver usando o navegador de quiosque ou outro Microsoft Store para o aplicativo de negócios, decida com que frequência verificar se há atualizações de aplicativo que exigem reinicialização para concluir a instalação do aplicativo. Se não estiver configurado, Microsoft Store para aplicativos de negócios será reiniciado em um tempo não agendado 3 dias após a instalação de uma atualização de aplicativo.
     
     - **Hora de início da janela de manutenção**: selecione a data e hora do dia para iniciar a verificação de clientes para qualquer atualização de aplicativo que exija reinicialização. A hora de início padrão é meia-noite ou zero minutos.
     
     - **Recorrência da janela de manutenção**: o padrão é diário.
         Defina com que frequência as janelas de manutenção para atualizações de aplicativo ocorrerão. A recomendação é diária para evitar reinicializações de aplicativo não agendadas.

  [CSP ApplicationManagement/ScheduleForceRestartForUpdateFailures](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-scheduleforcerestartforupdatefailures)

## <a name="multi-app-kiosks"></a>Quiosques de várias aplicações

As aplicações neste modo estão disponíveis no menu Iniciar. Estas aplicações são as únicas aplicações que o utilizador pode abrir. Se um aplicativo tiver uma dependência em outro aplicativo, ambos deverão ser incluídos na lista de aplicativos permitidos. Por exemplo, o Internet Explorer 64-bit tem uma dependência do Internet Explorer 32-bit, portanto, você deve permitir "C:\Arquivos de Programas\internet Explorer\iexplore.exe" e "C:\Arquivos de programas (x86) \Internet Explorer\iexplore.exe". 

- **Selecione um modo de quiosque**: escolha **vários quiosques de aplicativos**.

- **Direcionar dispositivos Windows 10 em modo S**:
  - **Sim**: permite que aplicativos da loja e aplicativos AUMID (exclua aplicativos Win32) no perfil de quiosque.
  - **Não**: permite aplicativos da loja, aplicativos Win32 e aplicativos AUMID no perfil de quiosque. Esse perfil de quiosque não é implantado em dispositivos de modo S.

- **Tipo de início de sessão do utilizador**: as aplicações que adicionar são executadas como a conta de utilizador que introduzir. As opções são:

  - **Logon automático (Windows 10 versão 1803 e posterior)** : Use em quiosques em ambientes voltados para o público que não exigem que o usuário entre, de forma semelhante a uma conta de convidado. Esta definição utiliza o [CSP AssignedAccess](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp).
  - **Conta de utilizador local**: **adicione** a conta de utilizador local (para o dispositivo). A conta que você digita entra no quiosque.
  - **Usuário ou grupo do Azure AD (Windows 10 versão 1803 e posterior)** : selecione **Adicionar**e escolha usuários ou grupos do Azure ad na lista. Pode selecionar vários utilizadores e grupos. Escolha **Selecionar** para guardar as alterações.
  - **Visitante do HoloLens**: A conta de visitante é uma conta de convidado que não necessita de credenciais ou de autenticação do utilizador, como está descrito em [Shared PC mode concepts (Conceitos de modo de PC partilhado)](https://docs.microsoft.com/windows/configuration/set-up-shared-or-guest-pc#shared-pc-mode-concepts).

- **Navegador e aplicativos**: Adicione os aplicativos a serem executados no dispositivo de quiosque. Lembre-se de que pode adicionar várias aplicações.

  - **Navigator**

    - **Adicionar Microsoft Edge**: o Microsoft Edge é adicionado à grade do aplicativo e todos os aplicativos podem ser executados nesse quiosque. Escolha o **tipo de modo de quiosque do Microsoft Edge**:

      - **Modo normal (versão completa do Microsoft Edge)** : executa uma versão completa do Microsoft Edge com todos os recursos de navegação. Os dados e o estado do usuário são salvos entre sessões.
      - **Navegação pública (InPrivate)** : executa uma versão de várias guias do Microsoft Edge InPrivate com uma experiência personalizada para quiosques que são executados no modo de tela inteira.

      Para obter mais informações sobre essas opções, consulte [implantar o modo de quiosque do Microsoft Edge](https://docs.microsoft.com/microsoft-edge/deploy/microsoft-edge-kiosk-mode-deploy#supported-configuration-types).

      > [!NOTE]
      > Essa configuração habilita o navegador Microsoft Edge no dispositivo. Para definir configurações específicas do Microsoft Edge, crie um perfil de configuração de dispositivo (**configuração do dispositivo** > **perfis** > **Criar perfil** > **Windows 10** para plataforma > **restrições de dispositivo**  >  **navegador Microsoft Edge**). O [navegador Microsoft Edge](device-restrictions-windows-10.md#microsoft-edge-browser) lista e descreve as configurações disponíveis.

    - **Adicionar navegador de quiosque**: essas configurações controlam um aplicativo de navegador da Web no quiosque. Garanta que implementa uma aplicação de browser para os dispositivos de quiosque com as [Aplicações de Cliente](../apps/apps-add.md).

      Introduza as seguintes definições:

      - **URL da home page predefinido**: introduza o URL predefinido mostrado quando o browser do quiosque abre ou quando o browser é reiniciado. Por exemplo, introduza: `http://bing.com` ou `http://www.contoso.com`.

      - **Botão de início**: **mostre** ou **oculte** o botão de início do browser do quiosque. Por predefinição, o botão não é mostrado.

      - **Botões de navegação**: **mostre** ou **oculte** os botões voltar e avançar. Por predefinição, os botões de navegação não são mostrados.

      - **Botão de terminar sessão**: **mostre** ou **oculte** o botão de terminar sessão. Quando o botão é apresentado, o utilizador seleciona-o e a aplicação pede para terminar a sessão. Ao confirmar, o browser limpa todos os dados de navegação (cookies, cache, etc.) e abre o URL predefinido. Por predefinição, o botão não é mostrado.

      - **Atualizar o browser após um tempo de inatividade**: introduza o período de tempo de inatividade (1-1440 minutos) necessário antes de o browser do quiosque reiniciar num estado novo. O tempo de inatividade é o número de minutos decorridos desde a última interação do utilizador. Por predefinição, o valor está vazio ou em branco, o que significa que não existe nenhum tempo limite de inatividade.

      - **Sites permitidos**: utilize esta definição para permitir que determinados sites sejam abertos. Por outras palavras, utilize esta funcionalidade para restringir ou impedir determinados sites no dispositivo. Por exemplo, pode permitir que todos os sites em `contoso.com*` sejam abertos. Por predefinição, todos os sites são permitidos.

        Para permitir sites específicos, carregue um ficheiro .csv que inclua uma lista dos sites permitidos. Se não adicionar um ficheiro .csv, todos os sites serão permitidos.

      > [!NOTE]
      > Os quiosques do Windows 10 com o logon automático habilitado usando o navegador de quiosque da Microsoft devem usar uma licença offline da Microsoft Store para empresas. Esse requisito é porque o logon automático usa uma conta de usuário local sem credenciais de Azure Active Directory (AD). Portanto, as licenças online não podem ser avaliadas. Para obter mais informações, consulte [distribuir aplicativos offline](https://docs.microsoft.com/microsoft-store/distribute-offline-apps).

  - **Aplicativos**

    - **Adicionar aplicação da loja**: adicione uma aplicação na Microsoft Store para Empresas. Se não tiver aplicações listadas, poderá obter aplicações e [adicioná-las ao Intune](../apps/store-apps-windows.md). Por exemplo, pode adicionar o Browser do Quiosque, Excel, OneNote e muito mais.

    - **Adicionar Aplicação Win32**: uma aplicação Win32 é uma aplicação de ambiente de trabalho tradicional, como o Visual Studio Code ou o Google Chrome. Introduza as seguintes propriedades:

      - **Nome da aplicação**: obrigatório. Introduza um nome para a aplicação.
      - **Caminho local**: obrigatório. Introduza o caminho para o executável, tal como `C:\Program Files (x86)\Microsoft VS Code\Code.exe` ou `C:\Program Files (x86)\Google\Chrome\Application\chrome.exe`.
      - **ID do modelo de utilizador da aplicação (AUMID)** : introduza o ID do modelo de utilizador da aplicação (AUMID) da aplicação Win32. Esta definição determina o esquema de início do mosaico na área de trabalho. Para obter essa ID, consulte [Get-StartApps](https://docs.microsoft.com/powershell/module/startlayout/get-startapps?view=win10-ps).

    - **Adicionar por AUMID**: utilize esta opção para adicionar aplicações do Windows de caixa de entrada, como o Bloco de notas ou a Calculadora. Introduza as seguintes propriedades:

      - **Nome da aplicação**: obrigatório. Introduza um nome para a aplicação.
      - **ID do modelo de utilizador da aplicação (AUMID)** : obrigatório. Introduza o ID do modelo de utilizador da aplicação (AUMID) da aplicação Windows. Para obter este ID, veja [Find the Application User Model ID of an installed app](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app) (Localizar o ID do Modelo de Utilizador da Aplicação de uma aplicação instalada).

    - **Inicialização aberta**: opcional. Escolha um aplicativo para iniciar a inicialização a partir do momento em que o usuário entrar. Apenas um único aplicativo pode ser inicializado de vez em execução.
    - **Tamanho do mosaico**: obrigatório. Escolha um tamanho de mosaico da aplicação: Pequeno, Médio, Largo ou Grande.

  > [!TIP]
  > Depois de adicionar todas as aplicações, pode alterar a ordem de apresentação ao clicar e arrastar as aplicações na lista.  

- **Utilizar o esquema do menu Iniciar alternativo**: escolha **Sim** para introduzir um ficheiro XML que descreva como as aplicações são apresentadas no menu Iniciar, incluindo a ordem das aplicações. Utilize esta opção se precisar de uma personalização adicional no menu Iniciar. O artigo [Customize and export Start layout (Personalizar e exportar o esquema do menu Iniciar)](https://docs.microsoft.com/windows/configuration/customize-and-export-start-layout) fornece algumas orientações e um ficheiro XML de exemplo.

- **Barra de tarefas do Windows**: escolha **Mostrar** ou **Ocultar** a barra de tarefas. Por predefinição, a barra de tarefas não é mostrada. Os ícones, como o ícone Wi-Fi, são mostrados, mas as configurações não podem ser alteradas pelos usuários finais.

- **Permitir acesso a pasta de downloads**: escolha **Sim** para permitir que os usuários acessem a pasta de downloads no Windows Explorer. Por padrão, o acesso à pasta de downloads está desabilitado. Esse recurso é comumente usado para que os usuários finais acessem itens baixados de um navegador.

## <a name="next-steps"></a>Próximos passos

[Atribua o perfil](device-profile-assign.md) e [monitorize o respetivo estado](device-profile-monitor.md).

Você também pode criar perfis de quiosque para dispositivos [Android](device-restrictions-android.md#kiosk), [Android Enterprise](device-restrictions-android-for-work.md#dedicated-device-settings)e [Windows Holographic for Business](kiosk-settings-holographic.md) .
