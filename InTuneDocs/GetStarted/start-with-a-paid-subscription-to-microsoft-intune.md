---
title: "Guia de introdução do Intune | Microsoft Intune"
description: "Requisitos e pré-requisitos para começar a utilizar a sua subscrição do Intune"
keywords: 
author: Staciebarker
manager: angrobe
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d158503c-1276-422b-ab81-5f66c1cd7e7a
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 2a192c71b1b82f59b34ea614d09d895174f8112b
ms.openlocfilehash: d10bb6ce48ba000154d117b2481690a198d25e49


---


# Guia de introdução do Intune
Este guia de introdução orienta-o ao longo dos passos de configuração de uma subscrição paga do Microsoft Intune, para que possa gerir os dispositivos móveis e os PCs Windows em utilização na sua organização de forma rápida e fácil. Pode seguir os passos por ordem ou avançar se um passo não for aplicável ao seu ambiente específico ou às necessidades da sua empresa.

>[!NOTE]
>Este artigo foca-se na configuração do Intune como um serviço autónomo. Em alternativa, se utilizar atualmente o Microsoft System Center Configuration Manager para gerir computadores e servidores, pode [expanda o Configuration Manager para gerir dispositivos móveis](https://technet.microsoft.com/library/jj884158.aspx). Pode fazê-lo ao ligar o Intune ao Configuration Manager numa implementação híbrida de gestão dispositivos móveis (MDM).

Os passos deste guia de introdução partilham muitos dos mesmos passos que se encontram no [Guia de avaliação do Intune](/intune/understand-explore/get-started-with-a-30-day-trial-of-microsoft-intune). No entanto, quando terminar a avaliação e estiver pronto para começar a gerir os seus dispositivos móveis, tem de abordar vários requisitos adicionais:

-   Sincronizar contas do Active Directory no local com o Intune e o Azure Active Directory.

-   Atualizar os registos públicos e do serviço DNS junto da sua entidade de registo de domínios.

-   Personalizar funcionalidades do Intune para utilização em produção.

>[!TIP]
>Se comprar um mínimo de 150 licenças para o Microsoft Intune num plano elegível, pode utilizar o *Benefício do FastTrack Center*, um serviço em que os especialistas da Microsoft trabalham em conjunto consigo para preparar o seu ambiente para o Intune. Veja [Descrição do Benefício do Serviço do Microsoft Intune](https://technet.microsoft.com/library/mt228265.aspx).


## Antes de começar
Utilize este guia se estiver a começar com uma subscrição paga e estiver pronto para implementar o Intune e efetuar alterações à sua infraestrutura de rede existente. Estas tarefas podem ir desde simplesmente adicionar ou atualizar os registos DNS internos e externos até sincronizar as contas de utilizador do Active Directory existentes com o Azure Active Directory. Seja qual for a combinação de funcionalidades de gestão de dispositivos móveis do Intune que opte por utilizar, terá de planear cuidadosamente de que forma o Intune irá interagir com os seus componentes e serviços de rede atuais. Mais concretamente, deve rever:

-   **Como é que vai gerir a identidade do utilizador**: na maioria das empresas de média a grande dimensão, a forma mais fácil e prática de gerir a identidade do utilizador com o Intune é ligar os serviços de diretório existentes ao Intune através do Azure Active Directory. Isto é especialmente verdade se já utilizar outros serviços cloud Microsoft, como o Office 365 ou o Exchange Online. Sincronizar as contas de utilizador existentes com o [Microsoft Azure Active Directory Connect](https://www.microsoft.com/download/details.aspx?id=47594) é uma forma rápida e fácil de ligar o Active Directory no local ao Azure Active Directory e configurar uma experiência de autenticação de início de sessão único para os seus utilizadores.

-   **Como é que o DNS vai ser afetado**: se pretender utilizar o seu próprio nome de domínio em vez do domínio onmicrosoft.com predefinido que obtém quando se inscreve pela primeira vez no Intune, irão ser necessárias algumas atualizações do registo DNS público. As atualizações do registo DNS são necessárias para que os dispositivos móveis possam localizar o serviço do Intune e garantir que o serviço de gestão para a sua subscrição funciona corretamente para gerir todos os dispositivos em utilização pela sua organização.

## Tenha os seguintes itens à mão
Está pronto para começar? Quando começar a utilizar a subscrição paga do Intune, vai precisar dos seguintes itens:

### Um dispositivo com um browser preparado para o Silverlight
Precisa disto para aceder à consola de administração do Intune, na qual irá gerir os dispositivos, as aplicações e as políticas. Também precisa de um browser para aceder ao Portal da Empresa do Intune baseado na Web quando não aceder à aplicação do Portal da Empresa a partir de um dispositivo móvel. Para facilitar as coisas, pode utilizar a definição "modo de privacidade" no browser que utiliza para a administração do Intune (por exemplo: no Internet Explorer, pode clicar em **Ferramentas** &gt; **Navegação InPrivate **).

>[!TIP]
>Devido a este requisito, o browser Microsoft Edge não é suportado para aceder à consola de administração do Intune.


### Certificados para dispositivos móveis
Se estiver a gerir dispositivos iOS ou Windows Phone com o Intune, vai precisar de certificados e contas para obter esses certificados. Não irá precisar de certificados adicionais para gerir dispositivos Android.

- Os utilizadores do **Windows Phone 8.1** que instalem a aplicação do Portal da Empresa a partir da Loja não precisam de certificados. No entanto, é necessário um [certificado de assinatura de código Symantec](https://products.websecurity.symantec.com/orders/enrollment/microsoftCert.do) para o **Windows Phone 8.0** ou para utilizar o Intune para implementar a aplicação do Portal da Empresa em dispositivos Windows Phone 8.1.

>[!NOTE]
>Este guia de introdução pressupõe que os utilizadores obtêm a aplicação do Portal da Empresa a partir da Loja em dispositivos Windows Phone 8.1 ou posteriores. Para obter informações sobre o suporte do Windows Phone 8.0, consulte [Configurar a gestão do Windows Phone 8.0 com o Microsoft Intune](/Intune/deploy-use/set-up-windows-phone-8.0-management-with-microsoft-intune).

- Não existem requisitos de certificados para **PCs Windows** ou **dispositivos Windows RT** ao inscrever PCs Windows como dispositivos ou ao [instalar o cliente de PC Windows para o Microsoft Intune](/intune/deploy-use/install-the-windows-pc-client-with-microsoft-intune).

- Em dispositivos **iOS** ou **Mac OS X**, terá de pedir um certificado de serviço Apple Push Notification, conforme descrito no passo 3 do artigo [Configurar a gestão de dispositivos iOS e Mac com o Microsoft Intune](/intune/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune).

## Passos seguintes
Está na altura de começar a utilizar o guia de introdução do Intune!

>[!div class="step-by-step"]
[**Iniciar sessão no Intune** &rarr;](start-with-a-paid-subscription-to-microsoft-intune-step-1.md)



<!--HONumber=Jul16_HO4-->


