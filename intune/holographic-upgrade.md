---
title: Atualizar o Windows Holographic para o Windows Holographic for Business
titleSuffix: Azure portal
description: Saiba como atualizar os dispositivos com o Windows Holographic para o Windows Holographic for Business
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 1/30/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: c467d2d4e02785bfac48afe2b39c50300eb4be40
ms.sourcegitcommit: a6fd6b3df8e96673bc2ea48a2b9bda0cf0a875ae
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2018
---
# <a name="upgrade-devices-running-windows-holographic-to-windows-holographic-for-business"></a>Atualizar os dispositivos com o Windows Holographic para o Windows Holographic for Business


Para gerir dispositivos que executam o Windows Holographic com o Microsoft Intune, tem de criar um perfil de Atualização da Edição para atualizar os dispositivos do Windows Holographic para o Windows Holographic for Business. Para o Microsoft HoloLens, pode comprar o conjunto de aplicações comercial para obter a licença necessária para a atualização. Para obter mais informações, veja [Desbloquear as funcionalidades do Windows Holographic for Business](https://docs.microsoft.com/en-us/hololens/hololens-upgrade-enterprise).

## <a name="to-set-up-an-edition-upgrade-device-configuration-profile"></a>Para configurar um perfil de configuração de dispositivos de Atualização da Edição

1. Inicie sessão no [portal do Azure](https://portal.azure.com) com a sua conta de administrador.


2.  Clique em **Configuração do dispositivo**, **Perfis** e, em seguida, clique em **+ Criar perfil**.

    ![Criar perfil](media/Holographic-create-profile.png)

3.  No painel **Criar perfil**, escreva um nome para o perfil, selecione **Windows 10 e posterior** para a plataforma e selecione **Atualização da edição** para o tipo de perfil. Clique em **Configurar Definições**.

5. No painel **Atualização da Edição**, em **Edição para a qual atualizar**, selecione **Windows 10 Holographic for Business**. Em **Ficheiro de Licença**, procure e selecione o ficheiro de licença XML que lhe foi fornecido.

    ![Introduzir o nome do ficheiro XML](media/Holographic-edition-upgrade.png)
 
5.  Clique em **OK** e, em seguida, clique em **Criar** para criar o perfil.


## <a name="deploy-the-edition-upgrade-policy"></a>Implementar a política de Atualização da Edição

Em seguida, tem de atribuir o perfil de Atualização da Edição a dispositivos ou grupos selecionados.

1. No perfil que criou nos passos anteriores, clique em **Atribuições**.

2. No painel **Atribuições**, selecione os dispositivos e grupos de utilizadores que pretende incluir e excluir com a política.

![Incluir e excluir grupos](media/Holographic-groups.PNG)

Quando estes utilizadores ou dispositivos estão inscritos no Intune, o perfil de Atualização da Edição é aplicado. 

## <a name="next-steps"></a>Próximos passos

Para obter mais informações sobre grupos, veja [Introdução aos grupos](get-started-groups.md).

