---
title: "Atualizar aplicações"
description: "Utilize as informações contidas neste tópico para compreender como pode atualizar aplicações quando é necessária uma nova versão."
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 12/27/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: beee6933-876a-4be0-b395-4c24cfbd519b
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: c643ea0e75a3376a30d43fc0c5ac4ef421c65bea
ms.sourcegitcommit: 769db6599d5eb0e2cca537d0f60a5df9c9f05079
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/15/2017
---
# <a name="update-apps-using-microsoft-intune"></a>Atualizar aplicações com o Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

O Microsoft Intune pode ajudá-lo a gerir as atualizações de aplicações. Utilize as informações contidas neste tópico para compreender como pode atualizar aplicações quando é necessária uma nova versão.

## <a name="how-to-update-apps"></a>Como atualizar aplicações
Quando for lançada uma nova versão de uma aplicação que implementou, o Intune permite-lhe atualizar e implementar uma versão mais recente da aplicação. Apenas pode substituir uma implementação por uma versão mais recente da mesma aplicação (com o mesmo identificador). Não pode utilizar atualizações de aplicação para atualizar uma implementação com um pacote de aplicação diferente.

### <a name="app-identifiers"></a>Identificadores de aplicações
O identificador de aplicação é uma propriedade que identifica de forma exclusiva uma aplicação. Não pode instalar várias cópias de uma aplicação com o mesmo identificador. Seguem-se alguns exemplos de identificadores de aplicações:

- **iOS** - ID de Pacote (por exemplo, com.microsoft.excel)
- **Android** - ID de Pacote (por exemplo: com.microsoft.excel)
- **Windows Phone** - (instalador xap) utilize ID de Produto (GUID)
- **Windows** - (. appx/appxbundle) utilize o Nome Completo do Pacote



> [!IMPORTANT]
> Quando implementa uma aplicação com uma ação de implementação de **Instalação necessária** e, posteriormente, altera a ação de implementação para **Instalação disponível**, as atualizações da aplicação não são instaladas automaticamente em dispositivos que instalaram a aplicação antes de ter sido efetuada a alteração da implementação. Para corrigir este problema, pode efetuar o seguinte:
>
> -   Peça ao utilizador do dispositivo para aceder ao portal da empresa, selecionar a aplicação instalada e escolher **Instalar**.
> -   Altere a ação de implementação para **Desinstalar**e, depois de a aplicação estar desinstalada, volte a implementar a aplicação com uma ação de implementação de **Instalação Disponível**.

### <a name="to-update-an-app"></a>Para atualizar uma aplicação

1.  Na [consola de administração do Microsoft Intune](https://manage.microsoft.com), escolha **Aplicações** &gt; **Aplicações**.

2.  Na lista **Aplicações**, selecione a aplicação que pretende atualizar e, em seguida, clique em **Editar**.

3.  No assistente para **Editar Software**, forneça os detalhes novos do pacote de aplicação.

4.  Quando terminar, escolha **Atualizar**.

Quando os dispositivos voltarem a verificar as aplicações disponíveis, a aplicação será atualizada automaticamente para a versão mais recente.
Em relação às aplicações instaladas a partir de um pacote de aplicação (aplicações de linha de negócio), a aplicação será atualizada automaticamente tanto para implementações necessárias como disponíveis, desde que a aplicação tenha o mesmo identificador.

No que respeita às aplicações implementadas como ligação a uma loja, a atualização é gerida pela loja onde a aplicação foi comprada.
