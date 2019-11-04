---
title: Configurações de linhas de base de segurança do Intune para o Microsoft Edge
titleSuffix: Microsoft Intune
description: Configurações de linha de base de segurança com suporte pelo Intune para gerenciar o navegador Microsoft Edge
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/30/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: shpate
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8f4e56340d871ea5e0bcec7e541a418c32d021d0
ms.sourcegitcommit: 60f0ff6d2efbae0f2ce14b9a9f3f9267309e209b
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73415554"
---
# <a name="microsoft-edge-baseline-settings-for-intune"></a>Configurações de linha de base do Microsoft Edge para Intune

Exiba as configurações de linha de base do navegador da Web do Microsoft Edge com suporte pelo Microsoft Intune. Os padrões de linha de base do Microsoft Edge representam a configuração recomendada para os navegadores do Microsoft Edge e podem não corresponder os padrões de linha de base para outras linhas de base de segurança.

> [!NOTE]
> A linha de base do Microsoft Edge está em visualização pública. 

## <a name="microsoft-edge"></a>Microsoft Edge

- **Impedir o bypass de prompts do Microsoft defender SmartScreen para sites**  
  **Padrão**: habilitado  
  CSP do Microsoft Edge: [navegador/PreventSmartScreenPromptOverride](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverride)

  Essa configuração de política permite que você decida se os usuários podem substituir os avisos do Microsoft defender SmartScreen sobre sites potencialmente mal-intencionados. 
  - Se você habilitar essa configuração, os usuários não poderão ignorar os avisos do Microsoft defender SmartScreen e eles ficarão impedidos de continuar no site. 
  - Se você desabilitar ou não definir essa configuração, os usuários poderão ignorar os avisos do Microsoft defender SmartScreen e continuar no site.

- **Versão mínima do SSL habilitada**  
  **Padrão**: habilitado  

  Defina uma versão mínima com suporte do SSL. Se você definir essa política como *não configurada*, o Microsoft Edge usará uma versão mínima padrão do *TLS 1,0*. Quando definido como *habilitado*, você pode selecionar uma versão mínima com base nos seguintes valores:

  - TLS 1,0
  - TLS 1,1
  - TLS 1,2

  - **Versão mínima do SSL habilitada**  
    **Padrão**: TLS 1,2

- **Evitar ignorar avisos do Microsoft defender SmartScreen sobre downloads**  
  **Padrão**: habilitado  
  CSP do Microsoft Edge: [navegador/PreventSmartScreenPromptOverrideForFiles](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverrideforfiles)  

  Essa política permite determinar se os usuários podem substituir os avisos do Microsoft defender SmartScreen sobre downloads não verificados.
  - Se você habilitar essa política, os usuários em sua organização não poderão ignorar os avisos do Microsoft defender SmartScreen e eles serão impedidos de concluir os downloads não verificados.
  - Se você desabilitar ou não configurar essa política, os usuários poderão ignorar os avisos do Microsoft defender SmartScreen e concluir os downloads não verificados.

- **Permitir que os usuários continuem na página de aviso de SSL**  
  **Padrão**: desabilitado  
  CSP do Microsoft Edge: [navegador/PreventCertErrorOverrides](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-preventcerterroroverrides)  

  O Microsoft Edge mostra uma página de aviso quando os usuários visitam sites que têm erros de SSL. Se você definir essa política como *habilitada* ou *não configurada*, os usuários poderão clicar nessas páginas de aviso. Quando essa política é *desabilitada*, os usuários são impedidos de clicar em qualquer página de aviso. 

- **Configuração padrão do Adobe Flash**  
  **Padrão**: habilitado  
  CSP do Microsoft Edge: [navegador/AllowFlash](https://docs.microsoft.coms/windows/client-management/mdm/policy-csp-browser#browser-allowflash)e [navegador/AllowFlashClickToRun](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-allowflashclicktorun)  

  Determina se os sites que não são cobertos por ' PluginsAllowedForUrls ' ou ' PluginsBlockedForUrls ' podem executar automaticamente o plug-in Adobe Flash. 

  - Selecione ' BlockPlugins ' para bloquear o Adobe Flash em todos os sites
  - Selecione ' ClickToPlay ' para permitir que o Adobe Flash seja executado, mas exija que o usuário clique no espaço reservado para iniciá-lo.
  
   Em qualquer caso, as políticas ' PluginsAllowedForUrls ' e ' PluginsBlockedForUrls ' têm precedência sobre ' DefaultPluginsSetting '. A reprodução automática só é permitida para domínios listados explicitamente na política ' PluginsAllowedForUrls '. 
   Se você quiser habilitar a reprodução automática para todos os sites, considere adicionar http://* e https://* a essa lista. 
   
   - Se você definir essa política como *não configurada*, o usuário poderá alterar essa configuração manualmente. * 2 = bloquear o plug-in do Adobe Flash * 3 = Clique para reproduzir a opção anterior ' 1 ' Set Allow-All, mas essa funcionalidade agora é manipulada apenas pela política ' PluginsAllowedForUrls '. As políticas existentes que usam ' 1 ' funcionarão no modo de clique para reprodução.  
 
  - **Configuração padrão do Adobe Flash**  
    **Padrão**: bloquear o plug-in Adobe Flash

- **Habilitar o isolamento de site para cada site**  
  **Padrão**: habilitado  

  A política ' SitePerProcess ' pode ser usada para impedir que os usuários não possam optar pelo comportamento padrão de isolar todos os sites. Você também pode usar a política IsolateOrigins para isolar origens adicionais e mais refinadas.

  - Quando essa política é definida como *habilitada*, os usuários não podem recusar o comportamento padrão em que cada site é executado em seu próprio processo. 
  - Se você usar *desabilitado* ou *não configurado*, um usuário poderá recusar o isolamento do site. (Por exemplo, usando a entrada "desabilitar isolamento de site" em edge://flags.) Desabilitar a política ou não configurar a política não desliga o isolamento do site.

- **Esquemas de autenticação com suporte**  
  **Padrão**: habilitado  

  Especifica quais esquemas de autenticação HTTP têm suporte. Você pode configurar a política usando estes valores: ' Basic ', ' Digest ', ' NTLM ' e ' Negotiate '. Separe vários valores com vírgulas. Se você não configurar essa política, todos os quatro esquemas serão usados.
 
  - **Esquemas de autenticação com suporte**  
    Selecione uma das seguintes opções: 
    - Basic
    - Digest
    - NTLM *(selecionado por padrão)*
    - Negotiate *(selecionado por padrão)*

- **Habilitar o salvamento de senhas no Gerenciador de senhas**  
  **Padrão**: desabilitado  
  CSP do Microsoft Edge: [navegador/AllowPasswordManager](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-allowpasswordmanager)  

  Habilitar o Microsoft Edge para salvar senhas de usuário. 
  - Se você habilitar essa política, os usuários poderão salvar suas senhas no Microsoft Edge. Na próxima vez que visitarem o site, o Microsoft Edge irá inserir a senha automaticamente. 
  - Se você desabilitar essa política, os usuários não poderão salvar novas senhas, mas ainda podem usar senhas salvas anteriormente. 
  
  Quando você define essa política como *habilitada* ou *desabilitada*, os usuários não podem alterar ou substituir essa política no Microsoft Edge. 
  
  Se você definir isso como *não configurado*, os usuários poderão salvar senhas, bem como desativar esse recurso.

- **Controlar quais extensões não podem ser instaladas**  
  **Padrão**: habilitado  

  Listar as extensões específicas que os usuários não podem instalar no Microsoft Edge. Quando você implanta essa política, todas as extensões nessa lista que foram instaladas anteriormente são desabilitadas e o usuário não poderá habilitá-las. Se você remover um item da lista de extensões bloqueadas, essa extensão será reabilitada automaticamente em qualquer lugar em que tiver sido instalada anteriormente.
  
  Use **\*** para bloquear todas as extensões que não estão explicitamente listadas na lista de permissões. Se essa política estiver definida como *não configurada*, os usuários poderão instalar qualquer extensão no Microsoft Edge. 
  
  Valor de exemplo: extension_id1 extension_id2.  
  <br>
  - **IDs de extensão que o usuário deve ser impedido de instalar (ou * para todos)**  
    Selecione **Adicionar** e especifique extensões adicionais. **\*** é selecionado por padrão.

- **Configurar o Microsoft defender SmartScreen**  
  **Padrão**: habilitado  
  CSP do Microsoft Edge: [navegador/AllowSmartScreen](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-allowsmartscreen)  
  
  Essa configuração de política permite que você configure se deseja ativar o Microsoft defender SmartScreen. O Microsoft defender SmartScreen fornece mensagens de aviso para ajudar a proteger seus usuários contra possíveis golpes de phishing e software mal-intencionado. 
  
  - Por padrão, o Microsoft defender SmartScreen está ativado. Se você habilitar essa configuração, o Microsoft defender SmartScreen será ativado e os usuários não poderão desativá-lo.
  - Se você desabilitar essa configuração, o Microsoft defender SmartScreen será desativado e os usuários não poderão ativá-lo. 
  - Quando definido como *não configurado*, os usuários podem escolher se deseja usar o Microsoft defender SmartScreen. 
  
  Essa política está disponível somente em instâncias do Windows que ingressaram em um domínio do Microsoft Active Director ou em instâncias do Windows 10 pro ou Enterprise que são registradas para o gerenciamento de dispositivos.

- **Permitir hosts de mensagens nativas no nível de usuário (instalado sem permissões de administrador)**  
  **Padrão**: desabilitado  

  Permite a instalação em nível de usuário de hosts de mensagens nativas. 
  - Se você desabilitar essa política, o Microsoft Edge usará apenas hosts de mensagens nativos instalados no nível do sistema. Por padrão, se você não configurar essa política, o Microsoft Edge permitirá o uso de hosts de mensagens nativas no nível de usuário.

## <a name="next-steps"></a>Próximos passos

[Usar linhas de base de segurança no Intune](security-baselines.md)
