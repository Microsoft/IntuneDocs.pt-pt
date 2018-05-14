---
title: Criar uma política de conformidade de dispositivos Windows no Microsoft Intune – Azure | Microsoft Docs
description: Crie ou configure uma política de conformidade de dispositivos do Microsoft Intune para o Windows Phone 8.1, Windows 8.1 e posterior e Windows 10 e dispositivos posteriores. Verifique a conformidade do sistema operativo mínimo e máximo, defina as restrições e o comprimento de palavras-passe, exija o bitlocker, defina o nível de ameaça aceitável e ative a encriptação no armazenamento de dados, incluindo o Surface Hub e o Windows Holographic para Empresas.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/26/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 64df804bf2f882991cccd3f77014369cd86b69a8
ms.sourcegitcommit: 4c06fa8e9932575e546ef2e880d96e96a0618673
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/03/2018
---
# <a name="add-a-device-compliance-policy-for-windows-devices-in-intune"></a>Adicionar uma política de conformidade para dispositivos Windows no Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Uma política de conformidade de dispositivos do Intune para Windows especifica as regras e definições que os dispositivos Windows têm de cumprir para serem considerados como estando em conformidade. Pode utilizar estas políticas com acesso condicional para permitir ou bloquear o acesso a recursos da empresa. Também pode obter relatórios de dispositivos e agir relativamente a situações de não conformidade. Pode criar políticas de conformidade de dispositivos para cada plataforma no portal do Azure no Intune. Para saber mais sobre as políticas de conformidade, veja [Introdução à conformidade de dispositivos](device-compliance-get-started.md).

A seguinte tabela descreve como as definições não conformes são geridas quando uma política de conformidade é utilizada com uma política de acesso condicional.

---------------------------

| **Definição de política** | **Windows 8.1 e posterior** | **Windows Phone 8.1 e posterior** |
|----| ----| --- |
| **Configuração do PIN ou da palavra-passe** | Corrigido | Corrigido |   
| **Encriptação do dispositivo** | Não aplicável | Corrigido |   
| **Dispositivo desbloqueado por jailbreak ou obtenção de controlo de raiz** | Não aplicável | Não aplicável |  
| **Perfil de e-mail** | Não aplicável | Não aplicável |   
| **Versão mínima do SO** | Em quarentena | Em quarentena |   
| **Versão máxima do SO** | Em quarentena | Em quarentena |   
| **Atestado do estado de funcionamento do Windows** | Em Quarentena: Windows 10 e Windows 10 Mobile|Não aplicável: Windows 8.1 |

-------------------------------

**Remediado** = O sistema operativo do dispositivo impõe a conformidade. (Por exemplo, forçar o utilizador a definir um PIN.)

**Em Quarentena** = O sistema operativo do dispositivo não impõe a conformidade. (Por exemplo, os dispositivos Android não forçam o utilizador a encriptar o dispositivo.) Quando o dispositivo não é conforme, são efetuadas as seguintes ações:

- O dispositivo é bloqueado se uma política de acesso condicional se aplicar ao utilizador.
- O portal da empresa notifica o utilizador sobre eventuais problemas de conformidade.

## <a name="create-a-device-compliance-policy"></a>Criar uma política de conformidade de dispositivo

[!INCLUDE [new-device-compliance-policy](./includes/new-device-compliance-policy.md)]
5. Em **Plataforma**, selecione **Windows Phone 8.1**, **Windows 8.1 e posterior** ou **Windows 10 e posterior**.
6. Escolha **Configurar Definições**, aceda às definições **Estado de Funcionamento do Dispositivo**, **Propriedades do Dispositivo** e **Segurança do Sistema**. Quando tiver terminado, selecione **OK** e **Criar**.

<!--- 4. Choose **Actions for noncompliance** to say what actions should happen when a device is determined as noncompliant with this policy.
5. In the **Actions for noncompliance** pane, choose **Add** to create a new action.  The action parameters pane allows you to specify the action, email recipients that should receive the notification in addition to the user of the device, and the content of the notification that you want to send.
6. The message template option allows you to create several custom emails depending on when the action is set to take. For example, you can create a message for notifications that are sent for the first time and a different message for final warning before access is blocked. The custom messages that you create can be used for all your device compliance policy.
7. Specify the **Grace period** which determines when that action to take place.  For example, you may want to send a notification as soon as the device is evaluated as noncompliant, but allow some time before enforcing the conditional access policy to block access to company resources like SharePoint online.
8. Choose **Add** to finish creating the action.
9. You can create multiple actions and the sequence in which they should occur. Choose **Ok** when you are finished creating all the actions.--->

## <a name="windows-81-devices-policy-settings"></a>Definições de política de dispositivos Windows 8.1

Estas definições de política aplicam-se a dispositivos que executam as seguintes plataformas:

- Windows Phone 8.1
- Windows 8.1 e posterior

### <a name="device-properties"></a>Propriedades do dispositivo

- **SO mínimo necessário**: quando um dispositivo não cumpre o requisito de versão mínima do SO, será comunicado como não conforme. É apresentada uma ligação com informações sobre como atualizar. O utilizador final pode optar por atualizar o dispositivo e, em seguida, obter acesso aos recursos da empresa.
- **Versão do SO máxima permitida**: quando um dispositivo utiliza uma versão do SO posterior à versão especificada na regra, o acesso aos recursos da empresa é bloqueado. É pedido ao utilizador para contactar o administrador de TI. Até a regra ser alterada para permitir a versão do SO, este dispositivo não poderá aceder aos recursos da empresa.

Os PCs Windows 8.1 devolvem a versão **3**. Se a regra de versão de SO estiver definida como Windows 8.1 para o Windows, o dispositivo é comunicado como não conforme, mesmo que tenha o sistema operativo Windows 8.1.

### <a name="system-security"></a>Segurança do sistema

#### <a name="password"></a>Palavra-passe

- **Exigir uma palavra-passe para desbloquear os dispositivos móveis**: **exige** que os utilizadores introduzam uma palavra-passe para poderem aceder aos dispositivos.
- **Palavras-passe simples**: defina como **Bloquear** para que os utilizadores não possam criar palavras-passe simples, como **1234** ou **1111**. Defina como **Não configurado** para permitir aos utilizadores criar palavras-passe como **1234** ou **1111**.
- **Comprimento mínimo da palavra-passe**: introduza o número mínimo de dígitos ou carateres que a palavra-passe tem de ter.

  Para dispositivos que executam o Windows e são acedidos com uma conta Microsoft, a política de conformidade não consegue avaliar corretamente:
  - Se o comprimento mínimo da palavra-passe é superior a oito carateres
  - Ou, se o número mínimo de conjuntos de carateres é superior a dois

- **Tipo de palavra-passe**: escolha se uma palavra-passe deve ter apenas carateres **Numéricos** ou se deve existir uma combinação de números e de outros carateres (**Alfanuméricos**).
  
  - **Número de carateres não alfanuméricos na palavra-passe**: se o **Tipo obrigatório de palavra-passe** estiver definido como **Alfanumérico**, esta definição especificará o número mínimo de conjuntos de carateres que a palavra-passe tem de conter. Os quatro conjuntos de carateres são:
    - Letras minúsculas
    - Letras maiúsculas
    - Símbolos
    - Números

    Definir um número mais relevado exige que o utilizador crie uma palavra-passe mais complexa. Nos dispositivos com o Windows e cujo acesso é feito com uma conta Microsoft, a política de conformidade não avalia corretamente se o comprimento mínimo da palavra-passe é superior a oito carateres ou se o número mínimo de conjuntos de carateres é superior a dois.

- **Máximo de minutos de inatividade antes de ser exigida a palavra-passe**: introduza o tempo de inatividade antes de o utilizador ter de reintroduzir a palavra-passe.
- **Expiração da palavra-passe (dias)**: selecione o número de dias antes de a palavra-passe expirar e ser preciso criar uma nova.
- **Número de palavras-passe anteriores para impedir a reutilização**: introduza o número de palavras-passe utilizadas anteriormente que não podem ser utilizadas.

#### <a name="encryption"></a>Encriptação

- **Encriptação obrigatória no dispositivo móvel**: **exija** que o dispositivo seja encriptado para ligar a recursos de armazenamento de dados.

## <a name="windows-10-and-later-policy-settings"></a>Definições de política do Windows 10 e posterior

### <a name="device-health"></a>Device health

- **Exigir o BitLocker**: se o Bitlocker estiver ativado, o dispositivo será capaz de proteger os dados que são armazenados na unidade contra acessos não autorizados, quando o sistema é desligado ou entra em hibernação. A Encriptação de Unidade BitLocker do Windows encripta todos os dados armazenados no volume do sistema operativo Windows. O BitLocker utiliza o TPM para ajudar a proteger o sistema operativo Windows e os dados de utilizador. Também ajuda a garantir que os computadores não são adulterados, mesmo que não estejam a ser vigiados, sejam roubados ou se percam. Se os computadores estiverem equipados com um TPM compatível, o BitLocker utiliza o TPM para bloquear as chaves de encriptação que protegem os dados. Como resultado, as chaves não podem ser acedidas até o TPM ter verificado o estado dos computadores.
- **Exigir que o Arranque Seguro seja ativado no dispositivo:** se o Arranque Seguro estiver ativado, o sistema será forçado a fazer o arranque para um estado de fábrica fidedigno. Além disso, com o Arranque Seguro ativado, os componentes do núcleo utilizados para arrancar o computador têm de ter assinaturas criptográficas corretas e que sejam consideradas fidedignas pela organização que fabricou o dispositivo. O firmware UEFI verifica a assinatura antes de permitir que o computador seja iniciado. Se um ficheiro tiver sido adulterado, danificando a respetiva assinatura, o sistema não arrancará.
- **Exigir a integridade do código:** a integridade do código é uma funcionalidade que valida a integridade de um ficheiro de controlador ou de sistema sempre que é carregado para a memória. A integridade do código deteta se um ficheiro de controlador ou de sistema não assinado está a ser carregado para o kernel. Também deteta se um ficheiro de sistema foi modificado por software malicioso que está a ser executado por uma conta de utilizador com privilégios administrativos.
- **Exigir que o dispositivo esteja ao Nível de Ameaça do Dispositivo ou abaixo do mesmo**: utilize esta definição para assumir a avaliação de riscos dos serviços de defesa contra ameaças como uma condição para conformidade. Selecione o nível de ameaça máximo permitido:
  - **Protegido**: esta opção é a mais segura, uma vez que o dispositivo não pode ter qualquer ameaça. Se forem detetadas ameaças de qualquer nível no dispositivo, o mesmo será avaliado como não conforme.
  - **Baixo**: o dispositivo é avaliado como em conformidade se só estiverem presentes ameaças de nível baixo. Qualquer nível mais alto coloca o dispositivo num estado de não conforme.
  - **Médio**: o dispositivo será avaliado como estando em conformidade se as ameaças existentes forem de nível baixo ou médio. Se forem detetadas ameaças de nível alto no dispositivo, este será determinado como não conforme.
  - **Elevado**: esta opção é a menos segura e permite todos os níveis de ameaça. Poderá ser útil se utilizar esta solução apenas para fins de relatórios.

Para obter mais informações sobre como funciona o serviço HAS, veja [Health Attestation CSP](https://docs.microsoft.com/windows/client-management/mdm/healthattestation-csp) (CSP de Atestado de Estado de Funcionamento).

### <a name="device-properties"></a>Propriedades do dispositivo

- **Versão mínima do SO**: introduza a versão mínima permitida com o formato de número major.minor.build.revision. O número build.revision tem de corresponder à versão devolvida pelo comando `ver` ou `winver`.

  Quando um dispositivo tem uma versão anterior à versão de SO especificada, é comunicado como não conforme. É apresentada uma ligação com informações sobre como atualizar. O utilizador final pode optar por atualizar o dispositivo para poder aceder aos recursos da empresa.

- **Versão máxima do SO**: introduza a versão máxima permitida com o formato de número major.minor.build.revision. O número build.revision tem de corresponder à versão devolvida pelo comando `ver` ou `winver`.

  Quando um dispositivo está a utilizar uma versão do SO posterior à especificada na regra, o acesso aos recursos da empresa é bloqueado e é pedido ao utilizador que contacte o administrador de TI. Até a regra ser alterada para permitir a versão do SO, este dispositivo não pode ser utilizado no acesso aos recursos da empresa.

- **SO mínimo obrigatório para dispositivos móveis**: introduza a versão mínima permitida com o formato de número major.minor.build.

  Quando um dispositivo tem uma versão anterior à versão de SO especificada, é comunicado como não conforme. É apresentada uma ligação com informações sobre como atualizar. O utilizador final pode optar por atualizar o dispositivo para poder aceder aos recursos da empresa.

- **SO máximo obrigatório para dispositivos móveis**: introduza a versão máxima permitida com o formato de número major.minor.build.

  Quando um dispositivo está a utilizar uma versão do SO posterior à especificada na regra, o acesso aos recursos da empresa é bloqueado e é pedido ao utilizador que contacte o administrador de TI. Até a regra ser alterada para permitir a versão do SO, este dispositivo não pode ser utilizado no acesso aos recursos da empresa.

- **Compilações válidas do sistema operativo**: introduza um intervalo para as versões de sistemas operativos aceitáveis, incluindo um mínimo e máximo. Também pode **Exportar** uma lista de ficheiros de valores separados por vírgulas (CSV) destes números de compilação de SO aceitáveis.

### <a name="system-security-settings"></a>Definições de segurança do sistema

#### <a name="password"></a>Palavra-passe

- **Exigir uma palavra-passe para desbloquear os dispositivos móveis**: **exige** que os utilizadores introduzam uma palavra-passe para poderem aceder aos dispositivos.
- **Palavras-passe simples**: defina como **Bloquear** para que os utilizadores não possam criar palavras-passe simples, como **1234** ou **1111**. Defina como **Não configurado** para permitir aos utilizadores criar palavras-passe como **1234** ou **1111**.
- **Tipo de palavra-passe**: escolha se uma palavra-passe deve ter apenas carateres **Numéricos** ou se deve existir uma combinação de números e de outros carateres (**Alfanuméricos**).

  - **Número de carateres não alfanuméricos na palavra-passe**: se o **Tipo obrigatório de palavra-passe** estiver definido como **Alfanumérico**, esta definição especificará o número mínimo de conjuntos de carateres que a palavra-passe tem de conter. Os quatro conjuntos de carateres são:
    - Letras minúsculas
    - Letras maiúsculas
    - Símbolos
    - Números

    Definir um número mais relevado exige que o utilizador crie uma palavra-passe mais complexa.

- **Comprimento mínimo da palavra-passe**: introduza o número mínimo de dígitos ou carateres que a palavra-passe tem de ter.
- **Máximo de minutos de inatividade antes de ser exigida a palavra-passe**: introduza o tempo de inatividade antes de o utilizador ter de reintroduzir a palavra-passe.
- **Expiração da palavra-passe (dias)**: selecione o número de dias antes de a palavra-passe expirar e ser preciso criar uma nova.
- **Número de palavras-passe anteriores para impedir a reutilização**: introduza o número de palavras-passe utilizadas anteriormente que não podem ser utilizadas.
- **Exigir palavra-passe quando o dispositivo regressa do estado de inatividade (Móvel e Holographic)**: force os utilizadores a introduzir a palavra-passe sempre que o dispositivo regressar de um estado inativo.

### <a name="encryption"></a>Encriptação

- **Encriptação do armazenamento de dados num dispositivo**: escolha **Exigir** a encriptação do armazenamento de dados nos dispositivos.

## <a name="windows-holographic-for-business"></a>Windows Holographic for Business

O Windows Holographic for Business utiliza a plataforma **Windows 10 e posterior**. O Windows Holographic for Business suporta a seguinte definição:

- **Segurança do Sistema** > **Encriptação** > **Encriptação do armazenamento de dados no dispositivo**.

Para verificar a encriptação de dispositivos no Microsoft HoloLens, veja [Verify device encryption (Verificar a encriptação de dispositivos)](https://docs.microsoft.com/hololens/hololens-encryption#verify-device-encryption).

## <a name="surface-hub"></a>Surface Hub
O Surface Hub utiliza a plataforma **Windows 10 e posterior**. Os Surface Hubs são suportados para o acesso condicional e a conformidade. Para ativar estas funcionalidades nos Surface Hubs, recomendamos que [ative a inscrição automática de dispositivos Windows 10](windows-enroll.md) no Intune (também requer o Azure Active Directory (AAD)) e direcione os dispositivos Surface Hub como grupos de dispositivos. Os Surface Hubs têm de ser associados ao Azure Active Directory para que a compatibilidade e o acesso condicional funcionem.

Veja [configurar a inscrição para dispositivos Windows](windows-enroll.md) para obter orientações.

## <a name="assign-user-or-device-groups"></a>Atribuir grupos de utilizadores ou dispositivos

1. Escolha uma política configurada por si. As políticas existentes encontram-se em **Conformidade do dispositivo** > **Políticas**.
2. Escolha a política e, em seguida, **Atribuições**. Pode incluir ou excluir grupos de segurança do Azure AD.
3. Escolha **Grupos selecionados** para ver os grupos de segurança do Azure AD. Selecione os grupos de utilizadores ou de dispositivos aos quais pretende aplicar esta política e escolha **Guardar** para implementar a política.

A política foi aplicada. Os dispositivos utilizados pelos utilizadores visados pela política são avaliados quanto à conformidade.

## <a name="next-steps"></a>Próximos passos
[Automatizar o e-mail e adicionar ações para dispositivos não conformes](actions-for-noncompliance.md)  
[Monitorizar as políticas de conformidade do Dispositivo do Intune](compliance-policy-monitor.md)
