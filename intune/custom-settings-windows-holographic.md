---
title: "Definições personalizadas no Intune para dispositivos com o Windows Holographic for Business"
titlesuffix: Azure portal
description: "Saiba quais são as definições que pode utilizar num perfil personalizado do Windows Holographic for Business."
keywords: 
author: vhorne
ms.author: victorh
manager: angrobe
ms.date: 1/24/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ae46aef10ca294637a4d433ce273d3c53e695d64
ms.sourcegitcommit: 93622d740cbd12043eedc25a9699cc4256e23e7e
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/01/2018
---
# <a name="custom-device-settings-for-windows-holographic-for-business-devices-in-microsoft-intune"></a>Definições personalizadas para dispositivos com o Windows Holographic for Business no Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

 Utilize o perfil **personalizado** do Microsoft Intune para Windows Holographic for Business para implementar definições de OMA-URI (Open Mobile Alliance Uniform Resource Identifier) que podem ser utilizadas para controlar as funcionalidades nos dispositivos. O Windows Holographic for Business disponibiliza várias definições de fornecedores de serviços de configuração (CSPs). Para obter uma descrição geral do CSP, veja [Introdução a fornecedores de serviços de configuração (CSPs) para profissionais de TI](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers). Para obter CSPs específicos suportados pelo Windows Holographic, veja [CSPs suportados no Windows Holographic](https://docs.microsoft.com/en-us/windows/client-management/mdm/configuration-service-provider-reference#hololens).

Se estiver à procura de uma determinada definição, lembre-se de que o [perfil de restrição de dispositivos do Windows Holographic for Business](device-restrictions-windows-holographic.md) contém muitas definições incorporadas e não necessita que especifique valores personalizados.

1. Utilize as instruções em [Como configurar definições personalizadas dos dispositivos no Microsoft Intune](custom-settings-configure.md) para começar.
2. No painel **Criar Perfil**, escolha **Definições** para adicionar uma ou mais definições OMA-URI.
3. No painel **Definições de OMA-URI Personalizadas**, clique em **Adicionar** para adicionar um novo valor. Também pode clicar em **Exportar** para criar uma lista de todos os valores que configurou num ficheiro de valores separados por vírgulas (.csv).
4. Para cada definição OMA-URI que pretende adicionar, introduza as informações seguintes. Utilize a lista neste tópico para saber mais sobre as definições que pode utilizar:
    - **Nome da definição** – introduza um nome exclusivo para a definição OMA-URI para o ajudar a identificá-la na lista de definições.
    - **Descrição da definição** – opcionalmente, introduza uma descrição para a definição.
    - **Tipo de dados** – escolha entre:
        - **Cadeia**
        - **Cadeia (XML)**
        - **Data e hora**
        - **Número inteiro**
        - **Vírgula flutuante**
        - **Booleano**
    - **OMA-URI (sensível às maiúsculas e minúsculas)** – especifique o OMA-URI para o qual pretende fornecer uma definição.
    - **Valor** - indique o valor a associar ao OMA-URI que introduziu.
5. Quando tiver terminado, volte ao painel **Criar Perfil** e clique em **Criar**.
O perfil é criado e apresentado no painel da lista de perfis.

## <a name="supported-custom-settings"></a>Definições personalizadas suportadas

O Windows Holographic for Business suporta as seguintes definições personalizadas:


|Nome da definição|OMA-URI|Tipo de dados  |
|---------|---------|---------|
|AllowFastReconnect     |./Vendor/MSFT/Policy/Config/Authentication/AllowFastReconnect|Número inteiro (0 – não permitido, 1 – permitido)|
|AllowVPN     |./Vendor/MSFT/Policy/Config/Settings/AllowVPN|Número inteiro (0 – não permitido, 1 – permitido)|



## <a name="how-to-find-the-policies-you-can-configure"></a>Como encontrar as políticas que pode configurar

Pode consultar a lista completa de todos os fornecedores de serviços de configuração (CSPs) que o Windows Holographic suporta em [CSPs suportados no Windows Holographic](https://docs.microsoft.com/en-us/windows/client-management/mdm/configuration-service-provider-reference#hololens). Nem todas as definições são compatíveis com todas as versões do Windows Holographic. A tabela no tópico Windows indica quais as versões suportadas para cada CSP.

Além disso, o Intune não suporta todas as definições listadas no tópico. Para saber se o Intune suporta a definição que pretende, abra o tópico dessa definição. Cada página de definição mostra a sua operação suportada. Para trabalhar com o Intune, a definição tem de suportar as operações **Adicionar** ou **Substituir**.


