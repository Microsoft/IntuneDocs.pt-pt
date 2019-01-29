---
title: Definições de quiosque para Windows 10 no Microsoft Intune – Azure | Microsoft Docs
description: Configurar os dispositivos do Windows 10 (e posteriores) como quiosques de aplicação única e várias aplicações, personalizar o menu Iniciar, adicionar aplicações, mostrar a barra de tarefas e configurar um navegador da web no Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/22/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.openlocfilehash: 61cb1a3c9de10020381d62a2a7795d5ff728db22
ms.sourcegitcommit: 6f2f2fa70f4e47fa5ad2f3c536ba7116e1bd1d05
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/29/2019
ms.locfileid: "55199426"
---
# <a name="windows-10-and-later-device-settings-to-run-as-a-kiosk-in-intune"></a>Windows 10 e posteriores definições do dispositivo para ser executado como um quiosque no Intune

No Windows 10 e dispositivos posteriores, pode configurar estes dispositivos a executar no modo de local público de aplicação única ou modo de local público de várias aplicações.

Este artigo apresenta e descreve as diferentes definições que pode controlar no Windows 10 e dispositivos posteriores. Como parte da sua solução de gestão (MDM) de dispositivos móveis, utilize estas definições para configurar o Windows 10 e dispositivos posteriores para ser executado no modo de local público.

Enquanto administrador do Intune, pode criar e atribuir estas definições para os seus dispositivos.

Para saber mais sobre a funcionalidade de quiosque do Windows no Intune, veja [configurar definições de local público](kiosk-settings.md).

## <a name="before-you-begin"></a>Antes de começar

[Criar o perfil](kiosk-settings.md#create-the-profile).

## <a name="single-full-screen-app-kiosks"></a>Quiosques de uma aplicação em ecrã inteiro

Ao escolher o modo de quiosque de uma aplicação, introduza as seguintes definições:

- **Tipo de início de sessão do utilizador**: As aplicações que adicionar conta run as a utilizador que introduzir. As opções são:

  - **Início de sessão automático (Windows 10 versão 1803 e posterior)**: Para quiosques em ambientes destinados ao público, que não exigem o utilizador iniciar sessão, semelhante a uma conta de convidado. Esta definição utiliza o [CSP AssignedAccess](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp).
  - **Conta de utilizador local**: Introduza a conta de utilizador local (para o dispositivo). A conta que introduzir serve para iniciar sessão no quiosque.

- **Tipo de aplicação**: Selecione **Store app**.

- **Aplicação seja executada no modo de quiosque**: Escolher **adicionar uma aplicação da loja**e selecione uma aplicação a partir da lista.

    Não tem aplicações listadas? Adicione algumas através dos passos indicados em [Aplicações de Cliente](apps-add.md).

    Selecione **OK** para guardar as alterações.

- **Definições do browser de local público**: Estas definições controlam uma aplicação de browser no quiosque. Certifique-se de que obtém o [aplicação de browser do quiosque](https://businessstore.microsoft.com/store/details/kiosk-browser/9NGB5S5XG2KP) da Store, adicione-o para o Intune como um [aplicação de cliente](apps-add.md)e, em seguida, atribuir a aplicação para os dispositivos de local público.

  Introduza as seguintes definições:

  - **Padrão de URL da home page**: Introduza o URL predefinido mostrado quando se abre o browser de local público ou quando reinicia o browser. Por exemplo, introduza: `http://bing.com` ou `http://www.contoso.com`.

  - **Botão início**: **Mostrar** ou **ocultar** botão de início do browser de local público. Por predefinição, o botão não é mostrado.

  - **Botões de navegação**: **Mostrar** ou **ocultar** os botões voltar e avançar. Por predefinição, os botões de navegação não são mostrados.

  - **Botão de sessão final**: **Mostrar** ou **ocultar** no botão de sessão final. Quando o botão é apresentado, o utilizador seleciona-o e a aplicação pede para terminar a sessão. Ao confirmar, o browser limpa todos os dados de navegação (cookies, cache, etc.) e abre o URL predefinido. Por predefinição, o botão não é mostrado.

  - **Atualize o browser após o tempo de inatividade**: Introduza a quantidade de tempo de inatividade (1-1440 minutos) até que o browser do quiosque reinicia um novo Estado. O tempo de inatividade é o número de minutos decorridos desde a última interação do utilizador. Por predefinição, o valor está vazio ou em branco, o que significa que não existe nenhum tempo limite de inatividade.

  - **Permissão de Web sites**: Utilize esta definição para permitir que os sites específicos abrir. Por outras palavras, utilize esta funcionalidade para restringir ou impedir determinados sites no dispositivo. Por exemplo, pode permitir que todos os sites em `http://contoso.com*` sejam abertos. Por predefinição, todos os sites são permitidos.
 
      Para permitir sites específicos, carregue um ficheiro que inclua uma lista dos sites permitidos em linhas separadas. Se não adicionar um ficheiro, todos os sites serão permitidos. O Intune suporta o * (asterisco) como um caráter universal.

      O seu ficheiro de exemplo deve ser semelhante à seguinte lista:

      `http://bing.com`  
      `https://bing.com`  
      `http://contoso.com/*`  
      `https://contoso.com/*`  

  Selecione **OK** para guardar as alterações.

## <a name="multi-app-kiosks"></a>Quiosques de várias aplicações

As aplicações neste modo estão disponíveis no menu Iniciar. Estas aplicações são as únicas aplicações que o utilizador pode abrir.

Ao escolher o modo de quiosque de várias aplicações, introduza as seguintes definições:

- **O destino do Windows 10 no dispositivos de modo S**: Escolher **Sim** para permitir que aplicações da loja e aplicações AUMID (exclui as aplicações Win32) no perfil de local público. Escolha **Não** para permitir as aplicações da loja, as aplicações Win32 e as aplicações AUMID no perfil de quiosque. Quando escolhe **Não**, este perfil de quiosque não é implementado em dispositivos no modo S.

- **Tipo de início de sessão do utilizador**: As aplicações que adicionar conta run as a utilizador que introduzir. As opções são:

  - **Início de sessão automático (Windows 10 versão 1803 e posterior)**: Para quiosques em ambientes destinados ao público, que não exigem o utilizador iniciar sessão, semelhante a uma conta de convidado. Esta definição utiliza o [CSP AssignedAccess](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp).
  - **Conta de utilizador local**: **Adicionar** a conta de utilizador local (para o dispositivo). A conta que introduzir serve para iniciar sessão no quiosque.
  - **Utilizador do AD do Azure ou de grupo (Windows 10 versão 1803 e posterior)**: Selecione **Adicionar** para escolher os utilizadores ou grupos do Microsoft Azure AD na lista. Pode selecionar vários utilizadores e grupos. Escolha **Selecionar** para guardar as alterações.
  - **Visitante do HoloLens**: A conta do visitante é uma conta de convidado que não requer credenciais de utilizador ou a autenticação, conforme descrito em [partilhados conceitos de modo de PC](https://docs.microsoft.com/windows/configuration/set-up-shared-or-guest-pc#shared-pc-mode-concepts).

- **Aplicativos**: Adicione as aplicações para executar no dispositivo local público. Lembre-se de que pode adicionar várias aplicações.

  - **Adicionar aplicação da loja**: Adicione uma aplicação a partir da Microsoft Store para empresas. Se não tiver aplicações listadas, poderá obter aplicações e [adicioná-las ao Intune](store-apps-windows.md). Por exemplo, pode adicionar o Browser do Quiosque, Excel, OneNote e muito mais.

  - **Adicionar aplicação Win32**: Uma aplicação de Win32 é uma aplicação de ambiente de trabalho tradicional, como o Visual Studio Code ou o Google Chrome. Introduza as seguintes propriedades:

    - **Nome da aplicação**: Necessário. Introduza um nome para a aplicação.
    - **Caminho local**: Necessário. Introduza o caminho para o executável, tal como `C:\Program Files (x86)\Microsoft VS Code\Code.exe` ou `C:\Program Files (x86)\Google\Chrome\Application\chrome.exe`.
    - **O modelo de utilizador de aplicação ID (AUMID)**: Introduza o ID do modelo de utilizador da aplicação (AUMID) da aplicação Win32. Esta definição determina o esquema de início do mosaico na área de trabalho. Para obter este ID, veja [Find the Application User Model ID of an installed app](https://docs.microsoft.com/powershell/module/startlayout/get-startapps?view=win10-ps) (Localizar o ID do Modelo de Utilizador da Aplicação de uma aplicação instalada).
    - **Mosaico tamanho**: Necessário. Escolha um tamanho de mosaico da aplicação: Pequeno, Médio, Largo ou Grande.
  
  - **Adicionar por AUMID**: Utilize esta opção para adicionar aplicações de Windows de caixa de entrada, como o bloco de notas ou Calculadora. Introduza as seguintes propriedades: 

    - **Nome da aplicação**: Necessário. Introduza um nome para a aplicação.
    - **O modelo de utilizador de aplicação ID (AUMID)**: Necessário. Introduza o ID do modelo de utilizador da aplicação (AUMID) da aplicação Windows. Para obter este ID, veja [Find the Application User Model ID of an installed app](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app) (Localizar o ID do Modelo de Utilizador da Aplicação de uma aplicação instalada).
    - **Mosaico tamanho**: Necessário. Escolha um tamanho de mosaico da aplicação: Pequeno, Médio, Largo ou Grande.

  > [!TIP]
  > Depois de adicionar todas as aplicações, pode alterar a ordem de apresentação ao clicar e arrastar as aplicações na lista.  

  Selecione **OK** para guardar as alterações.

- **Definições do browser de local público**: Estas definições controlam uma aplicação de browser no quiosque. Garanta que implementa uma aplicação de browser para os dispositivos de quiosque com as [Aplicações de Cliente](apps-add.md).

  Introduza as seguintes definições:

  - **Padrão de URL da home page**: Introduza o URL predefinido mostrado quando se abre o browser de local público ou quando reinicia o browser. Por exemplo, introduza: `http://bing.com` ou `http://www.contoso.com`.

  - **Botão início**: **Mostrar** ou **ocultar** botão de início do browser de local público. Por predefinição, o botão não é mostrado.

  - **Botões de navegação**: **Mostrar** ou **ocultar** os botões voltar e avançar. Por predefinição, os botões de navegação não são mostrados.

  - **Botão de sessão final**: **Mostrar** ou **ocultar** no botão de sessão final. Quando o botão é apresentado, o utilizador seleciona-o e a aplicação pede para terminar a sessão. Ao confirmar, o browser limpa todos os dados de navegação (cookies, cache, etc.) e abre o URL predefinido. Por predefinição, o botão não é mostrado.

  - **Atualize o browser após o tempo de inatividade**: Introduza a quantidade de tempo de inatividade (1-1440 minutos) até que o browser do quiosque reinicia um novo Estado. O tempo de inatividade é o número de minutos decorridos desde a última interação do utilizador. Por predefinição, o valor está vazio ou em branco, o que significa que não existe nenhum tempo limite de inatividade.

  - **Permissão de Web sites**: Utilize esta definição para permitir que os sites específicos abrir. Por outras palavras, utilize esta funcionalidade para restringir ou impedir determinados sites no dispositivo. Por exemplo, pode permitir que todos os sites em `contoso.com*` sejam abertos. Por predefinição, todos os sites são permitidos.

    Para permitir sites específicos, carregue um ficheiro .csv que inclua uma lista dos sites permitidos. Se não adicionar um ficheiro .csv, todos os sites serão permitidos.

  Selecione **OK** para guardar as alterações.

- **Esquema de iniciar alternativa utilize**: Escolher **Sim** para introduzir um arquivo XML que descreve a forma como as aplicações são apresentadas no menu Iniciar, incluindo a ordem das aplicações. Utilize esta opção se precisar de uma personalização adicional no menu Iniciar. O artigo [Customize and export Start layout (Personalizar e exportar o esquema do menu Iniciar)](https://docs.microsoft.com/windows/configuration/customize-and-export-start-layout) fornece algumas orientações e um ficheiro XML de exemplo.

- **Barra de tarefas do Windows**: Optar por **mostrar** ou **ocultar** a barra de tarefas. Por predefinição, a barra de tarefas não é mostrada. Ícones, por exemplo, o ícone de Wi-Fi, são apresentados, mas as definições não podem ser alteradas pelos usuários finais.

## <a name="next-steps"></a>Passos Seguintes

[Atribua o perfil](device-profile-assign.md) e [monitorize o respetivo estado](device-profile-monitor.md).

Também pode criar perfis de local público para [Android](device-restrictions-android.md#kiosk), [Android Enterprise](device-restrictions-android-for-work.md#kiosk-settings), e [Windows Holographic for Business](kiosk-settings-holographic.md) dispositivos.
