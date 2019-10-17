---
title: Gerir dispositivos com o Microsoft Intune – Azure | Microsoft Docs
description: Reveja os dispositivos que gere com o Microsoft Intune, incluindo uma lista de dispositivos exportada para um ficheiro no formato csv, veja os seus dispositivos associados ao Azure Active Directory, consulte um registo de alterações de ações no dispositivo, utilize o TeamViewer Connector para permitir que os administradores de TI resolvam remotamente problemas em dispositivos Android e veja todas as ações que consegue executar nos seus dispositivos.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 09/19/2018
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
ms.openlocfilehash: a3ee6240d9efb0d09c41a6a9b1260cd4189927a8
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72509428"
---
# <a name="what-is-microsoft-intune-device-management"></a>O que é a gestão de dispositivos do Microsoft Intune?

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Enquanto administrador de TI, tem de garantir que os dispositivos geridos estão a disponibilizar os recursos de que os seus utilizadores precisam para trabalhar ao proteger os dados contra riscos.

A carga de trabalho **Dispositivos** dá-lhe informações aprofundadas sobre os dispositivos que gere e permite-lhe realizar tarefas remotas nesses dispositivos.

## <a name="get-to-your-devices"></a>Aceder aos seus dispositivos

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. Selecione **Dispositivos**. Esta vista mostra informações detalhadas sobre os dispositivos dos utilizadores e o que pode fazer com as mesmas, incluindo:

   - **Descrição geral:** mostra um instantâneo visual dos dispositivos inscritos e também mostra quantos dispositivos estão a utilizar as diferentes plataformas, incluindo Android, iOS e mais.
   - **Todos os dispositivos:** mostra uma lista dos dispositivos inscritos que está a gerir.

     Utilize a funcionalidade **Exportar** para criar uma lista .csv de todos os dispositivos, em incrementos de 10 000 (Internet Explorer) ou 30 000 (Microsoft Edge, Chrome).

     Selecione qualquer dispositivo para [Exibir detalhes adicionais sobre esse dispositivo](device-inventory.md), incluindo detalhes de hardware, aplicativos instalados, seu status de política de conformidade e muito mais.

   - **Dispositivos do Azure AD:** mostra uma lista dos dispositivos registados ou associados ao Azure Active Directory (Azure AD). Saiba mais sobre a [gestão de dispositivos do Azure AD](https://docs.microsoft.com/azure/active-directory/device-management-introduction).
   - **Ações do dispositivo:** inclui um histórico das ações remotas realizadas nos diferentes dispositivos, incluindo a ação, o respetivo estado, quem a iniciou e quando.

     ![Captura de ecrã das ações de monitorização do dispositivo](./media/device-management/monitor-device-actions.png)

   - **Registos de auditoria:** é um registo das atividades que geram uma alteração no Microsoft Intune. O tópico [Registos de auditoria](../fundamentals/monitor-audit-logs.md) fornece mais detalhes.
   - **Conector do TeamViewer:** é um serviço que permite que os utilizadores de dispositivos Android geridos pelo Intune obtenham assistência remota por parte do administrador de TI. Saiba mais sobre o [TeamViewer](teamviewer-support.md).
   - **Ajuda e Suporte:** fornece um atalho para sugestões de resolução de problemas, pedir suporte ou verificar o estado do Intune.

## <a name="available-device-actions"></a>Ações do dispositivo disponíveis
As ações disponíveis dependem da plataforma do dispositivo e da configuração do dispositivo.

- [Ver o inventário de dispositivos](device-inventory.md)
- Realize as ações remotas de dispositivos:
  - [Extinguir](devices-wipe.md#retire)
  - [Eliminação](devices-wipe.md#wipe)
  - [Bloqueio remoto](device-remote-lock.md)
  - [Repor código de acesso](device-passcode-reset.md)
  - [Ignorar Bloqueio de Ativação](device-activation-lock-bypass.md) (apenas em iOS)
  - [Começar do Zero](device-fresh-start.md) (apenas no Windows)
  - [Modo perdido](device-lost-mode.md) (apenas em iOS)
  - [Localizar dispositivo](device-locate.md) (apenas em iOS)
  - [Reiniciar](device-restart.md) (apenas no Windows)
  - [Reposição do PIN do Windows 10](device-windows-pin-reset.md)
  - [Controlo remoto do Android](teamviewer-support.md)
  - [Sincronizar o dispositivo](device-sync.md)
  - [Enviar notificação personalizada](custom-notifications.md#send-a-custom-notification-to-a-single-device) (Android, Ios)

## <a name="next-steps"></a>Próximos passos

- Em **Todos os dispositivos**, selecione um dispositivo para ver mais detalhes sobre esse dispositivo específico.
- Selecione **Ações do dispositivo** para ver o estado das ações efetuadas nos dispositivos que gere.
