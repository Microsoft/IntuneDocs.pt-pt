---
title: "Definições da política de atualização de edição do Windows"
description: "Saiba como atualizar automaticamente os dispositivos Windows 10 para uma versão diferente com o Intune."
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 04/14/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8589866a-3f13-489b-a5cd-cee017d16d54
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: coryfe
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 690fe1f1b2555996b2ef124cde6e3fba53e82ec7
ms.sourcegitcommit: 1a54bdf22786aea1cf1b497d54024470e1024aeb
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/10/2017
---
# <a name="windows-edition-upgrade-policy-settings-in-microsoft-intune"></a>Definições de política de atualização de edição do Windows no Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

A **Política de Atualização de Edição** do Microsoft Intune permite-lhe atualizar automaticamente dispositivos que executam uma das seguintes versões do Windows 10 para uma edição diferente:
* Computadores com o Windows 10
* Windows 10 Holographic
* Windows 10 Mobile

Os seguintes caminhos de atualização são suportados:
- Desde o Windows 10 Pro ao Windows 10 Enterprise
- Desde o Windows 10 Home ao Windows 10 Education
- Desde o Windows 10 Mobile ao Windows 10 Mobile Enterprise
- Desde o Windows 10 Holographic Pro ao Windows 10 Holographic Enterprise

## <a name="before-you-start"></a>Antes de começar
Antes de começar a atualizar dispositivos para a versão mais recente, irá necessitar de um dos seguintes:
* Uma chave de produto válida para instalar a nova versão do Windows em todos os dispositivos visados pela política (para edições do Windows 10 para computadores). Pode utilizar chaves MAK (Chaves de Ativação Múltipla) ou KMS (Servidor de Gestão de Chaves).
**ou** Um ficheiro de licenciamento da Microsoft que contém as informações de licenciamento para instalar a nova versão do Windows em todos os dispositivos visados pela política (para as edições Windows 10 Mobile e Windows 10 Holographic).
* Os dispositivos Windows 10 visados têm de estar inscritos no Microsoft Intune. Não é possível utilizar a política de atualização de edição com PCs que executam o software de cliente de PCs do Intune.

## <a name="edition-upgrade-policy-settings"></a>Definições da política de atualização de edição

|Nome da definição|Detalhes|
|-|-|
|**Nome**|Introduza um nome para a política de atualização de edição.|
|**Descrição**|Opcionalmente, introduza uma descrição para a política que o ajude a identificá-la na consola do Intune.
|**Edição a atualizar**|Na lista pendente, selecione a versão do Windows 10, do Windows 10 Holographic ou do Windows 10 Mobile para a qual pretende atualizar os dispositivos segmentados.
|**Chave de Produto**|Especifique a chave de produto que obteve da Microsoft, que pode ser utilizada para atualizar todos os computadores com Windows 10 visados.<br>Depois de criar uma política que contém uma chave de produto, já não será possível editar a chave de produto. Isto deve-se ao facto de a chave ficar obscurecida por razões de segurança. Para alterar a chave de produto, tem de introduzir novamente a chave completa.
|**Ficheiro de Licenciamento**|Escolha **Procurar** para selecionar o ficheiro de licença que obteve da Microsoft, que contém informações sobre a licença para a edição Windows Holographic ou Windows 10 Mobile para a qual pretende atualizar os dispositivos visados.

### <a name="see-also"></a>Consulte também
[Gerir definições e funcionalidades nos seus dispositivos com as políticas do Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)
