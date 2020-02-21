---
title: aplicações iOS/iPadOS com políticas de proteção de aplicações
description: Este tópico descreve o que esperar quando a sua aplicação iOS/iPadOS é gerida por políticas de proteção de aplicações.
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
ms.openlocfilehash: c854811a9deb938613af872f3cf86244ab9121b3
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514664"
---
# <a name="what-to-expect-when-your-iosipados-app-is-managed-by-app-protection-policies"></a>O que esperar quando a sua aplicação iOS/iPadOS for gerida por políticas de proteção de aplicações

As políticas de proteção de aplicações intonantes aplicam-se a apps que são utilizadas para o trabalho ou para a escola. Isto significa que quando os seus colaboradores e alunos usam as suas apps num contexto pessoal, podem notar nenhuma diferença na sua experiência. No contexto de trabalho ou escolar, no entanto, podem receber indicações para tomar decisões de conta, atualizar as suas configurações ou contactá-lo para obter ajuda. Use este artigo para saber o que os seus utilizadores experimentam quando tentam aceder e usar aplicações protegidas por Intune.  

## <a name="access-apps"></a>Acesso às aplicações

Se o dispositivo **não estiver inscrito no Intune**, será pedido ao utilizador para reiniciar a aplicação quando utilizá-la pela primeira vez. É necessário reiniciar para que as políticas de proteção de aplicações possam ser aplicadas à aplicação.

<!--- The following screenshot from the Skype app illustrates this restart request: --->

<!---  ![Screenshot of the iOS/iPadOS device showing PIN prompt](./media/end-user-mam-apps-ios/iOS_AppPINPrompt.png) --->

Para dispositivos que estejam **inscritos para gestão no Intune**, o utilizador vê uma mensagem a indicar que a sua aplicação é agora gerida.

## <a name="use-apps-with-multi-identity-support"></a>Utilizar aplicações com suporte de identidades múltiplas

As aplicações que suportam multiidentidade permitem-lhe utilizar diferentes contas pessoais e de trabalho para aceder às mesmas apps. As políticas de proteção de aplicações, como a introdução de um PIN de dispositivo, são ativadas quando os utilizadores acedem a estas aplicações num contexto de trabalho ou de escola.   

Os utilizadores podem experimentar o PEDIDO PIN de forma diferente em todas as suas apps, dependendo da configuração das políticas.  Por exemplo, pode configurar as suas políticas para:       
* O Microsoft Outlook pede ao utilizador um PIN quando lançar a aplicação. 
* O OneDrive pede ao utilizador um pino quando iniciar sessão na sua conta de trabalho.  
* Microsoft Word, PowerPoint e Excel solicitam ao utilizador um pin quando acedem a documentos armazenados na empresa OneDrive para localização de Negócios.  

- Saiba mais sobre as aplicações que suportam a [proteção de aplicações e várias identidades](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) com o Intune.  

## <a name="manage-user-accounts-on-the-device"></a>Gerir contas de utilizador no dispositivo  

As políticas de proteção de aplicações intonantes limitam os utilizadores a uma conta de trabalho ou escola gerida por app. As políticas de proteção de aplicações não limitam o número de contas não geridas que um utilizador pode adicionar.   

- Se um utilizador tentar adicionar uma segunda conta gerida, é-lhe pedido para selecionar a conta gerida a utilizar. Se o utilizador adicionar a segunda conta, a primeira conta é removida.
- Se adicionar políticas de proteção a outra das contas do utilizador, o utilizador é solicitado a selecionar qual a conta gerida a utilizar. A outra conta é removida. 

Alguns utilizadores não terão a opção de alternar ou selecionar entre contas geridas. A opção não está disponível em dispositivos que sejam:
* Gerido por Intune  
* Gerido por soluções de gestão da mobilidade empresarial de terceiros e configurado com a definição IntuneMAMUPN 

O seguinte exemplo descreve como várias contas de utilizador são tratadas:  

User A trabalha para duas empresas:**Empresa X** e **Empresa Y.** O utilizador A tem uma conta de trabalho para cada empresa, e ambos usam o Intune para implementar políticas de proteção de aplicações. **A Empresa X** implementa políticas de proteção de aplicações **antes** da **Empresa Y**. A conta que está associada à **Empresa X** recebe primeiro a política de proteção de aplicações. Se pretender que a conta de utilizador que está associada à Empresa Y seja gerida pelas políticas de proteção de aplicações, terá de remover a conta de utilizador que está associada à Empresa X e adicionar a conta de utilizador que está associada à Empresa Y.  

## <a name="next-steps"></a>Próximos passos

[O que esperar quando a aplicação Android é gerida por políticas de proteção de aplicações](end-user-mam-apps-android.md)
