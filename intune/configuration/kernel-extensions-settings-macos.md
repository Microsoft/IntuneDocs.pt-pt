---
title: configurações de extensão do kernel macOS no Microsoft Intune – Azure | Microsoft Docs
titleSuffix: ''
description: Adicione, configure ou crie configurações em dispositivos macOS para usar extensões de kernel. Além disso, permita que os usuários substituam as extensões aprovadas, permitam todas as extensões de um identificador de equipe ou permitam extensões ou aplicativos específicos no Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/10/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1306bfea1880061980413d283943e6521c1ac213
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71730604"
---
# <a name="macos-device-settings-to-configure-and-use-kernel-extensions-in-intune"></a>configurações de dispositivo macOS para configurar e usar extensões de kernel no Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Este artigo lista e descreve as diferentes configurações de extensão do kernel que você pode controlar em dispositivos macOS. Como parte da sua solução de MDM (gerenciamento de dispositivo móvel), use essas configurações para adicionar e gerenciar extensões de kernel em seus dispositivos.

Para saber mais sobre extensões de kernel no Intune e quaisquer pré-requisitos, consulte [adicionar extensões de kernel MacOS](../kernel-extensions-overview-macos.md).

Estas definições são adicionadas a um perfil de configuração do dispositivo no Intune e, em seguida, atribuídas ou implementadas nos dispositivos macOS.

## <a name="before-you-begin"></a>Antes de começar

[Criar um perfil de configuração de extensões de kernel do dispositivo](../kernel-extensions-overview-macos.md).

> [!NOTE]
> Essas configurações se aplicam a diferentes tipos de registro. Para obter mais informações sobre os diferentes tipos de registro, consulte [registro do MacOS](../macos-enroll.md).

## <a name="kernel-extensions"></a>Extensões do kernel

### <a name="settings-apply-to-user-approved-automated-device-enrollment"></a>As configurações se aplicam a: Usuário aprovado, registro de dispositivo automatizado

- **Permitir substituições do usuário**: **Permitir** permite que os usuários aprovem as extensões de kernel não incluídas no perfil de configuração. **Não configurado** (padrão) impede que os usuários permitam extensões não incluídas no perfil de configuração. Ou seja, somente as extensões incluídas no perfil de configuração são permitidas.

  Consulte [carregamento de extensão de kernel aprovado pelo usuário](https://developer.apple.com/library/archive/technotes/tn2459/_index.html) (abre o site da Apple) para obter mais informações sobre esse recurso.

- **Identificadores de equipe permitidos**: Use essa configuração para permitir uma ou várias IDs de equipe. Todas as extensões de kernel assinadas com as IDs de equipe que você inserir são permitidas e confiáveis. Em outras palavras, use esta opção para permitir todas as extensões de kernel dentro da mesma ID de equipe, que pode ser um desenvolvedor ou parceiro específico.

  **Adicione** um identificador de equipe de extensões de kernel válidas e assinadas que você deseja carregar. Você pode adicionar vários identificadores de equipe. O identificador de equipe deve ser alfanumérico (letras e números) e ter 10 caracteres. Por exemplo, introduza `ABCDE12345`.

  Depois de adicionar um identificador de equipe, ele também pode ser excluído.

  [Localize sua ID de equipe](https://help.apple.com/developer-account/#/dev55c3c710c) (abre o site da Apple) tem mais informações.

- **Extensões de kernel permitidas**: Use essa configuração para permitir extensões de kernel específicas. Somente as extensões de kernel inseridas são permitidas ou confiáveis. 

  **Adicione** o identificador de pacote e o identificador de equipe de uma extensão de kernel que você deseja carregar. Para extensões de kernel herdadas não assinadas, use um identificador de equipe vazio. Você pode adicionar várias extensões de kernel. O identificador de equipe deve ser alfanumérico (letras e números) e ter 10 caracteres. Por exemplo, insira `com.contoso.appname.macos` para **ID do pacote**e `ABCDE12345` para **identificador de equipe**.

  > [!TIP]
  > Para obter a ID de pacote de uma extensão de kernel (kext) em um dispositivo macOS, você pode:
  >
  > 1. No terminal, execute `kextstat | grep -v com.apple`e observe a saída. Instale o software ou o kext que você deseja. Execute `kextstat | grep -v com.apple` novamente e procure alterações.
  >
  >    No terminal, `kextstat` lista todas as extensões de kernel no sistema operacional. 
  >
  > 2. No dispositivo, abra o arquivo de lista de propriedades de informações (info. plist) para um kext. A ID do pacote é mostrada. Cada kext tem um arquivo info. plist armazenado dentro do. 

> [!NOTE]
> Você não precisa adicionar identificadores de equipe e extensões de kernel. Você pode configurar um ou outro.

## <a name="next-steps"></a>Passos seguintes

[Atribua o perfil](../device-profile-assign.md) e [monitorize o respetivo estado](../device-profile-monitor.md).
