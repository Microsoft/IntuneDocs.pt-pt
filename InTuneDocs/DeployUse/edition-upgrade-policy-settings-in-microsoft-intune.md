---
# required metadata

title: Definições de política de atualização de edição do Windows no Microsoft Intune | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 8589866a-3f13-489b-a5cd-cee017d16d54

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Definições de política de atualização de edição do Windows no Microsoft Intune
A **Política de Atualização de Edição** do Microsoft Intune permite-lhe atualizar automaticamente dispositivos que executam uma das seguintes versões do Windows 10 para uma edição mais recente:
* Windows 10 Desktop
* Windows 10 Holographic

## Antes de começar
Antes de começar a atualizar dispositivos para a versão mais recente, irá necessitar de um dos seguintes:
* Uma chave de produto válida para instalar a nova versão do Windows em todos os dispositivos que segmentar com a política (para edições Windows 10 Desktop).
* Um ficheiro de licenciamento da Microsoft que contém as informações de licenciamento para instalar a nova versão do Windows em todos os dispositivos que segmentar com a política (para as edições Windows 10 Mobile e Windows 10 Holographic).
* Os dispositivos Windows 10 visados têm de estar inscritos no Microsoft Intune.

## Definições da política de atualização de edição

|Nome da definição|Detalhes|
|-|-|
|**Nome**|Introduza um nome para a política de atualização de edição.|
|**Descrição**|Opcionalmente, introduza uma descrição para a política que o ajude a identificá-la na consola do Intune.
|**Edição a atualizar**|Na lista pendente, selecione a versão do Windows 10 Desktop, do Windows 10 Holographic ou do Windows 10 Mobile para a qual pretende atualizar os dispositivos segmentados.
|**Chave de Produto**|Especifique a chave de produto que obteve da Microsoft, que pode ser utilizada para atualizar todos os dispositivos Windows 10 Desktop visados.<br>Depois de criar uma política que contém uma chave de produto, já não será possível editar a chave de produto. Isto deve-se ao facto de a chave ficar obscurecida por razões de segurança. Para alterar a chave de produto, tem de introduzir novamente a chave completa.
|**Ficheiro de licenciamento**|Clique em **Procurar** para selecionar o ficheiro de licença que obteve da Microsoft, que contém informações sobre a licença para a edição Windows Holographic para a qual pretende atualizar os dispositivos visados.

### Consulte também
[Gerir definições e funcionalidades nos seus dispositivos com as políticas do Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)

<!--HONumber=May16_HO1-->


