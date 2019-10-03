---
title: Solucionar problemas comuns do Intune Exchange Connector
titleSuffix: Microsoft Intune
description: Solucionar e resolver problemas comuns para o Microsoft Intune Exchange Connector local
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/02/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4219d9d4f7d7e8c56acc218d16d8277ed2cf3821
ms.sourcegitcommit: f04e21ec459998922ba9c7091ab5f8efafd8a01c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71817537"
---
# <a name="resolve-common-problems-for-the-intune-exchange-connector"></a>Resolver problemas comuns do Intune Exchange Connector
 
Este artigo pode ajudar o administrador do Intune a resolver problemas comuns para a operação do Intune Exchange Connector.  

Antes de continuar, examine solucionar problemas do Exchange Connector local do Intune para obter informações básicas sobre o conector antes de iniciar a solução de problemas e problemas comuns para a configuração do conector. 

## <a name="exchange-activesync-device-not-discovered-from-exchange"></a>Dispositivo do Exchange ActiveSync não detetado a partir do Exchange

[Monitorize a atividade do conector do Exchange](exchange-connector-install.md#on-premises-intune-exchange-connector-high-availability-support) para ver se o conector do Exchange está a sincronizar com o servidor Exchange. Se uma sincronização rápida ou uma sincronização completa foi concluída com êxito desde que o dispositivo foi associado, pode verificar a existência de outros possíveis problemas, que se encontram listados abaixo. Se não tiver sido efetuada uma sincronização, recolha os registos de sincronização e anexe-os a um pedido de suporte.  

- Se um utilizador não tiver uma licença do Intune, o conector do Exchange não irá detetar os respetivos dispositivos.  

- Se o endereço SMTP principal de um utilizador for diferente do respetivo UPN no Azure Active Directory (Azure AD), o Exchange Connector não detetará dispositivos para esse utilizador. Corrija o endereço SMTP principal para resolver o problema.  

- Se você tiver servidores de caixa de correio do Exchange 2010 e do Exchange 2013 em seu ambiente, é recomendável apontar o Exchange Connector para um servidor de acesso para cliente (CAS) do Exchange 2013. Caso contrário, se o Exchange Connector estiver configurado para se comunicar com uma CAS do Exchange 2010, o Exchange Connector não descobrirá nenhum dispositivo dos usuários do Exchange 2013.  

- Para ambientes do Exchange Online dedicado, você deve apontar o Exchange Connector para uma CAS do Exchange 2013 (não um CAS do Exchange 2010) no ambiente dedicado durante a configuração inicial, pois o conector se comunicará com essas CAS somente durante a execução Cmdlets do PowerShell.  


## <a name="problems-with-the-notification-email-message"></a>Problemas com a mensagem de email de notificação  

Para dar suporte a dispositivos não Knox Android para acesso condicional para caixas de correio locais, o registro do Intune deve começar da mensagem de email "comece agora mesmo" enviada pelo Exchange Connector do Intune. Iniciar o registro da mensagem garante que o dispositivo receba uma ActiveSyncid exclusiva em todas as plataformas (Exchange, Azure AD, Intune).  

Há várias razões pelas quais um usuário pode não receber a mensagem de email de notificação:  

- A conta de notificação não está configurada corretamente.
- A descoberta automática falha para a conta de notificação.
- A solicitação do EWS para enviar a mensagem de email falha.

Use o seguinte para solucionar problemas de notificação por email.

### <a name="review-the-notification-account-thats-used-to-retrieve-autodiscover-settings"></a>Examinar a conta de notificação que é usada para recuperar as configurações de descoberta automática
1. Verifique se o serviço descoberta automática e os serviços Web do Exchange estão configurados nos serviços de acesso para cliente do Exchange. Para obter mais informações, consulte [serviços de acesso para cliente](https://docs.microsoft.com/Exchange/architecture/client-access/client-access).

   Para obter mais informações, consulte [serviço de descoberta automática no Exchange Server](https://docs.microsoft.com/Exchange/architecture/client-access/autodiscover?view=exchserver-2019).


2. Verifique se sua conta de notificação atende aos seguintes requisitos:

   - A conta tem uma caixa de correio ativa hospedada pelo seu servidor Exchange local.  

   - O UPN da conta corresponde ao endereço SMTP.

3. Para que a descoberta automática funcione, o servidor DNS deve ter um registro DNS para **autodiscover.SMTPdomain.com** (por exemplo autodiscover.contoso.com) que aponte para o servidor de acesso para cliente do Exchange. Para verificar se o registro está presente, faça o seguinte, ao especificar o FQDN no lugar do *autodiscover.SMTPdomain.com*:

   1. Em um prompt de comando, digite **nslookup**e pressione Enter.  

   2. Digite **autodiscover.SMTPdomain.com**e pressione Enter.

      A saída deve ser semelhante à imagem a seguir:  
      ![Resultados do nslookup](./media/troubleshoot-exchange-connector-common-problems/nslookup-results.png
)

   Você também pode testar o serviço descoberta automática da Internet em https://testconnectivity.microsoft.com/ ou de um domínio local usando a ferramenta Analisador de conectividade da Microsoft. Para obter mais informações, consulte a [ferramenta Analisador de conectividade da Microsoft](https://docs.microsoft.com/en-us/previous-versions/office/exchange-remote-connectivity/jj851141(v=exchg.80)). Baixe a [ferramenta Analisador de conectividade da Microsoft](http://go.microsoft.com/fwlink/?LinkID=313782).


### <a name="review-autodisocvery"></a>Examinar Autodisocvery  

Se a descoberta automática falhar, tente as seguintes etapas:
1. [Configure um registro DNS de descoberta automática válido](https://docs.microsoft.com/previous-versions/exchange-server/exchange-150/mt473798(v=exchg.150)). 

2. Codifique a URL do EWS no arquivo de configuração do Intune Exchange Connector, da seguinte maneira:

   1. Determine a URL do EWS. A URL do EWS padrão para o Exchange é **https://<mailServerFQDN>/EWS/Exchange. asmx**, embora suas possam ser diferentes. Contate o administrador do Exchange para verificar a URL correta para o seu ambiente.

   2. Edite o arquivo **OnPremisesExchangeConnectorServiceConfiguration. xml** . Por padrão, o arquivo está localizado em **%ProgramData%\Microsoft\Windows Intune Exchange Connector** no computador que está executando o Exchange Connector. Abra o arquivo usando um editor de texto e, em seguida, altere a seguinte linha para refletir a URL do EWS para seu ambiente: `<ExchangeWebServiceURL> https://<YourExchangeHOST>/EWS/Exchange.asmx</ExchangeWebServiceURL>`
    

3. Salve o arquivo e reinicie o computador ou reinicie o serviço de Microsoft Intune Exchange Connector.

>[!NOTE]
> Nessa configuração, o Intune Exchange Connector interrompe o uso da descoberta automática e, em vez disso, conecta-se diretamente à URL do EWS.

## <a name="next-steps"></a>Passos seguintes  

O artigo a seguir pode ajudar a resolver erros específicos:
- [Resolva erros comuns para o Intune Exchange Connector](troubleshoot-exchange-connector-common-errors.md).

Procure assistência do suporte ou da Comunidade do Intune.
- Consulte [obter suporte](../fundamentals/get-support.md) para usar o console do Intune para ajudar a solucionar o problema ou para abrir um caso de suporte com a Microsoft. 
- Poste seu problema nos [fóruns de Microsoft Intune](https://social.technet.microsoft.com/Forums/en-US/home?forum=microsoftintuneprod).  
