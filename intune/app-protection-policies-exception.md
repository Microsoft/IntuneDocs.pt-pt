---
title: Exceções da política de transferência de dados para aplicações
titleSuffix: Microsoft Intune
description: Crie exceções para a política de transferência de dados da Gestão de Aplicações Móveis (MAM) do Intune.
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 03/28/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f9015e3a-c22c-42eb-90e6-ba48dee3a41d
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 812f73cb0857298f01967cebbb36f0b8220fb9c6
ms.sourcegitcommit: 179bea63fe52a8cce236b6ca8d82a6bd51bf17a5
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/15/2018
---
# <a name="how-to-create-exceptions-to-the-intune-mobile-application-management-mam-data-transfer-policy"></a>Como criar exceções para a política de transferência de dados da Gestão de Aplicações Móveis (MAM) do Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Como administrador, pode criar exceções para a política de transferência de dados da Gestão de Aplicações Móveis (MAM) do Intune. Uma exceção permite-lhe escolher especificamente que aplicações não geridas podem transferir dados de e para aplicações geridas. As aplicações não geridas que incluir na lista de exceções têm de ser consideradas fidedignas pelas TI. 

>[!WARNING] 
> Será responsável por fazer alterações à política de exceção de transferência de dados. As adições a esta política permitem que as aplicações não geridas (aplicações que não são geridas pelo Intune) acedam a dados protegidos por aplicações geridas. Este acesso a dados protegidos poderá resultar em falhas de segurança dos dados. Adicione exceções de transferência de dados apenas para as aplicações que a sua organização tem de utilizar, mas que não suportam as Políticas de Proteção de Aplicações do Intune. Além disso, adicione exceções apenas para aplicações que considera não representarem riscos de fuga de dados.

Na Política de Proteção de Aplicações do Intune, definir a opção **Permitir que a aplicação transfira dados para outras aplicações** para **Aplicações geridas por políticas** significa que a aplicação apenas pode transferir dados para aplicações geridas pelo Intune. Se precisar de permitir a transferência de dados para aplicações específicas que não suportem a aplicação Intune, pode criar exceções a essa política ao utilizar a opção **Selecione as aplicações a excluir**. As exceções permitem que as aplicações geridas pelo Intune invoquem aplicações não geridas com base no protocolo de URL (iOS) ou nome do pacote (Android). Por predefinição, o Intune adiciona aplicações nativas fundamentais à lista de exceções. 

## <a name="ios-data-transfer-exceptions"></a>Exceções de transferência de dados em dispositivos iOS
Para uma política destinada a dispositivos iOS, pode configurar exceções de transferência de dados pelo protocolo de URL. Para adicionar uma exceção, verifique a documentação fornecida pelo programador da aplicação para encontrar informações acerca dos protocolos de URL suportados. Para obter informações adicionais sobre as exceções de transferência de dados em dispositivos iOS, veja [Definições de políticas de proteção de aplicações iOS – isenções de transferência de dados](app-protection-policy-settings-ios.md#data-transfer-exemptions).

## <a name="android-data-transfer-exceptions"></a>Exceções de transferência de dados em dispositivos Android
Para uma política destinada a dispositivos Android, pode configurar as exceções de transferência de dados pelo nome do pacote de aplicação. Pode procurar a aplicação para a qual pretende adicionar uma exceção na página da loja **Google Play**, para encontrar o nome do pacote de aplicação. Para obter informações adicionais sobre as exceções de transferência de dados em dispositivos Android, veja [Definições de políticas de proteção de aplicações Android – isenções de transferência de dados](app-protection-policy-settings-android.md#data-transfer-exemptions).


>[!TIP]
> Pode localizar o ID do pacote de uma aplicação ao navegar para a aplicação na Google Play Store. O ID do pacote está contido no URL da página da aplicação. Por exemplo, o ID do pacote da aplicação Microsoft Word é **com.microsoft.office.word**.

### <a name="example"></a>Exemplo
Adicionar o pacote **WebEx** como uma exceção à política de transferência de dados da MAM permite que as ligações WebEx numa mensagem de e-mail do Outlook gerido sejam abertas diretamente na aplicação WebEx. A transferência de dados é restrita noutras aplicações não geridas.

- Exemplo de **WebEx** para iOS: para isentar a aplicação **WebEx** para ter permissão para ser invocada pelas aplicações geridas pelo Intune, tem de adicionar uma exceção de transferência de dados para a seguinte cadeia: <code>wbx</code>
    
 - Exemplo de **Maps** para iOS: para isentar a aplicação **Maps** nativa para que esta tenha permissão para ser invocada pelas aplicações geridas pelo Intune, tem de adicionar uma exceção de transferência de dados para a seguinte cadeia: <code>maps</code>

- Exemplo de **WebEx** para Android: para isentar a aplicação **WebEx** para que esta tenha permissão para ser invocada pelas aplicações geridas pelo Intune, tem de adicionar uma exceção de transferência de dados para a seguinte cadeia: <code>com.cisco.webex.meetings</code>
    
- Exemplo de **SMS** para Android: para isentar a aplicação **SMS** nativa para que esta tenha permissão para ser invocada pelas aplicações geridas pelo Intune em várias aplicações de mensagens e dispositivos Android, tem de adicionar exceções de transferência de dados para as seguintes cadeias: 
    <code>com.google.android.apps.messaging</code>
    
    <code>com.android.mms</code>
    
    <code>com.samsung.android.messaging</code>

## <a name="next-steps"></a>Próximos passos

- [Criar e implementar políticas de proteção de aplicações](app-protection-policies.md)
- [Definições de políticas de proteção de aplicações iOS – isenções de transferência de dados](app-protection-policy-settings-ios.md#data-transfer-exemptions)
- [Definições de políticas de proteção de aplicações Android – isenções de transferência de dados](app-protection-policy-settings-android.md#data-transfer-exemptions)
