---
title: "Criar uma política de conformidade de dispositivos Windows no Microsoft Intune"
titleSuffix: 
description: "Crie uma política de conformidade de dispositivos do Microsoft Intune para dispositivos Windows, para que possa especificar os requisitos que um dispositivo tem de cumprir para estar em conformidade."
keywords: 
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 32af54e3e753e7ded3c86d9d44b793da7fe2e9c0
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/08/2018
---
# <a name="how-to-create-a-device-compliance-policy-for-windows-devices-in-intune"></a>Como criar uma política de conformidade para dispositivos Windows no Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Uma política de conformidade de dispositivos do Intune para Windows especifica as regras e definições que os dispositivos Windows têm de cumprir para serem considerados como estando em conformidade. Pode utilizar estas políticas com acesso condicional para permitir ou bloquear o acesso aos recursos da empresa, tal como pode obter relatórios de dispositivos e agir relativamente a situações de não conformidade. Pode criar políticas de conformidade de dispositivos para cada plataforma no portal do Azure no Intune. Para saber mais sobre políticas de conformidade e os pré-requisitos que tem de cumprir antes de criar uma política de conformidade, veja [Introdução à conformidade do dispositivo](device-compliance-get-started.md).

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

## <a name="create-a-compliance-policy-in-the-azure-portal"></a>Criar uma política de conformidade no portal do Azure

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços** > **Intune**. O Intune encontra-se na secção **Monitorização + Gestão**.
1. No painel **Intune**, selecione **Conformidade do dispositivo**. Em **Gerir**, selecione **Políticas** e, em seguida, **Criar política**.
2. Escreva um nome, uma descrição e escolha a plataforma à qual quer que esta política se aplique.
3. Selecione **Configurar Definições** para especificar aqui as definições de **Segurança do Sistema**, **Estado de funcionamento do Dispositivo** e **Propriedades do Dispositivo**. Quando tiver terminado, escolha **OK**.

<!--- 4. Choose **Actions for noncompliance** to say what actions should happen when a device is determined as noncompliant with this policy.
5. In the **Actions for noncompliance** pane, choose **Add** to create a new action.  The action parameters pane allows you to specify the action, email recipients that should receive the notification in addition to the user of the device, and the content of the notification that you want to send.
6. The message template option allows you to create several custom emails depending on when the action is set to take. For example, you can create a message for notifications that are sent for the first time and a different message for final warning before access is blocked. The custom messages that you create can be used for all your device compliance policy.
7. Specify the **Grace period** which determines when that action to take place.  For example, you may want to send a notification as soon as the device is evaluated as noncompliant, but allow some time before enforcing the conditional access policy to block access to company resources like SharePoint online.
8. Choose **Add** to finish creating the action.
9. You can create multiple actions and the sequence in which they should occur. Choose **Ok** when you are finished creating all the actions.--->

## <a name="assign-user-groups"></a>Atribuir grupos de utilizadores

Para atribuir uma política de conformidade a utilizadores, escolha uma política que tenha configurado. As políticas existentes encontram-se no painel **Conformidade do dispositivo – Políticas**.

1. Escolha a política que quer atribuir aos utilizadores e, em seguida, **Atribuições**. Esta ação abre o painel onde pode selecionar **Grupos de segurança do Azure Active Directory** e atribuí-los à política.
2. Selecione **Grupos selecionados** para abrir o painel que apresenta os grupos de segurança do Azure AD.  Selecionar **Guardar** implementa a política para os utilizadores.

Aplicou a política aos utilizadores. Os dispositivos utilizados pelos utilizadores visados pela política serão avaliados quanto à conformidade.

<!---## Compliance policy settings--->

## <a name="system-security-settings"></a>Definições de segurança do sistema

### <a name="password"></a>Palavra-passe

- **Palavra-passe obrigatória para desbloquear dispositivos móveis:** defina esta opção como **Sim** para exigir que os utilizadores introduzam uma palavra-passe para que possam aceder ao respetivo dispositivo.
- **Permitir palavras-passe simples:** defina esta opção como **Sim** para permitir que os utilizadores criem palavras-passe simples, tais como "**1234**" ou "**1111**".
- **Comprimento mínimo da palavra-passe:** especifique o número mínimo de dígitos ou carateres que a palavra-passe do utilizador tem de ter.
- **Solicitar tipo de palavra-passe:** especifique se os utilizadores têm de criar uma palavra-passe **Alfanumérica**, ou **Numérica**.

Nos dispositivos com o Windows e cujo acesso é feito com uma conta Microsoft, a política de conformidade não avalia corretamente se o comprimento mínimo da palavra-passe é superior a oito carateres ou se o número mínimo de conjuntos de carateres é superior a dois.

- **Número mínimo de conjuntos de carateres:** se o **Tipo obrigatório de palavra-passe** estiver definido como **Alfanumérico**, esta definição especificará o número mínimo de conjuntos de carateres que a palavra-passe tem de conter. Os quatro conjuntos de carateres são:
  - Letras minúsculas
  - Letras maiúsculas
  - Símbolos
  - Números

A definição de um número mais alto nesta definição obrigará os utilizadores a criarem palavras-passe mais complexas. Nos dispositivos com o Windows e cujo acesso é feito com uma conta Microsoft, a política de conformidade não avalia corretamente se o comprimento mínimo da palavra-passe é superior a oito carateres ou se o número mínimo de conjuntos de carateres é superior a dois.

- **Minutos de inatividade antes de a palavra-passe ser exigida:** especifica o tempo de inatividade antes de o utilizador ter de reintroduzir a palavra-passe.
- **Expiração da palavra-passe (dias)**: selecione o número de dias antes de a palavra-passe do utilizador expirar e ser necessário criar uma nova.
- **Memorizar histórico de palavras-passe:** utilize esta definição juntamente com **Impedir a reutilização de palavras-passe anteriores** para impedir o utilizador de criar palavras-passe utilizadas anteriormente.
- **Impedir a reutilização de palavras-passe anteriores:** se a opção **Memorizar histórico de palavras-passe** estiver selecionada, especifique o número de palavras-passe utilizadas anteriormente que não podem ser reutilizadas.
- **Exigir uma palavra-passe quando o dispositivo regressa de um estado inativo:** esta definição deve ser utilizada em conjunto com a definição **Minutos de inatividade antes de a palavra-passe ser exigida**. Será pedido aos utilizadores finais que introduzam uma palavra-passe para aceder a dispositivos que tenham estado inativos durante o período de tempo especificado na definição **Minutos de inatividade antes de a palavra-passe ser exigida**.

**Esta definição só se aplica a dispositivos Windows 10 Mobile.**

### <a name="encryption"></a>Encriptação

- **Exigir encriptação no dispositivo móvel:** defina esta opção como **Sim** para exigir que os dispositivos sejam encriptados para ligar aos recursos.



## <a name="device-health-settings"></a>Definições de estado de funcionamento do dispositivo

- **Exigir que os dispositivos sejam comunicados como estando em bom estado de funcionamento:** pode definir uma regra para exigir que os dispositivos **Windows 10 Mobile** sejam comunicados como estando em bom estado de funcionamento nas Políticas de Conformidade novas ou existentes. Se esta definição estiver ativada, os dispositivos com o Windows 10 serão avaliados através do Serviço de Atestado de Estado de Funcionamento (HAS) quanto aos seguintes pontos de dados:
  - **BitLocker está ativado:** se o BitLocker estiver ativado, o dispositivo é capaz de proteger os dados que são armazenados na unidade contra acesso não autorizado, quando o sistema é desligado ou entra em hibernação. A Encriptação de Unidade BitLocker do Windows encripta todos os dados armazenados no volume do sistema operativo Windows. O BitLocker utiliza o TPM para ajudar a proteger o sistema operativo Windows e os dados de utilizador e ajuda a garantir que os computadores não são adulterados, mesmo que não estejam a ser vigiados, sejam roubados ou se percam. Se os computadores estiverem equipados com um TPM compatível, o BitLocker utiliza o TPM para bloquear as chaves de encriptação que protegem os dados. Como resultado, as chaves não podem ser acedidas até o TPM ter verificado o estado do computador
  - **A integridade do código está ativada:** a integridade do código é uma funcionalidade que valida a integridade de um ficheiro de controlador ou de sistema sempre que é carregado para a memória. A integridade do código deteta se está a ser carregado um ficheiro de controlador ou de sistema não assinado para o kernel ou se um ficheiro de sistema foi modificado por software malicioso que está a ser executado por uma conta de utilizador com privilégios administrativos.
  - **O Arranque Seguro está ativado:** se o Arranque Seguro estiver ativado, o sistema é forçado a fazer o arranque para um estado de fábrica fidedigno. Além disso, com o Arranque Seguro ativado, os componentes do núcleo utilizados para arrancar o computador têm de ter assinaturas criptográficas corretas e que sejam consideradas fidedignas pela organização que fabricou o dispositivo. O firmware UEFI verifica isto antes de permitir que o computador seja iniciado. Se um ficheiro tiver sido adulterado, danificando a respetiva assinatura, o sistema não arrancará.

Para obter informações sobre como funciona o serviço HAS, veja [Health Attestation CSP (CSP de Atestado de Estado de Funcionamento)](https://msdn.microsoft.com/library/dn934876.aspx).

## <a name="device-property-settings"></a>Definições de propriedade do dispositivo

- **SO mínimo necessário:** quando um dispositivo não cumpre o requisito de versão mínima do SO, será reportado como não conforme. É apresentada uma ligação com informações sobre como atualizar. O utilizador final pode optar por atualizar o dispositivo para poder aceder aos recursos da empresa.
- **Versão do SO máxima permitida:** quando um dispositivo utiliza uma versão do SO posterior à especificada na regra, o acesso aos recursos da empresa é bloqueado e é pedido ao utilizador que contacte o administrador de TI. Até a regra ser alterada para permitir a versão do SO, este dispositivo não pode ser utilizado no acesso aos recursos da empresa.

<!---## Compliance policy settings for Windows PCs--->

## <a name="system-security-settings"></a>Definições de segurança do sistema

### <a name="password"></a>Palavra-passe

- **Comprimento mínimo da palavra-passe:** - suportada no Windows 8.1.

Especifique o número mínimo de dígitos ou carateres que a palavra-passe do utilizador tem de ter.

Nos dispositivos acedidos com uma Conta Microsoft, a política de conformidade não avalia corretamente se o **Comprimento mínimo da palavra-passe** é superior a oito carateres ou se o **Número mínimo de conjuntos de carateres** é superior a dois carateres.

- **Tipo obrigatório de palavra-passe:** suportado no Windows RT, Windows RT 8.1 e Windows 8.1

Especifique se os utilizadores têm de criar uma palavra-passe **Alfanumérica** ou **Numérica**.

- **Número mínimo de conjuntos de carateres:** suportado no Windows RT, Windows RT 8.1 e Windows 8.1. Se **Tipo obrigatório de palavra-passe** estiver definido como **Alfanumérico**, esta definição especifica o número mínimo de conjuntos de carateres que a palavra-passe tem de ter. Os quatro conjuntos de carateres são:
  - Letras minúsculas
  - Letras maiúsculas
  - Símbolos
  - Números: definir um número maior nesta definição obriga os utilizadores a criarem palavras-passe mais complexas.

Nos dispositivos acedidos com uma Conta Microsoft, a política de conformidade não avalia corretamente se o **Comprimento mínimo da palavra-passe** é superior a oito carateres ou se o **Número mínimo de conjuntos de carateres** é superior a dois carateres.

- **Minutos de inatividade antes de a palavra-passe ser exigida:** - suportada no Windows RT, Windows RT 8.1 e Windows 8.1

Especifique o tempo de inatividade antes de o utilizador ter de reintroduzir a palavra-passe.

- **Expiração da palavra-passe (dias):** suportado no Windows RT, Windows RT 8.1 e Windows 8.1.

Selecione o número de dias antes de a palavra-passe do utilizador expirar e ser necessário criar uma nova.

- **Memorizar histórico de palavras-passe:** - suportada no Windows RT, Windows RT e Windows 8.1.

Utilize esta definição juntamente com **Impedir a reutilização de palavras-passe anteriores** para impedir o utilizador de criar palavras-passe utilizadas anteriormente.

- **Impedir a reutilização de palavras-passe anteriores:** - suportada no Windows RT, Windows RT 8.1 e Windows 8.1

Se a opção **Memorizar histórico de palavras-passe:** estiver selecionada, especifique o número de palavras-passe utilizadas anteriormente que não podem ser reutilizadas.


## <a name="device-health-settings"></a>Definições de estado de funcionamento do dispositivo

- **Exigir que os dispositivos sejam comunicados como estando em bom estado de funcionamento:** - suportada nos dispositivos com o Windows 10. Pode definir uma regra para exigir que os dispositivos com o Windows 10 sejam comunicados como estando em bom estado de funcionamento nas Políticas de Conformidade novas ou existentes. Se esta definição estiver ativada, os dispositivos com o Windows 10 serão avaliados através do Serviço de Atestado de Estado de Funcionamento (HAS) quanto aos seguintes pontos de dados:
  - **BitLocker está ativado:** se o BitLocker estiver ativado, o dispositivo é capaz de proteger os dados que são armazenados na unidade contra acesso não autorizado, quando o sistema é desligado ou entra em hibernação. A Encriptação de Unidade BitLocker do Windows encripta todos os dados armazenados no volume do sistema operativo Windows. O BitLocker utiliza o TPM para ajudar a proteger o sistema operativo Windows e os dados de utilizador e ajuda a garantir que os computadores não são adulterados, mesmo que não estejam a ser vigiados, sejam roubados ou se percam. Se os computadores estiverem equipados com um TPM compatível, o BitLocker utiliza o TPM para bloquear as chaves de encriptação que protegem os dados. Como resultado, as chaves não podem ser acedidas até o TPM ter verificado o estado do computador
  - **A integridade do código está ativada:** a integridade do código é uma funcionalidade que valida a integridade de um ficheiro de controlador ou de sistema sempre que é carregado para a memória. A integridade do código deteta se está a ser carregado um ficheiro de controlador ou de sistema não assinado para o kernel ou se um ficheiro de sistema foi modificado por software malicioso que está a ser executado por uma conta de utilizador com privilégios administrativos.
  - **O Arranque Seguro está ativado:** se o Arranque Seguro estiver ativado, o sistema é forçado a fazer o arranque para um estado de fábrica fidedigno. Além disso, com o Arranque Seguro ativado, os componentes do núcleo utilizados para arrancar o computador têm de ter assinaturas criptográficas corretas e que sejam consideradas fidedignas pela organização que fabricou o dispositivo. O firmware UEFI verifica isto antes de permitir que o computador seja iniciado. Se um ficheiro tiver sido adulterado, danificando a respetiva assinatura, o sistema não arrancará.
  - **O antimalware de início antecipado está ativado:** o antimalware de início antecipado (ELAM) proporciona proteção aos computadores da sua rede quando são iniciados e antes de os controladores de terceiros serem inicializados.

Para obter informações sobre como funciona o serviço HAS, veja [Health Attestation CSP (CSP de Atestado de Estado de Funcionamento)](https://msdn.microsoft.com/library/dn934876.aspx).

## <a name="device-property-settings"></a>Definições de propriedade do dispositivo

- **SO mínimo obrigatório:** - suportada no Windows 8.1 e Windows 10.

Especifique o número major.minor.build aqui. O número de versão tem de corresponder à versão devolvida pelo comando ```winver```.

Quando um dispositivo tem uma versão anterior à versão de SO especificada, é comunicado como não conforme. É apresentada uma ligação com informações sobre como atualizar. O utilizador final pode optar por atualizar o dispositivo para poder aceder aos recursos da empresa.

- **Versão máxima de SO permitida:** - suportada no Windows 8.1 e Windows 10.

Quando um dispositivo está a utilizar uma versão do SO posterior à especificada na regra, o acesso aos recursos da empresa é bloqueado e é pedido ao utilizador que contacte o administrador de TI. Até a regra ser alterada para permitir a versão do SO, este dispositivo não pode ser utilizado no acesso aos recursos da empresa.

Para localizar a versão de SO a utilizar para as definições **SO mínimo obrigatório** e **Versão máxima de SO permitida**, execute o comando **winver** a partir da linha de comandos. O comando winver devolve a versão comunicada do sistema operativo.

- Os PCs Windows 8.1 devolvem a versão **3**. Se a regra de versão de SO estiver definida como Windows 8.1 para o Windows, o dispositivo é comunicado como não conforme, mesmo que tenha o sistema operativo Windows 8.1.
- Nos PCs com o Windows 10, a versão deve ser definida como "10.0" + o número de Compilação do SO devolvido pelo comando winver.

## <a name="windows-holographic-for-business-support"></a>Suporte do Windows Holographic for Business

O Windows Holographic for Business suporta a seguinte definição:

- Segurança do Sistema/Encriptação

  **Encriptação do armazenamento de dados no dispositivo**.

Para verificar a encriptação de dispositivos no Microsoft HoloLens, veja [Verify device encryption (Verificar a encriptação de dispositivos)](https://docs.microsoft.com/hololens/hololens-encryption#verify-device-encryption).

## <a name="next-steps"></a>Próximos passos

Veja o seguinte tópico para saber como pode monitorizar a conformidade do dispositivo:

- [Como monitorizar a compatibilidade do dispositivo](device-compliance-monitor.md)
