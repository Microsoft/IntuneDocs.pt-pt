---
title: Solucionar problemas comuns do Intune Exchange Connector
titleSuffix: Microsoft Intune
description: Solucionar e resolver problemas comuns do Exchange Connector local Microsoft Intune.
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/26/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: de365312a7d293527c3c83fbbd84ab55de41d530
ms.sourcegitcommit: 23e9c48348a6eba494d072a2665b7481e5b5c84e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/26/2019
ms.locfileid: "74547680"
---
# <a name="resolve-common-problems-with-the-intune-exchange-connector"></a>Resolver problemas comuns com o Intune Exchange Connector
 
Este artigo pode ajudar o administrador do Intune a resolver problemas comuns com a operação do Intune Exchange Connector.

Antes de iniciar a solução de problemas, examine [solucionar problemas do Exchange Connector local do Intune](troubleshoot-exchange-connector.md) para obter informações básicas sobre o conector. Examine também problemas comuns para a configuração do conector.

## <a name="an-exchange-activesync-device-isnt-discovered-from-exchange"></a>Um dispositivo do Exchange ActiveSync não é descoberto no Exchange

Quando um dispositivo do Exchange ActiveSync não for descoberto do Exchange, [monitore a atividade do Exchange Connector](exchange-connector-install.md#on-premises-intune-exchange-connector-high-availability-support) para ver se o Exchange Connector está sincronizando com o Exchange Server. Se nenhuma sincronização ocorreu desde que o dispositivo ingressou, colete os logs de sincronização e anexe-os a uma solicitação de suporte. Se uma sincronização completa ou sincronização rápida tiver sido concluída com êxito desde que o dispositivo ingressou, verifique os seguintes problemas:

- Verifique se os usuários têm uma licença do Intune. Caso contrário, o Exchange Connector não descobrirá seus dispositivos.

- Se o endereço SMTP primário do usuário for diferente do nome principal do usuário (UPN) no Azure Active Directory (Azure AD), o Exchange Connector não descobrirá nenhum dispositivo para esse usuário. Corrija o endereço SMTP principal para resolver o problema.

- Se você tiver servidores de caixa de correio do Exchange 2010 e do Exchange 2013 em seu ambiente, é recomendável apontar o Exchange Connector para um servidor de acesso para cliente (CAS) do Exchange 2013. Se o Exchange Connector estiver configurado para se comunicar com uma CAS do Exchange 2010, o Exchange Connector não descobrirá nenhum dispositivo de usuário no Exchange 2013.

- Para ambientes do Exchange Online dedicado, você deve apontar o Exchange Connector para uma CAS do Exchange 2013 (não um CAS do Exchange 2010) no ambiente dedicado durante a configuração inicial. O conector se comunicará somente com uma CAS do Exchange 2013 quando ele executar os cmdlets do PowerShell.

## <a name="problems-with-the-notification-email-message"></a>Problemas com a mensagem de email de notificação

Para dar suporte ao acesso condicional para caixas de correio locais em dispositivos que não executam o Android Knox, verifique se o registro do Intune começa com a mensagem de email "comece agora mesmo" que o Intune Exchange Connector envia. Iniciar o registro da mensagem garante que o dispositivo receba uma ActiveSyncid exclusiva em todas as plataformas (Exchange, Azure AD, Intune).

Um usuário pode não receber a mensagem de email de notificação porque:

- A conta de notificação foi configurada incorretamente.
- Falha na descoberta automática da conta de notificação.
- A solicitação do EWS (serviços Web do Exchange) para enviar a mensagem de email falhou.

Examine as seções a seguir para solucionar problemas de notificação por email.

### <a name="check-the-notification-account-that-retrieves-autodiscover-settings"></a>Verificar a conta de notificação que recupera as configurações de descoberta automática

1. Verifique se o serviço descoberta automática e o EWS estão configurados nos serviços de acesso para cliente do Exchange. Para obter mais informações, consulte [serviços de acesso para cliente](https://docs.microsoft.com/Exchange/architecture/client-access/client-access) e [serviço descoberta automática no Exchange Server](https://docs.microsoft.com/Exchange/architecture/client-access/autodiscover?view=exchserver-2019).

2. Verifique se sua conta de notificação atende aos seguintes requisitos:

   - A conta tem uma caixa de correio ativa hospedada pelo seu servidor Exchange local.

   - O UPN da conta corresponde ao endereço SMTP.

3. A descoberta automática requer um servidor DNS que tenha um registro DNS para **autodiscover.SMTPdomain.com** (por exemplo autodiscover.contoso.com) que aponte para o servidor de acesso para cliente do Exchange. Para verificar o registro, especifique o FQDN no lugar de *autodiscover.SMTPdomain.com* e siga estas etapas:

   1. Em um prompt de comando, digite *nslookup*.

   2. Insira *autodiscover.SMTPdomain.com*. A saída deve ser semelhante à imagem a seguir: ![resultados nslookup](./media/troubleshoot-exchange-connector-common-problems/nslookup-results.png
      )

   Você também pode testar o serviço descoberta automática da Internet em https://testconnectivity.microsoft.com. Ou testá-lo de um domínio local usando a ferramenta Microsoft Connectivity Analyzer. Para obter mais informações, consulte a [ferramenta Analisador de conectividade da Microsoft](https://docs.microsoft.com/previous-versions/office/exchange-remote-connectivity/jj851141(v=exchg.80)).


### <a name="check-autodiscovery"></a>Verificar descoberta automática

Se a descoberta automática falhar, tente as seguintes etapas:

1. [Configure um registro DNS de descoberta automática válido](https://docs.microsoft.com/previous-versions/exchange-server/exchange-150/mt473798(v=exchg.150)).

2. Codifique a URL do EWS no arquivo de configuração do Intune Exchange Connector:

   1. Determine a URL do EWS. A URL do EWS padrão para o Exchange é `https://<mailServerFQDN>/ews/exchange.asmx`, mas sua URL pode ser diferente. Contate o administrador do Exchange para verificar a URL correta para o seu ambiente.

   2. Edite o arquivo *OnPremisesExchangeConnectorServiceConfiguration. xml* . Por padrão, o arquivo está localizado em *%ProgramData%\Microsoft\Windows Intune Exchange Connector* no computador que executa o Exchange Connector. Abra o arquivo em um editor de texto e, em seguida, altere a seguinte linha para refletir a URL do EWS para seu ambiente: `<ExchangeWebServiceURL> https://<YourExchangeHOST>/EWS/Exchange.asmx</ExchangeWebServiceURL>`

3. Salve o arquivo e reinicie o computador ou reinicie o serviço do conector do Exchange Microsoft Intune.

>[!NOTE]
> Nessa configuração, o Intune Exchange Connector interrompe o uso da descoberta automática e, em vez disso, conecta-se diretamente à URL do EWS.

## <a name="next-steps"></a>Próximos passos

Para obter ajuda com erros específicos, tente [resolver erros comuns para o Intune Exchange Connector](troubleshoot-exchange-connector-common-errors.md).

Para obter suporte ou para obter ajuda da Comunidade do Intune:

- Consulte [obter suporte](../fundamentals/get-support.md) para usar o console do Intune para solucionar o problema ou para abrir um caso de suporte com a Microsoft.
- Poste seu problema nos [fóruns de Microsoft Intune](https://social.technet.microsoft.com/Forums/home?forum=microsoftintuneprod).