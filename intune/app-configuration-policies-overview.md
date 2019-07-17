---
title: Políticas de configuração de aplicações para o Microsoft Intune
titleSuffix: ''
description: Saiba como utilizar políticas de configuração de aplicações num dispositivo iOS ou Android no Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/08/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 834B4557-80A9-48C0-A72C-C98F6AF79708
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1e5ddf39a201f1a70f997e03f0b65706853adefa
ms.sourcegitcommit: 7c251948811b8b817e9fe590b77f23aed95b2d4e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/15/2019
ms.locfileid: "67885124"
---
# <a name="app-configuration-policies-for-microsoft-intune"></a>Políticas de configuração de aplicações para o Microsoft Intune

Utilize políticas de configuração de aplicações no Microsoft Intune para disponibilizar definições de configuração para uma aplicação para iOS ou Android. Essas definições de configuração permitem que um aplicativo seja personalizado usando uma abordagem padrão do setor para configuração e gerenciamento de aplicativos. As definições de políticas de configuração são utilizadas quando a aplicação as procura, normalmente quando é executada pela primeira vez.

Pode atribuir uma política de configuração de aplicações a um grupo de utilizadores e dispositivos através de uma combinação de atribuições de inclusão e exclusão. Depois de adicionar uma política de configuração da aplicação, pode definir as atribuições dessa política. Quando definir as atribuições da política, poderá optar por incluir e excluir os grupos de utilizadores aos quais a política será aplicada. Quando escolher incluir um ou mais grupos, poderá optar por selecionar grupos específicos para incluir ou selecionar grupos incorporados. Os grupos incorporados incluem **Todos os Utilizadores**, **Todos os Dispositivos** e **Todos os Utilizadores + Todos os Dispositivos**.

Uma configuração de aplicativo, por exemplo, pode exigir que você especifique qualquer um dos seguintes detalhes:

- Um número de porta personalizado
- Definições de idioma
- Definições de segurança
- Definições de imagem corporativa tal como um logótipo de empresa

Se os usuários fossem inserir essas configurações em vez disso, eles poderiam fazer isso incorretamente, o que poderia aumentar a carga de seu suporte técnico e reduzir a adoção de novos aplicativos.

As políticas de configuração de aplicativo podem ajudá-lo a eliminar problemas de configuração de aplicativo, permitindo que você atribua configurações de configuração a uma política atribuída aos usuários antes que eles executem o aplicativo. As definições são então fornecidas automaticamente e os utilizadores não têm de executar nenhuma ação.

As definições de configuração são utilizadas sempre que a aplicação as procurar. Normalmente, uma aplicação procura as definições de configuração quando é executada pelo utilizador pela primeira vez.

Tem duas opções sobre como utilizar configurações de aplicações com o Intune:
- **Dispositivos geridos** – o dispositivo é gerido pelo Intune como o fornecedor de gestão de dispositivos móveis (MDM).
- **Aplicações geridas** – uma aplicação é gerida sem inscrição do dispositivo.

> [!NOTE]
> Enquanto administrador do Microsoft Intune, pode controlar as contas de utilizadores que são adicionadas a aplicações do Microsoft Office em dispositivos geridos. Pode limitar o acesso exclusivamente a contas de utilizadores autorizadas e bloquear contas pessoais em dispositivos inscritos. As aplicações de apoio processam a configuração da aplicação e removem e bloqueiam contas não aprovadas.

## <a name="apps-that-support-app-configuration"></a>Aplicações que suportam a configuração de aplicações

### <a name="managed-devices"></a>Dispositivos geridos
Pode utilizar políticas de configuração de aplicações para aplicações que as suportam. Para dar suporte à configuração de aplicativo no Intune, os aplicativos devem ter sido escritos para dar suporte ao uso de configurações de aplicativo, conforme definido pela [comunidade AppConfig](https://www.appconfig.org/members). Consulte o seu fornecedor de aplicações para obter detalhes.

### <a name="managed-apps"></a>Aplicações geridas
Pode preparar as suas aplicações de linha de negócio ao incorporar o SDK da Aplicação Intune na aplicação ou ao encapsular a aplicação após esta ter sido desenvolvida. O SDK de aplicativos do Intune, disponível para iOS e Android, habilita seu aplicativo para as políticas de configuração de proteção de aplicativo do Intune. Esforça-se para reduzir a quantidade de alterações de código necessárias do programador de aplicações. Para obter mais informações, veja [Descrição geral do SDK da Aplicação Intune](app-sdk.md).

## <a name="graph-api-support-for-app-configuration"></a>Suporte da Graph API para configuração de aplicações

Além disso, pode utilizar a Graph API para realizar tarefas de configuração de aplicações. Para obter mais detalhes, veja [Graph API Reference MAM Targeted Config (Configuração de MAM Direcionada de Referência para Graph API)](https://graph.microsoft.io/docs/api-reference/beta/api/intune_mam_targetedmanagedappconfiguration_create).

## <a name="next-steps"></a>Passos Seguintes

### <a name="managed-devices"></a>Dispositivos geridos

- Saiba como utilizar a configuração de aplicações com os seus dispositivos iOS.  Consulte [Adicionar políticas de configuração de aplicativo para dispositivos IOS gerenciados](app-configuration-policies-use-ios.md).
- Saiba como utilizar a configuração de aplicações com os seus dispositivos Android.  Veja [Adicionar políticas de configuração de aplicações para dispositivos Android geridos](app-configuration-policies-use-android.md).

### <a name="managed-apps"></a>Aplicações geridas

- Saiba como utilizar a configuração de aplicações com aplicações geridas. Veja [Add app configuration policies for managed apps without device enrollment (Adicionar políticas de configuração de aplicações para aplicações geridas sem inscrição de dispositivos)](app-configuration-policies-managed-app.md).
