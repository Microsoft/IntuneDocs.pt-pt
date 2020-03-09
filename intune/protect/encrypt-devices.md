---
title: Criptografia dispositivos com o método de encriptação suportado pelas plataformas
titleSuffix: Microsoft Intune
description: Criptografe dispositivos com métodos de encriptação incorporados como BitLocker ou FileVault, e gere as chaves de recuperação para esses dispositivos encriptados dentro do portal Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/03/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: annovich
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: a2b988af00ce1ab5b9fa4e664d09b383403bd002
ms.sourcegitcommit: 25e4847ead0f56c269cfefe1e01c1b9106a28cf1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/05/2020
ms.locfileid: "78368489"
---
# <a name="use-device-encryption-with-intune"></a>Utilizar encriptação do dispositivo com Intune

Utilize o Intune para gerir um disco incorporado ou conduzir encriptação para proteger dados dos seus dispositivos.

Configure a encriptação do disco como parte de um perfil de configuração do dispositivo para proteção de pontofinal. As seguintes plataformas e tecnologias de encriptação são suportadas pela Intune:

- macOS: FileVault
- Windows 10 e mais tarde: BitLocker

Intune também fornece um relatório de [encriptação](encryption-monitor.md) incorporado que apresenta detalhes sobre o estado de encriptação dos dispositivos, em todos os seus dispositivos geridos.

## <a name="filevault-encryption-for-macos"></a>Encriptação FileVault para macOS

Utilize insinopara configurar a encriptação do disco FileVault em dispositivos que executam o macOS. Em seguida, utilize o relatório de encriptação Intune para visualizar detalhes de encriptação desses dispositivos e para gerir as chaves de recuperação para dispositivos encriptados FileVault.

A inscrição do dispositivo aprovado pelo utilizador é necessária para que o FileVault funcione no dispositivo. O utilizador deve aprovar manualmente o perfil de gestão a partir das preferências do sistema para que a inscrição seja considerada aprovada pelo utilizador.

FileVault é um programa de encriptação de discos inteiros que está incluído com macOS. Pode utilizar o Intune para configurar o FileVault em dispositivos que executam **o macOS 10.13 ou posteriormente**.

Para configurar o FileVault, crie um perfil de [configuração](../configuration/device-profile-create.md) do dispositivo para proteção de pontofinal para a plataforma macOS. As definições do FileVault são uma das categorias de definições disponíveis para a proteção do ponto final macOS.

Depois de criar uma política para encriptar dispositivos com FileVault, a política é aplicada aos dispositivos em duas fases. Em primeiro lugar, o dispositivo está preparado para permitir que a Intune recupere e volte a fazer o backup da chave de recuperação. Esta ação é referida como caução. Depois de a chave ser depositada, a encriptação do disco pode começar.

![Definições de FileVault](./media/encrypt-devices/filevault-settings.png)

Para mais detalhes sobre a definição do FileVault pode gerir com intune, consulte [FileVault](endpoint-protection-macos.md#filevault) no artigo Intune para configurações de proteção de pontofinal macOS.

### <a name="permissions-to-manage-filevault"></a>Permissões para gerir fileVault

Para gerir o FileVault in Tune, a sua conta deve ter as permissões de controlo de acesso (RBAC) baseadas em [funções](../fundamentals/role-based-access-control.md) aplicáveis.

Seguem-se as permissões FileVault, que fazem parte da categoria de **tarefas Remotas,** e as funções RBAC incorporadas que concedem a permissão:
 
- **Obtenha a tecla FileVault:**
  - Operador de mesa de ajuda
  - Gestor de segurança endpoint

- **Chave Rotate FileVault**
  - Operador de mesa de ajuda

### <a name="how-to-configure-macos-filevault"></a>Como configurar o macOS FileVault

1. Inscreva-se no [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Selecione **Dispositivos** > Perfis de **Configuração** > **Criar perfil**.

3. Definir as seguintes opções:

   - Plataforma: macOS
   - Tipo de perfil: Proteção de ponto final

4. Selecione **Definições** > **FileVault**.

5. Para *fileVault,* **selecione Ativar**.

6. Para o tipo de *tecla de recuperação,* apenas a **chave pessoal** é suportada.

   Considere adicionar uma mensagem para ajudar a orientar os utilizadores finais sobre como recuperar a chave de recuperação do seu dispositivo. Estas informações podem ser úteis para os utilizadores finais quando utiliza a definição para a rotação da chave de recuperação pessoal, que pode gerar automaticamente uma nova chave de recuperação para um dispositivo periodicamente.

   Por exemplo: Para recuperar uma chave de recuperação perdida ou recentemente rotativa, inscreva-se no site do Portal da Empresa Intune a partir de qualquer dispositivo. No portal, vá a *Dispositivos* e selecione o dispositivo que tem o FileVault ativado e, em seguida, selecione a *chave de recuperação Get*. A chave de recuperação atual é apresentada.

7. Configure as definições restantes [do FileVault](endpoint-protection-macos.md#filevault) para satisfazer as necessidades do seu negócio e, em seguida, selecione **OK**.

  8. Complete a configuração de configurações adicionais e, em seguida, guarde o perfil.  

### <a name="manage-filevault"></a>Gerir fileVault

Depois de O Intune encriptar um dispositivo macOS com fileVault, pode visualizar e gerir as teclas de recuperação do FileVault quando visualiza rumar o relatório de [encriptação](encryption-monitor.md)Intune .

Depois de a Intune encriptar um dispositivo macOS com fileVault, pode visualizar a chave de recuperação pessoal desse dispositivo a partir do Portal da Empresa web em qualquer dispositivo. Uma vez no Portal da Empresa web, escolha o dispositivo macOS encriptado e, em seguida, opte por "Obter a chave de recuperação" como uma ação remota do dispositivo.

### <a name="retrieve-personal-recovery-key-from-mem-encrypted-macos-devices"></a>Recuperar a chave de recuperação pessoal dos dispositivos macOS encriptados mEM

Os utilizadores finais recuperam a sua chave de recuperação pessoal (chave FileVault) utilizando a aplicação portal da empresa iOS. O dispositivo que tenha a chave de recuperação pessoal deve ser matriculado com Intune e encriptado com fileVault através de Intune. Utilizando a aplicação portal da empresa iOS, o utilizador final pode abrir uma página web que inclui a chave de recuperação pessoal fileVault. Também pode recuperar a chave de recuperação de Intune selecionando **Dispositivos** > *o dispositivo macOS encriptado e matriculado* > Obter a chave de **recuperação**. 

## <a name="bitlocker-encryption-for-windows-10"></a>Encriptação BitLocker para Windows 10

Utilize insinopara configurar a encriptação bitLocker drive em dispositivos que executam o Windows 10. Em seguida, utilize o relatório de encriptação Intune para visualizar detalhes de encriptação para esses dispositivos. Também pode aceder a informações importantes para o BitLocker a partir dos seus dispositivos, conforme encontrado no Azure Ative Directory (Azure AD).

O BitLocker está disponível em dispositivos que executam **o Windows 10 ou mais tarde**.

Configure o BitLocker quando criar um perfil de [configuração](../configuration/device-profile-create.md) do dispositivo para proteção de pontofinal para a plataforma Windows 10 ou posterior. As definições bitLocker estão na categoria de definições de encriptação do Windows para proteção de ponto final do Windows 10.

![Definições bitLocker](./media/encrypt-devices/bitlocker-settings.png)

### <a name="how-to-configure-windows-10-bitlocker"></a>Como configurar o Windows 10 BitLocker

1. Inscreva-se no [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Selecione **Dispositivos** > Perfis de **Configuração** > **Criar perfil**.

3. Definir as seguintes opções:

   - Plataforma: Windows 10 e mais tarde
   - Tipo de perfil: Proteção de ponto final

4. Selecione **Definições** > **encriptação do Windows**.

5. Configure as definições para o BitLocker para atender às necessidades do seu negócio e, em seguida, selecione **OK**.

6. Complete a configuração de configurações adicionais e, em seguida, guarde o perfil.

### <a name="silently-enable-bitlocker-on-devices"></a>Ativar silenciosamente o BitLocker nos dispositivos

Pode configurar uma política BitLocker que automaticamente e silenciosamente ativa o BitLocker num dispositivo. Isto significa que o BitLocker permite com sucesso sem apresentar qualquer UI ao utilizador final, mesmo quando esse utilizador não é um Administrador local no dispositivo.

**Pré-requisitos do dispositivo:**

Um dispositivo deve satisfazer as seguintes condições para ser elegível para permitir silenciosamente o BitLocker:

- O dispositivo deve executar a versão 1809 do Windows 1809 ou mais tarde
- O dispositivo deve ser Azure AD Joined  

**Configuração da política BitLocker:**

As seguintes duas definições para as definições de [base bitLocker](../protect/endpoint-protection-windows-10.md#bitlocker-base-settings) devem ser configuradas na política BitLocker:

- **Aviso para outra encriptação do disco** = *Block*.
- **Permitir que os utilizadores padrão permitam encriptação durante a adesão do Azure AD** = *permitir*

A política BitLocker **não deve exigir** a utilização de um PIN de arranque ou chave de arranque. Quando é *necessária*uma chave PIN ou chave de arranque de arranque TPM, o BitLocker não pode ativar silenciosamente e requer interação do utilizador final.  Este requisito é cumprido através das seguintes três definições de [unidade BitLocker OS](../protect/endpoint-protection-windows-10.md#bitlocker-os-drive-settings) na mesma política:

- PIN de **arranque tpm compatível** não deve ser definido para exigir PIN de arranque com *TPM*
- Chave de **arranque TPM compatível** não deve ser definida para exigir chave de arranque com *TPM*
- Chave de **arranque TPM compatível e PIN** não devem definir para exigir chave de arranque e PIN com *TPM*



### <a name="manage-bitlocker"></a>Gerir o BitLocker

Depois de O Intune encriptar um dispositivo Windows 10 com o BitLocker, pode visualizar e recuperar as chaves de recuperação do BitLocker quando visualizar o relatório de [encriptação](encryption-monitor.md)Intune .

### <a name="rotate-bitlocker-recovery-keys"></a>Teclas de recuperação BitLocker rotativas

Pode utilizar uma ação do dispositivo Intune para rodar remotamente a chave de recuperação BitLocker de um dispositivo que executa a versão 1909 do Windows 10 ou mais tarde.

#### <a name="prerequisites"></a>Pré-requisitos

Os dispositivos devem cumprir os seguintes pré-requisitos para suportar a rotação da chave de recuperação BitLocker:

- Os dispositivos devem executar a versão 1909 do Windows 10 ou mais tarde

- Os dispositivos azure ad-joined e híbrido-join-join devem ter suporte para a rotação da chave ativada:

  - **Rotação da palavra-passe de recuperação orientada pelo cliente**

  Esta definição encontra-se sob *encriptação do Windows* como parte de uma política de configuração do dispositivo para a Proteção de Pontofinal do Windows 10.
  
#### <a name="to-rotate-the-bitlocker-recovery-key"></a>Para rodar a chave de recuperação BitLocker

1. Inscreva-se no [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Selecione **Dispositivos** > **Todos os dispositivos**.

3. Na lista de dispositivos que gere, selecione um dispositivo, selecione **Mais,** e, em seguida, selecione a ação remota do dispositivo de rotação da **tecla BitLocker.**

## <a name="next-steps"></a>Próximos passos

Crie uma política de [conformidade com o dispositivo.](compliance-policy-create-windows.md)

Use o relatório de encriptação, para gerir:

- [Chaves de recuperação BitLocker](encryption-monitor.md#bitlocker-recovery-keys)
- [Chaves de recuperação fileVault](encryption-monitor.md#filevault-recovery-keys)

Reveja as definições de encriptação que pode configurar com Intune para:

- [BitLocker](endpoint-protection-windows-10.md#windows-encryption)
- [FileVault](endpoint-protection-macos.md#filevault)
