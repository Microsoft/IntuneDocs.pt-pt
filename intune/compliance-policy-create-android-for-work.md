---
title: Criar uma política de conformidade do Android for Work no Microsoft Intune – Azure | Microsoft Docs
description: Crie ou configure uma política de conformidade de dispositivos do Microsoft Intune para dispositivos Android for Work. Opte por permitir dispositivos com jailbreak, defina o nível de ameaça aceitável, verifique o Google Play, introduza a versão do sistema operativo mínima e máxima, escolha os seus requisitos de palavra-passe e permita aplicações de sideload.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/16/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 9da89713-6306-4468-b211-57cfb4b51cc6
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: c1d438aa7416b1629af7ab2b899afa06720e2b49
ms.sourcegitcommit: 6a9830de768dd97a0e95b366fd5d2f93980cee05
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/10/2018
---
# <a name="add-a-device-compliance-policy-for-android-for-work-devices-in-intune"></a>Adicionar uma política de conformidade para dispositivos Android for Work no Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Uma política de conformidade de dispositivos do Intune para Android for Work especifica as regras e as definições que estes têm de cumprir para serem considerados como estando em conformidade. Pode utilizar estas políticas com acesso condicional para permitir ou bloquear o acesso a recursos da empresa. Também pode obter relatórios de dispositivos e agir relativamente a situações de não conformidade. Pode criar políticas de conformidade de dispositivos para plataformas diferentes no portal do Azure no Intune. Para saber mais sobre as políticas de conformidade, veja [Introdução à conformidade de dispositivos](device-compliance-get-started.md).

A seguinte tabela descreve como as definições não conformes são geridas quando uma política de conformidade é utilizada com uma política de acesso condicional.

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

**Em Quarentena** = O sistema operativo do dispositivo não impõe a conformidade. (Por exemplo, os dispositivos Android não forçam o utilizador a encriptar o dispositivo.) Quando o dispositivo não é conforme, são efetuadas as seguintes ações:

- Se uma política de acesso condicional se aplicar ao utilizador, o dispositivo é bloqueado.
- O portal da empresa notifica o utilizador sobre eventuais problemas de conformidade.

## <a name="create-a-device-compliance-policy"></a>Criar uma política de conformidade de dispositivo

[!INCLUDE [new-device-compliance-policy](./includes/new-device-compliance-policy.md)]
5. Em **Plataforma**, selecione **Android for Work**. Escolha **Configurar Definições**, aceda às definições **Estado de Funcionamento do Dispositivo**, **Propriedades do Dispositivo** e **Segurança do Sistema**. Quando terminar, selecione **OK** e **Criar**.

<!--- 4. Choose **Actions for noncompliance** to say what actions should happen when a device is determined as noncompliant with this policy.
5. In the **Actions for noncompliance** pane, choose **Add** to create a new action.  The action parameters pane allows you to specify the action, email recipients that should receive the notification in addition to the user of the device, and the content of the notification that you want to send.
6. The message template option allows you to create several custom emails depending on when the action is set to take. For example, you can create a message for notifications that are sent for the first time and a different message for final warning before access is blocked. The custom messages that you create can be used for all your device compliance policy.
7. Specify the **Grace period** which determines when that action to take place.  For example, you may want to send a notification as soon as the device is evaluated as noncompliant, but allow some time before enforcing the conditional access policy to block access to company resources like SharePoint online.
8. Choose **Add** to finish creating the action.
9. You can create multiple actions and the sequence in which they should occur. Choose **Ok** when you are finished creating all the actions.--->

## <a name="device-health"></a>Device health

- **Dispositivos com jailbreak**: se ativar esta definição, os dispositivos com jailbreak serão avaliados como não conformes.
- **Exigir que o dispositivo esteja ao Nível de Ameaça do Dispositivo ou abaixo do mesmo**: utilize esta definição para assumir a avaliação de riscos da solução Lookout MTP como uma condição de conformidade. Selecione o nível de ameaça máximo permitido:
  - **Protegido**: esta opção é a mais segura e significa que o dispositivo não pode ter qualquer ameaça. Se forem detetadas ameaças de qualquer nível no dispositivo, o mesmo será avaliado como não conforme.
  - **Baixo**: o dispositivo é avaliado como em conformidade se só estiverem presentes ameaças de nível baixo. Qualquer nível mais alto coloca o dispositivo num estado de não conforme.
  - **Médio**: o dispositivo é avaliado como conforme se só estiverem presentes ameaças de nível baixo ou médio. Se forem detetadas ameaças de nível alto no dispositivo, este será determinado como não conforme.
  - **Elevado**: esta opção é a menos segura e permite todos os níveis de ameaça. Poderá ser útil se utilizar esta solução apenas para fins de relatórios.
- **Os Serviços Google Play estão configurados**: solicite que a aplicação de Serviços do Google Play esteja instalada e ativada. Os serviços do Google Play permitem realizar atualizações de segurança, que são uma dependência de nível base de várias funcionalidades de segurança dos dispositivos Google certificados.
- **Fornecedor de segurança atualizado**: solicite que um fornecedor de segurança atualizado proteja um dispositivo contra vulnerabilidades conhecidas.
- **Atestado de dispositivo SafetyNet**: introduza o nível de [Atestado de SafetyNet](https://developer.android.com/training/safetynet/attestation.html) que tem de ser cumprido. As opções são:
  - **Não configurado**
  - **Verificação de integridade básica**
  - **Verificação de integridade básica e de dispositivos certificados**

#### <a name="threat-scan-on-apps"></a>Análise de ameaças nas aplicações

Em dispositivos com perfis de trabalho (Android for Work), a definição **Análise de ameaças nas aplicações** pode ser encontrada como uma definição de política de configuração. Os administradores podem ativar a definição para um dispositivo.

Se a sua empresa utilizar perfis de trabalho do Android, poderá ativar a **Análise de ameaças nas aplicações** para os dispositivos inscritos. Estabeleça um perfil de dispositivo e solicite a definição de segurança do sistema. Para obter mais informações, veja [Definições de restrição de dispositivos Android for Work no Intune](device-restrictions-android-for-work.md).

## <a name="device-property-settings"></a>Definições de propriedade do dispositivo

- **Versão do SO mínima**: quando um dispositivo não cumpre o requisito de versão mínima do SO, será comunicado como não estando em conformidade. É apresentada uma ligação com informações sobre como atualizar. O utilizador final pode optar por atualizar o dispositivo para, em seguida, poder aceder aos recursos da empresa.
- **Versão do SO máxima**: quando um dispositivo utiliza uma versão do SO posterior à versão especificada na regra, o acesso aos recursos da empresa é bloqueado. Além disso, é pedido ao utilizador para contactar o administrador de TI. Até a regra ser alterada para permitir a versão do SO, o dispositivo não poderá aceder aos recursos da empresa.

## <a name="system-security-settings"></a>Definições de segurança do sistema

### <a name="password"></a>Palavra-passe

- **Exigir uma palavra-passe para desbloquear os dispositivos móveis**: **exige** que os utilizadores introduzam uma palavra-passe para poderem aceder aos dispositivos.
- **Comprimento mínimo da palavra-passe**: introduza o número mínimo de dígitos ou carateres que a palavra-passe do utilizador tem de ter.
- **Tipo de palavra-passe necessária**: escolha se uma palavra-passe deve conter apenas carateres numéricos ou uma combinação de números e de outros carateres. Escolha entre:
  - **Dispositivo Predefinido**
  - **Biométrica de segurança baixa**
  - **Pelo menos numérica**
  - **Complexo numérico**
  - **Pelo menos alfabética**
  - **Pelo menos alfanumérica**
  - **Pelo menos alfanumérica com símbolos**
- **Máximo de minutos de inatividade antes de ser exigida a palavra-passe**: introduza o tempo de inatividade antes de o utilizador ter de reintroduzir a palavra-passe.
- **Expiração da palavra-passe (dias)**: selecione o número de dias antes de a palavra-passe expirar e ser preciso criar uma nova.
- **Número de palavras-passe anteriores para impedir a reutilização**: introduza o número de palavras-passe recentes que não podem ser utilizadas. Utilize esta definição para impedir o utilizador final de criar palavras-passe utilizadas anteriormente.

### <a name="encryption"></a>Encriptação

- **Exigir encriptação em dispositivos móveis**: uma vez que os dispositivos Android for Work impõem a encriptação, não necessita de configurar esta definição.

### <a name="device-security"></a>Segurança do Dispositivo

- **Bloquear aplicações de origens desconhecidas**: uma vez que os dispositivos Android for Work restringem sempre a instalação de origens desconhecidas, não necessita de configurar esta definição.
- **Integridade de tempo de execução de aplicações do portal da empresa**: verifica se a aplicação do Portal da Empresa tem o ambiente do tempo de execução predefinido instalado, se está assinada corretamente, se não se encontra no modo de depuração e se foi instalada a partir de uma origem conhecida.
- **Bloquear a depuração de USB no dispositivo**: uma vez que a depuração USB já se encontra desativada em dispositivos Android for Work, não tem de configurar esta definição.
- **Nível de correção de segurança mínimo**: selecione o nível de correção de segurança mais antigo que um dispositivo pode ter. Os dispositivos que não tenham, pelo menos, este nível de correção serão considerados como não conformes. A data tem de ser introduzida no formato `YYYY-MM-DD`.

## <a name="assign-user-groups"></a>Atribuir grupos de utilizadores

1. Escolha uma política configurada por si. As políticas existentes encontram-se em **Conformidade do dispositivo** > **Políticas**.
2. Escolha a política e, em seguida, **Atribuições**. Pode incluir ou excluir grupos de segurança do Azure Active Directory (AD).
3. Escolha **Grupos selecionados** para ver os grupos de segurança do Azure AD. Selecione os grupos de utilizadores aos quais pretende aplicar esta política e escolha **Guardar** para implementar a política aos utilizadores.

Aplicou a política aos utilizadores. Os dispositivos utilizados pelos utilizadores visados pela política são avaliados quanto à conformidade.

## <a name="next-steps"></a>Próximos passos
[Automatizar o e-mail e adicionar ações para dispositivos não conformes](actions-for-noncompliance.md)  
[Monitorizar as políticas de conformidade do Dispositivo do Intune](compliance-policy-monitor.md)
