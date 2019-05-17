---
title: Configurar um nome de domínio personalizado
titleSuffix: Microsoft Intune
description: Adicionar um nome de domínio personalizado à sua subscrição do Microsoft Intune
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 02/22/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 2382f36f-13d8-4a32-81ad-6cfa604889c3
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4d0c3d11eb3a031f34704dcd9ecf16f3312ac818
ms.sourcegitcommit: 1cae690ca2ac6cc97bbcdf656f54b31878297ae8
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/22/2019
ms.locfileid: "59895985"
---
# <a name="configure-a-custom-domain-name"></a>Configurar um nome de domínio personalizado

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

Este tópico informa os administradores sobre como podem criar um CNAME DNS para simplificar e personalizar a experiência de início de sessão com o Microsoft Intune.

Quando a sua organização se inscreve num serviço Microsoft baseado na cloud, como o Intune, é-lhe disponibilizado um nome de domínio inicial, alojado no Azure Active Directory (AD) semelhante a: **o-seu-dominio.onmicrosoft.com**. Neste exemplo, **o-seu-dominio** é o nome de domínio que escolheu quando se inscreveu. **onmicrosoft.com** é o sufixo atribuído às contas que adicionar à sua subscrição. Pode configurar o domínio personalizado da sua organização para aceder ao Intune, em alternativa ao nome de domínio fornecido com a sua subscrição.

Antes de criar contas de utilizador ou sincronizar o seu Active Directory no local, recomendamos vivamente que decida se irá utilizar apenas o domínio .onmicrosoft.com ou se irá adicionar um ou mais nomes de domínio personalizados. Configure um domínio personalizado antes de adicionar utilizadores para simplificar a gestão de utilizadores. Esta ação permite que os utilizadores iniciem sessão com as credenciais que utilizam para aceder aos outros recursos do domínio.

Ao subscrever um serviço baseado na cloud da Microsoft, a instância desse serviço torna-se num [inquilino do Microsoft Azure AD](http://technet.microsoft.com/library/jj573650.aspx#BKMK_WhatIsAnAzureADTenant), que proporciona serviços de identidade e de diretório para o seu serviço baseado na cloud. E, visto que as tarefas de configuração do Intune para utilizar o nome de domínio personalizado da sua organização são as mesmas que nos outros inquilinos do Microsoft Azure AD, pode utilizar as informações e procedimentos descritos em [Adicionar o domínio](https://azure.microsoft.com/documentation/articles/active-directory-add-domain/).

> [!TIP]
> Para saber mais sobre os domínios personalizados, veja [Conceptual overview of custom domain names in Azure Active Directory (Descrição geral conceptual de nomes de domínio personalizados no Azure Active Directory)](https://azure.microsoft.com/documentation/articles/active-directory-add-domain-concepts/).

Não é possível mudar o nome ou remover a parte onmicrosoft.com do nome de domínio inicial. Pode adicionar, verificar ou remover nomes de domínio personalizados utilizados com o Intune para manter a identidade da sua empresa clara.

## <a name="to-add-and-verify-your-custom-domain"></a>Adicionar e verificar o seu domínio personalizado

1. Aceda ao [centro de administração do Microsoft 365](https://admin.microsoft.com/) e inicie sessão na sua conta de administrador.

2. No painel de navegação, selecione **Configuração** &gt; **Domínios**.

3. Selecione **Adicionar domínio** e escreva o seu nome de domínio personalizado. Selecione **Seguinte**.
   ![Captura de ecrã do centro de administração do Microsoft 365 com as opções Definições > Domínios selecionadas e um novo nome de domínio a ser adicionado](./media/domain-custom-add.png)
4. A caixa de diálogo **Verificar domínio** é aberta, indicando os valores para criar o registo TXT no seu fornecedor de alojamento DNS.
    - **Utilizadores do GoDaddy**: o centro de administração do Microsoft 365 redireciona-o para a página de início de sessão do GoDaddy. Depois de introduzir as suas credenciais e de aceitar o contrato de permissão de alteração de domínio, o registo TXT é criado automaticamente. Em alternativa, pode [criar o registo TXT](https://support.office.com/article/Create-DNS-records-at-GoDaddy-for-Office-365-f40a9185-b6d5-4a80-bb31-aa3bb0cab48a).
    - **Utilizadores de register.com**: devem seguir as [instruções passo a passo](https://support.office.com/article/Create-DNS-records-at-Register-com-for-Office-365-55bd8c38-3316-48ae-a368-4959b2c1684e#BKMK_verify) para criar o registo TXT.

Os passos para adicionar e verificar um domínio personalizado podem também ser [executados no Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-add-domain/).

Pode saber mais [acerca do seu domínio onmicrosoft.com inicial no Office 365](https://support.office.com/article/About-your-initial-onmicrosoft-com-domain-in-Office-365-B9FC3018-8844-43F3-8DB1-1B3A8E9CFD5A)
