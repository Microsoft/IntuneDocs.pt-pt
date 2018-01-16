---
title: Integrar o Zimperium com o Intune
titleSuffix: Intune on Azure
description: Integrar o Intune com o Zimperium
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 12/29/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 363fd280-1865-4a61-855b-eb75c3c62753
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 515f99f694a9125d60bb9210becc6722bfb9e24f
ms.sourcegitcommit: a3a744ea55f38a360ca9f788c77a5b3018d1add5
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/30/2017
---
# <a name="integrate-zimperium-with-intune"></a>Integrar o Zimperium com o Intune

Tem de realizar os passos seguintes para integrar a solução de Defesa Contra Ameaças para Dispositivos Móveis do Zimperium com o Intune.

## <a name="before-you-begin"></a>Antes de começar

> [!NOTE]
> Os passos seguintes devem ser realizados na [consola do Zimperium MTD](https://staging2-console.zimperium.com).

Antes de iniciar o processo de integração do Zimperium com o Intune, certifique-se de que tem os seguintes elementos:

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

-   O Zimperium sincroniza com a associação do Grupo de Inscrição do Azure AD para preencher a respetiva base de dados do dispositivo.

-   Permitir que a consola de administração do Zimperium utilize o Início de Sessão Único (SSO) do Azure AD.

-   Permitir que a aplicação Zimperium inicie sessão através do SSO do Azure AD.

## <a name="to-set-up-zimperium-integration"></a>Para configurar a integração do Zimperium

1.  Aceda à [Consola do Zimperium MTD](https://staging2-console.zimperium.com) e inicie sessão com as suas credenciais.

2.  Selecione **Gestão** a partir do menu esquerdo.

3.  Selecione o separador **definições de MDM**.

4.  Selecione **Adicionar MDM** e, em seguida, selecione **Microsoft Intune** a partir da lista **Fornecedor de MDM**.

5.  Assim que definir o Microsoft Intune como serviço MDM, é apresentada a janela **Configuração do Microsoft Intune**, escolha **Adicionar Azure Active Directory** para cada opção: **Zimperium zConsole** e **Aplicações zIPS para iOS e Android** para autorizar o Zimperium a comunicar com o Intune e o Azure AD através do Início de Sessão Único do Azure AD.

    > [!IMPORTANT]
    > Tem de adicionar as aplicações Zimperium zConsole e zIPS para iOS e Android para concluir o processo de integração com o Intune.

6.  Selecione **Aceitar** para autorizar a aplicação Zimperium a comunicar com o Intune e o Azure Active Directory.

7.  Assim que adicionar a **Zimperium zConsole** e as aplicações **zIPS para iOS e Android** ao Azure AD, adicione os grupos de segurança do Azure AD para que a Zimperium possa sincronizar o grupo de segurança do Azure AD com o seu serviço.

8.  Selecione **Concluir** para guardar a configuração e iniciar a primeira sincronização do grupo de segurança do Azure AD.

## <a name="next-steps"></a>Próximos passos

-   [Configurar aplicações do Zimperium](mtd-apps-ios-app-configuration-policy-add-assign.md)
