---
title: Registo de Alterações do Armazém de Dados do Intune
titlesuffix: Microsoft Intune
description: Uma lista de alterações na API do Armazém de Dados do Intune.
keywords: Armazém de Dados do Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/09/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: E85DBB2D-67BB-4E10-82D6-E43046B9C43C
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: f4af9708838dc0393e87614342f4e3b563bb5101
ms.sourcegitcommit: 11bd3dbbc9dd762df7c6d20143f2171799712547
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/10/2018
ms.locfileid: "48903578"
---
# <a name="change-log-for-the-intune-data-warehouse-api"></a>Registo de alterações da API do Armazém de Dados do Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Mantenha-se a par das atualizações do Armazém de Dados do Intune.

## <a name="1808"></a>1808
_Lançada em agosto de 2018_

### <a name="v10-collections"></a>Coleções v1.0  

Agora, pode utilizar a versão v1.0 do Armazém de Dados do Intune, ao definir o parâmetro de consulta `api-version=v1.0`. As atualizações para coleções no Armazém de Dados são acumulativas por natureza e não interrompem cenários existentes.

### <a name="enrollment-failure-collection-released-to-beta"></a>Coleção de Falhas de Inscrição Lançada para Beta

A nova coleção `Enrollment Failure` é lançada para beta. Pode utilizar esta coleção para entender como a inscrição está a decorrer ao visualizar as falhas mais comuns. 


## <a name="1805"></a>1805
_Lançado em maio de 2018_

### <a name="correction-to-device-count-in-devices-collection"></a>Correção na contagem de dispositivos na coleção **Dispositivos** 

Foi feita uma correção à coleção **Dispositivos** que pode diminuir o número total de dispositivos que filtram pelo atributo `isDeleted`. Esta lista é um resultado da correção e não é um erro. Para mais informações sobre a coleção **Dispositivos**, veja [Referência para entidades de dispositivos](reports-ref-devices.md). 


## <a name="1801"></a>1801
_Lançada em janeiro de 2018_

### <a name="intune-data-warehouse-application-only-authentication----1867540---"></a>Autenticação apenas com a aplicação do Armazém de Dados do Intune <!-- 1867540 -->

Pode configurar uma aplicação com o Azure Active Directory (Azure AD) e autenticar para o Armazém de Dados do Intune. Para obter mais informações, veja [Autenticação apenas com a aplicação do Armazém de Dados do Intune](data-warehouse-app-only-auth.md).

### <a name="azure-ad-and-intune-credential-requirements----2077525---"></a>Requisitos de credenciais do Azure AD e do Intune <!-- 2077525 -->

- Já não é necessário atribuir uma licença do Intune ao utilizador ao aceder ao Armazém de Dados do Intune (incluindo a API).
- O nome da função do Intune foi alterado de **Relatórios** para **Armazém de dados do Intune**. 

    Para obter mais informações, veja [Requisitos de credenciais do Azure AD e do Intune](reports-api-url.md#azure-ad-and-intune-credential-requirements).

### <a name="odata-query-options----2077711---"></a>Opções de consulta de OData <!-- 2077711 -->

Pode utilizar <code>$select</code> como um parâmetro de consulta de OData. A versão atual suporta os seguintes parâmetros de consulta de OData: <code>$filter</code>, <code>$orderby</code>, <code>$select</code>, <code>$skip</code> e <code>$top</code>. Para obter mais informações, veja [Opções de consulta de OData](reports-api-url.md#odata-query-options).

### <a name="new-entities-in-the-in-data-warehouse-data-model----2077804---"></a>Novas entidades no modelo de dados do Armazém de Dados <!-- 2077804 -->

 - A entidade [**MobileAppDeviceuserInstallStatus**](reports-ref-application.md#mobileappdeviceuserinstallstatus) foi adicionada. A entidade **MobileAppDeviceUserInstallStatus** representa um estado de instalação da aplicação móvel de um determinado dispositivo e utilizador.
 - A entidade [**MobileAppInstallState**](reports-ref-application.md#mobileappinstallstate) foi adicionada. A entidade **MobileAppInstallState** representa o estado de instalação de uma aplicação móvel depois de ser atribuída a um grupo que contém dispositivos, utilizadores ou ambos. 

## <a name="1710"></a>1710
_Lançado em novembro de 2017_

### <a name="a-new-entity-collection-named-current-user-is-limited-to-currently-active-user-data----1544273---"></a>A nova coleção de entidades com o nome Utilizador Atual está limitada aos dados dos utilizadores atualmente ativos<!-- 1544273 -->

A coleção de entidades **Utilizadores** contém todos os utilizadores do Azure Active Directory (Azure AD) com licenças atribuídas na empresa. Estes registos incluem estados do utilizador durante o período de recolha dos dados, mesmo que o utilizador tenha sido removido. Por exemplo, um utilizador pode ser adicionado ao Intune e, em seguida, removido no decorrer do mês anterior. Apesar de este utilizador não estar presente no momento do relatório, o utilizador e o estado estão presentes nos dados. Pode criar um relatório que mostrará a duração da presença no histórico do utilizador nos seus dados.

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
