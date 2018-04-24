---
title: Especificar números IMEI
description: O Microsoft Intune permite aos administradores importar números IMEI para plataformas de dispositivos móveis para ajudar a identificar os dispositivos móveis pertencentes à empresa
keywords: ''
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 03/22/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 1712bd39-562b-4409-9cec-155d5f4d8a39
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: cdc1e1ac6147903ec6ada30e7a3b42189a228c78
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/16/2018
---
# <a name="specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers"></a>Especifique os dispositivos da empresa com os números de identidade internacional do equipamento móvel (IMEI)

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

O Microsoft Intune permite aos administradores importar números de identidade internacional do equipamento móvel (IMEI) para plataformas de dispositivos móveis com números IMEI para ajudar a identificar os dispositivos móveis pertencentes à empresa. Após a inscrição dos dispositivos no Intune, pode ver os dispositivos cujos números IMEI foram importados em **Grupos** > **Descrição Geral** > **Todos os Dispositivos**. O **Grupo de dispositivos** lista os dispositivos com números IMEI importados como **Empresa** na coluna **Propriedade**.

1. Na [consola de administração do Microsoft Intune](https://manage.microsoft.com), selecione **Groups**&gt; **All Devices** &gt; **All Corporate Pre-enrolled Devices** &gt; **By IMEI (All platforms)** e, em seguida, clique em **Add devices…**. Pode adicionar dispositivos de duas formas:

   - **Carregar um ficheiro .csv que contenha números de série** – crie uma lista de valores separados por vírgulas (.csv) de duas colunas sem cabeçalho, limitada até 5000 dispositivos ou 5 MB por ficheiro .csv. O campo de detalhes está limitado a 128 carateres. 


     |                 |                           |
     |-----------------|---------------------------|
     | &lt;IMEI n.º 1&gt; | &lt;Detalhes do Dispositivo n.º 1&gt; |
     | &lt;IMEI n.º 2&gt; | &lt;Detalhes do Dispositivo n.º 2&gt; |

     Se visualizar este ficheiro .csv num editor de texto, este é apresentado como:

     ```
     01234567890123,device details
     02234567890123,device details
     ```

   - **Adicionar manualmente os detalhes de dispositivos** – introduza o número IMEI e os detalhes de um máximo de 15 dispositivos.

   O campo *Detalhes* é para utilização administrativa. Pode especificar os detalhes para ajudar a identificar o dispositivo na lista de dispositivos pertencentes à empresa listados pelo ID de hardware. Estas informações não são enviadas para o dispositivo, mas irão aparecer na consola do Intune.

2. Selecione **Next**.
3. No painel **Rever Dispositivos**, pode confirmar os números IMEI de dispositivos importados. Também pode decidir se quer substituir os **Detalhes** dos números IMEI que serão importados novamente. Pode desmarcar a caixa **Substituir** para manter os Detalhes atuais. Escolha **Concluir** para importar os números IMEI.
4. Os números IMEI importados e as descrições são adicionadas à lista **Por IMEI (Todas as plataformas)**.

> [!IMPORTANT]
> Se estiver a importar números IMEI para dispositivos Android, tenha em atenção que alguns desses dispositivos poderão ter múltiplos números IMEI. Se importar um número IMEI que não corresponda ao IMEI comunicado ao Intune pelo dispositivo, este será classificado como um dispositivo pessoal em vez de um dispositivo da empresa.

Quando um dispositivo com um número IMEI é inscrito no Intune, normalmente, quando um utilizador instalar a aplicação Portal da Empresa e concluir o processo de inscrição, o dispositivo será marcado como sendo de propriedade da empresa e será apresentado como inscrito no grupo **Dispositivos IMEI**.

>[!NOTE]
> Quando a sua organização for migrada para o novo portal do Azure num futuro próximo, verá uma alteração desta funcionalidade. Na consola de administrador do Intune existente, os administradores podem aceitar detalhes associados de um CSV carregado e substituir os detalhes existentes por identificadores de hardware individuais. No novo portal do Azure, poderá substituir automaticamente os detalhes de todos os identificadores de hardware ou ignorar os novos detalhes de identificadores existentes.

Para obter especificações detalhadas sobre os Identificadores Internacionais do Equipamento Móvel, veja [3GGPP TS 23.003](https://portal.3gpp.org/desktopmodules/Specifications/SpecificationDetails.aspx?specificationId=729).
