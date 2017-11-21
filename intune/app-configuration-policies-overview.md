---
title: "Políticas de configuração de aplicações do Intune | Documentos da Microsoft"
titlesuffix: Azure portal
description: "Saiba como utilizar políticas de configuração de aplicações do Intune."
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 10/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 834B4557-80A9-48C0-A72C-C98F6AF79708
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 406d0faa1e03a41d20c1b584d2d37f9810ddbf32
ms.sourcegitcommit: ce35790090ebe768d5f75c108e8d5934fd19c8c7
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/09/2017
---
# <a name="app-configuration-policies-for-intune"></a>Políticas de configuração de aplicações do Intune

Disponibilize definições quando os utilizadores executarem uma aplicação para iOS ou Android com políticas de configuração de aplicações no Microsoft Intune. Por exemplo, uma aplicação poderá exigir que os utilizadores especifiquem:

- Um número de porta personalizado.
- Definições de idioma.
- Definições de segurança.
- Definições de imagem corporativa, como um logótipo de empresa.

Se os utilizadores introduzirem estas definições incorretamente, isso pode aumentar a carga sobre o suporte técnico e tornar mais lenta a adoção de novas aplicações.

As políticas de configuração de aplicação podem ajudar a eliminar estes problemas, permitindo-lhe atribuir estas definições aos utilizadores de uma política antes de executarem a aplicação. As definições são então fornecidas automaticamente e os utilizadores não têm de executar nenhuma ação.

Não atribua estas políticas diretamente a utilizadores nem a dispositivos. Em alternativa, associe uma política à aplicação e, em seguida, atribua a aplicação. As definições de política são utilizadas sempre que a aplicação as verificar (normalmente, a primeira vez que for executada).

Tem duas opções sobre como utilizar configurações de aplicações com o Intune:
 - **Dispositivos geridos**  
   O dispositivo é gerido pelo Intune como o fornecedor de gestão de dispositivos móveis (MDM).
 - **Aplicações geridas**  
   Uma aplicação é gerida sem inscrição de dispositivos.

## <a name="apps-that-support-app-configuration"></a>Aplicações que suportam a configuração de aplicações

Pode utilizar políticas de configuração de aplicações para aplicações que as suportam. Para suportar a configuração de aplicações no Intune, as aplicações têm de ter sido escritas de forma a suportar a utilização das configurações de aplicações. Consulte o seu fornecedor de aplicações para obter detalhes.

Pode preparar as suas aplicações de linha de negócio ao incorporar o SDK da Aplicação Intune na aplicação ou ao encapsular a aplicação após esta ter sido desenvolvida. O SDK da Aplicação Intune, disponível para iOS e Android, permite à sua aplicação ter políticas de proteção de aplicações do Intune. Esforça-se para reduzir a quantidade de alterações de código necessárias do programador de aplicações. Para obter mais informações, veja [Descrição geral do SDK da Aplicação Intune](app-sdk.md).

## <a name="graph-api-support-for-app-configuration"></a>Suporte da Graph API para configuração de aplicações

Além disso, pode utilizar a Graph API para realizar tarefas de configuração de aplicações. Para obter mais detalhes, veja [Graph API Reference MAM Targeted Config (Configuração de MAM Direcionada de Referência para Graph API)](https://graph.microsoft.io/docs/api-reference/beta/api/intune_mam_targetedmanagedappconfiguration_create).

## <a name="next-steps"></a>Próximos passos

### <a name="managed-devices"></a>Dispositivos geridos

 - Saiba como utilizar a configuração de aplicações com os seus dispositivos iOS.  Veja [Adicionar políticas de configuração de aplicações para dispositivos iOS geridos](app-configuration-policies-use-ios.md).
 - Saiba como utilizar a configuração de aplicações com os seus dispositivos Android.  Veja [Adicionar políticas de configuração de aplicações para dispositivos Android geridos](app-configuration-policies-use-android.md).

### <a name="managed-apps"></a>Aplicações geridas

 - Saiba como utilizar a configuração de aplicações com aplicações geridas. Veja [Add app configuration policies for managed apps without device enrollment (Adicionar políticas de configuração de aplicações para aplicações geridas sem inscrição de dispositivos)](app-configuration-policies-managed-app.md).