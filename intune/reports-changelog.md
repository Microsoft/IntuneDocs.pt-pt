---
title: "Registo de Alterações do Armazém de Dados do Intune | Documentos da Microsoft"
description: "Uma lista de alterações na API do Armazém de Dados do Intune."
keywords: "Armazém de Dados do Intune"
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 11/14/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: E85DBB2D-67BB-4E10-82D6-E43046B9C43C
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 7269d0552a0c01e4702eaae861d6c24f3f4f6f02
ms.sourcegitcommit: d26930f45ba9e6292a49bcb08defb5b3f14b704b
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/15/2017
---
# <a name="change-log-for-the-intune-data-warehouse-api"></a>Registo de alterações da API do Armazém de Dados do Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Mantenha-se a par das atualizações do Armazém de Dados do Intune.

## <a name="1710"></a>1710
_Lançado em novembro de 2017_

### <a name="a-new-entity-collection-named-current-user-is-limited-to-currently-active-user-data----1544273---"></a>A nova coleção de entidades com o nome Utilizador Atual está limitada aos dados dos utilizadores atualmente ativos<!-- 1544273 -->

A coleção de entidades **Utilizadores** contém dados do último mês. Estes registos incluem estados do utilizador durante o período de recolha dos dados, mesmo que o utilizador tenha sido removido. Por exemplo, um utilizador pode ser adicionado ao Intune e, em seguida, removido no decorrer do mês anterior. Apesar de este utilizador não estar presente no momento do relatório, o utilizador e o estado estão presentes nos dados. Pode criar um relatório que mostrará a duração da presença no histórico do utilizador nos seus dados.

Em contrapartida, a nova coleção de entidades **Utilizador Atual** contém apenas os utilizadores que não foram removidos. A coleção de entidades **Utilizador Atual** contém apenas os utilizadores atualmente ativos. Para obter informações sobre a coleção de entidades **Utilizador Atual**, veja [Reference for current user entity (Referência para a entidade utilizador atual)](reports-ref-current-user.md).

## <a name="1709"></a>1709
_Lançamento em outubro de 2017_

### <a name="user-device-association-entity-collection-added-to-intune-data-warehouse-data-model----1187917---"></a>Coleção de entidades de associação de dispositivos do utilizador adicionada ao modelo de dados do Armazém de Dados do Intune <!-- 1187917 -->

Agora pode criar relatórios e visualizações de dados com as informações de associação de dispositivos do utilizador que associam o utilizador às coleções de dispositivos de entidades. Pode aceder ao modelo de dados através do ficheiro do Power BI (PBIX) obtido na página do Intune do Armazém de Dados, através do ponto final do OData ou ao desenvolver um cliente personalizado. Para obter mais informações, veja a [Associação de Dispositivos do Utilizador](reports-ref-user-device.md).

### <a name="new-entities-in-the-in-data-warehouse-data-model----1479526--------"></a>Novas entidades no modelo de dados do Armazém de Dados <!-- 1479526 --><!-- -->

 - A entidade [**UserDeviceAssociation**](reports-ref-user-device.md) foi adicionada. A entidade **UserDeviceAssociation** contém associações de dispositivos do utilizador na sua organização. Agora pode criar relatórios e visualizações de dados com as informações de associação de dispositivos do utilizador que associam o utilizador às coleções de dispositivos de entidades.  
 - A entidade [**IntuneManagementExtension**](reports-ref-intunemanagementextension.md) foi adicionada. **IntuneManagementExtension** contém entidades para dispositivos móveis que controlam informações como o estado da versão e da instalação.

## <a name="next-steps"></a>Próximos passos
 - Saiba mais sobre [as novidades todas as semanas no Intune](whats-new.md). Também pode descobrir quais são as alterações futuras, os avisos importantes sobre o serviço e as informações sobre versões anteriores. 
 - Leia o [Blogue do Microsoft Intune](http://go.microsoft.com/fwlink/?LinkID=273882).