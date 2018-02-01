---
title: Como administrar remotamente dispositivos com o TeamViewer
titlesuffix: Azure portal
description: Saiba como administrar remotamente dispositivos com o TeamViewer.
keywords: 
author: arob98
ms.author: angrobe
manager: dougeby
ms.date: 12/14/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 72cdd888-efca-46e6-b2e7-fb9696bb2fba
ms.reviewer: davidra
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 476480ce3957ef2d411b37a0a078707c721fd2e6
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/25/2018
---
# <a name="provide-remote-assistance-for-intune-managed-devices"></a>Fornecer assistência remota em dispositivos geridos no Intune

O Intune pode utilizar o software [TeamViewer](https://www.teamviewer.com) (adquirido separadamente) para lhe permitir disponibilizar assistência remota a utilizadores de dispositivos que gere. Utilize as informações neste tópico para começar.

## <a name="before-you-start"></a>Antes de começar

### <a name="supported-devices"></a>Dispositivos suportados

Os dispositivos Android e Windows geridos pelo Intune suportam a administração remota.

>[!NOTE]
>O Windows Holographic (HoloLens), o Windows Team (Surface Hub) e o Windows 10 S não são suportados pelo software TeamViewer. Ainda precisa de gerir dispositivos através do [cliente de PC](/intune-classic/deploy-use/pc-management-comparison?toc=/intune/toc.json) no portal clássico do Intune.



### <a name="required-permissions"></a>Permissões necessárias

Confirme que o utilizador do portal do Azure tem as seguintes permissões atribuídas como uma [função do Intune](https://docs.microsoft.com/intune-azure/access-control/role-based-access-control):
- Para permitir que o administrador modifique as definições do conector do TeamViewer, conceda a permissão **Atualizar Assistência Remota**.
- Para permitir que o administrador inicie um novo pedido de assistência remota, conceda a permissão **Pedir Assistência Remota**. Os utilizadores com a permissão **Pedir Assistência Remota** podem pedir para iniciar sessão para qualquer utilizador. Não estão limitadas por âmbitos de funções do Intune. Os âmbitos de atribuição de funções do Intune não limitam os dispositivos ou os utilizadores para os quais os pedidos de Assistência Remota possam ser iniciados.

>[!NOTE]
>Ao ativar o TeamViewer, está a permitir que o TeamViewer para o Conector do Intune crie sessões do TeamViewer, leia os dados do Active Directory e guarde o token de acesso da conta do TeamViewer.

### <a name="configure-the-intune-teamviewer-connector"></a>Configurar o conector do TeamViewer no Intune

Antes de poder fornecer assistência remota a dispositivos, tem de configurar o conector do TeamViewer no Intune através dos seguintes passos:


1. Inicie sessão no portal do Azure.
2. Escolha **Mais Serviços** > **Monitorização + Gestão** > **Intune**.
3. No painel **Intune**, escolha **Dispositivos**.
4. No painel **Dispositivos e grupos**, escolha **Configurar** > **Conector do TeamViewer**.
5. No painel **Conector do TeamViewer**, clique em **Ativar**, em seguida, veja e aceite o contrato de licença de serviço do TeamViewer.
6. Escolha **Iniciar sessão no TeamViewer e Autorizar**.
7. É aberta uma página da Web para o site do TeamViewer. Introduza as suas credenciais de licença do TeamViewer e, em seguida, clique em **Iniciar Sessão**.


## <a name="how-to-remotely-administer-a-device"></a>Como administrar remotamente um dispositivo

1. Inicie sessão no portal do Azure.
2. Escolha **Mais Serviços** > **Monitorização + Gestão** > **Intune**.
3. No painel **Intune**, escolha **Dispositivos**.
4. No painel **Dispositivos**, escolha **Gerir** > **Todos os dispositivos**.
5. Selecione o dispositivo que deseja administrar remotamente e, em seguida, no painel de propriedades do dispositivo, escolha **Mais** > **Nova Sessão de Assistência Remota**.
6. Quando o Intune estiver ligado ao serviço do TeamViewer, verá algumas informações sobre o dispositivo. Escolha **Ligar** para iniciar a sessão remota.

![Exemplo do TeamViewer para Android](./media/android-teamviewer.png)

Na janela do TeamViewer, pode executar uma variedade de ações remotas no dispositivo, incluindo o controlo remoto do dispositivo. Para obter detalhes completos das ações que pode executar, veja a [documentação do TeamViewer](https://www.teamviewer.com/support/documents/).

Quando terminar, feche a janela do TeamViewer.

## <a name="next-steps"></a>Próximos passos

Um utilizador final verá um sinalizador de notificação no ícone da aplicação Portal da Empresa no respetivo dispositivo e uma notificação ao abrir a aplicação. Em seguida, pode aceitar o pedido de assistência remota.
