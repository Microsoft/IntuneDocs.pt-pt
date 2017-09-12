---
title: "Configurar atualizações de edição do Windows 10 com o Intune"
titlesuffix: Azure portal
description: "Saiba como utilizar o Intune para atualizar dispositivos Windows 10 que gere para uma edição diferente.\""
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 07/26/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ae8b6528-7979-47d8-abe0-58cea1905270
ms.reviewer: coryfe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8f6bd4c4af168bc64acabc05fdaad93558ddd10a
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/09/2017
---
# <a name="how-to-configure-windows-10-edition-upgrades-in-microsoft-intune"></a>Como configurar atualizações de edição do Windows 10 no Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Utilize as informações deste tópico para saber como configurar um perfil de atualização de edição do Windows 10. Este perfil permite-lhe atualizar automaticamente dispositivos que executam uma das seguintes versões do Windows 10 para uma edição diferente:

- Windows 10 Home
- Windows 10 Holographic
- Windows 10 Mobile


Os seguintes caminhos de atualização são suportados:

- Desde o Windows 10 Pro ao Windows 10 Enterprise
- Desde o Windows 10 Home ao Windows 10 Education
- Desde o Windows 10 Mobile ao Windows 10 Mobile Enterprise
- Desde o Windows 10 Holographic Pro ao Windows 10 Holographic Enterprise


## <a name="before-you-start"></a>Antes de começar
Antes de começar a atualizar dispositivos para a versão mais recente, precisa de:

- Uma chave de produto válida para instalar a nova versão do Windows em todos os dispositivos visados pela política (para edições do Windows 10 para computadores). Pode utilizar Chaves de Ativação Múltipla (MAK), chaves KMS (Servidor de Gestão de Chaves) ou um ficheiro de licenciamento da Microsoft que contém as informações de licenciamento para instalar a nova versão do Windows em todos os dispositivos abrangidos pela política (para as edições Windows 10 Mobile e Windows 10 Holographic).
- Os dispositivos Windows 10 aos quais irá atribuir a política têm de estar inscritos no Microsoft Intune. Não é possível utilizar a política de atualização de edição com PCs que executam o software de cliente de PCs do Intune.

## <a name="create-a-device-profile-containing-device-restriction-settings"></a>Criar um perfil de dispositivo com as definições de restrição de dispositivos

1. Inicie sessão no portal do Azure.
2. Escolha **Mais Serviços** > **Monitorização + Gestão** > **Intune**.
3. No painel **Intune**, escolha **Configuração do dispositivo**.
2. No painel **Configuração do Dispositivo**, escolha **Gerir** > **Perfis**.
3. No painel de perfis, escolha **Criar Perfil**.
4. No painel **Criar Perfil**, introduza um **Nome** e uma **Descrição** para o perfil de atualização da edição.
5. Na lista pendente **Plataforma**, escolha **Windows 10 e posterior**.
6. Na lista pendente **Tipo de perfil**, escolha **Atualização de Edição**.
7. No painel **Atualização de Edição**, configure as seguintes definições:
    - **Edição para atualizar** – Na lista pendente, selecione a versão do Windows 10 que pretende atualizar nos dispositivos.
    - **Edição para a qual atualizar** – Na lista pendente, selecione a versão do Windows 10 Desktop, do Windows 10 Holographic ou do Windows 10 Mobile para a qual pretende atualizar os dispositivos visados.
    - **Chave de Produto** – Especifique a chave de produto que obteve da Microsoft, que pode servir para atualizar todos os dispositivos Windows 10 Desktop visados.<br>Depois de criar uma política que contém uma chave de produto, já não poderá editar a chave de produto. Isto deve-se ao facto de a chave ficar obscurecida por razões de segurança. Para alterar a chave de produto, tem de introduzir novamente a chave completa.
    - **Ficheiro de Licença** – Escolha **Procurar** para selecionar o ficheiro de licença que obteve da Microsoft, que contém informações sobre a licença para a edição Windows Holographic ou Windows 10 Mobile para a qual pretende atualizar os dispositivos visados.
8. Quando tiver terminado, volte ao painel **Criar Perfil** e clique em **Criar**.

O perfil é criado e apresentado no painel da lista de perfis.

## <a name="next-steps"></a>Próximos passos

Se quiser continuar e atribuir este perfil a grupos, veja [Como atribuir perfis de dispositivo](device-profile-assign.md).

>[!NOTE]
>Se remover a atribuição de políticas, a versão do Windows no dispositivo não será revertida e continuará a funcionar normalmente.

