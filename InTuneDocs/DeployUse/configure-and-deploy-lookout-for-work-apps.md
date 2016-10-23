---
title: "Implementar a aplicação Lookout for Work | Microsoft Intune"
description: "Configure e implemente a aplicação Lookout for Work para Android."
author: karthikaraman
manager: angrobe
ms.date: 10/12/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: 524c4209-ad57-4d35-955e-a00d796bf858
ms.reviewer: sandera
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 99005e15268a60cd801ef1c717088dff2f82927b
ms.openlocfilehash: 8dce0689d5c4a0672b227eedf3ae738217eb17cf


---

# Configurar e implementar a aplicação Lookout for Work
Este artigo explica-lhe como configurar e implementar a aplicação Lookout for Work em dispositivos Android e iOS.

## Android (aplicação da Google Play Store)

* **Passo 1:**   carregue a aplicação Lookout for Work para Android na [consola do administrador do Microsoft Intune](https://manage.microsoft.com) tal como descrito no tópico [Adicionar aplicações para dispositivos móveis no Microsoft Intune](https://docs.microsoft.com/en-us/intune/deploy-use/add-apps-for-mobile-devices-in-microsoft-intune).
>[!NOTE]
> Não clique na caixa para exigir um browser gerido.

![captura de ecrã da página de aplicações da consola do administrador do Intune a mostrar as aplicações Lookout for Work na lista](../media/mtp/lookout-app-listed-intune-console.png)

* **Passo 2:** implemente a aplicação aos utilizadores. Selecione a aplicação Lookout for Work apresentada no ecrã acima e selecione **Gerir Implementação**.

  Tem de selecionar os mesmos utilizadores que foram adicionados à opção Gestão de Inscrições na consola do Lookout.  Consulte o Passo 3 na [secção Configurar a sua subscrição para a proteção contra ameaças de dispositivos do Lookout](set-up-your-subscription-with-lookout-mtp#configure-your-subscription-with-lookout-mtp) para obter informações sobre como adicionar grupos de utilizadores ao Lookout MTP.
>[!IMPORTANT]
> O assistente de implementação da aplicação Intune não se apercebe dos grupos de utilizadores do Azure AD e utiliza os grupos de utilizadores do Intune, pelo que tem de criar um grupo de utilizadores do Intune com base no grupo de utilizadores do Azure AD inscrito na consola do Lookout, conforme descrito [neste](plan-your-user-and-device-groups.md) tópico.

Selecione a opção **Instalação Necessária** para exigir que a aplicação Lookout seja instalada no dispositivo do utilizador.


## iOS (versão Enterprise da aplicação Lookout)

* **Passo 1:** certifique-se de que a **gestão de iOS** está configurada no seu dispositivo. Para obter instruções sobre como configurar o seu dispositivo para a gestão de iOS consulte [Configurar a gestão de dispositivos iOS e Mac](Set up iOS and Mac device management.md).

* **Passo 2:** **volte a assinar** a aplicação Lookout for Work para iOS. A Lookout faz a distribuição da respetiva aplicação Lookout for Work para iOS fora da iOS App Store. **Antes de distribuir a aplicação**,tem de voltar a assinar a aplicação com o seu iOS Enterprise Developer Certificate. Para obter instruções detalhadas para voltar a assinar a aplicação Lookout for Work para iOS, consulte [Lookout for Work iOS app re-signing process (Processo de reassinatura da aplicação Lookout for Work para iOS – em inglês)](https://personal.support.lookout.com/hc/en-us/articles/114094038714) no site da Lookout.


* **Passo 3:** ative a autenticação do Azure Active Directory para utilizadores iOS do seguinte modo:
  1.  Inicie sessão no portal de gestão do [Azure Active Directory](https://manage.windowsazure.com) e navegue para a página da aplicação.
  2.  Adicione a **aplicação Lookout for Work para iOS** como uma **aplicação de cliente nativo**.
  ![captura de ecrã da caixa de diálogo adicionar aplicações a mostrar a opção aplicação de cliente nativo](../media/mtp/aad-add-app.png)
  
  3. Substitua o valor **com.lookout.enterprise.onomedasuaempresa** pelo ID de pacote de cliente que selecionou quando assinou o IPA.
  4.  Adicione o URI de redirecionamento adicional: **&lt;companyportal://code/>** seguido de uma versão com codificação URL do seu URI de redirecionamento original.
  5.  Adicione **Permissões Delegadas** à sua aplicação.

  Para mais detalhes, consulte [Configure a native client application (Configurar uma aplicação de cliente nativo – em inglês)](https://azure.microsoft.com/en-us/documentation/articles/app-service-mobile-how-to-configure-active-directory-authentication/#optional-configure-a-native-client-application).


* **Passo 4:** carregue o ficheiro .ipa reassinado tal como descrito no tópico [Adicionar aplicações para dispositivos móveis no Microsoft Intune](https://docs.microsoft.com/en-us/intune/deploy-use/add-apps-for-mobile-devices-in-microsoft-intune). Defina a versão de SO mínima para iOS 8.0 ou posterior.

  ![captura de ecrã da página de aplicações na consola de administração do Intune com a aplicação Lookout for Work apresentada na lista de aplicações](../media/mtp/ios-app-uploaded-intune.png)

* **Passo 5:** crie a política de configuração de aplicações geridas tal como descrito em [Configurar aplicações iOS com políticas de configuração de aplicações móveis no Microsoft Intune](https://docs.microsoft.com/en-us/intune/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune).

  ![captura de ecrã do assistente criar nova política com a política de configuração de aplicações para iOS 8.0 ou posterior realçada](../media/mtp/ios-app-config.png)

* **Passo 6:** **para implementar a aplicação aos utilizadores**, selecione a aplicação Lookout for Work e selecione **Gerir Implementação**.

  Tem de selecionar os mesmos utilizadores que foram adicionados à opção Gestão de Inscrições na consola do Lookout.  Consulte o Passo 3 na [secção Configurar a sua subscrição para a proteção contra ameaças de dispositivos do Lookout](set-up-your-subscription-with-lookout-mtp#configure-your-subscription-with-lookout-mtp) para obter informações sobre como adicionar grupos de utilizadores ao Lookout MTP.
>[!IMPORTANT]
> O assistente de implementação da aplicação Intune não se apercebe dos grupos de utilizadores do Azure AD e utiliza os grupos de utilizadores do Intune, pelo que tem de criar um grupo de utilizadores do Intune com base no grupo de utilizadores do Azure AD inscrito na consola do Lookout, conforme descrito [neste](plan-your-user-and-device-groups.md) tópico.

Selecione a opção **Instalação Necessária** para exigir que a aplicação Lookout seja instalada no dispositivo do utilizador.

## O que acontece quando a aplicação implementada é aberta no dispositivo




Quando o utilizador abre o Lookout for Work no dispositivo, é-lhe pedido para ativar a aplicação e selecionar a opção Iniciar sessão com o Azure Active Directory. Pode encontrar instruções detalhadas sobre o fluxo do utilizador final nos tópicos seguintes:

* [É-lhe pedido que instale o Lookout for Work no seu dispositivo Android](http://docs.microsoft.com/intune/enduser/you-are-prompted-to-install-lookout-for-work-android)

* [Tem de resolver uma ameaça que o Lookout for Work encontrou no seu dispositivo Android](http://docs.microsoft.com/intune/enduser/you-need-to-resolve-a-threat-found-by-lookout-for-work-android)

## Passos seguintes
* [Ativar a regra de proteção contra ameaças de dispositivo na política de conformidade](enable-device-threat-protection-rule-in-compliance-policy.md)



<!--HONumber=Oct16_HO2-->


