---
title: "Utilizar políticas de configuração da aplicação Intune para Android for Work"
titleSuffix: Intune on Azure
description: "Saiba como utilizar políticas de configuração de aplicação para disponibilizar dados de configuração a uma aplicação Android for Work quando é executada.\""
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 06/05/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d0b6f3fe-2bd4-4518-a6fe-b9fd115ed5e0
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f9ea697cafa0f277c176e55443250d32ca378dbb
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/01/2017
---
# <a name="how-to-use-microsoft-intune-app-configuration-policies-for-android-for-work"></a>Como utilizar as políticas de configuração de aplicações do Microsoft Intune para Android for Work

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Utilize políticas de configuração de aplicações no Microsoft Intune para disponibilizar definições que poderão estar disponíveis quando os utilizadores executarem uma aplicação do Android for Work. Nem todas as aplicações suportam a configuração de aplicação. Verifique junto do programador da aplicação para ver se este criou ou não a sua aplicação para suportar políticas de configuração de aplicações.

As políticas de configuração de aplicações podem ajudá-lo a pré-configurar as definições da aplicação disponíveis para os utilizadores antes de estes executarem a aplicação. Algumas aplicações Android suportam opções de configurações geridas que pode configurar na consola do Intune com o [estruturador de configuração](#use-configuration-designer). Algumas definições de configuração em aplicações (tais como aquelas com tipos de Pacote) não podem ser configuradas com o estruturador de configuração.  Precisará de utilizar o [editor de JSON](#use-json-editor) para esses valores.   As definições são fornecidas para aplicações automaticamente quando a aplicação é instalada.

Não atribua estas políticas diretamente a utilizadores nem a dispositivos. Em alternativa, associe uma política à aplicação e, em seguida, atribua a aplicação. As definições de política são utilizadas quando a aplicação as verificar (normalmente, a primeira vez for executada).

## <a name="use-configuration-designer"></a>Utilizar o estruturador de configuração

1. No portal do Intune, escolha **Aplicações móveis**. Em **Gerir**, escolha **Políticas de configuração de aplicações** e, em seguida, clique em **Adicionar**.
2. Defina os seguintes detalhes:
    - **Nome** – O nome do perfil que será apresentado na consola do Intune
    - **Descrição** – A descrição do perfil que será apresentada na consola do Intune
    - **Plataforma** – Selecione **Android**
    - O **Tipo de inscrição do dispositivo** - **Inscrito com o Intune** encontra-se pré-selecionado.
3. Selecione **Aplicação Associada** para escolher a aplicação para a qual pretende definir uma política de configuração.  Selecionar na lista de aplicações Android for Work que aprovou e sincronizou com o Intune
4. Selecione **Definições de configuração**.
5. Para o **Formato das definições de configuração**, selecione **Utilizar estruturador de configuração**.
6. Selecione **Adicionar**. É apresentada uma lista das definições de configuração disponíveis. A lista inclui:
    - **Chaves de configuração** – Nome da definição.
    - **Tipo de valor** – A definição que pode ser configurada, por exemplo, **Booleano** ou **Cadeia de caracteres**.
    - **Descrição** – Uma descrição da definição de configuração.
7. Selecione as caixas de seleção das definições que pretende configurar com este perfil e, em seguida, clique em **OK**.
8. É apresentada uma lista das definições selecionadas com o **Valor de configuração** disponível. Especifique um valor para cada definição e, em seguida, clique em **OK**.

## <a name="use-json-editor"></a>Utilizar o editor de JSON

1. No portal do Intune, escolha **Aplicações móveis**. Em **Gerir**, escolha **Políticas de configuração de aplicações** e, em seguida, clique em **Adicionar**.
2. Defina os seguintes detalhes:
    - **Nome** – O nome do perfil que será apresentado na consola do Intune
    - **Descrição** – A descrição do perfil que será apresentada na consola do Intune
    - **Plataforma** – Selecione **Android**
    - O **Tipo de inscrição do dispositivo** - **Inscrito com o Intune** encontra-se pré-selecionado.
3. Selecione **Aplicação Associada** para escolher a aplicação para a qual pretende definir uma política de configuração.  Selecione na lista de aplicações Android for Work que aprovou e sincronizou com o Intune.
5. Selecione **Definições de Configuração**.
6. Para o **Formato das definições de configuração**, selecione **Entrar no editor de JSON**.
7. No editor, pode definir valores JSON para as definições de configuração. Pode escolher **Transferir modelo JSON** para transferir um ficheiro de exemplo que pode configurar.
8. Quando concluir, escolha **OK** e, em seguida, clique em **Adicionar**.

A política será criada e é apresentada no painel da lista de políticas.

Em seguida, continue a [atribuir](apps-deploy.md) e [monitorizar](apps-monitor.md) a aplicação como é habitual.

Quando a aplicação atribuída for executada num dispositivo, será executada com as definições que configurou na política de configuração de aplicação.

## <a name="preconfigure-permissions-grant-state-for-apps"></a>Pré-configurar o estado de concessão de permissões para aplicações

Também pode pré-configurar uma permissão para que as aplicações acedam às funcionalidades do dispositivo Android. Por predefinição, as aplicações Android que requerem permissões de dispositivos, tal como o acesso à localização ou à câmara do dispositivo, solicitam aos utilizadores que aceitem ou recusem as permissões. Por exemplo, se uma aplicação utilizar o microfone do dispositivo, o utilizador final será solicitado a conceder permissão à aplicação para utilizar o microfone.

1. No portal do Intune, escolha **Aplicações móveis**. Em **Gerir**, escolha **Políticas de configuração de aplicações** e, em seguida, clique em **Adicionar**.
2. Defina os seguintes detalhes:
    - **Nome** – O nome do perfil que será apresentado na consola do Intune
    - **Descrição** – A descrição do perfil que será apresentada na consola do Intune
    - **Plataforma** – Selecione **Android**
    - O **Tipo de inscrição do dispositivo** - **Inscrito com o Intune** encontra-se pré-selecionado.
3. Selecione **Aplicação Associada** para escolher a aplicação para a qual pretende definir uma política de configuração.  Selecione na lista de aplicações Android for Work que aprovou e sincronizou com o Intune.
5. Selecione **Permissões** e, em seguida, escolha **Adicionar**.
6. Selecione na lista de permissões de aplicações disponíveis e, em seguida, escolha **OK**.
7. Selecione uma opção para cada permissão a conceder com esta política:
    - **Pedido** – Pedir ao utilizador para aceitar ou recusar.
    - **Conceder automaticamente** – Aprovar automaticamente sem notificar o utilizador.
    - **Recusar automaticamente** – Recusar automaticamente sem notificar o utilizador.
8. Para atribuir a política de configuração de aplicações, selecione a política de configuração de aplicações, **Atribuição** e, em seguida, **Selecionar grupos**.
9. Selecione os grupos de utilizadores a atribuir e, em seguida, escolha **Selecionar**.
10. Escolha **Guardar** para atribuir a política.
