---
title: Atualizar recursos do BIOS do Windows usando políticas de MDM no Microsoft Intune-Azure | Microsoft Docs
description: Adicione um perfil de DFCI (interface de configuração de firmware de dispositivo) para gerenciar configurações de UEFI, como CPU, hardware interno e opções de inicialização em dispositivos Windows 10 no Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/06/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 38f02d694f1935e4732805f3ae7c66fd9718057a
ms.sourcegitcommit: 78cebd3571fed72a3a99e9d33770ef3d932ae8ca
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/13/2019
ms.locfileid: "74059596"
---
# <a name="use-device-firmware-configuration-interface-profiles-on-windows-devices-in-microsoft-intune-public-preview"></a>Usar perfis de interface de configuração de firmware de dispositivo em dispositivos Windows no Microsoft Intune (visualização pública)

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Ao usar o Intune para gerenciar dispositivos do AutoPilot, você pode gerenciar configurações de UEFI (BIOS) depois que elas são registradas, usando a DFCI (interface de configuração de firmware do dispositivo). Para obter uma visão geral dos benefícios, cenários e pré-requisitos, consulte [visão geral do DFCI](https://microsoft.github.io/mu/dyn/mu_plus/DfciPkg/Docs/Dfci_Feature/).

O DFCI [permite que o Windows](https://docs.microsoft.com/windows/client-management/mdm/uefi-csp) passe comandos de gerenciamento do INTUNE para UEFI (Unified Extensible Firmware Interface).

No Intune, use esse recurso para controlar as configurações do BIOS. Normalmente, o firmware é mais resiliente a ataques mal-intencionados. Ele limita o controle dos usuários finais sobre o BIOS, que é bom em uma situação comprometida.

Por exemplo, você usa dispositivos Windows 10 em um ambiente seguro e deseja desabilitar a câmera. Você pode desabilitar a câmera na camada de firmware, portanto, não importa o que o usuário final faz. Reinstalar o sistema operacional ou apagar o computador não ligará a câmera novamente. Em outro exemplo, bloqueie as opções de inicialização para impedir que os usuários inicializem outro sistema operacional ou uma versão mais antiga do Windows que não tenha os mesmos recursos de segurança.

Ao reinstalar uma versão mais antiga do Windows, instalar um sistema operacional separado ou formatar o disco rígido, você não poderá substituir o gerenciamento de DFCI. Esse recurso pode impedir que malwares se comuniquem com processos do sistema operacional, incluindo processos de sistema operacional elevados. A cadeia de confiança do DFCI usa criptografia de chave pública e não depende da segurança de senha UEFI (BIOS) local. Essa camada de segurança impede que usuários locais acessem configurações gerenciadas dos menus de UEFI (BIOS) do dispositivo.

Esta funcionalidade aplica-se a:

- Windows 10 RS5 (1809) e posterior em UEFI com suporte

## <a name="before-you-begin"></a>Antes de começar

- O fabricante do dispositivo deve ter DFCI adicionado ao seu firmware UEFI no processo de fabricação ou como uma atualização de firmware instalada. Trabalhe com seus fornecedores de dispositivo para determinar [os fabricantes que dão suporte a DFCI](https://microsoft.github.io/mu/dyn/mu_plus/DfciPkg/Docs/Scenarios/DfciScenarios/#oems-that-support-dfci)ou a versão de firmware necessária para usar o DFCI.

- O dispositivo deve ser registrado para o piloto automático do Windows por um [parceiro CSP (provedor de solução Microsoft Cloud)](https://partner.microsoft.com/cloud-solution-provider)ou registrado diretamente pelo OEM. 

  Os dispositivos registrados manualmente para o piloto automático, como [importado de um arquivo CSV](../enrollment/enrollment-autopilot.md#add-devices), não têm permissão para usar o DFCI. Por design, o gerenciamento de DFCI requer atestado externo da aquisição comercial do dispositivo por meio de um OEM ou um registro de parceiro CSP da Microsoft para o Windows AutoPilot.

  Depois que o dispositivo for registrado, seu número de série será mostrado na lista de dispositivos do Windows AutoPilot.

  Para obter mais informações sobre o piloto automático, incluindo quaisquer requisitos, consulte [registrar dispositivos Windows no Intune usando o Windows AutoPilot](../enrollment/enrollment-autopilot.md).

## <a name="create-your-azure-ad-security-groups"></a>Criar seus grupos de segurança do Azure AD

Os perfis de implantação do AutoPilot são atribuídos aos grupos de segurança do Azure AD. Certifique-se de criar grupos que incluam seus dispositivos com suporte DFCI. Para dispositivos DFCI, a maioria das organizações pode criar grupos de dispositivos, em vez de grupos de usuários. Considere os seguintes cenários:

- Os recursos humanos (RH) têm diferentes dispositivos Windows. Por motivos de segurança, você não quer que ninguém nesse grupo use a câmera nos dispositivos. Nesse cenário, você pode criar um grupo de usuários de segurança de RH para que a política se aplique aos usuários no grupo RH, seja qual for o tipo de dispositivo.
- No chão de fábrica, você tem 10 dispositivos. Em todos os dispositivos, você deseja impedir a inicialização dos dispositivos de um dispositivo USB. Nesse cenário, você pode criar um grupo de dispositivos de segurança e adicionar esses 10 dispositivos ao grupo.

Para obter mais informações sobre como criar grupos no Intune, consulte [Adicionar grupos para organizar usuários e dispositivos](../fundamentals/groups-add.md).

## <a name="create-the-profiles"></a>Criar os perfis

Para usar o DFCI, crie os seguintes perfis e atribua-os ao seu grupo.

### <a name="create-an-autopilot-deployment-profile"></a>Criar um perfil de implementação do Autopilot

Esse perfil configura e pré-configurar novos dispositivos. [Perfil de implantação do AutoPilot](../enrollment/enrollment-autopilot.md#create-an-autopilot-deployment-profile) lista as etapas para criar o perfil.

### <a name="create-an-enrollment-state-page-profile"></a>Criar um perfil de página de estado de registro

Esse perfil garante que os dispositivos sejam verificados e habilitados para DFCI durante a instalação do Windows. É altamente recomendável usar esse perfil para bloquear o uso do dispositivo até que todos os aplicativos e perfis sejam instalados. [Perfil de página de estado de registro](../enrollment/windows-enrollment-status.md) lista as etapas para criar o perfil.

### <a name="create-the-dfci-profile"></a>Criar o perfil DFCI

Esse perfil inclui as configurações de DFCI que você configura.

1. Entre no centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selecione **dispositivos** > **perfis de configuração** > **Criar perfil**.
3. Introduza as seguintes propriedades:

    - **Nome**: Insira um nome descritivo para o perfil. Atribua nomes às políticas de forma que possa identificá-las facilmente mais tarde. Por exemplo, um bom nome de perfil é **Windows: definir configurações de DFCI em dispositivos Windows**.
    - **Descrição:** introduza uma descrição para o perfil. Esta definição é opcional, mas recomendada.
    - **Plataforma**: selecione **Windows 10 e posterior**.
    - **Tipo de perfil**: selecione a **interface de configuração do firmware do dispositivo**.

4. Configure as definições:

    - **Permitir que o usuário local altere as configurações de UEFI (BIOS)** : suas opções:
      - **Somente configurações não definidas**: o usuário local pode alterar qualquer configuração *, exceto* as configurações definidas explicitamente para **habilitar** ou **desabilitar** pelo Intune.
      - **Nenhum**: o usuário local não pode alterar nenhuma configuração de UEFI (BIOS), incluindo as configurações não mostradas no perfil DFCI.

    - **Virtualização de CPU e e/s**: suas opções:
        - **Não configurado**: o Intune não toca nesse recurso e deixa todas as configurações como estão.
        - **Habilitado**: o BIOS habilita os recursos de virtualização de CPU e e/s da plataforma para uso pelo sistema operacional. Ele ativa a segurança baseada em virtualização do Windows e as tecnologias do Device Guard.
        - **Desabilitar**: o BIOS DESABILITA a CPU da plataforma & recursos de virtualização de e/s e impede que eles sejam usados.
    - **Câmeras**: suas opções:
        - **Não configurado**: o Intune não toca nesse recurso e deixa todas as configurações como estão.
        - **Habilitado**: todas as câmeras internas gerenciadas diretamente pela UEFI (BIOS) estão habilitadas. Periféricos, como câmeras USB, não são afetados.
        - **Desabilitado**: todas as câmeras internas gerenciadas diretamente pela UEFI (BIOS) estão desabilitadas. Periféricos, como câmeras USB, não são afetados.
    - **Microfones e alto-falantes**: suas opções:
        - **Não configurado**: o Intune não toca nesse recurso e deixa todas as configurações como estão.
        - **Habilitado**: todos os microfones internos e os alto-falantes gerenciados diretamente pela UEFI (BIOS) estão habilitados. Periféricos, como dispositivos USB, não são afetados.
        - **Desabilitado**: todos os microfones internos e os alto-falantes diretamente gerenciados pela UEFI (BIOS) estão desabilitados. Periféricos, como dispositivos USB, não são afetados.
    - **Rádios (Bluetooth, Wi-Fi, NFC, etc.)** : suas opções:
        - **Não configurado**: o Intune não toca nesse recurso e deixa todas as configurações como estão.
        - **Habilitado**: todos os rádios internos gerenciados diretamente pela UEFI (BIOS) estão habilitados. Periféricos, como dispositivos USB, não são afetados.
        - **Desabilitado**: todos os rádios internos gerenciados diretamente pela UEFI (BIOS) estão desabilitados. Periféricos, como dispositivos USB, não são afetados.

        > [!WARNING]
        > Se você desabilitar a configuração de **rádios** , o dispositivo exigirá uma conexão de rede com fio. Caso contrário, o dispositivo pode não ser gerenciável.

    - **Inicialização de mídia externa (USB, SD)** : suas opções:
        - **Não configurado**: o Intune não toca nesse recurso e deixa todas as configurações como estão.
        - **Habilitado**: UEFI (BIOS) permite a inicialização a partir do armazenamento de disco não rígido.
        - **Desabilitado**: UEFI (BIOS) não permite a inicialização do armazenamento de disco não rígido.
    - **Inicialize a partir de adaptadores de rede**: suas opções:
        - **Não configurado**: o Intune não toca nesse recurso e deixa todas as configurações como estão.
        - **Habilitado**: UEFI (BIOS) permite a inicialização de interfaces de rede internas.
        - **Desabilitado**: UEFI (BIOS) não permite a inicialização de interfaces de rede internas.

5. Assim que terminar, selecione **OK** > **Criar** para guardar as alterações. O perfil é criado e apresentado na lista.

## <a name="assign-the-profiles-and-reboot"></a>Atribuir os perfis e reinicializar

Depois que os perfis são criados, eles estão [prontos para serem atribuídos](../configuration/device-profile-assign.md). Certifique-se de atribuir os perfis aos grupos de segurança do Azure AD que incluem seus dispositivos DFCI.

Quando o dispositivo executa o Windows AutoPilot, durante a página de status de registro, DFCI pode forçar uma reinicialização. Essa primeira reinicialização registra a UEFI no Intune. 

Se você quiser confirmar se o dispositivo está registrado, você pode reinicializar o dispositivo novamente, mas ele não é necessário. Use as instruções do fabricante do dispositivo para abrir o menu UEFI e confirme se a UEFI agora é gerenciada.

Na próxima vez que o dispositivo sincronizar com o Intune, o Windows receberá as configurações de DFCI. Reinicialize o dispositivo. Essa terceira reinicialização é necessária para que a UEFI receba as configurações de DFCI do Windows.

## <a name="update-existing-dfci-settings"></a>Atualizar configurações de DFCI existentes

Se você quiser alterar as configurações de DFCI existentes em dispositivos que estão em uso, você pode. No perfil DFCI existente, altere as configurações e salve as alterações. Como o perfil já foi atribuído, as novas configurações de DFCI entrarão em vigor quando:

1. O dispositivo faz check-in com o serviço do Intune para examinar as atualizações de perfil. Os check-ins acontecem em vários momentos. Para obter mais informações, consulte [quando os dispositivos obtêm uma política, um perfil ou atualizações de aplicativo](../configuration/device-profile-troubleshoot.md#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned).

2. Para impor as novas configurações, reinicialize o dispositivo [remotamente](../remote-actions/device-restart.md) ou localmente.

Você também pode [sinalizar dispositivos para fazer check-in](../remote-actions/device-sync.md). Após uma sincronização bem-sucedida, [sinalize para reinicializar](../remote-actions/device-restart.md).

>[!NOTE]
> Excluir o perfil DFCI ou remover um dispositivo do grupo atribuído ao perfil não remove as configurações de DFCI ou reabilita os menus UEFI (BIOS). Se você quiser parar de usar o DFCI, atualize seu perfil DFCI existente. Para obter mais informações sobre as etapas, consulte [desativar o dispositivo](#retire) neste artigo.

## <a name="reuse-retire-or-recover-the-device"></a>Reutilizar, desativar ou recuperar o dispositivo

### <a name="reuse"></a>Posterior

Se você planeja redefinir o Windows para realocar o dispositivo, [Limpe o dispositivo](../remote-actions/devices-wipe.md). **Não** remova o registro de dispositivo do piloto automático.

Depois de apagar o dispositivo, mova o dispositivo para o grupo atribuído os novos perfis DFCI e AutoPilot. Certifique-se de reinicializar o dispositivo para executar novamente a instalação do Windows.

### <a name="retire"></a>Extinguir

Quando você estiver pronto para desativar o dispositivo e liberá-lo do gerenciamento, atualize o perfil DFCI para as configurações de UEFI (BIOS) que você deseja no estado de saída. Normalmente, você deseja que todas as configurações estejam habilitadas. Por exemplo:

1. Abra seu perfil do DFCI (**dispositivos** > **perfis de configuração**).
2. Altere o **permitir que o usuário local altere as configurações de UEFI (BIOS)** **somente para as configurações não definidas**.
3. Defina todas as outras configurações como **não configurado**.
4. Salve suas configurações.

Estas etapas desbloqueiam os menus UEFI (BIOS) do dispositivo. Os valores permanecem iguais aos do perfil (**habilitado** ou **desabilitado**) e não são configurados de volta para valores padrão do sistema operacional.

Agora você está pronto para apagar o dispositivo. Depois que o dispositivo for apagado, exclua o registro do piloto automático. A exclusão do registro impede que o dispositivo seja reregistrado automaticamente quando reinicializa.

### <a name="recover"></a>Recupera

Se você apagar um dispositivo e excluir o registro do piloto automático antes de desbloquear os menus UEFI (BIOS), os menus permanecerão bloqueados. O Intune não pode enviar atualizações de perfil para desbloqueá-lo.

Para desbloquear o dispositivo, abra o menu UEFI (BIOS) e atualize o gerenciamento da rede. A recuperação desbloqueia os menus, mas deixa todas as configurações de UEFI (BIOS) definidas para os valores no perfil de DFCI do Intune anterior.

## <a name="end-user-impact"></a>Impacto do usuário final

Quando a política DFCI é aplicada, os usuários locais não podem alterar as configurações definidas pelo DFCI, mesmo que o menu UEFI (BIOS) seja protegido por senha. Dependendo das configurações definidas, os usuários finais podem receber erros de que os componentes de hardware não são encontrados ou não podem ser diagnosticados. Certifique-se de fornecer documentação aos usuários finais explicando as opções que você desabilitou.  

## <a name="next-steps"></a>Próximos passos

Depois que o perfil for atribuído, [monitore seu status](../device-profile-monitor.md).
