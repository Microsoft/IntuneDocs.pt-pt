---
title: definições de dispositivos macOS no Microsoft Intune – Azure | Documentos da Microsoft
titlesuffix: ''
description: Adicionar, configurar ou criar definições em dispositivos macOS para restringir funcionalidades, incluindo a definição de requisitos de palavra-passe, controlar o ecrã bloqueado, utilize aplicações incorporadas, adicionar restrito ou aplicações aprovadas, lidar com dispositivos bluetooth, ligar para a cloud na cópia de segurança e o armazenamento, ativar o modo de local público, adicionar domínios e controlar como os utilizadores interagem com o browser Safari no Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/19/2018
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0d58a23899fbf6758687811b293418ee3b2adfb3
ms.sourcegitcommit: 9a4c5b6c2ce511edaeace25426a23f180cb71e15
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/07/2019
ms.locfileid: "57565354"
---
# <a name="macos-device-settings-to-allow-or-restrict-features-using-intune"></a>definições de dispositivos macOS para permitir ou restringir funcionalidades com o Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Este artigo apresenta e descreve as diferentes definições que pode controlar em dispositivos macOS. Como parte da sua solução de gestão (MDM) de dispositivos móveis, utilize estas definições para permitir ou desativar funcionalidades, definir regras de palavra-passe, permitir ou restringir aplicações específicas e muito mais.

Estas definições são adicionadas a um perfil de configuração do dispositivo no Intune e, em seguida, atribuídas ou implementadas nos seus dispositivos macOS.

## <a name="before-you-begin"></a>Antes de começar

[Criar um perfil de configuração de restrições de dispositivos](device-restrictions-configure.md#create-the-profile).

## <a name="general"></a>Geral

- **Bloquear a colocação em cache conteúdo**: Escolher **não configurado** (predefinição) para ativar a colocação em cache conteúdo. A colocação em cache conteúdo armazena dados de aplicações, dados de navegador da web, downloads e muito mais localmente no dispositivo. Selecione **bloco** para impedir que esses dados a ser armazenados na cache.

  Para obter mais informações sobre a colocação em cache conteúdo no macOS, veja [gerir a colocação em cache conteúdo no Mac](https://support.apple.com/guide/mac-help/manage-content-caching-on-mac-mchl3b6c3720/mac) (abre-se outro Web site).

  Esta funcionalidade aplica-se a:  
  - macOS 10.13 e posterior

- **Diferir atualizações de software (apenas supervisionadas)**: Quando definido como **não configurado** (predefinição), as atualizações de software são apresentadas no dispositivo como Apple as lança. Por exemplo, se uma atualização de macOS é lançada pela Apple numa data específica, em seguida, essa atualização naturalmente aparece no dispositivo em torno da data de lançamento.

  **Ativar** permite-lhe atrasar a quando as atualizações de software são apresentadas nos dispositivos, de 0 a 90 dias. Esta definição não controla quando as atualizações são ou não estão instaladas. 

  - **Atrasar a visibilidade das atualizações de software**: Introduza um valor de 0 a 90 dias. Quando expira o atraso, os utilizadores obtêm uma notificação para atualizar para a versão mais antiga do SO disponível quando o atraso foi acionado.

    Por exemplo, se uma atualização do macOS está disponível no **1º de Janeiro**, e **atrasar visibilidade** está definida como **5 dias**, em seguida, a atualização não é mostrada como uma atualização disponível nos dispositivos. Sobre o **sexto dia** após o lançamento, que a atualização está disponível, e os utilizadores finais podem instalá-la.

    Esta funcionalidade aplica-se a:  
    - macOS 10.13.4 e posterior

## <a name="password"></a>Palavra-passe

- **palavra-passe**: Exija que o utilizador final introduza uma palavra-passe para aceder ao dispositivo.
  - **Tipo de palavra-passe obrigatório**: Especifique se a palavra-passe só pode ser numérica ou se tem de ser alfanumérica (conter letras e números). Esta definição só é suportada na versão 10.10.3 do Mac OS X e posterior.
  - **Número de carateres não alfanuméricos na palavra-passe**: Especifica o número de carateres complexos necessários na palavra-passe (de **0** a **4**).<br>Um caráter complexo é um símbolo, por exemplo "**?**".
  - **Comprimento mínimo da palavra-passe**: Introduza o comprimento mínimo da palavra-passe de um utilizador tem de configurar (entre **4** e **16** carateres).
  - **Palavras-passe simples**: Permite a utilização de palavras-passe simples, tal como **0000** ou **1234**.
  - **Máximo de minutos após o bloqueio de ecrã antes de palavra-passe é exigida**: Especifica o período de tempo durante o qual o computador tem de estar inativo antes de ser exigida uma palavra-passe para o desbloquear.
  - **Máximo de minutos de inatividade até o ecrã bloquear**: Especifique o período de tempo que o computador tem de estar inativo antes do ecrã ser bloqueado.
  - **Expiração de palavra-passe (dias)**: Especifica o número de dias que decorrem antes de o utilizador ter de alterar a palavra-passe (de **1** a **255** dias).
  - **Impedir a reutilização de palavras-passe anteriores**: Introduza o número de palavras-passe utilizadas anteriormente que não podem ser reutilizadas, partir **1** ao **24**.

- **Palavra-passe de bloco preenchimento automático**: Escolher **bloco** para impedir a utilização da funcionalidade de palavras-passe de preenchimento automático no macOS. Escolher **bloco** também tem o impacto seguinte:

  - Os utilizadores não são-lhe pedidos para utilizar uma palavra-passe guardada no Safari ou em todas as aplicações.
  - Palavras-passe forte de automáticas estão desativadas e as palavras-passe fortes não são sugeridas para os utilizadores.

  **Não configurado** permite que esses recursos.

- **Bloquear pedidos de proximidade de palavra-passe**: Escolher **bloco** para que o dispositivo de um utilizador não solicitar palavras-passe do dispositivos próximos. **Não configurado** permite que estes pedidos de palavra-passe.

- **Bloquear a partilha de palavra-passe**: **Bloco** impede a partilha de palavras-passe entre dispositivos com o AirDrop. **Não configurado** permite que as palavras-passe a ser partilhado.

## <a name="restricted-apps"></a>Aplicações restritas

Na lista de aplicações restritas, pode configurar uma das seguintes listas:

- R **aplicações proibidas** lista: Indique as aplicações não geridas pelo Intune que os utilizadores não têm permissão para instalar e executar. Os utilizadores não são impedidos de instalar uma aplicação proibida mas, se o fizerem, será reportado para o administrador.
- Uma **aplicações aprovadas** lista: Indique as aplicações que os utilizadores têm permissão para instalar. Os utilizadores não podem instalar aplicações que não estão listadas. As aplicações geridas pelo Intune são automaticamente permitidas. Os utilizadores não são impedidos de instalar uma aplicação que não esteja na lista aprovada. No entanto, se o fizerem, será reportado para o administrador.

Para configurar a lista, clique em **Adicionar** e, em seguida, especifique um nome à sua escolha, opcionalmente, o publicador da aplicação e o ID do grupo da aplicação (por exemplo, *com.apple.calculator*).

## <a name="domains"></a>Domínios

### <a name="unmarked-email-domains"></a>Domínios de e-mail não marcados

No campo **URL de Domínio de E-mail**, adicione um ou mais URLs à lista. Quando os utilizadores recebem um e-mail de um domínio não configurado, o e-mail é marcado como não fidedigno na aplicação Mail do macOS.

## <a name="next-steps"></a>Passos Seguintes

[Atribua o perfil](device-profile-assign.md) e [monitorize o respetivo estado](device-profile-monitor.md).

Também pode restringir funcionalidades do dispositivo e definições no [iOS](device-restrictions-ios.md) dispositivos.