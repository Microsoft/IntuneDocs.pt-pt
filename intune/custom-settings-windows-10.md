---
title: "Definições personalizadas do Intune para dispositivos Windows 10"
titlesuffix: Azure portal
description: "Saiba quais são as definições que pode utilizar num perfil personalizado do Windows 10.\""
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 05/09/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7bcea136-7260-4042-b21b-c7dab86b380d
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 03dd17d1ef6cde7514720c063cef7da4c3c7db3d
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/09/2017
---
# <a name="custom-device-settings-for-windows-10-devices-in-microsoft-intune"></a>Definições de dispositivos personalizadas para dispositivos Windows 10 no Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

 Utilize o perfil **personalizado** do Microsoft Intune para Windows 10 e Windows 10 Mobile para implementar definições OMA-URI (Open Mobile Alliance Uniform Resource Identifier) que podem ser utilizadas para controlar as funcionalidades nos dispositivos. O Windows 10 disponibiliza várias definições CSP, por exemplo, o [Fornecedor de Serviços de Configuração de Políticas (CSP de Políticas)](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers).
Se estiver à procura de uma determinada definição, lembre-se de que o [perfil de restrição de dispositivos do Windows 10](device-restrictions-windows-10.md) contém muitas definições que estão incorporados no Intune e não necessitam que especifique valores personalizados.

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
O perfil será criado e é apresentado no painel da lista de perfis.

## <a name="example"></a>Exemplo
Na captura de ecrã abaixo, a definição **Connectivity/AllowVPNOverCellular** foi ativada. Isto permite que um dispositivo Windows 10 abra uma ligação VPN quando estiver numa rede celular.

> ![Exemplo de uma política personalizada que contém as definições de VPN](./media/custom-policy-example.png)


## <a name="how-to-find-the-policies-you-can-configure"></a>Como encontrar as políticas que pode configurar

Encontrará uma lista completa de todos os fornecedores de serviços de configuração (CSPs) que suportam o Windows 10 na [Configuration service provider reference (Referência do fornecedor de serviços de configuração)](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference) na biblioteca de documentação do Windows.

Nem todas as definições são compatíveis com todas as versões do Windows 10. A tabela no tópico Windows indica quais as versões suportadas para cada CSP.

Além disso, o Intune não suporta todas as definições listadas no tópico. Para saber se o Intune suporta a definição que pretende, abra o tópico dessa definição. Cada página de definição mostra a sua operação suportada. Para trabalhar com o Intune, a definição tem de suportar as operações **Adicionar** ou **Substituir**.


