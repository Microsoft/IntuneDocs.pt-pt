---
title: Escolher como inscrever dispositivos iOS no Intune
titlesuffix: Microsoft Intune
description: Configure a inscrição de dispositivos iOS no Microsoft Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 439c33a6-e80c-4da9-ba09-a51fc36f62ad
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 545c5b26b6c908f4a9e7066d3f76cbf774c8fbea
ms.sourcegitcommit: 08e1b0d45c84eb9525a0a59f5540d41434da2814
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/19/2018
ms.locfileid: "39146701"
---
# <a name="enroll-ios-devices-in-intune"></a>Inscrever dispositivos iOS no Intune

O Intune ativa a gestão de dispositivos móveis (MDM) de iPads e iPhones para conceder aos utilizadores acesso a aplicações e ao e-mail da empresa.

Enquanto administrador do Intune, pode ativar a inscrição para dispositivos iOS. Pode permitir que os utilizadores inscrevam dispositivos pessoais, também conhecido como inscrição BYOD ("Bring Your Own Device"). Também pode ativar a inscrição de dispositivos pertencentes à empresa.

## <a name="prerequisites-for-ios-enrollment"></a>Pré-requisitos para a inscrição de dispositivos iOS
Antes de poder ativar dispositivos iOS, conclua os seguintes passos:
- [Configurar o Intune](setup-steps.md) – estes passos irão configurar a sua infraestrutura do Intune. Em particular, a inscrição de dispositivos requer que [defina a autoridade de MDM](mdm-authority-set.md).
- [Obter um Certificado Push de MDM da Apple](apple-mdm-push-certificate-get.md) - a Apple exige um certificado para ativar a gestão de dispositivos iOS e macOS.

## <a name="user-owned-ios-devices-byod"></a>Dispositivos iOS propriedade do utilizador (BYOD)

Pode permitir que os seus utilizadores inscrevam os respetivos dispositivos pessoais na gestão do Intune. Chama-se a isto "bring your own device (traga o seu próprio dispositivo)", ou BYOD. Após concluir os pré-requisitos e atribuir licenças aos utilizadores, estes podem transferir a aplicação Portal da Empresa do Intune a partir da App Store e seguir as instruções da inscrição na aplicação.

## <a name="company-owned-ios-devices"></a>Dispositivos iOS pertencentes à empresa
Para as organizações que compram dispositivos para os respetivos utilizadores, o Intune suporta os seguintes métodos de inscrição de dispositivos iOS pertencentes à empresa:

- Programa de Registo de Aparelho (DEP) da Apple
- Gestor Escolar da Apple
- Inscrição do Assistente de Configuração do Apple Configurator
- Inscrição direta no Apple Configurator

Também pode inscrever os dispositivos iOS pertencentes à empresa com uma conta de [gestor de inscrição de dispositivos](device-enrollment-manager-enroll.md).

## <a name="device-enrollment-program"></a>Programa de Inscrição de Dispositivos
As organizações podem adquirir dispositivos iOS através do Programa de Inscrição de Dispositivos (DEP) da Apple. O DEP permite-lhe implementar um perfil de inscrição através de uma ligação sem fios para incluir os dispositivos na gestão. Saiba mais sobre o [Programa de Inscrição de Dispositivos](device-enrollment-program-enroll-ios.md).

## <a name="apple-school-manager"></a>Gestor Escolar da Apple
O Gestor Escolar da Apple é um programa de compra e inscrição de dispositivos da Apple para escolas. À semelhança do DEP, pode implementar um perfil para inscrever dispositivos para gestão. Saiba mais sobre o [Gestor Escolar da Apple](apple-school-manager-set-up-ios.md).

## <a name="apple-configurator"></a>Apple Configurator
Pode inscrever dispositivos iOS com o Apple Configurator num computador Mac. Para preparar os dispositivos, deve ligá-los via USB e instalar um perfil de inscrição. Pode inscrever dispositivos com o Apple Configurator de duas formas:
- Inscrição com o Assistente de Configuração – realiza a reposição de fábrica do dispositivo, prepara-o para executar o Assistente de Configuração e instala as políticas da empresa para o novo utilizador do dispositivo.
- Inscrição direta – não efetua a reposição de fábrica do dispositivo e inscreve o dispositivo com uma política predefinida. Este método destina-se a dispositivos sem afinidade de utilizador.

Saiba mais sobre a [inscrição no Apple Configurator](apple-configurator-setup-assistant-enroll-ios.md).

## <a name="use-the-company-portal-on-dep-enrolled-or-apple-configurator-enrolled-devices"></a>Utilizar o Portal da Empresa em dispositivos inscritos pelo Apple Configurator ou pelo DEP

Os dispositivos configurados com a afinidade de utilizador podem instalar e executar a aplicação do Portal da Empresa para transferir aplicações e gerir dispositivos. Assim que os utilizadores recebem os respetivos dispositivos, têm de executar vários passos adicionais para concluir o Assistente de Configuração e instalar a aplicação Portal da Empresa.

A afinidade de utilizador é necessária para suportar o seguinte:
  - Aplicações de gestão de aplicações móveis (MAM)
  - Acesso condicional a e-mail e dados da empresa
  - Aplicação Portal da Empresa

**Como os utilizadores inscrevem dispositivos iOS pertencentes à empresa com afinidade de utilizador**
1. Quando os utilizadores ligam os dispositivos, é-lhes pedido que concluam o Assistente de Configuração. 
2. Após concluir a configuração, é pedido o ID Apple aos utilizadores. Terão de fornecer um ID Apple para permitir que o dispositivo instale o Portal da Empresa. 
3. O dispositivo iOS instala automaticamente a aplicação Portal da Empresa a partir da App Store.
4. Os utilizadores devem iniciar a aplicação Portal da Empresa e iniciar sessão com as credenciais (por exemplo, o nome pessoal exclusivo ou UPN) associadas à respetiva subscrição no Intune. 
5. Depois de iniciar sessão, o processo de inscrição é concluído. Os utilizadores podem agora utilizar este dispositivo com o conjunto completo de funcionalidades.

### <a name="about-corporate-owned-managed-devices-with-no-user-affinity"></a>Sobre dispositivos pertencentes à empresa geridos sem afinidade de utilizador

Os dispositivos configurados sem afinidade de utilizador não suportam o Portal da Empresa e não devem ter a aplicação instalada. O Portal da Empresa foi concebido para utilizadores com credenciais da empresa e que necessitam de acesso a recursos empresariais personalizados (por exemplo, e-mail). Os dispositivos inscritos sem afinidade de utilizador não se destinam a ter um início de sessão de utilizador dedicado. Os dispositivos de quiosque, ponto de venda (POS) ou utilitário partilhado são casos de utilização típicos para dispositivos inscritos sem afinidade de utilizador.

Se for necessária afinidade de utilizador, confirme que o perfil de inscrição do dispositivo tem a opção **Afinidade do Utilizador** selecionada antes de o inscrever. Para alterar o estado de afinidade num dispositivo, tem de extinguir e voltar a inscrever o dispositivo.

