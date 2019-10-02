---
title: Criar uma política de conformidade de dispositivos MTD com o Microsoft Intune
titleSuffix: Microsoft Intune
description: Crie uma política de conformidade de dispositivo do Intune que utilize os níveis de ameaça de parceiro MTD para determinar se um dispositivo móvel pode aceder a recursos da empresa.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/02/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5d12254f-ffab-4792-b19c-ab37f5e02f35
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2315136fe277f06f6dbb11c13139a9dc193ce6f7
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71729576"
---
# <a name="create-mobile-threat-defense-mtd-device-compliance-policy-with-intune"></a>Criar a política de conformidade de dispositivos da Defesa Contra Ameaças para Dispositivos Móveis (MTD) com o Intune

> [!NOTE] 
> Estas informações aplicam-se a todos os parceiros de Defesa Contra Ameaças para Dispositivos Móveis.

O Intune com a MTD ajuda-o a detetar ameaças e a avaliar os riscos em dispositivos móveis. Pode criar uma regra de política de conformidade de dispositivos do Intune que avalie o risco para determinar se o dispositivo está ou não em conformidade. Você pode usar uma [política de acesso condicional](create-conditional-access-intune.md) para bloquear o acesso a serviços com base na conformidade do dispositivo.

## <a name="before-you-begin"></a>Antes de começar

Como parte da configuração da MTD, na consola do parceiro MTD, criou uma política que classifica as várias ameaças como sendo de nível alto, médio e baixo. Na política de conformidade de dispositivos do Intune, precisa agora de definir o nível de Defesa Contra Ameaças para Dispositivos Móveis.

Pré-requisitos da política de conformidade de dispositivos com a MTD:

- Configurar a integração da MTD com o Intune

## <a name="to-create-an-mtd-device-compliance-policy"></a>Para criar uma política de conformidade MTD do dispositivo

1. Aceda ao [portal do Azure](https://portal.azure.com/) e inicie sessão com as credenciais do Intune.

2. No **Dashboard do Azure**, selecione **Todos os serviços**, no menu à esquerda e, em seguida, escreva **Intune** no filtro da caixa de texto.

3. Selecione **Intune** e o **Dashboard do Intune** será aberto.

4. No **Dashboard do Intune**, selecione **Conformidade do dispositivo** e, em seguida, selecione **Políticas** na secção **Gerir**.

5. Selecione **Criar política**, introduza o **Nome** e **Descrição** da conformidade do dispositivo, selecione a **Plataforma** e, em seguida, selecione **Configurar** na secção **Definições**.

6. No painel **política de conformidade**, selecione **Estado de Funcionamento do Dispositivo**.

7. No painel **Estado de Funcionamento do Dispositivo**, selecione o Nível de Ameaças para Dispositivos Móveis na lista pendente em **Exigir que o dispositivo esteja no Nível de Ameaça para Dispositivos ou abaixo do mesmo**.

    a.  **Protegido**: Esse nível é o mais seguro. O dispositivo não pode aceder aos recursos da empresa se contiver ameaças. Se forem detetadas ameaças, o dispositivo será avaliado como não conforme.

    b.  **Baixo**: O dispositivo estará em conformidade se apenas ameaças de nível baixo estiverem presentes. Qualquer nível mais alto coloca o dispositivo num estado de não conforme.

    c.  **Médio**: O dispositivo estará em conformidade se as ameaças encontradas no dispositivo forem de nível baixo ou médio. Se forem detetadas ameaças de nível alto, o estado do dispositivo será determinado como não conforme.

    d.  **Alto**: Esse nível é o menos seguro. Este nível permite que todos os níveis de ameaça estejam presentes e utiliza a Defesa Contra Ameaças para Dispositivos Móveis apenas para a criação de relatórios. É necessário que os dispositivos tenham a aplicação de MTD ativada com esta definição.

8. Clique em **OK** duas vezes e, em seguida, selecione **Criar**.

> [!IMPORTANT]
> Se você criar políticas de acesso condicional para o Office 365 ou outros serviços, a avaliação de conformidade do dispositivo será avaliada e os dispositivos não compatíveis serão impedidos de acessar recursos corporativos até que a ameaça seja resolvida no dispositivo.

## <a name="to-assign-an-mtd-device-compliance-policy"></a>Para atribuir uma política de conformidade MTD do dispositivo

Para atribuir uma política de conformidade de dispositivos a utilizadores, selecione uma política que tenha configurado anteriormente. As políticas existentes encontram-se no painel **Conformidade do dispositivo – políticas**.

1. Escolha a política que quer atribuir aos utilizadores e, em seguida, **Atribuições**. Esta ação abre o painel onde pode selecionar **grupos de segurança do Azure Active Directory** e atribuí-los à política.

2. Selecione **Selecionar grupos a incluir** para abrir o painel que apresenta os grupos de segurança do Azure AD.  Escolher **Selecionar** implementa a política para os utilizadores.

    > [!NOTE] 
    > Aplicou a política aos utilizadores. Os dispositivos utilizados pelos utilizadores visados pela política são avaliados quanto à conformidade.

## <a name="next-steps"></a>Passos seguintes

- [Ativar a Defesa Contra Ameaças para Dispositivos Móveis no Intune](mtd-connector-enable.md)
