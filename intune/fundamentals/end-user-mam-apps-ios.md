---
title: Aplicações iOS com políticas de proteção de aplicações
description: Este tópico descreve o que esperar quando a sua aplicação iOS é gerida por políticas de proteção de aplicações.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 02/15/2018
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
ms.openlocfilehash: a1a3dcd7068a004f94b97b5ec6c43c609662a76d
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/05/2019
ms.locfileid: "73414565"
---
# <a name="what-to-expect-when-your-ios-app-is-managed-by-app-protection-policies"></a>O que esperar quando a sua aplicação iOS é gerida por políticas de proteção de aplicações

 Este tópico descreve a experiência do usuário ao usar aplicativos que têm políticas de proteção de aplicativo aplicadas. As políticas de proteção de aplicações são aplicadas apenas quando as aplicações são utilizadas num contexto de trabalho: por exemplo, quando o utilizador está a aceder a aplicações com uma conta profissional ou a aceder a ficheiros armazenados na localização empresarial do OneDrive para Empresas.

## <a name="access-apps"></a>Acesso às aplicações

Se o dispositivo **não estiver inscrito no Intune**, será pedido ao utilizador para reiniciar a aplicação quando utilizá-la pela primeira vez. É preciso um reinício para que as políticas de proteção de aplicações possam ser aplicadas.

<!--- The following screenshot from the Skype app illustrates this restart request: --->

<!---  ![Screenshot of the iOS device showing PIN prompt](./media/end-user-mam-apps-ios/iOS_AppPINPrompt.png) --->

Para dispositivos que estejam **inscritos para gestão no Intune**, o utilizador vê uma mensagem a indicar que a sua aplicação é agora gerida.

## <a name="use-apps-with-multi-identity-support"></a>Utilizar aplicações com suporte de identidades múltiplas

As aplicações que suportam várias identidades permitem-lhe utilizar contas diferentes (profissionais e pessoais) para aceder às mesmas aplicações, enquanto as políticas de proteção de aplicações são aplicadas apenas quando as aplicações são utilizadas no contexto de trabalho.  

Por exemplo, o utilizador obtém um pedido de PIN ao aceder a dados de trabalho. Para a **aplicação Outlook**, é pedido ao utilizador um PIN ao iniciar a aplicação. Para a **aplicação OneDrive**, é pedido ao utilizador um pin quando escreve na conta profissional.  Para o Microsoft **Word**, **PowerPoint** e **Excel**, é pedido um pin ao utilizador quando acede a documentos armazenados na localização empresarial do OneDrive para Empresas.

- Saiba mais sobre as aplicações que suportam a [proteção de aplicações e várias identidades](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) com o Intune.

As políticas de proteção de aplicações só são aplicadas no contexto profissional. Por conseguinte, a aplicação pode comportar-se de forma diferente consoante se o contexto é profissional ou pessoal.

## <a name="manage-user-accounts-on-the-device"></a>Gerir contas de utilizador no dispositivo

As aplicações de identidades múltiplas permitem aos utilizadores adicionar várias contas.  A aplicação Intune apenas suporta uma conta gerida.  A aplicação Intune não limita o número de contas não geridas.

Quando existe uma conta gerida numa aplicação:

- Se um utilizador tentar adicionar uma segunda conta gerida, é-lhe pedido para selecionar a conta gerida a utilizar.  A outra conta é removida.
- Se o administrador de TI adicionar uma política a uma segunda conta existente, é pedido ao utilizador que selecione a conta gerida a utilizar.  A outra conta é removida.

Leia o seguinte cenário de exemplo para obter uma compreensão mais aprofundada de como são tratadas as várias contas de utilizador.

O usuário A trabalha para duas empresas:**empresa X** e **empresa Y**. O usuário A tem uma conta de trabalho para cada empresa e ambos usam o Intune para implantar políticas de proteção de aplicativo. A **empresa X** implanta políticas de proteção de aplicativo **antes** **da empresa Y**. A conta associada à **empresa X** Obtém a política de proteção do aplicativo primeiro. Se pretender que a conta de utilizador que está associada à Empresa Y seja gerida pelas políticas de proteção de aplicações, terá de remover a conta de utilizador que está associada à Empresa X e adicionar a conta de utilizador que está associada à Empresa Y.

### <a name="add-a-second-account"></a>Adicionar uma segunda conta

Se estiver a utilizar um dispositivo iOS, quando tentar adicionar uma segunda conta profissional nesse dispositivo, poderá ver uma mensagem a informá-lo de que essa ação não é permitida. As contas são apresentadas e, em seguida, pode escolher a conta que pretende remover.

## <a name="next-steps"></a>Próximos passos

[O que esperar quando a aplicação Android é gerida por políticas de proteção de aplicações](end-user-mam-apps-android.md)
