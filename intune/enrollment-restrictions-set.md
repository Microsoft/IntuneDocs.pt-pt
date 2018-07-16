---
title: Definir restrições de inscrição no Microsoft Intune
titlesuffix: ''
description: Restrinja a inscrição por plataforma e defina um limite de inscrição de dispositivos no Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 9691982c-1a03-4ac1-b7c5-73087be8c5f2
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 7eee5baebb8373488999a5e75db5288e483379e5
ms.sourcegitcommit: 98b444468df3fb2a6e8977ce5eb9d238610d4398
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/07/2018
ms.locfileid: "37905823"
---
# <a name="set-enrollment-restrictions"></a>Definir restrições de inscrição

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Como administrador do Intune, pode criar e gerir as restrições de inscrição que definem o número e o tipo de dispositivos que podem ser inscritos para serem geridos com o Intune. Pode criar múltiplas restrições e aplicá-las a diferentes grupos de utilizadores. Pode definir uma [ordem de prioridade](#change-enrollment-restriction-priority) para as diferentes restrições.

>[!NOTE]
>As restrições de inscrição não são funcionalidades de segurança. A identidade dos dispositivos pode ser falsificada de forma a contornar estas restrições. Estas restrições são uma forma de dissuadir utilizadores sem fins maliciosos.

>[!NOTE]
>As funcionalidades de prioridade e restrições de inscrição atribuídas a grupos mencionadas neste artigo estão a ser implementadas na base de clientes do Intune. Até esta implementação ser concluída, poderá não ter acesso às funcionalidades de prioridade e grupo.

As restrições de inscrição específicas que pode criar incluem:

- Número máximo de dispositivos inscritos.
- Plataformas de dispositivos que podem ser inscritas:
  - Android.
  - Perfil de trabalho do Android.
  - iOS.
  - macOS.
  - Windows.
- Versão do sistema operativo da plataforma para iOS, Android, perfil de trabalho do Android e Windows. (Apenas as versões do Windows 10 podem ser utilizadas. Deixe em branco se o Windows 8.1 for permitido.)
  - Versão mínima.
  - Versão máxima.
- Restringir dispositivos pessoais (apenas para iOS, Android, perfil de trabalho do Android ou macOS).

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

Pode alterar as definições de uma restrição de tipos de dispositivo ao seguir estes passos:

1. Inicie sessão no portal do Azure.
2. Selecione **Mais Serviços**, procure o **Intune** e, em seguida, selecione **Intune**.
3. Selecione **Inscrição de dispositivos** > **Restrições de inscrição**.
4. Em **Restrições de Tipos de Dispositivos**, selecione a restrição que pretende definir.
5. No nome da restrição (**Todos os Utilizadores** para a restrição predefinida), selecione **Plataformas**. Selecione **Permitir** ou **Bloquear** para cada plataforma listada.
6. Selecione **Guardar**.
7. No nome da restrição (**Todos os Utilizadores** para a restrição predefinida), selecione **Configurações de Plataformas**. Em seguida, selecione as **Versões** mínimas e máximas para as plataformas listadas. As versões suportadas incluem:
    - O perfil de trabalho do Android suporta major.minor.rev.build.
    - O iOS suporta major.minor.rev.
    - O Windows suporta major.minor.rev.build apenas para Windows 10.
  As versões do sistema operativo não se aplicam aos dispositivos Apple inscritos com o Programa de Registo de Aparelho, o Apple School Manager ou a aplicação Apple Configurator.
8. Especifique se quer **Permitir** ou **Bloquear** dispositivos **pessoais** para cada plataforma listada.
    ![Área de trabalho de restrições de dispositivos, com as configurações de plataformas de dispositivos predefinidas a mostrar as definições de dispositivos pessoais que foram configuradas](media/device-restrictions-platform-configurations.png)
9. Selecione **Guardar**.


>[!NOTE]
>- Se bloquear a inscrição de dispositivos pessoais Android, os dispositivos pessoais com perfil de trabalho do Android continuarão a poder ser inscritos.
>- Por predefinição, as definições dos dispositivos com perfil de trabalho do Android são as mesmas que as definições dos seus dispositivos Android. Depois de alterar as definições do perfil de trabalho do Android, este já não será o caso.
>- Se bloquear a inscrição pessoal do perfil de trabalho do Android, só será possível inscrever dispositivos Android empresariais como perfil de trabalho do Android.

## <a name="set-device-limit-restrictions"></a>Definir restrições de limite de dispositivos

Pode alterar as definições de uma restrição de limite de dispositivos ao seguir estes passos:

1. Inicie sessão no portal do Azure.
2. Selecione **Mais Serviços**, procure o **Intune** e, em seguida, selecione **Intune**.
3. Selecione **Inscrição de dispositivos** > **Restrições de inscrição**.
4. Em **Restrições de Limite de Dispositivos**, selecione a restrição que pretende definir.
5. Selecione **Limite de Dispositivos** e, em seguida, na lista pendente, selecione o número máximo de dispositivos que um utilizador pode inscrever.
    ![Painel de restrições de limites de dispositivos, com as restrições de limites de dispositivos](./media/device-restrictions-limit.png)
6. Selecione **Guardar**.


Os utilizadores verão uma notificação que os irá informar quando atingirem o limite de dispositivos inscritos. Por exemplo, no iOS, tem o seguinte aspeto:

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
