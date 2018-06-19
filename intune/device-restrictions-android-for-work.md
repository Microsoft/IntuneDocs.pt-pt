---
title: Restrições de dispositivos do Android for Work no Microsoft Intune – Azure | Microsoft Docs
description: Em dispositivos a executar o Android for Work, pode restringir algumas definições no dispositivo, incluindo as ações de copiar e colar, mostrar notificações, permissões de aplicações, partilha de dados, comprimento da palavra-passe, falhas de início de sessão, utilização de impressões digitais para desbloquear, reutilização de palavras-passe e permitir a partilha de contactos profissionais por bluetooth.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 4/25/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e1db0e98318c05c7a1a854ed1af77d9d9654cc38
ms.sourcegitcommit: 401cedcd7acc6cb3a6f18d4679bdadb0e0cdf443
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/28/2018
ms.locfileid: "32046320"
---
# <a name="work-device-restriction-settings-in-intune"></a>Definições de restrições de dispositivos profissionais no Intune

Este artigo lista todas as definições de restrições de dispositivos do Microsoft Intune que pode configurar para dispositivos a executar o Android for Work.

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

## <a name="work-profile-settings"></a>Definições de perfil de trabalho

### <a name="general-settings"></a>Definições Gerais

- **Copiar e colar entre perfis pessoais e perfis de trabalho**: controla as ações de copiar e colar entre aplicações pessoais e aplicações de trabalho. Selecione **Bloquear** para ativar o bloqueio. Selecione **Não configurado** para desativar o bloqueio.
- **Partilha de dados entre perfis de trabalho e perfis pessoais**: controla se as aplicações no perfil de trabalho podem partilhar dados com as aplicações no perfil pessoal. Esta definição controla ações de partilha nas aplicações (por exemplo, a opção **Partilha...** na aplicação do browser Chrome) e não se aplica ao comportamento copiar/colar na área de transferência. Ao contrário das [definições de política de proteção de aplicações](https://docs.microsoft.com/intune-classic/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune), as definições de restrição de dispositivos são geridas no portal do Intune e utilizam a partição do perfil Android for Work para isolar as aplicações geridas. Escolha entre:
  - **Restrições de partilha predefinidas**: o comportamento de partilha predefinido do dispositivo, que varia consoante a versão do Android. Por predefinição, é permitida a partilha do perfil pessoal com o perfil de trabalho. Também por predefinição, é bloqueada a partilha do perfil de trabalho para o perfil pessoal. Esta definição impede a partilha de dados do perfil de trabalho para o perfil pessoal. A Google não proporciona uma forma de bloquear a partilha do perfil pessoal para o perfil de trabalho em dispositivos com versões 6.0 e posteriores.
  - **As aplicações no perfil de trabalho podem processar o pedido de partilha do perfil pessoal**: ativa a funcionalidade do Android incorporada que permite a partilha do perfil pessoal para o perfil de trabalho. Quando ativada, um pedido de partilha de uma aplicação no perfil pessoal pode partilhar com aplicações no perfil de trabalho. Esta definição é o comportamento predefinido para dispositivos Android com versões anteriores à 6.0.
  - **Permitir partilha entre limites**: ativa a partilha entre limites do perfil de trabalho em ambas as direções. Quando seleciona esta definição, as aplicações no perfil de trabalho podem partilhar dados com aplicações sem destaque no perfil pessoal. Utilize esta definição com cuidado, uma vez que permite que aplicações geridas no perfil de trabalho sejam partilhadas com aplicações no lado não gerido do dispositivo.

- **Notificações do perfil de trabalho quando o dispositivo está bloqueado**: controla se as aplicações no perfil de trabalho podem apresentar dados em notificações quando o dispositivo está bloqueado.
- **Permissões de aplicações predefinidas**: define a política de permissões predefinida para todas as aplicações do perfil de trabalho. A partir do Android 6, é pedido ao utilizador para conceder determinadas permissões necessárias pelas aplicações quando a aplicação é iniciada. Esta definição de política permite-lhe decidir se é pedido aos utilizadores a concessão de permissões para todas as aplicações no perfil de trabalho. Por exemplo, poderá atribuir uma aplicação ao perfil de trabalho que precisa de acesso de localização. Normalmente, essa aplicação pede ao utilizador para aprovar ou recusar o acesso à localização da aplicação. Esta política permite-lhe decidir se todas as permissões devem ser concedidas automaticamente sem um pedido de confirmação, se devem negadas automaticamente sem um pedido de confirmação ou se deve ser permitido ao utilizador final que decida. Escolha entre:
  - **Predefinição do dispositivo**
  - **Pedido de confirmação**
  - **Conceder automaticamente**
  - **Negar automaticamente**

    O estado de concessão de permissões pode ser definido posteriormente para aplicações específicas, ao utilizar uma política de Configuração de Aplicações para uma aplicação individual (em **Aplicações móveis** > **Políticas de configuração de aplicações**).

- **Adicionar e remover contas**

   Impede os utilizadores de adicionarem ou removerem contas manualmente no perfil de trabalho.

   Por exemplo, ao implementar a aplicação Gmail num perfil do Android For Work, pode impedir os utilizadores finais de adicionarem ou removerem contas neste perfil de trabalho.

- **Partilha de contactos por Bluetooth**: permite aceder aos contactos do trabalho a partir de outro dispositivo, como um automóvel, que esteja emparelhado através de Bluetooth. Por predefinição, esta definição não está configurada e os contactos do perfil de trabalho não são apresentados. Selecione **Ativar** para permitir esta partilha e mostrar os contactos do perfil de trabalho. Esta definição aplica-se a dispositivos de perfil de trabalho do Android em Android OS v6.0 e mais recentes. Deste modo, pode permitir que determinados dispositivos Bluetooth coloquem os contactos de trabalho na cache após a primeira ligação. A desativação desta política após um emparelhamento/sincronização inicial pode não remover os contactos de trabalho dos dispositivos Bluetooth.

- **Captura de ecrã**: bloqueia a captura de ecrã no dispositivo quando está no perfil de trabalho. Também impede que os conteúdos presentes sejam apresentados em dispositivos de visualização que não tenham uma saída de vídeo segura.

- **Apresentar o ID de autor de chamada do contacto de trabalho no perfil pessoal**: quando esta opção está ativada (não configurada), os detalhes de autor de chamada do contacto de trabalho são apresentados no perfil pessoal. Quando a opção está bloqueada, o número do autor da chamada do contacto de trabalho não é apresentado no perfil pessoal. Aplica-se ao Android OS v6.0 e a versões mais recentes.

- **Câmara**: bloqueia a câmara no dispositivo quando está no perfil de trabalho. A câmara na parte pessoal não é afetada por esta definição.

### <a name="work-profile-password"></a>Palavra-passe do perfil de trabalho

- **Exigir Palavra-passe de Perfil de Trabalho**: aplica-se ao Android 7.0 e posterior com o perfil de trabalho ativado. Defina uma política de código de acesso que se aplique às aplicações no perfil de trabalho. Por predefinição, o utilizador final pode utilizar os dois PINs definidos separadamente ou pode optar por combinar os PINs no mais forte dos dois.
- **Comprimento mínimo da palavra-passe**: introduza o número mínimo de carateres que a palavra-passe do utilizador tem de ter (**4**-**16**)
- **Máximo de minutos de inatividade até ao bloqueio do perfil de trabalho**: selecione a quantidade de tempo antes de o perfil de trabalho ser bloqueado. Em seguida, o utilizador tem de introduzir as credenciais para recuperar o acesso.
- **Número de falhas de início de sessão antes de limpar o dispositivo**: introduza o número de vezes que uma palavra-passe incorreta pode ser introduzida antes de o perfil de trabalho do dispositivo ser eliminado.
- **Expiração da palavra-passe (dias)**: introduza o número de dias até ser preciso alterar a palavra-passe do utilizador final (**1**-**255**).
- **Tipo de palavra-passe necessária**: selecione o tipo de palavra-passe que tem de ser definido no dispositivo. Escolha entre:
  - **Predefinição do dispositivo**
  - **Biométrica de segurança baixa**
  - **Necessário**
  - **Pelo menos numérica**
  - **Complexo numérico**: números repetidos ou consecutivos, como "1111" ou "1234", não são permitidos
  - **Pelo menos alfabética**
  - **Pelo menos alfanumérica**
  - **Pelo menos alfanumérica com símbolos**
- **Impedir a reutilização de palavras-passe anteriores**: introduza o número de novas palavras-passe que têm de ser utilizadas antes de poder ser reutilizada uma antiga (**1**-**24**).
- **Desbloqueio por impressão digital**: impede os utilizadores finais de utilizarem a deteção de impressão digital do dispositivo para o desbloquear
- **Smart Lock e outros agentes de fidedignidade**: controla a funcionalidade Smart Lock em dispositivos compatíveis. Esta capacidade de telefone, por vezes conhecida como agente de confiança, permite desativar ou ignorar a palavra-passe do perfil de trabalho se o dispositivo estiver numa localização fidedigna. Por exemplo, quando está ligado a um dispositivo Bluetooth específico ou quando está próximo de uma etiqueta NFC. Utilize esta definição para impedir que os utilizadores configurem o Smart Lock.

## <a name="device-password"></a>Palavra-passe do dispositivo

- **Comprimento mínimo da palavra-passe**: introduza o número mínimo de carateres que a palavra-passe do utilizador tem de ter (**4**-**14**)
- **Máximo de minutos de inatividade até o ecrã ser bloqueado**: selecione a quantidade de tempo antes de um dispositivo inativo ser automaticamente bloqueado
- **Número de falhas de início de sessão antes de limpar o dispositivo**: introduza o número de vezes que uma palavra-passe incorreta pode ser introduzida antes de todos os dados do dispositivo serem eliminados
- **Expiração da palavra-passe (dias)**: introduza o número de dias até ser preciso alterar a palavra-passe do utilizador final (**1**-**255**)
- **Tipo de palavra-passe necessária**: selecione o tipo de palavra-passe que tem de ser definido no dispositivo. Escolha entre:
  - **Predefinição do dispositivo**
  - **Biométrica de segurança baixa**
  - **Necessário**
  - **Pelo menos numérica**
  - **Complexo numérico**: números repetidos ou consecutivos, como "1111" ou "1234", não são permitidos
  - **Pelo menos alfabética**
  - **Pelo menos alfanumérica**
  - **Pelo menos alfanumérica com símbolos**
- **Impedir a reutilização de palavras-passe anteriores**: introduza o número de novas palavras-passe que têm de ser utilizadas antes de poder ser reutilizada uma antiga (**1**-**24**).
- **Desbloqueio por impressão digital**: impede um utilizador final de utilizar a deteção de impressão digital do dispositivo para o desbloquear
- **Smart Lock e outros agentes de fidedignidade**: controla a funcionalidade Smart Lock em dispositivos compatíveis. Esta capacidade de telefone, por vezes conhecida como agente de confiança, permite desativar ou ignorar a palavra-passe de bloqueio do ecrã do dispositivo se o dispositivo estiver numa localização fidedigna. Por exemplo, quando está ligado a um dispositivo Bluetooth específico ou quando está próximo de uma etiqueta NFC. Utilize esta definição para impedir que os utilizadores configurem o Smart Lock.

## <a name="system-security"></a>Segurança do sistema

- **Análise de ameaças em aplicações**: exija que a definição **Verificar Aplicações** esteja ativada para os perfis pessoais e de trabalho.

   > [!Note]
   > Esta definição só funciona para dispositivos Android O e posteriores.

## <a name="next-step"></a>Passo seguinte

Para guardar e atribuir o perfil a utilizadores e dispositivos, veja [Configurar definições de restrições de dispositivos](device-restrictions-configure.md).
