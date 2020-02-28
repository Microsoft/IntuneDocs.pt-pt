---
title: Administrar remotamente dispositivos no Microsoft Intune – Azure | Microsoft Docs
description: Veja as funções necessárias para utilizar o TeamViewer, como instalar o conector do TeamViewer e orientação passo a passo para administrar remotamente dispositivos com o Microsoft Intune no portal do Azure
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/27/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 72cdd888-efca-46e6-b2e7-fb9696bb2fba
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: fede9e67e77804ca293bbe9889d5a6623e4ea90c
ms.sourcegitcommit: 045ca42cad6f86024af9a38a380535f42a6b4bef
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/28/2020
ms.locfileid: "77781126"
---
# <a name="use-teamviewer-to-remotely-administer-intune-devices"></a>Utilizar o TeamViewer para administrar remotamente dispositivos do Intune

Os dispositivos geridos pelo Intune podem ser administrados remotamente com o [TeamViewer](https://www.teamviewer.com). O TeamViewer é um programa de terceiros que pode comprar separadamente. Este tópico mostra-lhe como configurar o TeamViewer no Intune e como administrar remotamente um dispositivo. 

## <a name="prerequisites"></a>Pré-requisitos

- Utilize um dispositivo suportado. O Administrador de Dispositivos Android gerido sintonizado, o Perfil de Trabalho Android, o Windows, o iOS/iPadOS e os dispositivos macOS suportam a administração remota. O TeamViewer pode não suportar o Windows Holographic (HoloLens), Windows Team (Surface Hub) ou Windows 10 S. Para conhecer a suportabilidade e obter todas as atualizações, veja [TeamViewer](https://www.teamviewer.com).

> [!NOTE]
> Android Dedicado e Totalmente Gerido não são suportados.

- O administrador do Intune no portal do Azure tem de ter as seguintes [funções do Intune](../fundamentals/role-based-access-control.md):  

  - **Atualizar Assistência Remota**: permite que os administradores modifiquem as definições do conector do TeamViewer
  - **Pedir Assistência Remota**: permite que os administradores iniciem uma nova sessão de assistência remota para qualquer utilizador. Os utilizadores com esta função não estão limitados pelas funções do Intune num âmbito. Além disso, os grupos de utilizadores ou dispositivos com uma função do Intune num âmbito também podem pedir assistência remota. 

- Uma conta [TeamViewer](https://www.teamviewer.com) com as credenciais de inscrição. Apenas algumas licenças TeamViewer podem apoiar a integração com o Intune. Para obter necessidades específicas do TeamViewer, consulte [TeamViewer Integration Partner: Microsoft Intune](https://www.teamviewer.com/integrations/microsoft-intune/).

Ao utilizar o TeamViewer, está a permitir que o Conector do TeamViewer para o Intune crie sessões do TeamViewer, leia os dados do Active Directory e guarde o token de acesso da conta do TeamViewer.

## <a name="configure-the-teamviewer-connector"></a>Configurar o conector do TeamViewer

Para fornecer assistência remota a dispositivos, configure o conector do TeamViewer no Intune através dos seguintes passos:

1. Inscreva-se no [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selecione **a administração do Inquilino** > **Conectores e fichas** > **Conector TeamViewer**.
3. Selecione **Ligar** e, em seguida, aceite o contrato de licença.
4. Selecione **Iniciar sessão no TeamViewer para autorizar**.
5. É aberta uma página da Web para o site do TeamViewer. Introduza as suas credenciais de licença do TeamViewer e, em seguida, clique em **Iniciar Sessão**.

## <a name="remotely-administer-a-device"></a>Administrar remotamente um dispositivo

Após o conector estar configurado, estará pronto para administrar remotamente um dispositivo. Utilize os seguintes passos: 

1. No [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selecione **Dispositivos** e, em seguida, selecione **Todos os dispositivos**.
3. A partir da lista, selecione o dispositivo que pretende administrar remotamente > **...**  > Nova Sessão de **Assistência Remota.**
4. Quando o Intune estiver ligado ao serviço do TeamViewer, verá algumas informações sobre o dispositivo. Selecione **Ligar** para iniciar a sessão remota.

![Utilizar o TeamViewer para administrar remotamente dispositivos Android – exemplo](./media/teamviewer-support/android-teamviewer.png)

Quando inicia uma sessão remota, os utilizadores vêem uma bandeira de notificação no ícone da aplicação do Portal da Empresa no seu dispositivo. Uma notificação também aparece quando a aplicação abre. Os utilizadores podem então aceitar o pedido de assistência remota.

> [!NOTE]
> Os dispositivos Windows que estão matriculados utilizando métodos "sem uso", como DEM e WCD, não mostram a notificação do TeamViewer na aplicação Portal da Empresa. Nestes cenários, recomenda-se utilizar o portal TeamViewer para gerar a sessão.

No TeamViewer, pode realizar diversas ações no dispositivo, incluindo assumir o controlo do mesmo. Para obter detalhes completos do que pode fazer, veja [Orientação do TeamViewer](https://www.teamviewer.com/support/documents/).

Quando terminar, feche a janela do TeamViewer.
