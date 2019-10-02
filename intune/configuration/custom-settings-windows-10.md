---
title: Adicionar definições personalizadas para dispositivos Windows 10 no Microsoft Intune – Azure | Microsoft Docs
description: Adicione ou crie um perfil personalizado para utilizar as definições OMA-URI para dispositivos com o Windows 10 no Microsoft Intune. Utilize um perfil personalizado para adicionar definições personalizadas.
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
ms.openlocfilehash: 51ee389351dd0ccccf69f01e932f7374ca38b03b
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71730880"
---
# <a name="use-custom-settings-for-windows-10-devices-in-intune"></a>Utilizar definições personalizadas para dispositivos Windows 10 no Intune

Ao utilizar o Microsoft Intune, pode adicionar ou criar definições personalizadas para os seus dispositivos Windows 10 com "perfis personalizados". Os perfis personalizados são uma funcionalidade do Intune. Foram concebidos para adicionar definições e funcionalidades de dispositivos que não estão incorporadas Intune.

Os perfis personalizados do Windows 10 utilizam definições Open Mobile Alliance Uniform Resource Identifier (OMA-URI) para configurar diferentes funcionalidades. Estas definições são normalmente utilizadas por fabricantes de dispositivos móveis para controlar as funcionalidades no dispositivo. 

O Windows 10 disponibiliza diversas definições do Fornecedor de Serviços de Configuração (CSP), tal como o [Fornecedor de Serviços de Configuração de Políticas (CSP de Políticas)](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers).

Se estiver à procura de uma definição específica, lembre-se de que o [perfil de restrição de dispositivos Windows 10](device-restrictions-windows-10.md) inclui várias definições incorporadas. Por isso, poderá não ter de introduzir valores personalizados.

Este artigo apresenta o seguinte:

- Como criar um perfil personalizado para dispositivos Windows 10
- Uma lista de definições OMA-URI recomendadas
- Um exemplo de um perfil personalizado que abre uma ligação VPN

## <a name="create-the-profile"></a>Criar o perfil

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Selecione **Configuração do dispositivo** > **Perfis** > **Criar perfil**.
3. Introduza as seguintes definições:

    - **Nome**: Insira um nome para o perfil, como `windows 10 custom profile`.
    - **Descrição**: introduza uma descrição para o perfil.
    - **Plataforma**: Escolha **Windows 10 e posterior**.
    - **Tipo de perfil**: Escolha **personalizado**.

4. Em **Definições OMA-URI Personalizadas**, selecione **Adicionar**. Introduza as seguintes definições:

    - **Nome**: Introduza um nome exclusivo para a definição OMA-URI para o ajudar a identificá-la na lista de definições.
    - **Descrição**: Insira uma descrição que dê uma visão geral da configuração e quaisquer outros detalhes importantes.
    - **OMA-URI** (diferencia maiúsculas de minúsculas): Insira o OMA-URI que você deseja usar como uma configuração.
    - **Tipo de dados**: Escolha o tipo de dados que você usará para essa configuração de OMA-URI. As opções são:

        - Cadeia
        - Cadeia (ficheiro XML)
        - Data e Hora
        - Número inteiro
        - Vírgula flutuante
        - Booleano
        - Base64 (ficheiro)

    - **Valor**: Insira o valor de dados que você deseja associar ao OMA-URI que você inseriu. O valor depende do tipo de dados que selecionou. Por exemplo, se optar por **Data e hora**, selecione o valor num seletor de datas.

    Depois de adicionar algumas definições, pode selecionar **Exportar**. A opção **Exportar** cria uma lista de todos os valores que adicionou num ficheiro de valores separados por vírgulas (.csv).

5. Selecione **OK** para guardar as alterações. Continue a adicionar mais definições conforme necessário.
6. Quanto terminar, selecione **OK** > **Criar** para criar o perfil do Intune. Depois de criado, o perfil é apresentado na lista **Configuração do dispositivo – Perfis**.

## <a name="example"></a>Exemplo

No seguinte exemplo, a definição **Conectividade/PermitirVPNAtravésDeRedeMóvel** está ativada. Esta definição permite que um dispositivo com o Windows 10 abra uma ligação VPN através de uma rede móvel.

![Exemplo de uma política personalizada que contém as definições de VPN](./media/custom-settings-windows-10/custom-policy-example.png)

## <a name="find-the-policies-you-can-configure"></a>Encontrar as políticas que pode configurar

Está disponível uma lista completa de todos os fornecedores de serviços de configuração (CSPs) suportados pelo Windows 10 na [Configuration service provider reference](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference) (Referência de fornecedores de serviços de configuração).

Nem todas as definições são compatíveis com todas as versões do Windows 10. O artigo [Configuration service provider reference](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference) (Referência de fornecedores de serviços de configuração) indica-lhe que versões são suportadas para cada CSP.

Além disso, o Intune não suporta todas as definições apresentadas na [Configuration service provider reference](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference) (Referência de fornecedores de serviços de configuração). Para saber se o Intune suporta a definição que pretende, abra o artigo referente a essa definição. Cada página de definição mostra a respetiva operação suportada. Para trabalhar com o Intune, a configuração deve dar suporte às operações **Adicionar**, **substituir**e **obter** . Se o valor retornado pela operação **Get** não corresponder ao valor fornecido pelas operações de **adição** ou **substituição** , o Intune relatará um erro de conformidade.

## <a name="next-steps"></a>Passos seguintes

O perfil está criado, mas ainda não está ativo. Em seguida, [atribua o perfil](device-profile-assign.md).
