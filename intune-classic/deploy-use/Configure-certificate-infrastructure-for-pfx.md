---
title: Configurar a infraestrutura de certificados para PFX
description: Criar e implementar perfis de certificado .PFX.
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 11/17/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2c543a02-44a5-4964-8000-a45e3bf2cc69
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: vinaybha
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 66306a30a0b1af941d616aeeb005a8ea1ba983b8
ms.sourcegitcommit: 1a54bdf22786aea1cf1b497d54024470e1024aeb
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/10/2017
---
# <a name="configure-certificate-infrastructure"></a>Configurar a infraestrutura de certificados

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Este tópico descreve o que precisa para criar e implementar perfis de certificado .PFX.

Para efetuar qualquer autenticação baseada em certificado na sua organização, é necessário uma Autoridade de Certificação Empresarial.

Para utilizar perfis de certificado .PFX, para além da Autoridade de Certificação Empresarial, também é necessário:

-   Um computador que possa comunicar com a Autoridade de Certificação. Em alternativa, pode utilizar o próprio computador da Autoridade de Certificação.

-  O Intune Certificate Connector, que é executado no computador que pode comunicar com a Autoridade de Certificação.

## <a name="on-premises-infrastructure-description"></a>Descrição da infraestrutura no local


-    **Domínio do Active Directory**: todos os servidores indicados nesta secção (exceto o Servidor Proxy de Aplicações Web) têm de ser associados ao seu domínio do Active Directory.

-  **Autoridade de Certificação**: uma Autoridade de Certificação (AC) Empresarial que é executada numa edição Enterprise do Windows Server 2008 R2 ou posterior. Não é suportada uma AC Autónoma. Para obter instruções sobre como configurar uma Autoridade de Certificação, consulte [Instalar a Autoridade de Certificação](http://technet.microsoft.com/library/jj125375.aspx).
    Se a sua AC for executada no Windows Server 2008 R2, tem de [instalar a correção de KB2483564](http://support.microsoft.com/kb/2483564/).

-  **Um computador que possa comunicar com a Autoridade de Certificação**. Em alternativa, utilize o próprio computador da Autoridade de Certificação.
-  **Microsoft Intune Certificate Connector**: utilize a consola de administração do Intune para transferir o instalador do **Certificate Connector** (**ndesconnectorssetup.exe**). Em seguida, pode executar **ndesconnectorssetup.exe** no computador onde pretende instalar o Certificate Connector. Para perfis de certificado .PFX, instale o Certificate Connector no computador que comunica com a Autoridade de Certificação.
-  **Servidor Proxy de Aplicações Web** (opcional): pode utilizar um servidor com o Windows Server 2012 R2 ou posterior como um servidor Proxy de Aplicações Web (WAP). Esta configuração:
    -  Permite aos dispositivos receberem certificados através de uma ligação à Internet.
    -  É uma recomendação de segurança quando os dispositivos se ligam através da Internet para receber e renovar certificados.

 > [!NOTE]           
> -    O servidor que aloja o WAP [tem de instalar uma atualização](http://blogs.technet.com/b/ems/archive/2014/12/11/hotfix-large-uri-request-in-web-application-proxy-on-windows-server-2012-r2.aspx) que ativa o suporte para os URLs longos que são utilizados pelo Serviço de Inscrição de Dispositivos de Rede (NDES). Esta atualização está incluída no [rollup da atualização de dezembro de 2014](http://support.microsoft.com/kb/3013769)ou individualmente a partir do [KB3011135](http://support.microsoft.com/kb/3011135).
>-  Além disso, o servidor que aloja o WAP tem de ter um certificado SSL que corresponda ao nome que está a ser publicado em clientes externos, e tem de confiar no certificado SSL utilizado no servidor NDES. Estes certificados permitem ao servidor do WAP terminar a ligação SSL de clientes e criar uma nova ligação SSL ao servidor do NDES.
    Para obter informações sobre certificados para o WAP, veja a secção **Planear os certificados** do artigo [Planear a Publicação de Aplicações Através do Proxy de Aplicações Web](https://technet.microsoft.com/library/dn383650.aspx). Para obter informações gerais sobre os servidores WAP, veja [Trabalhar com o Proxy da Aplicação Web](http://technet.microsoft.com/library/dn584113.aspx).|


### <a name="certificates-and-templates"></a>Certificados e Modelos

|Objeto|Detalhes|
|----------|-----------|
|**Modelo de Certificado**|Configura este modelo na sua AC emissora.|
|**Certificado da AC de Raiz Fidedigna**|Exporta-o como um ficheiro **.cer** a partir da AC emissora ou qualquer dispositivo que confia na AC emissora e implementa-o em dispositivos com o perfil de certificado da AC Fidedigna.<br /><br />Utiliza apenas um certificado da AC de Raiz Fidedigna por cada plataforma de sistema operativo e associa-o a cada perfil de Certificado de Raiz Fidedigna que criar.<br /><br />Pode utilizar certificados da AC de Raiz Fidedigna adicionais quando necessário. Por exemplo, pode fazê-lo para conceder um estatuto de fidedignidade a uma AC que assina os certificados de autenticação do servidor para os seus pontos de acesso Wi-Fi.|


## <a name="configure-your-infrastructure"></a>Configurar a sua infraestrutura
Antes de poder configurar perfis de certificado, tem de concluir as tarefas seguintes. Estas tarefas requerem conhecimento do Windows Server 2012 R2 e dos Serviços de Certificados do Active Directory (ADCS):

- **Tarefa 1** – configurar modelos de certificado na autoridade de certificação.
- **Tarefa 2** – ativar, instalar e configurar o Intune Certificate Connector.

### <a name="task-1---configure-certificate-templates-on-the-certification-authority"></a>Tarefa 1 – configurar modelos de certificado na autoridade de certificação
Nesta tarefa, vai publicar o modelo de certificado.

##### <a name="to-configure-the-certification-authority"></a>Para configurar a autoridade de certificação

1.  Na AC emissora, utilize o snap-in Modelos de Certificado para criar um novo modelo personalizado ou copie e edite um modelo existente (como o Modelo de Utilizador) para utilizar com o .PFX.

    O modelo deve incluir o seguinte:

    -   Especifique um **Nome a apresentar do modelo** amigável.

    -   No separador **Nome do Requerente**, selecione **Fornecer no pedido**. 

    -   No separador **Extensões** certifique-se de que a **Descrição das Políticas de Aplicações** inclui a **Autenticação do Cliente**.

        > [!IMPORTANT]
        > Para os modelos de certificado iOS e Mac OS X, no separador **Extensões**, edite **Utilização de Chaves** e certifique-se de que a opção **A assinatura é uma prova de origem** não está selecionada.

2.  Reveja o separador **Período de validade** no separador **Geral** do modelo. Por predefinição, o Intune utiliza o valor configurado no modelo. Contudo, tem a opção de configurar a AC para permitir que o autor do pedido especifique um valor diferente que pode, posteriormente, configurar a partir da Consola de administração do Intune. Se pretender utilizar sempre o valor no modelo, ignore o resto deste passo.

    > [!IMPORTANT]
    > As plataformas iOS e Mac OS X utilizam sempre o conjunto de valores no modelo, independentemente de outras configurações que efetuar.

    Para configurar a AC de modo a que permita ao autor do pedido especificar o período de validade, execute os seguintes comandos na AC:

    a.  **certutil -setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE**

    b.  **net stop certsvc**

    c.  **net start certsvc**

3.  Na AC emissora, utilize o snap-in Autoridade de Certificação para publicar o modelo de certificado.

    a.  Selecione o nó **Modelos de Certificados**, clique em **Ação**-&gt; **Novo** &gt; **Modelo de certificado a emitir** e, em seguida, selecione o modelo que criou no passo 2.

    b.  Valide o modelo publicado ao visualizá-lo na pasta **Modelos de Certificado**.

4.  No computador da AC, certifique-se de que o computador que aloja o Intune Certificate Connector tem permissão de inscrição, para que possa aceder ao modelo que foi utilizado na criação do perfil .PFX. Defina essa permissão no separador **Segurança** das propriedades do computador da AC.

### <a name="task-2---enable-install-and-configure-the-intune-certificate-connector"></a>Tarefa 2 – ativar, instalar e configurar o Intune Certificate Connector
Nesta tarefa irá:

Transferir, instalar e configurar o Certificate Connector.

##### <a name="to-enable-support-for-the-certificate-connector"></a>Para ativar o suporte do Certificate Connector

1.  Abra a [consola de administração do Intune](https://manage.microsoft.com) e escolha **Administração** &gt; **Certificate Connector**.

2.  Escolha **Configurar Certificate Connector no Local**.

3.  Selecione **Ativar Certificate Connector**e, em seguida, escolha **OK**.

##### <a name="to-download-install-and-configure-the-certificate-connector"></a>Para transferir, instalar e configurar o Certificate Connector

1.  Abra a [consola de administração do Intune](https://manage.microsoft.com) e, em seguida, escolha **Administração** &gt; **Gestão de Dispositivos Móveis** &gt; **Certificate Connector** &gt; **Transferir Certificate Connector**.

2.  Após a conclusão da transferência, execute o instalador transferido (**ndesconnectorssetup.exe**).

  Execute o instalador no computador com capacidade para ligar à Autoridade de Certificação. Escolha a opção .PFX Distribution e, em seguida, escolha **Instalar**. Após a conclusão da instalação, continue ao criar um perfil de certificado, conforme descrito em [Configurar perfis de certificado](configure-intune-certificate-profiles.md).

   <!-- Not sure about step 3 below -->

3.  Quando lhe for pedido o certificado de cliente para o Certificate Connector, escolha **Selecionar** e selecione o certificado de **autenticação de cliente** que instalou na Tarefa 3.

    Após selecionar o certificado de autenticação de cliente, é encaminhado para a superfície do **Certificado de Cliente do Microsoft Intune Certificate Connector** . Embora o certificado que selecionou não seja mostrado, escolha **Seguinte** para ver as propriedades do certificado. Em seguida, escolha **Seguinte**, e, em seguida, **Instalar**.

4.  Após o assistente ser concluído, mas antes de o fechar, clique em **Iniciar a IU do Certificate Connector**.

    > [!TIP]
    > Se fechar o assistente antes de iniciar a IU do Certificate Connector, pode abri-lo novamente ao executar o seguinte comando:
    >
    > **&lt;install_Path&gt;\NDESConnectorUI\NDESConnectorUI.exe**

5.  Na IU do **Certificate Connector** :

    a. Escolha **Iniciar Sessão** e introduza as suas credenciais de administrador do serviço Intune ou as credenciais de administrador inquilino com permissão de administração global.

    b. Selecione o separador **Avançadas** e, em seguida, forneça credenciais para uma conta que tenha permissão para **Emitir e Gerir Certificados** na sua Autoridade de Certificados emissora.

    c. Escolha **Aplicar**.

    Agora, pode fechar a IU do Certificate Connector.

6.  Abra uma linha de comandos e escreva **services.msc**. Em seguida, prima **Enter**, clique com o botão direito do rato no **Serviço Connector do Intune** e escolha **Reiniciar**.


### <a name="next-steps"></a>Passos seguintes
Está agora pronto para configurar perfis de certificado, conforme descrito em [Configurar perfis de certificado](Configure-Intune-certificate-profiles.md).
