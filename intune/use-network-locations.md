---
title: Vincular dispositivos Android através da localização de rede no Microsoft Intune – Azure | Microsoft Docs
description: Crie ou configure localizações de rede para dispositivos Android no Microsoft Intune. Pode marcar dispositivos como não estando em conformidade com base na localização de rede do dispositivo. Se o dispositivo sair da localização de rede, pode bloquear o acesso aos recursos da empresa.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 05/21/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: ayesham
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d2431695f89c9cdf339a0192e27f8140ec042435
ms.sourcegitcommit: 430b290474b11f9df87785b01edc178e6bae2049
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/05/2019
ms.locfileid: "57396233"
---
# <a name="use-locations-network-fence-in-intune"></a>Utilizar Localizações (barreira de rede) no Intune

Pode bloquear o acesso a uma rede empresarial se um dispositivo sair de uma localização. A funcionalidade **Localizações** no Intune fornece esta opção. 

Pode criar uma política de conformidade com base na localização de rede, também conhecida como barreira de rede. A política garante que os dispositivos têm de estar ligados a uma rede de trabalho para estarem em conformidade. Esta política pode ser utilizada com as políticas de acesso condicional para os dispositivos terem acesso aos recursos de trabalho *apenas* quando estiverem ligados à rede de trabalho. Quando o dispositivo não estiver ligado à rede de trabalho, deixará de estar em conformidade e perderá o acesso aos recursos de trabalho.

Considere o seguinte cenário:

Na sua instalação de fabrico, alguns colaboradores utilizam dispositivos Android. Um colaborador leva o dispositivo Android para fora da instalação ou fábrica. Para ajudar a impedir o acesso não autorizado, pode:

1. Criar uma localização com um intervalo IPv4 chamado **Andar de fabrico**.
2. Criar uma política de conformidade que exija que estes dispositivos estejam ligados à sua rede empresarial e atribuir esta política.
3. Se o dispositivo sair da instalação de fabrico, será considerado como não estando em conformidade e deixará de ter acesso aos recursos empresariais.

Além disso, pode adicionar [ações de não conformidade](#configure-the-actions-for-noncompliance). Quando o dispositivo voltar ao local e à localização de rede, recuperará o acesso aos recursos empresariais.

## <a name="prerequisites"></a>Pré-requisitos

Para criar uma política de conformidade com base na localização:

- Crie uma localização de rede como intervalos de rede IPV4 para o servidor de Gateway, servidor DHCP e/ou servidor DNS ao qual os dispositivos se ligam
- Crie a política de conformidade que utiliza estas localizações e define a ação a realizar quando o dispositivo deixar de estar ligado à localização de rede
- Dispositivos com o Android 6.0 e superior, com a aplicação Portal da Empresa atualizada

## <a name="create-a-location"></a>Criar uma localização

1. No Intune, selecione **Conformidade do dispositivo** > **Localizações** > **Criar**.

2. Introduza as seguintes propriedades:  

   - Necessário. Dê um **Nome** à localização, como **Andar de fabrico** ou **Edifício 44-protegido**.
   - Opcional. Introduza um **Intervalo IPv4** com notação CIDR (Classless Interdomain Routing), como `aaa.bbb.ccc.ddd/n`.
   - Opcional. Introduza o endereço do **Gateway IPv4**, como `aaa.bbb.ccc.ddd`.
   - Opcional. Introduza o endereço do **Servidor DHCP IPv4**, como `aaa.bbb.ccc.ddd`.
   - Opcional. Introduza uma lista de endereços **Servidores de DNS IPv4**. Esta definição utiliza a **correspondência de subconjuntos**. Se os Servidores de DNS IPv4 no dispositivo forem subconjuntos dos valores definidos, o dispositivo será considerado como DENTRO da barreira. Certifique-se de que introduz um endereço por linha, como:  
     `aaa.bbb.ccc.ddd`  
     `aaa.bbb.ccc.ddd`
   - Opcional. Introduza uma lista de **Sufixos DNS**. Esta definição utiliza a **correspondência de subconjuntos**. Se os Sufixos DNS no dispositivo forem subconjuntos dos valores definidos, o dispositivo será considerado como DENTRO da barreira. Certifique-se de que introduz um nome de domínio em cada linha, como:  
     `contoso.com`  
     `contoso.org`

3. **Guarde** as suas alterações.

## <a name="create-the-location-compliance-policy"></a>Criar a política de conformidade de localização

Quando criar a política de conformidade, selecione **Android** para a **Plataforma**. Em **Localizações**, pode selecionar uma ou mais das localizações de rede que adicionou. Estas localizações fazem parte da barreira de rede que está a criar para os seus dispositivos.

[Criar a política de conformidade com base na localização de rede](compliance-policy-create-android.md#locations) fornece algumas orientações.

## <a name="configure-the-actions-for-noncompliance"></a>Configurar as ações de não conformidade

Depois de criar a política de conformidade, a ação predefinida de não conformidade é aplicada ao dispositivo. Pode adicionar mais ações. Por exemplo, adicione uma ação que envia um e-mail ao utilizador quando o dispositivo deixar de estar em conformidade com as localizações.

[Adicionar as ações de não conformidade](actions-for-noncompliance.md) fornece algumas orientações.

## <a name="company-portal-app"></a>Aplicação Portal da Empresa

Quando o dispositivo estiver ligado às suas localizações, será apresentado como estando em conformidade na aplicação Portal da Empresa. Quando o dispositivo não estiver ligado a uma das suas localizações, será apresentado como não estando em conformidade.

## <a name="next-steps"></a>Passos Seguintes
[Monitorizar as políticas de conformidade de dispositivos](compliance-policy-monitor.md)  
[Introdução às políticas de conformidade](device-compliance-get-started.md)
