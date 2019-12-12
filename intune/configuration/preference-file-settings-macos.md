---
title: Adicionar configurações de arquivo de preferência a dispositivos macOS no Microsoft Intune – Azure | Microsoft Docs
titleSuffix: ''
description: Adicione um arquivo XML ou plist que inclua informações importantes sobre seu aplicativo. Use um perfil de configuração de dispositivo de arquivo de preferência para alterar as informações de chave no arquivo de lista de propriedades e atribuí-lo aos dispositivos macOS.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/02/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6ed04c1bf135793da9cece9debc2c7cdd481601a
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/05/2019
ms.locfileid: "74691683"
---
# <a name="add-a-property-list-file-to-macos-devices-using-microsoft-intune"></a>Adicionar um arquivo de lista de propriedades a dispositivos macOS usando Microsoft Intune

Usando Microsoft Intune, você pode adicionar um arquivo de lista de Propriedades (. plist) para dispositivos macOS ou aplicativos em dispositivos macOS.

Esta funcionalidade aplica-se a:

- dispositivos macOS executando 10,7 e mais recentes

Os arquivos de lista de propriedades normalmente incluem informações sobre aplicativos macOS. Para obter mais informações, consulte [sobre os arquivos de lista de propriedades de informações](https://developer.apple.com/library/archive/documentation/General/Reference/InfoPlistKeyReference/Articles/AboutInformationPropertyListFiles.html) (site da Apple) e configurações de [carga personalizada](https://support.apple.com/guide/mdm/custom-mdm9abbdbe7/1/web/1).

Este artigo lista e descreve as diferentes configurações de arquivo de lista de propriedades que você pode adicionar a dispositivos macOS. Como parte da sua solução de MDM (gerenciamento de dispositivo móvel), use essas configurações para adicionar a ID do pacote de aplicativo (`com.company.application`) e adicionar seu arquivo. plist.

Estas definições são adicionadas a um perfil de configuração do dispositivo no Intune e, em seguida, atribuídas ou implementadas nos dispositivos macOS.

## <a name="before-you-begin"></a>Antes de começar

[Crie o perfil](device-profile-create.md).

## <a name="what-you-need-to-know"></a>O que tem de saber

- Essas configurações não são validadas. Certifique-se de testar suas alterações antes de atribuir o perfil aos seus dispositivos.
- Se você não tiver certeza de como inserir uma chave de aplicativo, altere a configuração no aplicativo. Em seguida, examine o arquivo de preferência do aplicativo usando o [Xcode](https://developer.apple.com/xcode/) para ver como a configuração está definida. A Apple recomenda a remoção de configurações não gerenciáveis usando o Xcode antes de importar o arquivo.
- Somente alguns aplicativos funcionam com as preferências gerenciadas e podem não permitir que você gerencie todas as configurações.
- Certifique-se de carregar os arquivos de lista de propriedades que direcionam as configurações de canal do dispositivo, não as configurações de canal do usuário Os arquivos de lista de propriedades direcionam todo o dispositivo.

## <a name="preference-file"></a>Ficheiro de preferência

- **Nome de domínio de preferência**: os arquivos de lista de propriedades são normalmente usados para navegadores da Web (Microsoft Edge), [proteção avançada contra ameaças do Microsoft defender](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-atp-mac)e aplicativos personalizados. Quando você cria um domínio de preferência, uma ID de pacote também é criada. Insira a ID do pacote, como `com.company.application`. Por exemplo, digite `com.Contoso.applicationName`, `com.Microsoft.Edge` ou `com.microsoft.wdav`.
- **Arquivo de lista de propriedades**: selecione o arquivo de lista de propriedades associado ao seu aplicativo. Certifique-se de que seja um arquivo `.plist` ou `.xml`. Por exemplo, carregue um arquivo de `YourApp-Manifest.plist` ou `YourApp-Manifest.xml`.
- **Conteúdo do arquivo**: as informações de chave no arquivo de lista de propriedades são mostradas. Se você precisar alterar as informações da chave, abra o arquivo de lista em outro editor e recarregue o arquivo no Intune.

Selecione **OK** > **Criar** para guardar as alterações. O perfil é criado e mostrado na lista de perfis.

## <a name="next-steps"></a>Próximos passos

O perfil está criado, mas ainda não está ativo. Em seguida, [atribua o perfil](device-profile-assign.md) e [monitorize o estado](device-profile-monitor.md).

Para obter mais informações sobre arquivos de preferência para o Microsoft Edge, consulte [definir configurações de política do Microsoft Edge no MacOS](https://docs.microsoft.com/deployedge/configure-microsoft-edge-on-mac).
