---
title: Usar configurações de VPN para Android Enterprise no Microsoft Intune – Azure | Microsoft Docs
description: Veja todas as configurações para criar conexões VPN em dispositivos Android Enterprise no Microsoft Intune. Insira o nome da conexão, o endereço IP ou o FQDN do servidor VPN, escolha como os usuários se autenticam e escolha os tipos de conexão Citrix, SonicWall, Check Point e Pulse Secure.
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
ms.openlocfilehash: a0c11be374e36ec32feb9540f6cfd4f1bc794e9c
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/19/2019
ms.locfileid: "75206317"
---
# <a name="android-enterprise-device-settings-to-configure-vpn-in-intune"></a>Configurações de dispositivo do Android Enterprise para configurar a VPN no Intune



Este artigo lista e descreve as diferentes configurações de conexão VPN que você pode controlar em dispositivos Android Enterprise. Como parte da sua solução de MDM (gerenciamento de dispositivo móvel), use essas configurações para criar uma conexão VPN, escolha como a VPN é autenticada, selecione um tipo de servidor VPN e muito mais.

Como administrador do Intune, você pode criar e atribuir configurações de VPN a dispositivos Android Enterprise. 

Para saber mais sobre perfis de VPN no Intune, confira [perfis de VPN](vpn-settings-configure.md).

> [!NOTE]
> Para configurar a VPN Always on, você precisa criar um perfil de VPN e também criar um perfil de [restrições de dispositivo](device-restrictions-android-for-work.md#connectivity) com a configuração de VPN AlwaysOn configurada.

## <a name="before-you-begin"></a>Antes de começar

[Crie um perfil de configuração de dispositivo](vpn-settings-configure.md#create-a-device-profile)e escolha **Android Enterprise**.

## <a name="device-owner-only"></a>Proprietário do dispositivo apenas

- **Nome da ligação**: introduza um nome para esta ligação. Os utilizadores finais verão este nome quando procurarem no dispositivo as ligações VPN disponíveis. Por exemplo, introduza `Contoso VPN`.
- **Endereço IP ou FQDN**: introduza o endereço IP ou nome de domínio completamente qualificado (FQDN) do servidor VPN ao qual os dispositivos são ligados. Por exemplo, introduza **192.168.1.1** ou **vpn.contoso.com**.

  - **Método de autenticação**: selecione como os dispositivos serão autenticados no servidor VPN. As opções são:
  
    - **Certificados**: selecione um perfil de certificado SCEP ou PKCS existente para autenticar a ligação. [Configurar certificados](../protect/certificates-configure.md) lista os passos para criar um perfil de certificado.
    - **Nome de usuário e senha**: ao entrar no servidor VPN, os usuários finais são solicitados a inserir seu nome de usuários e senha.

- **Tipo de ligação**: selecione o tipo de ligação VPN. As opções são:

  - **Cisco AnyConnect**
  - **Acesso ao F5**
  - **Pulse Secure**

## <a name="work-profile-only"></a>Apenas perfil de trabalho

- **Nome da ligação**: introduza um nome para esta ligação. Os utilizadores finais verão este nome quando procurarem no dispositivo as ligações VPN disponíveis. Por exemplo, introduza `Contoso VPN`.
- **Endereço IP ou FQDN**: introduza o endereço IP ou nome de domínio completamente qualificado (FQDN) do servidor VPN ao qual os dispositivos são ligados. Por exemplo, introduza **192.168.1.1** ou **vpn.contoso.com**.

  - **Método de autenticação**: selecione como os dispositivos serão autenticados no servidor VPN. As opções são:
  
    - **Certificados**: selecione um perfil de certificado SCEP ou PKCS existente para autenticar a ligação. [Configurar certificados](../protect/certificates-configure.md) lista os passos para criar um perfil de certificado.
    - **Nome de usuário e senha**: ao entrar no servidor VPN, os usuários finais são solicitados a inserir seu nome de usuários e senha.

- **Tipo de ligação**: selecione o tipo de ligação VPN. As opções são:

  - **Cisco AnyConnect**
  - **Acesso ao F5**
  - **Pulse Secure**
  - **SonicWall Mobile Connect**
  - **Check Point Capsule VPN**

## <a name="next-steps"></a>Próximos passos

[Atribua o perfil](device-profile-assign.md) e [monitorize o respetivo estado](device-profile-monitor.md).

Você também pode criar perfis de VPN para dispositivos [Android](vpn-settings-android.md), [Ios](vpn-settings-ios.md), [MacOS](vpn-settings-macos.md), [Windows 10 e posterior](vpn-settings-windows-10.md), [Windows 8.1](vpn-settings-windows-8-1.md)e [Windows Phone 8,1](vpn-settings-windows-phone-8-1.md) .
