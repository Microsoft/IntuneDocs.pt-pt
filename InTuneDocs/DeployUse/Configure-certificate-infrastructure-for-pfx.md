---
title: Configurar a infraestrutura de certificados para PFX | Microsoft Intune
description:
keywords:
author: nbigman
manager: jeffgilb
ms.date: 05/16/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 2c543a02-44a5-4964-8000-a45e3bf2cc69

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: vinaybha
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:


---
# Configurar a infraestrutura de certificados
Este tópico descreve o que precisa para criar e implementar perfis de certificado.

Para efetuar qualquer autenticação baseada em certificado na sua organização, é necessário uma Autoridade de Certificação Empresarial.

Para utilizar perfis de certificado .PFX, para além da Autoridade de Certificação Empresarial, também é necessário:

-   Um computador que possa comunicar com a Autoridade de Certificação. Em alternativa, pode utilizar o próprio computador da Autoridade de Certificação.

 -  O Intune Certificate Connector, que é executado no computador que pode comunicar com a Autoridade de Certificação.

## Descrição da infraestrutura no local


-    **Domínio do Active Directory**: todos os servidores indicados nesta secção (exceto o Servidor de Proxy de Aplicações Web) têm de ser associados ao seu domínio do Active Directory.

-  **Autoridade de Certificação** (AC): uma Autoridade de Certificação (AC) Empresarial que seja executada numa edição Enterprise do Windows Server 2008 R2 ou posterior. Não é suportada uma AC Autónoma. Para obter instruções sobre como configurar uma Autoridade de Certificação, consulte [Instalar a Autoridade de Certificação](http://technet.microsoft.com/library/jj125375.aspx).
    Se a sua AC for executada no Windows Server 2008 R2, tem de [instalar a correção de KB2483564](http://support.microsoft.com/kb/2483564/).

 -  **Um computador que possa comunicar com a Autoridade de Certificação**. Em alternativa, utilize o próprio computador da Autoridade de Certificação.
-  **Microsoft Intune Certificate Connector**: utilize a consola de administração do Intune para transferir o instalador do **Certificate Connector** (**ndesconnectorssetup.exe**). Em seguida, pode executar **ndesconnectorssetup.exe** no computador onde pretende instalar o Certificate Connector. Para perfis de certificado .PFX, instale o Certificate Connector no computador que comunica com a Autoridade de Certificação.
-  **Servidor Proxy de Aplicações Web** (opcional): pode utilizar um servidor com o Windows Server 2012 R2 ou posterior como um servidor Proxy de Aplicações Web (WAP). Esta configuração:
    -  Permite aos dispositivos receberem certificados através de uma ligação à Internet.
    -  É uma recomendação de segurança quando os dispositivos se ligam através da Internet para receber e renovar certificados.

 > [!NOTE]           
> -    O servidor que aloja o WAP [tem de instalar uma atualização](http://blogs.technet.com/b/ems/archive/2014/12/11/hotfix-large-uri-request-in-web-application-proxy-on-windows-server-2012-r2.aspx) que ativa o suporte para os URLs longos que são utilizados pelo Serviço de Inscrição de Dispositivos de Rede. Esta atualização está incluída no [rollup da atualização de dezembro de 2014](http://support.microsoft.com/kb/3013769)ou individualmente a partir do [KB3011135](http://support.microsoft.com/kb/3011135).
>-  Além disso, o servidor que aloja o WAP tem de ter um certificado SSL que corresponda ao nome que está a ser publicado em clientes externos, e tem de confiar no certificado SSL utilizado no servidor do NDES. Estes certificados permitem ao servidor do WAP terminar a ligação SSL de clientes e criar uma nova ligação SSL ao servidor do NDES.
Para obter informações sobre certificados para o WAP, consulte a secção **Planear os certificados** do artigo [Planear a Publicação de Aplicações Através do Proxy de Aplicações Web](https://technet.microsoft.com/library/dn383650.aspx). Para obter informações gerais sobre os servidores WAP, veja [Trabalhar com o Proxy da Aplicação Web](http://technet.microsoft.com/library/dn584113.aspx).|


### Certificados e Modelos

|Objeto|Detalhes|
|----------|-----------|
|**Modelo de Certificado**|Configura este modelo na sua AC emissora.|
|**Certificado da AC de Raiz Fidedigna**|Exporta-o como um ficheiro **.cer** a partir da AC emissora ou qualquer dispositivo que confia na AC emissora e implementa-o em dispositivos com o perfil de certificado da AC Fidedigna.<br /><br />Utiliza apenas um certificado da AC de Raiz Fidedigna por cada plataforma de sistema operativo e associa-o a cada perfil de Certificado de Raiz Fidedigna que criar.<br /><br />Pode utilizar certificados da AC de Raiz Fidedigna adicionais quando necessário. Por exemplo, pode fazê-lo para conceder um estatuto de fidedignidade a uma AC que assina os certificados de autenticação do servidor para os seus pontos de acesso Wi-Fi.|


## Configurar a sua infraestrutura
Antes de poder configurar perfis de certificado, tem de concluir as seguintes tarefas, o que requer conhecimento do Windows Server 2012 R2 e dos Serviços de Certificados do Active Directory (ADCS):

**Tarefa 1** -configurar modelos de certificado na autoridade de certificação **Tarefa 2** - ativar, instalar e configurar o Intune Certificate Connector

### Tarefa 1 - configurar modelos de certificado na autoridade de certificação
Nesta tarefa, vai publicar o modelo de certificado

##### Para configurar a autoridade de certificação

1.  Na AC emissora, utilize o snap-in Modelos de Certificado para criar um novo modelo personalizado ou copie um modelo existente e, em seguida, edite um modelo existente (como o Modelo de Utilizador) para utilizar com o .pFX.

    O modelo tem de ter as seguintes configurações:

    -   Especifique um **Nome a apresentar do modelo** amigável.

    -   No separador **Nome do Requerente** , selecione **Fornecer no pedido**. (A segurança é imposta pelo módulo de política do Intune para o NDES).

    -   No separador **Extensões** certifique-se de que a **Descrição das Políticas de Aplicações** inclui a **Autenticação do Cliente**.

        > [!IMPORTANT] Para os modelos de certificado iOS e Mac OS X, no separador **Extensões**, edite **Utilização de Chaves** e certifique-se de que a opção **A assinatura é uma prova de origem** não está selecionada.


3.  Reveja o separador **Período de validade** no separador **Geral** do modelo. Por predefinição, o Intune utiliza o valor configurado no modelo. Contudo, tem a opção de configurar a AC para permitir que o autor do pedido especifique um valor diferente que pode, posteriormente, configurar a partir da Consola de administração do Intune. Se pretender utilizar sempre o valor no modelo, ignore o resto deste passo.

    > [!IMPORTANT] As plataformas iOS e Mac OS X utilizam sempre o conjunto de valores no modelo, independentemente de outras configurações que fizer.

    Para configurar a AC de modo a que permita ao autor do pedido especificar o período de validade, execute os seguintes comandos na AC:

    1.  **certutil -setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE**

    2.  **net stop certsvc**

    3.  **net start certsvc**

4.  Na AC emissora, utilize o snap-in Autoridade de Certificação para publicar o modelo de certificado.

    1.  Selecione o nó **Modelos de Certificados**, clique em **Ação**-&gt; **Novo** &gt; **Modelo de Certificado a Emitir** e, em seguida, selecione o modelo que criou no passo 2.

    2.  Valide o modelo publicado ao visualizá-lo na pasta **Modelos de Certificado** .

5.  No computador da AC, certifique-se de que o computador que aloja o Intune Certificate Connector tem permissão de inscrição, para que possa aceder ao modelo que foi utilizado na criação do perfil .PFX. Defina essa permissão no separador **Segurança** das propriedades do computador da AC.

### Tarefa 2 - ativar, instalar e configurar o Intune Certificate Connector
Nesta tarefa irá:

Transferir, instalar e configurar o Certificate Connector

##### Para ativar o suporte do Certificate Connector

1.  Abra a [consola de administração do Intune](https://manage.microsoft.com), clique em **Administração** &gt; **Certificate Connector**.

2.  Clique em **Configurar Certificate Connector no Local**.

3.  Selecione **Ativar Certificate Connector**e, em seguida, clique em **OK**.

##### Para transferir, instalar e configurar o Certificate Connector

1.  Abra a [consola de administração do Intune](https://manage.microsoft.com) e, em seguida, clique em **Administração** &gt; **Gestão de Dispositivos Móveis** &gt; **Certificate Connector** &gt; **Transferir Certificate Connector**.

2.  Após a conclusão da transferência, execute o instalador transferido (**ndesconnectorssetup.exe**):

  Execute o instalador no computador com capacidade para ligar à Autoridade de Certificação. Escolha a opção .PFX Distribution e clique em Instalar. Após a conclusão da instalação, continue ao criar um perfil de certificado, conforme descrito em [Configure certificate profiles (Configurar perfis de certificado)](configure-intune-certificate-profiles.md).

   <!-- Not sure about step 3 below -->

3.  Quando lhe for pedido o certificado de cliente para o Certificate Connector, clique em **Selecionar** e selecione o certificado de **autenticação de cliente** que instalou na Tarefa 3.

    Após selecionar o certificado de autenticação de cliente, é encaminhado para a superfície do **Certificado de Cliente do Microsoft Intune Certificate Connector** . Embora o certificado que selecionou não seja apresentado, clique em **Seguinte** para ver as propriedades do certificado. Em seguida, clique em **Seguinte**e, em seguida, clique em **Instalar**.

4.  Após o assistente ser concluído, mas antes de o fechar, clique em **Iniciar a IU do Certificate Connector**.

    > [!TIP] Se fechar o assistente antes de iniciar a IU do Certificate Connector, pode abri-lo novamente ao executar o seguinte comando:
    >
    > **&lt;install_Path&gt;\NDESConnectorUI\NDESConnectorUI.exe**

5.  Na IU do **Certificate Connector** :

    Clique em **Iniciar Sessão** e introduza as suas credenciais de administrador do serviço Intune ou as credenciais de administrador inquilino com a permissão de administração global.

  <!--  If your organization uses a proxy server and the proxy is needed for the NDES server to access the Internet, click **Use proxy server** and then provide the proxy server name, port, and account credentials to connect.-->

    Selecione o separador **Avançadas** e, em seguida, forneça credenciais para uma conta que tenha permissão para **Emitir e Gerir Certificados** na sua Autoridade de Certificados e, em seguida, clique em **Aplicar**.

    Agora, pode fechar a IU do Certificate Connector.

6.  Abra uma linha de comandos e introduza **services.msc**, prima **Enter**, clique com o botão direito do rato no **Serviço Connector do Intune** e, em seguida, clique em **Reiniciar**.

Para se certificar de que o serviço está em execução, abra um browser e introduza o seguinte URL que deverá devolver um erro **403** :

**http:// &lt;FQDN_of_your_NDES_server&gt;/certsrv/mscep/mscep.dll**

### Passos seguintes
Está agora pronto para configurar perfis de certificado, conforme descrito em [Configure certificate profiles (Configurar perfis de certificado)](Configure-Intune-certificate-profiles.md).


<!--HONumber=Jun16_HO1-->


