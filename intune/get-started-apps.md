---
title: "Introdução às aplicações"
titlesuffix: Azure portal
description: "Localize e adicione aplicações a dispositivos para que os seus funcionários comecem a trabalhar."
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 08/16/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a1542fc3-672e-47c1-a21f-82826a2f8ac4
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 28bc8547d56073a2175ca57e03dbd9b94fc03ba9
ms.sourcegitcommit: fa6aaf12611c3e03e38e467806fc30b1d0255e88
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/12/2017
---
# <a name="get-started-with-adding-apps"></a>Introdução à adição de aplicações

O Intune suporta várias formas de implementar aplicações em dispositivos da sua empresa:

* **Instaladores de software**: em que carrega um ficheiro que é transferido para os dispositivos dos seus utilizadores
* __Ligações externas__: para quando tem uma aplicação numa loja de aplicações públicas ou uma aplicação Web
* **Aplicações geridas**: para dispositivos iOS em que precisa de gestão de aplicações móveis adicional aplicada às aplicações disponíveis na App Store

Verá um dos métodos de implementação de aplicações mais rápidos ao atribuir uma aplicação de loja pública.

## <a name="how-do-i-assign-a-public-store-app"></a>Como atribuo uma aplicação de loja pública?

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Utilize a opção **Procurar recursos**, procure o **Intune**.
3. Selecione **Aplicações Móveis** e, em seguida, selecione **Aplicações**.
4. Selecione **Adicionar** e, em seguida, selecione **Aplicação da loja iOS** como o **Tipo de aplicação**.
5. Na caixa de texto, procure uma aplicação para atribuir ao dispositivo. Selecione a aplicação e, em seguida, selecione **OK**.
6. No painel **Adicionar aplicação**, selecione **Informações da aplicação** e, em seguida, certifique-se de que todas as informações da aplicação estão preenchidas. Pode adicionar outros detalhes opcionais para o ajudar a organizar esta aplicação, como **Proprietário**, **Notas**, **Programador** e um **URL de privacidade** para a política de privacidade da sua empresa.
7. Certifique-se de que selecionou Sim para Apresentar como aplicação em destaque no Portal da Empresa e, em seguida, selecione OK.
8. Selecione **Adicionar** para adicionar a aplicação. Esta ação irá direcioná-lo para a **Descrição Geral** dessa aplicação. Selecione **Atribuições** e, em seguida, clique em **Selecionar grupos** para a atribuir ao seu grupo de teste. **Disponibilize** a aplicação para transferência. A aplicação deverá ser apresentada como uma **Aplicação em Destaque** no seu dispositivo de teste.

## <a name="learn-more"></a>Saiba mais

* [O que é a gestão de aplicações com o Intune?](app-management.md)
* [Descrição geral do ciclo de vida das aplicações](app-lifecycle.md)
* [O que são as políticas de proteção de aplicações?](app-protection-policy.md)
