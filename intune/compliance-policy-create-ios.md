---
title: Criar política de conformidade de dispositivos iOS no Microsoft Intune – Azure | Microsoft Docs
description: Crie uma política de conformidade de dispositivos no Microsoft Intune para dispositivos iOS para introduzir uma conta de e-mail, verificar dispositivos alvo de jailbreak, verificar a versão mínima e máxima do sistema operativo e definir restrições de palavra-passe, incluindo comprimento da palavra-passe e inatividade de dispositivos.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/20/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 3cfb8222-d05b-49e3-ae6f-36ce1a16c61d
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 887f45cdc79aa5e45de3e8a1df5d12665d2ed8ab
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/16/2018
---
# <a name="add-a-device-compliance-policy-for-ios-devices-in-intune"></a>Adicionar uma política de conformidade de dispositivos para dispositivos iOS no Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Uma política de conformidade de dispositivos iOS no Intune determina as regras e definições que os dispositivos iOS têm de cumprir para estarem em conformidade. Quando utiliza políticas de conformidade de dispositivos com acesso condicional, pode permitir ou bloquear o acesso aos recursos da empresa. Também pode obter relatórios de dispositivos e agir relativamente a situações de não conformidade. Pode criar as políticas de conformidade de dispositivos para cada plataforma no portal do Azure no Intune. Para saber mais sobre políticas de conformidade e os pré-requisitos de que precisa antes de criar uma política de conformidade, veja [Introdução à conformidade do dispositivo](device-compliance-get-started.md).

A seguinte tabela descreve como as definições não conformes são geridas quando uma política de conformidade é utilizada com uma política de acesso condicional.

| **Definição de política** | **iOS 8.0 e posterior** |
| --- | --- |
| **Configuração do PIN ou da palavra-passe** | Corrigido |
| **Encriptação do dispositivo** | Corrigido (ao definir um PIN) |
| **Dispositivo desbloqueado por jailbreak ou obtenção de controlo de raiz** | Em quarentena (não é uma definição)
| **Perfil de e-mail** | Em quarentena |
|**Versão mínima do SO** | Em quarentena |
| **Versão máxima do SO** | Em quarentena |
| **Atestado do estado de funcionamento do Windows** | Não aplicável |

**Remediado** = O sistema operativo do dispositivo impõe a conformidade. (Por exemplo, forçar o utilizador a definir um PIN.)

**Em Quarentena** = O sistema operativo do dispositivo não impõe a conformidade. (Por exemplo, os dispositivos Android não forçam o utilizador a encriptar o dispositivo.) Quando o dispositivo não é conforme, são efetuadas as seguintes ações:

- O dispositivo é bloqueado se uma política de acesso condicional se aplicar ao utilizador.
- O portal da empresa notifica o utilizador sobre eventuais problemas de conformidade.

## <a name="create-a-compliance-policy-in-the-azure-portal"></a>Criar uma política de conformidade no portal do Azure

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços**, filtre por **Intune** e selecione **Microsoft Intune**.
3. Selecione **Conformidade do dispositivo** > **Políticas** > **Criar Política**.
4. Introduza um nome, uma descrição e escolha a plataforma à qual pretende que esta política se aplique.
5. Selecione **Definições** para introduzir as definições de **E-mail**, **Estado de Funcionamento do Dispositivo**, **Propriedades do Dispositivo** e **Segurança do Sistema**. Quando tiver terminado, selecione **OK**.

<!--- 4. Choose **Actions for noncompliance** to say what actions should happen when a device is determined as noncompliant with this policy.
5. In the **Actions for noncompliance** pane, choose **Add** to create a new action.  The action parameters pane allows you to specify the action, email recipients that should receive the notification in addition to the user of the device, and the content of the notification that you want to send.
7. The message template option allows you to create several custom emails depending on when the action is set to take. For example, you can create a message for notifications that are sent for the first time and a different message for final warning before access is blocked. The custom messages that you create can be used for all your device compliance policy.
7. Specify the **Grace period** which determines when that action to take place.  For example, you may want to send a notification as soon as the device is evaluated as noncompliant, but allow some time before enforcing the conditional access policy to block access to company resources like SharePoint online.
8. Choose **Add** to finish creating the action.
9. You can create multiple actions and the sequence in which they should occur. Choose **Ok** when you are finished creating all the actions.--->

## <a name="assign-user-groups"></a>Atribuir grupos de utilizadores

Para atribuir uma política de conformidade a utilizadores, escolha uma política que tenha configurado. As políticas existentes encontram-se no painel **Conformidade do dispositivo – Políticas**.

1. Escolha a política que quer atribuir aos utilizadores e, em seguida, **Atribuições**. É aberto um painel onde pode selecionar **grupos de segurança do Azure Active Directory** e atribuí-los à política.
2. Selecione **Grupos selecionados** para abrir o painel que apresenta os grupos de segurança do Azure AD.  Selecionar **Guardar** implementa a política para os utilizadores.

Aplicou a política aos utilizadores.  Os dispositivos utilizados pelos utilizadores visados pela política são avaliados quanto à conformidade.

<!---## Compliance policy settings--->

## <a name="email"></a>E-mail

- **A conta de e-mail tem de ser gerida pelo Intune:** quando esta opção está definida como **Sim**, o dispositivo tem de utilizar o perfil de e-mail implementado no dispositivo. O dispositivo é considerado não conforme nas seguintes situações:
  - O perfil de e-mail é implementado para um grupo de utilizadores que não o grupo de utilizadores visado pela política de conformidade.
  - O utilizador já configurou uma conta de e-mail no dispositivo que corresponde ao perfil de e-mail do Intune implementado no dispositivo. O Intune não pode substituir o perfil aprovisionado pelo utilizador, pelo que não o consegue gerir. Para garantir a conformidade, o utilizador tem de remover as definições de e-mail existentes. Em seguida, o Intune pode instalar o perfil de e-mail gerido.
- **Selecionar o perfil de e-mail que deve ser gerido pelo Intune:** se a definição **A conta de e-mail tem de ser gerida pelo Intune** estiver selecionada, selecione a opção **Selecionar** para especificar o perfil de e-mail do Intune. O perfil de e-mail tem de estar presente no dispositivo.

Para obter informações sobre o perfil de e-mail, veja [Configurar o acesso a e-mail empresarial através de perfis de e-mail com o Microsoft Intune](https://docs.microsoft.com/intune-classic/deploy-use/configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune).

## <a name="device-health"></a>Device health

- **Dispositivos alvo de jailbreak**: se ativar esta definição, os dispositivos alvo de jailbreak não são conformes.
- **Exigir que o dispositivo esteja ao Nível de Ameaças do Dispositivo ou abaixo do mesmo**: selecione o nível de ameaça máximo para marcar dispositivos como não conformes. Por exemplo, se definir o nível de ameaça para **Médio**, então os dispositivos nos níveis médio, baixo ou protegido são conformes. Os dispositivos com um nível de ameaça elevado não são conformes.

## <a name="device-properties"></a>Propriedades do dispositivo

- **SO mínimo necessário:** quando um dispositivo não cumpre o requisito de versão mínima do SO, será reportado como não conforme. É apresentada uma hiperligação com informações sobre como atualizar. O utilizador pode optar por atualizar o dispositivo. Depois, pode aceder aos recursos da empresa.
- **Versão do SO máxima permitida**: quando um dispositivo utiliza uma versão do SO posterior à versão especificada na regra, o acesso aos recursos da empresa é bloqueado. Em seguida, é pedido ao utilizador para contactar o seu administrador de TI. Até a regra ser alterada para permitir a versão do SO, este dispositivo não pode aceder aos recursos da empresa.

## <a name="system-security"></a>Segurança do sistema

### <a name="password"></a>Palavra-passe

> [!NOTE]
> Após ser aplicada uma política de conformidade ou de configuração para um dispositivo iOS, será pedido aos utilizadores que definam um código de acesso a cada 15 minutos. Os utilizadores continuam a receber o pedido até que seja definido um código de acesso.

- **Pedir uma palavra-passe para desbloquear dispositivos móveis**: defina esta opção como **Sim** para pedir ao utilizador que introduza uma palavra-passe para poder aceder ao respetivo dispositivo. Os dispositivos iOS que utilizam uma palavra-passe são encriptados.
- **Palavras-passe simples**: defina esta opção como **Sim** para permitir que o utilizador crie uma palavra-passe como **1234** ou **1111**.
- **Comprimento mínimo da palavra-passe**: introduza o número mínimo de dígitos ou carateres que a palavra-passe tem de ter.
- **Tipo de palavra-passe necessária**: especifique se o utilizador tem de criar uma palavra-passe **Alfanumérica** ou **Numérica**.
- **Número de carateres não alfanuméricos na palavra-passe**: introduza o número mínimo de carateres especiais (&, #, %, !, etc.) que têm de ser incluídos na palavra-passe.

    Definir um número mais relevado exige que o utilizador crie uma palavra-passe mais complexa.

- **Máximo de minutos de inatividade antes de ser exigida a palavra-passe**: introduza o tempo de inatividade antes de o utilizador ter de reintroduzir a palavra-passe.
- **Expiração da palavra-passe (dias)**: selecione o número de dias antes de a palavra-passe expirar e ser preciso criar uma nova.
- **Número de palavras-passe anteriores cuja reutilização está bloqueada**: introduza o número de palavras-passe utilizadas anteriormente que não podem ser utilizadas.

<!--- ## Next steps

[How to monitor device compliance](device-compliance-monitor.md)--->
