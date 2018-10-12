---
title: Atualizar ou utilizar o modo S em dispositivos com o Windows 10 no Microsoft Intune – Azure | Microsoft Docs
description: Crie um perfil de dispositivo no Microsoft Intune para atualizar dispositivos com o Windows 10 para edições diferentes. Por exemplo, pode atualizar o Windows 10 Professional para o Windows 10 Enterprise. Também pode ativar ou sair do modo S num dispositivo através do perfil de configuração. Consulte também os caminhos de atualização suportados para o Windows 10 Pro, N Edition, Education, Cloud, Enterprise, Core, Holographic e Mobile.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/11/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ae8b6528-7979-47d8-abe0-58cea1905270
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f0e4ba42559a068ebefb453aba18060803dc36e0
ms.sourcegitcommit: f3974c810e172f345853dacd7f2ca0abc11b1a5b
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/11/2018
ms.locfileid: "44389630"
---
# <a name="use-a-configuration-profile-to-upgrade-windows-10-or-switch-from-s-mode-in-intune"></a>Utilizar um perfil de configuração para atualizar o Windows 10 ou sair do modo S no Intune
[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Configure um perfil de atualização no Intune para atualizar automaticamente os dispositivos que executam a edição Windows 10 para uma edição diferente. Consulte também os caminhos de atualização suportados.

## <a name="before-you-begin"></a>Antes de começar
Antes de atualizar os dispositivos para a versão mais recente, precisa dos seguintes pré-requisitos:

- Uma chave de produto válida para instalar a versão atualizada do Windows em todos os dispositivos visados pela política (para edições do Windows 10 Desktop). Pode utilizar chaves MAK (Chaves de Ativação Múltipla) ou KMS (Servidor de Gestão de Chaves). Para as edições Windows 10 Mobile e Windows 10 Holographic, pode utilizar um ficheiro de licença da Microsoft que inclua as informações de licenciamento para instalar a versão atualizada do Windows em todos os dispositivos visados pela política.
- Os dispositivos com o Windows 10 aos quais atribuir a política estão inscritos no Microsoft Intune. Não é possível utilizar a política de atualização de edição com PCs que executam o software de cliente de PCs do Intune.

## <a name="supported-upgrade-paths"></a>Caminhos de atualização suportados
A seguinte tabela indica os caminhos de atualização suportados para o perfil de atualização de edição do Windows 10.

| Atualizar a partir do | Atualizar para o |
|---|---|
| Windows 10 Pro | Windows 10 Education <br/>Windows 10 Enterprise <br/>Windows 10 Pro Education |
| Edição Windows 10 Pro N | Edição Windows 10 Education N <br/>Edição Windows 10 Enterprise N <br/>Edição Windows 10 Pro Education N | 
| Windows 10 Pro Education | Windows 10 Education | 
| Edição Windows 10 Pro Education N | Edição Windows 10 Education N |
| Windows 10 Cloud | Windows 10 Education <br/>Windows 10 Enterprise <br/>Windows 10 Pro <br/>Windows 10 Pro Education | 
| Edição Windows 10 Cloud N | Edição Windows 10 Education N <br/>Edição Windows 10 Enterprise N <br/>Edição Windows 10 Pro N <br/>Edição Windows 10 Pro Education N | 
| Windows 10 Enterprise | Windows 10 Education | 
| Edição Windows 10 Enterprise N | Edição Windows 10 Education N | 
| Windows 10 Core | Windows 10 Education <br/>Windows 10 Enterprise <br/>Windows 10 Pro Education | 
| Edição Windows 10 Core N | Edição Windows 10 Education N <br/>Edição Windows 10 Enterprise N <br/>Edição Windows 10 Pro Education N | 
| Windows 10 Holographic | Windows 10 Holographic for Business |
| Windows 10 Mobile | Windows 10 Mobile Enterprise |


<!-- Testing a new table on 3/5/18 

The following lists provide the supported upgrade paths for the Windows 10 edition upgrade profile. The Windows 10 edition to upgrade to is in bold followed by the list of supported editions that you can upgrade from:

**Windows 10 Education**
- Windows 10 Pro
- Windows 10 Pro Education
- Windows 10 Cloud
- Windows 10 Enterprise
- Windows 10 Core
    
**Windows 10 Education N edition**    
- Windows 10 Pro N edition
- Windows 10 Pro Education N edition
- Windows 10 Cloud N edition
- Windows 10 Enterprise N edition
- Windows 10 Core N edition
    
**Windows 10 Enterprise**
- Windows 10 Pro
- Windows 10 Cloud
- Windows 10 Core
    
**Windows 10 Enterprise N edition**
- Windows 10 Pro N edition
- Windows 10 Cloud N edition
- Windows 10 Core N edition
    
**Windows 10 Pro**
- Windows 10 Cloud
    
**Windows 10 Pro N edition**
- Windows 10 Cloud N edition
    
**Windows 10 Pro Education**
- Windows 10 Pro
- Windows 10 Cloud
- Windows 10 Core
    
**Windows 10 Pro Education N edition**
- Windows 10 Pro N edition
- Windows 10 Cloud N edition
- Windows 10 Core N edition

**Windows 10 Holographic for Business**
- Windows 10 Holographic

**Windows 10 Mobile Enterprise**
- Windows 10 Mobile -->

<!--The following table provides information about the supported upgrade paths for Windows 10 editions in this policy:

![supported](./media/check_grn.png)  (X) = not supported    
![unsupported](./media/x_blk.png)    (green checkmark) = supported    

|Upgrade from edition\Upgrade to edition|Education|Education N|Pro Education|Pro Education N|Enterprise|Enterprise N|Professional|Professional N|Mobile Enterprise|Holographic for Business|
|--------|--------|--------|--------|--------|--------|--------|--------|--------|--------|--------|--------|
|Pro|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Pro N|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Pro Education|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Pro Education N|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Cloud|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Cloud N|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Enterprise|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Enterprise N|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Core|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)   |![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Core N|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Mobile|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|
|Holographic|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png) -->

## <a name="upgrade-the-edition"></a>Atualizar a edição

1. No [portal do Azure](https://portal.azure.com), selecione **Todos os serviços**, filtre o **Intune** e selecione **Microsoft Intune**.
2. Selecione **Configuração do dispositivo** > **Perfis** > **Criar Perfil**.
3. Introduza um **Nome** e uma **Descrição** para o perfil. Por exemplo, introduza algo como `Windows 10 edition upgrade`
4. Em **Plataforma**, selecione **Windows 10 e versões posteriores**.
5. Em **Tipo de perfil**, selecione **Atualização da edição**.
6. Nas propriedades **Atualização da Edição**, introduza as seguintes definições:

   - **Edição a atualizar**: selecione a edição Windows 10 para a qual está a atualizar. Os dispositivos visados por esta política são atualizados para a edição que escolher.
   - **Chave de Produto**: introduza a chave de produto que recebeu da Microsoft. Depois de criar a política que contém a chave de produto, a chave não pode ser atualizada e é ocultada por motivos de segurança. Para alterar a chave de produto, introduza novamente a chave completa.
   - **Ficheiro de Licença**: para **Windows 10 Holographic for Business** ou **Edição Windows 10 Mobile**, selecione **Procurar** para selecionar o ficheiro de licença que recebeu da Microsoft. Este ficheiro de licença inclui as informações de licença das edições para as quais está a atualizar os dispositivos visados.

7. Selecione **OK** para guardar as alterações. Selecione **Criar** para criar o perfil.

## <a name="switch-out-of-s-mode"></a>Sair do modo S

O [modo S do Windows 10](https://support.microsoft.com/help/4456067/windows-10-switch-out-of-s-mode) foi concebido para segurança e desempenho. Se os seus dispositivos apenas executarem aplicações da Microsoft Store, pode utilizar o modo S para ajudar a mantê-los seguros. Se os seus dispositivos necessitarem de aplicações que não estão disponíveis na Microsoft Store, saia do modo S. Sair do modo S é definitivo. Depois de sair do modo S, não pode voltar para o modo Windows 10 S.

Os passos seguintes mostram como criar um perfil que controla o modo S nos dispositivos Windows 10 (1809 ou posterior).

1. No [portal do Azure](https://portal.azure.com), selecione **Todos os serviços**, filtre o **Intune** e selecione **Microsoft Intune**.
2. Selecione **Configuração do dispositivo** > **Perfis** > **Criar Perfil**.
3. Introduza um **Nome** e uma **Descrição** para o perfil. Por exemplo, introduza algo como `Windows 10 switch off S mode`
4. Em **Plataforma**, selecione **Windows 10 e versões posteriores**.
5. Em **Tipo de perfil**, selecione **Atualização da edição**.
6. Selecione **Alteração de modo (apenas no Windows Insider)** e defina a propriedade **Sair do modo S**. As opções são:

    - **Nenhuma configuração**: um dispositivo no modo S permanece no modo S. Um utilizador final pode retirar o dispositivo do modo S.
    - **Manter no modo S**: não permite ao utilizador final retirar o dispositivo do modo S.
    - **Alterar**: retira o dispositivo do modo S.

7. Selecione **OK** para guardar as alterações. Selecione **Criar** para criar o perfil.

O perfil será criado e apresentado nos perfis.

## <a name="next-steps"></a>Próximos passos

[Atribua este perfil](device-profile-assign.md) aos seus grupos.

>[!NOTE]
>Se remover a atribuição de políticas mais tarde, a versão do Windows no dispositivo não será revertida e continuará a funcionar normalmente.
