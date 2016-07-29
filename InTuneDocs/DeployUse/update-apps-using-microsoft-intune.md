---
title: "Atualizar aplicações | Microsoft Intune"
description: "Utilize as informações contidas neste tópico para compreender como pode atualizar aplicações quando é necessária uma nova versão."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 07/12/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: beee6933-876a-4be0-b395-4c24cfbd519b
ms.reviewer: mghadial
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 6716a3d1fb53dc3de0189f637d5664d0a2023d05
ms.openlocfilehash: 5e163cf4e8190d0bc967415f1d907465e4e13f36


---

# Atualizar aplicações com o Microsoft Intune
O Microsoft Intune pode ajudá-lo a gerir as atualizações de aplicações. Utilize as informações contidas neste tópico para compreender como pode atualizar aplicações quando é necessária uma nova versão.

## Como atualizar aplicações
Quando for lançada uma nova versão de uma aplicação que implementou, o Intune permite-lhe atualizar e implementar uma versão mais recente da aplicação. Apenas pode substituir uma implementação por uma versão mais recente da mesma aplicação (utilizando o mesmo identificador). Não pode utilizar atualizações de aplicações para atualizar uma implementação com um pacote de aplicações diferente.

### Identificadores de aplicações
O identificador de aplicação é uma propriedade que identifica de forma exclusiva uma aplicação. Não pode instalar várias cópias de uma aplicação com o mesmo identificador. Por exemplo:

- **iOS** - ID de Pacote (por exemplo, com.microsoft.excel)
- **Android** - ID de Pacote (por exemplo: com.microsoft.excel)
- **Windows Phone** - (instalador xap) utilize ID de Produto (GUID)
- **Windows** - (. appx/appxbundle) utilize o Nome Completo do Pacote



> [!IMPORTANT]
> Quando implementa uma aplicação com uma ação de implementação de **Instalação necessária** e, posteriormente, altera a ação de implementação para **Instalação disponível**, as atualizações da aplicação não são instaladas automaticamente em dispositivos que instalaram a aplicação antes de ter sido efetuada a alteração da implementação. Para corrigir este problema, pode efetuar o seguinte:
> 
> -   Peça ao utilizador do dispositivo para aceder ao portal da empresa, selecionar a aplicação instalada e clicar em **Instalar**.
> -   Altere a ação de implementação para **Desinstalar**e, depois de a aplicação estar desinstalada, volte a implementar a aplicação com uma ação de implementação de **Instalação Disponível**.

### Para atualizar uma aplicação

1.  Na [consola de administrador do Microsoft Intune](https://manage.microsoft.com), selecione **Aplicações** &gt; **Aplicações**.

2.  Na lista **Aplicações** , selecione a aplicação que pretende atualizar e, em seguida, clique em **Editar**.

3.  No assistente para **Editar Software** , forneça os detalhes novos do pacote de aplicações.

4.  Quando terminar, escolha **Atualizar**.

Quando os dispositivos voltarem a verificar as aplicações disponíveis, a aplicação será atualizada automaticamente para a versão mais recente.
Para as aplicações instaladas a partir de um pacote de aplicações (aplicações de linha de negócio), a aplicação será atualizada automaticamente para implementações para as necessárias, desde que a aplicação tenha o mesmo identificador.
No que respeita às aplicações implementadas como ligação a uma loja, a atualização é gerida pela loja onde a aplicação foi comprada.






<!--HONumber=Jul16_HO4-->


