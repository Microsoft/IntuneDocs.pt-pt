---
# required metadata

title: Ligações VPN | Microsoft Intune
description:
keywords:
author: Nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: abc57093-7351-408f-9f41-a30877f96f73

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Ligações VPN no Microsoft Intune
 As Redes Virtuais Privadas (VPN) permitem-lhe conceder aos seus utilizadores acesso remoto protegido à rede da sua empresa. Os utilizadores remotos podem trabalhar como se os respetivos dispositivos estivessem ligados fisicamente à rede. Os dispositivos utilizam um perfil de ligação VPN para iniciar uma ligação com o servidor VPN. Utilize **Perfis de VPN** no Microsoft Intune para implementar definições da VPN em utilizadores e dispositivos na sua organização. Ao implementar estas definições, estará a minimizar o esforço do utilizador final para se ligar aos recursos na rede da empresa.

Por exemplo, pretende aprovisionar todos os dispositivos iOS com as definições necessárias para estabelecer uma ligação a uma partilha de ficheiros na rede da empresa. Pode criar um perfil da VPN com as definições necessárias para se ligar à rede da empresa e, em seguida, implementar este perfil em todos os utilizadores com dispositivos iOS. Os utilizadores verão a ligação VPN na lista de redes disponíveis e poderão ligar-se sem qualquer esforço.

Pode configurar os seguintes tipos de dispositivo com perfis da VPN:

* Dispositivos a executar o Android 4 e posterior
* Dispositivos com iOS 7.1 e posterior
* Dispositivos com Mac OS X 10.9 e posterior
* Dispositivos inscritos com Windows 8.1 e posterior
* Dispositivos a executar o Windows Phone 8.1 e posterior
* Dispositivos que executam o Windows 10 Desktop e Mobile.

As opções de configuração do perfil da VPN variam consoante o tipo de dispositivo selecionado.

## Tipos de ligação VPN

O Intune suporta a criação de perfis de VPN que utilizem os seguintes tipos de ligação:




Tipo de ligação |iOS e Mac OS X  |Android  |Windows 8,1|Windows RT|Windows RT 8.1|Windows Phone 8.1  |Windows 10 Desktop e Mobile |
---------|---------|---------|---------|---------|---------
Cisco AnyConnect |Sim |Sim   |Não    |     Não    |Não  |Não    | Sim, (apenas OMA-URI, Mobile)|     
Pulse Secure |Sim  |Sim |Sim   |Não  |Sim  |Sim| Sim|        
F5 Edge Client |Sim |Sim |Sim |Não  |Sim  |   Sim |  Sim|   
Dell SonicWALL Mobile Connect |Sim |Sim |Sim |Não  |Sim |Sim |Sim|         
CheckPoint Mobile VPN |Sim |Sim |Sim |Sim |Sim|Sim|Sim|




> [!IMPORTANT] Antes de poder utilizar os perfis da VPN implementados num dispositivo, tem de instalar a aplicação VPN aplicável para o perfil. Pode utilizar as informações no tópico [Implementar aplicações em dispositivos móveis no Microsoft Intune](deploy-apps-in-microsoft-intune.md), que o ajuda a implementar a aplicação aplicável com o Intune.  

 Saiba como criar perfis de VPN personalizados com definições de URI em [Configurações personalizadas para perfis de VPN](custom-configurations-for-vpn-profiles.md).     

## Como os perfis da VPN são protegidos

Os perfis da VPN podem utilizar vários tipos de ligação e protocolos diferentes de fabricantes diferentes. Normalmente, estas ligações são protegidas através de um de dois métodos:

### Certificados

Quando cria o perfil da VPN, pode escolher um perfil de certificado SCEP ou .PFX que tenha criado anteriormente no Intune.

Este é conhecido como o certificado de identidade e é utilizado para autenticar um perfil de certificado fidedigno (ou um certificado de raiz) que criou para estabelecer que o dispositivo do utilizador tem permissões para se ligar. O certificado fidedigno é implementado no computador que irá autenticar a ligação VPN (normalmente, o servidor VPN).

Para obter mais informações sobre como criar e utilizar perfis de certificado no Intune, consulte [Proteger o acesso a recursos com perfis de certificado](secure-resource-access-with-certificate-profiles.md).

### Nome de utilizador e palavra-passe

O utilizador é autenticado no servidor VPN ao fornecer o respetivo nome de utilizador e palavra-passe.

## Criar um perfil da VPN

1. Na [consola de administração do Microsoft Intune](https://manage.microsoft.com), clique em **Política > Adicionar Política**.
2. Selecione um modelo para a nova política expandindo o tipo de dispositivo relevante e, em seguida, selecione o perfil da VPN desse dispositivo:
    * **Perfil da VPN (Android 4 e posterior)**
    * **Perfil da VPN (iOS 7.1 e posterior)**
    * **Perfil da VPN (Mac OS X 10.9 e posterior)**
    * **Perfil da VPN (Windows 8.1 e posterior)**
    * **Perfil da VPN (Windows Phone 8.1 e posterior)**
    * **Perfil da VPN (Windows 10 Desktop e Mobile e posterior)**

    Só pode criar e implementar uma política de perfil da VPN personalizada. As definições recomendadas não estão disponíveis.

3. Utilize a seguinte tabela que o ajuda a configurar as definições de perfil da VPN:

Nome da definição  |Mais informações  
---------|---------
**Nome**     |Introduza um nome exclusivo para o perfil da VPN, de modo a conseguir identificá-lo na consola do Intune.         
**Descrição**     |Forneça uma descrição geral do perfil da VPN e outras informações relevantes que poderão ajudá-lo a localizá-lo.         
**Nome da ligação VPN (apresentado aos utilizadores)**     |Especifique um nome para o perfil da VPN. Este é nome que será visto pelos utilizadores na lista de ligações VPN disponíveis nos respetivos dispositivos.         
**Tipo de ligação**     |  Selecione um dos seguintes tipos de ligação para utilizar no perfil da VPN: **Cisco AnyConnect** (não disponível para Windows 8.1 nem Windows Phone 8.1), **Pulse Secure**, **F5 Edge Client**, **Dell SonicWALL Mobile Connect**, **CheckPoint Mobile VPN**
**Descrição do servidor VPN**     | Especifique uma descrição do servidor VPN ao qual os dispositivos serão ligados. **Exemplo:** servidor VPN da Contoso. Se o tipo de ligação for **F5 Edge Client**, utilize o campo **Lista de servidores** para especificar uma lista de descrições e endereços IP de servidores.
**Endereço IP ou FQDN do servidor**    |Fornece o endereço IP ou nome de domínio completamente qualificado do servidor VPN ao qual os dispositivos serão ligados. **Exemplos:** 192.168.1.1, vpn.contoso.com.  Se o tipo de ligação for **F5 Edge Client**, utilize o campo **Lista de servidores** para especificar uma lista de descrições e endereços IP de servidores.         |         
**Lista de servidores**     |Clique em **Adicionar** para adicionar um servidor VPN novo para utilizar na ligação VPN. Também pode especificar o servidor predefinido da ligação. Esta opção só é apresentada se o tipo de ligação for **F5 Edge Client**.         
**Enviar todo o tráfego de rede através da ligação VPN**     |Se selecionar esta opção, todo o tráfego de rede será enviado através da ligação VPN. Se não selecionar esta opção, o cliente negociará dinamicamente as rotas de divisão do túnel ao estabelecer a ligação com o servidor VPN de terceiros. Apenas as ligações à rede da empresa são enviadas através de um túnel VPN. Os túneis VPN não são utilizados ao ligar-se a recursos na Internet.
**Método de autenticação**| Selecione o método de autenticação utilizado pela ligação VPN: **Certificados** ou **Nome de Utilizador e Palavra-passe**. (O Nome de Utilizador e a Palavra-passe não estarão disponíveis se o tipo de ligação for Cisco AnyConnect). A opção **Método de autenticação** não está disponível para o Windows 8.1
**Memorizar as credenciais do utilizador sempre que iniciar sessão**|Selecione este opção para garantir que as credenciais do utilizador são memorizadas, para que o mesmo não tenha de introduzi-las sempre que for efetuada uma ligação.
**Selecione um certificado de cliente para autenticação de cliente (Certificado de Identidade)**|Selecione o certificado SCEP de cliente criado anteriormente que será utilizado para autenticar a ligação VPN. Para obter mais informações sobre como utilizar perfis de certificado no Intune, consulte [Proteger o acesso a recursos com perfis de certificado](secure-resource-access-with-certificate-profiles.md). Esta opção só é apresentada se o método de autenticação for **Certificados**.
**Função**| Especifique o nome da função de utilizador que tem acesso a esta ligação. Uma função de utilizador define opções e definições pessoais e ativa ou desativa funcionalidades de acesso específicas. Esta opção só é apresentada se o tipo de ligação for **Pulse Secure**.
**Realm**|Especifique o nome do realm de autenticação que pretende utilizar. Um realm de autenticação é um agrupamento de recursos de autenticação que é utilizado pelo tipo de ligação Pulse Secure. Esta opção só é apresentada se o tipo de ligação for **Pulse Secure**.
**Grupo ou domínio de início de sessão**|Especifique o nome do grupo ou domínio de início de sessão ao qual pretende ligar-se. Esta opção só é apresentada se o tipo de ligação for **Dell SonicWALL Mobile Connect**.
**Identificação digital**|Especifique uma cadeia de carateres, por exemplo "Código de Identificação Digital da Contoso", que será utilizada para verificar a fidedignidade do servidor VPN. A identificação digital pode ser: enviada para o cliente para que confie em qualquer servidor que apresente essa mesma impressão digital ao ligar. Se o dispositivo ainda não incluir a identificação digital, pedirá ao utilizador para confiar no servidor VPN ao qual se está a ligar e mostrar a identificação digital (o utilizador verifica-a manualmente e clica em **confiar** para ligar). Esta opção só é apresentada se o tipo de ligação for **CheckPoint Mobile VPN**.
**VPN Por Aplicação**|Selecione esta opção se pretende associar esta ligação VPN a uma aplicação iOS ou Mac OS X, para que a ligação seja aberta quando a aplicação é executada. Pode associar o perfil da VPN a uma aplicação ao implementar o software. Para obter mais informações, consulte [Implementar aplicações no Microsoft Intune](deploy-apps-in-microsoft-intune.md)
**Detetar automaticamente as definições de proxy** (apenas em iOS, Mac OS X, Windows 8.1 e Windows Phone 8.1)|Se o seu servidor VPN precisar de um servidor proxy para a ligação, especifique se pretende que os dispositivos detetem automaticamente as definições de ligação. Para mais informações, consulte a documentação do Windows Server.
**Utilizar um script de configuração automática** (apenas em iOS, Mac OS X, Windows 8.1 e Windows Phone 8.1)|Se o seu servidor VPN precisar de um servidor proxy para a ligação, especifique se pretende utilizar um script de configuração automática para selecionar as definições e, em seguida, especifique um URL para o ficheiro com as mesmas. Para mais informações, consulte a documentação do Windows Server.
**Utilizar um servidor proxy** (apenas em iOS, Mac OS X, Windows 8.1 e Windows Phone 8.1)|Se o seu servidor VPN precisar de um servidor proxy para a ligação, selecione este opção e, em seguida, especifique o endereço e número de porta do servidor proxy. Para mais informações, consulte a documentação do Windows Server.
**Ignorar as definições de proxy para endereços locais** (apenas em iOS, Mac OS X, Windows 8.1 e Windows Phone 8.1)|Se o seu servidor VPN precisar de um servidor proxy para a ligação, selecione esta opção caso não pretenda utilizar o servidor proxy para endereços locais especificados. Para mais informações, consulte a documentação do Windows Server.
**XML Personalizado** (Windows 8.1 e posteriores e Windows Phone 8.1 e posteriores)|Permite-lhe especificar comandos XML personalizados que configuram a ligação VPN. Exemplos. Para **Pulse Secure**: &lt;pulse-schema&gt;&lt;isSingleSignOnCredential&gt;true&lt;/isSingleSignOnCredential&gt;&lt;/pulse-schema&gt;. Para **CheckPoint Mobile VPN**: &lt;CheckPointVPN port="443" name="CheckPointSelfhost" sso="true"  debug="3" /&gt;. Para **Dell SonicWALL Mobile Connect**: &lt;MobileConnect&gt;&lt;Compression&gt;false&lt;/Compression&gt;&lt;debugLogging&gt;True&lt;/debugLogging&gt;&lt;packetCapture&gt;False&lt;/packetCapture&gt;&lt;/MobileConnect&gt;. Para **F5 Edge Client**: &lt;f5-vpn-conf&gt;&lt;single-sign-on-credential /&gt;&lt;/f5-vpn-conf&gt;. Consulte a documentação de cada fabricante relativa à VPN para mais informações sobre como escrever comandos XML personalizados.
**Lista de pesquisa de Sufixos DNS** (apenas no Windows Phone 8.1)|Especifique um sufixo DNS em cada linha. Cada sufixo DNS especificado será procurado ao ligar-se a um site com um nome abreviado. Por exemplo, especifique os sufixos DNS **dominio1.contoso.com** e **dominio2.contoso.com**, aceda ao URL **http://omeuwebsite** e os URLs **http://omeuwebsite.dominio1.contoso.com** e **http://omeuwebsite.dominio2.contoso.com** serão procurados.
**Ignorar a VPN quando estiver ligado à rede Wi-Fi da empresa** (apenas no Windows Phone 8.1)|Especifica que a ligação VPN não será utilizada quando o dispositivo estiver ligado à rede Wi-Fi da empresa.
**Ignorar a VPN quando estiver ligado à rede Wi-Fi doméstica** (apenas no Windows Phone 8.1)|Especifica que a ligação VPN não será utilizada quando o dispositivo estiver ligado à rede Wi-Fi doméstica.

As seguintes definições adicionais estão disponíveis para dispositivos do Windows 10 Desktop e Mobile

Nome da definição  |Mais informações  
---------|---------
**Regras network traffic (de tráfego de rede)**| Defina os protocolos, as portas locais e remotas e os intervalos de endereços que irão estar ativados para a ligação VPN. Se não criar uma regra de tráfego de rede, todos os protocolos, portas e intervalos de endereços estarão ativados. Depois de criar uma regra, apenas os protocolos, portas e intervalos de endereços que especificar nessa regra ou nas regras adicionais serão utilizados pela ligação VPN.
**Rotas**|Que rotas a ligação VPN irá utilizar.
**Servidores DNS**| Que servidores DNS são utilizados pela ligação VPN assim que tiver sido estabelecida a ligação.         
**Aplicações associadas**     | Pode fornecer uma lista de aplicações que irão utilizar automaticamente a ligação VPN. O tipo de aplicação irá determinar o identificador de aplicações. Para aplicações universais, indique o Nome da Família de Pacotes, e para aplicações de ambiente de trabalho, indique o caminho do ficheiro da aplicação.          


Apresentamos um exemplo de quando poderá utilizar definições de limites da empresa. Se pretender ativar a VPN apenas para ambiente de trabalho remoto, poderá criar uma regra de tráfego de rede que permita o tráfego para o número de protocolo 27 na porta externa 3996. Nenhum outro tráfego utilizará a VPN.

Definir rotas em limites empresariais é útil quando o seu tipo de ligação VPN não lhe permite definir o modo como o tráfego é processado em túnel dividido. Nesse caso, utilize **Rotas** para listar as rotas que utilizarão a VPN.

Pode restringir a utilização do dispositivo com o Windows 10 utilização VPN para aplicações específicas, criando uma definição de OMA-URI personalizada.

A nova política é apresentada no nó **Políticas de Configuração** da área de trabalho **Política** .

## Implementar a política

1.  Na área de trabalho **Política**, selecione a política que pretende implementar e, em seguida, clique em **Gerir Implementação**.

2.  Na caixa de diálogo **Gerir a Implementação** , para:

    -   **Para implementar a política** - selecione um ou mais grupos nos quais pretende implementar a política e, em seguida, clique em **Adicionar** &gt; **OK**.

    -   **Para fechar a caixa de diálogo sem implementar a política** - clique em **Cancelar**.


Após uma implementação efetuada com êxito, os utilizadores verão o nome da ligação VPN especificado na lista de ligações VPN nos respetivos dispositivos.

Um resumo do estado e alertas na página **Descrição Geral** da área de trabalho **Política** identificam problemas com a política que necessitam da sua atenção. Para além disso, é apresentado um resumo de estado na área de trabalho Dashboard.



<!--HONumber=May16_HO1-->

