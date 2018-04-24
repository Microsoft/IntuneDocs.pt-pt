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
ms.openlocfilehash: 01523dc4c887214794d4600219ce0b77549b4734
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/16/2018
---
# <a name="enroll-ios-devices-in-intune"></a>Inscrever dispositivos iOS no Intune

O Intune ativa a gestão de dispositivos móveis (MDM) de iPads e iPhones para conceder aos utilizadores acesso a aplicações e ao e-mail da empresa.

Enquanto administrador do Intune, pode ativar a inscrição para dispositivos iOS. Pode permitir que os utilizadores inscrevam dispositivos pessoais. Este processo é conhecido como inscrição BYOD (Bring Your Own Device). Também pode ativar a inscrição de dispositivos pertencentes à empresa.

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

Os dispositivos configurados com a afinidade de utilizador podem instalar e executar a aplicação Portal da Empresa para transferir aplicações e gerir dispositivos. Assim que os utilizadores recebem os respetivos dispositivos, têm de executar vários passos adicionais para concluir o Assistente de Configuração e instalar a aplicação Portal da Empresa.

A afinidade de utilizador é necessária para suportar o seguinte:
  - Aplicações de gestão de aplicações móveis (MAM)
  - Acesso condicional a e-mail e dados da empresa
  - Aplicação Portal da Empresa

**Como os utilizadores inscrevem dispositivos iOS pertencentes à empresa com afinidade de utilizador**
1. Quando os utilizadores ligam os dispositivos, é-lhes pedido que concluam o Assistente de Configuração. Durante a configuração, os utilizadores recebem um pedido de credenciais. Terão de utilizar as credenciais (ou seja, o nome pessoal exclusivo ou UPN) associadas à respetiva subscrição no Intune.

2. Durante a configuração, os utilizadores recebem um pedido do Apple ID. Terão de fornecer um Apple ID para permitir que o dispositivo instale o Portal da Empresa. Também podem fornecer o ID no menu de definições do iOS após a conclusão da configuração.

3. Depois de concluir a configuração, o dispositivo iOS tem de instalar a aplicação Portal da Empresa a partir da App Store.

4. O utilizador poderá então iniciar sessão no Portal da Empresa através do UPN utilizado quando configurou o dispositivo.

5. Após iniciar sessão, é pedido ao utilizador que inscreva o dispositivo. O primeiro passo consiste em identificar o dispositivo. A aplicação apresenta uma lista de dispositivos iOS que já foram inscritos pela empresa e atribuídos à conta do Intune do utilizador. Deve escolher o dispositivo correspondente.

   Se este dispositivo ainda não tiver sido inscrito pela empresa, escolha **novo dispositivo** para continuar o fluxo de inscrição padrão.

6. No ecrã seguinte, o utilizador tem de confirmar o número de série do novo dispositivo. O utilizador pode tocar na ligação **Confirmar o Número de Série** para abrir as instruções de utilização da aplicação Definições e verificar o número de série. Em seguida, o utilizador tem de introduzir os últimos quatro carateres do número de série na aplicação Portal da Empresa.

   Este passo verifica se o dispositivo é o dispositivo da empresa inscrito no Intune. Se o número de série do dispositivo não coincidir, significa que foi selecionado o dispositivo errado. O utilizador deve voltar ao ecrã anterior e selecionar um dispositivo diferente.

7. Depois de verificar o número de série, a aplicação Portal da Empresa redireciona o utilizador para o site do Portal da Empresa para finalizar a inscrição. Em seguida, o site solicita ao utilizador que volte para a aplicação.

8. A inscrição está agora concluída. Agora, o utilizador pode utilizar este dispositivo com o conjunto completo de capacidades.

### <a name="about-corporate-owned-managed-devices-with-no-user-affinity"></a>Sobre dispositivos pertencentes à empresa geridos sem afinidade de utilizador

Os dispositivos configurados sem afinidade de utilizador não suportam o Portal da Empresa e não devem ter a aplicação instalada. O Portal da Empresa foi concebido para utilizadores com credenciais da empresa e que necessitam de acesso a recursos empresariais personalizados (por exemplo, e-mail). Os dispositivos inscritos sem afinidade de utilizador não se destinam a ter um início de sessão de utilizador dedicado. Os dispositivos de quiosque, ponto de venda (POS) ou utilitário partilhado são casos de utilização típicos para dispositivos inscritos sem afinidade de utilizador.

Se for necessária afinidade de utilizador, confirme que o perfil de inscrição do dispositivo tem a opção **Afinidade do Utilizador** selecionada antes de o inscrever. Para alterar o estado de afinidade num dispositivo, tem de extinguir e voltar a inscrever o dispositivo.

