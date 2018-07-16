---
title: Definições de quiosque do Android no Microsoft Intune – Azure | Microsoft Docs
description: Configure dispositivos de quiosque do Android Enterprise.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 7/5/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 28eca6fa3738519602ee5b2a778bc75bde487156
ms.sourcegitcommit: 98b444468df3fb2a6e8977ce5eb9d238610d4398
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/07/2018
ms.locfileid: "37909104"
---
# <a name="android-enterprise-kiosk-settings-in-intune"></a>Definições de quiosque do Android Enterprise no Intune

Os perfis de quiosque do Android suportam as seguintes definições de configuração. Ao criar um perfil, estas definições são apresentadas quando seleciona **Tipo de perfil** > **Proprietário do Dispositivo Apenas** > **Restrições do dispositivo**. Para ver estas definições, selecione **Propriedades** a partir de um perfil de restrição de dispositivos Android Enterprise e, em seguida, selecione **Configurar**.

## <a name="general-settings"></a>Definições gerais

- **Captura de ecrã**: selecione **Bloquear** para impedir que os utilizadores capturem o ecrã do dispositivo.
- **Câmara**: selecione **Bloquear** para desativar a câmara do dispositivo.
- **Política de permissões predefinida**: esta definição configura a política de permissões predefinida para pedidos de permissões de runtime. Os valores possíveis incluem:
    - **Predefinição do dispositivo**: utiliza a predefinição do dispositivo.
    - **Pedir**: é pedido ao utilizador que aprove a permissão.
    - **Conceder automaticamente**: as permissões são concedidas automaticamente.
    - **Negar automaticamente**: as permissões são negadas automaticamente.
- **Alterações de volume**: selecione **Bloquear** para impedir que os utilizadores alterem o volume do dispositivo.
- **Reposição de dados de fábrica**: selecione **Bloquear** para impedir que os utilizadores efetuem uma reposição de fábrica do dispositivo.
- **Arranque seguro**: selecione **Bloquear** para impedir que os utilizadores reiniciem o dispositivo em modo de segurança.
- **Barra de estado**: selecione **Bloquear** para impedir que os utilizadores acedam à barra de estado, incluindo definições rápidas e notificações.
- **Alterações à definição de Wi-Fi**: selecione **Bloquear** para impedir que os utilizadores alterem as configurações de Wi-Fi criadas pelo proprietário do dispositivo. Os utilizadores podem criar as suas próprias configurações de Wi-Fi.
- **Configuração do ponto de acesso Wi-Fi**: selecione **Bloquear** para impedir que os utilizadores criem ou editem configurações de Wi-Fi.
- **Funcionalidades de depuração**: selecione **Permitir** para permitir que os utilizadores utilizem funcionalidades de depuração.
- **Ajuste do microfone**: selecione **Bloquear** para impedir que os utilizadores ajustem o volume ou desativem o som do microfone.
- **E-mails da proteção da reposição de fábrica**: selecione **Endereços de e-mail da conta Google** para definir endereços de e-mail (separados por ponto e vírgula) que podem desbloquear o dispositivo após uma reposição de fábrica. Se não for especificado um e-mail, qualquer pessoa pode desbloquear o dispositivo após uma reposição de fábrica.
- **Saída de emergência da rede**: selecione **Ativar** para permitir a ativação da funcionalidade de saída de emergência da rede. Se não conseguir estabelecer uma ligação de rede no momento do arranque, a saída de emergência pedirá ao utilizador que se ligue temporariamente a uma rede para poder atualizar a política do dispositivo. Depois da aplicação da política, a rede temporária é esquecida e o dispositivo continua o arranque. Isto evita que não seja possível ligar a uma rede caso não exista uma rede adequada na última política e o dispositivo arranque para uma aplicação no modo de bloqueio de tarefa, ou que o utilizador não consiga aceder às definições do dispositivo.
- **Permitir a instalação a partir de origens desconhecidas**: selecione **Permitir** para permitir que os utilizadores instalem a partir de origens desconhecidas.
- **Atualização do sistema**: selecione uma opção para definir a forma como o dispositivo processa atualizações por ondas eletromagnéticas:
    - **Predefinição do Dispositivo**: utiliza a predefinição do dispositivo.
    - **Automático**: as atualizações são instaladas automaticamente.
    - **Adiado**: as atualizações são adiadas até uma data posterior.
    - **Janela de manutenção**: é pedido aos utilizadores através de uma janela de manutenção que aprovem a atualização.

## <a name="kiosk-settings"></a>Definições de quiosque

- **Modo de quiosque**: define se o dispositivo só pode executar uma aplicação ou múltiplas aplicações. Para obter mais informações, veja [Kiosk settings for Android devices](android-kiosk-settings.md) (Definições de quiosque para dispositivos Android).
    - **Quiosque de uma aplicação**: os utilizadores só podem aceder a uma aplicação.
    - **Quiosque de várias aplicações**: os utilizadores podem aceder a um conjunto limitado de aplicações.

## <a name="device-password-settings"></a>Definições de palavra-passe do dispositivo

- **Keyguard**: selecione **Desativar** para impedir que os utilizadores utilizem o Keyguard no dispositivo.
- **Tipo de palavra-passe necessária**: define o tipo de palavra-passe necessária para o dispositivo.
- **Comprimento mínimo da palavra-passe**: define o comprimento mínimo da palavra-passe necessário para o dispositivo.
- **Número de falhas de início de sessão antes de limpar o dispositivo**: define o número de falhas de início de sessão que têm de ocorrer antes de o dispositivo ser limpo.

## <a name="power-settings"></a>Definições de energia

- **Tempo para bloquear ecrã**: define o período de tempo de inatividade necessário antes de o dispositivo ser bloqueado.
- **Ecrã ligado enquanto o dispositivo está ligado**: selecione que fontes de energia fazem com que o ecrã do dispositivo permaneça ligado enquanto o dispositivo está ligado.

## <a name="users-and-accounts-settings"></a>Definições de utilizadores e contas

- **Adicionar novos utilizadores**: selecione **Bloquear** para impedir que os utilizadores adicionem novos utilizadores.
- **Remoção do utilizador**: selecione **Bloquear** para impedir que os utilizadores removam utilizadores.
- **Alterações à conta**: selecione **Bloquear** para impedir que os utilizadores modifiquem as contas.

## <a name="next-steps"></a>Próximos passos
[Atribua o perfil](device-profile-assign.md) e [monitorize o respetivo estado](device-profile-monitor.md).



