---
title: Políticas de conformidade de dispositivos no Microsoft Intune – Azure | Microsoft Docs
description: Começar a utilizar com políticas de conformidade de dispositivo de utilização, visão geral do Estado e níveis de gravidade, utilizar o estado InGracePeriod, trabalhar com acesso condicional, processamento de dispositivos sem uma política atribuída e as diferenças de conformidade no portal do Azure e portal clássico no Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/08/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: fbed6185abe7656c3269805d1d5ed09eccbaf05e
ms.sourcegitcommit: 02803863eba37ecf3d8823a7f1cd7c4f8e3bb42c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2019
ms.locfileid: "59423526"
---
# <a name="set-rules-on-devices-to-allow-access-to-resources-in-your-organization-using-intune"></a>Definir regras em dispositivos para permitir o acesso a recursos na sua organização utilizar o Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Muitas soluções de gestão (MDM) de dispositivos móveis ajudar a proteger dados organizacionais ao exigir que os utilizadores e dispositivos para cumprir alguns requisitos. No Intune, esse recurso é chamado de "políticas de conformidade". Políticas de conformidade definem as regras e definições que os utilizadores e dispositivos têm de cumprir para estar em conformidade. Quando combinado com acesso condicional, os administradores podem bloquear os utilizadores e dispositivos que não cumprem as regras.

Por exemplo, pode exigir um administrador do Intune:

- Os utilizadores finais utilizam uma palavra-passe para aceder aos dados organizacionais em dispositivos móveis
- O dispositivo não estiver desbloqueado por jailbreak ou rooting
- Uma versão de sistema operativo mínimo ou máximo no dispositivo
- O dispositivo esteja ao ou num nível de ameaça

Também pode utilizar esta funcionalidade para monitorizar o estado de conformidade nos dispositivos na sua organização.

> [!IMPORTANT]
> Intune segue o agendamento de entrada do dispositivo para todas as avaliações de conformidade no dispositivo. [Saiba mais sobre o agendamento da entrada dispositivo](device-profile-troubleshoot.md#how-long-does-it-take-for-mobile-devices-to-get-a-policy-or-apps-after-they-have-been-assigned).

<!---### Actions for noncompliance

You can specify what needs to happen when a device is determined as noncompliant. This can be a sequence of actions during a specific time.
When you specify these actions, Intune will automatically initiate them in the sequence you specify. See the following example of a sequence of
actions for a device that continues to be in the noncompliant status for
a week:

-   When the device is first determined to be noncompliant, an email with noncompliant notification is sent to the user.

-   3 days after initial noncompliance state, a follow up reminder is sent to the user.

-   5 days after initial noncompliance state, a final reminder with a notification that access to company resources will be blocked on the device in 2 days if the compliance issues are not remediated is sent to the user.

-   7 days after initial noncompliance state, access to company resources is blocked. This requires that you have conditional access policy that specifies that access from noncompliant devices should    be blocked for services such as Exchange and SharePoint.

### Grace Period

This is the time between when a device is first determined as
noncompliant to when access to company resources on that device is blocked. This time allows for time that the user has to resolve
compliance issues on the device. You can also use this time to create your action sequences to send notifications to the user before their access is blocked.

Remember that you need to implement conditional access policies in addition to compliance policies in order for access to company resources to be blocked.--->

## <a name="device-compliance-policies-work-with-azure-ad"></a>Políticas de conformidade de dispositivos funcionam com o Azure AD

O Intune utiliza o Azure Active Directory (AD) [acesso condicional](https://docs.microsoft.com/azure/active-directory/conditional-access/overview) (abre-se outro web site do docs) para ajudar a impor a conformidade. Quando um dispositivo é inscrito no Intune, o processo de registo do Azure AD é iniciado, e as informações do dispositivo são atualizadas no Azure AD. Uma das principais informações do dispositivo é o estado de conformidade do dispositivo. Este estado de conformidade é utilizado pelas políticas de acesso condicional para bloquear ou permitir o acesso ao e-mail e outros recursos de organização.

- [O que é a gestão de dispositivos no Azure Active Directory](https://docs.microsoft.com/azure/active-directory/device-management-introduction) é um ótimo recurso no porquê e como os dispositivos são registados no Azure AD.

- [Acesso condicional](conditional-access.md) e [formas comuns de utilizar o acesso condicional](conditional-access-intune-common-ways-use.md) descrever esta funcionalidade, que diz respeito ao Intune.

## <a name="ways-to-use-device-compliance-policies"></a>Formas de utilizar as políticas de conformidade de dispositivos

#### <a name="with-conditional-access"></a>Com acesso condicional

Para dispositivos que estejam em conformidade com as regras de política, pode permitir que esses dispositivos o acesso ao e-mail e outros recursos da organização. Se os dispositivos não estiverem em conformidade com as regras de política, em seguida, eles não recebem acesso a recursos da organização. Isto é o acesso condicional.

#### <a name="without-conditional-access"></a>Sem acesso condicional

Também pode utilizar as políticas de conformidade de dispositivos sem acesso condicional. Quando utilizar políticas de conformidade de forma independente, os dispositivos visados são avaliados e reportados com o respetivo estado de conformidade. Por exemplo, pode obter um relatório sobre o número de dispositivos não está encriptado ou quais os dispositivos que estão desbloqueados por jailbreak ou rooting. Quando utilizar políticas de conformidade sem acesso condicional, não existem quaisquer restrições de acesso aos recursos da organização.

## <a name="ways-to-deploy-device-compliance-policies"></a>Formas de implementar as políticas de conformidade de dispositivos

Pode implementar a política de conformidade a utilizadores em grupos de utilizadores ou dispositivos em grupos de dispositivos. Quando uma política de conformidade é implementada num utilizador, todos os dispositivos do utilizador são verificados relativamente à conformidade. No Windows 10 versão 1803 e dispositivos mais recentes, é recomendado implementar para grupos de dispositivos *se* o utilizador primário não tiver inscrito o dispositivo. Utilizar grupos de dispositivos neste cenário ajuda com os relatórios de conformidade.

O Intune também inclui um conjunto de definições de política de conformidade incorporada. As seguintes diretivas internas obterem avaliadas em todos os dispositivos inscritos no Intune:

- **Marcar os dispositivos sem política de conformidade atribuída como**: Esta propriedade tem dois valores:

  - **Compatível**: a funcionalidade de segurança está desativada
  - **Não compatível** (predefinição): a funcionalidade de segurança está ativada

  Se um dispositivo não tiver uma política de conformidade atribuída, este dispositivo é considerado não conforme. Por predefinição, os dispositivos são marcados como **Não compatíveis**. Se utilizar o acesso condicional, recomendamos que altere a definição para **não conformes**. Se um utilizador final não estiver em conformidade porque não foi atribuída uma política, o [aplicação Portal da empresa](company-portal-app.md) mostra `No compliance policies have been assigned`.

- **Deteção avançada de jailbreak**: Quando ativada, esta definição faz com que os dispositivos iOS a dar entrada no Intune com mais frequência. A ativação desta propriedade utiliza os serviços de localização do dispositivo e afeta a utilização da bateria. Os dados de localização do utilizador não estão armazenados pelo Intune.

  Ativar esta definição exige que os dispositivos:
  - Ative os serviços de localização ao nível do SO.
  - Permitir que o portal da empresa utilizar os serviços de localização.
  - Avaliem e comuniquem o estado de jailbreak do mesmo no Intune, pelo menos, uma vez a cada 72 horas. Caso contrário, o dispositivo será marcado como não conforme. Avaliação é acionada por abrir a aplicação Portal da empresa ou mover fisicamente o dispositivo medidores 500 ou mais. Se o dispositivo não se Mexe medidores 500 em 72 horas, o utilizador precisa abrir a aplicação Portal da empresa para a avaliação de quebra de desbloqueado por aprimorada.

- **Período de validade do Estado de conformidade (dias)**: Introduza o período de tempo que os dispositivos comunicam o estado para todas as políticas de conformidade recebidas. Os dispositivos que não devolvam o estado dentro deste período de tempo são tratados como não conformes. O valor predefinido é 30 dias.

Pode utilizar estas políticas incorporadas para monitorizar estas definições. Intune também [atualiza ou verifica a existência de atualizações](create-compliance-policy.md#refresh-cycle-times) em intervalos diferentes, consoante a plataforma de dispositivo. [Perguntas comuns, problemas e resoluções com as políticas de dispositivos e perfis no Microsoft Intune](device-profile-troubleshoot.md) é um bom recurso.

Os relatórios de conformidade são uma excelente forma de verificar o estado dos dispositivos. [Monitorizar políticas de conformidade](compliance-policy-monitor.md) inclui algumas orientações.

## <a name="non-compliance-and-conditional-access-on-the-different-platforms"></a>Acesso condicional em diferentes plataformas e a não conformidade

A seguinte tabela descreve como as definições não conformes são geridas quando uma política de conformidade é utilizada com uma política de acesso condicional.

---------------------------

|**Definição de política**| **Plataforma** |
| --- | ----|
| **Configuração do PIN ou da palavra-passe** | - **Android 4.0 e posterior**: Em quarentena</br>- **Samsung Knox Standard 4.0 e posterior**: Em quarentena</br>- **Android Enterprise**: Em quarentena</br></br>- **iOS 8.0 e posterior**: Corrigido</br>- **macOS 10.11 e posterior**: Corrigido</br></br>- **Windows 8.1 e posterior**: Corrigido</br>- **Windows Phone 8.1 e posterior**: Corrigido|
| **Encriptação do dispositivo** | - **Android 4.0 e posterior**: Em quarentena</br>- **Samsung Knox Standard 4.0 e posterior**: Em quarentena</br>- **Android Enterprise**: Em quarentena</br></br>- **iOS 8.0 e posterior**: Corrigido (ao definir um PIN)</br>- **macOS 10.11 e posterior**: Corrigido (ao definir um PIN)</br></br>- **Windows 8.1 e posterior**: Não aplicável</br>- **Windows Phone 8.1 e posterior**: Corrigido |
| **Dispositivo desbloqueado por jailbreak ou obtenção de controlo de raiz** | - **Android 4.0 e posterior**: Em quarentena (não é uma definição)</br>- **Samsung Knox Standard 4.0 e posterior**: Em quarentena (não é uma definição)</br>- **Android Enterprise**: Em quarentena (não é uma definição)</br></br>- **iOS 8.0 e posterior**: Em quarentena (não é uma definição)</br>- **macOS 10.11 e posterior**: Não aplicável</br></br>- **Windows 8.1 e posterior**: Não aplicável</br>- **Windows Phone 8.1 e posterior**: Não aplicável |
| **Perfil de e-mail** | - **Android 4.0 e posterior**: Não aplicável</br>- **Samsung Knox Standard 4.0 e posterior**: Não aplicável</br>- **Android Enterprise**: Não aplicável</br></br>- **iOS 8.0 e posterior**: Em quarentena</br>- **macOS 10.11 e posterior**: Em quarentena</br></br>- **Windows 8.1 e posterior**: Não aplicável</br>- **Windows Phone 8.1 e posterior**: Não aplicável |
| **Versão mínima do SO** | - **Android 4.0 e posterior**: Em quarentena</br>- **Samsung Knox Standard 4.0 e posterior**: Em quarentena</br>- **Android Enterprise**: Em quarentena</br></br>- **iOS 8.0 e posterior**: Em quarentena</br>- **macOS 10.11 e posterior**: Em quarentena</br></br>- **Windows 8.1 e posterior**: Em quarentena</br>- **Windows Phone 8.1 e posterior**: Em quarentena |
| **Versão máxima do SO** | - **Android 4.0 e posterior**: Em quarentena</br>- **Samsung Knox Standard 4.0 e posterior**: Em quarentena</br>- **Android Enterprise**: Em quarentena</br></br>- **iOS 8.0 e posterior**: Em quarentena</br>- **macOS 10.11 e posterior**: Em quarentena</br></br>- **Windows 8.1 e posterior**: Em quarentena</br>- **Windows Phone 8.1 e posterior**: Em quarentena |
| **Atestado do estado de funcionamento do Windows** | - **Android 4.0 e posterior**: Não aplicável</br>- **Samsung Knox Standard 4.0 e posterior**: Não aplicável</br>- **Android Enterprise**: Não aplicável</br></br>- **iOS 8.0 e posterior**: Não aplicável</br>- **macOS 10.11 e posterior**: Não aplicável</br></br>- **Windows 10 e Windows 10 Mobile**: Em quarentena</br>- **Windows 8.1 e posterior**: Em quarentena</br>- **Windows Phone 8.1 e posterior**: Não aplicável |

---------------------------

**Remediado**: Sistema operativo do dispositivo impõe a conformidade. Por exemplo, forçar o utilizador a definir um PIN.

**Em quarentena**: Sistema operativo do dispositivo não impõe a conformidade. Por exemplo, os dispositivos Android e Android Enterprise não forçam o utilizador a encriptar o dispositivo. Quando o dispositivo não é conforme, são realizadas as seguintes ações:

  - Se uma política de acesso condicional se aplicar ao utilizador, o dispositivo é bloqueado.
  - A aplicação Portal da empresa notifica o utilizador sobre eventuais problemas de conformidade.

## <a name="azure-classic-portal-vs-azure-portal"></a>Portal clássico do Azure vs.  Portal do Azure

A principal diferença ao utilizar políticas de conformidade de dispositivos no portal do Azure:

- No portal do Azure, as políticas de conformidade são criadas em separado para cada plataforma suportada
- No portal clássico do Azure, uma política de conformidade de dispositivos é comum a todas as plataformas suportadas

<!--- -   In the Azure portal, you have the ability to specify actions and notifications that are initiated when a device is determined to be noncompliant. This ability does not exist in the Intune admin console.

-   In the Azure portal, you can set a grace period to allow time for the end-user to get their device back to compliance status before they completely lose the ability to get company data on their device. This is not available in the Intune admin console.--->

As políticas de conformidade de dispositivos criadas no [portal clássico do Azure](https://manage.microsoft.com) não aparecem no [portal do Azure](https://portal.azure.com). No entanto, continuam a ser direcionadas para os utilizadores e geríveis através do portal clássico.

Para utilizar as funcionalidades relacionadas com a conformidade de dispositivos no portal do Azure, terá de criar novas políticas de conformidade de dispositivos no portal do Azure. Se atribuir uma política de conformidade de dispositivos no portal do Azure a um utilizador a quem também tenha sido atribuída uma política de conformidade de dispositivos do portal clássico, as políticas de conformidade de dispositivos do portal do Azure terão precedência sobre as políticas criadas no portal clássico.

## <a name="next-steps"></a>Passos Seguintes

- [Criar uma política](create-compliance-policy.md) e ver os pré-requisitos.
- Ver as definições de conformidade para as plataformas de dispositivos diferentes:

  - [Android](compliance-policy-create-android.md)
  - [Android Enterprise](compliance-policy-create-android-for-work.md)
  - [iOS](compliance-policy-create-ios.md)
  - [macOS](compliance-policy-create-mac-os.md)
  - [Windows 10 e posterior](compliance-policy-create-windows.md)
  - [Windows 8.1 e Windows Phone 8.1](compliance-policy-create-windows-8-1.md)

- [Referência para as entidades de políticas](reports-ref-policy.md) tem informações sobre as entidades de política do armazém de dados do Intune.