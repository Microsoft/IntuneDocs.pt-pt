---
title: Criar uma política de conformidade de dispositivos Android no Microsoft Intune – Azure | Microsoft Docs
description: Criar ou configurar uma política de conformidade de dispositivos do Microsoft Intune para dispositivos Android. Opte por permitir dispositivos com jailbreak, defina o nível de ameaça aceitável, verifique o Google Play, introduza a versão do sistema operativo mínima e máxima, escolha os seus requisitos de palavra-passe e permita aplicações de sideload.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 05/17/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: e1258fe4-0b5c-4485-8bd1-152090df6345
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ed2dcda510c455be1ad532228bfbcbeb898d971a
ms.sourcegitcommit: b7789fd2f34528275c13a717699cf53a289ed04e
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/09/2018
ms.locfileid: "48891034"
---
# <a name="add-a-device-compliance-policy-for-android-devices-in-intune"></a>Adicionar uma política de conformidade de dispositivos Android no Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Uma política de conformidade de dispositivos do Intune para Android especifica as regras e definições que os dispositivos Android têm de cumprir para serem considerados como estando em conformidade. Pode utilizar estas políticas com acesso condicional para permitir ou bloquear o acesso a recursos da empresa. Também pode obter relatórios de dispositivos e agir relativamente a situações de não conformidade. Pode criar políticas de conformidade de dispositivos para cada plataforma no portal do Azure no Intune. Para saber mais sobre as políticas de conformidade, veja [Introdução à conformidade de dispositivos](device-compliance-get-started.md).

A seguinte tabela descreve como as definições não conformes são geridas quando uma política de conformidade é utilizada com uma política de acesso condicional.

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

**Remediado** = O sistema operativo do dispositivo impõe a conformidade. (Por exemplo, forçar o utilizador a definir um PIN.)

**Em Quarentena** = O sistema operativo do dispositivo não impõe a conformidade. (Por exemplo, os dispositivos Android não forçam o utilizador a encriptar o dispositivo.) Quando o dispositivo não é conforme, são efetuadas as seguintes ações:

- O dispositivo é bloqueado se uma política de acesso condicional se aplicar ao utilizador.
- O portal da empresa notifica o utilizador sobre eventuais problemas de conformidade.

## <a name="create-a-device-compliance-policy"></a>Criar uma política de conformidade de dispositivo

[!INCLUDE [new-device-compliance-policy](./includes/new-device-compliance-policy.md)]
5. Em **Plataforma**, selecione **Android**. Escolha **Configurar Definições**, aceda às definições **Estado de Funcionamento do Dispositivo**, **Propriedades do Dispositivo** e **Segurança do Sistema**. Quando terminar, selecione **OK** e **Criar**.

<!--- 4. Choose **Actions for noncompliance** to say what actions should happen when a device is determined as noncompliant based on the configured settings in this policy.
5. In the **Actions for noncompliance** pane, choose **Add** to create a new action.  The action parameters pane allows you to specify the action, email recipients that should receive the notification in addition to the user of the device, and the content of the notification that you want to send.
6. The message template option allows you to create several custom emails depending on when the action is set to take. For example, you can create a message for notifications that are sent for the first time and a different message for final warning before access is blocked. The custom messages that you create can be used for all your device compliance policy.
7. Specify the **Grace period** which determines when that action to take place.  For example, you may want to send a notification as soon as the device is evaluated as noncompliant, but allow some time before enforcing the conditional access policy to block access to company resources like SharePoint online.
8. Choose **Add** to finish creating the action.
9. You can create multiple actions and the sequence in which they should occur. Choose **OK** when you are finished creating all the actions.--->

<!---##  Compliance policy settings--->

## <a name="device-health"></a>Device health

- **Dispositivos com jailbreak**: se ativar esta definição, os dispositivos com jailbreak serão avaliados como não conformes.
- **Exigir que o dispositivo esteja ao Nível de Ameaça do Dispositivo ou abaixo do mesmo**: utilize esta definição para assumir a avaliação de riscos da solução Lookout MTP como uma condição de conformidade. Selecione o nível de ameaça máximo permitido:
  - **Protegido**: esta opção é a mais segura, uma vez que o dispositivo não pode ter qualquer ameaça. Se forem detetadas ameaças de qualquer nível no dispositivo, o mesmo será avaliado como não conforme.
  - **Baixo**: o dispositivo é avaliado como em conformidade se só estiverem presentes ameaças de nível baixo. Qualquer nível mais alto coloca o dispositivo num estado de não conforme.
  - **Médio**: o dispositivo será avaliado como estando em conformidade se as ameaças existentes forem de nível baixo ou médio. Se forem detetadas ameaças de nível alto no dispositivo, este será determinado como não conforme.
  - **Elevado**: esta opção é a menos segura e permite todos os níveis de ameaça. Poderá ser útil se utilizar esta solução apenas para fins de relatórios.
- **Os Serviços Google Play estão configurados**: solicite que a aplicação de Serviços do Google Play esteja instalada e ativada. Os serviços do Google Play permitem realizar atualizações de segurança, que são uma dependência de nível base de várias funcionalidades de segurança dos dispositivos Google certificados.
- **Fornecedor de segurança atualizado**: solicite que um fornecedor de segurança atualizado proteja um dispositivo contra vulnerabilidades conhecidas.
- **Análise de ameaças nas aplicações**: exija que a funcionalidade **Verificar Aplicações** do Android esteja ativada.

  > [!NOTE]
  > Na plataforma Android legada, esta funcionalidade é uma definição de conformidade. O Intune só consegue verificar se esta definição está ativada ao nível do dispositivo. Em dispositivos com perfis de trabalho do Android, esta definição encontra-se como uma definição de política de configuração. permitindo que os administradores ativem a definição para um dispositivo.

  Se a sua empresa utilizar perfis de trabalho do Android, poderá ativar a **Análise de ameaças nas aplicações** para os dispositivos inscritos. Estabeleça um perfil de dispositivo e solicite a definição de segurança do sistema. Para obter mais informações, veja [Definições de restrição de dispositivos de perfil de trabalho Android no Intune](device-restrictions-android-for-work.md).

- **Atestado de dispositivo SafetyNet**: introduza o nível de [Atestado de SafetyNet](https://developer.android.com/training/safetynet/attestation.html) que tem de ser cumprido. As opções são:
  - **Não configurado**
  - **Verificação de integridade básica**
  - **Verificação de integridade básica e de dispositivos certificados**

## <a name="device-property-settings"></a>Definições de propriedade do dispositivo

- **Versão do SO mínima**: quando um dispositivo não cumpre o requisito de versão mínima do SO, será comunicado como não estando em conformidade. É apresentada uma ligação com informações sobre como atualizar. O utilizador final pode optar por atualizar o dispositivo e, em seguida, obter acesso aos recursos da empresa.
- **Versão do SO máxima**: quando um dispositivo utiliza uma versão do SO posterior à versão especificada na regra, o acesso aos recursos da empresa é bloqueado. É pedido ao utilizador para contactar o administrador de TI. Até a regra ser alterada para permitir a versão do SO, este dispositivo não poderá aceder aos recursos da empresa.

## <a name="system-security-settings"></a>Definições de segurança do sistema

### <a name="password"></a>Palavra-passe

- **Exigir uma palavra-passe para desbloquear os dispositivos móveis**: **exige** que os utilizadores introduzam uma palavra-passe para poderem aceder aos dispositivos.
- **Comprimento mínimo da palavra-passe**: introduza o número mínimo de dígitos ou carateres que a palavra-passe do utilizador tem de ter.
- **Tipo de palavra-passe necessária**: selecione se uma palavra-passe deve ter apenas carateres numéricos ou se deve existir uma combinação de números e de outros carateres. Escolha entre:
  - **Dispositivo Predefinido**
  - **Biométrica de segurança baixa**
  - **Pelo menos numérica**
  - **Complexo numérico**: os números repetidos ou consecutivos (como "1111" ou "1234") não são permitidos.
  - **Pelo menos alfabética**
  - **Pelo menos alfanumérica**
  - **Pelo menos alfanumérica com símbolos**
- **Máximo de minutos de inatividade antes de ser exigida a palavra-passe**: introduza o tempo de inatividade antes de o utilizador ter de reintroduzir a palavra-passe.
- **Expiração da palavra-passe (dias)**: selecione o número de dias antes de a palavra-passe expirar e de o utilizador ter de criar uma nova.
- **Número de palavras-passe anteriores para impedir a reutilização**: introduza o número de palavras-passe recentes que não podem ser utilizadas. Utilize esta definição para impedir o utilizador final de criar palavras-passe utilizadas anteriormente.

### <a name="encryption"></a>Encriptação

- **Encriptação do armazenamento de dados num dispositivo** (Android 4.0 e superior ou KNOX 4.0 e superior): escolha **Exigir** a encriptação do armazenamento de dados nos dispositivos. Os dispositivos são encriptados quando seleciona a definição **Palavra-passe obrigatória para desbloquear os dispositivos móveis**.

### <a name="device-security"></a>Segurança do Dispositivo

- **Bloquear aplicações de origens desconhecidas**: opte por bloquear os dispositivos que tenham a opção “Segurança > Origens Desconhecidas” ativada (Android 4.0 – Android 7.x. Não suportada pelo Android 8.0 e posterior). Para aplicações de sideload, as origens desconhecidas têm de ser permitidas. Se não tiver aplicações Android de sideload, ative esta política de conformidade.

  > [!IMPORTANT]
  > As aplicações de sideload requerem a ativação da definição **Bloquear aplicações de origens desconhecidas**. Aplique esta política de conformidade apenas se não tiver aplicações Android de sideload nos dispositivos.

- **Integridade de tempo de execução de aplicações do portal da empresa**: verifica se a aplicação do Portal da Empresa tem o ambiente do tempo de execução predefinido instalado, se está assinada corretamente, se não se encontra no modo de depuração e se foi instalada a partir de uma origem conhecida.
- **Bloquear a depuração de USB no dispositivo** (Android 4.2 ou posterior): escolha impedir que os dispositivos utilizem a funcionalidade de depuração USB.
- **Nível de correção de segurança mínimo** (Android 6.0 ou posterior): selecione o nível de correção de segurança mais antigo que um dispositivo pode ter. Os dispositivos que não tenham, pelo menos, este nível de correção serão considerados como não conformes. A data tem de ser introduzida no formato `YYYY-MM-DD`.

## <a name="locations"></a>Localizações

Na sua política, escolha uma das localizações existentes. Ainda não tem uma localização? [Utilizar Localizações (barreira de rede) no Intune](use-network-locations.md) fornece algumas orientações.

1. Selecione a opção **Selecionar localizações**.
2. Na lista, verifique a sua localização e escolha **Selecionar**.
3. **Guarde** a política.
4. Selecione **Ações para não conformidade**. A ação predefinida marca imediatamente o dispositivo como não conforme. Esta ação aplica-se quando seleciona pelo menos uma localização e se o dispositivo não estiver ligado às localizações selecionadas.

  Pode alterar esta ação para atualizar a agenda quando o dispositivo for marcado como não conforme, tal como após um dia. Também pode configurar uma segunda ação que envia um e-mail para o utilizador quando o dispositivo deixa de estar em conformidade com as suas localizações.

## <a name="assign-user-groups"></a>Atribuir grupos de utilizadores

1. Escolha uma política configurada por si. As políticas existentes encontram-se em **Conformidade do dispositivo** > **Políticas**.
2. Escolha a política e, em seguida, **Atribuições**. Pode incluir ou excluir grupos de segurança do Azure Active Directory (AD).
3. Escolha **Grupos selecionados** para ver os grupos de segurança do Azure AD. Selecione os grupos de utilizadores aos quais pretende aplicar esta política e escolha **Guardar** para implementar a política aos utilizadores.

Aplicou a política aos utilizadores. Os dispositivos utilizados pelos utilizadores visados pela política são avaliados quanto à conformidade.

## <a name="next-steps"></a>Próximos passos
[Automatizar o e-mail e adicionar ações para dispositivos não conformes](actions-for-noncompliance.md)  
[Monitorizar as políticas de conformidade do Dispositivo do Intune](compliance-policy-monitor.md)
