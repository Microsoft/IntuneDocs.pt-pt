---
title: "Configurar atualizações de edição do Windows 10 com o Intune | Pré-visualização do Azure no Intune | Documentos da Microsoft"
description: "Pré-visualização do Azure no Intune: saiba como utilizar o Intune para atualizar dispositivos Windows 10 que gere."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ae8b6528-7979-47d8-abe0-58cea1905270
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b4d095506215b775d56d172e9aabae1737757310
ms.openlocfilehash: 49da713cfe61ce21501e0a8e0f6e0c225b2bc291
ms.lasthandoff: 02/16/2017


---

# <a name="how-to-configure-windows-10-edition-upgrades-in-microsoft-intune"></a>Como configurar atualizações de edição do Windows 10 no Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Utilize as informações deste tópico para saber como configurar um perfil de atualização de edição do Windows 10. Este perfil permite-lhe atualizar automaticamente dispositivos que executam uma das seguintes versões do Windows 10 para uma edição mais recente:

- Computadores com o Windows 10
- Windows 10 Holographic
- Windows 10 Mobile

Os seguintes caminhos de atualização são suportados:

- Desde o Windows 10 Pro ao Windows 10 Enterprise
- Desde o Windows 10 Home ao Windows 10 Education
- Desde o Windows 10 Mobile ao Windows 10 Mobile Enterprise
- Desde o Windows 10 Holographic Pro ao Windows 10 Holographic Enterprise

## <a name="before-you-start"></a>Antes de começar
Antes de começar a atualizar dispositivos para a versão mais recente, irá necessitar de um dos seguintes:

- Uma chave de produto válida para instalar a nova versão do Windows em todos os dispositivos visados pela política (para edições do Windows 10 para computadores). Pode utilizar chaves MAK (Chaves de Ativação Múltipla) ou KMS (Servidor de Gestão de Chaves). ou Um ficheiro de licenciamento da Microsoft que contém as informações de licenciamento para instalar a nova versão do Windows em todos os dispositivos visados pela política (para as edições Windows 10 Mobile e Windows 10 Holographic).
- Os dispositivos Windows 10 visados têm de estar inscritos no Microsoft Intune. Não é possível utilizar a política de atualização de edição com PCs que executam o software de cliente de PCs do Intune.

## <a name="create-a-device-profile-containing-device-restriction-settings"></a>Criar um perfil de dispositivo com as definições de restrição de dispositivos

1. Inicie sessão no portal do Azure.
2. Escolha **Mais Serviços** > **Outros** > **Intune**.
3. No painel **Intune**, escolha **Configurar dispositivos**.
2. No painel **Configuração do Dispositivo**, escolha **Gerir** > **Perfis**.
3. No painel de perfis, escolha **Criar Perfil**.
4. No painel **Criar Perfil**, introduza um **Nome** e uma **Descrição** para o perfil de atualização da edição.
5. Na lista pendente **Plataforma**, escolha **Windows 10 e posterior**.
6. Na lista pendente **Tipo de perfil**, escolha **Atualização de Edição**.
7. No painel **Atualização de Edição**, configure as seguintes opções:
    - **Edição para atualizar** – Na lista pendente, selecione a versão do Windows 10 que pretende atualizar nos dispositivos.
    - **Edição para a qual atualizar** – Na lista pendente, selecione a versão do Windows 10 Desktop, do Windows 10 Holographic ou do Windows 10 Mobile para a qual pretende atualizar os dispositivos visados.
    - **Chave de Produto** – Especifique a chave de produto que obteve da Microsoft, que pode servir para atualizar todos os dispositivos Windows 10 Desktop visados.<br>Depois de criar uma política que contém uma chave de produto, já não poderá editar a chave de produto. Isto deve-se ao facto de a chave ficar obscurecida por razões de segurança. Para alterar a chave de produto, tem de introduzir novamente a chave completa.
    - **Ficheiro de Licença** – Escolha **Procurar** para selecionar o ficheiro de licença que obteve da Microsoft, que contém informações sobre a licença para a edição Windows Holographic ou Windows 10 Mobile para a qual pretende atualizar os dispositivos visados.
8. Quando tiver terminado, volte ao painel **Criar Perfil** e clique em **Criar**.

O perfil será criado e é apresentado no painel da lista de perfis.
Se quiser continuar e atribuir este perfil a grupos, veja [Como atribuir perfis de dispositivo](how-to-assign-device-profiles.md).


