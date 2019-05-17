---
title: Definições dos dispositivos macOS no Microsoft Intune – Azure | Microsoft Docs
titleSuffix: ''
description: Adicionar, configurar ou criar definições em dispositivos macOS para restringir funcionalidades, incluindo a definição de requisitos de palavra-passe, controlar o ecrã bloqueado, utilizar aplicações incorporadas, adicionar aplicações restritas ou aprovadas, gerir dispositivos Bluetooth, ligar à cloud para cópia de segurança e armazenamento, ativar o modo de quiosque, adicionar domínios e controlar como os utilizadores interagem com o browser Safari no Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/13/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5feec66e791da4038bd069cdad69a7ba573f27f3
ms.sourcegitcommit: 1cae690ca2ac6cc97bbcdf656f54b31878297ae8
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/22/2019
ms.locfileid: "59897056"
---
# <a name="macos-device-settings-to-allow-or-restrict-features-using-intune"></a>Definições dos dispositivos macOS para permitir ou restringir funcionalidades com o Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Este artigo apresenta e descreve as diferentes definições que pode controlar nos dispositivos macOS. Como parte da solução de gestão de dispositivos móveis (MDM), utilize estas definições para permitir ou desativar funcionalidades, definir regras de palavra-passe, permitir ou restringir aplicações específicas e muito mais.

Estas definições são adicionadas a um perfil de configuração do dispositivo no Intune e, em seguida, atribuídas ou implementadas nos dispositivos macOS.

## <a name="before-you-begin"></a>Antes de começar

[Crie um perfil de configuração de restrições do dispositivo](device-restrictions-configure.md#create-the-profile).

## <a name="general"></a>Geral

- **Bloquear Pesquisa de Definição**: **Bloquear** impede que o utilizador realce uma palavra e, em seguida, procure a sua definição no dispositivo. **Não configurado** (predefinição) permite o acesso ao recurso de pesquisa de definição.
- **Bloquear Ditado**: **Bloquear** impede o utilizador de utilizar entradas de voz para introduzir texto. **Não configurado** (predefinição) permite que o utilizador utilize a entrada de ditado.
- **Bloquear a colocação de conteúdos em cache**: escolha **Não configurado** (predefinição) para ativar a colocação de conteúdos em cache. A colocação de conteúdos em cache armazena dados de aplicações, dados de browsers, downloads e muito mais, localmente no dispositivo. Selecione **Bloquear** para impedir que estes dados sejam armazenados na cache.

  Para obter mais informações sobre a colocação de conteúdos em cache no macOS, veja [Gerir a cache de conteúdo no Mac](https://support.apple.com/guide/mac-help/manage-content-caching-on-mac-mchl3b6c3720/mac) (abre outro site).

  Esta funcionalidade aplica-se a:  
  - macOS 10.13 e posterior

- **Adiar atualizações de software**: quando definido como **Não configurado** (predefinição), as atualizações de software são mostradas no dispositivo à medida que a Apple as lança. Por exemplo, se uma atualização do macOS for lançada pela Apple numa data específica, essa atualização será mostrada naturalmente no dispositivo por volta da data de lançamento. São permitidas atualizações de compilações de seed sem atraso.

  **Ativar** permite-lhe adiar a apresentação das atualizações de software nos dispositivos, entre 0 e 90 dias. Esta definição não controla quando as atualizações são ou não instaladas. 

  - **Adiar visibilidade das atualizações de software**: introduza um valor entre 0 e 90 dias. Quando o adiamento expirar, os utilizadores recebem uma notificação para atualizar para a versão mais antiga do SO disponível quando o adiamento foi acionado.

    Por exemplo, se uma atualização do macOS estiver disponível a **1 de janeiro** e **Adiar visibilidade** estiver definida como **5 dias**, a atualização não será mostrada como uma atualização disponível nos dispositivos. No **sexto dia** após o lançamento, essa atualização estará disponível e os utilizadores finais poderão instalá-la.

    Esta funcionalidade aplica-se a:  
    - macOS 10.13.4 e posterior

## <a name="password"></a>Palavra-passe

- **Palavra-passe**: **Exigir** que o utilizador final introduza uma palavra-passe para aceder ao dispositivo. **Não configurado** (predefinição) não requer uma palavra-passe e não impõe restrições, como bloquear palavras-passe simples ou definir um comprimento mínimo.
  - **Tipo obrigatório de palavra-passe**: especifique se a palavra-passe pode ser Apenas numérica ou se tem de ser Alfanumérica (conter letras e números). Esta definição só é suportada na versão 10.10.3 do Mac OS X e posterior.
  - **Número de carateres não alfanuméricos na palavra-passe**: Especifica o número de carateres complexos necessários na palavra-passe (de **0** a **4**).<br>Um caráter complexo é um símbolo, por exemplo "**?**".
  - **Comprimento mínimo da palavra-passe**: introduza o comprimento mínimo da palavra-passe que um utilizador tem de configurar (entre **4** e **16** carateres).
  - **Palavras-passe simples**: Permite a utilização de palavras-passe simples, tal como **0000** ou **1234**.
  - **Máximo de minutos após o bloqueio de ecrã antes de ser exigida a palavra-passe**: Especifica o período de tempo durante o qual o computador tem de estar inativo antes de ser exigida uma palavra-passe para o desbloquear.
  - **Máximo de minutos de inatividade até o ecrã ser bloqueado**: especifique o período de tempo durante o qual o computador tem de estar inativo antes de o ecrã ser bloqueado.
  - **Expiração da palavra-passe (dias)**: Especifica o número de dias que decorrem antes de o utilizador ter de alterar a palavra-passe (de **1** a **255** dias).
  - **Impedir a reutilização de palavras-passe anteriores**: introduza o número de palavras-passe utilizadas anteriormente que não podem ser utilizadas novamente, de **1** a **24**.

- **Impedir o Utilizador de Modificar o Código de Acesso**: escolha **Bloquear** para impedir que o código de acesso seja alterado, adicionado ou removido. **Não configurado** (predefinição) permite que os códigos de acesso sejam adicionados, alterados ou removidos.
- **Bloquear Desbloqueio por Impressão Digital**: escolha **Bloquear** para impedir a utilização de uma impressão digital para desbloquear o dispositivo. **Não configurado** (predefinição) permite ao utilizador desbloquear o dispositivo através de uma impressão digital.

- **Bloquear Preenchimento Automático de Palavra-passes**: escolha **Bloquear** para impedir a utilização da funcionalidade Preenchimento Automático de Palavras-passe no macOS. A escolha de **Bloquear** também tem o seguinte impacto:

  - Não é pedido aos utilizadores que utilizem uma palavra-passe guardada no Safari nem noutras aplicações.
  - As Palavras-passe Seguras automáticas estão desativadas, pelo que não são sugeridas aos utilizadores.

  **Não configurado** (predefinição) permite estas funcionalidades.

- **Bloquear pedidos de proximidade de palavra-passe**: escolha **Bloquear** para que o dispositivo de um utilizador não peça palavras-passe aos dispositivos próximos. **Não configurado** (predefinição) permite estes pedidos de palavras-passe.

- **Bloquear partilha de palavras-passe**: **Bloquear** impede a partilha de palavras-passe entre dispositivos com o AirDrop. **Não configurado** (predefinição) permite que as palavras-passe sejam partilhadas.

## <a name="built-in-apps"></a>Aplicações Incorporadas

- **Bloquear Preenchimento Automático do Safari**: **Bloquear** desativa a funcionalidade de preenchimento automático no Safari no dispositivo. **Não configurado** (predefinição) permite que os utilizadores alterem as definições de preenchimento automático no browser.
- **Bloquear Câmara**: escolha **Bloquear** para impedir o acesso à câmara no dispositivo. **Não configurado** (predefinição) permite o acesso à câmara do dispositivo.
- **Bloquear Apple Music**: **Bloquear** reverte a aplicação Music para o modo clássico e desativa o Serviço Music. **Não configurado** (predefinição) permite a utilização da aplicação Apple Music.
- **Bloquear Resultados de Pesquisa na Internet com Spotlight**: **Bloquear** impede a pesquisa Spotlight de devolver resultados de uma pesquisa da Internet. **Não configurado** (predefinição) permite que o Spotlight se ligue à Internet para fornecer resultados da pesquisa.
- **Bloquear Transferência de Ficheiros no iTunes**: **Bloquear** desativa os serviços de partilha de ficheiros da aplicação. Disponível no macOS 10.13 e posterior. **Não configurado** (predefinição) permite que os serviços partilhem ficheiros da aplicação.

## <a name="restricted-apps"></a>Aplicações restritas

Na lista de aplicações restritas, pode configurar uma das seguintes listas:

- Uma lista de **Aplicações proibidas**: indique as aplicações não geridas pelo Intune que os utilizadores não têm permissão para instalar e executar. Os utilizadores não são impedidos de instalar uma aplicação proibida, mas se o fizerem, esta ação será comunicada ao administrador.
- Uma lista de **Aplicações aprovadas**: Indique as aplicações que os utilizadores têm permissão para instalar. Os utilizadores não podem instalar aplicações que não estejam listadas. As aplicações geridas pelo Intune são automaticamente permitidas. Os utilizadores não são impedidos de instalar uma aplicação que não esteja na lista aprovada. Mas, se o fizerem, esta ação será comunicada ao administrador.

Para configurar a lista, clique em **Adicionar** e, em seguida, especifique um nome à sua escolha, opcionalmente, o publicador da aplicação e o ID do grupo da aplicação (por exemplo, *com.apple.calculator*).

## <a name="connected-devices"></a>Dispositivos ligados

- **Bloquear AirDrop**: **Bloquear** impede que o AirDrop seja utilizado no dispositivo. **Não configurado** (predefinição) permite utilizar a funcionalidade AirDrop para trocar conteúdo com os dispositivos próximos.
- **Bloquear Desbloqueio Automático do Apple Watch**: **Bloquear** impede os utilizadores de desbloquear o dispositivo macOS com o Apple Watch. **Não configurado** (predefinição) permite aos utilizadores desbloquear o dispositivo macOS com o Apple Watch.

## <a name="cloud-and-storage"></a>Cloud e armazenamento

- **Bloquear sincronização do Keychain com o iCloud**: escolha **Bloquear** para desativar a sincronização das credenciais armazenadas no Keychain com o iCloud. **Não configurado** (predefinição) permite aos utilizadores sincronizar estas credenciais.
- **Bloquear Sincronização de Documentos para iCloud**: **Bloquear** impede o iCloud de sincronizar documentos e dados. **Não configurado** (predefinição) permite a sincronização de documentos e pares chave-valor com o espaço de armazenamento do iCloud.
- **Bloquear Cópia de Segurança do Correio para iCloud**: **Bloquear** impede que o iCloud seja sincronizado com a aplicação Correio do macOS. **Não configurado** (predefinição) permite a sincronização do Correio com o iCloud.
- **Bloquear Cópia de Segurança de Contactos para iCloud**: **Bloquear** impede que os contactos dos dispositivos sejam sincronizados com o iCloud. **Não configurado** (predefinição) permite a sincronização de contactos através do iCloud.
- **Bloquear Cópia de Segurança do Calendário para iCloud**: **Bloquear** impede que o iCloud seja sincronizado com a aplicação Calendário do macOS. **Não configurado** (predefinição) permite a sincronização do Calendário com o iCloud.
- **Bloquear Cópia de Segurança de Lembretes para iCloud**: **Bloquear** impede que o iCloud seja sincronizado com a aplicação Lembretes do macOS. **Não configurado** (predefinição) permite a sincronização dos Lembretes com o iCloud.
- **Bloquear Cópia de Segurança dos Marcadores para iCloud**: **Bloquear** impede que o iCloud seja sincronizado com os Marcadores dos dispositivos. **Não configurado** (predefinição) permite a sincronização de Marcadores com o iCloud.
- **Bloquear Cópia de Segurança das Notas para iCloud**: **Bloquear** impede que o iCloud seja sincronizado com as Notas dos dispositivos. **Não configurado** (predefinição) permite a sincronização das Notas com o iCloud.

## <a name="domains"></a>Domínios

- **URL do Domínio de E-mail**: adicione um ou mais URLs à lista. Quando os utilizadores recebem um e-mail de um domínio não configurado, o e-mail é marcado como não fidedigno na aplicação Mail do macOS.

## <a name="next-steps"></a>Próximos passos

[Atribua o perfil](device-profile-assign.md) e [monitorize o respetivo estado](device-profile-monitor.md).

Também pode restringir as funcionalidades e as definições dos dispositivos nos dispositivos [iOS](device-restrictions-ios.md).
