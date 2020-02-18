---
title: Gerir dispositivos de perfil de trabalho Android Enterprise no Microsoft Intune
titleSuffix: ''
description: O Microsoft Intune gere dispositivos de perfil de trabalho Android Enterprise para fornecer capacidades de gestão e privacidade adicionais quando as pessoas usam os seus dispositivos Android pessoais para trabalhar.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 2cc3c960-1fdd-47ca-a693-420d47b403de
ms.reviewer: chmaguir
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6941b3b79dd690c9861c8efead7f525e56e2b350
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/17/2020
ms.locfileid: "77415405"
---
# <a name="manage-android-work-profile-devices-with-intune"></a>Gerir dispositivos com perfil de trabalho do Android com o Intune

O Android Enterprise oferece um conjunto de opções de inscrição que fornecem aos utilizadores as funcionalidades mais atualizadas e seguras. A inscrição no perfil de trabalho do Android Enterprise permite um conjunto de funcionalidades e serviços que separam aplicações pessoais e dados de aplicações de trabalho e dados. Também fornece capacidades de gestão e privacidade adicionais quando as pessoas usam os seus dispositivos Android pessoais para trabalhar. 

## <a name="supported-devices"></a>Dispositivos suportados

As capacidades de gestão do Android Enterprise dependem de funcionalidades que fazem parte de sistemas operativos Android mais recentes. Para dispositivos que não suportam o Android Enterprise, a gestão convencional do Android continua disponível. Para mais informações, consulte [os requisitos do Android Enterprise](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012).

## <a name="onboarding"></a>Integração

Antes de inscrever dispositivos de perfil de trabalho Android Enterprise, deve completar algumas etapas de embarque. Estes passos estabelecem uma ligação entre o seu inquilino Intune e o Managed Google Play. Para mais informações, consulte [Enable a inscrição de dispositivos de perfil de trabalho Android Enterprise](android-work-profile-enroll.md).

## <a name="work-profile-management"></a>Gestão de perfis de trabalho

Quando gere um dispositivo de perfil de trabalho Android Enterprise com o Intune, não gere todo o dispositivo. As capacidades de gestão só afetam o perfil de trabalho que é criado no dispositivo durante a inscrição. Todas as aplicações implementadas no dispositivo com o Intune são instaladas no perfil de trabalho. Os ícones das aplicações no perfil de trabalho são diferenciados dos das aplicações pessoais no dispositivo. Todos os dados e aplicações para Android externos à parte Android Enterprise do dispositivo permanecem pessoais e sob controlo do utilizador final. Os utilizadores podem instalar qualquer aplicação na parte pessoal do dispositivo. Os administradores podem gerir e monitorizar aplicações e ações com âmbito definido para o perfil de trabalho.

O Intune oferece um conjunto de definições gerais incorporadas que pode configurar em dispositivos com perfil de trabalho do Android. Para obter mais informações, veja [Android work profile device policy settings](../protect/compliance-policy-create-android-for-work.md) (Definições de política de dispositivo com perfil de trabalho do Android).

## <a name="app-publishing-and-distribution"></a>Publicação e distribuição de aplicações

O Google Play gerido é parte integrante da distribuição e gestão de aplicações Android Enterprise. Todas as aplicações implementadas para dispositivos de perfil de trabalho Android Enterprise no perfil de trabalho provêm do serviço Managed Google Play. Para gerir e implementar aplicações na Play Store, inicie sessão no site do Google Play com as credenciais de administrador da empresa para a gestão do Google. Pode aprovar aplicações para implementação do Android Enterprise para que apareçam nos perfis de trabalho dos dispositivos. Estas aplicações são sincronizadas com a consola do Intune, onde podem ser implementadas e geridas através do Intune. As aplicações de linha de negócio (LOB) desenvolvidas pela sua organização têm de ser publicadas na Google Play Store Gerida através da consola de publicação de aplicações Android do Google. As aplicações de linha de negócio têm de ser configuradas na consola de publicação de aplicações Android para restringir o acesso à sua organização.

As aplicações podem ser instaladas sem a interação do utilizador e sem exigir que o utilizador permita a **Instalação de Origens Desconhecidas**. Para procurar e instalar aplicações opcionais ou disponíveis, o utilizador pode procurar na Google Play for Work Store no dispositivo. Para mais informações, consulte [as aplicações de atribuição para dispositivos](../apps/apps-add-android-for-work.md)de perfil de trabalho Android Enterprise com Intune .

## <a name="app-configuration"></a>Configuração de aplicações

O Android Enterprise fornece infraestruturas para implementar valores de configuração de apps para apps que as suportem. Ao especificar valores de configuração para aplicações de trabalho, garante que estão devidamente configuradas quando os utilizadores as iniciarem pela primeira vez. O suporte para configuração de aplicações requer que os programadores de aplicações criem as respetivas aplicações para Android especificamente para suportar valores de configuração geridos. Se o fizerem, pode utilizar o Intune para especificar e aplicar essas definições de configuração. Para obter mais informações, veja [Adicionar políticas de configuração da aplicação para dispositivos Android geridos](../apps/app-configuration-policies-use-android.md).

## <a name="email-configuration"></a>Configuração de e-mail

O Android Enterprise não fornece uma aplicação de e-mail padrão ou objeto de perfil de e-mail nativo como os fornecidos pelo iOS/iPadOS. As configurações de e-mail podem definir-se ao aplicar as definições de configuração de aplicações às aplicações de e-mail que as suportem. O Gmail e o Nine Work são duas aplicações clientes Exchange ActiveSync (EAS) na Play Store que suportam a configuração com a configuração da aplicação Android Enterprise.

O Intune disponibiliza modelos de configuração para as aplicações Gmail e Nine Work quando são geridas como aplicações de trabalho. Outras aplicações de e-mail que suportem os perfis de configuração de aplicações podem ser configuradas através das políticas de configuração de aplicações móveis.

Se estiver a utilizar o Exchange ActiveSync Conditional Access para um dispositivo de perfil de trabalho Android Enterprise, considere utilizar a aplicação de e-mail do Gmail ou do Nine Work. A aplicação Microsoft Outlook para Android, ou qualquer outra aplicação de e-mail que utilize autenticação moderna através da ADAL, também é suportada. Para obter mais informações, veja [Como configurar definições de e-mail no Microsoft Intune](../configuration/email-settings-configure.md).

## <a name="app-protection-policies"></a>Políticas de proteção de aplicações

As políticas de proteção de aplicações aplicadas são totalmente suportadas no perfil de trabalho e no perfil pessoal. Pode publicar aplicações de linha de negócio na consola de publicação de aplicações Android em https://play.google.com/apps/publish. Esta consola inclui uma opção que permite tornar as aplicações privadas para a sua organização. Para mais informações, consulte Adicionar uma política de conformidade de [dispositivos para dispositivos](../protect/compliance-policy-create-android-for-work.md)de perfil de trabalho Android Enterprise em Intune . Para obter informações gerais sobre políticas de proteção de aplicações, veja [O que são as políticas de proteção de aplicações?](../apps/app-protection-policy.md)

## <a name="vpn-profiles"></a>Perfis VPN

O suporte de VPN é semelhante aos perfis de VPN em Android. Os mesmos fornecedores VPN e opções básicas de configuração estão disponíveis para gestão Android Enterprise com duas diferenças:

- **VPN com âmbito de perfil de trabalho** – as ligações VPN estão limitadas às aplicações implementadas para o perfil de trabalho. Apenas aplicações geridas pelo Android Enterpise podem utilizar a ligação VPN. As aplicações pessoais no dispositivo não podem utilizar uma ligação VPN gerida. Para mais informações, consulte [as definições de VPN da Empresa Android](../configuration/vpn-settings-android-enterprise.md).

- **VPN específica da aplicação** – a VPN específica da aplicação pode ser configurada no Intune se o fornecedor de VPN suportar:
  - a configuração da VPN específica da aplicação
  - a capacidade de configurar VPN por app através do perfil de configuração da aplicação Android Enterprise.
  Para obter mais informações, veja [Utilizar um perfil personalizado do Microsoft Intune para criar um perfil VPN por aplicação para dispositivos Android](../configuration/android-pulse-secure-per-app-vpn.md).

## <a name="certificate-profiles"></a>Perfis de certificados

As mesmas opções de configuração de perfil de certificado que estão disponíveis para gestão android estão disponíveis em dispositivos de perfil de trabalho Android Enterprise. O Android Enterprise fornece APIs de gestão de certificados melhorados. A gestão de certificados melhorada fornece as seguintes funcionalidades:

- Garante que a implementação de certificados é automática e totalmente integrada para o utilizador.
- Garante que os certificados implementados são removidos após um dispositivo ser extinto do Intune e o perfil de trabalho ser removido.
- Fornece mensagens melhoradas que informam os utilizadores de que o certificado foi implementado e configurado pelo respetivo departamento de TI através do serviço de gestão.

Para obter mais informações, veja [Configurar um perfil de certificado para os seus dispositivos no Microsoft Intune](../protect/certificates-configure.md).

## <a name="wi-fi-profiles"></a>Perfis de Wi-Fi

Os perfis Wi-Fi geridos pelo Android Enterprise são removidos quando o dispositivo é retirado de Intune e o perfil de trabalho é eliminado. Para obter mais informações, veja [Como configurar definições de Wi-Fi no Microsoft Intune](../configuration/wi-fi-settings-configure.md).

## <a name="next-steps"></a>Próximos passos
- [Inscrever dispositivos Android](android-enroll.md)
- [Atribuir aplicativos a dispositivos de perfil de trabalho Android Enterprise com Intune](../apps/apps-add-android-for-work.md)
