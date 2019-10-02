---
title: Atualizar ou usar o modo S em dispositivos Windows 10-Microsoft Intune-Azure | Microsoft Docs
description: Use Microsoft Intune para atualizar dispositivos Windows 10 para uma edição diferente ou para o modo do comutador. Os administradores podem usar um perfil de configuração de dispositivo para atualizar o Windows 10 Professional para o Windows 10 Enterprise e desativar o modo S. Consulte os caminhos de atualização com suporte para Windows 10 pro, N Edition, educação, nuvem, Enterprise, Core, Holographic e Mobile.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ae8b6528-7979-47d8-abe0-58cea1905270
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: ad2977597ca9e5b6eef82fb3539917ea15ca2e31
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71730700"
---
# <a name="upgrade-windows-10-editions-or-switch-out-of-s-mode-on-devices-using-microsoft-intune"></a>Atualizar as edições do Windows 10 ou sair do modo S em dispositivos usando Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Como parte da sua solução de MDM (gerenciamento de dispositivo móvel), talvez você queira atualizar seus dispositivos Windows 10. Por exemplo, você deseja atualizar seus dispositivos Windows 10 Professional para o Windows 10 Enterprise. Ou, você deseja que o dispositivo mude para fora do modo S.

[Modo Windows 10 S](https://support.microsoft.com/help/4456067/windows-10-switch-out-of-s-mode) (abre outro site da Microsoft) foi projetado para segurança e desempenho. Você pode usar o Intune para desativar o modo S. Sair do modo S é definitivo. Depois de sair do modo S, não pode voltar para o modo Windows 10 S.

Veja algumas [perguntas frequentes](https://support.microsoft.com/help/4020089/windows-10-in-s-mode-faq) sobre o modo S.

Esta funcionalidade aplica-se a:

- Windows 10 e posterior
- Windows 10 1809 ou posterior para o modo S
- Windows Holographic for Business

Esses recursos estão disponíveis no Intune e podem ser configurados pelo administrador. O Intune usa "perfis de configuração" para criar e personalizar essas configurações para as necessidades da sua organização. Depois de adicionar esses recursos em um perfil, você pode enviar por Push ou implantar o perfil em dispositivos Windows 10 em sua organização. Quando você implanta o perfil, o Intune atualiza automaticamente os dispositivos ou opções fora do modo S.

Este artigo lista os caminhos de atualização com suporte e mostra como criar o perfil de configuração do dispositivo. Você também pode ver todas as configurações disponíveis de atualização e modo S para [Windows 10](edition-upgrade-windows-settings.md).

> [!NOTE]
> Se você remover a atribuição de política mais tarde, a versão do Windows no dispositivo não será revertida. O dispositivo continua a ser executado normalmente.

## <a name="prerequisites"></a>Pré-requisitos

Antes de atualizar os dispositivos, verifique se você tem os seguintes pré-requisitos:

- Uma chave de produto válida para instalar a versão atualizada do Windows em todos os dispositivos visados pela política (para edições do Windows 10 Desktop). Pode utilizar chaves MAK (Chaves de Ativação Múltipla) ou KMS (Servidor de Gestão de Chaves).
- Para as edições Windows 10 Mobile e Windows 10 Holographic, você pode usar um arquivo de licença da Microsoft. O arquivo de licença inclui as informações de licenciamento para instalar a edição atualizada em todos os dispositivos que você tem como destino com a política.
- Os dispositivos Windows 10 aos quais atribuir a política estão inscritos no Microsoft Intune. Não é possível utilizar a política de atualização de edição com PCs que executam o software de cliente de PCs do Intune.

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

<!--The following table provides information about the supported upgrade paths for Windows 10 editions in this policy:

![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)  (X) = not supported    
![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)    (green checkmark) = supported    

|Upgrade from edition\Upgrade to edition|Education|Education N|Pro Education|Pro Education N|Enterprise|Enterprise N|Professional|Professional N|Mobile Enterprise|Holographic for Business|
|--------|--------|--------|--------|--------|--------|--------|--------|--------|--------|--------|--------|
|Pro|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|
|Pro N|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|
|Pro Education|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|
|Pro Education N|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|
|Cloud|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|
|Cloud N|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|
|Enterprise|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|
|Enterprise N|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|
|Core|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|
|Core N|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|
|Mobile|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|
|Holographic|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png) -->

## <a name="create-the-profile"></a>Criar o perfil

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Selecione **Configuração do dispositivo** > **Perfis** > **Criar Perfil**.
3. Introduza as seguintes propriedades:

    - **Nome**: introduza um nome descritivo para o novo perfil. Por exemplo, insira algo como `Windows 10 edition upgrade profile` ou `Windows 10 switch off S mode`.
    - **Descrição**: introduza uma descrição para o perfil. Esta definição é opcional, mas recomendada.
    - **Plataforma**: Selecione a plataforma:  

        - **Windows 10 e posterior**

    - **Tipo de perfil**: Selecione **atualização de edição**.
    - **Definições**: Insira as configurações que você deseja configurar. Para obter uma lista de todas as configurações e o que elas fazem, consulte:

        - [Atualização do Windows 10 e modo S](edition-upgrade-windows-settings.md)
        - [Windows Holographic for Business](holographic-upgrade.md)

4. Selecione **OK** > **Criar** para guardar as alterações.

O perfil é criado e mostrado na lista. Certifique-se de [atribuir o perfil](device-profile-assign.md) e [monitorar seu status](device-profile-monitor.md).

## <a name="next-steps"></a>Passos seguintes

Depois que o perfil é criado, ele está pronto para ser atribuído. Em seguida, [atribua o perfil](device-profile-assign.md) e [monitorize o estado](device-profile-monitor.md).

Veja as configurações de atualização e modo S para dispositivos [Windows 10](edition-upgrade-windows-settings.md) e [Windows Holographic for Business](holographic-upgrade.md) .
