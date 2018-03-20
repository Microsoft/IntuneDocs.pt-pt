---
title: "Perfil VPN por aplicação para dispositivos Android – Pulse Secure"
titlesuffix: Azure portal
description: "Saiba como criar um perfil VPN por aplicação para dispositivos Android geridos pelo Intune.\""
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 03/05/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d035ebf5-85f4-4001-a249-75d24325061a
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 2a207f15e7c5b678368eeb54e8452638ff5a01ef
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/08/2018
---
# <a name="use-a-microsoft-intune-custom-profile-to-create-a-per-app-vpn-profile-for-android-devices"></a>Utilizar um perfil personalizado do Microsoft Intune para criar um perfil VPN por aplicação para dispositivos Android

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Pode criar um perfil VPN por aplicação para dispositivos Android 5.0 e posteriores geridos pelo Intune. Primeiro, crie um perfil de VPN que utilize o tipo de ligação Pulse Secure. Em seguida, crie uma política de configuração personalizada que associe o perfil de VPN a aplicações específicas.

Depois de atribuir a política ao dispositivo Android ou aos grupos de utilizadores, os utilizadores devem iniciar a VPN do PulseSecure. O PulseSecure permite apenas tráfego das aplicações especificadas para utilizar a ligação VPN aberta.

> [!NOTE]
>
> Apenas o tipo de ligação Pulse Secure é suportado para este perfil.


## <a name="step-1-create-a-vpn-profile"></a>Passo 1: criar um perfil de VPN


1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços** > **Intune**. O Intune encontra-se na secção **Monitorização + Gestão**.
3. No painel **Intune**, selecione **Configuração do dispositivo**.
2. No painel **Configuração do dispositivo**, na secção **Gerir**, selecione **Perfis**.
2. No painel da lista de perfis, selecione **Criar perfil**.
3. No painel **Criar Perfil**, introduza um **Nome** e uma **Descrição** opcional para o perfil de VPN.
4. Na lista pendente **Plataforma**, escolha **Android**.
5. Na lista pendente **Tipo de perfil**, escolha **VPN**.
3. Escolha **Definições** > **Configurar** e, em seguida, configure o perfil de VPN de acordo com as definições em [Como configurar definições de VPN](vpn-settings-configure.md) e em [Definições de VPN do Intune para dispositivos Android](vpn-settings-android.md).

Tome nota do valor **Nome da Ligação** que especificar ao criar o perfil de VPN. Esse nome será necessário no próximo passo. Por exemplo, **MyAppVpnProfile**.

## <a name="step-2-create-a-custom-configuration-policy"></a>Passo 2: criar uma política de configuração personalizada

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços** > **Intune**. O Intune encontra-se na secção **Monitorização + Gestão**.
3. No painel **Intune**, selecione **Configuração do dispositivo**.
2. No painel **Configuração do dispositivo**, na secção **Gerir**, selecione **Perfis**.
3. No painel Perfis, clique em **Criar Perfil**.
4. No painel **Criar Perfil**, introduza um **Nome** e uma **Descrição** para o perfil personalizado.
5. Na lista pendente **Plataforma**, escolha **Android**.
6. Na lista pendente **Tipo de perfil**, escolha **Personalizado**.
7. Escolha **Definições** > **Configurar**.
3. No painel **Definições OMA-URI personalizadas**, selecione **Adicionar**.
    - Introduza um nome para a definição.
    - Para **OMA-URI**, especifique esta cadeia: **./Vendor/MSFT/VPN/Profile/*Nome*/PackageList**, em que *Nome* é o nome do perfil VPN que anotou no Passo 1. Neste exemplo, a cadeia seria **./Vendor/MSFT/VPN/Profile/MyAppVpnProfile/PackageList**.
    - Para **Tipo de dados**, especifique **Cadeia**.
    - Para **Valor**, crie uma lista separada por ponto e vírgula dos pacotes a associar ao perfil. Por exemplo, se pretender que o Excel e o browser Google Chrome utilizem a ligação VPN, introduza **com.microsoft.office.excel;com.android.chrome**.

![Exemplo de política personalizada de VPN por aplicação Android](./media/android_per_app_vpn_oma_uri.png)

### <a name="set-your-app-list-to-blacklist-or-whitelist-optional"></a>Definir a lista de aplicações como lista de bloqueados ou lista de permitidos (opcional)
  Pode especificar uma lista de aplicações que *não* utilize a ligação VPN com o valor **BLACKLIST**. Todas as outras aplicações são ligadas através da VPN.
Em alternativa, pode utilizar o valor **WHITELIST** para especificar uma lista de aplicações que *possa* utilizar a ligação VPN. As aplicações que não estejam na lista não são ligadas através da VPN.
  1.    No painel **Definições OMA-URI personalizadas**, selecione **Adicionar**.
  2.    Introduza um nome para a definição.
  3.    Para **OMA-URI**, utilize esta cadeia: **./Vendor/MSFT/VPN/Profile/*Nome*/Mode**, em que *Nome* é o nome do perfil VPN que anotou no Passo 1. No nosso exemplo, a cadeia seria **./Vendor/MSFT/VPN/Profile/MyAppVpnProfile/Mode**.
  4.    Para **Tipo de dados**, especifique **Cadeia**.
  5.    Para **Valor**, introduza **BLACKLIST** ou **WHITELIST**.



## <a name="step-3-assign-both-policies"></a>Passo 3: atribuir ambas as políticas

Utilize as instruções em [Como atribuir perfis de dispositivo](device-profile-assign.md) para atribuir ambos os perfis aos utilizadores ou dispositivos obrigatórios.
