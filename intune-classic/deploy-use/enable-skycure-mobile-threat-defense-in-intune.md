---
title: "Ativar a Defesa Contra Ameaças para Dispositivos Móveis do Skycure no Intune"
description: "Ativar a Defesa Contra Ameaças para Dispositivos Móveis do Skycure no portal clássico do Intune."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/16/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0cc4e59d-819a-47a2-a26f-4f8d0f8df7bf
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: ce0e61a27f44f0c6cb00d79442d346db679a55ea
ms.sourcegitcommit: 1a54bdf22786aea1cf1b497d54024470e1024aeb
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/10/2017
---
# <a name="enable-skycure-mobile-threat-defense-in-intune"></a>Ativar a Defesa Contra Ameaças para Dispositivos Móveis do Skycure no Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Para ativar a ligação da defesa contra ameaças para dispositivos móveis do Skycure, já deve ter configurado o [Conector do Intune na consola do Skycure] (/intune-classic/deploy-use/setup-the-skycure-integration-with-Intune).

## <a name="to-enable-the-skycure-mtd-connection-in-intune"></a>Para ativar a ligação da MTD do Skycure no Intune

1.  Aceda ao [portal clássico do Intune](https://manage.microsoft.com/) e introduza as suas credenciais.

2.  Escolha **Administrador** &gt; **Integração de Serviço de Terceiros**, em seguida, escolha **Estado do Skycure** e ative a **Sincronização com a MTD** através do botão de alternar.

    ![Ativar o botão de alternar do Skycure no portal clássico do Intune](../media/mtp/enable-skycure-1.png)

> [!IMPORTANT] 
> Tem de configurar as aplicações do Skycure antes de criar as regras de política de conformidade e configurar o acesso condicional. Isto garante que a aplicação está pronta e disponível para os utilizadores finais instalarem antes de poderem aceder ao e-mail ou a outros recursos da empresa.

Este passo conclui a configuração da integração do Skycure e do Intune na consola do administrador do Intune. Os passos seguintes para implementar esta solução envolvem a implementação das aplicações Skycure for Work e a configuração da política de conformidade.

## <a name="next-steps"></a>Passos seguintes

[Criar a política de conformidade da Defesa Contra Ameaças para Dispositivos Móveis do Skycure](/intune-classic/deploy-use/create-skycure-mobile-threat-defense-compliance-policy)
