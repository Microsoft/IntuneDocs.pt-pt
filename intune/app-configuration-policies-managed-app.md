---
title: Políticas de configuração para aplicações geridas sem inscrição de dispositivos
titlesuffix: Microsoft Intune
description: Saiba como configurar políticas para aplicações geridas sem inscrição de dispositivos.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/02/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: E61C1618-79D0-41A1-B61F-4123FB6672FC
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6f18676f7bb6117364e49fc0ce41619ab032a4e9
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/14/2019
ms.locfileid: "57396065"
---
# <a name="add-app-configuration-policies-for-managed-apps-without-device-enrollment"></a>Adicionar políticas de configuração da aplicação para aplicações geridas sem inscrição de dispositivos

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Pode utilizar políticas de configuração da aplicação com aplicações geridas que suportem o SDK da Aplicação do Intune, até em dispositivos que não estejam inscritos. 

1. Inicie sessão no [Portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços** > **Intune**. O Intune encontra-se na secção **Monitorização + Gestão**.
3. Selecione a carga de trabalho **Aplicações do cliente**.
4. Selecione **Políticas de configuração da aplicação** no grupo **Gerir** e, em seguida, selecione **Adicionar**.
5. Defina os seguintes detalhes:
    - **Nome**  
      O nome do perfil que será apresentado no portal do Azure.
    - **Descrição**  
      A descrição do perfil que será apresentada no portal do Azure.
    - **Tipo de inscrição do dispositivo**  
      Selecione **Gerir aplicações**.
6. Selecione **aplicação associada** para escolher a aplicação que pretende configurar. Selecione a aplicação na lista de aplicações que aprovou e sincronizou com o Intune.
7. Para cada definição de configuração que a aplicação suporta, escreva o **Nome** e o **Valor** e selecione as reticências (**...**).  
    Para eliminar uma configuração, selecione as reticências (**...**) e selecione **Eliminar**.  
    
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

## <a name="next-steps"></a>Passos Seguintes

Continue a [atribuir](apps-deploy.md) e [monitorizar](apps-monitor.md) a aplicação como é habitual.
