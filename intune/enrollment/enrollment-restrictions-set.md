---
title: Definir restrições de inscrição no Microsoft Intune
titleSuffix: ''
description: Restrinja a inscrição por plataforma e defina um limite de inscrição de dispositivos no Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/17/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 9691982c-1a03-4ac1-b7c5-73087be8c5f2
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 78f79a734d0a7b4901b2248b20abd9d304926dd2
ms.sourcegitcommit: e75718ee6cf93c0e6c915f2776b785fe8db9f7e0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/10/2019
ms.locfileid: "74955512"
---
# <a name="set-enrollment-restrictions"></a>Definir restrições de inscrição

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Como administrador do Intune, você pode criar e gerenciar restrições de registro que definem quais dispositivos podem ser registrados no gerenciamento com o Intune, incluindo:
- Número de dispositivos.
- Sistemas operacionais e versões.

Pode criar múltiplas restrições e aplicá-las a diferentes grupos de utilizadores. Pode definir uma [ordem de prioridade](#change-enrollment-restriction-priority) para as diferentes restrições.

>[!NOTE]
>As restrições de inscrição não são funcionalidades de segurança. A identidade dos dispositivos pode ser falsificada de forma a contornar estas restrições. Estas restrições são uma forma de dissuadir utilizadores sem fins maliciosos.

As restrições de inscrição específicas que pode criar incluem:

- Número máximo de dispositivos inscritos.
- Plataformas de dispositivos que podem ser inscritas:
  - Administrador do dispositivo Android
  - Perfil de trabalho do Android Enterprise
  - iOS
  - macOS
  - Windows
  - Windows Mobile
- Versão do sistema operacional da plataforma para iOS, administrador do dispositivo Android, perfil de trabalho do Android Enterprise, Windows e Windows Mobile. (Apenas as versões do Windows 10 podem ser utilizadas. Deixe em branco se o Windows 8.1 for permitido.)
  - Versão mínima.
  - Versão máxima.
- Restringir [dispositivos de propriedade pessoal](device-enrollment.md#bring-your-own-device) (Ios, administrador de dispositivo Android, perfil de trabalho corporativo do Android, MacOS, Windows e Windows Mobile somente).

## <a name="default-restrictions"></a>Restrições predefinidas

As restrições predefinidas são fornecidas automaticamente para as restrições de inscrição relativas ao tipo e ao limite de número de dispositivos. Pode alterar as predefinições. As restrições predefinidas aplicam-se a todas as inscrições de utilizadores e sem utilizadores. Pode substituir estas predefinições ao criar novas restrições com prioridades mais altas.

## <a name="create-a-device-type-restriction"></a>Criar uma restrição de tipo de dispositivo

1. Entre no centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) > **dispositivos** > **restrições de registro** > **criar restrição** > **restrição de tipo de dispositivo**.
2. Na página **noções básicas** , dê à restrição um **nome** e uma **Descrição**opcional.
3. Escolha **Avançar** para ir para a página **configurações de plataforma** .
4. Em **plataforma**, escolha **permitir** para as plataformas que você deseja que essa restrição permita.
    ![limite de tela para escolher as configurações de plataforma](./media/enrollment-restrictions-set/choose-platform-settings.png)
5. Em **versões**, escolha as versões mínima e máxima às quais você deseja que as plataformas permitidas ofereçam suporte. As restrições de versão se aplicam somente a dispositivos registrados com o Portal da Empresa.
     Os formatos suportados pelas versões são os seguintes:
    - O administrador do dispositivo Android e o perfil de trabalho do Android Enterprise dão suporte ao principal. Minor. Rev. Build.
    - o iOS dá suporte a Major. Minor. Rev. As versões do sistema operacional não se aplicam a dispositivos Apple que se registram com o Programa de registro de dispositivos, Apple School Manager ou o aplicativo Apple Configurator.
    - O Windows dá suporte a Major. Minor. Build. Rev somente para Windows 10.
    
    > [!IMPORTANT]
    > As plataformas Android Enterprise (perfil de trabalho) e de administrador de dispositivo Android têm o seguinte comportamento:
    > - Se ambas as plataformas forem permitidas para o mesmo grupo, os usuários serão registrados com um perfil de trabalho se o dispositivo der suporte, caso contrário, eles serão registrados como DA. 
    > - Se ambas as plataformas forem permitidas para o grupo e refinadas para versões específicas e não sobrepostas, os usuários receberão o fluxo de registro definido para a versão do sistema operacional. 
    > - Se ambas as plataformas forem permitidas, mas bloqueadas para as mesmas versões, os usuários em dispositivos com as versões bloqueadas serão desativados no fluxo de registro do administrador do dispositivo Android e serão bloqueados do registro e serão solicitados a sair. 
    >
    > Vale a pena observar que nenhum registro de perfil de trabalho ou de administrador do dispositivo funcionará, a menos que os selecionado pré-requisitos apropriados tenham sido concluídos no registro do Android. 
    
   > [!Note]
   > O Windows 10 não fornece o número Rev durante o registro, por exemplo, se você inserir em 10.0.17134.100 e o dispositivo for 10.0.17134.174, ele será bloqueado durante o registro.

6. Em **pessoal de propriedade**, escolha **permitir** para as plataformas que você deseja permitir como dispositivos de propriedade pessoal.
7. Escolha **Avançar** para ir para a página **atribuições** .
8. Escolha **Selecionar grupos para incluir** e, em seguida, use a caixa Pesquisar para localizar os grupos que você deseja incluir nessa restrição. A restrição só será aplicada aos grupos à qual for atribuída. Se não atribuir uma restrição a pelo menos um grupo, a mesma não terá efeito. Em seguida, selecione **Selecionar**. 
    ![limite de tela para escolher as configurações de plataforma](./media/enrollment-restrictions-set/select-groups.png)
9. Selecione **Avançar** para ir para a página **revisar + criar** .
10. Selecione **criar** para criar a restrição.
11. A nova restrição é criada com uma prioridade diretamente acima das restrições predefinidas. Pode [alterar a prioridade](#change-enrollment-restriction-priority).


## <a name="create-a-device-limit-restriction"></a>Criar uma restrição de limite de dispositivo

1. Entre no centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) > **dispositivos** > **restrições de registro** > **criar restrição** > **restrição de limite de dispositivo**.
2. Na página **noções básicas** , dê à restrição um **nome** e uma **Descrição**opcional.
3. Escolha **Avançar** para ir para a página **limite de dispositivo** .
4. Para **limite de dispositivo**, selecione o número máximo de dispositivos que um usuário pode registrar.
    ![a extremidade da tela para escolher o limite do dispositivo](./media/enrollment-restrictions-set/choose-device-limit.png)
5. Escolha **Avançar** para ir para a página **atribuições** .
6. Escolha **Selecionar grupos para incluir** e, em seguida, use a caixa Pesquisar para localizar os grupos que você deseja incluir nessa restrição. A restrição só será aplicada aos grupos à qual for atribuída. Se não atribuir uma restrição a pelo menos um grupo, a mesma não terá efeito. Em seguida, selecione **Selecionar**. 
    ![limite de tela para selecionar grupos](./media/enrollment-restrictions-set/select-groups-device-limit.png)
7. Selecione **Avançar** para ir para a página **revisar + criar** .
8. Selecione **criar** para criar a restrição.
9. A nova restrição é criada com uma prioridade diretamente acima das restrições predefinidas. Pode [alterar a prioridade](#change-enrollment-restriction-priority).

Durante as inscrições BYOD, os utilizadores verão uma notificação que os informará quando atingirem o limite de dispositivos inscritos. Por exemplo, no iOS:

![Notificação de limite do dispositivo iOS](./media/enrollment-restrictions-set/enrollment-restrictions-ios-set-limit-notification.png)

> [!IMPORTANT]
> As restrições de limite de dispositivos não se aplicam aos seguintes tipos de inscrição do Windows:
> - Inscrições cogeridas
> - Inscrições GPO
> - Inscrições conjuntas no Azure Active Directory
> - Inscrições conjuntas em massa no Azure Active Directory
> - Inscrições no Autopilot
> - Registros do Gerenciador de registro de dispositivos
>
> Restrições de limite de dispositivo não são impostas para esses tipos de registro porque são consideradas cenários de dispositivo compartilhado.
> Pode definir limites fixos para estes tipos de inscrição no [Azure Active Directory](https://docs.microsoft.com/azure/active-directory/devices/device-management-azure-portal#configure-device-settings).


## <a name="change-enrollment-restrictions"></a>Alterar restrições de registro

Você pode alterar as configurações de uma restrição de registro seguindo as etapas abaixo. Essas restrições não afetam os dispositivos que já foram registrados. A inscrição de dispositivos com o [agente de PC do Intune](../fundamentals/manage-windows-pcs-with-microsoft-intune.md) não pode ser bloqueada com esta funcionalidade.

1. Entre no centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) > **dispositivos** > **restrições de registro** > escolha a restrição que você deseja alterar > **Propriedades**.
2. Escolha **Editar** ao lado das configurações que você deseja alterar.
3. Na página **Editar** , faça as alterações desejadas e prossiga para a página **examinar + salvar** e, em seguida, escolha **salvar**.


## <a name="blocking-personal-android-devices"></a>Bloquear dispositivos Android pessoais
- Se você bloquear dispositivos pessoais de administrador de dispositivo Android do registro, os dispositivos de perfil de trabalho corporativo Android Enterprise ainda poderão ser registrados.
- Por padrão, suas configurações de dispositivos de perfil de trabalho do Android Enterprise são as mesmas que suas configurações para dispositivos de administrador de dispositivo Android. Depois de alterar o perfil de trabalho do Android Enterprise ou as configurações do administrador do dispositivo Android, esse não é mais o caso.
- Se você bloquear o registro de perfil de trabalho do Android Enterprise pessoal, somente dispositivos Android corporativos poderão ser registrados com perfis de trabalho do Android Enterprise.

## <a name="blocking-personal-windows-devices"></a>Bloquear dispositivos Windows pessoais
Se bloquear a inscrição de dispositivos Windows de propriedade pessoal, o Intune verifica se cada novo pedido de inscrição do Windows foi autorizado como uma inscrição empresarial. As inscrições não autorizadas serão bloqueadas.

Os seguintes métodos estão qualificados como autorizados como uma inscrição empresarial Windows:
- A inscrição de utilizadores está a utilizar uma [conta do gestor de inscrição de dispositivos]( device-enrollment-manager-enroll.md).
- O dispositivo é inscrito através do [Windows Autopilot](enrollment-autopilot.md).
- O dispositivo está registado no Windows Autopilot, mas não é uma opção de apenas inscrição na MDM a partir das Definições do Windows.
- O número IMEI do dispositivo é apresentado em **Inscrição de dispositivos** >  **[Identificadores de dispositivos da empresa](corporate-identifiers-add.md)** . (Não suportado para o Windows Phone 8.1.)
- O dispositivo é inscrito através de um [pacote de aprovisionamento em massa](windows-bulk-enroll.md).
- O dispositivo é inscrito através do GPO ou da [inscrição automática do SCCM para cogestão](https://docs.microsoft.com/sccm/comanage/quickstart-paths#bkmk_path1).
 
As inscrições seguintes são marcadas como empresariais pelo Intune. Mas, uma vez que não permitem o controlo por dispositivo pelo administrador do Intune, serão bloqueadas:
- [Inscrição na MDM automática](windows-enroll.md#enable-windows-10-automatic-enrollment) com [associação do Azure Active Directory durante a configuração do Windows](https://docs.microsoft.com/azure/active-directory/device-management-azuread-joined-devices-frx)\*.
- [Inscrição na MDM automática](windows-enroll.md#enable-windows-10-automatic-enrollment) com [associação do Azure Active Directory a partir das definições do Windows](https://docs.microsoft.com/azure/active-directory/user-help/user-help-register-device-on-network)*.
 
Os seguintes métodos de inscrição pessoal também serão bloqueados:
- [Inscrição na MDM automática](windows-enroll.md#enable-windows-10-automatic-enrollment) com [Adicionar Conta Profissional a partir das Definições do Windows](https://docs.microsoft.com/azure/active-directory/user-help/user-help-join-device-on-network)\*.
- Opção [Apenas inscrição na MDM]( https://docs.microsoft.com/windows/client-management/mdm/mdm-enrollment-of-windows-devices#connecting-personally-owned-devices-bring-your-own-device) a partir das Definições do Windows.

\* Não serão bloqueados se estiverem registados no Autopilot.


## <a name="blocking-personal-ios-devices"></a>Bloqueando dispositivos iOS pessoais
Por padrão, o Intune classifica os dispositivos iOS como de propriedade pessoal. Para ser classificado como corporativo, um dispositivo iOS deve atender a uma das seguintes condições:
- Registrado com um número de série ou IMEI.
- Registrado usando o registro de dispositivo automatizado (anteriormente Programa de registro de dispositivos)


## <a name="change-enrollment-restriction-priority"></a>Alterar a prioridade das restrições de inscrição

A prioridade é utilizada quando um utilizador existe em múltiplos grupos que têm restrições atribuídas. Os utilizadores só estão sujeitos à restrição de prioridade mais alta atribuída ao grupo ao qual pertencem. Por exemplo, o João está no grupo A, com a prioridade 5 atribuída, e também está no grupo B, com a prioridade 2 atribuída. O João só está sujeito às restrições com a prioridade 2.

Quando criar uma restrição, a mesma será adicionada à lista diretamente acima das prioridades predefinidas.

A inscrição de dispositivos inclui restrições predefinidas para tipos e limites de dispositivos. Estas duas restrições aplicam-se a todos os utilizadores, a menos que sejam substituídas por restrições de prioridade mais alta.

Pode alterar a prioridade de qualquer restrição que não seja predefinida.

1. Inicie sessão no portal do Azure.
2. Selecione **Mais Serviços**, procure o **Intune** e, em seguida, selecione **Intune**.
3. Selecione **Inscrição de dispositivos** > **Restrições de inscrição**.
4. Paire o cursor do rato sobre a lista de prioridades das restrições.
5. Utilize os três pontos verticais para arrastar a prioridade para a posição pretendida na lista.
