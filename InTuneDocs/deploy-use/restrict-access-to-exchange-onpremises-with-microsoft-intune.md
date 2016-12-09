---
title: Restringir o acesso ao e-mail no Exchange no local | Microsoft Intune
description: Proteja e controle o acesso ao e-mail da empresa no Exchange no local com o acesso condicional.
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 10/12/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a55071f5-101e-4829-908d-07d3414011fc
ms.reviewer: chrisgre
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 87e37cd8334ddb9331c0662b691545cd0ab0553a
ms.openlocfilehash: 9567d67a8567113c81b20428b5e4f8749aae3d69


---

# <a name="restrict-email-access-to-exchange-on-premises-and-legacy-exchange-online-dedicated-with-intune"></a>Restringir o acesso ao e-mail no Exchange no local e no Exchange Online Dedicado legado com o Intune


Se tiver um ambiente do Exchange Online Dedicado e precisar de saber se está na configuração nova ou legada, contacte o seu gestor de conta.


Para controlar o acesso ao e-mail no Exchange no local ou no ambiente do Exchange Online Dedicado legado, configure o acesso condicional para o Exchange no local no Intune.
Para saber mais sobre como funciona o acesso condicional, leia o artigo [Restringir o acesso ao e-mail e a serviços do Office 365]( restrict-access-to-email-and-o365-services-with-microsoft-intune.md).

**Antes de** pode configurar o acesso condicional,verifique o seguinte:

-   A sua versão do Exchange tem de ser o **Exchange 2010 ou posterior**. Matriz de Servidor de Acesso de Cliente (CAS) do Exchange Server é suportada.

-   Tem de utilizar o **conector do Exchange no local**, que liga o [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] ao Microsoft Exchange no local. Este procedimento permite-lhe gerir dispositivos através da consola do [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]. Para obter detalhes sobre o conetor, consulte [Conetor do Exchange no local do Intune](intune-on-premises-exchange-connector.md).

    -   O conector do Exchange no local disponível na consola do Intune é específico do seu inquilino do Intune e não pode ser utilizado com nenhum outro inquilino. Deve também assegurar que o conetor do Exchange para o seu inquilino está instalado **em apenas um computador**.

        Este conector deve ser transferido a partir da consola de administração do Intune.  Para obter instruções sobre como configurar o conetor do Exchange no local, consulte [Configurar o conetor do Exchange no local no Exchange alojado ou no local](intune-on-premises-exchange-connector.md).

    -   O conector pode ser instalado em qualquer máquina, desde que a máquina possa comunicar com o servidor do Exchange.

    -   Este conector suporta o **ambiente do Exchange CAS**. Pode instalar tecnicamente o conector no servidor do Exchange CAS diretamente se desejar, mas não é recomendável, uma vez que irá aumentar a carga no servidor.
    Quando configurar o conector, tem de configurá-lo para comunicar com um dos servidores do Exchange CAS.

-   O **Exchange ActiveSync** tem de ser configurado com a autenticação baseada em certificado ou com a entrada de credenciais de utilizador.

Quando as políticas de acesso condicional são configuradas e direcionadas para um utilizador, antes de um utilizador poder ligar ao respetivo e-mail, o **dispositivo** que utiliza tem de ser:

-  **Inscrito** no [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] ou ser um PC associado a um domínio.

-  **Registado no Azure Active Directory**. Além disso, o ID do Exchange ActiveSync do cliente tem de ser registado no Azure Active Directory.

  O AAD DRS será automaticamente ativado para os clientes do Intune e do Office 365. Os clientes que já implementaram o Serviço de Registos de Dispositivos do ADFS não verão dispositivos registados no respetivo Active Directory no local. **Isto não é aplicável a PC com Windows ou a dispositivos Windows Phone**.

-   **Compatível** com todas as políticas de conformidade do [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] implementadas nesse dispositivo.

O diagrama seguinte ilustra o fluxo utilizado pelas políticas de acesso condicional no Exchange no local para avaliar se deve permitir ou bloquear dispositivos.

![Diagrama que mostra os pontos de decisão que determinam se um dispositivo tem permissão para aceder ao Exchange no local ou se é bloqueado](../media/ConditionalAccess8-2.png) Se uma política de acesso condicional não for cumprida, é apresentada ao utilizador uma das duas mensagens seguintes quando iniciar sessão:

- Se o dispositivo não estiver inscrito no [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)], ou não estiver registado no Azure Active Directory, é apresentada uma mensagem com instruções sobre como instalar a aplicação Portal da Empresa, inscrever o dispositivo e ativar o e-mail. Este processo também associa o ID do Exchange ActiveSync do ao registo do dispositivo no Azure Active Directory.

-   Se o dispositivo não for conforme, é apresentada uma mensagem que direciona o utilizador para o site do Portal da Empresa do [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] ou para a aplicação Portal da Empresa, onde é possível localizar informações sobre o problema e como resolvê-lo.

## <a name="support-for-mobile-devices"></a>Suporte para dispositivos móveis
-   Windows Phone 8.1 e posterior

-   Aplicação de e-mail nativa no iOS.

-   Clientes de correio EAS, como o Gmail para Android 4 ou posterior.
- Clientes de correio EAS em **dispositivos Android for Work:** apenas as aplicações **Gmail** e **Nine Work** são suportadas no **perfil de trabalho** em dispositivos Android for Work. Para obter acesso condicional ao seu trabalho com o Android for Work, tem de implementar um perfil de e-mail para a aplicação Gmail ou Nine Work, bem como implementar essas aplicações como uma instalação obrigatória. 

[!INCLUDE[wit_nextref](../includes/afw_rollout_disclaimer.md)]

> [!NOTE]
> A aplicação Microsoft Outlook não é suportada no Android e iOS.

## <a name="support-for-pcs"></a>Suporte de PCs

A aplicação **Correio**no Windows 8.1 e versões posteriores (quando inscritos através do [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)])

##  <a name="configure-a-conditional-access-policy"></a>Configurar uma política de acesso condicional

1.  Na [consola de administração do Microsoft Intune](https://manage.microsoft.com), escolha **Política** > **Acesso Condicional** > **Política do Exchange no local**.
![IntuneSA5aSelectExchOnPremPolicy](../media/IntuneSA5aSelectExchOnPremPolicy.png)

2.  Configure a política com as definições necessárias: ![Captura de ecrã da página da política do Exchange no local](../media/IntuneSA5bExchangeOnPremPolicy.png)

  - **Impedir que as aplicações de e-mail acedam ao Exchange no local se o dispositivo não estiver em conformidade ou não estiver inscrito no Microsoft Intune:** quando seleciona esta opção, os dispositivos que não são geridos pelo [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)], ou que não estão em conformidade com uma política de conformidade, são impedidos de aceder aos serviços do Exchange.

  - **Substituição da regra predefinida - Permitir sempre aos dispositivos inscritos e em conformidade aceder ao Exchange:** quando seleciona esta opção, os dispositivos inscritos no Intune e em conformidade com as políticas de conformidade estão autorizados a aceder ao Exchange.  
  Esta regra substitui a **Regra Predefinida**, o que significa que mesmo que defina a **Regra Predefinida** para colocar em quarentena ou bloquear o acesso, os dispositivos inscritos e em conformidade continuarão a poder aceder ao Exchange.

  - **Grupos Visados:** selecione os grupos de utilizadores do [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] que têm de inscrever o respetivo dispositivo no [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] antes de poderem aceder ao Exchange.

  - **Grupos Excluídos:** selecione os grupos de utilizadores do [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] excluídos da política de acesso condicional. Os utilizadores constantes nesta lista serão excluídos, mesmo que também estejam na lista **Grupos Visados**.

  - **Exceções de Plataforma:** escolha **Adicionar Regra** para configurar uma regra que defina os níveis de acesso para famílias e modelos de dispositivos móveis especificados. Como estes dispositivos podem ser de qualquer tipo, também pode configurar os tipos de dispositivos não suportados pelo [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)].

  - **Regra Predefinida:** em dispositivos que não são abrangidos por qualquer uma das outras regras, pode optar por permitir que acedam ao Exchange, que o bloqueiem ou o coloquem em quarentena. Quando define a regra para permitir o acesso, para os dispositivos inscritos e em conformidade, o acesso ao e-mail é concedido automaticamente para dispositivos iOS, Windows e Samsung KNOX. O utilizador final não tem de passar por nenhum processo para obter acesso ao respetivo e-mail.  Em dispositivos Android sem o Samsung KNOX, os utilizadores finais irão receber um e-mail de quarentena que inclui instruções orientadas para verificar a inscrição e a conformidade antes de poderem aceder ao e-mail. Se definir a regra para bloquear o acesso ou colocá-lo em quarentena, todos os dispositivos ficam bloqueados de aceder ao Exchange, independentemente de já estarem inscritos ou não no Intune. Para impedir que os dispositivos inscritos e em conformidade sejam afetados por esta regra, selecione **Substituição da Regra Predefinida.**
>[!TIP]
>Se a sua intenção for bloquear primeiro todos os dispositivos antes de conceder acesso ao e-mail, escolha a regra Bloquear acesso ou Quarentena. A regra predefinida será aplicada a todos os tipos de dispositivos, pelo que os tipos de dispositivos que forem configurados como exceções de plataforma e não forem suportados pelo [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] também são afetados.

  - **Notificação do Utilizador:** para além do e-mail de notificação enviado a partir do Exchange, o Intune envia um e-mail que contém passos para desbloquear o dispositivo. Pode editar a mensagem predefinida para personalizá-la de acordo com as suas necessidades. Como o e-mail de notificação do Intune com as instruções de correção é enviado para a caixa de correio do Exchange do utilizador, no caso de o dispositivo do utilizador ser bloqueado antes de receber a mensagem de e-mail, este pode utilizar um dispositivo desbloqueado ou outro método para aceder ao Exchange e ver a mensagem. Isto é particularmente verdadeiro quando a **Regra Predefinida** estiver definida como bloqueio ou quarentena.  Neste caso, o utilizador final terá de aceder à respetiva loja de aplicações, transferir a aplicação Portal da Empresa da Microsoft e inscrever o seu dispositivo. Isto é aplicável a dispositivos iOS, Windows e Samsung KNOX.  Para dispositivos sem o Samsung KNOX, terá de enviar o e-mail de quarentena para uma conta de e-mail alternativa, o qual o utilizador final tem de copiar em seguida para o respetivo dispositivo bloqueado para concluir o processo de inscrição e conformidade.
  > [!NOTE]
  > Para o Exchange poder enviar o e-mail de notificação, tem de especificar a conta que deve ser utilizada para enviá-lo.
  >
  > Para obter detalhes, consulte [Configurar o conetor do Exchange no local no Exchange alojado ou no local](intune-on-premises-exchange-connector.md).

3.  Quando tiver terminado, escolha **Guardar**.

-   Não tem de implementar a política de acesso condicional, pois esta entra em vigor imediatamente.

-   Depois de um utilizador configurar um perfil do Exchange ActiveSync, o dispositivo poderá demorar entre 1 a 3 horas até ser bloqueado (se não for gerido pelo [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]).

-   Se um utilizador bloqueado inscrever, posteriormente, o dispositivo no [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] e corrigir a não conformidade, o acesso ao e-mail será desbloqueado em dois minutos.

-   Se o utilizador anular a inscrição no [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)], o dispositivo poderá demorar entre uma a três horas até ser bloqueado.

**Para ver alguns cenários de exemplo de como poderia configurar a política de acesso condicional para restringir o acesso do dispositivo, consulte os [cenários de exemplo da restrição de acesso ao e-mail](restrict-email-access-example-scenarios.md).**

## <a name="next-steps"></a>Passos seguintes
[Restringir o acesso ao SharePoint Online](restrict-access-to-sharepoint-online-with-microsoft-intune.md)

[Restringir o acesso ao Skype para Empresas Online](restrict-access-to-skype-for-business-online-with-microsoft-intune.md)



<!--HONumber=Dec16_HO2-->


