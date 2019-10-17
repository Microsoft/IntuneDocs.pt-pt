---
title: Inscrever dispositivos iOS no Intune
titleSuffix: Microsoft Intune
description: Configure a inscrição de dispositivos iOS no Microsoft Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 439c33a6-e80c-4da9-ba09-a51fc36f62ad
ms.reviewer: tisilver
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2fb5208cd7df6dc68bcd20455ae9e06a9dbd7ff5
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72503142"
---
# <a name="enroll-ios-devices-in-intune"></a>Inscrever dispositivos iOS no Intune

O Intune permite que o MDM (gerenciamento de dispositivo móvel) de iPads e iPhones forneça aos usuários acesso seguro a email, dados e aplicativos da empresa.

Como administrador do Intune, você pode configurar o registro para dispositivos iOS e iPadOS para acessar os recursos da empresa. Você pode permitir que os usuários registrem dispositivos de propriedade pessoal, conhecido como registro de BYOD ("Traga seu próprio dispositivo"). Você também pode configurar o registro de dispositivos de propriedade da empresa.

## <a name="prerequisites-for-ios-enrollment"></a>Pré-requisitos para a inscrição de dispositivos iOS

Antes de poder ativar dispositivos iOS, conclua os seguintes passos:

- [Verifique se o dispositivo está qualificado para o registro de dispositivo da Apple](https://support.apple.com/en-us/HT204142#eligibility).
- [Configurar o Intune](../fundamentals/setup-steps.md) – estes passos irão configurar a sua infraestrutura do Intune. Em particular, a inscrição de dispositivos requer que [defina a autoridade de MDM](../fundamentals/mdm-authority-set.md).
- [Obter um Certificado Push de MDM da Apple](apple-mdm-push-certificate-get.md) - a Apple exige um certificado para ativar a gestão de dispositivos iOS e macOS.

## <a name="user-owned-ios-and-ipados-devices-byod"></a>Dispositivos iOS e iPadOS de Propriedade do usuário (BYOD)

Pode permitir que os seus utilizadores inscrevam os respetivos dispositivos pessoais na gestão do Intune. Chama-se a isto "bring your own device (traga o seu próprio dispositivo)", ou BYOD. Há três opções para registrar usuários:
- As políticas de proteção de aplicativo oferecem a experiência de BYOD mais leve, fornecendo gerenciamento somente no nível do aplicativo. No entanto, se você quiser também proteger o dispositivo com um PIN complexo de seis dígitos, poderá usar essas políticas junto com o registro do usuário.
- O registro de dispositivo é o que você pode considerar como registro típico de BYOD. Ele fornece aos administradores uma ampla variedade de opções de gerenciamento.
- O registro de usuário é um processo de registro mais simplificado que fornece aos administradores um subconjunto de opções de gerenciamento de dispositivo. Este recurso está atualmente em visualização. 

Depois de concluir os pré-requisitos e as licenças de usuário atribuídas, os usuários podem baixar o aplicativo Portal da Empresa do Intune da App Store e seguir as instruções de registro no aplicativo. Você pode personalizar a declaração de privacidade Portal da Empresa em dispositivos iOS, conforme explicado na [personalização da política de privacidade](../apps/company-portal-app.md#privacy-statement-customization).

## <a name="company-owned-ios-devices"></a>Dispositivos iOS pertencentes à empresa

Para as organizações que compram dispositivos para os respetivos utilizadores, o Intune suporta os seguintes métodos de inscrição de dispositivos iOS pertencentes à empresa:

- Programa de Registo de Aparelho (DEP) da Apple
- Gestor Escolar da Apple
- Inscrição do Assistente de Configuração do Apple Configurator
- Inscrição direta no Apple Configurator

Também pode inscrever os dispositivos iOS pertencentes à empresa com uma conta de [gestor de inscrição de dispositivos](device-enrollment-manager-enroll.md).

## <a name="device-enrollment-program"></a>Programa de Inscrição de Dispositivos

As organizações podem adquirir dispositivos iOS através do Programa de Inscrição de Dispositivos (DEP) da Apple. O DEP permite-lhe implementar um perfil de inscrição através de uma ligação sem fios para incluir os dispositivos na gestão. Para obter mais informações, consulte [programa de registro de dispositivos](device-enrollment-program-enroll-ios.md).

## <a name="user-enrollment"></a>Registro de usuário
O registro de usuário fornece aos administradores um subconjunto de opções de gerenciamento em comparação com outros métodos de registro. Para obter mais informações, consulte [ações de registro de usuário com suporte, senhas e outras opções](ios-user-enrollment-supported-actions.md) e [Configurar o registro de usuário do IOS e iPadOS](ios-user-enrollment.md).

## <a name="apple-school-manager"></a>Gestor Escolar da Apple

O Gestor Escolar da Apple é um programa de compra e inscrição de dispositivos da Apple para escolas. À semelhança do DEP, pode implementar um perfil para inscrever dispositivos para gestão. Saiba mais sobre o [Gestor Escolar da Apple](apple-school-manager-set-up-ios.md).

## <a name="apple-configurator"></a>Apple Configurator

Pode inscrever dispositivos iOS com o Apple Configurator num computador Mac. Para preparar os dispositivos, deve ligá-los via USB e instalar um perfil de inscrição. Pode inscrever dispositivos com o Apple Configurator de duas formas:

- Inscrição com o Assistente de Configuração – apaga os dados do dispositivo, prepara-o para executar o Assistente de Configuração e instala as políticas da empresa para o novo utilizador do dispositivo.
- Inscrição direta – não apaga os dados do dispositivo e inscreve-o com uma política predefinida. Este método destina-se a dispositivos sem afinidade de utilizador.

Saiba mais sobre a [inscrição no Apple Configurator](apple-configurator-enroll-ios.md).

## <a name="use-the-company-portal-on-dep-enrolled-or-apple-configurator-enrolled-devices"></a>Utilizar o Portal da Empresa em dispositivos inscritos pelo Apple Configurator ou pelo DEP

Os dispositivos configurados com a afinidade de utilizador podem instalar e executar a aplicação do Portal da Empresa para transferir aplicações e gerir dispositivos. Assim que os utilizadores recebem os respetivos dispositivos, têm de executar vários passos adicionais para concluir o Assistente de Configuração e instalar a aplicação Portal da Empresa.

A afinidade de utilizador é necessária para suportar o seguinte:

- Aplicações de gestão de aplicações móveis (MAM)
- Acesso condicional a email e dados da empresa
- Aplicação Portal da Empresa

### <a name="how-users-enroll-corporate-owned-ios-devices-with-user-affinity"></a>Como os utilizadores inscrevem dispositivos iOS pertencentes à empresa com afinidade de utilizador

1. Quando os utilizadores ligam os dispositivos, é-lhes pedido que concluam o Assistente de Configuração.
2. Após concluir a configuração, é pedido o ID Apple aos utilizadores. Terão de fornecer um ID Apple para permitir que o dispositivo instale o Portal da Empresa.
3. O dispositivo iOS instala automaticamente a aplicação Portal da Empresa a partir da App Store.
4. Os utilizadores devem iniciar a aplicação Portal da Empresa e iniciar sessão com as credenciais (por exemplo, o nome pessoal exclusivo ou UPN) associadas à respetiva subscrição no Intune.
5. Depois de iniciar sessão, o processo de inscrição é concluído. Os utilizadores podem agora utilizar este dispositivo com o conjunto completo de funcionalidades.

### <a name="about-corporate-owned-managed-devices-with-no-user-affinity"></a>Sobre dispositivos pertencentes à empresa geridos sem afinidade de utilizador

Os dispositivos configurados sem afinidade de utilizador não suportam o Portal da Empresa e não devem ter a aplicação instalada. O Portal da Empresa foi concebido para utilizadores com credenciais da empresa e que necessitam de acesso a recursos empresariais personalizados (por exemplo, e-mail). Os dispositivos inscritos sem afinidade de utilizador não se destinam a ter um início de sessão de utilizador dedicado. Os dispositivos de quiosque, ponto de venda (POS) ou utilitário partilhado são casos de utilização típicos para dispositivos inscritos sem afinidade de utilizador.

Se for necessária afinidade de utilizador, confirme que o perfil de inscrição do dispositivo tem a opção **Afinidade do Utilizador** selecionada antes de o inscrever. Para alterar o estado de afinidade num dispositivo, tem de extinguir e voltar a inscrever o dispositivo.

## <a name="see-also"></a>Consulte também

[Solucionando problemas de registro de dispositivo iOS no Microsoft Intune](https://support.microsoft.com/help/4039809)
