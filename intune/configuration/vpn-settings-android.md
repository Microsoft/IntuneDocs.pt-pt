---
title: Usar configurações de VPN para dispositivos Android no Microsoft Intune-Azure | Microsoft Docs
description: Veja todas as configurações para criar conexões VPN em dispositivos Android no Microsoft Intune. Insira o nome da conexão, o endereço IP ou o FQDN do servidor VPN, escolha como os usuários se autenticam e escolha os tipos de conexão Citrix, SonicWall, Check Point e Pulse Secure.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/06/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8d9fefc2413e2dafbf5d0ad67ea15f5f8406cc1c
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72506556"
---
# <a name="android-device-settings-to-configure-vpn-in-intune"></a>Configurações do dispositivo Android para configurar a VPN no Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Este artigo lista e descreve as diferentes configurações de conexão VPN que você pode controlar em dispositivos Android. Como parte da sua solução de MDM (gerenciamento de dispositivo móvel), use essas configurações para criar uma conexão VPN, escolha como a VPN é autenticada, selecione um tipo de servidor VPN e muito mais.

Como administrador do Intune, você pode criar e atribuir configurações de VPN a dispositivos Android. 

Para saber mais sobre perfis de VPN no Intune, confira [perfis de VPN](vpn-settings-configure.md).

## <a name="before-you-begin"></a>Antes de começar

[Crie um perfil de configuração de dispositivo](vpn-settings-configure.md#create-a-device-profile)e escolha **Android**.

## <a name="base-vpn"></a>VPN base

- **Nome da ligação**: introduza um nome para esta ligação. Os utilizadores finais verão este nome quando procurarem no dispositivo as ligações VPN disponíveis. Por exemplo, introduza `Contoso VPN`.
- **Endereço IP ou FQDN**: introduza o endereço IP ou nome de domínio completamente qualificado (FQDN) do servidor VPN ao qual os dispositivos são ligados. Por exemplo, introduza **192.168.1.1** ou **vpn.contoso.com**.

  - **Método de autenticação**: selecione como os dispositivos serão autenticados no servidor VPN. As opções são:

    - **Certificados**: selecione um perfil de certificado SCEP ou PKCS existente para autenticar a ligação. [Configurar certificados](../protect/certificates-configure.md) lista os passos para criar um perfil de certificado.
    - **Nome de usuário e senha**: ao entrar no servidor VPN, os usuários finais são solicitados a inserir seu nome de usuários e senha.

- **Tipo de ligação**: selecione o tipo de ligação VPN. As opções são:

  - **Check Point Capsule VPN**
  - **Cisco AnyConnect**
  - **SonicWall Mobile Connect**
  - **Acesso ao F5**
  - **Pulse Secure**
  - **Citrix SSO**

- **Impressão digital** (apenas na VPN Check Point Capsule): introduza uma cadeia (por exemplo, **Código de Impressão Digital da Contoso**) para verificar a fidedignidade do servidor VPN. Uma impressão digital é enviada ao cliente para que o cliente saiba confiar em qualquer servidor que tenha a mesma impressão digital. Se o dispositivo ainda não incluir a impressão digital, pedirá ao utilizador para confiar no servidor VPN ao mostrar a impressão digital. O usuário verifica a impressão digital manualmente e opta por confiar para se conectar.
- **Introduzir pares de chave e valor para os atributos de VPN do Citrix** (apenas no Citrix): introduza pares de chave e valor disponibilizados pelo Citrix. Estes valores configuram as propriedades da ligação VPN. 

  Você também pode **importar** um arquivo de valores separados por vírgula (. csv) com chaves e pares de valores. Certifique-se de examinar os **meus dados tem cabeçalhos** e propriedades de **chave** .

  Depois de adicionar os pares de chave e valores, use **Exportar** para fazer backup dos dados em um arquivo. csv.

## <a name="next-steps"></a>Próximos passos

[Atribua o perfil](device-profile-assign.md) e [monitorize o respetivo estado](device-profile-monitor.md).

Você também pode criar perfis de VPN para dispositivos [Android Enterprise](vpn-settings-android-enterprise.md), [Ios](vpn-settings-ios.md), [MacOS](vpn-settings-macos.md), [Windows 10 e posterior](vpn-settings-windows-10.md), [Windows 8.1](vpn-settings-windows-8-1.md)e [Windows Phone 8,1](vpn-settings-windows-phone-8-1.md) .
