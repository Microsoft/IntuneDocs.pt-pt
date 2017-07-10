---
title: Configurar e gerir certificados PKCS com o Intune
titleSuffix: Intune on Azure
description: Saiba como configurar a sua infraestrutura e, em seguida, crie e atribua certificados PKCS com o Intune."
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 06/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e189ebd1-6ca1-4365-9d5d-fab313b7e979
ms.reviewer: vinaybha
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 305a4d79aa81bd599369e72bc0cb307fdf452643
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/01/2017
---
# <a name="configure-and-manage-pkcs-certificates-with-intune"></a>Configurar e gerir certificados PKCS com o Intune
[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Este tópico mostra como configurar a sua infraestrutura e, em seguida, criar e atribuir perfis de certificados PKCS com o Intune.

Para efetuar qualquer autenticação baseada em certificado na sua organização, é necessário uma Autoridade de Certificação Empresarial.

Para utilizar perfis de certificado PKCS, para além da Autoridade de Certificação Empresarial, também é preciso:

-   Um computador que possa comunicar com a Autoridade de Certificação. Em alternativa, pode utilizar o próprio computador da Autoridade de Certificação.

-  O Intune Certificate Connector, que é executado no computador que pode comunicar com a Autoridade de Certificação.

## <a name="important-terms"></a>Termos importantes


-    **Domínio do Active Directory**: todos os servidores indicados nesta secção (exceto o Servidor Proxy de Aplicações Web) têm de ser associados ao seu domínio do Active Directory.

-  **Autoridade de Certificação**: uma Autoridade de Certificação (AC) Empresarial que é executada numa edição Enterprise do Windows Server 2008 R2 ou posterior. Não é suportada uma AC Autónoma. Para obter instruções sobre como configurar uma Autoridade de Certificação, consulte [Instalar a Autoridade de Certificação](http://technet.microsoft.com/library/jj125375.aspx).
    Se a sua AC for executada no Windows Server 2008 R2, tem de [instalar a correção de KB2483564](http://support.microsoft.com/kb/2483564/).

-  **Um computador que possa comunicar com a Autoridade de Certificação**. Em alternativa, utilize o próprio computador da Autoridade de Certificação.
-  **Microsoft Intune Certificate Connector**: no portal do Azure, transfira o instalador do **Certificate Connector** (**ndesconnectorssetup.exe**). Em seguida, pode executar **ndesconnectorssetup.exe** no computador onde pretende instalar o Certificate Connector. Para perfis de Certificado PKCS, instale o Certificate Connector no computador que comunica com a Autoridade de Certificação.
-  **Servidor Proxy de Aplicações Web** (opcional): pode utilizar um servidor com o Windows Server 2012 R2 ou posterior como um servidor Proxy de Aplicações Web (WAP). Esta configuração:
    -  Permite aos dispositivos receberem certificados através de uma ligação à Internet.
    -  É uma recomendação de segurança quando os dispositivos se ligam através da Internet para receber e renovar certificados.

 > [!NOTE]           
> -    O servidor que aloja o WAP [tem de instalar uma atualização](http://blogs.technet.com/b/ems/archive/2014/12/11/hotfix-large-uri-request-in-web-application-proxy-on-windows-server-2012-r2.aspx) que ativa o suporte para os URLs longos que são utilizados pelo Serviço de Inscrição de Dispositivos de Rede (NDES). Esta atualização está incluída no [rollup da atualização de dezembro de 2014](http://support.microsoft.com/kb/3013769)ou individualmente a partir do [KB3011135](http://support.microsoft.com/kb/3011135).
>-  Além disso, o servidor que aloja o WAP tem de ter um certificado SSL que corresponda ao nome que está a ser publicado em clientes externos, e tem de confiar no certificado SSL utilizado no servidor NDES. Estes certificados permitem ao servidor do WAP terminar a ligação SSL de clientes e criar uma nova ligação SSL ao servidor do NDES.
    Para obter informações sobre certificados para o WAP, consulte a secção **Planear os certificados** do artigo [Planear a Publicação de Aplicações Através do Proxy de Aplicações Web](https://technet.microsoft.com/library/dn383650.aspx). Para obter informações gerais sobre os servidores WAP, veja [Trabalhar com o Proxy da Aplicação Web](http://technet.microsoft.com/library/dn584113.aspx).|


## <a name="certificates-and-templates"></a>Certificados e modelos

|Objeto|Detalhes|
|----------|-----------|
|**Modelo de Certificado**|Configura este modelo na sua AC emissora.|
|**Certificado da AC de Raiz Fidedigna**|Exporta-o como um ficheiro **.cer** a partir da AC emissora ou de qualquer dispositivo que confie na AC emissora e atribui-o a dispositivos com o perfil de certificado da AC Fidedigna.<br /><br />Utiliza apenas um certificado da AC de Raiz Fidedigna por cada plataforma de sistema operativo e associa-o a cada perfil de Certificado de Raiz Fidedigna que criar.<br /><br />Pode utilizar certificados da AC de Raiz Fidedigna adicionais quando necessário. Por exemplo, pode fazê-lo para conceder um estatuto de fidedignidade a uma AC que assina os certificados de autenticação do servidor para os seus pontos de acesso Wi-Fi.|


## <a name="configure-your-infrastructure"></a>Configurar a sua infraestrutura
Para poder configurar perfis de certificados, tem de concluir os passos seguintes. Estes passos exigem o conhecimento do Windows Server 2012 R2 e dos Serviços de Certificados do Active Directory (ADCS):

- **Passo 1** – Configurar modelos de certificado na autoridade de certificação.
- **Passo 2**– Ativar, instalar e configurar o Intune Certificate Connector.

## <a name="step-1---configure-certificate-templates-on-the-certification-authority"></a>Passo 1 – Configurar modelos de certificado na autoridade de certificação

### <a name="to-configure-the-certification-authority"></a>Para configurar a autoridade de certificação

1.  Na AC emissora, utilize o snap-in Modelos de Certificado para criar um novo modelo personalizado ou copie e edite um modelo existente (como o Modelo de Utilizador) para utilizar com o PKCS.

    O modelo deve incluir o seguinte:

    -   Especifique um **Nome a apresentar do modelo** amigável.

    -   No separador **Nome do Requerente**, selecione **Fornecer no pedido**. (A segurança é imposta pelo módulo de política do Intune para o NDES).

    -   No separador **Extensões** certifique-se de que a **Descrição das Políticas de Aplicações** inclui a **Autenticação do Cliente**.

        > [!IMPORTANT]
        > Para os modelos de certificado iOS e macOS, no separador **Extensões**, edite **Utilização de Chave** e confirme que a opção **A assinatura é uma prova de origem** não está selecionada.

2.  Reveja o separador **Período de validade** no separador **Geral** do modelo. Por predefinição, o Intune utiliza o valor configurado no modelo. Contudo, tem a opção de configurar a AC para permitir que o autor do pedido especifique um valor diferente que pode, posteriormente, configurar a partir da Consola de administração do Intune. Se pretender utilizar sempre o valor no modelo, ignore o resto deste passo.

    > [!IMPORTANT]
    > O iOS e o macOS utilizam sempre o conjunto de valores no modelo, independentemente de outras configurações que realizar.

    Para configurar a AC de modo a que permita ao autor do pedido especificar o período de validade, execute os seguintes comandos na AC:

    a.  **certutil -setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE**

    b.  **net stop certsvc**

    c.  **net start certsvc**

3.  Na AC emissora, utilize o snap-in Autoridade de Certificação para publicar o modelo de certificado.

    a.  Selecione o nó **Modelos de Certificados**, clique em **Ação**-&gt; **Novo** &gt; **Modelo de certificado a emitir** e, em seguida, selecione o modelo que criou no passo 2.

    b.  Valide o modelo publicado ao visualizá-lo na pasta **Modelos de Certificado**.

4.  No computador da AC, confirme que o computador que aloja o Intune Certificate Connector tem permissão de inscrição, para que possa aceder ao modelo que foi utilizado na criação do perfil de certificado PKCS. Defina essa permissão no separador **Segurança** das propriedades do computador da AC.

## <a name="step-2---enable-install-and-configure-the-intune-certificate-connector"></a>Passo 2 – Ativar, instalar e configurar o Intune Certificate Connector
Neste passo, irá:

- Ativar o suporte do Certificate Connector
- Transferir, instalar e configurar o Certificate Connector.

### <a name="to-enable-support-for-the-certificate-connector"></a>Para ativar o suporte do Certificate Connector

1.  Inicie sessão no portal do Azure.
2.  Escolha **Mais Serviços** > **Monitorização + Gestão** > **Intune**.
3.  No painel **Intune**, escolha **Configurar dispositivos**.
2.  No painel **Configuração do Dispositivo**, escolha **Configurar** > **Autoridade de Certificação**.
2.  No **Passo 1**, escolha **Ativar**.

### <a name="to-download-install-and-configure-the-certificate-connector"></a>Para transferir, instalar e configurar o Certificate Connector

1.  No painel **Configurar dispositivos**, escolha **Configurar** > **Autoridade de Certificação**.
2.  escolha **Transferir o Certificate Connector**.
2.  Após a conclusão da transferência, execute o instalador transferido (**ndesconnectorssetup.exe**).
  Execute o instalador no computador com capacidade para ligar à Autoridade de Certificação. Escolha a opção Distribuição PKCS (PFX) e, em seguida, **Instalar**. Após a conclusão da instalação, continue ao criar um perfil de certificado, conforme descrito em [Como configurar perfis de certificado](certificates-configure.md).

3.  Quando lhe for pedido o certificado de cliente do Certificate Connector, escolha **Selecionar** e selecione o certificado de **autenticação de cliente** que instalou.

    Após selecionar o certificado de autenticação de cliente, é encaminhado para a superfície do **Certificado de Cliente do Microsoft Intune Certificate Connector** . Embora o certificado que selecionou não seja mostrado, escolha **Seguinte** para ver as propriedades do certificado. Em seguida, escolha **Seguinte**, e, em seguida, **Instalar**.

4.  Após o assistente ser concluído, mas antes de o fechar, clique em **Iniciar a IU do Certificate Connector**.

    > [!TIP]
    > Se fechar o assistente antes de iniciar a IU do Certificate Connector, pode abri-lo novamente ao executar o seguinte comando:
    >
    > **&lt;install_Path&gt;\NDESConnectorUI\NDESConnectorUI.exe**

5.  Na IU do **Certificate Connector** :

    a. Escolha **Iniciar Sessão** e introduza as suas credenciais de administrador do serviço Intune ou as credenciais de administrador inquilino com permissão de administração global.

  <!--  If your organization uses a proxy server and the proxy is needed for the NDES server to access the Internet, click **Use proxy server** and then provide the proxy server name, port, and account credentials to connect.-->

    b. Selecione o separador **Avançadas** e, em seguida, forneça credenciais para uma conta que tenha permissão para **Emitir e Gerir Certificados** na sua Autoridade de Certificados emissora.

    c. Escolha **Aplicar**.

    Agora, pode fechar a IU do Certificate Connector.

6.  Abra uma linha de comandos e escreva **services.msc**. Em seguida, prima **Enter**, clique com o botão direito do rato no **Serviço Connector do Intune** e escolha **Reiniciar**.

Para se certificar de que o serviço está em execução, abra um browser e introduza o seguinte URL que deverá devolver um erro **403** :

**http:// &lt;FQDN_of_your_NDES_server&gt;/certsrv/mscep/mscep.dll**


### <a name="how-to-create-a-pkcs-certificate-profile"></a>Como criar um perfil de certificado PKCS

No Portal do Azure, selecione a carga de trabalho **Configurar dispositivos**.
2. No painel **Configuração do dispositivo**, escolha **Gerir** > **Perfis**.
3. No painel de perfis, clique em **Criar Perfil**.
4. No painel **Criar Perfil**, introduza um **Nome** e uma **Descrição** para o perfil de certificado PKCS.
5. Na lista pendente **Plataforma**, selecione a plataforma do dispositivo para este certificado PKCS em:
    - **Android**
    - **Android for Work**
    - **iOS**
    - **Windows 10 e posterior**
6. Na lista pendente **Tipo de perfil**, escolha **Certificado PKCS**.
7. No painel **Certificado PKCS**, configure as seguintes definições:
    - **Limiar de renovação (%)** – Especifique a percentagem da duração do certificado antes de o dispositivo pedir a renovação do certificado.
    - **Período de validade do certificado** – Se tiver executado o comando **certutil - setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE** na AC emissora, que permite um período de validade personalizado, poderá especificar o tempo restante até o certificado expirar.<br>Pode especificar um valor inferior ao período de validade do modelo de certificado especificado, mas não superior. Por exemplo, se o período de validade do certificado no modelo de certificado for dois anos, pode especificar um valor de um ano, mas não um valor de cinco anos. O valor deve também ser inferior ao período de validade restante do certificado da AC emissora.
    - **Fornecedor de armazenamento de chaves (KSP)** (Windows 10) – especifique onde será armazenada a chave do certificado. Escolha um dos seguintes valores:
        - **Inscrever em KSP de Trusted Platform Module (TPM) se estiver presente, caso contrário, KSP de Software**
        - **Inscrever em KSP de Trusted Platform Module (TPM), caso contrário, ocorre uma falha**
        - **Inscrever em Passport, caso contrário, ocorre uma falha (Windows 10 e posterior)**
        - **Inscrever em KSP de Software**
    - **Autoridade de certificação** – uma Autoridade de Certificação (AC) Empresarial que é executada numa edição Enterprise do Windows Server 2008 R2 ou posterior. Não é suportada uma AC Autónoma. Para obter instruções sobre como configurar uma Autoridade de Certificação, consulte [Instalar a Autoridade de Certificação](http://technet.microsoft.com/library/jj125375.aspx). Se a sua AC for executada no Windows Server 2008 R2, tem de [instalar a correção de KB2483564](http://support.microsoft.com/kb/2483564/).
    - **Nome da autoridade de certificação** – introduza o nome da autoridade de certificação.
    - **Nome do modelo de certificado** – Introduza o nome de um modelo de certificado que o Serviço de Inscrição de Dispositivos de Rede esteja configurado para utilizar e que tenha sido adicionado a uma AC emissora.
    Confirme que o nome corresponde exatamente a um dos modelos de certificado listados no registo do servidor com o Serviço de Inscrição de Dispositivos de Rede em execução. Certifique-se de que especifica o nome do modelo de certificado e não o nome a apresentar do modelo de certificado. 
    Para localizar os nomes dos modelos de certificado, navegue para a seguinte chave: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Cryptography\MSCEP. Verá os modelos de certificado listados como valores para **EncryptionTemplate**, **GeneralPurposeTemplate**e **SignatureTemplate**. Por predefinição, o valor dos três modelos de certificado é IPSECIntermediateOffline, que é mapeado para o nome a apresentar de modelo **IPSec (Pedido offline)**. 
    - **Formato do nome do requerente** – Na lista, selecione de que forma o Intune cria automaticamente o nome do requerente no pedido de certificado. Se o certificado se destinar a um utilizador, pode também incluir o endereço de e-mail do utilizador no nome do requerente. Escolha entre:
        - **Não configurado**
        - **Nome comum**
        - **Nome comum, incluindo o e-mail**
        - **Nome comum como e-mail**
    - **Nome alternativo do requerente** – Especifique o modo como o Intune cria automaticamente os valores para o nome alternativo do requerente (SAN) no pedido de certificado. Por exemplo, se tiver selecionado um tipo de certificado de utilizador, pode incluir o nome principal de utilizador (UPN) no nome alternativo do requerente. Se o certificado de cliente for utilizado para autenticar um Servidor de Políticas de Rede, defina o nome alternativo do requerente com o UPN. 
    Também pode selecionar **atributo Personalizado do Azure AD**. Quando seleciona esta opção, é apresentado outro campo pendente. No campo pendente **atributo Personalizado do Azure AD**, existe uma opção: **Departamento**. Quando seleciona esta opção, se o departamento não estiver identificado no Azure AD, o certificado não é emitido. Para resolver este problema, identifique o departamento e guarde as alterações. Na próxima entrada do dispositivo, o problema é resolvido e o certificado é emitido. ASN.1 é a notação utilizada para este campo. 
    - **Utilização da chave expandida** (Android) – Escolha **Adicionar** para adicionar valores ao objetivo do certificado. Na maioria dos casos, o certificado irá exigir a **Autenticação de Cliente** para o utilizador ou dispositivo poder ser autenticado num servidor. Contudo, pode adicionar mais utilizações de chave conforme necessário. 
    - **Certificado de Raiz** (Android) – Escolha um perfil de certificado da AC de raiz que tenha configurado anteriormente e atribuído ao utilizador ou dispositivo. Este certificado da AC tem de ser o certificado de raiz da AC que irá emitir o certificado que está a configurar neste perfil de certificado. Este é o perfil de certificado fidedigno criado anteriormente.
8. Quando tiver terminado, volte ao painel **Criar Perfil** e clique em **Criar**.

O perfil é criado e apresentado no painel da lista de perfis.

## <a name="how-to-assign-the-certificate-profile"></a>Como atribuir o perfil de certificado

Antes de atribuir perfis de certificado a grupos, considere o seguinte:

- Ao atribuir perfis de certificado a grupos, o ficheiro de certificado do perfil de certificado da AC fidedigna é instalado no dispositivo. O dispositivo utiliza o perfil de certificado PKCS para criar um pedido de certificado por parte do dispositivo.
- Os perfis de certificado são instalados apenas em dispositivos que executam a plataforma que utiliza quando criou o perfil.
- Pode atribuir perfis de certificado a coleções de utilizadores ou de dispositivos.
- Para publicar um certificado num dispositivo rapidamente após a inscrição do mesmo, atribua o perfil de certificado a um grupo de utilizadores, em vez de atribuir a um grupo de dispositivos. Se atribuir a um grupo de dispositivos, será preciso um registo do dispositivo completo antes de o dispositivo receber políticas.
- Apesar de atribuir cada perfil separadamente, também terá de atribuir a AC de Raiz Confiável e o perfil PKCS. Caso contrário, a política de certificados PKCS falhará.

Para obter informações sobre como atribuir perfis, veja [Como atribuir perfis de dispositivo](device-profile-assign.md).
