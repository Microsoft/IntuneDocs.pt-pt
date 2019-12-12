---
title: Adicionar definições personalizadas para dispositivos Windows Phone 8.1 no Microsoft Intune – Azure | Microsoft Docs
titleSuffix: ''
description: Adicione ou crie um perfil personalizado para utilizar as definições OMA-URI para dispositivos com o Windows Phone 8.1 no Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/25/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a1362f6c6453569d1c306cd16397cc9a7f83736e
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72495342"
---
# <a name="use-custom-settings-for-windows-phone-81-devices-in-intune"></a>Utilizar definições personalizadas para dispositivos Windows Phone 8.1 no Intune

Ao utilizar o Microsoft Intune, pode adicionar ou criar definições personalizadas para os seus dispositivos Windows Phone 8.1 com "perfis personalizados". Os perfis personalizados são uma funcionalidade do Intune. Foram concebidos para adicionar definições e funcionalidades de dispositivos que não estão incorporadas Intune.

Os perfis personalizados do Windows Phone 8.1 utilizam definições Open Mobile Alliance Uniform Resource Identifier (OMA-URI) para configurar diferentes funcionalidades. Estas definições são normalmente utilizadas por fabricantes de dispositivos móveis para controlar as funcionalidades no dispositivo. [Windows Phone documentação do protocolo MDM do 8,1](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-phone/dn499787(v=technet.10)) lista as configurações.

Este artigo mostra-lhe como criar um perfil personalizado para dispositivos Windows Phone 8.1. 

## <a name="create-the-profile"></a>Criar o perfil

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Selecione **Configuração do dispositivo** > **Perfis** > **Criar perfil**.
3. Introduza as seguintes definições:

    - **Nome**: introduza um nome para o perfil, como `windows phone custom profile`.
    - **Descrição:** introduza uma descrição para o perfil.
    - **Plataforma**: selecione **Windows Phone 8.1**.
    - **Tipo de perfil**: selecione **Personalizado**.

4. Em **Definições OMA-URI Personalizadas**, selecione **Adicionar**. Introduza as seguintes definições:

    - **Nome** – introduza um nome exclusivo para a definição OMA-URI para o ajudar a identificá-la na lista de definições.
    - **Descrição**: introduza uma descrição geral da definição e quaisquer outras informações relevantes para o ajudar a localizar o perfil.
    - **OMA-URI** (sensível a maiúsculas e minúsculas): introduza a definição OMA-URI que pretende utilizar.
    - **Tipo de dados**: selecione o tipo de dados que irá utilizar para esta definição OMA-URI. As opções são:

        - Cadeia
        - Cadeia (ficheiro XML)
        - Data e Hora
        - Número inteiro
        - Vírgula flutuante
        - Booleano
        - Base64 (ficheiro)

    - **Valor**: introduza o valor de dados que pretende associar à definição OMA-URI que introduziu. O valor depende do tipo de dados que selecionou. Por exemplo, se optar por **Data e hora**, selecione o valor num seletor de datas.

    Depois de adicionar algumas definições, pode selecionar **Exportar**. A opção **Exportar** cria uma lista de todos os valores que adicionou num ficheiro de valores separados por vírgulas (.csv).

5. Selecione **OK** para guardar as alterações. Continue a adicionar mais definições conforme necessário.
6. Quanto terminar, selecione **OK** > **Criar** para criar o perfil do Intune. Depois de criado, o perfil é apresentado na lista **Configuração do dispositivo – Perfis**.

## <a name="example"></a>Exemplo

No exemplo a seguir, Windows 8.1 dispositivos telefônicos são impedidos de alterar redes de celular quando viajam fora da área de cobertura da operadora.

- **Nome**: permitir roaming de dados de celular
- **Descrição**: permitir ou não permitir roaming de dados de celular
- **OMA-URI** (diferencia maiúsculas de minúsculas):./Vendor/MSFT/PolicyManager/My/Connectivity/AllowCellularDataRoaming
- **Tipo de dados**: inteiro
- **Valor**: 0

## <a name="next-steps"></a>Próximos passos

O perfil está criado, mas ainda não está ativo. Em seguida, [atribua o perfil](device-profile-assign.md).

Saiba como criar um perfil personalizado em [dispositivos Windows 10](../custom-settings-windows-10.md).
