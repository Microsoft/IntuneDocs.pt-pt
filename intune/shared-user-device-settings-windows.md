---
title: Windows 10 partilhado definições do dispositivo – Microsoft Intune – Azure | Documentos da Microsoft
description: Adicionar e utilizar o Windows 10 para configurar os dispositivos que são partilhados ou utilizados por vários utilizadores no Microsoft Intune. Ver uma lista de todas as definições e o que fazer em dispositivos, incluindo o Microsoft Surface. Controlar as contas de convidado, gerir contas e eliminar contas inativas, permitir ou impedir guardar para o armazenamento local, definir power e opções de estado de suspensão, escolher quando as atualizações são instaladas e utilizam dispositivos em ambientes de educação num perfil de configuração do dispositivo.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/01/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 535f66c68b066454ce9706b1dd1d7a4fce5c265c
ms.sourcegitcommit: e63e3debb5f4d9a757f767913e72e39742137b17
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/01/2019
ms.locfileid: "58788492"
---
# <a name="windows-10-and-later-settings-to-manage-shared-devices-using-intune"></a>Definições Windows 10 e posteriores para gerir dispositivos partilhados, através do Intune

Windows 10 e dispositivos posteriores, como o Microsoft Surface, podem ser utilizados por vários utilizadores. Dispositivos que têm vários utilizadores são chamados dispositivos partilhados e são uma parte da gestão de dispositivos móveis soluções (MDM).

Utilizar o Microsoft Intune, os utilizadores finais podem iniciar sessão para esses dispositivos partilhados com uma conta de convidado. Que usam o dispositivo, eles apenas obtém acesso às funcionalidades que permite. Como o administrador do Intune, configurar o acesso, escolha quando as contas são eliminadas, definições de gestão de energia de controle e muito mais para os seus dispositivos Windows 10 partilhados.

Este artigo apresenta e descreve as definições que utilizar num perfil de configuração de dispositivos de 10 (e posterior) do Windows. Quando o perfil é criado no Intune, implementar ou atribuir o perfil a grupos de dispositivos na sua organização. Também pode atribuir este perfil a grupos de dispositivos com tipos de dispositivo misto e versões de SO.

Para obter mais informações sobre esta funcionalidade no Intune, consulte [controlar o acesso, contas e recursos de energia no PC partilhado ou dispositivos de vários utilizadores](shared-user-device-settings.md). Para obter mais informações sobre o CSP do Windows, consulte [SharedPC CSP](https://docs.microsoft.com/windows/client-management/mdm/sharedpc-csp).

## <a name="before-your-begin"></a>Antes de sua begin

[Criar o perfil](shared-user-device-settings.md).

## <a name="shared-multi-user-device-settings"></a>Definições de utilizador multi dispositivos partilhados

- **Modo de PC partilhado**: Escolher **ativar** para ativar o modo de PC compartilhado. Neste modo, apenas um utilizador inicia sessão no dispositivo por vez. Outro utilizador não pode iniciar sessão até que o primeiro utilizador encerrar a sessão. **Não configurado** deixa esta definição não geridos pelo Intune (predefinição) e não instalar quaisquer políticas para controlar esta definição num dispositivo.
- **Conta de convidado**: Opte por criar uma opção de convidado no ecrã de início de sessão. As contas de convidado não necessitam de quaisquer credenciais de utilizador ou a autenticação. Esta definição cria uma nova conta local sempre que é utilizado. As opções são:
  - **Convidado**: Cria uma conta de convidado localmente no dispositivo.
  - **Domínio**: Cria uma conta de convidado no Azure Active Directory (AD).
  - **Convidado e o domínio**: Cria uma conta de convidado localmente no dispositivo e no Azure Active Directory (AD).
- **Gerenciamento de contas**: Defina como **ativar** automaticamente eliminar contas locais criadas pelo convidados e contas no AD e o Azure AD. Quando um utilizador inicia a desativar o dispositivo, ou quando a manutenção do sistema é executada, estas contas são eliminadas. Quando ativada, também defina:
  - **Eliminação da conta**: Escolha quando as contas são eliminadas: **No limite de espaço de armazenamento**, **limiar de espaço de armazenamento e de limiar inativo**, ou **imediatamente após, termine**. Introduza também:
    - **Início eliminar threshold(%)**: Introduza uma percentagem (0 a 100) de espaço em disco. Quando o espaço de armazenamento/disco total cai abaixo do valor introduzido, as contas em cache são eliminadas. Continuamente elimina contas para recuperar espaço em disco. Contas que estão Inativas há mais tempo são eliminadas primeiro.
    - **Parar delete threshold(%)**: Introduza uma percentagem (0 a 100) de espaço em disco. Quando o espaço de disco total/armazenamento cumpre o valor introduzido, a eliminar para.

  Defina como **desativar** para manter o local, AD e contas do Azure AD criadas pelos convidados.

- **Armazenamento local**: Escolher **ativado** para impedir que os utilizadores de guardar e visualizar ficheiros na unidade de disco rígido do dispositivo. Escolher **desativado** para permitir que os utilizadores vejam e guardar ficheiros localmente com o Explorador de ficheiros. **Não configurado** deixa esta definição não geridos pelo Intune (predefinição) e não instalar quaisquer políticas para controlar esta definição num dispositivo.
- **Políticas de energia**: Quando definido como **ativado**, os utilizadores não podem tornar desativar hibernação, não é possível substituir todas as ações de suspensão (por exemplo, fechar a tampa) e não é possível alterar as definições de energia. Quando definido como **desativado**, os utilizadores podem hibernar o dispositivo, pode fechar a tampa no modo de suspensão no dispositivo e alterar as definições de energia. **Não configurado** deixa esta definição não geridos pelo Intune (predefinição) e não instalar quaisquer políticas para controlar esta definição num dispositivo.
- **Tempo limite de suspensão (em segundos)**: Introduza o número de segundos de Inativos (0 a 100) antes do dispositivo entra no modo de suspensão. Se não definir um período de tempo, o dispositivo entra em suspensão após 60 minutos.
- **Início de sessão quando sair do PC**: Defina como **ativado** para exigir aos utilizadores iniciar sessão com uma palavra-passe quando o dispositivo estiver fora do modo de suspensão. Escolher **desativado** para que os utilizadores não têm de introduzir o respetivo nome de utilizador e palavra-passe. **Não configurado** deixa esta definição não geridos pelo Intune (predefinição) e não instalar quaisquer políticas para controlar esta definição num dispositivo.
- **Hora (em minutos da meia-noite) de início de manutenção**: Introduza o tempo em minutos (0-1440) quando tarefas de manutenção automática, como a atualização do Windows, executam. A hora de início padrão é meia-noite, ou zero (`0`) minutos. Altere a hora de início ao introduzir uma hora de início em minutos a partir de meia-noite. Por exemplo, se pretender que a manutenção com início às 2 AM, introduza `120`. Se pretender que a manutenção para começar às 20:00, introduza `1200`.
- **Políticas de educação**: Escolher **ativado** para utilizar as definições recomendadas para dispositivos utilizados nas escolas, que são mais restritivas. Escolher **desativado** para que as políticas de educação recomendada e predefinida não são utilizadas. **Não configurado** deixa esta definição não geridos pelo Intune (predefinição) e não instalar quaisquer políticas para controlar esta definição num dispositivo.

  Para obter mais informações sobre o que fazem as políticas de educação, consulte [recomendações de configuração do Windows 10 para os clientes de educação](https://docs.microsoft.com/education/windows/configure-windows-for-education).

> [!TIP]
> [Configurar um PC compartilhado ou convidado](https://docs.microsoft.com/windows/configuration/set-up-shared-or-guest-pc) (abre-se outro web site do docs) é um ótimo recurso sobre esta funcionalidade do Windows 10, incluindo conceitos e as políticas de grupo que podem ser definidas no modo partilhado.

## <a name="next-steps"></a>Passos Seguintes

- [Atribua o perfil](device-profile-assign.md) e [monitorize o respetivo estado](device-profile-monitor.md).
- Ver as definições para [Windows Holographic for Business](shared-user-device-settings-windows-holographic.md).
