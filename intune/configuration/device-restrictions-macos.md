---
title: Definições dos dispositivos macOS no Microsoft Intune – Azure | Microsoft Docs
titleSuffix: ''
description: Adicionar, configurar ou criar definições em dispositivos macOS para restringir funcionalidades, incluindo a definição de requisitos de palavra-passe, controlar o ecrã bloqueado, utilizar aplicações incorporadas, adicionar aplicações restritas ou aprovadas, gerir dispositivos Bluetooth, ligar à cloud para cópia de segurança e armazenamento, ativar o modo de quiosque, adicionar domínios e controlar como os utilizadores interagem com o browser Safari no Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/22/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6513c09f252d5a914ace4e57e5a593877a387172
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/19/2019
ms.locfileid: "75206555"
---
# <a name="macos-device-settings-to-allow-or-restrict-features-using-intune"></a>Definições dos dispositivos macOS para permitir ou restringir funcionalidades com o Intune



Este artigo apresenta e descreve as diferentes definições que pode controlar nos dispositivos macOS. Como parte da solução de gestão de dispositivos móveis (MDM), utilize estas definições para permitir ou desativar funcionalidades, definir regras de palavra-passe, permitir ou restringir aplicações específicas e muito mais.

Estas definições são adicionadas a um perfil de configuração do dispositivo no Intune e, em seguida, atribuídas ou implementadas nos dispositivos macOS.

## <a name="before-you-begin"></a>Antes de começar

[Crie um perfil de configuração de restrições do dispositivo](../device-restrictions-configure.md).

> [!NOTE]
> Essas configurações se aplicam a diferentes tipos de registro. Para obter mais informações sobre os diferentes tipos de registro, consulte [registro do MacOS](../macos-enroll.md).

## <a name="general"></a>Geral

### <a name="settings-apply-to-device-enrollment-and-automated-device-enrollment"></a>As configurações se aplicam a: registro de dispositivo e registro de dispositivo automatizado

- **Pesquisa de definição**: **Bloquear** impede que o usuário realce uma palavra e, em seguida, procure sua definição no dispositivo. **Não configurado** (predefinição) permite o acesso ao recurso de pesquisa de definição.
- **Dictation**: **Block** impede que o usuário use a entrada de voz para inserir texto. **Não configurado** (predefinição) permite que o utilizador utilize a entrada de ditado.
- **Cache de conteúdo**: escolha **não configurado** (padrão) para habilitar o Caching de conteúdo. A colocação de conteúdos em cache armazena dados de aplicações, dados de browsers, downloads e muito mais, localmente no dispositivo. Selecione **Bloquear** para impedir que estes dados sejam armazenados na cache.

  Para obter mais informações sobre a colocação de conteúdos em cache no macOS, veja [Gerir a cache de conteúdo no Mac](https://support.apple.com/guide/mac-help/manage-content-caching-on-mac-mchl3b6c3720/mac) (abre outro site).

  Esta funcionalidade aplica-se a:  
  - macOS 10,13 e mais recente

- **Adiar atualizações de software**: quando definido como **não configurado** (padrão), as atualizações de software são mostradas no dispositivo à medida que a Apple as libera. Por exemplo, se uma atualização do macOS for lançada pela Apple numa data específica, essa atualização será mostrada naturalmente no dispositivo por volta da data de lançamento. São permitidas atualizações de compilações de seed sem atraso.

  **Ativar** permite-lhe adiar a apresentação das atualizações de software nos dispositivos, entre 0 e 90 dias. Esta definição não controla quando as atualizações são ou não instaladas. 

  - **Atrasar a visibilidade das atualizações de software**: Insira um valor de 0-90 dias. Quando o adiamento expirar, os utilizadores recebem uma notificação para atualizar para a versão mais antiga do SO disponível quando o adiamento foi acionado.

    Por exemplo, se uma atualização do macOS estiver disponível em **1º de janeiro**e a visibilidade do **atraso** for definida como **5 dias**, a atualização não será mostrada como uma atualização disponível. No **sexto dia** após o lançamento, essa atualização estará disponível e os utilizadores finais poderão instalá-la.

    Esta funcionalidade aplica-se a:  
    - macOS 10.13.4 e mais recente

- **Capturas de tela**: o dispositivo deve ser registrado no Dep (registro de dispositivo automatizado) da Apple. Quando definido como **Bloquear**, os usuários não podem salvar uma captura de tela da exibição. Ele também impede que o aplicativo sala de aula Observe telas remotas. **Não configurado** (padrão) permite que os usuários capturem capturas de tela e permite que o aplicativo sala de aula exiba telas remotas.

### <a name="settings-apply-to-automated-device-enrollment"></a>As configurações se aplicam a: registro de dispositivo automatizado

- **Observação de tela remota por meio do aplicativo sala de aula**: **desabilitar** impede que os professores usem o aplicativo sala de aula para ver as telas dos alunos. **Não configurado** (padrão) permite que os professores vejam as telas dos alunos.

  Para usar essa configuração, defina a configuração **capturas de tela** como **não configurado** (capturas de tela são permitidas).

- **Observação de tela não solicitada pelo aplicativo sala de aula**: **permitir** permite que os professores vejam as telas dos alunos sem exigir que o aluno concorde. **Não configurado** (padrão) exige que o aluno concorde antes que o professor possa ver as telas.

  Para usar essa configuração, defina a configuração **capturas de tela** como **não configurado** (capturas de tela são permitidas).

- **Os alunos devem solicitar permissão para sair da classe sala de aula**: **exigir** força alunos inscritos em um curso de sala de aula não gerenciado para obter aprovação do professor para deixar o curso. **Não configurado** (padrão) permite que o aluno deixe o curso sempre que o aluno escolher.

- **Os professores podem bloquear automaticamente dispositivos ou aplicativos no aplicativo sala de aula**: **permitir** permite que os professores bloqueiem o dispositivo ou aplicativo de um aluno sem a aprovação do aluno. **Não configurado** (padrão) exige que o aluno concorde antes que o professor possa bloquear o dispositivo ou o aplicativo.

- **Os alunos podem unir a classe sala de aula automaticamente**: **permitir** que os alunos ingressem em uma classe sem avisar o professor. **Não configurado** (padrão) requer aprovação de professor para ingressar em uma classe.

## <a name="password"></a>Palavra-passe

### <a name="settings-apply-to-device-enrollment-and-automated-device-enrollment"></a>As configurações se aplicam a: registro de dispositivo e registro de dispositivo automatizado

- **Senha**: **exige** que o usuário final Insira uma senha para acessar o dispositivo. **Não configurado** (padrão) não requer uma senha. Ele também não força nenhuma restrição, como o bloqueio de senhas simples ou a definição de um comprimento mínimo.
  - **Tipo de senha necessária**: especifique se a senha pode ser somente numérica ou se deve ser alfanumérica (conter letras e números).

    Esta funcionalidade aplica-se a:  
    - macOS 10.10.3 e mais recente

  - **Número de caracteres não alfanuméricos na senha**: especifique o número de caracteres complexos necessários na senha (**0** a **4**).<br>Um caráter complexo é um símbolo, por exemplo "**?**".
  - **Comprimento mínimo da senha**: Insira o comprimento mínimo da senha que um usuário deve configurar (entre **4** e **16** caracteres).
  - **Senhas simples**: permitir o uso de senhas simples, como **0000** ou **1234**.
  - **Máximo de minutos após o bloqueio de tela antes da senha ser necessária**: especifique quanto tempo o computador deve ficar inativo antes que uma senha seja necessária para desbloqueá-lo.
  - **Máximo de minutos de inatividade até a tela ser bloqueada**: especifique o período de tempo que o computador deve ficar ocioso antes que a tela seja bloqueada.
  - **Expiração da senha (dias)**: especifique o número de dias decorridos antes que o usuário precise alterar a senha (de**1** a **255** dias).
  - **Evitar a reutilização de senhas anteriores**: Insira o número de senhas usadas anteriormente que não podem ser reutilizadas, de **1** a **24**.

- **Impedir que o usuário modifique a senha**: escolha **Bloquear** para impedir que a senha seja alterada, adicionada ou removida. **Não configurado** (predefinição) permite que os códigos de acesso sejam adicionados, alterados ou removidos.
- **Bloquear impressão digital desbloquear**: escolha **Bloquear** para impedir o uso de uma impressão digital para desbloquear o dispositivo. **Não configurado** (predefinição) permite ao utilizador desbloquear o dispositivo através de uma impressão digital.

- **Bloquear AutoPreenchimento de senha**: escolha **Bloquear** para impedir o uso do recurso de senhas de preenchimento automático no MacOS. A escolha de **Bloquear** também tem o seguinte impacto:

  - Não é pedido aos utilizadores que utilizem uma palavra-passe guardada no Safari nem noutras aplicações.
  - As Palavras-passe Seguras automáticas estão desativadas, pelo que não são sugeridas aos utilizadores.

  **Não configurado** (predefinição) permite estas funcionalidades.

- **Bloquear solicitações de proximidade de senha**: escolha **Bloquear** para que o dispositivo de um usuário não solicite senhas de dispositivos próximos. **Não configurado** (predefinição) permite estes pedidos de palavras-passe.

- **Bloquear o compartilhamento de senha**: **Bloquear** impede o compartilhamento de senhas entre dispositivos usando o essoltar. **Não configurado** (predefinição) permite que as palavras-passe sejam partilhadas.

## <a name="built-in-apps"></a>Aplicações Incorporadas

### <a name="settings-apply-to-device-enrollment-and-automated-device-enrollment"></a>As configurações se aplicam a: registro de dispositivo e registro de dispositivo automatizado

- **Bloquear preenchimento do Safari**: o **bloco** desabilita o recurso de preenchimento automático no Safari no dispositivo. **Não configurado** (predefinição) permite que os utilizadores alterem as definições de preenchimento automático no browser.
- **Bloquear câmera**: escolha **Bloquear** para impedir o acesso à câmera no dispositivo. **Não configurado** (predefinição) permite o acesso à câmara do dispositivo.
- **Bloquear Apple Music**: o **bloco** reverte o aplicativo de música para o modo clássico e desabilita o serviço de música. **Não configurado** (predefinição) permite a utilização da aplicação Apple Music.
- **Bloquear resultados da pesquisa na Internet do Spotlight**: **Bloquear** impede que o Spotlight retorne qualquer resultado de uma pesquisa na Internet. **Não configurado** (predefinição) permite que o Spotlight se ligue à Internet para fornecer resultados da pesquisa.
- **Bloquear transferência de arquivos usando iTunes**: **Block** desabilita os serviços de compartilhamento de arquivos de aplicativo. **Não configurado** (predefinição) permite que os serviços partilhem ficheiros da aplicação.

  Esta funcionalidade aplica-se a:  
  - macOS 10,13 e mais recente

## <a name="restricted-apps"></a>Aplicações restritas

### <a name="settings-apply-to-device-enrollment-and-automated-device-enrollment"></a>As configurações se aplicam a: registro de dispositivo e registro de dispositivo automatizado

- **Tipo de lista de aplicativos restritos**: Crie uma lista de aplicativos que os usuários não têm permissão para instalar ou usar. As opções são:

  - **Não configurado** (padrão): não há restrições do Intune. Os usuários têm acesso aos aplicativos que você atribui e aos aplicativos internos.
  - **Aplicativos proibidos**: aplicativos não gerenciados pelo Intune que você não deseja instalar no dispositivo. Os usuários não são impedidos de instalar um aplicativo proibido. Mas se um usuário instalar um aplicativo dessa lista, ele será relatado no Intune.
  - **Aplicativos aprovados**: aplicativos que os usuários têm permissão para instalar. Os utilizadores não podem instalar aplicações que não estejam listadas. As aplicações geridas pelo Intune são automaticamente permitidas. Os utilizadores não são impedidos de instalar uma aplicação que não esteja na lista aprovada. Mas, se isso for feito, ele será relatado no Intune.
- **ID do lote de aplicativos**: Insira a [ID de lote](bundle-ids-built-in-ios-apps.md) do aplicativo que você deseja. Você pode mostrar ou ocultar aplicativos internos e aplicativos de linha de negócios. O site da Apple tem uma lista de [aplicativos da Apple internos](https://support.apple.com/HT208094).
- **Nome do aplicativo**: Insira o nome do aplicativo que você deseja. Você pode mostrar ou ocultar aplicativos internos e aplicativos de linha de negócios. O site da Apple tem uma lista de [aplicativos da Apple internos](https://support.apple.com/HT208094).
- **Editor**: Insira o editor do aplicativo desejado.

Para adicionar aplicações a estas listas, pode:

- **Adicionar**: Selecione para criar sua lista de aplicativos.
- **Importe** um arquivo CSV com detalhes sobre o aplicativo, incluindo a URL. Utilize o formato `<app bundle ID>, <app name>, <app publisher>`. Ou, **Exportar** para criar uma lista de aplicativos que você adicionou, no mesmo formato.

## <a name="connected-devices"></a>Dispositivos ligados

### <a name="settings-apply-to-device-enrollment-and-automated-device-enrollment"></a>As configurações se aplicam a: registro de dispositivo e registro de dispositivo automatizado

- **Bloquear o endrop**: o **bloco** impede o uso do essoltar no dispositivo. **Não configurado** (predefinição) permite utilizar a funcionalidade AirDrop para trocar conteúdo com os dispositivos próximos.
- **Bloquear Apple Watch desbloquear automaticamente**: **Bloquear** impede que os usuários desbloqueiem seu dispositivo MacOS com seus Apple Watch. **Não configurado** (predefinição) permite aos utilizadores desbloquear o dispositivo macOS com o Apple Watch.

## <a name="cloud-and-storage"></a>Cloud e armazenamento

### <a name="settings-apply-to-device-enrollment-and-automated-device-enrollment"></a>As configurações se aplicam a: registro de dispositivo e registro de dispositivo automatizado

- **Bloquear sincronização**de conjunto de chaves do icloud: escolha o **bloco** para desabilitar a sincronização de credenciais armazenadas no conjunto de chaves no iCloud. **Não configurado** (predefinição) permite aos utilizadores sincronizar estas credenciais.
- **Bloquear a sincronização de documentos do icloud**: **Bloquear** impede que o iCloud sincronize documentos e dados. **Não configurado** (predefinição) permite a sincronização de documentos e pares chave-valor com o espaço de armazenamento do iCloud.
- **Bloquear o backup de email do icloud**: **Bloquear** impede que o iCloud Sincronize com o aplicativo de email MacOS. **Não configurado** (predefinição) permite a sincronização do Correio com o iCloud.
- **Bloquear o backup de contato do icloud**: **Bloquear** impede que o iCloud sincronize os contatos dos dispositivos. **Não configurado** (predefinição) permite a sincronização de contactos através do iCloud.
- **Bloquear o backup do calendário do icloud**: **Bloquear** impede que o iCloud Sincronize com o aplicativo de calendário do MacOS. **Não configurado** (predefinição) permite a sincronização do Calendário com o iCloud.
- **Bloquear backup de lembrete do icloud**: **Bloquear** impede que o iCloud Sincronize com o aplicativo de lembretes do MacOS. **Não configurado** (predefinição) permite a sincronização dos Lembretes com o iCloud.
- **Bloquear o backup do indicador do icloud**: **Bloquear** impede o iCloud de sincronizar os indicadores de dispositivos. **Não configurado** (predefinição) permite a sincronização de Marcadores com o iCloud.
- **Bloquear backup das notas do icloud**: **Bloquear** impede que o iCloud sincronize as notas dos dispositivos. **Não configurado** (predefinição) permite a sincronização das Notas com o iCloud.
- **Bloquear biblioteca de fotos do icloud**: o **bloco** desabilita a biblioteca de fotos do icloud e impede que o iCloud sincronize as fotos dos dispositivos. Todas as fotos que não forem totalmente baixadas da biblioteca de fotos do iCloud serão removidas do armazenamento local no dispositivo. **Não configurado** (padrão) permite a sincronização de fotos entre o dispositivo e a biblioteca de fotos do icloud.
- **Entrega**: **não configurado** (padrão) permite que os usuários iniciem o trabalho em um dispositivo MacOS e continuem o trabalho iniciado em outro dispositivo IOS ou MacOS. **Bloquear** impede o recurso de entrega no dispositivo. 

  Esta funcionalidade aplica-se a:  
  - macOS 10,15 e mais recente

## <a name="domains"></a>Domains

### <a name="settings-apply-to-device-enrollment-and-automated-device-enrollment"></a>As configurações se aplicam a: registro de dispositivo e registro de dispositivo automatizado

- **URL do domínio de email**: **adicione** uma ou mais URLs à lista. Quando os usuários recebem um email de um domínio diferente daquele configurado, o email é marcado como não confiável no aplicativo macOS mail.

## <a name="next-steps"></a>Próximos passos

[Atribua o perfil](../device-profile-assign.md) e [monitorize o respetivo estado](../device-profile-monitor.md).

Também pode restringir as funcionalidades e as definições dos dispositivos nos dispositivos [iOS](../device-restrictions-ios.md).
