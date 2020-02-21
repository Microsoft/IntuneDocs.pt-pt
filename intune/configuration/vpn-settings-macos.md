---
title: Configure as definições de VPN para dispositivos macOS no Microsoft Intune - Azure  Microsoft Docs
description: Adicione ou crie um perfil de configuração de rede privada virtual (VPN), incluindo os detalhes de ligação, túnel dividido, configurações VPN personalizadas com os pares de identificador, chave e valor, configurações de procuração com um script de configuração, endereço IP ou FQDN, e porta TCP em Microsoft Intune em dispositivos que executam o macOS.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/18/2020
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b20a7eca6f71d46380f9fcdb1674226cc54a104f
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/20/2020
ms.locfileid: "77510784"
---
# <a name="add-vpn-settings-on-macos-devices-in-microsoft-intune"></a>Adicione as definições vpN em dispositivos macOS no Microsoft Intune



Este artigo mostra as definições do Intune que pode utilizar para configurar ligações VPN em dispositivos com macOS.

Consoante as definições que escolher, nem todos os valores na lista seguinte serão configuráveis.

## <a name="before-you-begin"></a>Antes de começar

Criar um perfil de [configuração do dispositivo](vpn-settings-configure.md).

> [!NOTE]
> Estas configurações estão disponíveis para todos os tipos de inscrição. Para obter mais informações sobre os tipos de matrículas, consulte a [inscrição do macOS.](../enrollment/macos-enroll.md)

## <a name="base-vpn-settings"></a>Definições de VPN Base

**Nome da ligação**: introduza um nome para esta ligação. Os utilizadores finais verão este nome quando procurarem no dispositivo a lista de ligações VPN disponíveis.
- **Endereço IP ou FQDN**: Forneça o endereço IP ou o nome de domínio totalmente qualificado do servidor VPN a que os dispositivos se ligam. Exemplos: **192.168.1.1**, **vpn.contoso.com**.
- **Método de autenticação**: escolha como os dispositivos serão autenticados no servidor VPN em:
  - **Certificados**: Sob **certificado de autenticação,** escolha um perfil de certificado SCEP ou PKCS que criou anteriormente para autenticar a ligação. Para obter mais informações sobre os perfis de certificado, veja [Como configurar certificados](../protect/certificates-configure.md).
  - **Nome de utilizador e palavra-passe**: Os utilizadores finais devem fornecer um nome de utilizador e uma senha para iniciar sessão no servidor VPN.
- **Tipo de ligação**: selecione o tipo de ligação VPN a partir da seguinte lista de fornecedores:
  - **Check Point Capsule VPN**
  - **Cisco AnyConnect**
  - **SonicWall Mobile Connect**
  - **F5 Edge Client**
  - **Pulse Secure**
  - **VPN Personalizada**
- **Túnel dividido**: **Ativar** ou **desativar** esta opção que permite que os dispositivos decidam qual a ligação a utilizar dependendo do tráfego. Por exemplo, um utilizador num hotel utiliza a ligação VPN para aceder aos ficheiros de trabalho, mas utiliza a rede padrão do hotel para a navegação normal na Internet.

<!--- **Per-app VPN** - Select this option if you want to associate this VPN connection with an iOS/iPadOS or macOS app so that the connection will be opened when the app is run. You can associate the VPN profile with an app when you assign the software. For more information, see [How to assign and monitor apps](../apps/apps-deploy.md). --->

## <a name="custom-vpn-settings"></a>Definições de VPN Personalizada

Se tiver selecionado **VPN Personalizada**, configure estas definições adicionais:

- **Identificador VPN**: Introduza um identificador para a aplicação VPN que está a utilizar. Este identificador é fornecido pelo seu fornecedor VPN.
- **Introduzir pares de chave e valor para os atributos de VPN personalizados**: adicione ou importe **Chaves** e **Valores** para personalizar a sua ligação VPN. Estes valores são normalmente fornecidos pelo seu fornecedor VPN.

## <a name="proxy-settings"></a>Definições de proxy

- **Script de configuração automática**: utilize um ficheiro para configurar o servidor proxy. Introduza o **URL do servidor proxy**, que contém o ficheiro de configuração. Por exemplo, introduza `http://proxy.contoso.com`.
- **Endereço**: Introduza o endereço do servidor proxy (como endereço IP).
- **Número de porta**: introduza o número de porta associado ao servidor proxy.

## <a name="next-steps"></a>Próximos passos

O perfil está criado, mas ainda não está ativo. Em seguida, [atribua o perfil](device-profile-assign.md) e [monitorize o estado](device-profile-monitor.md).

Configure as definições vpN nos dispositivos [Android](vpn-settings-android.md), [Android Enterprise,](vpn-settings-android-enterprise.md) [iOS/iPadOS](vpn-settings-ios.md)e [Windows 10.](vpn-settings-windows-10.md)
