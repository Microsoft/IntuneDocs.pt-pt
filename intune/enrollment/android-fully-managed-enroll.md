---
title: Configurar o registro do Intune para dispositivos Android Enterprise totalmente gerenciados
titleSuffix: Microsoft Intune
description: Saiba como registrar dispositivos Android Enterprise totalmente gerenciados no Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 1/15/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: priyar
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 755aefb955c2d30652434f2bd2e91981145fc56f
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72505604"
---
# <a name="set-up-intune-enrollment-of-android-enterprise-fully-managed-devices"></a>Configurar o registro do Intune de dispositivos Android Enterprise totalmente gerenciados 

Dispositivos Android Enterprise totalmente gerenciados são dispositivos de propriedade corporativa associados a um único usuário e usados exclusivamente para uso de trabalho e não pessoal. Os administradores podem gerenciar todo o dispositivo e impor controles de política não disponíveis para perfis de trabalho, como:
- Permitir instalação de aplicativo somente de Google Play gerenciados.
- Bloquear a desinstalação de aplicativos gerenciados.
- Impedir que os usuários redefinam dispositivos e assim por diante.

O Intune ajuda você a implantar aplicativos e configurações em dispositivos Android Enterprise, incluindo dispositivos Android Enterprise totalmente gerenciados. Para obter detalhes específicos sobre o Android Enterprise, veja [Android Enterprise requirements](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012) (Requisitos empresariais do Android).

## <a name="technical-requirements"></a>Requisitos técnicos

Você deve ter um locatário autônomo do Intune para gerenciar dispositivos Android Enterprise totalmente gerenciados. O gerenciamento de dispositivo totalmente gerenciado não está disponível no modo híbrido (conectado ao Configuration Manager) ou no console de gerenciamento do Silverlight herdado.

Os dispositivos devem atender a esses requisitos para serem gerenciados como um dispositivo Android Enterprise totalmente gerenciado:

- Android OS versão 6,0 e posteriores.
- Os dispositivos devem executar uma compilação do Android que tenha conectividade de serviços móveis do Google (GMS). Os dispositivos têm de ter os GMS disponíveis e têm de conseguir ligar-se aos mesmos.

Não há nenhuma restrição no fabricante/OEM do dispositivo se os requisitos acima forem atendidos.

## <a name="set-up-android-enterprise-fully-managed-device-management"></a>Configurar o gerenciamento de dispositivo totalmente gerenciado do Android Enterprise

Para configurar o gerenciamento de dispositivo totalmente gerenciado do Android Enterprise, siga estas etapas:

1. Para se preparar para gerenciar dispositivos móveis, você deve [definir a autoridade de MDM (gerenciamento de dispositivo móvel) como **Microsoft Intune**](../fundamentals/mdm-authority-set.md). Este item só é definido uma vez, quando está a configurar pela primeira vez o Intune para a gestão de dispositivos móveis.
2. [Ligue a sua conta do inquilino do Intune à sua conta do Android Enterprise](connect-intune-android-enterprise.md).
3. [Habilitar dispositivos de usuários de propriedade corporativa](#enable-corporate-owned-user-devices)
4. [Registre os dispositivos totalmente gerenciados](#enroll-the-fully-managed-devices).

### <a name="enable-corporate-owned-user-devices"></a>Habilitar dispositivos de usuário de propriedade corporativa

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) e escolha **registro de dispositivo** > **registro Android** > **dispositivos de usuário totalmente gerenciados e de propriedade corporativa**.
2. Em **permitir que os usuários registrem dispositivos de usuário de propriedade corporativa**, escolha **Sim**.

> [!NOTE]
> Se você tiver uma política de acesso condicional do Azure AD definida que usa o *exigir que um dispositivo seja marcado como* controle em conformidade e se aplicar a **todos os aplicativos de nuvem**, **Android** e **navegadores** , você deverá excluir o **Microsoft Intune** aplicativo de nuvem desta política. Isso ocorre porque os processos de instalação do Android usam uma guia Chrome para autenticar seus usuários durante o registro. Para obter mais informações, consulte [documentação de acesso condicional do Azure ad](https://docs.microsoft.com/azure/active-directory/conditional-access/).

Quando essa configuração é definida como **Sim**, ela fornece um token de registro (uma cadeia de caracteres aleatória) e um código QR para seu locatário do Intune. Esse único token de registro é válido para todos os usuários e não expirará. Dependendo do sistema operacional Android e da versão do dispositivo, você pode usar o token ou o código QR para registrar o dispositivo.

## <a name="enroll-the-fully-managed-devices"></a>Registrar os dispositivos totalmente gerenciados
Agora você pode [registrar seus dispositivos totalmente gerenciados](android-dedicated-devices-fully-managed-enroll.md).

## <a name="next-steps"></a>Próximos passos
- [Adicionar políticas de configuração de dispositivo do Android Enterprise totalmente gerenciado](../configuration/device-restrictions-android-for-work.md#device-owner-only)
- [Configurar políticas de configuração de aplicativo para dispositivos Android Enterprise totalmente gerenciados](../apps/app-configuration-policies-use-android.md)

