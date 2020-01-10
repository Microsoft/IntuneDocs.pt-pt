---
title: Exceções da política de transferência de dados para aplicações
titleSuffix: Microsoft Intune
description: Crie exceções para a política de transferência de dados de política de Proteção de Aplicativo do Intune (aplicativo).
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/09/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f9015e3a-c22c-42eb-90e6-ba48dee3a41d
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0ea66458060417fc828b2b7735b384e8cd3e25a9
ms.sourcegitcommit: 637375a390b6e34f9c4415c77b99fe2980bbf554
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/10/2020
ms.locfileid: "75839382"
---
# <a name="how-to-create-exceptions-to-the-intune-app-protection-policy-app-data-transfer-policy"></a>Como criar exceções para a política de transferência de dados de política de Proteção de Aplicativo do Intune (aplicativo)

Como administrador, você pode criar exceções para a política de transferência de dados de política de Proteção de Aplicativo do Intune (aplicativo). Uma exceção permite-lhe escolher especificamente que aplicações não geridas podem transferir dados de e para aplicações geridas. Sua ti deve confiar nos aplicativos não gerenciados que você incluir na lista de exceções. 

>[!WARNING] 
> Será responsável por fazer alterações à política de exceção de transferência de dados. As adições a esta política permitem que as aplicações não geridas (aplicações que não são geridas pelo Intune) acedam a dados protegidos por aplicações geridas. Este acesso a dados protegidos poderá resultar em falhas de segurança dos dados. Adicione exceções de transferência de dados apenas para as aplicações que a sua organização tem de utilizar, mas que não suportam as Políticas de Proteção de Aplicações do Intune. Além disso, adicione exceções apenas para aplicações que considera não representarem riscos de fuga de dados.

Em uma política de proteção de aplicativo do Intune, a configuração **permitir que o aplicativo transfira dados para outros aplicativos** para **aplicativos gerenciados por política** significa que o aplicativo pode transferir dados somente para aplicativos gerenciados pelo Intune. Se precisar permitir que os dados sejam transferidos para aplicativos específicos que não dão suporte ao aplicativo do Intune, você poderá criar exceções a essa política usando **selecionar aplicativos para isentar**. As exceções permitem que as aplicações geridas pelo Intune invoquem aplicações não geridas com base no protocolo de URL (iOS) ou nome do pacote (Android). Por predefinição, o Intune adiciona aplicações nativas fundamentais à lista de exceções. 

> [!NOTE]
> Modificar ou adicionar exceções de política de transferência de dados não afeta as outras Políticas de Proteção de Aplicações, tal como restrições de ações de cortar, copiar e colar. 

## <a name="ios-data-transfer-exceptions"></a>Exceções de transferência de dados em dispositivos iOS
Para uma política destinada a dispositivos iOS, pode configurar exceções de transferência de dados pelo protocolo de URL. Para adicionar uma exceção, verifique a documentação fornecida pelo programador da aplicação para encontrar informações acerca dos protocolos de URL suportados. Para obter mais informações sobre exceções de transferência de dados do iOS, consulte [configurações de política de proteção de aplicativo IOS – isenções de transferência de dados](app-protection-policy-settings-ios.md#data-transfer-exemptions).

> [!NOTE]
> A Microsoft não possui um método para localizar manualmente o protocolo URL que permite criar exceções para aplicações de terceiros. 

## <a name="android-data-transfer-exceptions"></a>Exceções de transferência de dados em dispositivos Android
Para uma política destinada a dispositivos Android, pode configurar as exceções de transferência de dados pelo nome do pacote de aplicação. Pode procurar a aplicação para a qual pretende adicionar uma exceção na página da loja **Google Play**, para encontrar o nome do pacote de aplicação. Para obter mais informações sobre exceções de transferência de dados do Android, consulte [configurações de política de proteção de aplicativo Android – isenções de transferência de dados](app-protection-policy-settings-android.md#data-transfer-exemptions).


>[!TIP]
> Pode localizar o ID do pacote de uma aplicação ao navegar para a aplicação na Google Play Store. O ID do pacote está contido no URL da página da aplicação. Por exemplo, o ID do pacote da aplicação Microsoft Word é **com.microsoft.office.word**.

### <a name="example"></a>Exemplo
Adicionar o pacote **WebEx** como uma exceção à politica de transferência de dados da MAM permite que as ligações WebEx numa mensagem de e-mail do Outlook gerido sejam abertas diretamente na aplicação WebEx. A transferência de dados é restrita noutras aplicações não geridas.

- exemplo de **WebEx** do IOS: para isentar o aplicativo **WebEx** para que ele possa ser invocado por aplicativos gerenciados pelo Intune, você deve adicionar uma exceção de transferência de dados para a seguinte cadeia de caracteres: <code>wbx</code>
    
- exemplo de **mapas** do IOS: para isentar o aplicativo do **Maps** nativo para que ele possa ser invocado por aplicativos gerenciados pelo Intune, você deve adicionar uma exceção de transferência de dados para a seguinte cadeia de caracteres: <code>maps</code>

- Exemplo de **WebEx** do Android: para isentar o aplicativo **WebEx** para que ele possa ser invocado por aplicativos gerenciados pelo Intune, você deve adicionar uma exceção de transferência de dados para a seguinte cadeia de caracteres: <code>com.cisco.webex.meetings</code>
    
- Exemplo de **SMS** do Android: para isentar o aplicativo **SMS** nativo para que ele possa ser invocado por aplicativos gerenciados pelo Intune em diferentes aplicativos de mensagens e dispositivos Android, você deve adicionar exceções de transferência de dados para as seguintes cadeias de caracteres: 
    <code>com.google.android.apps.messaging</code>
    
    <code>com.android.mms</code>
    
    <code>com.samsung.android.messaging</code>

- Exemplo de **instalador de certificado** do Android: para isentar o aplicativo de instalador de **certificado** nativo para que o Outlook para Android possa instalar um certificado S/MIME (fornecido como um anexo de email) no repositório de chaves do Android, você deve adicionar a exceção de transferência de dados para a seguinte cadeia de caracteres: <code>com.android.certinstaller</code>. Para obter mais informações, consulte [rotulagem e proteção contra sensibilidade no Outlook para IOS e Android](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/sensitive-labeling-and-protection-outlook-for-ios-android).

## <a name="next-steps"></a>Próximos passos

- [Criar e implementar políticas de proteção de aplicações](app-protection-policies.md)
- [Definições de políticas de proteção de aplicações iOS – isenções de transferência de dados](app-protection-policy-settings-ios.md#data-transfer-exemptions)
- [Definições de políticas de proteção de aplicações Android – isenções de transferência de dados](app-protection-policy-settings-android.md#data-transfer-exemptions)
