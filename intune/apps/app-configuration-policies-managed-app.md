---
title: Políticas de configuração para aplicações geridas sem inscrição de dispositivos
titleSuffix: Microsoft Intune
description: Saiba como configurar políticas para aplicações geridas sem inscrição de dispositivos.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/23/2020
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
ms.openlocfilehash: 4301afca471d0aa56fa1a0826ad7f88bcdf23de2
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/17/2020
ms.locfileid: "77414877"
---
# <a name="add-app-configuration-policies-for-managed-apps-without-device-enrollment"></a>Adicionar políticas de configuração da aplicação para aplicações geridas sem inscrição de dispositivos

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Pode utilizar políticas de configuração da aplicação com aplicações geridas que suportem o SDK da Aplicação do Intune, até em dispositivos que não estejam inscritos. 

1. Inscreva-se no [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Escolha as **políticas** de **configuração** de Apps > Apps > **adicionar** > **aplicações geridas.**
3. Na página **Basics,** delineie os seguintes detalhes:
    - **Nome**: O nome do perfil que aparecerá no portal Azure.
    - **Descrição**: A descrição do perfil que aparecerá no portal Azure.
    - Tipo de **inscrição do dispositivo**: As aplicações geridas são selecionadas.
4. Escolha **selecione aplicações públicas** ou **selecione aplicações personalizadas** para escolher a aplicação que vai configurar. Selecione a aplicação na lista de aplicações que aprovou e sincronizou com o Intune.
5. Clique em **Seguir** para visualizar a página **Definições.**
6. Para cada configuração que a aplicação suporta, escreva o **Nome** e **o Valor**. 

   As aplicações ativadas pelo SDK da Aplicação do Intune suportam configurações em pares chave-valor. Para saber mais sobre que configurações de chave-valor são suportadas, consulte a documentação de cada aplicação. Tenha em atenção que pode utilizar os tokens que serão dinamicamente preenchidos com dados gerados pela aplicação. Para mais informações, consulte os valores de [Configuração para utilização de fichas](~/apps/app-configuration-policies-managed-app.md#configuration-values-for-using-tokens). Para obter informações sobre o Outlook para as definições de definição de políticas de configuração de aplicações iOS/iPadOS, consulte Manage Outlook para a configuração da [aplicação iOS/iPadOS com](https://technet.microsoft.com/library/mt813789(v=exchg.150).aspx)o Microsoft Intune .

    Para eliminar uma configuração, selecione as reticências ( **...** ) e selecione **Eliminar**.  

7. Clique em **Seguir** para exibir a página **de Tarefas.**
8. Clique em **Selecionar grupos para incluir**.
9. Selecione um grupo nos **grupos Select para incluir** o painel e clique **em Selecionar**.
10. Clique em **Selecionar grupos para excluir** para apresentar o painel relacionado.
11. Escolha os grupos que pretende excluir e, em seguida, clique em **Selecionar**.

    >[!NOTE]
    >Ao adicionar um grupo, se outro grupo já tiver sido incluído num determinado tipo de atribuição, o mesmo estará pré-selecionado e inalterável para outras atribuições de inclusão. Por conseguinte, esse grupo que foi utilizado não poderá ser utilizado como um grupo excluído.

12. Clique em **Seguir** para exibir a página **Review + criar.**
13. Clique **em Criar** para adicionar a política de configuração da aplicação ao Intune.

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
