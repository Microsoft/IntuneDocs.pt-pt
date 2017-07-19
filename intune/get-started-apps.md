---
title: "Introdução às aplicações"
titleSuffix: Intune on Azure
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 06/27/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a1542fc3-672e-47c1-a21f-82826a2f8ac4
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a086da185681a91daad214f1be2d4ff0e2827fbb
ms.sourcegitcommit: fd2e8f6f8761fdd65b49f6e4223c2d4a013dd6d9
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/03/2017
---
# <a name="getting-started-with-apps"></a>Introdução às aplicações

![Uma imagem a mostrar a adição da aplicação Microsoft Word.](/intune/media/generic-add-apps.png)

Os dispositivos de trabalho não servem de nada sem as aplicações certas. O Intune suporta várias formas de implementar aplicações em dispositivos da sua empresa:

* **Instaladores de software**: em que carrega um ficheiro que é transferido para os dispositivos dos seus utilizadores
* __Ligações externas__: para quando tem uma aplicação numa loja de aplicações públicas ou uma aplicação Web
* **Aplicações geridas**: para dispositivos iOS em que precisa de gestão de aplicações móveis adicional aplicada às aplicações disponíveis na App Store

Verá um dos métodos de implementação de aplicações mais rápidos ao atribuir uma aplicação de loja pública.

__Como atribuir uma aplicação de loja pública?__

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Utilize a opção **Procurar recursos**, procure o **Intune**.
3. Selecione **Aplicações Móveis** e, em seguida, selecione **Aplicações**.
4. Selecione **Adicionar** e, em seguida, selecione **Aplicação da loja iOS** como o **Tipo de aplicação**.
5. Na caixa de texto, procure uma aplicação para atribuir ao dispositivo. Selecione a aplicação e, em seguida, selecione **OK**.
6. No painel **Adicionar aplicação**, selecione **Informações da aplicação** e, em seguida, certifique-se de que todas as informações da aplicação estão preenchidas. Pode adicionar outros detalhes opcionais para o ajudar a organizar esta aplicação, como **Proprietário**, **Notas**, **Programador** e um **URL de privacidade** para a política de privacidade da sua empresa.
7. Certifique-se de que selecionou Sim para Apresentar como aplicação em destaque no Portal da Empresa e, em seguida, selecione OK.
8. Selecione **Adicionar** para adicionar a aplicação. Esta ação irá direcioná-lo para a **Descrição Geral** dessa aplicação. Selecione **Atribuições** e, em seguida, clique em **Selecionar grupos** para a atribuir ao seu grupo de teste. **Disponibilize** a aplicação para transferência. A aplicação deverá ser apresentada como uma **Aplicação em Destaque** no seu dispositivo de teste.
