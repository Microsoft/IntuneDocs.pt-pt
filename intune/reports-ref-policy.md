---
title: "Política | Documentos da Microsoft"
description: "Tópico de referência para a categoria Policy das coleções de entidades na API do Armazém de Dados do Intune."
keywords: "Armazém de Dados do Intune"
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: D5ADB9D8-D46A-43BD-AB0F-D6927508E3F4
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 4b3178b8469b5c92e4124ab00f9a635e63568d77
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/25/2018
---
# <a name="reference-for-policy-entities"></a>Referência para as entidades de políticas

A categoria **Policy** contém entidades para dispositivos móveis que registam informações como:

  -  Inventário de perfis de configuração de dispositivos, perfis de configuração de aplicações e políticas de conformidade  
  -  Número de dispositivos no estado com êxito, pendente, com falhas ou com erros por dia  
  -  Número de utilizadores no estado com êxito, pendente, com falhas ou com erros por dia  
  -  Número cumulativo de dispositivos no estado com êxito, pendente, com falhas ou com erros por dia  

## <a name="policy"></a>Policy

A entidade **Policy** apresenta uma lista de perfis de configuração de dispositivos, perfis de configuração de aplicações e políticas de conformidade. Pode atribuir as políticas com a Gestão de Dispositivos Móveis (MDM) a um grupo na sua empresa.

| Propriedade  | Descrição | Exemplo |
|---------|------------|--------|
| PolicyKey |Chave exclusiva para representar a política no armazém de dados. |123 |
| PolicyId |Identificador exclusivo da Política no armazém de dados. |b66bc706-ffff-7437-0340-032819502773 |
| PolicyName |Nome da Política. |"Linha de Base do Windows 10" |
| PolicyVersion |Versão da Política. Quando a política é editada ou alterada, é criada uma versão mais recente. |1, 2, 3 |
| IsDeleted |Indica se o registo da Política foi atualizado.  <br>True – a política tem um novo registo com campos atualizados. <br>False – o registo mais recente da política. |True/False |
| StartDateInclusiveUTC |Data e hora em UTC em que a política foi criada no armazém de dados. |11/23/2016 12:00:00 AM |
| DeletedDateUTC |Data e hora em UTC em que a propriedade IsDeleted foi alterada para True. |11/23/2016 12:00:00 AM |
| RowLastModifiedDateTimeUTC |Data e hora em UTC em que a política foi modificada pela última vez no armazém de dados. |11/23/2016 12:00:00 AM |

## <a name="policytype"></a>PolicyType

A entidade **PolicyType** apresenta uma lista dos tipos de perfis de configuração de dispositivos, perfis de configuração de aplicações e políticas de conformidade. Pode atribuir as políticas com a Gestão de Dispositivos Móveis (MDM) a um grupo na sua empresa.

| Propriedade  | Descrição | Exemplo |
|---------|------------|--------|
| PolicyTypeId |Identificador exclusivo da política no sistema de origem. |123 |
| PolicyTypeKey |Identificador exclusivo da política no armazém de dados. |1 |
| PolicyTypeName |Nome do tipo de política. |Política de Conformidade do Windows 10. |

## <a name="deviceconfiguration"></a>DeviceConfiguration

A entidade **DeviceConfigurationProfileDeviceActivity** apresenta uma lista do número de dispositivos no estado com êxito, pendente, com falhas ou com erros por dia. O número reflete os Perfis de configuração de dispositivos atribuídos à entidade. Por exemplo, se um dispositivo estiver no estado com êxito em todas as políticas atribuídas, o contador de casos com êxito tem um incremento de um para esse dia. Se um dispositivo tiver dois perfis atribuídos, um no estado com êxito e outro num estado com erros, a entidade incrementa o contador do estado com êxito (Succeeded) e coloca o dispositivo no estado com erros. A entidade apresenta uma lista de quantos dispositivos estão em cada um dos estados num determinado dia nos últimos 30 dias.

| Propriedade  | Descrição | Exemplo |
|---------|------------|--------|
| DateKey |Data-chave de quando a entrada do Perfil de Configuração do Dispositivo foi registada no armazém de dados. |20160703 |
| Pending |Número de Dispositivos exclusivos no estado pendente. |123 |
| Succeeded |Número de Dispositivos exclusivos no estado com êxito. |12 |
| Error |Número de Dispositivos exclusivos no estado com erros. |10 |
| Failed |Número de Dispositivos exclusivos no estado com falhas. |2 |

## <a name="userconfiguration"></a>UserConfiguration

A entidade **UserConfigurationProfileDeviceActivity** apresenta uma lista do número de utilizadores no estado com êxito, pendente, com falhas ou com erros por dia. O número reflete os Perfis de configuração de dispositivos atribuídos à entidade. Por exemplo, se um utilizador estiver no estado com êxito em todas as políticas atribuídas, sobe o contador com êxito em um para esse dia. Se um utilizador tem dois perfis atribuídos, um no estado com êxito e outro no estado com erros, contamos o utilizador no estado com erros.  A entidade **UserConfigurationProfileDeviceActivity** apresenta uma lista de quantos utilizadores estão em que estado num determinado dia nos últimos 30 dias.

| Propriedade  | Descrição | Exemplo |
|---------|------------|--------|
| DateKey |Data-chave de quando a entrada do Perfil de Configuração do Dispositivo foi registada no armazém de dados. |20160703 |
| Pending |Número de Utilizadores exclusivos no estado pendente. |123 |
| Succeeded |Número de Utilizadores exclusivos no estado com êxito. |12 |
| Error |Número de Utilizadores exclusivos no estado com erros. |10 |
| Failed |Número de Utilizadores exclusivos no estado com falhas. |2 |

## <a name="policytypeactivity"></a>PolicyTypeActivity

A entidade **PolicyTypeActivity** apresenta uma lista do número cumulativo de dispositivos no estado com êxito, pendente, com falhas ou com erros por dia. Apresenta uma lista destes estados relativamente a um perfil de configuração de dispositivo, perfil de configuração de aplicação ou política de conformidade por dia.

| Propriedade  | Descrição | Exemplo |
|---------|------------|--------|
| DateKey |Data-chave de quando a entrada do Perfil de configuração do dispositivo foi registada no armazém de dados. |20160703 |
| PolicyKey |A chave de política pode ser acompanhada pela Política para obter o policyName. |Linha de base do Windows 10 |
| PolicyTypeKey |O tipo de Chave de Política pode ser acompanhado do Tipo de Política para obter o nome do tipo de política. |Política de Compatibilidade do Windows 10 |
| Pending |Número de dispositivos exclusivos no estado pendente. |123 |
| Succeeded |Número de dispositivos exclusivos no estado com êxito. |12 |
| Error |Número de dispositivos exclusivos no estado com erros. |10 |
| Fail- |Número de dispositivos exclusivos no estado com falhas. |2 |