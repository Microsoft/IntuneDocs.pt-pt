---
title: Definições dos dispositivos macOS no Microsoft Intune – Azure | Microsoft Docs
titleSuffix: ''
description: Adicionar, configurar ou criar definições em dispositivos macOS para restringir funcionalidades, incluindo a definição de requisitos de palavra-passe, controlar o ecrã bloqueado, utilizar aplicações incorporadas, adicionar aplicações restritas ou aprovadas, gerir dispositivos Bluetooth, ligar à cloud para cópia de segurança e armazenamento, ativar o modo de quiosque, adicionar domínios e controlar como os utilizadores interagem com o browser Safari no Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/18/2020
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3d26c4c6cd05a411555f7824ad21b72431eb569c
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/20/2020
ms.locfileid: "77511177"
---
# <a name="macos-device-settings-to-allow-or-restrict-features-using-intune"></a>Definições dos dispositivos macOS para permitir ou restringir funcionalidades com o Intune



Este artigo apresenta e descreve as diferentes definições que pode controlar nos dispositivos macOS. Como parte da solução de gestão de dispositivos móveis (MDM), utilize estas definições para permitir ou desativar funcionalidades, definir regras de palavra-passe, permitir ou restringir aplicações específicas e muito mais.

Estas definições são adicionadas a um perfil de configuração do dispositivo no Intune e, em seguida, atribuídas ou implementadas nos dispositivos macOS.

## <a name="before-you-begin"></a>Antes de começar

[Crie um perfil de configuração de restrições do dispositivo](../device-restrictions-configure.md).

> [!NOTE]
> Estas definições aplicam-se a diferentes tipos de matrículas. Para obter mais informações sobre os diferentes tipos de matrículas, consulte a [inscrição do macOS.](../macos-enroll.md)

## <a name="general"></a>Geral

### <a name="settings-apply-to-device-enrollment-and-automated-device-enrollment"></a>Definições aplicam-se a: Inscrição do dispositivo e inscrição automática de dispositivos

- **Definição Lookup**: **O bloco** impede o utilizador de realçar uma palavra e, em seguida, procurar a sua definição no dispositivo. **Não configurado** (predefinição) permite o acesso ao recurso de pesquisa de definição.
- **Ditado**: **O bloco** impede o utilizador de utilizar a entrada de voz para introduzir texto. **Não configurado** (predefinição) permite que o utilizador utilize a entrada de ditado.
- **Cachecamento de conteúdo**: Escolha **Não configurado** (predefinido) para ativar o cache de conteúdo. A colocação de conteúdos em cache armazena dados de aplicações, dados de browsers, downloads e muito mais, localmente no dispositivo. Selecione **Bloquear** para impedir que estes dados sejam armazenados na cache.

  Para obter mais informações sobre a colocação de conteúdos em cache no macOS, veja [Gerir a cache de conteúdo no Mac](https://support.apple.com/guide/mac-help/manage-content-caching-on-mac-mchl3b6c3720/mac) (abre outro site).

  Esta funcionalidade aplica-se a:  
  - macOS 10.13 e mais recente

- **Defer atualizações de software**: Quando definido para **Não configurado** (padrão), as atualizações de software são mostradas no dispositivo à medida que a Apple as lança. Por exemplo, se uma atualização do macOS for lançada pela Apple numa data específica, essa atualização será mostrada naturalmente no dispositivo por volta da data de lançamento. São permitidas atualizações de compilações de seed sem atraso.

  **Ativar** permite-lhe adiar a apresentação das atualizações de software nos dispositivos, entre 0 e 90 dias. Esta definição não controla quando as atualizações são ou não instaladas. 

  - **Adiar a visibilidade das atualizações de software**: Introduza um valor de 0-90 dias. Quando o adiamento expirar, os utilizadores recebem uma notificação para atualizar para a versão mais antiga do SO disponível quando o adiamento foi acionado.

    Por exemplo, se uma atualização do macOS estiver disponível a **1 de janeiro**, e a visibilidade do **Atraso** for definida para **5 dias,** então a atualização não é mostrada como uma atualização disponível. No **sexto dia** após o lançamento, essa atualização estará disponível e os utilizadores finais poderão instalá-la.

    Esta funcionalidade aplica-se a:  
    - macOS 10.13.4 e mais recente

- **Screenshots**: O dispositivo deve ser matriculado na Inscrição automática de Dispositivos da Apple (DEP). Quando definido para **bloquear,** os utilizadores não podem guardar uma imagem do ecrã. Também impede que a aplicação classroom observe ecrãs remotos. **Não configurado** (predefinido) permite que os utilizadores capturem imagens e permite que a aplicação classroom veja ecrãs remotos.

### <a name="settings-apply-to-automated-device-enrollment"></a>Definições aplicam-se a: Inscrição automática de dispositivos

- **Observação de ecrã remoto através**da aplicação Classroom : **Disable** impede os professores de usar a app Classroom para ver os ecrãs dos seus alunos. **Não configurado** (padrão) permite que os professores vejam os ecrãs dos seus alunos.

  Para utilizar esta definição, defina a definição **de Screenshots** para **Não configurada** (são permitidas imagens).

- **Observação não solicitada por app classroom**: Permitir **que** os professores vejam os ecrãs dos seus alunos sem exigir que o aluno concorde. **Não configurado** (padrão) requer que o aluno concorde antes que o professor possa ver os ecrãs.

  Para utilizar esta definição, defina a definição **de Screenshots** para **Não configurada** (são permitidas imagens).

- **Os alunos devem pedir autorização para deixar a aula**de aula : **Exigir** que os alunos matriculados num curso de sala de aula não gerido saiam do curso de sala de aula para obter a aprovação dos professores para abandonar o curso. **Não configurado** (padrão) permite que o aluno saia do curso sempre que o aluno quiser.

- **Os professores podem bloquear automaticamente dispositivos ou aplicações na aplicação Classroom**: **Permitir** que os professores bloqueiem o dispositivo ou app de um aluno sem a aprovação do aluno. **Não configurado** (padrão) requer que o aluno concorde antes que o professor possa bloquear o dispositivo ou a aplicação.

- **Os alunos podem automaticamente aderir à aula**de aula : **Permitir** permite que os alunos entrem numa aula sem pedir ao professor. **Não configurado** (padrão) requer aprovação do professor para aderir a uma aula.

## <a name="password"></a>Palavra-passe

### <a name="settings-apply-to-device-enrollment-and-automated-device-enrollment"></a>Definições aplicam-se a: Inscrição do dispositivo e inscrição automática de dispositivos

- **Palavra-passe**: **Exija** que o utilizador final introduza uma senha para aceder ao dispositivo. **Não configurado** (predefinido) não requer uma palavra-passe. Também não força quaisquer restrições, tais como bloquear senhas simples ou definir um comprimento mínimo.
  - Tipo de **palavra-passe exigido**: Especifique se a palavra-passe pode ser apenas numérica, ou se deve ser Alfanumérica (conter letras e números).

    Esta funcionalidade aplica-se a:  
    - macOS 10.10.3 e mais recente

  - **Número de caracteres não alfanuméricos na palavra-passe:** Especifique o número de caracteres complexos exigidos na palavra-passe **(0** a **4**).<br>Um caráter complexo é um símbolo, por exemplo " **?** ".
  - Comprimento mínimo da **palavra-passe**: Introduza o comprimento mínimo da palavra-passe que um utilizador deve configurar (entre **4** e **16** caracteres).
  - **Palavras-passe simples**: Permitir a utilização de senhas simples como **0000** ou **1234**.
  - **Minutos máximos após**o bloqueio do ecrã antes da necessidade de senha : Especifique quanto tempo o computador deve estar inativo antes de ser necessária uma palavra-passe para desbloqueá-lo.
  - **Minutos máximos de inatividade até que o ecrã bloqueie**: Especifique o tempo de tempo que o computador deve estar inativo antes do bloqueio do ecrã.
  - **Expiração da palavra-passe (dias)** : Especifique quantos dias decorridos antes de o utilizador alterar a palavra-passe **(1** a **255** dias).
  - **Evite a reutilização de senhas anteriores**: Introduza o número de senhas anteriormente utilizadas que não podem ser reutilizadas, de **1** a **24**.

- **Bloqueie o utilizador de modificar a senha**: Escolha o **bloco** para impedir que a senha seja alterada, adicionada ou removida. **Não configurado** (predefinição) permite que os códigos de acesso sejam adicionados, alterados ou removidos.
- **Bloqueio de impressões digitais**: Escolha **o bloco** para evitar a utilização de uma impressão digital para desbloquear o dispositivo. **Não configurado** (predefinição) permite ao utilizador desbloquear o dispositivo através de uma impressão digital.

- **Bloquear palavra-passe AutoFill**: Escolha **o bloco** para evitar a utilização da função de palavras-passe automáticas no macOS. A escolha de **Bloquear** também tem o seguinte impacto:

  - Não é pedido aos utilizadores que utilizem uma palavra-passe guardada no Safari nem noutras aplicações.
  - As Palavras-passe Seguras automáticas estão desativadas, pelo que não são sugeridas aos utilizadores.

  **Não configurado** (predefinição) permite estas funcionalidades.

- Bloqueie pedidos de proximidade de **palavras-passe**: Escolha **o Bloco** para que o dispositivo do utilizador não solicite senhas de dispositivos próximos. **Não configurado** (predefinição) permite estes pedidos de palavras-passe.

- **Partilha de palavras-passe**bloqueada : **O bloco** impede a partilha de palavras-passe entre dispositivos que utilizam o AirDrop. **Não configurado** (predefinição) permite que as palavras-passe sejam partilhadas.

## <a name="built-in-apps"></a>Aplicações Incorporadas

### <a name="settings-apply-to-device-enrollment-and-automated-device-enrollment"></a>Definições aplicam-se a: Inscrição do dispositivo e inscrição automática de dispositivos

- **Block Safari AutoFill**: **Bloquear** desativa a função de enchimento automático no Safari no dispositivo. **Não configurado** (predefinição) permite que os utilizadores alterem as definições de preenchimento automático no browser.
- **Câmara de bloqueio**: Escolha o **bloco** para impedir o acesso à câmara no dispositivo. **Não configurado** (predefinição) permite o acesso à câmara do dispositivo.
- **Block Apple Music**: **Block** reverte a aplicação Music para o modo clássico e desativa o serviço Music. **Não configurado** (predefinição) permite a utilização da aplicação Apple Music.
- **Bloquear resultados**de pesquisa na Internet : **Bloquear** impede o Spotlight de devolver quaisquer resultados de uma pesquisa na Internet. **Não configurado** (predefinição) permite que o Spotlight se ligue à Internet para fornecer resultados da pesquisa.
- **Transferência de ficheiros de bloco utilizando o iTunes**: **Bloquear** desativa serviços de partilha de ficheiros de aplicações. **Não configurado** (predefinição) permite que os serviços partilhem ficheiros da aplicação.

  Esta funcionalidade aplica-se a:  
  - macOS 10.13 e mais recente

## <a name="restricted-apps"></a>Aplicações restritas

### <a name="settings-apply-to-device-enrollment-and-automated-device-enrollment"></a>Definições aplicam-se a: Inscrição do dispositivo e inscrição automática de dispositivos

- **Tipo de lista de aplicações restritas**: Criar uma lista de aplicações que os utilizadores não estão autorizados a instalar ou usar. As opções são:

  - **Não configurado** (predefinido): Não existem restrições de Intune. Os utilizadores têm acesso a apps que atribui e aplicações incorporadas.
  - **Aplicações proibidas**: Apps não geridas pela Intune que não deseja instaladas no dispositivo. Os utilizadores não estão impedidos de instalar uma aplicação proibida. Mas se um utilizador instalar uma aplicação a partir desta lista, é reportado no Intune.
  - **Aplicações aprovadas**: Apps que os utilizadores estão autorizados a instalar. Os utilizadores não podem instalar aplicações que não estejam listadas. As aplicações geridas pelo Intune são automaticamente permitidas. Os utilizadores não são impedidos de instalar uma aplicação que não esteja na lista aprovada. Mas se o fizerem, é relatado em Intune.
- Id do **pacote de aplicativos**: Introduza o pacote de aplicações [ID](bundle-ids-built-in-ios-apps.md) da app que deseja. Você pode mostrar ou esconder aplicativos incorporados e aplicativos de linha de negócio. O site da Apple tem uma lista de [aplicações incorporadas](https://support.apple.com/HT208094)da Apple.
- Nome da **aplicação**: Introduza o nome da aplicação que deseja. Você pode mostrar ou esconder aplicativos incorporados e aplicativos de linha de negócio. O site da Apple tem uma lista de [aplicações incorporadas](https://support.apple.com/HT208094)da Apple.
- **Editor**: Insira o editor da app que deseja.

Para adicionar aplicações a estas listas, pode:

- **Adicionar**: Selecione para criar a sua lista de aplicações.
- **Importe** um ficheiro CSV com detalhes sobre a aplicação, incluindo o URL. Utilize o formato `<app bundle ID>, <app name>, <app publisher>`. Ou, **Exportar** para criar uma lista de aplicações que adicionou, no mesmo formato.

## <a name="connected-devices"></a>Dispositivos ligados

### <a name="settings-apply-to-device-enrollment-and-automated-device-enrollment"></a>Definições aplicam-se a: Inscrição do dispositivo e inscrição automática de dispositivos

- **Block AirDrop**: **Bloco** evita a utilização do AirDrop no dispositivo. **Não configurado** (predefinição) permite utilizar a funcionalidade AirDrop para trocar conteúdo com os dispositivos próximos.
- **Bloqueio Apple Watch Auto Unlock**: O **bloco** impede os utilizadores de desbloquearem o seu dispositivo macOS com o apple Watch. **Não configurado** (predefinição) permite aos utilizadores desbloquear o dispositivo macOS com o Apple Watch.

## <a name="cloud-and-storage"></a>Cloud e armazenamento

### <a name="settings-apply-to-device-enrollment-and-automated-device-enrollment"></a>Definições aplicam-se a: Inscrição do dispositivo e inscrição automática de dispositivos

- Bloqueie a **sincronização do keychain iCloud:** Escolha o **Bloco** para desativar as credenciais de sincronização armazenadas no Keychain para o iCloud. **Não configurado** (predefinição) permite aos utilizadores sincronizar estas credenciais.
- **Bloquear o iCloud Document Sync**: **O bloco** impede o iCloud de sincronizar documentos e dados. **Não configurado** (predefinição) permite a sincronização de documentos e pares chave-valor com o espaço de armazenamento do iCloud.
- **Block iCloud Mail Backup**: **O bloco** impede que o iCloud se sincronize com a aplicação macOS Mail. **Não configurado** (predefinição) permite a sincronização do Correio com o iCloud.
- **Block iCloud Contact Backup**: **O bloco** impede o iCloud de sincronizar os contactos dos dispositivos. **Não configurado** (predefinição) permite a sincronização de contactos através do iCloud.
- **Block iCloud Calendar Backup**: **O bloco** impede que o iCloud se sincronize com a aplicação do calendário macOS. **Não configurado** (predefinição) permite a sincronização do Calendário com o iCloud.
- **Block iCloud Reminder Backup**: **O bloco** impede que o iCloud se sincronize com a aplicação de lembretes macOS. **Não configurado** (predefinição) permite a sincronização dos Lembretes com o iCloud.
- **Block iCloud Bookmark Backup**: **O bloco** impede o iCloud de sincronizar os marcadores dos dispositivos. **Não configurado** (predefinição) permite a sincronização de Marcadores com o iCloud.
- **Block iCloud Notes Backup**: **Bloco** impede o iCloud de sincronizar os dispositivos Notas. **Não configurado** (predefinição) permite a sincronização das Notas com o iCloud.
- **Bloqueie a biblioteca de fotos do iCloud**: **O bloco** desativa a biblioteca de fotos do iCloud e impede o iCloud de sincronizar as fotos dos dispositivos. Quaisquer fotos não totalmente descarregadas do iCloud Photo Library são removidas do armazenamento local do dispositivo. **Não configurado** (predefinido) permite sincronizar fotografias entre o dispositivo e a biblioteca de fotos iCloud.
- **Entrega**: **Não configurado** (predefinido) permite que os utilizadores comecem a trabalhar num dispositivo macOS e, em seguida, continuem o trabalho que iniciaram noutro dispositivo iOS/iPadOS ou macOS. **O bloco** impede a função de handoff no dispositivo. 

  Esta funcionalidade aplica-se a:  
  - macOS 10.15 e mais recente

## <a name="domains"></a>Domínios

### <a name="settings-apply-to-device-enrollment-and-automated-device-enrollment"></a>Definições aplicam-se a: Inscrição do dispositivo e inscrição automática de dispositivos

- URL de domínio de **e-mail**: **Adicione** um ou mais URLs na lista. Quando os utilizadores recebem um e-mail de um domínio diferente daquele configurado, o e-mail é marcado como não confiável na aplicação macOS Mail.

## <a name="next-steps"></a>Próximos passos

[Atribua o perfil](../device-profile-assign.md) e [monitorize o respetivo estado](../device-profile-monitor.md).

Também pode restringir as funcionalidades e definições do dispositivo nos dispositivos [iOS/iPadOS.](../device-restrictions-ios.md)
