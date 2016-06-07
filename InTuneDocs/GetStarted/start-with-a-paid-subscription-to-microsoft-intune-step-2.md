---
# required metadata

title: Configurar um nome de domínio personalizado | Microsoft Intune
description:
keywords:
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 2382f36f-13d8-4a32-81ad-6cfa604889c3

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# Configurar um nome de domínio personalizado

Por predefinição, o Intune utiliza o nome de domínio **<domain>.onmicrosoft.com** que foi criado quando subscreveu inicialmente o serviço. Se a sua organização for proprietária de um domínio personalizado, pode configurar a sua instância do Intune para utilizar esse domínio em vez do nome de domínio fornecido com a sua subscrição.

Antes de criar novas contas de utilizador ou sincronizar contas do Active Directory no local, recomendamos vivamente que decida se irá utilizar apenas o domínio .onmicrosoft.com ou se irá adicionar um ou mais nomes de domínio personalizados. Configurar um domínio personalizado antes de adicionar utilizadores pode ajudar a simplificar a gestão das identidades de utilizador da sua subscrição ao permitir que os utilizadores iniciem sessão com as credenciais que utilizam para aceder a outros recursos de domínio.

Ao subscrever um serviço baseado na nuvem da Microsoft, a instância desse serviço torna-se num [inquilino do Microsoft Azure AD](http://technet.microsoft.com/library/jj573650.aspx#BKMK_WhatIsAnAzureADTenant), que proporciona serviços de identidade e de diretório para o seu serviço baseado na nuvem. E visto que as tarefas de configuração do Intune para utilizar o nome de domínio personalizado da sua organização são as mesmas que nos outros inquilinos do Azure AD, pode utilizar as informações e procedimentos descritos em [Add your domain (Adicionar o seu domínio)](https://azure.microsoft.com/documentation/articles/active-directory-add-domain/)

> Para obter mais informações sobre a utilização do seu domínio personalizado com um serviço baseado na nuvem da Microsoft, veja [Conceptual overview of custom domain names in Azure Active Directory (Descrição geral concetual de nomes de domínio personalizados no Azure Active Directory)](https://azure.microsoft.com/documentation/articles/active-directory-add-domain-concepts/)

### Passos seguintes
Parabéns! Acabou de concluir o passo 2 do *Intune quick start guide (Guia de introdução do Intune)*

>[!div class="step-by-step"]

>[&larr; **Iniciar sessão no Intune**](.\start-with-a-paid-subscription-to-microsoft-intune-step-1.md)     [**Adicionar utilizadores ao Intune** &rarr;](.\start-with-a-paid-subscription-to-microsoft-intune-step-3.md)  


<!--HONumber=May16_HO2-->

