---
title: Windows Holographic Business partilhado definições do dispositivo – Microsoft Intune – Azure | Documentos da Microsoft
description: Adicionar e utilizar o Windows Holographic for Business para configurar os dispositivos que são partilhados ou utilizados por vários utilizadores no Microsoft Intune. Ver uma lista das definições de gestão de conta e o que fazer em dispositivos, incluindo o Microsoft HoloLens.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/09/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 151ceaa40f2993d3160b9de34eee92e53c35925d
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/14/2019
ms.locfileid: "57565864"
---
# <a name="windows-holographic-for-business-settings-to-manage-shared-devices-using-intune"></a>Windows Holographic for Business definições para gerir dispositivos partilhados, através do Intune

Windows Holographic for Business, dispositivos, como o Microsoft HoloLens, pode ser utilizado por vários utilizadores. Dispositivos que têm vários utilizadores são chamados dispositivos partilhados e são uma parte da gestão de dispositivos móveis soluções (MDM).

Utilizar o Microsoft Intune, os utilizadores podem iniciar sessão para esses dispositivos partilhados com uma conta de convidado. Que usam o dispositivo, eles apenas obtém acesso às funcionalidades que permite.

Este artigo apresenta e descreve as definições que utilizar Windows Holographic for Business no perfil de configuração do dispositivo. Quando o perfil é criado no Intune, em seguida, implementar ou atribuir o perfil a grupos de dispositivos na sua organização. Também pode atribuir este perfil para um grupo de dispositivos com tipos de dispositivo misto e versões de SO.

Para obter mais informações sobre esta funcionalidade no Intune, consulte [controlar o acesso, contas e recursos de energia no PC partilhado ou dispositivos de vários utilizadores](shared-user-device-settings.md). Para obter mais informações sobre o CSP do Windows, consulte [AccountManagement CSP](https://docs.microsoft.com/windows/client-management/mdm/accountmanagement-csp).

## <a name="before-your-begin"></a>Antes de sua begin

[Criar o perfil](shared-user-device-settings.md).

## <a name="shared-multi-user-device-settings"></a>Definições de utilizador multi dispositivos partilhados

> [!NOTE]
> Dispositivos que executam o Windows Holographic for Business, incluindo o Microsoft HoloLens, só suportam o **gerenciamento de contas** definições. Se configurar qualquer uma das outras definições mostradas no Intune, incluindo **modo de PC partilhado**, ele não tem qualquer impacto nestes dispositivos.

- **Gerenciamento de contas**: Defina como **ativar** automaticamente eliminar contas locais criadas pelo convidados e contas no AD e o Azure AD. Quando um utilizador inicia a desativar o dispositivo, ou quando a manutenção do sistema é executada, estas contas são eliminadas. Quando ativada, também defina:
  - **Eliminação da conta**: Escolha quando as contas são eliminadas: **No limite de espaço de armazenamento**, **limiar de espaço de armazenamento e de limiar inativo**, ou **imediatamente após, termine**. Introduza também:
    - **Início eliminar threshold(%)**: Introduza uma percentagem (0 a 100) de espaço em disco. Quando o espaço de armazenamento/disco total cai abaixo do valor introduzido, as contas em cache são eliminadas. Continuamente elimina contas para recuperar espaço em disco. Contas que estão Inativas há mais tempo são eliminadas primeiro.
    - **Parar delete threshold(%)**: Introduza uma percentagem (0 a 100) de espaço em disco. Quando o espaço de disco total/armazenamento cumpre o valor introduzido, a eliminar para.

  Defina como **desativar** para manter o local, AD e contas do Azure AD criadas pelos convidados.

  > [!NOTE]
  > Dispositivos Microsoft HoloLens só suportam o **gerenciamento de contas** definições.

## <a name="next-steps"></a>Passos Seguintes

- [Atribua o perfil](device-profile-assign.md) e [monitorize o respetivo estado](device-profile-monitor.md).
- Ver as definições para [Windows 10 e versões mais recentes](shared-user-device-settings-windows.md).
