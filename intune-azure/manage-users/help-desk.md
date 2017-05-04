---
title: "Portal de resolução de problemas de suporte técnico | Microsoft Docs"
titleSuffix: Intune Azure preview
description: "O pessoal de suporte técnico utiliza o portal de resolução de problemas para resolver problemas técnicos dos utilizadores"
keywords: 
author: NathBarn
ms.author: NathBarn
manager: angrobe
ms.date: 03/18/17
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1f39c02a-8d8a-4911-b4e1-e8d014dbce95
ms.reviewer: sumitp
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: e0ecc775f70703574c4e1adf0f0aa204f2745b72
ms.openlocfilehash: 723830f686991fe13de13f75c6a5d1bc84e6920b
ms.lasthandoff: 04/20/2017

---
# <a name="help-users-with-the-troubleshooting-portal-in-microsoft-intune"></a>Ajudar os utilizadores com o Portal de resolução de problemas no Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

O portal de resolução de problemas permite aos operadores de suporte técnico e aos administradores do Intune verem os utilizadores e os respetivos dispositivos e executar tarefas para resolver problemas técnicos do Intune.

## <a name="add-help-desk-operators"></a>Adicionar operadores de suporte técnico
Um administrador do Intune pode atribuir a permissão de operador de suporte técnico aos utilizadores. Os utilizadores do suporte técnico podem ver o portal do Intune, mas não podem ver ou executar tarefas administrativas fora da carga de trabalho de resolução de problemas.

1. Como um administrador do Intune, inicie sessão no [portal do Azure](https:portal.azure.com), selecione **Mais Serviços** > **Monitorização + Gestão** > **Intune**.
2. No painel de navegação à esquerda, selecione **Funções do Intune**.
3. Na carga de trabalho **Funções do Intune**, selecione **Operador de Suporte Técnico** e, em seguida, selecione **Atribuir**.
4. Escreva um **Nome da atribuição** (obrigatório), uma **Descrição da atribuição** (opcional) e, em seguida, atribua **Membros (Grupos)** e **Âmbito (Grupos)**.
5. Os membros da função Operador de Suporte Técnico podem agora utilizar o portal de resolução de problemas.

Para obter mais informações sobre as funções do Intune, veja [Funções do Intune (RBAC)](https://docs.microsoft.com/intune-azure/access-control/role-based-access-control).

## <a name="access-the-troubleshooting-portal"></a>Aceder ao portal de resolução de problemas

O pessoal de suporte técnico e os administradores do Intune podem aceder ao portal de resolução de problemas de duas formas:
- No [portal do Azure](https:portal.azure.com), selecione **Mais Serviços** > **Monitorização + Gestão** > **Intune** e, em seguida, no painel de navegação à esquerda, selecione **Resolução de problemas**. As outras cargas de trabalho são visíveis no painel de navegação à esquerda, mas não estão disponíveis.
![Captura de ecrã da carga de trabalho da Resolução de problemas do Intune com a ligação Selecionar Utilizador](media/help-desk-user.png)
- Abra [http://aka.ms/intunetroubleshooting](http://aka.ms/intunetroubleshooting) num browser. Apenas o Portal de resolução de problemas está visível.

## <a name="use-the-troubleshooting-portal"></a>Utilizar o portal de resolução de problemas

No portal de resolução de problemas, pode selecionar **Selecionar Utilizador** para ver informações dos utilizadores. As informações dos utilizadores podem ajudá-lo a compreender o estado atual dos utilizadores e dos dispositivos deles. O portal de resolução de problemas mostra os seguintes detalhes dos dispositivos e dos utilizadores do Intune:
- Informações da conta de utilizador
- Associação a grupos de utilizadores
- Detalhes do dispositivo

Os utilizadores do suporte técnico também podem executar tarefas remotas nos dispositivos, tais como o **Bloqueio remoto**.

