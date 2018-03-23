---
title: Dispositivos – Armazém de Dados do Intune
titlesuffix: Microsoft Intune
description: Tópico de referência para a categoria Devices das coleções de entidades na API do Armazém de Dados do Intune.
keywords: Armazém de Dados do Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/14/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 6955E12D-70D7-4802-AE3B-8B276F01FA4F
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: d8a7aeba4170bf6640083b95562d644299693f31
ms.sourcegitcommit: 21db583d6a9d3c15a8a8ee5579309dff1cfe1f8b
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/16/2018
---
# <a name="reference-for-devices-entities"></a>Referência para as entidades de dispositivos

A categoria **Devices** contém entidades para dispositivos móveis que registam informações como:

  -  Tipo de dispositivo
  -  Estado do registo e inscrição dos dispositivos
  -  Propriedade dos dispositivos
  -  Estado da gestão dos dispositivos
  -  Estado de associação dos dispositivos ao Azure AD
  -  Estado de inscrição
  -  Informações sobre o histórico dos dispositivos
  -  Inventário das aplicações no dispositivo

## <a name="devicetypes"></a>DeviceTypes

A entidade **DeviceTypes** representa o tipo de dispositivo referenciado por outras entidades do armazém de dados. Normalmente, o tipo de dispositivo descreve o modelo do dispositivo, o fabricante ou ambos.

| Propriedade  | Descrição |
|---------|------------|
| DeviceTypeID |Identificador exclusivo do tipo de dispositivo |
| DeviceTypeKey |Identificador exclusivo do tipo de dispositivo no armazém de dados – chave de substituição |
| DeviceTypeName |Tipo de dispositivo |

## <a name="example"></a>Exemplo

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
| 15 |HoloLens |Dispositivo Holo Lens |
| 16 |SurfaceHub |Dispositivo Surface Hub |
| 17 |AndroidForWork |Dispositivo Android gerido através do Proprietário do Perfil Android for Work |
| 100 |Blackberry |Dispositivo Blackberry |
| 101 |Palm |Dispositivo Palm |
| 255 |Unknown |Tipo de dispositivo desconhecido |

## <a name="clientregistrationstatetypes"></a>ClientRegistrationStateTypes

A entidade **ClientRegistrationStateTypes** representa o tipo de registo referenciado por outras tabelas do armazém de dados.

| Propriedade  | Descrição |
|---------|------------|
| clientRegisterationStateID |Identificador exclusivo para o estado do registo |
| clientRegisterationStateKey |Identificador exclusivo do estado do registo no armazém de dados – chave de substituição |
| clientRegisterationStateName |Estado do registo |

## <a name="example"></a>Exemplo

| ClientRegisterationStateID  | Nome | Descrição |
|---------|------------|--------|
| 0 |NotRegistered |Não registado |
| 1 |SMSIDConflict |Conflito de ID SMS |
| 2 |Registered |Registado |
| 3 |Revoked |Este estado significa que o administrador de TI bloqueou o cliente e o cliente pode ser desbloqueado. Um dispositivo também pode estar em estado Revoked após ser apagado ou extinto. |
| 4 |KeyConflict |Conflito de chaves |
| 5 |ApprovalPending |Aprovação pendente |
| 6 |ResetCert |Repor Certificado |
| 7 |NotRegisteredPendingEnrollment |Não registado, inscrição pendente |
| 8 |Unknown |Estado desconhecido |

## <a name="enrollmenttypes"></a>EnrollmentTypes

A entidade **EnrollmentTypes** indica como um dispositivo foi inscrito. O tipo de inscrição captura o método de inscrição. Os exemplos listam os diferentes tipos de inscrição e o seu significado.

| Propriedade  | Descrição |
|---------|------------|
| managementStateID |Identificador exclusivo do estado de gestão. |
| managementStateKey |Identificador exclusivo do estado de gestão no armazém de dados – chave de substituição. |
| managementStateName |Indica o estado da ação remota aplicada a este dispositivo. |

## <a name="example"></a>Exemplo

| enrollmentTypeID  | Nome | Descrição |
|---------|------------|--------|
| 0 |Unknown |Não foi recolhido o tipo de inscrição |
| 1 |UserEnrollment |Inscrição iniciada pelo utilizador |
| 2 |DeviceEnrollment |Inscrição de dispositivo com perfil sem utilizador |
| 3 |DeviceEnrollmentWithUDA |Inscrição de dispositivo com perfil UDA. |
| 4 |AzureDomainJoined |Inscrição de dispositivo iniciada pelo utilizador através do Azure Active Directory |
| 5 |UserEnrollmentWithServiceAccount |Inscrição iniciada pelo utilizador através da conta de serviço |
| 6 |DepDeviceEnrollment |Inscrição de Dispositivo DEP com perfil sem utilizador |
| 7 |DepDeviceEnrollmentWithUDA |Inscrição de Dispositivo DEP com perfil UDA |
| 8 |AutoEnrollment |Inscrição DRS e MDM combinada para cenário BYOD |

## <a name="ownertypes"></a>OwnerTypes

A entidade **EnrollmentTypes** indica se um dispositivo é empresarial, pessoal ou desconhecido.

| Propriedade  | Descrição | Exemplo |
|---------|------------|--------|
| ownerTypeID |Identificador exclusivo do tipo de proprietário. | |
| ownerTypeKey |Identificador exclusivo do tipo de proprietário no armazém de dados – chave de substituição. | |
| ownerTypeName |Representa o tipo de proprietário dos dispositivos:  <br>Company: o dispositivo é propriedade da empresa. <br>Personal: o dispositivo é propriedade pessoal (BYOD).  <br>Unknown: não existem informações sobre este dispositivo. |Company Personal Unknown |

## <a name="mdmstatuses"></a>MdmStatuses

A entidade **MdmStatuses** indica o estado de conformidade do dispositivo.

| Propriedade  | Descrição |
|---------|------------|
| MdmStatusID |Identificador exclusivo do estado de conformidade |
| MdmStatusKey |Identificador exclusivo do estado de conformidade no armazém de dados – chave de substituição | 
| ComplianceStatus |Estado de conformidade do dispositivo. Deve ter um dos valores da tabela abaixo | 


## <a name="example"></a>Exemplo

| MdmStatusID  | ComplianceStatus | Descrição |
|---------|------------|--------|
| 0 |Unknown |O estado de conformidade do dispositivo é desconhecido. |
| 1 |Compatível |O dispositivo está em conformidade. |
| 2 |Não compatível |O dispositivo não está em conformidade. |
| 3 |Conflito |A conformidade do dispositivo resultou num conflito. |
| 4 |Error |Ocorreu um erro ao ler o estado de conformidade do dispositivo. |


## <a name="managementstates"></a>ManagementStates

A entidade **ManagementStates** fornece detalhes sobre o estado do dispositivo. Os detalhes podem ser úteis nos casos em que são aplicadas ações remotas ou quando o dispositivo foi desbloqueado por jailbreak ou rooting.

| Propriedade  | Descrição |
|---------|------------|
| managementStateID | Identificador exclusivo do estado de gestão. |
| managementStateKey | Identificador exclusivo do estado de gestão no armazém de dados – chave de substituição. |
| managementStateName | Indica o estado da ação remota aplicada a este dispositivo. |

## <a name="example"></a>Exemplo

| managementStateID  | Nome | Descrição |
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

## <a name="workplacejoinstatetypes"></a>WorkPlaceJoinStateTypes

A entidade **WorkPlaceJoinStateTypes** representa o estado de Associação à Área de Trabalho do Azure Active Directory do dispositivo.  O fluxo de trabalho de inscrição pode utilizar um ou mais certificados para verificar ou autenticar. Quando a Área de Trabalho de um dispositivo for inscrita, estes certificados são utilizados para validar o dispositivo e o utilizador. A emissão dos certificados é fornecida através de um servidor SCEP (Serviço de Inscrição de Dispositivos de Rede). Os valores na entidade indicam os diversos estados em que um dispositivo pode estar durante este processo. Alguns destes estados incluem falhas de associação à Área de Trabalho devido à falha na emissão de um certificado obrigatório (de um servidor SCEP). Se um dispositivo nunca tiver passado por este fluxo de trabalho, o valor é definido como Unknown.

| Propriedade  | Descrição |
|---------|------------|
| WorkPlaceJoinStateID | Identificador exclusivo do estado de associação à área de trabalho |
| WorkPlaceJoinStateKey | Identificador exclusivo do estado de associação à área de trabalho no armazém de dados – chave de substituição |
| WorkPlaceJoinStateName | Estado de associação à área de trabalho |

## <a name="example"></a>Exemplo

| workPlaceJoinStateID  | Nome | Descrição |
|---------|------------|--------|
| 0 |Unknown |Se um dispositivo não estiver associado à área de trabalho, o estado será Unknown |
| 1 |Succeeded |Associado à área de trabalho com êxito |
| 2 |FailureToGetScepMetadata |Falha ao obter os metadados SCEP |
| 3 |FailureToGetScepChallenge |Falha ao obter o desafio SCEP |
| 4 |DeviceFailureToInstallScepCommand |Falha ao instalar o comando SCEP no dispositivo |
| 5 |DeviceFailureToGetCertificate |O dispositivo não conseguiu obter o certificado através do SCEP |
| 6 |DeviceScepPending |Estado pendente; o dispositivo ainda está a efetuar o SCEP |
| 7 |DeviceScepFailed |O dispositivo não conseguiu instalar o certificado através do SCEP |
| 8 |AADValidationFailed |Existe uma falha ao validar o dispositivo no AAD |

## <a name="managementagenttypes"></a>ManagementAgentTypes

A entidade **ManagementAgentTypes** representa os agentes utilizados para gerir um dispositivo.

| Propriedade  | Descrição |
|---------|------------|
| ManagementAgentTypeID | Identificador exclusivo do tipo de agente de gestão. |
| ManagementAgentTypeKey | Identificador exclusivo do tipo de agente de gestão no armazém de dados – chave de substituição. |
| ManagementAgentTypeName |Indica que tipo de agente é utilizado para gerir o dispositivo. |

## <a name="example"></a>Exemplo

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

| Propriedade  | Descrição |
|---------|------------|
| DeviceKey | Identificador exclusivo do dispositivo no armazém de dados – chave de substituição. |
| DeviceId | Identificador exclusivo do dispositivo. |
| DeviceName | Nome do dispositivo nas plataformas que permitem atribuir um nome aos dispositivos. Noutras plataformas, o Intune cria um nome a partir de outras propriedades. O atributo não pode estar disponível para todos os dispositivos. |
| DeviceTypeKey | Chave do atributo de tipo de dispositivo para este dispositivo. |
| ClientRegisterationStateKey | Chave do atributo de estado do registo do cliente para este dispositivo. |
| OwnerTypeKey | Chave do atributo de tipo de proprietário para este dispositivo: corporate, personal ou unknown. |
| objectSourceKey | Ignore esta coluna. |
| CreatedDate | Data em que o dispositivo foi inscrito. |
| LastContact | Última entrada de dispositivo conhecida com o Intune. |
| LastContactNotification | Última vez que o Intune notificou o dispositivo para dar entrada com o Intune. |
| LastContactWorkplaceJoin | O carimbo de data/hora a indicar o último estado conhecido de Associação à Área de Trabalho deste dispositivo. |
| ManagementAgentKey | Chave do agente de gestão associado a este dispositivo. |
| ManagementStateKey | Chave do estado de gestão associado a este dispositivo a indicar o estado mais recente de uma ação remota ou se foi desbloqueado por jailbreak/rooting. |
| ReferenceId | O ID do dispositivo no Azure Active Directory. |
| WorkPlaceJoinStateKey | Chave do estado de associação à área de trabalho deste dispositivo. |
| CategoryId | Ignore esta coluna. |
| EnrollmentTypeKey | Chave do tipo de inscrição associado a este dispositivo, indicando o método de inscrição. |
| CertExpirationDate | Data de expiração do certificado de gestão MDM. |
| MdmStatusKey | Uma chave para MdmStatus. |
| OSFamily | Família do SO (Windows, iOS, Android, etc.) |
| OSVersion | Versão do SO |
| OSMajorVersion | Componente de versão principal da versão do SO (major.minor.build.revision). |
| OSMinorVersion | Componente de versão secundária da versão do SO (major.minor.build.revision). |
| OSBuildNumber | Componente de versão de compilação da versão do SO (major.minor.build.revision). |
| OSRevisionNumber | Componente de versão de revisão da versão do SO (major.minor.build.revision). |
| EasID | O ID EAS do dispositivo, se o dispositivo for gerido pelo Exchange Active Sync. |
| GraphDeviceIsManaged | O último estado de gestão que o Intune definiu no Azure AD. |
| GraphDeviceIsCompliant | O último estado de conformidade que o Intune definiu no Azure AD. |
| SerialNumber | Número de série do dispositivo, se disponível. |
| EnrolledByUser | O ID do utilizador que inscreveu este dispositivo e que referencia a coluna UserId na tabela User. |
| RowLastModifiedDateTimeUTC | A última vez em que este registo foi modificado. |
| ProcessorArchitecture | Arquitetura do processador. |
| DeviceAction | A última ação de dispositivo emitida, Ignorar por enquanto. |
| Manufacturer | Fabricante do dispositivo. |
| Model | Modelo do dispositivo. |
| LastPolicyUpdateUtc | Última vez que a política foi atualizada no dispositivo. |
| LastExchangeStatusUtc | A última vez que o dispositivo foi sincronizado com o Exchange. |
| IsDeleted | Definido como True se o dispositivo já não for gerido pelo Intune. Mantém o último estado conhecido. |

## <a name="devicepropertyhistory"></a>DevicePropertyHistory

A entidade **DevicePropertyHistory** tem as mesmas propriedades que a tabela de dispositivos e instantâneos diários de cada registo de dispositivo por dia, nos últimos 90 dias. A coluna DateKey indica o dia para cada linha.

| Propriedade  | Descrição |
|---------|------------|
| DateKey |Referência à tabela de data que indica o dia. |
| DeviceKey |Identificador exclusivo do dispositivo no armazém de dados – chave de substituição. Esta é uma referência à tabela Dispositivos que contém o ID de dispositivo do Intune. |
| DeviceName |Nome do dispositivo nas plataformas que permitem atribuir um nome aos dispositivos. Noutras plataformas, o Intune cria um nome a partir de outras propriedades. O atributo não pode estar disponível para todos os dispositivos. |
| DeviceTypeKey |Chave do atributo de tipo de dispositivo para este dispositivo. |
| ClientRegisterationStateKey |Chave do atributo de estado do registo do cliente para este dispositivo. |
| OwnerTypeKey |Chave do atributo de tipo de proprietário para este dispositivo: corporate, personal ou unknown. |
| objectSourceKey |Ignore esta coluna. |
| CreatedDate |Data em que o dispositivo foi inscrito. |
| LastContact |Última entrada de dispositivo conhecida com o Intune. |
| LastContactNotification |Última vez que o Intune notificou o dispositivo para dar entrada com o Intune. |
| LastContactWorkplaceJoin |O carimbo de data/hora a indicar o último estado conhecido de Associação à Área de Trabalho deste dispositivo. |
| ManagementAgentKey |Chave do agente de gestão associado a este dispositivo. |
| ManagementStateKey |Chave do estado de gestão associado a este dispositivo a indicar o estado mais recente de uma ação remota ou se foi desbloqueado por jailbreak/rooting. |
| ReferenceId |O ID do dispositivo no Azure Active Directory. |
| WorkPlaceJoinStateKey |Chave do estado de associação à área de trabalho deste dispositivo. |
| CategoryId |Ignore esta coluna. |
| EnrollmentTypeKey |Chave do tipo de inscrição associado a este dispositivo, indicando o método de inscrição. |
| CertExpirationDate |Data de expiração do certificado de gestão MDM. |
| MdmStatusKey |Uma chave para MdmStatus. |
| OSFamily |Família do SO (Windows, iOS, Android, etc.) |
| OSVersion |Versão do SO. |
| OSMajorVersion |Componente de versão principal da versão do SO (major.minor.build.revision). |
| OSMinorVersion |Componente de versão secundária da versão do SO (major.minor.build.revision). |
| OSBuildNumber |Componente de versão de compilação da versão do SO (major.minor.build.revision). |
| OSRevisionNumber |Componente de versão de revisão da versão do SO (major.minor.build.revision). |
| EasID |O ID EAS do dispositivo, se o dispositivo for gerido pelo Exchange Active Sync. |
| GraphDeviceIsManaged |O último estado de gestão que o Intune definiu no Azure AD. |
| GraphDeviceIsCompliant |O último estado de conformidade que o Intune definiu no Azure AD. |
| SerialNumber |Número de série do dispositivo, se disponível. |
| EnrolledByUser |O ID do utilizador que inscreveu este dispositivo e que referencia a coluna UserId na tabela User. |
| RowLastModifiedDateTimeUTC |A última vez em que este registo foi modificado. |
| ProcessorArchitecture |Arquitetura do processador. |
| DeviceAction |A última ação de dispositivo emitida, Ignorar por enquanto. |
| Manufacturer |Fabricante do dispositivo. |
| Model |Modelo do dispositivo. |
| LastPolicyUpdateUtc |Última vez que a política foi atualizada no dispositivo. |
| LastExchangeStatusUtc |A última vez que o dispositivo foi sincronizado com o Exchange. |

## <a name="mdmdeviceinventoryhistories"></a>MdmDeviceInventoryHistories

A entidade **MdmDeviceInventoryHistories** contém instantâneos diários dos dados de inventário de dispositivos geridos por MDM nos últimos 90 dias. A coluna DateKey indica o dia da linha. Algumas propriedades poderão não ser aplicáveis ou estar preenchidas para todos os dispositivos, pelo que deverá consultar esta página para obter detalhes. Para mais informações, consulte [Compreender os dispositivos com inventário no Microsoft Intune](https://docs.microsoft.com/Intune-classic/deploy-use/understand-your-devices-with-inventory-in-microsoft-Intune).

| Propriedade  | Descrição |
|---------|------------|
| DateKey | Referência à tabela de data que indica o dia. |
| DeviceKey |Identificador exclusivo do dispositivo no armazém de dados – chave de substituição. Esta é uma referência à tabela Dispositivos que contém o ID de dispositivo do Intune. |
| DeviceModel |Modelo do dispositivo. |
| SO |SO do dispositivo. |
| DeviceName |Nome do dispositivo nas plataformas que permitem atribuir um nome aos dispositivos. Noutras plataformas, o Intune cria um nome a partir de outras propriedades. O atributo não pode estar disponível para todos os dispositivos. |
| SoftwareVersion |Na maioria dos casos, esta é a versão do SO, exceto nas plataformas Apple em que difere da versão do SO. |
| Imei |Número IMEI |
| HardwareInventoryTimeUtc |A primeira vez que o inventário foi reportado para este dispositivo. |
| InventoryModifiedTimeUtc |A última vez que o inventário foi armazenado quando este instantâneo foi tirado. |
| InventoryReportingTimeUtc |A última vez em que o inventário foi recolhido para este dispositivo. |
| ExchangeActiveSyncId |ID de Dispositivo do Exchange ActiveSync. |
| ComputerSystemDescription |Descrição do Sistema. |
| ComputerSystemName |Nome do Sistema. |
| ComputerSystemManufacturer |Fabricante do Sistema. |
| ComputerSystemModel |Modelo do Sistema. |
| UserName |Nome de utilizador. |
| OSType |Tipo de SO. |
| OSCaption |Legenda de SO. |
| OSName |Nome do SO. |
| OSManufacturer |Fabricante de SO. |
| OSProductSuite |Pacote de Produto de SO. |
| OSProductType |Tipo de Produto de SO. |
| Locale |Região de SO. |
| PhysicalMemoryCapacity |Capacidade de Memória Física (em bytes). |
| PhysicalMemoryRemovable |Memória Amovível Física (em bytes). |
| SystemEnclosureChassisTypesInnerText |Define o tipo de chassis de sistema para este dispositivo. Os números indicam os seguintes valores:  <br>0 ou vazio = Desconhecido   <br>1 = É um Computador   <br>2 = É um Portátil  <br>3 = É uma Estação de Trabalho  <br>4 = É um Servidor Empresarial  <br>100 = É um Telemóvel  <br>101 = É um Tablet  <br>102/103 = Outro tipo desconhecido de Dispositivo Móvel |
| SystemEnclosureModel |Modelo de Bastidor do Sistema. |
| SystemEnclosureSerialNumber |Número de Série de Bastidor do Sistema. |
| NetworkAdapterConfigurationText |Texto de configuração do adaptador de rede. |
| MacAddress |Endereço MAC. |
| SmsID |ID de dispositivo do Intune. |
| CertExpiry |Data de expiração do certificado de gestão MDM. |
| DeviceClientAgentVersion |Versão do Agente do Cliente. |
| DeviceClientID |ID de Cliente do Dispositivo. |
| SerialNumber |Número de Série. |
| DeviceManufacturer |Fabricante do Dispositivo. |
| DMVersion |Versão de DM. |
| FirmwareVersion |Versão de Firmware. |
| HardwareVersion |Versão de Hardware. |
| PlatformType |Tipo de Plataforma. |
| ProcessorLevel |Nível do Processador. |
| ProcessorRevision |Revisão do Processador. |
| Product |Produto. |
| ProductVersion |Versão do Produto. |
| OEM |Fabricante de Equipamento Original. |
| DeviceBuildVersion |Versão da Compilação do Dispositivo. |
| Meid |Identificador de equipamento móvel. |
| PhoneNumber |Número de telefone. |
| SubscriberCarrierNetwork |Nome de Rede da Operadora Telefónica. |
| CellularTechnology |Tipo de Rede da Operadora Telefónica (CDMA/GSM). |
| Imsi |Número IMSI. |
| JailBroken |True se o dispositivo estiver desbloqueado por Jailbreak ou Rooting. |
| IsActivationLockEnabled |True se o Bloqueio de Ativação estiver Ativado |
| DeviceType |Tipo de Dispositivo |
| IsSupervised |É supervisionado |
| DeviceDisplayNumberOfColors |Número de cores do ecrã do dispositivo |
| HorizontalResolution |Resolução de ecrã horizontal do dispositivo |
| VerticalResolution |Resolução de ecrã vertical do dispositivo |
| StorageFree |Armazenamento livre (em bytes) |
| StorageTotal |Armazenamento total (em bytes) |
| ProgramFree |Memória de Programa Livre (em bytes) |
| ProgramTotal |Memória de Programa Total (em bytes) |
| RemovableStorageFree |Armazenamento amovível livre (em bytes) |
| RemovableStorageTotal |Armazenamento amovível total (em bytes) |
| DeviceMemoryDeviceCapacity |Capacidade de memória do dispositivo |
| DeviceMemoryAvailableDeviceCapacity |Capacidade disponível de memória do dispositivo |
| DeviceOSVersion |Versão do SO |
| DeviceOSPlatform |Plataforma do SO |
| DeviceOSLanguage |Idioma do SO |
| PasswordMaxAttemptsBeforeWipe |Máximo de tentativas de palavra-passe permitido antes de apagar o dispositivo |
| PasswordMinComplexChars |Número mínimo de carateres complexos necessários na palavra-passe |
| PasswordMinLength |Comprimento mínimo necessário da palavra-passe |
| PasswordHistory |Palavra-passe – mínimo de palavras-passe históricas não aceites |
| PasswordEnabled |Palavra-passe – ativada? |
| PasswordExpiration |Palavra-passe – data de expiração. |
| AllowRecoveryPassword |Permitir a recuperação da palavra-passe. |
| PasswordAutoLockTimeout |Palavra-passe – tempo limite de bloqueio automático. |
| PasswordType |Tipo de Palavra-Passe. |
| BacklightACTimeout |Limite de tempo de retroiluminação quando ligado a uma fonte de alimentação. |
| BacklightBatTimeout |Limite de tempo de retroiluminação ao usar a bateria. |
| PowerBackupPercent |Percentagem de energia alternativa. |
| BatteryPercent |Percentagem de bateria restante. |
| PlatformID |ID da Plataforma. |
| ExchangeDeviceID |ID de Dispositivo do Exchange. |
| SmsProcessorDescription |Descrição de processador. |
| OwnerEmailAddress |Endereço de e-mail do proprietário. |
| DeviceOSName |Nome do SO. |
| WifiMac |Endereço Wi-Fi para Mac. |
| EthernetMac |Endereço MAC Ethernet. |
| RequireEncryption |Indica se o dispositivo está ou não encriptado. |
| ActivationLockBypassCode |Código para ignorar o bloqueio de ativação. |

## <a name="applicationinventory"></a>ApplicationInventory

A entidade **ApplicationInventory** lista as aplicações encontradas no dispositivo aquando da recolha do inventário.

| Propriedade  | Descrição |
|---------|------------|
| DeviceKey |Uma referência à tabela de dispositivos. |
| ApplicationKey |? (copiado de ExchangeDeviceService\DeviceApplication). |
| ApplicationName |? (copiado de ExchangeDeviceService\DeviceApplication). |
| ApplicationVersion |? (copiado de ExchangeDeviceService\DeviceApplication). |
| BundleSize |? (copiado de ExchangeDeviceService\DeviceApplication). |
