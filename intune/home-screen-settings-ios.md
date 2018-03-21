---
title: "Definições de esquema do ecrã principal do Microsoft Intune para dispositivos iOS"
titlesuffix: Azure portal
description: "Saiba quais são as definições que pode utilizar para personalizar o ecrã principal e a dock em dispositivos iOS."
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 03/02/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 88be142c98d7b89720d245c738a45a26ac825395
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/08/2018
---
# <a name="microsoft-intune-home-screen-layout-settings-for-devices-running-ios"></a>Definições de esquema do ecrã principal do Microsoft Intune para dispositivos iOS

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Utilize estas definições para configurar as pastas e o esquema de aplicações na dock e no ecrã principal dos dispositivos iOS.

Os dispositivos iOS com um perfil atribuído têm de estar no modo supervisionado e a executar o iOS 9.3 ou posterior.

1. A partir do [Intune no Portal do Azure](https://portal.azure.com), navegue para [**Funcionalidades do dispositivo** na área de configuração do dispositivo](device-features-configure.md).
2. No painel **Funcionalidades do dispositivo**, selecione **Esquema de Ecrã Principal (apenas supervisionado)**.
3. No painel **Esquema de Ecrã Principal (apenas supervisionado)**, selecione se quer configurar os esquemas da **Dock** ou das **Páginas**.

## <a name="add-items-to-the-dock"></a>Adicionar itens à dock

No painel **Dock**, pode adicionar até seis itens ou pastas à dock do ecrã iOS. No entanto, existem vários dispositivos que suportam menos itens. Por exemplo, os dispositivos iPhone suportam até quatro itens. Neste caso, apenas os primeiros quatro itens que configurou serão apresentados no dispositivo.

1. Escolha **Adicionar** para adicionar um item à dock.
2. No painel **Adicionar Linha**, selecione se quer adicionar uma **Aplicação** ou **Pasta**.
3. Utilize as informações contidas neste tópico para configurar as aplicações e pastas que pretende que sejam apresentadas na dock.
4. Continue a adicionar itens. Quando tiver terminado, clique em **OK** em cada painel até regressar ao painel **Criar Perfil**. Selecione **Criar**.

>[!TIP]
> Pode arrastar e largar itens em quaisquer listas de páginas e Ecrãs principais para os reordenar.

### <a name="example"></a>Exemplo

Neste exemplo, configurou o ecrã da dock para mostrar apenas as aplicações Safari, Correio e Bolsa. Na imagem seguinte, a aplicação Correio está selecionada para mostrar as suas propriedades:

![Exemplo de definições da dock do iOS](./media/FfFiUcP.png)

Ao atribuir uma política a um iPhone, criará uma dock com aspeto semelhante à seguinte captura de ecrã:

![Exemplo de esquema da dock do iOS no iPhone](./media/bAgCe8F.png)

## <a name="add-home-screen-pages"></a>Adicionar páginas ao Ecrã principal

Adicione as páginas que pretende que apareçam no ecrã principal e as aplicações apresentadas em cada página. As aplicações que adicionar a uma página são dispostas da esquerda para a direita, pela ordem em que estão especificadas na lista. Se adicionar mais aplicações do que aquelas que cabem numa página, estas serão movidas para a página seguinte.

1. No painel **Páginas**, selecione **Adicionar**.
2. No painel **Adicionar Linha**, introduza um **Nome da página**. Este nome é utilizado para sua referência no portal do Azure e *não é apresentado* no dispositivo iOS.
3. Escolha **Adicionar** e, em seguida, escolha se pretende adicionar uma **Aplicação** ou uma **Pasta** à página.
4. Configure as aplicações e pastas que pretende que sejam apresentadas na página com as informações contidas neste tópico.

### <a name="example"></a>Exemplo

Neste exemplo, configurou uma nova página com o nome **Contoso**. A página mostra apenas as aplicações Encontrar Amigos e Definições. Na imagem seguinte, a aplicação Definições está selecionada para mostrar as suas propriedades:

![Exemplo de definições de Ecrã principal do iOS](./media/Jc2OxyX.png)

Ao atribuir a política a um iPhone, criará uma página com um aspeto semelhante à seguinte captura de ecrã:

![Dispositivo iOS com o ecrã principal modificado](./media/Bd37PHa.png)

## <a name="how-to-add-an-app-to-the-list"></a>Como adicionar uma aplicação à lista

1. Introduza o **Nome da Aplicação**. Este nome é utilizado para sua referência no portal do Azure e *não é apresentado* no dispositivo iOS.
2. Introduza o **ID do Pacote de Aplicações** da aplicação que pretende apresentar. Para obter ajuda, veja **Referência de ID do pacote para aplicações iOS incorporadas** mais adiante neste tópico.
3. Clique em **OK** e continue a adicionar itens, até um máximo de **6** para a dock do dispositivo, e **60** para uma página do dispositivo.
4. Quando concluir o procedimento, clique em **OK**.

## <a name="how-to-add-a-folder-to-the-list"></a>Como adicionar uma pasta à lista

As aplicações que adicionar a uma página numa pasta são dispostas da esquerda para a direita, pela ordem em que estão especificadas na lista. Se adicionar mais aplicações do que aquelas que cabem numa página, estas serão movidas para a página seguinte.

1. Introduza o **Nome da pasta**. Este nome é apresentado aos utilizadores no respetivo dispositivo.
2. Escolha **Adicionar** para criar uma página na pasta. Pode adicionar até 20 páginas.
3. No painel **Adicionar Linha**, introduza um nome para a página. Este nome é utilizado para sua referência no portal do Azure e *não é apresentado* no dispositivo iOS.
3. Introduza o **Nome da Aplicação**. Este nome é utilizado para sua referência no portal do Azure e *não é apresentado* no dispositivo iOS.
2. Introduza o **ID do Pacote de Aplicações** da aplicação que pretende apresentar. Para obter ajuda , veja **Como adicionar uma aplicação à lista**.
3. Selecione **Adicionar**. Pode adicionar até 60 itens.
4. Quando concluir o procedimento, clique em **OK**.


## <a name="bundle-id-reference-for-built-in-ios-apps"></a>Referência de ID do pacote para aplicações iOS incorporadas

Esta lista mostra o ID do pacote de algumas aplicações iOS comuns incorporadas. Para localizar o ID do pacote de outras aplicações, contacte o fabricante de software.

|||
|-|-|
|Nome da aplicação|ID do Pacote|
|App Store|com.apple.AppStore|
|Calculadora|com.apple.calculator|
|Calendário|com.apple.mobilecal|
|Câmara|com.apple.camera|
|Relógio|com.apple.mobiletimer|
|Bússola|com.apple.compass|
|Contactos|com.apple.MobileAddressBook|
|FaceTime|com.apple.facetime|
|Encontrar Amigos|com.apple.mobileme.fmf1|
|Localizar iPhone|com.apple.mobileme.fmip1|
|Centro de Jogos|com.apple.gamecenter|
|GarageBand|com.apple.mobilegarageband|
|Estado de Funcionamento|com.apple.Health|
|iBooks|com.apple.iBooks|
|iTunes Store|com.apple.MobileStore|
|iTunes U|com.apple.itunesu|
|Keynote|com.apple.Keynote|
|Correio|com.apple.mobilemail|
|Mapas|com.apple.Maps|
|Mensagens|com.apple.MobileSMS|
|Música|com.apple.Music|
|Notícias|com.apple.news|
|Notas|com.apple.mobilenotes|
|Números|com.apple.Numbers|
|Páginas|com.apple.Pages|
|Photo Booth|com.apple.Photo-Booth|
|Fotografias|com.apple.mobileslideshow|
|Podcasts|com.apple.podcasts|
|Lembretes|com.apple.reminders|
|Safari|com.apple.mobilesafari|
|Definições|com.apple.Preferences|
|Bolsa|com.apple.stocks|
|Sugestões|com.apple.tips|
|Vídeos|com.apple.videos|
|VoiceMemos|com.apple.VoiceMemos|
|Wallet|com.apple.Passbook|
|Watch|com.apple.Bridge|
|Meteorologia|com.apple.weather|


## <a name="next-steps"></a>Próximos passos

Agora pode atribuir o perfil do dispositivo aos grupos que selecionar. Para obter detalhes, veja [Como atribuir perfis de dispositivo](device-profile-assign.md).
