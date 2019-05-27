---
title: Adicionar definições personalizadas para dispositivos Windows Phone 8.1 no Microsoft Intune – Azure | Microsoft Docs
titleSuffix: ''
description: Adicione ou crie um perfil personalizado para utilizar as definições OMA-URI para dispositivos com o Windows Phone 8.1 no Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/24/2018
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: cb54f5e4cede6141c87073a7dfb6570cf85e920b
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/23/2019
ms.locfileid: "66042884"
---
# <a name="use-custom-settings-for-windows-phone-81-devices-in-intune"></a>Utilizar definições personalizadas para dispositivos Windows Phone 8.1 no Intune

Ao utilizar o Microsoft Intune, pode adicionar ou criar definições personalizadas para os seus dispositivos Windows Phone 8.1 com "perfis personalizados". Os perfis personalizados são uma funcionalidade do Intune. Foram concebidos para adicionar definições e funcionalidades de dispositivos que não estão incorporadas Intune.

Os perfis personalizados do Windows Phone 8.1 utilizam definições Open Mobile Alliance Uniform Resource Identifier (OMA-URI) para configurar diferentes funcionalidades. Estas definições são normalmente utilizadas por fabricantes de dispositivos móveis para controlar as funcionalidades no dispositivo.

Este artigo mostra-lhe como criar um perfil personalizado para dispositivos Windows Phone 8.1. 

## <a name="create-the-profile"></a>Criar o perfil

1. No [portal do Azure](https://portal.azure.com), selecione **Todos os serviços**, filtre o **Intune** e selecione **Microsoft Intune**.
2. Selecione **Configuração do dispositivo** > **Perfis** > **Criar perfil**.
3. Introduza as seguintes definições:

    - **Nome**: Introduza um nome para o perfil, como `windows phone custom profile`.
    - **Descrição**: introduza uma descrição para o perfil.
    - **Plataforma**: Choose **Windows Phone 8.1**.
    - **Tipo de perfil**: Escolher **personalizado**.

4. Em **Definições OMA-URI Personalizadas**, selecione **Adicionar**. Introduza as seguintes definições:

    - **Nome**: Introduza um nome exclusivo para a definição OMA-URI para o ajudar a identificá-la na lista de definições.
    - **Descrição**: Introduza uma descrição que proporcione uma descrição geral da definição e outras informações relevantes para o ajudar a localizar o perfil.
    - **OMA-URI** (sensível a maiúsculas e minúsculas): Introduza o OMA-URI que pretende utilizar como uma definição.
    - **Tipo de dados**: Escolha o tipo de dados que irá utilizar para esta definição de OMA-URI. As opções são:

        - Cadeia
        - Cadeia (ficheiro XML)
        - Data e Hora
        - Número inteiro
        - Vírgula flutuante
        - Booleano
        - Base64 (ficheiro)

    - **Valor**: Introduza o valor de dados que pretende associar ao OMA-URI que introduziu. O valor depende do tipo de dados que selecionou. Por exemplo, se optar por **Data e hora**, selecione o valor num seletor de datas.

    Depois de adicionar algumas definições, pode selecionar **Exportar**. A opção **Exportar** cria uma lista de todos os valores que adicionou num ficheiro de valores separados por vírgulas (.csv).

5. Selecione **OK** para guardar as alterações. Continue a adicionar mais definições conforme necessário.
6. Quanto terminar, selecione **OK** > **Criar** para criar o perfil do Intune. Depois de criado, o perfil é apresentado na lista **Configuração do dispositivo – Perfis**.

## <a name="next-steps"></a>Passos Seguintes

O perfil está criado, mas ainda não está ativo. Em seguida, [atribua o perfil](device-profile-assign.md).

Saiba como criar um perfil personalizado em [dispositivos Windows 10](custom-settings-windows-10.md).
