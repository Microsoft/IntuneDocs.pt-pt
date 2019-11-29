---
title: Perfis de aprovisionamento de aplicações iOS no Microsoft Intune
titleSuffix: ''
description: O Intune proporciona-lhe as ferramentas necessárias para atribuir proativamente um novo perfil de aprovisionamento a dispositivos que tenham aplicações prestes a expirar.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
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
ms.openlocfilehash: 31bad59c33a34d0b92d93979b20b58f70fd042ef
ms.sourcegitcommit: 73b362173929f59e9df57e54e76d19834f155433
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/27/2019
ms.locfileid: "74564088"
---
# <a name="use-ios-app-provisioning-profiles-to-prevent-your-apps-from-expiring"></a>Utilizar perfis de aprovisionamento de aplicações iOS para impedir as aplicações de expirar

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

## <a name="introduction"></a>Introdução

As aplicações de linha de negócio iOS da Apple atribuídas a iPhones e iPads são criadas com um perfil de aprovisionamento incluído e um código assinado com um certificado. Quando as aplicações são executadas, o iOS confirma a integridade das mesmas e aplica as políticas definidas pelo perfil de aprovisionamento. São feitas as confirmações seguintes:

- **Integridade do ficheiro de instalação** - o iOS compara os detalhes das aplicações com a chave pública do certificado de assinatura de empresa. Caso sejam diferentes, é possível que os conteúdos das aplicações tenham sido alterados e a aplicação não poderá ser executada.
- **Imposição de capacidades** - o iOS tenta impor as capacidades das aplicações do perfil de aprovisionamento empresarial (não dos perfis de aprovisionamento de programadores individuais) presente no ficheiro de instalação (.ipa) das aplicações.


Geralmente, o certificado de assinatura da empresa que utiliza para assinar as aplicações dura três anos. No entanto, o perfil de aprovisionamento expira após um ano. Enquanto o certificado permanecer válido, o Intune proporciona-lhe as ferramentas para atribuir pró-ativamente uma nova política de perfil de aprovisionamento a dispositivos que tenham aplicações prestes a expirar.
Quando o certificado expirar, tem de voltar a assinar a aplicação com um certificado novo e incorporar um novo perfil de aprovisionamento com a chave desse certificado novo.

Enquanto administrador, pode incluir e excluir grupos de segurança para atribuir a configuração de aprovisionamento de aplicações iOS. Por exemplo, pode atribuir uma configuração de aprovisionamento de aplicações iOS a Todos os Utilizadores, mas excluir um grupo executivo.

## <a name="how-to-create-an-ios-mobile-app-provisioning-profile"></a>Como criar um perfil de aprovisionamento de aplicação móvel de iOS

1. Entre no centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selecione **aplicativos** > **perfis de provisionamento de aplicativo IOS** > **Criar perfil**.
3. Na página **noções básicas** , adicione os seguintes valores:
    - **Nome** – indique um nome para este perfil de aprovisionamento móvel.
    - **Descrição** - opcionalmente, indique uma descrição para a política.
    - **Carregar ficheiro de perfil** – escolha o ícone **Abrir** e, em seguida, escolha um ficheiro de Perfil de Configuração Móvel da Apple (com a extensão `.mobileprovision`) que transferiu do [site Apple Developer](https://developer.apple.com/).

   A **data de validade** será populada a partir de um valor no arquivo de perfil de configuração móvel da Apple que você adicionou acima.<br>

   <img alt="Create profile - Basics" src="~/apps/media/app-provisioning-profile-ios/app-provisioning-profile-ios-01.png">

4. Clique em **Avançar: marcas de escopo**.<br>
   Na página **marcas de escopo** , você pode opcionalmente configurar marcas de escopo para determinar quem pode ver o perfil de provisionamento de aplicativo Ios no Intune. Para obter mais informações sobre marcas de escopo, consulte [usar o controle de acesso baseado em função e marcas de escopo para distribuí-lo](../fundamentals/scope-tags.md).
5. Clique em **Avançar: atribuições**.<br>
   A página **atribuições** permite que você atribua o perfil a usuários e dispositivos. É importante observar que você pode atribuir um perfil a um dispositivo, independentemente de o dispositivo ser gerenciado pelo Intune ou não.
6. Clique em **Avançar: examinar + criar** para examinar os valores inseridos para o perfil.
7. Quando terminar, clique em **criar** para criar o perfil de provisionamento de aplicativo Ios no Intune. 

## <a name="next-steps"></a>Próximos passos

Atribua o perfil aos dispositivos iOS necessários. Para obter mais informações, siga os passos em [Como atribuir perfis de dispositivo](../device-profile-assign.md).
