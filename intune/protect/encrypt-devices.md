---
title: Criptografar dispositivos com o método de criptografia com suporte de plataformas
titleSuffix: Microsoft Intune
description: Criptografe dispositivos com métodos de criptografia internos, como BitLocker ou FileVault, e gerencie as chaves de recuperação para esses dispositivos criptografados no portal do Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/21/2019
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
ms.openlocfilehash: 13d6a2b9cdc8596c7f5cf81218377754e9412be1
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/05/2019
ms.locfileid: "74390310"
---
# <a name="use-device-encryption-with-intune"></a>Usar a criptografia de dispositivo com o Intune

Use o Intune para gerenciar um disco interno de dispositivos ou criptografia de unidade para proteger dados em seus dispositivos.

Configure a criptografia de disco como parte de um perfil de configuração de dispositivo para o Endpoint Protection. As seguintes plataformas e tecnologias de criptografia têm suporte do Intune:

- macOS: FileVault
- Windows 10 e posterior: BitLocker

O Intune também fornece um relatório de [criptografia](encryption-monitor.md) interno que apresenta detalhes sobre o status de criptografia dos dispositivos em todos os seus dispositivos gerenciados.

## <a name="filevault-encryption-for-macos"></a>Criptografia FileVault para macOS

Use o Intune para configurar a criptografia de disco FileVault em dispositivos que executam o macOS. Em seguida, use o relatório de criptografia do Intune para exibir os detalhes de criptografia para esses dispositivos e para gerenciar as chaves de recuperação para dispositivos criptografados FileVault.

O FileVault é um programa de criptografia de disco completo que está incluído no macOS. Você pode usar o Intune para configurar o FileVault em dispositivos que executam o **macOS 10,13 ou posterior**.

Para configurar o FileVault, crie um [perfil de configuração de dispositivo](../configuration/device-profile-create.md) para o Endpoint Protection da plataforma MacOS. As configurações de FileVault são uma das categorias de configurações disponíveis para o macOS Endpoint Protection.

Depois de criar uma política para criptografar dispositivos com o FileVault, a política é aplicada aos dispositivos em dois estágios. Primeiro, o dispositivo está preparado para habilitar o Intune a recuperar e fazer backup da chave de recuperação. Isso é conhecido como caução. Depois que a chave estiver em garantia, a criptografia de disco poderá ser iniciada.

![Configurações de FileVault](./media/encrypt-devices/filevault-settings.png)

Para obter detalhes sobre a configuração de FileVault que você pode gerenciar com o Intune, consulte [FileVault](endpoint-protection-macos.md#filevault) no artigo do Intune para configurações do MacOS Endpoint Protection.

### <a name="how-to-configure-macos-filevault"></a>Como configurar o macOS FileVault

1. Entre no centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Selecione **dispositivos** > **perfis de configuração** > **Criar perfil**.

3. Defina as seguintes opções:

   - Plataforma: macOS
   - Tipo de perfil: Endpoint Protection

4. Selecione **configurações** > **FileVault**.

5. Para *FileVault*, selecione **habilitar**.

6. Para o *tipo de chave de recuperação*, somente a **chave pessoal** tem suporte.

   Considere adicionar uma mensagem para orientar os usuários finais sobre como recuperar a chave de recuperação para seu dispositivo. Essas informações podem ser úteis para os usuários finais quando você usa a configuração para rotação de chave de recuperação pessoal, que pode gerar automaticamente uma nova chave de recuperação para um dispositivo periodicamente.

   Por exemplo: para recuperar uma chave de recuperação perdida ou recentemente girada, entre no site do Portal da Empresa do Intune de qualquer dispositivo. No portal, vá para *dispositivos* e selecione o dispositivo que tem o FileVault habilitado e, em seguida, selecione *obter chave de recuperação*. A chave de recuperação atual é exibida.

7. Defina as [configurações de FileVault](endpoint-protection-macos.md#filevault) restantes para atender às suas necessidades de negócios e selecione **OK**.

   > [!IMPORTANT]
   > Há um problema conhecido quando a configuração **desabilitar prompt em sair** está definida como *habilitar*. Quando definido como *habilitar*, a configuração para o **número de vezes permitido para bypass** deve ser definida como um valor e não deve ser definida como *não configurada*. Se definido como *não configurado*, o perfil falha no dispositivo. Nesse cenário, o dispositivo informa o **Resumo do estado do perfil** como **erro** sem mais detalhes.
   >
   > Quando **desabilitar prompt na saída** estiver definido como *não configurado*, o **número de vezes permitido para bypass** pode *não ser configurado* ou ter um valor.
   >
   > Este problema será resolvido numa atualização futura.

8. Conclua a configuração de configurações adicionais e salve o perfil.  

### <a name="manage-filevault"></a>Gerenciar FileVault

Depois que o Intune criptografa um dispositivo macOS com FileVault, você pode exibir e gerenciar as chaves de recuperação do FileVault ao exibir o [relatório de criptografia](encryption-monitor.md)do Intune.

Depois que o Intune criptografa um dispositivo macOS com FileVault, você pode exibir a chave de recuperação pessoal desse dispositivo do Portal da Empresa da Web em qualquer dispositivo. Uma vez no Portal da Empresa da Web, escolha o dispositivo macOS criptografado e, em seguida, escolha "obter chave de recuperação" como uma ação de dispositivo remoto.

## <a name="bitlocker-encryption-for-windows-10"></a>Criptografia BitLocker para Windows 10

Use o Intune para configurar Criptografia de Unidade de Disco BitLocker em dispositivos que executam o Windows 10. Em seguida, use o relatório de criptografia do Intune para exibir detalhes de criptografia para esses dispositivos. Você também pode acessar informações importantes para o BitLocker de seus dispositivos, conforme encontrado no Azure Active Directory (Azure AD).

O BitLocker está disponível em dispositivos que executam o **Windows 10 ou posterior**.

Configure o BitLocker ao criar um [perfil de configuração de dispositivo](../configuration/device-profile-create.md) para o Endpoint Protection para a plataforma Windows 10 ou posterior. As configurações do BitLocker estão na categoria configurações de criptografia do Windows para o Windows 10 Endpoint Protection.

![Configurações do BitLocker](./media/encrypt-devices/bitlocker-settings.png)

### <a name="how-to-configure-windows-10-bitlocker"></a>Como configurar o BitLocker do Windows 10

1. Entre no centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Selecione **dispositivos** > **perfis de configuração** > **Criar perfil**.

3. Defina as seguintes opções:

   - Plataforma: Windows 10 e posterior
   - Tipo de perfil: Endpoint Protection

4. Selecione **configurações** > **criptografia do Windows**.

5. Defina as configurações do BitLocker para atender às suas necessidades de negócios e selecione **OK**.

6. Conclua a configuração de configurações adicionais e salve o perfil.

### <a name="manage-bitlocker"></a>Gerir o BitLocker

Depois que o Intune criptografar um dispositivo Windows 10 com o BitLocker, você poderá exibir e recuperar as chaves de recuperação do BitLocker ao exibir o [relatório de criptografia](encryption-monitor.md)do Intune.

### <a name="rotate-bitlocker-recovery-keys"></a>Girar as chaves de recuperação do BitLocker

Você pode usar uma ação de dispositivo do Intune para girar remotamente a chave de recuperação do BitLocker de um dispositivo que executa o Windows 10 versão 1909 ou posterior.

#### <a name="prerequisites"></a>Pré-requisitos

Os dispositivos devem atender aos seguintes pré-requisitos para dar suporte à rotação da chave de recuperação do BitLocker:

- Os dispositivos devem executar o Windows 10 versão 1909 ou posterior

- Os dispositivos ingressados no Azure AD e híbridos devem ter suporte para a rotação de chaves habilitada:

  - **Rotação de senha de recuperação controlada pelo cliente**

  Essa configuração é encontrada em *criptografia do Windows* como parte de uma política de configuração de dispositivo para o Windows 10 Endpoint Protection.
  
#### <a name="to-rotate-the-bitlocker-recovery-key"></a>Para girar a chave de recuperação do BitLocker

1. Entre no centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Selecione **Dispositivos** > **Todos os dispositivos**.

3. Na lista de dispositivos que você gerencia, selecione um dispositivo, selecione **mais**e, em seguida, selecione a ação remota do dispositivo de **rotação de chave do BitLocker** .

## <a name="next-steps"></a>Próximos passos

Criar [uma política de conformidade do dispositivo](compliance-policy-create-windows.md) .

Use o relatório de criptografia para gerenciar:

- [Chaves de recuperação do BitLocker](encryption-monitor.md#bitlocker-recovery-keys)
- [Chaves de recuperação FileVault](encryption-monitor.md#filevault-recovery-keys)

Examine as configurações de criptografia que você pode configurar com o Intune para:

- [BitLocker](endpoint-protection-windows-10.md#windows-encryption)
- [FileVault](endpoint-protection-macos.md#filevault)
