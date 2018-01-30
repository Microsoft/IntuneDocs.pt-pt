---
title: "Criar uma política de conformidade para Android for Work"
titleSuffix: Azure portal
description: "Saiba como criar uma política de conformidade para dispositivos Android for Work.\""
keywords: 
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9da89713-6306-4468-b211-57cfb4b51cc6
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e9ec660fcbd1f02fb0767e322edfdfa7f85964a7
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/25/2018
---
# <a name="how-to-create-a-device-compliance-policy-for-android-for-work-devices-in-intune"></a>Como criar uma política de conformidade para dispositivos Android for Work no Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

As políticas de conformidade são criadas para cada plataforma.  Pode criar uma política de conformidade no portal do Azure. Para obter mais informações sobre o que é a política de compatibilidade, veja o tópico [O que é a conformidade do dispositivo](device-compliance.md). Para saber mais sobre os pré-requisitos que tem de cumprir antes de criar uma política de conformidade, veja o tópico [Introdução à conformidade do dispositivo](device-compliance-get-started.md).

A tabela que se segue descreve como as definições não conformes são geridas quando uma política de conformidade é utilizada com uma política de acesso condicional.

--------------------------

|**definição de política**| **Android for Work** |
| --- | --- |
| **Configuração do PIN ou da palavra-passe** |  Em quarentena |
| **Encriptação do dispositivo** |  Em quarentena |
| **Dispositivo desbloqueado por jailbreak ou obtenção de controlo de raiz** | Em quarentena (não é uma definição) |
| **perfil de e-mail** | Não aplicável |
| **Versão mínima do SO** | Em quarentena |
| **Versão máxima do SO** | Em quarentena |
| **Atestado do estado de funcionamento do Windows** |Não aplicável |

**Remediado** = O sistema operativo do dispositivo impõe a conformidade. (Por exemplo, forçar o utilizador a definir um PIN.)+

**Em Quarentena** = O sistema operativo do dispositivo não impõe a conformidade. (Por exemplo, os dispositivos Android não forçam o utilizador a encriptar o dispositivo.) Quando os dispositivos não são conformes, são efetuadas as seguintes ações:

- O dispositivo é bloqueado se uma política de acesso condicional se aplicar ao utilizador.
- O portal da empresa notifica o utilizador sobre eventuais problemas de conformidade.

## <a name="create-a-compliance-policy-in-the-azure-portal"></a>Criar uma política de conformidade no portal do Azure

1. No painel **Intune**, escolha **Definir Conformidade do dispositivo**. Em **Gerir**, escolha **Todas as políticas de conformidade do dispositivo** e **Criar**.
2. Escreva um nome, uma descrição e escolha a plataforma à qual quer que esta política se aplique.
3. Escolha **Requisitos de conformidade** para especificar as definições de **Segurança**, de **Estado de funcionamento do dispositivo** e de **Propriedade do dispositivo** aqui. Quando tiver terminado, escolha **OK**.

<!--- 4. Choose **Actions for noncompliance** to say what actions should happen when a device is determined as noncompliant with this policy.
5. In the **Actions for noncompliance** blade, choose **Add** to create a new action.  The action parameters blade allows you to specify the action, email recipients that should receive the notification in addition to the user of the device, and the content of the notification that you want to send.
6. The message template option allows you to create several custom emails depending on when the action is set to take. For example, you can create a message for notifications that are sent for the first time and a different message for final warning before access is blocked. The custom messages that you create can be used for all your device compliance policy.
7. Specify the **Grace period** which determines when that action to take place.  For example, you may want to send a notification as soon as the device is evaluated as noncompliant, but allow some time before enforcing the conditional access policy to block access to company resources like SharePoint online.
8. Choose **Add** to finish creating the action.
9. You can create multiple actions and the sequence in which they should occur. Choose **Ok** when you are finished creating all the actions.--->

## <a name="assign-user-groups"></a>Atribuir grupos de utilizadores

Para atribuir uma política de conformidade a utilizadores, escolha uma política que tenha configurado. As políticas existentes encontram-se no painel **Conformidade – política**.

1. Escolha a política que quer atribuir aos utilizadores e, em seguida, **Atribuições**. Esta ação abre o painel onde pode selecionar **Grupos de segurança do Azure Active Directory** e atribuí-los à política.
2. Escolha **Selecionar grupos** para abrir o painel que apresenta os grupos de segurança do Azure AD.  Escolher **Selecionar** implementa a política para os utilizadores.

Aplicou a política aos utilizadores.  Os dispositivos utilizados pelos utilizadores visados pela política serão avaliados quanto à conformidade.

<!--- ##  Compliance policy settings--->

## <a name="system-security-settings"></a>Definições de segurança do sistema

### <a name="password"></a>Palavra-passe

- **Palavra-passe obrigatória para desbloquear dispositivos móveis:** defina esta opção como **Sim** para exigir que os utilizadores introduzam uma palavra-passe para que possam aceder ao respetivo dispositivo.
- **Comprimento mínimo da palavra-passe:** especifique o número mínimo de dígitos ou carateres que a palavra-passe tem de ter.
- **Qualidade da palavra-passe:** esta definição deteta se os requisitos de palavra-passe que especificou estão configurados no dispositivo. Ative esta definição para exigir que os utilizadores configurem determinados requisitos de palavra-passe para dispositivos Android. Escolha entre:
  - **Biométrica de segurança baixa**
  - **Necessário**
  - **Pelo menos numérica**
  - **Pelo menos alfabética**
  - **Pelo menos alfanumérica**
  - **Alfanumérica com símbolos**
- **Minutos de inatividade antes de a palavra-passe ser exigida:** especifica o tempo de inatividade antes de o utilizador ter de reintroduzir a palavra-passe.
- **Expiração da palavra-passe (dias):** selecione o número de dias antes de a palavra-passe do utilizador expirar e ser preciso criar uma nova.
- **Memorizar histórico de palavras-passe:** utilize esta definição juntamente com **Impedir a reutilização de palavras-passe anteriores** para impedir o utilizador de criar palavras-passe utilizadas anteriormente.
- **Impedir a reutilização de palavras-passe anteriores:** se a opção **Memorizar histórico de palavras-passe** estiver selecionada, especifique o número de palavras-passe utilizadas anteriormente que não podem ser reutilizadas.
- **Exigir uma palavra-passe quando o dispositivo regressa de um estado inativo:** esta definição deve ser utilizada em conjunto com a definição **Minutos de inatividade antes de a palavra-passe ser exigida**. Será pedido aos utilizadores finais que introduzam uma palavra-passe para aceder a dispositivos que tenham estado inativos durante o período de tempo especificado na definição **Minutos de inatividade antes de a palavra-passe ser exigida**.


### <a name="encryption"></a>Encriptação

- **Exigir encriptação em dispositivos móveis:** uma vez que os dispositivos Android for Work impõem a encriptação, não necessita de configurar esta definição.


## <a name="device-health-and-security-settings"></a>Definições de estado de funcionamento e segurança do dispositivo

- **O dispositivo não pode ter jailbreak ou root:** se ativar esta definição, os dispositivos com jailbreak serão avaliados como não conformes.
- **Exigir que os dispositivos impeçam a instalação de aplicações de origens desconhecidas:** uma vez que os dispositivos Android for Work restringem sempre a instalação de origens desconhecidas, não necessita de configurar esta definição. .
- **Exigir que a depuração USB esteja desativada**: uma vez que a depuração USB já se encontra desativada em dispositivos Android for Work, não necessita de configurar esta definição.
- **Nível do patch de segurança mínimo Android**: utilize esta definição para especificar o nível de patch de segurança mínimo de Android. Os dispositivos que não tenham, pelo menos, este nível de correção não serão conformes. A data tem de ser especificada no formato: AAAA-MM-DD.
- **Exigir que a proteção contra ameaças de dispositivos seja ativada**: utilize esta definição para assumir a avaliação de riscos da solução Lookout MTP como uma condição para conformidade. Selecione o nível de ameaça máximo permitido, que será um dos seguintes:
  - **Nenhum (seguro):** é o nível mais seguro. Isto significa que o dispositivo não pode ter nenhuma ameaça. Se o dispositivo detetar qualquer nível de ameaças, será avaliado como não conforme.
  - **Baixo:** o dispositivo é avaliado como conforme se só estiverem presentes ameaças de nível baixo. Qualquer nível mais alto coloca o dispositivo num estado de não conforme.
  - **Médio:** o dispositivo é avaliado como conforme se só estiverem presentes ameaças de nível baixo ou médio. Se forem detetadas ameaças de nível alto no dispositivo, será determinado como não conforme.
  - **Alto:** este é o nível menos seguro. Essencialmente, este nível permite todos os níveis de ameaças e possivelmente só será útil se utilizar esta solução apenas para a criação de relatórios.

Para obter mais detalhes, consulte [Ativar a regra de proteção contra ameaças de dispositivo na política de conformidade](https://docs.microsoft.com/intune-classic/deploy-use/enable-device-threat-protection-rule-in-compliance-policy).

## <a name="device-property-settings"></a>Definições de propriedade do dispositivo

- **SO mínimo necessário:** quando um dispositivo não cumpre o requisito de versão mínima do SO, será reportado como não conforme. É apresentada uma ligação com informações sobre como atualizar. O utilizador final pode optar por atualizar o dispositivo para poder aceder aos recursos da empresa.
- **Versão do SO máxima permitida:** quando um dispositivo utiliza uma versão do SO posterior à especificada na regra, o acesso aos recursos da empresa é bloqueado e é pedido ao utilizador que contacte o administrador de TI. Até a regra ser alterada para permitir a versão do SO, este dispositivo não pode ser utilizado no acesso aos recursos da empresa.

<!--- ## Next steps

[How to monitor device compliance](device-compliance-monitor.md)--->
