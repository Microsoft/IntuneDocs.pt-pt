---
title: Definições personalizadas para dispositivos com o Windows 10 no Microsoft Intune – Azure | Microsoft Docs
description: Configure definições OMA-URI personalizadas em dispositivos a executar o Windows 10 com um perfil personalizado no Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 6/18/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: bdbb6643a4ee8aace0db22cd7f9189f7ac6445f0
ms.sourcegitcommit: ada99fefe9a612ed753420116f8c801ac4bf0934
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36232831"
---
# <a name="custom-oma-uri-settings-for-windows-10-devices---intune"></a>Definições OMA-URI personalizadas para dispositivos com o Windows 10 – Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Utilize o perfil **personalizado** do Microsoft Intune para Windows 10 e Windows 10 Mobile para implementar definições OMA-URI (Open Mobile Alliance Uniform Resource Identifier). Estas definições são utilizadas para controlar funcionalidades em dispositivos. O Windows 10 disponibiliza diversas definições do Fornecedor de Serviços de Configuração (CSP), tal como o [Fornecedor de Serviços de Configuração de Políticas (CSP de Políticas)](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers).

Se procura uma definição específica, lembre-se de que o [perfil de restrição de dispositivos do Windows 10](device-restrictions-windows-10.md) contém diversas definições incorporadas no Intune e que não necessitam de valores personalizados.

## <a name="configure-custom-settings"></a>Configurar definições personalizadas

1. Crie um novo perfil de configuração com o tipo de perfil **Personalizado**. O artigo [Como configurar definições de dispositivos personalizadas](custom-settings-configure.md) indica os passos.
2. Em **Definições OMA-URI Personalizadas**, selecione **Adicionar** para criar uma nova definição. Também pode clicar em **Exportar** para criar uma lista de todos os valores que configurou num ficheiro de valores separados por vírgulas (.csv).
3. Para cada definição OMA-URI que pretende adicionar, introduza as informações seguintes:

- **Nome** – introduza um nome exclusivo para a definição OMA-URI para o ajudar a identificá-la na lista de definições.
- **Descrição** – opcionalmente, introduza uma descrição para a definição.
- **OMA-URI (sensível às maiúsculas e minúsculas)**: introduza o OMA-URI para o qual pretende proporcionar uma definição.
- **Tipo de dados**: escolha entre:
  - **Cadeia**
  - **Cadeia (XML)**
  - **Data e hora**
  - **Número inteiro**
  - **Vírgula flutuante**
  - **Booleano**
  - **Base64**
- **Valor**– introduza o valor ou ficheiro a associar à definição OMA-URI que introduziu.

4. Quando tiver concluído, selecione **OK**. Em **Criar perfil** selecione  **Criar**. O perfil é criado e é apresentado na lista de perfis.

## <a name="example"></a>Exemplo
No seguinte exemplo, a definição **Conectividade/PermitirVPNAtravésDeRedeMóvel** está ativada. Esta definição permite que um dispositivo com o Windows 10 abra uma ligação VPN através de uma rede móvel.

![Exemplo de uma política personalizada que contém as definições de VPN](./media/custom-policy-example.png)

## <a name="find-the-policies-you-can-configure"></a>Encontrar as políticas que pode configurar

Pode encontrar uma lista completa de todos os fornecedores de serviços de configuração (CSPs) suportados pelo Windows 10 na [Configuration service provider reference](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference) (Referência de fornecedores de serviços de configuração).

Nem todas as definições são compatíveis com todas as versões do Windows 10. O artigo [Configuration service provider reference](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference) (Referência de fornecedores de serviços de configuração) indica-lhe que versões são suportadas para cada CSP.

Além disso, o Intune não suporta todas as definições apresentadas. Para saber se o Intune suporta a definição que pretende, abra o artigo referente a essa definição. Cada página de definição mostra a sua operação suportada. Para trabalhar com o Intune, a definição tem de suportar as operações **Adicionar** ou **Substituir**.
