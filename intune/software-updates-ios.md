---
title: Configurar as políticas de atualização de software iOS no Microsoft Intune
titlesuffix: ''
description: Configure políticas de atualização para iOS para forçar os dispositivos iOS supervisionados a instalarem automaticamente as atualizações de software disponíveis mais recentes.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/19/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.openlocfilehash: 1d4223ae4feb417f77909b320cd0295347b44461
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/26/2018
---
# <a name="configure-ios-update-policies-in-microsoft-intune"></a>Configurar as políticas de atualização de iOS no Microsoft Intune

As políticas de atualização de software permitem-lhe forçar os dispositivos com iOS 10.3 ou posterior supervisionados a instalarem automaticamente as atualizações do SO mais recentes disponíveis. Esta funcionalidade só está disponível para dispositivos supervisionados. Pode configurar os dias e as horas em que não pretende que os dispositivos instalem a atualização. 

Quando o dispositivo verifica, a cada 8 horas (aproximadamente), se existe uma atualização disponível e esta ação não ocorrer durante uma hora restrita, o dispositivo tentará transferir e instalar a versão mais recente do SO. Não é necessária nenhuma interação do utilizador para atualizar o dispositivo. A política não impediria um utilizador de atualizar o SO.

## <a name="configure-the-ios-update-policy"></a>Configurar a política de atualização de iOS
1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços** > **Intune**. O Intune encontra-se na secção **Monitorização + Gestão**.
3. No painel **Intune**, selecione **Atualizações de software** > **Políticas de Atualização de iOS**.
4. No painel políticas, selecione **Criar** e, em seguida, introduza um nome e descrição para a política.
5. Selecione **Definições** > **Configurar** e introduza os detalhes para quando os dispositivos iOS não são forçados a instalar a atualização mais recente. Pode configurar os dias da semana, o fuso horário, a hora de início e a hora de fim.
6. Escolha **OK** para guardar esta configuração. Está novamente no painel **Criar política de atualização**. Escolha **Criar** para criar a política e guardar as suas definições.

O perfil é criado e apresentado no painel da lista de políticas de atualização de iOS. A MDM da Apple não permite forçar o dispositivo a instalar a atualização numa determinada hora ou data. 

## <a name="change-the-restricted-times-for-the-policy"></a>Alterar as horas restritas da política

1.  No painel **Atualizações de software**, selecione **Políticas de Atualização de iOS**.
2.  Selecione a política de atualização de iOS que pretende atualizar.
3.  Selecione **Propriedades** e atualize a informação das horas restritas.
4.  Selecione os dias da semana
5.  O fuso horário em que esta política será aplicada
6.  A hora de início e a hora de fim das horas bloqueadas

## <a name="assign-an-ios-update-policy-to-users"></a>Atribuir uma política de atualização de iOS a utilizadores

Para atribuir uma política de atualização de iOS a utilizadores, escolha uma política que tenha configurado. As políticas existentes encontram-se no painel **Atualizações de software** > **Políticas de Atualização de iOS**.

1. Escolha a política que quer atribuir aos utilizadores e, em seguida, **Atribuições**. É aberto o painel onde pode selecionar grupos de segurança do Azure Active Directory e atribuí-los à política.
2. Selecione **Grupos selecionados** para abrir o painel que apresenta os grupos de segurança do Azure AD. Determine quem tem acesso à política ao indicar os grupos a incluir e a excluir.
3. Selecione **Guardar** para implementar a política aos utilizadores.

Aplicou a política aos seus utilizadores ou dispositivos. Os dispositivos utilizados pelos utilizadores visados pela política são avaliados quanto à conformidade das atualizações. Esta política também suporta dispositivos sem utilizador.

## <a name="monitor-ios-device-installation-failures"></a>Monitorizar as falhas de instalação em dispositivos iOS
<!-- 1352223 -->
O relatório **Falhas de Instalação para Dispositivos iOS** está disponível no painel **Atualizações de software**. No relatório, poderá ver uma lista dos dispositivos iOS supervisionados que foram abrangidos por uma política de atualização de iOS e não tiveram êxito ao tentar atualizar. Pode ver o estado com o motivo pelo qual cada um dos dispositivos não foi atualizado automaticamente. Os dispositivos atualizados e em bom estado de funcionamento não serão apresentados na lista. Consideramos atualizado um dispositivo com a atualização mais recente suportada pelo mesmo.

