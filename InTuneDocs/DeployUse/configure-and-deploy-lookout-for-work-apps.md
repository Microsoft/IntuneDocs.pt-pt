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
ms.sourcegitcommit: 9c2ffb5fe497d56d8250fe3dec7db606c2067a1c
ms.openlocfilehash: c43104ff199e1800bfded35154d2be0cfd0c40f3


---

# Configurar e implementar a aplicação Lookout for Work
Nesta versão, é suportada a aplicação Lookout for Work em dispositivos Android a executar a versão 4.1 e posterior.
## Android
Esta secção descreve como configurar e implementar a aplicação Lookout for Work para dispositivos Android inscritos no Intune.  
* Passo 1: na [consola do administrador do Microsoft Intune](https://manage.microsoft.com), aceda a **Aplicações** e selecione **Adicionar Aplicações**.   
* Passo 2: na página **Configuração do Software** do editor, selecione **Ligação externa** e especifique o URL seguinte: https://play.google.com/store/apps/details?id=com.lookout.enterprise
>[!NOTE]
>Não clique na caixa para exigir um browser gerido.

* Passo 3: na página **Descrição do software**, preencha as seguintes informações:
  * **Editor:** Lookout Mobile Security
  * **Nome:** Lookout for Work
  * **Descrição:** o Lookout oferece a melhor proteção contra ameaças para dispositivos móveis para manter o seu dispositivo seguro. Quando a aplicação Lookout está instalada no dispositivo, a aplicação protege o seu dispositivo de ameaças e irá alertá-lo a si e ao administrador da sua empresa, se forem detetadas algumas.
  * **Categoria:** Gestão de Computadores
* Passo 4: após a conclusão com êxito, verá uma mensagem **Carregamento de dados para o Microsoft Intune concluído com êxito**.

Na Consola do Intune, quando clica em **Aplicações** irá ver a aplicação Lookout for Work na lista ![captura de ecrã da página de aplicações da consola de administração do Intune a mostrar a aplicação Lookout for Work na lista](../media/mtp/lookout-app-listed-intune-console.png)

Passo 5: nesta fase, o Intune sabe como implementar a aplicação Lookout for Work para Android.   Pode implementar a aplicação para os utilizadores, ao selecionar a aplicação Lookout for Work apresentada no ecrã acima e ao selecionar **Gerir Implementação**.

Tem de selecionar os mesmos utilizadores adicionados na opção Gestão de Inscrições na consola do Lookout MTP.  Consulte o Passo 3 na [secção Configurar a sua subscrição com o Lookout MTP](set-up-your-subscription-with-lookout-mtp#configure-your-subscription-with-lookout-mtp) para obter informações sobre adicionar grupos de utilizadores ao Lookout MTP.
>[!IMPORTANT]
> O assistente de implementação de aplicações do Intune não tem conhecimento dos grupos de utilizadores do Azure AD e em alternativa utiliza os grupos de utilizadores do Intune. Por isso, tem de criar um grupo de utilizadores do Intune com base no grupo de utilizadores do Azure AD que está inscrito na consola do Lookout MTP, conforme descrito [neste](plan-your-user-and-device-groups.md) tópico.

Passo 6: selecione a opção **Instalação Necessária** para exigir que a aplicação Lookout seja instalada no dispositivo do utilizador.

### Ativação do dispositivo
Com a opção **Instalação Necessária** selecionada para a implementação, o Intune irá enviar a aplicação Lookout for Work para o dispositivo.   

Quando o utilizador abre o Lookout for Work no dispositivo, é-lhe pedido para ativar a aplicação e selecionar a opção Iniciar sessão com o Azure Active Directory. Pode encontrar instruções detalhadas sobre o fluxo do utilizador final nos tópicos seguintes:

* [É-lhe pedido que instale o Lookout for Work no seu dispositivo Android](http://docs.microsoft.com/intune/enduser/you-are-prompted-to-install-lookout-for-work-android)

* [Tem de resolver uma ameaça que o Lookout for Work encontrou no seu dispositivo Android](http://docs.microsoft.com/intune/enduser/you-need-to-resolve-a-threat-found-by-lookout-for-work-android)

## Passos seguintes
* [Ativar a regra de proteção contra ameaças de dispositivo na política de conformidade](enable-device-threat-protection-rule-in-compliance-policy.md)



<!--HONumber=Sep16_HO2-->


