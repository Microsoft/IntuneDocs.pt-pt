---
title: Configure iOS software update policies in Microsoft Intune (Configurar as políticas de atualização de software iOS no Microsoft Intune) – Azure | Microsoft Docs
description: Crie ou adicione uma política de configuração no Microsoft Intune para restringir a instalação automática de atualizações de software em dispositivos iOS geridos ou supervisionados pelo Intune. Pode selecionar as datas e as horas em que as atualizações não serão instaladas. Também pode atribuir esta política a grupos, utilizadores ou dispositivos e verificar a existência de falhas de instalação.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/24/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.openlocfilehash: 1fe0258d3b6d9092c032184fca5fc0f8dc3f12df
ms.sourcegitcommit: 4d314df59747800169090b3a870ffbacfab1f5ed
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/30/2018
ms.locfileid: "43313501"
---
# <a name="configure-ios-update-policies-in-intune"></a>Configurar as políticas de atualização de iOS no Microsoft Intune

As políticas de atualização de software permitem-lhe forçar os dispositivos iOS supervisionados a instalarem automaticamente as atualizações de SO disponíveis mais recentes. Esta funcionalidade só está disponível para dispositivos supervisionados. Ao configurar uma política, pode adicionar os dias e as horas em que não quer que os dispositivos instalem uma atualização. 

O dispositivo comunica com o Intune aproximadamente de 8 em 8 horas. Se uma atualização estiver disponível num período de tempo não restringido, o dispositivo irá transferir e instalar a atualização de SO mais recente. Não é necessária nenhuma interação do utilizador para atualizar o dispositivo. A política não impede um utilizador de atualizar manualmente o SO.

Esta funcionalidade suporta dispositivos com o iOS 10.3 ou posterior.

## <a name="configure-the-policy"></a>Configurar a política
1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços**, filtre por **Intune** e selecione **Microsoft Intune**.
3. Selecione **Atualizações de Software** > **Atualizar políticas para iOS** > **Criar**.
4. Introduza um nome e uma descrição para a política.
5. Selecione **Definições**. 

    Introduza os detalhes para quando os dispositivos iOS não são forçados a instalar as atualizações mais recentes. Estas definições criam um período de tempo restrito. Pode configurar os **Dias** da semana, o **Fuso horário**, a **Hora de início** e a **Hora de fim**, bem como se quer ou não ativar a **Visibilidade de atraso das atualizações de software (dias)** para introduzir utilizadores. Pode selecionar um intervalo de atraso de atualizações de software entre 1 e 90 dias. Para optar ativamente por não definir um atraso de atualizações de software, introduza 0. Estas definições de atualizações só se aplicarão a dispositivos iOS supervisionados.

6. Selecione **OK** para guardar as alterações. Selecione **Criar** para criar a política.

O perfil é criado e apresentado na lista de políticas. A MDM da Apple não lhe permite forçar um dispositivo a instalar atualizações numa determinada hora ou data. 

## <a name="change-the-restricted-times-for-the-policy"></a>Alterar as horas restritas da política

1. Em **Atualizações de Software**, selecione **Atualizar políticas para iOS**.
2. Selecione uma política existente > **Propriedades**.
3. Atualize a hora restrita:

    1. Selecione os dias da semana
    2. Selecione o fuso horário em que esta política é aplicada
    3. Introduza a hora de início e a hora de fim das horas bloqueadas

    > [!NOTE]
    > Se a **Hora de início** e a **Hora de fim** estiverem ambas definidas para as 00:00, a verificação da hora de manutenção será desativada.

## <a name="assign-the-policy-to-users"></a>Atribuir uma política de atualização de iOS a utilizadores

As políticas existentes são atribuídas a grupos, utilizadores ou dispositivos. A política é aplicada quando é atribuída.

1. Em **Atualizações de Software**, selecione **Atualizar políticas para iOS**.
2. Selecione uma política existente > **Atribuições**. 
3. Selecione os grupos, utilizadores ou dispositivos do Azure Active Directory a excluir ou incluir nesta política.
4. Selecione **Guardar** para implementar a política aos seus grupos.

Os dispositivos utilizados pelos utilizadores abrangidos pela política são avaliados quanto à conformidade das atualizações. Esta política também suporta dispositivos sem utilizador.

## <a name="monitor-device-installation-failures"></a>Monitorizar as falhas de instalação em dispositivos
A opção <!-- 1352223 -->
**Atualizações de Software** > **Falhas de instalação para dispositivos iOS** mostra uma lista de dispositivos iOS abrangidos por uma política de atualização que tentaram efetuar uma atualização sem êxito. Pode ver o estado com o motivo pelo qual cada um dos dispositivos não foi atualizado automaticamente. Os dispositivos atualizados e em bom estado de funcionamento não são apresentados na lista. Os dispositivos atualizados incluem as atualizações mais recentes suportadas pelos mesmos.

