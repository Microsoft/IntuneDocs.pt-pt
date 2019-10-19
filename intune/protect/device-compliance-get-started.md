---
title: Políticas de conformidade de dispositivos no Microsoft Intune – Azure | Microsoft Docs
description: Comece a usar as políticas de conformidade do dispositivo, visão geral dos níveis de status e gravidade, usando o status do InGracePeriod, trabalhando com o acesso condicional, manipulando dispositivos sem uma política atribuída e as diferenças de conformidade no portal do Azure e Portal clássico no Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 05/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: samyada
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c6ab0fd0220b252fe2361c0721ea026afcc232c0
ms.sourcegitcommit: 62e264052738fc7fc6f22750589fb4bee7cd9d09
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/17/2019
ms.locfileid: "72531998"
---
# <a name="set-rules-on-devices-to-allow-access-to-resources-in-your-organization-using-intune"></a>Definir regras em dispositivos para permitir o acesso a recursos na sua organização através do Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Muitas soluções de gestão de dispositivos móveis (MDM) ajudam a proteger os dados organizacionais ao exigir que os utilizadores e os dispositivos cumpram alguns requisitos. No Intune, esta funcionalidade é denominada “políticas de conformidade”. As políticas de conformidade definem as regras e as definições que os utilizadores e os dispositivos têm de cumprir para estarem em conformidade. Quando combinado com o acesso condicional, os administradores podem bloquear usuários e dispositivos que não atendem às regras.

Por exemplo, um administrador do Intune pode exigir que:

- Os utilizadores finais utilizem uma palavra-passe para aceder aos dados organizacionais nos dispositivos móveis
- O dispositivo não estejam desbloqueados por jailbreak ou rooting
- Exista uma versão mínima ou máxima do sistema operativo no dispositivo
- O dispositivo se mantenha ou esteja abaixo de um nível de ameaça

Também pode utilizar esta funcionalidade para monitorizar o estado de conformidade dos dispositivos na sua organização.

> [!IMPORTANT]
> O Intune segue o agendamento de registo do dispositivo para todas as avaliações de conformidade no dispositivo. [Ciclos de atualização de política e perfil](../configuration/device-profile-troubleshoot.md#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned) lista os tempos de atualização estimados.

<!---### Actions for noncompliance

You can specify what needs to happen when a device is determined as noncompliant. This can be a sequence of actions during a specific time.
When you specify these actions, Intune will automatically initiate them in the sequence you specify. See the following example of a sequence of
actions for a device that continues to be in the noncompliant status for
a week:

- When the device is first determined to be noncompliant, an email with noncompliant notification is sent to the user.

- 3 days after initial noncompliance state, a follow up reminder is sent to the user.

- 5 days after initial noncompliance state, a final reminder with a notification that access to company resources will be blocked on the device in 2 days if the compliance issues are not remediated is sent to the user.

- 7 days after initial noncompliance state, access to company resources is blocked. This requires that you have Conditional Access policy that specifies that access from noncompliant devices should    be blocked for services such as Exchange and SharePoint.

### Grace Period

This is the time between when a device is first determined as
noncompliant to when access to company resources on that device is blocked. This time allows for time that the user has to resolve
compliance issues on the device. You can also use this time to create your action sequences to send notifications to the user before their access is blocked.

Remember that you need to implement Conditional Access policies in addition to compliance policies in order for access to company resources to be blocked.--->

## <a name="device-compliance-policies-work-with-azure-ad"></a>As políticas de conformidade de dispositivos funcionam com o Microsoft Azure AD

O Intune usa o [acesso condicional](https://docs.microsoft.com/azure/active-directory/conditional-access/overview) do Azure Active Directory (AD) (abre outro site de documentos) para ajudar a reforçar a conformidade. Quando um dispositivo se inscreve no Intune, é iniciado o processo de registo do Microsoft Azure AD e a informação do dispositivo é atualizada no Microsoft Azure AD. Uma das principais informações do dispositivo é o estado de conformidade do dispositivo. Esse status de conformidade é usado pelas políticas de acesso condicional para bloquear ou permitir o acesso a email e outros recursos da organização.

- [O que é a gestão de dispositivos no Azure Active Directory](https://docs.microsoft.com/azure/active-directory/device-management-introduction) é um excelente recurso sobre o porquê e a forma como os dispositivos são registados no Microsoft Azure AD.

- O [acesso condicional](conditional-access.md) e as [maneiras comuns de usar o acesso condicional](conditional-access-intune-common-ways-use.md) descrevem esse recurso, pois ele está relacionado ao Intune.

## <a name="ways-to-use-device-compliance-policies"></a>Formas de utilizar as políticas de conformidade de dispositivos

### <a name="with-conditional-access"></a>Com acesso condicional

Para dispositivos que estejam em conformidade com as regras da política, poderá conceder a esses dispositivos o acesso ao e-mail e a outros recursos da organização. Se os dispositivos não estiverem em conformidade com as regras da política, não obterão acesso aos recursos da organização. Esse é o acesso condicional.

### <a name="without-conditional-access"></a>Sem acesso condicional

Você também pode usar políticas de conformidade do dispositivo sem qualquer acesso condicional. Quando utilizar políticas de conformidade de forma independente, os dispositivos visados são avaliados e reportados com o respetivo estado de conformidade. Por exemplo, pode obter um relatório sobre o número de dispositivos que não estão encriptados ou quais os dispositivos que foram desbloqueados por jailbreak ou rooting. Quando você usa políticas de conformidade sem acesso condicional, não há nenhuma restrição de acesso aos recursos da organização.

## <a name="ways-to-deploy-device-compliance-policies"></a>Formas de implementar as políticas de conformidade de dispositivos

Pode implementar a política de conformidade a utilizadores em grupos de utilizadores ou dispositivos em grupos de dispositivos. Quando uma política de conformidade é implementada num utilizador, todos os dispositivos do utilizador são verificados relativamente à conformidade. No Windows 10 versão 1803 e dispositivos mais recentes, é recomendado implementar para grupos de dispositivos *se* o utilizador primário não tiver inscrito o dispositivo. Utilizar grupos de dispositivos neste cenário ajuda com os relatórios de conformidade.

O Intune também inclui um conjunto de definições de políticas de conformidade incorporadas. As seguintes políticas incorporadas são avaliadas em todos os dispositivos inscritos no Intune:

- **Marcar os dispositivos sem política de conformidade atribuída como**: esta propriedade tem dois valores:

  - **Compatível**(padrão): recurso de segurança desativado
  - **Não compatível**: recurso de segurança ativado

  Se um dispositivo não tiver uma política de conformidade atribuída, esse dispositivo será considerado em conformidade por padrão. Se você usar o acesso condicional com políticas de conformidade, recomendamos que você altere a configuração padrão para **não compatível**. Se um utilizador final não estiver em conformidade porque não foi atribuída uma política, a [aplicação do Portal da Empresa](../apps/company-portal-app.md) mostrará `No compliance policies have been assigned`.

- **Detecção de jailbreak avançada**: Quando habilitada, essa configuração faz com que os dispositivos IOS verifiquem com o Intune com mais frequência. A ativação desta propriedade utiliza os serviços de localização do dispositivo e afeta a utilização da bateria. Os dados de localização do utilizador não são armazenados pelo Intune.

  Ativar esta definição exige que os dispositivos:
  - Ativem os serviços de localização ao nível do SO.
  - Permitam que o Portal da Empresa utilize os serviços de localização.
  - Avaliem e comuniquem o estado de jailbreak do mesmo no Intune, pelo menos, uma vez a cada 72 horas. Caso contrário, o dispositivo será marcado como não conforme. A avaliação é acionada ao abrir a aplicação do Portal da Empresa ou ao mover fisicamente o dispositivo uma distância de 500 metros ou mais. Se o dispositivo não se mover 500 metros em 72 horas, o utilizador precisará de abrir a aplicação do Portal da Empresa para a avaliação avançada de jailbreak.

- **Período de validade do estado de conformidade (dias)** : introduza o período de tempo durante o qual os dispositivos devem comunicar o estado para todas as políticas de conformidade recebidas. Os dispositivos que não devolvam o estado dentro deste período de tempo são tratados como não conformes. O valor predefinido é 30 dias.

Pode utilizar estas políticas incorporadas para monitorizar as definições. O Intune também [atualiza ou verifica a existência de atualizações](create-compliance-policy.md#refresh-cycle-times) com diferentes intervalos, consoante a plataforma do dispositivo. O artigo [Perguntas comuns, problemas e resoluções relativas aos perfis e políticas dos dispositivos no Microsoft Intune](../configuration/device-profile-troubleshoot.md) poder ser útil.

Os relatórios de conformidade são uma excelente forma de verificar o estado dos dispositivos. O artigo [Monitorizar as políticas de conformidade](compliance-policy-monitor.md) inclui algumas orientações.

## <a name="non-compliance-and-conditional-access-on-the-different-platforms"></a>Não conformidade e acesso condicional em diferentes plataformas

A tabela a seguir descreve como as configurações não compatíveis são gerenciadas quando uma política de conformidade é usada com uma política de acesso condicional.

---------------------------

|**Definição de política**| **Plataforma** |
| --- | ----|
| **Configuração do PIN ou da palavra-passe** | - **Android 4,0 e posterior**: em quarentena</br>- **Samsung Knox Standard 4,0 e posterior**: em quarentena</br>- **Android Enterprise**: em quarentena</br></br>- **iOS 8,0 e posterior**: corrigido</br>- **macOS 10,11 e posterior**: corrigido</br></br>- **Windows 8.1 e posterior**: corrigido</br>- **Windows Phone 8,1 e posterior**: corrigido|
| **Encriptação do dispositivo** | - **Android 4,0 e posterior**: em quarentena</br>- **Samsung Knox Standard 4,0 e posterior**: em quarentena</br>- **Android Enterprise**: em quarentena</br></br>- **iOS 8,0 e posterior**: corrigido (ao definir o PIN)</br>- **macOS 10,11 e posterior**: corrigido (ao definir o PIN)</br></br>- **Windows 8.1 e posterior**: não aplicável</br>- **Windows Phone 8,1 e posterior**: corrigido |
| **Dispositivo desbloqueado por jailbreak ou obtenção de controlo de raiz** | - **Android 4,0 e posterior**: em quarentena (não é uma configuração)</br>- **Samsung Knox Standard 4,0 e posterior**: em quarentena (não é uma configuração)</br>- **Android Enterprise**: em quarentena (não é uma configuração)</br></br>- **iOS 8,0 e posterior**: em quarentena (não é uma configuração)</br>- **macOS 10,11 e posterior**: não aplicável</br></br>- **Windows 8.1 e posterior**: não aplicável</br>- **Windows Phone 8,1 e posterior**: não aplicável |
| **Perfil de e-mail** | - **Android 4,0 e posterior**: não aplicável</br>- **Samsung Knox Standard 4,0 e posterior**: não aplicável</br>- **Android Enterprise**: não aplicável</br></br>- **iOS 8,0 e posterior**: em quarentena</br>- **macOS 10,11 e posterior**: em quarentena</br></br>- **Windows 8.1 e posterior**: não aplicável</br>- **Windows Phone 8,1 e posterior**: não aplicável |
| **Versão mínima do SO** | - **Android 4,0 e posterior**: em quarentena</br>- **Samsung Knox Standard 4,0 e posterior**: em quarentena</br>- **Android Enterprise**: em quarentena</br></br>- **iOS 8,0 e posterior**: em quarentena</br>- **macOS 10,11 e posterior**: em quarentena</br></br>- **Windows 8.1 e posterior**: em quarentena</br>- **Windows Phone 8,1 e posterior**: em quarentena |
| **Versão máxima do SO** | - **Android 4,0 e posterior**: em quarentena</br>- **Samsung Knox Standard 4,0 e posterior**: em quarentena</br>- **Android Enterprise**: em quarentena</br></br>- **iOS 8,0 e posterior**: em quarentena</br>- **macOS 10,11 e posterior**: em quarentena</br></br>- **Windows 8.1 e posterior**: em quarentena</br>- **Windows Phone 8,1 e posterior**: em quarentena |
| **Atestado do estado de funcionamento do Windows** | - **Android 4,0 e posterior**: não aplicável</br>- **Samsung Knox Standard 4,0 e posterior**: não aplicável</br>- **Android Enterprise**: não aplicável</br></br>- **iOS 8,0 e posterior**: não aplicável</br>- **macOS 10,11 e posterior**: não aplicável</br></br>- **Windows 10 e Windows 10 Mobile: em**quarentena</br>- **Windows 8.1 e posterior**: em quarentena</br>- **Windows Phone 8,1 e posterior**: não aplicável |

---------------------------

**Corrigido**: o sistema operacional do dispositivo impõe a conformidade. Por exemplo, forçar o utilizador a definir um PIN.

Em **quarentena**: o sistema operacional do dispositivo não impõe conformidade. Por exemplo, os dispositivos Android e Android Enterprise não forçam o utilizador a encriptar o dispositivo. Quando o dispositivo não é conforme, são realizadas as seguintes ações:

- Se uma política de acesso condicional se aplicar ao usuário, o dispositivo será bloqueado.
- A aplicação do Portal da Empresa notifica o utilizador sobre eventuais problemas de conformidade.

## <a name="azure-classic-portal-vs-azure-portal"></a>Portal clássico do Azure versus portal do Azure

A principal diferença ao utilizar políticas de conformidade de dispositivos no portal do Azure:

- No portal do Azure, as políticas de conformidade são criadas em separado para cada plataforma suportada
- No portal clássico do Azure, uma política de conformidade de dispositivos é comum a todas as plataformas suportadas

<!--- - In the Azure portal, you have the ability to specify actions and notifications that are initiated when a device is determined to be noncompliant. This ability does not exist in the Intune admin console.

- In the Azure portal, you can set a grace period to allow time for the end-user to get their device back to compliance status before they completely lose the ability to get company data on their device. This is not available in the Intune admin console.--->

As políticas de conformidade de dispositivos criadas no [portal clássico do Azure](https://manage.microsoft.com) não aparecem no [portal do Azure](https://portal.azure.com). No entanto, continuam a ser direcionadas para os utilizadores e geríveis através do portal clássico.

Para utilizar as funcionalidades relacionadas com a conformidade de dispositivos no portal do Azure, terá de criar novas políticas de conformidade de dispositivos no portal do Azure. Se atribuir uma política de conformidade de dispositivos no portal do Azure a um utilizador a quem também tenha sido atribuída uma política de conformidade de dispositivos do portal clássico, as políticas de conformidade de dispositivos do portal do Azure terão precedência sobre as políticas criadas no portal clássico.

## <a name="next-steps"></a>Próximos passos

- [Criar uma política](create-compliance-policy.md) e ver os pré-requisitos.
- Ver as definições de conformidade para as diferentes plataformas de dispositivos:

  - [Android](compliance-policy-create-android.md)
  - [Android Enterprise](compliance-policy-create-android-for-work.md)
  - [iOS](compliance-policy-create-ios.md)
  - [macOS](compliance-policy-create-mac-os.md)
  - [Windows 10 e posterior](compliance-policy-create-windows.md)
  - [Windows Holographic for Business](compliance-policy-create-windows.md#windows-holographic-for-business)
  - [Windows 8.1 e Windows Phone 8.1](compliance-policy-create-windows-8-1.md)

- [Referência das entidades de políticas](../reports-ref-policy.md) tem informações sobre as entidades das políticas do Data Warehouse do Intune.
