---
title: "Introdução às aplicações no Microsoft Intune"
titlesuffix: 
description: "Localize e adicione aplicações a dispositivos para que a sua força de trabalho comece a trabalhar."
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 3/02/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a1542fc3-672e-47c1-a21f-82826a2f8ac4
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0185eebbe436da73e1920d7cd834f0897a143894
ms.sourcegitcommit: 7e5c4d43cbd757342cb731bf691ef3891b0792b5
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/05/2018
---
# <a name="get-started-with-adding-apps-in-microsoft-intune"></a>Introdução à adição de aplicações no Microsoft Intune

Antes de poder atribuir, monitorizar, configurar ou proteger aplicações, tem de adicioná-las ao Intune. O Intune suporta vários tipos de aplicação diferentes. Além disso, as opções disponíveis diferem para cada tipo de aplicação.

O Intune permite-lhe adicionar e atribuir estes tipos de aplicação aos dispositivos da sua empresa:
- **Aplicações da loja** – para dispositivos iOS em que precisa de gestão de aplicações móveis adicional aplicada às aplicações disponíveis na App Store.
- **Aplicações desenvolvidas internamente (linha de negócio)** – opção para a qual carrega um ficheiro que é transferido para os dispositivos dos seus utilizadores.
- **Aplicações incorporadas** – opção na qual atribui aplicações geridas organizadas, tais como aplicações do Office 365, a dispositivos iOS e Android. 
- **Aplicações na Web** – opção em que o Intune cria um atalho para a aplicação Web no ecrã principal do dispositivo.

## <a name="how-do-i-assign-a-public-store-app"></a>Como atribuo uma aplicação de loja pública?

O seguinte exemplo irá guiá-lo ao longo dos passos para adicionar uma aplicação iOS no Microsoft Intune.

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços** > **Intune**. O Intune encontra-se na secção **Monitorização + Gestão**.
3. No painel **Intune**, escolha **Aplicações móveis**.
4. Na carga de trabalho **Aplicações móveis**, selecione **Aplicações** na secção **Gerir**.
5. Selecione **Adicionar** no lado direito do painel **Aplicações**.
6. Na lista **Tipo de aplicação**, selecione **iOS** nos tipos de **Aplicação da loja** disponíveis.
6. Selecione **Procurar na App Store**.
7. No painel **Procurar na App Store**, primeiro selecione a região da Loja de aplicações.
8. Escreva o nome (ou parte do mesmo) na caixa de pesquisa. O Intune procura na loja e apresenta uma lista de resultados relevantes.
9. Na lista, selecione a aplicação que pretende e, em seguida, clique em **Selecionar**.
10. Selecione **Informações da aplicação** para configurar as informações da aplicação.
11. (Opcional) Adicione detalhes para o ajudar a organizar esta aplicação, como **Proprietário**, **Notas**, **Programador** e um **URL de Privacidade** (a apontar para a política de privacidade da sua empresa).
12. Selecione **Sim** para a opção **Apresentar como aplicação em destaque no Portal da Empresa**. 
13. Clique em **OK** após ter adicionado todas as informações da aplicação necessárias.
14. Clique em **Adicionar** no painel **Adicionar aplicação**. Será direcionado para a **Descrição geral** dessa aplicação. 

## <a name="next-steps"></a>Passos seguintes

Agora que adicionou uma aplicação ao Intune, pode atribuir os grupos de funcionários que poderão incluir a aplicação no seu dispositivo.

- [Como atribuir aplicações a grupos](apps-deploy.md)
- 
## <a name="learn-more"></a>Saiba mais

* [O que é a gestão de aplicações com o Intune?](app-management.md)
* [Descrição geral do ciclo de vida das aplicações](app-lifecycle.md)
* [O que são as políticas de proteção de aplicações?](app-protection-policy.md)
