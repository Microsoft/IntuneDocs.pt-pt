---
title: 'Guia de Início Rápido: adicionar e atribuir uma aplicação cliente'
titlesuffix: Microsoft Intune
description: Neste guia de início rápido, irá utilizar o Microsoft Intune para adicionar e atribuir uma aplicação cliente.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/09/2018
ms.topic: quickstart
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: dab6f5c8-1ebb-42c4-a7a7-7af001f94e15
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 6d0a7485aa25dee74bf54192fa931d081be81cd8
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/20/2018
ms.locfileid: "52184519"
---
# <a name="quickstart-add-and-assign-a-client-app"></a>Guia de Início Rápido: adicionar e atribuir uma aplicação cliente

Neste guia de início rápido, irá utilizar o Intune para adicionar e atribuir uma aplicação cliente à força de trabalho da sua empresa. Uma das prioridades de um administrador é garantir que os utilizadores finais têm acesso às aplicações que precisam para trabalhar. 

Se não tiver uma subscrição do Intune, [inscreva-se numa conta de avaliação gratuita](free-trial-sign-up.md).

## <a name="prerequisites"></a>Pré-requisitos

- Para concluir este guia de início rápido, tem de [criar um utilizador](quickstart-create-user.md), [criar um grupo](quickstart-create-group.md) e [inscrever um dispositivo](quickstart-setup-auto-enrollment.md).

## <a name="sign-in-to-intune"></a>Iniciar sessão no Intune

Inicie sessão no [Intune](https://aka.ms/intuneportal) enquanto [Administrador global ou um Administrador de Serviços do Intune](users-add.md#types-of-administrators). Se criou uma Subscrição de avaliação do Intune, a conta com a qual criou a subscrição é de Administrador global.

## <a name="add-the-client-app-to-intune"></a>Adicionar a aplicação cliente ao Intune

É possível incluir uma aplicação para que o Intune possa gerir aspetos da mesma. 

Siga os seguintes passos para adicionar uma aplicação ao Intune:

1. No [Intune](https://aka.ms/intuneportal), selecione **Aplicações do cliente** > **Aplicações** > **Adicionar**. 
2. Selecione **Windows 10** na secção **Office 365 Suite** da caixa pendente **Tipo de aplicação**.
3. Selecione **Configurar o Conjunto de Aplicações** para selecionar as aplicações do Office que serão atribuídas ao utilizador do Intune.
4. Clique em **OK** para aceitar as aplicações selecionadas por predefinição.
5. Selecione **Informações do Conjunto de Aplicações**.
6. Introduza **Conjunto de Aplicações do Microsoft Office 365** como **Nome do Conjunto de Aplicações**.
7. Introduza **O conjunto de Aplicações do Microsoft Office 365.** como **Descrição do Conjunto de Aplicações**.
8. Clique em **Sim** junto a **Apresentar como aplicação em destaque no Portal da Empresa**.
9. Clique em **OK**.

    ![Captura de ecrã a mostrar a adição de informações da aplicação](media/quickstart-add-assign-app/quickstart-add-assign-app-01.png)

8. Selecione **Definições do Conjunto de Aplicações**.
9. Na caixa pendente **Atualizar Canal**, selecione **Mensalmente**.
10. Clique em **OK** > **Adicionar**.

## <a name="assign-the-app-to-a-group"></a>Atribuir a aplicação a um grupo

Depois de adicionar uma aplicação ao Microsoft Intune, pode atribuí-la a grupos de utilizadores ou dispositivos.

> [!NOTE]
> Este guia de início rápido baseia-se em guias de início rápido anteriores nesta série. Veja a secção [Pré-requisitos](quickstart-add-assign-app.md#prerequisites) deste guia de início rápido para obter mais informações.

Siga os seguintes passos para atribuir uma aplicação a um grupo:
1. No [Intune](https://aka.ms/intuneportal), selecione **Aplicações do cliente** > **Aplicações**. 
2. Selecione a aplicação que pretende atribuir a um grupo.   
3. Clique em **Atribuições** > **Adicionar grupo** para apresentar o painel **Adicionar grupo**.
4. Selecione **Disponível para dispositivos inscritos** na caixa pendente **Tipo de atribuição**. 
5. Clique em **Grupos Incluídos** > **Selecionar grupos para incluir** > **Técnicos de Teste da Contoso**.
6. Clique em **Selecionar** > **OK** > **OK** > **Guardar** para atribuir ao grupo.

Agora já atribuiu a aplicação ao grupo **Técnicos de Teste da Contoso**.

## <a name="install-the-app-on-the-enrolled-device"></a>Instalar a aplicação no dispositivo inscrito

Tem de instalar e utilizar a aplicação Portal da Empresa para instalar a aplicação **Tarefas da Contoso** disponibilizada pelo Intune. Siga os seguintes passos para verificar se a aplicação está disponível para o utilizador do dispositivo inscrito.

1. Inicie sessão no seu dispositivo inscrito com o Windows 10 Desktop.

    > [!IMPORTANT]
    > O dispositivo tem de estar [inscrito no Intune](quickstart-enroll-windows-device.md). Além disso, tem de iniciar sessão no dispositivo com uma conta incluída no grupo ao qual atribuiu a aplicação.

2. A partir do menu **Iniciar**, abra a **Microsoft Store**. Em seguida, localize a aplicação **Portal da Empresa** e instale-a.
3. Inicie a aplicação **Portal da Empresa**.
4. Clique na aplicação que adicionou com o Intune. Neste guia de início rápido, adicionou a aplicação **Conjunto de Aplicações do Microsoft Office 365**.

    > [!NOTE]
    > Se não tiver atribuído com êxito nenhuma aplicação ao utilizador do Intune, verá a seguinte mensagem: *O seu administrador de TI não lhe disponibilizou nenhuma aplicação.*

5. Clique em **Instalar**.

Se as suas necessidades empresariais incluírem a atribuição da aplicação Portal da Empresa à sua força de trabalho, pode atribuir manualmente a aplicação Portal da Empresa do Windows 10 diretamente a partir do Intune. Para obter mais informações, veja [Adicionar manualmente a aplicação Portal da Empresa do Windows 10 através do Microsoft Intune](store-apps-company-portal-app.md).

## <a name="next-steps"></a>Passos Seguintes

Neste guia de início rápido, adicionou aplicações ao Intune, atribuiu as aplicações a um grupo e instalou as aplicações no dispositivo inscrito com o Windows 10 Desktop. Para obter mais informações sobre a gestão de aplicações no Intune, veja [O que é a gestão de aplicações do Microsoft Intune?](app-management.md)

Para seguir esta série de guias de início rápido do Intune, continue para o próximo guia de início rápido.

> [!div class="nextstepaction"]
> [Guia de Início Rápido: criar e atribuir uma política de proteção de aplicações](quickstart-create-assign-app-policy.md)
