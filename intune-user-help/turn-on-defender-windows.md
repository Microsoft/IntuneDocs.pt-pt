---
title: Ativar o Windows Defender | Microsoft Docs
description: Saiba como ativar o Windows Defender para aceder aos recursos da empresa.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 11/08/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d16dd2de-3ed5-474f-a04b-36dcd350162c
searchScope:
- User help
ROBOTS: ''
ms.reviewer: shburbid
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 9190282edb8d356d7d43a634d10991a4b4c19c16
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/16/2018
---
# <a name="turn-on-windows-defender-to-access-company-resources"></a>Ativar o Windows Defender para aceder aos recursos da empresa

A sua empresa ou escola querem garantir que os dispositivos que acedem aos respetivos recursos estão protegidos. Existem algumas formas de utilizarem o [Windows Defender](https://www.microsoft.com/safety/pc-security/windows-defender.aspx), a proteção incorporada do Windows contra software malicioso.

Existem algumas definições que talvez tenha de alterar no seu Windows Defender para corrigir problemas de acesso. Estes passos poderão exigir que aceda a alguns locais diferentes no seu computador.

## <a name="turn-on-windows-defender"></a>Ativar o Windows Defender

1. Em **Iniciar**, abra o **Painel de Controlo**.
2. Abra as **Ferramentas Administrativas** > **Editar política de grupo**. Esta ação abre o **Editor de Políticas de Grupo Local** numa nova janela.
3. Abra a **Configuração do Computador** > **Modelos Administrativos** > **Componentes do Windows** > **Antivírus do Windows Defender**. A definição **Desativar o Antivírus do Windows Defender** está sob as pastas de outras definições. 
4. Abra **Desativar o Antivírus do Windows Defender** e certifique-se de que este está definido como **Desativado** ou **Não configurado**.

## <a name="turn-on-real-time-protection"></a>Ativar a Proteção em Tempo Real

Certifique-se de que a Proteção em Tempo Real está ativada ao aceder a **Iniciar** e ao procurar por **Centro de Segurança do Windows Defender**. Selecione **Definições de proteção contra vírus e ameaças** e confirme que tanto a **Proteção em tempo real** como a **Proteção fornecida pela cloud** estão no modo **Ativado**. Se estas opções não forem apresentadas, faça o seguinte para ativá-las:

1. Em **Iniciar**, abra o **Painel de Controlo**.
2. Abra as **Ferramentas Administrativas** > **Editar política de grupo**. Esta ação abre o **Editor de Políticas de Grupo Local** numa nova janela.
3. Abra a **Configuração do Computador** > **Modelos Administrativos** > **Componentes do Windows** > **Centro de Segurança do Windows Defender** > **Proteção contra vírus e ameaças**.
4. Abra a definição **Área da proteção contra vírus e ameaças** e defina-a como **Desativado**.

## <a name="update-your-antivirus-definitions"></a>Atualizar as definições do antivírus

Certifique-se de que as definições do antivírus estão atualizadas ao aceder a **Iniciar** e ao procurar por **Centro de Segurança do Windows Defender**. Selecione **Atualizações de proteção** e **Procurar atualizações** para se certificar de que a proteção contra vírus do seu dispositivo está atualizada. Se esta opção não for apresentada, siga os passos em [Ativar a Proteção em Tempo Real](turn-on-defender-windows.md#turn-on-real-time-protection)

Ainda precisa de ajuda? Contacte o suporte da empresa. Para encontrar as informações de contacto dele, verifique o [site do Portal da Empresa](https://portal.manage.microsoft.com#HelpDeskDialog).
