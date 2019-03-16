---
title: Atualizar ou utilizar o modo de S em dispositivos Windows 10 – Microsoft Intune – Azure | Documentos da Microsoft
description: Utilizar o Microsoft Intune para atualizar dispositivos Windows 10 para uma edição diferente ou ativar o modo de S. Os administradores podem utilizar um perfil de configuração do dispositivo para atualizar o Windows 10 Professional para Windows 10 Enterprise e ativar ou alternar do modo de S. Consulte os caminhos de atualização suportados para o Windows 10 Pro, edição N, Education, na Cloud, Enterprise, principal, Holographic e Mobile.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/22/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ae8b6528-7979-47d8-abe0-58cea1905270
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5b206cfca048416b1e859e9230f037e1158d46ec
ms.sourcegitcommit: c4258bb5824daf3f7e0ac3bb8afc539bde4d95da
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/16/2019
ms.locfileid: "57991096"
---
# <a name="upgrade-windows-10-editions-or-enable-s-mode-on-devices-using-microsoft-intune"></a>Atualizar as edições do Windows 10 ou ativar o modo de S em dispositivos com o Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Como parte da sua solução de gestão (MDM) de dispositivos móveis, pode querer atualizar os dispositivos Windows 10. Por exemplo, quiser atualizar os seus dispositivos Windows 10 Professional para Windows 10 Enterprise. Ou, se pretender ativar S mobile, para que dispositivos executam apenas para aplicações da Microsoft Store.

O [modo S do Windows 10](https://support.microsoft.com/help/4456067/windows-10-switch-out-of-s-mode) foi concebido para segurança e desempenho. Se os seus dispositivos apenas executarem aplicações da Microsoft Store, pode utilizar o modo S para ajudar a mantê-los seguros. Se os seus dispositivos utilizar aplicações que não estão disponíveis em que a Microsoft Store, em seguida, alternar do modo de S. Sair do modo S é definitivo. Depois de sair do modo S, não pode voltar para o modo Windows 10 S.

Esta funcionalidade aplica-se a:

- Windows 10 e posterior
- Windows 10 1809 ou posterior para o modo de S
- Windows Holographic for Business

Estas funcionalidades estão disponíveis no Intune e são configuráveis pelo administrador. O Intune utiliza "perfis de configuração" para criar e personalizar estas definições para as necessidades da sua organização. Depois de adicionar esses recursos num perfil, pode, em seguida, enviar por push ou implementar o perfil para dispositivos Windows 10 na sua organização. Quando implementa o perfil, o Intune é automaticamente atualiza os dispositivos ou permite o modo de S.

Este artigo apresenta uma lista de caminhos de atualização e mostra-lhe como criar o perfil de configuração do dispositivo. Também pode ver todas a atualização disponível e definições do modo de S para [Windows 10](edition-upgrade-windows-settings.md).

> [!NOTE]
> Se remover a atribuição de política mais tarde, a versão do Windows no dispositivo não é revertida. O dispositivo continua a ser executados normalmente.

## <a name="prerequisites"></a>Pré-requisitos

Antes de atualizar dispositivos, certifique-se de que tem os seguintes pré-requisitos:

- Uma chave de produto válida para instalar a versão atualizada do Windows em todos os dispositivos visados pela política (para edições do Windows 10 Desktop). Pode utilizar chaves MAK (Chaves de Ativação Múltipla) ou KMS (Servidor de Gestão de Chaves).
- Para as edições do Windows 10 Mobile e Windows 10 Holographic, pode utilizar um ficheiro de licença da Microsoft. O ficheiro de licença inclui as informações de licenciamento para instalar a edição atualizada em todos os dispositivos visados com a política.
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

## <a name="create-the-profile"></a>Criar o perfil

1. Na [portal do Azure](https://portal.azure.com), selecione **todos os serviços** > Filtrar **Intune** > selecione **Intune**.
2. Selecione **Configuração do dispositivo** > **Perfis** > **Criar Perfil**.
3. Introduza as seguintes propriedades:

    - **Nome**: Introduza um nome descritivo para o novo perfil. Por exemplo, introduza semelhante `Windows 10 edition upgrade profile` ou `Windows 10 switch off S mode`.
    - **Descrição**: Introduza uma descrição para o perfil. Esta definição é opcional, mas recomendada.
    - **Plataforma**: Selecione a plataforma:  

        - **Windows 10 e posterior**

    - **Tipo de perfil**: Selecione **atualização de edição**.
    - **Definições**: Introduza as definições que pretende configurar. Para obter uma lista de todas as definições e o que fazer, consulte:

        - [Atualização do Windows 10 e o modo de S](edition-upgrade-windows-settings.md)
        - [Windows Holographic for Business](holographic-upgrade.md)

4. Selecione **OK** > **Criar** para guardar as alterações. 

O perfil é criado e apresentado na lista. Não se esqueça [atribuir o perfil](device-profile-assign.md) e [monitorizar o estado](device-profile-monitor.md).

## <a name="next-steps"></a>Passos Seguintes

Depois do perfil é criado, está pronto para ser atribuído. Em seguida, [atribuir o perfil](device-profile-assign.md) e [monitorizar o estado](device-profile-monitor.md).

Ver a atualização e as definições do modo de S para [Windows 10](edition-upgrade-windows-settings.md) e [Windows Holographic for Business](holographic-upgrade.md) dispositivos.
