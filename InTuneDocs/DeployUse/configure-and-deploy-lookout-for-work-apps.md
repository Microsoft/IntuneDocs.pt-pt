---
title: "Implementar a aplicação Lookout for Work | Microsoft Intune"
description: "Configure e implemente a aplicação Lookout for Work para Android."
author: karthikaraman
manager: angrobe
ms.date: 09/13/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: 524c4209-ad57-4d35-955e-a00d796bf858
ms.reviewer: sandera
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: c4d05b9ba7249e4068d21480b1c9db342277757e
ms.openlocfilehash: 687a102ccb34cb7acfaab1e8a1d4b67cb54b9e92


---

# Configurar e implementar a aplicação Lookout for Work
Este artigo explica como configurar e implementar a aplicação Lookout for Work para dispositivos que estão inscritos e que estão a executar o Android 4.1 ou posterior.

* **Passo 1:** Na [Consola de administrador do Microsoft Intune](https://manage.microsoft.com), aceda a **Aplicações** e selecione **Adicionar Aplicações**.   
* **Passo 2:** na página **Configuração do Software** do editor, selecione **Ligação externa** e especifique o URL seguinte: https://play.google.com/store/apps/details?id=com.lookout.enterprise
>[!NOTE]
>Não clique na caixa para exigir um browser gerido.

* **Passo 3:** na página **Descrição do software**, preencha as seguintes informações:
  * **Editor:** Lookout Mobile Security
  * **Nome:** Lookout for Work
  * **Descrição:** o Lookout oferece a melhor proteção contra ameaças para dispositivos móveis para manter o seu dispositivo seguro. Quando a aplicação Lookout está instalada no dispositivo, a aplicação protege o seu dispositivo de ameaças e irá alertá-lo a si e ao administrador da sua empresa, se forem detetadas algumas.
  * **Categoria:** Gestão de Computadores
* **Passo 4:** após a conclusão com êxito, verá uma mensagem **Carregamento de dados para o Microsoft Intune concluído com êxito**.

Quando clicar em **Aplicações** na consola de administrador do Intune, irá ver a aplicação Lookout for Work na lista ![captura de ecrã da página de aplicações da consola de administrador do Intune a mostrar a aplicação Lookout for Work na lista](../media/mtp/lookout-app-listed-intune-console.png)

**Para implementar a aplicação para os utilizadores**, selecione a aplicação Lookout for Work apresentada no ecrã acima e selecione **Gerir Implementação**.

Tem de selecionar os mesmos utilizadores que foram adicionados à opção Gestão de Inscrições na consola do Lookout MTP.  Consulte o Passo 3 na [secção Configurar a sua subscrição com o Lookout MTP](set-up-your-subscription-with-lookout-mtp#configure-your-subscription-with-lookout-mtp) para obter informações sobre adicionar grupos de utilizadores ao Lookout MTP.
>[!IMPORTANT]
> O assistente de implementação da aplicação Intune não se apercebe dos grupos de utilizadores do Azure AD e utiliza os grupos de utilizadores do Intune, pelo que deve criar um grupo de utilizadores do Intune com base no grupo de utilizadores do Azure AD que é inscrito na consola do Lookout MTP, conforme descrito [neste](plan-your-user-and-device-groups.md) tópico.

Selecione a opção **Instalação Necessária** para exigir que a aplicação Lookout seja instalada no dispositivo do utilizador.


Com a opção **Instalação Necessária** selecionada para a implementação, o Intune irá enviar a aplicação Lookout for Work para o dispositivo.   

Quando o utilizador abre o Lookout for Work no dispositivo, é-lhe pedido para ativar a aplicação e selecionar a opção Iniciar sessão com o Azure Active Directory. Pode encontrar instruções detalhadas sobre o fluxo do utilizador final nos tópicos seguintes:

* [É-lhe pedido que instale o Lookout for Work no seu dispositivo Android](http://docs.microsoft.com/intune/enduser/you-are-prompted-to-install-lookout-for-work-android)

* [Tem de resolver uma ameaça que o Lookout for Work encontrou no seu dispositivo Android](http://docs.microsoft.com/intune/enduser/you-need-to-resolve-a-threat-found-by-lookout-for-work-android)

## Passos seguintes
* [Ativar a regra de proteção contra ameaças de dispositivo na política de conformidade](enable-device-threat-protection-rule-in-compliance-policy.md)



<!--HONumber=Sep16_HO3-->


