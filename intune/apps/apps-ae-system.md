---
title: Adicione aplicações do sistema Android Enterprise ao Microsoft Intune
titleSuffix: ''
description: Saiba como adicionar aplicações do sistema Enterprise ao Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/23/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: priyar
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 613369070d847265f371a7b228a2b6d81bf813fe
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/26/2020
ms.locfileid: "76755260"
---
# <a name="add-android-enterprise-system-apps-to-microsoft-intune"></a>Adicione aplicações do sistema Android Enterprise ao Microsoft Intune

Antes de atribuir uma aplicação a um dispositivo ou grupo de utilizadores, tem de primeiro adicionar a aplicação ao Microsoft Intune. Os aplicativos do sistema têm suporte em dispositivos Android Enterprise. Pode ativar um aplicativo de sistema para [dispositivos dedicados](../enrollment/android-kiosk-enroll.md) ao Android Enterprise ou [dispositivos totalmente geridos.](../enrollment/android-fully-managed-enroll.md)

## <a name="add-the-app"></a>Adicionar a aplicação

Pode adicionar uma aplicação do sistema Android Enterprise ao Intune a partir do portal Azure, fazendo o seguinte:

1. Entre no centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selecione **aplicativos** > **todos os aplicativos** > **Adicionar**.
3. No painel de **tipo de aplicação Select,** sob os **outros** tipos disponíveis, selecione **aplicação do sistema Android Enterprise**.
4. Clique em **Selecionar**. Os passos da **aplicação Add** são apresentados.
Na página de informações da **App,** adicione os detalhes da aplicação:
    - Nome da **aplicação**: Introduza o nome da aplicação.
    - **Publicador**: introduza o nome do publicador da aplicação.  
    - **Nome do pacote**: Introduza um nome de pacote. Intune validará que o nome do pacote é válido.
5. Clique em **Seguir** para exibir a página **de tags scope.**
8. Clique em **Selecionar etiquetas** de âmbito para adicionar opcionalmente etiquetas de âmbito para a aplicação. Para mais informações, consulte [Utilize o controlo de acesso baseado em funções (RBAC) e as etiquetas](~/fundamentals/scope-tags.md)de âmbito para TI distribuídos .
9. Clique em **Avançar** para exibir a página **atribuições** .
10. Selecione as atribuições de grupo para a aplicação. Para mais informações, consulte [Adicionar grupos para organizar utilizadores e dispositivos](~/fundamentals/groups-add.md). 
11. Clique em **Seguir** para exibir a página **Review + criar.** Reveja os valores e configurações que inseriu para a aplicação.
12. Quando terminar, clique em **Criar** para adicionar a app ao Intune.

A lâmina **de visão geral** da aplicação que criou é exibida.

> [!NOTE]
> Terá de trabalhar com o OEM do seu dispositivo para encontrar o nome do pacote da app que deseja ativar/desativar.

A aplicação criada é apresentada na lista de aplicações, onde a pode atribuir aos grupos que selecionar. 

As aplicações do sistema Android Enterprise vão ativar ou desativar aplicações que já fazem parte da plataforma. Para ativar uma aplicação, atribua a aplicação do sistema conforme **necessário**. Para desativar uma aplicação, atribua a aplicação do sistema como **Desinstalar**. As aplicações do sistema não podem ser atribuídas como disponíveis para um utilizador.


## <a name="next-steps"></a>Próximos passos

- [Atribuir aplicações a grupos](apps-deploy.md)
