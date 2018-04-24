---
title: Implementar e monitorizar políticas de conformidade
description: Utilize as instruções passo a passo neste tópico para implementar e monitorizar uma política de conformidade de dispositivos.
keywords: ''
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 11/14/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d8f246d4-0d86-4c8b-a1bf-9977985506d8
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 7e3f67411a4eff357102756e785f4cbbff120d23
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/16/2018
---
# <a name="deploy-and-monitor-a-device-compliance-policy-in-microsoft-intune"></a>Implementar e monitorizar políticas de conformidade de dispositivos no Microsoft Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

## <a name="deploy-a-compliance-policy"></a>Implementar uma política de conformidade
Implemente a política de conformidade que [criou](create-a-device-compliance-policy-in-microsoft-intune.md) em um ou mais grupos de utilizadores na sua organização. Quando uma política de conformidade é implementada num utilizador, os dispositivos do utilizador são verificados relativamente à conformidade.

1.  Na área de trabalho **Policy**, selecione a política que pretende implementar e, em seguida, escolha **Manage Deployment**.
![Captura de ecrã da página de política de conformidade que mostra a opção de menu Gerir Implementação na parte superior](./media/intune-sa-3c-deploy-compliance-policy2.png)

2.  Na caixa de diálogo **Manage Deployment**, selecione um ou mais grupos nos quais quer implementar a política e, em seguida, selecione **Add** > **OK**.
![Captura de ecrã da caixa de diálogo Gerir Implementação](./media/intune-sa-3d-deploy-compliance-policy3-Manage.png) Utilize grupos do Active Directory que já tenha criado e sincronizado com o Intune ou crie-os manualmente na consola do Intune. Para saber mais sobre como implementar políticas, consulte [Implementar uma política de configuração](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).

Utilize o resumo de estado e os alertas na página **Descrição geral** da área de trabalho **Política** para identificar problemas da política que necessitem da sua atenção. Para além disso, é apresentado um resumo de estado na área de trabalho **Dashboard** .

> [!IMPORTANT]
> Se não tiver implementado uma política de conformidade e ativar uma política de acesso condicional do Exchange, todos os dispositivos visados terão acesso.

## <a name="monitor-the-compliance-policy"></a>Monitorizar a política de conformidade

#### <a name="to-view-devices-that-do-not-conform-to-a-compliance-policy"></a>Para ver os dispositivos que não estão em conformidade com uma política de conformidade

1.  Na [consola de administração do Microsoft Intune](https://manage.microsoft.com), selecione **Groups** > **All Devices**.

2.  Faça duplo clique no nome de um dispositivo na lista de dispositivos.

3.  Escolha o separador **Policy** para ver uma lista das políticas desse dispositivo.

4.  Na lista pendente **Filters**, selecione **Does not conform to compliance policy**.
![Captura de ecrã que mostra a lista de opções na lista de filtros](./media/intune-sa-3e-view-device-noncompliance.png)

#### <a name="to-view-the-health-attestation-reports"></a>Para ver os relatórios do atestado de estado de funcionamento

1.  Na [consola de administração do Microsoft Intune](https://manage.microsoft.com), escolha **Reports**.

2.  Na página **Does not conform to compliance policy**, pode ver um relatório com todos os dados do atestado de estado de funcionamento do Windows 10 que o Intune recolheu. Também pode utilizar os filtros para criar um relatório com um subconjunto dos dados. Os filtros podem basear-se no tipo de dispositivo, de sistema operativo ou apenas num subconjunto dos pontos de dados.

## <a name="how-intune-resolves-policy-conflicts"></a>Como o Intune resolve conflitos de políticas
Se forem aplicadas múltiplas políticas do Intune a um dispositivo, podem ocorrer conflitos de políticas. Se as definições de políticas se sobrepuserem, o Intune utiliza as seguintes regras para resolver eventuais conflitos:

-   Se as definições em conflito pertencerem a uma política de configuração do Intune e a uma política de conformidade, as definições da política de conformidade têm prioridade sobre as definições da política de configuração. Isto acontece mesmo que as definições na política de conformidade sejam mais seguras.

-   Se tiver implementado múltiplas políticas de conformidade, o Intune utilizará a mais segura destas políticas.

## <a name="next-steps"></a>Próximos passos
Para saber como utilizar a política de conformidade com políticas de acesso condicional para controlar o acesso aos serviços da sua organização, consulte [Restringir o acesso ao e-mail e a serviços do O365](restrict-access-to-email-and-o365-services-with-microsoft-intune.md).


### <a name="see-also"></a>Consulte também
[Introdução às políticas de conformidade de dispositivos no Intune](introduction-to-device-compliance-policies-in-microsoft-intune.md)
