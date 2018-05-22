---
title: Introdução às aplicações no Microsoft Intune
titlesuffix: ''
description: Localize e adicione aplicações a dispositivos para que a sua força de trabalho comece a trabalhar.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 05/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a1542fc3-672e-47c1-a21f-82826a2f8ac4
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 5d99812c57596e10d0cdfa2c0f4504f8a6ac583c
ms.sourcegitcommit: 34e96e57af6b861ecdfea085acf3c44cff1f3d43
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
---
# <a name="get-started-with-adding-apps-in-microsoft-intune"></a>Introdução à adição de aplicações no Microsoft Intune

Antes de poder atribuir, monitorizar, configurar ou proteger aplicações, tem de adicioná-las ao Intune. O Intune suporta vários tipos de aplicação diferentes. Além disso, as opções disponíveis diferem para cada tipo de aplicação.

O Intune permite-lhe adicionar e atribuir estes tipos de aplicação aos dispositivos da sua empresa:
- **Aplicações da loja** – para dispositivos iOS em que precisa de gestão de aplicações móveis adicional aplicada às aplicações disponíveis na App Store.
- **Aplicações desenvolvidas internamente (linha de negócio)** – opção para a qual carrega um ficheiro que é transferido para os dispositivos dos seus utilizadores.
- **Aplicações incorporadas** – opção na qual atribui aplicações geridas organizadas, tais como aplicações do Office 365, a dispositivos iOS e Android.
- **Aplicações na Web** – opção em que o Intune cria um atalho para a aplicação Web no ecrã principal do dispositivo.

## <a name="how-do-i-assign-a-public-store-app"></a>Como atribuo uma aplicação de loja pública?

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços** > **Intune**. O Intune encontra-se na secção **Monitorização + Gestão**.
3. Selecione **Aplicações Móveis** e, em seguida, selecione **Aplicações**.
4. Selecione **Adicionar** e, em seguida, selecione **iOS** como o **Tipo de aplicação**.
5. Selecione **Selecionar aplicação** para mostrar o painel **Procurar na App Store**.
6. Na caixa de texto, procure uma aplicação para atribuir ao dispositivo. Selecione a aplicação e, em seguida, selecione **Selecionar**.
7. No painel **Adicionar aplicação**, selecione **Informações da aplicação** e, em seguida, certifique-se de que todas as informações da aplicação estão preenchidas. Pode adicionar outros detalhes opcionais para o ajudar a organizar esta aplicação, como **Proprietário**, **Notas**, **Programador** e um **URL de privacidade** para a política de privacidade da sua empresa.
8. Certifique-se de que selecionou **Sim** para **Apresentar como aplicação em destaque no Portal da Empresa** e, em seguida, selecione **OK**.
9. Selecione **Adicionar** no painel **Adicionar aplicação** para adicionar a aplicação. Esta ação direciona-o para a **Descrição Geral** dessa aplicação. Selecione **Atribuições** e, em seguida, clique em **Adicionar grupo** para a atribuir ao seu grupo de teste. **Disponibilize** a aplicação para transferência. A aplicação deverá ser apresentada como uma **Aplicação em Destaque** no seu dispositivo de teste.


- [Como atribuir aplicações a grupos](apps-deploy.md)

## <a name="learn-more"></a>Saiba mais

* [O que é a gestão de aplicações com o Intune?](app-management.md)
* [Descrição geral do ciclo de vida das aplicações](app-lifecycle.md)
* [O que são as políticas de proteção de aplicações?](app-protection-policy.md)
