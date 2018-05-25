---
title: Configurar uma página de estado de inscrição
titleSuffix: Microsoft Intune
description: Dê as boas-vindas aos utilizadores que estão a inscrever dispositivos com o Windows 10.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 5/17/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 8518d8fa-a0de-449d-89b6-8a33fad7b3eb
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: c6604c35cebdad4341f27a51db1a4c735f9a9818
ms.sourcegitcommit: 6bd5867c41fb5288fde114dbfcc127dd206f7148
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
---
# <a name="set-up-an-enrollment-status-page"></a>Configurar uma página de estado de inscrição
 
[!INCLUDE [azure_portal](./includes/azure_portal.md)]
 
Durante a configuração do dispositivo, a página de estado de inscrição apresenta informações sobre o estado da instalação no dispositivo do utilizador final. Algumas aplicações, perfis e certificados poderão não estar totalmente instalados quando um utilizador for inscrito. A página de estado pode ajudar os utilizadores a compreender o estado do respetivo dispositivo durante e após a inscrição. Pode ativar a página de estado para todos os seus utilizadores, bem como impedir os utilizadores de utilizar o dispositivo até que todas as aplicações e perfis atribuídos estejam instalados.
 
Para ativar a página de estado de inscrição para todos os seus utilizadores finais, siga os passos abaixo.
 
1.  No [Intune](https://aka.ms/intuneportal), selecione **Inscrição de dispositivos** > **Inscrição no Windows** > **Página de Estado de Inscrição (Pré-visualização)**.
2.  No painel **Página de Estado de Inscrição**, selecione **Predefinição** > **Definições**.
3.  Para **Mostrar progresso de instalação de aplicações e perfis**, selecione **Sim**.
4.  Selecione as outras definições que pretende ativar e, em seguida, selecione **Guardar**.
 
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
- Os perfis de conectividade (VPN e Wi-Fi) ainda não são controlados, pelo que apresentarão sempre "0 de 0".
- Os certificados ainda não são controlados, pelo que apresentarão sempre "0 de 0".

### <a name="account-setup"></a>Configuração da conta
Para a configuração da conta, a página de estado de inscrição controla os seguintes itens:
- Políticas de segurança
    - Um CSP para todas as inscrições.
    - Os CSPs configurados pelo Intune não são controlados aqui.
- Aplicações
    - Aplicações MSI de linha de negócio por utilizador atribuídas a Todos os Dispositivos, Todos os Utilizadores ou a um grupo de utilizadores de que seja membro o utilizador que inscreve o dispositivo.
    - Aplicações MSI de linha de negócio por computador atribuídas a Todos os Utilizadores ou a um grupo de utilizadores de que seja membro o utilizador que inscreve o dispositivo.
    - Aplicações da loja de linha de negócio atribuídas a Todos os Dispositivos, Todos os Utilizadores ou a um grupo de utilizadores de que seja membro o utilizador que inscreve o dispositivo, com o contexto de instalação = Utilizador.
    - Aplicações online da loja atribuídas a Todos os Dispositivos, Todos os Utilizadores ou a um grupo de utilizadores de que seja membro o utilizador que inscreve o dispositivo, com o contexto de instalação = Utilizador.
    - Aplicações offline da loja atribuídas a Todos os Dispositivos, Todos os Utilizadores ou a um grupo de utilizadores de que seja membro o utilizador que inscreve o dispositivo, com o contexto de instalação = Utilizador.
- Perfis de conectividade
    - Perfis de VPN e de Wi-Fi atribuídos a Todos os Utilizadores ou a um grupo de utilizadores de que seja membro o utilizador que inscreve o dispositivo.
- Certificados
    - Perfis de certificados atribuídos a Todos os Utilizadores ou a um grupo de utilizadores de que seja membro o utilizador que inscreve o dispositivo.

## <a name="next-steps"></a>Próximos passos
Depois de configurar as suas páginas de inscrição do Windows, saiba como gerir dispositivos Windows. Para obter mais informações, veja [O que é a gestão de dispositivos do Microsoft Intune?](https://docs.microsoft.com/intune/device-management)