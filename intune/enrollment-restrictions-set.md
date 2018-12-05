---
title: Definir restrições de inscrição no Microsoft Intune
titlesuffix: ''
description: Restrinja a inscrição por plataforma e defina um limite de inscrição de dispositivos no Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/17/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 9691982c-1a03-4ac1-b7c5-73087be8c5f2
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: e813d64d3019748eed3c985dcefda744188ad850
ms.sourcegitcommit: d3b1e3fffd3e0229292768c7ef634be71e4736ae
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/04/2018
ms.locfileid: "52861035"
---
# <a name="set-enrollment-restrictions"></a>Definir restrições de inscrição

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Como administrador do Intune, pode criar e gerir as restrições de inscrição que definem o número e o tipo de dispositivos que podem ser inscritos para serem geridos com o Intune. Pode criar múltiplas restrições e aplicá-las a diferentes grupos de utilizadores. Pode definir uma [ordem de prioridade](#change-enrollment-restriction-priority) para as diferentes restrições.

>[!NOTE]
>As restrições de inscrição não são funcionalidades de segurança. A identidade dos dispositivos pode ser falsificada de forma a contornar estas restrições. Estas restrições são uma forma de dissuadir utilizadores sem fins maliciosos.

As restrições de inscrição específicas que pode criar incluem:

- Número máximo de dispositivos inscritos.
- Plataformas de dispositivos que podem ser inscritas:
  - Android
  - Perfil de trabalho do Android
  - iOS
  - macOS
  - Windows
- Versão do sistema operativo da plataforma para iOS, Android, perfil de trabalho do Android e Windows. (Apenas as versões do Windows 10 podem ser utilizadas. Deixe em branco se o Windows 8.1 for permitido.)
  - Versão mínima.
  - Versão máxima.
- Restringir dispositivos pessoais (apenas para iOS, Android, perfil de trabalho do Android, macOS ou Windows).

## <a name="default-restrictions"></a>Restrições predefinidas

As restrições predefinidas são fornecidas automaticamente para as restrições de inscrição relativas ao tipo e ao limite de número de dispositivos. Pode alterar as predefinições. As restrições predefinidas aplicam-se a todas as inscrições de utilizadores e sem utilizadores. Pode substituir estas predefinições ao criar novas restrições com prioridades mais altas.

## <a name="create-a-restriction"></a>Criar uma restrição

1. Inicie sessão no portal do Azure.
2. Selecione **Mais Serviços**, procure o **Intune** e, em seguida, selecione **Intune**.
3. Selecione **Inscrição de dispositivos** > **Restrições de inscrição**.
4. Selecione **Criar restrição**.
5. Forneça um nome e uma descrição.
6. Selecione um **Tipo de restrição** e, em seguida, selecione **Criar**.
7. Para definir o máximo de dispositivos que um utilizador pode inscrever, selecione **Limite de dispositivos** para definir restrições de limites de dispositivos.
8. Se quiser permitir ou bloquear diversas plataformas ou versões, selecione **Plataformas** e **Configurações de plataformas** para definir restrições de tipos de dispositivo.
9. Selecione **Atribuições** > **+ Selecionar grupos**.
10. Em **Selecionar grupos**, selecione um ou mais grupos e, em seguida, selecione **Selecionar**. A restrição só será aplicada aos grupos à qual for atribuída. Se não atribuir uma restrição a pelo menos um grupo, a mesma não terá efeito.
11. Selecione **Guardar**.
12. A nova restrição é criada com uma prioridade diretamente acima das restrições predefinidas. Pode [alterar a prioridade](#change-enrollment-restriction-priority).

## <a name="set-device-type-restrictions"></a>Definir restrições de tipos de dispositivos

Pode alterar as definições de uma restrição de tipos de dispositivo ao seguir os passos abaixo. Estas restrições não afetam os dispositivos que já tenham sido inscritos. A inscrição de dispositivos com o [agente de PC do Intune](/intune-classic/deploy-use/manage-windows-pcs-with-microsoft-intune) não pode ser bloqueada com esta funcionalidade.

1. Inicie sessão no portal do Azure.
2. Selecione **Mais Serviços**, procure o **Intune** e, em seguida, selecione **Intune**.
3. Selecione **Inscrição de dispositivos** > **Restrições de inscrição**.
4. Em **Restrições de Tipos de Dispositivos** > selecione a restrição que pretende definir > **Propriedades** > **Selecionar plataformas**. Selecione **Permitir** ou **Bloquear** para cada plataforma listada.
    ![Captura de ecrã para permitir ou bloquear uma plataforma](media/enrollment-restrictions-set/platform-allow-block.png)
5. Escolha **OK**.
6. Selecione **Configurar plataformas**.
    ![Captura de ecrã para configurar plataformas](media/enrollment-restrictions-set/configure-platforms.png)
7. Selecione as **Versões** mínimas e máximas para as plataformas apresentadas. Os formatos suportados pelas versões são os seguintes:
    - O perfil de trabalho do Android suporta major.minor.rev.build.
    - O iOS suporta major.minor.rev. As versões do sistema operativo não se aplicam aos dispositivos Apple inscritos com o Programa de Registo de Aparelho, o Apple School Manager ou a aplicação Apple Configurator.
    - O Windows suporta major.minor.rev.build apenas para Windows 10.
8. Selecione se pretende **Permitir** ou **Bloquear** dispositivos de **Propriedade pessoal** para cada plataforma apresentada.
9. Escolha **OK**.

### <a name="blocking-personal-android-devices"></a>Bloquear dispositivos Android pessoais
- Se bloquear a inscrição de dispositivos pessoais Android, os dispositivos pessoais com perfil de trabalho do Android continuarão a poder ser inscritos.
- Por predefinição, as definições dos dispositivos com perfil de trabalho do Android são as mesmas que as definições dos seus dispositivos Android. Depois de alterar as definições do perfil de trabalho do Android, este já não será o caso.
- Se bloquear a inscrição pessoal do perfil de trabalho do Android, só será possível inscrever dispositivos Android empresariais como perfil de trabalho do Android.

### <a name="blocking-personal-windows-devices"></a>Bloquear dispositivos Windows pessoais
Se bloquear a inscrição de dispositivos Windows de propriedade pessoal, o Intune verifica se cada novo pedido de inscrição do Windows foi autorizado como uma inscrição empresarial. As inscrições não autorizadas serão bloqueadas.

Os seguintes métodos estão qualificados como autorizados como uma inscrição empresarial Windows:
 - A inscrição de utilizadores está a utilizar uma [conta do gestor de inscrição de dispositivos]( device-enrollment-manager-enroll.md).
- O dispositivo é inscrito através do [Windows AutoPilot](enrollment-autopilot.md).
- O dispositivo está registado no Windows Autopilot, mas não é uma opção de apenas inscrição na MDM a partir das Definições do Windows.
- O número IMEI do dispositivo é apresentado em **Inscrição de dispositivos** > **[Identificadores de dispositivos da empresa](corporate-identifiers-add.md)**. (Não suportado para o Windows Phone 8.1.)
- O dispositivo é inscrito através de um [pacote de aprovisionamento em massa](windows-bulk-enroll.md).
- O dispositivo é inscrito através da [inscrição automática do SCCM para cogestão](https://docs.microsoft.com/sccm/core/clients/manage/co-management-overview#how-to-configure-co-management.md).
 
As inscrições seguintes estão marcadas como empresariais pelo Intune, mas uma vez que não oferecem ao administrador do Intune controlo por dispositivo, serão bloqueadas:
 - [Inscrição na MDM automática](windows-enroll.md#enable-windows-10-automatic-enrollment) com [associação do Azure Active Directory durante a configuração do Windows](https://docs.microsoft.com/azure/active-directory/device-management-azuread-joined-devices-frx)\*.
- [Inscrição na MDM automática](windows-enroll.md#enable-windows-10-automatic-enrollment) com [associação do Azure Active Directory a partir das definições do Windows](https://docs.microsoft.com/azure/active-directory/user-help/user-help-register-device-on-network)*.
 
Os seguintes métodos de inscrição pessoal também serão bloqueados:
- [Inscrição na MDM automática](windows-enroll.md#enable-windows-10-automatic-enrollment) com [Adicionar Conta Profissional a partir das Definições do Windows](https://docs.microsoft.com/azure/active-directory/user-help/user-help-join-device-on-network)\*.
- Opção [Apenas inscrição na MDM]( https://docs.microsoft.com/windows/client-management/mdm/mdm-enrollment-of-windows-devices#connecting-personally-owned-devices-bring-your-own-device) a partir das Definições do Windows.

\* Não serão bloqueados se estiverem registados no Autopilot.

## <a name="set-device-limit-restrictions"></a>Definir restrições de limite de dispositivos

Pode alterar as definições de uma restrição de limite de dispositivos ao seguir estes passos:

1. Inicie sessão no portal do Azure.
2. Selecione **Mais Serviços**, procure o **Intune** e, em seguida, selecione **Intune**.
3. Selecione **Inscrição de dispositivos** > **Restrições de inscrição**.
4. Em **Restrições de Limite de Dispositivos**, selecione a restrição que pretende definir.
5. Selecione **Limite de Dispositivos** e, em seguida, na lista pendente, selecione o número máximo de dispositivos que um utilizador pode inscrever.
    ![Painel de restrições de limites de dispositivos, com as restrições de limites de dispositivos](./media/device-restrictions-limit.png)
6. Selecione **Guardar**.


Durante a inscrição de BYOD, os utilizadores veem uma notificação que irá informar quando atingirem o respetivo limite de dispositivos inscritos. Por exemplo, no iOS, tem o seguinte aspeto:

![Notificação de limite do dispositivo iOS](./media/enrollment-restrictions-ios-set-limit-notification.png)

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
