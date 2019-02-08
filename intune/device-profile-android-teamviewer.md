---
title: Administrar remotamente dispositivos no Microsoft Intune – Azure | Microsoft Docs
description: Veja as funções necessárias para utilizar o TeamViewer, como instalar o conector do TeamViewer e orientação passo a passo para administrar remotamente dispositivos com o Microsoft Intune no portal do Azure
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/05/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 72cdd888-efca-46e6-b2e7-fb9696bb2fba
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 33aa956696d9a7362fe50c5f7b46d9e0cf5bc1e7
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/07/2019
ms.locfileid: "55835680"
---
# <a name="use-teamviewer-to-remotely-administer-intune-devices"></a>Utilizar o TeamViewer para administrar remotamente dispositivos do Intune

Os dispositivos geridos pelo Intune podem ser administrados remotamente com o [TeamViewer](https://www.teamviewer.com). O TeamViewer é um programa de terceiros que pode comprar separadamente. Este tópico mostra-lhe como configurar o TeamViewer no Intune e como administrar remotamente um dispositivo. 

## <a name="prerequisites"></a>Pré-requisitos

- Utilize um dispositivo suportado. Os dispositivos Android, Windows, iOS e macOS geridos pelo Intune suportam a administração remota. O TeamViewer pode não suportar o Windows Holographic (HoloLens), Windows Team (Surface Hub) ou Windows 10 S. Para conhecer a suportabilidade e obter todas as atualizações, veja [TeamViewer](https://www.teamviewer.com).

- O administrador do Intune no portal do Azure tem de ter as seguintes [funções do Intune](role-based-access-control.md):  

    - **Atualizar assistência remota**: Permite que os administradores modifiquem as definições do conector de TeamViewer
    - **Pedir assistência remota**: Permite aos administradores iniciar uma nova sessão de assistência remota para qualquer utilizador. Os utilizadores com esta função não estão limitados pelas funções do Intune num âmbito. Além disso, os grupos de utilizadores ou dispositivos com uma função do Intune num âmbito também podem pedir assistência remota. 

- R [TeamViewer](https://www.teamviewer.com) conta com as credenciais de início de sessão. Apenas algumas licenças do TeamViewer deve dar suporte a integração com o Intune. Para as necessidades específicas do TeamViewer, consulte [parceiro de integração do TeamViewer: Microsoft Intune](https://www.teamviewer.com/integrations/microsoft-intune/).

Ao utilizar o TeamViewer, está a permitir que o Conector do TeamViewer para o Intune crie sessões do TeamViewer, leia os dados do Active Directory e guarde o token de acesso da conta do TeamViewer.

## <a name="configure-the-teamviewer-connector"></a>Configurar o conector do TeamViewer

Para fornecer assistência remota a dispositivos, configure o conector do TeamViewer no Intune através dos seguintes passos:

1. No [portal do Azure](https://portal.azure.com), selecione **Todos os Serviços** e procure **Microsoft Intune**.
2. No **Microsoft Intune**, selecione **Dispositivos** e, em seguida, selecione **Conector do TeamViewer**.
3. Selecione **Ligar** e, em seguida, aceite o contrato de licença.
4. Selecione **Iniciar sessão no TeamViewer para autorizar**.
5. É aberta uma página da Web para o site do TeamViewer. Introduza as suas credenciais de licença do TeamViewer e, em seguida, clique em **Iniciar Sessão**.

## <a name="remotely-administer-a-device"></a>Administrar remotamente um dispositivo

Após o conector estar configurado, estará pronto para administrar remotamente um dispositivo. Utilize os seguintes passos: 

1. No [portal do Azure](https://portal.azure.com), selecione **Todos os Serviços** e procure **Microsoft Intune**.
2. No **Microsoft Intune**, selecione **Dispositivos** e, em seguida, selecione **Todos os dispositivos**.
3. Na lista, selecione o dispositivo que pretende administrar remotamente. Nas propriedades do dispositivo, selecione **Nova Sessão de Assistência Remota**.
4. Quando o Intune estiver ligado ao serviço do TeamViewer, verá algumas informações sobre o dispositivo. Selecione **Ligar** para iniciar a sessão remota.

![Utilizar o TeamViewer para administrar remotamente dispositivos Android – exemplo](./media/android-teamviewer.png)

Quando inicia uma sessão remota, os utilizadores veem um sinalizador de notificação no ícone da aplicação Portal da empresa nos respetivos dispositivos. Também é apresentada uma notificação quando a aplicação abre. Os utilizadores, em seguida, podem aceitar o pedido de assistência remota.

> [!NOTE]
> Dispositivos Windows inscritos através de métodos "sem utilizador", como o DEM e WCD, não mostram a notificação do TeamViewer na aplicação Portal da empresa. Nestes cenários, é recomendado para utilizar o portal do TeamViewer para gerar a sessão.

No TeamViewer, pode realizar diversas ações no dispositivo, incluindo assumir o controlo do mesmo. Para obter detalhes completos do que pode fazer, veja [Orientação do TeamViewer](https://www.teamviewer.com/support/documents/).

Quando terminar, feche a janela do TeamViewer.
