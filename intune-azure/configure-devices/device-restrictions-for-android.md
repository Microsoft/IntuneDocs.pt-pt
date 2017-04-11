---
title: "Definições de restrição de dispositivos no Intune para dispositivos Android"
titleSuffix: Intune Azure preview
description: "Pré-visualização do Azure no Intune: saiba que definições do Intune pode utilizar para controlar as definições dos dispositivos e a funcionalidade em dispositivos Android."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 03/29/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6bdf714a-5d93-485c-8b52-513635c60cb6
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: f316b332c3f1b80b9d6af488943298fcfea13741
ms.openlocfilehash: 009c6491b8ce457a371f5db31de3f122fa41fb95
ms.lasthandoff: 03/30/2017


---

# <a name="android-and-samsung-knox-standard-device-restriction-settings-in-microsoft-intune"></a>Definições de restrição de dispositivos Android e Samsung KNOX Standard no Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

## <a name="general"></a>Geral

|||||
|-|-|-|-|
|Nome da definição|Detalhes|Android 4.0+|Samsung KNOX Standard|
|**Câmara**|Permite a utilização da câmara do dispositivo.|Sim|Sim|
|**Copiar e colar**|Permite as funções de copiar e colar no dispositivo.|Não|Sim|
|**Partilha da área de transferência entre aplicações**|Permite a utilização da área de transferência para efetuar a ação copiar e colar entre aplicações.|Não|Sim|
|**Submissão de dados de diagnóstico**|Impede o utilizador de submeter dados de diagnóstico a partir do dispositivo.|Não|Sim|
|**Reposição de fábrica**|Permite ao utilizador efetuar uma reposição de fábrica no dispositivo.|Não|Sim|
|**Geolocalização**|Permite que o dispositivo utilize informações de localização (apenas no Samsung KNOX Standard).|Não|Sim|
|**Desligar**|Permite ao utilizador desligar o dispositivo.<br>Se esta definição estiver desativada, a definição **Número de falhas de início de sessão antes da eliminação de dados no dispositivo** dos dispositivos Samsung KNOX Standard não funcionará.|Não|Sim|
|**Captura de ecrã**|Permite ao utilizador capturar o conteúdo do ecrã como uma imagem.|Não|Sim|
|**Assistente de voz**|Permite a utilização de software de assistente de voz no dispositivo.|Não|Sim|
|**YouTube**|Permite a utilização da aplicação YouTube no dispositivo.|Não|Sim|

## <a name="password"></a>Palavra-passe

|||||
|-|-|-|-|
|Nome da definição|Detalhes|Android 4.0+|Samsung KNOX Standard|
|**Palavra-passe**|Exija que o utilizador final introduza uma palavra-passe para aceder ao dispositivo.|Sim|Sim|
|**Comprimento mínimo da palavra-passe**|Introduza o comprimento mínimo da palavra-passe que um utilizador tem de configurar (entre 4 e 16 carateres).|Sim|Sim|
|**Máximo de minutos de inatividade até o ecrã ser bloqueado**|Especifica o número de minutos de inatividade antes de o dispositivo bloquear automaticamente.|Sim|Sim|
|**Número de falhas de início de sessão antes de eliminar os dados do dispositivo**|Especifica o número de falhas de início de sessão consecutivas a permitir antes de o dispositivo ser apagado.|Sim|Sim|
|**Expiração da Palavra-passe (dias)**|Especifica o número de dias antes de ser necessário alterar a palavra-passe do dispositivo.|Sim|Sim|
|**Tipo obrigatório de palavra-passe**|Especifica o nível de complexidade da palavra-passe exigido e se podem ser utilizados dispositivos biométricos.|Sim|Sim|
|**Impedir a reutilização de palavras-passe anteriores**|Impede que o utilizador final crie uma palavra-passe que já tenha utilizado antes.|Sim|Sim|
|**Desbloqueio por impressão digital**|Permite a utilização de uma impressão digital para desbloquear os dispositivos suportados.|Não|Sim|
|**Smart Lock e outros agentes de fidedignidade**|Permite-lhe controlar a funcionalidade Smart Lock em dispositivos Android compatíveis (Samsung KNOX Standard 5.0 e posterior). Esta capacidade de telefone, por vezes conhecida como agente de confiança, permite desativar ou ignorar a palavra-passe de bloqueio do ecrã do dispositivo se o dispositivo estiver numa localização fidedigna (por exemplo, quando está ligado a um dispositivo Bluetooth específico ou quando está próximo de uma etiqueta NFC). Pode utilizar esta definição para impedir que os utilizadores configurem o Smart Lock.|Sim (5.0 e posterior)|Não|
|**Encriptação**|Requer que os ficheiros no dispositivo estejam encriptados.|Sim|Sim|

## <a name="google-play-store"></a>Google Play Store

|||||
|-|-|-|-|
|Nome da definição|Detalhes|Android 4.0+|Samsung KNOX Standard|
|**Google Play Store**|Permite ao utilizador aceder à Google Play Store no dispositivo|Não|Sim|

## <a name="restricted-apps"></a>Aplicações restritas

Na lista de aplicações restritas, pode configurar uma das seguintes listas:

Uma lista de **Aplicações proibidas** – Indique as aplicações (não geridas pelo Intune) que os utilizadores não têm permissão para instalar e executar.
Uma lista de **Aplicações aprovadas** – Indique as aplicações que os utilizadores têm permissão para instalar. Para permanecerem compatíveis, os utilizadores não têm de instalar aplicações que não estejam listadas. As aplicações geridas pelo Intune são automaticamente permitidas.
Os perfis de dispositivo que contêm as definições de aplicações restritas têm de ser implementados em grupos de utilizadores.

Para configurar a lista, clique em **Adicionar** e, em seguida, especifique um nome à sua escolha, o fabricante da aplicação (opcional) e o URL para a aplicação na loja de aplicações.

### <a name="how-to-specify-the-url-to-an-app-in-the-store"></a>Como especificar o URL para uma aplicação na loja

Para especificar um URL de aplicação na lista de aplicações conformes e não conformes, siga os seguintes passos:

Na [secção Aplicações do Google Play](https://play.google.com/store/apps), procure a aplicação que pretende utilizar.

Abra a página de instalação da aplicação e copie o URL para a área de transferência. Agora pode utilizar este URL na lista de aplicações conformes ou na lista de aplicações não conformes.

Exemplo: procure Microsoft Office Mobile no Google Play. O URL a utilizar será **https://play.google.com/store/apps/details?id=com.microsoft.office.officehub&hl=pt**.

### <a name="additional-options"></a>Opções adicionais

Também pode clicar em **Importar** para preencher a lista a partir de um ficheiro csv, no formato <*url da aplicação*>, <*nome da aplicação*>, <*publicador da aplicação*> ou clicar em **Exportar** para criar um ficheiro csv que contenha o conteúdo da lista de aplicações restritas no mesmo formato.        

## <a name="browser"></a>Browser
|||||
|-|-|-|-|
|Nome da definição|Detalhes|Android 4.0+|Samsung KNOX Standard|
|**Browser**|Especifica se pode ser utilizado o browser predefinido do dispositivo.|Não|Sim|
|**Preenchimento automático**|Permite a utilização da função de preenchimento automático do browser.|Não|Sim|
|**Cookies**|Permite ao browser do dispositivo utilizar cookies.|Não|Sim|
|**Javascript**|Permite que o browser do dispositivo execute scripts em Java.|Não|Sim|
|**Pop-ups**|Permite a utilização do bloqueador de janelas pop-up no browser.|Não|Sim|

## <a name="cloud-and-storage"></a>Cloud e Armazenamento
|||||
|-|-|-|-|
|Nome da definição|Detalhes|Android 4.0+|Samsung KNOX Standard|
|**Cópia de segurança do Google**|Permite a utilização da cópia de segurança do Google.|Não|Sim|
|**Sincronização automática da conta Google**|Permite que as definições da conta Google sejam sincronizadas automaticamente.|Não|Sim|
|**Armazenamento amovível**|Permite ao dispositivo utilizar armazenamento amovível, como um cartão SD.|Não|Sim|
|**Encriptação nos cartões de armazenamento**|Especifica se o cartão de armazenamento do dispositivo tem de estar encriptado.|Não|Sim|

## <a name="cellular-and-connectivity"></a>Rede Móvel e Conectividade
|||||
|-|-|-|-|
|Nome da definição|Detalhes|Android 4.0+|Samsung KNOX Standard|
|**Roaming de dados**|Permite dados em roaming quando o dispositivo estiver numa rede celular.|Não|Sim|
|**Mensagens SMS/MMS**|Permite a utilização de mensagens SMS e MMS no dispositivo.|Não|Sim|
|**Marcação por voz**|Ativa ou desativa a funcionalidade de marcação por voz no dispositivo.|Não|Sim|
|**Chamadas em roaming**|Permite chamadas em roaming quando o dispositivo estiver numa rede celular.|Não|Sim|
|**Bluetooth**|Permite a utilização de Bluetooth no dispositivo.|Não|Sim|
|**NFC**|Permite operações que utilizam comunicação de proximidade se o dispositivo a suportar.|Não|Sim|
|**Wi-Fi**|Permite a utilização das capacidades Wi-Fi do dispositivo.|Não|Sim|
|**Tethering Wi-Fi**|Permite a utilização de tethering Wi-Fi no dispositivo.|Não|Sim|

## <a name="kiosk"></a>Kiosk
|||||
|-|-|-|-|
|Nome da definição|Detalhes|Android 4.0+|Samsung KNOX Standard|
|**Selecionar uma aplicação gerida**|Navegue até às aplicações geridas e selecione uma que possa ser executada quando o dispositivo estiver no modo de local público (as aplicações especificadas como uma ligação para a loja não são atualmente suportadas). Não será permitida a execução de outras aplicações no dispositivo.|Não|Sim|
|**Botão de suspensão do ecrã**|Ativa ou desativa o botão suspender/reativar ecrã do dispositivo.|Não|Sim|
|**Botões de volume**|Ativa ou desativa a utilização dos botões de volume no dispositivo.|Não|Sim|

