---
title: Inscrição no Intune configuração do Android Enterprise dispositivos totalmente geridos
titleSuffix: Microsoft Intune
description: Saiba como inscrever dispositivos Android Enterprise totalmente geridos no Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 1/15/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9edfa2ec7a408f512d4cb0b99a468db0b29f5868
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/23/2019
ms.locfileid: "66044194"
---
# <a name="set-up-intune-enrollment-of-android-enterprise-fully-managed-devices-preview"></a>Configurar o Intune inscrição do Android Enterprise totalmente dispositivos geridos (pré-visualização)

Dispositivos do Android Enterprise totalmente gerido são dispositivos pertencentes à empresa associados a um único utilizador e a utilização de utilizado exclusivamente para o trabalho e pessoal não. Os administradores podem gerir todo o dispositivo e impor controlos de política indisponíveis para desempenhar perfis, tais como:
- Permitir instalação de aplicações apenas a partir do Google Play gerido
- bloquear a desinstalação de aplicações geridas
- impedir os utilizadores de dispositivos de reposição de fábrica e assim por diante.

O Intune ajuda-o a implementar aplicações e dispositivos geridos de definições para dispositivos Android Enterprise, incluindo totalmente o Android Enterprise. Para obter detalhes específicos sobre o Android Enterprise, veja [Android Enterprise requirements](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012) (Requisitos empresariais do Android).

## <a name="technical-requirements"></a>Requisitos técnicos

Tem de ter um inquilino do Intune autónomo para gerir dispositivos Android Enterprise totalmente gerido. Gestão de dispositivos totalmente gerida não está disponível em qualquer um dos modos de híbridas (Configuration Manager-ligado) ou na consola de gestão legada do Silverlight.

Dispositivos têm de cumprir estes requisitos para ser gerido como uma empresa Android totalmente gerido de dispositivo:

- Versão do SO Android 5.1 e posterior.
- Dispositivos têm de executar uma compilação do Android que tem conectividade do Google Mobile Services (GMS). Os dispositivos têm de ter os GMS disponíveis e têm de conseguir ligar-se aos mesmos.

Não existe nenhuma restrição nos fabricante de dispositivo/OEM forem cumpridos os requisitos acima.

## <a name="set-up-android-enterprise-fully-managed-device-management"></a>Configurar a gestão de dispositivos Android Enterprise totalmente gerido

Para configurar o Android Enterprise totalmente geridos gestão de dispositivos, siga estes passos:

1. Para se preparar para gerir dispositivos móveis, terá [definir a autoridade de gestão (MDM) do dispositivo móvel para **Microsoft Intune**](mdm-authority-set.md). Este item só é definido uma vez, quando está a configurar pela primeira vez o Intune para a gestão de dispositivos móveis.
2. [Ligue a sua conta do inquilino do Intune à sua conta do Android Enterprise](connect-intune-android-enterprise.md).
3. [Permitir que os dispositivos do utilizador pertencentes à empresa](#enable-corporate-owned-user-devices)
4. [Inscrever os dispositivos totalmente geridos](#enroll-the-fully-managed-devices).

### <a name="enable-corporate-owned-user-devices"></a>Permitir que os dispositivos pertencentes à empresa de utilizador empresarial

1. Vá para o [portal do Intune](https://portal.azure.com) e escolha **inscrição de dispositivos** > **inscrição de dispositivos Android** > **pertencente à empresa, totalmente dispositivos de utilizador (pré-visualização) geridos**.
2. Sob **permitir que os utilizadores a inscrição de dispositivos do utilizador pertencentes**, escolha **Sim**.

Quando esta definição está definida como **Sim**, fornece-lhe um token de inscrição (uma cadeia aleatória) e um código QR para o seu inquilino do Intune. Este token de inscrição única é válido para todos os seus utilizadores e não expira. Consoante o SO Android e a versão do dispositivo, pode utilizar o token ou código QR para inscrever o dispositivo de quiosque.

## <a name="enroll-the-fully-managed-devices"></a>Inscrever os dispositivos totalmente geridos
Agora, pode [inscrever os dispositivos totalmente geridos](android-dedicated-devices-fully-managed-enroll.md).

## <a name="considerations-for-this-preview-feature"></a>Considerações para esta funcionalidade de pré-visualização
Esta pré-visualização pública inclui um conjunto básico de recursos para o Android Enterprise totalmente geridos pelo conjunto de solução. Queremos ouvi sobre a sua experiência com as funcionalidades de pré-visualização usando qualquer um dos seus canais de comunicação atual para a equipe (como [UserVoice](https://microsoftintune.uservoice.com/forums/291681-ideas?category_id=210853)).

Esta pré-visualização suporta as seguintes funcionalidades para Android Enterprise dispositivos totalmente geridos:
- Inscrição de dispositivo com NFC, entrada de token, código QR e Zero Touch
- Configuração do dispositivo para grupos de utilizadores
- Configuração para grupos de utilizadores e de distribuição de aplicações


Ao utilizar estas funcionalidades de pré-visualização, tenha em atenção o seguinte:
- Funcionalidades em pré-visualização não são recomendadas para a missão crítica ou implementações de produção. 
- Funcionalidades de pré-visualização são implementadas para os padrões de produção do Microsoft Intune. No entanto, nem todas as funcionalidades do Intune estão disponíveis para utilização com dispositivos de utilizador do Android Enterprise totalmente gerido. Funcionalidades de pré-visualização claramente são rotuladas com "(pré-visualização)" na consola do Intune. 
- As funcionalidades de pré-visualização são totalmente compatíveis através dos canais de suporte do Intune habituais.
- Inscrição de dispositivos Android Enterprise totalmente gerido com o Samsung Knox Mobile inscrição não é suportada em pré-visualização. 
- Utilização do Portal da empresa do Intune aplicação não é suportada no Android Enterprise totalmente os dispositivos geridos. 
- Funcionalidades do Intune, como o acesso condicional, as políticas de proteção de aplicações e certificado de implementação não são suportados em pré-visualização. 
- Filtragem de grupo de dispositivos de qualquer aplicação ou o perfil não é suportada em pré-visualização. Filtragem de grupo usuário só é suportada. 
- Não existe nenhuma interface do Usuário de primeira classe para a configuração de e-mail, Wi-Fi ou VPN. Utilize políticas de configuração de aplicações para configurar as definições de configuração de aplicações suportadas.

## <a name="next-steps"></a>Passos Seguintes
- [Adicionar o que Android Enterprise totalmente gerido de políticas de configuração do dispositivo](device-restrictions-android-for-work.md#device-owner-only)
- [Configurar políticas de configuração de aplicações para Android Enterprise dispositivos totalmente geridos](app-configuration-policies-use-android.md)

