---
title: Introdução ao Microsoft Intune
titleSuffix: ''
description: Percorra uma série de guias de início rápido para saber mais sobre o Intune.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 11/12/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 6bfab644-c1e2-4154-a254-e95b9a1d75f2
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.openlocfilehash: 8adb038fbd5fa1b4ad2400a215eb228b81433bde
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/20/2018
ms.locfileid: "52186907"
---
# <a name="what-can-intune-do-for-my-company"></a>O que pode o Intune fazer pela minha empresa?
O Microsoft Intune é um serviço de gestão de mobilidade empresarial (EMM) baseado na cloud que ajuda a sua força de trabalho a ser produtiva, mantendo os seus dados empresariais protegidos.

Com o Intune, pode:

- Gerir os dispositivos móveis que a sua força de trabalho utiliza para aceder aos dados da empresa.
- Gerir as aplicações móveis que a sua força de trabalho utiliza.
- Proteger as informações da sua empresa ao ajudar a controlar a forma como a sua força de trabalho acede às mesmas e as partilha.
- Garantir que os dispositivos e as aplicações são compatíveis com os requisitos de segurança da empresa.

## <a name="common-business-problems-that-intune-helps-solve"></a>Problemas empresariais comuns que o Intune ajuda a resolver

* [Proteger o seu e-mail no local e os dados, para que os dispositivos móveis possam aceder aos mesmos](common-scenarios.md#protecting-your-on-premises-email-and-data-so-it-can-be-safely-accessed-by-mobile-devices)
* [Proteger o seu e-mail e dados do Office 365, para que os dispositivos móveis possam aceder em segurança aos mesmos](common-scenarios.md#protecting-your-office-365-email-and-data-so-it-can-be-safely-accessed-by-mobile-devices)
* [Distribuir telemóveis pertencentes à empresa à sua força de trabalho](common-scenarios.md#issue-corporate-owned-phones-to-your-employees)
* [Oferecer um programa BYOD ou de dispositivos pessoais a todos os funcionários](common-scenarios.md#offer-a-bring-your-own-device-program-to-all-employees)
* [Permitir que os seus funcionários acedam de forma segura ao Office 365 a partir de um quiosque público não gerido](common-scenarios.md#enable-your-employees-to-securely-access-office-365-from-an-unmanaged-public-kiosk)
* [Distribuir tablets partilhados de utilização limitada aos trabalhadores de tarefas](common-scenarios.md#issue-limited-use-shared-tablets-to-your-employees)

## <a name="quickstarts"></a>Guias de Introdução

Compreendemos que iniciar a gestão de dispositivos móveis pode ser difícil, uma vez que existem várias decisões diferentes que terá de tomar em nome da sua empresa. Os seguintes guias de início rápido vão ajudá-lo a começar a utilizar o Intune e a concluir tarefas comuns o mais rápido possível.

Pode seguir a ordem pretendida dos **Guias de Início Rápido** através da tabela de conteúdos à esquerda da página.

- [Experimentar o Intune gratuitamente](free-trial-sign-up.md) – crie uma subscrição gratuita para experimentar o Intune num ambiente de teste.    
- [Create a user](quickstart-create-user.md) (Criar um utilizador) – adicione um utilizador ao Intune para lhe permitir aceder a recursos da empresa em dispositivos móveis.
- [Create a group](quickstart-create-group.md) (Criar um grupo) – organize os utilizadores em grupos para ser mais fácil gerir as políticas e aplicações a que podem aceder.
- [Set up automatic enrollment](quickstart-setup-auto-enrollment.md) (Configurar a inscrição automática) – configure o Microsoft Intune para inscrever dispositivos automaticamente mediante o início de sessão de utilizadores específicos em dispositivos com o Windows 10.
- [Enroll your device](quickstart-enroll-windows-device.md) (Inscrever o dispositivo) – assuma a função de um utilizador do Intune e inscreva o seu dispositivo no Microsoft Intune. Em seguida, regresse ao Intune e confirme o dispositivo inscrito.
- [Create a device compliance policy](quickstart-set-password-length-android.md) (Criar uma política de conformidade de dispositivo) – crie uma política de conformidade de dispositivo e atribua a política a um grupo.
- [Send notifications to noncompliant devices](quickstart-send-notification.md) (Enviar notificações para dispositivos não conformes) – envie uma notificação por e-mail para os membros da sua força de trabalho que têm dispositivos não conformes ao criar e atribuir uma política de conformidade.
- [Add and assign an app](quickstart-add-assign-app.md) (Adicionar e atribuir uma aplicação) – adicione e atribua uma aplicação cliente à força de trabalho da sua empresa.
- [Create and assign an app protection policy](quickstart-create-assign-app-policy.md) (Criar e atribuir uma política de proteção de aplicações) – crie e atribua uma política de proteção de aplicações para uma aplicação cliente no dispositivo de um utilizador final.
- [Create and assign a custom role](quickstart-create-custom-role.md) (Criar e atribuir uma função personalizada) – crie e atribua uma função personalizada com permissões específicas a um serviço de segurança operacional. 
- [Create an email device profile for iOS](quickstart-email-profile.md) (Criar um perfil de e-mail para dispositivos iOS) – crie um perfil de e-mail para dispositivos iOS.

## <a name="prerequisites"></a>Pré-requisitos

Antes de começar, tem de ter uma conta de administrador e de inquilino do Intune ativada. Crie uma subscrição para [experimentar o Intune gratuitamente](free-trial-sign-up.md) num ambiente de teste. Os subscritores atuais também podem concluir estas atividades no seu inquilino dinâmico. Estes artigos de introdução pressupõem que está a trabalhar em dispositivos de teste.

Também deverá garantir que é o administrador global da sua organização para poder concluir todas as tarefas de Introdução.

## <a name="intune-architecture"></a>Arquitetura do Intune

O Intune é o componente de Enterprise Mobility + Security (EMS) que gere aplicações e dispositivos móveis. Integra-se com outros componentes de EMS, como o Azure Active Directory (Azure AD) para controlo de acesso e identidade, e o Azure Information Protection para proteção de dados. Ao utilizá-lo com o Office 365, pode fomentar a produtividade da sua força de trabalho em todos os dispositivos e, ao mesmo tempo, manter as informações da sua organização protegidas.

![Diagrama da arquitetura geral do Microsoft Intune](/intune/media/intunearchitecture.svg)

## <a name="next-steps"></a>Passos Seguintes

[Introdução ao Azure ](get-started-azure.md) – compreenda a anatomia do portal do Azure e como fazer alterações à página que vê.

## <a name="learn-more"></a>Saiba mais

* [O que é o Intune?](introduction-intune.md)
* [O que é o portal do Azure?](what-is-intune.md)
* [Ciclos de vida dos dispositivos e das aplicações](introduction-device-app-lifecycles.md)