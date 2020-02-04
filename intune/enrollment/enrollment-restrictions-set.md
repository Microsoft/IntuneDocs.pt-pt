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
ms.openlocfilehash: 0dac0607fcaa92ebe65a7ddacc3cd91c63bf246e
ms.sourcegitcommit: 5178aec0244e023e73546f3d10f1a76eaf1f4a3e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2020
ms.locfileid: "76971866"
---
# <a name="set-enrollment-restrictions"></a>Definir restrições de inscrição

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Como administrador intune, pode criar e gerir restrições de inscrição que definam quais os dispositivos que podem inscrever-se na gestão com o Intune, incluindo o:
- Número de dispositivos.
- Sistemas operativos e versões.

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
- Versão do sistema operativo da plataforma para iOS, administrador de dispositivos Android, perfil de trabalho Android Enterprise, Windows e Windows Mobile. (Apenas as versões do Windows 10 podem ser utilizadas. Deixe em branco se o Windows 8.1 for permitido.)
  - Versão mínima.
  - Versão máxima.
- Restringir [dispositivos pessoais](device-enrollment.md#bring-your-own-device) (iOS, administrador de dispositivos Android, perfil de trabalho Android Enterprise, macOS, Windows e Windows Mobile apenas).

## <a name="default-restrictions"></a>Restrições predefinidas

As restrições predefinidas são fornecidas automaticamente para as restrições de inscrição relativas ao tipo e ao limite de número de dispositivos. Pode alterar as predefinições. As restrições predefinidas aplicam-se a todas as inscrições de utilizadores e sem utilizadores. Pode substituir estas predefinições ao criar novas restrições com prioridades mais altas.

## <a name="create-a-device-type-restriction"></a>Criar uma restrição de tipo de dispositivo

1. Inscreva-se no [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) > **Devices** > Restrições de **inscrição** > **Criar restrições** de restrição > **restrição**do tipo de dispositivo .
2. Na página **Basics,** dê à restrição um **nome** e **descrição**opcional.
3. Escolha **O Próximo** para ir à página de definições da **Plataforma.**
4. No âmbito **da Plataforma,** escolha **Permitir** as plataformas que pretende que esta restrição permita.
    ![tampa de ecrã para escolher as definições da plataforma](./media/enrollment-restrictions-set/choose-platform-settings.png)
5. Em **Versões,** escolha as versões mínimas e máximas que deseja que as plataformas permitidas suportem. As restrições de versão aplicam-se apenas aos dispositivos matriculados no Portal da Empresa.
     Os formatos suportados pelas versões são os seguintes:
    - O administrador de dispositivos Android e o perfil de trabalho android Enterprise suportam major.minor.rev.build.
    - O iOS suporta major.minor.rev. As versões do sistema operativo não se aplicam aos dispositivos da Apple que se inscrevam no Programa de Inscrição de Dispositivos, no Apple School Manager ou na aplicação Apple Configurator.
    - O Windows suporta major.minor.build.rev apenas para windows 10.
    
    > [!IMPORTANT]
    > As plataformas de administrador de dispositivos Android Enterprise (perfil de trabalho) e Android têm o seguinte comportamento:
    > - Se ambas as plataformas forem permitidas para o mesmo grupo, então os utilizadores serão matriculados com um perfil de trabalho se o seu dispositivo o suportar, caso contrário se matricularão como DA. 
    > - Se ambas as plataformas forem permitidas para o grupo e refinadas para versões específicas e não sobrepostas, então os utilizadores receberão o fluxo de inscrição definido para a sua versão OS. 
    > - Se ambas as plataformas forem permitidas, mas bloqueadas para as mesmas versões, os utilizadores de dispositivos com as versões bloqueadas serão retirados do fluxo de inscrição do administrador do dispositivo Android e, em seguida, ficam bloqueados da inscrição e solicitados a assinar. 
    >
    > Vale a pena notar que nem o perfil de trabalho nem a inscrição do administrador do dispositivo funcionarão a menos que os requisitos adequados tenham sido preenchidos no Android Registration. 
    
   > [!Note]
   > O Windows 10 não fornece o número de rev durante as matrículas, pelo que, por exemplo, se introduzir em 10.0.17134.100 e o dispositivo for de 10.0.17134.174, será bloqueado durante a inscrição.

6. Sob **propriedade pessoal,** escolha **Permitir** as plataformas que pretende permitir como dispositivos pessoais.
7. No **fabricante do Dispositivo,** introduza uma lista separada da vírposta dos fabricantes que pretende bloquear.
8. Escolha **O Próximo** para ir à página de **Atribuiçãos.**
9. Escolha **os grupos Select para incluir** e, em seguida, use a caixa de pesquisa para encontrar grupos que pretende incluir nesta restrição. A restrição só será aplicada aos grupos à qual for atribuída. Se não atribuir uma restrição a pelo menos um grupo, a mesma não terá efeito. Em seguida, selecione **Selecionar**. 
    ![tampa de ecrã para escolher as definições da plataforma](./media/enrollment-restrictions-set/select-groups.png)
10. Selecione **Next** para ir à página **Review + criar.**
11. Selecione **Criar** para criar a restrição.
12. A nova restrição é criada com uma prioridade diretamente acima das restrições predefinidas. Pode [alterar a prioridade](#change-enrollment-restriction-priority).


## <a name="create-a-device-limit-restriction"></a>Criar uma restrição de limite de dispositivo

1. Inscreva-se no [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) > **Dispositivos** > Restrições de **Inscrição** > **Criar restrições** de restrição > **restrição**de limite de dispositivo .
2. Na página **Basics,** dê à restrição um **nome** e **descrição**opcional.
3. Escolha **O Próximo** para ir à página limite do **Dispositivo.**
4. Para o limite do **dispositivo,** selecione o número máximo de dispositivos que um utilizador pode inscrever.
    ![tampa de ecrã para escolher o limite do dispositivo](./media/enrollment-restrictions-set/choose-device-limit.png)
5. Escolha **O Próximo** para ir à página de **Atribuiçãos.**
6. Escolha **os grupos Select para incluir** e, em seguida, use a caixa de pesquisa para encontrar grupos que pretende incluir nesta restrição. A restrição só será aplicada aos grupos à qual for atribuída. Se não atribuir uma restrição a pelo menos um grupo, a mesma não terá efeito. Em seguida, selecione **Selecionar**. 
    ![tampa de ecrã para selecionar grupos](./media/enrollment-restrictions-set/select-groups-device-limit.png)
7. Selecione **Next** para ir à página **Review + criar.**
8. Selecione **Criar** para criar a restrição.
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
> - Inscrições do Gestor de Inscrição de Dispositivos
>
> As restrições de limite do dispositivo não são aplicadas para estes tipos de inscrição porque são considerados cenários de dispositivos partilhados.
> Pode definir limites fixos para estes tipos de inscrição no [Azure Active Directory](https://docs.microsoft.com/azure/active-directory/devices/device-management-azure-portal#configure-device-settings).


## <a name="change-enrollment-restrictions"></a>Alterar restrições de inscrição

Pode alterar as definições para uma restrição de inscrição seguindo os passos abaixo. Estas restrições não efetuam dispositivos que já foram matriculados. A inscrição de dispositivos com o [agente de PC do Intune](../fundamentals/manage-windows-pcs-with-microsoft-intune.md) não pode ser bloqueada com esta funcionalidade.

1. Inscreva-se no [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) > **Dispositivos** > Restrições de **Inscrição** > escolha a restrição que pretende alterar > **Properties**.
2. Escolha **editar** ao lado das definições que pretende alterar.
3. Na página **Editar,** faça as alterações que deseja e proceda à página **'Rever + guardar',** em seguida, escolha **Guardar**.


## <a name="blocking-personal-android-devices"></a>Bloquear dispositivos Android pessoais
- Se bloquear dispositivos de administrador de dispositivos Android pessoalmente da inscrição, os dispositivos de perfil de trabalho Android Enterprise, propriedade pessoal, ainda podem inscrever-se.
- Por padrão, as definições de dispositivos de perfil de trabalho do Android Enterprise são as mesmas que as definições dos dispositivos de administrador de dispositivos Android. Depois de alterar o seu perfil de trabalho Android Enterprise ou as definições do administrador do dispositivo Android, isso já não acontece.
- Se bloquear a inscrição pessoal do perfil de trabalho do Android Enterprise, apenas os dispositivos Android de propriedade corporativa podem inscrever-se com perfis de trabalho Android Enterprise.

## <a name="blocking-personal-windows-devices"></a>Bloquear dispositivos Windows pessoais
Se bloquear a inscrição de dispositivos Windows de propriedade pessoal, o Intune verifica se cada novo pedido de inscrição do Windows foi autorizado como uma inscrição empresarial. As inscrições não autorizadas serão bloqueadas.

Os seguintes métodos estão qualificados como autorizados como uma inscrição empresarial Windows:
- A inscrição de utilizadores está a utilizar uma [conta do gestor de inscrição de dispositivos]( device-enrollment-manager-enroll.md).
- O dispositivo é inscrito através do [Windows Autopilot](enrollment-autopilot.md).
- O dispositivo está registado no Windows Autopilot, mas não é uma opção de apenas inscrição na MDM a partir das Definições do Windows.
- O número IMEI do dispositivo é apresentado em **Inscrição de dispositivos** >  **[Identificadores de dispositivos da empresa](corporate-identifiers-add.md)** . (Não suportado para o Windows Phone 8.1.)
- O dispositivo é inscrito através de um [pacote de aprovisionamento em massa](windows-bulk-enroll.md).
- O dispositivo é registrado por meio de GPO ou [registro automático de Configuration Manager para cogerenciamento](https://docs.microsoft.com/configmgr/comanage/quickstart-paths#bkmk_path1).
 
As inscrições seguintes são marcadas como empresariais pelo Intune. Mas, uma vez que não permitem o controlo por dispositivo pelo administrador do Intune, serão bloqueadas:
- [Inscrição na MDM automática](windows-enroll.md#enable-windows-10-automatic-enrollment) com [associação do Azure Active Directory durante a configuração do Windows](https://docs.microsoft.com/azure/active-directory/device-management-azuread-joined-devices-frx)\*.
- [Inscrição na MDM automática](windows-enroll.md#enable-windows-10-automatic-enrollment) com [associação do Azure Active Directory a partir das definições do Windows](https://docs.microsoft.com/azure/active-directory/user-help/user-help-register-device-on-network)*.
 
Os seguintes métodos de inscrição pessoal também serão bloqueados:
- [Inscrição na MDM automática](windows-enroll.md#enable-windows-10-automatic-enrollment) com [Adicionar Conta Profissional a partir das Definições do Windows](https://docs.microsoft.com/azure/active-directory/user-help/user-help-join-device-on-network)\*.
- Opção [Apenas inscrição na MDM]( https://docs.microsoft.com/windows/client-management/mdm/mdm-enrollment-of-windows-devices#connecting-personally-owned-devices-bring-your-own-device) a partir das Definições do Windows.

\* Não serão bloqueados se estiverem registados no Autopilot.


## <a name="blocking-personal-ios-devices"></a>Bloquear dispositivos pessoais iOS
Por predefinição, intune classifica os dispositivos iOS como propriedade pessoal. Para ser classificado como propriedade corporativa, um dispositivo iOS deve preencher uma das seguintes condições:
- Registado com um número de série ou IMEI.
- Matriculado utilizando inscrição automática de dispositivos (anteriormente Programa de Inscrição de Dispositivos)


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
