---
title: Utilize certificados de chaves privadas e públicas no Microsoft Intune - Azure Microsoft Docs
description: Utilize os certificados de criptografia de chaves públicas (PKCS) com o Microsoft Intune, trabalhe com certificados de raiz e modelos de certificado, instale o Conector de CertificadoIno (NDES) e utilize perfis de configuração do dispositivo para um Certificado PKCS.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/20/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: b963a508ac140988993d3953d6a9d6398404e7b6
ms.sourcegitcommit: 67f926ba83f8a955e16b741a610ad84d6044f8f9
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/21/2020
ms.locfileid: "77529299"
---
# <a name="configure-and-use-pkcs-certificates-with-intune"></a>Configurar e utilizar certificados PKCS com o Intune

Intune apoia a utilização de certificados de par de chaves privadas e públicas (PKCS). Este artigo pode ajudá-lo a configurar a infraestrutura necessária, como conectores de certificados no local, exportar um certificado PKCS e, em seguida, adicionar o certificado a um perfil de configuração do dispositivo Intune.

O Microsoft Intune inclui configurações incorporadas para utilizar certificados PKCS para acesso e autenticação aos recursos das suas organizações. Os certificados autenticam e garantem o acesso aos seus recursos corporativos, como uma VPN ou uma rede Wi-Fi. Implementa estas definições para dispositivos utilizando perfis de configuração do dispositivo em Intune.

Para obter informações sobre a utilização de certificados PKCS importados, consulte [certificados PFX importados](certificates-imported-pfx-configure.md).


## <a name="requirements"></a>Requisitos

Para utilizar certificados PKCS com Intune, necessitará da seguinte infraestrutura:

- **Domínio do Diretório Ativo:**  
  Todos os servidores listados nesta secção devem ser unidos ao seu domínio de Diretório Ativo.

  Para obter mais informações sobre a instalação e configuração de Serviços de Domínio de Diretório Ativo (AD DS), consulte [design e planeamento aD DS](https://docs.microsoft.com/windows-server/identity/ad-ds/plan/ad-ds-design-and-planning).

- **Autoridade de Certificação:**  
   Uma Autoridade de Certificação Empresarial (CA).

  Para obter informações sobre a instalação e configuração dos Serviços de Certificados de Diretório Ativo (AD CS), consulte o [Ative Directory Certificate Services Step-by-Step Guide](https://technet.microsoft.com/library/cc772393).

  > [!WARNING]  
  > O Intune requer a execução do AD CS com uma Autoridade de Certificação (AC) Empresarial e não uma AC Autónoma.

- **Um cliente:**  
  Para ligar à Enterprise CA.

- **Certificado de raiz:**  
  Uma cópia exportada do certificado de raiz da AC Empresarial.

- **Conector** de certificado intune da Microsoft (também chamado *conector de certificado NDES):*  
  No portal Intune, vá à **configuração** do dispositivo > **Conectores** de Certificado > **Adicionar**, e siga os *Passos para instalar o conector para #12 PKCS*. Utilize o link de descarregamento no portal para iniciar o download do instalador de conector de certificado **NDESConnectorSetup.exe**.  

  Intune suporta até 100 instâncias deste conector por inquilino. Cada instância do conector deve estar num servidor Windows separado. Pode instalar uma instância deste conector no mesmo servidor que uma instância do Conector de Certificado PFX para o Microsoft Intune. Quando utiliza vários conectores, a infraestrutura do conector suporta alta disponibilidade e equilíbrio de carga, uma vez que qualquer instância de conector disponível pode processar os pedidos do certificado PKCS. 

  Este conector processa pedidos de certificado PKCS utilizados para autenticação ou assinatura de e-mail S/MIME.

  O Conector de Certificado Intune da Microsoft também suporta o modo Federal de Processamento de Informações (FIPS). O FIPS não é obrigatório, mas pode emitir e revogar certificados quando está ativado.

- **Conector de certificado PFX para Microsoft Intune**:  
  Se planeia utilizar encriptação de e-mail S/MIME, utilize o portal Intune para descarregar o *Conector* de Certificado PFX que suporta a importação de certificados PFX.  Vá à **configuração** do dispositivo > **Conectores** de certificados > **Adicionar,** e siga os *Passos para instalar o conector para certificados PFX importados*. Utilize o link de descarregamento no portal para iniciar o download do instalador **PfxCertificateConnectorBootstrapper.exe**.

  Cada inquilino intune suporta uma única instância deste conector. Pode instalar este conector no mesmo servidor que uma instância do conector Microsoft Intune Certificate.

  Este conector trata dos pedidos de ficheiros PFX importados para Intune para encriptação de e-mail S/MIME para um utilizador específico.  

  Este conector pode atualizar-se automaticamente quando novas versões estiverem disponíveis. Para utilizar a capacidade de atualização, deve:
  - Instale o Conector de Certificado PFX para microsoft Intune no seu servidor.  
  - Para receber automaticamente atualizações importantes, certifique-se de que as firewalls estão abertas que permitem ao conector contactar **autoupdate.msappproxy.net** na porta **443**.   

  Para mais informações, consulte [os pontos finais da Rede para o Microsoft Intune](../fundamentals/intune-endpoints.md)e os requisitos de configuração da [rede Intune e largura de banda](../fundamentals/network-bandwidth-use.md).

- **Servidor do Windows:**  
  Utilize um Servidor windows para hospedar:

  - Conector de certificado intune da Microsoft - para autenticação e cenários de assinatura de e-mail S/MIME
  - Conector de certificado PFX para Microsoft Intune - para cenários de encriptação de e-mail S/MIME.

  Os conectores requerem acesso às mesmas portas que detalhadopara dispositivos geridos, como se encontra no [conteúdo do ponto final](https://docs.microsoft.com/intune/fundamentals/intune-endpoints#access-for-managed-devices)do nosso dispositivo .

  A Intune suporta a instalação do *Conector de CertificadoPFX* no mesmo servidor que o *Conector*de Certificado Intune da Microsoft .
  
## <a name="export-the-root-certificate-from-the-enterprise-ca"></a>Exportar o certificado de raiz da AC Empresarial

Para autenticar um dispositivo com VPN, WiFi ou outros recursos, um dispositivo necessita de um certificado CA raiz ou intermédio. Os passos seguintes explicam como obter o certificado necessário a partir da AC Empresarial.

**Utilize uma linha de comando:**  
1. Inicie sessão no servidor da Autoridade de Certificação de Raiz com Conta administradora.
 
2. Vá **iniciar** > **Executar**e, em seguida, entre **cmd** para abrir o pedido de comando. 
    
3. Especifique **certutil -ca.cert ca_name.cer** para exportar o certificado Raiz como um ficheiro chamado *ca_name.cer*.



## <a name="configure-certificate-templates-on-the-ca"></a>Configurar modelos de certificado no CA

1. Inicie sessão na AC Empresarial com uma conta que tenha privilégios administrativos.
2. Abra a consola **Autoridade de Certificação**, clique com o botão direito do rato em **Modelos de Certificado** e selecione **Gerir**.
3. Encontre o modelo de modelo de modelo **do utilizador,** clique-o à direita e escolha o **Modelo Duplicado** para abrir **propriedades de novo modelo**.

    > [!NOTE]
    > Para cenários de encriptação e assinaturas de e-mail com S/MIME, muitos administradores utilizam certificados separados para assinar e encriptar. Se estiver a utilizar os Serviços de Certificados do Microsoft Active Directory, pode utilizar o modelo **Apenas Assinatura do Exchange** para certificados de assinaturas de e-mail S/MIME e o modelo **Utilizador do Exchange** para certificados de encriptação S/MIME.  Se estiver a usar uma autoridade de certificação de terceiros, sugere-se que reveja as suas orientações para configurar modelos de assinatura e encriptação.

4. No separador **Compatibilidade**:

    - Defina **Autoridade de Certificação** como **Windows Server 2008 R2**
    - Defina **Destinatário do certificado** como **Windows 7/Server 2008 R2**

5. No separador **Geral**, defina o **Nome a apresentar do modelo** para algo que seja relevante para si.

    > [!WARNING]
    > Por predefinição, o **Nome do modelo** é igual ao **Nome a apresentar do modelo***sem espaços*. Anote o nome do modelo, irá precisar dele mais tarde.

6. Em **Processamento de Pedidos**, selecione **Permitir que a chave privada seja exportada**.
7. Em **Criptografia**, confirme se o **Tamanho mínimo da chave** está definido como 2048.
8. Em **Nome do Requerente**, selecione **Fornecer no pedido**.
9. Em **Extensões**, confirme se vê o Sistema de Encriptação de Ficheiros, Proteger o E-mail e Autenticação de Cliente em **Políticas de Aplicações**.

    > [!IMPORTANT]
    > Para os modelos de certificados iOS/iPadOS, vá ao separador **Extensões,** atualize o **Uso da Chave,** e confirme que a **Assinatura é prova de origem.**

10. Em **Segurança**, adicione a Conta de Computador do servidor no local onde irá instalar o Microsoft Intune Certificate Connector. Conceda a esta conta as permissões **Ler** e **Inscrever**.
11. Selecione **Aplicar** > **OK** para guardar o modelo de certificado. Feche a **Consola de Modelos de Certificado**.
12. Na consola **Autoridade de Certificação**, clique com o botão direito do rato em **Modelos de Certificado** > **Novo** > **Modelo de Certificado a Emitir**. Selecione o modelo criado nos passos anteriores. Selecione **OK**.
13. Para que o servidor gere os certificados para dispositivos e utilizadores matriculados, utilize os seguintes passos:

    1. Clique com o botão direito do rato na Autoridade de Certificação e escolha **Propriedades**.
    2. No separador Segurança, adicione a conta do Computador do servidor onde executa os conectores (**Microsoft Intune Certificate Connector** ou **PFX Certificate Connector for Microsoft Intune**). 
    3. Conceda as permissões **Emitir e Gerir Certificados** e **Pedir Certificados** à conta de computador.

14. Termine a sessão na AC Empresarial.

## <a name="download-install-and-configure-the-microsoft-intune-certificate-connector"></a>Descarregue, instale e configure o Conector de Certificado Intune da Microsoft

> [!IMPORTANT]  
> O Conector de Certificado Intune da Microsoft não pode ser instalado na Autoridade de Certificados de Emissão (CA), e deve ser instalado num servidor Windows separado.  

1. Inscreva-se no [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Selecione **a administração do Inquilino** > **Conectores e fichas** > **Conectores** de Certificado >  **+ Adicionar**.

3. Clique em *Baixar o software de conector* do certificado para o conector para pKCS #12 e guarde o ficheiro para um local a que possa aceder a partir do servidor onde vai instalar o conector.

   ![Microsoft Intune Certificate Connector download](./media/certficates-pfx-configure/download-ndes-connector.png)
 
4. Após a transferência ser concluída, inicie sessão no servidor. Em seguida:

    1. Certifique-se de que o .NET 4.5 Framework ou superior está instalado, pois é necessário para o Certificate Connector do NDES. O .NET 4.5 Framework vem incluído automaticamente com o Windows Server 2012 R2 e versões mais recentes.
    2. Execute o instalador (NDESConnectorSetup.exe) e aceite a localização predefinida. O conector é instalado em `\Program Files\Microsoft Intune\NDESConnectorUI`. Nas Opções do Instalador, selecione **PFX Distribution** (Distribuição PFX). Continue para concluir a instalação.
    3. Por predefinição, o serviço do conector é executado na conta do sistema local. Se for necessário um proxy para aceder à Internet, confirme que a conta do serviço local consegue aceder às definições de proxy no servidor.

5. O Conector de Certificado Intune da Microsoft abre o separador **De Inscrição.** Para permitir a ligação ao Intune, **Sign In**, e insira uma conta com permissões administrativas globais.
6. No separador **Avançadas**, recomendamos que deixe a opção **Utilizar a conta SYSTEM deste computador (predefinição)** selecionada.
7. **Aplicar** > **Fechar**
8. Volte ao portal Intune (**Intune** > Configuração de **dispositivos** > **Conectores de Certificação).** Após alguns momentos, é mostrada uma marca de verificação verde e o estado de **Ligação** está **Ativo**. Agora o servidor do conector pode comunicar com o Intune.
9. Se tiver um proxy web no seu ambiente de rede, poderá necessitar de configurações adicionais para permitir que o conector funcione. Para mais informações, consulte [O Trabalho com os servidores proxy existentes no local](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy-configure-connectors-with-proxy-servers) na documentação do Diretório Ativo Azure.
<ul><li>Android Enterprise *(Perfil de Trabalho)*</li><li>iOS</li><li>macOS</li><li>O Windows 10 e, posteriormente, > O Conector de Certificado Intune da Microsoft suporta o TLS 1.2. Se o TLS 1.2 estiver instalado no servidor que acolhe o Conector, o conector utiliza TLS 1.2. Caso contrário, é utilizado TLS 1.1. Atualmente, é utilizado o TLS 1.1 para a autenticação entre os dispositivos e o servidor.

## <a name="create-a-trusted-certificate-profile"></a>Criar um perfil de certificado fidedigno

1. Inscreva-se no [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Selecione **Dispositivos** > Perfis de **Configuração** > **Criar perfil**.

   ![Navegue para Intune e crie um novo perfil para um certificado de confiança](./media/certficates-pfx-configure/certificates-pfx-configure-profile-new.png)

3. Introduza as seguintes propriedades:

    - O **Nome** do perfil
    - Opcionalmente, defina uma descrição
    - A **Plataforma** na qual vai implementar o perfil
    - Defina o **Tipo de perfil** como **Certificado fidedigno**

4. Selecione **Definições**e especifique o Certificado Raiz CA do ficheiro .cer que exportou anteriormente.

   > [!NOTE]
   > Dependendo da plataforma escolhida no **Passo 2,** pode ou não ter a opção de escolher a **loja Destino** para o certificado.

   ![Criar um perfil e carregar um certificado fidedigno](./media/certficates-pfx-configure/certificates-pfx-configure-profile-fill.png)

5. Selecione **OK** > **Criar** para guardar o perfil.

6. Para atribuir o novo perfil a um ou mais dispositivos, veja [Atribuir perfis de dispositivo no Microsoft Intune](../configuration/device-profile-assign.md).

## <a name="create-a-pkcs-certificate-profile"></a>Criar um perfil de certificado PKCS

1. Inscreva-se no [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Selecione e vá aos perfis de **configuração** de **dispositivos** >  > **Criar perfil**.

3. Introduza as seguintes propriedades:

    - O **Nome** do perfil
    - Opcionalmente, defina uma descrição
    - A **Plataforma** na qual vai implementar o perfil
    - Defina o **Tipo de perfil** como **Certificado PKCS**

4. Selecione **Definições**e configure as propriedades que se aplicam à plataforma selecionada:
   
   |Definição     | Platform     | Detalhes   |
   |------------|------------|------------|
   |**Limiar de renovação (%)**        |<ul><li>Todas         |Recomendado é 20%  | 
   |**Período de validade do certificado**  |<ul><li>Todas         |Se não alterar o modelo de certificado, esta opção pode ser definida para um ano. |
   |**Fornecedor de armazenamento chave (KSP)**   |<ul><li>Windows 10  | Para windows, selecione onde guardar as chaves do dispositivo. |
   |**Autoridade de certificação**      |<ul><li>Todas         |Exibe o nome de domínio interno totalmente qualificado (FQDN) da sua Enterprise CA.  |
   |**Nome da autoridade de certificação** |<ul><li>Todas         |Lista o nome da sua Enterprise CA, como "Autoridade de Certificação Contoso". |
   |**Tipo de certificado**             |<ul><li>Android Enterprise *(Perfil de Trabalho)*</li><li>iOS</li><li>macOS</li><li>Windows 10 e posterior|Selecione um tipo: <ul><li> **Os** certificados de utilizador podem conter atributos de utilizador e dispositivo no assunto e san do certificado. </il><li>**Os** certificados do dispositivo só podem conter atributos de dispositivo no sujeito e san do certificado. Utilize o Dispositivo para cenários como dispositivos sem uso, como quiosques ou outros dispositivos partilhados.  <br><br> Esta seleção afeta o formato de nome do Assunto. |
   |**Formato de nome de assunto**          |<ul><li>Todas         |Para a maioria das plataformas, detete esta opção para **o nome comum,** salvo necessidade em contrário.<br><br>Para as seguintes plataformas, o formato de nome sujeito é determinado pelo tipo de certificado: <ul><li>Android Enterprise *(Perfil de Trabalho)*</li><li>iOS</li><li>macOS</li><li>Windows 10 e posterior</li></ul>  <p> Consulte o [formato de nome do Assunto](#subject-name-format) mais tarde neste artigo. |
   |**Nome alternativo do sujeito**     |<ul><li>Todas         |Detete esta opção para **o nome principal do Utilizador (UPN)** salvo necessidade em contrário. |
   |**Utilização alargada da chave**           |<ul><li> Administrador de dispositivos Android </li><li>Android Enterprise (*Proprietário de Dispositivos,* *Perfil de Trabalho)* </li><li>Windows 10 |Os certificados geralmente requerem *autenticação do cliente* para que o utilizador ou dispositivo possa autenticar um servidor. |
   |**Permitir que todas as aplicações tenham acesso à chave privada** |<ul><li>macOS  |Configurar para **permitir** dar aplicações configuradas para o acesso do dispositivo mac associado à chave privada dos certificados PKCS. <br><br> Para obter mais informações sobre esta definição, consulte *AllowAllAppsAccess* the Certificate Payload section of [Configuration Profile Reference](https://developer.apple.com/business/documentation/Configuration-Profile-Reference.pdf) in the Apple developer documentation. |
   |**Certificado raiz**             |<ul><li>Administrador de dispositivos Android </li><li>Android Enterprise (*Proprietário de Dispositivos,* *Perfil de Trabalho)* |Selecione um perfil de certificado CA raiz que tenha sido previamente atribuído. |

5. Selecione **OK** > **Criar** para guardar o perfil.

6. Para atribuir o novo perfil a um ou mais dispositivos, veja [Atribuir perfis de dispositivo no Microsoft Intune](../configuration/device-profile-assign.md).

   > [!NOTE]
   > Em dispositivos com perfil Android Enterprise, os certificados instalados com um perfil de certificado PKCS não são visíveis no dispositivo. Para confirmar a implementação bem sucedida do certificado, verifique o estado do perfil na consola Intune.

### <a name="subject-name-format"></a>Formato do nome do requerente

Quando cria um perfil de certificado PKCS para as seguintes plataformas, as opções para o formato de nome de assunto dependem do tipo de Certificado que selecionar, seja **utilizador** ou **dispositivo**.  

Plataformas:

- Android Enterprise *(Perfil de Trabalho)*
- iOS
- macOS
- Windows 10 e posterior

> [!NOTE]
> Existe uma questão conhecida para a utilização do PKCS para obter certificados [que é a mesma questão que se vê para](certificates-profile-scep.md#avoid-certificate-signing-requests-with-escaped-special-characters) o SCEP quando o nome do assunto no pedido de assinatura de certificado (CSR) resultante inclui um dos seguintes caracteres como um personagem escapado (prosseguido por um \\de backslash ):
> - \+
> - ;
> - ,
> - =

- **Tipo de certificado Utilizador**  
  As opções de formato para o *formato de nome sujeito* incluem duas variáveis: Nome **Comum (CN)** e **E-mail (E)** . O **Nome Comum (CN)** pode ser definido para qualquer uma das seguintes variáveis:

  - **CN={{{UserName}}** : O nome principal do utilizador, tal como janedoe@contoso.com.
  - **CN={{AAD_Device_ID}}** : um ID atribuído ao registar um dispositivo no Azure Active Directory (AD). Este ID é normalmente utilizado na autenticação com o Azure AD.
  - **CN={{{SERIALNUMBER}}** : O número de série único (SN) normalmente utilizado pelo fabricante para identificar um dispositivo.
  - **CN={{{IMEINumber}}** : O número único de identidade de equipamento móvel internacional (IMEI) utilizado para identificar um telemóvel.
  - **CN={{{OnPrem_Distinguished_Name}}** : Uma sequência de nomes relativos distintos separados por vírem, tais como *CN=Jane Doe,OU=UserAccounts,DC=corp,DC=contoso,DC=com*.

    Para utilizar a variável *{{OnPrem_Distinguished_Name}}* certifique-se de sincronizar o atributo do utilizador de nome no *local* utilizando o [Azure AD Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) para o seu AD Azure.

  - **CN={{noPremisesSamAccountName}}** : Os administradores podem sincronizar o atributo samAccountName do Diretório Ativo para a AD Azure utilizando a ligação Azure AD a um atributo chamado *noPremisesSamAccountName*. Intune pode substituir essa variável como parte de um pedido de emissão de certificado em matéria de certificado. O atributo samAccountName é o nome de entrada do utilizador utilizado para suportar clientes e servidores a partir de uma versão anterior do Windows (pré-Windows 2000). O formato de sinal do utilizador no formato de nome é: *DomainName\testUser*, ou apenas *testUser*.

    Para utilizar a variável *{{onPremisesSamAccountName}}* certifique-se de sincronizar o atributo do utilizador *no LocalsSamAccountName* utilizando o [Azure AD Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) para o seu Azure AD.

  Através de uma combinação de uma ou várias destas variáveis e cadeias estáticas, pode criar um formato de nome de requerente personalizado, como o seguinte:  
  - **CN={{UserName}},E={{EmailAddress}},OU=Mobile,O=Finance Group,L=Redmond,ST=Washington,C=US**
  
  Este exemplo inclui um formato de nome de assunto que utiliza as variáveis CN e E, e cordas para valores da Unidade Organizacional, Organização, Localização, Estado e País. O artigo [função CertStrToName](https://msdn.microsoft.com/library/windows/desktop/aa377160.aspx) descreve esta função e as cadeias suportadas da mesma.

- **Tipo de certificado Dispositivo**  
  As opções de formato para o formato de nome sujeito incluem as seguintes variáveis: 
  - **{{AAD_Device_ID}}**
  - **{{Device_Serial}}**
  - **{{Device_IMEI}}**
  - **{{Número de Série}}**
  - **{{IMEINumber}}**
  - **{{AzureADDeviceId}}**
  - **{{WiFiMacAddress}}**
  - **{{IMEI}}**
  - **{{DeviceName}}**
  - **{{FullQualifiedDomainName}}** *(Apenas aplicável para dispositivos windows e focados em domínios)*
  - **{{MEID}}**

  Pode especificar estas variáveis, seguidas pelo texto para a variável, na caixa de texto. Por exemplo, o nome comum para um dispositivo chamado *Device1* pode ser adicionado como **CN={{DeviceName}}Dispositivo1**.

  > [!IMPORTANT]  
  > - Quando especificar uma variável, encerre o nome variável em parênteses encaracolados { } como se pode ver no exemplo, para evitar um erro.  
  > - As propriedades do dispositivo utilizadas no *assunto* ou *SAN* de um certificado de dispositivo, como **IMEI,** **SerialNumber**, e **FullQualifiedDomainName,** são propriedades que podem ser falsificadas por uma pessoa com acesso ao dispositivo.
  > - Um dispositivo deve suportar todas as variáveis especificadas num perfil de certificado para que esse perfil seja instalado nesse dispositivo.  Por exemplo, se **{{IMEI}}** for utilizado no nome do assunto de um perfil SCEP e for atribuído a um dispositivo que não tenha um número IMEI, o perfil não é instalado.  
 


## <a name="whats-new-for-connectors"></a>Novidades para Conectores

As atualizações dos dois conectores de certificado são divulgadas periodicamente. Quando atualizarmos um conector, pode ler sobre as alterações aqui.

O *Conector de CertificadoPFX para microsoft Intune* [suporta atualizações automáticas,](#requirements)enquanto o *Conector de Certificado Intune* é atualizado manualmente.

### <a name="may-17-2019"></a>17 de maio de 2019

- **Conector de certificado PFX para Microsoft Intune - versão 6.1905.0.404**  
  Alterações nesta versão:  
  - Corrigiu um problema em que os certificados PFX existentes continuam a ser reprocessados, o que faz com que o conector deixe de processar novos pedidos. 

### <a name="may-6-2019"></a>6 de maio de 2019

- **Conector de certificado PFX para Microsoft Intune - versão 6.1905.0.402**  
  Alterações nesta versão:  
  - O intervalo de votação para o conector é reduzido de 5 minutos para 30 segundos.
 
### <a name="april-2-2019"></a>2 de abril de 2019

- **Conector de Certificado Intune - versão 6.1904.1.0**  
  Alterações nesta versão:  
  - Corrigiu um problema em que o conector pode não se inscrever na Intune depois de iniciar a sessão no conector com uma conta de administrador global.  
  - Inclui correções de fiabilidade à revogação do certificado.  
  - Inclui correções de desempenho para aumentar a rapidez com que os pedidos de certificados PKCS são processados.  

- **Conector de certificado PFX para Microsoft Intune - versão 6.1904.0.401**
  > [!NOTE]  
  > A atualização automática para esta versão do conector PFX só está disponível a 11 de abril de 2019.  

  Alterações nesta versão:  
  - Corrigiu um problema em que o conector pode não se inscrever na Intune depois de iniciar a sessão no conector com uma conta de administrador global.  


## <a name="next-steps"></a>Próximos passos

O perfil está criado, mas ainda não está ativo. Em seguida, [atribua o perfil](../configuration/device-profile-assign.md) e [monitorize o estado](../configuration/device-profile-monitor.md).

[Utilize o SCEP para certificados,](certificates-scep-configure.md)ou [emita certificados PKCS de um serviço web do gestor Symantec PKI.](certificates-digicert-configure.md)
