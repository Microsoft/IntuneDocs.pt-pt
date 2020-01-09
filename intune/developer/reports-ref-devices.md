---
title: Dispositivos – Armazém de Dados do Intune
titleSuffix: Microsoft Intune
description: Tópico de referência para a categoria Devices das coleções de entidades na API do Armazém de Dados do Intune.
keywords: Armazém de Dados do Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/03/2020
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 6955E12D-70D7-4802-AE3B-8B276F01FA4F
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 85b6d49f435ec45a2c6a2b81387ea25a1c15299b
ms.sourcegitcommit: 8d7406b75ef0d75cc2ed03b1a5e5f74ff10b98c0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/03/2020
ms.locfileid: "75654078"
---
# <a name="reference-for-devices-entities"></a>Referência para as entidades de dispositivos

A categoria **dispositivos** contém entidades para dispositivos móveis que rastreiam informações como:

- Tipo de Dispositivo
- Estado do registo e inscrição dos dispositivos
- Propriedade dos dispositivos
- Estado da gestão dos dispositivos
- Estado de associação dos dispositivos ao Azure AD
- Estado de inscrição
- Informações sobre o histórico dos dispositivos
- Inventário das aplicações no dispositivo

## <a name="devicetypes"></a>deviceTypes

A entidade **deviceTypes** representa o tipo de dispositivo referenciado por outras entidades de data warehouse. Normalmente, o tipo de dispositivo descreve o modelo do dispositivo, o fabricante ou ambos.

| Propriedade  | Description |
|---------|------------|
| deviceTypeID |Identificador exclusivo do tipo de dispositivo |
| deviceTypeKey |Identificador exclusivo do tipo de dispositivo no armazém de dados – chave de substituição |
| deviceTypeName |Tipo de Dispositivo |

### <a name="example"></a>Exemplo

| deviceTypeID  | Nome | Description |
|---------|------------|--------|
| 0 |Ambiente de Trabalho |Dispositivo de Ambiente de Trabalho do Windows |
| 1 |WindowsRT |Dispositivo WindowsRT |
| 2 |WinMO6 |Dispositivo Windows Mobile 6.0 |
| 3 |Nokia |Dispositivo Nokia |
| 4 |WindowsPhone |Dispositivo Windows Phone |
| 5 |Mac |Dispositivo Mac |
| 6 |WinCE |Dispositivo Windows CE |
| 7 |WinEmbedded |Dispositivo Windows Embedded |
| 8 |IPhone |Dispositivo iPhone |
| 9 |IPad |Dispositivo iPad |
| 10 |IPod |Dispositivo iPod |
| 11 |Android |Dispositivo Android gerido através do Administrador de Dispositivos |
| 12 |ISocConsumer |Dispositivo iSoc Consumer |
| 14 |MacMDM |Dispositivo Mac OS X gerido com o agente MDM incorporado |
| 15 |HoloLens |Dispositivo HoloLens |
| 16 |SurfaceHub |Dispositivo Surface Hub |
| 17 |AndroidForWork |Dispositivo Android gerido através do Proprietário do Perfil Android |
| 100 |Blackberry |Dispositivo Blackberry |
| 101 |Palm |Dispositivo Palm |
| 255 |Unknown |Tipo de dispositivo desconhecido |

## <a name="enrollmentactivities"></a>enrollmentActivities 
A entidade **enrollmentActivity** indica a atividade de um registro de dispositivo.

| Propriedade                      | Description                                                               |
|-------------------------------|---------------------------------------------------------------------------|
| dateKey                       | Chave da data em que esta atividade de registro foi registrada.               |
| deviceEnrollmentTypeKey       | Chave do tipo de registro.                                        |
| deviceTypeKey                 | Chave do tipo de dispositivo.                                                |
| enrollmentEventStatusKey      | Chave do status que indica o êxito ou a falha do registro.    |
| enrollmentFailureCategoryKey  | Chave da categoria de falha de registro (se o registro falhar).        |
| enrollmentFailureReasonKey    | Chave do motivo da falha de registro (se o registro falhar).          |
| osVersion                     | A versão do sistema operacional do dispositivo.                               |
| count                         | Contagem total de atividades de registro que correspondem às classificações acima.  |

## <a name="enrollmenteventstatuses"></a>enrollmentEventStatuses 
A entidade **enrollmentEventStatus** indica o resultado de um registro de dispositivo.

| Propriedade                   | Description                                                                       |
|----------------------------|-----------------------------------------------------------------------------------|
| enrollmentEventStatusKey   | Identificador exclusivo do status de registro no data warehouse (chave substituta)  |
| enrollmentEventStatusName  | O nome do status do registro. Veja os exemplos abaixo.                            |

### <a name="example"></a>Exemplo

| enrollmentEventStatusName  | Description                            |
|----------------------------|----------------------------------------|
| Êxito                    | Um registro de dispositivo bem-sucedido         |
| Failed                     | Um registro de dispositivo com falha             |
| Não disponível              | O status do registro não está disponível.  |

## <a name="enrollmentfailurecategories"></a>enrollmentFailureCategories 
A entidade **EnrollmentFailureCategory** indica por que um registro de dispositivo falhou. 

| Propriedade                       | Description                                                                                 |
|--------------------------------|---------------------------------------------------------------------------------------------|
| enrollmentFailureCategoryKey   | Identificador exclusivo da categoria de falha de registro no data warehouse (chave substituta)  |
| enrollmentFailureCategoryName  | O nome da categoria de falha de registro. Veja os exemplos abaixo.                            |

### <a name="example"></a>Exemplo

| enrollmentFailureCategoryName   | Description                                                                                                   |
|---------------------------------|---------------------------------------------------------------------------------------------------------------|
| Não Aplicável                  | A categoria de falha de registro não é aplicável.                                                            |
| Não disponível                   | A categoria de falha de registro não está disponível.                                                             |
| Unknown                         | Erro desconhecido.                                                                                                |
| Autenticação                  | Falha na autenticação.                                                                                        |
| Autorização                   | A chamada foi autenticada, mas não está autorizada a se registrar.                                                         |
| AccountValidation               | Falha ao validar a conta para registro. (Conta bloqueada, registro não habilitado)                      |
| Uservalidation                  | Não foi possível validar o usuário. (O usuário não existe, licença ausente)                                           |
| DeviceNotSupported              | O dispositivo não tem suporte para gerenciamento de dispositivo móvel.                                                         |
| Inmanutenção                   | A conta está em manutenção.                                                                                    |
| BadRequest                      | O cliente enviou uma solicitação que não é compreendida/suportada pelo serviço.                                        |
| FeatureNotSupported             | Não há suporte para os recursos usados por este registro para esta conta.                                        |
| EnrollmentRestrictionsEnforced  | As restrições de registro configuradas pelo administrador bloquearam esse registro.                                          |
| ClientDisconnected              | O cliente atingiu o tempo limite ou o registro foi anulado pelo usuário final.                                                        |
| Desabandono                 | O registro foi abandonado pelo usuário final. (O usuário final iniciou a integração, mas não conseguiu concluí-la no tempo hábil)  |

## <a name="enrollmentfailurereasons"></a>enrollmentFailureReasons  
A entidade **EnrollmentFailureReason** indica um motivo mais detalhado para uma falha de registro de dispositivo em uma determinada categoria de falha.  

| Propriedade                     | Description                                                                               |
|------------------------------|-------------------------------------------------------------------------------------------|
| enrollmentFailureReasonKey   | Identificador exclusivo do motivo da falha no registro no data warehouse (chave substituta)  |
| enrollmentFailureReasonName  | O nome do motivo da falha no registro. Veja os exemplos abaixo.                            |

### <a name="example"></a>Exemplo

| enrollmentFailureReasonName      | Description                                                                                                                                                                                            |
|----------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Não Aplicável                   | O motivo da falha no registro não é aplicável.                                                                                                                                                       |
| Não disponível                    | O motivo da falha no registro não está disponível.                                                                                                                                                        |
| Unknown                          | Erro desconhecido.                                                                                                                                                                                         |
| UserNotLicensed                  | O usuário não foi encontrado no Intune ou não tem uma licença válida.                                                                                                                                     |
| UserUnknown                      | O usuário não é conhecido pelo Intune.                                                                                                                                                                           |
| BulkAlreadyEnrolledDevice        | Somente um usuário pode registrar um dispositivo. Este dispositivo foi registrado anteriormente por outro usuário.                                                                                                                |
| EnrollmentOnboardingIssue        | A autoridade de MDM (gerenciamento de dispositivo móvel) do Intune ainda não está configurada.                                                                                                                                 |
| AppleChallengeIssue              | A instalação do perfil de gerenciamento do iOS foi atrasada ou falhou.                                                                                                                                         |
| AppleOnboardingIssue             | Um certificado de push de MDM da Apple é necessário para se registrar no Intune.                                                                                                                                       |
| DeviceCap                        | O usuário tentou registrar mais dispositivos do que o máximo permitido.                                                                                                                                        |
| AuthenticationRequirementNotMet  | O serviço de registro do Intune não pôde autorizar esta solicitação.                                                                                                                                            |
| UnsupportedDeviceType            | Este dispositivo não atende aos requisitos mínimos para registro no Intune.                                                                                                                                  |
| EnrollmentCriteriaNotMet         | Falha ao registrar este dispositivo devido a uma regra de restrição de registro configurada.                                                                                                                          |
| BulkDeviceNotPreregistered       | O IMEI (identificador de equipamentos móveis internacional) ou o número de série do dispositivo não foi encontrado.  Sem esse identificador, os dispositivos são reconhecidos como dispositivos de propriedade pessoal que estão bloqueados no momento.  |
| FeatureNotSupported              | O usuário estava tentando acessar um recurso que ainda não foi lançado para todos os clientes ou não é compatível com a configuração do Intune.                                                            |
| Desabandono                  | O registro foi abandonado pelo usuário final. (O usuário final iniciou a integração, mas não conseguiu concluí-la no tempo hábil)                                                                                           |
| APNSCertificateExpired           | Os dispositivos da Apple não podem ser gerenciados com um certificado de push MDM da Apple expirado.                                                                                                                            |
## <a name="ownertypes"></a>ownerTypes

A entidade **enrolltype** indica se um dispositivo é corporativo, de propriedade pessoal ou desconhecido.

| Propriedade  | Description | Exemplo |
|---------|------------|--------|
| ownerTypeID |Identificador exclusivo do tipo de proprietário. | |
| ownerTypeKey |Identificador exclusivo do tipo de proprietário no armazém de dados – chave de substituição. | |
| ownerTypeName |Representa o tipo de proprietário dos dispositivos:  <br>Corporativo-o dispositivo é de propriedade da empresa. <br>Personal: o dispositivo é propriedade pessoal (BYOD).  <br>Unknown: não existem informações sobre este dispositivo. |Pessoal corporativo desconhecido |

> [!Note]  
> Para o `ownerTypeName` em AzureAD ao criar grupos dinâmicos para dispositivos, você precisa definir o valor do filtro `deviceOwnership` como `Company`. Para obter mais informações, consulte [regras para dispositivos](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership#rules-for-devices). 

## <a name="managementstates"></a>managementStates

A entidade **managementStates** fornece detalhes sobre o estado do dispositivo. Os detalhes podem ser úteis nos casos em que são aplicadas ações remotas ou quando o dispositivo foi desbloqueado por jailbreak ou rooting.

| Propriedade  | Description |
|---------|------------|
| managementStateID | Identificador exclusivo do estado de gestão. |
| managementStateKey | Identificador exclusivo do estado de gestão no armazém de dados – chave de substituição. |
| managementStateName | Indica o estado da ação remota aplicada a este dispositivo. |

### <a name="example"></a>Exemplo

| managementStateID  | Nome | Description |
|---------|------------|--------|
| 0 |Managed | Gerido sem ações remotas pendentes. |
| 1 |RetirePending | Existe um comando de extinção pendente para o dispositivo. |
| 2 |RetireFailed | O comando de extinção no dispositivo falhou. |
| 3 |WipePending | Existe um comando para apagar pendente para o dispositivo. |
| 4 |WipeFailed | O comando para apagar falhou no dispositivo. |
| 5 |Unhealthy | Mau estado de funcionamento. |
| 6 |DeletePending | Existe um comando de eliminação pendente para o dispositivo. |
| 7 |RetireIssued | Foi emitido um comando de extinção para o dispositivo. |
| 8 |WipeIssued | Foi emitido um comando para apagar. |
| 9 |WipeCanceled | O comando para apagar foi cancelado. |
| 10 |RetireCanceled | O comando de extinção foi cancelado. |
| 11 |Discovered | O dispositivo foi detetado recentemente no Intune. Após dar entrada pela primeira vez será movido para o estado Managed. |

## <a name="managementagenttypes"></a>managementAgentTypes

A entidade **ManagementAgentType** representa os agentes usados para gerenciar um dispositivo.

| Propriedade  | Description |
|---------|------------|
| managementAgentTypeID | Identificador exclusivo do tipo de agente de gestão. |
| managementAgentTypeKey | Identificador exclusivo do tipo de agente de gestão no armazém de dados – chave de substituição. |
| managementAgentTypeName |Indica que tipo de agente é utilizado para gerir o dispositivo. |

### <a name="example"></a>Exemplo

| ManagementAgentTypeID  | Nome | Description |
|---------|------------|--------|
| 1 |EAS | O dispositivo é gerido através do Exchange Active Sync |
| 2 |MDM | O dispositivo é gerido através de um agente MDM |
| 3 |EasMdm | O dispositivo é gerido através do Exchange Active Sync e de um agente MDM |
| 4 |IntuneClient | O dispositivo é gerido pelo agente de PC do Intune |
| 5 |EasIntuneClient | O dispositivo é gerido através do Exchange Active Sync e do agente de PC do Intune |
| 8 |ConfigManagerClient | O dispositivo é gerenciado pelo agente de Configuration Manager |
| 16 |Unknown | Tipo de agente de gestão desconhecido |

## <a name="devices"></a>dispositivos

A entidade **dispositivos** lista todos os dispositivos registrados sob gerenciamento e suas propriedades correspondentes.

|          Propriedade          |                                                                                       Description                                                                                      |
|:--------------------------:|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
| deviceKey                  | Identificador exclusivo do dispositivo no armazém de dados – chave de substituição.                                                                                                               |
| deviceId                   | Identificador exclusivo do dispositivo.                                                                                                                                                     |
| deviceName                 | Nome do dispositivo nas plataformas que permitem atribuir um nome aos dispositivos. Noutras plataformas, o Intune cria um nome a partir de outras propriedades. O atributo não pode estar disponível para todos os dispositivos. |
| deviceTypeKey              | Chave do atributo de tipo de dispositivo para este dispositivo.                                                                                                                                    |
| deviceRegistrationState    | Chave do atributo de estado do registo do cliente para este dispositivo.                                                                                                                      |
| ownerTypeKey               | Chave do atributo de tipo de proprietário para este dispositivo: corporate, personal ou unknown.                                                                                                    |
| enrolledDateTime           | A data e hora em que o dispositivo foi inscrito.                                                                                                                                         |
| lastSyncDateTime           | Última entrada de dispositivo conhecida com o Intune.                                                                                                                                              |
| managementAgentKey         | Chave do agente de gestão associado a este dispositivo.                                                                                                                             |
| managementStateKey         | Chave do estado de gestão associado a este dispositivo a indicar o estado mais recente de uma ação remota ou se foi desbloqueado por jailbreak/rooting.                                                |
| azureADDeviceId            | O deviceID do Azure para este dispositivo.                                                                                                                                                  |
| azureADRegistered          | Se o dispositivo está registado no Azure Active Directory.                                                                                                                             |
| deviceCategoryKey          | Chave da categoria associada a este dispositivo.                                                                                                                                     |
| deviceEnrollmentType       | Chave do tipo de inscrição associado a este dispositivo, indicando o método de inscrição.                                                                                             |
| complianceStateKey         | Chave do estado de Conformidade associado a este dispositivo.                                                                                                                             |
| osVersion                  | Versão do sistema operativo do dispositivo.                                                                                                                                                |
| easDeviceId                | ID do Exchange ActiveSync do dispositivo.                                                                                                                                                  |
| serialNumber               | SerialNumber                                                                                                                                                                           |
| userId                     | O Identificador Exclusivo para o utilizador associado ao dispositivo.                                                                                                                           |
| rowLastModifiedDateTimeUTC | A data e hora em UTC em que este dispositivo foi modificado pela última vez no armazém de dados.                                                                                                       |
| fabricante               | Fabricante do dispositivo                                                                                                                                                             |
| modelo                      | Modelo do dispositivo                                                                                                                                                                    |
| operatingSystem            | Sistema operativo do dispositivo. Windows, iOS, etc.                                                                                                                                   |
| isDeleted                  | O binário para mostrar se o dispositivo é eliminado ou não.                                                                                                                                 |
| androidSecurityPatchLevel  | Nível do patch de segurança para Android                                                                                                                                                           |
| MEID                       | MEID                                                                                                                                                                                   |
| isSupervised               | Estado supervisionado do dispositivo                                                                                                                                                               |
| freeStorageSpaceInBytes    | Armazenamento Livre em Bytes.                                                                                                                                                                 |
| totalStorageSpaceInBytes   | Armazenamento Total em Bytes.                                                                                                                                                                |
| encryptionState            | Estado de encriptação no dispositivo.                                                                                                                                                      |
| subscriberCarrier          | Operadora subscritora do dispositivo                                                                                                                                                       |
| phoneNumber                | Número de telefone do dispositivo                                                                                                                                                             |
| IMEI                       | IMEI                                                                                                                                                                                   |
| cellularTechnology         | Tecnologia de rede móvel do dispositivo                                                                                                                                                    |
| WiFiMacAddress             | MAC Wi-Fi                                                                                                                                                                              |
| ICCD                       | Identificador de placa de circuito integrado                                                                                                                                                     |

## <a name="devicepropertyhistories"></a>devicePropertyHistories

A entidade **devicePropertyHistory** tem as mesmas propriedades que a tabela de dispositivos e instantâneos diários de cada registro de dispositivo por dia nos últimos 90 dias. A coluna DateKey indica o dia para cada linha.

|          Propriedade          |                                                                                      Description                                                                                     |
|:--------------------------:|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
| dateKey                    | Referência à tabela de data que indica o dia.                                                                                                                                          |
| deviceKey                  | Identificador exclusivo do dispositivo na chave data warehouse-substituta. Esta é uma referência à tabela Dispositivos que contém o ID de dispositivo do Intune.                               |
| deviceName                 | Nome do dispositivo nas plataformas que permitem atribuir um nome aos dispositivos. Noutras plataformas, o Intune cria um nome a partir de outras propriedades. O atributo não pode estar disponível para todos os dispositivos. |
| deviceRegistrationStateKey | Chave do atributo de estado do registo do dispositivo para este dispositivo.                                                                                                                    |
| ownerTypeKey               | Chave do atributo de tipo de proprietário para este dispositivo: corporate, personal ou unknown.                                                                                                  |
| managementStateKey         | Chave do estado de gestão associado a este dispositivo a indicar o estado mais recente de uma ação remota ou se foi desbloqueado por jailbreak/rooting.                                                |
| azureADRegistered          | Se o dispositivo está registado no Azure Active Directory.                                                                                                                             |
| complianceStateKey         | Uma chave para o ComplianceState.                                                                                                                                                            |
| OSVersion                  | Versão do SO.                                                                                                                                                                          |
| Jailbreak                 | Se o dispositivo está desbloqueado por jailbreak ou rooting.                                                                                                                                         |
| deviceCategoryKey          | Chave do atributo da categoria do dispositivo para este dispositivo. 

