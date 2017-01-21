---
title: Acerca do Android for Work | Documentos da Microsoft
description: "O Intune gere o Android for Work para fornecer privacidade e capacidades de gestão adicionais quando as pessoas utilizam os respetivos dispositivos Android para trabalho."
keywords: 
author: nathbarn
manager: angrobe
ms.date: 11/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: aa0002d9-f5a0-466e-98ac-3970cb77e3a2
translationtype: Human Translation
ms.sourcegitcommit: b6d5ea579b675d85d4404f289db83055642ffddd
ms.openlocfilehash: e9a99868e7bd4c3aa45de4d221f28c1d2f3efb74


---

# <a name="manage-android-for-work-devices-with-intune"></a>Gerir dispositivos Android for Work com o Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

O Android for Work é um conjunto de funcionalidades e serviços para dispositivos Android. Estes serviços e funcionalidades fornecem privacidade e capacidades de gestão adicionais quando as pessoas utilizam os respetivos dispositivos Android para trabalho. O Intune pode ajudá-lo a implementar aplicações e recursos da empresa em dispositivos Android for Work, para garantir a separação de informações pessoais e profissionais. Com uma implementação bem-sucedida, as aplicações e os dados a que as mesmas acedem permanecem exclusivamente no ambiente Android for Work no dispositivo.

[!INCLUDE[wit_nextref](../includes/afw_rollout_disclaimer.md)]

## <a name="supported-devices"></a>Dispositivos suportados

O Android for Work necessita do hardware Android mais recente, pois muitas capacidades de gestão dependem de funcionalidades integradas no novo sistema operativo Android. Atualmente, o Android for Work é suportado em dispositivos com Android 5.0 Lollipop e posterior, com suporte para perfis de trabalho. Para dispositivos sem suporte nativo para Android for Work, continua a ser disponibilizada gestão convencional Android. Saiba mais sobre os [requisitos do Android for Work](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012).

## <a name="onboarding"></a>Integração

Antes de inscrever dispositivos Android for Work, tem de efetuar alguns passos de integração. Estes passos estabelecem uma ligação entre o seu inquilino do Intune e o serviço Google Play for Work, que é uma parte importante do processo de gestão e distribuição de aplicações do Android for Work. Saiba mais sobre [Ativar a inscrição do Android for Work](https://docs.microsoft.com/en-us/intune/deploy-use/set-up-android-for-work).

## <a name="work-profile-management"></a>Gestão de perfis de trabalho

Ao gerir um dispositivo Android for Work com o Intune, não gere o dispositivo inteiro. As capacidades de gestão afetam apenas um perfil de trabalho criado durante a inscrição. As aplicações implementadas para o dispositivo com o Intune fazem parte do perfil de trabalho. Os ícones de aplicações no perfil de trabalho apresentam uma mala laranja. Esta marcação distingue as aplicações de trabalho das aplicações pessoais no dispositivo. Todos os dados e aplicações para Android externos à parte Android for Work do dispositivo permanecem pessoais e sob controlo do utilizador final. Os utilizadores podem instalar qualquer aplicação na parte pessoal do dispositivo, enquanto os administradores podem gerir e monitorizar ações com âmbito definido para o perfil de trabalho.

## <a name="app-publishing-and-distribution"></a>Publicação e distribuição de aplicações

O serviço Google Play for Work faz parte integral da gestão e distribuição de aplicações. Todas as aplicações implementadas para dispositivos Android for Work no perfil de trabalho são provenientes do Play for Work. Para gerir e implementar aplicações na Play Store, inicie sessão como administrador do Intune no site do Play for Work e aprove as aplicações para o seu inquilino do Intune. Estas aplicações são sincronizadas com a consola do Intune, onde podem depois ser implementadas e geridas através do Intune. As aplicações de Linha de negócio (LOB) desenvolvidas pela sua organização têm de ser publicadas no Play for Work através da consola de publicação de aplicações Android do Google. As aplicações de linha de negócio têm de ser configuradas na consola de publicação de aplicações Android para restringir o acesso à sua organização.

As aplicações são instaladas sem interação com o utilizador e sem requerer que o utilizador permita a **Instalação de Origens Desconhecidas**. Para procurar e instalar aplicações opcionais ou disponíveis, utiliza-se a aplicação da Play Store com distintivo de trabalho no respetivo dispositivo. Saiba mais sobre [Implementar aplicações para Android for Work](https://docs.microsoft.com/en-us/intune/deploy-use/android-for-work-apps).

## <a name="app-configuration"></a>Configuração de aplicações

O Android for Work fornece infraestrutura para implementar valores de configuração de aplicações para aplicações que os suportem. Ao especificar valores de configuração para aplicações de trabalho, garante que estão devidamente configuradas quando os utilizadores as iniciarem pela primeira vez. O suporte para configuração de aplicações requer que os programadores de aplicações criem as respetivas aplicações para Android especificamente para suportar valores de configuração geridos. Se o fizerem, pode utilizar o Intune para especificar e aplicar essas definições de configuração. Saiba mais sobre as [definições de configuração de aplicações do Android for Work](afw-app-configuration-policy.md).

## <a name="email-configuration"></a>Configuração de e-mail

O Android for Work não fornece uma aplicação de e-mail predefinida nem um objeto de perfil de e-mail nativo, como acontece no caso do iOS. As configurações de e-mail podem definir-se ao aplicar as definições de configuração de aplicações às aplicações de e-mail que as suportem. O Gmail e o Nine Work são duas aplicações de cliente do Exchange ActiveSync (EAS) na Play Store que suportam a configuração com a configuração de aplicações do Android for Work.

O Intune fornece modelos de configuração para as aplicações Gmail e Nine Work. Outras aplicações de e-mail que suportem os perfis de configuração de aplicações podem ser configuradas através das políticas de configuração de aplicações móveis.

Se estiver a utilizar o acesso condicional do EAS para um dispositivo Android for Work, deverá utilizar a aplicação de e-mail Gmail ou Nine Work. A aplicação Microsoft Outlook para Android, ou qualquer outra aplicação de e-mail que utilize autenticação moderna através da ADAL, também é suportada. Saiba mais sobre os [Perfis de e-mail para e-mail da empresa](configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune.md).

## <a name="mobile-app-management-policies"></a>Políticas de gestão de aplicações móveis

As políticas de restrição aplicadas a aplicações ativadas para gestão de aplicações móveis (MAM) são totalmente suportadas no perfil de trabalho e no perfil pessoal. Pode publicar aplicações de linha de negócio na consola de publicação de aplicações Android em https://play.google.com/apps/publish. Esta consola inclui uma opção que permite tornar as aplicações privadas para a sua organização. Saiba mais sobre as [Definições de política de conformidade](afw-compliance-policy-settings-in-microsoft-intune.md). Para mais informações, consulte as [políticas de gestão de aplicações móveis](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md).

## <a name="vpn-profiles"></a>Perfis da VPN

O suporte de VPN é semelhante aos perfis de VPN em Android. Estão disponíveis os mesmos fornecedores de VPN e as mesmas opções básicas de configuração. Existem duas diferenças principais:

1.  **VPN com âmbito de perfil de trabalho** – o âmbito das ligações VPN é definido apenas para as aplicações implementadas para o perfil de trabalho. Apenas as aplicações geridas do Android for Work podem utilizar a ligação VPN. As aplicações pessoais no dispositivo não podem utilizar uma ligação VPN gerida.

2.  **VPN específica da aplicação** – se um fornecedor de VPN suportar a configuração da VPN específica da aplicação e fornecer a capacidade de configurar a VPN por aplicação através do perfil de configuração de aplicações do Android for Work, a VPN específica da aplicação pode ser configurada no Intune. Contacte o fornecedor da VPN para saber se esta capacidade é suportada. Saiba mais sobre os [perfis de ligação VPN](vpn-connections-in-microsoft-intune.md).

## <a name="certificate-profiles"></a>Perfis de certificados

As opções de configuração de perfis de certificados que estão disponíveis para gestão de Android tradicional também estão disponíveis em dispositivos Android for Work. O Android for Work fornece APIs de gestão de certificados melhorada. A gestão de certificados melhorada fornece as seguintes funcionalidades:

1.  Garante que a implementação de certificados é automática e totalmente integrada para o utilizador.

2.  Garante que os certificados implementados são totalmente removidos após um dispositivo ser extinto do Intune e o perfil de trabalho ser removido.

3.  Fornece mensagens melhoradas que informam os utilizadores de que o certificado foi implementado e configurado pelo respetivo departamento de TI através do serviço de gestão.

Saiba mais sobre os [Perfis de certificado](secure-resource-access-with-certificate-profiles.md).

## <a name="wi-fi-profiles"></a>Perfis de Wi-Fi

Os perfis de Wi-Fi geridos pelo Android for Work são garantidamente removidos quando o dispositivo é extinto do Intune e o perfil de trabalho é eliminado. Saiba mais sobre os [perfis de Wi-Fi](wi-fi-connections-in-microsoft-intune.md).

## <a name="next-steps"></a>Passos seguintes
[Ativar a inscrição do Android for Work](https://docs.microsoft.com/en-us/intune/deploy-use/set-up-android-for-work)
[Implementar aplicações para o Android for Work](https://docs.microsoft.com/en-us/intune/deploy-use/android-for-work-apps)



<!--HONumber=Dec16_HO2-->


