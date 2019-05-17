---
title: Configurar uma página de estado de inscrição
titleSuffix: Microsoft Intune
description: Configure uma página de saudação para os utilizadores que inscrevem dispositivos Windows 10.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/5/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 8518d8fa-a0de-449d-89b6-8a33fad7b3eb
ms.reviewer: damionw
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8d19be73472aed6b6ede1cfdc3d14007c5222c43
ms.sourcegitcommit: 1cae690ca2ac6cc97bbcdf656f54b31878297ae8
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/22/2019
ms.locfileid: "59896617"
---
# <a name="set-up-an-enrollment-status-page"></a>Configurar uma página de estado de inscrição
 
[!INCLUDE [azure_portal](./includes/azure_portal.md)]
 
Durante a configuração do dispositivo com o Intune, a Página de Estado de Inscrição apresenta as informações de instalação no dispositivo. Algumas aplicações, perfis e certificados poderão não ser instalados antes de o utilizador concluir a inscrição inicial ou iniciar sessão no dispositivo. A página de estado de inscrição pode ajudar os utilizadores a compreender o estado do respetivo dispositivo durante a configuração do mesmo. Pode criar múltiplos perfis de página de estado de inscrição e aplicá-los a grupos diferentes. Os perfis podem ser definidos para:
- Ver o progresso da instalação.
- Bloquear a utilização até à conclusão da instalação.
- Especificar o que um utilizador pode fazer se a configuração do dispositivo falhar.

Também pode definir a ordem de prioridade para cada perfil para que as atribuições de perfil em conflito do mesmo utilizador ou dispositivo sejam tidas em consideração.

> [!NOTE]
> A Página de estado de inscrição não será apresentada se apenas o dispositivo estiver num grupo atribuído. O utilizador tem de estar num grupo atribuído para ser apresentada a página de estado de inscrição.

## <a name="turn-on-default-enrollment-status-page-for-all-users"></a>Ativar a página de estado de inscrição predefinida para todos os utilizadores

Para ativar a página de estado de inscrição, siga os passos abaixo.
 
1. No [Intune](https://aka.ms/intuneportal), selecione **Inscrição de dispositivos** > **Inscrição no Windows** > **Página de Estado de Inscrição (Pré-visualização)**.
2. No painel **Página de Estado de Inscrição**, selecione **Predefinição** > **Definições**.
3. Para **Mostrar progresso de instalação de aplicações e perfis**, selecione **Sim**.
4. Selecione as outras definições que pretende ativar e, em seguida, selecione **Guardar**.

## <a name="create-enrollment-status-page-profile-and-assign-to-a-group"></a>Criar um perfil de página de estado de inscrição e atribuí-lo a um grupo

1. No [Intune](https://aka.ms/intuneportal), selecione **Inscrição de dispositivos** > **Inscrição no Windows** > **Página de Estado de Inscrição (Pré-visualização)** > **Criar perfil**.
2. Forneça um **Nome** e uma **Descrição**.
3. Selecione **Criar**.
4. Selecione o novo perfil na lista **Página de Estado de Inscrição**.
5. Selecione **Atribuições** > **Selecionar grupos** > selecione os grupos que pretende que adotem este perfil > **Selecionar** > **Guardar**.
6. Selecione **Definições** > selecione as definições que pretende aplicar a este perfil > **Guardar**.

## <a name="set-the-enrollment-status-page-priority"></a>Definir a prioridade de página de estado de inscrição

Um dispositivo ou utilizador poderá estar em múltiplos grupos e ter múltiplos perfis de página de estado de inscrição. Para lidar com esses conflitos, pode definir as prioridades de cada perfil. Se alguém tiver mais do que um perfil de página de estado de inscrição, só será aplicado o perfil com a prioridade mais alta.

1. No [Intune](https://aka.ms/intuneportal), selecione **Inscrição de dispositivos** > **Inscrição no Windows** > **Página de Estado de Inscrição (Pré-visualização)**.
2. Paire o cursor sobre o perfil na lista.
3. Utilize os três pontos verticais para arrastar o perfil para a posição pretendida na lista.

## <a name="block-access-to-a-device-until-a-specific-application-is-installed"></a>Bloquear o acesso a um dispositivo até que uma aplicação específica esteja instalada

Pode especificar que aplicações têm de ser instaladas para o utilizador poder aceder à área de trabalho.

1. No Intune, escolha **Inscrição de dispositivos**  > **Inscrição no Windows** > **Página de Estado de Inscrição (Pré-visualização)**.
2. Escolha um perfil > **Definições**.
3. Escolha **Sim** para **Mostrar progresso de instalação de aplicações e perfis**.
4. Escolha **Sim** para **Bloquear a utilização de dispositivos até que todas as aplicações e perfis sejam instalados**.
5. Escolha **Selecionado** para **Bloquear a utilização de dispositivos até que as necessárias aplicações sejam instaladas, caso estejam atribuídas ao utilizador/dispositivo**.
 6. Escolha **Selecionar aplicações** > escolha as aplicações > **Selecionar** > **Guardar**.

## <a name="enrollment-status-page-tracking-information"></a>Informações de controlo da página de estado de inscrição

A página de estado controla as informações sobre a preparação e configuração do dispositivo e sobre a configuração da conta.

### <a name="device-preparation"></a>Preparação do dispositivo

Para a preparação do dispositivo, a página de estado de inscrição controla os atestados principais do Trusted Platform Module (TPM) (quando aplicável), o progresso ao aderir ao Azure Active Directory e a inscrição no Intune.

### <a name="device-setup"></a>Configuração do dispositivo

Para a configuração do dispositivo, a página de estado de inscrição controla os seguintes itens, se estiverem atribuídos a Todos os Dispositivos:
- Políticas de segurança
    - Um fornecedor de serviços de configuração (CSO) para todas as inscrições.
    - Os CSPs configurados pelo Intune não são controlados aqui.
- Aplicações
    - Aplicações de linha de negócio (LoB) por computador.
    - As aplicações da loja de linha de negócio com contexto de instalação = Dispositivo.
    - As aplicações da loja e aplicações offline de linha de negócio com contexto de instalação = Dispositivo.
- Perfis de conectividade
    - Perfis de VPN ou de Wi-Fi atribuídos a **Todos os Dispositivos** ou a um grupo de dispositivos em que o dispositivo que está a ser inscrito é membro, mas apenas para dispositivos do Autopilot
- Perfis de certificado Wi-Fi atribuídos a **Todos os Dispositivos** ou a um grupo de dispositivos em que o dispositivo que está a ser inscrito é membro, mas apenas para dispositivos do Autopilot

### <a name="account-setup"></a>Configuração da conta
Para a configuração da conta, a página de estado de inscrição controla os seguintes itens:
- Políticas de segurança
    - Um CSP para todas as inscrições.
    - Os CSPs configurados pelo Intune não são controlados aqui.
- Aplicações
    - Aplicações MSI de linha de negócio por utilizador atribuídas a Todos os Dispositivos, Todos os Utilizadores ou a um grupo de utilizadores de que seja membro o utilizador que inscreve o dispositivo.
    - Aplicações MSI de linha de negócio por computador atribuídas a Todos os Utilizadores ou a um grupo de utilizadores de que seja membro o utilizador que inscreve o dispositivo.
    - Aplicações da loja de linha de negócio, aplicações da loja online e aplicações da loja offline que estão atribuídas a qualquer um dos seguintes:
        - Todos os Dispositivos
        - Todos os Utilizadores
        - Um grupo de utilizadores no qual o utilizador que inscreve o dispositivo é um membro com o contexto de instalação definido para Utilizador.
- Perfis de conectividade
    - Perfis de VPN e de Wi-Fi atribuídos a Todos os Utilizadores ou a um grupo de utilizadores de que seja membro o utilizador que inscreve o dispositivo.
- Certificados
    - Perfis de certificados atribuídos a Todos os Utilizadores ou a um grupo de utilizadores de que seja membro o utilizador que inscreve o dispositivo.

## <a name="next-steps"></a>Próximos passos
Depois de configurar as suas páginas de inscrição do Windows, saiba como gerir dispositivos Windows. Para obter mais informações, veja [O que é a gestão de dispositivos do Microsoft Intune?](https://docs.microsoft.com/intune/device-management)
