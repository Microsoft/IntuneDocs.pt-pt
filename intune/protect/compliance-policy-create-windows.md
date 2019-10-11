---
title: Configurações de conformidade do Windows 10 no Microsoft Intune – Azure | Microsoft Docs
description: Consulte uma lista de todas as configurações que você pode usar ao definir a conformidade para seus dispositivos Windows 10, Windows Holographic e Surface Hub no Microsoft Intune. Verifique a conformidade no sistema operacional mínimo e máximo, defina as restrições de senha e o comprimento, verifique as soluções de antivírus (antivírus) do parceiro, habilite a criptografia no armazenamento de dados e muito mais.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/10/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 493db6299aa8242d0ca6ab669b313e85d0dc14c6
ms.sourcegitcommit: b1e97211db7cb949eb39be6776b3a11d434fdab0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/10/2019
ms.locfileid: "72251579"
---
# <a name="windows-10-and-later-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>Configurações do Windows 10 e posteriores para marcar dispositivos como em conformidade ou sem conformidade usando o Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Este artigo lista e descreve as diferentes configurações de conformidade que você pode configurar em dispositivos Windows 10 e posteriores no Intune. Como parte da sua solução de MDM (gerenciamento de dispositivo móvel), use essas configurações para exigir o BitLocker, defina um sistema operacional mínimo e máximo, defina um nível de risco usando a ATP (proteção avançada contra ameaças) do Microsoft defender e muito mais.

Este recurso se aplica a:

- Windows 10 e posterior
- Windows Holographic para empresas
- Surface Hub

Como administrador do Intune, use essas configurações de conformidade para ajudar a proteger seus recursos organizacionais. Para saber mais sobre as políticas de conformidade e o que elas fazem, consulte Introdução [à conformidade do dispositivo](device-compliance-get-started.md).

## <a name="before-you-begin"></a>Antes de começar

[Crie uma política de conformidade](create-compliance-policy.md#create-the-policy). Para **plataforma**, selecione **Windows 10 e posterior**.

## <a name="device-health"></a>Integridade do dispositivo

- **Exigir BitLocker**: quando definido como **exigir**, o dispositivo pode proteger os dados armazenados na unidade contra o acesso não autorizado quando o sistema está desligado ou hibernando. O Windows Criptografia de Unidade de Disco BitLocker criptografa todos os dados armazenados no volume do sistema operacional Windows. O BitLocker usa o TPM para ajudar a proteger o sistema operacional Windows e os dados do usuário. Ele também ajuda a confirmar se um computador não está adulterado, mesmo se ele for deixado em modo autônomo, perdido ou roubado. Se o computador estiver equipado com um TPM compatível, o BitLocker usará o TPM para bloquear as chaves de criptografia que protegem os dados. Como resultado, as chaves não podem ser acessadas até que o TPM Verifique o estado do computador.

  Quando definido como **não configurado** (padrão), essa configuração não é avaliada quanto à conformidade ou à não conformidade.

- **Exigir que a inicialização segura seja habilitada no dispositivo**: quando definida como **exigir**, o sistema é forçado a inicializar para um estado confiável de fábrica. Quando habilitado, os principais componentes usados para inicializar o computador devem ter assinaturas criptográficas corretas que são confiáveis para a organização que fabricou o dispositivo. O firmware UEFI verifica a assinatura antes de permitir que o computador seja iniciado. Se algum arquivo for violado, o que interromperá a assinatura, o sistema não inicializará.

  Quando definido como **não configurado** (padrão), essa configuração não é avaliada quanto à conformidade ou à não conformidade.

  > [!NOTE]
  > O **exigir a inicialização segura a ser habilitada na configuração do dispositivo** tem suporte em alguns dispositivos do TPM 1,2 e 2,0. Para dispositivos que não dão suporte ao TPM 2,0 ou posterior, o status da política no Intune é mostrado como **não compatível**. Para obter mais informações sobre as versões com suporte, consulte [atestado de integridade do dispositivo](https://docs.microsoft.com/windows/security/information-protection/tpm/trusted-platform-module-overview#device-health-attestation).

- **Exigir integridade de código**: a integridade do código é um recurso que valida a integridade de um arquivo do driver ou do sistema sempre que ele é carregado na memória. Quando definido como **exigir**, a integridade de código detecta se um arquivo de sistema ou driver não assinado está sendo carregado no kernel. Ele também detecta se um arquivo do sistema é alterado por software mal-intencionado executado por uma conta de usuário com privilégios de administrador.

  Quando definido como **não configurado** (padrão), essa configuração não é avaliada quanto à conformidade ou à não conformidade.

Mais recursos:

- O [CSP de atestado de integridade](https://docs.microsoft.com/windows/client-management/mdm/healthattestation-csp) tem detalhes sobre como o serviço tem funciona.
- [Dica de suporte: usando configurações de Atestado de Integridade do Dispositivo como parte de sua política de conformidade do Intune](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Using-Device-Health-Attestation-Settings-as-Part-of/ba-p/282643)

## <a name="device-properties"></a>Propriedades do dispositivo

- **Versão mínima do so**: Insira a versão mínima permitida no formato de **número Major.Minor.Build.cu** . Para obter o valor correto, abra um prompt de comando e digite `ver`. O comando `ver` retorna a versão no seguinte formato:

  `Microsoft Windows [Version 10.0.17134.1]`

  Quando um dispositivo tem uma versão anterior à versão do sistema operacional que você insere, ele é relatado como não compatível. É mostrado um link com informações sobre como atualizar. O usuário final pode optar por atualizar seu dispositivo. Após a atualização, eles podem acessar os recursos da empresa.

- **Versão máxima do sistema operacional**: Insira a versão máxima permitida, no formato de **número principal. secundária. Build. Revision** . Para obter o valor correto, abra um prompt de comando e digite `ver`. O comando `ver` retorna a versão no seguinte formato:

  `Microsoft Windows [Version 10.0.17134.1]`

  Quando um dispositivo estiver usando uma versão do sistema operacional posterior à versão inserida, o acesso aos recursos da organização será bloqueado. O usuário final será solicitado a entrar em contato com o administrador de ti. O dispositivo não poderá acessar os recursos da organização até que a regra seja alterada para permitir a versão do sistema operacional.

- **Sistema operacional mínimo necessário para dispositivos móveis**: Insira a versão mínima permitida, no formato de número principal. secundária. Build.

  Quando um dispositivo tem uma versão anterior que a versão do sistema operacional inserida, ele é relatado como não compatível. É mostrado um link com informações sobre como atualizar. O usuário final pode optar por atualizar seu dispositivo. Após a atualização, eles podem acessar os recursos da empresa.

- **Sistema operacional máximo necessário para dispositivos móveis**: Insira a versão máxima permitida, no número principal. secundária. Build.

  Quando um dispositivo estiver usando uma versão do sistema operacional posterior à versão inserida, o acesso aos recursos da organização será bloqueado. O usuário final será solicitado a entrar em contato com o administrador de ti. O dispositivo não poderá acessar os recursos da organização até que a regra seja alterada para permitir a versão do sistema operacional.

- **Compilações de sistema operacional válidas**: Insira um intervalo para as versões de sistemas operacionais aceitáveis, incluindo um mínimo e um máximo. Você também pode **Exportar** uma lista de arquivos CSV (valores separados por vírgula) desses números de compilação de so aceitáveis.

## <a name="configuration-manager-compliance"></a>Conformidade de Configuration Manager

Aplica-se somente a dispositivos cogerenciados que executam o Windows 10 e posterior. Os dispositivos somente do Intune retornam um status não disponível.

- **Exigir conformidade do dispositivo do System Center Configuration Manager**: escolha **exigir** para forçar todas as configurações (itens de configuração) em System Center Configuration Manager para serem compatíveis. 

  Por exemplo, você precisa que todas as atualizações de software sejam instaladas nos dispositivos. Em Configuration Manager, esse requisito tem o estado "instalado". Se algum programa no dispositivo estiver em um estado desconhecido, o dispositivo não será compatível no Intune.
  
  Quando **não configurado**, o Intune não verifica se há configurações de Configuration Manager para fins de conformidade.

## <a name="system-security"></a>Segurança do sistema

### <a name="password"></a>Palavra-passe

- **Exigir uma senha para desbloquear dispositivos móveis**: **exigir** que os usuários insiram uma senha antes que possam acessar seu dispositivo. Quando **não configurado**, o Intune não avalia o dispositivo para as configurações de senha para fins de conformidade.
- **Senhas simples**: Defina como **Bloquear** para que os usuários não possam criar senhas simples, como **1234** ou **1111**. Defina como **não configurado** para permitir que os usuários criem senhas como **1234** ou **1111**.
- **Tipo de senha**: escolha o tipo de senha ou PIN necessário. Suas opções:

  - **Padrão do dispositivo**: requer uma senha, PIN numérico ou PIN alfanumérico
  - **Numeric**: exigir uma senha ou PIN numérico
  - **Alfanumérico**: exigir uma senha ou PIN alfanumérico. Escolha também a **complexidade da senha**: 
    
    - **Exigir dígitos e letras minúsculas**
    - **Exigir dígitos, letras minúsculas e letras maiúsculas**
    - **Exigir dígitos, letras minúsculas, letras maiúsculas e caracteres especiais**

    > [!TIP]
    > As políticas de senha alfanuméricas podem ser complexas. Incentivamos os administradores a ler os CSPs para obter mais informações:
    >
    > - [CSP DeviceLock/AlphanumericDevicePasswordRequired](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-alphanumericdevicepasswordrequired)
    > - [CSP DeviceLock/MinDevicePasswordComplexCharacters](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-mindevicepasswordcomplexcharacters)

- **Comprimento mínimo da senha**: Insira o número mínimo de dígitos ou caracteres que a senha deve ter.
- **Máximo de minutos de inatividade antes que a senha seja exigida**: Insira o tempo ocioso antes que o usuário precise digitar novamente a senha.
- **Expiração da senha (dias)** : Insira o número de dias antes que a senha expire e ela deve criar uma nova, de 1-730.
- **Número de senhas anteriores para evitar a reutilização**: Insira o número de senhas usadas anteriormente que não podem ser usadas.
- **Exigir senha quando o dispositivo retorna do estado ocioso (móvel e Holographic)** : forçar os usuários a inserir a senha sempre que o dispositivo retornar do estado ocioso.

  > [!IMPORTANT]
  > Quando o requisito de senha for alterado em uma área de trabalho do Windows, os usuários serão afetados na próxima vez que entrarem, como é quando o dispositivo vai de ocioso para ativo. Os usuários com senhas que atendem ao requisito ainda são solicitados a alterar suas senhas.

### <a name="encryption"></a>Encriptação

- **Criptografia de armazenamento de dados em um dispositivo**: escolha **exigir** para criptografar o armazenamento de dados em seus dispositivos.

  > [!NOTE]
  > A **criptografia de armazenamento de dados em uma** configuração de dispositivo verifica genericamente a presença de criptografia no dispositivo. Para obter uma configuração de criptografia mais robusta, considere o uso de **exigir BitLocker**, que aproveita o Windows atestado de integridade do dispositivo para validar o status do BitLocker no nível do TPM.

### <a name="device-security"></a>Segurança do dispositivo

- **Firewall**: Defina como **exigir** para ativar o Microsoft defender firewall e impedir que os usuários o desativem. **Não configurado** (padrão) não controla o Microsoft defender firewall nem altera as configurações existentes.

  [CSP do firewall](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp)

  > [!NOTE]
  > Se o dispositivo for sincronizado imediatamente após uma reinicialização ou sincronizar imediatamente a ativação do estado de suspensão, essa configuração poderá ser relatada como um **erro**. Esse cenário pode não afetar o status geral de conformidade do dispositivo. Para reavaliar o status de conformidade, [sincronize manualmente o dispositivo](https://docs.microsoft.com/intune-user-help/sync-your-device-manually-windows).

- **Trusted Platform Module (TPM)** : quando definido como **exigir**, o Intune verifica a compatibilidade da versão. O dispositivo será compatível se a versão do chip do TPM for maior que 0 (zero). O dispositivo não será compatível se não houver uma versão do TPM no dispositivo. Quando **não estiver configurado**, o Intune não verificará o dispositivo em busca de uma versão de chip do TPM.

  [DeviceStatus CSP-DeviceStatus/TPM/nó SpecificationVersion](https://docs.microsoft.com/windows/client-management/mdm/devicestatus-csp)
  
- **Antivírus**: quando definido como **exigir**, você pode verificar a conformidade usando soluções de antivírus registradas com a [central de segurança do Windows](https://blogs.windows.com/windowsexperience/2017/01/23/introducing-windows-defender-security-center/), como Symantec e Microsoft defender. Quando **não configurado**, o Intune não verifica se há soluções antivírus instaladas no dispositivo.
- **AntiSpyware**: quando definido como **exigir**, você pode verificar a conformidade usando soluções AntiSpyware registradas com a [central de segurança do Windows](https://blogs.windows.com/windowsexperience/2017/01/23/introducing-windows-defender-security-center/), como Symantec e Microsoft defender. Quando **não configurado**, o Intune não verifica se há soluções AntiSpyware instaladas no dispositivo.

### <a name="defender"></a>Defender

- **Microsoft Defender Antimalware**: Defina como **exigir** para ativar o serviço antimalware do Microsoft defender e impedir que os usuários o desativem. **Não configurado** (padrão) não controla o serviço nem altera as configurações existentes.
- **Versão mínima do Microsoft Defender Antimalware**: Insira a versão mínima permitida do serviço antimalware do Microsoft defender. Por exemplo, introduza `4.11.0.0`. Quando deixado em branco, qualquer versão do serviço antimalware do Microsoft defender pode ser usada.
- **Inteligência de segurança antimalware do Microsoft defender atualizada**: controla as atualizações de proteção contra ameaças e vírus de segurança do Windows nos dispositivos. **Exigir** força a inteligência de segurança do Microsoft defender a ser atualizada. **Não configurado** (padrão) não impõe nenhum requisito.

  [As atualizações de inteligência de segurança para o Microsoft defender antivírus e outros antimalware da Microsoft](https://www.microsoft.com/en-us/wdsi/defenderupdates) têm mais informações sobre a inteligência de segurança.

- **Proteção em tempo real**: **requer** a habilitação da proteção em tempo real, que verifica o malware, spyware e outros softwares indesejados. **Não configurado** (padrão) não controla esse recurso, nem altera as configurações existentes.

  [CSP do defender/AllowRealtimeMonitoring](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowrealtimemonitoring)

## <a name="microsoft-defender-atp"></a>Microsoft Defender ATP

- **Exigir que o dispositivo esteja na pontuação de risco do computador ou abaixo**dela: Use essa configuração para realizar a avaliação de risco dos serviços de ameaça de defesa como uma condição para conformidade. Escolha o nível máximo de ameaça permitido:

  - **Clear**: essa opção é a mais segura, pois o dispositivo não pode ter nenhuma ameaça. Se o dispositivo for detectado como tendo qualquer nível de ameaça, ele será avaliado como não compatível.
  - **Baixo**: o dispositivo será avaliado como em conformidade se apenas ameaças de nível baixo estiverem presentes. Qualquer coisa superior coloca o dispositivo em um status de não conformidade.
  - **Médio**: o dispositivo será avaliado como em conformidade se as ameaças existentes no dispositivo forem de nível baixo ou médio. Se for detectado que o dispositivo tem ameaças de alto nível, ele será determinado como não compatível.
  - **Alta**: essa opção é a menos segura e permite todos os níveis de ameaça. Pode ser útil se você estiver usando essa solução somente para fins de relatório.
  
  Para configurar o Microsoft defender ATP (proteção avançada contra ameaças) como seu serviço de ameaça de defesa, consulte [habilitar o Microsoft defender ATP com acesso condicional](advanced-threat-protection.md).

Selecione **OK** > **criar** para salvar suas alterações.

## <a name="windows-holographic-for-business"></a>Windows Holographic para empresas

O Windows Holographic for Business usa a plataforma **Windows 10 e posterior** . O Windows Holographic for Business dá suporte à seguinte configuração:

- **Segurança do sistema** > **criptografia** > **de armazenamento de dados no dispositivo**.

Para verificar a criptografia do dispositivo no Microsoft HoloLens, consulte [verificar criptografia do dispositivo](https://docs.microsoft.com/hololens/hololens-encryption#verify-device-encryption).

## <a name="surface-hub"></a>Surface Hub

Surface Hub usa a plataforma **Windows 10 e posterior** . Os hubs de superfície têm suporte para conformidade e acesso condicional. Para habilitar esses recursos em Surface hubs, recomendamos que você [habilite o registro automático do Windows 10](../enrollment/windows-enroll.md) no Intune (requer Azure Active Directory (Azure AD)) e direcione os dispositivos Surface Hub como grupos de dispositivos. Os hubs de superfície precisam ser ingressados no Azure AD para que a conformidade e o acesso condicional funcionem.

Consulte [Configurar o registro para dispositivos Windows](../enrollment/windows-enroll.md) para obter diretrizes.

## <a name="next-steps"></a>Passos seguintes

- [Adicione ações para dispositivos não compatíveis](actions-for-noncompliance.md) e [use marcas de escopo para filtrar políticas](../fundamentals/scope-tags.md).
- [Monitore suas políticas de conformidade](compliance-policy-monitor.md).
- Consulte as [configurações de política de conformidade para dispositivos Windows 8.1](compliance-policy-create-windows-8-1.md) .
