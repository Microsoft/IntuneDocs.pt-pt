---
title: Definições de conformidade do Windows 10 no Microsoft Intune - Azure Microsoft Docs
description: Consulte uma lista de todas as definições que pode utilizar ao definir a conformidade com os dispositivos Windows 10, Windows Holographic e Surface Hub no Microsoft Intune. Verifique a conformidade com o sistema operativo mínimo e máximo, delineie restrições e comprimento de senha, verifique se existem soluções antivírus parceiros (AV), permita a encriptação no armazenamento de dados e muito mais.
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
ms.openlocfilehash: e0fb33748c5bd21ca8997e2195ba0b7d71f4f6f9
ms.sourcegitcommit: 25e4847ead0f56c269cfefe1e01c1b9106a28cf1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/06/2020
ms.locfileid: "78856124"
---
# <a name="windows-10-and-later-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>Windows 10 e posteriordefinições para marcar dispositivos como conformes ou não conformes usando Intune

Este artigo lista e descreve as diferentes definições de conformidade que pode configurar no Windows 10 e posteriormente em Dispositivos Intune. Como parte da sua solução de gestão de dispositivos móveis (MDM), utilize estas definições para exigir o BitLocker, definir um sistema operativo mínimo e máximo, definir um nível de risco utilizando a Proteção avançada de ameaças (ATP) do Microsoft Defender, e muito mais.

Esta funcionalidade aplica-se a:

- Windows 10 e posterior
- Windows Holographic for Business
- Surface Hub

Enquanto administrador do Intune, utilize estas definições de conformidade para ajudar a proteger os recursos da sua organização. Para saber mais sobre as políticas de conformidade e para o que servem, veja a [introdução à conformidade de dispositivos](device-compliance-get-started.md).

## <a name="before-you-begin"></a>Antes de começar

[Criar uma política de conformidade](create-compliance-policy.md#create-the-policy). Em **Plataforma**, selecione **Windows 10 e versões posteriores**.

## <a name="device-health"></a>Estado de Funcionamento do Dispositivo

### <a name="windows-health-attestation-service-evaluation-rules"></a>Regras de avaliação do Serviço de Attestation saúde do Windows

- **Requerer bitLocker**:  
   A Encriptação de Unidade BitLocker do Windows encripta todos os dados armazenados no volume do sistema operativo Windows. O BitLocker utiliza o Módulo de Plataforma Fidedigna (TPM) para ajudar a proteger o sistema operativo Windows e os dados do utilizador. Também ajuda a confirmar que um computador não é adulterado, mesmo que a sua esquerda não seja vigiada, perdida ou roubada. Se o computador estiver equipado com um TPM compatível, o BitLocker utiliza o TPM para bloquear as chaves de encriptação que protegem os dados. Como resultado, as chaves não podem ser acedidas até que o TPM verifique o estado do computador.  

   - **Não configurado** *(predefinido)* - Esta definição não é avaliada para conformidade ou incumprimento.
   - **Require** - O dispositivo pode proteger os dados armazenados na unidade de acesso não autorizado quando o sistema está desligado, ou hiberna.  


- **Exigir que a Bota Segura esteja ativada no dispositivo:**  
    - **Não configurado** *(predefinido)* - Esta definição não é avaliada para conformidade ou incumprimento.
    - **Require** - O sistema é forçado a iniciar um estado de confiança na fábrica. Os componentes centrais utilizados para o arranque da máquina devem ter assinaturas criptográficas corretas que são fidedignas pela organização que fabricou o dispositivo. O firmware UEFI verifica a assinatura antes de permitir que o computador seja iniciado. Se algum ficheiro for adulterado, o que quebra a sua assinatura, o sistema não arranca.

  > [!NOTE]
  > A **Bota Segura Requerer ativada na** definição do dispositivo é suportada em alguns dispositivos TPM 1.2 e 2.0. Para os dispositivos que não suportam o TPM 2.0 ou posterior, o estado da política no Intune é mostrado como **Não Conforme**. Para obter mais informações sobre versões suportadas, consulte [Attestation de Saúde do Dispositivo](https://docs.microsoft.com/windows/security/information-protection/tpm/trusted-platform-module-overview#device-health-attestation).

- **Requerer a integridade do código:**  
  A integridade do código é uma funcionalidade que valida a integridade de um ficheiro de controlador ou sistema cada vez que é carregado na memória.
  - **Não configurado** *(predefinido)* - Esta definição não é avaliada para conformidade ou incumprimento.
  -  **Require** - Exija a integridade do código, que deteta se um controlador ou ficheiro do sistema não assinado está a ser carregado no núcleo. Também deteta se um ficheiro de sistema é alterado por software malicioso ou executado por uma conta de utilizador com privilégios de administrador.

Mais recursos:

- Para mais detalhes sobre como funciona o serviço de Attestation Health, consulte [Health Attestation CSP](https://docs.microsoft.com/windows/client-management/mdm/healthattestation-csp).
- [Dica de suporte: Utilizando as definições de atestado de saúde do dispositivo como parte da sua política de conformidade intune](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Using-Device-Health-Attestation-Settings-as-Part-of/ba-p/282643).

## <a name="device-properties"></a>Propriedades do Dispositivo

### <a name="operating-system-version"></a>Versão do Sistema Operativo

- **Versão mínima do SO**:  
  Introduza a versão mínima permitida no formato **número major.minor.build.CU.** Para obter o valor correto, abra uma linha de comandos e escreva `ver`. O comando `ver` devolve a versão no seguinte formato:

  `Microsoft Windows [Version 10.0.17134.1]`

  Quando um dispositivo tem uma versão anterior do que a versão S em que entra, é reportado como incompatível. É apresentada uma hiperligação com informações sobre como atualizar. O utilizador final pode optar por atualizar o dispositivo. Depois de atualizarem, podem aceder aos recursos da empresa.

- **Versão máxima do SO**:  
  Introduza a versão máxima permitida, no formato **número major.minor.build.revision.** Para obter o valor correto, abra uma linha de comandos e escreva `ver`. O comando `ver` devolve a versão no seguinte formato:

  `Microsoft Windows [Version 10.0.17134.1]`

  Quando um dispositivo está a usar uma versão S mais tarde do que a versão introduzida, o acesso aos recursos da organização é bloqueado. É pedido ao utilizador final para contactar o administrador de TI. O dispositivo não pode aceder aos recursos da organização até que a regra seja alterada para permitir a versão S.

- **Sistema mínimo de sotabilidade exigido para dispositivos móveis:**  
  Introduza a versão mínima permitida, no formato número major.minor.build.

  Quando um dispositivo tem uma versão anterior em que a versão S em que entra, é reportado como incompatível. É apresentada uma hiperligação com informações sobre como atualizar. O utilizador final pode optar por atualizar o dispositivo. Depois de atualizarem, podem aceder aos recursos da empresa.

- **Os máximos necessários para dispositivos móveis:**  
  Introduza a versão máxima permitida, no número maior.minor.build.

  Quando um dispositivo está a usar uma versão S mais tarde do que a versão introduzida, o acesso aos recursos da organização é bloqueado. É pedido ao utilizador final para contactar o administrador de TI. O dispositivo não pode aceder aos recursos da organização até que a regra seja alterada para permitir a versão S.

- **Sistema operativo válido constrói:**  
  Introduza uma gama para as versões aceitáveis dos sistemas operativos, incluindo um mínimo e máximo. Também pode **Exportar** uma lista de ficheiros de valores separados por vírgulas (CSV) destes números de compilação de SO aceitáveis.

## <a name="configuration-manager-compliance"></a>Conformidade do Gestor de Configuração

Aplica-se apenas a dispositivos cogeridos que executam o Windows 10 e posteriormente. Os dispositivos intune devolvem um estado não disponível.

- Exigir a **conformidade do dispositivo com o Gestor de Configuração:**  
  - **Não configurado** *(predefinido)* - Intune não verifica se há nenhuma das definições do Gestor de Configuração para a conformidade.
  - **Require** - Exija que todas as definições (itens de configuração) no Gestor de Configuração sejam conformes.  

    Por exemplo, pode exigir que todas as atualizações do software sejam instaladas nos dispositivos. No Gestor de Configuração, este requisito tem o estado "Instalado". Se algum programa no dispositivo estiver num estado desconhecido, então o dispositivo não está em conformidade no Intune.

## <a name="system-security"></a>Segurança do sistema

### <a name="password"></a>Palavra-passe

- **Exigir uma palavra-passe para desbloquear os dispositivos móveis**:  
  - **Não configurado** *(predefinido)* - Esta definição não é avaliada para conformidade ou incumprimento.
  - **Exigir** - Os utilizadores devem introduzir uma palavra-passe antes de poderem aceder ao seu dispositivo. 

- **Palavras-passe simples**:  
  - **Não configurado** *(predefinido)* - Os utilizadores podem criar senhas simples, tais como **1234** ou **1111**.
  - **Bloco** - Os utilizadores não podem criar senhas simples, tais como **1234** ou **1111**.

- **Tipo de palavra-passe**:  
  Escolha o tipo de senha ou PIN necessário. As opções são:
  - **Predefinição do dispositivo** *(predefinição*) - Requeira uma palavra-passe, PIN numérico ou PIN alfanumérico
  - **Numérico** - Exija uma palavra-passe ou PIN numérico
  - **Alfanumérico** - Exija uma palavra-passe, ou PIN alfanumérico.  
  
  Quando definido para *Alphanumérico,* estão disponíveis as seguintes definições:  
  - **Complexidade da palavra-passe:**  
    As opções são: 
    - **Requerer dígitos e letras minúsculas** *(padrão)*
    - **Requerem dígitos, letras minúsculas e letras maiúsculas**
    - **Requerem dígitos, letras minúsculas, letras maiúsculas e caracteres especiais**

    > [!TIP]
    > As políticas alfanuméricas de senha podem ser complexas. Encorajamos os administradores a ler os CSPs para obter mais informações:
    >
    > - [DeviceLock/AlphanumericDevicePasswordSRequired CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-alphanumericdevicepasswordrequired)
    > - [DeviceLock/MinDevicePasswordComplexCharacters CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-mindevicepasswordcomplexcharacters)

- **Comprimento mínimo da palavra-passe**:  
  introduza o número mínimo de dígitos ou carateres que a palavra-passe tem de ter.

- **Minutos de inatividade antes de a palavra-passe ser exigida**:  
  introduza o tempo de inatividade antes de o utilizador ter de reintroduzir a palavra-passe.

- **Expiração da palavra-passe (dias)** :  
  Insira o número de dias antes de a palavra-passe expirar, e devem criar uma nova, de 1-730.

- **Número de palavras-passe anteriores para impedir a reutilização**:  
  introduza o número de palavras-passe utilizadas anteriormente que não podem ser utilizadas.

- **Exija uma palavra-passe quando o dispositivo regressar do estado inativo (Móvel e Holográfico)** :  
  - **Não configurado** *(predefinido)*
  - **Require** - Exija que os utilizadores do dispositivo introduzam a palavra-passe sempre que o dispositivo retorna de um estado inativo.

  > [!IMPORTANT]
  > Quando o requisito da palavra-passe é alterado num ambiente de trabalho do Windows, os utilizadores são impactados da próxima vez que iniciarem o seu inatividade, pois é aí que o dispositivo passa de inativo para ativo. Os utilizadores com senhas que cumpram o requisito ainda são solicitados a alterar as suas palavras-passe.

### <a name="encryption"></a>Encriptação

- **Encriptação do armazenamento de dados num dispositivo**:  
  Esta definição aplica-se a todas as unidades de um dispositivo.
  - **Não configurado** *(predefinido)*
  - **Exigir** - Utilizar *o Necessário* para encriptar o armazenamento de dados nos seus dispositivos.

  > [!NOTE]
  > A definição **Encriptação do armazenamento de dados num dispositivo** verifica genericamente a presença de encriptação no dispositivo. Para uma definição de encriptação mais avançada, considere utilizar **Exigir o BitLocker**, que tira partido do Windows Device Health Attestation para validar o estado do Bitlocker ao nível do TPM.

### <a name="device-security"></a>Segurança do Dispositivo  

- **Firewall**:  
  - **Não configurado** *(predefinido)* - Intune não controla o Microsoft Defender Firewall, nem altera as definições existentes.
  - **Require** - Ligue o Microsoft Defender Firewall e evite que os utilizadores o desliguem.  

  [Firewall CSP](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp)

  > [!NOTE]
  > Se o dispositivo sincronizar imediatamente após um reboot, ou sincronizar imediatamente o sono, então esta definição pode reportar como um **Erro**. Este cenário pode não afetar o estado geral de conformidade do dispositivo. Para reavaliar o estado de conformidade, [sincronize](https://docs.microsoft.com/intune-user-help/sync-your-device-manually-windows)manualmente o dispositivo .

- **Módulo de Plataforma Fidedigna (TPM)** :  
  - **Não configurado** *(predefinido)* - Intune não verifica o dispositivo para uma versão de chip TPM.
  - **Require** - Intune verifica a versão do chip TPM para conformidade. O dispositivo está em conformidade se a versão do chip TPM for superior a **0** (zero). O dispositivo não é compatível se não houver uma versão TPM no dispositivo.  

  [DispositivoStatus CSP - DispositivoStatus/TPM/Caderno de versão de especificação](https://docs.microsoft.com/windows/client-management/mdm/devicestatus-csp)
  
- **Antivírus**:  
  - **Não configurado** *(predefinido)* - Intune não verifica se existem soluções antivírus instaladas no dispositivo. 
  - **Require** - Verifique a conformidade utilizando soluções antivírus que estejam registadas no [Windows Security Center](https://blogs.windows.com/windowsexperience/2017/01/23/introducing-windows-defender-security-center/), como o Symantec e o Microsoft Defender.

- **Antispyware:**  
  - **Não configurado** *(predefinido)* - Intune não verifica se existem soluções antispyware instaladas no dispositivo.
  - **Require** - Verifique a conformidade utilizando soluções antispyware que estejam registadas no [Windows Security Center](https://blogs.windows.com/windowsexperience/2017/01/23/introducing-windows-defender-security-center/), como o Symantec e o Microsoft Defender.  

### <a name="defender"></a>Defender

*As seguintes definições de conformidade são suportadas com o Windows 10 Desktop.*

- **Microsoft Defender Antimalware**:  
  - **Não configurado** *(predefinido)* - Intune não controla o serviço, nem altera as definições existentes.
  - **Require** - Ligue o serviço anti-malware Microsoft Defender e evite que os utilizadores o desliguem.

- **Versão mínima do Microsoft Defender Antimalware:**  
  Introduza a versão mínima permitida do serviço anti-malware Microsoft Defender. Por exemplo, introduza `4.11.0.0`. Quando deixada em branco, qualquer versão do serviço anti-malware Microsoft Defender pode ser utilizada.  

  *Por defeito, nenhuma versão está configurada.*

- Inteligência de **segurança Antimalware Microsoft Defender**atualizado:  
  Controla as atualizações de proteção contra vírus do Windows Security e de proteção contra ameaças nos dispositivos.
  - **Não configurado** *(predefinido)* - Intune não impõe quaisquer requisitos.
  - **Require** - Force a inteligência de segurança do Microsoft Defender a estar atualizada.

  [Defender/Saúde/SignatureOutOfDate CSP](https://docs.microsoft.com/windows/client-management/mdm/defender-csp)
  
  Para mais informações, consulte [as atualizações de inteligência de Segurança para o Antivírus](https://www.microsoft.com/en-us/wdsi/defenderupdates)do Microsoft Defender e outros antimalware da Microsoft .

- **Proteção em tempo real:**  
  - **Não configurado** *(predefinido)* - Intune não controla esta funcionalidade, nem altera as definições existentes.
  - **Require** - Ligue a proteção em tempo real, que procura malware, spyware e outros softwares indesejados.  

  [Defender/Permitir Monitorização Real](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowrealtimemonitoring)

## <a name="microsoft-defender-atp"></a>Microsoft Defender ATP

### <a name="microsoft-defender-advanced-threat-protection-rules"></a>Regras avançadas de proteção contra ameaças do Microsoft Defender

- **Exigir que o dispositivo esteja na pontuação de risco da máquina:**  
  Utilize esta configuração para fazer a avaliação de risco dos seus serviços de ameaça de defesa como condição para o cumprimento. Selecione o nível de ameaça máximo permitido:
  - **Não configurado** *(predefinido)*  
  - **Clear** - Esta opção é a mais segura, uma vez que o dispositivo não pode ter ameaças. Se o dispositivo for detetado como tendo qualquer nível de ameaça, é avaliado como não conforme.
  - **Baixo** - O dispositivo é avaliado como conforme se apenas houver ameaças de baixo nível. Qualquer nível mais alto coloca o dispositivo num estado de não conforme.
  - **Médio** - O dispositivo é avaliado como conforme se as ameaças existentes no dispositivo forem de baixo ou médio nível. Se forem detetadas ameaças de nível alto no dispositivo, este será determinado como não conforme.
  - **Alta** - Esta opção é a menos segura, e permite todos os níveis de ameaça. Poderá ser útil se utilizar esta solução apenas para fins de relatórios.
  
  Para configurar o Microsoft Defender ATP (Advanced Threat Protection) como serviço de ameaça de defesa, consulte [Enable Microsoft Defender ATP com acesso condicional](advanced-threat-protection.md).


## <a name="windows-holographic-for-business"></a>Windows Holographic for Business

O Windows Holographic for Business utiliza a plataforma **Windows 10 e posterior**. O Windows Holographic for Business suporta a seguinte definição:

- **Segurança do Sistema** > **Encriptação** > **Encriptação do armazenamento de dados no dispositivo**.

Para verificar a encriptação de dispositivos no Microsoft HoloLens, veja [Verify device encryption (Verificar a encriptação de dispositivos)](https://docs.microsoft.com/hololens/hololens-encryption#verify-device-encryption).

## <a name="surface-hub"></a>Surface Hub

O Surface Hub utiliza a plataforma **Windows 10 e posterior**. Os Surface Hubs são suportados tanto para a conformidade como para o Acesso Condicional. Para ativar estas funcionalidades nos Surface Hubs, recomendamos que ative a [inscrição automática do Windows 10](../enrollment/windows-enroll.md) em Intune (requer o Azure Ative Directory (Azure AD)) e direcione os dispositivos Surface Hub como grupos de dispositivos. Os Surface Hubs são necessários para serem Azure AD unidos para o cumprimento e acesso condicional ao trabalho.

Para obter orientação, consulte [a configuração da inscrição para dispositivos Windows](../enrollment/windows-enroll.md).

## <a name="next-steps"></a>Próximos passos

- [Adicionar ações para dispositivos não conformes](actions-for-noncompliance.md) e [utilizar etiquetas de âmbito para filtrar políticas](../fundamentals/scope-tags.md).
- [Monitorizar as políticas de conformidade](compliance-policy-monitor.md).
- Consulte as definições da política de conformidade para dispositivos [Windows 8.1.](compliance-policy-create-windows-8-1.md)
