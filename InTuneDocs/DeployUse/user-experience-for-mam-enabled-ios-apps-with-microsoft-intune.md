---
title: "Aplicações iOS com políticas de MAM | Microsoft Intune"
description: "Este tópico descreve o que esperar quando a sua aplicação iOS é gerida por políticas de gestão de aplicações móveis."
keywords: 
author: karthikaraman
ms.author: karaman
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
ms.sourcegitcommit: 389daf0ed39fa2cd4b2e5d6e52cbd6809a568c9e
ms.openlocfilehash: 3f9d9c7cafcdac0db21e5ba35f713fe630c65b99


---

# O que esperar quando a sua aplicação iOS é gerida por políticas de MAM
 Este tópico descreve a experiência do utilizador para aplicações com políticas de MAM. As políticas de gestão de aplicações móveis (MAM) são aplicadas apenas quando as aplicações são utilizadas no contexto de trabalho, como aceder a aplicações com a sua conta profissional ou aceder a ficheiros armazenados na localização empresarial do OneDrive para Empresas.
##  Aceder a aplicações

Se o dispositivo **não estiver inscrito no Intune**, será pedido ao utilizador final para reiniciar a aplicação quando utilizar a aplicação pela primeira vez.  É necessário um reinício para que as políticas de MAM possam ser aplicadas à aplicação. A seguinte captura de ecrã ilustra isto, utilizando a aplicação Skype:


![captura de ecrã do dispositivo iOS que mostra o pedido de PIN](../media/appmanagement/iOS_AppPINPrompt.png)

Para dispositivos que estejam **inscritos para gestão no Intune**, o utilizador final verá uma mensagem a indicar que a sua aplicação é agora gerida:

![captura de ecrã do dispositivo iOS que mostra a mensagem a indicar a gestão pela sua empresa com o pedido de PIN](../media/appmanagement/ios-managed-devices-pin-prompt.png)

##  Utilizar aplicações com suporte de várias identidades

As políticas de MAM são apenas aplicadas no contexto de trabalho ao utilizar a aplicação, pelo que poderá experimentar diferentes comportamentos da aplicação consoante o contexto: profissional ou pessoal.  

Para aplicações que suportam várias identidades, o Intune apenas aplica as políticas de MAM se o utilizador final utilizar a aplicação no contexto de trabalho.  Por exemplo, o utilizador final irá obter um pedido de PIN ao aceder a dados de trabalho.  Para a **aplicação Outlook**, é pedido ao utilizador final um PIN ao iniciar a aplicação. Para a **aplicação OneDrive**, isto acontece quando o utilizador final introduz a conta profissional.  Para o Microsoft **Word**, **PowerPoint* e **Excel**, isto acontece quando o utilizador final acede a documentos armazenados na localização empresarial do OneDrive para Empresas.
##  Gerir contas de utilizador no dispositivo

O Intune só suporta a implementação de políticas de MAM apenas numa conta de utilizador por dispositivo.

* Consoante a aplicação que estiver a utilizar, o segundo utilizador poderá ou não estar bloqueado no dispositivo. No entanto, em todos os casos, apenas o primeiro utilizador que obtém as políticas de MAM é afetado pela política.
  * O **Microsoft Word**, **Excel** e **PowerPoint** não bloqueiam uma segunda conta de utilizador, mas a segunda conta de utilizador não é afetada pelas políticas de MAM.  

  * Nas **aplicações OneDrive e Outlook**, só pode utilizar uma conta profissional.  Não é permitido adicionar várias contas profissionais nestas aplicações.  Pode, contudo, remover um utilizador e adicionar um utilizador diferente no dispositivo.

* Se um dispositivo tiver várias contas de utilizador existentes antes de as políticas de MAM serem implementadas, a conta em que as políticas de MAM são implementadas em primeiro lugar é gerida pelas políticas de MAM do Intune.


Leia o cenário de exemplo abaixo para obter uma compreensão mais aprofundada de como são tratadas as várias contas de utilizador.

O utilizador A trabalha para duas empresas - a **Empresa X** e a **Empresa Y**. O utilizador A tem uma conta profissional para cada empresa e ambas utilizam o Intune para implementar políticas de MAM. A **Empresa X** implementa políticas de MAM **antes da** **Empresa Y**. A conta associada à **Empresa X** obterá a política de MAM, mas a conta associada à Empresa Y não. Se pretender que a conta de utilizador associada à Empresa Y seja gerida pelas políticas de MAM, tem de remover a conta de utilizador associada à Empresa X.
### Adicionar uma segunda conta

Se estiver a utilizar um dispositivo iOS, quando tentar adicionar uma segunda conta profissional no mesmo dispositivo, poderá ver uma mensagem a informá-lo de que essa ação não é permitida.  As contas serão apresentadas e pode escolher a conta que pretende remover.

![Captura de ecrã da caixa de diálogo com a mensagem a informar que a ação não é permitida e com as opções Sim e Não](../media/AppManagement/iOS_SwitchUser.PNG)
## Passos seguintes
[O que esperar quando a sua aplicação Android é gerida por políticas de MAM](user-experience-for-mam-enabled-android-apps-with-microsoft-intune.md)
### Consulte também
[Criar e implementar políticas de gestão de aplicações móveis com o Microsoft Intune](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md)



<!--HONumber=Oct16_HO3-->


