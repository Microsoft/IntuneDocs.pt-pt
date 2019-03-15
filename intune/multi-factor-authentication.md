---
title: Exigir a autenticação multifator para inscrição de dispositivos no Intune
titlesuffix: Microsoft Intune
description: Como exigir a autenticação multifator no Azure AD para a inscrição de dispositivos no Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 94280c73-c05c-4e72-b0dd-a7cb997782f9
ROBOTS: ''
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d1df55ba9c3c2bc07a413ed6cc05e2f92c7f4a92
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/14/2019
ms.locfileid: "57391970"
---
# <a name="require-multi-factor-authentication-for-intune-device-enrollments"></a>Exigir a autenticação multifator para inscrições de dispositivos no Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

O Intune pode utilizar a autenticação multifator (MFA) do Azure Active Directory (AD) para a inscrição de dispositivos para ajudá-lo a proteger os recursos da sua empresa.

A MFA exige dois ou mais dos seguintes métodos de verificação:

- Algo que saiba (normalmente uma palavra-passe ou PIN).
- Algo que tenha (um dispositivo fidedigno que não seja duplicado facilmente, como um telemóvel).
- Algo que seja (biometria, como uma impressão digital).

A MFA é suportada para iOS, Android, Windows 8.1 ou posterior, Windows Phone 8.1, Windows 10 Mobile ou dispositivos posteriores.

Ao ativar a MFA, os utilizadores finais têm de fornecer duas formas de credenciais para inscrever um dispositivo.

## <a name="configure-intune-to-require-multi-factor-authentication-at-device-enrollment"></a>Configurar o Intune para exigir a autenticação multifator na inscrição de dispositivos

Para exigir MFA na inscrição de um dispositivo, siga estes passos:

>[!Important]
>Tem de ter a edição Azure Active Directory Premium P1 ou superior atribuída aos seus utilizadores para implementar esta política.

>[!Important]
>Não configure **Regras de acesso com base no dispositivo** para a Inscrição no Microsoft Intune.

1. Inicie sessão no [Portal do Microsoft Azure](https://portal.azure.com) com as suas credenciais.
2. No portal, aceda a **Intune** e escolha **acesso condicional**. O nó de acesso condicional acedido a partir *Intune* é o mesmo nó como acedidos a partir de *do Azure AD*.
4. Selecione **Nova política**.
5. Em **Nova política**, escreva um nome descritivo para a política.
6. Na secção **Atribuições**, selecione **Utilizadores e grupos**. 
7. Em **Utilizadores e grupos**, selecione **Selecionar utilizadores ou grupos** e a opção **Utilizadores e grupos**. Em seguida, selecione os utilizadores e/ou grupos que receberão esta política e selecione **Concluído**.
8. Na secção **Atribuições**, selecione **Aplicações na cloud**.
9. No separador **Incluir** das **Aplicações na cloud**, clique em **Selecionar aplicações** e, em seguida, **Selecionar** > **Inscrição do Microsoft Intune**. Em seguida, selecione **Concluído**.
10. Na secção **Atribuições**, para **Condições**, não tem de configurar definições para a MFA.
11. Na secção **Controlos de acesso**, selecione **Conceder**.
12. Em **Conceder**, selecione **Conceder acesso** e, em seguida, **Exigir autenticação multifator**. Não selecione **Pedir que o dispositivo seja marcado como compatível** porque um dispositivo não pode ser avaliado pela conformidade até estar inscrito. Em seguida, selecione **Selecionar**.
13. Em **Nova política**, selecione **Ativar política** > **Ativada** e, em seguida, selecione **Criar**.



## <a name="next-steps"></a>Passos Seguintes

Quando os utilizadores finais inscreverem o respetivo dispositivo, têm de autenticar com uma segunda forma de identificação, como um PIN, telefone ou biometria.
