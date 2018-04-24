---
title: Definições personalizadas do Microsoft Intune para dispositivos com o Windows 10
titlesuffix: ''
description: Saiba quais são as definições personalizadas que pode configurar num perfil personalizado do Windows 10.
keywords: ''
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/1/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: c8e0d56c91b710a86949844d2fd455e4183488f5
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/16/2018
---
# <a name="microsoft-intune-custom-device-settings-for-devices-running-windows-10"></a>Definições personalizadas do Microsoft Intune para dispositivos com o Windows 10

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

 Utilize o perfil **personalizado** do Microsoft Intune para Windows 10 e Windows 10 Mobile para implementar definições OMA-URI (Open Mobile Alliance Uniform Resource Identifier) que podem ser utilizadas para controlar as funcionalidades nos dispositivos. O Windows 10 disponibiliza várias definições do Fornecedor de Serviços de Configuração (CSP), por exemplo, o [Fornecedor de Serviços de Configuração de Políticas (CSP de Políticas)](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers).
Se estiver à procura de uma determinada definição, lembre-se de que o [perfil de restrição de dispositivos do Windows 10](device-restrictions-windows-10.md) contém muitas definições que estão incorporados no Intune e não necessitam que especifique valores personalizados.

## <a name="configure-custom-settings"></a>Configurar definições personalizadas

1. Utilize as instruções em [Como configurar definições personalizadas dos dispositivos no Microsoft Intune](custom-settings-configure.md) para começar.
1. No painel **Definições OMA-URI Personalizadas**, clique em **Adicionar** para adicionar um novo valor. Também pode clicar em **Exportar** para criar uma lista de todos os valores que configurou num ficheiro de valores separados por vírgulas (.csv).
1. Para cada definição OMA-URI que pretende adicionar, introduza as informações seguintes. Utilize a lista neste artigo para saber mais sobre as definições que pode utilizar:
    - **Nome** – Introduza um nome exclusivo para a definição OMA-URI para o ajudar a identificá-la na lista de definições.
    - **Descrição** – opcionalmente, introduza uma descrição para a definição.
    - **OMA-URI (sensível às maiúsculas e minúsculas)** – especifique o OMA-URI para o qual pretende fornecer uma definição.
    - **Tipo de dados** – escolha entre:
        - **Cadeia**
        - **Cadeia (XML)**
        - **Data e hora**
        - **Número inteiro**
        - **Vírgula flutuante**
        - **Booleano**
        - **Base64**
    - **Valor** – indique o valor ou ficheiro a associar ao OMA-URI que introduziu.
1. Quando tiver terminado, selecione **OK**, volte ao painel **Criar perfil** e selecione **Criar**.
O perfil será criado e apresentado no painel Lista de perfis.

## <a name="example"></a>Exemplo
Na captura de ecrã seguinte, a definição **Connectivity/AllowVPNOverCellular** foi ativada. Isto permite que um dispositivo Windows 10 abra uma ligação VPN quando estiver numa rede celular.

> ![Exemplo de uma política personalizada que contém as definições de VPN](./media/custom-policy-example.png)


## <a name="how-to-find-the-policies-you-can-configure"></a>Como encontrar as políticas que pode configurar

Encontrará uma lista completa de todos os fornecedores de serviços de configuração (CSPs) que suportam o Windows 10 na [Configuration service provider reference (Referência do fornecedor de serviços de configuração)](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference) na biblioteca de documentação do Windows.

Nem todas as definições são compatíveis com todas as versões do Windows 10. A tabela no artigo Windows indica quais as versões suportadas para cada CSP.

Além disso, o Intune não suporta todas as definições listadas no artigo. Para saber se o Intune suporta a definição que pretende, abra o artigo referente a essa definição. Cada página de definição mostra a sua operação suportada. Para trabalhar com o Intune, a definição tem de suportar as operações **Adicionar** ou **Substituir**.
