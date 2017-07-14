---
title: "Aplicações iOS com políticas de proteção de aplicações"
description: "Este tópico descreve o que esperar quando a sua aplicação iOS é gerida por políticas de proteção de aplicações."
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 05/05/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b57e6525-b57c-4cb4-a84c-9f70ba1e8e19
ms.reviewer: andcerat
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: e66042e5198b76ec484fe0218127acb653394cce
ms.sourcegitcommit: f100c943a635f5a08254ba7cf30f1aaebb7e810e
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/13/2017
---
# O que esperar quando a sua aplicação iOS é gerida por políticas de proteção de aplicações
<a id="what-to-expect-when-your-ios-app-is-managed-by-app-protection-policies" class="xliff"></a>

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

 Este tópico descreve a experiência do utilizador durante a utilização de aplicações com políticas de proteção de aplicações aplicadas aos mesmos. As políticas de proteção de aplicações são aplicadas apenas quando as aplicações são utilizadas num contexto de trabalho: por exemplo, quando o utilizador está a aceder a aplicações com uma conta profissional ou a aceder a ficheiros armazenados na localização empresarial do OneDrive para Empresas.

##  Acesso às aplicações
<a id="access-apps" class="xliff"></a>

Se o dispositivo **não estiver inscrito no Intune**, será pedido ao utilizador para reiniciar a aplicação quando utilizá-la pela primeira vez. É preciso um reinício para que as políticas de proteção de aplicações possam ser aplicadas.

<!--- The following screenshot from the Skype app illustrates this restart request: --->


<!---  ![Screenshot of the iOS device showing PIN prompt](../media/appmanagement/iOS_AppPINPrompt.png) --->

Para dispositivos que estejam **inscritos para gestão no Intune**, o utilizador vê uma mensagem a indicar que a sua aplicação é agora gerida.

##  Utilizar aplicações com suporte de identidades múltiplas
<a id="use-apps-with-multi-identity-support" class="xliff"></a>

As aplicações que suportam várias identidades permitem-lhe utilizar contas diferentes (profissionais e pessoais) para aceder às mesmas aplicações, enquanto as políticas de proteção de aplicações são aplicadas apenas quando as aplicações são utilizadas no contexto de trabalho.  

Por exemplo, o utilizador obtém um pedido de PIN ao aceder a dados de trabalho. Para a **aplicação Outlook**, é pedido ao utilizador um PIN ao iniciar a aplicação. Para a **aplicação OneDrive**, é pedido ao utilizador um pin quando escreve na conta profissional.  Para o Microsoft **Word**, **PowerPoint** e **Excel**, é pedido um pin ao utilizador quando acede a documentos armazenados na localização empresarial do OneDrive para Empresas.

- Saiba mais sobre as aplicações que suportam [MAM e várias identidades](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) com o Intune.

As políticas de proteção de aplicações só são aplicadas no contexto profissional. Por conseguinte, a aplicação pode comportar-se de forma diferente consoante se o contexto é profissional ou pessoal.

##  Gerir contas de utilizador no dispositivo
<a id="manage-user-accounts-on-the-device" class="xliff"></a>

O Intune suporta a implementação de políticas de proteção de aplicações apenas numa conta de utilizador por dispositivo.

* Consoante a aplicação que estiver a utilizar, o segundo utilizador poderá estar bloqueado no dispositivo. No entanto, em todos os casos, apenas o primeiro utilizador que obtém as políticas de proteção de aplicações é afetado pela política.
  * O **Microsoft Word**, **Excel** e **PowerPoint** não bloqueiam uma segunda conta de utilizador, mas a segunda conta de utilizador não é afetada pelas políticas de proteção de aplicações.  

  * Nas **aplicações OneDrive** e **Outlook**, só pode utilizar uma conta profissional. Não pode adicionar várias contas profissionais para estas aplicações. Pode, contudo, remover um utilizador e adicionar um utilizador diferente no dispositivo.

* Se um dispositivo tiver várias contas de utilizador antes de as políticas de proteção de aplicações serem implementadas, a conta em que as políticas de proteção de aplicações são implementadas em primeiro lugar é gerida pelas políticas de proteção de aplicações do Intune.


Leia o seguinte cenário de exemplo para obter uma compreensão mais aprofundada de como são tratadas as várias contas de utilizador.

O utilizador A trabalha para duas empresas — a **Empresa X** e a **Empresa Y**. O utilizador A tem uma conta profissional para cada empresa e ambas utilizam o Intune para implementar políticas de proteção de aplicações. A **Empresa X** implementa políticas de proteção de aplicações **antes da** **Empresa Y**. A conta que está associada à **Empresa X** obtém a política de proteção de aplicações, mas a conta que está associada à Empresa Y não. Se pretender que a conta de utilizador que está associada à Empresa Y seja gerida pelas políticas de proteção de aplicações, terá de remover a conta de utilizador que está associada à Empresa X.

### Adicionar uma segunda conta
<a id="add-a-second-account" class="xliff"></a>

Se estiver a utilizar um dispositivo iOS, quando tentar adicionar uma segunda conta profissional nesse dispositivo, poderá ver uma mensagem a informá-lo de que essa ação não é permitida. As contas serão apresentadas e, em seguida, pode escolher a conta que pretende remover.

## Próximos passos
<a id="next-steps" class="xliff"></a>
[O que esperar quando a aplicação Android é gerida por políticas de proteção de aplicações](end-user-mam-apps-android.md)