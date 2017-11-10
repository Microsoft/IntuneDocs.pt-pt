---
title: "Registo de Alterações do Armazém de Dados do Intune | Documentos da Microsoft"
description: "Uma lista de alterações na API do Armazém de Dados do Intune."
keywords: "Armazém de Dados do Intune"
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 10/19/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: E85DBB2D-67BB-4E10-82D6-E43046B9C43C
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: b81846c2e45f968184d50d2ea7c50aabb86b4964
ms.sourcegitcommit: e9f9fccccef691333143b7523d1b325ee7d1915a
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/02/2017
---
# <a name="change-log-for-the-intune-data-warehouse-api"></a>Registo de alterações da API do Armazém de Dados do Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Mantenha-se a par das atualizações do Armazém de Dados do Intune.

## <a name="1710"></a>1710
_Lançamento: outubro de 2017_

### <a name="user-entity-contains-latest-user-data-in-data-warehouse-data-model----1544273---"></a>A entidade User contém dados de utilizador no modelo de dados do Armazém de Dados <!-- 1544273 -->

A primeira versão do modelo de dados do Armazém de Dados do Intune continha apenas dados de histórico recentes do Intune. Os criadores de relatórios não conseguiam capturar o estado atual de um utilizador. Nesta atualização, a [**entidade User**](reports-ref-user.md) será preenchida com os dados mais recentes do utilizador.

### <a name="new-entity-in-the-in-data-warehouse-data-model----1479526---"></a>Nova entidade no modelo de dados do Armazém de Dados <!-- 1479526 -->

A entidade [**UserDeviceAssociation**](reports-ref-user-device.md) foi adicionada. A entidade **UserDeviceAssociation** contém associações de dispositivos do utilizador na sua organização.

## <a name="next-steps"></a>Próximos passos
 - Saiba mais sobre [as novidades todas as semanas no Intune](whats-new.md). Também pode descobrir quais são as alterações futuras, os avisos importantes sobre o serviço e as informações sobre versões anteriores. 
 - Leia o [Blogue do Microsoft Intune](http://go.microsoft.com/fwlink/?LinkID=273882).