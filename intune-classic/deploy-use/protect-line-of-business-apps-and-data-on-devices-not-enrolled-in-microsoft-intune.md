---
title: Proteger aplicações LOB em dispositivos não inscritos
description: Este tópico descreve como pode preparar as suas aplicações de linha de negócio personalizadas de modo a aplicar políticas de gestão de dispositivos móveis que ajudem a evitar a perda de dados.
keywords: ''
author: mattbriggs
ms.author: mabriggs
manager: angrobe
ms.date: 11/14/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 00219467-a62e-43b6-954b-3084f54c45ba
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 0fbc7ae1937aff60e8e494df06ee2c30e2fe8855
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/16/2018
---
# <a name="protect-line-of-business-apps-and-data-on-devices-that-are-not-enrolled-in-microsoft-intune"></a>Proteger aplicações e dados de linha de negócio em dispositivos não inscritos no Microsoft Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

As políticas de gestão de aplicações móveis (MAM) ajudam a proteger dados empresariais ao impedir ações que poderiam originar fugas de dados empresariais e ao aplicar requisitos de acesso a dados, por exemplo a introdução de um PIN da aplicação. Para aplicar políticas de MAM a aplicações de linha de negócio iOS e Android, primeiro tem de encapsular a aplicação com a Ferramenta de Encapsulamento de Aplicações do Microsoft Intune. O encapsulamento de aplicações é o processo de aplicar uma camada de gestão a uma aplicação móvel sem que seja necessário fazer alterações à mesma e distribuí-la pelos utilizadores.  

Este tópico explica os passos necessários para aplicar políticas de MAM a aplicações acedidas por utilizadores em **dispositivos pertencentes aos empregados, que não são geridos**, e em dispositivos geridos por uma **solução de gestão de dispositivos móveis (MDM) de terceiros**.  Para preparar as aplicações de linha de negócio que são executadas em **dispositivos que estão inscritos na MDM do Intune**, veja [Decidir como preparar as aplicações para a gestão de aplicações móveis com o Microsoft Intune](/intune/apps-prepare-mobile-application-management).


##  <a name="step-1-prepare-the-app"></a>Passo 1: preparar a aplicação

Para poder aplicar políticas de MAM a uma aplicação, primeiro tem de encapsular a aplicação com a Ferramenta de Encapsulamento de Aplicações do Microsoft Intune para [iOS](/intune/app-wrapper-prepare-ios) e [Android](/intune/app-wrapper-prepare-android) ou utilizar o [SDK da Aplicação Intune](/intune/app-sdk) para integrar manualmente as funcionalidades de proteção da aplicação Intune.

Para obter mais informações sobre a utilização da Ferramenta de Encapsulamento de Aplicações vs. o SDK, veja [Decidir como preparar as aplicações para a gestão de aplicações móveis com o Microsoft Intune](/intune/apps-prepare-mobile-application-management).

## <a name="step-2-add-the-app"></a>Passo 2: adicionar a aplicação

Para associar a aplicação de linha de negócio às políticas de MAM, tem de adicionar os detalhes da aplicação ao seu inquilino/subscrição do Intune, para tal siga estes passos:

1. No [Portal do Azure](https://portal.azure.com/), aceda a **Gestão de aplicações móveis do Intune** > **Definições** e escolha **Aplicações de linha de negócio**.

   ![Captura de ecrã do painel Definições com a opção de linha de negócio](../media/mam-azure-portal-lob-on-settings.png)

2. No painel **Aplicações de linha de negócio**, escolha **Adicionar uma aplicação personalizada**.

   ![Captura de ecrã do painel de aplicações de linha de negócio com o botão Adicionar uma aplicação personalizada na parte superior](../media/mam-azure-portal-add-lob-app-action.png)
3. Forneça um nome para a aplicação, o identificador de pacote no campo Identificador da aplicação e a plataforma (iOS ou Android).

   ![Captura de ecrã do painel Adicionar uma aplicação personalizada](../media/mam-azure-portal-add-app-details.png)

   Este passo ajuda a criar uma lista exclusiva da sua aplicação. A aplicação será também apresentada na lista de Aplicações de destino para uma política de MAM do seu inquilino, conforme descrito no passo seguinte.

## <a name="step-3-apply-mam-policies"></a>Passo 3: aplicar políticas de MAM
Depois de os metadados de aplicação serem carregados para o serviço, a aplicação é apresentada na lista de aplicações. Pode agora [criar uma nova política ou utilizar uma política existente](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md) e aplicá-la à aplicação de linha de negócio que adicionou no passo 2.

>[!IMPORTANT]
>Tem de direcionar a política MAM aos utilizadores que vão utilizar a aplicação encapsulada.  Os utilizadores em relação aos quais não tenha sido aplicada esta política não podem utilizar a aplicação.


  ![Captura de ecrã do painel Lista visada de aplicações, com a nova aplicação de linha de negócio apresentada](../media/mam-azure-portal-lob-on-targeted-app-list.png)
## <a name="step-4-distribute-the-app"></a>Passo 4: distribuir a aplicação
É possível implementar aplicações para os utilizadores das seguintes formas:
* Para dispositivos que estão inscritos numa solução de MDM de terceiros, pode distribuir aplicações através da sua solução de MDM.
* Para dispositivos que não são geridos por qualquer solução de MDM, é necessária uma solução personalizada. Os utilizadores têm de transferir e instalar a aplicação nos respetivos dispositivos.

## <a name="change-the-metadata"></a>Alterar os metadados
Se precisar de alterar os detalhes da aplicação, como o nome da aplicação ou o identificador do pacote, tem de [remover a aplicação](#remove-apps) e [adicioná-la](#step-2-add-the-app) aos novos metadados.

##  <a name="remove-apps"></a>Remover aplicações
Pode remover uma aplicação de linha de negócio da lista de aplicações. Este procedimento removerá a aplicação da lista e a associação às políticas de MAM, mas não removerá ou desinstalará a aplicação do dispositivo do utilizador.  

1. No [Portal do Azure](https://portal.azure.com/), aceda a **Gestão de aplicações móveis do Intune** > **Definições**. No painel **Definições**, escolha **Linha de negócio** para abrir a lista de aplicações existentes.  
2. Selecione a aplicação que pretende remover e escolha o menu **(…) contexto**.

   ![Captura de ecrã do painel de aplicações de linha de negócio com o botão de reticências](../media/mam-azure-portal-lob-context-menu.png)
3. Escolha **Eliminar aplicação** para eliminar a aplicação.

   ![Captura de ecrã do painel de linha de negócio com a opção de eliminação de aplicações](../media/mam-azure-portal-delete-app.png)

   Este procedimento removerá aplicações da lista de aplicações de linha de negócio e a Lista de aplicações visadas na política de MAM.
