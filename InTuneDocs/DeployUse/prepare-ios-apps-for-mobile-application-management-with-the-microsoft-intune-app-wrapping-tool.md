---
title: "Encapsular aplicações iOS com a Ferramenta de Encapsulamento de Aplicações | Microsoft Intune"
description: "Utilize as informações neste tópico para saber como pode encapsular as suas aplicações iOS sem modificar os próprios códigos. Prepare as aplicações para que possa aplicar políticas de gestão de aplicações móveis."
keywords: 
author: karthikaraman
ms.author: karaman
manager: angrobe
ms.date: 09/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 99ab0369-5115-4dc8-83ea-db7239b0de97
ms.reviewer: oldang
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: c67a5042fd177a4c5bd897092e84281db0977f5e
ms.openlocfilehash: 2c187b61b8fe25b2870d0cbc62f8352494583fc2


---

# Preparar as aplicações iOS para gestão de aplicações móveis com a Ferramenta de Encapsulamento de Aplicações do Intune
Utilize a **Ferramenta de Encapsulamento de Aplicações do Microsoft Intune para iOS** para modificar o comportamento das aplicações iOS internas para restringir funcionalidades da aplicação sem alterar o código da aplicação em si.

A ferramenta consiste numa aplicação da linha de comandos do Mac OS que cria um "encapsulamento" em torno de uma aplicação. Assim que uma aplicação é processada, pode alterar as funcionalidades da mesma ao utilizar [políticas de gestão de aplicações móveis](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md) do Intune configuradas por si.

Para transferir a ferramenta, veja [Ferramenta de Encapsulamento de Aplicações do Microsoft Intune para iOS](https://github.com/msintuneappsdk/intune-app-wrapping-tool-ios).



## Passo 1. cumprir os pré-requisitos de utilização da ferramenta de encapsulamento de aplicações
Leia [esta publicação no blogue](http://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx) para saber mais sobre os pré-requisitos e como os definir.

|Requisito|Mais informações|
|---------------|--------------------------------|
|Sistema operativo e conjunto de ferramentas suportados|Tem de executar a ferramenta de encapsulamento de aplicações num computador macOS que execute o OS X 10.8.5 ou posterior, que tem a versão 5 ou posterior do conjunto de ferramentas do Xcode instalada.|
|Certificado de assinatura e perfil de aprovisionamento|Precisa de ter um perfil de aprovisionamento e um certificado de assinatura da Apple. Veja a [documentação para programadores Apple](https://developer.apple.com/).|
|Processar uma aplicação com a Ferramenta de Encapsulamento de Aplicações|As aplicações têm de ser programadas e assinadas pela sua empresa ou por um fabricante independente de software (ISV). Não pode utilizar esta ferramenta para processar aplicações da Apple Store. As aplicações têm de ter sido escritas para o iOS 8.0 ou posterior. As aplicações têm de estar no formato PIE (Position Independent Executable). Para obter mais informações sobre o formato PIE, consulte a sua documentação de programador da Apple. Por fim, a aplicação tem de ter a extensão no formato **.app** ou **.ipa**.|
|Aplicações que a ferramenta de encapsulamento não pode processar|Aplicações encriptadas, aplicações não assinadas e aplicações com atributos de ficheiro expandidos.|
|Definir a elegibilidade para a sua aplicação|Tem de definir a elegibilidade, que fornece as capacidades e permissões adicionais de aplicações além das normalmente concedidas, antes de encapsular a aplicação. Consulte [Definição de elegibilidade da aplicação](#setting-app-entitlements) para obter instruções.|

## Passo 2. instalar a ferramenta de encapsulamento de aplicações

1.  A partir do [repositório da **Ferramenta de Encapsulamento de Aplicações do Microsoft Intune para iOS** alojado no GitHub](https://github.com/msintuneappsdk/intune-app-wrapping-tool-ios), transfira localmente os ficheiros da ferramenta de encapsulamento de aplicações para um computador macOS.

2.  Faça duplo clique no ficheiro de instalação **Microsoft Intune App Wrapping Tool for iOS.dmg**. Será apresentada uma janela com o Contrato de Licença do Utilizador Final (EULA). Leia atentamente o documento.

3. Selecione **Concordo** para aceitar o EULA, essa ação monta o pacote no seu computador.

4.  Abra o pacote **IntuneMAMPackager** e guarde os ficheiros numa pasta local no seu computador macOS. Já está pronto para executar a ferramenta de encapsulamento de aplicações.

## Passo 3. executar a ferramenta de encapsulamento de aplicações
* No seu computador macOS, abra uma janela Terminal e navegue para a pasta onde guardou os ficheiros da ferramenta de encapsulamento de aplicações. A ferramenta executável designa-se **IntuneMAMPackager** e está localizada em **IntuneMAMPackager/Contents/MacOS**. Terá de executar o comando da seguinte forma:

    ```
./IntuneMAMPackager/Contents/MacOS/IntuneMAMPackager -i /<path of input app>/<app filename> -o /<path to output folder>/<app filename> -p /<path to provisioning profile> -c <SHA1 hash of the certificate> [-b [<output app build string>]] [-v] [-e] [-x /<array of extension provisioning profile paths>]

    ```

    > [!NOTE]
    > Alguns parâmetros são opcionais, conforme apresentado na tabela abaixo.

    **Exemplo:** O comando de exemplo seguinte executa a ferramenta de encapsulamento de aplicações numa aplicação denominada **MyApp.ipa**. São especificados um perfil de aprovisionamento e um hash SHA-1. É criada a aplicação processada, designada **MyApp_Wrapped.ipa** e armazenada na pasta Desktop do utilizador.

    ```
    ./IntuneMAMPackager/Contents/MacOS/IntuneMAMPackager -i ~/Desktop/MyApp.ipa -o ~/Desktop/MyApp_Wrapped.ipa -p ~/Desktop/My_Provisioning_Profile_.mobileprovision -c 12A3BC45D67EF8901A2B3CDEF4ABC5D6E7890FAB  -v true
    ```
    Pode utilizar as seguintes propriedades de linha de comandos na ferramenta de encapsulamento de aplicações:

    |Propriedade|Como a utilizar|
  |------------|--------------------|
  |**-i**|`<Path of the input native iOS application file>`. O ficheiro tem de terminar em .app ou .ipa. |
  |**-o**|`<Path of the wrapped output application>` |
  |**-p**|`<Path of your provisioning profile for iOS apps>`|
  |**-c**|`<SHA1 hash of the signing certificate>`|
    |-h|Apresenta informações de utilização detalhadas nas propriedades de linha de comandos disponíveis para a ferramenta de encapsulamento de aplicações.|
  |-v|(Opcional mas útil) Dá saída de mensagens verbosas para a consola.|
  |-e | (Opcional) Utilize este sinalizador para fazer com que a ferramenta de encapsulamento de aplicações remova as elegibilidades em falta à medida que processa a aplicação. Consulte a secção "Definir elegibilidades de aplicação" para obter mais detalhes.|
  |-xe| (Opcional) Imprime informações acerca das extensões iOS na aplicação e que elegibilidades são necessárias para as utilizar. Consulte a secção "Definir elegibilidades de aplicação" para obter mais detalhes. |
  |-x| (Opcional) `<An array of paths to extension provisioning profiles>`. Utilize esta opção se a sua aplicação necessitar de perfis de aprovisionamento de extensões.|
  |-f |(Opcional) `<Path to a plist file specifying arguments.>` Utilize este sinalizador à frente do ficheiro [plist](https://developer.apple.com/library/mac/documentation/Cocoa/Conceptual/PropertyLists/Introduction/Introduction.html) se optar por utilizar o modelo plist para especificar o resto das propriedades do IntuneMAMPackager: -i, -o, -p, etc. Consulte a secção "Utilizar uma plist para argumentos de entrada" para obter mais detalhes. |
  |-b|(Opcional) Utilize -b sem um argumento se quiser que a aplicação de saída encapsulada tenha a mesma versão de pacote que a aplicação de entrada (não recomendado). <br/><br/> Utilize `-b <custom bundle version>` se quiser que a aplicação encapsulada tenha uma CFBundleVersion personalizada. Se optar por especificar uma CFBundleVersion personalizada, recomendamos que incremente a CFBundleVersion da aplicação nativa pelo componente menos significativo, por exemplo: 1.0.0 -> 1.0.1. |


###Utilize uma plist para argumentos de entrada
Uma forma simples de executar a Ferramenta de Encapsulamento de Aplicações é colocar todos os argumentos de comando num ficheiro [plist](https://developer.apple.com/library/mac/documentation/Cocoa/Conceptual/PropertyLists/Introduction/Introduction.html). O plist é um formato de ficheiro semelhante a XML que podemos utilizar para dar entrada dos nossos argumentos de linha de comandos através de uma interface de formulário.

Na pasta **IntuneMAMPackager/Contents/MacOS**, abra `Parameters.plist`, um modelo plist em branco com um editor de texto ou com o Xcode. Introduza os seus argumentos para as seguintes chaves:

| Chave Plist |  Valor Predefinido| Notas |
|------------------|--------------|-----|
| Caminho de Pacote de Aplicação de Entrada  |vazio| Mesmo que -i. |
| Caminho de Pacote de Aplicação de Saída |vazio| Mesmo que -o.|
| Caminho de Perfil de Aprovisionamento |vazio| Mesmo que -p. |
| Hash de Certificado SHA-1 |vazio| Mesmo que -c. |
| Verbose Ativada |falso| Mesmo que -v. |
| Remover Elegibilidades em Falta | falso| Mesmo que -c.|
| Impedir Compilação Predefinida |falso | Equivalente a utilizar -b sem argumentos. |
|Substituição de Cadeia da Compilação | vazio| A CFBundleVersion personalizada da aplicação de saída encapsulada |
|Caminhos de Perfil de Aprovisionamento de Extensão | vazio| Uma matriz dos perfis de aprovisionamento de extensão da aplicação.
  

Por fim, execute o IntuneMAMPackager com o ficheiro plist como único argumento:

```
./IntuneMAMPackager –f Parameters.plist
```

* Depois de o processamento ser concluído, será apresentada a mensagem **A aplicação foi encapsulada com êxito**.

    Se ocorrer um erro, consulte [Mensagens de erro](prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md#error-messages) para obter ajuda.

*   A aplicação encapsulada é guardada no ficheiro de saída que especificou anteriormente. Agora pode carregar a aplicação para o [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] e associá-la a uma política de gestão de aplicações móveis.

    > [!IMPORTANT]
    > Ao carregar a aplicação encapsulada, pode tentar atualizar uma versão mais antiga da aplicação se uma versão mais antiga (encapsulada ou nativa) já tiver sido implementada no Intune. Se ocorrer um erro, utilize a aplicação como uma nova aplicação e elimine a versão antiga.

    Pode implementar a aplicação nos grupos do [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] e a aplicação irá agora ser executada no dispositivo com as restrições da aplicação que especificou.

## Mensagens de erro e ficheiros de registo
Utilize as seguintes informações para resolver problemas com a ferramenta de encapsulamento de aplicações.

### Mensagens de erro
Se a ferramenta de encapsulamento de aplicações não conseguir concluir com êxito, será apresentada na consola uma das seguintes mensagens de erro:

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
|Especificou um certificado de assinatura inválido. Especifique um certificado de assinatura da Apple válido.|Certifique-se de que transferiu o certificado de assinatura correto a partir do portal de programador da Apple. O seu certificado poderá ter expirado ou uma chave pública ou privada poderá estar em falta. Se o seu perfil de aprovisionamento e o certificado da Apple puderem ser utilizados para assinar corretamente uma aplicação no Xcode, significa que são válidos para a ferramenta de encapsulamento de aplicações.|
|A aplicação de entrada que especificou é inválida. Especifique uma aplicação válida.|Certifique-se de que tem uma aplicação iOS válida que tenha sido compilada como um ficheiro .app ou .ipa.|
|A aplicação de entrada que especificou está encriptada. Especifique uma aplicação não encriptada válida.|A ferramenta de encapsulamento de aplicações não suporta aplicações encriptadas. Forneça uma aplicação não encriptada.|
|A aplicação de entrada que especificou não está no formato PIE (Position Independent Executable). Especifique uma aplicação válida no formato PIE.|As aplicações PIE (Position Independent Executable) podem ser carregadas num endereço de memória aleatório quando são executadas, o que pode ser vantajoso a nível da segurança. Para obter mais informações, consulte a sua documentação de Programador da Apple.|
|A aplicação de entrada que especificou já foi encapsulada. Especifique uma aplicação não encapsulada válida.|Não pode processar uma aplicação que já tenha sido processada pela ferramenta. Se pretender processar novamente uma aplicação, execute a ferramenta com a versão original da aplicação.|
|A aplicação de entrada que especificou não está assinada. Especifique uma aplicação assinada válida.|A ferramenta de encapsulamento de aplicações requer que as aplicações sejam assinadas. Consulte a sua documentação de programador para saber como assinar uma aplicação encapsulada.|
|A aplicação de entrada que especificou tem de estar no formato .ipa ou .app.|A ferramenta de encapsulamento de aplicações só aceita as extensões .app e .ipa. Certifique-se de que o seu ficheiro de entrada tem uma extensão válida e de que foi compilado como ficheiro .app ou .ipa.|
|A aplicação de entrada que especificou já foi encapsulada e encontra-se na versão mais recente do modelo de política.|A ferramenta de encapsulamento de aplicações não irá encapsular novamente uma aplicação encapsulada existente com a versão mais recente do modelo de política.|
|AVISO: não especificou um hash de certificado SHA1. Certifique-se de que a sua aplicação encapsulada está assinada antes de a implementar.|Certifique-sede que especifica um hash SHA1 válido que siga o sinalizador da linha de comandos **–c**. |

### Ficheiros de registo da ferramenta de encapsulamento de aplicações
As aplicações encapsuladas com a ferramenta de encapsulamento de aplicações geram registos que são escritos na consola de dispositivos de cliente iOS. Estas informações são úteis se tiver problemas com a aplicação e precisar de diagnosticar se o problema está relacionado com a ferramenta de encapsulamento de aplicações. Para obter estas informações, utilize os passos seguintes:

1.  Reproduza o problema ao executar a aplicação.

2.  Recolha o resultado da consola ao seguir as instruções da Apple para [Depurar Aplicações iOS Implementadas](https://developer.apple.com/library/ios/qa/qa1747/_index.html).

3.  Filtre os registos guardados do resultado das Restrições da Aplicação ao introduzir o seguinte script na consola:

    ```
    grep “IntuneAppRestrictions” <text file containing console output> > <required filtered log file name>
    ```
    Pode submeter os registos filtrados à Microsoft.

    > [!NOTE]
    > No ficheiro de registo, o item "versão de compilação" representa a versão de compilação do Xcode.

    As aplicações encapsuladas também apresentam aos utilizadores a opção para enviar registos diretamente a partir do dispositivo por e-mail depois de a aplicação falhar. Os utilizadores podem enviar-lhe os registos para que os examine e reencaminhe para a Microsoft se necessário.


### Certificado, perfil de aprovisionamento e requisitos de autenticação

A ferramenta de encapsulamento de aplicações tem alguns requisitos que têm de ser cumpridos para garantir uma funcionalidade completa.

|Requisito|Detalhes|
|---------------|-----------|
|Perfil de aprovisionamento|**Certifique-se de que o ficheiro de aprovisionamento é válido antes de o incluir**. A ferramenta de encapsulamento de aplicações não verifica se o perfil de aprovisionamento já expirou quando processa uma aplicação iOS. Se especificar um perfil de aprovisionamento já expirado, a ferramenta de moldagem de aplicações irá incluir o perfil de aprovisionamento expirado e não saberá que existe um problema até não ser possível instalar a aplicação num dispositivo iOS.|
|Certificado|**Certifique-se de que o certificado é válido antes de o especificar**. A ferramenta não verifica se um certificado já expirou quando processa aplicações iOS. Se indicar um hash de um certificado expirado, a ferramenta irá processar e assinar a aplicação, mas ocorrerá uma falha de instalação em dispositivos.<br /><br />**Certifique-se de que o certificado fornecido para assinar o pacote de aplicação tem uma correspondência no perfil de aprovisionamento**. Se o perfil de aprovisionamento tiver uma correspondência para o certificado fornecido para assinatura da aplicação encapsulada, a ferramenta não será validada.|
|Autenticação|Um dispositivo tem de ter um PIN para a encriptação funcionar. Nos dispositivos em que implementou a aplicação encapsulada, o utilizador terá de proceder novamente à autenticação do [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] ao tocar na barra de estado do dispositivo. A política predefinida numa aplicação encapsulada é *autenticação após reinicialização*. O iOS processa todas as notificações externas (por exemplo, uma chamada) ao sair da aplicação e reiniciá-la.


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

-   O certificado de assinatura, o perfil de aprovisionamento e a aplicação de linha de negócio que especificar têm de estar no mesmo computador macOS que utiliza para executar a ferramenta de encapsulamento de aplicações. Se os ficheiros estiverem num caminho UNC, certifique-se de que é possível aceder aos mesmos a partir do computador macOS. O caminho tem de estar protegido por IPsec ou assinatura SMB.

    A aplicação encapsulada importada para a consola do [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] deve estar no mesmo computador no qual a ferramenta é executada. Se o ficheiro estiver num caminho UNC, certifique-se de que é possível aceder ao mesmo no computador que está a executar a consola do [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]. O caminho tem de estar protegido por IPsec ou assinatura SMB.

-   O ambiente para o qual a ferramenta de encapsulamento da aplicação é transferida a partir do repositório GitHub tem de ter segurança por assinatura IPsec ou SMB.

-   A aplicação que processar tem de ser proveniente de uma origem fidedigna para garantir a proteção contra ataques.

-   Certifique-se de que a pasta de saída que especifica na ferramenta de encapsulamento de aplicações está protegida, principalmente se for uma pasta remota.

-   As aplicações iOS que incluem uma caixa de diálogo de carregamento de ficheiros podem permitir aos utilizadores contornar as restrições de cortar, copiar e colar aplicadas à aplicação. Por exemplo, um utilizador poderia utilizar a caixa de diálogo de carregamento de ficheiros para carregar uma captura de ecrã dos dados da aplicação.

-   Quando os utilizadores monitorizam a pasta de documentos no respetivo dispositivo a partir de uma aplicação encapsulada, poderão ver uma pasta com o nome **.msftintuneapplauncher**. Se esta pasta for alterada ou eliminada, poderá afetar o correto funcionamento das aplicações com restrições.

### Consulte também
- [Decidir como preparar as aplicações para a gestão de aplicações móveis com o Microsoft Intune](decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune.md)</br>
- [Gerir definições e funcionalidades nos seus dispositivos com as políticas do Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)</br>
- [Utilizar o SDK para ativar aplicações para gestão de aplicações móveis](use-the-sdk-to-enable-apps-for-mobile-application-management.md)



<!--HONumber=Oct16_HO2-->


