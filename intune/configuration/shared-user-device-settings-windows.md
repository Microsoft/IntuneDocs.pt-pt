---
title: Configurações de dispositivo compartilhado do Windows 10-Microsoft Intune-Azure | Microsoft Docs
description: Adicione e use o Windows 10 para configurar dispositivos que são compartilhados ou usados por vários usuários no Microsoft Intune. Veja uma lista de todas as configurações e o que elas fazem nos dispositivos, incluindo o Microsoft Surface. Controle contas de convidado, gerencie contas e exclua contas inativas, permita ou Evite salvar no armazenamento local, defina opções de energia e suspensão, escolha quando as atualizações são instaladas e use dispositivos em ambientes de educação em um perfil de configuração de dispositivo.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/01/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0e59a4ba7a929df448eddaf36038c2d6deaa0a7a
ms.sourcegitcommit: 23e9c48348a6eba494d072a2665b7481e5b5c84e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/26/2019
ms.locfileid: "74547925"
---
# <a name="windows-10-and-later-settings-to-manage-shared-devices-using-intune"></a>Configurações do Windows 10 e posteriores para gerenciar dispositivos compartilhados usando o Intune

Os dispositivos Windows 10 e posteriores, como o Microsoft Surface, podem ser usados por muitos usuários. Os dispositivos que têm vários usuários são chamados de dispositivos compartilhados e fazem parte das soluções de MDM (gerenciamento de dispositivo móvel).

Usando Microsoft Intune, os usuários finais podem entrar nesses dispositivos compartilhados com uma conta de convidado. À medida que usam o dispositivo, eles só obtêm acesso aos recursos permitidos. Como administrador do Intune, você configura o acesso, escolhe quando as contas são excluídas, controla as configurações de gerenciamento de energia e muito mais para seus dispositivos Windows 10 compartilhados.

Este artigo lista e descreve as configurações usadas em um perfil de configuração de dispositivo do Windows 10 (e posterior). Quando o perfil é criado no Intune, você implanta ou atribui o perfil aos grupos de dispositivos em sua organização. Você também pode atribuir esse perfil a grupos de dispositivos com tipos de dispositivos mistos e versões de sistema operacional.

Para obter mais informações sobre esse recurso no Intune, consulte [controlar o acesso, contas e recursos de energia no PC compartilhado ou em dispositivos de vários usuários](shared-user-device-settings.md). Para obter mais informações sobre o CSP do Windows, consulte [SHAREDPC CSP](https://docs.microsoft.com/windows/client-management/mdm/sharedpc-csp).

## <a name="before-your-begin"></a>Antes de começar

[Crie o perfil](shared-user-device-settings.md).

## <a name="shared-multi-user-device-settings"></a>Configurações de dispositivo de vários usuários compartilhado

- **Modo de PC compartilhado**: escolha **habilitar** para ativar o modo de PC compartilhado. Nesse modo, apenas um usuário entra no dispositivo por vez. Outro usuário não pode entrar até o primeiro usuário sair. **Não configurado** (padrão) deixa essa configuração não gerenciada pelo Intune e não envia nenhuma política para controlar essa configuração em um dispositivo.
- **Conta de convidado**: escolha criar uma opção de convidado na tela de entrada. As contas de convidado não exigem nenhuma credencial ou autenticação de usuário. Essa configuração cria uma nova conta local cada vez que é usada. As opções são:
  - **Convidado**: cria uma conta de convidado localmente no dispositivo.
  - **Domínio**: cria uma conta de convidado no Azure Active Directory (AD).
  - **Convidado e domínio**: cria uma conta de convidado localmente no dispositivo e no Azure Active Directory (AD).
- **Gerenciamento de conta**: Defina como **habilitar** para excluir automaticamente as contas locais criadas por convidados e contas no AD e no Azure AD. Quando um usuário desconecta o dispositivo ou quando a manutenção do sistema é executada, essas contas são excluídas. Quando habilitado, também defina:
  - **Exclusão de conta**: escolha quando as contas são excluídas: **no limite de espaço de armazenamento**, no limite de espaço de **armazenamento e no limite inativo**, ou **imediatamente após**o logout. Insira também:
    - **Iniciar exclusão limite (%)** : Insira um percentual (0-100) de espaço em disco. Quando o espaço total de disco/armazenamento cai abaixo do valor inserido, as contas armazenadas em cache são excluídas. Ele exclui continuamente as contas para recuperar o espaço em disco. As contas que estão inativas mais longas são excluídas primeiro.
    - **Parar exclusão limite (%)** : Insira um percentual (0-100) de espaço em disco. Quando o espaço total de disco/armazenamento atende ao valor inserido, a exclusão é interrompida.

  Defina como **desabilitar** para manter as contas local, AD e Azure ad criadas por convidados.

- **Armazenamento local**: escolha **habilitado** para impedir que os usuários salvem e exibam arquivos no disco rígido do dispositivo. Escolha **desabilitado** para permitir que os usuários vejam e salvem arquivos localmente usando o explorador de arquivos. **Não configurado** (padrão) deixa essa configuração não gerenciada pelo Intune e não envia nenhuma política para controlar essa configuração em um dispositivo.
- **Políticas de energia**: quando definido como **habilitado**, os usuários não podem desativar a hibernação, não podem substituir todas as ações de suspensão (como fechar a tampa) e não podem alterar as configurações de energia. Quando definido como **desabilitado**, os usuários podem hibernar o dispositivo, pode fechar a tampa para suspender o dispositivo e alterar as configurações de energia. **Não configurado** (padrão) deixa essa configuração não gerenciada pelo Intune e não envia nenhuma política para controlar essa configuração em um dispositivo.
- **Tempo limite de suspensão (em segundos)** : Insira o número de segundos inativos (0-100) antes de o dispositivo entrar no modo de suspensão. Se você não definir uma hora, o dispositivo vai para o estado de suspensão após 60 minutos.
- **Entrar quando o PC é ativado**: Defina como **habilitado** para exigir que os usuários entrem com uma senha quando o dispositivo sair do modo de suspensão. Escolha **desabilitado** para que os usuários não precisem inserir seu nome de usuário e senha. **Não configurado** (padrão) deixa essa configuração não gerenciada pelo Intune e não envia nenhuma política para controlar essa configuração em um dispositivo.
- **Hora de início da manutenção (em minutos da meia-noite)** : Insira o tempo em minutos (0-1440) quando as tarefas de manutenção automáticas, como Windows Update, são executadas. A hora de início padrão é meia-noite ou zero (`0`) minutos. Altere a hora de início inserindo uma hora de início em minutos da meia-noite. Por exemplo, se você quiser que a manutenção comece às 2h, insira `120`. Se você quiser que a manutenção comece às 20h, digite `1200`.
- **Políticas de educação**: escolha **habilitado** para usar as configurações recomendadas para dispositivos usados em escolas, que são mais restritivas. Escolha **desabilitado** para que as políticas de educação padrão e recomendadas não sejam usadas. **Não configurado** (padrão) deixa essa configuração não gerenciada pelo Intune e não envia nenhuma política para controlar essa configuração em um dispositivo.

  Para obter mais informações sobre o que as políticas de educação fazem, consulte [recomendações de configuração do Windows 10 para clientes educacionais](https://docs.microsoft.com/education/windows/configure-windows-for-education).

> [!TIP]
> [Configurar um PC compartilhado ou convidado](https://docs.microsoft.com/windows/configuration/set-up-shared-or-guest-pc) (abre outro site de documentos) é um excelente recurso nesse recurso do Windows 10, incluindo conceitos e políticas de grupo que podem ser definidos no modo compartilhado.

## <a name="next-steps"></a>Próximos passos

- [Atribua o perfil](device-profile-assign.md) e [monitorize o respetivo estado](device-profile-monitor.md).
- Consulte as configurações do [Windows Holographic for Business](shared-user-device-settings-windows-holographic.md).
