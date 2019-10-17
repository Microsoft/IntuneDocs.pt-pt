---
title: Política do Microsoft Intune para permitir/bloquear aplicações do Samsung Knox
titleSuffix: ''
description: Crie um perfil personalizado para permitir e bloquear aplicações para dispositivos Samsung Knox Standard.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/5/2018
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: afaee427b593cfaed957279b520765242a1aacd3
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72506643"
---
# <a name="use-custom-policies-in-microsoft-intune-to-allow-and-block-apps-for-samsung-knox-standard-devices"></a>Utilizar políticas personalizadas no Microsoft Intune para permitir e bloquear aplicações para dispositivos Samsung Knox Standard 

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Utilize o procedimento neste artigo para criar uma política personalizada do Microsoft Intune que crie um dos seguintes casos:

- Uma lista de aplicações que estão bloqueadas de executar no dispositivo. A execução das aplicações nesta lista está bloqueada, mesmo se já tiverem sido instaladas quando a política foi aplicada.
- Uma lista de aplicações que os utilizadores do dispositivo estão autorizados a instalar a partir da loja Google Play. Apenas as aplicações na lista podem ser instaladas. Mais nenhuma outra aplicação pode ser instalada a partir da loja.

Estas definições só podem ser utilizadas por dispositivos com o Samsung Knox Standard.

## <a name="create-an-allowed-or-blocked-app-list"></a>Criar uma lista de aplicações permitidas ou bloqueadas

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. No painel **Intune**, selecione **Configuração do dispositivo**.
2. No painel **Configuração do dispositivo**, selecione **Gerir** > **Perfis**.
2. No painel da lista de perfis, selecione **Criar perfil**.
3. No painel **Criar perfil**, introduza um **Nome** e uma **Descrição** opcional para este perfil de dispositivo.
2. Selecione uma **Plataforma** de **Android** e um **Tipo de perfil** de **Personalizado**.
3. Clique em **Definições**.
3. No painel **Definições OMA-URI personalizadas**, selecione **Adicionar**.
4. Na caixa de diálogo **Adicionar ou Editar Definição OMA-URI**, especifique as seguintes definições:

   Para uma lista de aplicações que estão impedidas de executar no dispositivo:

   - **Nome** – Introduza **PreventStartPackages**.
   - **Descrição** – Introduza uma descrição opcional, como “Lista de aplicações cuja execução está bloqueada”.
   - **Tipo de dados** – Na lista pendente, escolha **Cadeia**.
   - **OMA-URI** – Introduza **./Vendor/MSFT/PolicyManager/My/ApplicationManagement/PreventStartPackages**
   - **Valor** – Introduza uma lista de nomes de pacotes de aplicações que pretende permitir. Pode utilizar **; : ,** ou **|** como delimitador. (Exemplo: pacote1;pacote2;)

   Para uma lista de aplicações que os utilizadores têm permissão para instalar a partir da Google Play Store, excluindo todas as outras aplicações:
   - **Nome** – Introduza **AllowInstallPackages**.
   - **Descrição** – Introduza uma descrição opcional, como “Lista de aplicações que os utilizadores podem instalar a partir do Google Play”.
   - **Tipo de dados** – Na lista pendente, escolha **Cadeia**.
   - **OMA-URI** – Introduza **./Vendor/MSFT/PolicyManager/My/ApplicationManagement/AllowInstallPackages**
   - **Valor** – Introduza uma lista de nomes de pacotes de aplicações que pretende permitir. Pode utilizar **; : ,** ou **|** como delimitador. (Exemplo: pacote1;pacote2;)

4. Clique em **OK** e, em seguida, no painel **Criar Perfil**, selecione **Criar**.

>[!TIP]
> Pode localizar o ID do pacote de uma aplicação ao navegar para a aplicação na Google Play Store. O ID do pacote está contido no URL da página da aplicação. Por exemplo, o ID do pacote da aplicação Microsoft Word é **com.microsoft.office.word**.

Da próxima vez que cada dispositivo visado iniciar sessão, serão aplicadas as definições da aplicação.


<!---## Assign the custom profile--->