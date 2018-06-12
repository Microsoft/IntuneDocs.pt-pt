---
title: Ver perfis de dispositivo com o Microsoft Intune – Azure | Microsoft Docs
description: Veja e faça a gestão dos detalhes do perfil de configuração do dispositivo no Microsoft Intune para ver um gráfico do número de dispositivos atribuídos a um perfil e que dispositivos têm perfis atribuídos ou implementados.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 05/23/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 9deaed87-fb4b-4689-ba88-067bc61686d7
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: bffb6832200379fca0221d8718afdebe06163980
ms.sourcegitcommit: 97b9f966f23895495b4c8a685f1397b78cc01d57
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34744793"
---
# <a name="monitor-device-profiles-in-microsoft-intune"></a>Monitorizar perfis de dispositivos no Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

O Intune inclui algumas funcionalidades no portal do Azure para ajudar a monitorizar e a gerir os perfis de configuração do dispositivo. Por exemplo, pode verificar o estado de um perfil, ver que dispositivos estão atribuídos e atualizar as propriedades de um perfil.

## <a name="view-existing-profiles"></a>Ver perfis existentes

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços**, filtre por **Intune** e selecione **Microsoft Intune**.
3. Selecione **Configuração do dispositivo** > **Perfis**.

Todos os perfis existentes estão listados e incluem detalhes como a plataforma e se o perfil está atribuído a algum dispositivo.

## <a name="view-details-on-a-profile"></a>Ver detalhes de um perfil

Depois de criar o perfil do dispositivo, o Intune disponibiliza gráficos. Estes gráficos apresentam o estado de um perfil, como a atribuição com êxito a dispositivos ou se o perfil mostra um conflito.

1. Selecione um perfil existente. Por exemplo, selecione um perfil do macOS.
2. Selecione o separador **Descrição geral**.

    O gráfico na parte superior mostra o número de dispositivos atribuídos ao perfil do dispositivo específico. Por exemplo, se o perfil de configuração do dispositivo se aplicar a dispositivos iOS, o gráfico apresentará a contagem de dispositivos macOS.

    Também mostra o número de dispositivos de outras plataformas que são atribuídos ao mesmo perfil do dispositivo. Por exemplo, mostra a contagem de dispositivos não macOS.

    ![Ver o número de dispositivos atribuídos ao perfil do dispositivo](./media/device-configuration-profile-graphical-chart.png)

    O gráfico na parte inferior mostra o número de utilizadores atribuídos ao perfil do dispositivo específico. Por exemplo, se o perfil de configuração do dispositivo se aplicar a utilizadores do macOS, o gráfico apresentará a contagem de utilizadores do macOS.

3. Selecione o círculo no gráfico na parte superior. O **Estado do dispositivo** é apresentado.

    São listados os dispositivos atribuídos ao perfil, além de indicar se o perfil foi implementado com êxito. Note também que apenas lista os dispositivos com a plataforma específica (por exemplo, macOS).

    Feche os detalhes do **Estado do dispositivo**.

4. Selecione o círculo no gráfico na parte inferior. O **Estado do utilizador** é apresentado. 

    São indicados os utilizadores atribuídos ao perfil, além de indicar se o perfil foi implementado com êxito. Note também que apenas indica os utilizadores com a plataforma específica (por exemplo, macOS).

    Feche os detalhes do **Estado do utilizador**.

5. Novamente na lista **Perfis**, selecione um perfil específico. Também pode alterar as propriedades existentes:
  - **Propriedades**: altere o nome ou atualize as definições existentes.
  - **Atribuições**: inclua ou exclua dispositivos que a política deve aplicar. Escolha **Grupos Selecionados** para escolher grupos específicos.
  - **Estado do dispositivo**: são listados os dispositivos atribuídos ao perfil, além de indicar se o perfil foi implementado com êxito. Pode selecionar um dispositivo específico para obter ainda mais detalhes, incluindo as aplicações instaladas.
  - **Estado do utilizador**: lista os nomes dos utilizadores com dispositivos afetados por este perfil e se o perfil foi implementado com êxito. Pode selecionar um utilizador específico para obter ainda mais detalhes.
  - **Estado por definição**: filtra os resultados ao mostrar as definições individuais no perfil e mostra se a definição foi aplicada com êxito.

## <a name="next-steps"></a>Próximos passos
[Atribuir perfis de utilizador e de dispositivo](device-profile-assign.md)  
[Problemas comuns com os perfis de dispositivos e soluções](device-profile-troubleshoot.md)