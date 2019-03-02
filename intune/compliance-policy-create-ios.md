---
title: Criar política de conformidade de dispositivos iOS no Microsoft Intune – Azure | Microsoft Docs
description: Crie ou configure uma política de conformidade de dispositivos no Microsoft Intune para dispositivos iOS para introduzir uma conta de e-mail, verificar dispositivos com jailbreak, verificar a versão mínima e máxima do sistema operativo e definir restrições de palavra-passe, incluindo comprimento da palavra-passe e inatividade de dispositivos.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/14/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 3cfb8222-d05b-49e3-ae6f-36ce1a16c61d
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: da8b68fed8d411e14316744eec44857cd34803a4
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/02/2019
ms.locfileid: "57231048"
---
# <a name="add-a-device-compliance-policy-for-ios-devices-in-intune"></a>Adicionar uma política de conformidade de dispositivos para dispositivos iOS no Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Uma política de conformidade de dispositivos iOS no Intune determina as regras e definições que os dispositivos iOS têm de cumprir para estarem em conformidade. Quando utiliza políticas de conformidade de dispositivos com acesso condicional, pode permitir ou bloquear o acesso aos recursos da empresa. Também pode obter relatórios de dispositivos e agir relativamente a situações de não conformidade. Pode criar as políticas de conformidade de dispositivos para cada plataforma no portal do Azure no Intune. Para saber mais sobre as políticas de conformidade, veja [Introdução à conformidade de dispositivos](device-compliance-get-started.md).

A seguinte tabela descreve como as definições não conformes são geridas quando uma política de conformidade é utilizada com uma política de acesso condicional.

---------------------------

| **Definição de política** | **iOS 8.0 e posterior** |
| --- | --- |
| **Configuração do PIN ou da palavra-passe** | Corrigido |
| **Encriptação do dispositivo** | Corrigido (ao definir um PIN) |
| **Dispositivo desbloqueado por jailbreak ou obtenção de controlo de raiz** | Em quarentena (não é uma definição)
| **Perfil de e-mail** | Em quarentena |
|**Versão mínima do SO** | Em quarentena |
| **Versão máxima do SO** | Em quarentena |
| **Atestado do estado de funcionamento do Windows** | Não aplicável |

---------------------------

**Remediado** = O sistema operativo do dispositivo impõe a conformidade. (Por exemplo, forçar o utilizador a definir um PIN.)

**Em Quarentena** = O sistema operativo do dispositivo não impõe a conformidade. (Por exemplo, os dispositivos Android não forçam o utilizador a encriptar o dispositivo.) Quando o dispositivo não é conforme, são efetuadas as seguintes ações:

- O dispositivo é bloqueado se uma política de acesso condicional se aplicar ao utilizador.
- O portal da empresa notifica o utilizador sobre eventuais problemas de conformidade.

## <a name="create-a-device-compliance-policy"></a>Criar uma política de conformidade de dispositivo

[!INCLUDE [new-device-compliance-policy](./includes/new-device-compliance-policy.md)]
4. Em **Plataforma**, selecione **iOS**. 
5. Escolher **configurar as definições**e introduza o **E-Mail**, **estado de funcionamento do dispositivo**, **propriedades do dispositivo**, e **sistema Segurança** definições descritas neste tópico. Quando tiver terminado, selecione **OK** e **Criar**.

<!--- 4. Choose **Actions for noncompliance** to say what actions should happen when a device is determined as noncompliant with this policy.
5. In the **Actions for noncompliance** pane, choose **Add** to create a new action.  The action parameters pane allows you to specify the action, email recipients that should receive the notification in addition to the user of the device, and the content of the notification that you want to send.
7. The message template option allows you to create several custom emails depending on when the action is set to take. For example, you can create a message for notifications that are sent for the first time and a different message for final warning before access is blocked. The custom messages that you create can be used for all your device compliance policy.
7. Specify the **Grace period** which determines when that action to take place.  For example, you may want to send a notification as soon as the device is evaluated as noncompliant, but allow some time before enforcing the conditional access policy to block access to company resources like SharePoint online.
8. Choose **Add** to finish creating the action.
9. You can create multiple actions and the sequence in which they should occur. Choose **Ok** when you are finished creating all the actions.--->

## <a name="email"></a>Email

- **Exigir que os dispositivos móveis tenham um perfil de e-mail gerido**: Se definir esta opção para exigir, os dispositivos que não têm uma mensagem de e-mail, perfil gerido pelo Intune são considerados não conformes. Um dispositivo pode não ter um perfil de e-mail gerido quando não está corretamente direcionado ou se o utilizador tiver configurado manualmente a conta de e-mail no dispositivo.

  O dispositivo é considerado não conforme nas seguintes situações:
  - O perfil de e-mail é implementado para um grupo de utilizadores que não o grupo de utilizadores visado pela política de conformidade.
  - O utilizador já configurou uma conta de e-mail no dispositivo que corresponde ao perfil de e-mail do Intune implementado no dispositivo. O Intune não pode substituir o perfil aprovisionado pelo utilizador, pelo que não o consegue gerir. Para garantir a conformidade, o utilizador tem de remover as definições de e-mail existentes. Em seguida, o Intune pode instalar o perfil de e-mail gerido.

- **Selecione o perfil de e-mail que tem de ser gerido pelo Intune**: Se o **conta de E-Mail tem de ser gerenciada pelo Intune** definição está selecionada, escolha **selecione** para especificar o perfil de e-mail do Intune. O perfil de e-mail tem de estar presente no dispositivo.

Para obter informações sobre o perfil de e-mail, veja [Configurar o acesso a e-mail empresarial através de perfis de e-mail com o Microsoft Intune](email-settings-configure.md).

## <a name="device-health"></a>Device health

- **Os dispositivos com Jailbreak**: Se ativar esta definição, os dispositivos com jailbreak não estão em conformidade.
- **Exigir o dispositivo esteja ao nível ou abaixo do nível de ameaça do dispositivo** (iOS 8.0 e mais recente): Escolha o nível de ameaça máximo para marcar dispositivos como não conformes. Os dispositivos que excederem este nível de ameaça serão marcados como não conformes:
  - **Protegido**: Esta opção é a mais segura, uma vez que o dispositivo não pode ter qualquer ameaça. Se forem detetadas ameaças de qualquer nível no dispositivo, o mesmo será avaliado como não conforme.
  - **Baixa**: O dispositivo é avaliado como conforme se só estiverem presentes ameaças de nível baixo. Qualquer nível mais alto coloca o dispositivo num estado de não conforme.
  - **Médio**: O dispositivo é avaliado como conforme se as ameaças existentes no dispositivo forem de nível baixo ou médio. Se forem detetadas ameaças de nível alto no dispositivo, este será determinado como não conforme.
  - **Alta**: Esta opção é menos segura e permite todos os níveis de ameaça. Poderá ser útil se utilizar esta solução apenas para fins de relatórios.

## <a name="device-properties"></a>Propriedades do dispositivo

- **SO mínimo obrigatório**: Quando um dispositivo não cumpre o requisito de versão mínima do SO, será comunicado como não conforme. É apresentada uma hiperligação com informações sobre como atualizar. O utilizador pode optar por atualizar o dispositivo. Depois, pode aceder aos recursos da empresa.
- **Versão do SO máxima permitida**: Quando um dispositivo utiliza uma versão do SO posterior à versão especificada na regra, o acesso aos recursos da empresa é bloqueado. Em seguida, é pedido ao utilizador para contactar o seu administrador de TI. Até a regra ser alterada para permitir a versão do SO, este dispositivo não pode aceder aos recursos da empresa.
- **Versão de compilação de SO mínimo**: Quando a Apple publica atualizações de segurança, o número de compilação, normalmente, é atualizado, não a versão do SO. Utilize esta funcionalidade para inserir um número de compilação permitido mínimo no dispositivo. Esta verificação de conformidade suporta dispositivos com iOS 8.0 e mais recente. 
- **Versão de compilação do SO máximo**: Quando a Apple publica atualizações de segurança, o número de compilação, normalmente, é atualizado, não a versão do SO. Utilize esta funcionalidade para inserir um número de compilação permitido máximo no dispositivo. Esta verificação de conformidade suporta dispositivos com iOS 8.0 e mais recente.

## <a name="system-security"></a>Segurança do sistema

### <a name="password"></a>Palavra-passe

> [!NOTE]
> Após ser aplicada uma política de conformidade ou de configuração para um dispositivo iOS, será pedido aos utilizadores que definam um código de acesso a cada 15 minutos. Os utilizadores continuam a receber o pedido até que seja definido um código de acesso.

- **Exigir uma palavra-passe para desbloquear dispositivos móveis**: **Exigir** que os utilizadores introduzam uma palavra-passe antes de poderem aceder ao respetivo dispositivo. Os dispositivos iOS que utilizam uma palavra-passe são encriptados.
- **Palavras-passe simples**: Defina como **bloco** para que os utilizadores não é possível criar palavras-passe simples, tal como **1234** ou **1111**. Defina como **Não configurado** para permitir aos utilizadores criar palavras-passe como **1234** ou **1111**.
- **Comprimento mínimo da palavra-passe**: Introduza o número mínimo de dígitos ou carateres que a palavra-passe tem de ter.
- **Tipo de palavra-passe obrigatório**: Escolha se uma palavra-passe deve ter apenas **numérico** carateres, ou se deve existir uma combinação de números e outros carateres (**alfanumérico**).
- **Número de carateres não alfanuméricos na palavra-passe**: Introduza o número mínimo de carateres especiais (&, #, %,!, e assim por diante) que têm de ser incluído na palavra-passe.

    Definir um número mais relevado exige que o utilizador crie uma palavra-passe mais complexa.

- **Máximo de minutos de inatividade antes da palavra-passe é necessária**: Introduza o tempo de inatividade antes do utilizador ter de reintroduzir a palavra-passe.
- **Expiração de palavra-passe (dias)**: Selecione o número de dias antes da palavra-passe expirar e ser necessário criar um novo.
- **Número de palavras-passe anteriores cuja reutilização está**: Introduza o número de palavras-passe utilizadas anteriormente que não pode ser utilizado.

### <a name="restricted-applications"></a>Aplicações restritas 
Pode restringir aplicações ao adicionar os respetivos IDs do pacote à política. Em seguida, se um dispositivo tiver a aplicação instalada, o dispositivo será marcado como não conforme. 
- **Nome da aplicação**: Introduza um nome amigável para ajudar a identificar o ID de pacote. 
- **ID do pacote de aplicação**: Introduza o identificador do pacote exclusivo atribuído pelo fornecedor da aplicação. Para localizar o ID do pacote, veja [How to find the bundle ID for an iOS app](https://support.microsoft.com/help/4294074/how-to-find-the-bundle-id-for-an-ios-app) (Como localizar o ID do pacote de uma aplicação iOS).  

## <a name="assign-user-groups"></a>Atribuir grupos de utilizadores

1. Escolha uma política configurada por si. As políticas existentes encontram-se em **Conformidade do dispositivo** > **Políticas**.
2. Escolha a política e, em seguida, **Atribuições**. Pode incluir ou excluir grupos de segurança do Azure Active Directory (AD).
3. Escolha **Grupos selecionados** para ver os grupos de segurança do Azure AD. Selecione os grupos de utilizadores aos quais pretende aplicar esta política e escolha **Guardar** para implementar a política aos utilizadores.

Aplicou a política aos utilizadores. Os dispositivos utilizados pelos utilizadores visados pela política são avaliados quanto à conformidade.

## <a name="next-steps"></a>Passos Seguintes
[Automatizar o e-mail e adicionar ações para dispositivos não conformes](actions-for-noncompliance.md)  
[Monitorizar as políticas de conformidade do Dispositivo do Intune](compliance-policy-monitor.md)
