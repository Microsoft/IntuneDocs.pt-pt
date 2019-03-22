---
title: definições de dispositivos macOS no Microsoft Intune – Azure | Documentos da Microsoft
titlesuffix: ''
description: Adicionar, configurar, ou criar definições em dispositivos macOS para restringir funcionalidades, incluindo a definição de requisitos de palavra-passe, controlar o ecrã bloqueado, utilize aplicações incorporadas, adicionar restrito ou aplicações aprovadas, lidar com dispositivos bluetooth, ligar à cloud para cópia de segurança e o armazenamento, ativar o modo de local público, adicionar domínios e controlar como os utilizadores interagem com o browser Safari no Microsoft Intune.
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
ms.openlocfilehash: 0a59c40a5f1095e832f84c4b21d553e3c5f11ed7
ms.sourcegitcommit: 464cf677e3746eaba46836dedfb94572a75032f9
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/21/2019
ms.locfileid: "58330424"
---
# <a name="macos-device-settings-to-allow-or-restrict-features-using-intune"></a>definições de dispositivos macOS para permitir ou restringir funcionalidades com o Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Este artigo apresenta e descreve as diferentes definições que pode controlar em dispositivos macOS. Como parte da sua solução de gestão (MDM) de dispositivos móveis, utilize estas definições para permitir ou desativar funcionalidades, definir regras de palavra-passe, permitir ou restringir aplicações específicas e muito mais.

Estas definições são adicionadas a um perfil de configuração do dispositivo no Intune e, em seguida, atribuídas ou implementadas nos seus dispositivos macOS.

## <a name="before-you-begin"></a>Antes de começar

[Criar um perfil de configuração de restrições de dispositivos](device-restrictions-configure.md#create-the-profile).

## <a name="general"></a>Geral

- **Bloquear pesquisa de definição de**: **Bloco** impede o utilizador de realçar uma palavra e, em seguida, procurar a respetiva definição no dispositivo. **Não configurado** (predefinição) permite o acesso para o recurso de pesquisa de definição.
- **Bloquear o ditado**: **Bloco** impede o utilizador através de entradas de voz para introduzir texto. **Não configurado** (predefinição) permite que o utilizador utilize a entrada de ditado.
- **Bloquear a colocação em cache conteúdo**: Escolher **não configurado** (predefinição) para ativar a colocação em cache conteúdo. A colocação em cache conteúdo armazena dados de aplicações, dados de navegador da web, downloads e muito mais localmente no dispositivo. Selecione **bloco** para impedir que esses dados a ser armazenados na cache.

  Para obter mais informações sobre a colocação em cache conteúdo no macOS, veja [gerir a colocação em cache conteúdo no Mac](https://support.apple.com/guide/mac-help/manage-content-caching-on-mac-mchl3b6c3720/mac) (abre-se outro Web site).

  Esta funcionalidade aplica-se a:  
  - macOS 10.13 e posterior

- **Diferir atualizações de software**: Quando definido como **não configurado** (predefinição), as atualizações de software são apresentadas no dispositivo como Apple as lança. Por exemplo, se uma atualização de macOS é lançada pela Apple numa data específica, em seguida, essa atualização naturalmente aparece no dispositivo em torno da data de lançamento. São permitidas atualizações de compilação de seed sem demora.

  **Ativar** permite-lhe atrasar a quando as atualizações de software são apresentadas nos dispositivos, de 0 a 90 dias. Esta definição não controla quando as atualizações são ou não estão instaladas. 

  - **Atrasar a visibilidade das atualizações de software**: Introduza um valor de 0 a 90 dias. Quando expira o atraso, os utilizadores obtêm uma notificação para atualizar para a versão mais antiga do SO disponível quando o atraso foi acionado.

    Por exemplo, se uma atualização do macOS está disponível no **1º de Janeiro**, e **atrasar visibilidade** está definida como **5 dias**, em seguida, a atualização não é mostrada como uma atualização disponível nos dispositivos. Sobre o **sexto dia** após o lançamento, que a atualização está disponível, e os utilizadores finais podem instalá-la.

    Esta funcionalidade aplica-se a:  
    - macOS 10.13.4 e posterior

## <a name="password"></a>Palavra-passe

- **palavra-passe**: **Exigir** o utilizador final introduza uma palavra-passe para aceder ao dispositivo. **Não configurado** não requer uma palavra-passe (predefinição) e não forçar restrições, como o bloqueio de palavras-passe simples ou definir um comprimento mínimo.
  - **Tipo de palavra-passe obrigatório**: Especifique se a palavra-passe só pode ser numérica ou se tem de ser alfanumérica (conter letras e números). Esta definição só é suportada na versão 10.10.3 do Mac OS X e posterior.
  - **Número de carateres não alfanuméricos na palavra-passe**: Especifica o número de carateres complexos necessários na palavra-passe (de **0** a **4**).<br>Um caráter complexo é um símbolo, por exemplo "**?**".
  - **Comprimento mínimo da palavra-passe**: Introduza o comprimento mínimo da palavra-passe de um utilizador tem de configurar (entre **4** e **16** carateres).
  - **Palavras-passe simples**: Permite a utilização de palavras-passe simples, tal como **0000** ou **1234**.
  - **Máximo de minutos após o bloqueio de ecrã antes de palavra-passe é exigida**: Especifica o período de tempo durante o qual o computador tem de estar inativo antes de ser exigida uma palavra-passe para o desbloquear.
  - **Máximo de minutos de inatividade até o ecrã bloquear**: Especifique o período de tempo que o computador tem de estar inativo antes do ecrã ser bloqueado.
  - **Expiração de palavra-passe (dias)**: Especifica o número de dias que decorrem antes de o utilizador ter de alterar a palavra-passe (de **1** a **255** dias).
  - **Impedir a reutilização de palavras-passe anteriores**: Introduza o número de palavras-passe utilizadas anteriormente que não podem ser reutilizadas, partir **1** ao **24**.

- **Impedir o utilizador modifique o código de acesso**: Escolher **bloco** para parar o código de acesso do que está a ser alterado, adicionado ou removido. **Não configurado** (predefinição) permite que os códigos de acesso ser adicionado, alteradas ou removidas.
- **Desbloqueio por impressão digital do bloco**: Escolher **bloco** para impedir a utilização de uma impressão digital para desbloquear o dispositivo. **Não configurado** (predefinição) permite ao utilizador desbloquear o dispositivo através de uma impressão digital.

- **Palavra-passe de bloco preenchimento automático**: Escolher **bloco** para impedir a utilização da funcionalidade de palavras-passe de preenchimento automático no macOS. Escolher **bloco** também tem o impacto seguinte:

  - Os utilizadores não são-lhe pedidos para utilizar uma palavra-passe guardada no Safari ou em todas as aplicações.
  - Palavras-passe forte de automáticas estão desativadas e as palavras-passe fortes não são sugeridas para os utilizadores.

  **Não configurado** (predefinição) permite que esses recursos.

- **Bloquear pedidos de proximidade de palavra-passe**: Escolher **bloco** para que o dispositivo de um utilizador não solicitar palavras-passe do dispositivos próximos. **Não configurado** (predefinição) permite que estes pedidos de palavra-passe.

- **Bloquear a partilha de palavra-passe**: **Bloco** impede a partilha de palavras-passe entre dispositivos com o AirDrop. **Não configurado** (predefinição) permite que as palavras-passe a ser partilhado.

## <a name="built-in-apps"></a>Aplicações Incorporadas

- **Bloquear o preenchimento automático do Safari**: **Bloco** desativa a funcionalidade de preenchimento automático no Safari no dispositivo. **Não configurado** (predefinição) permite que os utilizadores alterem as definições do browser.
- **Bloquear câmara**: Escolher **bloco** para impedir o acesso à câmara do dispositivo. **Não configurado** (predefinição) permite o acesso à câmara do dispositivo.
- **Bloquear músicas do Apple**: **Bloco** reverte o aplicativo de música para o modo clássico e desativa o serviço de música. **Não configurado** (predefinição) permite o uso de aplicação Apple Music.
- **Bloquear os resultados da pesquisa Spotlight Internet**: **Bloco** impede o destaque do retorno de resultados de uma pesquisa na Internet. **Não configurado** (predefinição) permite que o destaque pesquisa ligar à Internet para fornecer os resultados da pesquisa.
- **Transferência de ficheiros de bloco usando iTunes**: **Bloco** desativa os serviços de partilha de ficheiros de aplicação. Disponível no macOS 10.13 e posterior. **Não configurado** (predefinição) permite que os serviços de partilha de ficheiros de aplicação.

## <a name="restricted-apps"></a>Aplicações restritas

Na lista de aplicações restritas, pode configurar uma das seguintes listas:

- R **aplicações proibidas** lista: Indique as aplicações não geridas pelo Intune que os utilizadores não têm permissão para instalar e executar. Os utilizadores não são impedidos de instalar uma aplicação proibida mas, se o fizerem, será reportado para o administrador.
- Uma **aplicações aprovadas** lista: Indique as aplicações que os utilizadores têm permissão para instalar. Os utilizadores não podem instalar aplicações que não estão listadas. As aplicações geridas pelo Intune são automaticamente permitidas. Os utilizadores não são impedidos de instalar uma aplicação que não esteja na lista aprovada. No entanto, se o fizerem, será reportado para o administrador.

Para configurar a lista, clique em **Adicionar** e, em seguida, especifique um nome à sua escolha, opcionalmente, o publicador da aplicação e o ID do grupo da aplicação (por exemplo, *com.apple.calculator*).

## <a name="connected-devices"></a>Dispositivos ligados

- **Bloquear AirDrop**: **Bloco** impede o AirDrop a utilizar no dispositivo. **Não configurado** (predefinição) permite o uso da funcionalidade AirDrop para trocar conteúdos com dispositivos próximos.
- **Bloquear o Apple Watch automática desbloquear**: **Bloco** impede os utilizadores de desbloquear o dispositivo macOS com o Apple Watch. **Não configurado** (predefinição) permite aos utilizadores desbloquear os dispositivos macOS com o Apple Watch.

## <a name="cloud-and-storage"></a>Cloud e armazenamento

- **Bloquear a sincronização de Keychain do iCloud**: Escolher **bloco** para desativar a sincronização credenciais armazenadas na Keychain com o iCloud. **Não configurado** (predefinição) permite aos utilizadores sincronizar estas credenciais.
- **Bloquear a sincronização de documentos do iCloud**: **Bloco** impede a sincronização de documentos e dados de iCloud. **Não configurado** (predefinição) permite a sincronização de documentos e chave-valor para o seu espaço de armazenamento do iCloud.
- **Bloquear a cópia de segurança de email do iCloud**: **Bloco** impede que o iCloud sincronizados com o aplicativo de email do macOS. **Não configurado** (predefinição) permite a sincronização de correio com o iCloud.
- **Bloquear o contacto de cópia de segurança de iCloud**: **Bloco** impede a sincronização de contactos de dispositivos de iCloud. **Não configurado** (predefinição) permite a sincronização de contactos com o iCloud.
- **Bloquear o calendário de cópia de segurança de iCloud**: **Bloco** impede que o iCloud sincronizados com a aplicação de calendário do macOS. **Não configurado** (predefinição) permite a sincronização de calendário com o iCloud.
- **Bloquear o lembrete de cópia de segurança de iCloud**: **Bloco** impede que o iCloud sincronizados com a aplicação de lembretes de macOS. **Não configurado** (predefinição) permite a sincronização de lembretes para o iCloud.
- **Bloquear a cópia de segurança do marcador do iCloud**: **Bloco** impede a sincronizar os dispositivos indicadores de iCloud. **Não configurado** (predefinição) permite a sincronização de marcador para o iCloud.
- **Bloquear as notas de cópia de segurança de iCloud**: **Bloco** impede a sincronizar os dispositivos notas de iCloud. **Não configurado** (predefinição) permite a sincronização de notas para o iCloud.

## <a name="domains"></a>Domínios

- **URL do domínio de e-mail**: Adicione um ou mais URLs à lista. Quando os utilizadores recebem um e-mail de um domínio não configurado, o e-mail é marcado como não fidedigno na aplicação Mail do macOS.

## <a name="next-steps"></a>Passos Seguintes

[Atribua o perfil](device-profile-assign.md) e [monitorize o respetivo estado](device-profile-monitor.md).

Também pode restringir funcionalidades do dispositivo e definições no [iOS](device-restrictions-ios.md) dispositivos.
