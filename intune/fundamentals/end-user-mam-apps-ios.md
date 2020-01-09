---
title: Aplicações iOS com políticas de proteção de aplicações
description: Este tópico descreve o que esperar quando a sua aplicação iOS é gerida por políticas de proteção de aplicações.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 11/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: b57e6525-b57c-4cb4-a84c-9f70ba1e8e19
ms.reviewer: andcerat
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 165ce160339647e396b9cfc3a8374f21c77665f8
ms.sourcegitcommit: f9dc50642efa8656054ef67f9335b9b46b655f93
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/02/2020
ms.locfileid: "75606626"
---
# <a name="what-to-expect-when-your-ios-app-is-managed-by-app-protection-policies"></a>O que esperar quando a sua aplicação iOS é gerida por políticas de proteção de aplicações

As políticas de proteção de aplicativo do Intune se aplicam a aplicativos usados para trabalho ou escola. Isso significa que, quando seus funcionários e alunos usam seus aplicativos em um contexto pessoal, eles não podem notar nenhuma diferença em sua experiência. No entanto, no contexto corporativo ou de estudante, eles podem receber prompts para tomar decisões de conta, atualizar suas configurações ou contatá-lo para obter ajuda. Use este artigo para saber o que os usuários têm experiência ao tentar acessar e usar aplicativos protegidos pelo Intune.  

## <a name="access-apps"></a>Acesso às aplicações

Se o dispositivo **não estiver inscrito no Intune**, será pedido ao utilizador para reiniciar a aplicação quando utilizá-la pela primeira vez. Uma reinicialização é necessária para que as políticas de proteção do aplicativo possam ser aplicadas ao aplicativo.

<!--- The following screenshot from the Skype app illustrates this restart request: --->

<!---  ![Screenshot of the iOS device showing PIN prompt](./media/end-user-mam-apps-ios/iOS_AppPINPrompt.png) --->

Para dispositivos que estejam **inscritos para gestão no Intune**, o utilizador vê uma mensagem a indicar que a sua aplicação é agora gerida.

## <a name="use-apps-with-multi-identity-support"></a>Utilizar aplicações com suporte de identidades múltiplas

Os aplicativos que oferecem suporte a várias identidades permitem que você use contas pessoais e de trabalho diferentes para acessar os mesmos aplicativos. As políticas de proteção de aplicativo, como a inserção de um PIN de dispositivo, são ativadas quando os usuários acessam esses aplicativos em um contexto corporativo ou de estudante.   

Os usuários podem experimentar o prompt de PIN de forma diferente em todos os seus aplicativos, dependendo de como você configura as políticas.  Por exemplo, você pode configurar suas políticas para que:       
* O Microsoft Outlook solicita um PIN ao usuário quando ele inicia o aplicativo. 
* O OneDrive solicita ao usuário um PIN quando eles entram em sua conta corporativa.  
* O Microsoft Word, o PowerPoint e o Excel solicitam ao usuário um PIN quando acessam documentos armazenados no local da empresa no OneDrive for Business.  

- Saiba mais sobre as aplicações que suportam a [proteção de aplicações e várias identidades](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) com o Intune.  

## <a name="manage-user-accounts-on-the-device"></a>Gerir contas de utilizador no dispositivo  

As políticas de proteção de aplicativo do Intune limitam os usuários a uma conta corporativa ou de estudante gerenciada por aplicativo. As políticas de proteção de aplicativo não limitam o número de contas não gerenciadas que um usuário pode adicionar.   

- Se um utilizador tentar adicionar uma segunda conta gerida, é-lhe pedido para selecionar a conta gerida a utilizar. Se o usuário adicionar a segunda conta, a primeira conta será removida.
- Se você adicionar políticas de proteção a outra das contas do usuário, o usuário será solicitado a selecionar qual conta gerenciada usar. A outra conta é removida. 

Alguns usuários não terão a opção de alternar ou selecionar entre contas gerenciadas. A opção não está disponível em dispositivos que são:
* Gerenciado pelo Intune  
* Gerenciado por soluções de gerenciamento de mobilidade corporativa de terceiros e configurados com a configuração IntuneMAMUPN 

O cenário de exemplo a seguir descreve como várias contas de usuário são tratadas:  

O usuário A trabalha para duas empresas:**empresa X** e **empresa Y**. O usuário A tem uma conta de trabalho para cada empresa e ambos usam o Intune para implantar políticas de proteção de aplicativo. A **empresa X** implanta políticas de proteção de aplicativo **antes** **da empresa Y**. A conta associada à **empresa X** Obtém a política de proteção do aplicativo primeiro. Se pretender que a conta de utilizador que está associada à Empresa Y seja gerida pelas políticas de proteção de aplicações, terá de remover a conta de utilizador que está associada à Empresa X e adicionar a conta de utilizador que está associada à Empresa Y.  

## <a name="next-steps"></a>Próximos passos

[O que esperar quando a aplicação Android é gerida por políticas de proteção de aplicações](end-user-mam-apps-android.md)
