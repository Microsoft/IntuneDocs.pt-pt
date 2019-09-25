---
title: Encapsular aplicações iOS com a Ferramenta de Encapsulamento de Aplicações do Intune
description: Saiba como encapsular as suas aplicações iOS sem alterar o código da aplicação. Prepare as aplicações para que possa aplicar políticas de gestão de aplicações móveis.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/12/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 99ab0369-5115-4dc8-83ea-db7239b0de97
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 228a4af302a1344f60dc43c02c12efac23e34f74
ms.sourcegitcommit: ec22a186a9cfa489a8490698e387624e480892d8
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/13/2019
ms.locfileid: "71238645"
---
# <a name="prepare-ios-apps-for-app-protection-policies-with-the-intune-app-wrapping-tool"></a>Preparar as aplicações iOS para as políticas de proteção de aplicações com a Ferramenta de Encapsulamento de Aplicações do Intune

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

Utilize a Ferramenta de Encapsulamento de Aplicações do Microsoft Intune para iOS para ativar as políticas de proteção da aplicação Intune para aplicações iOS internas sem alterar o código da aplicação em si.

A ferramenta consiste numa aplicação da linha de comandos do macOS que cria um encapsulamento em torno de uma aplicação. Depois de uma aplicação ser processada, pode alterar a funcionalidade da aplicação ao implementar [políticas de proteção de aplicações](app-protection-policies.md) à mesma.

Para transferir a ferramenta, veja [Ferramenta de Encapsulamento de Aplicações do Microsoft Intune para iOS](https://github.com/msintuneappsdk/intune-app-wrapping-tool-ios) no GitHub.



## <a name="general-prerequisites-for-the-app-wrapping-tool"></a>Pré-requisitos gerais da Ferramenta de Encapsulamento de Aplicações

Antes de executar a Ferramenta de Encapsulamento de Aplicações, terá de cumprir alguns pré-requisitos gerais:

* Transfira a [Ferramenta de Encapsulamento de Aplicações do Microsoft Intune para iOS](https://github.com/msintuneappsdk/intune-app-wrapping-tool-ios) a partir do GitHub.

* Ter um computador macOS que execute o OS X 10.8.5 ou posterior e tenha a versão 9 ou posterior do conjunto de ferramentas do Xcode instalada.

* A aplicação iOS de entrada tem de ser programada e assinada pela sua empresa ou por um fabricante de software independente (ISV).

  * O ficheiro de aplicação de entrada tem de ter a extensão **.ipa** ou **.app**.

  * A aplicação de entrada tem de estar compilada para o iOS 10 ou posterior.

  * A aplicação de entrada não pode ser encriptada.

  * A aplicação de entrada não pode ter atributos de ficheiro expandidos.

  * A aplicação de entrada tem de ter elegibilidades definidas antes de ser processada pela Ferramenta de Encapsulamento de Aplicações do Intune. As [elegibilidades](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/EntitlementKeyReference/Chapters/AboutEntitlements.html) fornecem as capacidades e permissões adicionais de aplicações além das normalmente concedidas. Consulte [Definição de elegibilidade da aplicação](#setting-app-entitlements) para obter instruções.

## <a name="apple-developer-prerequisites-for-the-app-wrapping-tool"></a>Pré-requisitos para Programadores Apple da Ferramenta de Encapsulamento de Aplicações

Para distribuir aplicações encapsuladas exclusivamente para os utilizadores da sua organização, precisa de uma conta do [Apple Developer Enterprise Program](https://developer.apple.com/programs/enterprise/) e várias entidades de assinatura de aplicações ligadas à sua conta de Programador Apple.

Para saber mais sobre a distribuição de aplicações iOS internamente para os utilizadores da sua organização, leia o guia oficial para [Distribuir Aplicações do Apple Developer Enterprise Program](https://developer.apple.com/library/content/documentation/IDEs/Conceptual/AppDistributionGuide/DistributingEnterpriseProgramApps/DistributingEnterpriseProgramApps.html#//apple_ref/doc/uid/TP40012582-CH33-SW1).

É necessário o seguinte para distribuir aplicações encapsuladas pelo Intune:

* Uma conta de programador do Apple Developer Enterprise Program.

* Um certificado de assinatura de distribuição interna e ad-hoc com um Identificador de Equipa válido.

  * É necessário o hash SHA1 do certificado de assinatura como um parâmetro para a Ferramenta de Encapsulamento de Aplicações do Intune.


* Um perfil de aprovisionamento de distribuição interna.

### <a name="steps-to-create-an-apple-developer-enterprise-account"></a>Passos para criar uma conta do Apple Developer Enterprise
1. Aceda ao [site do Apple Developer Enterprise Program](https://developer.apple.com/programs/enterprise/).

2. Na parte superior direita da página, clique em **Inscrever**.

3. Leia a lista de verificação sobre o que precisa para se inscrever. Clique em **Iniciar Inscrição** na parte inferior da página.

4. **Inicie sessão** com o ID Apple da sua organização. Se não tiver um, clique em **Criar ID Apple**.

5. Selecione o **Tipo de Entidade** e clique em **Continuar**.

6. Preencha o formulário com as informações da sua organização. Clique em **Continuar**. Neste passo, a Apple contacta-o para verificar se está autorizado a inscrever a sua organização.

8. Após a verificação, clique em **Aceitar Licenciar**.

9. Depois de aceitar licenciar, conclua ao **comprar e ativar o programa**.

10. Se for o agente da equipa (a pessoa associada ao Apple Developer Enterprise Program em nome da sua organização), crie primeiro a equipa ao convidar os membros de equipa e atribuir funções. Para saber como gerir a sua equipa, leia a documentação da Apple em [Gerir a Sua Equipa de Conta de Programador](https://developer.apple.com/library/content/documentation/IDEs/Conceptual/AppDistributionGuide/ManagingYourTeam/ManagingYourTeam.html#//apple_ref/doc/uid/TP40012582-CH16-SW1).

### <a name="steps-to-create-an-apple-signing-certificate"></a>Passos para criar um certificado de assinatura da Apple

1. Aceda ao [portal de Programador da Apple](https://developer.apple.com/).

2. Na parte superior direita da página, clique em **Conta**.

3. **Inicie sessão** com o seu ID Apple organizacional.

4. Clique em **Certificados, IDs e Perfis**.

   ![Portal do desenvolvedor da Apple – certificados, IDs & perfis](./media/iOS-signing-cert-1.png)

5. Clique no ![sinal de adição do portal de Programador da Apple](./media/iOS-signing-cert-2.png) no canto superior direito para adicionar um certificado iOS.

6. Opte por criar um certificado **Interno e Ad-Hoc** em **Produção**.

   ![Selecionar o certificado Interno e Ad-Hoc](./media/iOS-signing-cert-3.png)

   >[!NOTE]
   >Se não planeia distribuir a aplicação e apenas pretende testá-la internamente, pode utilizar um certificado de Programação de Aplicações para iOS em alternativa ao certificado de Produção. Se utilizar um certificado de programação, certifique-se de que o perfil de aprovisionamento móvel refere os dispositivos em que a aplicação será instalada.

7. Clique em **Seguinte** na parte inferior da página.

8. Leia as instruções sobre a criação de um **Pedido de Assinatura de Certificado (CSR)** através da aplicação Acesso a Porta-chaves no seu computador macOS.

   ![Leia as instruções para criar um CSR](./media/iOS-signing-cert-4.png)

9. Siga as instruções acima para criar um Pedido de Assinatura de Certificado. No seu computador macOS, inicie a aplicação **Acesso a Porta-chaves**.

10. No menu do macOS na parte superior do ecrã, aceda a **Acesso a Porta-chaves > Assistente de Certificados > Pedir um Certificado a Partir de uma Autoridade de Certificação**.  

    ![Pedir um certificado a partir de uma Autoridade de Certificação no Acesso a Porta-chaves](./media/iOS-signing-cert-5.png)

11. Siga as instruções do site de programador da Apple acima sobre como criar um ficheiro CSR. Guarde o ficheiro CSR no seu computador macOS.

    ![Insira informações para o certificado que você está solicitando](./media/iOS-signing-cert-6.png)

12. Regresse ao site de programador da Apple. Clique em **Continue** (Continuar). Em seguida, carregue o ficheiro CSR.

13. A Apple gera o certificado de assinatura. Transfira e guarde-o numa localização fácil de memorizar no seu computador macOS.

    ![Transferir o certificado de assinatura](./media/iOS-signing-cert-7.png)

14. Faça duplo clique no ficheiro de certificado que acabou de transferir para adicionar o certificado a um porta-chaves.

15. Abra novamente o **Acesso a Porta-chaves**. Localize o seu certificado ao procurar o respetivo nome no canto superior direito da barra de pesquisa. Clique com o botão direito do rato no item para aceder ao menu e clique em **Obter Informações**. Nos ecrãs de exemplo, estamos a utilizar um certificado de programação em alternativa ao certificado de produção.

    ![Adicionar o certificado a um porta-chaves](./media/iOS-signing-cert-8.png)

16. É apresentada uma janela informativa. Desloque para baixo e procure a etiqueta **Impressões Digitais**. Copie a cadeia **SHA1** (desfocada) a utilizar como argumento "-c" para a Ferramenta de Encapsulamento de Aplicações.

    ![informações do iPhone – cadeia de caracteres SHA1 de impressões digitais](./media/iOS-signing-cert-9.png)



### <a name="steps-to-create-an-in-house-distribution-provisioning-profile"></a>Passos para criar um perfil de Aprovisionamento de Distribuição Interna

1. Volte ao [portal de contas de Programador da Apple](https://developer.apple.com/account/) e **inicie sessão** com o seu ID Apple organizacional.

2. Clique em **Certificados, IDs e Perfis**.

3. Clique no ![sinal de adição do portal de Programador da Apple](./media/iOS-signing-cert-2.png) no canto superior direito para adicionar um perfil de aprovisionamento do iOS.

4. Opte por criar um perfil de aprovisionamento **Interno** em **Distribuição**.

   ![Selecionar o perfil de aprovisionamento interno](./media/iOS-provisioning-profile-1.png)

5. Clique em **Continue** (Continuar). Certifique-se de que associa o certificado de assinatura gerado anteriormente ao perfil de aprovisionamento.

6. Siga os passos para transferir o perfil (com a extensão .mobileprovision) para o seu computador macOS.

7. Guarde o ficheiro numa localização fácil de memorizar. Este ficheiro será utilizado para o parâmetro -p quando utilizar a Ferramenta de Encapsulamento de Aplicações.



## <a name="download-the-app-wrapping-tool"></a>Transferir a Ferramenta de Encapsulamento de Aplicações

1. Transfira os ficheiros para a Ferramenta de Encapsulamento de Aplicações do [GitHub](https://github.com/msintuneappsdk/intune-app-wrapping-tool-ios) para um computador macOS.

2. Faça duplo clique no ficheiro **Microsoft Intune App Wrapping Tool for iOS.dmg**. Será apresentada uma janela com o Contrato de Licença do Utilizador Final (EULA). Leia atentamente o documento.

3. Selecione **Concordo** para aceitar o EULA, essa ação monta o pacote no seu computador.

## <a name="run-the-app-wrapping-tool"></a>executar a Ferramenta de Encapsulamento de Aplicações

### <a name="use-terminal"></a>Utilizar o terminal

Abra o Terminal macOS e execute o seguinte comando:

```bash
/Volumes/IntuneMAMPackager/Contents/MacOS/IntuneMAMPackager -i /<path of input app>/<app filename> -o /<path to output folder>/<app filename> -p /<path to provisioning profile> -c <SHA1 hash of the certificate> [-b [<output app build string>]] [-v] [-e] [-x /<array of extension provisioning profile paths>]
```

> [!NOTE]
> Alguns parâmetros são opcionais, conforme apresentado na tabela seguinte.

**Example:** O comando de exemplo a seguir executa a ferramenta de encapsulamento de aplicativo no aplicativo chamado MyApp. ipa. Um perfil de aprovisionamento e um hash SHA-1 do certificado de assinatura são especificados e que servem para assinar a aplicação encapsulada. É criada a aplicação de saída (MyApp_Wrapped.ipa) e armazenada na sua pasta Ambiente de trabalho.

```bash
./IntuneMAMPackager/Contents/MacOS/IntuneMAMPackager -i ~/Desktop/MyApp.ipa -o ~/Desktop/MyApp_Wrapped.ipa -p ~/Desktop/My_Provisioning_Profile_.mobileprovision -c "12 A3 BC 45 D6 7E F8 90 1A 2B 3C DE F4 AB C5 D6 E7 89 0F AB"  -v true
```

### <a name="command-line-parameters"></a>Parâmetros da linha de comandos
Pode utilizar os seguintes parâmetros de linha de comandos na Ferramenta de Encapsulamento de Aplicações:

|Propriedade|Como a utilizar|
|---------------|--------------------------------|
|**-i**|`<Path of the input native iOS application file>`. O nome do ficheiro tem de terminar em .app ou .ipa. |
|**-o**|`<Path of the wrapped output application>` |
|**-p**|`<Path of your provisioning profile for iOS apps>`|
|**-c**|`<SHA1 hash of the signing certificate>`|
|**-h**| Mostra informações de utilização detalhadas sobre propriedades de linha de comandos disponíveis para a Ferramenta de Encapsulamento de Aplicações. |
|**-AA**|Adicional `<Authority URI of the input app if the app uses the Azure Active Directory Authentication Library>` ou seja, `login.windows.net/common` |
|**-AC**|Adicional `<Client ID of the input app if the app uses the Azure Active Directory Authentication Library>` Esse é o GUID no campo ID do cliente é da listagem do seu aplicativo na folha de registro do aplicativo. |
|**-ar**|Adicional `<Redirect/Reply URI of the input app if the app uses the Azure Active Directory Authentication Library>` Esse é o URI de redirecionamento configurado no registro do aplicativo. Normalmente, seria o protocolo de URL do aplicativo que o aplicativo Microsoft Authenticator retornaria após a autenticação orientada. |
|**-v**| (Opcional) Dá saída de mensagens verbosas para a consola. Recomenda-se a utilização deste sinalizador para depurar quaisquer erros. |
|**-e**| (Opcional) Utilize este sinalizador para fazer com que a Ferramenta de Encapsulamento de Aplicações remova as elegibilidades em falta à medida que processa a aplicação. Veja [Definição de elegibilidade da aplicação](#setting-app-entitlements) para obter mais detalhes.|
|**-xe**| (Opcional) Imprime informações acerca das extensões iOS na aplicação e que elegibilidades são necessárias para as utilizar. Veja [Definição de elegibilidade da aplicação](#setting-app-entitlements) para obter mais detalhes. |
|**-x**| (Opcional) `<An array of paths to extension provisioning profiles>`. Utilize esta opção se a sua aplicação necessitar de perfis de aprovisionamento de extensões.|
|**-b**|(Opcional) Utilize -b sem um argumento se quiser que a aplicação de saída encapsulada tenha a mesma versão de pacote que a aplicação de entrada (não recomendado). <br/><br/> Utilize `-b <custom bundle version>` se quiser que a aplicação encapsulada tenha uma CFBundleVersion personalizada. Se optar por especificar uma CFBundleVersion personalizada, é recomendado incrementar a CFBundleVersion da aplicação nativa pelo componente menos significativo, como 1.0.0 -> 1.0.1. |
|**-Citrix**|Adicional Inclua o SDK do Citrix XenMobile app (variante somente de rede). Você deve ter o [Citrix MDX Toolkit](https://docs.citrix.com/en-us/mdx-toolkit/about-mdx-toolkit.html) instalado para usar essa opção. |
|**-f**|(Opcional) `<Path to a plist file specifying arguments.>` Utilize este sinalizador à frente do ficheiro [plist](https://developer.apple.com/library/mac/documentation/Cocoa/Conceptual/PropertyLists/Introduction/Introduction.html) se optar por utilizar o modelo plist para especificar o resto das propriedades do IntuneMAMPackager, como -i, -o e -p. Consulte Utilizar uma plist para argumentos de entrada. |

### <a name="use-a-plist-to-input-arguments"></a>Utilize uma plist para argumentos de entrada
Uma forma simples de executar a Ferramenta de Encapsulamento de Aplicações é colocar todos os argumentos de comando num ficheiro [plist](https://developer.apple.com/library/mac/documentation/Cocoa/Conceptual/PropertyLists/Introduction/Introduction.html). O plist é um formato de ficheiro semelhante a XML que pode utilizar para dar entrada dos seus argumentos de linha de comandos através de uma interface de formulário.

Na pasta IntuneMAMPackager/Contents/MacO, abra `Parameters.plist` (um modelo plist em branco) com um editor de texto ou com o Xcode. Introduza os seus argumentos para as seguintes chaves:

| Chave plist | Type |  Default Value | Notas |
|------------------|-----|--------------|-----|
| Caminho de Pacote de Aplicação de Entrada |Cadeia|vazio| Mesmo que -i|
| Caminho de Pacote de Aplicação de Saída |Cadeia|vazio| Mesmo que -o|
| Caminho de Perfil de Aprovisionamento |Cadeia|vazio| Mesmo que -p|
| Hash de Certificado SHA-1 |Cadeia|vazio| Mesmo que -c|
| Autoridade ADAL |Cadeia|vazio| Mesmo que-AA|
| ID do cliente ADAL |Cadeia|vazio| Mesmo que-AC|
| URI de resposta da ADAL |Cadeia|vazio| Mesmo que o ar|
| Verbose Ativada |Booleano|false| Mesmo que -v|
| Remover Elegibilidades em Falta |Booleano|false| Mesmo que -c|
| Impedir a atualização de compilação padrão |Bool|false| Equivalente a utilizar -b sem argumentos|
| Substituição de Cadeia da Compilação |Cadeia|vazio| A CFBundleVersion personalizada da aplicação de saída encapsulada|
| Incluir o SDK do Citrix XenMobile app (variante somente de rede)|Booleano|false| Mesmo que-Citrix|
| Caminhos de Perfil de Aprovisionamento de Extensão |Matriz de Cadeias|vazio| Uma matriz dos perfis de aprovisionamento de extensão da aplicação.


Execute o IntuneMAMPackager com o ficheiro plist como único argumento:

```bash
./IntuneMAMPackager –f Parameters.plist
```

### <a name="post-wrapping"></a>Pós-encapsulamento

Depois de o processamento de encapsulamento ser concluído, será apresentada a mensagem "A aplicação foi encapsulada com êxito". Se ocorrer um erro, consulte [Mensagens de erro](#error-messages-and-log-files) para obter ajuda.

A aplicação encapsulada é guardada no ficheiro de saída que especificou anteriormente. Pode carregar a aplicação para a consola de administrador do Intune e associá-la a uma política de gestão de aplicações móveis.

> [!IMPORTANT]
> Ao carregar a aplicação encapsulada, pode tentar atualizar uma versão mais antiga da aplicação se uma versão mais antiga (encapsulada ou nativa) já tiver sido implementada no Intune. Se ocorrer um erro, utilize a aplicação como uma nova aplicação e elimine a versão antiga.

Agora pode implementar a aplicação nos seus grupos de utilizadores e nas suas políticas de proteção de aplicações de destino para a aplicação. A aplicação será executada no dispositivo com as políticas de proteção da aplicação que especificou.

## <a name="how-often-should-i-rewrap-my-ios-application-with-the-intune-app-wrapping-tool"></a>Com que frequência devo encapsular novamente a minha aplicação iOS com a Ferramenta de Encapsulamento de Aplicações do Intune?
Os principais cenários nos quais teria de encapsular novamente as suas aplicações são os seguintes:
* A própria aplicação lançou uma nova versão. A versão anterior da aplicação foi encapsulada e carregada para a consola do Intune.
* A Ferramenta de Encapsulamento de Aplicações do Intune para iOS lançou uma nova versão com correções de erros importantes ou funcionalidades específicas e novas da política de proteção de aplicações do Intune. Isto ocorre passadas seis a oito semanas através do repositório do GitHub para a [Ferramenta de Encapsulamento de Aplicações do Microsoft Intune para iOS](https://github.com/msintuneappsdk/intune-app-wrapping-tool-ios).

Para o iOS, embora seja possível encapsular com perfis de aprovisionamento/certificados diferentes do original que foi utilizado para assinar a aplicação, se as elegibilidades especificadas na aplicação não estiverem incluídas no novo perfil de aprovisionamento, o encapsulamento irá falhar. Utilizar a opção de linha de comandos "–e", que remove todas as elegibilidades em falta da aplicação, para impedir que o encapsulamento falhe neste cenário pode causar falhas de funcionalidade na aplicação.

As melhores práticas para encapsular novamente incluem:
* Garantir que um perfil de aprovisionamento diferente tem todas as elegibilidades necessárias como qualquer perfil de aprovisionamento anterior. 

## <a name="error-messages-and-log-files"></a>Mensagens de erro e ficheiros de registo
Utilize as seguintes informações para resolver problemas com a ferramenta de encapsulamento de aplicações.

### <a name="error-messages"></a>Mensagens de erro
Se a ferramenta de encapsulamento de aplicações não conseguir concluir com êxito, será apresentada na consola uma das seguintes mensagens de erro:

|Mensagem de erro|Mais informações|
|-----------------|--------------------|
|Tem de especificar um perfil de aprovisionamento do iOS válido.|O seu perfil de aprovisionamento poderá não ser válido. Certifique-se de que tem as permissões corretas para os dispositivos e de que o seu perfil está corretamente direcionado para a programação ou para a distribuição. Também é provável que o seu perfil de aprovisionamento tenha expirado.|
|Especifique um nome de aplicação de entrada válido.|Certifique-se de que o nome da aplicação de entrada que especificou está correto.|
|Especifique um caminho válido para a aplicação de saída.|Certifique-se de que o caminho da aplicação de saída que especificou existe e está correto.|
|Especifique um perfil de aprovisionamento de entrada válido.|Certifique-se de que forneceu um nome e extensão do perfil de aprovisionamento válidos. É provável que faltem elegibilidades no seu perfil de aprovisionamento ou que não tenha incluído a opção de linha de comandos –p.|
|Não foi possível localizar a aplicação de entrada que especificou. Especifique um caminho e nome de aplicação de entrada válidos.|Certifique-se de que o caminho da aplicação de entrada é válido e existe. Certifique-se de que a aplicação de entrada existe nessa localização.|
|Não foi possível localizar o ficheiro do perfil de aprovisionamento de entrada que especificou. Especifique um ficheiro do perfil de aprovisionamento de entrada válido.|Certifique-se de que o caminho para o ficheiro de aprovisionamento de entrada é válido e que o ficheiro que especificou existe.|
|Não foi possível localizar a pasta da aplicação de saída que especificou. Especifique um caminho válido para a aplicação de saída.|Certifique-se de que o caminho de saída que especificou é válido e existe.|
|A aplicação de saída não tem a extensão **.ipa**.|A Ferramenta de Encapsulamento de Aplicações só aceita aplicações com as extensões **.app** e **.ipa**. Certifique-se de que o seu ficheiro de saída tem uma extensão válida.|
|Especificou um certificado de assinatura inválido. Especifique um certificado de assinatura da Apple válido.|Certifique-se de que transferiu o certificado de assinatura correto a partir do portal de programador da Apple. O seu certificado poderá ter expirado ou uma chave pública ou privada poderá estar em falta. Se o seu perfil de aprovisionamento e o certificado da Apple puderem ser utilizados para assinar corretamente uma aplicação no Xcode, significa que são válidos para a Ferramenta de Encapsulamento de Aplicações.|
|A aplicação de entrada que especificou é inválida. Especifique uma aplicação válida.|Certifique-se de que tem uma aplicação iOS válida que tenha sido compilada como um ficheiro .app ou .ipa.|
|A aplicação de entrada que especificou está encriptada. Especifique uma aplicação não encriptada válida.|A Ferramenta de Encapsulamento de Aplicações não suporta aplicações encriptadas. Forneça uma aplicação não encriptada.|
|A aplicação de entrada que especificou não está no formato PIE (Position Independent Executable). Especifique uma aplicação válida no formato PIE.|As aplicações no formato Position Independent Executable (PIE) podem ser carregadas num endereço de memória aleatória ao ser executadas. Isto pode ter vantagens de segurança. Para obter mais informações sobre vantagens de segurança, consulte a sua documentação Apple Developer.|
|A aplicação de entrada que especificou já foi encapsulada. Especifique uma aplicação não encapsulada válida.|Não pode processar uma aplicação que já tenha sido processada pela ferramenta. Se pretender processar novamente uma aplicação, execute a ferramenta com a versão original da aplicação.|
|A aplicação de entrada que especificou não está assinada. Especifique uma aplicação assinada válida.|A ferramenta de encapsulamento de aplicações requer que as aplicações sejam assinadas. Consulte a sua documentação de programador para saber como assinar uma aplicação encapsulada.|
|A aplicação de entrada que especificou tem de estar no formato .ipa ou .app.|A ferramenta de encapsulamento de aplicações só aceita as extensões .app e .ipa. Certifique-se de que o seu ficheiro de entrada tem uma extensão válida e de que foi compilado como ficheiro .app ou .ipa.|
|A aplicação de entrada que especificou já foi encapsulada e encontra-se na versão mais recente do modelo de política.|A Ferramenta de Encapsulamento de Aplicações não volta a encapsular uma aplicação encapsulada existente com a versão mais recente do modelo de política.|
|ALERTA Você não especificou um hash de certificado SHA1. Certifique-se de que a sua aplicação encapsulada está assinada antes de a implementar.|Certifique-se de que especifica um hash SHA1 válido que siga o sinalizador da linha de comandos –c. |

### <a name="log-files-for-the-app-wrapping-tool"></a>Ficheiros de registo da Ferramenta de Encapsulamento de Aplicações
As aplicações encapsuladas com a Ferramenta de Encapsulamento de Aplicações geram registos que são escritos na consola de dispositivos de cliente iOS. Estas informações são úteis se tiver problemas com a aplicação e precisar de determinar se o problema está relacionado com a Ferramenta de Encapsulamento de Aplicações. Para obter estas informações, utilize os passos seguintes:

1. Reproduza o problema ao executar a aplicação.

2. Recolha o resultado da consola ao seguir as instruções da Apple para [Depurar Aplicações iOS Implementadas](https://developer.apple.com/library/ios/qa/qa1747/_index.html).

3. Filtre os registos guardados do resultado das Restrições da Aplicação ao introduzir o seguinte script na consola:

    ```bash
    grep “IntuneAppRestrictions” <text file containing console output> > <required filtered log file name>
    ```

    Pode submeter os registos filtrados à Microsoft.

    > [!NOTE]
    > No ficheiro de registo, o item "versão de compilação" representa a versão de compilação do Xcode.

    As aplicações encapsuladas também apresentam aos utilizadores a opção para enviar registos diretamente a partir do dispositivo por e-mail depois de a aplicação falhar. Os utilizadores podem enviar-lhe os registos para que os examine e reencaminhe para a Microsoft se necessário.


### <a name="certificate-provisioning-profile-and-authentication-requirements"></a>Certificado, perfil de aprovisionamento e requisitos de autenticação

A Ferramenta de Encapsulamento de Aplicações para iOS tem alguns requisitos que têm de ser cumpridos para garantir uma funcionalidade completa.

|Requisito|Detalhes|
|---------------|-----------|
|Perfil de aprovisionamento do iOS|Certifique-se de que o ficheiro de aprovisionamento é válido antes de o incluir. A Ferramenta de Encapsulamento de Aplicações não verifica se o perfil de aprovisionamento já expirou quando processa uma aplicação iOS. Se especificar um perfil de aprovisionamento já expirado, a ferramenta de moldagem de aplicações irá incluir o perfil de aprovisionamento expirado e não saberá que existe um problema até não ser possível instalar a aplicação num dispositivo iOS.|
|Certificado de assinatura de iOS|Confirme que o certificado de assinatura é válido antes de o especificar. A ferramenta não verifica se um certificado já expirou quando processa aplicações iOS. Se indicar um hash de um certificado expirado, a ferramenta irá processar e assinar a aplicação, mas ocorrerá uma falha de instalação em dispositivos.<br /><br />Confirme que o certificado disponibilizado para assinar a aplicação encapsulada tem uma correspondência no perfil de aprovisionamento. Se o perfil de aprovisionamento tiver uma correspondência para o certificado fornecido para assinatura da aplicação encapsulada, a ferramenta não será validada.|
|Autenticação|Um dispositivo tem de ter um PIN para a encriptação funcionar. Nos dispositivos em que implementou a aplicação encapsulada, o utilizador terá de iniciar sessão novamente com uma conta escolar ou profissional ao tocar na barra de estado do dispositivo. A política predefinida numa aplicação encapsulada é *autenticação após reinicialização*. O iOS processa qualquer notificação externa (como um telefonema) ao sair da aplicação e, em seguida, voltar a iniciá-la.


## <a name="setting-app-entitlements"></a>Definição de elegibilidade da aplicação
Antes de encapsular a sua aplicação, pode conceder *elegibilidade* para atribuir à aplicação permissões e funcionalidades adicionais que excedem o que uma aplicação pode fazer normalmente. É utilizado um *ficheiro de elegibilidade* durante a assinatura de código para especificar permissões especiais na sua aplicação (por exemplo, acesso a uma keychain partilhada). São ativados serviços aplicacionais específicos no Xcode, denominados *capacidades*, durante o desenvolvimento da aplicação. Depois de ativadas, as capacidades são refletidas no ficheiro de elegibilidade. Para mais informações sobre elegibilidade e capacidades, consulte [Adicionar Capacidades](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/AddingCapabilities/AddingCapabilities.html) na iOS Developer Library. Para obter uma lista completa de capacidades suportadas, veja [Supported capabilities (Capacidades suportadas)](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/SupportedCapabilities/SupportedCapabilities.html).

### <a name="supported-capabilities-for-the-app-wrapping-tool-for-ios"></a>Capacidades suportadas para a Ferramenta de Encapsulamento de Aplicações para iOS

|Funcionalidade|Descrição|Orientações recomendadas|
|--------------|---------------|------------------------|
|Grupos de aplicações|Utilize grupos de aplicações para permitir que várias aplicações acedam a contentores partilhados e permitir a comunicação adicional entre processos entre as aplicações.<br /><br />Para ativar grupos de aplicações, abra o painel **Capacidades** e clique em **ATIVAR** em **Grupos de Aplicações**. Pode adicionar grupos de aplicações ou selecionar grupos já existentes.|Quando utilizar Grupos de Aplicações, utilize a notação de DNS reverso:<br /><br />*Grupo.com.nomeDaEmpresa.GrupoDeAplicações*|
|Modos em segundo plano|A ativação de modos em segundo plano permite à aplicação iOS continuar a ser executada em segundo plano.||
|Proteção de dados|A proteção de dados adiciona um nível de segurança aos ficheiros armazenados no disco pela aplicação iOS. A proteção de dados utiliza o hardware de encriptação incorporado presente em dispositivos específicos para armazenar ficheiros num formato encriptado no disco. A aplicação tem de ser aprovisionada para utilizar a proteção de dados.||
|Compras via aplicação|A compra via aplicação incorpora uma loja diretamente na sua aplicação, permitindo ligar à loja e processar pagamentos do utilizador em segurança. Pode utilizar a compra via aplicação para recolher o pagamento de funcionalidade melhorada ou de conteúdo adicional utilizável pela sua aplicação.||
|Partilha de keychain|A ativação da partilha de keychain permite à aplicação partilhar palavras-passe na keychain com outras aplicações desenvolvidas pela sua equipa.|Quando utilizar a partilha de keychain, utilize a notação de DNS reverso:<br /><br />*com.companyName.KeychainGroup*|
|VPN Pessoal|Ative a VPN pessoal para permitir à aplicação criar e controlar uma configuração de VPN do sistema personalizada utilizando a estrutura de Extensão de Rede.||
|Notificações push|O serviço Apple Push Notification (APNs) permite a uma aplicação que não está em execução em primeiro plano notificar o utilizador de que tem informações para o mesmo.|Para que as notificações push funcionem, tem de utilizar um perfil de aprovisionamento específico da aplicação.<br /><br />Siga os passos na [documentação de programador da Apple](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/AddingCapabilities/AddingCapabilities.html).|
|Configuração de acessórios sem fios|A ativação da configuração de acessórios sem fios adiciona a estrutura Acessórios Externos ao seu projeto e permite à aplicação configurar acessórios Wi-Fi MFi.||

### <a name="steps-to-enable-entitlements"></a>Passos para ativar a elegibilidade

1. Ativar capacidades na sua aplicação:

    a.  No Xcode, aceda ao destino da sua aplicação e clique no painel **Capacidades**.

    b.  Ative as capacidades adequadas. Para obter informações detalhadas sobre cada capacidade e como determinar os valores corretos, consulte [Adicionar Capacidades](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/AddingCapabilities/AddingCapabilities.html) na iOS Developer Library.

    c.  Anote quaisquer IDs que criou durante o processo. Estes também podem ser chamados valores `AppIdentifierPrefix`.

    d.  Crie e assine a aplicação a ser encapsulada.

2. Ativar a elegibilidade no seu perfil de aprovisionamento:

    a.  Inicie sessão no Apple Developer Member Center.

    b.  Crie um perfil de aprovisionamento para a sua aplicação. Para obter instruções, veja [How to Obtain the Prerequisites for the Intune App Wrapping Tool for iOS (Como Obter os Pré-requisitos para a Ferramenta de Encapsulamento de Aplicações do Microsoft Intune para iOS)](https://blogs.technet.microsoft.com/enterprisemobility/2015/02/25/how-to-obtain-the-prerequisites-for-the-intune-app-wrapping-tool-for-ios/)

    c.  No perfil de aprovisionamento, ative a mesma elegibilidade existente na sua aplicação. Terá de fornecer os mesmos IDs (os valores `AppIdentifierPrefix`) que especificou durante o desenvolvimento da aplicação. 

    d.  Termine o assistente do perfil de aprovisionamento e transfira o ficheiro.

3. Certifique-se de que cumpriu todos os pré-requisitos e, em seguida, encapsule a aplicação.

### <a name="troubleshoot-common-errors-with-entitlements"></a>Resolução de erros comuns com elegibilidade
Se a Ferramenta de Encapsulamento de Aplicações para iOS mostrar um erro de elegibilidade, tente os seguintes passos de resolução de problemas.

|Problema|Causa|Resolução|
|---------|---------|--------------|
|Falha ao analisar a elegibilidade gerada a partir da aplicação de entrada.|A Ferramenta de Encapsulamento de Aplicações não consegue ler o ficheiro de elegibilidade extraído da aplicação. O formato do ficheiro de elegibilidade poderá estar incorreto.|Inspecione o ficheiro de elegibilidade para a sua aplicação. As instruções seguintes explicam como fazê-lo. Quando inspecionar o ficheiro de elegibilidade, verifique a existência de sintaxe formada incorretamente. O ficheiro deve estar no formato XML.|
|A elegibilidade está em falta no perfil de aprovisionamento (é listada a elegibilidade em falta). Empacote novamente a aplicação com um perfil de aprovisionamento com esta elegibilidade.|Existe um erro de correspondência entre a elegibilidade ativada no perfil de aprovisionamento e as capacidades ativadas na aplicação. Este erro de correspondência também se aplica aos IDs associados a capacidades específicas (como grupos de aplicações e acesso de keychain).|Geralmente, pode criar um novo perfil de aprovisionamento que permite as mesmas capacidades que a aplicação. Quando os IDs entre o perfil e a aplicação não corresponderem, a Ferramenta de Encapsulamento de Aplicações substituirá os IDs, se tal for possível. Se ainda obtiver este erro depois de criar um novo perfil de aprovisionamento, pode tentar remover a elegibilidade da aplicação utilizando o parâmetro –e (consulte a secção "Utilizar o parâmetro –e para remover a elegibilidade de uma aplicação").|

### <a name="find-the-existing-entitlements-of-a-signed-app"></a>Localizar a elegibilidade existente de uma aplicação assinada
Para rever a elegibilidade existente de uma aplicação assinada e o perfil de aprovisionamento:

1. Localize o ficheiro .ipa e altere a extensão para .zip.

2. Expanda o ficheiro .zip. Isto produzirá uma pasta Payload com o pacote .app.

3. Utilize a ferramenta de assinatura de código para verificar a elegibilidade no pacote .app, sendo que `YourApp.app` é o nome real do seu pacote .app.

    ```bash
    codesign -d --entitlements :- "Payload/YourApp.app"
    ```

4. Utilize a ferramenta de segurança para verificar a elegibilidade do perfil de aprovisionamento incorporado da aplicação, sendo que `YourApp.app` é o nome real do seu pacote .app.

    ```bash
    security cms -D -i "Payload/YourApp.app/embedded.mobileprovision"
    ```

### <a name="remove-entitlements-from-an-app-by-using-the-e-parameter"></a>Remover a elegibilidade de uma aplicação ao utilizar o parâmetro –e
Este comando remove quaisquer capacidades ativadas na aplicação que não estão no ficheiro de elegibilidade. Se remover capacidades que estão a ser utilizadas pela aplicação, pode causar uma falha na sua aplicação. Um exemplo de onde poderá remover capacidades em falta é se tiver uma aplicação produzida pelo fornecedor com todas as capacidades por predefinição.

```bash
./IntuneMAMPackager/Contents/MacOS/IntuneMAMPackager –i /<path of input app>/<app filename> -o /<path to output folder>/<app filename> –p /<path to provisioning profile> –c <SHA1 hash of the certificate> -e
```

## <a name="security-and-privacy-for-the-app-wrapping-tool"></a>Segurança e privacidade da Ferramenta de Encapsulamento de Aplicações
Utilize as seguintes práticas recomendadas de segurança e privacidade quando utilizar a Ferramenta de Encapsulamento de Aplicações.

- O certificado de assinatura, o perfil de aprovisionamento e a aplicação de linha de negócio que especificar têm de estar no mesmo computador macOS que utiliza para executar a ferramenta de encapsulamento de aplicações. Se os ficheiros estiverem num caminho UNC, certifique-se de que é possível aceder aos mesmos a partir do computador macOS. O caminho tem de estar protegido por IPsec ou assinatura SMB.

    A aplicação encapsulada importada para a consola do administrador deve estar no mesmo computador no qual a ferramenta é executada. Se o ficheiro estiver num caminho UNC, confira que é acessível no computador que está a executar a consola do administrador. O caminho tem de estar protegido por IPsec ou assinatura SMB.

- O ambiente para o qual a Ferramenta de Encapsulamento de Aplicações é transferida a partir do repositório GitHub tem de ter segurança por assinatura IPsec ou SMB.

- A aplicação que processar tem de ser proveniente de uma origem fidedigna para garantir a proteção contra ataques.

- Certifique-se de que a pasta de saída que especifica na Ferramenta de Encapsulamento de Aplicações está protegida, principalmente se for uma pasta remota.

- As aplicações iOS que incluem uma caixa de diálogo de carregamento de ficheiros podem permitir aos utilizadores contornar as restrições de cortar, copiar e colar aplicadas à aplicação. Por exemplo, um utilizador poderia utilizar a caixa de diálogo de carregamento de ficheiros para carregar uma captura de ecrã dos dados da aplicação.

- Quando monitorizar a pasta de documentos no respetivo dispositivo a partir de uma aplicação encapsulada, poderá ver uma pasta com o nome .msftintuneapplauncher. Se alterar ou eliminar este ficheiro, poderá afetar o correto funcionamento das aplicações com restrições.

## <a name="intune-app-wrapping-tool-for-ios-with-citrix-mdx-mvpn"></a>Ferramenta de Encapsulamento de Aplicações do Intune para iOS com Citrix MDX mVPN
Esta funcionalidade é uma integração com o encapsulamento de aplicações Citrix MDX para iOS. A integração é um simples sinalizador de linha de comandos `-citrix` opcional e adicional para as Ferramentas de Encapsulamento de Aplicações do Intune.

### <a name="requirements"></a>Requisitos

Para utilizar o sinalizador `-citrix`, terá de instalar o [encapsulamento de aplicações Citrix MDX para iOS](https://docs.citrix.com/en-us/mdx-toolkit/10/xmob-mdx-kit-app-wrap-ios.html) na mesma máquina macOS. As transferências encontram-se em [Citrix XenMobile Downloads](https://www.citrix.com/downloads/xenmobile/) e estão limitadas a clientes do Citrix depois de iniciar sessão. Certifique-se de que está instalado na localização predefinida: `/Applications/Citrix/MDXToolkit`. 

> [!NOTE] 
> O suporte para a integração do Intune e Citrix está limitado a dispositivos com o iOS 10 e superior.

### <a name="use-the--citrix-flag"></a>Utilizar o sinalizador `-citrix`
Execute o seu comando de encapsulamento de aplicações geral com o sinalizador `-citrix` anexado. Atualmente, o sinalizador `-citrix` não aceita argumentos.

**Formato de utilização**:

```bash
./IntuneMAMPackager/Contents/MacOS/IntuneMAMPackager -i /<path of input app>/<app filename> -o /<path to output folder>/<app filename> -p /<path to provisioning profile> -c <SHA1 hash of the certificate> [-b [<output app build string>]] [-v] [-e] [-x /<array of extension provisioing profile paths>] [-citrix]
```

**Comando de exemplo**:

```bash
./IntuneMAMPackager/Contents/MacOS/IntuneMAMPackager -i ~/Desktop/MyApp.ipa -o ~/Desktop/MyApp_Wrapped.ipa -p ~/Desktop/My_Provisioning_Profile_.mobileprovision -c 12A3BC45D67EF8901A2B3CDEF4ABC5D6E7890FAB  -v true -citrix
```

## <a name="getting-logs-for-your-wrapped-applications"></a>Obter registos para as aplicações encapsuladas
Utilize os seguintes passos para obter registos para as aplicações encapsuladas durante a resolução de problemas.

1. Aceda à aplicação Definições do iOS no dispositivo e selecione a aplicação LOB.
2. Em **Consola de Diagnóstico**, escolha **Ativar**.
3. Inicie a aplicação LOB.
4. Clique na ligação “Introdução”.
5. Agora, pode partilhar os registos através do e-mail ou copiá-los para uma localização do OneDrive.

> [!NOTE]
> A funcionalidade de registo está ativada nas aplicações que tenham sido encapsuladas com a Ferramenta de Encapsulamento de Aplicações do Intune versão 7.1.13 ou superior.

## <a name="see-also"></a>Consulte também

- [Decidir como preparar as aplicações para a gestão de aplicações móveis com o Microsoft Intune](apps-prepare-mobile-application-management.md)
- [Perguntas comuns, problemas e resoluções com perfis e políticas de dispositivo](device-profile-troubleshoot.md)
- [Utilizar o SDK para ativar aplicações para gestão de aplicações móveis](app-sdk.md)
