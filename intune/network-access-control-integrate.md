---
title: "Integração de controlo de acesso à rede com o Intune"
titlesuffix: Azure portal
description: "Integração de controlo de acesso à rede (NAC) com o Intune"
keywords: 
author: bruceperlerMS
ms.author: bruceper
manager: angrobe
ms.date: 12/18/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: aa7ecff7-8579-4009-8fd6-e17074df67de
ms.reviewer: davidra
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0379f2843b77b0d7ed6a54065e14f91946398d65
ms.sourcegitcommit: 061dab899e3fbc59b0128e2b4fbdf8ebf80afddd
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/19/2017
---
# <a name="network-access-control-nac-integration-with-intune"></a>Integração de controlo de acesso à rede (NAC) com o Intune

O Intune integra-se com parceiros de controlo de acesso à rede para ajudar as organizações a proteger os dados empresariais quando os dispositivos tentam aceder a recursos no local.

## <a name="how-do-intune-and-nac-solutions-help-protect-your-organization-resources"></a>Como é que o Intune e as soluções de NAC ajudam a proteger os recursos da sua organização?

As soluções de NAC são responsáveis por verificar a inscrição do dispositivo e o estado de conformidade com o Intune para tomar decisões de controlo de acesso. Se o dispositivo não estiver inscrito, ou se estiver inscrito e não cumprir as políticas de conformidade do dispositivo do Intune, o dispositivo deve ser redirecionado para o Intune para inscrição e/ou para uma verificação da conformidade do dispositivo.

### <a name="example"></a>Exemplo

Se o dispositivo estiver inscrito e em conformidade com o Intune, a solução de NAC deve permitir que o dispositivo aceda aos recursos empresariais. Por exemplo, o acesso dos utilizadores pode ser permitido ou recusado quando tentam aceder aos recursos de Wi-Fi ou VPN empresariais.

## <a name="feature-behaviors"></a>Comportamentos da funcionalidade

Os dispositivos que estão a ser ativamente sincronizados com o Intune não podem ser movidos de **Conforme** / **Não Conforme** para **Não Sincronizado** (ou **Desconhecido**). O estado **Desconhecido** está reservado para dispositivos inscritos recentemente que ainda não foram avaliados quanto à conformidade.

Para os dispositivos cujo acesso aos recursos está bloqueado, o serviço de bloqueio deve redirecionar todos os utilizadores para o [portal de gestão](https://portal.manage.microsoft.com) para determinar o motivo pelo qual está bloqueado.  Se os utilizadores visitarem esta página, os seus dispositivos serão reavaliados de forma síncrona quanto à conformidade.

## <a name="nac-and-conditional-access"></a>NAC e acesso condicional

O NAC funciona com acesso condicional para disponibilizar decisões de controlo de acesso. Para obter mais detalhes, veja [Formas comuns de utilizar o acesso condicional com o Intune](conditional-access-intune-common-ways-use.md).

## <a name="how-the-nac-integration-works"></a>Como funciona a integração de NAC

Veja a seguir uma descrição geral sobre como a integração do NAC funciona quando integrada com o Intune. Os três primeiros passos (1 a 3) explicam o processo de inclusão. Assim que a solução de NAC estiver integrada com o Intune, os passos 4 a 9 descrevem a operação em curso.

![Como o NAC funciona com o Intune](./media/ca-intune-common-ways-2.png)

1. Registe a solução de parceiro de NAC com o Azure Active Directory (AAD) e conceda permissões delegadas à API de NAC do Intune.
2. Configure a solução de parceiro de NAC com as definições adequadas, incluindo o URL de deteção do Intune.
3. Configure a solução de parceiro de NAC para a autenticação de certificados.
4. O utilizador liga-se ao ponto de acesso Wi-Fi empresarial ou faz um pedido de ligação VPN.
5. A solução de parceiro de NAC reencaminha as informações do dispositivo para o Intune e pergunta ao Intune sobre a inscrição do dispositivo e o estado de conformidade.
6. Se o dispositivo não estiver em conformidade ou não estiver inscrito, a solução de parceiro de NAC indica ao utilizador que inscreva ou corrija a conformidade do dispositivo.
7. O dispositivo tenta verificar novamente o estado de conformidade e/ou inscrição.
8. Uma vez que o dispositivo esteja inscrito e em conformidade, a solução de parceiro de NAC obtém o estado do Intune.
9. A ligação é estabelecida com êxito, o que permite que o dispositivo aceda aos recursos empresariais.

## <a name="next-steps"></a>Próximos passos

- [Integrar o Cisco ISE com o Intune](http://www.cisco.com/c/en/us/td/docs/security/ise/2-1/admin_guide/b_ise_admin_guide_21/b_ise_admin_guide_20_chapter_01000.html)
- [Integrar o Citrix NetScaler com o Intune](http://docs.citrix.com/en-us/netscaler-gateway/12/microsoft-intune-integration/configuring-network-access-control-device-check-for-netscaler-gateway-virtual-server-for-single-factor-authentication-deployment.html)
- [Integrar o HP Aruba Clear Pass com o Intune](https://support.arubanetworks.com/Documentation/tabid/77/DMXModule/512/Command/Core_Download/Default.aspx?EntryId=23757)
