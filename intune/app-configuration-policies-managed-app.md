---
title: "Adicionar políticas de configuração da aplicação para aplicações geridas sem inscrição de dispositivos | Documentos da Microsoft"
titlesuffix: Azure portal
description: "Saiba como utilizar as políticas de configuração da aplicação para aplicações geridas sem inscrição de dispositivos."
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 10/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: E61C1618-79D0-41A1-B61F-4123FB6672FC
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 750ce7dbb0dccf08757e076826e2d3650b6e6ab5
ms.sourcegitcommit: 67c037af31c1f167ec9b4f4baa754631c817e7d1
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/01/2017
---
# <a name="add-app-configuration-policies-for-managed-apps-without-device-enrollment"></a>Adicionar políticas de configuração da aplicação para aplicações geridas sem inscrição de dispositivos

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Pode utilizar políticas de configuração da aplicação com aplicações geridas que suportem o SDK da Aplicação Intune inclusive em dispositivos que não estejam inscritos. 

1. Inicie sessão no portal do Azure.
2. Escolha **Mais Serviços** > **Monitorização + Gestão** + **Intune**.
3. Selecione a carga de trabalho **Aplicações Móveis**.
4. Clique em **Políticas de configuração da aplicação** no grupo **Gerir** e, em seguida, clique em **Adicionar**.
5. Defina os seguintes detalhes:
    - **Nome**  
      O nome do perfil que será apresentado no portal do Azure.
    - **Descrição**  
      A descrição do perfil que será apresentada no portal do Azure.
    - **Tipo de inscrição do dispositivo**  
      Selecione **Gerir aplicações**.
6. Selecione **Aplicação associada** para escolher a aplicação que vai configurar. Selecione a aplicação na lista de aplicações que aprovou e sincronizou com o Intune.
7. Para cada definição de configuração suportada pela aplicação, escreva o **Nome** e o **Valor**e clique nas reticências (**...**).  
    Para eliminar uma configuração, clique nas reticências (**...**) e selecione **Eliminar**.  
    As aplicações ativadas pelo SDK da Aplicação Intune suportam configurações em pares chave-valor. Consulte a documentação de cada aplicação para saber mais informações sobre as configurações de chave-valor suportadas.  
    Além disso, pode utilizar os tokens que serão dinamicamente preenchidos com dados gerados pela aplicação.

## <a name="configuration-values-using-tokens"></a>Valores de configuração com utilização de tokens

Alguns tokens podem ser gerados e enviados para a aplicação gerida pelo Intune. Por exemplo, se a configuração da aplicação permitir utilizar uma definição de e-mail, pode adicionar um e-mail dinâmico através da utilização de um token. Escreva o nome esperado pela aplicação no campo **Nome** e, em seguida, escreva `\{\{mail\}\}` no campo **Valor**.

O Intune suporta os seguintes tipos de tokens nas definições de configuração:

- \{\{userprincipalname\}\} - (Exemplo: **John@contoso.com**)
- \{\{mail\}\} - (Exemplo: **John@contoso.com**)
- \{\{partialupn\}\} - (Exemplo: **João**)
- \{\{accountid\}\} - (Exemplo: **fc0dc142-71d8-4b12-bbea-bae2a8514c81**)
- \{\{deviceid\}\} - (Exemplo: **b9841cd9-9843-405f-be28-b2265c59ef97**)
- \{\{userid\}\} - (Exemplo: **3ec2c00f-b125-4519-acf0-302ac3761822**)
- \{\{username\}\} - (Exemplo: **João Teixeira**)
- \{\{PrimarySMTPAddress\}\} – (Exemplo: testuser@ad.domain.com) 


> [!Note]  
> Os carateres \{\{ e \}\} são utilizados apenas por tipos de token e não devem ser utilizados para outros fins.

## <a name="next-steps"></a>Próximos passos

Continue a [atribuir](apps-deploy.md) e [monitorizar](apps-monitor.md) a aplicação como é habitual.