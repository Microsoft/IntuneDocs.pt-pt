---
title: Políticas de configuração para aplicações geridas sem inscrição de dispositivos
titlesuffix: Microsoft Intune
description: Saiba como configurar políticas para aplicações geridas sem inscrição de dispositivos.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 06/11/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: E61C1618-79D0-41A1-B61F-4123FB6672FC
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8ce8791eaf72f5fda969401c19e72c6cc8b538d6
ms.sourcegitcommit: b47fad133ef8ef1eb65484463431c6c53f6a638a
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35291466"
---
# <a name="add-app-configuration-policies-for-managed-apps-without-device-enrollment"></a>Adicionar políticas de configuração da aplicação para aplicações geridas sem inscrição de dispositivos

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Pode utilizar políticas de configuração da aplicação com aplicações geridas que suportem o SDK da Aplicação do Intune, até em dispositivos que não estejam inscritos. 

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços** > **Intune**. O Intune encontra-se na secção **Monitorização + Gestão**.
3. Selecione a carga de trabalho **Aplicações Móveis**.
4. Selecione **Políticas de configuração da aplicação** no grupo **Gerir** e, em seguida, selecione **Adicionar**.
5. Defina os seguintes detalhes:
    - **Nome**  
      O nome do perfil que será apresentado no portal do Azure.
    - **Descrição**  
      A descrição do perfil que será apresentada no portal do Azure.
    - **Tipo de inscrição do dispositivo**  
      Selecione **Gerir aplicações**.
6. Selecione **Aplicação associada** para escolher a aplicação que vai configurar. Selecione a aplicação na lista de aplicações que aprovou e sincronizou com o Intune.
7. Para cada definição de configuração que a aplicação suporta, escreva o **Nome** e o **Valor** e selecione as reticências (**...**).  
    Para eliminar uma configuração, selecione as reticências (**...**) e selecione **Eliminar**.  
    
As aplicações ativadas pelo SDK da Aplicação do Intune suportam configurações em pares chave-valor. Para saber mais sobre que configurações de chave-valor são suportadas, consulte a documentação de cada aplicação. Tenha em atenção que pode utilizar os tokens que serão dinamicamente preenchidos com dados gerados pela aplicação. Para obter informações sobre as definições de política de configuração da aplicação Outlook para iOS, veja [Gerir a configuração da aplicação Outlook para iOS com o Microsoft Intune](https://technet.microsoft.com/en-us/library/mt813789(v=exchg.150).aspx).

## <a name="configuration-values-for-using-tokens"></a>Valores de configuração para utilizar tokens

O Intune pode gerar determinados tokens e enviá-los para a aplicação gerida. Por exemplo, se a configuração da aplicação puder utilizar uma definição de e-mail, pode adicionar um e-mail dinâmico através de um token. Escreva o nome esperado pela aplicação no campo **Nome** e, em seguida, escreva `\{\{mail\}\}` no campo **Valor**.

O Intune suporta os seguintes tipos de tokens nas definições de configuração:

- \{\{userprincipalname\}\} – por exemplo, **John@contoso.com**
- \{\{mail\}\} – por exemplo, **John@contoso.com**
- \{\{partialupn\}\} – por exemplo, **João**
- \{\{accountid\}\} – por exemplo, **fc0dc142-71d8-4b12-bbea-bae2a8514c81**
- \{\{userid\}\} – por exemplo, **3ec2c00f-b125-4519-acf0-302ac3761822**
- \{\{username\}\} – por exemplo, **John Doe**
- \{\{PrimarySMTPAddress\}\} – por exemplo, **testuser@ad.domain.com** 


> [!Note]  
> Os carateres \{\{ e \}\} são utilizados apenas por tipos de token e não devem ser utilizados para outros fins.

## <a name="next-steps"></a>Próximos passos

Continue a [atribuir](apps-deploy.md) e [monitorizar](apps-monitor.md) a aplicação como é habitual.
