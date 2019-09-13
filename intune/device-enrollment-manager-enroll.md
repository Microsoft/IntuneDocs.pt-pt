---
title: Inscrever dispositivos com uma conta do gestor de inscrição de dispositivos
titleSuffix: Microsoft Intune
description: Utilize a conta do gestor de inscrição de dispositivos para inscrever dispositivos no Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 7196b33e-d303-4415-ad0b-2ecdb14230fd
ms.reviewer: damionw
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: c3ec5bf1ed668f5775cf5a7c46a2c19d02eb227d
ms.sourcegitcommit: 05139901411d14a85c2340c0ebae02d2c178a851
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/11/2019
ms.locfileid: "70905022"
---
# <a name="enroll-devices-in-intune-by-using-a-device-enrollment-manager-account"></a>Inscrever dispositivos no Intune ao utilizar uma conta de Gestor de inscrição de dispositivos

Pode inscrever até 1000 dispositivos móveis com uma única conta do Azure Active Directory ao utilizar uma conta do gestor de inscrição de dispositivos (DEM). O DEM é uma permissão do Intune que pode ser aplicada a uma conta de utilizador do AAD e que permite que o utilizador inscreva até 1000 dispositivos. Uma conta DEM é útil para cenários onde os dispositivos são inscritos e preparados antes de serem distribuídos aos utilizadores. Por design, há um limite de 25 contas do DEM (Gerenciador de registro de dispositivo) em Microsoft Intune.

## <a name="limitations-of-devices-that-are-enrolled-with-a-dem-account"></a>Limitações dos dispositivos inscritos com uma conta DEM

As contas de utilizador DEM e os dispositivos que estão inscritos com uma conta de utilizador DEM têm as seguintes limitações:

- Uma licença do Intune deve ser atribuída a um usuário da conta do DEM.
- A limpeza não pode ser feita a partir do Portal da Empresa. A limpeza de um dispositivo inscrito por uma conta de utilizador DEM pode ser feita no portal do Azure a partir do Intune.
- Apenas o dispositivo local é apresentado na aplicação Portal da Empresa ou do site.
- As contas de utilizador DEM não podem utilizar aplicações Apple Volume Purchase Program (VPP) com licenças de utilizador Apple VPP devido aos requisitos do ID Apple por utilizador para a gestão de aplicações.
- Os dispositivos podem instalar as aplicações VPP se tiverem licenças do dispositivo Apple VPP.
- Dispositivos estão bloqueados para o acesso condicional com a exceção do Windows 10 versão 1803 +
- Todos os dispositivos registrados com as contas do DEM precisam ser devidamente licenciados para serem gerenciados pelo Intune. A licença pode ser uma licença de usuário do Intune ou uma licença de dispositivo do Intune.
- Se você estiver [registrando dispositivos de perfil de trabalho do Android Enterprise](android-work-profile-enroll.md) usando uma conta do DEM, haverá um limite de 10 dispositivos que podem ser registrados por conta.


## <a name="add-a-device-enrollment-manager"></a>Adicionar um gestor de inscrição de dispositivos

1. No [Intune no portal do Azure](https://aka.ms/intuneportal), selecione **Inscrição de dispositivos** > **Gestores de inscrições de dispositivos**.

2. Selecione **Adicionar**.

3. No painel **Adicionar Utilizador**, introduza um nome principal para o utilizador DEM e selecione **Adicionar**. O utilizador DEM é adicionado à lista de utilizadores DEM.

## <a name="permissions-for-dem"></a>Permissões para DEM

As funções de Administrador Global ou Administrador de Serviço do Intune no Azure AD são necessárias para:
- Atribuir uma permissão de DEM a uma conta de utilizador do Azure AD
- Ver todos os utilizadores DEM

Se um utilizador não tiver uma função de Administrador Global ou Administrador de Serviço do Intune atribuída, mas tiver permissões de leitura ativadas para a função de Gestores de Inscrição de Dispositivos atribuída ao mesmo, só poderá ver os utilizadores DEM que criou.


## <a name="remove-device-enrollment-manager-permissions"></a>Remover as permissões de gestor de inscrição de dispositivos

A remoção de um gestor de inscrição de dispositivos não afeta os dispositivos inscritos.

**Para remover um gestor de inscrição de dispositivos**

1. No [Intune, no portal do Azure](https://aka.ms/intuneportal), selecione **Inscrição de dispositivos** e, em seguida, selecione **Gestores de inscrições de dispositivos**.
2. No painel **Gestores de inscrições de dispositivos**, selecione o gestor de inscrição de dispositivos e selecione **Eliminar**.

