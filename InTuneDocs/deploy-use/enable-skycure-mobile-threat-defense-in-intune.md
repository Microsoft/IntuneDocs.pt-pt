---
title: "Ativar a Defesa Contra Ameaças para Dispositivos Móveis do Skycure no Intune | Documentos da Microsoft"
description: "Ative a Defesa Contra Ameaças para Dispositivos Móveis do Skycure na consola clássica do Intune."
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
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: e76d66768ac58df25313e102b7f60d2bc7bbc59b
ms.openlocfilehash: a110f2ae4d8a101a7fb977aa651e5ce2c8828e7e
ms.lasthandoff: 03/22/2017


---

# <a name="enable-skycure-mobile-threat-defense-in-intune"></a>Ativar a Defesa Contra Ameaças para Dispositivos Móveis do Skycure no Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Para ativar a ligação da Defesa contra Ameaças para Dispositivos Móveis (MTD) do Skycure no Intune, já deve ter configurado o [Conetor do Intune na consola do Skycure](https://docs.microsoft.com/intune/deploy-use/setup-the-skycure-integration-with-Intune).

## <a name="to-enable-the-skycure-mtd-connection-in-intune"></a>Para ativar a ligação da MTD do Skycure no Intune

1.  Aceda à [consola clássica do Intune](https://manage.microsoft.com/) e introduza as suas credenciais.

2.  Escolha **Administrador** &gt; **Integração de Serviço de Terceiros**, em seguida, escolha **Estado do Skycure** e ative a **Sincronização com a MTD** através do botão de alternar.

    ![Ativar o botão de alternar do Skycure na consola clássica do Intune](../media/mtp/enable-skycure-1.png)

> [!IMPORTANT] 
> Tem de configurar as aplicações do Skycure antes de criar as regras de política de conformidade e configurar o acesso condicional. Isto garante que a aplicação está pronta e disponível para os utilizadores finais instalarem antes de poderem aceder ao e-mail ou a outros recursos da empresa.

Este passo conclui a configuração da integração do Skycure e do Intune na consola do administrador do Intune. Os passos seguintes para implementar esta solução envolvem a implementação das aplicações Skycure for Work e a configuração da política de conformidade.

## <a name="next-steps"></a>Próximos passos

[Criar a política de conformidade da Defesa Contra Ameaças para Dispositivos Móveis do Skycure](https://docs.microsoft.com/intune/deploy-use/create-skycure-mobile-threat-defense-compliance-policy)
