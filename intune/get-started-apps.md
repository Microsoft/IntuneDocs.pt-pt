---
title: "Introdução às aplicações"
titlesuffix: Azure portal
description: "Localize e adicione aplicações a dispositivos para que os seus funcionários comecem a trabalhar."
keywords: 
author: erikre
ms.author: erikre
manager: dougeby
ms.date: 12/06/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a1542fc3-672e-47c1-a21f-82826a2f8ac4
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: c1838f1d856efdebb7e2114cb61dd8d88ca100f7
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/25/2018
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
4. Selecione **Adicionar** e, em seguida, selecione **iOS** em **Aplicação da loja** como o **Tipo de aplicação**.
5. Selecione **Selecionar aplicação** para mostrar o painel **Procurar na App Store**.
6. Na caixa de texto, procure uma aplicação para atribuir ao dispositivo. Selecione a aplicação e, em seguida, selecione **Selecionar**.
7. No painel **Adicionar aplicação**, selecione **Informações da aplicação** e, em seguida, certifique-se de que todas as informações da aplicação estão preenchidas. Pode adicionar outros detalhes opcionais para o ajudar a organizar esta aplicação, como **Proprietário**, **Notas**, **Programador** e um **URL de privacidade** para a política de privacidade da sua empresa.
8. Certifique-se de que selecionou **Sim** para **Apresentar como aplicação em destaque no Portal da Empresa** e, em seguida, selecione **OK**.
9. Selecione **Adicionar** no painel **Adicionar aplicação** para adicionar a aplicação. Esta ação irá direcioná-lo para a **Descrição Geral** dessa aplicação. Selecione **Atribuições** e, em seguida, clique em **Selecionar grupos** para a atribuir ao seu grupo de teste. **Disponibilize** a aplicação para transferência. A aplicação deverá ser apresentada como uma **Aplicação em Destaque** no seu dispositivo de teste.

## <a name="learn-more"></a>Saiba mais

* [O que é a gestão de aplicações com o Intune?](app-management.md)
* [Descrição geral do ciclo de vida das aplicações](app-lifecycle.md)
* [O que são as políticas de proteção de aplicações?](app-protection-policy.md)
