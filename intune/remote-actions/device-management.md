---
title: Gerir dispositivos com o Microsoft Intune – Azure | Microsoft Docs
description: Reveja os dispositivos que gere com o Microsoft Intune, incluindo uma lista de dispositivos exportada para um ficheiro no formato csv, veja os seus dispositivos associados ao Azure Active Directory, consulte um registo de alterações de ações no dispositivo, utilize o TeamViewer Connector para permitir que os administradores de TI resolvam remotamente problemas em dispositivos Android e veja todas as ações que consegue executar nos seus dispositivos.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/14/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d2412418-d91a-4767-a3d6-bc88bb29caa2
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: bbb6a53158ff713ad3c3ff768b2a5e6b1c75605f
ms.sourcegitcommit: 25e4847ead0f56c269cfefe1e01c1b9106a28cf1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/06/2020
ms.locfileid: "78856276"
---
# <a name="what-is-microsoft-intune-device-management"></a>O que é a gestão de dispositivos do Microsoft Intune?

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Enquanto administrador de TI, tem de garantir que os dispositivos geridos estão a disponibilizar os recursos de que os seus utilizadores precisam para trabalhar ao proteger os dados contra riscos.

A carga de trabalho dos **Dispositivos** dá-lhe informações sobre os dispositivos que gere e permite ativar tarefas remotas nesses dispositivos.

## <a name="get-to-your-devices"></a>Aceder aos seus dispositivos

1. Inscreva-se no [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).
3. Selecione **Dispositivos**. Esta vista mostra informações detalhadas sobre os dispositivos dos utilizadores e o que pode fazer com as mesmas, incluindo:

   - **A visão geral** mostra uma imagem visual dos dispositivos matriculados, quantos dispositivos estão a usar as diferentes plataformas, e muito mais.
   - **Todos os dispositivos:** mostra uma lista dos dispositivos inscritos que está a gerir.

     Utilize a função **Export** para criar uma lista .zip de todos os dispositivos, em incrementos de 10.000 (Internet Explorer) ou 30.000 (Microsoft Edge, Chrome).

     Selecione qualquer dispositivo para [visualizar detalhes adicionais sobre esse dispositivo](device-inventory.md), como detalhes de hardware, aplicações instaladas, políticas e muito mais.

   - **Dispositivos do Azure AD:** mostra uma lista dos dispositivos registados ou associados ao Azure Active Directory (Azure AD). Saiba mais sobre a [gestão de dispositivos do Azure AD](https://docs.microsoft.com/azure/active-directory/device-management-introduction).
   - **As ações** do dispositivo incluem um histórico das ações remotas feitas em diferentes dispositivos, incluindo a ação, o seu estado, que iniciaram a ação, e a hora.

     ![Captura de ecrã das ações de monitorização do dispositivo](./media/device-management/monitor-device-actions.png)

   - **Registos de auditoria:** é um registo das atividades que geram uma alteração no Microsoft Intune. O tópico [Registos de auditoria](../fundamentals/monitor-audit-logs.md) fornece mais detalhes.
   - **Conector do TeamViewer:** é um serviço que permite que os utilizadores de dispositivos Android geridos pelo Intune obtenham assistência remota por parte do administrador de TI. Saiba mais sobre o [TeamViewer](teamviewer-support.md).
   - **Ajuda e Suporte:** fornece um atalho para sugestões de resolução de problemas, pedir suporte ou verificar o estado do Intune.

## <a name="available-device-actions"></a>Ações do dispositivo disponíveis
As ações disponíveis dependem da plataforma do dispositivo e da configuração do dispositivo.

- [Ver o inventário de dispositivos](device-inventory.md)
- Realize as ações remotas de dispositivos:
  - [Reset do piloto automático](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-autopilot-reset#reset-devices-with-remote-windows-autopilot-reset)
  - [Rotação da tecla BitLocker](../protect/encrypt-devices.md#rotate-bitlocker-recovery-keys) (apenas windows)
  - [Eliminar](devices-wipe.md#delete-devices-from-the-intune-portal)
  - [Bloqueio de ativação de desativação](device-activation-lock-disable.md) (apenas iOS)
  - [Começar do Zero](device-fresh-start.md) (apenas no Windows)
  - [Digitalização completa](../configuration/device-restrictions-windows-10.md#microsoft-defender-antivirus) (apenas windows 10)
  - [Localizar dispositivo](device-locate.md) (apenas em iOS)
  - [Modo perdido](device-lost-mode.md) (apenas em iOS)
  - [Sondagem rápida](../configuration/device-restrictions-windows-10.md#microsoft-defender-antivirus) (apenas windows 10)
  - [Controlo remoto do Android](teamviewer-support.md)
  - [Bloqueio remoto](device-remote-lock.md)
  - [Rename device (Mudar o nome de dispositivos)](device-rename.md)
  - [Repor código de acesso](device-passcode-reset.md)
  - [Reiniciar](device-restart.md) (apenas no Windows)
  - [Extinguir](devices-wipe.md#retire)
  - [Atualizar a Inteligência de Segurança do Windows Defender](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-antivirus/manage-protection-updates-windows-defender-antivirus)
  - [Reposição do PIN do Windows 10](device-windows-pin-reset.md)
  - [Eliminação](devices-wipe.md#wipe)
  - [Enviar notificação personalizada](custom-notifications.md#send-a-custom-notification-to-a-single-device) (Android, iOS/iPadOS)
  - [Sincronizar o dispositivo](device-sync.md)

## <a name="next-steps"></a>Próximos passos

- Em **Todos os dispositivos**, selecione um dispositivo para ver mais detalhes sobre esse dispositivo específico.
- Selecione **Ações do dispositivo** para ver o estado das ações efetuadas nos dispositivos que gere.
