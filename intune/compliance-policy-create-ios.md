---
title: "Como criar uma política de conformidade para iOS"
titleSuffix: Intune on Azure
description: "Saiba como criar uma política de conformidade para dispositivos iOS.\""
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3cfb8222-d05b-49e3-ae6f-36ce1a16c61d
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 9337586ad5daa909f38aba2b25fc159b44f55e65
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/01/2017
---
# <a name="how-to-create-a-device-compliance-policy-for-ios-devices-in-intune"></a>Como criar uma política de conformidade para dispositivos iOS no Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

As políticas de conformidade são criadas para cada plataforma.  Pode criar uma política de conformidade no portal do Azure. Para obter mais informações sobre o que é a política de compatibilidade, veja o tópico [O que é a conformidade do dispositivo](device-compliance.md). Para saber mais sobre os pré-requisitos que tem de cumprir antes de criar uma política de conformidade, veja o tópico [Introdução à conformidade do dispositivo](device-compliance-get-started.md).

A tabela que se segue descreve como as definições não conformes são geridas quando uma política de conformidade é utilizada com uma política de acesso condicional.

-------------------------------


| **Definição de política** | **iOS 8.0 e posterior** |
| --- | --- |
| **Configuração do PIN ou da palavra-passe** | Corrigido |   
| **Encriptação do dispositivo** | Corrigido (ao definir um PIN) |
| **Dispositivo desbloqueado por jailbreak ou obtenção de controlo de raiz** | Em quarentena (não é uma definição)
| **Perfil de e-mail** | Em quarentena |
|**Versão mínima do SO** | Em quarentena |
| **Versão máxima do SO** | Em quarentena |  
| **Atestado do estado de funcionamento do Windows** | Não aplicável |  
----------------------------


**Remediado** = O sistema operativo do dispositivo impõe a conformidade. (Por exemplo, forçar o utilizador a definir um PIN.)

**Em Quarentena** = O sistema operativo do dispositivo não impõe a conformidade. (Por exemplo, os dispositivos Android não forçam o utilizador a encriptar o dispositivo.) Quando os dispositivos não são conformes, são efetuadas as seguintes ações:

- O dispositivo é bloqueado se uma política de acesso condicional se aplicar ao utilizador.
- O portal da empresa notifica o utilizador sobre eventuais problemas de conformidade.

## <a name="create-a-compliance-policy-in-the-azure-portal"></a>Criar uma política de conformidade no portal do Azure

1. No painel **Intune**, escolha **Definir Conformidade do dispositivo**. Em **Gerir**, escolha **Todas as políticas de conformidade do dispositivo** e **Criar**.
2. Escreva um nome, uma descrição e escolha a plataforma à qual quer que esta política se aplique.
3. Escolha **Requisitos de conformidade** para especificar as definições de **Segurança**, de **Estado de funcionamento do dispositivo** e de **Propriedade do dispositivo** aqui. Quando tiver terminado, escolha **OK**.

<!--- 4. Choose **Actions for noncompliance** to say what actions should happen when a device is determined as noncompliant with this policy.
5. In the **Actions for noncompliance** blade, choose **Add** to create a new action.  The action parameters blade allows you to specify the action, email recipients that should receive the notification in addition to the user of the device, and the content of the notification that you want to send.
7. The message template option allows you to create several custom emails depending on when the action is set to take. For example, you can create a message for notifications that are sent for the first time and a different message for final warning before access is blocked. The custom messages that you create can be used for all your device compliance policy.
7. Specify the **Grace period** which determines when that action to take place.  For example, you may want to send a notification as soon as the device is evaluated as noncompliant, but allow some time before enforcing the conditional access policy to block access to company resources like SharePoint online.
8. Choose **Add** to finish creating the action.
9. You can create multiple actions and the sequence in which they should occur. Choose **Ok** when you are finished creating all the actions.--->

## <a name="assign-user-groups"></a>Atribuir grupos de utilizadores

Para atribuir uma política de conformidade a utilizadores, escolha uma política que tenha configurado. As políticas existentes encontram-se no painel **Conformidade – políticas**.

1. Escolha a política que quer atribuir aos utilizadores e, em seguida, **Atribuições**. Esta ação abre o painel onde pode selecionar **Grupos de segurança do Azure Active Directory** e atribuí-los à política.
2. Escolha **Selecionar grupos** para abrir o painel que apresenta os grupos de segurança do Azure AD.  Escolher **Selecionar** implementa a política para os utilizadores.

Aplicou a política aos utilizadores.  Os dispositivos utilizados pelos utilizadores visados pela política serão avaliados quanto à conformidade.

<!---## Compliance policy settings--->

## <a name="system-security-settings"></a>Definições de segurança do sistema

### <a name="password"></a>Palavra-passe

- **Exigir uma palavra-passe para desbloquear dispositivos móveis**: defina esta opção como **Sim** para exigir que o utilizador introduza uma palavra-passe para poder aceder ao dispositivo dele. Os dispositivos iOS que utilizam uma palavra-passe são encriptados.
- **Permitir palavras-passe simples**: defina esta opção para **Sim** para permitir que o utilizador crie uma palavra-passe simples, como **1234** ou **1111**.
- **Comprimento mínimo da palavra-passe**: especifique o número mínimo de dígitos ou carateres que a palavra-passe tem de ter.
- **Tipo obrigatório de palavra-passe**: especifique se o utilizador tem de criar uma palavra-passe **Alfanumérica** ou **Numérica**.
- **Número mínimo de conjuntos de carateres**: se definir **Tipo obrigatório de palavra-passe** como **Alfanumérico**, utilize esta definição para especificar o número mínimo de conjuntos de carateres que a palavra-passe deve ter. Os quatro conjuntos de carateres são:
  - Letras minúsculas
  - Letras maiúsculas
  - Símbolos
  - Números

Definir um número mais relevado requer que o utilizador crie uma palavra-passe mais complexa.

Para dispositivos iOS, esta definição refere-se ao número de carateres especiais (por exemplo, **!** , **#**, **&amp;**) que têm de ser incluídos na palavra-passe.

- **Minutos de inatividade antes de a palavra-passe ser exigida**: especifique o tempo de inatividade antes de o utilizador ter de reintroduzir a palavra-passe.
- **Expiração da palavra-passe (dias)**: selecione o número de dias antes de a palavra-passe expirar e ser preciso criar uma nova.
- **Memorizar histórico de palavras-passe**: utilize esta definição juntamente com **Impedir a reutilização de palavras-passe anteriores** para impedir o utilizador de criar palavras-passe utilizadas anteriormente.
- **Impedir a reutilização de palavras-passe anteriores**: se tiver selecionado **Memorizar histórico de palavras-passe**, especifique o número de palavras-passe utilizadas anteriormente que não podem ser reutilizadas.
- **Exigir uma palavra-passe quando o dispositivo regressa de um estado inativo**: utilize esta definição em conjunto com a definição em **Minutos de inatividade antes de a palavra-passe ser exigida**. Será pedido ao utilizador que introduza uma palavra-passe para aceder a dispositivos que tenham estado inativos durante o período de tempo especificado na definição **Minutos de inatividade antes de a palavra-passe ser exigida**.

### <a name="email-profile"></a>Perfil de e-mail

- **A conta de e-mail tem de ser gerida pelo Intune**: quando esta opção está definida como **Sim**, o dispositivo tem de utilizar o perfil de e-mail implementado no dispositivo. O dispositivo é considerado não conforme nas seguintes situações:
  - O perfil de e-mail é implementado para um grupo de utilizadores que não o grupo de utilizadores visado pela política de conformidade.
  - O utilizador já configurou uma conta de e-mail no dispositivo que corresponde ao perfil de e-mail do Intune implementado no dispositivo. O Intune não pode substituir o perfil aprovisionado pelo utilizador, pelo que não o consegue gerir. Para garantir a conformidade, o utilizador tem de remover as definições de e-mail existentes. Em seguida, o Intune pode instalar o perfil de e-mail gerido.
- **Selecionar o perfil de e-mail que deve ser gerido pelo Intune**: se a definição **A conta de e-mail tem de ser gerida pelo Intune** estiver selecionada, escolha a opção **Selecionar** para especificar o perfil de e-mail do Intune. O perfil de e-mail tem de estar presente no dispositivo.

Para obter informações sobre o perfil de e-mail, veja [Configurar o acesso a e-mail empresarial através de perfis de e-mail com o Microsoft Intune](https://docs.microsoft.com/intune-classic/deploy-use/configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune).

## <a name="device-health-settings"></a>Definições de estado de funcionamento do dispositivo

- **O dispositivo não pode ter jailbreak ou root**: se ativar esta definição, os dispositivos com jailbreak não serão conformes.

## <a name="device-properties"></a>Propriedades do dispositivo

- **SO mínimo obrigatório**: quando um dispositivo não cumpre o requisito de versão mínima do SO, será reportado como não conforme. É apresentada uma hiperligação com informações sobre como atualizar. O utilizador pode optar por atualizar o dispositivo. Depois, pode aceder aos recursos da empresa.
- **Versão máxima de SO permitida**: quando um dispositivo utiliza uma versão do SO posterior à especificada na regra, o acesso aos recursos da empresa é bloqueado e é pedido ao utilizador que contacte o administrador de TI. Até a regra ser alterada para permitir a versão do SO, este dispositivo não pode ser utilizado no acesso aos recursos da empresa.

<!--- ## Next steps

[How to monitor device compliance](device-compliance-monitor.md)--->
