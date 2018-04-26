---
title: "Configurar um nome de domínio personalizado | Documentos da Microsoft"
description: "Adicionar um nome de domínio personalizado à sua subscrição do Intune"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 02/14/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2382f36f-13d8-4a32-81ad-6cfa604889c3
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: ab6d9b6b296fb4e1fb0aaa9496fede28976728dc
ms.openlocfilehash: 86062a73092f6e438de7a315d9ec1c2f395c9c50
ms.lasthandoff: 04/14/2017


---


# <a name="configure-a-custom-domain-name"></a>Configurar um nome de domínio personalizado

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Este tópico informa os administradores sobre como podem criar um CNAME DNS para simplificar e personalizar a experiência de início de sessão.

Quando a sua organização se inscreve num serviço Microsoft baseado na cloud, como o Intune, é-lhe disponibilizado um nome de domínio inicial, alojado no Azure Active Directory (AD) semelhante a: **yourdomain.onmicrosoft.com**. Neste exemplo, **oseudomínio** é o nome de domínio que escolheu quando se inscreveu e **onmicrosoft.com** é o sufixo atribuído às contas que adicionar à sua subscrição. Se a sua organização for proprietária de um domínio personalizado, pode configurar a sua instância do Intune para utilizar esse domínio em vez do nome de domínio fornecido com a sua subscrição.

Antes de criar contas de utilizador ou sincronizar o seu Active Directory no local, recomendamos vivamente que decida se irá utilizar apenas o domínio .onmicrosoft.com ou se irá adicionar um ou mais nomes de domínio personalizados. Configurar um domínio personalizado antes de adicionar utilizadores pode ajudar a simplificar a gestão das identidades de utilizador da sua subscrição ao permitir que os utilizadores iniciem sessão com as credenciais que utilizam para aceder a outros recursos de domínio.

Ao subscrever um serviço baseado na cloud da Microsoft, a instância desse serviço torna-se num [inquilino do Microsoft Azure AD](http://technet.microsoft.com/library/jj573650.aspx#BKMK_WhatIsAnAzureADTenant), que proporciona serviços de identidade e de diretório para o seu serviço baseado na cloud. E visto que as tarefas de configuração do Intune para utilizar o nome de domínio personalizado da sua organização são as mesmas que nos outros inquilinos do Azure AD, pode utilizar as informações e procedimentos descritos em [Adicionar o seu domínio](https://azure.microsoft.com/documentation/articles/active-directory-add-domain/).

> [!TIP]
> Para obter mais informações sobre a utilização do seu domínio personalizado com um serviço baseado na cloud da Microsoft, veja [Descrição geral concetual de nomes de domínio personalizados no Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-add-domain-concepts/).

Não é possível mudar o nome ou remover esse nome de domínio inicial. No entanto, pode adicionar, verificar ou remover os seus próprios nomes de domínio personalizado para utilizar com o Intune, que é útil se pretender manter a sua identidade empresarial.

## <a name="to-add-and-verify-your-custom-domain"></a>Adicionar e verificar o seu domínio personalizado

1. Aceda a [portal de gestão do Office 365](https://portal.office.com/Admin/Default.aspx) e inicie sessão na sua conta de administrador.

2. No painel de navegação, selecione **Definições** &gt; **Domínios**.

3. Selecione **Adicionar domínio** e escreva o seu nome de domínio personalizado.

4. A caixa de diálogo **Verificar domínio** é aberta, indicando os valores para criar o registo TXT no seu fornecedor de alojamento DNS.
    - **Utilizadores da GoDaddy**: são redirecionados pelo portal de Gestão do Office 365 para a página de início de sessão da GoDaddy. Depois de introduzir as suas credenciais e de aceitar o contrato de permissão de alteração de domínio, o registo TXT é criado automaticamente. Em alternativa, pode [criar o registo TXT](https://support.office.com/article/Create-DNS-records-at-GoDaddy-for-Office-365-f40a9185-b6d5-4a80-bb31-aa3bb0cab48a).
    - **Utilizadores da register.com**: devem seguir as [instruções passo a passo](https://support.office.com/article/Create-DNS-records-at-Register-com-for-Office-365-55bd8c38-3316-48ae-a368-4959b2c1684e#BKMK_verify) para criar o registo TXT.

    > [!TIP]
    > Certifique-se que cria um alias de DNS (CNAME) para a [inscrição de dispositivos Windows](/Intune/deploy-use/set-up-windows-phone-management-with-microsoft-intune), enquanto faz as alterações no seu fornecedor de alojamento DNS.

Os passos para adicionar e verificar um domínio personalizado podem também ser [executados no Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-add-domain/).

Pode saber mais [acerca do seu domínio onmicrosoft.com inicial no Office 365](https://support.office.com/article/About-your-initial-onmicrosoft-com-domain-in-Office-365-B9FC3018-8844-43F3-8DB1-1B3A8E9CFD5A)

>[!div class="step-by-step"]

>[&larr; **Iniciar sessão no Intune**](.\start-with-a-paid-subscription-to-microsoft-intune-step-1.md)     [**Adicionar utilizadores ao Intune** &rarr;](.\start-with-a-paid-subscription-to-microsoft-intune-step-3.md)  

