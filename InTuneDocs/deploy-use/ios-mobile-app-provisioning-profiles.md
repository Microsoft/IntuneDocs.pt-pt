---
title: "Perfis de aprovisionamento de aplicações | Microsoft Intune"
description: "O Intune proporciona-lhe as ferramentas para implementar proativamente uma nova política de perfil de aprovisionamento em dispositivos que tenham aplicações prestes a expirar."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 07/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 86fbe736-7bdb-4f5e-ae21-13c91eb2462c
ms.reviewer: mghadial
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 409433dbe5ca777b33b21a2655e15cde8003b4a2
ms.openlocfilehash: d67b26b23e65d4a144c1efda1494de1df94cc33c


---

# <a name="use-ios-mobile-provisioning-profile-policies-to-prevent-your-apps-from-expiring"></a>Utilizar políticas de perfil de aprovisionamento móvel de iOS para impedir as aplicações de expirar


As aplicações de linha de negócio iOS da Apple implementadas em iPhones e iPads são criadas com um perfil de aprovisionamento incluído e o respetivo código assinado com um certificado. Quando as aplicações são executadas, o iOS confirma a integridade das mesmas e aplica as políticas definidas pelo perfil de aprovisionamento. São feitas as confirmações seguintes:

- **Integridade do ficheiro de instalação** - o iOS compara os detalhes das aplicações com a chave pública do certificado de assinatura de empresa. Caso sejam diferentes, é possível que o conteúdo das aplicações tenha sido alterado e a aplicação não poderá ser executada.
- **Imposição de capacidades** - o iOS tenta impor as capacidades das aplicações do perfil de aprovisionamento empresarial (não dos perfis de aprovisionamento de programadores individuais) presente no ficheiro de instalação (.ipa) das aplicações.


Geralmente, o certificado de assinatura da empresa que utiliza para assinar as aplicações dura três anos. No entanto, o perfil de aprovisionamento expira após um ano. Enquanto o certificado permanecer válido, o Intune proporciona-lhe as ferramentas para implementar proativamente uma nova política de perfil de aprovisionamento em dispositivos que tenham aplicações prestes a expirar.
Quando o certificado expirar, tem de voltar a assinar a aplicação com um certificado novo e incorporar um novo perfil de aprovisionamento com a chave desse certificado novo.



## <a name="how-to-find-out-when-a-line-of-business-app-will-expire"></a>Como saber quando uma aplicação de linha de negócio vai expirar

1. Na [consola de administração do Microsoft Intune](https://manage.microsoft.com), escolha **Aplicações** > **Aplicações**.
2. Na lista de aplicações, veja a coluna **Data de expiração** para ver a data de expiração da aplicação. Também pode definir a lista pendente **Filtros** como **Expirada/prestes a expirar** para ver apenas as aplicações que requerem medidas.

## <a name="how-to-create-an-ios-mobile-provisioning-profile-policy"></a>Como criar uma política de perfil de aprovisionamento móvel de iOS


1. Na [consola de administração do Microsoft Intune](https://manage.microsoft.com), escolha **Política** > **Descrição Geral** > **Adicionar Política**.
2. Na caixa de diálogo **Criar uma Nova Política**, escolha **iOS** > **Política de Perfil de Aprovisionamento Móvel** e, em seguida, escolha **Criar Política**.
3. Na página **Geral**, configure os valores seguintes:
    - **Nome** - indique um nome para esta política de perfil de aprovisionamento móvel.
    - **Descrição** - opcionalmente, indique uma descrição para a política.
    - **Ficheiro de perfil de configuração** -clique em **Importar** e em seguida, escolha um ficheiro de Perfil de Configuração Móvel da Apple (com a extensão **.mobileprovision**) que transferiu a partir do Web site Apple Developer (Programador Apple).
4. Quando terminar, escolha **Guardar Política**.
5. Agora, implemente a política nos dispositivos iOS necessários. Para obter mais informações, veja [Gerir definições e funcionalidades nos seus dispositivos com as políticas do Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).



<!--HONumber=Dec16_HO2-->


