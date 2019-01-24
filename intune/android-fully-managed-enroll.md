---
title: Inscrição no Intune configuração para Android dispositivos totalmente geridos
titlesuffix: Microsoft Intune
description: Saiba como inscrever Android totalmente gerido de dispositivos no Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 1/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.openlocfilehash: 45c1d1f293454b32b97c8147f08809565714743a
ms.sourcegitcommit: 911923e9fe0eed52b1c93e400f776956835e582f
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/17/2019
ms.locfileid: "54387092"
---
# <a name="set-up-intune-enrollment-of-android-fully-managed-devices-preview"></a>Configurar o Intune inscrição do Android totalmente dispositivos geridos (pré-visualização)

Android dispositivos totalmente geridos são dispositivos pertencentes à empresa associados a um único utilizador e a utilização de utilizado exclusivamente para o trabalho e pessoal não. Os administradores podem gerir todo o dispositivo e impor controlos de política indisponíveis para desempenhar perfis, tais como:
- Permitir instalação de aplicações apenas a partir do Google Play gerido
- bloquear a desinstalação de aplicações geridas
- impedir os utilizadores de dispositivos de reposição de fábrica e assim por diante.

O Intune ajuda-o a implementar aplicações e definições para dispositivos Android enterprise, incluindo Android totalmente geridas de dispositivos. Para obter detalhes específicos sobre o Android Enterprise, veja [Android enterprise requirements (Requisitos empresariais do Android)](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012).

## <a name="technical-requirements"></a>Requisitos técnicos

Tem de ter do Intune dispositivos geridos pelo inquilino autónomo para gerir totalmente o Android. Gestão de devcie totalmente gerida não está disponível em qualquer um dos modos de híbrida (ligado SCCM) ou na consola de gestão legada do Silverlight.

Dispositivos têm de cumprir estes requisitos para ser gerido como um dispositivo Android gerido totalmente o dispositivo:

- SO Android versão 6.0 e superior.
- Dispositivos têm de executar uma compilação do Android que tem conectividade do Google Mobile Services (GMS). Os dispositivos têm de ter os GMS disponíveis e têm de conseguir ligar-se aos mesmos.

Não existe nenhuma restrição nos fabricante de dispositivo/OEM forem cumpridos os requisitos acima.

## <a name="set-up-android-fully-managed-device-management"></a>Configurar o Android totalmente geridos gestão de dispositivos

Para configurar o Android totalmente geridos gestão de dispositivos, siga estes passos:

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
Esta pré-visualização pública inclui um conjunto básico de recursos para o Android totalmente geridos pelo conjunto de solução. Queremos ouvi sobre a sua experiência com as funcionalidades de pré-visualização usando qualquer um dos seus canais de comunicação atual para a equipe (como [UserVoice](https://microsoftintune.uservoice.com/forums/291681-ideas?category_id=210853)).

Esta pré-visualização suporta as seguintes funcionalidades para Android dispositivos totalmente geridos:
- Inscrição de dispositivo com NFC, entrada de token, código QR e Zero Touch
- Configuração do dispositivo para grupos de utilizadores
- Configuração para grupos de utilizadores e de distribuição de aplicações


Ao utilizar estas funcionalidades de pré-visualização, tenha em atenção o seguinte:
- Funcionalidades em pré-visualização não são recomendadas para a missão crítica ou implementações de produção. 
- Funcionalidades de pré-visualização são implementadas para os padrões de produção do Microsoft Intune. No entanto, nem todas as funcionalidades do Intune estão disponíveis para utilização com o Android totalmente geridos os dispositivos dos utilizadores. Funcionalidades de pré-visualização claramente são rotuladas com "(pré-visualização)" na consola do Intune. 
- As funcionalidades de pré-visualização são totalmente compatíveis através dos canais de suporte do Intune habituais.
- Inscrição Android totalmente geridos dispositivos com o Samsung Knox inscrição móvel não é suportada em pré-visualização. 
- Utilização do Portal da empresa do Intune aplicação não é totalmente suportada no Android dispositivos geridos. 
- Funcionalidades do Intune, como o acesso condicional, as políticas de proteção de aplicações e certificado de implementação não são suportados em pré-visualização. 
- Filtragem de grupo de dispositivos de qualquer aplicação ou o perfil não é suportada em pré-visualização. Filtragem de grupo usuário só é suportada. 
- Não existe nenhuma interface do Usuário de primeira classe para a configuração de e-mail, Wi-Fi ou VPN. Utilize políticas de configuração de aplicações para configurar as definições de configuração de aplicações suportadas.

## <a name="next-steps"></a>Passos Seguintes
- [Adicionar que Android totalmente gerido de políticas de configuração do dispositivo](device-restrictions-android-for-work.md#device-owner-only)
- [Configurar políticas de configuração de aplicações para Android dispositivos totalmente geridos](app-configuration-policies-use-android.md)
