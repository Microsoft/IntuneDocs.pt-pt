---
title: Integrar o Zimperium MTD com o Microsoft Intune | Microsoft Intune
description: Como configurar a solução de Defesa Contra Ameaças (MTD) do Zimperium com o Microsoft Intune para controlar o acesso aos seus recursos empresariais a partir de dispositivos móveis.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 12/04/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 363fd280-1865-4a61-855b-eb75c3c62753
ms.reviewer: davidra
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: bc7128e006b46f8e918c71697cf2b371fe81fbd7
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/02/2019
ms.locfileid: "57229484"
---
# <a name="integrate-zimperium-with-intune"></a>Integrar o Zimperium com o Intune

Tem de realizar os passos seguintes para integrar a solução de Defesa Contra Ameaças para Dispositivos Móveis do Zimperium com o Intune.

## <a name="before-you-begin"></a>Antes de começar

> [!NOTE]
> Os seguintes passos são realizados na [consola do Zimperium MTD](https://sso.zimperium.com/signon/aad/).

Antes de iniciar o processo de integração do Zimperium com o Intune, certifique-se de que tem a seguinte subscrição e credenciais:

-   Subscrição do Microsoft Intune

-   Credenciais de administrador do Active Directory Administrador Global do diretório do Azure para conceder as permissões seguintes:

    -   Iniciar sessão e ler o perfil de utilizador

    -   Aceder ao diretório como o utilizador com sessão iniciada

    -   Ler dados do diretório

    -   Enviar informações do dispositivo para o Intune

-   Credenciais do administrador para aceder à consola do Zimperium MTD.

### <a name="zimperium-app-authorization"></a>Autorização da aplicação Zimperium

O processo de autorização da aplicação Zimperium consiste no seguinte:

-   Conceda as permissões de serviço do Zimperium transmita informações relacionadas com estado de funcionamento do dispositivo ao Intune. Para conceder estas permissões, tem de utilizar credenciais de Administrador Global. Concessão de permissões é uma operação única. Depois das permissões são concedidas, as credenciais de Administrador Global não são necessários para a operação do dia a dia.

-   O Zimperium sincroniza com a associação do Grupo de Inscrição do Azure Active Directory (AD) para preencher a respetiva base de dados do dispositivo.

-   Permitir que a consola de administração do Zimperium utilize o Início de Sessão Único (SSO) do Azure AD.

-   Permitir que a aplicação Zimperium inicie sessão através do SSO do Azure AD.

Para obter mais informações sobre o consentimento e de aplicações do Azure Active Directory, consulte [solicitar as permissões de um administrador do](https://docs.microsoft.com/azure/active-directory/develop/v2-permissions-and-consent#request-the-permissions-from-a-directory-admin) no artigo do Azure Active Directory *permissões e consentimento no Azure Active Ponto final de v2.0 do diretório*.


## <a name="to-set-up-zimperium-integration"></a>Para configurar a integração do Zimperium

1.  Aceda à [Consola do Zimperium MTD](https://sso.zimperium.com/signon/aad/) e inicie sessão com as suas credenciais. Para executar o processo de configuração de integração do Zimperium, tem de iniciar sessão com um utilizador do Azure Active Directory que tenha a função de Administrador Global. Esta operação de configuração de uso individual utiliza os direitos de Administrador Global para conceder permissão na sua organização para as aplicações Zimperium a comunicar com o Intune. 

2.  Selecione **Gestão** a partir do menu esquerdo.

3.  Selecione o separador **definições de MDM**.

4.  Selecione **Adicionar MDM** e, em seguida, selecione **Microsoft Intune** a partir da lista **Fornecedor de MDM**.

5.  Depois de definir o Microsoft Intune como serviço MDM, o **configuração do Microsoft Intune** janela aparece, escolha a **adicionar Azure Active Directory** para cada opção: **Zimperium zConsole**, **zIPS para iOS e as aplicações Android** para autorizar o Zimperium a comunicar com o Intune e o Azure AD através do Azure AD início de sessão único.

    > [!IMPORTANT]  
    > Tem de adicionar o Zimperium zConsole, zIPS aplicações iOS e Android para concluir o processo de integração com o Intune.

6.  Selecione **Aceitar** para autorizar a aplicação Zimperium a comunicar com o Intune e o Azure Active Directory.

7.  Depois de adicionar o **Zimperium zConsole** e o **zIPS para iOS e Android** aplicações para o Azure AD, adicione os grupos de segurança do Azure AD. Esta adição permite que o Zimperium sincronize o grupo de segurança do Azure AD com o seu serviço.

8.  Selecione **Concluir** para guardar a configuração e iniciar a primeira sincronização do grupo de segurança do Azure AD.

9.  Terminar sessão da consola do Zimperium MTD.

## <a name="next-steps"></a>Passos Seguintes

-   [Configurar aplicações do Zimperium](mtd-apps-ios-app-configuration-policy-add-assign.md)
