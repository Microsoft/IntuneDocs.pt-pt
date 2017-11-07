---
title: "Autenticação multifator para inscrição de dispositivos no Intune"
titlesuffix: Azure portal
description: "Como solicitar a autenticação multifator no Azure AD para inscrição de dispositivos."
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 10/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 94280c73-c05c-4e72-b0dd-a7cb997782f9
ROBOTS: 
ms.custom: intune-azure
ms.openlocfilehash: a3aabe77257fd7e6964dd7bd83035c8a491a58b4
ms.sourcegitcommit: 94d3d86f8ae9f82a9872384bbaae53580036a4ff
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/01/2017
---
# <a name="multi-factor-authentication-for-intune-device-enrollments"></a>Autenticação multifator para inscrições de dispositivos no Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

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
>Não configure **Regras de acesso com base no dispositivo** para a Inscrição no Microsoft Intune.

1. Inicie sessão no [Portal do Microsoft Azure](https://portal.azure.com) com as suas credenciais.
2. No portal, selecione **Azure Active Directory**.
2. No **Azure Active Directory**, selecione **Gerir** > **Aplicações empresariais**.
3. Em **Aplicações empresariais**, selecione **Gerir** > **Todas as aplicações**. É-lhe apresentada uma lista de todas as aplicações do Azure que gere.
3. A partir da lista, selecione **Inscrição do Microsoft Intune**.
4. Em **Inscrição do Microsoft Intune**, selecione **Segurança** > **Acesso condicional**.
5. Selecione **Nova política**.
6. Em **Nova política**, escreva um nome descritivo para a política.
7. Na secção **Atribuições**, selecione **Utilizadores e grupos**.
8. Em **Utilizadores e grupos**, selecione os utilizadores ou grupos que receberão esta política e, em seguida, selecione **Concluído**.
9. Na secção **Atribuições**, selecione **Aplicações na cloud**.
10. No separador **Incluir** das **Aplicações na cloud**, clique em **Selecionar aplicações** e, em seguida, **Selecionar** > **Inscrição do Microsoft Intune**. Em seguida, selecione **Concluído**.
11. Na secção **Atribuições**, selecione **Condições**.
12. Em **Condições**, não tem de configurar as definições para a MFA.
13. Na secção **Controlos de acesso**, selecione **Conceder**.
14. Em **Conceder**, selecione **Conceder acesso** e, em seguida, **Exigir autenticação multifator**.
    Não selecione **Pedir que o dispositivo seja marcado como compatível** porque um dispositivo não pode ser avaliado pela conformidade até estar inscrito.
15. Clique em **Selecionar**.
16. Em **Nova política**, selecione **Ativar política** > **Ativada** e, em seguida, selecione **Criar**.



## <a name="next-steps"></a>Próximos passos

Quando os utilizadores finais inscreverem o respetivo dispositivo, têm de autenticar com uma segunda forma de identificação, como um PIN, telefone ou biometria.
