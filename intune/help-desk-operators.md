---
title: "Portal de resolução de problemas de suporte técnico"
titleSuffix: Intune on Azure
description: "O pessoal de suporte técnico utiliza o portal de resolução de problemas para resolver problemas técnicos dos utilizadores"
keywords: 
author: NathBarn
ms.author: NathBarn
manager: angrobe
ms.date: 06/28/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1f39c02a-8d8a-4911-b4e1-e8d014dbce95
ms.reviewer: sumitp
ms.custom: intune-azure
ms.openlocfilehash: 7a61c3703cd1016ef63c8baa371c3a21dca127fc
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/01/2017
---
# <a name="help-users-with-the-troubleshooting-portal-in-microsoft-intune"></a>Ajudar os utilizadores com o Portal de resolução de problemas no Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

O portal de resolução de problemas permite que os operadores de suporte técnico e os administradores do Intune vejam as informações de utilizador para resolverem pedidos de ajuda dos utilizadores. As organizações que têm operadores de suporte técnico podem atribuir o **Operador de suporte técnico** a um grupo de utilizadores, que pode então utilizar o painel Resolução de Problemas para ajudar os utilizadores.

Por exemplo, quando um utilizador contacta o suporte acerca de um problema técnico com o Intune, o operador de suporte técnico introduz o nome do utilizador. O Intune apresenta informações pertinentes que podem ajudar a resolver muitos problemas de nível 1, como o estado do utilizador, falha na instalação da aplicação ou problemas de conformidade. Os problemas abrangidos podem incluir:
- O dispositivo não responde
-   O dispositivo não consegue aceder às definições de VPN ou Wi-Fi
-   Falha na instalação da aplicação


## <a name="add-help-desk-operators"></a>Adicionar operadores de suporte técnico
Um administrador do Intune pode atribuir a permissão de operador de suporte técnico aos utilizadores de duas formas:
- Atribuir a função incorporada **Operador de Suporte Técnico**
- Criar e atribuir uma função personalizada

## <a name="assign-help-desk-operator-role"></a>Atribuir a função de operador de suporte técnico
Enquanto administrador do Intune, pode atribuir a função Operador de Suporte Técnico a um grupo de utilizadores. Os membros desse grupo podem utilizar o portal de administração. Cada operador de suporte técnico tem de ter uma licença do Intune para aceder ao portal do Intune. Saiba como [atribuir licenças do Intune](licenses-assign.md).

1. Como administrador do Intune, inicie sessão no portal do Intune e selecione **Funções do Intune**.
2. Na carga de trabalho **Funções do Intune**, selecione **Operador de Suporte Técnico** > **Atribuições** e, em seguida, selecione **Atribuir**.
  ![Captura de ecrã a mostrar o portal do Intune, com as funções do Intune realçadas e uma lista das funções incorporadas, incluindo Operador de Suporte Técnico com a opção Atribuições realçada e uma caixa vermelha à volta de Atribuir](./media/help-desk-user-assign.png)
3. Escreva um **Nome da atribuição** (obrigatório), uma **Descrição da atribuição** (opcional) e, em seguida, atribua **Membros (Grupos)** e **Âmbito (Grupos)**.
4. Os membros da função Operador de Suporte Técnico podem agora utilizar o portal de resolução de problemas.

Para obter mais informações sobre as funções do Intune, veja [Funções do Intune (RBAC)](role-based-access-control.md).

## <a name="create-a-custom-role-for-troubleshooting"></a>Criar uma função personalizada para a resolução de problemas
Como administrador do Intune, pode criar uma função personalizada que permite que os utilizadores utilizem o portal de resolução de problemas com permissões que se adequam às necessidades da sua organização. Para obter mais informações sobre as funções do Intune, veja [Funções do Intune (RBAC)](role-based-access-control.md).

![Captura de ecrã a mostrar o portal do Intune, com as funções do Intune realçadas e uma lista das funções incorporadas, incluindo Operador de Suporte Técnico](./media/help-desk-user-add.png)

Para utilizar a consola do Intune para obter uma vista de suporte técnico, uma função de suporte técnico personalizada deve ter as seguintes permissões:
- Aplicações Móveis: ler
- Aplicações Geridas: ler
- Dispositivos Geridos: ler
- Organização: ler

## <a name="access-the-troubleshooting-portal"></a>Aceder ao portal de resolução de problemas

O pessoal de suporte técnico e os administradores do Intune podem aceder ao portal de resolução de problemas de duas formas:
- Abra [http://aka.ms/intunetroubleshooting](http://aka.ms/intunetroubleshooting) num browser.
- No portal do Intune, aceda a **Ajuda e Suporte** > **Resolução de Problemas**.

![Captura de ecrã da carga de trabalho da Resolução de Problemas do Intune com a ligação Selecionar Utilizador](media/help-desk-user.png)

## <a name="use-the-troubleshooting-portal"></a>Utilizar o portal de resolução de problemas

No portal de resolução de problemas, pode escolher **Selecionar utilizador** para ver informações dos utilizadores. As informações dos utilizadores podem ajudá-lo a compreender o estado atual dos utilizadores e dos dispositivos deles. O portal de resolução de problemas mostra os seguintes detalhes de resolução de problemas:
- **Estado do inquilino**
- **Estado de utilizador**
- **Dispositivos** e ações do dispositivo
- **Associação a grupos**
- **Estado da proteção de aplicações**
