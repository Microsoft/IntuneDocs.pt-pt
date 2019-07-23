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
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 54d9fa1016ff39fcf1e7da9c21391ce70f7acaac
ms.sourcegitcommit: e451295ca3ee3efc31bf9ee360e599b28ef643ea
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/12/2019
ms.locfileid: "67863090"
---
# <a name="set-up-intune-enrollment-of-android-enterprise-fully-managed-devices-preview"></a>Configurar o registro do Intune de dispositivos Android Enterprise totalmente gerenciados (versão prévia)

Dispositivos Android Enterprise totalmente gerenciados são dispositivos de propriedade corporativa associados a um único usuário e usados exclusivamente para uso de trabalho e não pessoal. Os administradores podem gerenciar todo o dispositivo e impor controles de política não disponíveis para perfis de trabalho, como:
- Permitir instalação de aplicativo somente de Google Play gerenciados.
- Bloquear a desinstalação de aplicativos gerenciados.
- Impedir que os usuários redefinam dispositivos e assim por diante.

O Intune ajuda você a implantar aplicativos e configurações em dispositivos Android Enterprise, incluindo dispositivos Android Enterprise totalmente gerenciados. Para obter detalhes específicos sobre o Android Enterprise, veja [Android Enterprise requirements](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012) (Requisitos empresariais do Android).

## <a name="technical-requirements"></a>Requisitos técnicos

Você deve ter um locatário autônomo do Intune para gerenciar dispositivos Android Enterprise totalmente gerenciados. O gerenciamento de dispositivo totalmente gerenciado não está disponível no modo híbrido (conectado ao Configuration Manager) ou no console de gerenciamento do Silverlight herdado.

Os dispositivos devem atender a esses requisitos para serem gerenciados como um dispositivo Android Enterprise totalmente gerenciado:

- Versão do SO Android 5.1 e posterior.
- Os dispositivos devem executar uma compilação do Android que tenha conectividade de serviços móveis do Google (GMS). Os dispositivos têm de ter os GMS disponíveis e têm de conseguir ligar-se aos mesmos.

Não há nenhuma restrição no fabricante/OEM do dispositivo se os requisitos acima forem atendidos.

## <a name="set-up-android-enterprise-fully-managed-device-management"></a>Configurar o gerenciamento de dispositivo totalmente gerenciado do Android Enterprise

Para configurar o gerenciamento de dispositivo totalmente gerenciado do Android Enterprise, siga estas etapas:

1. Para se preparar para gerenciar dispositivos móveis, você deve [definir a autoridade de MDM (gerenciamento de dispositivo móvel) como **Microsoft Intune**](mdm-authority-set.md). Este item só é definido uma vez, quando está a configurar pela primeira vez o Intune para a gestão de dispositivos móveis.
2. [Ligue a sua conta do inquilino do Intune à sua conta do Android Enterprise](connect-intune-android-enterprise.md).
3. [Habilitar dispositivos de usuários de propriedade corporativa](#enable-corporate-owned-user-devices)
4. [Registre os dispositivos totalmente gerenciados](#enroll-the-fully-managed-devices).

### <a name="enable-corporate-owned-user-devices"></a>Habilitar dispositivos de usuário de propriedade corporativa

1. Conecte-se ao [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) e escolha **registro** > de dispositivo registro do**Android** > **dispositivos de usuário totalmente gerenciados (versão prévia)** .
2. Em **permitir que os usuários registrem dispositivos de usuário de propriedade corporativa**, escolha **Sim**.

> [!NOTE]
> Se você tiver uma política de acesso condicional do Azure AD definida que usa o *exigir que um dispositivo seja marcado como* controle em conformidade e se aplicar a **todos os aplicativos de nuvem**, **Android** e **navegadores** , você deverá excluir o **Microsoft Intune** aplicativo de nuvem desta política. Isso ocorre porque os processos de instalação do Android usam uma guia Chrome para autenticar seus usuários durante o registro. Para obter mais informações, consulte [documentação de acesso condicional do Azure ad](https://docs.microsoft.com/azure/active-directory/conditional-access/).

Quando essa configuração é definida como **Sim**, ela fornece um token de registro (uma cadeia de caracteres aleatória) e um código QR para seu locatário do Intune. Esse único token de registro é válido para todos os usuários e não expirará. Dependendo do sistema operacional Android e da versão do dispositivo, você pode usar o token ou o código QR para registrar o dispositivo de quiosque.

## <a name="enroll-the-fully-managed-devices"></a>Registrar os dispositivos totalmente gerenciados
Agora você pode [registrar seus dispositivos totalmente gerenciados](android-dedicated-devices-fully-managed-enroll.md).

## <a name="considerations-for-this-preview-feature"></a>Considerações para este recurso de visualização
Essa visualização pública inclui um conjunto principal de recursos para o conjunto de soluções totalmente gerenciadas do Android Enterprise. Queremos saber mais sobre sua experiência usando os recursos de visualização usando qualquer um dos seus canais de comunicação atuais com a equipe (como [UserVoice](https://microsoftintune.uservoice.com/forums/291681-ideas?category_id=210853)).

Esta versão prévia dá suporte aos seguintes recursos para dispositivos Android Enterprise totalmente gerenciados:
- Registro de dispositivo usando NFC, entrada de token, código QR e Zero Touch
- Configuração de dispositivo para grupos de usuários
- Distribuição e configuração de aplicativos para grupos de usuários


Ao usar esses recursos de visualização, tenha em mente o seguinte:
- Os recursos na visualização não são recomendados para implantações de missão crítica ou de produção. 
- Os recursos de visualização são implementados para Microsoft Intune padrões de produção. No entanto, nem todos os recursos do Intune estão disponíveis para uso com dispositivos de usuário totalmente gerenciados do Android Enterprise. Os recursos de visualização são claramente rotulados com "(visualização)" no console do Intune. 
- Os recursos de visualização são totalmente compatíveis com os canais de suporte comuns do Intune.
- Registrar dispositivos Android Enterprise totalmente gerenciados usando o registro móvel Samsung Knox não tem suporte na versão prévia. 
- O uso do aplicativo Portal da Empresa do Intune não tem suporte em dispositivos Android Enterprise totalmente gerenciados. 
- Recursos do Intune como acesso condicional, políticas de proteção de aplicativo e implantação de certificado não têm suporte na visualização. 
- O direcionamento de grupo de dispositivos de qualquer perfil ou aplicativo não tem suporte na visualização. Há suporte apenas para o direcionamento de grupo de usuários. 
- Não há nenhuma interface do usuário de primeira classe para configurar email, WiFi ou VPN. Use as políticas de configuração de aplicativo para definir as definições de configuração de aplicativo com suporte.

## <a name="next-steps"></a>Passos Seguintes
- [Adicionar políticas de configuração de dispositivo do Android Enterprise totalmente gerenciado](device-restrictions-android-for-work.md#device-owner-only)
- [Configurar políticas de configuração de aplicativo para dispositivos Android Enterprise totalmente gerenciados](app-configuration-policies-use-android.md)

