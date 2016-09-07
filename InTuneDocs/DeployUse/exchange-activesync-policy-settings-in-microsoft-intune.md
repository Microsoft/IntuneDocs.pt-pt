---
title: "Definições de política do Exchange ActiveSync | Microsoft Intune"
description: "Utilize a política do Exchange ActiveSync do Intune para configurar definições que lhe permitam controlar funcionalidades em dispositivos geridos pelo Exchange ActiveSync."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 08/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e9cbb826-b155-4df6-abf3-60c6f05b2783
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 727d28cff074124b5401f6c2931f87df3a9d2d23
ms.openlocfilehash: d8f7de4013c1bdf6174cd4e1d7491514b11a14a3


---

# Definições de política do Exchange ActiveSync no Microsoft Intune
Utilize a política do **Exchange ActiveSync** do Microsoft Intune para configurar definições que controlam um leque de funcionalidades em dispositivos geridos pelo Exchange ActiveSync.


## Definições de palavra-passe

|Nome da definição|Detalhes
|----------------|
|**Palavra-passe obrigatória para desbloquear os dispositivos móveis**|Especifica se os dispositivos devem ser bloqueados ao utilizar uma palavra-passe.<br>(não aplicável a dispositivos com o Windows RT).|
|**Tipo obrigatório de palavra-passe**|Especifica o tipo de palavra-passe que será necessária, como apenas numérica ou alfanumérica.|
|**Comprimento mínimo da palavra-passe**|Especifica o número mínimo de carateres necessários na palavra-passe do dispositivo.|
|**Permitir palavras-passe simples**|Especifica se é possível utilizar palavras-passe simples, incluindo "0000" e "1234".|
|**Número de falhas de início de sessão consecutivas a permitir antes do dispositivo ser apagado**|Especifica o número de vezes que um utilizador pode introduzir uma palavra-passe incorreta antes de o dispositivo ser apagado.|
|**Expiração da palavra-passe (dias)**|Especifica o número de dias após o qual é necessário alterar a palavra-passe do dispositivo.
|**Memorizar histórico de palavras-passe**|Especifica se devem ser permitidas ou não palavras-passe utilizadas anteriormente.|
|**Memorizar histórico de palavras-passe** – **Evita a reutilização de palavras-passe anteriores**|especifica o número de palavras-passe utilizadas anteriormente que não podem ser utilizadas novamente.|
|**Minutos de inatividade antes da palavra-passe ser exigida**|Especifica o período de tempo durante o qual o dispositivo tem de estar inativo antes de o ecrã ser bloqueado.

## Definições de encriptação

|Nome da definição|Detalhes|
|----------------|
|**Encriptação obrigatória no dispositivo móvel**<sup>1</sup>|Requer que os dados num dispositivo sejam encriptados quando suportado.<br><br>Para dispositivos Windows Phone 8, tem de definir esta opção como **Sim**.<br /><br />Para ativar a encriptação em dispositivos iOS, ative a definição **Palavra-passe obrigatória para desbloquear os dispositivos móveis**.|
|**Encriptação obrigatória nos cartões de armazenamento**|Requer que os dados que estejam num armazenamento externo, como um cartão SD, sejam encriptados (nos dispositivos suportados).
<sup>1</sup> Informações adicionais para dispositivos com o Windows 8.1

-   Se quiser impor a encriptação nos dispositivos que executam o Windows 8.1, tem de instalar a [atualização de cliente MDM para Windows de dezembro de 2014](http://support.microsoft.com/kb/3013816) em cada dispositivo.

-   Se ativar esta definição em dispositivos com o Windows 8.1, todos os utilizadores do dispositivo têm de ter uma conta Microsoft.

-   Se quiser que a encriptação funcione em dispositivos com o Windows 8.1, o dispositivo tem de estar em conformidade com os requisitos de certificação de hardware do [InstantGo](http://blogs.windows.com/bloggingwindows/2014/06/19/instantgo-a-better-way-to-sleep/) da Microsoft.

-   Se impor a encriptação num dispositivo com Windows 8.1, a chave de recuperação só é acessível a partir da conta Microsoft do utilizador, que é acedida a partir da respetiva conta do OneDrive. Não pode recuperar esta chave em nome de um utilizador.

## Definições de e-mail

|Nome da definição|Detalhes
|----------------|
|**Permitir que os utilizadores transfiram anexos de e-mail**|Especifica se os anexos de e-mail podem ser transferidos para o dispositivo.|
|**Período de sincronização de e-mail**|Especifica o número de dias de e-mail recebido que será sincronizado com o dispositivo.
|**Permitir que os dispositivos móveis que não suportam completamente as definições do Exchange ActiveSync sincronizem com o Exchange**|Especifica se pretende permitir o acesso ao Exchange em dispositivos que não suportam uma ou mais definições do Exchange ActiveSync.

## Definições do browser

|Nome da definição|Detalhes
|----------------|-
|**Permitir browser**|Especifica se o browser do dispositivo pode ser utilizado.<br>(Não disponível para Windows RT ou Windows Phone).

## Definições de hardware

|Nome da definição|Detalhes
|----------------|
|**Permitir câmara**|Especifica se a câmara do dispositivo pode ser utilizada.<br>(Não disponível para Windows RT ou Windows Phone).



### Consulte também
[Gerir definições e funcionalidades nos seus dispositivos com as políticas do Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)



<!--HONumber=Aug16_HO5-->


