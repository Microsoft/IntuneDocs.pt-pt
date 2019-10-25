---
title: Criar política de proteção de aplicativo MTD (defesa contra ameaças móveis) com o Intune
titleSuffix: Microsoft Intune
description: Criar política de proteção de aplicativo MTD (defesa contra ameaças móveis) com Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 15d986bc5017a44571c6194f9c6b53167b671349
ms.sourcegitcommit: 06a1fe83fd95c9773c011690e8520733e1c031e3
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/23/2019
ms.locfileid: "72795311"
---
# <a name="create-mobile-threat-defense-app-protection-policy-with-intune"></a>Criar política de proteção do aplicativo de defesa contra ameaças móveis com o Intune

> [!NOTE] 
> Este artigo se aplica a todos os parceiros de MTD (defesa contra ameaças móveis) que dão suporte a políticas de proteção de aplicativo: melhores dispositivos móveis (Android), Zimperium (iOS), Lookout for Work (Android/iOS).

O Intune com a MTD ajuda-o a detetar ameaças e a avaliar os riscos em dispositivos móveis. Você pode criar uma política de proteção de aplicativo do Intune que avalia o risco para determinar se o dispositivo tem permissão de acesso a dados corporativos ou não. 

## <a name="before-you-begin"></a>Antes de começar

Como parte da configuração da MTD, na consola do parceiro MTD, criou uma política que classifica as várias ameaças como sendo de nível alto, médio e baixo. Agora você precisa definir o nível de defesa contra ameaças móveis na política de proteção de aplicativo do Intune.

Pré-requisitos para a política de proteção de aplicativo com MTD:

- Configure a integração do MTD com o Intune. Sem essa integração, a política de proteção do aplicativo MTD não terá nenhum efeito.

## <a name="to-create-an-mtd-app-protection-policy"></a>Para criar uma política de proteção de aplicativo MTD

1. Aceda ao [portal do Azure](https://portal.azure.com/) e inicie sessão com as credenciais do Intune.

2. No **Dashboard do Azure**, selecione **Todos os serviços**, no menu à esquerda e, em seguida, escreva **Intune** no filtro da caixa de texto.

3. Selecione **Intune** e o **Dashboard do Intune** será aberto.

4. No **painel do Intune**, escolha **aplicativos cliente**e, em seguida, escolha políticas de **proteção de aplicativo** na seção **gerenciar** .

5. Escolha **criar política**, digite o **nome**, a **Descrição**, selecione a **plataforma**. 

6. No painel **inicialização condicional** , na tabela **condições do dispositivo** , escolha o nível de ameaça móvel na lista suspensa no **nível máximo de ameaça do dispositivo permitido**.

    a.  **Seguro**: este é o nível mais seguro. O dispositivo não pode aceder aos recursos da empresa se contiver ameaças. Se forem detetadas ameaças, o dispositivo será avaliado como não conforme.

    b.  **Baixo**: o dispositivo está em conformidade se só estiverem presentes ameaças de nível baixo. Qualquer nível mais alto coloca o dispositivo num estado de não conforme.

    c.  **Médio**: o dispositivo está em conformidade se as ameaças encontradas forem de nível baixo ou médio. Se forem detetadas ameaças de nível alto, o estado do dispositivo será determinado como não conforme.

    d.  **Elevado**: este é o nível menos seguro. Este nível permite que todos os níveis de ameaça estejam presentes e utiliza a Defesa Contra Ameaças para Dispositivos Móveis apenas para a criação de relatórios. É necessário que os dispositivos tenham a aplicação de MTD ativada com esta definição.

7. Clique em **salvar** duas vezes e, em seguida, escolha **criar**.

## <a name="to-assign-an-mtd-app-protection-policy"></a>Para atribuir uma política de proteção de aplicativo MTD

Para atribuir uma política de conformidade de dispositivos a utilizadores, selecione uma política que tenha configurado anteriormente. As políticas existentes encontram-se no painel **Conformidade do dispositivo – políticas**.

1. Escolha a política que quer atribuir aos utilizadores e, em seguida, **Atribuições**. Essa ação abre o painel em que você pode selecionar **Azure Active Directory grupos de segurança** e atribuí-los à política.

2. Escolha **Selecionar grupos a serem incluídos** para abrir o painel que exibe os grupos de segurança do Azure AD. Escolher **selecionar** implanta a política para os usuários.

> [!NOTE] 
> Aplicou a política aos utilizadores. Os dispositivos usados pelos usuários que são alvo da política são avaliados para acesso a dados corporativos em aplicativos de destino por meio da proteção de aplicativo do Intune.

## <a name="next-steps"></a>Próximos passos  

- Saiba mais sobre a [defesa contra ameaças móveis](~/protect/mobile-threat-defense.md) em Microsoft Intune.
