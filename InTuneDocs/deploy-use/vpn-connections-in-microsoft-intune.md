---
title: "Ligações VPN | Documentos da Microsoft"
description: "Utilize Perfis de VPN para implementar definições da VPN em utilizadores e dispositivos na sua organização."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/20/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: abc57093-7351-408f-9f41-a30877f96f73
ms.reviewer: karanda
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 0ba06e1d698e051ba72e9f88a654d37041c57cf1
ms.openlocfilehash: cd9785889ca8b2a78a49ea2b04284d32b3fa8a65


---

# <a name="vpn-connections-in-microsoft-intune"></a>Ligações VPN no Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

As Redes Virtuais Privadas (VPN) permitem-lhe conceder aos seus utilizadores acesso remoto protegido à rede da sua empresa. Os dispositivos utilizam um *perfil de ligação VPN* para iniciar uma ligação com o servidor VPN. Utilize os *Perfis VPN* no Microsoft Intune para implementar definições de VPN a utilizadores e dispositivos na sua organização, para que possam ligar-se de forma fácil e segura à rede.

Por exemplo, suponha que pretende aprovisionar todos os dispositivos iOS com as definições necessárias para estabelecer uma ligação a uma partilha de ficheiros na rede da empresa. Pode criar um perfil de VPN com as definições necessárias para se ligar à rede da empresa e, em seguida, implementar este perfil em todos os utilizadores com dispositivos iOS. Os utilizadores verão a ligação VPN na lista de redes disponíveis e poderão ligar-se sem qualquer esforço.

Pode configurar os seguintes tipos de dispositivo com perfis de VPN:

* Dispositivos a executar o Android 4 e posterior
* Dispositivos Android for Work
* Dispositivos com iOS 8.0 ou posterior
* Dispositivos com Mac OS X 10.9 e posterior
* Dispositivos inscritos com Windows 8.1 e posterior
* Dispositivos a executar o Windows Phone 8.1 e posterior
* Dispositivos que executam o Windows 10 e o Windows 10 Mobile

As opções de configuração do perfil da VPN variam consoante o tipo de dispositivo selecionado.

[!INCLUDE[wit_nextref](../includes/afw_rollout_disclaimer.md)]

## <a name="vpn-connection-types"></a>Tipos de ligação VPN

O Intune suporta a criação de perfis de VPN que utilizem os seguintes tipos de ligação:




Tipo de ligação |iOS e Mac OS X  |Android e Android for Work|Windows 8.1|Windows RT 8.1|Windows Phone 8.1|Computadores com o Windows 10 e dispositivos móveis com o Windows 10 Mobile |
----------------|------------------|-------|-----------|----------|--------------|-----------------|----------------------|
Cisco AnyConnect|Sim |Sim   |Não    |Não  |Não    | Sim, (apenas OMA-URI, Mobile)|     
Cisco (IPsec)|Sim |Sim   |Não  |Não  |Não | Não|
Citrix|Sim |Não   |Não  |Não  |Não | Não|
Pulse Secure|Sim  |Sim |Sim   |Sim  |Sim| Sim|        
F5 Edge Client|Sim |Sim |Sim |Sim  |   Sim |  Sim|   
Dell SonicWALL Mobile Connect|Sim |Sim |Sim |Sim |Sim |Sim|         
CheckPoint Mobile VPN|Sim |Sim |Sim |Sim|Sim|Sim|
Microsoft SSL (SSTP)|Não |Não |Não |Não|Não|VPNv1 OMA-URI *|
Microsoft Automatic|Não |Não |Não |Não|Sim (OMA-URI)|Sim|
IKEv2|Perfil personalizado iOS|Não |Não |Não|Sim (OMA-URI)|Sim|
PPTP|Perfil personalizado iOS|Não |Não |Não|Não|Sim|
L2TP|Perfil personalizado iOS|Não |Não |Não|Sim (OMA-URI)|Sim|

\* Sem definições adicionais, que estão disponíveis para o Windows 10.

> [!IMPORTANT]
> Antes de poder utilizar os perfis da VPN implementados num dispositivo, tem de instalar a aplicação VPN aplicável para o perfil. Pode utilizar as informações do tópico [Implementar aplicações em dispositivos móveis no Microsoft Intune](deploy-apps-in-microsoft-intune.md), que o ajuda a implementar a aplicação aplicável com o Intune.  

 Saiba como criar perfis de VPN personalizados com definições URI em [Configurações personalizadas para perfis de VPN](create-custom-vpn-profiles.md).     

## <a name="methods-of-securing-vpn-profiles"></a>Métodos para proteger perfis de VPN

Os perfis da VPN podem utilizar vários tipos de ligação e protocolos diferentes de fabricantes diferentes. Normalmente, estas ligações são protegidas através de um de dois métodos.

### <a name="certificates"></a>Certificados

Quando cria o perfil da VPN, pode escolher um perfil de certificado SCEP ou .PFX que tenha criado anteriormente no Intune. Este é conhecido como certificado de identidade. É utilizado para autenticação em relação a um certificado fidedigno (ou um *certificado de raiz*) que criou para estabelecer que o dispositivo do utilizador tem permissões para se ligar. O certificado fidedigno é implementado no computador que irá autenticar a ligação VPN (normalmente, o servidor VPN).

Para mais informações sobre como criar e utilizar perfis de certificado no Intune, veja [Proteger o acesso a recursos com perfis de certificado](secure-resource-access-with-certificate-profiles.md).

### <a name="user-name-and-password"></a>Nome de utilizador e palavra-passe

O utilizador é autenticado no servidor VPN ao fornecer um nome de utilizador e uma palavra-passe.

## <a name="create-a-vpn-profile"></a>Criar um perfil da VPN

1. Na [consola de administração do Microsoft Intune](https://manage.microsoft.com), escolha **Política** > **Adicionar Política**.
2. Selecione um modelo para a nova política expandindo o tipo de dispositivo relevante e, em seguida, selecione o perfil da VPN desse dispositivo:
    * **Perfil da VPN (Android 4 e posterior)**
    * **Perfil da VPN (Android for Work)**
    * **Perfil da VPN (iOS 8.0 e posterior)**
    * **Perfil da VPN (Mac OS X 10.9 e posterior)**
    * **Perfil da VPN (Windows 8.1 e posterior)**
    * **Perfil da VPN (Windows Phone 8.1 e posterior)**
    * **Perfil da VPN (computadores com o Windows 10 e dispositivos móveis com o Windows 10 Mobile e posterior)**

 Só pode criar e implementar uma política de perfil da VPN personalizada. As definições recomendadas não estão disponíveis.

> [!Note]
> Um perfil da VPN para dispositivos Android for Work irá ativar uma ligação VPN apenas para aplicações que estejam instaladas no perfil de trabalho do dispositivo.
>
> Alguns tipos de ligação VPN suportam VPN por aplicação para dispositivos Android for Work e para a ativação da VPN por aplicação em aplicações distribuídas através do Intune.  

3. Utilize a seguinte tabela que o ajuda a configurar as definições de perfil da VPN:

Nome da definição  |Mais informações  
---------|---------
**Nome**     |Introduza um nome exclusivo para o perfil da VPN, de modo a conseguir identificá-lo na consola do Intune.         
**Descrição**     |Forneça uma descrição geral do perfil da VPN e outras informações relevantes que poderão ajudá-lo a localizá-lo.         
**Nome da ligação VPN (apresentado aos utilizadores)**     |Especifique um nome para o perfil da VPN. Este é nome que será visto pelos utilizadores na lista de ligações VPN disponíveis nos respetivos dispositivos.         
**Tipo de ligação**     |  Selecione um dos seguintes tipos de ligação a utilizar no perfil da VPN: **Cisco AnyConnect** (não disponível para Windows 8.1 nem Windows Phone 8.1), **Pulse Secure**, **Citrix**, **F5 Edge Client**, **Dell SonicWALL Mobile Connect**, **CheckPoint Mobile VPN**.
**Descrição do servidor VPN**     | Especifique uma descrição do servidor VPN ao qual os dispositivos serão ligados. Exemplo: **Servidor VPN da Contoso**. Se o tipo de ligação for **F5 Edge Client**, utilize o campo **Lista de servidores** para especificar uma lista de descrições e endereços IP de servidores.
**Endereço IP ou FQDN do servidor**    |Fornece o endereço IP ou nome de domínio completamente qualificado do servidor VPN ao qual os dispositivos serão ligados. Exemplos: **192.168.1.1**, **vpn.contoso.com**.  Se o tipo de ligação for **F5 Edge Client**, utilize o campo **Lista de servidores** para especificar uma lista de descrições e endereços IP de servidores.         |         
**Lista de servidores**     |Escolha **Adicionar** para adicionar um servidor VPN novo para utilizar na ligação da VPN. Também pode especificar o servidor predefinido da ligação. Esta opção só é apresentada se o tipo de ligação for **F5 Edge Client**.         
**Enviar todo o tráfego de rede através da ligação VPN**     |Se selecionar esta opção, todo o tráfego de rede será enviado através da ligação VPN. Se não selecionar esta opção, o cliente negociará dinamicamente as rotas de divisão do túnel ao estabelecer a ligação com o servidor VPN de terceiros. Apenas as ligações à rede da empresa são enviadas através de um túnel VPN. Os túneis VPN não são utilizados ao ligar-se a recursos na Internet.
**Método de autenticação**| Selecione o método de autenticação utilizado pela ligação VPN: **Certificados** ou **Nome de Utilizador e Palavra-passe**. (O **Nome de Utilizador e a Palavra-passe** não estarão disponíveis se o tipo de ligação for Cisco AnyConnect.) A opção **Método de autenticação** não está disponível para o Windows 8.1.
**Memorizar as credenciais do utilizador sempre que iniciar sessão**|Selecione este opção para garantir que as credenciais do utilizador são memorizadas, para que o mesmo não tenha de introduzi-las sempre que for efetuada uma ligação.
**Selecione um certificado de cliente para autenticação de cliente (Certificado de Identidade)**|Selecione o certificado SCEP de cliente criado anteriormente que será utilizado para autenticar a ligação VPN. Para mais informações sobre como utilizar perfis de certificado no Intune, veja [Proteger o acesso a recursos com perfis de certificado](secure-resource-access-with-certificate-profiles.md). Esta opção só é apresentada se o método de autenticação for **Certificados**.
**Função**| Especifique o nome da função de utilizador que tem acesso a esta ligação. Uma função de utilizador define opções e definições pessoais e ativa ou desativa funcionalidades de acesso específicas. Esta opção só é apresentada se o tipo de ligação for **Pulse Secure** ou **Citrix**.
**Realm**|Especifique o nome do realm de autenticação que pretende utilizar. Um realm de autenticação é um agrupamento de recursos de autenticação utilizado pelo tipo de ligação Pulse Secure ou Citrix. Esta opção só é apresentada se o tipo de ligação for **Pulse Secure** ou **Citrix**.
**Grupo ou domínio de início de sessão**|Especifique o nome do grupo ou domínio de início de sessão ao qual pretende ligar-se. Esta opção só é apresentada se o tipo de ligação for **Dell SonicWALL Mobile Connect**.
**Identificação digital**|Especifique uma cadeia de carateres (por exemplo "Código de Identificação Digital da Contoso") que será utilizada para verificar a fidedignidade do servidor VPN. A identificação digital pode ser enviada para o cliente para que confie em qualquer servidor que apresente essa mesma identificação digital ao ligar. Se o dispositivo ainda não incluir a identificação digital, pedirá ao utilizador para confiar no servidor VPN ao qual está a ligar e mostrar a identificação digital. (O utilizador verifica manualmente a mesma e escolhe **fidedignidade** para estabelecer a ligação.) Esta opção só é apresentada se o tipo de ligação for **CheckPoint Mobile VPN**.
**VPN Por Aplicação**|Selecione esta opção se pretende associar esta ligação VPN a uma aplicação iOS ou Mac OS X, para que a ligação seja aberta quando a aplicação é executada. Pode associar o perfil da VPN a uma aplicação ao implementar o software. Para mais informações, consulte [Implementar aplicações no Microsoft Intune](deploy-apps-in-microsoft-intune.md).
**VPN a pedido**|Pode configurar a VPN a pedido para dispositivos iOS 8.0 e posteriores. As instruções para a configuração são fornecidas em [VPN a pedido para dispositivos iOS](#on-demand-vpn-for-ios-devices).
**Detetar automaticamente as definições de proxy** (apenas em iOS, Mac OS X, Windows 8.1 e Windows Phone 8.1)|Se o seu servidor VPN precisar de um servidor proxy para a ligação, especifique se pretende que os dispositivos detetem automaticamente as definições de ligação. Para mais informações, consulte a documentação do Windows Server.
**Utilizar um script de configuração automática** (apenas em iOS, Mac OS X, Windows 8.1 e Windows Phone 8.1)|Se o seu servidor VPN precisar de um servidor proxy para a ligação, especifique se pretende utilizar um script de configuração automática para selecionar as definições e, em seguida, especifique um URL para o ficheiro com as mesmas. Para mais informações, consulte a documentação do Windows Server.
**Utilizar um servidor proxy** (apenas em iOS, Mac OS X, Windows 8.1 e Windows Phone 8.1)|Se o seu servidor VPN precisar de um servidor proxy para a ligação, selecione este opção e, em seguida, especifique o endereço e número de porta do servidor proxy. Para mais informações, consulte a documentação do Windows Server.
**Ignorar as definições de proxy para endereços locais** (apenas em iOS, Mac OS X, Windows 8.1 e Windows Phone 8.1)|Se o seu servidor VPN precisar de um servidor proxy para a ligação, selecione esta opção caso não pretenda utilizar o servidor proxy para endereços locais especificados. Para mais informações, consulte a documentação do Windows Server.
**XML Personalizado** (Windows 8.1 e posteriores e Windows Phone 8.1 e posteriores)|Especifique comandos XML personalizados que configuram a ligação VPN. Exemplo para **Pulse Secure**: &lt;pulse-schema&gt;&lt;isSingleSignOnCredential&gt;true&lt;/isSingleSignOnCredential&gt;&lt;/pulse-schema&gt;. Exemplo para **CheckPoint Mobile VPN**: &lt;CheckPointVPN port="443" name="CheckPointSelfhost" sso="true"  debug="3" /&gt;. Exemplo para **Dell SonicWALL Mobile Connect**: &lt;MobileConnect&gt;&lt;Compression&gt;false&lt;/Compression&gt;&lt;debugLogging&gt;True&lt;/debugLogging&gt;&lt;packetCapture&gt;False&lt;/packetCapture&gt;&lt;/MobileConnect&gt;. Exemplo para **F5 Edge Client**: &lt;f5-vpn-conf&gt;&lt;single-sign-on-credential /&gt;&lt;/f5-vpn-conf&gt;. Consulte a documentação de cada fabricante relativa à VPN para obter mais informações sobre como escrever comandos XML personalizados.
**Lista de pesquisa de Sufixos DNS** (apenas no Windows Phone 8.1)|Especifique um sufixo DNS em cada linha. Cada sufixo DNS especificado será procurado ao ligar-se a um site com um nome abreviado. Por exemplo, especifique os sufixos DNS **dominio1.contoso.com** e **dominio2.contoso.com**, aceda ao URL **http://omeuwebsite** e os URLs **http://omeuwebsite.dominio1.contoso.com** e **http://omeuwebsite.dominio2.contoso.com** serão procurados.
**Ignorar a VPN quando estiver ligado à rede Wi-Fi da empresa** (apenas no Windows Phone 8.1)|Selecione esta opção para especificar que a ligação VPN não será utilizada quando o dispositivo estiver ligado à rede Wi-Fi da empresa.
**Ignorar a VPN quando estiver ligado à rede Wi-Fi doméstica** (apenas no Windows Phone 8.1)|Selecione esta opção para especificar que a ligação VPN não será utilizada quando o dispositivo estiver ligado à rede Wi-Fi doméstica.

As seguintes definições adicionais estão disponíveis para computadores e dispositivos móveis com o Windows 10.

Nome da definição  |Mais informações  
---------|---------
**Regras network traffic (de tráfego de rede)**|Selecione os protocolos, as portas locais e remotas e os intervalos de endereços que irão estar ativados para a ligação VPN. Se não criar uma regra de tráfego de rede, todos os protocolos, portas e intervalos de endereços estarão ativados. Depois de criar uma regra, a ligação VPN apenas utilizará os protocolos, portas e intervalos de endereços que especificar nessa regra.
**Rotas**|Selecione as rotas que a ligação VPN irá utilizar.
**Servidores DNS**| Selecione os servidores DNS que a ligação VPN utilizará depois de a ligação ser estabelecida.         
**Aplicações associadas**|Forneça uma lista de aplicações que irão utilizar automaticamente a ligação VPN. O tipo de aplicação irá determinar o identificador de aplicações. Para uma aplicação universal, forneça o nome de família do pacote. Para uma aplicação de ambiente de trabalho, forneça o caminho do ficheiro da aplicação.          


> [!IMPORTANT]
> Recomendamos a proteção de todas as listas de aplicações que compilar para utilização na configuração da VPN por aplicação. Se um utilizador não autorizado modificar a sua lista e importá-la para a lista de aplicações VPN por aplicação, irá autorizar potencialmente o acesso VPN para aplicações que não devem ter acesso. Uma forma de proteger as listas de aplicação é utilizar uma lista de controlo de acesso (ACL).

Segue-se um exemplo de quando poderá utilizar definições de limites da empresa. Se pretender ativar a VPN apenas para Ambiente de Trabalho Remoto, crie uma regra de tráfego de rede que permita o tráfego para o protocolo 27 na porta externa 3996. Nenhum outro tráfego utilizará a VPN.

Definir rotas em limites empresariais é útil quando o seu tipo de ligação VPN não lhe permite definir o modo como o tráfego é processado em túnel dividido. Nesse caso, utilize **Rotas** para listar as rotas que utilizarão a VPN.

Pode restringir a utilização da VPN para dispositivos com o Windows 10 para aplicações específicas, criando uma definição de OMA-URI personalizada.

A nova política é apresentada no nó **Políticas de Configuração** da área de trabalho **Política**.

### <a name="on-demand-vpn-for-ios-devices"></a>VPN a pedido para dispositivos iOS
Pode configurar a VPN a pedido para dispositivos iOS 8.0 e posteriores.

> [!NOTE]
>  
> Não é possível utilizar a VPN por aplicação e a VPN a pedido na mesma política.

1. Na página de configuração de políticas, localize **Regras a pedido para esta ligação VPN**. As colunas têm a etiqueta **Correspondência**, a condição que as regras verificam, e **Ação**, a ação que a política aciona quando a condição é cumprida.
2. Escolha **Adicionar** para criar uma regra. Existem dois tipos de correspondências que pode configurar na regra. Só pode configurar um dos seguintes tipos por regra.
  - **SSIDs**, que se referem às redes sem fios.
  - **Domínios de pesquisa DNS**, que são...  Pode utilizar nomes de domínio completamente qualificados como *equipa.corp.contoso.com* ou utilizar domínios como *contoso.com*, que é o equivalente a utilizar * *.contoso.com*.
3. Opcional: forneça uma pesquisa de cadeia de URL, que é um URL que a regra utiliza como um teste. Se o dispositivo no qual está instalado este perfil for capaz de aceder a este URL sem redirecionamento, a VPN será estabelecida e ligará o dispositivo ao URL de destino. O utilizador não verá o site de pesquisa de cadeia de URL. Um exemplo de uma pesquisa de cadeia de URL é o endereço de um servidor Web de auditoria que verifica a conformidade do dispositivo antes de ligar a VPN. Outra possibilidade é a de o URL testar a capacidade de a VPN estabelecer ligação a um site, antes de ligar o dispositivo ao URL de destino através da VPN.
4. Escolha uma das seguintes ações:
  - **Ligar**
  - **Avaliar ligação**, que tem três definições: a. **Ação de domínio** – escolha **Ligar caso seja necessário** ou **Nunca ligar**
    ; b. **Lista de domínios separada por vírgulas** – configure esta opção apenas se escolher uma **Ação de domínio** em **Ligar caso seja necessário**
     c. **Pesquisa de cadeia de URL necessária** – um URL de HTTP ou HTTPS (preferencial) como *https://vpntestprobe.contoso.com*. A regra verificará se existe uma resposta deste endereço. Caso contrário e se a **Ação de domínio** for **Ligar caso seja necessário**, será acionada a VPN.
     > [!TIP]
     >
     >Um exemplo de quando utilizar esta ação é quando alguns sites na rede da sua empresa requerem uma ligação de rede empresarial de VPN ou direta, mas outras não. Se estiver listada em **Lista de domínios de pesquisa DNS separada por vírgulas** *corp.contoso.com*, pode escolher **Ligar caso seja necessário** e, em seguida, listar sites específicos dentro dessa rede que possam precisar de uma VPN, tais como *sharepoint.corp.contoso.com*. A regra, em seguida, verificará se *vpntestprobe.contoso.com* pode ser contactado. Se não for possível, será acionada a VPN para o site do SharePoint.
  - **Ignorar** – esta ação não efetua alterações na conetividade da VPN. Se a VPN estiver ligada, deixe-a ligada; se não estiver ligada, não a ligue. Por exemplo, poderá ter uma regra que liga a VPN para todos os seus sites internos da empresa, mas deseja que um desses sites internos esteja acessível apenas quando o dispositivo está, realmente, ligado à rede empresarial. Nesse caso, poderia criar uma regra para ignorar para esse site.
  - **Desligar** – desligue dispositivos da VPN quando as condições corresponderem. Por exemplo, pode listar as redes sem fios da empresa no campo **SSIDs** e criar uma regra que desliga os dispositivos da VPN, quando estes ligam a uma dessas redes.

As regras específicas do domínio são avaliadas antes das regras de todos os domínios.


## <a name="deploy-the-policy"></a>Implementar a política

1.  Na área de trabalho **Policy**, selecione a que pretende implementar e escolha **Manage Deployment**.

2.  Na caixa de diálogo **Manage Deployment**, para:

    -   Para implementar a política, selecione um ou mais grupos nos quais pretende implementá-la e, em seguida, escolha **Add** &gt; **OK**.

    -   Para fechar a caixa de diálogo sem implementar a política, escolha **Cancel**.


Após uma implementação efetuada com êxito, os utilizadores verão o nome da ligação VPN especificado na lista de ligações VPN nos respetivos dispositivos.

Um resumo do estado e alertas na página **Overview** da área de trabalho **Policy** identificam problemas com a política que necessitam da sua atenção. Para além disso, é apresentado um resumo de estado na área de trabalho Dashboard.





<!--HONumber=Dec16_HO3-->


