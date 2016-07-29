---
title: "Encapsular aplicações iOS com a Ferramenta de Encapsulamento de Aplicações | Microsoft Intune"
description: "Utilize as informações neste tópico para saber como pode encapsular as suas aplicações iOS sem modificar os próprios códigos. Prepare as aplicações para que possa aplicar políticas de gestão de aplicações móveis."
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 07/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 99ab0369-5115-4dc8-83ea-db7239b0de97
ms.reviewer: matgates
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 19a5b8f8260bace2bbe3626da3df281306f53024
ms.openlocfilehash: ebd68513da55b8bb1715d2c82636abf791cae1ff


---

# Preparar as aplicações iOS para gestão de aplicações móveis com a Ferramenta de Encapsulamento de Aplicações do Intune
Utilize a **Ferramenta de Encapsulamento de Aplicações do Microsoft Intune para iOS** para modificar o comportamento das aplicações iOS internas para restringir funcionalidades da aplicação sem alterar o código da aplicação em si.

A ferramenta consiste numa aplicação da linha de comandos do Mac OS que cria um "wrapper" em torno de uma aplicação. Assim que uma aplicação é processada, pode alterar as funcionalidades da mesma ao utilizar [políticas de gestão de aplicações móveis](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md) configuradas por si.

Para transferir a ferramenta, veja [Ferramenta de Encapsulamento de Aplicações do Microsoft Intune para iOS](http://www.microsoft.com/en-us/download/details.aspx?id=45218).

## Passo 1: cumprir os pré-requisitos de utilização da ferramenta de encapsulamento de aplicações

|Requisito|Mais informações|
|---------------|--------------------------------|
|Sistema operativo e conjunto de ferramentas suportados|Tem de executar a ferramenta de encapsulamento de aplicações num computador Mac que execute o OS X 10.8.5 ou posterior, que tem a versão 5 ou posterior do conjunto de ferramentas do Xcode instalada.|
|Certificado de assinatura e perfil de aprovisionamento|Precisa de ter um perfil de aprovisionamento e um certificado de assinatura da Apple. Veja a [documentação para programadores Apple](https://developer.apple.com/).|
|Processar uma aplicação com a Ferramenta de Encapsulamento de Aplicações|As aplicações têm de ser programadas e assinadas pela sua empresa ou por um fabricante independente de software (ISV). Não pode utilizar esta ferramenta para processar aplicações da Apple Store. As aplicações têm de ter sido escritas para o iOS 7.0 ou posterior. As aplicações têm de estar no formato PIE (Position Independent Executable). Para obter mais informações sobre o formato PIE, consulte a sua documentação de programador da Apple. Por fim, a aplicação tem de ter a extensão no formato **.app** ou **.ipa**.|
|Aplicações que a ferramenta de encapsulamento não pode processar|Aplicações encriptadas, aplicações não assinadas e aplicações com atributos de ficheiro expandidos.|
|Aplicações que utilizam a Biblioteca do Azure Active Directory (ADAL)|Se utilizar a ADAL, a aplicação tem de incorporar uma versão da ADAL superior ou igual a 1.0.2 e o programador tem de conceder o acesso à aplicação ao recurso Gestão de Aplicações Móveis do Intune.<br /><br />Consulte [Informações para aplicações que utilizam a Biblioteca do Azure Active Directory](prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md#information-for-apps-that-use-the-azure-active-directory-library) neste artigo para obter detalhes sobre como utilizar a ADAL.|
|Definir a elegibilidade para a sua aplicação|Tem de definir a elegibilidade, que fornece as capacidades e permissões adicionais de aplicações além das normalmente concedidas, antes de encapsular a aplicação. Consulte [Definição de elegibilidade da aplicação](#setting-app-entitlements) para obter instruções.|

## Passo 2: instalar a ferramenta de encapsulamento de aplicações

1.  Na página **Ferramenta de Encapsulamento de Aplicações do Microsoft Intune para iOS**, no [Centro de Transferências da Microsoft](https://www.microsoft.com/download/details.aspx?id=45218), transfira o ficheiro de instalação da ferramenta de encapsulamento de aplicações para um computador Mac.

2.  No computador Mac, faça duplo clique no ficheiro de instalação **Microsoft Intune App Wrapping Tool for iOS.dmg**.

3.  Escolha **Concordo** para aceitar o Contrato de Licença do Utilizador Final (EULA). O instalador é montado e apresentado no computador Mac.

4.  Abra o instalador e copie os ficheiros apresentados para uma nova pasta no computador Mac. Pode agora desligar a unidade do instalador montado.

    Já está pronto para executar a ferramenta de encapsulamento de aplicações.

## Passo 3: executar a ferramenta de encapsulamento de aplicações

1.  No computador Mac, abra uma janela de Terminal e navegue até à pasta onde guardou os ficheiros. Uma vez que os ficheiros executáveis estão dentro do pacote, terá de executar o comando da seguinte forma:
```
    ./IntuneMAMPackager/Contents/MacOS/IntuneMAMPackager –i /<path of input app>/<app filename> -o /<path to output folder>/<app filename> –p /<path to provisioning profile> –c <SHA1 hash of the certificate> -a <client ID of input app> -r <reply URI of input app> -v true
```
    > [!NOTE]
    > Some parameters are optional as shown in the table below.

    **Example:** The following example command runs the app wrapping tool on an app named **MyApp.ipa**. A provisioning profile and SHA-1 hash are specified. The processed app is created and stored in the **/users/myadmin/Documents** on the Mac computer.

    ```
    /users/myadmin/Downloads/IntuneMAMPackager.app/Contents/MacOS/IntuneMAMPackager -i /users/myadmin/Downloads/MyApp.ipa -o /users/myadmin/Documents/MyApp_Wrapped.ipa -p /users/myadmin/Downloads/My_Provisioning_Profile_.mobileprovision -c 12A3BC45D67EF8901A2B3CDEF4ABC5D6E7890FAB –a 20e1cd0d-268e-4308-9583-02ae97dd353e –r https://contoso/ -v true
    ```
    You can use the following command line properties with the app wrapping tool:

|Propriedade|Mais informações|
  |------------|--------------------|
  |**-h**|Apresenta as propriedades da linha de comandos disponíveis para a ferramenta de encapsulamento de aplicações.|
  |**-i**|Especifica o caminho e o nome do ficheiro da aplicação de entrada.|
  |**-o**|Especifica o caminho no qual guardou a aplicação processada.|
  |**-p**|Especifica o caminho para o seu perfil de aprovisionamento de aplicações iOS.|
  |**-c**|Especifica o hash SHA1 do certificado de assinatura.|
  |**-a**|ID de cliente da aplicação de entrada (no formato GUID) se a aplicação utilizar Bibliotecas do Azure Active Directory (Opcional).|
  |**-r**|Redireciona o URI da aplicação de entrada se a aplicação utilizar Bibliotecas do Azure Active Directory (Opcional).|
  |**-v**|Exporta mensagens em modo verboso para a consola (Opcional).|

2. Depois de o processamento ser concluído, será apresentada a mensagem **A aplicação foi encapsulada com êxito** .

    Se ocorrer um erro, consulte [Mensagens de erro](prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md#error-messages) para obter ajuda.

3.  A aplicação encapsulada é guardada no ficheiro de saída que especificou anteriormente. Agora pode carregar a aplicação para o [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] e associá-la a uma política de gestão de aplicações móveis.

    > [!IMPORTANT]
    > Tem de carregar a aplicação como uma nova aplicação. Não pode atualizar uma versão antiga e não encapsulada da aplicação.

    Pode implementar a aplicação nos grupos do [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] e a aplicação irá agora ser executada no dispositivo com as restrições da aplicação que especificou.

## Mensagens de erro e ficheiros de registo
Utilize as seguintes informações para resolver problemas com a ferramenta de encapsulamento de aplicações.

### Mensagens de erro
Se a ferramenta de encapsulamento de aplicações não conseguir concluir com êxito, poderá ser-lhe apresentada uma das seguintes mensagens de erro:

|Mensagem de erro|Mais informações|
|-----------------|--------------------|
|Tem de especificar um perfil de aprovisionamento do iOS válido.|O seu perfil de aprovisionamento poderá não ser válido. Certifique-se de que tem as permissões corretas para os dispositivos e de que o seu perfil está corretamente direcionado para a programação ou para a distribuição. Também é provável que o seu perfil de aprovisionamento tenha expirado.|
|Especifique um nome de aplicação de entrada válido.|Certifique-se de que o nome da aplicação de entrada que especificou está correto.|
|Especifique um caminho válido para a aplicação de saída.|Certifique-se de que o caminho da aplicação de saída que especificou existe e está correto.|
|Especifique um perfil de aprovisionamento de entrada válido.|Certifique-se de que forneceu um nome e extensão do perfil de aprovisionamento válidos. É provável que faltem elegibilidades no seu perfil de aprovisionamento ou que não tenha incluído a opção de linha de comandos **–p**.|
|Não foi possível localizar a aplicação de entrada que especificou. Especifique um caminho e nome de aplicação de entrada válidos.|Certifique-se de que o caminho da aplicação de entrada é válido e existe. Certifique-se de que a aplicação de entrada existe nessa localização.|
|Não foi possível localizar o ficheiro do perfil de aprovisionamento de entrada que especificou. Especifique um ficheiro do perfil de aprovisionamento de entrada válido.|Certifique-se de que o caminho para o ficheiro de aprovisionamento de entrada é válido e que o ficheiro que especificou existe.|
|Não foi possível localizar a pasta da aplicação de saída que especificou. Especifique um caminho válido para a aplicação de saída.|Certifique-se de que o caminho de saída que especificou é válido e existe.|
|A aplicação de saída não tem a extensão .ipa.|A ferramenta de encapsulamento de aplicações só aceita aplicações com as extensões **.app** e **.ipa** . Certifique-se de que o seu ficheiro de saída tem uma extensão válida.|
|Especificou um certificado de assinatura inválido. Especifique um certificado de assinatura da Apple válido.|Certifique-se de que transferiu o certificado de assinatura correto a partir do portal de programador da Apple. O seu certificado poderá ter expirado. Se o seu perfil de aprovisionamento e o certificado da Apple puderem ser utilizados para assinar corretamente uma aplicação no Xcode, significa que são válidos para a ferramenta de encapsulamento de aplicações.|
|A aplicação de entrada que especificou é inválida. Especifique uma aplicação válida.|Certifique-se de que tem uma aplicação iOS válida que tenha sido compilada como um ficheiro .app ou .ipa.|
|A aplicação de entrada que especificou está encriptada. Especifique uma aplicação não encriptada válida.|A ferramenta de encapsulamento de aplicações não suporta aplicações encriptadas. Especifique uma aplicação não encriptada.|
|A aplicação de entrada que especificou não está no formato PIE (Position Independent Executable). Especifique uma aplicação válida no formato PIE.|As aplicações PIE (Position Independent Executable) podem ser carregadas num endereço de memória aleatório quando são executadas, o que pode ser vantajoso a nível da segurança. Para obter mais informações, consulte a sua documentação de Programador da Apple.|
|A aplicação de entrada que especificou já foi encapsulada. Especifique uma aplicação não encapsulada válida.|Não pode processar uma aplicação que já tenha sido processada pela ferramenta. Se pretender processar novamente uma aplicação, execute a ferramenta com a versão original da aplicação.|
|A aplicação de entrada que especificou não está assinada. Especifique uma aplicação assinada válida.|A ferramenta de encapsulamento de aplicações requer que as aplicações sejam assinadas. Consulte a sua documentação de programador para saber como assinar uma aplicação encapsulada.|
|A aplicação de entrada que especificou tem de estar no formato .ipa ou .app.|A ferramenta de encapsulamento de aplicações só aceita as extensões .app e .ipa. Certifique-se de que o seu ficheiro de entrada tem uma extensão válida e de que foi compilado como ficheiro .app ou .ipa.|
|A aplicação de entrada que especificou já foi encapsulada e encontra-se na versão mais recente do modelo de política.|A ferramenta de encapsulamento de aplicações não irá encapsular novamente uma aplicação encapsulada existente com a versão mais recente do modelo de política.|
|O ID de Cliente do Azure Active Directory indicado não é um GUID corretamente formado. Especifique um ID de Cliente válido.|Ao utilizar o parâmetro de ID de Cliente, certifique-se de que indicou um ID de Cliente válido no formato GUID.|
|O URI de resposta do Azure Active Directory indicado não é um URI corretamente formado. Especifique um URI de resposta válido.|Ao utilizar a propriedade de linha de comandos do URI de resposta, certifique-se de que indicou um URI de resposta válido.|
|AVISO: não especificou um hash de certificado SHA1. Certifique-se de que a sua aplicação encapsulada está assinada antes de a implementar.|Certifique-se de que especifica um hash SHA válido (através da propriedade de linha de comandos **–c** ).|

### Ficheiros de registo da ferramenta de encapsulamento de aplicações
As aplicações encapsuladas com a ferramenta de encapsulamento de aplicações geram registos que são escritos na consola de dispositivos de cliente iOS. Estas informações são úteis caso tenha problemas com a aplicação e precise de diagnosticar se o problema está relacionado com a ferramenta de encapsulamento de aplicações. Para obter estas informações, utilize os passos seguintes:

1.  Reproduza o problema ao executar a aplicação.

2.  Recolha o resultado da consola ao seguir as instruções da Apple para [Depurar Aplicações iOS Implementadas](https://developer.apple.com/library/ios/qa/qa1747/_index.html).

3.  Filtre os registos guardados do resultado das Restrições da Aplicação ao introduzir o seguinte script na consola:

    ```
    grep “IntuneAppRestrictions” <text file containing console output> > <required filtered log file name>
    ```
    Pode submeter os registos filtrados à Microsoft.

    > [!NOTE]
    > No ficheiro de registo, o item "versão de compilação" representa a versão de compilação do Xcode.

    As aplicações encapsuladas também apresentam aos utilizadores a opção para enviar registos diretamente a partir do dispositivo por e-mail depois de a aplicação falhar. Os utilizadores podem enviar-lhe o registo para que o examine e reencaminhe para a Microsoft se necessário.

## Informações para aplicações que utilizam a Biblioteca do Azure Active Directory
As informações nesta secção aplicam-se apenas às aplicações que utilizam a Biblioteca do Azure Active Directory (ADAL). Caso não tenha a certeza se a sua aplicação utiliza esta biblioteca, contacte o programador da aplicação.

A aplicação tem de incorporar uma versão da ADAL superior ou igual a 1.0.2.

Para aplicações que utilizem a ADAL, tem de aplicar-se o seguinte:

-   A aplicação tem de incorporar uma versão da ADAL superior ou igual a 1.0.2

-   Os programadores têm de conceder acesso à aplicação ao recurso Gestão de Aplicações Móveis do Intune, conforme descrito em [Passos a seguir para aplicações que utilizam a ADAL](#steps-to-follow-for-apps-that-use-adal).

### Descrição geral de identificadores que tem de obter
As aplicações que utilizem a ADAL têm de ser registadas através do portal de gestão do Azure para obter dois identificadores exclusivos para a respetiva aplicação:

|Identificador|Mais informações|Valor predefinido|
|--------------|--------------------|-----------------|
|**ID de Cliente**|É gerado um identificador GUID exclusivo para cada aplicação depois de a mesma ser registada no Azure Active Directory.<br /><br />Se souber o ID de cliente específico da aplicação, pode especificar este valor. Caso contrário, terá de ser utilizado o valor predefinido.|6c7e8096-f593-4d72-807f-a5f86dcc9c77|
|**URI de Redirecionamento**|Um valor URI que os programadores podem fornecer quando registarem a respetiva aplicação no Azure Active Directory para garantir que os tokens de autenticação são devolvidos especificamente para esse ponto final.<br /><br />Fornecer um URI de redireccionamento é um parâmetro opcional da ferramenta de encapsulamento de aplicações. Caso não seja especificado, será utilizado um URI predefinido.|urn:ietf:wg:oauth:2.0:oob|


### Passos a seguir para aplicações que utilizam a ADAL

1.  Reveja [Descrição geral de identificadores que tem de obter](#overview-of-identifiers-you-need-to-get) para identificar os valores que precisa de obter.

2.  Configure o acesso à gestão de aplicações móveis no Azure Active Directory ao efetuar o seguinte:

    1. Iniciar sessão numa conta existente do Azure Active Directory no portal de gestão do Azure.

    2.  Clicar em **registo de aplicação LOB existente** no Azure Active Directory.

    3.  Na secção de configuração, selecionar **Configurar o Acesso a APIs da Web noutras aplicações**.

    4.  Na secção **Permissão para outras aplicações**, na primeira lista pendente, selecione **Gestão de Aplicações Móveis do Intune**.

        Pode agora utilizar o ID de Cliente da aplicação na ferramenta de encapsulamento de aplicações. Pode encontrar o ID de Cliente da aplicação no portal de gestão do Azure Active Directory, conforme descrito na secção [Descrição geral de identificadores que tem de obter](#overview-of-identifiers-you-need-to-get).

3.  Utilize os valores **Client-ID** (utilizando a propriedade **–a**) e **Redirect-URI** como propriedades de linha de comandos na ferramenta de encapsulamento de aplicações. Se não tiver estes valores, serão utilizados os valores predefinidos. Tem de especificar ambos os valores, caso contrário, o utilizador final não conseguirá autenticar com êxito a aplicação processada.

### Certificado, perfil de aprovisionamento e requisitos de autenticação

|Requisito|Detalhes|
|---------------|-----------|
|Perfil de aprovisionamento|**Certifique-se de que o perfil de aprovisionamento é válido antes de o incluir** – A ferramenta de encapsulamento de aplicações não verifica se o perfil de aprovisionamento expirou ao processar uma aplicação iOS. Se especificar um perfil de aprovisionamento já expirado, a ferramenta de moldagem de aplicações irá incluir o perfil de aprovisionamento expirado e não saberá que existe um problema até não ser possível instalar a aplicação num dispositivo iOS.|
|Certificado|**Certifique-se de que o certificado é válido antes de o especificar** – A ferramenta de encapsulamento de aplicações não verifica se o certificado expirou ao processar aplicações iOS. Se indicar um hash de um certificado expirado, a ferramenta irá processar e assinar a aplicação, mas ocorrerá uma falha de instalação em dispositivos.<br /><br />**Certifique-se de que o certificado fornecido para assinar a aplicação em pacote tem uma correspondência no perfil de aprovisionamento** – A ferramenta não verifica se o perfil de aprovisionamento tem uma correspondência do certificado fornecido para assinar a aplicação encapsulada.|
|Autenticação|Um dispositivo tem de ter um PIN definido para a encriptação funcionar. Nos dispositivos em que implementou a aplicação encapsulada, o utilizador terá de proceder novamente à autenticação do [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] ao tocar na barra de estado do dispositivo. A política predefinida numa aplicação encapsulada é *autenticação após reinicialização*. O iOS processa qualquer notificação externa (por exemplo um telefonema) como uma saída da aplicação e, em seguida, voltar a iniciá-la.<br /><br />Nas aplicações encapsuladas, o primeiro utilizador que iniciar sessão numa aplicação encapsulada do mesmo fabricante é colocado em cache. A partir deste momento, apenas esse utilizador tem permissão para aceder à aplicação. Para redefinir o utilizador, terá de cancelar a inscrição do dispositivo e, em seguida, reinscrevê-lo.|

### Resolução de problemas e notas técnicas sobre a ADAL

-   Se não forem localizados recursos da ADAL, a ferramenta não incluirá a biblioteca dinâmica da ADAL. A ferramenta irá procurar a biblioteca da ADAL com um nome **ADALiOS.bundle** na pasta raiz.

-   A ferramenta não procura binários da ADAL (caso existam) na aplicação. Se a aplicação ligar a uma versão desatualizada, poderão ocorrer erros de runtime durante o início de sessão se as políticas de autenticação estiverem ativadas.

-   [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] obtém o token do AAD para o ID de recurso do MAM do [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] para autenticação. No entanto, o token não é utilizado em nenhuma chamada que, por sua vez, vá verificar a respetiva validade. [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] só lê o UPN do utilizador com sessão iniciada para determinar o acesso da aplicação. O token do AAD não é utilizado para outras chamadas de serviço.

-   Os tokens de autenticação são partilhados entre aplicações do mesmo fabricante, uma vez que estão armazenadas numa keychain partilhada. Se pretender isolar uma aplicação específica, tem de utilizar um certificado de assinatura e um perfil de aprovisionamento diferentes nessa aplicação.

-   São impedidos pedidos de início de sessão duplos se fornecer o ID de Cliente e URI de Redirecionamento da aplicação cliente. Este ID de Cliente precisa de estar registado para aceder ao ID de recurso do MAM do [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] publicado no Dashboard do AAD. Caso contrário, ocorrerá uma falha ao iniciar sessão quando a aplicação for executada.

## Definição de elegibilidade da aplicação
Antes de encapsular a sua aplicação, pode conceder **elegibilidade** para conceder capacidades e permissões adicionais de aplicações que excedem o que uma aplicação pode fazer normalmente.  É utilizado um **ficheiro de elegibilidade** durante a assinatura de código para especificar permissões especiais na sua aplicação (por exemplo, acesso a uma keychain partilhada). Serviços aplicacionais específicos, denominados **capacidades**, são ativados no Xcode durante o desenvolvimento da aplicação. Depois de ativadas, as capacidades são refletidas no ficheiro de elegibilidade. Para mais informações sobre elegibilidade e capacidades, consulte [Adicionar Capacidades](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/AddingCapabilities/AddingCapabilities.html) na iOS Developer Library. Para obter uma lista completa de capacidades suportadas, veja [Supported capabilities (Capacidades suportadas)](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/SupportedCapabilities/SupportedCapabilities.html).

### Capacidades suportadas para a Ferramenta de Encapsulamento de Aplicações para iOS

|Funcionalidade|Descrição|Orientações recomendadas|
|--------------|---------------|------------------------|
|Grupos de Aplicações|Utilize grupos de aplicações para permitir que várias aplicações acedam a contentores partilhados e permitir a comunicação adicional entre processos entre as aplicações.<br /><br />Para ativar grupos de aplicações, abra o painel **Capacidades** e clique no comutador **ATIVAR** na secção **Grupos de Aplicações**. Pode adicionar grupos de aplicações ou selecionar grupos já existentes.|Quando utilizar Grupos de Aplicações, utilize a notação de DNS reverso:<br /><br />*group.com.companyName.AppGroup*|
|Modos em Segundo Plano|A ativação de modos em segundo plano permite à aplicação iOS continuar a ser executada em segundo plano.||
|Proteção de dados|A proteção de dados adiciona um nível de segurança aos ficheiros armazenados no disco pela aplicação iOS. A proteção de dados utiliza o hardware de encriptação incorporado presente em dispositivos específicos para armazenar ficheiros num formato encriptado no disco. A aplicação tem de ser aprovisionada para utilizar a proteção de dados.||
|Compras Via Aplicação|A compra via aplicação incorpora uma loja diretamente na sua aplicação, permitindo ligar à loja e processar pagamentos do utilizador em segurança. Pode utilizar a Compra Via Aplicação para recolher o pagamento de funcionalidade melhorada ou de conteúdo adicional utilizável pela sua aplicação.||
|Partilha de Keychain|A ativação da partilha de keychain permite à aplicação partilhar palavras-passe na keychain com outras aplicações desenvolvidas pela sua equipa.|Quando utilizar a Partilha de Keychain, utilize a notação de DNS reverso:<br /><br />*com.companyName.KeychainGroup*|
|VPN Pessoal|Ative a VPN pessoal para permitir à aplicação criar e controlar uma configuração de VPN do sistema personalizada utilizando a estrutura de Extensão de Rede.||
|Notificações Push|O serviço Apple Push Notification (APNs) permite a uma aplicação que não está em execução em primeiro plano notificar o utilizador de que tem informações para o mesmo.|Para que as notificações push funcionem, tem de utilizar um perfil de aprovisionamento específico da aplicação.<br /><br />Siga os passos na [documentação de programador da Apple](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/AddingCapabilities/AddingCapabilities.html).|
|Configuração de Acessórios Sem Fios|A ativação da configuração de acessórios sem fios adiciona a estrutura Acessórios Externos ao seu projeto e permite à aplicação configurar acessórios Wi-Fi MFi.||

### Passos para ativar a elegibilidade

1.  Ativar capacidades na sua aplicação:

    1.  No Xcode, navegue para o destino da sua aplicação e clique no painel **Capacidades**.

    2.  Ative as capacidades adequadas. Para obter informações detalhadas sobre cada capacidade e como determinar os valores corretos, consulte [Adicionar Capacidades](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/AddingCapabilities/AddingCapabilities.html) na iOS Developer Library.

    3.  Anote quaisquer IDs que criou durante o processo.

    4.  Crie e assine a aplicação a ser encapsulada.

2.  Ativar a elegibilidade no seu perfil de aprovisionamento:

    1.  Inicie sessão no Apple Developer Member Center.

    2.  Crie um perfil de aprovisionamento para a sua aplicação. Para obter instruções, veja [How to Obtain the Prerequisites for the Intune App Wrapping Tool for iOS (Como Obter os Pré-requisitos para a Ferramenta de Encapsulamento de Aplicações do Microsoft Intune para iOS)](https://blogs.technet.microsoft.com/enterprisemobility/2015/02/25/how-to-obtain-the-prerequisites-for-the-intune-app-wrapping-tool-for-ios/)

    3.  No perfil de aprovisionamento, ative a mesma elegibilidade existente na sua aplicação. Terá de fornecer os mesmos IDs que especificou durante o desenvolvimento da aplicação.

    4.  Conclua o assistente do perfil de aprovisionamento e transfira o ficheiro.

3.  Certifique-se de que cumpriu todos os pré-requisitos e, em seguida, encapsule a aplicação.

### Resolução de erros comuns com elegibilidade
Se a Ferramenta de Encapsulamento de Aplicações para iOS apresentar um erro de elegibilidade, tente os seguintes passos de resolução de problemas.

|Problema|Causa|Resolução|
|---------|---------|--------------|
|Falha ao analisar a elegibilidade gerada a partir da aplicação de entrada.|A Ferramenta de Encapsulamento de Aplicações não consegue ler o ficheiro de elegibilidade extraído da aplicação. O formato do ficheiro de elegibilidade poderá estar incorreto.|Inspecione o ficheiro de elegibilidade para a sua aplicação. Para tal, siga as instruções detalhadas abaixo. Quando inspecionar o ficheiro de elegibilidade, verifique a existência de sintaxe formada incorretamente. O ficheiro deve estar no formato XML.|
|A elegibilidade está em falta no perfil de aprovisionamento (é listada a elegibilidade em falta). Empacote novamente a aplicação com um perfil de aprovisionamento com esta elegibilidade.|Existe um erro de correspondência entre a elegibilidade ativada no perfil de aprovisionamento e as capacidades ativadas na aplicação. Este erro de correspondência também se aplica aos IDs associados a capacidades específicas (ou seja, Grupos de Aplicações, Acesso de Keychain, etc.).|Geralmente, pode criar um novo perfil de aprovisionamento que permite as mesmas capacidades que a aplicação. Quando os IDs entre o perfil e a aplicação não corresponderem, a Ferramenta de Encapsulamento de Aplicações substituirá os IDs, se tal for possível. Se ainda obtiver este erro depois de criar um novo perfil de aprovisionamento, pode tentar remover a elegibilidade da aplicação utilizando o parâmetro **–e** (consulte a secção «Utilizar o parâmetro –e para remover a elegibilidade de uma aplicação» abaixo).|

### Localizar a elegibilidade existente de uma aplicação assinada
Para rever a elegibilidade existente de uma aplicação assinada e o perfil de aprovisionamento:

1.  Localize o ficheiro .ipa e altere a extensão para .zip.

2.  Expanda o ficheiro .zip. Isto produzirá uma pasta Payload com o pacote .app.

3.  Utilize a ferramenta de assinatura de código para verificar a elegibilidade no pacote .app como se segue:

    ```
    $ codesign -d --entitlements :- "Payload/YourApp.app"
    ```
    em que `YourApp.app` é o nome real do pacote .app.

4.  Utilize a ferramenta de segurança para verificar a elegibilidade do perfil de aprovisionamento incorporado da aplicação:

    ```
    $ security -D -i "Payload/YourApp.app/embedded.mobileprovision"
    ```
    em que `YourApp.app` é o nome real do pacote .app.

### Utilizar o parâmetro –e para remover a elegibilidade de uma aplicação
Este comando remove quaisquer capacidades ativadas na aplicação que não estão no ficheiro de elegibilidade. Se remover capacidades que estão a ser utilizadas pela aplicação, pode causar uma falha na sua aplicação. Um exemplo de onde poderá remover capacidades em falta é se tiver uma aplicação produzida pelo fornecedor com todas as capacidades por predefinição.

```
./IntuneMAMPackager/Contents/MacOS/IntuneMAMPackager –i /<path of input app>/<app filename> -o /<path to output folder>/<app filename> –p /<path to provisioning profile> –c <SHA1 hash of the certificate> -e
```

## Segurança e privacidade da ferramenta de encapsulamento de aplicações
Utilize as seguintes melhores práticas de segurança e privacidade quando utilizar a ferramenta de encapsulamento de aplicações.

-   O certificado de assinatura, o perfil de aprovisionamento e a aplicação de linha de negócio que especificar têm de estar no mesmo computador Mac que utiliza para executar a ferramenta de encapsulamento de aplicações. Se os ficheiros estiverem num caminho UNC, certifique-se de que é possível aceder aos mesmos a partir do computador Mac. O caminho tem de estar protegido por IPsec ou assinatura SMB.

    A aplicação encapsulada importada para a consola do [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] deve estar no mesmo computador no qual a ferramenta é executada. Se o ficheiro estiver num caminho UNC, certifique-se de que é possível aceder ao mesmo no computador que está a executar a consola do [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]. O caminho tem de estar protegido por IPsec ou assinatura SMB.

-   O ambiente para onde a ferramenta de encapsulamento de aplicações é transferida a partir do site do Centro de Transferências da Microsoft tem de estar protegido por IPsec ou assinatura SMB.

-   A aplicação que processar tem de ser proveniente de uma origem de fidedigna para garantir a proteção contra ataques.

-   Certifique-se de que a pasta de saída que especifica na ferramenta de encapsulamento de aplicações está protegida, principalmente se for uma pasta remota.

-   As aplicações iOS que incluem uma caixa de diálogo de carregamento de ficheiros podem permitir aos utilizadores contornar as restrições de cortar, copiar e colar aplicadas à aplicação. Por exemplo, um utilizador poderia utilizar a caixa de diálogo de carregamento de ficheiros para carregar uma captura de ecrã dos dados da aplicação.

-   Quando os utilizadores monitorizam a pasta de documentos no respetivo dispositivo a partir de uma aplicação encapsulada, poderão ver uma pasta com o nome **.msftintuneapplauncher**. Se esta pasta for alterada ou eliminada, poderá afetar o correto funcionamento das aplicações com restrições.

### Consulte também
- [Decidir como preparar as aplicações para a gestão de aplicações móveis com o Microsoft Intune](decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune.md)</br>
- [Gerir definições e funcionalidades nos seus dispositivos com as políticas do Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)</br>
- [Utilizar o SDK para ativar aplicações para gestão de aplicações móveis](use-the-sdk-to-enable-apps-for-mobile-application-management.md)



<!--HONumber=Jul16_HO4-->


