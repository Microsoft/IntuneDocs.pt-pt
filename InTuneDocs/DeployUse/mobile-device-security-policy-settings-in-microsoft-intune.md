---
title: "Definições de política de segurança de dispositivos móveis | Microsoft Intune"
description: 
keywords: 
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e5ab3b76-08af-4893-b294-fb6627fdc4c6
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 42e21b802fb605c98f688485c3b77703b3950e94
ms.openlocfilehash: 8b7dac0bef8505567a9d0485fe6e952a3f6aa305


---

# Definições de política de segurança de dispositivos móveis no Microsoft Intune
> [!IMPORTANT]
> Agora, o Microsoft Intune inclui políticas de configuração separadas para cada plataforma de dispositivo, sendo que estas políticas contêm as definições mais atualizadas à sua disposição. Pode continuar a utilizar a política de segurança do dispositivo móvel e todas as implementações existentes continuarão a funcionar. No entanto, deve planear a migração para as novas políticas de configuração logo que possível, pois a política de segurança do dispositivo móvel será removida no futuro.

Utilize as políticas de segurança de dispositivos móveis do Intune para configurar uma grande variedade de definições que pode implementar em dispositivos geridos na sua organização. Estas definições podem ser utilizadas para controlar a funcionalidade e segurança dos seus dispositivos.

Pode criar e implementar políticas de segurança de dispositivos móveis para os seguintes tipos de dispositivos:

-   Dispositivos Windows RT 8.1 e dispositivos Windows 8.1 inscritos

-   Windows RT

-   Windows Phone 8 e Windows Phone 8.1

-   iOS

-   Android e Samsung KNOX

> [!NOTE]
> Algumas definições não são aplicáveis a alguns dispositivos. Consulte a tabela abaixo para obter uma lista completa das definições que pode configurar.

## Definições de segurança

|Nome da definição|Windows 8.1 e Windows RT 8.1|Windows RT|Windows Phone 8 e Windows Phone 8.1|iOS|Android e Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Palavra-passe obrigatória para desbloquear os dispositivos móveis**|Não|Não|Sim|Sim|Sim|
|**Tipo obrigatório de palavra-passe**<br /><br />(especifica o tipo de palavra-passe que será necessária, como apenas numérica ou alfanumérica)|Sim|Sim|Sim|Sim|Não|
|**Tipo de palavra-passe obrigatório – Número mínimo de conjuntos de carateres**<br /><br />Existem quatro conjuntos de carateres, letras minúsculas, letras maiúsculas, números e símbolos. Esta definição especifica quantos conjuntos de carateres diferentes têm de ser incluídos na palavra-passe). (No entanto, para dispositivos iOS, isto especifica o número de carateres de símbolos que têm de ser incluídos na palavra-passe)|Sim|Sim|Sim|Sim|Não|
|**Comprimento mínimo da palavra-passe**|Sim|Sim|Sim|Sim|Sim|
|**Permitir palavras-passe simples**<br /><br />As palavras-passes simples incluem "0000" e "1234"|Não|Não|Sim|Sim|Não|
|**Número de falhas de início de sessão consecutivas a permitir antes do dispositivo ser apagado**|Sim|Sim|Sim|Sim|Sim|
|**Minutos de inatividade antes de o ecrã se desligar**<sup>1</sup>|Sim|Sim|Sim|Sim|Sim|
|**Expiração da Palavra-passe (dias)**|Sim|Sim|Sim|Sim|Sim|
|**Memorizar histórico de palavras-passe**|Sim|Sim|Sim|Sim|Sim|
|**Memorizar histórico de palavras-passe** – **Evita a reutilização de palavras-passe anteriores**|Sim|Sim|Sim|Sim|Sim|
|**Qualidade da palavra-passe**|Não|Não|Não|Não|Sim|
|**Permitir palavra-passe por imagem e PIN**|Sim|Sim|Não|Não|Não|
|**Minutos de inatividade antes da palavra-passe ser exigida**|Não|Não|Não|Sim|Não|
|**Permitir desbloqueio por impressão digital**|Não|Não|Não|iOS 7 e posterior|Não|
Para dispositivos iOS, quando configura as definições **Minutos de inatividade antes de o ecrã desligar** e **Minutos de inatividade antes de a palavra-passe ser exigida**, estas são aplicadas em sequência. Por exemplo, se definir o valor das duas definições para **5** minutos, o ecrã desliga-se automaticamente após 5 minutos e o dispositivo fica bloqueado após mais 5 minutos. No entanto, se o utilizador desligar o ecrã manualmente, a segunda definição será imediatamente aplicada. No mesmo exemplo, depois de o utilizador desligar o ecrã, o dispositivo bloqueia 5 minutos depois.

Quando implementa uma política de comprimento de palavra-passe em dispositivos que executam o Windows RT, os utilizadores serão forçados a repor as respetivas palavras-passe, ainda que estas estejam em conformidade com os requisitos da política.

## Definições de encriptação

|Nome da definição|Windows 8.1 e Windows RT 8.1|Windows RT|Windows Phone 8 e Windows Phone 8.1|iOS|Android e Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Encriptação obrigatória no dispositivo móvel**<sup>1</sup><br /><br />Para dispositivos Windows Phone 8, tem de definir esta opção como **Sim**.<br /><br />Para ativar a encriptação em dispositivos iOS, ative a definição **Palavra-passe obrigatória para desbloquear os dispositivos móveis**.|Sim|Não|Sim|Não|Sim|
|**Encriptação obrigatória nos cartões de armazenamento**<br /><br />Aplica-se aos dispositivos que também são geridos pelo Exchange ActiveSync.|n/d|n/d|n/d (as aplicações e os dados associados são encriptados automaticamente)|n/d|Sim|
Informações adicionais para dispositivos que executam o Windows 8.1

-   Para impor a encriptação nos dispositivos que executam o Windows 8.1, tem de instalar a [atualização de cliente MDM para Windows de dezembro de 2014](http://support.microsoft.com/kb/3013816) em cada dispositivo.

-   Se ativar esta definição em dispositivos com o Windows 8.1, todos os utilizadores do dispositivo têm de ter uma Conta Microsoft.

-   Para que a encriptação funcione, o dispositivo tem de estar em conformidade com os requisitos de certificação de hardware do [InstantGo](http://blogs.windows.com/bloggingwindows/2014/06/19/instantgo-a-better-way-to-sleep/) da Microsoft.

-   Quando impõe a encriptação a um dispositivo, a chave de recuperação só é acessível a partir da Conta Microsoft do utilizador, que é acedida a partir da respetiva conta do OneDrive. Não pode recuperar esta chave em nome de um utilizador.

## Definições de malware

|Nome da definição|Windows 8.1 e Windows RT 8.1|Windows RT|Windows Phone 8 e Windows Phone 8.1|iOS|Android e Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Requerer firewall de rede**|Sim|Não|Não|Não|Não|
|**Ativar SmartScreen**|Sim|Não|Não|Não|Não|

## Definições do sistema

|Nome da definição|Windows 8.1 e Windows RT 8.1|Windows RT|Windows Phone 8 e Windows Phone 8.1|iOS|Android e Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Requerer atualizações automáticas**|Sim|Não|Não|Não|Não|
|**Requerer atualizações automáticas – classificação mínima de atualizações a instalar automaticamente**<br /><br />Escolha a classificação das atualizações que serão instaladas automaticamente:<br /><br />**Importante** – Instala todas as atualizações classificadas como importantes.<br /><br />**Recomendada** – Instala todas as atualizações classificadas como importantes ou recomendadas.|Sim|Não|Não|Não|Não|
|**Permitir captura de ecrã**|Não|Não|Apenas no Windows Phone 8.1|Sim|Sim (apenas Samsung KNOX)|
|**Permitir centro de controlo no ecrã de bloqueio**|Não|Não|Não|iOS 7 e posterior|Não|
|**Permitir vista de notificações no ecrã de bloqueio**|Não|Não|Não|iOS 7 e posterior|Não|
|**Permitir vista atual no ecrã de bloqueio**|Não|Não|Não|iOS 7 e posterior|Não|
|**Controlo de Conta de Utilizador**|Sim|Não|Não|Não|Não|
|**Permitir submissão de dados de diagnóstico**|Sim|Não|Apenas no Windows Phone 8.1|Sim|Sim (apenas Samsung KNOX)|
|**Permitir certificados TLS não fidedignos**|Não|Não|Não|Sim|Não|
|**Permitir software de carteira pessoal quando bloqueado**|Não|Não|Não|Sim|Não|
|**Permitir a reposição de fábrica**|Não|Não|Não|Não|Sim (apenas Samsung KNOX)|


## Definições da nuvem - documentos e dados

|Nome da definição|Windows 8.1 e Windows RT 8.1|Windows RT|Windows Phone 8 e Windows Phone 8.1|iOS|Android e Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Permitir cópia de segurança para iCloud**|Não|Não|Não|Sim|Não|
|**Permitir sincronização de documentos para iCloud**|Não|Não|Não|Sim|Não|
|**Permitir sincronização de Fluxo de Fotografias para iCloud**|Não|Não|Não|Sim|Não|
|**Exigir cópia de segurança encriptada**|Não|Não|Não|Sim|Não|
|**URL das Pastas de Trabalho**<br /><br />(define o URL da pasta de trabalho para permitir que os documentos sejam sincronizados em todos os dispositivos)|Sim|Não|Não|Não|Não|
|**Permitir cópia de segurança do Google**|Não|Não|Não|Não|Sim (apenas Samsung KNOX)|

## Definições da nuvem – contas e sincronização

|Nome da definição|Windows 8.1 e Windows RT 8.1|Windows RT|Windows Phone 8 e Windows Phone 8.1|iOS|Android e Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Permitir conta Microsoft**|Não|Não|Apenas no Windows Phone 8.1|Não|Não|
|**Permitir sincronização automática da conta Google**|Não|Não|Não|Não|Sim (apenas Samsung KNOX)|

## Definições de e-mail

|Nome da definição|Windows 8.1 e Windows RT 8.1|Windows RT|Windows Phone 8 e Windows Phone 8.1|iOS|Android e Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Permitir que os utilizadores transfiram anexos de e-mail**<sup>1</sup>|n/d|n/d|n/d|n/d|n/d|
|**Período de sincronização de e-mail** Aplica-se aos dispositivos que também são geridos pelo Exchange ActiveSync.|n/d|n/d|n/d|n/d|n/d|
|**Permitir que os dispositivos móveis que não suportam completamente estas definições se sincronizem com o Exchange (Exchange ActiveSync)** Aplica-se aos dispositivos que também são geridos pelo Exchange ActiveSync.|n/d|n/d|n/d|n/d|n/d|
|**Tornar a conta Microsoft opcional na aplicação Windows Mail**|Sim|Não|Não|Não|Não|
|**Permitir contas de e-mail personalizadas**|Não|Não|Apenas no Windows Phone 8.1|Não|Não|

## Definições da aplicação - browser

|Nome da definição|Windows 8.1 e Windows RT 8.1|Windows RT|Windows Phone 8 e Windows Phone 8.1|iOS|Android e Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Permitir browser**|Não|Não|Apenas no Windows Phone 8.1|Sim|Sim (apenas Samsung KNOX)|
|**Permitir preenchimento automático**|Sim|Não|Não|Sim|Sim (apenas Samsung KNOX)|
|**Permitir bloqueador de janelas de pop-up**|Sim|Não|Não|Sim|Sim (apenas Samsung KNOX)|
|**Permitir cookies**|Não|Não|Não|Sim|Sim (apenas Samsung KNOX)|
|**Permitir plug-ins**|Sim|Não|Não|Não|Não|
|**Permitir scripting ativo**|Sim|Não|Não|Sim|Sim (apenas Samsung KNOX)|
|**Permitir aviso de fraude**|Sim|Não|Não|Sim|Não|
|**Permitir site da intranet para introdução de uma única palavra**<br /><br />(permite utilizar uma única palavra para direcionar o Internet Explorer para um site, como, por exemplo, "Bing")|Sim|Não|Não|Não|Não|
|**Permitir deteção automática de rede intranet**|Sim|Não|Não|Não|Não|
|**Nível de segurança para a Internet**|Sim|Não|Não|Não|Não|
|**Nível de segurança para a intranet**|Sim|Não|Não|Não|Não|
|**Nível de segurança para sites fidedignos**|Sim|Não|Não|Não|Não|
|**Nível de segurança para sites restritos**|Sim|Não|Não|Não|Não|
|**Enviar cabeçalho Do Not Track**|Sim|Não|Não|Não|Não|
|**Permitir acesso ao menu do Modo Empresarial**|Sim|Não|Não|Não|Não|
|**Localização da lista de sites do Modo Empresarial**|Sim|Não|Não|Não|Não|

## Definições da aplicação - aplicações

|Nome da definição|Windows 8.1 e Windows RT 8.1|Windows RT|Windows Phone 8 e Windows Phone 8.1|iOS|Android e Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Permitir loja de aplicações**|Não|Não|Apenas no Windows Phone 8.1|Sim|Sim (apenas Samsung KNOX)|
|**Exigir uma palavra-passe para aceder à loja de aplicações**|Não|Não|Não|Sim|Não|
|**Permitir compras via aplicação**|Não|Não|Não|Sim|Não|
|**Permitir documentos geridos em outras aplicações não geridas**|Não|Não|Não|iOS 7 e posterior|Não|
|**Permitir documentos não geridos em outras aplicações geridas**|Não|Não|Não|iOS 7 e posterior|Não|
|**Permitir videoconferência**|Não|Não|Não|Sim|Não|
|**Permitir conteúdo para adultos no arquivo de multimédia**|Não|Não|Não|Sim|Não|
|**Permitir instalação de aplicações**|Não|Não|Não|iOS 6 e posterior|Não|

## Definições da aplicação - Jogos

|Nome da definição|Windows 8.1 e Windows RT 8.1|Windows RT|Windows Phone 8 e Windows Phone 8.1|iOS|Android e Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Permitir amigos do Centro de Jogos**|Não|Não|Não|Sim|Não|
|**Permitir jogos multijogador**|Não|Não|Não|Sim|Não|

## Definições das capacidades do dispositivo - hardware

|Nome da definição|Windows 8.1 e Windows RT 8.1|Windows RT|Windows Phone 8 e Windows Phone 8.1|iOS|Android e Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Permitir câmara**|Não|Não|Apenas no Windows Phone 8.1|Sim|Sim|
|**Permitir armazenamento amovível**|Não|Não|Sim|Não|Sim (apenas Samsung KNOX)|
|**Permitir Wi-Fi**|Não|Não|Apenas no Windows Phone 8.1|Não|Sim (apenas Samsung KNOX)|
|**Permitir partilha de Wi-Fi**|Não|Não|Apenas no Windows Phone 8.1|Não|Sim (apenas Samsung KNOX)|
|**Permitir ligação automática a hotspots Wi-Fi**|Não|Não|Apenas no Windows Phone 8.1|Não|Não|
|**Permitir relatórios de hotspots Wi-Fi**<br /><br />(enviar informações sobre ligações Wi-Fi para ajudar a detetar ligações próximas)|Não|Não|Apenas no Windows Phone 8.1|Não|Não|
|**Permitir geolocalização**<br /><br />(permite que o dispositivo utilize informações de localização)|Não|Não|Apenas no Windows Phone 8.1|Não|Sim (apenas Samsung KNOX)|
|**Permitir NFC**<br /><br />(permite operações que utilizam comunicação de proximidade)|Não|Não|Apenas no Windows Phone 8.1|Não|Sim (apenas Samsung KNOX)|
|**Permitir Bluetooth**|Não|Não|Apenas no Windows Phone 8.1|Não|Sim (apenas Samsung KNOX)|
|**Permitir desligar**<br>Se esta definição estiver desativada, a definição **Número de falhas de início de sessão repetidas permitidas antes da eliminação de dados no dispositivo** para dispositivos Samsung KNOX não funcionará.|Não|Não|Não|Não|Sim (apenas Samsung KNOX)|

## Definições das capacidades do dispositivo - rede móvel

|Nome da definição|Windows 8.1 e Windows RT 8.1|Windows RT|Windows Phone 8 e Windows Phone 8.1|iOS|Android e Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Permitir chamadas em roaming**|Não|Não|Não|Sim|Sim (apenas Samsung KNOX)|
|**Permitir roaming de dados**|Sim|Não|Não|Sim|Sim (apenas Samsung KNOX)|
|**Permitir sincronização automática em roaming**|Não|Não|Não|Sim|Não|
|**Permitir mensagens SMS/MMS**|Não|Não|Não|Não|Sim (apenas Samsung KNOX)|

## Definições das capacidades do dispositivo - funcionalidades

|Nome da definição|Windows 8.1 e Windows RT 8.1|Windows RT|Windows Phone 8 e Windows Phone 8.1|iOS|Android e Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Permitir assistente de voz**|Não|Não|Não|Sim|Sim (apenas Samsung KNOX)|
|**Permitir assistente de voz quando o dispositivo está bloqueado**|Não|Não|Não|Sim|Não|
|**Permitir marcação por voz**|Não|Não|Não|Sim|Sim (apenas Samsung KNOX)|
|**Permitir copiar e colar**|Não|Não|Apenas no Windows Phone 8.1|Não|Sim (apenas Samsung KNOX)|
|**Permitir partilha da área de transferência entre aplicações**|Não|Não|Não|Não|Sim (apenas Samsung KNOX)|
|**Permitir o YouTube**|Não|Não|Não|Não|Sim (apenas Samsung KNOX)|

### Consulte também
[Gerir definições e funcionalidades nos seus dispositivos com as políticas do Microsoft Intune.md](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)




<!--HONumber=Jun16_HO4-->


