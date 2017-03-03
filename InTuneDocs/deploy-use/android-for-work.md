---
title: Acerca do Android for Work | Documentos da Microsoft
description: "O Intune gere o Android for Work para fornecer privacidade e capacidades de gestão adicionais quando as pessoas utilizam os respetivos dispositivos Android para trabalho."
keywords: 
author: nathbarn
manager: angrobe
ms.date: 02/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: aa0002d9-f5a0-466e-98ac-3970cb77e3a2
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: a5c024c2139536f004799b18a0f6d1d1eb4875b2
ms.openlocfilehash: bdacb61d1713bf24b2f33f144afa0db356e10ee0
ms.lasthandoff: 02/23/2017


---

# <a name="manage-android-for-work-devices-with-intune"></a>Gerir dispositivos Android for Work com o Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

O Android for Work é um conjunto de funcionalidades e serviços para dispositivos Android que separa as aplicações e dados pessoais de um perfil de trabalho com aplicações e dados de trabalho. O Android for Work fornece privacidade e capacidades de gestão adicionais quando as pessoas utilizam os respetivos dispositivos Android para trabalho. O Intune ajuda-o a implementar aplicações e recursos da empresa em dispositivos Android for Work, para garantir a separação de informações pessoais e profissionais. Com uma implementação bem-sucedida, as aplicações e os dados a que as mesmas acedem permanecem exclusivamente no ambiente Android for Work no dispositivo.

## <a name="supported-devices"></a>Dispositivos suportados

As capacidades de gestão do Android for Work dependem de funcionalidades integradas no novo sistema operativo Android. Atualmente, o Android for Work é suportado em dispositivos com Android 5.0 Lollipop e posterior que suportem perfis de trabalho. Para os dispositivos que não suportam o Android for Work, a gestão Android convencional continua disponível. Saiba mais sobre os [requisitos do Android for Work](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012).

## <a name="onboarding"></a>Integração

Antes de inscrever dispositivos Android for Work, tem de efetuar alguns passos de integração. Estes passos estabelecem uma ligação entre o seu inquilino do Intune e o serviço Google Play for Work, que é uma parte importante do processo de gestão e distribuição de aplicações do Android for Work. Saiba mais sobre [Ativar a inscrição do Android for Work](https://docs.microsoft.com/intune/deploy-use/set-up-android-for-work).

## <a name="work-profile-management"></a>Gestão de perfis de trabalho

Ao gerir um dispositivo Android for Work com o Intune, não gere o dispositivo inteiro. As capacidades de gestão só afetam o perfil de trabalho que é criado no dispositivo durante a inscrição. Todas as aplicações implementadas no dispositivo com o Intune são instaladas no perfil de trabalho. Os ícones no perfil de trabalho apresentam uma pasta laranja para distinguir as aplicações de trabalho das aplicações pessoais no dispositivo. Todos os dados e aplicações para Android externos à parte Android for Work do dispositivo permanecem pessoais e sob controlo do utilizador final. Os utilizadores podem instalar qualquer aplicação na parte pessoal do dispositivo, enquanto os administradores podem gerir e monitorizar aplicações e ações com âmbito definido para o perfil de trabalho.

O Intune oferece um conjunto de definições gerais incorporadas que pode configurar em dispositivos Android for Work. Saiba mais sobre as [definições de política do Android for Work](android-for-work-policy-settings-in-microsoft-intune.md)

## <a name="app-publishing-and-distribution"></a>Publicação e distribuição de aplicações

O serviço Google Play for Work é uma parte importante da gestão e distribuição de aplicações do Android for Work. Todas as aplicações implementadas em dispositivos Android for Work no perfil de trabalho são provenientes do serviço Play for Work. Para gerir e implementar aplicações na Play Store, inicie sessão como administrador do Intune no site do Play for Work e aprove as aplicações para o seu inquilino do Intune. Estas aplicações são sincronizadas com a consola do Intune, onde podem depois ser implementadas e geridas através do Intune. As aplicações de Linha de negócio (LOB) desenvolvidas pela sua organização têm de ser publicadas no Play for Work através da consola de publicação de aplicações Android do Google. As aplicações de linha de negócio têm de ser configuradas na consola de publicação de aplicações Android para restringir o acesso à sua organização.

As aplicações podem ser instaladas sem a interação do utilizador e sem exigir que o utilizador permita a **Instalação de Origens Desconhecidas**. Para procurar e instalar aplicações opcionais ou disponíveis, o utilizador pode procurar na Play Store no seu dispositivo. Saiba mais sobre [Implementar aplicações para Android for Work](https://docs.microsoft.com/intune/deploy-use/android-for-work-apps).

## <a name="app-configuration"></a>Configuração de aplicações

O Android for Work fornece infraestrutura para implementar valores de configuração de aplicações para aplicações que os suportem. Ao especificar valores de configuração para aplicações de trabalho, garante que estão devidamente configuradas quando os utilizadores as iniciarem pela primeira vez. O suporte para configuração de aplicações requer que os programadores de aplicações criem as respetivas aplicações para Android especificamente para suportar valores de configuração geridos. Se o fizerem, pode utilizar o Intune para especificar e aplicar essas definições de configuração. Saiba mais sobre as [definições de configuração de aplicações do Android for Work](afw-app-configuration-policy.md).

## <a name="email-configuration"></a>Configuração de e-mail

O Android for Work não fornece uma aplicação de e-mail predefinida nem um objeto de perfil de e-mail nativo, como acontece no caso do iOS. As configurações de e-mail podem definir-se ao aplicar as definições de configuração de aplicações às aplicações de e-mail que as suportem. O Gmail e o Nine Work são duas aplicações de cliente do Exchange ActiveSync (EAS) na Play Store que suportam a configuração com a configuração de aplicações do Android for Work.

O Intune fornece modelos de configuração para as aplicações Gmail e Nine Work. Outras aplicações de e-mail que suportem os perfis de configuração de aplicações podem ser configuradas através das políticas de configuração de aplicações móveis.

Se estiver a utilizar o acesso condicional do Exchange ActiveSync para um dispositivo Android for Work, deverá utilizar a aplicação de e-mail Gmail ou Nine Work. A aplicação Microsoft Outlook para Android, ou qualquer outra aplicação de e-mail que utilize autenticação moderna através da ADAL, também é suportada. Saiba mais sobre os [Perfis de e-mail para e-mail da empresa](configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune.md).

## <a name="mobile-app-management-policies"></a>Políticas de gestão de aplicações móveis

As políticas de restrição aplicadas a aplicações ativadas para gestão de aplicações móveis (MAM) são totalmente suportadas no perfil de trabalho e no perfil pessoal. Pode publicar aplicações de linha de negócio na consola de publicação de aplicações Android em https://play.google.com/apps/publish. Esta consola inclui uma opção que permite tornar as aplicações privadas para a sua organização. Saiba mais sobre as [definições de política de conformidade do Android for Work](afw-compliance-policy-settings-in-microsoft-intune.md). Para obter informações gerais sobre as políticas de MAM, consulte [políticas de gestão de aplicações móveis](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md).

## <a name="vpn-profiles"></a>Perfis da VPN

O suporte de VPN é semelhante aos perfis de VPN em Android. Os mesmos fornecedores de VPN e as mesmas opções básicas de configuração estão disponíveis para a gestão do Android for Work com duas diferenças:

-  **VPN com âmbito de perfil de trabalho** – as ligações VPN estão limitadas às aplicações implementadas para o perfil de trabalho. Apenas as aplicações geridas do Android for Work podem utilizar a ligação VPN. As aplicações pessoais no dispositivo não podem utilizar uma ligação VPN gerida.

-  **VPN específica da aplicação** – se um fornecedor de VPN suportar a configuração da VPN específica da aplicação e fornecer a capacidade de configurar a VPN por aplicação através do perfil de configuração de aplicações do Android for Work, a VPN específica de uma aplicação pode ser configurada no Intune. Contacte o fornecedor da VPN para saber se esta capacidade é suportada. Saiba mais sobre os [perfis de ligação VPN](vpn-connections-in-microsoft-intune.md).

## <a name="certificate-profiles"></a>Perfis de certificados

As opções de configuração de perfis de certificados que estão disponíveis para gestão de Android também estão disponíveis em dispositivos Android for Work. O Android for Work fornece APIs de gestão de certificados melhorada. A gestão de certificados melhorada fornece as seguintes funcionalidades:

- Garante que a implementação de certificados é automática e totalmente integrada para o utilizador.
-  Garante que os certificados implementados são totalmente removidos após um dispositivo ser extinto do Intune e o perfil de trabalho ser removido.
-  Fornece mensagens melhoradas que informam os utilizadores de que o certificado foi implementado e configurado pelo respetivo departamento de TI através do serviço de gestão.

Saiba mais sobre os [Perfis de certificado](secure-resource-access-with-certificate-profiles.md).

## <a name="wi-fi-profiles"></a>Perfis de Wi-Fi

Os perfis de Wi-Fi geridos pelo Android for Work são removidos quando o dispositivo é extinto do Intune e o perfil de trabalho é eliminado. Saiba mais sobre os [perfis de Wi-Fi](wi-fi-connections-in-microsoft-intune.md).

## <a name="next-steps"></a>Passos seguintes
[Ativar a inscrição do Android for Work](https://docs.microsoft.com/en-us/intune/deploy-use/set-up-android-for-work)

[Implementar aplicações para Android for Work](https://docs.microsoft.com/en-us/intune/deploy-use/android-for-work-apps)

