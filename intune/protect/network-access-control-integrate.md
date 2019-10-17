---
title: Integração de controlo de acesso à rede com o Microsoft Intune – Azure | Microsoft Docs
description: As soluções de controlo de acesso à rede (NAC) verificam a inscrição e conformidade dos dispositivos com o Intune. O NAC inclui determinados comportamentos e funciona com acesso condicional. Veja os passos necessários para subscrever e obter uma lista das soluções de parceiros.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 04/25/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: aa7ecff7-8579-4009-8fd6-e17074df67de
ms.reviewer: davidra
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 142d24452c401f83322b71a104ed47759eb6179f
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72509105"
---
# <a name="network-access-control-nac-integration-with-intune"></a>Integração de controlo de acesso à rede (NAC) com o Intune

O Intune integra-se com parceiros de controlo de acesso à rede para ajudar as organizações a proteger os dados empresariais quando os dispositivos tentam aceder a recursos no local.

## <a name="how-do-intune-and-nac-solutions-help-protect-your-organization-resources"></a>Como é que o Intune e as soluções de NAC ajudam a proteger os recursos da sua organização?

As soluções de NAC verificam a inscrição do dispositivo e o estado de conformidade com o Intune para tomar decisões de controlo de acesso. Se o dispositivo não estiver inscrito, ou se estiver inscrito e não cumprir as políticas de conformidade do dispositivo do Intune, o dispositivo deverá ser redirecionado para o Intune para ser inscrito ou para ser sujeito a uma verificação da conformidade.

### <a name="example"></a>Exemplo

Se o dispositivo estiver inscrito e em conformidade com o Intune, a solução de NAC deve permitir que o dispositivo aceda aos recursos empresariais. Por exemplo, o acesso dos utilizadores pode ser permitido ou recusado quando tentam aceder aos recursos de Wi-Fi ou VPN empresariais.

## <a name="feature-behaviors"></a>Comportamentos da funcionalidade

Os dispositivos que estão a ser ativamente sincronizados com o Intune não podem ser movidos de **Compatível** / **Não Compatível** para **Não Sincronizado** (ou **Desconhecido**). O estado **Desconhecido** está reservado para dispositivos inscritos recentemente que ainda não tenham sido avaliados quanto à conformidade.

Para os dispositivos cujo acesso aos recursos está bloqueado, o serviço de bloqueio deve redirecionar todos os utilizadores para o [portal de gestão](https://portal.manage.microsoft.com) para determinar o motivo pelo qual está bloqueado.  Se os utilizadores visitarem esta página, os seus dispositivos serão reavaliados de forma síncrona quanto à conformidade.

## <a name="nac-and-conditional-access"></a>NAC e acesso condicional

O NAC funciona com acesso condicional para fornecer decisões de controle de acesso. Para obter mais informações, consulte [maneiras comuns de usar o acesso condicional com o Intune](conditional-access-intune-common-ways-use.md).

## <a name="how-the-nac-integration-works"></a>Como funciona a integração de NAC

A lista seguinte é uma descrição geral sobre como a integração do NAC funciona quando integrada com o Intune. Os três primeiros passos (1 a 3) explicam o processo de inclusão. Assim que a solução de NAC estiver integrada com o Intune, os passos 4 a 9 descrevem a operação em curso.

![Imagem conceitual de como o NAC funciona com o Intune](./media/network-access-control-integrate/ca-intune-common-ways-2.png)

1. Registe a solução de parceiro de NAC com o Azure Active Directory (AAD) e conceda permissões delegadas à API de NAC do Intune.
2. Configure a solução de parceiro de NAC com as definições adequadas, incluindo o URL de deteção do Intune.
3. Configure a solução de parceiro de NAC para a autenticação de certificados.
4. O utilizador liga-se ao ponto de acesso Wi-Fi empresarial ou faz um pedido de ligação VPN.
5. A solução de parceiro de NAC reencaminha as informações do dispositivo para o Intune e pergunta ao Intune sobre a inscrição do dispositivo e o estado de conformidade.
6. Se o dispositivo não estiver em conformidade ou não estiver inscrito, a solução de parceiro de NAC indica ao utilizador que inscreva ou corrija a conformidade do dispositivo.
7. O dispositivo tenta verificar novamente o estado de conformidade e inscrição quando aplicável.
8. Uma vez que o dispositivo esteja inscrito e em conformidade, a solução de parceiro de NAC obtém o estado do Intune.
9. A ligação é estabelecida com êxito, o que permite que o dispositivo aceda aos recursos empresariais.

## <a name="use-nac-for-vpn-on-your-ios-devices"></a>Usar o NAC para VPN em seus dispositivos iOS  

- O NAC está disponível nas seguintes VPNs sem habilitar o NAC no perfil de VPN:

  - NAC para Cisco Legacy AnyConnect
  - F5 acesso herdado
  - Citrix VPN

- O NAC também está disponível para acesso Citrix SSO e F5. Para habilitar o NAC para SSO da Citrix:

  - Use o 12.0.59 do gateway da Citrix ou superior.  
  - Os usuários devem ter o Citrix SSO 1.1.6 ou posterior instalado.
  - [Integre o Netscaler ao Intune para NAC](https://docs.citrix.com/en-us/netscaler-gateway/12/microsoft-intune-integration/configuring-network-access-control-device-check-for-netscaler-gateway-virtual-server-for-single-factor-authentication-deployment.html) , conforme descrito na documentação do produto Citrix.
  - No perfil VPN, selecione **configurações de Base** > **habilitar o NAC (controle de acesso à rede)** > selecione **concordo**.

  A conexão VPN é desconectada a cada 24 horas por motivos de segurança. A VPN pode ser imediatamente reconectada.

- Para habilitar o NAC para acesso F5:

  - Use F5 BIG-IP 13.1.1.5. Não há suporte para BIG-IP 14.
  - Integre BIG-IP ao Intune para NAC. A [visão geral: Configurando o APM para verificações de postura de dispositivo com os sistemas de gerenciamento de ponto de extremidade](https://support.f5.com/kb/en-us/products/big-ip_apm/manuals/product/apm-client-configuration-7-1-6/6.html#guid-0bd12e12-8107-40ec-979d-c44779a8cc89) F5 Guide lista as etapas.
  - No perfil VPN, selecione **configurações de Base** > **habilitar o NAC (controle de acesso à rede)** > selecione **concordo**.

  A conexão VPN é desconectada a cada 24 horas por motivos de segurança. A VPN pode ser imediatamente reconectada.

- O controle de acesso à rede não tem suporte para o seguinte cliente VPN no iOS:
  - Cisco AnyConnect

Estamos trabalhando com nossos parceiros para lançar uma solução de NAC para esses clientes mais recentes. Quando as soluções estiverem prontas, este artigo será atualizado com informações adicionais.

## <a name="next-steps"></a>Próximos passos

- [Integrar o Cisco ISE com o Intune](https://www.cisco.com/c/en/us/td/docs/security/ise/2-1/admin_guide/b_ise_admin_guide_21/b_ise_admin_guide_20_chapter_01000.html)
- [Integrar o Citrix NetScaler com o Intune](https://docs.citrix.com/en-us/netscaler-gateway/12/microsoft-intune-integration/configuring-network-access-control-device-check-for-netscaler-gateway-virtual-server-for-single-factor-authentication-deployment.html)
- [Integrar o Gerenciador de políticas de acesso de BIG-IP do F5 ao Intune](https://support.f5.com/kb/en-us/products/big-ip_apm/manuals/product/apm-client-configuration-13-0-0/6.html)
- [Integrar o HP Aruba ClearPass com o Intune](https://support.arubanetworks.com/Documentation/tabid/77/DMXModule/512/Command/Core_Download/Default.aspx?EntryId=31271)
- [Integrar o secRMM (Gestor de Suportes de Dados Amovíveis de Segurança) da Squadra com o Intune](http://www.squadratechnologies.com/StaticContent/ProductDownload/secRMM/9.9.0.0/secRMMIntuneAccessControlSetupGuide.pdf)
