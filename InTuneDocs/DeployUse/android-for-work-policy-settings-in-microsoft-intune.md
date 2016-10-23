---

title: "Definições de política do Android for Work | Microsoft Intune"
description: "Crie políticas que controlem as definições e funcionalidades em dispositivos Android for Work que gere com o Intune."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 10/12/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 35a53076-74d6-486d-b201-e0da2e170008
ms.reviewer: chrisbal
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 32bded5047b1a08738418e3e36382eeae1a5f3b4
ms.openlocfilehash: f7c676b25f5dd5b7ee1d1d7c1b51b75a41b5c102


---

# Definições de política do Android for Work no Microsoft Intune

O Intune oferece um conjunto de definições gerais incorporadas que pode configurar em dispositivos Android for Work.

## Política de configuração geral

Utilize a **política de configuração geral do Intune para Android for Work** para configurar definições de perfil de segurança e de trabalho para os seus dispositivos Android for Work.

Se a definição que procura não for apresentada neste tópico, poderá conseguir criá-la através de uma política personalizada para Android que lhe permita utilizar definições OMA-URI para controlar o dispositivo. Para obter mais informações, consulte [Definições de política personalizada](#custom-policy-settings) mais adiante neste tópico.

> [!TIP]
> Os dispositivos são automaticamente encriptados quando aprovisiona um perfil de trabalho. Não pode alterar esta definição.

### Definições de palavra-passe

|Nome da definição|Detalhes|
|----------------|-|
|**Palavra-passe obrigatória para desbloquear os dispositivos móveis**|Especifica se uma palavra-passe é obrigatória em dispositivos geridos. Escolha entre:<br><br>- **Complexa** – necessita de pelo menos uma letra, número e símbolo<br>- **Alfanumérica** – necessita de pelo menos um número e um caráter alfanumérico<br>- **Alfabética** – necessita de pelo menos letras ou símbolos<br>- **Numérica complexa** – necessita de carateres numéricos que não sejam repetidos ou consecutivos<br>- **Numérica**<br><br>Caso esta definição não esteja ativada, não existem requisitos de complexidade.|
|**Comprimento mínimo da palavra-passe**|Especifica o número mínimo de carateres ou números na palavra-passe.|
|**Minutos de inatividade antes de o dispositivo bloquear**|Especifica o número de minutos sem atividade do utilizador antes do dispositivo bloquear automaticamente.|
|**Permitir o bloqueio do smart card e outros agentes de fidedignidade**<br>(Android 6 e posterior)|Permite controlar a funcionalidade Smart Lock nos dispositivos Android compatíveis. Esta capacidade de telefone, por vezes conhecida como agente de confiança, permite desativar ou ignorar a palavra-passe de bloqueio do ecrã do dispositivo se o dispositivo estiver numa localização fidedigna (por exemplo, quando está ligado a um dispositivo Bluetooth específico ou quando está próximo de uma etiqueta NFC). Pode utilizar esta definição para impedir que os utilizadores configurem o Smart Lock.|
|**Número de falhas de início de sessão seguidas antes de o perfil de trabalho ser removido**|Especifica o número de falhas de início de sessão que são permitidas antes de o perfil de trabalho ser removido do dispositivo. Esta ação não efetua uma limpeza completa do dispositivo.|
|**Memorizar histórico de palavras-passe**|Impede a utilização de palavras-passe utilizadas anteriormente.|
|**Memorizar histórico de palavras-passe** - **Evita a reutilização de palavras-passe anteriores**|Especifica o número de palavras-passe utilizadas anteriormente a memorizar.|
|**Expiração da Palavra-passe (dias)**|Especifica o número de dias antes de ser necessário alterar a palavra-passe do dispositivo.|
|**Permitir desbloqueio por impressão digital**<br>(Android 6 e posterior)|Esta funcionalidade permite-lhe utilizar uma impressão digital para desbloquear dispositivos.|


### Definições de perfil de trabalho

|Nome da definição|Detalhes|
|----------------|-|
|**Permitir a partilha de dados entre perfis de trabalho e pessoais**|Permite que as aplicações do perfil de trabalho partilhem dados com as aplicações no perfil pessoal do utilizador. Escolha entre:<br><br>- **Impedir qualquer partilha entre limites**<br>- **As aplicações no perfil de trabalho podem processar um pedido de partilha do perfil pessoal**<br>- **Sem restrições à partilha**|
|**Ocultar notificações do perfil de trabalho quando o dispositivo está bloqueado**<br>(Android 6 e posterior)|Controlar quando mostrar as notificações do perfil de trabalho quando o dispositivo está bloqueado.|
|**Predefinir uma política de permissões de aplicação**<br>(Android 6 e posterior)|Predefine a política de permissões para todas as aplicações do perfil de trabalho.|




## Definições de política personalizada
Utilize a **política de configuração personalizada para Android for Work** do Microsoft Intune para implementar as definições OMA-URI que podem ser utilizadas para controlar funcionalidades nos dispositivos Android for Work. Tratam-se de definições padrão utilizadas por inúmeros fabricantes de dispositivos móveis para controlar as funcionalidades dos dispositivos.

Esta capacidade destina-se a permitir a implementação de definições do Android que não são configuráveis com políticas do Intune.

> [!NOTE]
> Atualmente, as políticas personalizadas do Android apenas suportam a configuração de definições Wi-Fi para dispositivos Android que incluam uma chave pré-partilhada.

### Definições gerais

|Nome da definição|Detalhes|
    |----------------|--------------------|
    |**Nome**|Introduza um nome exclusivo para a política personalizada do Android para o ajudar a identificá-la na consola do Intune.|
    |**Descrição**|Indique uma descrição geral da política personalizada do Android e outras informações relevantes que o ajudem a localizá-la.|

### Definições OMA-URI

   |Nome da definição|Detalhes|
    |--------|--------------------|
    |**Nome da definição**|Introduza um nome exclusivo para a definição OMA-URI para o ajudar a identificá-la na lista de definições.|
    |**Descrição da definição**|Indique uma descrição geral da definição e outras informações relevantes para o ajudar a localizá-la.|
    |**Tipo de dados**|Selecione o tipo de dados em que especificará esta definição OMA-URI. Escolha entre **Cadeia, Cadeia (XML), Data e hora, Número inteiro, Vírgula flutuante** ou **Booleano**.|
    |**OMA-URI (sensível às maiúsculas e minúsculas)**|Especifique o OMA-URI para o qual pretende fornecer uma definição.|
    |**Valor**|Indique o valor a associar ao OMA-URI especificado anteriormente.|

### Exemplos

- [Criar um perfil Wi-Fi com uma chave pré-partilhada](pre-shared-key-wi-fi-profile.md)
- [Utilizar uma política personalizada para criar um perfil de VPN por aplicação para dispositivos Android](per-app-vpn-for-android-pulse-secure.md)

### Consulte também
[Gerir definições e funcionalidades nos seus dispositivos com as políticas do Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)


<!--HONumber=Oct16_HO2-->


