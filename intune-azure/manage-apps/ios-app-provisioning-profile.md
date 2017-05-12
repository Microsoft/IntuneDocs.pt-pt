---
title: "Perfis de aprovisionamento de aplicações | Documentos da Microsoft"
titleSuffix: Intune Azure preview
description: "Pré-visualização do Azure no Intune: o Intune proporciona-lhe as ferramentas para atribuir pró-ativamente um novo perfil de aprovisionamento a dispositivos que tenham aplicações prestes a expirar."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 05/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bbc3ba4a-df48-4aeb-988b-69a177764e3a
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 3758df744311392528be01c826527c2a9d879975
ms.openlocfilehash: fa3e0b481c31779261d5f6b23b729ca55331266b
ms.contentlocale: pt-pt
ms.lasthandoff: 05/10/2017

---

# <a name="use-ios-mobile-provisioning-profiles-to-prevent-your-apps-from-expiring"></a>Utilizar perfis de aprovisionamento móvel de iOS para impedir as aplicações de expirar

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

## <a name="introduction"></a>Introdução

As aplicações de linha de negócio iOS da Apple atribuídas a iPhones e iPads são criadas com um perfil de aprovisionamento incluído e um código assinado com um certificado. Quando as aplicações são executadas, o iOS confirma a integridade das mesmas e aplica as políticas definidas pelo perfil de aprovisionamento. São feitas as confirmações seguintes:

- **Integridade do ficheiro de instalação** - o iOS compara os detalhes das aplicações com a chave pública do certificado de assinatura de empresa. Caso sejam diferentes, é possível que o conteúdo das aplicações tenha sido alterado e a aplicação não poderá ser executada.
- **Imposição de capacidades** - o iOS tenta impor as capacidades das aplicações do perfil de aprovisionamento empresarial (não dos perfis de aprovisionamento de programadores individuais) presente no ficheiro de instalação (.ipa) das aplicações.


Geralmente, o certificado de assinatura da empresa que utiliza para assinar as aplicações dura três anos. No entanto, o perfil de aprovisionamento expira após um ano. Enquanto o certificado permanecer válido, o Intune proporciona-lhe as ferramentas para atribuir pró-ativamente uma nova política de perfil de aprovisionamento a dispositivos que tenham aplicações prestes a expirar.
Quando o certificado expirar, tem de voltar a assinar a aplicação com um certificado novo e incorporar um novo perfil de aprovisionamento com a chave desse certificado novo.


## <a name="how-to-create-an-ios-mobile-app-provisioning-profile"></a>Como criar um perfil de aprovisionamento de aplicação móvel de iOS

1. Inicie sessão no portal do Azure.
2. Escolha **Mais Serviços** > **Outros** > **Intune**.
3. No painel **Intune**, escolha **Aplicações móveis**.
1.  Na carga de trabalho **Aplicações móveis**, escolha **Gerir** > **Perfis de aprovisionamento de iOS**.
2.  No painel da lista de perfis, escolha **Criar perfil**.
3. No painel **Criar perfil**, configure os seguintes valores:
    - **Nome** – indique um nome para este perfil de aprovisionamento móvel.
    - **Descrição** - opcionalmente, indique uma descrição para a política.
    - **Carregar ficheiro de perfil** – escolha **Importar** e, em seguida, escolha um ficheiro de Perfil de Configuração Móvel da Apple (com a extensão **.mobileprovision**) que transferiu do site Apple Developer.
4. Quando tiver terminado, escolha **Criar**.

## <a name="next-steps"></a>Próximos passos

Atribua o perfil aos dispositivos iOS necessários. Para obter mais informações, siga os passos em [Como atribuir perfis de dispositivo](../configure-devices/how-to-assign-device-profiles.md).

