---
title: Gerenciar dispositivos Android Enterprise Work profile no Microsoft Intune
titleSuffix: ''
description: O Microsoft Intune gerencia dispositivos Android Enterprise de perfil de trabalho para fornecer recursos de gerenciamento adicionais e privacidade quando as pessoas usam seus dispositivos Android pessoais para o trabalho.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 2cc3c960-1fdd-47ca-a693-420d47b403de
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3a51951d02d73a0d79f6246dd9502c3c7fe89759
ms.sourcegitcommit: b78793ccbef2a644a759ca3110ea73e7ed6ceb8f
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/16/2019
ms.locfileid: "69550085"
---
# <a name="manage-android-work-profile-devices-with-intune"></a>Gerir dispositivos com perfil de trabalho do Android com o Intune

O Android Enterprise oferece um conjunto de opções de registro que fornecem aos usuários os recursos mais atualizados e seguros. O registro no perfil de trabalho do Android Enterprise permite um conjunto de recursos e serviços que separa aplicativos e dados pessoais de aplicativos e dados de trabalho. Ele também fornece recursos de gerenciamento e privacidade adicionais quando as pessoas usam seus dispositivos Android pessoais para o trabalho. 

## <a name="supported-devices"></a>Dispositivos suportados

Os recursos de gerenciamento do Android Enterprise contam com recursos que fazem parte de sistemas operacionais Android mais recentes. Para dispositivos que não dão suporte ao Android Enterprise, o gerenciamento convencional do Android permanece disponível. Para obter mais informações, consulte [requisitos do Android Enterprise](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012).

## <a name="onboarding"></a>Integração

Antes de registrar dispositivos de perfil de trabalho do Android Enterprise, você deve concluir algumas etapas de integração. Estas etapas estabelecem uma conexão entre o locatário do Intune e o Google Play gerenciado. Para obter mais informações, consulte [habilitar o registro de dispositivos Android Enterprise Work Profile](android-work-profile-enroll.md).

## <a name="work-profile-management"></a>Gestão de perfis de trabalho

Ao gerenciar um dispositivo de perfil de trabalho do Android Enterprise com o Intune, você não gerencia todo o dispositivo. As capacidades de gestão só afetam o perfil de trabalho que é criado no dispositivo durante a inscrição. Todas as aplicações implementadas no dispositivo com o Intune são instaladas no perfil de trabalho. Os ícones das aplicações no perfil de trabalho são diferenciados dos das aplicações pessoais no dispositivo. Todos os dados e aplicações para Android externos à parte Android Enterprise do dispositivo permanecem pessoais e sob controlo do utilizador final. Os utilizadores podem instalar qualquer aplicação na parte pessoal do dispositivo. Os administradores podem gerir e monitorizar aplicações e ações com âmbito definido para o perfil de trabalho.

O Intune oferece um conjunto de definições gerais incorporadas que pode configurar em dispositivos com perfil de trabalho do Android. Para obter mais informações, veja [Android work profile device policy settings](compliance-policy-create-android-for-work.md) (Definições de política de dispositivo com perfil de trabalho do Android).

## <a name="app-publishing-and-distribution"></a>Publicação e distribuição de aplicações

O Google Play gerenciado é parte integrante da distribuição e do gerenciamento de aplicativos do Android Enterprise. Todos os aplicativos implantados em dispositivos Android Enterprise de perfil de trabalho no perfil de trabalho são provenientes do serviço de Google Play gerenciado. Para gerir e implementar aplicações na Play Store, inicie sessão no site do Google Play com as credenciais de administrador da empresa para a gestão do Google. Você pode aprovar aplicativos para a implantação do Android Enterprise para que eles apareçam nos perfis de trabalho dos dispositivos. Estas aplicações são sincronizadas com a consola do Intune, onde podem ser implementadas e geridas através do Intune. As aplicações de linha de negócio (LOB) desenvolvidas pela sua organização têm de ser publicadas na Google Play Store Gerida através da consola de publicação de aplicações Android do Google. As aplicações de linha de negócio têm de ser configuradas na consola de publicação de aplicações Android para restringir o acesso à sua organização.

As aplicações podem ser instaladas sem a interação do utilizador e sem exigir que o utilizador permita a **Instalação de Origens Desconhecidas**. Para procurar e instalar aplicações opcionais ou disponíveis, o utilizador pode procurar na Google Play for Work Store no dispositivo. Para obter mais informações, consulte [atribuir aplicativos a dispositivos de perfil de trabalho do Android Enterprise com o Intune](apps-add-android-for-work.md).

## <a name="app-configuration"></a>Configuração de aplicações

O Android Enterprise fornece infraestrutura para implantar valores de configuração de aplicativo em aplicativos que dão suporte a eles. Ao especificar valores de configuração para aplicações de trabalho, garante que estão devidamente configuradas quando os utilizadores as iniciarem pela primeira vez. O suporte para configuração de aplicações requer que os programadores de aplicações criem as respetivas aplicações para Android especificamente para suportar valores de configuração geridos. Se o fizerem, pode utilizar o Intune para especificar e aplicar essas definições de configuração. Para obter mais informações, veja [Adicionar políticas de configuração da aplicação para dispositivos Android geridos](app-configuration-policies-use-android.md).

## <a name="email-configuration"></a>Configuração de e-mail

O Android Enterprise não fornece um aplicativo de email padrão ou um objeto de perfil de email nativo como os fornecidos pelo iOS. As configurações de e-mail podem definir-se ao aplicar as definições de configuração de aplicações às aplicações de e-mail que as suportem. O Gmail e o nove funcionam são dois aplicativos cliente do Exchange ActiveSync (EAS) no Play Store que dão suporte à configuração com a configuração de aplicativo empresarial do Android.

O Intune disponibiliza modelos de configuração para as aplicações Gmail e Nine Work quando são geridas como aplicações de trabalho. Outras aplicações de e-mail que suportem os perfis de configuração de aplicações podem ser configuradas através das políticas de configuração de aplicações móveis.

Se você estiver usando o acesso condicional do Exchange ActiveSync para um dispositivo de perfil de trabalho do Android Enterprise, considere o uso do aplicativo de email Gmail ou nove work. A aplicação Microsoft Outlook para Android, ou qualquer outra aplicação de e-mail que utilize autenticação moderna através da ADAL, também é suportada. Para obter mais informações, veja [Como configurar definições de e-mail no Microsoft Intune](email-settings-configure.md).

## <a name="app-protection-policies"></a>Políticas de proteção de aplicações

As políticas de proteção de aplicações aplicadas são totalmente suportadas no perfil de trabalho e no perfil pessoal. Pode publicar aplicações de linha de negócio na consola de publicação de aplicações Android em https://play.google.com/apps/publish. Esta consola inclui uma opção que permite tornar as aplicações privadas para a sua organização. Para obter mais informações, consulte [Adicionar uma política de conformidade do dispositivo para dispositivos Android Enterprise Work profile no Intune](compliance-policy-create-android-for-work.md). Para obter informações gerais sobre políticas de proteção de aplicações, veja [O que são as políticas de proteção de aplicações?](app-protection-policy.md)

## <a name="vpn-profiles"></a>Perfis da VPN

O suporte de VPN é semelhante aos perfis de VPN em Android. Os mesmos provedores de VPN e opções de configuração básica estão disponíveis para o gerenciamento do Android Enterprise com duas diferenças:

- **VPN com âmbito de perfil de trabalho** – as ligações VPN estão limitadas às aplicações implementadas para o perfil de trabalho. Somente aplicativos gerenciados da empresa Android podem usar a conexão VPN. As aplicações pessoais no dispositivo não podem utilizar uma ligação VPN gerida. Para obter mais informações, consulte [configurações de VPN do Android Enterprise](vpn-settings-android-enterprise.md).

- **VPN específica da aplicação** – a VPN específica da aplicação pode ser configurada no Intune se o fornecedor de VPN suportar:
  - a configuração da VPN específica da aplicação
  - a capacidade de configurar a VPN por aplicativo por meio do perfil de configuração do aplicativo Android Enterprise.
  Para obter mais informações, veja [Utilizar um perfil personalizado do Microsoft Intune para criar um perfil VPN por aplicação para dispositivos Android](android-pulse-secure-per-app-vpn.md).

## <a name="certificate-profiles"></a>Perfis de certificados

As mesmas opções de configuração de perfil de certificado disponíveis para o gerenciamento do Android estão disponíveis em dispositivos Android Enterprise Work Profile. O Android Enterprise fornece APIs de gerenciamento de certificado aprimoradas. A gestão de certificados melhorada fornece as seguintes funcionalidades:

- Garante que a implementação de certificados é automática e totalmente integrada para o utilizador.
- Garante que os certificados implementados são removidos após um dispositivo ser extinto do Intune e o perfil de trabalho ser removido.
- Fornece mensagens melhoradas que informam os utilizadores de que o certificado foi implementado e configurado pelo respetivo departamento de TI através do serviço de gestão.

Para obter mais informações, veja [Configurar um perfil de certificado para os seus dispositivos no Microsoft Intune](certificates-configure.md).

## <a name="wi-fi-profiles"></a>Perfis de Wi-Fi

Os perfis de Wi-Fi gerenciados pelo Android Enterprise são removidos quando o dispositivo é desativado do Intune e o perfil de trabalho é excluído. Para obter mais informações, veja [Como configurar definições de Wi-Fi no Microsoft Intune](wi-fi-settings-configure.md).

## <a name="next-steps"></a>Passos seguintes
- [Inscrever dispositivos Android](android-enroll.md)
- [Atribuir aplicativos a dispositivos Android Enterprise de perfil de trabalho com o Intune](apps-add-android-for-work.md)
