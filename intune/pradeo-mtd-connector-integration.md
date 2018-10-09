---
title: Configurar a integração do Pradeo com o Intune
titleSuffix: Intune on Azure
description: Integração do conector Pradeo com o Intune
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/27/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 82872ba6-80f8-4cc9-adf4-0ccd8ff26dd2
ms.openlocfilehash: 1f59463eeaa9926f2a4ca0d9a9b9b60dd63a8537
ms.sourcegitcommit: fffa64f28278573dc83a846b647315def2108781
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48231179"
---
# <a name="integrate-pradeo-with-intune"></a>Integrar o Pradeo com o Intune

Tem de realizar os passos seguintes para integrar a solução de Defesa Contra Ameaças para Dispositivos Móveis do Pradeo com o Intune.

## <a name="before-you-begin"></a>Antes de começar

> [!NOTE]
> Os seguintes passos devem ser realizados na [consola do Pradeo Security](https://www.apps-security.com).

Antes de iniciar o processo de integração do Pradeo com o Intune, certifique-se de que tem os seguintes elementos:

-   Subscrição do Microsoft Intune

-   Credenciais de administrador do Azure Active Directory para conceder as seguintes permissões:

    -   Iniciar sessão e ler o perfil de utilizador

    -   Aceder ao diretório como o utilizador com sessão iniciada

    -   Ler dados do diretório

    -   Enviar informações do dispositivo para o Intune

-   Credenciais de administrador para aceder à consola do Pradeo Security.

### <a name="pradeo-app-authorization"></a>Autorização da aplicação Pradeo

O processo de autorização da aplicação Pradeo consiste no seguinte:

-   Permitir que o serviço do Pradeo transmita informações relacionadas com o estado de funcionamento do dispositivo ao Intune.

-   O Pradeo sincroniza com a associação do Grupo de Inscrição do Azure AD para preencher a respetiva base de dados do dispositivo.

-   Permitir que a consola de administração do Pradeo utilize o Início de Sessão Único (SSO) do Azure AD.

-   Permitir que a aplicação Pradeo inicie sessão através do SSO do Azure AD.

## <a name="to-set-up-pradeo-integration"></a>Para configurar a integração do Pradeo

1.  Aceda à [consola do Pradeo Security](https://www.apps-security.com) e inicie sessão com as suas credenciais.

2.  Selecione **Administração – Gestão de Mobilidade Empresarial** no menu.

3.  Selecione o **logótipo do Intune**.

4.  Na janela **EMM (Gestão de mobilidade empresarial) – Intune**, em **Passo 1**, selecione o botão **Conector do Pradeo**. 

    ![Janela EMM Intune do Pradeo](./media/pradeo_setup.png)

5. Na janela de ligação do Microsoft Intune, introduza as suas credenciais do Intune.

5.  A página Web do Pradeo é reaberta. Em **Passo 2**, selecione o botão **Estado de Funcionamento dos Dispositivos do Pradeo**.

7. Na janela Conector do Pradeo-Intune, selecione **Aceitar**. 

8. Na janela Conector de API de dispositivo do Pradeo, selecione **Aceitar**.

9. A página Web do Pradeo é reaberta. Em **Passo 3**, selecione o botão **Ligar à Microsoft**. 

10. Na janela de autenticação do Microsoft Intune, introduza as suas credenciais do Intune.

11. Quando a mensagem **Integração Bem-sucedida** for apresentada, significa que a integração foi concluída.

## <a name="next-steps"></a>Próximos passos

-   [Configurar as aplicações do Pradeo](mtd-apps-ios-app-configuration-policy-add-assign.md)