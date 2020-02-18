---
title: Inscreva dispositivos iOS/iPadOS em Intune
titleSuffix: Microsoft Intune
description: Configurar a inscrição de dispositivos iOS/iPadOS no Microsoft Intune.
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
ms.openlocfilehash: 8d5aeb17084ea0bb76429b1fa15c9de5855220ab
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/17/2020
ms.locfileid: "77415302"
---
# <a name="enroll-iosipados-devices-in-intune"></a>Inscreva dispositivos iOS/iPadOS em Intune

A Intune permite que a gestão de dispositivos móveis (MDM) de iPads e iPhones dê aos utilizadores acesso seguro a emails, dados e apps da empresa.

Como administrador intune, pode configurar a inscrição para dispositivos iOS/iPadOS e iPadOS para aceder aos recursos da empresa. Pode permitir que os utilizadores inscrevam dispositivos pessoais, conhecidos como "bring your own device" (BYOD). Também pode configurar a inscrição de dispositivos da empresa.

## <a name="prerequisites-for-iosipados-enrollment"></a>Pré-requisitos para a inscrição do iOS/iPadOS

Antes de poder ativar os dispositivos iOS/iPadOS, complete os seguintes passos:

- [Certifique-se de que o seu dispositivo é elegível para a inscrição do dispositivo Apple](https://support.apple.com/en-us/HT204142#eligibility).
- [Configurar o Intune](../fundamentals/setup-steps.md) – estes passos irão configurar a sua infraestrutura do Intune. Em particular, a inscrição de dispositivos requer que [defina a autoridade de MDM](../fundamentals/mdm-authority-set.md).
- [Obtenha um certificado Apple MDM Push](apple-mdm-push-certificate-get.md) - a Apple necessita de um certificado para permitir a gestão de dispositivos iOiOS/iPadOS e macOS.

## <a name="user-owned-iosipados-and-ipados-devices-byod"></a>Dispositivos iOS/iPadOS e iPadOS (BYOD)

Pode permitir que os seus utilizadores inscrevam os respetivos dispositivos pessoais na gestão do Intune. Chama-se a isto "bring your own device (traga o seu próprio dispositivo)", ou BYOD. Existem três opções para inscrever utilizadores:
- As Políticas de Proteção de Aplicações proporcionam-lhe a experiência BYOD mais leve, proporcionando agestão apenas a nível de aplicações. No entanto, se pretender também proteger o dispositivo com um PIN complexo de 6 dígitos, pode utilizar estas políticas juntamente com a Inscrição do Utilizador.
- Inscrição no Dispositivo é o que você pode pensar como inscrição típica byod. Fornece aos administradores um vasto leque de opções de gestão.
- A Inscrição do Utilizador é um processo de inscrição mais simplificado que fornece aos administradores um subconjunto de opções de gestão de dispositivos. Esta funcionalidade encontra-se em pré-visualização. 

Depois de ter preenchido os pré-requisitos e as licenças de utilizador atribuídas, os utilizadores podem descarregar a aplicação Intune Company Portal a partir da App Store e seguir as instruções de inscrição na app. Pode personalizar a declaração de privacidade do Portal da Empresa nos dispositivos iOS/iPadOS, conforme explicado na personalização da declaração de [privacidade.](../apps/company-portal-app.md#privacy-statement-customization)

## <a name="company-owned-iosipados-devices"></a>Dispositivos iOS/iPadOS da empresa

Para as organizações que compram dispositivos para os seus utilizadores, a Intune suporta os seguintes métodos de inscrição de dispositivos iOS/iPadOS:

- Programa de Registo de Aparelho (DEP) da Apple
- Gestor Escolar da Apple
- Inscrição do Assistente de Configuração do Apple Configurator
- Inscrição direta no Apple Configurator

Também pode inscrever dispositivos iOS/iPadOS da empresa com uma conta de gestor de [inscrição](device-enrollment-manager-enroll.md) de dispositivos.

## <a name="device-enrollment-program"></a>Programa de Inscrição de Dispositivos

As organizações podem adquirir dispositivos iOS/iPadOS através do Programa de Inscrição de Dispositivos da Apple (DEP). O DEP permite-lhe implementar um perfil de inscrição através de uma ligação sem fios para incluir os dispositivos na gestão. Para mais informações, consulte [o Programa de Inscrição de Dispositivos.](device-enrollment-program-enroll-ios.md)

## <a name="user-enrollment"></a>Inscrição do utilizador
A Inscrição do Utilizador confere aos administradores um subconjunto de opções de gestão em comparação com outros métodos de inscrição. Para mais informações, consulte [as ações suportadas pelo Utilizador, palavras-passe e outras opções](ios-user-enrollment-supported-actions.md) e [configurar iOS/iPadOS e iPadOS User Registration](ios-user-enrollment.md).

## <a name="apple-school-manager"></a>Gestor Escolar da Apple

O Gestor Escolar da Apple é um programa de compra e inscrição de dispositivos da Apple para escolas. À semelhança do DEP, pode implementar um perfil para inscrever dispositivos para gestão. Saiba mais sobre o [Gestor Escolar da Apple](apple-school-manager-set-up-ios.md).

## <a name="apple-configurator"></a>Apple Configurator

Pode inscrever dispositivos iOS/iPadOS com o Configurator apple a funcionar num computador Mac. Para preparar os dispositivos, deve ligá-los via USB e instalar um perfil de inscrição. Pode inscrever dispositivos com o Apple Configurator de duas formas:

- Inscrição com o Assistente de Configuração – apaga os dados do dispositivo, prepara-o para executar o Assistente de Configuração e instala as políticas da empresa para o novo utilizador do dispositivo.
- Inscrição direta – não apaga os dados do dispositivo e inscreve-o com uma política predefinida. Este método destina-se a dispositivos sem afinidade de utilizador.

Saiba mais sobre a [inscrição no Apple Configurator](apple-configurator-enroll-ios.md).

## <a name="use-the-company-portal-on-dep-enrolled-or-apple-configurator-enrolled-devices"></a>Utilizar o Portal da Empresa em dispositivos inscritos pelo Apple Configurator ou pelo DEP

Os dispositivos configurados com a afinidade de utilizador podem instalar e executar a aplicação do Portal da Empresa para transferir aplicações e gerir dispositivos. Assim que os utilizadores recebem os respetivos dispositivos, têm de executar vários passos adicionais para concluir o Assistente de Configuração e instalar a aplicação do Portal da Empresa.

A afinidade de utilizador é necessária para suportar o seguinte:

- Aplicações de gestão de aplicações móveis (MAM)
- Acesso Condicional a emails e dados da empresa
- Aplicação do Portal da Empresa

### <a name="how-users-enroll-corporate-owned-iosipados-devices-with-user-affinity"></a>Como os utilizadores matriculam dispositivos iOS/iPadOS de propriedade corporativa com afinidade do utilizador

1. Quando os utilizadores ligam os dispositivos, é-lhes pedido que concluam o Assistente de Configuração.
2. Após concluir a configuração, é pedido o ID Apple aos utilizadores. Terão de fornecer um ID Apple para permitir que o dispositivo instale o Portal da Empresa.
3. O dispositivo iOS/iPadOS instala automaticamente a aplicação Portal da Empresa a partir da App Store.
4. Os utilizadores devem iniciar a aplicação Portal da Empresa e iniciar sessão com as credenciais (por exemplo, o nome pessoal exclusivo ou UPN) associadas à respetiva subscrição no Intune.
5. Depois de iniciar sessão, o processo de inscrição é concluído. Os utilizadores podem agora utilizar este dispositivo com o conjunto completo de funcionalidades.

### <a name="about-corporate-owned-managed-devices-with-no-user-affinity"></a>Sobre dispositivos pertencentes à empresa geridos sem afinidade de utilizador

Os dispositivos configurados sem afinidade de utilizador não suportam o Portal da Empresa e não devem ter a aplicação instalada. O Portal da Empresa foi concebido para utilizadores com credenciais da empresa e que necessitam de acesso a recursos empresariais personalizados (por exemplo, e-mail). Os dispositivos inscritos sem afinidade de utilizador não se destinam a ter um início de sessão de utilizador dedicado. Os dispositivos de quiosque, ponto de venda (POS) ou utilitário partilhado são casos de utilização típicos para dispositivos inscritos sem afinidade de utilizador.

Se for necessária afinidade de utilizador, confirme que o perfil de inscrição do dispositivo tem a opção **Afinidade do Utilizador** selecionada antes de o inscrever. Para alterar o estado de afinidade num dispositivo, tem de extinguir e voltar a inscrever o dispositivo.

## <a name="see-also"></a>Veja também

[Problemas de resolução de problemas de problemas de matrícula de dispositivos iOS/iPadOS no Microsoft Intune](https://support.microsoft.com/help/4039809)
