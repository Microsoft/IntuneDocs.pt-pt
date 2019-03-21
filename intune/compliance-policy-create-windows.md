---
title: Verificação de conformidade em dispositivos Windows no Microsoft Intune – Azure | Documentos da Microsoft
description: Crie ou configure uma política de conformidade de dispositivos do Microsoft Intune para o Windows Phone 8.1, Windows 8.1 e posterior e Windows 10 e dispositivos posteriores. Verifique a conformidade do sistema operativo mínimo e máximo, defina as restrições e o comprimento de palavras-passe, exija o bitlocker, verifique a existência de soluções AV de terceiros, defina o nível de ameaça aceitável e ative a encriptação no armazenamento de dados, incluindo o Surface Hub e o Windows Holographic para Empresas.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/20/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: acf14ea6f1b667cb631a424223a40e44a8338edd
ms.sourcegitcommit: 768430b5296573c6e007ae4e13d57aeda4be4b7e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/21/2019
ms.locfileid: "58306847"
---
# <a name="add-a-device-compliance-policy-for-windows-devices-in-intune"></a>Adicionar uma política de conformidade para dispositivos Windows no Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Uma política de conformidade de dispositivos do Intune inclui regras e definições que os dispositivos têm de cumprir para ser considerado conforme. Utilize estas políticas com acesso condicional para permitir ou bloquear o acesso a recursos da sua organização. Também pode obter relatórios de dispositivos e agir relativamente a situações de não conformidade.

Para saber mais sobre as políticas de conformidade, veja [Introdução à conformidade de dispositivos](device-compliance-get-started.md).

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
| **Atestado do estado de funcionamento do Windows** | Em quarentena: Computadores e dispositivos móveis com o Windows 10 Mobile|Não aplicável: Windows 8.1 |

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

- **SO mínimo obrigatório**: Quando um dispositivo não cumpre o requisito de versão mínima do SO, será comunicado como não conforme. É apresentada uma ligação com informações sobre como atualizar. O utilizador final pode optar por atualizar o dispositivo e, em seguida, obter acesso aos recursos da empresa.
- **Versão do SO máxima permitida**: Quando um dispositivo utiliza uma versão do SO posterior à versão introduzida na regra, o acesso aos recursos da empresa é bloqueado. É pedido ao utilizador para contactar o administrador de TI. O dispositivo não é possível aceder a recursos organizacionais até que alterar a regra para permitir que a versão do SO.

Os PCs Windows 8.1 devolvem a versão **3**. Se a regra de versão de SO estiver definida como Windows 8.1 para o Windows, o dispositivo é comunicado como não conforme, mesmo que tenha o sistema operativo Windows 8.1.

### <a name="system-security"></a>Segurança do sistema

#### <a name="password"></a>Palavra-passe

- **Exigir uma palavra-passe para desbloquear dispositivos móveis**: **Exigir** que os utilizadores introduzam uma palavra-passe antes de poderem aceder ao respetivo dispositivo.
- **Palavras-passe simples**: Defina como **bloco** para que os utilizadores não é possível criar palavras-passe simples, tal como **1234** ou **1111**. Defina como **Não configurado** para permitir aos utilizadores criar palavras-passe como **1234** ou **1111**.
- **Comprimento mínimo da palavra-passe**: Introduza o número mínimo de dígitos ou carateres que a palavra-passe tem de ter.

  Para dispositivos que executam o Windows e são acedidos com uma conta Microsoft, a política de conformidade não consegue avaliar corretamente:
  - Se o comprimento mínimo da palavra-passe é superior a oito carateres
  - Ou, se o número mínimo de conjuntos de carateres é superior a dois

- **Tipo de palavra-passe**: Escolha se uma palavra-passe deve ter apenas **numérico** carateres, ou se deve existir uma combinação de números e outros carateres (**alfanumérico**).
  
  - **Número de carateres não alfanuméricos na palavra-passe**: Se **Tipo obrigatório de palavra-passe** estiver definido como **Alfanumérico**, esta definição especifica o número mínimo de conjuntos de carateres que a palavra-passe tem de ter. Os quatro conjuntos de carateres são:
    - Letras minúsculas
    - Letras maiúsculas
    - Símbolos
    - Números

    Definir um número mais relevado exige que o utilizador crie uma palavra-passe mais complexa. Para dispositivos que são acedidos com uma conta Microsoft, a política de conformidade não avalia corretamente:

    - Se o comprimento mínimo da palavra-passe é superior a oito carateres
    - Ou, se definir o número mínimo de carateres é superior a dois

- **Máximo de minutos de inatividade antes da palavra-passe é necessária**: Introduza o tempo de inatividade antes do utilizador ter de reintroduzir a palavra-passe.
- **Expiração de palavra-passe (dias)**: Selecione o número de dias antes da palavra-passe expirar e ser necessário criar um novo.
- **Número de palavras-passe anteriores cuja reutilização está**: Introduza o número de palavras-passe utilizadas anteriormente que não pode ser utilizado.

#### <a name="encryption"></a>Encriptação

- **Exigir encriptação no dispositivo móvel**: **Exigir** o dispositivo sejam encriptados para ligar a recursos de armazenamento de dados.

## <a name="windows-10-and-later-policy-settings"></a>Definições de política do Windows 10 e posterior

### <a name="device-health"></a>Device health

- **Exigir o BitLocker**: Quando o BitLocker estiver ativado, o dispositivo pode proteger os dados armazenados na unidade contra acesso não autorizado, quando o sistema é desligado ou entra em hibernação. A Encriptação de Unidade BitLocker do Windows encripta todos os dados armazenados no volume do sistema operativo Windows. O BitLocker utiliza o TPM para ajudar a proteger o sistema operativo Windows e os dados de utilizador. Ele também ajuda a confirmar que um computador não estiver adulterado, mesmo que sua esquerda autônoma, perda ou roubo. Se os computadores estiverem equipados com um TPM compatível, o BitLocker utiliza o TPM para bloquear as chaves de encriptação que protegem os dados. Como resultado, as chaves não podem ser acedidas até que o TPM verifica o estado do computador.
- **Exigir que o arranque seguro seja ativado no dispositivo**: Se o Arranque Seguro estiver ativado, o sistema é forçado a fazer o arranque para um estado de fábrica fidedigno. Além disso, com o Arranque Seguro ativado, os componentes do núcleo utilizados para arrancar o computador têm de ter assinaturas criptográficas corretas e que sejam consideradas fidedignas pela organização que fabricou o dispositivo. O firmware UEFI verifica a assinatura antes de permitir que o computador seja iniciado. Se todos os ficheiros são adulterados, que quebra a respetiva assinatura, o sistema não arranque.

  > [!NOTE]
  > O **necessitam de arranque seguro seja ativado no dispositivo** definição é suportada em alguns TPM 1.2 e 2.0 dispositivos. Para os dispositivos que não suportam o TPM 2.0 ou posterior, o estado da política no Intune é mostrado como **Não Conforme**. Para obter mais informações sobre as versões suportadas, consulte [atestado de estado de funcionamento do dispositivo](https://docs.microsoft.com/windows/security/information-protection/tpm/trusted-platform-module-overview#device-health-attestation).

- **Exigir integridade de código**: Integridade do código é uma funcionalidade que valida a integridade de um ficheiro de controlador ou de sistema sempre que é carregado na memória. Integridade do código Deteta se um ficheiro de controlador ou de sistema não assinado está a ser carregado para o kernel. Também Deteta se um ficheiro de sistema é modificado por software malicioso executado por uma conta de utilizador com privilégios de administrador.

Recursos adicionais:

- [CSP de atestado de estado de funcionamento](https://docs.microsoft.com/windows/client-management/mdm/healthattestation-csp) contém os detalhes sobre como funciona o serviço HAS.
- [Sugestão de suporte: Utilizar definições de atestado de estado de funcionamento do dispositivo como parte da sua política de conformidade do Intune ](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Using-Device-Health-Attestation-Settings-as-Part-of/ba-p/282643)

### <a name="device-properties"></a>Propriedades do dispositivo

- **Versão mínima do SO**: Introduza a versão mínima permitida no **número major.minor.build.CU** formato. Para obter o valor correto, abra uma linha de comandos e escreva `ver`. O comando `ver` devolve a versão no seguinte formato:

  `Microsoft Windows [Version 10.0.17134.1]`

  Quando um dispositivo tem uma versão anterior à versão de SO, introduzir, será comunicado como não conforme. É apresentada uma hiperligação com informações sobre como atualizar. O utilizador final pode optar por atualizar o dispositivo. Após a atualização, podem aceder a recursos da empresa.

- **Versão do SO máxima**: Introduza o máximo permitido de versão, no **número major** formato. Para obter o valor correto, abra uma linha de comandos e escreva `ver`. O comando `ver` devolve a versão no seguinte formato:

  `Microsoft Windows [Version 10.0.17134.1]`

  Quando um dispositivo utiliza uma versão do SO posterior à introduzido na regra, o acesso aos recursos da empresa é bloqueado e é pedido ao utilizador que contacte o administrador de TI. O dispositivo não é possível aceder aos recursos da empresa até que a regra seja alterada para permitir que a versão do SO.

- **SO mínimo obrigatório para dispositivos móveis**: Introduza o mínimo de versão, no formato de número major.

  Quando um dispositivo tem uma versão anterior que a versão do SO introduzir, será comunicado como não conforme. É apresentada uma hiperligação com informações sobre como atualizar. O utilizador final pode optar por atualizar o dispositivo. Após a atualização, podem aceder a recursos da empresa.

- **SO máximo obrigatório para dispositivos móveis**: Introduza o máximo permitido de versão, o número major.

  Quando um dispositivo utiliza uma versão do SO posterior à introduzir, acesso aos recursos da empresa é bloqueado e é pedido ao utilizador que contacte o administrador de TI. O dispositivo não é possível aceder aos recursos da empresa até que a regra seja alterada para permitir que a versão do SO.

- **Compilações válidas do sistema operativo**: Introduza um intervalo para as versões de sistemas operativos aceitáveis, incluindo um mínimo e máximo. Também pode **Exportar** uma lista de ficheiros de valores separados por vírgulas (CSV) destes números de compilação de SO aceitáveis.

### <a name="configuration-manager-compliance"></a>Compatibilidade do Configuration Manager

Aplica-se apenas a dispositivos cogeridos com Windows 10 e posterior. Dispositivos apenas o Intune devolvem um Estado não está disponível.

- **Exigir conformidade do dispositivo do System Center Configuration Manager**: Escolher **requerem** para forçar a todas as definições (itens de configuração) no System Center Configuration Manager, para estar em conformidade. 

  Por exemplo, pode exigir que todas as atualizações do software sejam instaladas nos dispositivos. No Configuration Manager, este requisito apresenta o estado "Instalado". Se todos os programas no dispositivo estão num Estado desconhecido, em seguida, o dispositivo está em conformidade no Intune.
  
  Quando **não configurado**, o Intune não verifica para qualquer uma das definições de compatibilidade do Configuration Manager.

### <a name="system-security-settings"></a>Definições de segurança do sistema

#### <a name="password"></a>Palavra-passe

- **Exigir uma palavra-passe para desbloquear dispositivos móveis**: **Exigir** que os utilizadores introduzam uma palavra-passe antes de poderem aceder ao respetivo dispositivo.
- **Palavras-passe simples**: Defina como **bloco** para que os utilizadores não é possível criar palavras-passe simples, tal como **1234** ou **1111**. Defina como **Não configurado** para permitir aos utilizadores criar palavras-passe como **1234** ou **1111**.
- **Tipo de palavra-passe**: Escolha se uma palavra-passe deve ter apenas **numérico** carateres, ou se deve existir uma combinação de números e outros carateres (**alfanumérico**).

  - **Número de carateres não alfanuméricos na palavra-passe**: Se **Tipo obrigatório de palavra-passe** estiver definido como **Alfanumérico**, esta definição especifica o número mínimo de conjuntos de carateres que a palavra-passe tem de ter. Os quatro conjuntos de carateres são:
    - Letras minúsculas
    - Letras maiúsculas
    - Símbolos
    - Números

    Definir um número mais relevado exige que o utilizador crie uma palavra-passe mais complexa.

- **Comprimento mínimo da palavra-passe**: Introduza o número mínimo de dígitos ou carateres que a palavra-passe tem de ter.
- **Máximo de minutos de inatividade antes da palavra-passe é necessária**: Introduza o tempo de inatividade antes do utilizador ter de reintroduzir a palavra-passe.
- **Expiração de palavra-passe (dias)**: Selecione o número de dias antes da palavra-passe expirar e ser necessário criar um novo.
- **Número de palavras-passe anteriores cuja reutilização está**: Introduza o número de palavras-passe utilizadas anteriormente que não pode ser utilizado.
- **Exigir palavra-passe quando o dispositivo regressa do Estado de inatividade (Mobile e Holographic)**: Forçar os usuários a introduzir a palavra-passe sempre que o dispositivo regressa de um estado inativo.

#### <a name="encryption"></a>Encriptação

- **Encriptação do armazenamento de dados num dispositivo de**: Escolher **requerem** para encriptar o armazenamento de dados nos seus dispositivos.

  > [!NOTE]
  > A definição **Encriptação do armazenamento de dados num dispositivo** verifica genericamente a presença de encriptação no dispositivo. Para uma definição de encriptação mais avançada, considere utilizar **Exigir o BitLocker**, que tira partido do Windows Device Health Attestation para validar o estado do Bitlocker ao nível do TPM.

#### <a name="device-security"></a>Segurança do Dispositivo

- **Antivírus**: Quando definido como **requerem**, pode verificar a conformidade com as soluções antivírus que estão registadas [Centro de segurança do Windows](https://blogs.windows.com/windowsexperience/2017/01/23/introducing-windows-defender-security-center/), por exemplo, Symantec e o Windows Defender. Quando estiver definido como **Não configurado**, o Intune não verifica a existência de soluções AV instaladas no dispositivo.
- **AntiSpyware**: Quando definido como **requerem**, pode verificar conformidade através de soluções de anti-spyware que estão registadas [Centro de segurança do Windows](https://blogs.windows.com/windowsexperience/2017/01/23/introducing-windows-defender-security-center/), por exemplo, Symantec e o Windows Defender. Quando estiver definido como **Não configurado**, o Intune não verifica a existência de soluções de AntiSpyware instaladas no dispositivo.

### <a name="windows-defender-atp"></a>Windows Defender ATP

- **Exigir que o dispositivo estar ou sob a classificação de risco de máquina**: Utilize esta definição para assumir a avaliação de risco de defesa contra os serviços de ameaças como uma condição para conformidade. Selecione o nível de ameaça máximo permitido:
  - **Limpar**: Esta opção é a mais segura, uma vez que o dispositivo não pode ter qualquer ameaça. Se o dispositivo detetar qualquer nível de ameaças, é avaliado como não conforme.
  - **Baixa**: O dispositivo é avaliado como conforme se só estiverem presentes ameaças de nível baixo. Qualquer nível mais alto coloca o dispositivo num estado de não conforme.
  - **Médio**: O dispositivo é avaliado como conforme se as ameaças existentes no dispositivo forem de nível baixo ou médio. Se forem detetadas ameaças de nível alto no dispositivo, este será determinado como não conforme.
  - **Alta**: Esta opção é menos segura e permite todos os níveis de ameaça. Poderá ser útil se utilizar esta solução apenas para fins de relatórios.
  
  Para configurar o Windows Defender ATP (Proteção Avançada Contra Ameaças) como o seu serviço de defesa contra ameaças, veja [Ativar o Windows Defender ATP com acesso condicional](advanced-threat-protection.md).

## <a name="windows-holographic-for-business"></a>Windows Holographic for Business

O Windows Holographic for Business utiliza a plataforma **Windows 10 e posterior**. O Windows Holographic for Business suporta a seguinte definição:

- **Segurança do Sistema** > **Encriptação** > **Encriptação do armazenamento de dados no dispositivo**.

Para verificar a encriptação de dispositivos no Microsoft HoloLens, veja [Verify device encryption (Verificar a encriptação de dispositivos)](https://docs.microsoft.com/hololens/hololens-encryption#verify-device-encryption).

## <a name="surface-hub"></a>Surface Hub
O Surface Hub utiliza a plataforma **Windows 10 e posterior**. Os Surface Hubs são suportados para o acesso condicional e a conformidade. Para ativar estas funcionalidades nos Surface Hubs, recomendamos que [ativar a inscrição automática do Windows 10](windows-enroll.md) no Intune (por também requer o Azure Active Directory (Azure AD)) e os dispositivos Surface Hub como grupos de dispositivos de destino. Os Surface Hubs têm de ser associados ao Azure AD para conformidade e acesso condicional funcionar.

Veja [configurar a inscrição para dispositivos Windows](windows-enroll.md) para obter orientações.

## <a name="assign-user-or-device-groups"></a>Atribuir grupos de utilizadores ou dispositivos

1. Escolha uma política configurada por si. As políticas existentes encontram-se em **Conformidade do dispositivo** > **Políticas**.
2. Escolha a política e, em seguida, **Atribuições**. Pode incluir ou excluir grupos de segurança do Azure AD.
3. Escolha **Grupos selecionados** para ver os grupos de segurança do Azure AD. Selecione os grupos de utilizadores ou de dispositivos aos quais pretende aplicar esta política e escolha **Guardar** para implementar a política.

A política foi aplicada. Os dispositivos utilizados pelos utilizadores abrangidos pela política são avaliados quanto à conformidade.

## <a name="next-steps"></a>Passos Seguintes
[Automatizar o e-mail e adicionar ações para dispositivos não conformes](actions-for-noncompliance.md)  
[Monitorizar as políticas de conformidade do Dispositivo do Intune](compliance-policy-monitor.md)
