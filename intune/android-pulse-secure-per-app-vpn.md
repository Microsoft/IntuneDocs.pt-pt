---
title: "Perfil VPN por aplicação para dispositivos Android – Pulse Secure"
titleSuffix: Intune Azure preview
description: "Pré-visualização do Azure no Intune: saiba como criar um perfil de VPN por aplicação para dispositivos Android geridos pelo Intune."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 05/04/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d035ebf5-85f4-4001-a249-75d24325061a
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: babeaa13da863ca3335c3a05dbabb4a9ac7889ce
ms.contentlocale: pt-pt
ms.lasthandoff: 05/23/2017


---

# <a name="use-a-microsoft-intune-custom-profile-to-create-a-per-app-vpn-profile-for-android-devices"></a>Utilizar um perfil personalizado do Microsoft Intune para criar um perfil VPN por aplicação para dispositivos Android

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

Pode criar um perfil VPN por aplicação para dispositivos Android 5.0 e posteriores geridos pelo Intune. Primeiro, crie um perfil de VPN que utilize o tipo de ligação Pulse Secure. Em seguida, crie uma política de configuração personalizada que associe o perfil de VPN a aplicações específicas.

Depois de atribuir a política ao dispositivo Android ou aos grupos de utilizadores, os utilizadores devem iniciar a VPN do PulseSecure. O PulseSecure irá então permitir tráfego apenas das aplicações especificadas para utilizar a ligação VPN aberta.

> [!NOTE]
>
> Apenas o tipo de ligação Pulse Secure é suportado para este perfil.


## <a name="step-1-create-a-vpn-profile"></a>Passo 1: criar um perfil de VPN


1. Inicie sessão no portal do Azure.
2. Escolha **Mais Serviços** > **Outros** > **Intune**.
3. No painel **Intune**, escolha **Configuração do dispositivo**.
2. No painel **Configuração do Dispositivo**, escolha **Gerir** > **Perfis**.
2. No painel da lista de perfis, escolha **Criar Perfil**.
3. No painel **Criar Perfil**, introduza um **Nome** e uma **Descrição** opcional para o perfil de VPN.
4. Na lista pendente **Plataforma**, escolha **Android**.
5. Na lista pendente **Tipo de perfil**, escolha **VPN**.
3. Escolha **Definições** > **Configurar** e, em seguida, configure o perfil de VPN de acordo com as definições em [Como configurar definições de VPN](vpn-settings-configure.md) e em [Definições de VPN do Intune para dispositivos Android](vpn-settings-android.md).

Tome nota do nome do perfil de VPN para utilização no próximo passo. Por exemplo, **MyAppVpnProfile**.

## <a name="step-2-create-a-custom-configuration-policy"></a>Passo 2: criar uma política de configuração personalizada

1. Inicie sessão no portal do Azure.
2. Escolha **Mais Serviços** > **Outros** > **Intune**.
3. No painel **Intune**, escolha **Configuração do dispositivo**.
2. No painel **Configuração do Dispositivo**, escolha **Gerir** > **Perfis**.
3. No painel de perfis, clique em **Criar Perfil**.
4. No painel **Criar Perfil**, introduza um **Nome** e uma **Descrição** para o perfil personalizado.
5. Na lista pendente **Plataforma**, escolha **Android**.
6. Na lista pendente **Tipo de perfil**, escolha **Personalizado**.
7. Escolha **Definições** > **Configurar**.
3. No painel **Definições de OMA-URI personalizadas**, escolha **Adicionar**.
    - Introduza um nome para a definição.
    - Para **Tipo de dados**, especifique **Cadeia**.
    - Para **OMA-URI**, especifique esta cadeia: **./Vendor/MSFT/VPN/Profile/*Name*/PackageList**, em que *Name* é o nome do perfil VPN que anotou no Passo 1. Neste exemplo, a cadeia seria **./Vendor/MSFT/VPN/Profile/MyAppVpnProfile/PackageList**.
    - Para **Valor**, crie uma lista separada por ponto e vírgula dos pacotes a associar ao perfil. Por exemplo, se pretender que o Excel e o browser Google Chrome utilizem a ligação VPN, introduza **com.microsoft.office.excel;com.android.chrome**.

![Exemplo de política personalizada de VPN por aplicação Android](./media/android_per_app_vpn_oma_uri.png)

### <a name="set-your-app-list-to-blacklist-or-whitelist-optional"></a>Definir a lista de aplicações como lista de bloqueados ou lista de permitidos (opcional)
  Pode especificar uma lista de aplicações que *não* utilize a ligação VPN com o valor **BLACKLIST**. Todas as outras aplicações estabelecerão ligação através da VPN.
Em alternativa, pode utilizar o valor **WHITELIST** para especificar uma lista de aplicações que *possa* utilizar a ligação VPN. As aplicações que não estejam na lista não estabelecerão ligação através da VPN.
  1.    No painel **Definições de OMA-URI personalizadas**, escolha **Adicionar**.
  2.    Introduza um nome para a definição.
  3.    Para **Tipo de dados**, especifique **Cadeia**.
  4.    Para **OMA-URI**, utilize esta cadeia: **./Vendor/MSFT/VPN/Profile/*Name*/Mode**, em que *Name* é o nome do perfil VPN que anotou no Passo 1. No nosso exemplo, a cadeia seria **./Vendor/MSFT/VPN/Profile/MyAppVpnProfile/Mode**.
  5.    Para **Valor**, introduza **BLACKLIST** ou **WHITELIST**.



## <a name="step-3-assign-both-policies"></a>Passo 3: atribuir ambas as políticas

Utilize as instruções em [Como atribuir perfis de dispositivo](device-profile-assign.md) para atribuir ambos os perfis aos utilizadores ou dispositivos obrigatórios.
