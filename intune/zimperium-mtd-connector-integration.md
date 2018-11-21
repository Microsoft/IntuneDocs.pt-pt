---
title: Integrar o Zimperium MTD com o Microsoft Intune
titleSuffix: ''
description: Como configurar a solução de Defesa Contra Ameaças (MTD) do Zimperium com o Microsoft Intune para controlar o acesso aos seus recursos empresariais a partir de dispositivos móveis.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 12/29/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 363fd280-1865-4a61-855b-eb75c3c62753
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 68896a363cab37aabe9a597872da0fe75c44c473
ms.sourcegitcommit: 3903f20cb5686532ccd8c36aa43c5150cee7cca2
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/21/2018
ms.locfileid: "52267242"
---
# <a name="integrate-zimperium-with-intune"></a>Integrar o Zimperium com o Intune

Tem de realizar os passos seguintes para integrar a solução de Defesa Contra Ameaças para Dispositivos Móveis do Zimperium com o Intune.

## <a name="before-you-begin"></a>Antes de começar

> [!NOTE]
> Os seguintes passos são realizados na [consola do Zimperium MTD](https://sso.zimperium.com/signon/aad/).

Antes de iniciar o processo de integração do Zimperium com o Intune, certifique-se de que tem a seguinte subscrição e credenciais:

-   Subscrição do Microsoft Intune

-   Credenciais de administrador do Azure Active Directory para conceder as seguintes permissões:

    -   Iniciar sessão e ler o perfil de utilizador

    -   Aceder ao diretório como o utilizador com sessão iniciada

    -   Ler dados do diretório

    -   Enviar informações do dispositivo para o Intune

-   Credenciais do administrador para aceder à consola do Zimperium MTD.

### <a name="zimperium-app-authorization"></a>Autorização da aplicação Zimperium

O processo de autorização da aplicação Zimperium consiste no seguinte:

-   Permitir que o serviço do Zimperium transmita informações relacionadas com o estado de funcionamento do dispositivo ao Intune.

-   O Zimperium sincroniza com a associação do Grupo de Inscrição do Azure Active Directory (AD) para preencher a respetiva base de dados do dispositivo.

-   Permitir que a consola de administração do Zimperium utilize o Início de Sessão Único (SSO) do Azure AD.

-   Permitir que a aplicação Zimperium inicie sessão através do SSO do Azure AD.

## <a name="to-set-up-zimperium-integration"></a>Para configurar a integração do Zimperium

1.  Aceda a [consola do Zimperium MTD](https://sso.zimperium.com/signon/aad/) e inicie sessão com as suas credenciais.

2.  Selecione **Gestão** a partir do menu esquerdo.

3.  Escolha o **definições de MDM** separador.

4.  Selecione **Adicionar MDM** e, em seguida, selecione **Microsoft Intune** a partir da lista **Fornecedor de MDM**.

5.  Depois de definir o Microsoft Intune como serviço MDM, o **configuração do Microsoft Intune** janela aparece, escolha o **adicionar Azure Active Directory** para cada opção:  **Zimperium zConsole**, **zIPS para iOS e as aplicações Android** para autorizar o Zimperium a comunicar com o Intune e o Azure AD através do Azure AD início de sessão único.

    > [!IMPORTANT]
    > Tem de adicionar as aplicações Zimperium zConsole e zIPS para iOS e Android para concluir o processo de integração com o Intune.

6.  Escolher **Accept** para autorizar a aplicação Zimperium a comunicar com o Intune e Azure Active Directory.

7.  Assim que adicionar a **Zimperium zConsole** e as aplicações **zIPS para iOS e Android** ao Azure AD, adicione os grupos de segurança do Azure AD. Esta adição permite que o Zimperium sincronize o grupo de segurança do Azure AD com o seu serviço.

8.  Escolher **concluir** para guardar a configuração e iniciar a primeira sincronização do grupo de segurança do Azure AD.

## <a name="next-steps"></a>Passos Seguintes

-   [Configurar aplicações do Zimperium](mtd-apps-ios-app-configuration-policy-add-assign.md)
