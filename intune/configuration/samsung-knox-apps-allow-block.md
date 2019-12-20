---
title: Política do Microsoft Intune para permitir/bloquear aplicações do Samsung Knox
titleSuffix: ''
description: Crie um perfil personalizado para permitir e bloquear aplicações para dispositivos Samsung Knox Standard.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/18/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4b83a0339d87375502159467af323fceae5eb6e2
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/19/2019
ms.locfileid: "75207082"
---
# <a name="use-custom-policies-in-microsoft-intune-to-allow-and-block-apps-for-samsung-knox-standard-devices"></a>Utilizar políticas personalizadas no Microsoft Intune para permitir e bloquear aplicações para dispositivos Samsung Knox Standard 

Utilize o procedimento neste artigo para criar uma política personalizada do Microsoft Intune que crie um dos seguintes casos:

- Uma lista de aplicações que estão bloqueadas de executar no dispositivo. A execução das aplicações nesta lista está bloqueada, mesmo se já tiverem sido instaladas quando a política foi aplicada.
- Uma lista de aplicações que os utilizadores do dispositivo estão autorizados a instalar a partir da loja Google Play. Apenas as aplicações na lista podem ser instaladas. Mais nenhuma outra aplicação pode ser instalada a partir da loja.

Estas definições só podem ser utilizadas por dispositivos com o Samsung Knox Standard.

## <a name="create-an-allowed-or-blocked-app-list"></a>Criar uma lista de aplicações permitidas ou bloqueadas

1. Entre no centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selecione **dispositivos** > **perfis de configuração** > **Criar perfil**.
3. Introduza as seguintes definições:

    - **Nome**: Insira um nome descritivo para o perfil. Atribua nomes aos perfis de forma que possa identificá-los facilmente mais tarde. Por exemplo, um bom nome de perfil é o **perfil personalizado do Windows Phone**.
    - **Descrição**: introduza uma descrição que lhe permita obter uma descrição geral da definição e outros detalhes importantes.
    - **Plataforma**: selecione **Android**.
    - **Tipo de perfil**: selecione **personalizado**.

4. Em **Definições OMA-URI Personalizadas**, selecione **Adicionar**. Introduza as seguintes definições:

    Para uma lista de aplicações que estão impedidas de executar no dispositivo:

    - **Nome**: insira **PreventStartPackages**.
    - **Descrição**: introduza uma descrição geral da definição e quaisquer outras informações relevantes para o ajudar a localizar o perfil. Por exemplo, insira a **lista de aplicativos que estão impedidos de serem executados**.
    - **OMA-URI** (diferencia maiúsculas de minúsculas): Enter **./Vendor/MSFT/PolicyManager/My/ApplicationManagement/PreventStartPackages**.
    - **Tipo de dados**: selecione **cadeia de caracteres**.
    - **Valor**: Insira uma lista dos nomes de pacote de aplicativo que você deseja permitir. Você pode usar `;`, `:`ou `|` como um delimitador. Por exemplo, introduza `package1;package2;`.

   Para uma lista de aplicações que os utilizadores têm permissão para instalar a partir da Google Play Store, excluindo todas as outras aplicações:

    - **Nome**: insira **AllowInstallPackages**.
    - **Descrição**: Insira uma descrição que dê uma visão geral da configuração e quaisquer outras informações relevantes para ajudá-lo a localizar o perfil. Por exemplo, insira a **lista de aplicativos que os usuários podem instalar de Google Play**.
    - **OMA-URI** (diferencia maiúsculas de minúsculas): Enter **./Vendor/MSFT/PolicyManager/My/ApplicationManagement/AllowInstallPackages**.
    - **Tipo de dados**: selecione **cadeia de caracteres**.
    - **Valor**: Insira uma lista dos nomes de pacote de aplicativo que você deseja permitir. Você pode usar `;`, `:`ou `|` como um delimitador. Por exemplo, introduza `package1;package2;`.

5. Selecione **OK** para guardar as alterações.
6. Quando terminar, selecione **OK** > **criar** para criar o perfil do Intune. Ao concluir, seu perfil é mostrado na lista **dispositivos – perfis de configuração** .

>[!TIP]
> Pode localizar o ID do pacote de uma aplicação ao navegar para a aplicação na Google Play Store. O ID do pacote está contido no URL da página da aplicação. Por exemplo, o ID do pacote da aplicação Microsoft Word é **com.microsoft.office.word**.

Na próxima vez em que cada dispositivo de destino fizer check-in, as configurações do aplicativo serão aplicadas.

## <a name="next-steps"></a>Próximos passos

O perfil está criado, mas ainda não está ativo. Em seguida, [atribua o perfil](../device-profile-assign.md) e [monitorize o estado](device-profile-monitor.md).
