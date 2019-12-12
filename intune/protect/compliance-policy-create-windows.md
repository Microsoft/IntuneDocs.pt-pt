---
title: Configurações de conformidade do Windows 10 no Microsoft Intune – Azure | Microsoft Docs
description: Consulte uma lista de todas as configurações que você pode usar ao definir a conformidade para seus dispositivos Windows 10, Windows Holographic e Surface Hub no Microsoft Intune. Verifique a conformidade no sistema operacional mínimo e máximo, defina as restrições de senha e o comprimento, verifique as soluções de antivírus (antivírus) do parceiro, habilite a criptografia no armazenamento de dados e muito mais.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 12/09/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: samyada
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 60a87340c1a275b8fb878ef2f3891cca23fc9c85
ms.sourcegitcommit: f5108039f0ade52e95ea3ac1da1aa16d02224af3
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/09/2019
ms.locfileid: "74946668"
---
# <a name="windows-10-and-later-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>Configurações do Windows 10 e posteriores para marcar dispositivos como em conformidade ou sem conformidade usando o Intune

Este artigo lista e descreve as diferentes configurações de conformidade que você pode configurar em dispositivos Windows 10 e posteriores no Intune. Como parte da sua solução de MDM (gerenciamento de dispositivo móvel), use essas configurações para exigir o BitLocker, defina um sistema operacional mínimo e máximo, defina um nível de risco usando a ATP (proteção avançada contra ameaças) do Microsoft defender e muito mais.

Esta funcionalidade aplica-se a:

- Windows 10 e posterior
- Windows Holographic for Business
- Surface Hub

Enquanto administrador do Intune, utilize estas definições de conformidade para ajudar a proteger os recursos da sua organização. Para saber mais sobre as políticas de conformidade e para o que servem, veja a [introdução à conformidade de dispositivos](device-compliance-get-started.md).

## <a name="before-you-begin"></a>Antes de começar

[Criar uma política de conformidade](create-compliance-policy.md#create-the-policy). Em **Plataforma**, selecione **Windows 10 e versões posteriores**.

## <a name="device-health"></a>Estado de Funcionamento do Dispositivo

### <a name="windows-health-attestation-service-evaluation-rules"></a>Regras de avaliação do serviço de atestado de integridade do Windows

- **Exigir BitLocker**:  
   A Encriptação de Unidade BitLocker do Windows encripta todos os dados armazenados no volume do sistema operativo Windows. O BitLocker usa o Trusted Platform Module (TPM) para ajudar a proteger o sistema operacional Windows e os dados do usuário. Ele também ajuda a confirmar se um computador não está adulterado, mesmo se ele for deixado em modo autônomo, perdido ou roubado. Se os computadores estiverem equipados com um TPM compatível, o BitLocker utiliza o TPM para bloquear as chaves de encriptação que protegem os dados. Como resultado, as chaves não podem ser acessadas até que o TPM Verifique o estado do computador.  

   - **Não configurado** (*padrão*)-essa configuração não é avaliada quanto à conformidade ou à não conformidade.
   - **Exigir** – o dispositivo pode proteger os dados armazenados na unidade contra acesso não autorizado quando o sistema estiver desligado ou hibernando.  


- **Exigir que a inicialização segura seja habilitada no dispositivo**:  
    - **Não configurado** (*padrão*)-essa configuração não é avaliada quanto à conformidade ou à não conformidade.
    - **Exigir** -o sistema é forçado a inicializar para um estado confiável de fábrica. Os componentes principais que são usados para inicializar o computador devem ter assinaturas criptográficas corretas que são confiáveis para a organização que fabricou o dispositivo. O firmware UEFI verifica a assinatura antes de permitir que o computador seja iniciado. Se algum arquivo for violado, o que interromperá a assinatura, o sistema não inicializará.

  > [!NOTE]
  > O **exigir a inicialização segura a ser habilitada na configuração do dispositivo** tem suporte em alguns dispositivos do TPM 1,2 e 2,0. Para os dispositivos que não suportam o TPM 2.0 ou posterior, o estado da política no Intune é mostrado como **Não Conforme**. Para obter mais informações sobre as versões com suporte, consulte [atestado de integridade do dispositivo](https://docs.microsoft.com/windows/security/information-protection/tpm/trusted-platform-module-overview#device-health-attestation).

- **Exigir integridade de código**:  
  A integridade de código é um recurso que valida a integridade de um arquivo do driver ou do sistema sempre que ele é carregado na memória.
  - **Não configurado** (*padrão*)-essa configuração não é avaliada quanto à conformidade ou à não conformidade.
  -  **Require** -requer integridade de código, que detecta se um arquivo de sistema ou driver não assinado está sendo carregado no kernel. Ele também detecta se um arquivo de sistema é alterado por software mal-intencionado ou executado por uma conta de usuário com privilégios de administrador.

Mais recursos:

- Para obter detalhes sobre como o serviço de atestado de integridade funciona, consulte [CSP de atestado de integridade](https://docs.microsoft.com/windows/client-management/mdm/healthattestation-csp).
- [Dica de suporte: usando configurações de atestado de integridade do dispositivo como parte de sua política de conformidade do Intune](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Using-Device-Health-Attestation-Settings-as-Part-of/ba-p/282643).

## <a name="device-properties"></a>Propriedades do Dispositivo

### <a name="operating-system-version"></a>Versão do Sistema Operativo

- **Versão mínima do SO**:  
  Insira a versão mínima permitida no formato de **número Major.Minor.Build.cu** . Para obter o valor correto, abra uma linha de comandos e escreva `ver`. O comando `ver` devolve a versão no seguinte formato:

  `Microsoft Windows [Version 10.0.17134.1]`

  Quando um dispositivo tem uma versão anterior à versão do sistema operacional que você insere, ele é relatado como não compatível. É apresentada uma hiperligação com informações sobre como atualizar. O utilizador final pode optar por atualizar o dispositivo. Após a atualização, eles podem acessar os recursos da empresa.

- **Versão máxima do SO**:  
  Insira a versão máxima permitida, no formato de **número principal. secundária. Build. Revision** . Para obter o valor correto, abra uma linha de comandos e escreva `ver`. O comando `ver` devolve a versão no seguinte formato:

  `Microsoft Windows [Version 10.0.17134.1]`

  Quando um dispositivo estiver usando uma versão do sistema operacional posterior à versão inserida, o acesso aos recursos da organização será bloqueado. É pedido ao utilizador final para contactar o administrador de TI. O dispositivo não poderá acessar os recursos da organização até que a regra seja alterada para permitir a versão do sistema operacional.

- **Sistema operacional mínimo necessário para dispositivos móveis**:  
  Insira a versão mínima permitida, no formato de número principal. secundária. Build.

  Quando um dispositivo tem uma versão anterior que a versão do sistema operacional inserida, ele é relatado como não compatível. É apresentada uma hiperligação com informações sobre como atualizar. O utilizador final pode optar por atualizar o dispositivo. Após a atualização, eles podem acessar os recursos da empresa.

- **Sistema operacional máximo necessário para dispositivos móveis**:  
  Insira a versão máxima permitida, no número principal. secundária. Build.

  Quando um dispositivo estiver usando uma versão do sistema operacional posterior à versão inserida, o acesso aos recursos da organização será bloqueado. É pedido ao utilizador final para contactar o administrador de TI. O dispositivo não poderá acessar os recursos da organização até que a regra seja alterada para permitir a versão do sistema operacional.

- **Builds de sistema operacional válidos**:  
  Insira um intervalo para as versões de sistemas operacionais aceitáveis, incluindo um mínimo e um máximo. Também pode **Exportar** uma lista de ficheiros de valores separados por vírgulas (CSV) destes números de compilação de SO aceitáveis.

## <a name="configuration-manager-compliance"></a>Conformidade de Configuration Manager

Aplica-se somente a dispositivos cogerenciados que executam o Windows 10 e posterior. Os dispositivos somente do Intune retornam um status não disponível.

- **Exigir conformidade do dispositivo de System Center Configuration Manager**:  
  - **Não configurado** (*padrão*)-o Intune não verifica se há configurações de Configuration Manager para fins de conformidade.
  - **Require** -requer que todas as configurações (itens de configuração) em System Center Configuration Manager sejam compatíveis.  

    Por exemplo, pode exigir que todas as atualizações do software sejam instaladas nos dispositivos. No Configuration Manager, este requisito apresenta o estado "Instalado". Se algum programa no dispositivo estiver em um estado desconhecido, o dispositivo não será compatível no Intune.

## <a name="system-security"></a>Segurança do sistema

### <a name="password"></a>Palavra-passe

- **Exigir uma palavra-passe para desbloquear os dispositivos móveis**:  
  - **Não configurado** (*padrão*)-essa configuração não é avaliada quanto à conformidade ou à não conformidade.
  - **Exigir** -os usuários devem inserir uma senha antes que possam acessar seu dispositivo. 

- **Palavras-passe simples**:  
  - **Não configurado** (*padrão*)-os usuários podem criar senhas simples, como **1234** ou **1111**.
  - **Bloquear** -os usuários não podem criar senhas simples, como **1234** ou **1111**.

- **Tipo de palavra-passe**:  
  Escolha o tipo de senha ou PIN necessário. As opções são:
  - **Padrão do dispositivo** (*padrão*)-exigir uma senha, PIN numérico ou PIN alfanumérico
  - **Numeric** -exigir uma senha ou PIN numérico
  - **Alfanumérico** -exigir uma senha ou PIN alfanumérico.  
  
  Quando definido como *alfanumérico*, as seguintes configurações estão disponíveis:  
  - **Complexidade da senha**:  
    As opções são: 
    - **Exigir dígitos e letras minúsculas** (*padrão*)
    - **Exigir dígitos, letras minúsculas e letras maiúsculas**
    - **Exigir dígitos, letras minúsculas, letras maiúsculas e caracteres especiais**

    > [!TIP]
    > As políticas de senha alfanuméricas podem ser complexas. Incentivamos os administradores a ler os CSPs para obter mais informações:
    >
    > - [CSP DeviceLock/AlphanumericDevicePasswordRequired](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-alphanumericdevicepasswordrequired)
    > - [CSP DeviceLock/MinDevicePasswordComplexCharacters](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-mindevicepasswordcomplexcharacters)

- **Comprimento mínimo da palavra-passe**:  
  introduza o número mínimo de dígitos ou carateres que a palavra-passe tem de ter.

- **Minutos de inatividade antes de a palavra-passe ser exigida**:  
  introduza o tempo de inatividade antes de o utilizador ter de reintroduzir a palavra-passe.

- **Expiração da palavra-passe (dias)** :  
  Insira o número de dias antes que a senha expire e ela deve criar uma nova, de 1-730.

- **Número de palavras-passe anteriores para impedir a reutilização**:  
  introduza o número de palavras-passe utilizadas anteriormente que não podem ser utilizadas.

- **Exigir senha quando o dispositivo retorna do estado ocioso (móvel e Holographic)** :  
  - **Não configurado** (*padrão*)
  - **Exigir** -exigir que os usuários do dispositivo insiram a senha toda vez que o dispositivo retornar do estado ocioso.

  > [!IMPORTANT]
  > Quando o requisito de senha for alterado em uma área de trabalho do Windows, os usuários serão afetados na próxima vez que entrarem, como é quando o dispositivo vai de ocioso para ativo. Os usuários com senhas que atendem ao requisito ainda são solicitados a alterar suas senhas.

### <a name="encryption"></a>Encriptação

- **Encriptação do armazenamento de dados num dispositivo**:  
  Essa configuração se aplica a todas as unidades em um dispositivo.
  - **Não configurado** (*padrão*)
  - **Exigir** -use *exigir* para criptografar o armazenamento de dados em seus dispositivos.

  > [!NOTE]
  > A definição **Encriptação do armazenamento de dados num dispositivo** verifica genericamente a presença de encriptação no dispositivo. Para uma definição de encriptação mais avançada, considere utilizar **Exigir o BitLocker**, que tira partido do Windows Device Health Attestation para validar o estado do Bitlocker ao nível do TPM.

### <a name="device-security"></a>Segurança do Dispositivo  

- **Firewall**:  
  - **Não configurado** (*padrão*)-o Intune não controla o Microsoft defender firewall nem altera as configurações existentes.
  - **Exigir** -ativar o Microsoft defender firewall e impedir que os usuários o desativem.  

  [CSP do firewall](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp)

  > [!NOTE]
  > Se o dispositivo for sincronizado imediatamente após uma reinicialização ou sincronizar imediatamente a ativação do estado de suspensão, essa configuração poderá ser relatada como um **erro**. Esse cenário pode não afetar o status geral de conformidade do dispositivo. Para reavaliar o status de conformidade, [sincronize manualmente o dispositivo](https://docs.microsoft.com/intune-user-help/sync-your-device-manually-windows).

- **Trusted Platform Module (TPM)** :  
  - **Não configurado** (*padrão*)-o Intune não verifica a versão do chip do TPM no dispositivo.
  - **Exigir** -o Intune verifica a versão do chip do TPM quanto à conformidade. O dispositivo será compatível se a versão do chip do TPM for maior que **0** (zero). O dispositivo não será compatível se não houver uma versão do TPM no dispositivo.  

  [DeviceStatus CSP-DeviceStatus/TPM/nó SpecificationVersion](https://docs.microsoft.com/windows/client-management/mdm/devicestatus-csp)
  
- **Antivírus**:  
  - **Não configurado** (*padrão*)-o Intune não verifica se há soluções antivírus instaladas no dispositivo. 
  - **Exigir** -verificar a conformidade usando soluções de antivírus registradas com a [central de segurança do Windows](https://blogs.windows.com/windowsexperience/2017/01/23/introducing-windows-defender-security-center/), como Symantec e Microsoft defender.

- **AntiSpyware**:  
  - **Não configurado** (*padrão*)-o Intune não verifica se há soluções AntiSpyware instaladas no dispositivo.
  - **Exigir** -verificar a conformidade usando soluções AntiSpyware registradas com a [central de segurança do Windows](https://blogs.windows.com/windowsexperience/2017/01/23/introducing-windows-defender-security-center/), como Symantec e Microsoft defender.  

### <a name="defender"></a>Defender

*As configurações de conformidade a seguir têm suporte com o Windows 10 desktop.*

- **Antimalware do Microsoft defender**:  
  - **Não configurado** (*padrão*)-o Intune não controla o serviço nem altera as configurações existentes.
  - **Exigir** -ativar o serviço antimalware do Microsoft defender e impedir que os usuários o desativem.

- **Versão mínima do Microsoft Defender Antimalware**:  
  Insira a versão mínima permitida do serviço antimalware do Microsoft defender. Por exemplo, introduza `4.11.0.0`. Quando deixado em branco, qualquer versão do serviço antimalware do Microsoft defender pode ser usada.  

  *Por padrão, nenhuma versão é configurada*.

- **Inteligência de segurança antimalware do Microsoft defender atualizada**:  
  Controla as atualizações de proteção contra ameaças e vírus de segurança do Windows nos dispositivos.
  - **Não configurado** (*padrão*)-o Intune não impõe nenhum requisito.
  - **Exigir** -força a inteligência de segurança do Microsoft defender a ser atualizada.

  [CSP do defender/Health/SignatureOutOfDate](https://docs.microsoft.com/windows/client-management/mdm/defender-csp)
  
  Para obter mais informações, consulte [atualizações de inteligência de segurança para o Microsoft defender antivírus e outros antimalware da Microsoft](https://www.microsoft.com/en-us/wdsi/defenderupdates).

- **Proteção em tempo real**:  
  - **Não configurado** (*padrão*)-o Intune não controla esse recurso nem altera as configurações existentes.
  - **Exigir** – ative a proteção em tempo real, que verifica o malware, spyware e outros softwares indesejados.  

  [CSP do defender/AllowRealtimeMonitoring](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowrealtimemonitoring)

## <a name="microsoft-defender-atp"></a>Microsoft Defender ATP

### <a name="microsoft-defender-advanced-threat-protection-rules"></a>Regras de proteção avançada contra ameaças do Microsoft defender

- **Exigir que o dispositivo esteja na pontuação de risco do computador ou abaixo**dela:  
  Use essa configuração para realizar a avaliação de risco de seus serviços de ameaça de defesa como uma condição para conformidade. Selecione o nível de ameaça máximo permitido:
  - **Não configurado** (*padrão*)  
  - **Clear** -essa opção é a mais segura, pois o dispositivo não pode ter nenhuma ameaça. Se o dispositivo for detectado como tendo qualquer nível de ameaça, ele será avaliado como não compatível.
  - **Baixo** -o dispositivo será avaliado como compatível se apenas ameaças de nível baixo estiverem presentes. Qualquer nível mais alto coloca o dispositivo num estado de não conforme.
  - **Médio** -o dispositivo será avaliado como em conformidade se as ameaças existentes no dispositivo forem de nível baixo ou médio. Se forem detetadas ameaças de nível alto no dispositivo, este será determinado como não conforme.
  - **Alta** -essa opção é a menos segura e permite todos os níveis de ameaça. Poderá ser útil se utilizar esta solução apenas para fins de relatórios.
  
  Para configurar o Microsoft defender ATP (proteção avançada contra ameaças) como seu serviço de ameaça de defesa, consulte [habilitar o Microsoft defender ATP com acesso condicional](advanced-threat-protection.md).


## <a name="windows-holographic-for-business"></a>Windows Holographic for Business

O Windows Holographic for Business utiliza a plataforma **Windows 10 e posterior**. O Windows Holographic for Business suporta a seguinte definição:

- **Segurança do Sistema** > **Encriptação** > **Encriptação do armazenamento de dados no dispositivo**.

Para verificar a encriptação de dispositivos no Microsoft HoloLens, veja [Verify device encryption (Verificar a encriptação de dispositivos)](https://docs.microsoft.com/hololens/hololens-encryption#verify-device-encryption).

## <a name="surface-hub"></a>Surface Hub

O Surface Hub utiliza a plataforma **Windows 10 e posterior**. Os hubs de superfície têm suporte para conformidade e acesso condicional. Para habilitar esses recursos em Surface hubs, recomendamos que você [habilite o registro automático do Windows 10](../enrollment/windows-enroll.md) no Intune (requer Azure Active Directory (Azure AD)) e direcione os dispositivos Surface Hub como grupos de dispositivos. Os hubs de superfície precisam ser ingressados no Azure AD para que a conformidade e o acesso condicional funcionem.

Para obter diretrizes, consulte [Configurar o registro para dispositivos Windows](../enrollment/windows-enroll.md).

## <a name="next-steps"></a>Próximos passos

- [Adicionar ações para dispositivos não conformes](actions-for-noncompliance.md) e [utilizar etiquetas de âmbito para filtrar políticas](../fundamentals/scope-tags.md).
- [Monitorizar as políticas de conformidade](compliance-policy-monitor.md).
- Consulte as [configurações de política de conformidade para dispositivos Windows 8.1](compliance-policy-create-windows-8-1.md) .
