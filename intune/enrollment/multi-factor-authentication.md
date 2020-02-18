---
title: Exigir a autenticação multifator para inscrição de dispositivos no Intune
titleSuffix: Microsoft Intune
description: Como exigir a autenticação multifator no Azure AD para a inscrição de dispositivos no Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 94280c73-c05c-4e72-b0dd-a7cb997782f9
ROBOTS: ''
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 14347d12888ff5ef61d4543409a08fbdeb371c89
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/17/2020
ms.locfileid: "77415207"
---
# <a name="require-multi-factor-authentication-for-intune-device-enrollments"></a>Exigir a autenticação multifator para inscrições de dispositivos no Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

O Intune pode utilizar a autenticação multifator (MFA) do Azure Active Directory (AD) para a inscrição de dispositivos para ajudá-lo a proteger os recursos da sua empresa.

A MFA exige dois ou mais dos seguintes métodos de verificação:

- Algo que saiba (normalmente uma palavra-passe ou PIN).
- Algo que tenha (um dispositivo fidedigno que não seja duplicado facilmente, como um telemóvel).
- Algo que seja (biometria, como uma impressão digital).

O MFA é suportado para dispositivos iOS/iPadOS, Android, Windows 8.1 ou posterior, Windows Phone 8.1 ou Windows 10 Mobile ou dispositivos posteriores.

Ao ativar a MFA, os utilizadores finais têm de fornecer duas formas de credenciais para inscrever um dispositivo.

## <a name="configure-intune-to-require-multi-factor-authentication-at-device-enrollment"></a>Configurar o Intune para exigir a autenticação multifator na inscrição de dispositivos

Para exigir MFA na inscrição de um dispositivo, siga estes passos:

>[!Important]
>Tem de ter a edição Azure Active Directory Premium P1 ou superior atribuída aos seus utilizadores para implementar esta política.

>[!Important]
>Não configure **Regras de acesso com base no dispositivo** para a Inscrição no Microsoft Intune.

1. Inscreva-se no [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431), escolha **dispositivos** > **acesso condicional**. O nó de Acesso Condicional acedido a partir do *Intune* é o mesmo nó acedido a partir do *Azure AD*.
2. Selecione **Nova política**.
3. Em **Nova política**, escreva um nome descritivo para a política.
4. Na secção **Atribuições**, selecione **Utilizadores e grupos**. 
5. Em **Utilizadores e grupos**, selecione **Selecionar utilizadores ou grupos** e a opção **Utilizadores e grupos**. Em seguida, selecione os utilizadores e/ou grupos que receberão esta política e selecione **Concluído**.
6. Na secção **Atribuições**, selecione **Aplicações na cloud**.
7. No separador **Incluir** das **Aplicações na cloud**, clique em **Selecionar aplicações** e, em seguida, **Selecionar** > **Inscrição do Microsoft Intune**. Em seguida, selecione **Concluído**. Ao escolher a **Microsoft Intune Registration**, o acesso condicional MFA é aplicado apenas à inscrição do dispositivo (solicitação mFA única).
8. Na secção **Atribuições**, para **Condições**, não tem de configurar definições para a MFA.
9. Na secção **Controlos de acesso**, selecione **Conceder**.
10. Em **Conceder**, selecione **Conceder acesso** e, em seguida, **Exigir autenticação multifator**. Não selecione **Pedir que o dispositivo seja marcado como compatível** porque um dispositivo não pode ser avaliado pela conformidade até estar inscrito. Em seguida, selecione **Selecionar**.
11. Em **Nova política**, selecione **Ativar política** > **Ativada** e, em seguida, selecione **Criar**.



## <a name="next-steps"></a>Próximos passos

Quando os utilizadores finais inscreverem o respetivo dispositivo, têm de autenticar com uma segunda forma de identificação, como um PIN, telefone ou biometria.
