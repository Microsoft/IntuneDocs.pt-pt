---
title: "Política do Intune para permitir/bloquear aplicações do Samsung KNOX"
titleSuffix: Intune Azure preview
description: "Pré-visualização do Azure no Intune: crie um perfil personalizado para permitir e bloquear aplicações para dispositivos Samsung KNOX Standard."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d035ebf5-85f4-4001-a249-75d24325061a
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: ca4f1adc5704ecd66d2af7823f95ca63ec20469e
ms.openlocfilehash: a47ea4c8d3027cb34fd8ecd8324fac52c9846a77
ms.contentlocale: pt-pt
ms.lasthandoff: 03/17/2017



---
# <a name="use-custom-policies-to-allow-and-block-apps-for-samsung-knox-standard-devices-in-microsoft-intune"></a>Utilizar políticas personalizadas para permitir e bloquear aplicações para dispositivos Samsung KNOX Standard no Microsoft Intune
[!INCLUDE[azure_preview](../includes/azure_preview.md)] Utilize os procedimentos deste tópico para criar uma política personalizada do Microsoft Intune que cria um dos seguintes casos:

- Uma lista de aplicações que estão bloqueadas de executar no dispositivo. A execução das aplicações nesta lista está bloqueada, mesmo se já tiverem sido instaladas quando a política foi aplicada.
- Uma lista de aplicações que os utilizadores do dispositivo estão autorizados a instalar a partir da loja Google Play. Apenas as aplicações na lista podem ser instaladas. Mais nenhuma outra aplicação pode ser instalada a partir da loja.

Estas definições só podem ser utilizadas por dispositivos que executem Samsung KNOX Standard.

## <a name="create-an-allowed-or-blocked-app-list"></a>Criar uma lista de aplicações permitidas ou bloqueadas

1. Inicie sessão no portal do Azure.
2. Escolha **Mais Serviços** > **Outros** > **Intune**.
3. No painel **Intune**, escolha **Configuração do dispositivo**.
2. No painel **Configuração do Dispositivo**, escolha **Gerir** > **Perfis**.
2. No painel da lista de perfis, escolha **Criar Perfil**.
3. No painel **Criar Perfil**, introduza um **Nome** e uma **Descrição** opcional para este perfil de dispositivo.
2. Escolha um **Tipo de plataforma** de **Android** e um Tipo de perfil de **Personalizado**.
3. Clique em **Definições**.
3. No painel **Definições de OMA-URI personalizadas**, escolha **Adicionar**.
4. Na caixa de diálogo **Adicionar ou Editar Definição OMA-URI**, especifique o seguinte:

### <a name="for-a-list-of-apps-that-are-blocked-from-running-on-the-device"></a>Para uma lista de aplicações que estão impedidas de executar no dispositivo:

- **Nome** – Introduza **PreventStartPackages**.
- **Descrição** – Introduza uma descrição opcional, como “Lista de aplicações cuja execução está bloqueada”.
-     **Tipo de dados** – Na lista pendente, escolha **Cadeia**.
-     **OMA-URI** – Introduza **./Vendor/MSFT/PolicyManager/My/ApplicationManagement/PreventStartPackages**
-     **Valor** – Introduza uma lista de nomes de pacotes de aplicações que pretende permitir. Pode utilizar **; : ,** ou **|** como delimitador. (Exemplo: pacote1;pacote2;)

### <a name="for-a-list-of-apps-that-users-are-allowed-to-install-from-the-google-play-store-while-excluding-all-other-apps"></a>Para uma lista de aplicações que os utilizadores têm permissão para instalar a partir da Google Play Store, excluindo todas as outras aplicações:
- **Nome** – Introduza **AllowInstallPackages**.
- **Descrição** – Introduza uma descrição opcional, como “Lista de aplicações que os utilizadores podem instalar a partir do Google Play”.
- **Tipo de dados** – Na lista pendente, escolha **Cadeia**.
- **OMA-URI** – Introduza **./Vendor/MSFT/PolicyManager/My/ApplicationManagement/AllowInstallPackages**
- **Valor** – Introduza uma lista de nomes de pacotes de aplicações que pretende permitir. Pode utilizar **; : ,** ou **|** como delimitador. (Exemplo: pacote1;pacote2;)

4. Clique em **OK** e, em seguida, no painel **Criar Perfil**, escolha **Criar**.

>[!TIP]
> Pode localizar o ID do pacote de uma aplicação ao navegar para a aplicação na Google Play Store. O ID do pacote está contido no URL da página da aplicação. Por exemplo, o ID do pacote da aplicação Microsoft Word é **com.microsoft.office.word**.

Da próxima vez que cada dispositivo visado iniciar sessão, serão aplicadas as definições da aplicação.


<!---## Assign the custom profile--->

