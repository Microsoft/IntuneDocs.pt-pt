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
ms.openlocfilehash: 19ecbc632b924dda297b3692cabf5345b4724b30
ms.sourcegitcommit: 47c9af81c385c7e893fe5a85eb79cf08e69e6831
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/25/2020
ms.locfileid: "77575780"
---
# <a name="reference-for-devices-entities"></a>Referência para as entidades de dispositivos

A categoria **de dispositivos** contém entidades para dispositivos móveis que rastreiam informações como:

- Tipo de Dispositivo
- Estado do registo e inscrição dos dispositivos
- Propriedade dos dispositivos
- Estado da gestão dos dispositivos
- Estado de associação dos dispositivos ao Azure AD
- Estado de inscrição
- Informações sobre o histórico dos dispositivos
- Inventário das aplicações no dispositivo

## <a name="devicetypes"></a>deviceTypes

A entidade **dispositivoTypes** representa o tipo de dispositivo referenciado por outras entidades de armazém de dados. Normalmente, o tipo de dispositivo descreve o modelo do dispositivo, o fabricante ou ambos.

| Propriedade  | Description |
|---------|------------|
| deviceTypeID |Identificador exclusivo do tipo de dispositivo |
| deviceTypeKey |Identificador exclusivo do tipo de dispositivo no armazém de dados – chave de substituição |
| dispositivoTypeName |Tipo de Dispositivo |

### <a name="example"></a>Exemplo

| deviceTypeID  | Nome | Description |
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
| 15 |HoloLens |Dispositivo HoloLens |
| 16 |SurfaceHub |Dispositivo Surface Hub |
| 17 |AndroidForWork |Dispositivo Android gerido através do Proprietário do Perfil Android |
| 100 |Blackberry |Dispositivo Blackberry |
| 101 |Palm |Dispositivo Palm |
| 255 |Unknown |Tipo de dispositivo desconhecido |

## <a name="enrollmentactivities"></a>enrollmentActivities 
A entidade **de inscriçãoAtividade** indica a atividade de inscrição de um dispositivo.

| Propriedade                      | Description                                                               |
|-------------------------------|---------------------------------------------------------------------------|
| dateKey                       | Chave da data em que esta atividade de inscrição foi registada.               |
| deviceEnrollmentTypeKey       | Chave do tipo de inscrição.                                        |
| deviceTypeKey                 | Chave do tipo de dispositivo.                                                |
| enrollmentEventStatusKey      | Chave do estado indicando o sucesso ou falha da inscrição.    |
| enrollmentFailureCategoryKey  | Chave da categoria de falha de inscrição (se a matrícula falhar).        |
| enrollmentFailureReasonKey    | Chave do motivo de falha de inscrição (se a inscrição falhou).          |
| osVersion                     | A versão do sistema operativo do dispositivo.                               |
| count                         | Contagem total de atividades de inscrição correspondentes às classificações acima referidas.  |

## <a name="enrollmenteventstatuses"></a>enrollmentEventStatuses 
A entidade **de inscriçãoEventStatus** indica o resultado de uma inscrição no dispositivo.

| Propriedade                   | Description                                                                       |
|----------------------------|-----------------------------------------------------------------------------------|
| enrollmentEventStatusKey   | Identificador único do estado de inscrição no armazém de dados (chave de substituição)  |
| enrollmentEventStatusName  | O nome do estado de inscrição. Veja os exemplos abaixo.                            |

### <a name="example"></a>Exemplo

| enrollmentEventStatusName  | Description                            |
|----------------------------|----------------------------------------|
| Êxito                    | Uma inscrição bem sucedida do dispositivo         |
| Falhou                     | Uma inscrição falhada do dispositivo             |
| Não disponível              | O estado da inscrição não está disponível.  |

## <a name="enrollmentfailurecategories"></a>enrollmentFailureCategories 
A entidade **de Categoria de Falhas de Matrícula** indica porque é que uma matrícula do dispositivo falhou. 

| Propriedade                       | Description                                                                                 |
|--------------------------------|---------------------------------------------------------------------------------------------|
| enrollmentFailureCategoryKey   | Identificador único da categoria de falha de inscrição no armazém de dados (chave de substituição)  |
| enrollmentFailureCategoryName  | O nome da categoria de falha de inscrição. Veja os exemplos abaixo.                            |

### <a name="example"></a>Exemplo

| enrollmentFailureCategoryName   | Description                                                                                                   |
|---------------------------------|---------------------------------------------------------------------------------------------------------------|
| Não Aplicável                  | A categoria de falha de inscrição não é aplicável.                                                            |
| Não disponível                   | A categoria de falha de inscrição não está disponível.                                                             |
| Unknown                         | Erro desconhecido.                                                                                                |
| Autenticação                  | A autenticação falhou.                                                                                        |
| Autorização                   | A chamada foi autenticada, mas não autorizada a inscrever-se.                                                         |
| Validação de Contas               | Não validou a conta para inscrição. (Conta bloqueada, inscrição não ativada)                      |
| Validação de Utilizadores                  | O utilizador não pôde ser validado. (Utilizador não existe, licença em falta)                                           |
| DispositivoNotSuportado              | O dispositivo não é suportado para a gestão de dispositivos móveis.                                                         |
| InManutenção                   | A conta está na manutenção.                                                                                    |
| BadRequest                      | O cliente enviou um pedido que não é compreendido/suportado pelo serviço.                                        |
| FeatureNotSupported             | As características utilizadas por esta inscrição não são suportadas para esta conta.                                        |
| EnrollmentRestrictionsEnforced  | As restrições de inscrição configuradas pela administração bloquearam esta inscrição.                                          |
| Cliente Desligado              | O cliente cronometrado ou a inscrição foi abortado pelo utilizador final.                                                        |
| Abandono de Utilizadores                 | A inscrição foi abandonada pelo utilizador final. (Utilizador final começou a embarcar mas não o completou atempadamente)  |

## <a name="enrollmentfailurereasons"></a>enrollmentFailureReasons  
A entidade **RegistrationFailureReason** indica uma razão mais detalhada para uma falha de inscrição de dispositivos dentro de uma determinada categoria de falha.  

| Propriedade                     | Description                                                                               |
|------------------------------|-------------------------------------------------------------------------------------------|
| enrollmentFailureReasonKey   | Identificador único do motivo de falha de inscrição no armazém de dados (chave de substituição)  |
| enrollmentFailureReasonName  | O nome da razão de falha de inscrição. Veja os exemplos abaixo.                            |

### <a name="example"></a>Exemplo

| enrollmentFailureReasonName      | Description                                                                                                                                                                                            |
|----------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Não Aplicável                   | O motivo da falha de inscrição não é aplicável.                                                                                                                                                       |
| Não disponível                    | O motivo da falha de inscrição não está disponível.                                                                                                                                                        |
| Unknown                          | Erro desconhecido.                                                                                                                                                                                         |
| UserNotLicensed                  | O utilizador não foi encontrado em Intune ou não tem uma licença válida.                                                                                                                                     |
| UserUnknown                      | O utilizador não é conhecido de Intune.                                                                                                                                                                           |
| BulkAlreadyEnrolledDevice        | Apenas um utilizador pode inscrever um dispositivo. Este dispositivo foi previamente matriculado por outro utilizador.                                                                                                                |
| EnrollmentOnboardingIssue        | A autoridade de gestão de dispositivos móveis intune (MDM) ainda não está configurada.                                                                                                                                 |
| AppleChallengeIssue              | A instalação do perfil de gestão do iOS foi adiada ou falhou.                                                                                                                                         |
| AppleOnboardingIssue             | É necessário um certificado de push Apple MDM para se inscrever no Intune.                                                                                                                                       |
| Tampa de Dispositivo                        | O utilizador tentou inscrever mais dispositivos do que o máximo permitido.                                                                                                                                        |
| AuthenticationRequirementNotMet  | O serviço de inscrição intonou não autorizou este pedido.                                                                                                                                            |
| Tipo de Dispositivo não suportado            | Este dispositivo não satisfaz os requisitos mínimos para a inscrição intune.                                                                                                                                  |
| EnrollmentCriteriaNotMet         | Este dispositivo não se inscreveu devido a uma regra de restrição de inscrição configurada.                                                                                                                          |
| BulkDeviceNotPreregistered       | O identificador internacional de equipamentos móveis deste dispositivo (IMEI) ou número de série não foi encontrado.  Sem este identificador, os dispositivos são reconhecidos como dispositivos pessoais que estão atualmente bloqueados.  |
| FeatureNotSupported              | O utilizador estava a tentar aceder a uma funcionalidade que ainda não foi lançada para todos os clientes ou que não é compatível com a sua configuração Intune.                                                            |
| Abandono de Utilizadores                  | A inscrição foi abandonada pelo utilizador final. (Utilizador final começou a embarcar mas não o completou atempadamente)                                                                                           |
| APNSCertificadocado           | Os dispositivos apple não podem ser geridos com um certificado de push Apple MDM expirado.                                                                                                                            |
## <a name="ownertypes"></a>ownerTypes

A entidade **de inscriçãoType** indica se um dispositivo é corporativo, propriedade pessoal ou desconhecido.

| Propriedade  | Description | Exemplo |
|---------|------------|--------|
| ownerTypeID |Identificador exclusivo do tipo de proprietário. | |
| ownerTypeKey |Identificador exclusivo do tipo de proprietário no armazém de dados – chave de substituição. | |
| ownerTypeName |Representa o tipo de proprietário dos dispositivos:  <br>Corporate - dispositivo é propriedade da empresa. <br>Personal: o dispositivo é propriedade pessoal (BYOD).  <br>Unknown: não existem informações sobre este dispositivo. |Corporate Personal Unknown |

> [!Note]  
> Para o `ownerTypeName` no AzureAD ao criar Grupos Dinâmicos para dispositivos, é necessário definir o valor do filtro `deviceOwnership` como `Company`. Para mais informações, consulte [Regras para dispositivos](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership#rules-for-devices). 

## <a name="managementstates"></a>managementStates

A entidade **ManagementStates** fornece detalhes sobre o estado do dispositivo. Os detalhes podem ser úteis nos casos em que são aplicadas ações remotas ou quando o dispositivo foi desbloqueado por jailbreak ou rooting.

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

A entidade **ManagementAgentType** representa os agentes utilizados para gerir um dispositivo.

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
| 8 |ConfigManagerClient | O dispositivo é gerido pelo agente 'Gestor de Configuração' |
| 16 |Unknown | Tipo de agente de gestão desconhecido |

## <a name="devices"></a>dispositivos

A entidade de **dispositivos** lista todos os dispositivos matriculados sob gestão e respetivas propriedades.

|          Propriedade          |                                                                                       Description                                                                                      |
|:--------------------------:|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
| dispositivoChave                  | Identificador exclusivo do dispositivo no armazém de dados – chave de substituição.                                                                                                               |
| deviceId                   | Identificador exclusivo do dispositivo.                                                                                                                                                     |
| deviceName                 | Nome do dispositivo nas plataformas que permitem atribuir um nome aos dispositivos. Noutras plataformas, o Intune cria um nome a partir de outras propriedades. O atributo não pode estar disponível para todos os dispositivos. |
| deviceTypeKey              | Chave do atributo de tipo de dispositivo para este dispositivo.                                                                                                                                    |
| dispositivoRegistrationState    | Chave do atributo de estado do registo do cliente para este dispositivo.                                                                                                                      |
| ownerTypeKey               | Chave do atributo de tipo de proprietário para este dispositivo: corporate, personal ou unknown.                                                                                                    |
| enrolledDateTime           | A data e hora em que o dispositivo foi inscrito.                                                                                                                                         |
| lastSyncDateTime           | Última entrada de dispositivo conhecida com o Intune.                                                                                                                                              |
| managementAgentKey         | Chave do agente de gestão associado a este dispositivo.                                                                                                                             |
| managementStateKey         | Chave do estado de gestão associado a este dispositivo a indicar o estado mais recente de uma ação remota ou se foi desbloqueado por jailbreak/rooting.                                                |
| azureADDeviceId            | O deviceID do Azure para este dispositivo.                                                                                                                                                  |
| azureADRegistro          | Se o dispositivo está registado no Azure Active Directory.                                                                                                                             |
| deviceCategoryKey          | Chave da categoria associada a este dispositivo.                                                                                                                                     |
| dispositivoInscriçType       | Chave do tipo de inscrição associado a este dispositivo, indicando o método de inscrição.                                                                                             |
| complianceStateKey         | Chave do estado de Conformidade associado a este dispositivo.                                                                                                                             |
| osVersion                  | Versão do sistema operativo do dispositivo.                                                                                                                                                |
| easDeviceId                | Troque o ID ActiveSync do dispositivo.                                                                                                                                                  |
| serialNumber               | SerialNumber                                                                                                                                                                           |
| userId                     | O Identificador Exclusivo para o utilizador associado ao dispositivo.                                                                                                                           |
| rowLastModificadoDateTimeUTC | A data e hora em UTC em que este dispositivo foi modificado pela última vez no armazém de dados.                                                                                                       |
| fabricante               | Fabricante do dispositivo                                                                                                                                                             |
| modelo                      | Modelo do dispositivo                                                                                                                                                                    |
| operatingSystem            | Sistema operativo do dispositivo. Windows, iOS/iPadOS, etc.                                                                                                                                   |
| isDeleted                  | O binário para mostrar se o dispositivo é eliminado ou não.                                                                                                                                 |
| androidSecurityPatchLevel  | Nível do patch de segurança para Android                                                                                                                                                           |
| MEID                       | MEID                                                                                                                                                                                   |
| isSupervised               | Estado supervisionado do dispositivo                                                                                                                                                               |
| freeStorageSpaceInBytes    | Armazenamento Livre em Bytes.                                                                                                                                                                 |
| totalStorageSpaceInBytes   | Armazenamento Total em Bytes.                                                                                                                                                                |
| encryptionState            | Estado de encriptação no dispositivo.                                                                                                                                                      |
| subscritorCarrier          | Operadora subscritora do dispositivo                                                                                                                                                       |
| phoneNumber                | Número de telefone do dispositivo                                                                                                                                                             |
| IMEI                       | IMEI                                                                                                                                                                                   |
| tecnologia celular         | Tecnologia de rede móvel do dispositivo                                                                                                                                                    |
| WiFiMacAddress             | MAC Wi-Fi                                                                                                                                                                              |
| ICCD                       | Identificador de cartão de circuito integrado                                                                                                                                                     |

## <a name="devicepropertyhistories"></a>devicePropertyHistories

A entidade **do dispositivoPropertyHistory** tem as mesmas propriedades que a tabela de dispositivos e instantâneos diários de cada registo de dispositivos por dia nos últimos 90 dias. A coluna DateKey indica o dia para cada linha.

|          Propriedade          |                                                                                      Description                                                                                     |
|:--------------------------:|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
| dateKey                    | Referência à tabela de data que indica o dia.                                                                                                                                          |
| dispositivoChave                  | Identificador único do dispositivo no armazém de dados - chave de substituição. Esta é uma referência à tabela Dispositivos que contém o ID de dispositivo do Intune.                               |
| deviceName                 | Nome do dispositivo nas plataformas que permitem atribuir um nome aos dispositivos. Noutras plataformas, o Intune cria um nome a partir de outras propriedades. O atributo não pode estar disponível para todos os dispositivos. |
| deviceRegistrationStateKey | Chave do atributo de estado do registo do dispositivo para este dispositivo.                                                                                                                    |
| ownerTypeKey               | Chave do atributo de tipo de proprietário para este dispositivo: corporate, personal ou unknown.                                                                                                  |
| managementStateKey         | Chave do estado de gestão associado a este dispositivo a indicar o estado mais recente de uma ação remota ou se foi desbloqueado por jailbreak/rooting.                                                |
| azureADRegistro          | Se o dispositivo está registado no Azure Active Directory.                                                                                                                             |
| complianceStateKey         | Uma chave para o ComplianceState.                                                                                                                                                            |
| OSVersion                  | Versão do SO.                                                                                                                                                                          |
| prisãoQuebrado                 | Se o dispositivo está desbloqueado por jailbreak ou rooting.                                                                                                                                         |
| deviceCategoryKey          | Chave do atributo da categoria do dispositivo para este dispositivo. 

