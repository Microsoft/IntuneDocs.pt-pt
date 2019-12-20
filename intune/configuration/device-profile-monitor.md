---
title: Ver perfis de dispositivo com o Microsoft Intune – Azure | Microsoft Docs
description: Veja e faça a gestão dos detalhes do perfil de configuração do dispositivo no Microsoft Intune para ver um gráfico do número de dispositivos atribuídos a um perfil e que dispositivos têm perfis atribuídos ou implementados. Também pode resolver problemas de perfis com definições em conflito.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 9deaed87-fb4b-4689-ba88-067bc61686d7
ms.reviewer: karthib
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 25983117864f44b8131fdc49e60b7d24048da9fe
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/19/2019
ms.locfileid: "75206657"
---
# <a name="monitor-device-profiles-in-microsoft-intune"></a>Monitorizar perfis de dispositivos no Microsoft Intune



O Intune inclui alguns recursos para ajudar a monitorar e gerenciar os perfis de configuração do dispositivo. Por exemplo, pode verificar o estado de um perfil, ver que dispositivos estão atribuídos e atualizar as propriedades de um perfil.

## <a name="view-existing-profiles"></a>Ver perfis existentes

1. Entre no centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selecione **dispositivos** > **perfis de configuração**.

Todos os perfis existentes estão listados e incluem detalhes como a plataforma e se o perfil está atribuído a algum dispositivo.

## <a name="view-details-on-a-profile"></a>Ver detalhes de um perfil

Depois de criar o perfil do dispositivo, o Intune disponibiliza gráficos. Estes gráficos apresentam o estado de um perfil, como a atribuição com êxito a dispositivos ou se o perfil mostra um conflito.

1. Selecione um perfil existente. Por exemplo, selecione um perfil do macOS.
2. Selecione o separador **Descrição geral**.

    O gráfico de nível superior mostra o número de dispositivos atribuídos ao perfil do dispositivo. Por exemplo, se o perfil de configuração do dispositivo se aplicar a dispositivos iOS, o gráfico apresentará a contagem de dispositivos macOS.

    Também mostra o número de dispositivos de outras plataformas que são atribuídos ao mesmo perfil do dispositivo. Por exemplo, mostra a contagem de dispositivos não macOS.

    ![Ver o número de dispositivos atribuídos ao perfil do dispositivo](./media/device-profile-monitor/device-configuration-profile-graphical-chart.png)

    O gráfico inferior mostra o número de usuários atribuídos ao perfil do dispositivo. Por exemplo, se o perfil de configuração do dispositivo se aplicar a utilizadores do macOS, o gráfico apresentará a contagem de utilizadores do macOS.

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
    - **Status do usuário**: lista os nomes de usuário com dispositivos afetados por esse perfil e se o perfil foi implantado com êxito. Pode selecionar um utilizador específico para obter ainda mais detalhes.
    - **Estado por definição**: filtra os resultados ao mostrar as definições individuais no perfil e mostra se a definição foi aplicada com êxito.

## <a name="view-conflicts"></a>Ver os conflitos

Em **Dispositivos** > **Todos os dispositivos**, pode ver se existem definições que estejam a causar conflitos. Quando houver um conflito, você também verá todos os perfis de configuração que contêm essa configuração. Os administradores podem utilizar esta funcionalidade para ajudar a resolver problemas e corrigir discrepâncias com os perfis.

1. No Intune, selecione **Dispositivos** > **Todos os dispositivos** e selecione um dispositivo existente na lista. Um utilizador final pode obter o nome do dispositivo a partir da aplicação Portal da Empresa.
2. Selecione **Configuração do dispositivo**. É apresentada uma lista de todas as políticas de configuração que se aplicam ao dispositivo.
3. Selecione a política. São apresentadas todas as definições existentes nessa política que se aplicam ao dispositivo. Se um dispositivo apresentar o estado **Conflito**, selecione essa linha. Na nova janela, pode ver todos os perfis e os nomes dos perfis que têm a definição a causar o conflito.

Agora que já sabe qual é a definição em conflito e as políticas que incluem essa definição, deverá ser mais fácil resolver o conflito. 

## <a name="device-firmware-configuration-interface-profile-reporting"></a>Relatório de perfil da interface de configuração do firmware do dispositivo

> [!WARNING]
> O monitoramento de perfis DFCI está sendo criado no momento. Enquanto o DFCI está em visualização pública, os dados de monitoramento podem estar ausentes ou incompletos.

Os perfis de DFCI são relatados por configuração, assim como outros perfis de configuração de dispositivo. Dependendo do suporte do fabricante do DFCI, algumas configurações podem não se aplicar.

Com as configurações de perfil do DFCI, você pode ver os seguintes Estados:

- **Compatível**: esse estado mostra quando um valor de configuração no perfil corresponde à configuração no dispositivo. Esse Estado pode ocorrer nos seguintes cenários:

  - O perfil DFCI configurou com êxito a configuração no perfil.
  - O dispositivo não tem o recurso de hardware controlado pela configuração e a configuração do perfil está **desabilitada**.
  - A UEFI não permite que o DFCI desabilite o recurso e a configuração de perfil esteja **habilitada**.
  - O dispositivo não tem o hardware para desabilitar o recurso e a configuração de perfil está **habilitada**.

- **Não aplicável**: esse estado mostra quando um valor de configuração no perfil é **habilitado**e a configuração correspondente no dispositivo não é encontrada. Esse Estado pode acontecer se o hardware do dispositivo não tiver o recurso.

- Não **compatível**: esse estado mostra quando um valor de configuração no perfil não corresponde à configuração no dispositivo. Esse Estado pode ocorrer nos seguintes cenários:

  - A UEFI não permite que o DFCI desabilite uma configuração e a configuração do perfil esteja **desabilitada**.
  - O dispositivo não tem o hardware para desabilitar o recurso e a configuração do perfil está **desabilitada**.
  - O dispositivo não tem a versão mais recente do firmware DFCI.
  - O DFCI foi desabilitado antes de ser registrado no Intune usando um controle "recusar" local no menu UEFI.
  - O dispositivo foi registrado no Intune fora do registro do AutoPilot.
  - O dispositivo não foi registrado para o piloto automático por um CSP da Microsoft ou registrado diretamente pelo OEM.

## <a name="next-steps"></a>Próximos passos

[Perguntas comuns, problemas e resoluções com perfis de dispositivo](device-profile-troubleshoot.md)  
[Solucionar problemas de políticas e perfis e no Intune](troubleshoot-policies-in-microsoft-intune.md)
