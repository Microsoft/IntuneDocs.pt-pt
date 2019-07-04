---
title: Dispositivos – Armazém de Dados do Intune
titleSuffix: Microsoft Intune
description: Tópico de referência para a categoria Devices das coleções de entidades na API do Armazém de Dados do Intune.
keywords: Armazém de Dados do Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/09/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 6955E12D-70D7-4802-AE3B-8B276F01FA4F
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2b1fe488ed7d295a40b42c1fb17a76693004be4d
ms.sourcegitcommit: bccfbf1e3bdc31382189fc4489d337d1a554e6a1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/03/2019
ms.locfileid: "67547924"
---
# <a name="reference-for-devices-entities"></a>Referência para as entidades de dispositivos

A categoria **Devices** contém entidades para dispositivos móveis que registam informações como:

  - Tipo de dispositivo
  - Estado do registo e inscrição dos dispositivos
  - Propriedade dos dispositivos
  - Estado da gestão dos dispositivos
  - Estado de associação dos dispositivos ao Azure AD
  - Estado de inscrição
  - Informações sobre o histórico dos dispositivos
  - Inventário das aplicações no dispositivo

## <a name="devicetypes"></a>DeviceTypes

A entidade **DeviceTypes** representa o tipo de dispositivo referenciado por outras entidades do armazém de dados. Normalmente, o tipo de dispositivo descreve o modelo do dispositivo, o fabricante ou ambos.

| Propriedade  | Descrição |
|---------|------------|
| DeviceTypeID |Identificador exclusivo do tipo de dispositivo |
| DeviceTypeKey |Identificador exclusivo do tipo de dispositivo no armazém de dados – chave de substituição |
| DeviceTypeName |Tipo de dispositivo |

### <a name="example"></a>Exemplo

| deviceTypeID  | Nome | Descrição |
|---------|------------|--------|
| 0 |Desktop |Dispositivo de Ambiente de Trabalho do Windows |
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
| 15 |HoloLens |Dispositivos HoloLens |
| 16 |SurfaceHub |Dispositivo Surface Hub |
| 17 |AndroidForWork |Dispositivo Android gerido através do Proprietário do Perfil Android |
| 100 |Blackberry |Dispositivo Blackberry |
| 101 |Palm |Dispositivo Palm |
| 255 |Desconhecido |Tipo de dispositivo desconhecido |

## <a name="enrollmentactivities"></a>enrollmentActivities 
O **EnrollmentActivity** entidade indica a atividade de uma inscrição de dispositivos.

| Propriedade                      | Descrição                                                               |
|-------------------------------|---------------------------------------------------------------------------|
| dateKey                       | Chave da data quando esta atividade de inscrição foi registada.               |
| deviceEnrollmentTypeKey       | Chave do tipo do Registro.                                        |
| deviceTypeKey                 | Chave do tipo de dispositivo.                                                |
| enrollmentEventStatusKey      | Chave do Estado que indica o êxito ou falha do Registro.    |
| enrollmentFailureCategoryKey  | Chave de categoria de falha de inscrição (se a inscrição falha).        |
| enrollmentFailureReasonKey    | Chave do motivo da falha de inscrição (se a inscrição falha).          |
| osVersion                     | A versão do sistema operativo do dispositivo.                               |
| count                         | Contagem total de atividades de inscrição que correspondem a classificações acima.  |

## <a name="enrollmenteventstatuses"></a>enrollmentEventStatuses 
O **EnrollmentEventStatus** entidade indica o resultado de uma inscrição de dispositivos.

| Propriedade                   | Descrição                                                                       |
|----------------------------|-----------------------------------------------------------------------------------|
| enrollmentEventStatusKey   | Identificador exclusivo do Estado de inscrição no armazém de dados (chave de substituição)  |
| enrollmentEventStatusName  | O nome do Estado de inscrição. Veja exemplos abaixo.                            |

### <a name="example"></a>Exemplo

| enrollmentEventStatusName  | Descrição                            |
|----------------------------|----------------------------------------|
| Êxito                    | Uma inscrição de dispositivos com êxito         |
| Com Falhas                     | Uma inscrição de dispositivos com falhas             |
| Não disponível              | O estado de inscrição não está disponível.  |

## <a name="enrollmentfailurecategories"></a>enrollmentFailureCategories 
O **EnrollmentFailureCategory** entidade indica o motivo da falha uma inscrição de dispositivos. 

| Propriedade                       | Descrição                                                                                 |
|--------------------------------|---------------------------------------------------------------------------------------------|
| enrollmentFailureCategoryKey   | Identificador exclusivo da categoria de falha de inscrição no armazém de dados (chave de substituição)  |
| enrollmentFailureCategoryName  | O nome da categoria de falha de inscrição. Veja exemplos abaixo.                            |

### <a name="example"></a>Exemplo

| enrollmentFailureCategoryName   | Descrição                                                                                                   |
|---------------------------------|---------------------------------------------------------------------------------------------------------------|
| Não Aplicável                  | A categoria de falha de inscrição não é aplicável.                                                            |
| Não disponível                   | A categoria de falha de inscrição não está disponível.                                                             |
| Desconhecido                         | Erro desconhecido.                                                                                                |
| Authentication                  | Falha na autenticação.                                                                                        |
| Autorização                   | Chamada foi autenticada, mas não autorizada a inscrever.                                                         |
| AccountValidation               | Falha ao validar a conta para a inscrição. (Conta bloqueada, inscrição não ativada)                      |
| UserValidation                  | Não foi possível validar o utilizador. (O utilizador não existe, licença em falta)                                           |
| DeviceNotSupported              | Dispositivo não é suportado para a gestão de dispositivos móveis.                                                         |
| InMaintenance                   | Conta está em manutenção.                                                                                    |
| BadRequest                      | Cliente enviou um pedido que não é entendida/suportadas pelo serviço.                                        |
| FeatureNotSupported             | Utilizado por este inscrição ou estas funcionalidades não são suportadas para esta conta.                                        |
| EnrollmentRestrictionsEnforced  | Restrições de inscrição configuradas pelo administrador bloqueado neste inscrição.                                          |
| ClientDisconnected              | Cliente excedeu o limite de tempo ou inscrição foi abortada pelo utilizador final.                                                        |
| UserAbandonment                 | Inscrição foi abandonada pelo utilizador final. (O utilizador final à integração mas não foi possível concluí-la de forma atempada)  |

## <a name="enrollmentfailurereasons"></a>enrollmentFailureReasons  
O **EnrollmentFailureReason** entidade indica um motivo mais detalhado para uma falha de inscrição de dispositivos numa categoria de determinada falha.  

| Propriedade                     | Descrição                                                                               |
|------------------------------|-------------------------------------------------------------------------------------------|
| enrollmentFailureReasonKey   | Identificador exclusivo do motivo da falha de inscrição no armazém de dados (chave de substituição)  |
| enrollmentFailureReasonName  | O nome do motivo da falha de inscrição. Veja exemplos abaixo.                            |

### <a name="example"></a>Exemplo

| enrollmentFailureReasonName      | Descrição                                                                                                                                                                                            |
|----------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Não Aplicável                   | O motivo da falha de inscrição não é aplicável.                                                                                                                                                       |
| Não disponível                    | O motivo da falha de inscrição não está disponível.                                                                                                                                                        |
| Desconhecido                          | Erro desconhecido.                                                                                                                                                                                         |
| UserNotLicensed                  | O utilizador não foi encontrado no Intune ou não tem uma licença válida.                                                                                                                                     |
| UserUnknown                      | Utilizador não é conhecido para o Intune.                                                                                                                                                                           |
| BulkAlreadyEnrolledDevice        | Apenas um utilizador pode inscrever um dispositivo. Este dispositivo foi inscrito anteriormente por outro utilizador.                                                                                                                |
| EnrollmentOnboardingIssue        | Autoridade de gestão (MDM) de dispositivos móveis do Intune ainda não está configurada.                                                                                                                                 |
| AppleChallengeIssue              | A instalação de perfil de gestão do iOS foi adiada ou falhou.                                                                                                                                         |
| AppleOnboardingIssue             | Um certificado push de MDM da Apple é necessário para inscrever no Intune.                                                                                                                                       |
| DeviceCap                        | O utilizador tentado inscrever mais dispositivos do que o máximo permitido.                                                                                                                                        |
| AuthenticationRequirementNotMet  | Serviço de inscrição do Intune Falha ao autorizar este pedido.                                                                                                                                            |
| UnsupportedDeviceType            | Este dispositivo não cumpre os requisitos mínimos para inscrição no Intune.                                                                                                                                  |
| EnrollmentCriteriaNotMet         | Este dispositivo não foi possível inscrever devido a uma regra de restrição de inscrição configurada.                                                                                                                          |
| BulkDeviceNotPreregistered       | Identificador de equipamento móvel internacional (IMEI) ou número de série do dispositivo, este não foi encontrado.  Sem este identificador, os dispositivos são reconhecidos como dispositivos pessoais que estão atualmente bloqueados.  |
| FeatureNotSupported              | O utilizador estava a tentar aceder a uma funcionalidade que ainda não foi disponibilizada para todos os clientes ou não é compatível com a sua configuração do Intune.                                                            |
| UserAbandonment                  | Inscrição foi abandonada pelo utilizador final. (O utilizador final à integração mas não foi possível concluí-la de forma atempada)                                                                                           |
| APNSCertificateExpired           | Dispositivos da Apple não podem ser geridos com um certificado de push de MDM da Apple expirado.                                                                                                                            |
## <a name="ownertypes"></a>OwnerTypes

A entidade **EnrollmentTypes** indica se um dispositivo é empresarial, pessoal ou desconhecido.

| Propriedade  | Descrição | Exemplo |
|---------|------------|--------|
| ownerTypeID |Identificador exclusivo do tipo de proprietário. | |
| ownerTypeKey |Identificador exclusivo do tipo de proprietário no armazém de dados – chave de substituição. | |
| ownerTypeName |Representa o tipo de proprietário dos dispositivos:  <br>Empresarial – dispositivo é propriedade da empresa. <br>Personal: o dispositivo é propriedade pessoal (BYOD).  <br>Unknown: não existem informações sobre este dispositivo. |Empresarial desconhecido pessoa |

> [!Note]  
> Para o `ownerTypeName` AzureAD quando criar grupos dinâmicos para dispositivos, terá de definir o valor de filtro `deviceOwnership` como `Company`. Para obter mais informações, consulte [regras para dispositivos](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership#rules-for-devices). 

## <a name="managementstates"></a>ManagementStates

A entidade **ManagementStates** fornece detalhes sobre o estado do dispositivo. Os detalhes podem ser úteis nos casos em que são aplicadas ações remotas ou quando o dispositivo foi desbloqueado por jailbreak ou rooting.

| Propriedade  | Descrição |
|---------|------------|
| managementStateID | Identificador exclusivo do estado de gestão. |
| managementStateKey | Identificador exclusivo do estado de gestão no armazém de dados – chave de substituição. |
| managementStateName | Indica o estado da ação remota aplicada a este dispositivo. |

### <a name="example"></a>Exemplo

| managementStateID  | Nome | Descrição |
|---------|------------|--------|
| 0 |Managed | Gerido sem ações remotas pendentes. |
| 1 |RetirePending | Existe um comando de extinção pendente para o dispositivo. |
| 2 |RetireFailed | O comando de extinção no dispositivo falhou. |
| 3 |WipePending | Existe um comando para apagar pendente para o dispositivo. |
| 4 |WipeFailed | O comando para apagar falhou no dispositivo. |
| 5 |Estado de funcionamento incorreto | Mau estado de funcionamento. |
| 6 |DeletePending | Existe um comando de eliminação pendente para o dispositivo. |
| 7 |RetireIssued | Foi emitido um comando de extinção para o dispositivo. |
| 8 |WipeIssued | Foi emitido um comando para apagar. |
| 9 |WipeCanceled | O comando para apagar foi cancelado. |
| 10 |RetireCanceled | O comando de extinção foi cancelado. |
| 11 |Discovered | O dispositivo foi detetado recentemente no Intune. Após dar entrada pela primeira vez será movido para o estado Managed. |

## <a name="managementagenttypes"></a>ManagementAgentTypes

A entidade **ManagementAgentTypes** representa os agentes utilizados para gerir um dispositivo.

| Propriedade  | Descrição |
|---------|------------|
| ManagementAgentTypeID | Identificador exclusivo do tipo de agente de gestão. |
| ManagementAgentTypeKey | Identificador exclusivo do tipo de agente de gestão no armazém de dados – chave de substituição. |
| ManagementAgentTypeName |Indica que tipo de agente é utilizado para gerir o dispositivo. |

### <a name="example"></a>Exemplo

| ManagementAgentTypeID  | Nome | Descrição |
|---------|------------|--------|
| 1 |EAS | O dispositivo é gerido através do Exchange Active Sync |
| 2 |MDM | O dispositivo é gerido através de um agente MDM |
| 3 |EasMdm | O dispositivo é gerido através do Exchange Active Sync e de um agente MDM |
| 4 |IntuneClient | O dispositivo é gerido pelo agente de PC do Intune |
| 5 |EasIntuneClient | O dispositivo é gerido através do Exchange Active Sync e do agente de PC do Intune |
| 8 |ConfigManagerClient | O dispositivo é gerido pelo agente do System Center Configuration Manager |
| 16 |Unknown | Tipo de agente de gestão desconhecido |

## <a name="devices"></a>Dispositivos

A entidade **Devices** lista todos os dispositivos inscritos sob gestão e as propriedades correspondentes.

|          Propriedade          |                                                                                       Descrição                                                                                      |
|:--------------------------:|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
| DeviceKey                  | Identificador exclusivo do dispositivo no armazém de dados – chave de substituição.                                                                                                               |
| DeviceId                   | Identificador exclusivo do dispositivo.                                                                                                                                                     |
| DeviceName                 | Nome do dispositivo nas plataformas que permitem atribuir um nome aos dispositivos. Noutras plataformas, o Intune cria um nome a partir de outras propriedades. O atributo não pode estar disponível para todos os dispositivos. |
| DeviceTypeKey              | Chave do atributo de tipo de dispositivo para este dispositivo.                                                                                                                                    |
| DeviceRegistrationState    | Chave do atributo de estado do registo do cliente para este dispositivo.                                                                                                                      |
| OwnerTypeKey               | Chave do atributo de tipo de proprietário para este dispositivo: corporate, personal ou unknown.                                                                                                    |
| EnrolledDateTime           | A data e hora em que o dispositivo foi inscrito.                                                                                                                                         |
| LastSyncDateTime           | Última entrada de dispositivo conhecida com o Intune.                                                                                                                                              |
| ManagementAgentKey         | Chave do agente de gestão associado a este dispositivo.                                                                                                                             |
| ManagementStateKey         | Chave do estado de gestão associado a este dispositivo a indicar o estado mais recente de uma ação remota ou se foi desbloqueado por jailbreak/rooting.                                                |
| AzureADDeviceId            | O deviceID do Azure para este dispositivo.                                                                                                                                                  |
| AzureADRegistered          | Se o dispositivo está registado no Azure Active Directory.                                                                                                                             |
| DeviceCategoryKey          | Chave da categoria associada a este dispositivo.                                                                                                                                     |
| DeviceEnrollmentType       | Chave do tipo de inscrição associado a este dispositivo, indicando o método de inscrição.                                                                                             |
| ComplianceStateKey         | Chave do estado de Conformidade associado a este dispositivo.                                                                                                                             |
| OSVersion                  | Versão do sistema operativo do dispositivo.                                                                                                                                                |
| EasDeviceId                | ID do Exchange ActiveSync do dispositivo.                                                                                                                                                  |
| serialNumber               | serialNumber                                                                                                                                                                           |
| UserId                     | O Identificador Exclusivo para o utilizador associado ao dispositivo.                                                                                                                           |
| RowLastModifiedDateTimeUTC | A data e hora em UTC em que este dispositivo foi modificado pela última vez no armazém de dados.                                                                                                       |
| Fabricante               | Fabricante do dispositivo                                                                                                                                                             |
| Model                      | Modelo do dispositivo                                                                                                                                                                    |
| OperatingSystem            | Sistema operativo do dispositivo. Windows, iOS, etc.                                                                                                                                   |
| IsDeleted                  | O binário para mostrar se o dispositivo é eliminado ou não.                                                                                                                                 |
| AndroidSecurityPatchLevel  | Nível do patch de segurança para Android                                                                                                                                                           |
| MEID                       | MEID                                                                                                                                                                                   |
| isSupervised               | Estado supervisionado do dispositivo                                                                                                                                                               |
| FreeStorageSpaceInBytes    | Armazenamento Livre em Bytes.                                                                                                                                                                 |
| TotalStorageSpaceInBytes   | Armazenamento Total em Bytes.                                                                                                                                                                |
| EncryptionState            | Estado de encriptação no dispositivo.                                                                                                                                                      |
| SubscriberCarrier          | Operadora subscritora do dispositivo                                                                                                                                                       |
| PhoneNumber                | Número de telefone do dispositivo                                                                                                                                                             |
| IMEI                       | IMEI                                                                                                                                                                                   |
| CellularTechnology         | Tecnologia de rede móvel do dispositivo                                                                                                                                                    |
| WiFiMacAddress             | MAC Wi-Fi                                                                                                                                                                              |

## <a name="devicepropertyhistory"></a>DevicePropertyHistory

A entidade **DevicePropertyHistory** tem as mesmas propriedades que a tabela de dispositivos e instantâneos diários de cada registo de dispositivo por dia, nos últimos 90 dias. A coluna DateKey indica o dia para cada linha.

|          Propriedade          |                                                                                      Descrição                                                                                     |
|:--------------------------:|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
| DateKey                    | Referência à tabela de data que indica o dia.                                                                                                                                          |
| DeviceKey                  | Identificador exclusivo do dispositivo no armazém de dados – chave de substituição. Esta é uma referência à tabela Dispositivos que contém o ID de dispositivo do Intune.                               |
| DeviceName                 | Nome do dispositivo nas plataformas que permitem atribuir um nome aos dispositivos. Noutras plataformas, o Intune cria um nome a partir de outras propriedades. O atributo não pode estar disponível para todos os dispositivos. |
| DeviceRegistrationStateKey | Chave do atributo de estado do registo do dispositivo para este dispositivo.                                                                                                                    |
| OwnerTypeKey               | Chave do atributo de tipo de proprietário para este dispositivo: corporate, personal ou unknown.                                                                                                  |
| ManagementStateKey         | Chave do estado de gestão associado a este dispositivo a indicar o estado mais recente de uma ação remota ou se foi desbloqueado por jailbreak/rooting.                                                |
| AzureADRegistered          | Se o dispositivo está registado no Azure Active Directory.                                                                                                                             |
| ComplianceStateKey         | Uma chave para o ComplianceState.                                                                                                                                                            |
| OSVersion                  | Versão do SO.                                                                                                                                                                          |
| JailBroken                 | Se o dispositivo está desbloqueado por jailbreak ou rooting.                                                                                                                                         |
| DeviceCategoryKey          | Chave do atributo da categoria do dispositivo para este dispositivo. 

## <a name="applicationinventory"></a>ApplicationInventory

A entidade **ApplicationInventory** lista as aplicações encontradas no dispositivo aquando da recolha do inventário.


|      Propriedade      |                       Descrição                        |
|--------------------|----------------------------------------------------------|
|     DeviceKey      |              Uma referência à tabela de dispositivos.               |
|   ApplicationKey   | ? (copiado de ExchangeDeviceService\DeviceApplication). |
|  ApplicationName   | ? (copiado de ExchangeDeviceService\DeviceApplication). |
| ApplicationVersion | ? (copiado de ExchangeDeviceService\DeviceApplication). |
|     BundleSize     | ? (copiado de ExchangeDeviceService\DeviceApplication). |

