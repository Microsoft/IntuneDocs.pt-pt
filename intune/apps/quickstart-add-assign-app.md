---
title: 'Guia de Início Rápido: adicionar e atribuir uma aplicação cliente'
titleSuffix: Microsoft Intune
description: Neste guia de início rápido, irá utilizar o Microsoft Intune para adicionar e atribuir uma aplicação cliente.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
ms.topic: quickstart
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: dab6f5c8-1ebb-42c4-a7a7-7af001f94e15
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 40337b3c45885dacf486173814044a27b7f3f6cc
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/26/2020
ms.locfileid: "76755073"
---
# <a name="quickstart-add-and-assign-a-client-app"></a>Guia de Início Rápido: adicionar e atribuir uma aplicação cliente

Neste guia de início rápido, irá utilizar o Intune para adicionar e atribuir uma aplicação cliente à força de trabalho da sua empresa. Uma das prioridades de um administrador é garantir que os utilizadores finais têm acesso às aplicações que precisam para trabalhar. 

Se não tiver uma subscrição do Intune, [inscreva-se numa conta de avaliação gratuita](../fundamentals/free-trial-sign-up.md).

## <a name="prerequisites"></a>Pré-requisitos

- Para concluir este guia de início rápido, tem de [criar um utilizador](../fundamentals/quickstart-create-user.md), [criar um grupo](../fundamentals/quickstart-create-group.md) e [inscrever um dispositivo](../quickstart-setup-auto-enrollment.md).

## <a name="sign-in-to-intune"></a>Iniciar sessão no Intune

Entre no [Intune](https://aka.ms/intuneportal) como um [administrador global ou um administrador de serviços do Intune](../fundamentals/users-add.md#types-of-administrators). Se criou uma Subscrição de Avaliação do Intune, a conta com a qual criou a subscrição é de Administrador global.

## <a name="add-the-client-app-to-intune"></a>Adicionar a aplicação cliente ao Intune

É possível incluir uma aplicação para que o Intune possa gerir aspetos da mesma. 

Siga os seguintes passos para adicionar uma aplicação ao Intune:
1. Intune , selecione **Apps** > **Todas as aplicações** > **Adicionar**. [](https://aka.ms/intuneportal) 
2. Selecione o **Windows 10** na secção **Suite Office 365** do painel do **tipo Select.**
3. Clique em **Selecionar**. Os passos da **aplicação Add** são apresentados.
4. Confirme os detalhes predefinidos na página de informação da **Suite App.**
5. Clique em **Seguir** para exibir a página de suíte de **aplicação Configure.**
6. Ao lado do **Update Channel** selecione **Monthly** a partir da caixa de dropdown.
7. Confirme os restantes detalhes predefinidos na página de suite de aplicações ***Configure.**
8. Clique em **Seguir** para exibir a página **de tags scope.**
9. Clique em **Selecionar etiquetas** de âmbito para adicionar opcionalmente etiquetas de âmbito para a aplicação. Para mais informações, consulte [Utilize o controlo de acesso baseado em funções (RBAC) e as etiquetas](~/fundamentals/scope-tags.md)de âmbito para TI distribuídos .
10. Clique em **Avançar** para exibir a página **atribuições** .
11. Selecione as atribuições de grupo para a aplicação. Para mais informações, consulte [Adicionar grupos para organizar utilizadores e dispositivos](~/fundamentals/groups-add.md). 
12. Clique em **Seguir** para exibir a página **Review + criar.** Reveja os valores e configurações que inseriu para a aplicação.
13. Quando terminar, clique em **Criar** para adicionar a app ao Intune.

## <a name="assign-the-app-to-a-group"></a>Atribuir a aplicação a um grupo

Depois de adicionar uma aplicação ao Microsoft Intune, pode atribuí-la a grupos de utilizadores ou dispositivos.

> [!NOTE]
> Este quickstart baseia-se em quickstarts anteriores nesta série. Veja a secção [Pré-requisitos](quickstart-add-assign-app.md#prerequisites) deste guia de início rápido para obter mais informações.

Siga os seguintes passos para atribuir uma aplicação a um grupo:
1. Intune , selecione **Apps** > **Todas as aplicações.** [](https://aka.ms/intuneportal) 
2. Selecione a aplicação que pretende atribuir a um grupo.
3. Clique em **Atribuições** > **Adicionar grupo** para exibir o painel do **grupo Adicionar.**
4. Selecione **Disponível para dispositivos inscritos** na caixa pendente **Tipo de atribuição**. 
5. Clique em **Grupos Incluídos** > **Selecionar grupos para incluir** > **Técnicos de Teste da Contoso**.
6. Clique em **Selecionar** > **OK** > **OK** > **Guardar** para atribuir ao grupo.

Agora já atribuiu a aplicação ao grupo **Técnicos de Teste da Contoso**.

## <a name="install-the-app-on-the-enrolled-device"></a>Instalar a aplicação no dispositivo inscrito

Tem de instalar e utilizar a aplicação Portal da Empresa para instalar a aplicação **Tarefas da Contoso** disponibilizada pelo Intune. Siga os seguintes passos para verificar se a aplicação está disponível para o utilizador do dispositivo inscrito.

1. Inicie sessão no seu dispositivo inscrito com o Windows 10 Desktop.

    > [!IMPORTANT]
    > O dispositivo tem de estar [inscrito no Intune](../quickstart-enroll-windows-device.md). Além disso, tem de iniciar sessão no dispositivo com uma conta incluída no grupo ao qual atribuiu a aplicação.

2. A partir do menu **Iniciar**, abra a **Microsoft Store**. Em seguida, localize a aplicação **Portal da Empresa** e instale-a.
3. Inicie a aplicação **Portal da Empresa**.
4. Clique na aplicação que adicionou com o Intune. Neste guia de início rápido, adicionou a aplicação **Conjunto de Aplicações do Microsoft Office 365**.

    > [!NOTE]
    > Se não tiver atribuído com êxito nenhuma aplicação ao utilizador do Intune, verá a seguinte mensagem: *O seu administrador de TI não lhe disponibilizou nenhuma aplicação.*

5. Clique em **Instalar**.

Se as suas necessidades empresariais incluírem a atribuição da aplicação Portal da Empresa à sua força de trabalho, pode atribuir manualmente a aplicação Portal da Empresa do Windows 10 diretamente a partir do Intune. Para obter mais informações, veja [Adicionar manualmente a aplicação Portal da Empresa do Windows 10 através do Microsoft Intune](../company-portal-app.md).

## <a name="next-steps"></a>Próximos passos

Neste guia de início rápido, adicionou aplicações ao Intune, atribuiu as aplicações a um grupo e instalou as aplicações no dispositivo inscrito com o Windows 10 Desktop. Para obter mais informações sobre a gestão de aplicações no Intune, veja [O que é a gestão de aplicações do Microsoft Intune?](app-management.md)

Para seguir esta série de guias de início rápido do Intune, continue para o próximo guia de início rápido.

> [!div class="nextstepaction"]
> [Guia de Início Rápido: criar e atribuir uma política de proteção de aplicações](quickstart-create-assign-app-policy.md)
