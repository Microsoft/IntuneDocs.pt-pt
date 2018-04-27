---
title: Aplicações iOS com políticas de proteção de aplicações
titlesuffix: Microsoft Intune
description: Saiba o que esperar de uma aplicação iOS com políticas de proteção.
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 12/07/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 586d9440-3813-4dec-b865-8bd319befde0
ms.reviewer: andcerat
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 172e99a38e3aef500fca8563079e3656e372089b
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/26/2018
---
# <a name="what-to-expect-when-your-ios-app-is-managed-by-app-protection-policies"></a>O que esperar quando a sua aplicação iOS é gerida por políticas de proteção de aplicações

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Saiba mais sobre a experiência do utilizador em aplicações iOS com políticas de proteção. As políticas de proteção de aplicações só são aplicadas quando as aplicações são utilizadas no contexto de trabalho. Por exemplo, quando acede a uma aplicação com uma conta profissional ou quando acede a ficheiros armazenados na localização do OneDrive da sua empresa.
##  <a name="accessing-apps"></a>Aceder a aplicações

Se o dispositivo **não estiver inscrito no Intune**, será pedido ao utilizador que reinicie a aplicação quando a utilizar pela primeira vez.  É preciso um reinício para que as políticas de proteção de aplicações possam ser aplicadas à aplicação. A seguinte captura de ecrã ilustra isto, utilizando a aplicação Skype:


![captura de ecrã do dispositivo iOS que mostra o pedido de PIN](./media/ios-pin-prompt.png)

Para dispositivos que estejam **inscritos para gestão no Intune**, o utilizador verá uma mensagem a indicar que a sua aplicação é agora gerida:

![captura de ecrã do dispositivo iOS que mostra a mensagem a indicar a gestão pela sua empresa com o pedido de PIN](./media/ios-managed-devices-pin-prompt.png)

##  <a name="using-apps-with-multi-identity-support"></a>Utilizar aplicações com suporte de várias identidades

As políticas de proteção de aplicações entram em vigor quando um utilizador tenta aceder a dados relacionados com o trabalho.  Poderá observar diferentes comportamentos se o utilizador aceder à aplicação para fins pessoais. 

Em aplicações que suportam várias identidades, o Intune apenas aplica políticas de proteção se um utilizador aceder a dados profissionais.  Por exemplo, pode ser pedido ao utilizador que introduza um PIN.  Na **aplicação Outlook**, é apresentada uma mensagem quando um utilizador inicia a aplicação. Na **aplicação OneDrive**, é apresentada uma mensagem quando um utilizador introduz a sua conta profissional.  No Microsoft **Word**, **PowerPoint** e **Excel**, é apresentada uma mensagem quando um utilizador acede a documentos do OneDrive da empresa.
##  <a name="managing-user-accounts-on-the-device"></a>Gerir contas de utilizador no dispositivo

O Intune só suporta a implementação de políticas de proteção de aplicações apenas numa conta de utilizador por dispositivo.

* Consoante a aplicação que estiver a utilizar, o segundo utilizador poderá ou não estar bloqueado no dispositivo. No entanto, em todos os casos, apenas o primeiro utilizador que obtém as políticas de proteção de aplicações é afetado pela política.
  * O **Microsoft Word**, o **Excel** e o **PowerPoint** não impedirão o acesso a uma conta de utilizador adicional. No entanto, a conta de utilizador não será afetada pelas políticas de proteção de aplicações.

  * Nas **aplicações OneDrive e Outlook**, só pode utilizar uma conta profissional.  Não é permitido adicionar várias contas profissionais nestas aplicações.  No entanto, pode remover um utilizador de um dispositivo e, em seguida, adicionar um utilizador diferente ao dispositivo.

* Um dispositivo pode ter múltiplas contas de utilizador existentes antes de as políticas de proteção de aplicações serem implementadas. Neste caso, a primeira conta em que as políticas de proteção de aplicações forem implementadas será gerida pelas políticas de proteção de aplicações do Intune.


Leia o seguinte cenário de exemplo para saber como o Intune lida com múltiplas contas de utilizador.

O Utilizador A trabalha para duas empresas: a **Empresa X** e a **Empresa Y**. O utilizador A tem uma conta profissional para cada empresa e ambas utilizam o Intune para implementar políticas de proteção de aplicações. A **Empresa X** implementa políticas de proteção de aplicações **antes da** **Empresa Y**. A conta associada à **Empresa X** obterá a política de proteção de aplicações, mas a conta associada à Empresa Y não. Para que a conta de utilizador da Empresa Y seja gerida pelas políticas de proteção de aplicações, o Utilizador A tem de remover a conta de utilizador da Empresa X.
### <a name="adding-a-second-account"></a>Adicionar uma segunda conta

Se estiver a utilizar um dispositivo iOS, quando tentar adicionar uma segunda conta profissional no mesmo dispositivo, poderá ver uma mensagem a informá-lo de que essa ação não é permitida.  As contas serão apresentadas e pode escolher a conta que pretende remover.

![Captura de ecrã da caixa de diálogo com a mensagem a informar que a ação não é permitida e com as opções Sim e Não](./media/ios-switch-user.PNG)

## <a name="next-steps"></a>Próximos passos
[O que esperar quando a aplicação Android é gerida por políticas de proteção de aplicações](app-protection-enabled-apps-android.md)
### <a name="see-also"></a>Consulte também
[Criar e implementar políticas de proteção de aplicações com o Microsoft Intune](app-protection-policies.md)
