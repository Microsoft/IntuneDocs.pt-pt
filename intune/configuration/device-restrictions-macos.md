---
title: Definições dos dispositivos macOS no Microsoft Intune – Azure | Microsoft Docs
titleSuffix: ''
description: Adicionar, configurar ou criar definições em dispositivos macOS para restringir funcionalidades, incluindo a definição de requisitos de palavra-passe, controlar o ecrã bloqueado, utilizar aplicações incorporadas, adicionar aplicações restritas ou aprovadas, gerir dispositivos Bluetooth, ligar à cloud para cópia de segurança e armazenamento, ativar o modo de quiosque, adicionar domínios e controlar como os utilizadores interagem com o browser Safari no Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/10/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 675f98d952cb243b5aa43e94972b3ef42fbee463
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71730732"
---
# <a name="macos-device-settings-to-allow-or-restrict-features-using-intune"></a>Definições dos dispositivos macOS para permitir ou restringir funcionalidades com o Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Este artigo apresenta e descreve as diferentes definições que pode controlar nos dispositivos macOS. Como parte da solução de gestão de dispositivos móveis (MDM), utilize estas definições para permitir ou desativar funcionalidades, definir regras de palavra-passe, permitir ou restringir aplicações específicas e muito mais.

Estas definições são adicionadas a um perfil de configuração do dispositivo no Intune e, em seguida, atribuídas ou implementadas nos dispositivos macOS.

## <a name="before-you-begin"></a>Antes de começar

[Crie um perfil de configuração de restrições do dispositivo](../device-restrictions-configure.md).

> [!NOTE]
> Essas configurações se aplicam a diferentes tipos de registro. Para obter mais informações sobre os diferentes tipos de registro, consulte [registro do MacOS](../macos-enroll.md).

## <a name="general"></a>Geral

### <a name="settings-apply-to-device-enrollment"></a>As configurações se aplicam a: Inscrição de dispositivos

- **Pesquisa de definição**: **Bloquear** impede que o utilizador realce uma palavra e, em seguida, procure a sua definição no dispositivo. **Não configurado** (predefinição) permite o acesso ao recurso de pesquisa de definição.
- **Ditado**: **Bloquear** impede o utilizador de utilizar entradas de voz para introduzir texto. **Não configurado** (predefinição) permite que o utilizador utilize a entrada de ditado.
- **Caching de conteúdo**: escolha **Não configurado** (predefinição) para ativar a colocação de conteúdos em cache. A colocação de conteúdos em cache armazena dados de aplicações, dados de browsers, downloads e muito mais, localmente no dispositivo. Selecione **Bloquear** para impedir que estes dados sejam armazenados na cache.

  Para obter mais informações sobre a colocação de conteúdos em cache no macOS, veja [Gerir a cache de conteúdo no Mac](https://support.apple.com/guide/mac-help/manage-content-caching-on-mac-mchl3b6c3720/mac) (abre outro site).

  Esta funcionalidade aplica-se a:  
  - macOS 10,13 e mais recente

- **Adiar atualizações de software**: quando definido como **Não configurado** (predefinição), as atualizações de software são mostradas no dispositivo à medida que a Apple as lança. Por exemplo, se uma atualização do macOS for lançada pela Apple numa data específica, essa atualização será mostrada naturalmente no dispositivo por volta da data de lançamento. São permitidas atualizações de compilações de seed sem atraso.

  **Ativar** permite-lhe adiar a apresentação das atualizações de software nos dispositivos, entre 0 e 90 dias. Esta definição não controla quando as atualizações são ou não instaladas. 

  - **Adiar visibilidade das atualizações de software**: introduza um valor entre 0 e 90 dias. Quando o adiamento expirar, os utilizadores recebem uma notificação para atualizar para a versão mais antiga do SO disponível quando o adiamento foi acionado.

    Por exemplo, se uma atualização do macOS estiver disponível em **1º de janeiro**e a visibilidade do **atraso** for definida como **5 dias**, a atualização não será mostrada como uma atualização disponível. No **sexto dia** após o lançamento, essa atualização estará disponível e os utilizadores finais poderão instalá-la.

    Esta funcionalidade aplica-se a:  
    - macOS 10.13.4 e mais recente

- **Capturas de tela**: O dispositivo deve ser registrado no DEP (registro de dispositivo automatizado) da Apple. Quando definido como **Bloquear**, os usuários não podem salvar uma captura de tela da exibição. Ele também impede que o aplicativo sala de aula Observe telas remotas. **Não configurado** (padrão) permite que os usuários capturem capturas de tela e permite que o aplicativo sala de aula exiba telas remotas.

### <a name="settings-apply-to-automated-device-enrollment"></a>As configurações se aplicam a: Registro de dispositivo automatizado

- **Observação de tela remota por meio do aplicativo sala de aula**: **Desabilitar** impede que os professores usem o aplicativo sala de aula para ver as telas dos alunos. **Não configurado** (padrão) permite que os professores vejam as telas dos alunos.

  Para usar essa configuração, defina a configuração **capturas de tela** como **não configurado** (capturas de tela são permitidas).

- **Observação de tela não solicitada por aplicativo de sala de aula**: **Permitir** permite que os professores vejam as telas dos alunos sem exigir que o aluno concorde. **Não configurado** (padrão) exige que o aluno concorde antes que o professor possa ver as telas.

  Para usar essa configuração, defina a configuração **capturas de tela** como **não configurado** (capturas de tela são permitidas).

- **Os alunos devem solicitar permissão para sair da classe sala de aula**: **Exigir** que os alunos sejam inscritos em um curso de sala de aula não gerenciado para obter aprovação do professor para deixar o curso. **Não configurado** (padrão) permite que o aluno deixe o curso sempre que o aluno escolher.

- **Os professores podem bloquear automaticamente os dispositivos ou aplicativos no aplicativo sala de aula**: **Permitir** permite que os professores bloqueiem o dispositivo ou aplicativo de um aluno sem a aprovação do aluno. **Não configurado** (padrão) exige que o aluno concorde antes que o professor possa bloquear o dispositivo ou o aplicativo.

- **Os alunos podem ingressar automaticamente na classe sala de aula**: **Permitir** que os alunos ingressem em uma classe sem avisar o professor. **Não configurado** (padrão) requer aprovação de professor para ingressar em uma classe.

## <a name="password"></a>Palavra-passe

### <a name="settings-apply-to-device-enrollment"></a>As configurações se aplicam a: Inscrição de dispositivos

- **Palavra-passe**: **Exigir** que o utilizador final introduza uma palavra-passe para aceder ao dispositivo. **Não configurado** (padrão) não requer uma senha. Ele também não força nenhuma restrição, como o bloqueio de senhas simples ou a definição de um comprimento mínimo.
  - **Tipo obrigatório de palavra-passe**: especifique se a palavra-passe pode ser Apenas numérica ou se tem de ser Alfanumérica (conter letras e números).

    Esta funcionalidade aplica-se a:  
    - macOS 10.10.3 e mais recente

  - **Número de carateres não alfanuméricos na palavra-passe**: Especifica o número de carateres complexos necessários na palavra-passe (de **0** a **4**).<br>Um caráter complexo é um símbolo, por exemplo " **?** ".
  - **Comprimento mínimo da palavra-passe**: introduza o comprimento mínimo da palavra-passe que um utilizador tem de configurar (entre **4** e **16** carateres).
  - **Palavras-passe simples**: Permite a utilização de palavras-passe simples, tal como **0000** ou **1234**.
  - **Máximo de minutos após o bloqueio de ecrã antes de ser exigida a palavra-passe**: Especifica o período de tempo durante o qual o computador tem de estar inativo antes de ser exigida uma palavra-passe para o desbloquear.
  - **Máximo de minutos de inatividade até o ecrã ser bloqueado**: especifique o período de tempo durante o qual o computador tem de estar inativo antes de o ecrã ser bloqueado.
  - **Expiração da palavra-passe (dias)** : Especifica o número de dias que decorrem antes de o utilizador ter de alterar a palavra-passe (de **1** a **255** dias).
  - **Impedir a reutilização de palavras-passe anteriores**: introduza o número de palavras-passe utilizadas anteriormente que não podem ser utilizadas novamente, de **1** a **24**.

- **Impedir o Utilizador de Modificar o Código de Acesso**: escolha **Bloquear** para impedir que o código de acesso seja alterado, adicionado ou removido. **Não configurado** (predefinição) permite que os códigos de acesso sejam adicionados, alterados ou removidos.
- **Bloquear Desbloqueio por Impressão Digital**: escolha **Bloquear** para impedir a utilização de uma impressão digital para desbloquear o dispositivo. **Não configurado** (predefinição) permite ao utilizador desbloquear o dispositivo através de uma impressão digital.

- **Bloquear Preenchimento Automático de Palavra-passes**: escolha **Bloquear** para impedir a utilização da funcionalidade Preenchimento Automático de Palavras-passe no macOS. A escolha de **Bloquear** também tem o seguinte impacto:

  - Não é pedido aos utilizadores que utilizem uma palavra-passe guardada no Safari nem noutras aplicações.
  - As Palavras-passe Seguras automáticas estão desativadas, pelo que não são sugeridas aos utilizadores.

  **Não configurado** (predefinição) permite estas funcionalidades.

- **Bloquear pedidos de proximidade de palavra-passe**: escolha **Bloquear** para que o dispositivo de um utilizador não peça palavras-passe aos dispositivos próximos. **Não configurado** (predefinição) permite estes pedidos de palavras-passe.

- **Bloquear partilha de palavras-passe**: **Bloquear** impede a partilha de palavras-passe entre dispositivos com o AirDrop. **Não configurado** (predefinição) permite que as palavras-passe sejam partilhadas.

## <a name="built-in-apps"></a>Aplicações Incorporadas

### <a name="settings-apply-to-device-enrollment"></a>As configurações se aplicam a: Inscrição de dispositivos

- **Bloquear Preenchimento Automático do Safari**: **Bloquear** desativa a funcionalidade de preenchimento automático no Safari no dispositivo. **Não configurado** (predefinição) permite que os utilizadores alterem as definições de preenchimento automático no browser.
- **Bloquear Câmara**: escolha **Bloquear** para impedir o acesso à câmara no dispositivo. **Não configurado** (predefinição) permite o acesso à câmara do dispositivo.
- **Bloquear Apple Music**: **Bloquear** reverte a aplicação Music para o modo clássico e desativa o Serviço Music. **Não configurado** (predefinição) permite a utilização da aplicação Apple Music.
- **Bloquear Resultados de Pesquisa na Internet com Spotlight**: **Bloquear** impede a pesquisa Spotlight de devolver resultados de uma pesquisa da Internet. **Não configurado** (predefinição) permite que o Spotlight se ligue à Internet para fornecer resultados da pesquisa.
- **Bloquear Transferência de Ficheiros no iTunes**: **Bloquear** desativa os serviços de partilha de ficheiros da aplicação. **Não configurado** (predefinição) permite que os serviços partilhem ficheiros da aplicação.

  Esta funcionalidade aplica-se a:  
  - macOS 10,13 e mais recente

## <a name="restricted-apps"></a>Aplicações restritas

### <a name="settings-apply-to-device-enrollment"></a>As configurações se aplicam a: Inscrição de dispositivos

- **Tipo de lista de aplicativos restritos**: Crie uma lista de aplicativos que os usuários não têm permissão para instalar ou usar. As opções são:

  - **Não configurado** (predefinição): Não há restrições do Intune. Os usuários têm acesso aos aplicativos que você atribui e aos aplicativos internos.
  - **Aplicações proibidas**: Aplicativos não gerenciados pelo Intune que você não deseja instalar no dispositivo. Os usuários não são impedidos de instalar um aplicativo proibido. Mas se um usuário instalar um aplicativo dessa lista, ele será relatado no Intune.
  - **Aplicações aprovadas**: Aplicativos que os usuários têm permissão para instalar. Os utilizadores não podem instalar aplicações que não estejam listadas. As aplicações geridas pelo Intune são automaticamente permitidas. Os utilizadores não são impedidos de instalar uma aplicação que não esteja na lista aprovada. Mas, se isso for feito, ele será relatado no Intune.
- **ID do pacote da aplicação**: Insira a [ID de lote](bundle-ids-built-in-ios-apps.md) do aplicativo que você deseja. Você pode mostrar ou ocultar aplicativos internos e aplicativos de linha de negócios. O site da Apple tem uma lista de [aplicativos da Apple internos](https://support.apple.com/HT208094).
- **Nome da aplicação**: Insira o nome do aplicativo que você deseja. Você pode mostrar ou ocultar aplicativos internos e aplicativos de linha de negócios. O site da Apple tem uma lista de [aplicativos da Apple internos](https://support.apple.com/HT208094).
- **Publicador**: Insira o editor do aplicativo desejado.

Para adicionar aplicações a estas listas, pode:

- **Adicionar**: Selecione para criar sua lista de aplicativos.
- **Importe** um arquivo CSV com detalhes sobre o aplicativo, incluindo a URL. Utilize o formato `<app bundle ID>, <app name>, <app publisher>`. Ou, **Exportar** para criar uma lista de aplicativos que você adicionou, no mesmo formato.

## <a name="connected-devices"></a>Dispositivos ligados

### <a name="settings-apply-to-device-enrollment"></a>As configurações se aplicam a: Inscrição de dispositivos

- **Bloquear AirDrop**: **Bloquear** impede que o AirDrop seja utilizado no dispositivo. **Não configurado** (predefinição) permite utilizar a funcionalidade AirDrop para trocar conteúdo com os dispositivos próximos.
- **Bloquear Desbloqueio Automático do Apple Watch**: **Bloquear** impede os utilizadores de desbloquear o dispositivo macOS com o Apple Watch. **Não configurado** (predefinição) permite aos utilizadores desbloquear o dispositivo macOS com o Apple Watch.

## <a name="cloud-and-storage"></a>Cloud e armazenamento

### <a name="settings-apply-to-device-enrollment"></a>As configurações se aplicam a: Inscrição de dispositivos

- **Bloquear sincronização do Keychain com o iCloud**: escolha **Bloquear** para desativar a sincronização das credenciais armazenadas no Keychain com o iCloud. **Não configurado** (predefinição) permite aos utilizadores sincronizar estas credenciais.
- **Bloquear Sincronização de Documentos para iCloud**: **Bloquear** impede o iCloud de sincronizar documentos e dados. **Não configurado** (predefinição) permite a sincronização de documentos e pares chave-valor com o espaço de armazenamento do iCloud.
- **Bloquear Cópia de Segurança do Correio para iCloud**: **Bloquear** impede que o iCloud seja sincronizado com a aplicação Correio do macOS. **Não configurado** (predefinição) permite a sincronização do Correio com o iCloud.
- **Bloquear Cópia de Segurança de Contactos para iCloud**: **Bloquear** impede que os contactos dos dispositivos sejam sincronizados com o iCloud. **Não configurado** (predefinição) permite a sincronização de contactos através do iCloud.
- **Bloquear Cópia de Segurança do Calendário para iCloud**: **Bloquear** impede que o iCloud seja sincronizado com a aplicação Calendário do macOS. **Não configurado** (predefinição) permite a sincronização do Calendário com o iCloud.
- **Bloquear Cópia de Segurança de Lembretes para iCloud**: **Bloquear** impede que o iCloud seja sincronizado com a aplicação Lembretes do macOS. **Não configurado** (predefinição) permite a sincronização dos Lembretes com o iCloud.
- **Bloquear Cópia de Segurança dos Marcadores para iCloud**: **Bloquear** impede que o iCloud seja sincronizado com os Marcadores dos dispositivos. **Não configurado** (predefinição) permite a sincronização de Marcadores com o iCloud.
- **Bloquear Cópia de Segurança das Notas para iCloud**: **Bloquear** impede que o iCloud seja sincronizado com as Notas dos dispositivos. **Não configurado** (predefinição) permite a sincronização das Notas com o iCloud.
- **Bloquear biblioteca de fotos do icloud**: **Bloquear** desabilita a biblioteca de fotos do icloud e impede que o iCloud sincronize as fotos dos dispositivos. Todas as fotos que não forem totalmente baixadas da biblioteca de fotos do iCloud serão removidas do armazenamento local no dispositivo. **Não configurado** (padrão) permite sincronizar fotos entre o dispositivo e a biblioteca de fotos do iCloud.
- **Entrega**: **Não configurado** (padrão) permite que os usuários iniciem o trabalho em um dispositivo macOS e, em seguida, continuem o trabalho iniciado em outro dispositivo iOS ou macOS. **Bloquear** impede o recurso de entrega no dispositivo. 

  Esta funcionalidade aplica-se a:  
  - macOS 10,15 e mais recente

## <a name="domains"></a>Domínios

### <a name="settings-apply-to-device-enrollment"></a>As configurações se aplicam a: Inscrição de dispositivos

- **URL do Domínio de E-mail**: **Adicione** uma ou mais URLs à lista. Quando os usuários recebem um email de um domínio diferente daquele configurado, o email é marcado como não confiável no aplicativo macOS mail.

## <a name="next-steps"></a>Passos seguintes

[Atribua o perfil](../device-profile-assign.md) e [monitorize o respetivo estado](../device-profile-monitor.md).

Também pode restringir as funcionalidades e as definições dos dispositivos nos dispositivos [iOS](../device-restrictions-ios.md).
