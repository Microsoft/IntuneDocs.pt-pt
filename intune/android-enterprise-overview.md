---
title: Gerir dispositivos com perfil de trabalho do Android no Microsoft Intune
titlesuffix: ''
description: O Microsoft Intune gere os dispositivos com perfil de trabalho do Android para fornecer privacidade e capacidades de gestão adicionais quando as pessoas utilizam os respetivos dispositivos Android para trabalho.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 2cc3c960-1fdd-47ca-a693-420d47b403de
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 4082b845643aae47464e4df14ac6621fcf8f39cf
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/20/2018
ms.locfileid: "52180256"
---
# <a name="manage-android-work-profile-devices-with-intune"></a>Gerir dispositivos com perfil de trabalho do Android com o Intune

O Android Enterprise é um conjunto de funcionalidades e serviços que separa as aplicações e dados de aplicações pessoais dos de trabalho. O Android Enterprise fornece privacidade e capacidades de gestão adicionais quando as pessoas utilizam os respetivos dispositivos Android para trabalho. 

## <a name="supported-devices"></a>Dispositivos suportados

As capacidades de gestão do Android Enterprise dependem de funcionalidades integradas nos sistemas operativos Android mais recentes. Para os dispositivos que não suportam o Android Enterprise, a gestão de Android convencional continua disponível. Para obter mais informações, veja [Requisitos empresariais do Android](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012).

## <a name="onboarding"></a>Integração

Antes de inscrever dispositivos com perfil de trabalho do Android, tem de concluir alguns passos de integração. Estes passos estabelecem uma ligação entre o seu inquilino do Intune e o serviço Google Play for Work. Para obter mais informações, veja [Enable enrollment of Android work profile devices](android-work-profile-enroll.md) (Ativar a inscrição de dispositivos com perfil de trabalho do Android).

## <a name="work-profile-management"></a>Gestão de perfis de trabalho

Ao gerir um dispositivo com perfil de trabalho do Android com o Intune, não gere o dispositivo inteiro. As capacidades de gestão só afetam o perfil de trabalho que é criado no dispositivo durante a inscrição. Todas as aplicações implementadas no dispositivo com o Intune são instaladas no perfil de trabalho. Os ícones das aplicações no perfil de trabalho são diferenciados dos das aplicações pessoais no dispositivo. Todos os dados e aplicações para Android externos à parte Android Enterprise do dispositivo permanecem pessoais e sob controlo do utilizador final. Os utilizadores podem instalar qualquer aplicação na parte pessoal do dispositivo. Os administradores podem gerir e monitorizar aplicações e ações com âmbito definido para o perfil de trabalho.

O Intune oferece um conjunto de definições gerais incorporadas que pode configurar em dispositivos com perfil de trabalho do Android. Para obter mais informações, veja [Android work profile device policy settings](compliance-policy-create-android-for-work.md) (Definições de política de dispositivo com perfil de trabalho do Android).

## <a name="app-publishing-and-distribution"></a>Publicação e distribuição de aplicações

O serviço Google Play for Work é uma parte importante da gestão e distribuição de aplicações do Android Enterprise. Todas as aplicações implementadas em dispositivos com perfil de trabalho do Android no perfil de trabalho são provenientes do serviço Google Play Store Gerida. Para gerir e implementar aplicações na Play Store, inicie sessão no site do Google Play com as credenciais de administrador da empresa para a gestão do Google. Pode aprovar aplicações para a implementação do Android Enterprise para aparecerem nos perfis de trabalho dos dispositivos. Estas aplicações são sincronizadas com a consola do Intune, onde podem ser implementadas e geridas através do Intune. As aplicações de linha de negócio (LOB) desenvolvidas pela sua organização têm de ser publicadas na Google Play Store Gerida através da consola de publicação de aplicações Android do Google. As aplicações de linha de negócio têm de ser configuradas na consola de publicação de aplicações Android para restringir o acesso à sua organização.

As aplicações podem ser instaladas sem a interação do utilizador e sem exigir que o utilizador permita a **Instalação de Origens Desconhecidas**. Para procurar e instalar aplicações opcionais ou disponíveis, o utilizador pode procurar na Google Play for Work Store no dispositivo. Para obter mais informações, veja [Assign apps to Android work profile devices with Intune](apps-add-android-for-work.md) (Atribuir aplicações em dispositivos com perfil de trabalho do Android com o Intune).

## <a name="app-configuration"></a>Configuração de aplicações

O Android Enterprise fornece uma infraestrutura para implementar valores de configuração de aplicações para aplicações que os suportem. Ao especificar valores de configuração para aplicações de trabalho, garante que estão devidamente configuradas quando os utilizadores as iniciarem pela primeira vez. O suporte para configuração de aplicações requer que os programadores de aplicações criem as respetivas aplicações para Android especificamente para suportar valores de configuração geridos. Se o fizerem, pode utilizar o Intune para especificar e aplicar essas definições de configuração. Para obter mais informações, veja [Adicionar políticas de configuração da aplicação para dispositivos Android geridos](app-configuration-policies-use-android.md).

## <a name="email-configuration"></a>Configuração de e-mail

O Android Enterprise não fornece uma aplicação de e-mail predefinida nem um objeto de perfil de e-mail nativo, como acontece no caso do iOS. As configurações de e-mail podem definir-se ao aplicar as definições de configuração de aplicações às aplicações de e-mail que as suportem. O Gmail e o Nine Work são duas aplicações de cliente do Exchange ActiveSync (EAS) na Play Store que suportam a configuração com a configuração de aplicações do Android Enterprise.

O Intune disponibiliza modelos de configuração para as aplicações Gmail e Nine Work quando são geridas como aplicações de trabalho. Outras aplicações de e-mail que suportem os perfis de configuração de aplicações podem ser configuradas através das políticas de configuração de aplicações móveis.

Se estiver a utilizar o acesso condicional do Exchange ActiveSync para um dispositivo com perfil de trabalho do Android, pondere utilizar a aplicação de e-mail Gmail ou Nine Work. A aplicação Microsoft Outlook para Android, ou qualquer outra aplicação de e-mail que utilize autenticação moderna através da ADAL, também é suportada. Para obter mais informações, veja [Como configurar definições de e-mail no Microsoft Intune](email-settings-configure.md).

## <a name="app-protection-policies"></a>Políticas de proteção de aplicações

As políticas de proteção de aplicações aplicadas são totalmente suportadas no perfil de trabalho e no perfil pessoal. Pode publicar aplicações de linha de negócio na consola de publicação de aplicações Android em https://play.google.com/apps/publish. Esta consola inclui uma opção que permite tornar as aplicações privadas para a sua organização. Para obter mais informações, veja [Add a device compliance policy for Android work profile devices in Intune](compliance-policy-create-android-for-work.md) (Adicionar uma política de conformidade de dispositivos para dispositivos com perfil de trabalho do Android no Intune). Para obter informações gerais sobre políticas de proteção de aplicações, veja [O que são as políticas de proteção de aplicações?](app-protection-policy.md)

## <a name="vpn-profiles"></a>Perfis da VPN

O suporte de VPN é semelhante aos perfis de VPN em Android. Os mesmos fornecedores de VPN e as mesmas opções básicas de configuração estão disponíveis para a gestão do Android Enterprise com duas diferenças:

-  **VPN com âmbito de perfil de trabalho** – as ligações VPN estão limitadas às aplicações implementadas para o perfil de trabalho. Apenas as aplicações geridas do Android Enterprise podem utilizar a ligação VPN. As aplicações pessoais no dispositivo não podem utilizar uma ligação VPN gerida. Para obter mais informações, veja [Android enterprise VPN settings](vpn-settings-android.md#android-for-work-vpn-settings) (Definições de VPN do Android Enterprise).

-  **VPN específica da aplicação** – a VPN específica da aplicação pode ser configurada no Intune se o fornecedor de VPN suportar:
    - a configuração da VPN específica da aplicação
    - a capacidade de configurar a VPN por aplicação através do perfil de configuração de aplicações do Android Enterprise.
    Para obter mais informações, veja [Utilizar um perfil personalizado do Microsoft Intune para criar um perfil VPN por aplicação para dispositivos Android](android-pulse-secure-per-app-vpn.md).

## <a name="certificate-profiles"></a>Perfis de certificados

As opções de configuração de perfis de certificados que estão disponíveis para gestão de Android também estão disponíveis em dispositivos com perfil de trabalho do Android. O Android Enterprise fornece APIs de gestão de certificados melhorada. A gestão de certificados melhorada fornece as seguintes funcionalidades:

-  Garante que a implementação de certificados é automática e totalmente integrada para o utilizador.
-  Garante que os certificados implementados são removidos após um dispositivo ser extinto do Intune e o perfil de trabalho ser removido.
-  Fornece mensagens melhoradas que informam os utilizadores de que o certificado foi implementado e configurado pelo respetivo departamento de TI através do serviço de gestão.

Para obter mais informações, veja [Configurar um perfil de certificado para os seus dispositivos no Microsoft Intune](certificates-configure.md).

## <a name="wi-fi-profiles"></a>Perfis de Wi-Fi

Os perfis de Wi-Fi geridos pelo Android Enterprise são removidos quando o dispositivo é extinto do Intune e o perfil de trabalho é eliminado. Para obter mais informações, veja [Como configurar definições de Wi-Fi no Microsoft Intune](wi-fi-settings-configure.md).

## <a name="next-steps"></a>Passos Seguintes
- [Inscrever dispositivos Android](android-enroll.md)
- [Assign apps to Android work profile devices with Intune](apps-add-android-for-work.md) (Atribuir aplicações em dispositivos com perfil de trabalho do Android com o Intune)
