---
title: "Portal de resolução de problemas de suporte técnico"
titlesuffix: Azure portal
description: "O pessoal de suporte técnico utiliza o portal de resolução de problemas para resolver problemas técnicos dos utilizadores"
keywords: 
author: NathBarn
ms.author: NathBarn
manager: angrobe
ms.date: 08/23/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1f39c02a-8d8a-4911-b4e1-e8d014dbce95
ms.reviewer: sumitp
ms.custom: intune-azure
ms.openlocfilehash: 14b47727428fcd6a16f9960e21f70ee64c7757d1
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/09/2017
---
# <a name="use-the-troubleshooting-portal-to-help-users"></a>Utilizar o portal de resolução de problemas

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

O portal de resolução de problemas permite que os operadores de suporte técnico e os administradores do Intune vejam as informações de utilizador para resolverem pedidos de ajuda dos utilizadores. As organizações que têm operadores de suporte técnico podem atribuir o **Operador de suporte técnico** a um grupo de utilizadores, que pode então utilizar o painel Resolução de Problemas para ajudar os utilizadores.

Por exemplo, quando um utilizador contacta o suporte acerca de um problema técnico com o Intune, o operador de suporte técnico introduz o nome do utilizador. O Intune mostra dados úteis que podem ajudar a resolver vários problemas de nível 1, incluindo:
- Estado de utilizador
- Atribuições
- Resolver problemas de compatibilidade
- O dispositivo não responde
-   O dispositivo não consegue aceder às definições de VPN ou Wi-Fi
-   Falha na instalação da aplicação

## <a name="add-help-desk-operators"></a>Adicionar operadores de suporte técnico
Enquanto administrador do Intune, pode atribuir a função Operador de Suporte Técnico a um grupo de utilizadores. Os membros desse grupo podem utilizar o portal do Azure para resolver problemas dos utilizadores. Cada operador de suporte técnico tem de ter uma licença do Intune para aceder ao portal do Azure. Saiba como [atribuir licenças do Intune](licenses-assign.md).

Para adicionar operadores de suporte técnico:
1. [Adicione utilizadores ao Intune](users-add.md) se necessário.
2. [Crie um grupo de suporte técnico](groups-add.md) e adicione utilizadores ao grupo.
3. [Atribua a função de Operador de Suporte Técnico de RBAC](role-based-access-control.md#built-in-roles).

  ![Captura de ecrã do portal do Azure a mostrar as funções do Intune realçadas e uma lista das funções incorporadas, incluindo Operador de Suporte Técnico](./media/help-desk-user-add.png) Também pode [criar uma função personalizada](role-based-access-control.md#custom-roles), que pode modificar para conceder acesso aos operadores de suporte técnico.  Os operadores de suporte técnico necessitam das seguintes permissões para ajudar a resolver os problemas do utilizador:
    - Aplicações Móveis: ler
    - Aplicações Geridas: ler
    - Dispositivos Geridos: ler
    - Organização: ler
    - Políticas de Conformidade dos Dispositivos: ler
    - Configurações dos Dispositivos: ler

4. Para dar permissão aos operadores de suporte técnico para ver o estado de funcionamento do serviço e abrir pedidos de suporte do Intune, [conceda permissões de administrador aos utilizadores](https://docs.microsoft.com/azure/active-directory/active-directory-users-assign-role-azure-portal) como **Administrador de Serviços**. Não conceda a permissão **Administrador do Serviço Intune**, porque esta função de diretório contém mais direitos do que os necessários para operadores de suporte técnico.

## <a name="access-the-troubleshooting-portal"></a>Aceder ao portal de resolução de problemas

O pessoal de suporte técnico e os administradores do Intune podem aceder ao portal de resolução de problemas de duas formas:
- Abra o site [http://aka.ms/intunetroubleshooting](http://aka.ms/intunetroubleshooting) num browser para ver apenas o portal de resolução de problemas.
  ![Captura de ecrã da consola Resolução de problemas](./media/help-desk-console.png)
- Inicie sessão no portal do Azure, selecione **Mais Serviços** > **Monitorização + Gestão** > **Intune** e, em seguida, aceda a **Ajuda e Suporte** > **Resolução de problemas**.

Clique em **Utilizador selecionado** para ver um utilizador e os detalhes do mesmo.

## <a name="use-the-troubleshooting-portal"></a>Utilizar o portal de resolução de problemas

No portal de resolução de problemas, pode escolher **Selecionar utilizador** para ver informações dos utilizadores. As informações dos utilizadores podem ajudá-lo a compreender o estado atual dos utilizadores e dos dispositivos deles. O portal de resolução de problemas mostra os seguintes detalhes de resolução de problemas:
- **Estado da conta**
- **Estado de utilizador**
- **Dispositivos** com ações do dispositivo
- **Associação a grupos**
- **Estado da proteção de aplicações**
