---
title: "Definições de restrição de dispositivos no Intune para Android for Work | Microsoft Docs"
titleSuffix: Intune Azure preview
description: "Pré-visualização do Azure no Intune: saiba que definições do Intune pode utilizar para controlar as definições dos dispositivos e a funcionalidade em dispositivos Android for Work."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1830720b-16cb-4f2f-a71a-62967f882563
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: f9e8a5deb17ebb77d480213567e5ccf6550e3493
ms.openlocfilehash: be6303f2db508c2aca9ba9a40fcd43278f83c045
ms.contentlocale: pt-pt
ms.lasthandoff: 05/03/2017


---

# <a name="android-for-work-device-restriction-settings-in-microsoft-intune"></a>Definições de restrição de dispositivos Android for Work no Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

## <a name="work-profile-settings"></a>Definições de perfil de trabalho
-     **Partilha de dados entre perfis de trabalho e perfis pessoais** – utilize esta definição para controlar se as aplicações no perfil de trabalho podem partilhar dados com as aplicações no perfil pessoal. Escolha entre:
    - **Restrições de partilha predefinidas** – este é o comportamento de partilha predefinido do dispositivo, que varia consoante a versão do Android que está em execução. Por predefinição, é permitida a partilha do perfil pessoal com o perfil de trabalho. Também por predefinição, é bloqueada a partilha entre o perfil de trabalho e o perfil pessoal. Deste modo, impede a fuga de dados do perfil de trabalho para o perfil pessoal. A Google não proporciona uma forma de impedir que os dados sejam transmitidos do perfil pessoal para o perfil de trabalho em dispositivos com versões anteriores à 6.0.  
    - **As aplicações no perfil de trabalho podem processar o pedido de partilha do perfil pessoal** – utilize esta opção para ativar a funcionalidade do Android incorporada que permite a partilha do perfil pessoal para o perfil de trabalho. Quando esta opção estiver ativada, um pedido de partilha iniciado a partir de uma aplicação no perfil pessoal será capaz de partilhar com aplicações no perfil de trabalho. Este é o comportamento predefinido para dispositivos Android com versões anteriores à 6.0.
    - **As aplicações no perfil pessoal podem processar o pedido de partilha do perfil de trabalho** – ativa a partilha entre o limite do perfil de trabalho em ambas as direções. Quando seleciona esta definição, as aplicações no perfil de trabalho podem partilhar dados com aplicações não geridas no perfil pessoal.  Utilize esta definição com cuidado, uma vez que permite que dados geridos no perfil de trabalho sejam transferidos para o lado não gerido do dispositivo.


-     **Notificações do perfil de trabalho quando o dispositivo está bloqueado** –controla se as aplicações no perfil de trabalho podem apresentar notificações no ecrã quando o dispositivo está bloqueado.
-     **Permissões de aplicações predefinidas** – define a política de permissões predefinida para todas as aplicações do perfil de trabalho. A partir do Android 6, algumas permissões exigidas pelas aplicações são pedidas ao utilizador final no runtime. Esta definição de política permite-lhe decidir como ou se é pedido aos utilizadores a concessão de permissões de aplicações no perfil de trabalho.
Por exemplo, poderá transferir uma aplicação para o perfil de trabalho que precise de acesso de localização. Normalmente, essa aplicação apresentaria uma caixa de diálogo a perguntar ao utilizador se pretende conceder acesso de localização à aplicação e o utilizador pode aprová-lo ou negá-lo. Esta política permite-lhe decidir se todas as permissões devem ser concedidas automaticamente sem um pedido de confirmação, negadas automaticamente sem um pedido de confirmação ou permitir que o utilizador final decida. Escolha entre:
    -     **Predefinição do dispositivo**
    -     **Pedido de confirmação**
    -     **Conceder automaticamente**
    -     **Negar automaticamente**

## <a name="password"></a>Palavra-passe

- **Comprimento mínimo da palavra-passe:** introduza o número mínimo de carateres que a palavra-passe do utilizador tem de ter (**4**-**14**)
- **Máximo de minutos de inatividade até o ecrã ser bloqueado** –selecione a quantidade de tempo antes de um dispositivo inativo ser automaticamente bloqueado.
- **Número de falhas de início de sessão antes de eliminar os dados do dispositivo** – introduza o número de vezes que uma palavra-passe incorreta pode ser introduzida antes de todos os dados do dispositivo serem eliminados.
- **Expiração da palavra-passe (dias)** – introduza o número de dias até ser preciso alterar a palavra-passe do utilizador final (**1**-**255**).
- **Tipo de palavra-passe obrigatório** –selecione o tipo de palavra-passe que tem de ser definido no dispositivo. Escolha entre:
    - **Predefinição do dispositivo**
    - **Biométrica de segurança baixa**
    - **Necessário**
    - **Pelo menos numérica**
    - **Numérica complexa** – (números repetidos ou consecutivos, tais como “1111” ou “1234”, não são permitidos)
    - **Pelo menos alfabética**
    - **Pelo menos alfanumérica**
    - **Pelo menos alfanumérica com símbolos**
- **Impedir a reutilização de palavras-passe anteriores** –introduza o número de novas palavras-passe que têm de ter sido utilizadas antes de poder ser reutilizada uma antiga (**1**-**24**).
- **Desbloqueio por impressão digital** –impede um utilizador final de utilizar a deteção de impressão digital do dispositivo para o desbloquear.
- **Smart Lock e outros agentes de fidedignidade** – permite-lhe controlar a funcionalidade Smart Lock em dispositivos compatíveis. Esta capacidade de telefone, por vezes conhecida como agente de fidedignidade, permitirá desativar ou ignorar a palavra-passe de ecrã de bloqueio do dispositivo se o dispositivo estiver numa localização fidedigna (por exemplo, quando está ligado a um dispositivo Bluetooth específico ou quando está próximo de uma etiqueta NFC). Pode utilizar esta definição para impedir que os utilizadores configurem o Smart Lock.

## <a name="custom-policy-settings"></a>Definições de política personalizada
Utilize a **política de configuração personalizada para Android for Work** do Microsoft Intune para atribuir as definições OMA-URI que podem ser utilizadas para controlar as funcionalidades nos dispositivos Android for Work. Tratam-se de definições padrão utilizadas por inúmeros fabricantes de dispositivos móveis para controlar as funcionalidades dos dispositivos.

Esta capacidade destina-se a permitir a atribuição de definições do Android que não são configuráveis com as políticas do Intune.
Atualmente, o Intune suporta um número limitado de políticas personalizadas do Android. Consulte os exemplos neste tópico para saber quais as políticas que pode configurar.

### <a name="general-settings"></a>Definições gerais

|Nome da definição|Detalhes|
    |----------------|--------------------|
    |**Nome** |Introduza um nome exclusivo para a política personalizada do Android para o ajudar a identificá-la na consola do Intune.|
    |**Descrição** |Indique uma descrição geral da política personalizada do Android e outras informações relevantes que o ajudem a localizá-la.|

### <a name="oma-uri-settings"></a>Definições OMA-URI

  |Nome da definição|Detalhes|
  |--------|--------------------|
  |**Nome** |Introduza um nome exclusivo para a definição OMA-URI para o ajudar a identificá-la na lista de definições.|
  |**Descrição** |Indique uma descrição geral da definição e outras informações relevantes para o ajudar a localizá-la.|
    |**OMA-URI (sensível às maiúsculas e minúsculas)** |Especifique o OMA-URI para o qual pretende fornecer uma definição.|
  |**Tipo de dados** |Selecione o tipo de dados em que especificará esta definição OMA-URI. Escolha entre **Cadeia, Cadeia (XML), Data e hora, Número inteiro, Vírgula flutuante** ou **Booleano**.|
  |**Valor** |Indique o valor a associar ao OMA-URI especificado anteriormente.|

