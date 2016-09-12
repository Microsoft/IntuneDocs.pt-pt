---
title: "Nomes de domínio para o Microsoft Intune | Microsoft Intune"
description: "adicionar nome de domínio ao Intune"
keywords: 
author: andredm7
manager: swadhwa
ms.date: 06/20/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c3c136f0-330d-432a-a91f-16f7dd097e55
ms.reviewer: damionw
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 3eb096fea4569be24cf1ea42088705f0d5da38a4
ms.openlocfilehash: 176da99a198b0a8167ac5d7992a751f2c965f0ac


---



# Nomes de domínio personalizados com o Microsoft Intune

Quando a sua organização se inscreve num serviço Microsoft baseado na nuvem, como o Intune, é-lhe fornecido um nome de domínio inicial, alojado no Azure Active Directory parecido com: **yourdomain.onmicrosoft.com**. Neste exemplo, **oseudomínio** é o nome de domínio que escolheu quando se inscreveu e **onmicrosoft.com** é o sufixo atribuído às contas que adicionar à sua subscrição.

Não é possível mudar o nome ou remover esse nome de domínio inicial. No entanto, pode adicionar, verificar ou remover os seus próprios nomes de domínio personalizado para utilizar com o Intune, que é útil se pretender manter a sua identidade empresarial.

## Adicionar e verificar o seu domínio personalizado 

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

## Sincronizar os utilizadores no local com o Azure AD##

1. [Adicionar o sufixo UPN](https://technet.microsoft.com/en-us/library/cc772007.aspx) para o seu domínio personalizado no Active Directory no local.
2. Defina o sufixo UPN novo para os utilizadores no local que pretende importar.
3. Execute a [sincronização do Azure AD Connect](https://azure.microsoft.com/en-us/documentation/articles/active-directory-aadconnect/) para integrar os seus utilizadores no local com o Azure AD.
4. Assim que as informações de conta de utilizador forem sincronizadas com êxito, pode atribuir licenças do Microsoft Intune utilizando o [Portal de Gestão do Office 365](https://portal.office.com/Admin/Default.aspx).

### Consulte também

[Acerca do seu domínio onmicrosoft.com inicial no Office 365](https://support.office.com/en-us/article/About-your-initial-onmicrosoft-com-domain-in-Office-365-B9FC3018-8844-43F3-8DB1-1B3A8E9CFD5A?ui=en-US&rs=en-US&ad=US)

[What to know before you start Microsoft Intune (O que deve saber antes de iniciar o Microsoft Intune)](what-to-know-before-you-start-microsoft-intune.md)



<!--HONumber=Jul16_HO4-->


