---
title: Resolução de problemas do conector do Exchange
titleSuffix: Microsoft Intune
description: Resolução de problemas relacionados com o conector do Exchange no local do Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/02/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: a7e3c742-295b-40bb-9afa-17f243062500
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d3d9473b68f0420670130203409abf477355d93f
ms.sourcegitcommit: 2506cdbfccefd42587a76f14ee50c3849dad1708
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/11/2020
ms.locfileid: "75885522"
---
# <a name="troubleshoot-the-intune-exchange-connector"></a>Solucionar problemas do Intune Exchange Connector

Este artigo descreve como solucionar problemas relacionados ao Intune Exchange Connector.

## <a name="before-you-start"></a>Antes de começar

Antes de começar a solucionar problemas de um problema do Exchange Connector no Intune, colete algumas informações básicas para que você esteja trabalhando em uma base sólida. Essa abordagem pode ajudá-lo a entender melhor a natureza do problema e resolvê-lo mais rapidamente.

- Verifique se o processo atende aos requisitos de instalação. Consulte [Configurar o Exchange Connector local do Intune](exchange-connector-install.md).
- Verifique se sua conta tem as permissões de administrador do Exchange e do Intune.
- Observe o texto completo e exato da mensagem de erro, os detalhes e o local em que a mensagem é exibida.
- Determine quando o problema começou: 
  - Você está configurando o conector pela primeira vez? 
  - O conector funcionou corretamente e falhou?
  - Se ele estava funcionando, quais alterações ocorreram no ambiente do Intune, no ambiente do Exchange ou no computador que executa o software do conector?
- O que é a autoridade de MDM?
- Qual versão do Exchange você usa?

### <a name="use-powershell-to-get-more-data-on-exchange-connector-issues"></a>Usar o PowerShell para obter mais dados sobre problemas do Exchange Connector

- Para obter uma lista de todos os dispositivos móveis para uma caixa de correio, use `Get-ActiveSyncDeviceStatistics -mailbox mbx`
- Para obter uma lista de endereços SMTP para uma caixa de correio, use `Get-Mailbox -Identity user | select emailaddresses | fl`
- Para obter informações detalhadas sobre o estado de acesso de um dispositivo, use `Get-CASMailbox <upn> | fl`

## <a name="review-the-connector-configuration"></a>Examinar a configuração do conector

Examine os [requisitos do Exchange Connector local](exchange-connector-install.md#intune-exchange-connector-requirements) para verificar se o seu ambiente e o conector estão configurados corretamente. 

### <a name="general-considerations-for-the-connector"></a>Considerações gerais para o conector

- Verifique se o firewall e os servidores proxy permitem a comunicação entre o servidor que hospeda o Intune Exchange Connector e o serviço do Intune.

- O computador que hospeda o Intune Exchange Connector e o servidor de acesso para cliente do Exchange (CAS) deve estar ingressado no domínio e na mesma LAN. Certifique-se de que as permissões necessárias sejam adicionadas para a conta usada pelo Exchange Connector do Intune.

- A conta de notificação é usada para recuperar as configurações de *descoberta automática* . Para obter mais informações sobre o Autodisover no Exchange, consulte [serviço de descoberta automática no Exchange Server](https://docs.microsoft.com/exchange/architecture/client-access/autodiscover?view=exchserver-2016).

- O Intune Exchange Connector envia uma solicitação para a URL do EWS usando as credenciais da conta de notificação para enviar mensagens de email de notificação junto com o link de *introdução* (para registrar-se no Intune). O uso do link de *introdução* ao registro é um requisito para dispositivos Android não-Knox. Caso contrário, esses dispositivos serão bloqueados pelo acesso condicional.

### <a name="common-issues-for-connector-configurations"></a>Problemas comuns de configurações de conector

- **Permissões de conta**: na caixa de diálogo Microsoft Intune Exchange Connector, verifique se você especificou uma conta de usuário que tenha as permissões apropriadas para executar os [cmdlets do Windows PowerShell Exchange necessários](exchange-connector-install.md#exchange-cmdlet-requirements).
- **Mensagens de email de notificação**: habilite notificações e especifique uma conta de notificação.
- **Sincronização do servidor de acesso para cliente**: ao configurar o Exchange Connector, ESPECIFIQUE um CAS que tenha a menor latência de rede possível para o servidor que hospeda o Exchange Connector. A latência de comunicação entre as CAS e o Exchange Connector pode atrasar a descoberta de dispositivos, especialmente ao usar o Exchange Online dedicado.
- **Agendamento de sincronização**: um usuário com um dispositivo registrado recentemente pode ser atrasado para obter acesso até que o Exchange Connector Sincronize com as CAS do Exchange. Uma sincronização completa é realizada uma vez ao dia e uma sincronização (rápida) delta ocorre várias vezes ao dia. Pode [forçar manualmente uma sincronização rápida ou uma sincronização completa](exchange-connector-install.md#manually-force-a-quick-sync-or-full-sync) para minimizar atrasos.

## <a name="next-steps"></a>Próximos passos
Os artigos a seguir podem ajudar a resolver problemas comuns e erros específicos:

- [Resolva problemas comuns do Intune Exchange Connector](troubleshoot-exchange-connector-common-problems.md).
- [Resolva erros comuns para o Intune Exchange Connector](troubleshoot-exchange-connector-common-errors.md).

Busque assistência do suporte ou da Comunidade do Intune:

- Consulte [obter suporte](../fundamentals/get-support.md) para usar o console do Intune para ajudar a solucionar o problema ou para abrir um caso de suporte com a Microsoft. 
- Poste seu problema nos [fóruns de Microsoft Intune](https://social.technet.microsoft.com/Forums/en-US/home?forum=microsoftintuneprod).  
