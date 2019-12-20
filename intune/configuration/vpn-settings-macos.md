---
title: Definir configurações de VPN para dispositivos macOS no Microsoft Intune-Azure | Microsoft Docs
description: Adicione ou crie um perfil de configuração de VPN (rede virtual privada), incluindo os detalhes da conexão, túnel dividido, configurações de VPN personalizadas com os pares identificador, chave e valor, configurações de proxy com um script de configuração, endereço IP ou FQDN e porta TCP em Microsoft Intune em dispositivos que executam o macOS.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/09/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e0bb2cb757e944369642807f117683dad3a9805a
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/19/2019
ms.locfileid: "75206266"
---
# <a name="add-vpn-settings-on-macos-devices-in-microsoft-intune"></a>Adicionar configurações de VPN em dispositivos macOS no Microsoft Intune



Este artigo mostra as definições do Intune que pode utilizar para configurar ligações VPN em dispositivos com macOS.

Consoante as definições que escolher, nem todos os valores na lista seguinte serão configuráveis.

## <a name="before-you-begin"></a>Antes de começar

[Criar um perfil de configuração do dispositivo](vpn-settings-configure.md).

> [!NOTE]
> Essas configurações estão disponíveis para todos os tipos de registro. Para obter mais informações sobre os tipos de registro, consulte [registro do MacOS](../enrollment/macos-enroll.md).

## <a name="base-vpn-settings"></a>Definições de VPN Base

**Nome da ligação**: introduza um nome para esta ligação. Os utilizadores finais verão este nome quando procurarem no dispositivo a lista de ligações VPN disponíveis.
- **Endereço IP ou FQDN**: forneça o endereço IP ou o nome de domínio totalmente qualificado do servidor VPN ao qual os dispositivos se conectam. Exemplos: **192.168.1.1**, **vpn.contoso.com**.
- **Método de autenticação**: escolha como os dispositivos serão autenticados no servidor VPN em:
  - **Certificados**: em **certificado de autenticação**, escolha um perfil de certificado SCEP ou PKCS criado anteriormente para autenticar a conexão. Para obter mais informações sobre os perfis de certificado, veja [Como configurar certificados](../protect/certificates-configure.md).
  - **Nome de usuário e senha**: os usuários finais devem fornecer um nome de usuário e senha para fazer logon no servidor VPN.
- **Tipo de ligação**: selecione o tipo de ligação VPN a partir da seguinte lista de fornecedores:
  - **Check Point Capsule VPN**
  - **Cisco AnyConnect**
  - **SonicWall Mobile Connect**
  - **F5 Edge Client**
  - **Pulse Secure**
  - **VPN Personalizada**
- **Túnel dividido**: **habilite** ou **desabilite** essa opção que permite que os dispositivos decidam qual conexão usar dependendo do tráfego. Por exemplo, um utilizador num hotel utiliza a ligação VPN para aceder aos ficheiros de trabalho, mas utiliza a rede padrão do hotel para a navegação normal na Internet.

<!--- **Per-app VPN** - Select this option if you want to associate this VPN connection with an iOS or macOS app so that the connection will be opened when the app is run. You can associate the VPN profile with an app when you assign the software. For more information, see [How to assign and monitor apps](../apps/apps-deploy.md). --->

## <a name="custom-vpn-settings"></a>Definições de VPN Personalizada

Se tiver selecionado **VPN Personalizada**, configure estas definições adicionais:

- **Identificador de VPN**: Insira um identificador para o aplicativo VPN que você está usando. Esse identificador é fornecido pelo seu provedor de VPN.
- **Introduzir pares de chave e valor para os atributos de VPN personalizados**: adicione ou importe **Chaves** e **Valores** para personalizar a sua ligação VPN. Esses valores normalmente são fornecidos pelo seu provedor de VPN.

## <a name="proxy-settings"></a>Definições de proxy

- **Script de configuração automática**: utilize um ficheiro para configurar o servidor proxy. Introduza o **URL do servidor proxy**, que contém o ficheiro de configuração. Por exemplo, introduza `http://proxy.contoso.com`.
- **Endereço**: Insira o endereço do servidor proxy (como um endereço IP).
- **Número de porta**: introduza o número de porta associado ao servidor proxy.

## <a name="next-steps"></a>Próximos passos

O perfil está criado, mas ainda não está ativo. Em seguida, [atribua o perfil](device-profile-assign.md) e [monitorize o estado](device-profile-monitor.md).

Defina as configurações de VPN em dispositivos [Android](vpn-settings-android.md), [Android Enterprise](vpn-settings-android-enterprise.md), [Ios](vpn-settings-ios.md)e [Windows 10](vpn-settings-windows-10.md) .
