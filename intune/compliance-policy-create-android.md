---
title: "Como criar uma política de conformidade para Android"
titleSuffix: Intune on Azure
description: "Saiba como criar uma política de conformidade para dispositivos Android.\""
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e1258fe4-0b5c-4485-8bd1-152090df6345
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: cc68bf4a52e5fcf9a8fbb3550a5bee814f4f46f0
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/01/2017
---
# <a name="how-to-create-a-device-compliance-policy-for-android-devices-in-intune"></a>Como criar uma política de conformidade para dispositivos Android no Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

As políticas de conformidade do dispositivo são criadas para cada formulário de plataforma do Intune no portal do Azure. 

- Para obter mais informações sobre o que é a política de compatibilidade, veja o tópico [O que é a conformidade do dispositivo](device-compliance.md).
- Para saber mais sobre os pré-requisitos que tem de cumprir antes de criar uma política de conformidade, veja o tópico [Introdução à conformidade do dispositivo](device-compliance-get-started.md).

## <a name="to-create-a-device-compliance-policy"></a>Para criar uma política de conformidade do dispositivo

1. No painel **Intune**, escolha **Definir Conformidade do dispositivo**. Em **Gerir**, escolha **Todas as políticas de conformidade do dispositivo** e **Criar**.
2. Escreva um nome, uma descrição e escolha a plataforma à qual quer que esta política se aplique.
3. Escolha **Requisitos de conformidade** para especificar as definições de **Segurança**, de **Estado de funcionamento do dispositivo** e de **Propriedade do dispositivo**. Quando tiver terminado, escolha **OK**.

<!-- 4. Choose **Actions for noncompliance** to say what actions should happen when a device is determined as noncompliant based on the configured settings in this policy.
5. In the **Actions for noncompliance** blade, choose **Add** to create a new action.  The action parameters blade allows you to specify the action, email recipients that should receive the notification in addition to the user of the device, and the content of the notification that you want to send.
6. The message template option allows you to create several custom emails depending on when the action is set to take. For example, you can create a message for notifications that are sent for the first time and a different message for final warning before access is blocked. The custom messages that you create can be used for all your device compliance policy.
7. Specify the **Grace period** which determines when that action to take place.  For example, you may want to send a notification as soon as the device is evaluated as noncompliant, but allow some time before enforcing the conditional access policy to block access to company resources like SharePoint online.
8. Choose **Add** to finish creating the action.
9. You can create multiple actions and the sequence in which they should occur. Choose **OK** when you are finished creating all the actions.-->

## <a name="to-assign-user-groups"></a>Para atribuir grupos de utilizadores

Para atribuir uma política de conformidade a utilizadores, escolha uma política que tenha configurado. As políticas existentes encontram-se no painel **Conformidade – políticas**.

1. Escolha a política e, em seguida, **Atribuições**. Esta ação abre o painel onde pode selecionar **Grupos de segurança do Azure Active Directory** e atribuí-los à política.
2. Escolha **Selecionar grupos** para abrir o painel que apresenta os grupos de segurança do Azure AD. Aqui pode encontrar todos os grupos de segurança do Azure Active Directory.  Pode selecionar os grupos de utilizadores aos quais pretende aplicar esta política e escolher **Selecionar**. Escolher **Selecionar** implementa a política para os utilizadores.

Aplicou a política aos utilizadores.  Os dispositivos utilizados pelos utilizadores visados pela política serão avaliados quanto à conformidade.

<!---##  Compliance policy settings--->

## <a name="device-health-and-security-settings"></a>Definições de estado de funcionamento e segurança do dispositivo

- **O dispositivo não pode ter jailbreak ou root**: se ativar esta definição, os dispositivos com jailbreak serão avaliados como não conformes.
- **Exigir que os dispositivos impeçam a instalação de aplicações de origens desconhecidas (Android 4.0 ou posterior)**: para bloquear os dispositivos que tenham a opção **Segurança** > **Origens desconhecidas** ativada no dispositivo, ative esta definição e defina-a como **Sim**.

### <a name="important"></a>Importante

As aplicações de sideload requerem a ativação da definição **Origens desconhecidas**. Aplique esta política de conformidade apenas se não tiver aplicações Android de sideload nos dispositivos.

- **Exigir que a depuração USB esteja desativada (Android 4.2 ou posterior)**: esta definição especifica se a opção de deteção de depuração USB no dispositivo está ativada.
- **Exigir que os dispositivos tenham ativado o dispositivo de Análise para ameaças de segurança (Android 4.2 a 4.4)**: esta definição especifica que a funcionalidade **Verificar aplicações** está ativada no dispositivo.
- **Nível mínimo de correção de segurança Android (Android 6.0 ou posterior)**: utilize esta definição para especificar o nível mínimo de correção Android. Os dispositivos que não tenham, pelo menos, este nível de correção não serão conformes. A data tem de ser especificada no formato AAAA-MM-DD.
- **Exigir que a proteção contra ameaças de dispositivos seja ativada**: utilize esta definição para assumir a avaliação de riscos da solução Lookout MTP como uma condição para conformidade. Selecione o nível de ameaça máximo permitido, que será um dos seguintes:
  - **Nenhum (seguro)**: este é o nível mais seguro. Isto significa que o dispositivo não pode ter nenhuma ameaça. Se o dispositivo detetar qualquer nível de ameaças, será avaliado como não conforme.
  - **Baixo**: o dispositivo é avaliado como conforme se só estiverem presentes ameaças de nível baixo. Qualquer nível mais alto coloca o dispositivo num estado de não conforme.
  - **Médio**: o dispositivo é avaliado como conforme se só estiverem presentes ameaças de nível baixo ou médio. Se forem detetadas ameaças de nível alto no dispositivo, este será determinado como não conforme.
  - **Alto**: este é o nível menos seguro. Essencialmente, isto permite todos os níveis de ameaça. Provavelmente, será útil se utilizar esta solução apenas para fins de relatórios.

Para obter mais detalhes, consulte [Ativar a regra de proteção contra ameaças de dispositivo na política de conformidade](https://docs.microsoft.com/intune-classic/deploy-use/enable-device-threat-protection-rule-in-compliance-policy).

## <a name="system-security-settings"></a>Definições de segurança do sistema

### <a name="password"></a>Palavra-passe

- **Palavra-passe obrigatória para desbloquear dispositivos móveis**: defina esta opção como **Sim** para exigir que os utilizadores introduzam uma palavra-passe para poderem aceder aos dispositivos deles.
- **Comprimento mínimo da palavra-passe**: especifique o número mínimo de dígitos ou carateres que a palavra-passe do utilizador tem de ter.
- **Qualidade da palavra-passe**: esta definição deteta se os requisitos de palavra-passe que especificou estão configurados no dispositivo. Ative esta definição para exigir que os utilizadores cumpram determinados requisitos de palavra-passe para dispositivos Android. Escolha entre:
  - **Biométrica de segurança baixa**
  - **Necessário**
  - **Pelo menos numérica**
  - **Pelo menos alfabética**
  - **Pelo menos alfanumérica**
  - **Alfanumérica com símbolos**
- **Minutos de inatividade antes de a palavra-passe ser exigida**: especifique o tempo de inatividade antes de o utilizador ter de reintroduzir a palavra-passe.
- **Expiração da palavra-passe (dias)**: selecione o número de dias antes de a palavra-passe expirar e ser preciso criar uma nova.
- **Memorizar histórico de palavras-passe**: utilize esta definição juntamente com **Impedir a reutilização de palavras-passe anteriores** para impedir o utilizador de criar palavras-passe utilizadas anteriormente.
- **Impedir a reutilização de palavras-passe anteriores**: se tiver selecionado **Memorizar histórico de palavras-passe**, especifique o número de palavras-passe utilizadas anteriormente que não podem ser reutilizadas.
- **Exigir uma palavra-passe quando o dispositivo regressa de um estado inativo**: utilize esta definição em conjunto com a definição **Minutos de inatividade antes de a palavra-passe ser exigida**. Será pedido ao utilizador que introduza uma palavra-passe para aceder a dispositivos que tenham estado inativos durante o período de tempo especificado na definição **Minutos de inatividade antes de a palavra-passe ser exigida**.

### <a name="encryption"></a>Encriptação

- **Exigir encriptação no dispositivo móvel**: defina esta opção como **Sim** para exigir que os dispositivos sejam encriptados para ligar aos recursos. Os dispositivos são encriptados quando seleciona a definição **Palavra-passe obrigatória para desbloquear os dispositivos móveis**.

## <a name="device-property-settings"></a>Definições de propriedade do dispositivo

- **SO mínimo obrigatório**: quando um dispositivo não cumpre o requisito de versão mínima do SO, será reportado como não conforme. É apresentada uma hiperligação com informações sobre como atualizar. O utilizador pode optar por atualizar o dispositivo para poder aceder aos recursos da empresa.
- **Versão máxima de SO permitida**: quando um dispositivo utiliza uma versão do SO posterior à especificada na regra, o acesso aos recursos da empresa é bloqueado e é pedido ao utilizador que contacte o administrador de TI. Até as regras serem alteradas para permitir a versão do SO, este dispositivo não pode ser utilizado no acesso aos recursos da empresa.

## <a name="how-non-compliant-settings-work-with-conditional-access-policies"></a>Como é que as definições não compatíveis funcionam com as políticas de acesso condicional?

A tabela seguinte descreve como as definições não compatíveis são geridas quando uma política de conformidade é utilizada com uma política de acesso condicional.

--------------------

|**Definição de política**| **Android 4.0 e posterior, Samsung Knox Standard 4.0 e posterior** |
| --- | ----|
| **Configuração do PIN ou da palavra-passe** |  Em quarentena |
| **Encriptação do dispositivo** | Em quarentena |
| **Dispositivo desbloqueado por jailbreak ou obtenção de controlo de raiz** | Em quarentena (não é uma definição) |
| **perfil de e-mail** | Não aplicável |
| **Versão mínima do SO** | Em quarentena |
| **Versão máxima do SO** |   Em quarentena |
| **Atestado do estado de funcionamento do Windows** | Não aplicável |

--------------------------

**Remediado** = O sistema operativo do dispositivo impõe a conformidade. (Por exemplo, forçar o utilizador a definir um PIN.)+

**Em Quarentena** = O sistema operativo do dispositivo não impõe a conformidade. (Por exemplo, os dispositivos Android não forçam o utilizador a encriptar o dispositivo.) Quando os dispositivos não são conformes, são realizadas as seguintes ações:+

- O dispositivo é bloqueado se uma política de acesso condicional se aplicar ao utilizador.
- O portal da empresa notifica o utilizador sobre eventuais problemas de conformidade.

<!--- ## Next steps

[How to monitor device compliance](device-compliance-monitor.md)--->
