---
title: Políticas de configuração para aplicações geridas sem inscrição de dispositivos
titleSuffix: Microsoft Intune
description: Saiba como configurar políticas para aplicações geridas sem inscrição de dispositivos.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: E61C1618-79D0-41A1-B61F-4123FB6672FC
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 68032f47be043e8c49b6ad922392d14549293c35
ms.sourcegitcommit: 73b362173929f59e9df57e54e76d19834f155433
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/27/2019
ms.locfileid: "74564282"
---
# <a name="add-app-configuration-policies-for-managed-apps-without-device-enrollment"></a>Adicionar políticas de configuração da aplicação para aplicações geridas sem inscrição de dispositivos

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Pode utilizar políticas de configuração da aplicação com aplicações geridas que suportem o SDK da Aplicação do Intune, até em dispositivos que não estejam inscritos. 

1. Entre no centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Escolha os **aplicativos** > **políticas de configuração de aplicativo** > **Adicionar** > **aplicativos gerenciados**.
3. Defina os seguintes detalhes:
    - **Nome**  
      O nome do perfil que será apresentado no portal do Azure.
    - **Descrição**  
      A descrição do perfil que será apresentada no portal do Azure.
4. Escolha **selecionar aplicativos públicos** ou **selecione aplicativos personalizados** para escolher o aplicativo que você vai configurar. Selecione a aplicação na lista de aplicações que aprovou e sincronizou com o Intune.
5. Para cada definição de configuração que o aplicativo dá suporte, digite o **nome** e o **valor**.  
    Para eliminar uma configuração, selecione as reticências ( **...** ) e selecione **Eliminar**.  
    
As aplicações ativadas pelo SDK da Aplicação do Intune suportam configurações em pares chave-valor. Para saber mais sobre que configurações de chave-valor são suportadas, consulte a documentação de cada aplicação. Tenha em atenção que pode utilizar os tokens que serão dinamicamente preenchidos com dados gerados pela aplicação. Para obter informações sobre as definições de política de configuração da aplicação Outlook para iOS, veja [Gerir a configuração da aplicação Outlook para iOS com o Microsoft Intune](https://technet.microsoft.com/library/mt813789(v=exchg.150).aspx).

## <a name="configuration-values-for-using-tokens"></a>Valores de configuração para utilizar tokens

O Intune pode gerar determinados tokens e enviá-los para a aplicação gerida. Por exemplo, se a configuração da aplicação puder utilizar uma definição de e-mail, pode adicionar um e-mail dinâmico através de um token. Escreva o nome esperado pela aplicação no campo **Nome** e, em seguida, escreva `\{\{mail\}\}` no campo **Valor**.

O Intune suporta os seguintes tipos de tokens nas definições de configuração. Não são suportados outros pares chave/valor personalizados.

- \{\{userprincipalname\}\} – por exemplo, John@contoso.com
- \{\{mail\}\} – por exemplo, John@contoso.com
- \{\{partialupn\}\} – por exemplo, João
- \{\{accountid\}\} – por exemplo, fc0dc142-71d8-4b12-bbea-bae2a8514c81
- \{\{userid\}\} – por exemplo, 3ec2c00f-b125-4519-acf0-302ac3761822
- \{\{username\}\} – por exemplo, João Teixeira
- \{\{PrimarySMTPAddress\}\} – por exemplo, testuser@ad.domain.com


> [!Note]  
> Os carateres \{\{ e \}\} são utilizados apenas por tipos de token e não devem ser utilizados para outros fins.

## <a name="next-steps"></a>Próximos passos

Continue a [atribuir](apps-deploy.md) e [monitorizar](apps-monitor.md) a aplicação como é habitual.
