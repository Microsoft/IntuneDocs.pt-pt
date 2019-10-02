---
title: Inscrever-se ou iniciar sessão no Microsoft Intune
description: Como pode inscrever-se numa subscrição do Microsoft Intune ou iniciar sessão com a sua subscrição.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/02/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 0f3ce07a-b718-42a9-bace-f99a8b8abd94
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: fe3f856a2faba2c140fa92fa9ab486213c38a1c1
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71729620"
---
# <a name="sign-up-or-sign-in-to-microsoft-intune"></a>Inscrever-se ou iniciar sessão no Microsoft Intune

[!INCLUDE [both-portals](../../intune-classic/includes/note-for-both-portals.md)]

Este tópico informa os administradores de sistema acerca da inscrição numa conta do Intune.

Antes de se inscrever no Intune, confirme se já tem uma conta do Microsoft Online Services, um Contrato Enterprise ou contrato de licenciamento em volume equivalente. Um contrato de licenciamento em volume da Microsoft ou outra subscrição dos serviços cloud da Microsoft, como o Office 365, geralmente inclui uma conta escolar ou profissional.

Se já tiver uma conta escolar ou profissional, **inicie sessão** com a mesma e adicione o Intune à sua subscrição. Caso contrário, pode **inscrever-se** numa conta nova e utilizar o Intune para a sua organização.

>[!WARNING]
>Não pode combinar uma conta escolar ou profissional existente após inscrever-se numa conta nova.

## <a name="how-to-sign-up-for-intune"></a>Como se inscrever no Intune

1. Visite a página [Inscrição no Intune](https://admin.microsoft.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0%20).

   ![Captura de ecrã da página Web de inscrição numa conta de Avaliação do Microsoft Intune](./media/account-sign-up/account-sign-up-site.png)

2. Na página Inscrição, inicie sessão ou inscreva-se para gerir uma nova subscrição do Intune.

## <a name="post-sign-up-considerations"></a>Considerações de pós-inscrição
Depois de se inscrever numa nova subscrição, recebe uma mensagem de e-mail com as informações da sua conta para o endereço de e-mail que indicou durante o processo de inscrição. Este e-mail confirma que a sua subscrição está ativa.

Depois de concluir o processo de inscrição, você será direcionado para o centro de administração do Microsoft 365, usado para adicionar usuários e atribuir licenças a eles. Se tiver apenas contas baseadas na cloud com o seu nome de domínio onmicrosoft.com predefinido, pode adicionar utilizadores e atribuir licenças neste momento. Contudo, se planear utilizar o [nome de domínio personalizado](custom-domain-name-configure.md) da sua organização ou as [informações de conta de utilizador sincronizada](users-add.md#sync-active-directory-and-add-users-to-intune) do Active Directory no local, pode fechar essa janela do browser.

## <a name="sign-in-to-microsoft-intune"></a>Entrar no Microsoft Intune
Depois de se inscrever no Intune, você pode usar qualquer dispositivo com um [navegador com suporte](supported-devices-browsers.md#intune-supported-web-browsers) para entrar no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) para administrar o serviço.

Por padrão, sua conta deve ter uma das seguintes permissões no Azure AD:
- Administrador Global
- Administrador de serviços do Intune (também conhecido como administrador do Intune)

Para conceder acesso para administrar o serviço para usuários com outras permissões, consulte [controle de acesso baseado em função](role-based-access-control.md)

### <a name="intune-admin-portal-url"></a>URL do portal de administração do Intune

Centro de administração do Microsoft 365: https://devicemanagement.microsoft.com

Portal do Azure do Intune: https://portal.azure.com/#blade/Microsoft_Intune_DeviceSettings/ExtensionLandingBlade

Intune para Educação: https://intuneeducation.portal.azure.com

Portal clássico do Intune: https://manage.microsoft.com O portal clássico do Intune é usado somente para gerenciar dispositivos registrados com o cliente de software do Intune PC

### <a name="urls-for-intune-services-provided-by-office-365"></a>URLs para serviços do Intune fornecidos pelo Office 365

Microsoft 365 Business: https://portal.microsoft.com/adminportal

Gerenciamento de dispositivo móvel do Office 365: https://portal.office.com/adminportal/home#/MifoDevices

## <a name="see-also"></a>Consulte também
[Não é possível entrar no Office 365, no Azure ou no Intune](https://support.microsoft.com/help/2412085)
