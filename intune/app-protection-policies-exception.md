---
title: Exceções da política de transferência de dados para aplicações
titleSuffix: Microsoft Intune
description: Crie exceções para a política de transferência de dados da Gestão de Aplicações Móveis (MAM) do Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/01/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f9015e3a-c22c-42eb-90e6-ba48dee3a41d
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 94798e7745b5802a551c4dda6908ff9f5f803d8f
ms.sourcegitcommit: e9ba1280b95565a5c5674b825881655d0303e688
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/15/2019
ms.locfileid: "54297353"
---
# <a name="how-to-create-exceptions-to-the-intune-mobile-application-management-mam-data-transfer-policy"></a>Como criar exceções para a política de transferência de dados da Gestão de Aplicações Móveis (MAM) do Intune

Como administrador, pode criar exceções para a política de transferência de dados da Gestão de Aplicações Móveis (MAM) do Intune. Uma exceção permite-lhe escolher especificamente que aplicações não geridas podem transferir dados de e para aplicações geridas. O departamento de TI têm de confiar as aplicações não geridas que incluir na lista de exceções. 

>[!WARNING] 
> Será responsável por fazer alterações à política de exceção de transferência de dados. As adições a esta política permitem que as aplicações não geridas (aplicações que não são geridas pelo Intune) acedam a dados protegidos por aplicações geridas. Este acesso a dados protegidos poderá resultar em falhas de segurança dos dados. Adicione exceções de transferência de dados apenas para as aplicações que a sua organização tem de utilizar, mas que não suportam as Políticas de Proteção de Aplicações do Intune. Além disso, adicione exceções apenas para aplicações que considera não representarem riscos de fuga de dados.

Dentro de uma política de proteção da aplicação Intune, definindo **permitir que a aplicação transfira dados para outras aplicações** ao **aplicações geridas por políticas** significa que a aplicação pode transferir dados apenas para aplicações geridas pelo Intune. Se tiver de permitir que os dados a serem transferidos para aplicações específicas que não suportam a aplicação do Intune, pode criar exceções a esta política utilizando **selecionar aplicações para isentar**. As exceções permitem que as aplicações geridas pelo Intune invoquem aplicações não geridas com base no protocolo de URL (iOS) ou nome do pacote (Android). Por predefinição, o Intune adiciona aplicações nativas fundamentais à lista de exceções. 

> [!NOTE]
> Modificar ou adicionar exceções de política de transferência de dados não afeta as outras Políticas de Proteção de Aplicações, tal como restrições de ações de cortar, copiar e colar. 

## <a name="ios-data-transfer-exceptions"></a>Exceções de transferência de dados em dispositivos iOS
Para uma política destinada a dispositivos iOS, pode configurar exceções de transferência de dados pelo protocolo de URL. Para adicionar uma exceção, verifique a documentação fornecida pelo programador da aplicação para encontrar informações acerca dos protocolos de URL suportados. Para obter mais informações sobre as exceções de transferência de dados do iOS, veja [isenções de transferência de definições de política de proteção de aplicações iOS - dados](app-protection-policy-settings-ios.md#data-transfer-exemptions).

> [!NOTE]
> A Microsoft não possui um método para localizar manualmente o protocolo URL que permite criar exceções para aplicações de terceiros. 

## <a name="android-data-transfer-exceptions"></a>Exceções de transferência de dados em dispositivos Android
Para uma política destinada a dispositivos Android, pode configurar as exceções de transferência de dados pelo nome do pacote de aplicação. Pode procurar a aplicação para a qual pretende adicionar uma exceção na página da loja **Google Play**, para encontrar o nome do pacote de aplicação. Para obter mais informações sobre exceções de transferência de dados em dispositivos Android, consulte [isenções de transferência de definições de política de proteção de aplicações Android - dados](app-protection-policy-settings-android.md#data-transfer-exemptions).


>[!TIP]
> Pode localizar o ID do pacote de uma aplicação ao navegar para a aplicação na Google Play Store. O ID do pacote está contido no URL da página da aplicação. Por exemplo, o ID do pacote da aplicação Microsoft Word é **com.microsoft.office.word**.

### <a name="example"></a>Exemplo
Adicionar o pacote **WebEx** como uma exceção à politica de transferência de dados da MAM permite que as ligações WebEx numa mensagem de e-mail do Outlook gerido sejam abertas diretamente na aplicação WebEx. A transferência de dados é restrita noutras aplicações não geridas.

- iOS **Webex** exemplo:   Para isentar a **Webex** aplicações geridas por aplicação, de modo que a TI da permissão para ser invocada pelo Intune, tem de adicionar uma exceção de transferência de dados para a seguinte cadeia: <code>wbx</code>
    
 - iOS **Maps** exemplo:  Para isentar nativa **Maps** aplicações geridas por aplicação, de modo que a TI da permissão para ser invocada pelo Intune, tem de adicionar uma exceção de transferência de dados para a seguinte cadeia: <code>maps</code>

- Android **Webex** exemplo:   Para isentar a **Webex** aplicações geridas por aplicação, de modo que a TI da permissão para ser invocada pelo Intune, tem de adicionar uma exceção de transferência de dados para a seguinte cadeia: <code>com.cisco.webex.meetings</code>
    
- Android **SMS** exemplo:   Para isentar nativa **SMS** à aplicação para que a TI da permissão para ser invocada pelo Intune as aplicações geridas em várias aplicações de mensagens e dispositivos Android, tem de adicionar exceções de transferência de dados para as seguintes cadeias: 
    <code>com.google.android.apps.messaging</code>
    
    <code>com.android.mms</code>
    
    <code>com.samsung.android.messaging</code>

## <a name="next-steps"></a>Passos Seguintes

- [Criar e implementar políticas de proteção de aplicações](app-protection-policies.md)
- [Definições de políticas de proteção de aplicações iOS – isenções de transferência de dados](app-protection-policy-settings-ios.md#data-transfer-exemptions)
- [Definições de políticas de proteção de aplicações Android – isenções de transferência de dados](app-protection-policy-settings-android.md#data-transfer-exemptions)
