---
title: Como administrar remotamente dispositivos Android com o TeamViewer
titleSuffix: Intune on Azure
description: Saiba como administrar remotamente dispositivos Android com o TeamViewer."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 05/24/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 72cdd888-efca-46e6-b2e7-fb9696bb2fba
ms.reviewer: davidra
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 15a005ae2b84c7bd4f913f892089965c10f3b23e
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/01/2017
---
# <a name="provide-remote-assistance-for-intune-managed-android-devices"></a>Fornecer assistência remota em dispositivos Android geridos no Intune

O Intune pode utilizar o software [TeamViewer](https://www.teamviewer.com), adquirido separadamente, para lhe permitir disponibilizar assistência remota aos seus utilizadores com dispositivos Android. Utilize as informações neste tópico para configurar as opções e começar a trabalhar.

## <a name="before-you-start"></a>Antes de começar

### <a name="required-permissions"></a>Permissões necessárias

Confirme que o utilizador do portal do Azure tem as seguintes permissões atribuídas como uma [função do Intune](https://docs.microsoft.com/intune-azure/access-control/role-based-access-control):
- Para permitir que o administrador modifique as definições do conector do TeamViewer, conceda a permissão **Atualizar Assistência Remota**.
- Para permitir que o administrador inicie as definições de uma nova assistência remota, conceda a permissão **Pedir Assistência Remota**. Os utilizadores com esta permissão podem pedir para iniciar uma sessão para qualquer utilizador. Tal não está limitado por qualquer âmbito de atribuição de funções do Intune. Os âmbitos de atribuição de funções do Intune não limitam os dispositivos ou os utilizadores para os quais os pedidos de Assistência Remota possam ser iniciados.

>[!NOTE]
>Ao ativar o TeamViewer, está a permitir que o TeamViewer para o Conector do Intune crie sessões do TeamViewer, leia os dados do Active Directory e guarde o token de acesso da conta do TeamViewer.

### <a name="configure-the-intune-teamviewer-connector"></a>Configurar o conector do TeamViewer no Intune

Antes de poder fornecer assistência remota a dispositivos Android, precisará de configurar o conector do TeamViewer no Intune utilizando os seguintes passos:


1. Inicie sessão no portal do Azure.
2. Escolha **Mais Serviços** > **Monitorização + Gestão** > **Intune**.
3. No painel **Intune**, escolha **Dispositivos**.
4. No painel **Dispositivos e grupos**, escolha **Configurar** > **Conector do TeamViewer**.
5. No painel **Conector do TeamViewer**, clique em **Ativar**, em seguida, veja e aceite o contrato de licença de serviço do TeamViewer.
6. Escolha **Iniciar sessão no TeamViewer e Autorizar**.
7. É aberta uma página da Web para o site do TeamViewer. Introduza as suas credenciais de licença do TeamViewer e, em seguida, clique em **Iniciar Sessão**.


## <a name="how-to-remotely-administer-an-android-device"></a>Como administrar remotamente um dispositivo Android

1. Inicie sessão no portal do Azure.
2. Escolha **Mais Serviços** > **Monitorização + Gestão** > **Intune**.
3. No painel **Intune**, escolha **Dispositivos**.
4. No painel **Dispositivos**, escolha **Gerir** > **Todos os dispositivos**.
5. Selecione o dispositivo que deseja administrar remotamente e, em seguida, no painel de propriedades do dispositivo, escolha **Mais** > **Nova Sessão de Assistência Remota**.
6. Quando o Intune estiver ligado ao serviço do TeamViewer, verá algumas informações sobre o dispositivo Android. Escolha **Ligar** para iniciar a sessão remota.

![Janelas do TeamViewer para Android](./media/android-teamviewer.png)

Na janela do TeamViewer, pode executar uma variedade de ações remotas no dispositivo Android, incluindo o controlo remoto do dispositivo. Para obter detalhes completos das ações que pode executar, veja a [documentação do TeamViewer](https://www.teamviewer.com/support/documents/).

Quando concluir, feche a janela do TeamViewer.

## <a name="end-user-notifications"></a>Notificações do utilizador final

Um utilizador final verá um sinalizador de notificação no ícone da aplicação Portal da Empresa no dispositivo e também uma notificação quando abrir a aplicação. Em seguida, pode aceitar o pedido de assistência remota.

