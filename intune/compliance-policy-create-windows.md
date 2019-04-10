---
title: Definições de compatibilidade do Windows 10 no Microsoft Intune – Azure | Documentos da Microsoft
description: Ver uma lista de todas as definições que pode utilizar quando a definição de conformidade para os seus dispositivos Windows 10, Windows Holographic e Surface Hub no Microsoft Intune. Verificar a conformidade do mínimo e máximo do sistema operativo, de definir restrições de palavra-passe e de comprimento, verifique a existência de soluções de (AV) de software antivírus de parceiros, ativar a encriptação em armazenamento de dados e muito mais.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/04/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8d956526d483a74ca5929180a48ea2dcd8b3eab7
ms.sourcegitcommit: 02803863eba37ecf3d8823a7f1cd7c4f8e3bb42c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2019
ms.locfileid: "59423633"
---
# <a name="windows-10-and-later-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>Definições Windows 10 e posteriores para marcar dispositivos como compatíveis ou não compatíveis com o Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Este artigo apresenta e descreve as definições de conformidade diferentes que pode configurar no Windows 10 e dispositivos posteriores no Intune. Como parte da sua solução de gestão (MDM) de dispositivos móveis, utilize estas definições para exigir o BitLocker, defina um sistema de operativo mínima e máxima, defina um nível de risco com a proteção de ameaças avançada do Windows Defender (ATP) e muito mais.

Esta funcionalidade aplica-se a:

- Windows 10 e posterior
- Windows Holographic for Business
- Surface Hub

Enquanto administrador do Intune, utilize estas definições de conformidade para ajudar a proteger recursos da sua organização. Para saber mais sobre as políticas de conformidade e o que fazer, consulte [introdução à conformidade de dispositivo](device-compliance-get-started.md).

## <a name="before-you-begin"></a>Antes de começar

[Criar uma política de conformidade](create-compliance-policy.md#create-the-policy). Em **Plataforma**, selecione **Windows 10 e versões posteriores**.

## <a name="device-health"></a>Device health

- **Exigir o BitLocker**: Quando definido como **requerem**, o dispositivo pode proteger os dados armazenados na unidade contra acesso não autorizado, quando o sistema está desativado ou hiberna. A Encriptação de Unidade BitLocker do Windows encripta todos os dados armazenados no volume do sistema operativo Windows. O BitLocker utiliza o TPM para ajudar a proteger o sistema operativo Windows e os dados de utilizador. Ele também ajuda a confirmar que um computador não estiver adulterado, mesmo que sua esquerda autônoma, perda ou roubo. Se os computadores estiverem equipados com um TPM compatível, o BitLocker utiliza o TPM para bloquear as chaves de encriptação que protegem os dados. Como resultado, as chaves não podem ser acedidas até que o TPM verifica o estado do computador.

  Quando definido como **não configurado** (predefinição), esta definição não é avaliada de conformidade ou de não conformidade.

- **Exigir que o arranque seguro seja ativado no dispositivo**: Quando definido como **requerem**, o sistema é forçado a efetuar o arranque para um Estado de fábrica fidedigno. Quando ativada, os componentes do núcleo utilizados para arrancar o computador tem de ter assinaturas criptográficas corretas e que sejam consideradas fidedignas pela organização que fabricou o dispositivo. O firmware UEFI verifica a assinatura antes de permitir que o computador seja iniciado. Se todos os ficheiros são adulterados, que quebra a respetiva assinatura, o sistema não arranque.

  Quando definido como **não configurado** (predefinição), esta definição não é avaliada de conformidade ou de não conformidade.

  > [!NOTE]
  > O **necessitam de arranque seguro seja ativado no dispositivo** definição é suportada em alguns TPM 1.2 e 2.0 dispositivos. Para os dispositivos que não suportam o TPM 2.0 ou posterior, o estado da política no Intune é mostrado como **Não Conforme**. Para obter mais informações sobre as versões suportadas, consulte [atestado de estado de funcionamento do dispositivo](https://docs.microsoft.com/windows/security/information-protection/tpm/trusted-platform-module-overview#device-health-attestation).

- **Exigir integridade de código**: Integridade do código é uma funcionalidade que valida a integridade de um ficheiro de controlador ou de sistema sempre que é carregado na memória. Quando definido como **requerem**, integridade do código Deteta se um controlador não assinado ou o sistema está a ser carregado para o kernel. Também Deteta se um ficheiro de sistema é alterações por software malicioso executado por uma conta de utilizador com privilégios de administrador.

  Quando definido como **não configurado** (predefinição), esta definição não é avaliada de conformidade ou de não conformidade.

Mais recursos:

- [CSP de atestado de estado de funcionamento](https://docs.microsoft.com/windows/client-management/mdm/healthattestation-csp) contém os detalhes sobre como funciona o serviço HAS.
- [Sugestão de suporte: Utilizar definições de atestado de estado de funcionamento do dispositivo como parte da sua política de conformidade do Intune ](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Using-Device-Health-Attestation-Settings-as-Part-of/ba-p/282643)

## <a name="device-properties"></a>Propriedades do dispositivo

- **Versão mínima do SO**: Introduza a versão mínima permitida no **número major.minor.build.CU** formato. Para obter o valor correto, abra uma linha de comandos e escreva `ver`. O comando `ver` devolve a versão no seguinte formato:

  `Microsoft Windows [Version 10.0.17134.1]`

  Quando um dispositivo tem uma versão anterior à versão de SO, introduzir, será comunicado como não conforme. É apresentada uma hiperligação com informações sobre como atualizar. O utilizador final pode optar por atualizar o dispositivo. Após a atualização, podem aceder a recursos da empresa.

- **Versão do SO máxima**: Introduza o máximo permitido de versão, no **número major** formato. Para obter o valor correto, abra uma linha de comandos e escreva `ver`. O comando `ver` devolve a versão no seguinte formato:

  `Microsoft Windows [Version 10.0.17134.1]`

  Quando um dispositivo utiliza uma versão do SO posterior à versão introduzida, acesso aos recursos da organização é bloqueado. O utilizador final é pedido que contacte o administrador de TI. O dispositivo não é possível aceder aos recursos de organização, até que a regra seja alterada para permitir que a versão do SO.

- **SO mínimo obrigatório para dispositivos móveis**: Introduza o mínimo de versão, no formato de número major.

  Quando um dispositivo tem uma versão anterior que a versão do SO introduzir, será comunicado como não conforme. É apresentada uma hiperligação com informações sobre como atualizar. O utilizador final pode optar por atualizar o dispositivo. Após a atualização, podem aceder a recursos da empresa.

- **SO máximo obrigatório para dispositivos móveis**: Introduza o máximo permitido de versão, o número major.

  Quando um dispositivo utiliza uma versão do SO posterior à versão introduzida, acesso aos recursos da organização é bloqueado. O utilizador final é pedido que contacte o administrador de TI. O dispositivo não é possível aceder aos recursos de organização, até que a regra seja alterada para permitir que a versão do SO.

- **Compilações válidas do sistema operativo**: Introduza um intervalo para as versões de sistemas operativos aceitáveis, incluindo um mínimo e máximo. Também pode **Exportar** uma lista de ficheiros de valores separados por vírgulas (CSV) destes números de compilação de SO aceitáveis.

## <a name="configuration-manager-compliance"></a>Compatibilidade do Configuration Manager

Aplica-se apenas a dispositivos cogeridos com Windows 10 e posterior. Dispositivos apenas o Intune devolvem um Estado não está disponível.

- **Exigir conformidade do dispositivo do System Center Configuration Manager**: Escolher **requerem** para forçar a todas as definições (itens de configuração) no System Center Configuration Manager, para estar em conformidade. 

  Por exemplo, pode exigir que todas as atualizações do software sejam instaladas nos dispositivos. No Configuration Manager, este requisito apresenta o estado "Instalado". Se todos os programas no dispositivo estão num Estado desconhecido, em seguida, o dispositivo está em conformidade no Intune.
  
  Quando **não configurado**, o Intune não verifica para qualquer uma das definições de compatibilidade do Configuration Manager.

## <a name="system-security"></a>Segurança do sistema

### <a name="password"></a>Palavra-passe

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

### <a name="encryption"></a>Encriptação

- **Encriptação do armazenamento de dados num dispositivo de**: Escolher **requerem** para encriptar o armazenamento de dados nos seus dispositivos.

  > [!NOTE]
  > A definição **Encriptação do armazenamento de dados num dispositivo** verifica genericamente a presença de encriptação no dispositivo. Para uma definição de encriptação mais avançada, considere utilizar **Exigir o BitLocker**, que tira partido do Windows Device Health Attestation para validar o estado do Bitlocker ao nível do TPM.

### <a name="device-security"></a>Segurança do Dispositivo

- **Antivírus**: Quando definido como **requerem**, pode verificar a conformidade com as soluções antivírus que estão registadas [Centro de segurança do Windows](https://blogs.windows.com/windowsexperience/2017/01/23/introducing-windows-defender-security-center/), por exemplo, Symantec e o Windows Defender. Quando estiver definido como **Não configurado**, o Intune não verifica a existência de soluções AV instaladas no dispositivo.
- **AntiSpyware**: Quando definido como **requerem**, pode verificar conformidade através de soluções de anti-spyware que estão registadas [Centro de segurança do Windows](https://blogs.windows.com/windowsexperience/2017/01/23/introducing-windows-defender-security-center/), por exemplo, Symantec e o Windows Defender. Quando estiver definido como **Não configurado**, o Intune não verifica a existência de soluções de AntiSpyware instaladas no dispositivo.

## <a name="windows-defender-atp"></a>Windows Defender ATP

- **Exigir que o dispositivo estar ou sob a classificação de risco de máquina**: Utilize esta definição para assumir a avaliação de risco de defesa contra os serviços de ameaças como uma condição para conformidade. Selecione o nível de ameaça máximo permitido:

  - **Limpar**: Esta opção é a mais segura, uma vez que o dispositivo não pode ter qualquer ameaça. Se o dispositivo detetar qualquer nível de ameaças, é avaliado como não conforme.
  - **Baixa**: O dispositivo é avaliado como conforme se só estiverem presentes ameaças de nível baixo. Qualquer nível mais alto coloca o dispositivo num estado de não conforme.
  - **Médio**: O dispositivo é avaliado como conforme se as ameaças existentes no dispositivo forem de nível baixo ou médio. Se o dispositivo forem detectado ameaças de nível alto, este tem determinado como não conforme.
  - **Alta**: Esta opção é menos segura e permite todos os níveis de ameaça. Poderá ser útil se utilizar esta solução apenas para fins de relatórios.
  
  Para configurar o Windows Defender ATP (Proteção Avançada Contra Ameaças) como o seu serviço de defesa contra ameaças, veja [Ativar o Windows Defender ATP com acesso condicional](advanced-threat-protection.md).

Selecione **OK** > **Criar** para guardar as alterações.

## <a name="windows-holographic-for-business"></a>Windows Holographic for Business

O Windows Holographic for Business utiliza a plataforma **Windows 10 e posterior**. O Windows Holographic for Business suporta a seguinte definição:

- **Segurança do Sistema** > **Encriptação** > **Encriptação do armazenamento de dados no dispositivo**.

Para verificar a encriptação de dispositivos no Microsoft HoloLens, veja [Verify device encryption (Verificar a encriptação de dispositivos)](https://docs.microsoft.com/hololens/hololens-encryption#verify-device-encryption).

## <a name="surface-hub"></a>Surface Hub

O Surface Hub utiliza a plataforma **Windows 10 e posterior**. Os Surface Hubs são suportados para o acesso condicional e a conformidade. Para ativar estas funcionalidades nos Surface Hubs, recomendamos que [ativar a inscrição automática do Windows 10](windows-enroll.md) no Intune (requer o Azure Active Directory (Azure AD)) e os dispositivos Surface Hub como grupos de dispositivos de destino. Os Surface Hubs têm de ser associados ao Azure AD para conformidade e acesso condicional funcionar.

Veja [configurar a inscrição para dispositivos Windows](windows-enroll.md) para obter orientações.

## <a name="next-steps"></a>Passos Seguintes

- [Adicionar ações para dispositivos não conformes](actions-for-noncompliance.md) e [utilizar etiquetas de âmbito para políticas de filtro](scope-tags.md).
- [Monitorizar as suas políticas de conformidade](compliance-policy-monitor.md).
- Consulte a [definições de política de conformidade para Windows 8.1](compliance-policy-create-windows-8-1.md) dispositivos.