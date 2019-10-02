---
title: O que Microsoft Intune pode fazer para minha empresa
titleSuffix: ''
description: Problemas de negócios comuns que Microsoft Intune ajudam a resolver.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 02/26/2019
ms.topic: overview
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 6bfab644-c1e2-4154-a254-e95b9a1d75f2
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 845eb22522895e04f6ec4f46eda7a817e27a830c
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71731840"
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

Entendemos que a introdução ao gerenciamento de dispositivos móveis pode ser difícil. Há muitas decisões diferentes que você precisará tomar em nome de sua empresa. Os guias de início rápido a seguir ajudam você a começar a usar o Intune e a concluir algumas tarefas comuns, em um período mínimo de tempo.

Você pode seguir a ordem pretendida dos **guias de início rápido** usando o Sumário no lado esquerdo desta página.

- [Experimentar o Intune gratuitamente](free-trial-sign-up.md) – crie uma subscrição gratuita para experimentar o Intune num ambiente de teste.    
- [Create a user](quickstart-create-user.md) (Criar um utilizador) – adicione um utilizador ao Intune para lhe permitir aceder a recursos da empresa em dispositivos móveis.
- [Criar um grupo](quickstart-create-group.md) -organizar usuários em grupos para facilitar o gerenciamento das políticas e dos aplicativos que eles podem acessar.
- [Configurar o registro automático](../enrollment/quickstart-setup-auto-enrollment.md) – configure o Intune para registrar automaticamente os dispositivos quando usuários específicos entrarem em dispositivos Windows 10.
- [Registrar seu dispositivo](../enrollment/quickstart-enroll-windows-device.md) – pegue a função de um usuário do Intune e Registre seu dispositivo no Intune. Em seguida, retorne ao Intune e confirme se o dispositivo foi registrado com êxito.
- [Create a device compliance policy](../protect/quickstart-set-password-length-android.md) (Criar uma política de conformidade de dispositivo) – crie uma política de conformidade de dispositivo e atribua a política a um grupo.
- [Enviar notificações para dispositivos não compatíveis](../protect/quickstart-send-notification.md) – envie uma notificação por email aos membros de sua força de funcionários que têm dispositivos não compatíveis criando e atribuindo uma política de conformidade.
- [Add and assign an app](../apps/quickstart-add-assign-app.md) (Adicionar e atribuir uma aplicação) – adicione e atribua uma aplicação cliente à força de trabalho da sua empresa.
- [Create and assign an app protection policy](../apps/quickstart-create-assign-app-policy.md) (Criar e atribuir uma política de proteção de aplicações) – crie e atribua uma política de proteção de aplicações para uma aplicação cliente no dispositivo de um utilizador final.
- [Create and assign a custom role](create-custom-role.md) (Criar e atribuir uma função personalizada) – crie e atribua uma função personalizada com permissões específicas a um serviço de segurança operacional. 
- [Create an email device profile for iOS](../configuration/quickstart-email-profile.md) (Criar um perfil de e-mail para dispositivos iOS) – crie um perfil de e-mail para dispositivos iOS.

## <a name="prerequisites"></a>Pré-requisitos

Antes de começar, você deve ter uma conta de administrador e locatário do Intune ativada. Crie uma subscrição para [experimentar o Intune gratuitamente](free-trial-sign-up.md) num ambiente de teste. Os assinantes atuais também podem concluir essas atividades em seu locatário ativo. Esses artigos de introdução pressupõem que você está trabalhando em dispositivos de teste.

Também deverá garantir que é o administrador global da sua organização para poder concluir todas as tarefas de Introdução.

## <a name="intune-architecture"></a>Arquitetura do Intune

O Intune é o componente de Enterprise Mobility + Security (EMS) que gere aplicações e dispositivos móveis. Integra-se com outros componentes de EMS, como o Azure Active Directory (Azure AD) para controlo de acesso e identidade, e o Azure Information Protection para proteção de dados. Ao usá-lo com o Office 365, você pode permitir que sua força de equipe seja produtiva em todos os seus dispositivos, mantendo as informações da sua organização protegidas.

![Diagrama da arquitetura geral do Microsoft Intune](./media/get-started-evaluation/intunearchitecture.svg)

## <a name="next-steps"></a>Passos seguintes

[Introdução ao Azure ](tutorial-walkthrough-intune-portal.md) – compreenda a anatomia do portal do Azure e como fazer alterações à página que vê.

## <a name="learn-more"></a>Saiba mais

- [O que é o Intune?](what-is-intune.md)
- [O que é o portal do Azure?](what-is-intune.md)
- [Ciclos de vida dos dispositivos e das aplicações](device-lifecycle.md)
