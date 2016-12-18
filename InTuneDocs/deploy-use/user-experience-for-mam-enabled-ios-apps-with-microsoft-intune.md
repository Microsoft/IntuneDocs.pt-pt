---
title: "Aplicações iOS com políticas de MAM | Microsoft Intune"
description: "Este tópico descreve o que esperar quando a sua aplicação iOS é gerida por políticas de gestão de aplicações móveis."
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 10/18/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b57e6525-b57c-4cb4-a84c-9f70ba1e8e19
ms.reviewer: andcerat
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 87e37cd8334ddb9331c0662b691545cd0ab0553a
ms.openlocfilehash: 3aa6728036ff66ea489176063af2d136bef4c7cc


---

# <a name="what-to-expect-when-your-ios-app-is-managed-by-mam-policies"></a>O que esperar quando a sua aplicação iOS é gerida por políticas de MAM
 Este tópico descreve a experiência do utilizador para aplicações com políticas de MAM (gestão de acesso móvel). As políticas de MAM são aplicadas apenas quando as aplicações são utilizadas no contexto de trabalho: por exemplo, quando o utilizador está a aceder a aplicações com a sua conta profissional ou aceder a ficheiros armazenados na localização empresarial do OneDrive para Empresas.

##  <a name="access-apps"></a>Acesso às aplicações

Se o dispositivo **não estiver inscrito no Intune**, será pedido ao utilizador para reiniciar a aplicação quando utilizá-la pela primeira vez.  É preciso um reinício para que as políticas de MAM possam ser aplicadas à aplicação. A seguinte captura de ecrã da aplicação Skype ilustra este pedido de reinício:


![captura de ecrã do dispositivo iOS que mostra o pedido de PIN](../media/appmanagement/iOS_AppPINPrompt.png)

Para dispositivos que estejam **inscritos para gestão no Intune**, o utilizador vê uma mensagem a indicar que a sua aplicação é agora gerida:

![captura de ecrã do dispositivo iOS que mostra a mensagem que a aplicação é agora gerida pela sua empresa, com o pedido de PIN](../media/appmanagement/ios-managed-devices-pin-prompt.png)

##  <a name="use-apps-with-multi-identity-support"></a>Utilizar aplicações com suporte de identidades múltiplas

As políticas de MAM só são aplicadas no contexto profissional. Por conseguinte, a aplicação pode comportar-se de forma diferente consoante se o contexto é profissional ou pessoal.

 Por exemplo, o utilizador obtém um pedido de PIN ao aceder a dados de trabalho. Para a **aplicação Outlook**, é pedido ao utilizador um PIN ao iniciar a aplicação. Para a **aplicação OneDrive**, é pedido ao utilizador um pin quando escreve na conta profissional.  Para o Microsoft **Word**, **PowerPoint** e **Excel**, é pedido um pin ao utilizador quando acede a documentos armazenados na localização empresarial do OneDrive para Empresas.

##  <a name="manage-user-accounts-on-the-device"></a>Gerir contas de utilizador no dispositivo

O Intune só suporta a implementação de políticas de MAM apenas numa conta de utilizador por dispositivo.

* Consoante a aplicação que estiver a utilizar, o segundo utilizador poderá estar bloqueado no dispositivo. No entanto, em todos os casos, apenas o primeiro utilizador que obtém as políticas de MAM é afetado pela política.
  * O **Microsoft Word**, **Excel** e **PowerPoint** não bloqueiam uma segunda conta de utilizador, mas a segunda conta de utilizador não é afetada pelas políticas de MAM.  

  * Nas **aplicações OneDrive** e **Outlook**, só pode utilizar uma conta profissional. Não pode adicionar várias contas profissionais para estas aplicações. Pode, contudo, remover um utilizador e adicionar um utilizador diferente no dispositivo.

* Se um dispositivo tiver várias contas de utilizador existentes antes de as políticas de MAM serem implementadas, a conta em que as políticas de MAM são implementadas em primeiro lugar é gerida pelas políticas de MAM do Intune.


Leia o seguinte cenário de exemplo para obter uma compreensão mais aprofundada de como são tratadas as várias contas de utilizador.

O utilizador A trabalha para duas empresas — a **Empresa X** e a **Empresa Y**. O utilizador A tem uma conta profissional para cada empresa e ambas utilizam o Intune para implementar políticas de MAM. A **Empresa X** implementa políticas de MAM **antes da** **Empresa Y**. A conta que está associada à **Empresa X** obtém a política de MAM, mas a conta que está associada à Empresa Y não. Se pretender que a conta de utilizador que está associada à Empresa Y seja gerida pelas políticas de MAM, tem de remover a conta de utilizador que está associada à Empresa X.

### <a name="add-a-second-account"></a>Adicionar uma segunda conta

Se estiver a utilizar um dispositivo iOS, quando tentar adicionar uma segunda conta profissional nesse dispositivo, poderá ver uma mensagem a informá-lo de que essa ação não é permitida. As contas serão apresentadas e, em seguida, pode escolher a conta que pretende remover.

![Captura de ecrã da caixa de diálogo com a mensagem a informar que a ação não é permitida e com as opções Sim e Não](../media/AppManagement/iOS_SwitchUser.PNG)
## <a name="next-steps"></a>Próximos passos
[O que esperar quando a sua aplicação Android é gerida por políticas de MAM](user-experience-for-mam-enabled-android-apps-with-microsoft-intune.md)
### <a name="see-also"></a>Consulte também
[Criar e implementar políticas de gestão de aplicações móveis com o Microsoft Intune](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md)



<!--HONumber=Dec16_HO2-->


