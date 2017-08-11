---
title: "Aplicações iOS com políticas de proteção de aplicações"
titleSuffix: Intune on Azure
description: "Este tópico descreve o que esperar quando a sua aplicação iOS é gerida por políticas de proteção de aplicações.\""
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 586d9440-3813-4dec-b865-8bd319befde0
ms.reviewer: andcerat
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 4527e82ae9fa7226a0b7753111886882d85801e3
ms.sourcegitcommit: 2ee1e8248814d74cef80b609a8e43f59fa0b2618
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/09/2017
---
# <a name="what-to-expect-when-your-ios-app-is-managed-by-app-protection-policies"></a>O que esperar quando a sua aplicação iOS é gerida por políticas de proteção de aplicações

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Este tópico descreve a experiência do utilizador em aplicações com políticas de proteção. As políticas de proteção de aplicações são aplicadas apenas quando as aplicações são utilizadas no contexto de trabalho, como aceder a aplicações com a conta profissional ou aceder a ficheiros armazenados na localização empresarial do OneDrive para Empresas.
##  <a name="accessing-apps"></a>Aceder a aplicações

Se o dispositivo **não estiver inscrito no Intune**, será pedido ao utilizador final para reiniciar a aplicação quando utilizar a aplicação pela primeira vez.  É preciso um reinício para que as políticas de proteção de aplicações possam ser aplicadas à aplicação. A seguinte captura de ecrã ilustra isto, utilizando a aplicação Skype:


![captura de ecrã do dispositivo iOS que mostra o pedido de PIN](./media/ios-pin-prompt.png)

Para dispositivos que estejam **inscritos para gestão no Intune**, o utilizador final verá uma mensagem a indicar que a sua aplicação é agora gerida:

![captura de ecrã do dispositivo iOS que mostra a mensagem a indicar a gestão pela sua empresa com o pedido de PIN](./media/ios-managed-devices-pin-prompt.png)

##  <a name="using-apps-with-multi-identity-support"></a>Utilizar aplicações com suporte de várias identidades

As políticas de proteção de aplicações são apenas aplicadas no contexto de trabalho ao utilizar a aplicação, pelo que poderá experimentar diferentes comportamentos da aplicação consoante o contexto: profissional ou pessoal.  

Para aplicações que suportam várias identidades, o Intune apenas aplicará as políticas de proteção de aplicações se o utilizador final utilizar a aplicação no contexto de trabalho.  Por exemplo, o utilizador final irá obter um pedido de PIN ao aceder a dados de trabalho.  Para a **aplicação Outlook**, é pedido ao utilizador final um PIN ao iniciar a aplicação. Para a **aplicação OneDrive**, isto acontece quando o utilizador final introduz a conta profissional.  Para o Microsoft **Word**, **PowerPoint* e **Excel**, isto acontece quando o utilizador final acede a documentos armazenados na localização empresarial do OneDrive para Empresas.
##  <a name="managing-user-accounts-on-the-device"></a>Gerir contas de utilizador no dispositivo

O Intune só suporta a implementação de políticas de proteção de aplicações apenas numa conta de utilizador por dispositivo.

* Consoante a aplicação que estiver a utilizar, o segundo utilizador poderá ou não estar bloqueado no dispositivo. No entanto, em todos os casos, apenas o primeiro utilizador que obtém as políticas de proteção de aplicações é afetado pela política.
  * O **Microsoft Word**, **Excel** e **PowerPoint** não bloqueiam uma segunda conta de utilizador, mas a segunda conta de utilizador não é afetada pelas políticas de proteção de aplicações.  

  * Nas **aplicações OneDrive e Outlook**, só pode utilizar uma conta profissional.  Não é permitido adicionar várias contas profissionais nestas aplicações.  Pode, contudo, remover um utilizador e adicionar um utilizador diferente no dispositivo.

* Se um dispositivo tiver várias contas de utilizador existentes antes de as políticas de proteção de aplicações serem implementadas, a conta em que as políticas de proteção de aplicações são implementadas em primeiro lugar será gerida pelas políticas de proteção de aplicações do Intune.


Leia o cenário de exemplo abaixo para obter uma compreensão mais aprofundada de como são tratadas as várias contas de utilizador.

O utilizador A trabalha para duas empresas - a **Empresa X** e a **Empresa Y**. O utilizador A tem uma conta profissional para cada empresa e ambas utilizam o Intune para implementar políticas de proteção de aplicações. A **Empresa X** implementa políticas de proteção de aplicações **antes da** **Empresa Y**. A conta associada à **Empresa X** obterá a política de proteção de aplicações, mas a conta associada à Empresa Y não. Se pretender que a conta de utilizador associada à Empresa Y seja gerida pelas políticas de proteção de aplicações, terá de remover a conta de utilizador associada à Empresa X.
### <a name="adding-a-second-account"></a>Adicionar uma segunda conta

Se estiver a utilizar um dispositivo iOS, quando tentar adicionar uma segunda conta profissional no mesmo dispositivo, poderá ver uma mensagem a informá-lo de que essa ação não é permitida.  As contas serão apresentadas e pode escolher a conta que pretende remover.

![Captura de ecrã da caixa de diálogo com a mensagem a informar que a ação não é permitida e com as opções Sim e Não](./media/ios-switch-user.PNG)

## <a name="next-steps"></a>Próximos passos
[O que esperar quando a aplicação Android é gerida por políticas de proteção de aplicações](app-protection-enabled-apps-android.md)
### <a name="see-also"></a>Consulte também
[Criar e implementar políticas de proteção de aplicações com o Microsoft Intune](app-protection-policies.md)
