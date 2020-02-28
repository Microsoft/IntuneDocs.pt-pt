---
title: Perfis de fornecimento de aplicações iOS/iPadOS no Microsoft Intune
titleSuffix: ''
description: O Intune proporciona-lhe as ferramentas necessárias para atribuir proativamente um novo perfil de aprovisionamento a dispositivos que tenham aplicações prestes a expirar.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/27/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: bbc3ba4a-df48-4aeb-988b-69a177764e3a
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 184209573be3a63a1317df702782d4935383c6d9
ms.sourcegitcommit: 045ca42cad6f86024af9a38a380535f42a6b4bef
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/28/2020
ms.locfileid: "77781382"
---
# <a name="use-ios-app-provisioning-profiles-to-prevent-your-apps-from-expiring"></a>Utilizar perfis de aprovisionamento de aplicações iOS para impedir as aplicações de expirar

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

## <a name="introduction"></a>Introdução

As aplicações de linha de negócioapple iOS/iPadOS que são atribuídas a iPhones e iPads são construídas com um perfil de provisionamento incluído e código que é assinado com um certificado. Quando a aplicação é executada, o iOS/iPadOS confirma a integridade da aplicação iOS/iPadOS e aplica políticas definidas pelo perfil de provisionamento. São feitas as confirmações seguintes:

- **Integridade do ficheiro** de instalação - iOS/iPadOS compara os detalhes da aplicação com a chave pública do certificado de assinatura da empresa. Caso sejam diferentes, é possível que os conteúdos das aplicações tenham sido alterados e a aplicação não poderá ser executada.
- **Aplicação de capacidades** - iOS/iPadOS tenta impor as capacidades da app a partir do perfil de provisionamento da empresa (não perfis individuais de fornecimento de desenvolvedores) que estão no ficheiro de instalação de aplicações (.ipa).


Geralmente, o certificado de assinatura da empresa que utiliza para assinar as aplicações dura três anos. No entanto, o perfil de aprovisionamento expira após um ano. Enquanto o certificado permanecer válido, o Intune proporciona-lhe as ferramentas para atribuir pró-ativamente uma nova política de perfil de aprovisionamento a dispositivos que tenham aplicações prestes a expirar.
Quando o certificado expirar, tem de voltar a assinar a aplicação com um certificado novo e incorporar um novo perfil de aprovisionamento com a chave desse certificado novo.

Como administrador, pode incluir e excluir grupos de segurança para atribuir a configuração de provisionamento de aplicações iOS/iPadOS. Por exemplo, pode atribuir uma configuração de fornecimento de aplicações iOS/iPadOS a Todos os Utilizadores, mas excluir um grupo executivo.

## <a name="how-to-create-an-ios-mobile-app-provisioning-profile"></a>Como criar um perfil de aprovisionamento de aplicação móvel de iOS

1. Inscreva-se no [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selecione **Apps** > os perfis de **fornecimento de aplicações iOS** > **Criar o perfil**.
3. Na página Basics, adicione os **seguintes valores:**
    - **Nome** – indique um nome para este perfil de aprovisionamento móvel.
    - **Descrição** - opcionalmente, indique uma descrição para a política.
    - **Carregar ficheiro de perfil** – escolha o ícone **Abrir** e, em seguida, escolha um ficheiro de Perfil de Configuração Móvel da Apple (com a extensão `.mobileprovision`) que transferiu do [site Apple Developer](https://developer.apple.com/).

   A data de **validade** será preenchida a partir de um valor no ficheiro Apple Mobile Configuration Profile que adicionou acima.<br>

   <img alt="Create profile - Basics" src="~/apps/media/app-provisioning-profile-ios/app-provisioning-profile-ios-01.png">

4. Clique **em Seguir: Etiquetas**de âmbito .<br>
   Na página **scope tags** pode configurar opcionalmente as etiquetas de âmbito para determinar quem pode ver o perfil de provisionamento de aplicações iOS/iPadOS no Intune. Para obter mais informações sobre etiquetas de âmbito, consulte [Utilize o controlo de acesso baseado em papéis e as etiquetas](../fundamentals/scope-tags.md)de âmbito para TI distribuídos .
5. Clique **em seguir: Atribuições**.<br>
   A página **De missões** permite-lhe atribuir o perfil a utilizadores e dispositivos. É importante notar que pode atribuir um perfil a um dispositivo, quer o dispositivo seja ou não gerido pela Intune.
6. Clique **em Seguir: Rever + criar** para rever os valores introduzidos para o perfil.
7. Quando terminar, clique em **Criar** o perfil de provisionamento de aplicações iOS/iPadOS em Intune. 

## <a name="next-steps"></a>Próximos passos

Atribuir o perfil aos dispositivos iOS/iPadOS necessários. Para obter mais informações, siga os passos em [Como atribuir perfis de dispositivo](../device-profile-assign.md).
