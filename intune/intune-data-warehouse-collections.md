---
title: Coleções do Armazém de Dados do Intune
titlesuffix: Microsoft Intune
description: As coleções do Armazém de Dados do Intune proporcionam detalhes relacionados com a API do Armazém de Dados.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/04/2018
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 29f09230-dc56-43db-b599-d961967bda49
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune
ms.openlocfilehash: 4df55309587ac079cfeaec299d70635b090e300b
ms.sourcegitcommit: 443b4cb3390da47bf1e497b1f0c0137a5ddda7bd
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/06/2018
ms.locfileid: "43821636"
---
#  <a name="intune-data-warehouse-collections"></a>Coleções do Armazém de Dados do Intune

As seguintes coleções do Armazém de Dados do Intune proporciona as propriedades, descrições e exemplos para coleções v1.0 das entidades da API do Armazém de Dados. 

## <a name="apprevisions"></a>appRevisions
A entidade **appRevision** apresenta uma lista de todas as versões das aplicações.

|          Propriedade          |                                      Descrição                                      |                Exemplo               |
|:--------------------------:|:-------------------------------------------------------------------------------------:|:------------------------------------:|
| AppKey                     | Identificador exclusivo da Aplicação.                                                         | 123                                  |
| ApplicationID              | Identificador exclusivo da Aplicação – semelhante à AppKey, mas esta é uma chave natural.        | b66bc706-ffff-7437-0340-032819502773 |
| Revision                   | A versão como mencionada pelo administrador durante o carregamento do binário.                   | 2                                    |
| Title                      | Nome da aplicação.                                                                     | Excel                                |
| Publisher                  | Publicador da aplicação.                                                                 | Microsoft                            |
| UploadState                | Estado de carregamento da aplicação.                                                              | 1                                    |
| AppTypeKey                 | Referência ao AppType descrito na secção seguinte.                            | 1                                    |
| VppProgramTypeKey          | Referência ao VppProgramType descrito abaixo.                                        | 30876                                |
| CreationTime               | A hora em que esta revisão foi criada.                                            | 11/23/2016 0:00                      |
| ModifiedTime               | A última vez em que algo relacionado com esta revisão foi alterado.                            | 11/23/2016 0:00                      |
| Size                       | Tamanho do binário em bytes.                                                          | 120 392 000                          |
| StartDateInclusiveUTC      | Data e hora em UTC em que a revisão da Aplicação foi criada no armazém de dados.      | 11/23/2016 0:00                      |
| EndDateExclusiveUTC        | Data e hora em UTC em que a revisão desta aplicação se tornou obsoleta.                        | 11/23/2016 0:00                      |
| IsCurrent                  | Indica se a versão desta Aplicação é atual ou não no armazém de dados.         | True/False                           |
| RowLastModifiedDateTimeUTC | Data e hora em UTC em que esta versão da aplicação foi modificada pela última vez no armazém de dados. | 11/23/2016 0:00                      |

## <a name="apptypes"></a>appTypes
A entidade **appType** apresenta uma lista da origem da instalação de uma aplicação.

|   Propriedade  |        Descrição        |
|:-----------:|:-------------------------:|
| AppTypeID   | ID do tipo           |
| AppTypeKey  | Chave de substituição da chave |
| AppTypeName | Tipo de aplicação                  |

### <a name="example"></a>Exemplo

| AppTypeID |                Nome               |                     Descrição                     |
|:---------:|:---------------------------------:|:---------------------------------------------------:|
| 0         | Aplicação da loja Android               | Uma aplicação da loja Android.                             |
| 1         | Aplicação LOB Android                 | Uma aplicação de linha de negócios Android.                  |
| 2         | Aplicação gerida da loja Android (MAM) | Uma aplicação da loja Android com gestão ativada. |
| 3         | Aplicação da loja iOS                   | Uma aplicação da loja iOS.                                 |
| 4         | Aplicação LOB iOS                     | Uma aplicação de linha de negócios iOS.                      |
| 5         | Aplicação da loja iOS gerida (MAM)     | Uma aplicação da loja iOS com gestão ativada.       |
| 6         | O365 Pro Plus Suite             | O Office 365 Pro Plus Suite para Windows 10.     |
| 7         | Aplicação Web                         | Uma aplicação Web.                                        |
| 8         | Aplicação da loja Windows Phone 8.1     | Uma aplicação da loja Windows Phone 8.1.                    |
| 9         | Aplicação da loja Windows               | Uma aplicação da loja Windows.                              |
| 10        | Aplicação LOB do Windows                | Uma aplicação de linha de negócio AppX do Windows.              |
| 11        | Windows Mobile MSI              | Uma aplicação de linha de negócios MSI.                      |
| 12        | Aplicação LOB para Windows Phone           | Uma aplicação de linha de negócio do Windows Phone.             |

## <a name="compliancepolicystatusdeviceactivities"></a>compliancePolicyStatusDeviceActivities
A tabela seguinte apresenta um resumo dos estados de atribuição de políticas de conformidade a dispositivos. Esta tabela indica a contagem de dispositivos detetados em cada estado de conformidade.

|    Propriedade   |                                                                                      Descrição                                                                                     |  Exemplo |
|:-------------:|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|:--------:|
| DateKey       | Chave da data em que o resumo da política de conformidade foi criado.                                                                                                                   | 20161204 |
| Unknown       | Número de dispositivos que estão offline ou que não conseguiram comunicar com o Intune ou o Azure AD por outros motivos.                                                                           | 5        |
| NotApplicable | Número de dispositivos em que as políticas de conformidade visadas pelo administrador não são aplicáveis.                                                                                     | 201      |
| Compatível     | Número de dispositivos que aplicaram com êxito uma ou mais políticas de conformidade do dispositivo visadas pelo administrador.                                                                        | 4083     |
| InGracePeriod | Número de dispositivos que não estão em conformidade, embora se encontrem no período de tolerância definido pelo administrador.                                                                                  | 57       |
| NonCompliant  | Número de dispositivos que não conseguiram aplicar uma ou mais definições de políticas de conformidade do dispositivo visadas pelo administrador ou nos quais o utilizador ainda não está a cumprir as políticas visadas pelo administrador. | 43       |
|    Error      |    Número de dispositivos que não conseguiram comunicar com o Intune ou o Azure AD e devolveram uma mensagem de erro.                                                                          |    3     |

## <a name="compliancepolicystatusdeviceperpolicyactivities"></a>compliancePolicyStatusDevicePerPolicyActivities
A tabela seguinte apresenta um resumo dos estados de atribuição de políticas de conformidade a dispositivos por política e por tipo de política. Esta tabela indica a contagem de dispositivos detetados em cada estado de conformidade para todas as políticas de conformidade atribuídas.

|      Propriedade     |                                                                                      Descrição                                                                                     |  Exemplo |
|:-----------------:|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|:--------:|
| DateKey           | Chave da data em que o resumo da política de conformidade foi criado.                                                                                                                   | 20161219 |
| PolicyKey         | Chave da política de conformidade para a qual o resumo foi criado.                                                                                                                   | 10178    |
| PolicyPlatformKey | Chave do tipo de plataforma da política de conformidade para a qual o resumo foi criado.                                                                                            | 5        |
| Unknown           | Número de dispositivos que estão offline ou que não conseguiram comunicar com o Intune ou o Azure AD por outros motivos.                                                                           | 13       |
| NotApplicable     | Número de dispositivos em que as políticas de conformidade visadas pelo administrador não são aplicáveis.                                                                                     | 3        |
| Compatível         | Número de dispositivos que aplicaram com êxito uma ou mais políticas de conformidade do dispositivo visadas pelo administrador.                                                                        | 45       |
| InGracePeriod     | Número de dispositivos que não estão em conformidade, embora se encontrem no período de tolerância definido pelo administrador.                                                                                  | 3        |
| NonCompliant      | Número de dispositivos que não conseguiram aplicar uma ou mais definições de políticas de conformidade do dispositivo visadas pelo administrador ou nos quais o utilizador ainda não está a cumprir as políticas visadas pelo administrador. | 7        |
| Error             | Número de dispositivos que não conseguiram comunicar com o Intune ou o Azure AD e devolveram uma mensagem de erro.                                                                             | 3        |
## <a name="compliancestates"></a>complianceStates

|      Propriedade      |                       Descrição                      |
|:------------------:|:------------------------------------------------------:|
| complianceStatus   | Estado de conformidade de dispositivos com mdmStatusKey       |
| complianceStateKey | Chave de conformidade para corresponder ao estado do dispositivo e de conformidade |
| complianceStateID  | O ID para corresponder a este estado de conformidade                |

### <a name="example"></a>Exemplo

|  complianceStatus  |                       Descrição                      |
|:------------------:|:------------------------------------------------------:|
|    Unknown         |    Desconhecida.                                                                        |
|    Compatível       |    Compatível.                                                                      |
|    Não compatível    |       O dispositivo não está em conformidade e está bloqueado a partir de recursos da empresa.             |
|    Conflito        |    Está em conflito com outras regras.                                                      |
|    Error           |       Error.                                                                       |
|    ConfigManager   |    Gerido pelo Config Manager.                                                      |
|    InGracePeriod   |       O dispositivo não está em conformidade, mas ainda tem acesso aos recursos da empresa          |

## <a name="dates"></a>datas
A entidade **date** representa as datas que são referenciadas em múltiplas entidades do armazém de dados.

|     Propriedade    |                       Descrição                      |    Exemplo    |
|:---------------:|:------------------------------------------------------:|:-------------:|
| DateKey         | Identificador exclusivo para esta data no armazém de dados. | 20160703      |
| FullDate        | A data atual representada em formato Data/Hora completo.        | 7/3/2016 0:00 |
| DayOfWeek       | Dia da semana                                            | 1             |
| DayOfMonth      | Dia do mês                                           | 3             |
| DayOfYear       | Dia do ano                                            | 185           |
| WeekOfYear      | Semana do ano                                           | 28            |
| MonthOfYear     | Mês do ano                                      | 7             |
| CalendarQuarter | Trimestre civil                                       | 3             |
| CalendarYear    | Ano civil                                          | 2016          |
| DateKey         | Identificador exclusivo para esta data no armazém de dados. | 20160703      |
| FullDate        | A data atual representada em formato Data/Hora completo.        | 7/3/2016 0:00 |
| DayOfWeek       | Dia da semana                                            | 1             |
| DayOfMonth      | Dia do mês                                           | 3             |
| DayOfYear       | Dia do ano                                            | 185           |
| WeekOfYear      | Semana do ano                                           | 28            |
| MonthOfYear     | Mês do ano                                      | 7             |
| CalendarQuarter | Trimestre civil                                       | 3             |
| CalendarYear    | Ano civil                                          | 2016          |

## <a name="devicecategories"></a>deviceCategories

|      Propriedade      |                                    Descrição                                   |                Exemplo               |
|:------------------:|:--------------------------------------------------------------------------------:|:------------------------------------:|
| deviceCategoryID   | Identificador exclusivo para a categoria do dispositivo.                                       | fb415ba2-7c08-41f6-a5e5-685b50da2c4c |
| deviceCategoryKey  | Identificador exclusivo da categoria do dispositivo no armazém de dados – chave de substituição | 1                                    |
| deviceCategoryName | Nome a apresentar para a categoria do dispositivo.                                            | Smartphones                          |

## <a name="deviceconfigurationprofiledeviceactivities"></a>deviceConfigurationProfileDeviceActivities
A entidade **DeviceConfigurationProfileDeviceActivity** apresenta uma lista do número de dispositivos no estado com êxito, pendente, com falhas ou com erros por dia. O número reflete os Perfis de configuração de dispositivos atribuídos à entidade. Por exemplo, se um dispositivo estiver no estado com êxito em todas as políticas atribuídas, o contador de casos com êxito tem um incremento de um para esse dia. Se um dispositivo tiver dois perfis atribuídos, um no estado com êxito e outro num estado com erros, a entidade incrementa o contador do estado com êxito (Succeeded) e coloca o dispositivo no estado com erros. A entidade apresenta uma lista de quantos dispositivos estão em cada um dos estados num determinado dia nos últimos 30 dias.

|  Propriedade |                                          Descrição                                          |  Exemplo |
|:---------:|:---------------------------------------------------------------------------------------------:|:--------:|
| DateKey   | Data-chave de quando a entrada do Perfil de Configuração do Dispositivo foi registada no armazém de dados. | 20160703 |
| Pending   | Número de Dispositivos exclusivos no estado pendente.                                                    | 123      |
| Succeeded | Número de Dispositivos exclusivos no estado com êxito.                                                    | 12       |
| Error     | Número de Dispositivos exclusivos no estado com erros.                                                      | 10       |
| Failed    | Número de Dispositivos exclusivos no estado com falhas.                                                     | 2        |

## <a name="deviceconfigurationprofileuseractivities"></a>deviceConfigurationProfileUserActivities 
A entidade  **DeviceConfigurationProfileUserActivity**  apresenta uma lista do número de utilizadores no estado com êxito, pendente, com falhas ou com erros por dia. O número reflete os Perfis de configuração de dispositivos atribuídos à entidade. Por exemplo, se um utilizador estiver no estado com êxito em todas as políticas atribuídas, sobe o contador com êxito em um para esse dia. Se um utilizador tiver dois perfis atribuídos, um no estado com êxito e outro no estado com erros, é contado o utilizador no estado com erros. A entidade  **DeviceConfigurationProfileUserActivity**  apresenta uma lista de quantos utilizadores estão em que estado num determinado dia nos últimos 30 dias. 

| Propriedade  | Descrição  | Exemplo  |
|------------|----------------------------------------------------------------------------------------------|-----------|
| DateKey  | Data-chave de quando a entrada do Perfil de Configuração do Dispositivo foi registada no armazém de dados.  | 20160703  |
| Pending  | Número de Utilizadores exclusivos no estado pendente.  | 123  |
| Succeeded  | Número de Utilizadores exclusivos no estado com êxito.  | 12  |
| Error  | Número de Utilizadores exclusivos no estado com erros.  | 10  |
| Failed  | Número de Utilizadores exclusivos no estado com falhas.  | 2  |

## <a name="devicepropertyhistories"></a>devicePropertyHistories

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
| DeviceCategoryKey          | Chave do atributo da categoria do dispositivo para este dispositivo.                                                                                                                                    |
## <a name="deviceregistrationstates"></a>deviceRegistrationStates
A entidade **DeviceRegistrationState** representa o tipo de registo referenciado por outras coleções do armazém de dados. 

|           Propriedade          |                                     Descrição                                     |
|:---------------------------:|:-----------------------------------------------------------------------------------:|
| deviceRegistrationStateID   | Identificador exclusivo para o estado do registo                                            |
| deviceRegistrationStateKey  | Identificador exclusivo do estado do registo no armazém de dados – chave de substituição |
| deviceRegistrationStateName | Estado do registo                                                                  |
|    NotRegistered                     |    Não registado                                                                                                                                                                  |
|    Registado                        |       Registado                                                                                                                                                                   |
|    Revoked                           |       Este estado significa que o administrador de TI bloqueou o cliente e o cliente pode ser desbloqueado. Um dispositivo também pode estar em estado Revoked após ser apagado ou extinto.        |
|    KeyConflict                       |    Conflito de chaves                                                                                                                                                                    |
|    ApprovalPending                   |    Aprovação pendente                                                                                                                                                                |
|    CertificateReset                  |    Repor Certificado                                                                                                                                                               |
|    NotRegisteredPendingEnrollment    |    Não registado, inscrição pendente                                                                                                                                               |
|    Unknown                           |    Estado desconhecido                                                                                                                                                                   |

## <a name="devices"></a>dispositivos
A entidade **device** lista todos os dispositivos inscritos sob gestão e as propriedades correspondentes.

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
| EasDeviceId                | O ID do Exchange ActiveSync do dispositivo.                                                                                                                                                  |
| SerialNumber               | SerialNumber                                                                                                                                                                           |
| UserId                     | O Identificador Exclusivo para o utilizador associado ao dispositivo.                                                                                                                           |
| RowLastModifiedDateTimeUTC | A data e hora em UTC em que este dispositivo foi modificado pela última vez no armazém de dados.                                                                                                       |
| Manufacturer               | Fabricante do dispositivo                                                                                                                                                             |
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


## <a name="devicetypes"></a>deviceTypes
A entidade **deviceType** representa o tipo de dispositivo referenciado por outras entidades do armazém de dados. Normalmente, o tipo de dispositivo descreve o modelo do dispositivo, o fabricante ou ambos.

|    Propriedade    |                                  Descrição                                 |
|:--------------:|:----------------------------------------------------------------------------:|
| DeviceTypeID   | Identificador exclusivo do tipo de dispositivo                                       |
| DeviceTypeKey  | Identificador exclusivo do tipo de dispositivo no armazém de dados – chave de substituição |
| DeviceTypeName | Tipo de dispositivo                                                                |

### <a name="example"></a>Exemplo

| deviceTypeID |        Nome       |                      Descrição                      |
|:------------:|:-----------------:|:-----------------------------------------------------:|
| -1           | Não disponível   | O tipo de dispositivo não está disponível.                     |
| 0            | Desktop           | Dispositivo de Ambiente de Trabalho do Windows                              |
| 1            | Windows           | Dispositivo Windows                                      |
| 2            | WinMO6            | Dispositivo Windows Mobile 6.0                           |
| 3            | Nokia             | Dispositivo Nokia                                        |
| 4            | WindowsPhone      | Dispositivo Windows Phone                                |
| 5            | Mac               | Dispositivo Mac                                          |
| 6            | WinCE             | Dispositivo Windows CE                                   |
| 7            | WinEmbedded       | Dispositivo Windows Embedded                             |
| 8            | IPhone            | Dispositivo iPhone                                       |
| 9            | IPad              | Dispositivo iPad                                         |
| 10           | IPod              | Dispositivo iPod                                         |
| 11           | Android           | Dispositivo Android gerido através do Administrador de Dispositivos   |
| 12           | ISocConsumer      | Dispositivo iSoc Consumer                                |
| 13           | Unix              | Dispositivo UNIX                                         |
| 14           | MacMDM            | Dispositivo Mac OS X gerido com o agente MDM incorporado |
| 15           | HoloLens          | Dispositivo Holo Lens                                    |
| 16           | SurfaceHub        | Dispositivo Surface Hub                                  |
| 17           | AndroidForWork    | Dispositivo Android gerido através do Proprietário do Perfil Android  |
| 18           | AndroidEnterprise | Dispositivo empresarial Android.                          |
| 100          | Blackberry        | Dispositivo Blackberry                                   |
| 101          | Palm              | Dispositivo Palm                                         |
| 255          | Unknown           | Tipo de dispositivo desconhecido                                 |

## <a name="deviceenrollmenttypes"></a>deviceEnrollmentTypes
A entidade **deviceEnrollmentType** indica como um dispositivo foi inscrito. O tipo de inscrição captura o método de inscrição. Os exemplos listam os diferentes tipos de inscrição e o seu significado.

|         Propriedade         |                                    Descrição                                    |
|:------------------------:|:---------------------------------------------------------------------------------:|
| deviceEnrollmentTypeID   | Identificador exclusivo do tipo de inscrição.                                       |
| deviceEnrollmentTypeKey  | Identificador exclusivo do tipo de inscrição no armazém de dados – chave de substituição. |
| deviceEnrollmentTypeName | Nome do tipo de inscrição.                                                           |

### <a name="example"></a>Exemplo

| enrollmentTypeID |                Nome                |                                        Descrição                                       |
|:----------------:|:----------------------------------:|:----------------------------------------------------------------------------------------:|
| 0                | Unknown                            | Não foi recolhido o tipo de inscrição                                                      |
| 1                | UserEnrollment                     | Inscrição controlada pelo utilizador através do canal BYOD.                                           |
| 2                | DeviceEnrollmentManager            | Inscrição de utilizadores com uma conta de gestor de inscrição de dispositivos.                              |
| 3                | AppleBulkWithUser                  | Inscrição em massa da Apple com o desafio de utilizador. (DEP, Apple Configurator)                   |
| 4                | AppleBulkWithoutUser               | Inscrição em massa da Apple sem o desafio de utilizador.   (DEP, Apple Configurator, Mobile Config) |
| 5                | WindowsAzureADJoin                 | Associação ao Azure AD para o Windows 10.                                                                |
| 6                | WindowsBulkUserless                | Inscrição em massa do Windows 10 através do ICD com certificado.                               |
| 7                | WindowsAutoEnrollment              | Inscrição automática de dispositivos Windows 10.   (Adicionar conta profissional)                                    |
| 8                | WindowsBulkAzureDomainJoin         | Associação ao Azure AD em massa no Windows 10.                                                           |
| 9                | WindowsCoManagement                | Cogestão do Windows 10 acionada pelo AutoPilot ou pela Política de Grupo.                       |
| 10               | WindowsAzureADJoinsUsingDeviceAuth | Associação ao Azure AD no Windows 10 através da Autenticação do Dispositivo.                                            |


## <a name="intunemanagementextensions"></a>intuneManagementExtensions
A **intuneManagementExtension** apresenta o estado de funcionamento da **intuneManagementExtension** em cada dispositivo Windows 10 por dia. Os dados são mantidos relativamente aos últimos 60 dias.

|       Propriedade      |                          Descrição                          | Exemplo |
|:-------------------:|:-------------------------------------------------------------:|:-------:|
| DateKey             | Identificador exclusivo da Data.                                | 123     |
| TenantKey           | Identificador exclusivo do Inquilino.                              | 456     |
| DeviceKey           | Identificador exclusivo do Dispositivo.                              | 789     |
| ExtensionVersionKey | Identificador exclusivo da versão da IntuneManagementExtension. | 1       |
| ExtensionStateKey   | Identificador exclusivo do estado de funcionamento.                            | 2       |

## <a name="intunemanagementextensionhealthstates"></a>intuneManagementExtensionHealthStates
O **IntuneManagementExtensionHealthState** apresenta todos os estados de funcionamento possíveis da **IntuneManagementExtension**.

|      Propriedade     |                   Descrição                  | Exemplo |
|:-----------------:|:----------------------------------------------:|:-------:|
| ExtensionStateKey | Identificador exclusivo do estado de funcionamento.           | 2       |
| ExtensionState    | Estado de funcionamento de uma IntuneManagementExtension. | Bom estado de funcionamento |

## <a name="intunemanagementextensionversions"></a>intuneManagementExtensionVersions
A entidade **IntuneManagementExtensionVersion** apresenta todas as versões utilizadas pela **IntuneManagementExtension**.

|       Propriedade      |                          Descrição                          | Exemplo |
|:-------------------:|:-------------------------------------------------------------:|:-------:|
| ExtensionVersionKey | Identificador exclusivo da versão da IntuneManagementExtension. | 1       |
| ExtensionVersion    | O número da versão de quatro dígitos.                                   | 1.0.2.0 |

## <a name="managementagenttypes"></a>managementAgentTypes
A entidade **managementAgentType** representa os agentes utilizados para gerir um dispositivo.

|         Propriedade        |                                       Descrição                                       |
|:-----------------------:|:---------------------------------------------------------------------------------------:|
| ManagementAgentTypeID   | Identificador exclusivo do tipo de agente de gestão.                                         |
| ManagementAgentTypeKey  | Identificador exclusivo do tipo de agente de gestão no armazém de dados – chave de substituição. |
| ManagementAgentTypeName | Indica que tipo de agente é utilizado para gerir o dispositivo.                              |

### <a name="example"></a>Exemplo

| ManagementAgentTypeID |                Nome               |                                  Descrição                                 |
|:---------------------:|:---------------------------------:|:----------------------------------------------------------------------------:|
| 1                     | EAS                               | O dispositivo é gerido através do Exchange Active Sync                         |
| 2                     | MDM                               | O dispositivo é gerido através de um agente MDM                                   |
| 3                     | EasMdm                            | O dispositivo é gerido através do Exchange Active Sync e de um agente MDM        |
| 4                     | IntuneClient                      | O dispositivo é gerido pelo agente de PC do Intune                               |
| 5                     | EasIntuneClient                   | O dispositivo é gerido através do Exchange Active Sync e do agente de PC do Intune |
| 8                     | ConfigManagerClient               | O dispositivo é gerido pelo agente do System Center Configuration Manager     |
| 10                    | ConfigurationManagerClientMdm     | O dispositivo é gerido pelo Configuration Manager e MDM.                    |
| 11                    | ConfigurationManagerCLientMdmEas  | O dispositivo é gerido pelo Configuration Manager, MDM e Eas.               |
| 16                    | Unknown                           | Tipo de agente de gestão desconhecido                                              |
| 32                    | Jamf                              | Os atributos do dispositivo são obtidos a partir do Jamf.                               |
| 64                    | GoogleCloudDevicePolicyController |  O dispositivo é gerido pelo CloudDPC da Google.                                 |

## <a name="managementstates"></a>managementStates
A entidade **ManagementState** disponibiliza detalhes sobre o estado do dispositivo. Os detalhes podem ser úteis nos casos em que são aplicadas ações remotas ou quando o dispositivo foi desbloqueado por jailbreak ou rooting.

|       Propriedade      |                                     Descrição                                    |
|:-------------------:|:----------------------------------------------------------------------------------:|
| managementStateID   | Identificador exclusivo do estado de gestão.                                       |
| managementStateKey  | Identificador exclusivo do estado de gestão no armazém de dados – chave de substituição. |
| managementStateName | Indica o estado da ação remota aplicada a este dispositivo.                 |

### <a name="example"></a>Exemplo

| managementStateID |      Nome      |                                                   Descrição                                                   |
|:-----------------:|:--------------:|:---------------------------------------------------------------------------------------------------------------:|
| 0                 | Managed        | Gerido sem ações remotas pendentes.                                                                       |
| 1                 | RetirePending  | Existe um comando de extinção pendente para o dispositivo.                                                             |
| 2                 | RetireFailed   | O comando de extinção no dispositivo falhou.                                                                      |
| 3                 | WipePending    | Existe um comando para apagar pendente para o dispositivo.                                                               |
| 4                 | WipeFailed     | O comando para apagar falhou no dispositivo.                                                                        |
| 5                 | Unhealthy      | Mau estado de funcionamento.                                                                                              |
| 6                 | DeletePending  | Existe um comando de eliminação pendente para o dispositivo.                                                             |
| 7                 | RetireIssued   | Foi emitido um comando de extinção para o dispositivo.                                                               |
| 8                 | WipeIssued     | Foi emitido um comando para apagar.                                                                               |
| 9                 | WipeCanceled   | O comando para apagar foi cancelado.                                                                               |
| 10                | RetireCanceled | O comando de extinção foi cancelado.                                                                             |
| 11                | Discovered     | O dispositivo foi detetado recentemente no Intune. Após dar entrada pela primeira vez, será movido para o estado Managed. |

## <a name="mobileappinstallstates"></a>mobileAppInstallStates
A entidade MobileAppInstallState representa o estado de instalação de uma aplicação móvel depois de ser atribuída a um grupo que contém dispositivos, utilizadores ou ambos.

|       Propriedade      |                        Descrição                       |
|:-------------------:|:--------------------------------------------------------:|
| AppInstallStateKey  | O ID exclusivo do estado de instalação da aplicação da sua conta. |
| AppInstallState     | Valor Enum do estado de instalação da aplicação.                     |
| AppInstallStateName | Nome do estado de instalação da aplicação.                           |

## <a name="mobileappinstallstatuscounts"></a>mobileAppInstallStatusCounts
Representa um estado de instalação da aplicação móvel para um determinado tipo de dispositivo de destino através da Gestão de Aplicações Móveis com o Microsoft Intune.

|      Propriedade      |                                                          Descrição                                                          |
|:------------------:|:-----------------------------------------------------------------------------------------------------------------------------:|
| DateKey            | A chave da data quando o estado de instalação da aplicação foi registado.                                                                     |
| AppKey             | A chave da aplicação móvel que serve para identificar uma instância de AppRevision.                                                          |
| DeviceTypeKey      | A chave do Tipo de Dispositivo associado à Aplicação Móvel.                                                              |
| AppInstallStateKey | A chave do estado de instalação da aplicação que serve para identificar uma instância de MobileAppInstallState.                                         |
| CódigoDoErro          | O código de erro devolvido pelo instalador de aplicações, pela plataforma móvel ou pelo serviço relativo à instalação da aplicação. |
| Contagem              | Contagem total.                                                                                                                  |

## <a name="ownertypes"></a>ownerTypes
A entidade **ownerType** indica se um dispositivo é empresarial, pessoal ou desconhecido.

|    Propriedade   |                                                                                     Descrição                                                                                    |           Exemplo          |
|:-------------:|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|:--------------------------:|
| ownerTypeID   | Identificador exclusivo do tipo de proprietário.                                                                                                                                               |                            |
| ownerTypeKey  | Identificador exclusivo do tipo de proprietário no armazém de dados – chave de substituição.                                                                                                       |                            |
| ownerTypeName | Representa o tipo de proprietário dos dispositivos. Company – o dispositivo é propriedade da empresa.  Personal – o dispositivo é propriedade pessoal (BYOD).   Unknown – não existem informações sobre este dispositivo. | Company Personal Unknown |

## <a name="policies"></a>políticas
A entidade **Policy** apresenta uma lista de perfis de configuração de dispositivos, perfis de configuração de aplicações e políticas de conformidade. Pode atribuir as políticas com a Gestão de Dispositivos Móveis (MDM) a um grupo na sua empresa.

|          Propriedade          |                                                                       Descrição                                                                      |                Exemplo               |
|:--------------------------:|:------------------------------------------------------------------------------------------------------------------------------------------------------:|:------------------------------------:|
| PolicyKey                  | Chave exclusiva para representar a política no armazém de dados.                                                                                              | 123                                  |
| PolicyId                   | Identificador exclusivo da Política no armazém de dados.                                                                                                 | b66bc706-ffff-7437-0340-032819502773 |
| PolicyName                 | Nome da Política.                                                                                                                                    | "Linha de Base do Windows 10"                |
| PolicyVersion              | Versão da Política. Quando a política é editada ou alterada, é criada uma versão mais recente.                                                             | 1, 2, 3                              |
| IsDeleted                  | Indica se o registo da Política foi atualizado.  True – a política tem um novo registo com campos atualizados.  False – o registo mais recente da política. | True/False                           |
| StartDateInclusiveUTC      | Data e hora em UTC em que a política foi criada no armazém de dados.                                                                              | 11/23/2016 0:00                      |
| DeletedDateUTC             | Data e hora em UTC em que a propriedade IsDeleted foi alterada para True.                                                                                                   | 11/23/2016 0:00                      |
| RowLastModifiedDateTimeUTC | Data e hora em UTC em que a política foi modificada pela última vez no armazém de dados.                                                                        | 11/23/2016 0:00                      |

## <a name="policydeviceactivities"></a>policyDeviceActivities
A tabela seguinte mostra o número de dispositivos no estado com êxito, pendente, com falhas ou com erros por dia. O número apresentado reflete os perfis de dados por Tipo de Política. Por exemplo, se um dispositivo estiver no estado com êxito em todas as políticas atribuídas, o contador de casos com êxito tem um incremento de um para esse dia. Se um dispositivo tiver dois perfis atribuídos, um no estado com êxito e outro num estado com erros, a entidade incrementa o contador do estado com êxito (Succeeded) e coloca o dispositivo no estado com erros. A entidade **policyDeviceActivity** apresenta uma lista de quantos dispositivos estão em cada um dos estados num determinado dia nos últimos 30 dias.

|  Propriedade |                                           Descrição                                           |        Exemplo        |
|:---------:|:-----------------------------------------------------------------------------------------------:|:---------------------:|
| DateKey   | Data-chave de quando a entrada do Perfil de Configuração do Dispositivo foi registada no armazém de dados. | 20160703              |
| Pending   | Número de Dispositivos exclusivos no estado pendente.                                                    | 123                   |
| Succeeded | Número de Dispositivos exclusivos no estado com êxito.                                                    | 12                    |
| PolicyKey | A chave de Política pode ser acompanhada pela Política para obter o policyName.                                  | Linha de base do Windows 10 |
| Error     | Número de Dispositivos exclusivos no estado com erros.                                                      | 10                    |
| Failed    | Número de Dispositivos exclusivos no estado com falhas.                                                     | 2                     |

## <a name="policyplatformtypes"></a>policyPlatformTypes

|        Propriedade        |                      Descrição                      |     Exemplo    |
|:----------------------:|:-----------------------------------------------------:|:--------------:|
| PolicyPlatformTypeKey  | A chave exclusiva do tipo de plataforma da política.        | 20170519       |
| PolicyPlatformTypeId   | O identificador exclusivo do tipo de plataforma da política. | 1              |
| PolicyPlatformTypeName | O nome do tipo de plataforma da política.              | AndroidForWork |

## <a name="policytypeactivities"></a>policyTypeActivities
A entidade **PolicyTypeActivity** apresenta uma lista do número cumulativo de dispositivos no estado com êxito, pendente, com falhas ou com erros por dia. Apresenta uma lista destes estados relativamente a um perfil de configuração de dispositivo, perfil de configuração de aplicação ou política de conformidade por dia.

|    Propriedade   |                                          Descrição                                          |           Exemplo           |
|:-------------:|:---------------------------------------------------------------------------------------------:|:---------------------------:|
| DateKey       | Data-chave de quando a entrada do Perfil de configuração do dispositivo foi registada no armazém de dados. | 20160703                    |
| PolicyKey     | A chave de política pode ser acompanhada pela Política para obter o policyName.                                | Linha de base do Windows 10         |
| PolicyTypeKey | O tipo de Chave de Política pode ser acompanhado do Tipo de Política para obter o nome do tipo de política.             | Política de Compatibilidade do Windows 10 |
| Pending       | Número de dispositivos exclusivos no estado pendente.                                                    | 123                         |
| Succeeded     | Número de dispositivos exclusivos no estado com êxito.                                                    | 12                          |
| Error         | Número de dispositivos exclusivos no estado com erros.                                                      | 10                          |
| Failed        | Número de dispositivos exclusivos no estado com falhas.                                                     | 2                           |

## <a name="policytypes"></a>policyTypes
A entidade **PolicyType** apresenta uma lista dos tipos de perfis de configuração de dispositivos, perfis de configuração de aplicações e políticas de conformidade. Pode atribuir as políticas com a Gestão de Dispositivos Móveis (MDM) a um grupo na sua empresa.

|    Propriedade    |                       Descrição                      |            Exemplo            |
|:--------------:|:------------------------------------------------------:|:-----------------------------:|
| PolicyTypeId   | Identificador exclusivo da política no sistema de origem.  | 123                           |
| PolicyTypeKey  | Identificador exclusivo da política no armazém de dados. | 1                             |
| PolicyTypeName | Nome do tipo de política.                               | Política de Conformidade do Windows 10. |

## <a name="policyuseractivities"></a>policyUserActivities
A tabela seguinte mostra o número de utilizadores no estado com êxito, pendente, com falhas ou com erros por dia. O número apresentado reflete os perfis de dados por Tipo de Política. Por exemplo, se um utilizador estiver no estado com êxito em todas as políticas atribuídas, sobe o contador com êxito em um para esse dia. Se um utilizador tiver dois perfis atribuídos, um no estado com êxito e outro no estado com erros, é contado o utilizador no estado com erros. A entidade **PolicyUserActivity** apresenta uma lista de quantos utilizadores estão em cada um dos estados num determinado dia nos últimos 30 dias.

|  Propriedade |                                          Descrição                                          |       Exemplo       |
|:---------:|:---------------------------------------------------------------------------------------------:|:-------------------:|
| DateKey   | Data-chave de quando a entrada do Perfil de Configuração do Dispositivo foi registada no armazém de dados. | 20160703            |
| Pending   | Número de Dispositivos exclusivos no estado pendente.                                                    | 123                 |
| Succeeded | Número de Dispositivos exclusivos no estado com êxito.                                                    | 12                  |
| PolicyKey | A chave de política pode ser acompanhada pela Política para obter o policyName.                                | Linha de base do Windows 10 |
| Error     | Número de Dispositivos exclusivos no estado com erros.                                                      | 10                  |

## <a name="termsandconditions"></a>termsAndConditions
A entidade **termsAndConditions** representa os metadados e o conteúdo de uma determinada política de Termos e Condições (T&C). O conteúdo das políticas de T&C é apresentado aos utilizadores após a sua primeira tentativa de inscrição no Intune e, em seguida, após as edições em que um administrador tiver exigido uma nova aceitação. Permitem que os administradores comuniquem as cláusulas que um utilizador tem de aceitar para inscrever dispositivos no Intune.

|    Propriedade        |    Descrição    |    Exemplo        |
|----------------------------------|-----------------------------------------------------------------------------------------------|-----------------------------------------------------------|
|    termsAndConditionsKey    |    Uma chave correspondente a uma entrada na coleção “userTermsAndConditionsAcceptances”    |    123    |
|    termsAndCondidionsId    |    O ID para esta entrada termsAndConditions    |    276edcb7-7440-4339-b6c5-8b6fc556fee6    |
|    termsAndConditionsVersion    |    A versão da entrada destes termos e condições    |    1    |
|    nome    |    O nome da entrada destes termos e condições.        |    Termos de utilização do Intune     |
|    descrição    |    A descrição para estes termos e condições.     |         |
|    título    |    O título para estes termos e condições.     |    Política empresarial da gestão de dispositivos        |
|    summaryOfTerms    |    O resumo dos termos que o utilizador recebeu.     |    Concordo com os termos e condições.    |
|    termsAndConditionsBodyText    |    O corpo do texto para estes termos e condições.       |    * Encriptação de dispositivos * Imposição do PIN com 6 dígitos    |
|    isDeleted    |    Valor de verdadeiro ou falso para saber se este valor foi eliminado.     |    Falso    |
|    startDateInclusiveUTC    |    A data de início dos termos e condições.     |    8/23/2018 4:01:34    |
|    endDateEclusiveUTC    |    A data de fim destes termos e condições.     |    12/31/9999 00:00:00    |

## <a name="userdeviceassociations"></a>userDeviceAssociations
A entidade **UserDeviceAssociation** contém associações de dispositivos do utilizador na sua organização.

|        Nome        |                                             Descrição                                            |     Exemplo     |
|:------------------:|:--------------------------------------------------------------------------------------------------:|:---------------:|
| UserKey            | Identificador exclusivo do utilizador no armazém de dados.   (Chave de substituição).                            | 123             |
| DeviceKey          | Identificador exclusivo do dispositivo no armazém de dados.                                             | 123             |
| CreatedDateTimeUTC | Data e hora em que a associação de dispositivos do utilizador foi criada. Utiliza o formato UTC.                     | 11/23/2016 0:00 |
| IsDeleted          | Indica que o utilizador anulou a inscrição desse dispositivo e essa associação já não está atualizada. | True/False      |
| EndedDateTimeUTC   | Data e hora em UTC em que a propriedade IsDeleted foi alterada para True.                                               | 6/23/2017 0:00  |

## <a name="users"></a>utilizadores
A entidade **user** lista todos os utilizadores do Azure Active Directory (Azure AD) com licenças atribuídas na sua empresa.

A coleção de entidades **user** contém dados do utilizador. Estes registos incluem estados do utilizador durante o período de recolha dos dados, mesmo que o utilizador tenha sido removido. Por exemplo, um utilizador pode ser adicionado ao Intune e, em seguida, removido no decorrer do mês anterior. Apesar de este utilizador não estar presente no momento do relatório, o utilizador e o estado estão presentes nos dados do mês anterior. Pode criar um relatório que mostrará a duração da presença no histórico do utilizador nos seus dados.

|          Propriedade          |                                                                                                           Descrição                                                                                                          |                Exemplo               |
|:--------------------------:|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|:------------------------------------:|
| UserKey                    | Identificador exclusivo do utilizador no armazém de dados – chave de substituição.                                                                                                                                                         | 123                                  |
| UserId                     | Identificador exclusivo do utilizador – semelhante a UserKey, mas é uma chave natural.                                                                                                                                                    | b66bc706-ffff-7437-0340-032819502773 |
| UserEmail                  | Endereço de e-mail do utilizador.                                                                                                                                                                                                     | John@constoso.com                    |
| UPN                        | O nome principal do utilizador.                                                                                                                                                                                               | John@constoso.com                    |
| DisplayName                | Nome a apresentar do utilizador.                                                                                                                                                                                                      | João                                 |
| IntuneLicensed             | Especifica se este utilizador tem ou não licença do Intune.                                                                                                                                                                              | True/False                           |
| IsDeleted                  | Indica se todas as licenças do utilizador expiraram e se o utilizador foi, por conseguinte, removido do Intune. Para um único registo, este sinalizador não se altera. Em vez disso, é criado um novo registo para um novo estado do utilizador. | True/False                           |
| RowLastModifiedDateTimeUTC | Data e hora em UTC quando o registo foi modificado pela última vez no armazém de dados                                                                                                                                                 | 11/23/2016 0:00                      |

## <a name="usertermsandconditionsacceptances"></a>userTermsAndConditionsAcceptances
A entidade **userTermsAndConditionsAcceptance** representa o estado de aceitação de uma determinada Política de Termos e Condições (T&C) por um determinado utilizador. Os utilizadores têm de aceitar a versão mais atualizada dos termos para manter o acesso ao Portal da Empresa.

|    Propriedade    |    Descrição    |    Exemplo    |
|-------------------------------|--------------------------------------------------------------------------------|----------------------------|
|    dateKey    |    Uma chave correspondente aos valores de data na coleção "datas".     |    20180823    |
|    userKey    |    Um mapeamento de chave de utilizador para um utilizador na coleção "utilizadores".     |    20000    |
|    termsAndConditionsKey    |    Uma chave correspondente a uma entrada na coleção “termsAndConditions”    |    1    |
|    acceptedDateTimeUTC    |    A hora em que o utilizador aceitou estes termos e condições    |    8/23/2018 4:01:34    |
|    lastModifiedDateTimeUTC    |    A última vez que esta entrada foi modificada.     |    8/23/2018 4:01:34    |

## <a name="vppprogramtypes"></a>vppProgramTypes 
A entidade **vppProgramType** apresenta uma lista de tipos de programas VPP possíveis para uma aplicação.

|      Propriedade      |          Descrição         |
|:------------------:|:----------------------------:|
| VppProgramTypeID   | ID do tipo.           |
| VppProgramTypeKey  | Chave de substituição da chave. |
| VppProgramTypeName | Tipo de Programa VPP.          |

### <a name="example"></a>Exemplo

|             VppProgramID             |         Nome        | Descrição                |
|:------------------------------------:|:-------------------:|----------------------------|
| 3DDA2474-470B-4503-9830-2665C21C1945 | Microsoft           | Programa VPP da Microsoft. |
| 00000000-0000-0000-0000-000000000000 | Ainda não está disponível | Valor predefinido, Sem VPP.   |
| B54814E0-68EA-4BA4-8088-B5AAB58E737B | Apple               | Programa VPP da Apple.     |

## <a name="next-steps"></a>Próximos passos

Para obter mais informações sobre o Armazém de Dados do Intune, veja [Modelo de dados do Armazém de Dados](https://docs.microsoft.com/intune/reports-ref-data-model).

