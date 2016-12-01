---
title: "Configurar um nome de domínio personalizado | Microsoft Intune"
description: "Adicionar um nome de domínio personalizado à sua subscrição do Intune"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 11/22/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2382f36f-13d8-4a32-81ad-6cfa604889c3
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 29b6e5a3d319c741482fcc2b600842e2e42b96e2
ms.openlocfilehash: 9fe78bca15ffee1e5e0e7e3758ff70b6bc92b619


---


# <a name="configure-a-custom-domain-name"></a>Configurar um nome de domínio personalizado

Quando a sua organização se inscreve num serviço Microsoft baseado na cloud, como o Intune, é-lhe disponibilizado um nome de domínio inicial, alojado no Azure Active Directory (AD) semelhante a: **yourdomain.onmicrosoft.com**. Neste exemplo, **oseudomínio** é o nome de domínio que escolheu quando se inscreveu e **onmicrosoft.com** é o sufixo atribuído às contas que adicionar à sua subscrição. Se a sua organização for proprietária de um domínio personalizado, pode configurar a sua instância do Intune para utilizar esse domínio em vez do nome de domínio fornecido com a sua subscrição.

Antes de criar contas de utilizador ou sincronizar o seu Active Directory no local, recomendamos vivamente que decida se irá utilizar apenas o domínio .onmicrosoft.com ou se irá adicionar um ou mais nomes de domínio personalizados. Configurar um domínio personalizado antes de adicionar utilizadores pode ajudar a simplificar a gestão das identidades de utilizador da sua subscrição ao permitir que os utilizadores iniciem sessão com as credenciais que utilizam para aceder a outros recursos de domínio.

Ao subscrever um serviço baseado na nuvem da Microsoft, a instância desse serviço torna-se num [inquilino do Microsoft Azure AD](http://technet.microsoft.com/library/jj573650.aspx#BKMK_WhatIsAnAzureADTenant), que proporciona serviços de identidade e de diretório para o seu serviço baseado na nuvem. E visto que as tarefas de configuração do Intune para utilizar o nome de domínio personalizado da sua organização são as mesmas que nos outros inquilinos do Azure AD, pode utilizar as informações e procedimentos descritos em [Adicionar o seu domínio](https://azure.microsoft.com/documentation/articles/active-directory-add-domain/).

> [!TIP]
> Para obter mais informações sobre a utilização do seu domínio personalizado com um serviço baseado na nuvem da Microsoft, veja [Descrição geral concetual de nomes de domínio personalizados no Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-add-domain-concepts/).

Não é possível mudar o nome ou remover esse nome de domínio inicial. No entanto, pode adicionar, verificar ou remover os seus próprios nomes de domínio personalizado para utilizar com o Intune, que é útil se pretender manter a sua identidade empresarial.

## <a name="to-add-and-verify-your-custom-domain"></a>Adicionar e verificar o seu domínio personalizado

1. Aceda a [portal de gestão do Office 365](https://portal.office.com/Admin/Default.aspx) e inicie sessão na sua conta de administrador.

2. No painel de navegação, selecione **Definições** &gt; **Domínios**.

3. Selecione **Adicionar domínio** e escreva o seu nome de domínio personalizado.

4. A caixa de diálogo **Verificar domínio** é aberta, indicando os valores para criar o registo TXT no seu fornecedor de alojamento DNS.
    - **Utilizadores da GoDaddy**: são redirecionados pelo portal de Gestão do Office 365 para a página de início de sessão da GoDaddy. Depois de introduzir as suas credenciais e de aceitar o contrato de permissão de alteração de domínio, o registo TXT é criado automaticamente. Em alternativa, pode [criar o registo TXT](https://support.office.com/en-us/article/Create-DNS-records-at-GoDaddy-for-Office-365-f40a9185-b6d5-4a80-bb31-aa3bb0cab48a?ui=en-US&rs=en-US&ad=US).
    - **Utilizadores da register.com**: devem seguir as [instruções passo a passo](https://support.office.com/en-us/article/Create-DNS-records-at-Register-com-for-Office-365-55bd8c38-3316-48ae-a368-4959b2c1684e?ui=en-US&rs=en-US&ad=US#BKMK_verify) para criar o registo TXT.

    > [!TIP]
    > Certifique-se que cria um alias de DNS (CNAME) para a [inscrição de dispositivos Windows](/Intune/deploy-use/set-up-windows-phone-management-with-microsoft-intune), enquanto faz as alterações no seu fornecedor de alojamento DNS.

Os passos para adicionar e verificar um domínio personalizado podem, como alternativa, ser [executados no Azure Active Directory](https://azure.microsoft.com/en-us/documentation/articles/active-directory-add-domain/).

Num cenário de nuvem híbrida, depois de adicionar o seu nome de domínio personalizado e ter sido verificado que a sua organização é a proprietária, pode continuar a gerir contas de utilizador no Active Directory no local, em seguida, sincronizá-la com o Azure AD.

## <a name="to-synchronize-on-premises-users-with-azure-ad"></a>Sincronizar os utilizadores no local com o Azure AD##

1. [Adicionar o sufixo UPN](https://technet.microsoft.com/en-us/library/cc772007.aspx) para o seu domínio personalizado no Active Directory no local.
2. Defina o sufixo UPN novo para os utilizadores no local que pretende importar.
3. Execute a [sincronização do Azure AD Connect](https://azure.microsoft.com/en-us/documentation/articles/active-directory-aadconnect/) para integrar os seus utilizadores no local com o Azure AD.
4. Assim que as informações de conta de utilizador forem sincronizadas com êxito, pode atribuir licenças do Microsoft Intune utilizando o [Portal de Gestão do Office 365](https://portal.office.com/Admin/Default.aspx).

### <a name="see-also"></a>Consulte também

[Acerca do seu domínio onmicrosoft.com inicial no Office 365](https://support.office.com/en-us/article/About-your-initial-onmicrosoft-com-domain-in-Office-365-B9FC3018-8844-43F3-8DB1-1B3A8E9CFD5A?ui=en-US&rs=en-US&ad=US)

[O que deve saber antes de iniciar o Microsoft Intune](what-to-know-before-you-start-microsoft-intune.md)
### <a name="next-steps"></a>Próximos passos
Parabéns! Acabou de concluir o passo 2 do *Guia de introdução do Intune*.

>[!div class="step-by-step"]

>[&larr; **Iniciar sessão no Intune**](.\start-with-a-paid-subscription-to-microsoft-intune-step-1.md)     [**Adicionar utilizadores ao Intune** &rarr;](.\start-with-a-paid-subscription-to-microsoft-intune-step-3.md)  



<!--HONumber=Nov16_HO4-->


