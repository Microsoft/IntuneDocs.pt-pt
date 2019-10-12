---
title: Definir restrições de registro no Microsoft Intune
titleSuffix: ''
description: Restrinja o registro por plataforma e defina um limite de registro de dispositivo no Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/17/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 9691982c-1a03-4ac1-b7c5-73087be8c5f2
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d96cd3e6496bbfde35a666bfcf4a1f6427e45173
ms.sourcegitcommit: 11ae6a37527ef5b3ac042743950254f3ef559c53
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/11/2019
ms.locfileid: "72280244"
---
# <a name="set-enrollment-restrictions"></a>Definir restrições de registro

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Como administrador do Intune, você pode criar e gerenciar restrições de registro que definem quais dispositivos podem ser registrados no gerenciamento com o Intune, incluindo:
- número de dispositivos
- sistemas operacionais e versões você pode criar várias restrições e aplicá-las a diferentes grupos de usuários. Você pode definir a [ordem de prioridade](#change-enrollment-restriction-priority) para suas diferentes restrições.

>[!NOTE]
>As restrições de registro não são recursos de segurança. Os dispositivos comprometidos podem disfarçar seu caractere. Essas restrições são uma barreira de melhor esforço para usuários não mal-intencionados.

As restrições de registro específicas que você pode criar incluem:

- Número máximo de dispositivos registrados.
- Plataformas de dispositivo que podem ser registradas:
  - Administrador do dispositivo Android
  - Perfil de trabalho do Android Enterprise
  - iOS
  - macOS
  - Windows
  - Windows Mobile
- Versão do sistema operacional da plataforma para iOS, administrador do dispositivo Android, perfil de trabalho do Android Enterprise, Windows e Windows Mobile. (Somente as versões do Windows 10 podem ser usadas. Deixe em branco se Windows 8.1 for permitido.)
  - Versão mínima.
  - Versão máxima.
- Restringir dispositivos de propriedade pessoal (iOS, administrador de dispositivo Android, perfil de trabalho corporativo do Android, macOS, Windows e Windows Mobile somente).

## <a name="default-restrictions"></a>Restrições padrão

As restrições padrão são fornecidas automaticamente para restrições de registro de tipo de dispositivo e limite de dispositivo. Você pode alterar as opções para os padrões. As restrições padrão aplicam-se a todos os registros de usuário e de usuário. Você pode substituir esses padrões criando novas restrições com prioridades mais altas.

## <a name="create-a-device-type-restriction"></a>Criar uma restrição de tipo de dispositivo

1. Inicie sessão no Portal do Azure.
2. Selecione **mais serviços**, pesquise **Intune**e, em seguida, escolha **Intune**.
3. Selecione **registro de dispositivo**@no__t-**1 restrições de registro** > **criar restrição** > **restrição de tipo de dispositivo**.
    limite de @no__t 0Screen para a criação de uma restrição de tipo de dispositivo @ no__t-1
4. Na página **noções básicas** , dê à restrição um **nome** e uma **Descrição**opcional.
5. Escolha **Avançar** para ir para a página **configurações de plataforma** .
6. Em **plataforma**, escolha **permitir** para as plataformas que você deseja que essa restrição permita.
    limite de @no__t 0Screen para escolher as configurações de plataforma @ no__t-1
7. Em **versões**, escolha as versões mínima e máxima às quais você deseja que as plataformas permitidas ofereçam suporte. As restrições de versão se aplicam somente a dispositivos registrados com o Portal da Empresa.
     Os formatos de versão com suporte incluem:
    - O administrador do dispositivo Android e o perfil de trabalho do Android Enterprise dão suporte ao principal. Minor. Rev. Build.
    - o iOS dá suporte a Major. Minor. Rev. As versões do sistema operacional não se aplicam a dispositivos Apple que se registram com o Programa de registro de dispositivos, Apple School Manager ou o aplicativo Apple Configurator.
    - O Windows dá suporte a Major. Minor. Build. Rev somente para Windows 10.
    > [!Note]
    > O Windows 10 não fornece o número Rev durante o registro, por exemplo, se você inserir em 10.0.17134.100 e o dispositivo for 10.0.17134.174, ele será bloqueado durante o registro.

8. Em **pessoal de propriedade**, escolha **permitir** para as plataformas que você deseja permitir como dispositivos de propriedade pessoal.
9. Escolha **Avançar** para ir para a página **atribuições** .
10. Escolha **Selecionar grupos para incluir** e, em seguida, use a caixa Pesquisar para localizar os grupos que você deseja incluir nessa restrição. A restrição aplica-se somente aos grupos aos quais ele está atribuído. Se você não atribuir uma restrição a pelo menos um grupo, ele não terá nenhum efeito. Em seguida, escolha **selecionar**. 
    limite de @no__t 0Screen para escolher as configurações de plataforma @ no__t-1
11. Selecione **Avançar** para ir para a página **revisar + criar** .
12. Selecione **criar** para criar a restrição.
13. A nova restrição é criada com uma prioridade logo acima do padrão. Você pode [alterar a prioridade](#change-enrollment-restriction-priority).


## <a name="create-a-device-limit-restriction"></a>Criar uma restrição de limite de dispositivo

1. Inicie sessão no Portal do Azure.
2. Selecione **mais serviços**, pesquise **Intune**e, em seguida, escolha **Intune**.
3. Selecione **registro de dispositivo**@no__t-**1 restrições de registro** > **criar restrição** > **restrição de limite de dispositivo**.
    limite de @no__t 0Screen para a criação de uma restrição de limite de dispositivo @ no__t-1
4. Na página **noções básicas** , dê à restrição um **nome** e uma **Descrição**opcional.
5. Escolha **Avançar** para ir para a página **limite de dispositivo** .
6. Para **limite de dispositivo**, selecione o número máximo de dispositivos que um usuário pode registrar.
    0Screen-Cap para escolher o limite de dispositivo @ no__t-1 @no__t
7. Escolha **Avançar** para ir para a página **atribuições** .
8. Escolha **Selecionar grupos para incluir** e, em seguida, use a caixa Pesquisar para localizar os grupos que você deseja incluir nessa restrição. A restrição aplica-se somente aos grupos aos quais ele está atribuído. Se você não atribuir uma restrição a pelo menos um grupo, ele não terá nenhum efeito. Em seguida, escolha **selecionar**. 
    limite de @no__t 0Screen para selecionar grupos @ no__t-1
11. Selecione **Avançar** para ir para a página **revisar + criar** .
12. Selecione **criar** para criar a restrição.
13. A nova restrição é criada com uma prioridade logo acima do padrão. Você pode [alterar a prioridade](#change-enrollment-restriction-priority).

Durante os registros de BYOD, os usuários veem uma notificação que informa quando eles atingiram seu limite de dispositivos registrados. Por exemplo, em iOS:

![notificação de limite de dispositivo iOS](./media/enrollment-restrictions-set/enrollment-restrictions-ios-set-limit-notification.png)

> [!IMPORTANT]
> Restrições de limite de dispositivo não se aplicam aos seguintes tipos de registro do Windows:
> - Registros cogerenciados
> - Registros de GPO
> - Azure Active Directory de registros associados
> - Registros ingressados Azure Active Directory em massa
> - Registros do piloto automático
> - Registros do Gerenciador de registro de dispositivos
>
> Restrições de limite de dispositivo não são impostas para esses tipos de registro porque são consideradas cenários de dispositivo compartilhado.
> Você pode definir limites rígidos para esses tipos [de registro no Azure Active Directory](https://docs.microsoft.com/azure/active-directory/devices/device-management-azure-portal#configure-device-settings).


## <a name="change-enrollment-restrictions"></a>Alterar restrições de registro

Você pode alterar as configurações de uma restrição de registro seguindo as etapas abaixo. Essas restrições não afetam os dispositivos que já foram registrados. Os dispositivos registrados com o [agente de computador do Intune](../fundamentals/manage-windows-pcs-with-microsoft-intune.md) não podem ser bloqueados com esse recurso.

1. Inicie sessão no Portal do Azure.
2. Selecione **mais serviços**, pesquise **Intune**e, em seguida, escolha **Intune**.
3. Selecione **registro de dispositivo** > **restrições de registro** > escolha a restrição que você deseja alterar > **Propriedades**.
4. Escolha **Editar** ao lado das configurações que você deseja alterar.
5. Na página **Editar** , faça as alterações desejadas e prossiga para a página **examinar + salvar** e, em seguida, escolha **salvar**.


## <a name="blocking-personal-android-devices"></a>Bloqueando dispositivos Android pessoais
- Se você bloquear dispositivos pessoais de administrador de dispositivo Android do registro, os dispositivos de perfil de trabalho corporativo Android Enterprise ainda poderão ser registrados.
- Por padrão, suas configurações de dispositivos de perfil de trabalho do Android Enterprise são as mesmas que suas configurações para dispositivos de administrador de dispositivo Android. Depois de alterar o perfil de trabalho do Android Enterprise ou as configurações do administrador do dispositivo Android, esse não é mais o caso.
- Se você bloquear o registro de perfil de trabalho do Android Enterprise pessoal, somente dispositivos Android corporativos poderão ser registrados com perfis de trabalho do Android Enterprise.

## <a name="blocking-personal-windows-devices"></a>Bloqueando dispositivos Windows pessoais
Se você bloquear dispositivos do Windows de propriedade pessoal do registro, o Intune verificará se cada nova solicitação de registro do Windows foi autorizada como um registro corporativo. Os registros não autorizados serão bloqueados.

Os métodos a seguir se qualificam como sendo autorizados como um registro corporativo do Windows:
- O usuário registrador está usando uma [conta de Gerenciador de registro de dispositivos]( device-enrollment-manager-enroll.md).
- O dispositivo é registrado por meio do [piloto automático do Windows](enrollment-autopilot.md).
- O dispositivo está registrado no Windows AutoPilot, mas não é uma opção somente registro de MDM das configurações do Windows.
- O número IMEI do dispositivo é listado no **registro de dispositivo** >  **[identificadores de dispositivo corporativo](corporate-identifiers-add.md)** . (Sem suporte para Windows Phone 8,1.)
- O dispositivo é registrado por meio de um [pacote de provisionamento em massa](windows-bulk-enroll.md).
- O dispositivo é registrado por meio de GPO ou [registro automático do SCCM para o cogerenciamento](https://docs.microsoft.com/sccm/comanage/quickstart-paths#bkmk_path1).
 
Os seguintes registros são marcados como corporativos pelo Intune. Mas como eles não oferecem o controle por dispositivo do administrador do Intune, eles serão bloqueados:
- [Registro automático de MDM](windows-enroll.md#enable-windows-10-automatic-enrollment) com [Azure Active Directory ingressar durante a instalação do Windows](https://docs.microsoft.com/azure/active-directory/device-management-azuread-joined-devices-frx)\*.
- [Registro automático de MDM](windows-enroll.md#enable-windows-10-automatic-enrollment) com [Azure Active Directory ingressar das configurações do Windows](https://docs.microsoft.com/azure/active-directory/user-help/user-help-register-device-on-network)*.
 
Os seguintes métodos de registro pessoal também serão bloqueados:
- [Registro automático de MDM](windows-enroll.md#enable-windows-10-automatic-enrollment) com [adicionar conta de trabalho das configurações do Windows](https://docs.microsoft.com/azure/active-directory/user-help/user-help-join-device-on-network)\*.
- Opção [somente registro de MDM]( https://docs.microsoft.com/windows/client-management/mdm/mdm-enrollment-of-windows-devices#connecting-personally-owned-devices-bring-your-own-device) das configurações do Windows.

\* eles não serão bloqueados se registrados com o piloto automático.


## <a name="change-enrollment-restriction-priority"></a>Alterar prioridade de restrição de registro

A prioridade é usada quando um usuário existe em vários grupos que recebem restrições. Os usuários estão sujeitos apenas à restrição de prioridade mais alta atribuída a um grupo no qual estão. Por exemplo, Joe está no grupo A atribuído a restrições de prioridade 5 e também no grupo B atribuído às restrições de prioridade 2. Joe está sujeito apenas às restrições de prioridade 2.

Quando você cria uma restrição, ela é adicionada à lista logo acima do padrão.

O registro de dispositivo inclui restrições padrão para restrições de limite de dispositivo e tipo de dispositivo. Essas duas restrições se aplicam a todos os usuários, a menos que sejam substituídas por restrições de prioridade mais alta.

Você pode alterar a prioridade de qualquer restrição não padrão.

1. Inicie sessão no Portal do Azure.
2. Selecione **mais serviços**, pesquise **Intune**e, em seguida, escolha **Intune**.
3. Selecione **registro de dispositivo** > **restrições de registro**.
4. Passe o mouse sobre a restrição na lista de prioridades.
5. Usando os três pontos verticais, arraste a prioridade para a posição desejada na lista.
