---
title: "Definir restrições de inscrição no Intune"
titleSuffix: Intune on Azure
description: "Restrinja a inscrição por plataforma e defina um limite de inscrição de dispositivos no Intune. \""
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 07/05/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f0a2b858-a824-4598-ab81-bdd8e62ac3b3
ms.reviewer: amyros
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 2c9d10e4e2a1d2a745b9e327bf9a8a9cd99e5ce4
ms.sourcegitcommit: fd5b7aa26446d2fa92c21638cb29371e43fe169f
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/06/2017
---
# <a name="add-groups-in-intune"></a>Adicionar grupos no Intune
O Intune utiliza grupos do Azure Active Directory (AD) para gerir dispositivos e utilizadores. Como administrador do Intune, pode configurar grupos para se adaptarem às suas necessidades organizacionais. Crie grupos para organizar utilizadores ou dispositivos por localização geográfica, departamento ou características de hardware. Utilize grupos para gerir tarefas em escala. Por exemplo, pode definir políticas para vários utilizadores ou implementar aplicações num conjunto de dispositivos.

Este tópico explica como adicionar grupos para utilizar no Intune.

Pode adicionar os seguintes tipos de grupos:
- **Grupos atribuídos** – adicione manualmente utilizadores ou dispositivos num grupo estático
- **Grupos dinâmicos** – (Azure Active Directory Premium) permite-lhe criar dinamicamente grupos de utilizadores ou dispositivos definidos com regras simples ou avançadas

## <a name="add-a-new-group"></a>Adicionar um novo grupo

Utilize os seguintes passos para criar um novo grupo.
1. No portal do Intune, aceda a **Grupos** e, em seguida, selecione **Novo grupo** no painel **Todos os grupos**.
  ![Captura de ecrã a mostrar o portal do Intune, com a opção Novo grupo selecionada](./media/groups-add-new.png)
2. Especifique o **Nome** e a **Descrição** do novo grupo. Estas propriedades só são apresentadas no portal do Intune e não são apresentadas aos utilizadores.

3. Selecione o **Tipo de associação**:
  - **Atribuído** para criar um grupo com membros atribuídos manualmente. Saiba mais sobre os [grupos atribuídos do Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-groups-create-azure-portal).
  - **Utilizador Dinâmico** para criar um grupo de utilizadores definido com uma **Consulta dinâmica**.
  - **Dispositivo Dinâmico** para criar um grupo de dispositivos definido com uma **Consulta dinâmica**.

  ![Captura de ecrã a mostrar as propriedades do grupo do Intune com Nome, Descrição, Tipo de associação, Ativar funcionalidades do Office e Membros](./media/groups-add-properties.png)

  O Azure AD permite-lhe criar grupos dinâmicos com base em regras que definem a associação. Saiba como [criar grupos dinâmicos baseados em atributos](https://docs.microsoft.com/azure/active-directory/active-directory-groups-dynamic-membership-azure-portal).

4. Pode selecionar **Ativar funcionalidades do Office** para conceder aos membros do grupo de utilizadores acesso a aplicações partilhadas do Office 365.
5. Selecione **Criar** para adicionar o novo grupo.

## <a name="see-also"></a>Consulte também
[Gerir o acesso a recursos com grupos do Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-manage-groups)
[Grupos clássicos do Intune no portal do Azure](groups-get-started.md)
