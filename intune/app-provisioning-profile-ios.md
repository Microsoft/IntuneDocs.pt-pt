---
title: Perfis de aprovisionamento de aplicações iOS no Microsoft Intune
titleSuffix: ''
description: O Intune proporciona-lhe as ferramentas necessárias para atribuir proativamente um novo perfil de aprovisionamento a dispositivos que tenham aplicações prestes a expirar.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/08/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: bbc3ba4a-df48-4aeb-988b-69a177764e3a
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 888c136934deca80877d75879e270807af194a1e
ms.sourcegitcommit: 364a7dbc7eaa414c7a9c39cf53eb4250e1ad3151
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2019
ms.locfileid: "59292227"
---
# <a name="use-ios-app-provisioning-profiles-to-prevent-your-apps-from-expiring"></a>Utilizar perfis de aprovisionamento de aplicações iOS para impedir as aplicações de expirar

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

## <a name="introduction"></a>Introdução

As aplicações de linha de negócio iOS da Apple atribuídas a iPhones e iPads são criadas com um perfil de aprovisionamento incluído e um código assinado com um certificado. Quando as aplicações são executadas, o iOS confirma a integridade das mesmas e aplica as políticas definidas pelo perfil de aprovisionamento. São feitas as confirmações seguintes:

- **Integridade do ficheiro de instalação** - o iOS compara os detalhes das aplicações com a chave pública do certificado de assinatura de empresa. Caso sejam diferentes, é possível que os conteúdos das aplicações tenham sido alterados e a aplicação não poderá ser executada.
- **Imposição de capacidades** - o iOS tenta impor as capacidades das aplicações do perfil de aprovisionamento empresarial (não dos perfis de aprovisionamento de programadores individuais) presente no ficheiro de instalação (.ipa) das aplicações.


Geralmente, o certificado de assinatura da empresa que utiliza para assinar as aplicações dura três anos. No entanto, o perfil de aprovisionamento expira após um ano. Enquanto o certificado permanecer válido, o Intune proporciona-lhe as ferramentas para atribuir pró-ativamente uma nova política de perfil de aprovisionamento a dispositivos que tenham aplicações prestes a expirar.
Quando o certificado expirar, tem de voltar a assinar a aplicação com um certificado novo e incorporar um novo perfil de aprovisionamento com a chave desse certificado novo.

Enquanto administrador, pode incluir e excluir grupos de segurança para atribuir a configuração de aprovisionamento de aplicações iOS. Por exemplo, pode atribuir uma configuração de aprovisionamento de aplicações iOS a Todos os Utilizadores, mas excluir um grupo executivo.

## <a name="how-to-create-an-ios-mobile-app-provisioning-profile"></a>Como criar um perfil de aprovisionamento de aplicação móvel de iOS

1. Inicie sessão no [Portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços** > **Intune**. O Intune encontra-se na secção **Monitorização + Gestão**.
3. No painel **Intune**, selecione **Aplicações do cliente**.
1.  Na carga de trabalho **Aplicações do cliente**, selecione **Gerir** > **Perfis de aprovisionamento da aplicação iOS**.
2.  No painel Lista de perfis, selecione **Criar perfil**.
3. No painel **Criar perfil**, configure os seguintes valores:
    - **Nome** – indique um nome para este perfil de aprovisionamento móvel.
    - **Descrição** - opcionalmente, indique uma descrição para a política.
    - **Carregar ficheiro de perfil** -escolha **Open** ícone e, em seguida, escolha um ficheiro de perfil de configuração móvel da Apple (com a extensão `.mobileprovision`) que transferiu a partir do [site Apple Developer](https://developer.apple.com/).
4. Quando tiver terminado, escolha **Criar**.

## <a name="next-steps"></a>Passos Seguintes

Atribua o perfil aos dispositivos iOS necessários. Para obter mais informações, siga os passos em [Como atribuir perfis de dispositivo](device-profile-assign.md).
