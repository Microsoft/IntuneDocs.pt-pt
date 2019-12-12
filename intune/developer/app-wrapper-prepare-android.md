---
title: Encapsular aplicações Android com a Ferramenta de Encapsulamento de Aplicações do Intune
description: Saiba como pode encapsular as suas aplicações Android sem alterar o código das mesmas. Prepare as aplicações para que possa aplicar políticas de gestão de aplicações móveis.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/02/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: e9c349c8-51ae-4d73-b74a-6173728a520b
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8fa63540afa18450f731180da3c2cee729010a65
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/05/2019
ms.locfileid: "74465698"
---
# <a name="prepare-android-apps-for-app-protection-policies-with-the-intune-app-wrapping-tool"></a>Preparar as aplicações Android para as políticas de proteção de aplicações com a Ferramenta de Encapsulamento de Aplicações do Intune

Utilize a Ferramenta de Encapsulamento de Aplicações do Microsoft Intune para Android para alterar o comportamento das suas aplicações Android internas ao restringir funcionalidades da aplicação sem alterar o código da aplicação em si.

A ferramenta é uma aplicação de linha de comandos do Windows executada no PowerShell, que cria um encapsulamento em torno da aplicação Android. Quando a aplicação estiver encapsulada, pode alterar a funcionalidade da aplicação ao configurar [políticas de gestão de aplicações móveis](../apps/app-protection-policies.md) no Intune.

Antes de executar a ferramenta, consulte as [Considerações de segurança para executar a ferramenta de encapsulamento de aplicações](#security-considerations-for-running-the-app-wrapping-tool). Para transferir a ferramenta, aceda à [Ferramenta de Encapsulamento de Aplicações do Microsoft Intune para Android](https://github.com/msintuneappsdk/intune-app-wrapping-tool-android) no GitHub.

## <a name="fulfill-the-prerequisites-for-using-the-app-wrapping-tool"></a>Cumprir os pré-requisitos de utilização da Ferramenta de Encapsulamento de Aplicações

- Tem de executar a Ferramenta de Encapsulamento de Aplicações num computador Windows com o Windows 7 ou posterior.

- A aplicação de entrada tem de ser um pacote de aplicação Android válido com a extensão de ficheiro .apk e:

  - Não pode ser encriptada.
  - Não pode ter sido encapsulada anteriormente pela Ferramenta de Encapsulamento de Aplicações.
  - Tem de ter sido escrita para Android 4.0 ou posterior.

- A aplicação tem de ter sido programada pela sua empresa ou para a mesma. Não pode utilizar esta ferramenta em aplicações transferidas a partir da Google Play Store.

- Para executar a Ferramenta de Encapsulamento de Aplicações, tem de instalar a versão mais recente do [Ambiente de Tempo de Execução Java](https://java.com/download/) e, em seguida, certificar-se de que a variável de caminho Java foi definida como C:\ProgramData\Oracle\Java\javapath nas variáveis do seu ambiente do Windows. Para obter mais ajuda, consulte a [documentação do Java](https://java.com/download/help/).

    > [!NOTE]
    > Nalguns casos, a versão de 32 bits do Java pode originar problemas de memória. É boa ideia instalar a versão de 64 bits.

- O Android exige que todos os pacotes de aplicação (.apk) sejam assinados. Para **reutilizar** certificados existentes e obter orientações gerais sobre certificados de assinatura, veja a secção [Reutilizar certificados de assinatura e encapsular aplicações](app-wrapper-prepare-android.md#reusing-signing-certificates-and-wrapping-apps). A ferramenta de chave executável Java keytool.exe serve para gerar as **novas** credenciais necessárias para assinar a aplicação de saída encapsulada. Todas as palavras-passe que definir têm de ser seguras, mas anote-as, uma vez que irá precisar delas mais tarde para executar a Ferramenta de Encapsulamento de Aplicações.

    > [!NOTE]
    > A Ferramenta de Encapsulamento de Aplicações do Intune não suporta esquemas de assinatura v2 e v3 da Google para a assinatura de aplicações. Depois de encapsular o ficheiro .apk com a Ferramenta de Encapsulamento de Aplicações do Intune, é recomendado utilizar a [ferramenta Apksigner fornecida pela Google]( https://developer.android.com/studio/command-line/apksigner). Isto irá garantir que, assim que a sua aplicação chegar aos dispositivos dos utilizadores finais, poderá ser iniciada corretamente de acordo com os padrões do Android. 

- Adicional Às vezes, um aplicativo pode atingir o limite de tamanho do executável do Dalvik (DEX) devido às classes do SDK do MAM do Intune que são adicionadas durante o encapsulamento. Os ficheiros do DEX fazem parte da compilação de uma aplicação Android. A ferramenta de encapsulamento de aplicativos do Intune manipula automaticamente o estouro de arquivo DEX durante o encapsulamento de aplicativos com um nível de API mínimo de 21 ou superior (a partir de [v. 1.0.2501.1](https://github.com/msintuneappsdk/intune-app-wrapping-tool-android/releases)). Para aplicativos com um nível de API Mín de < 21, a prática recomendada seria aumentar o nível mínimo de API usando o sinalizador de `-UseMinAPILevelForNativeMultiDex` do wrapper. Para os clientes não conseguirem aumentar o nível de API mínimo do aplicativo, as seguintes soluções alternativas de estouro de DEX estão disponíveis. Em determinadas organizações, isso pode exigir o trabalho com quem compila o aplicativo (ou seja, a equipe de Build do aplicativo):

  - Use o ProGuard para eliminar referências de classes não utilizadas do arquivo DEX primário do aplicativo.
  - Para clientes que usam o v 3.1.0 ou superior do plug-in Android gradle, desabilite o [dexer D8](https://android-developers.googleblog.com/2018/04/android-studio-switching-to-d8-dexer.html).  

## <a name="install-the-app-wrapping-tool"></a>instalar a Ferramenta de Encapsulamento de Aplicações

1. A partir do [repositório GitHub ](https://github.com/msintuneappsdk/intune-app-wrapping-tool-android), transfira o ficheiro de instalação InstallAWT.exe da Ferramenta de Encapsulamento do Intune para Android num computador Windows. Abra o ficheiro de instalação.

2. Aceite o contrato de licença e conclua a instalação.

Não se esqueça da pasta na qual instalou a ferramenta. A localização predefinida é: C:\Program Files (x86)\Microsoft Intune Mobile Application Management\Android\App Wrapping Tool.

## <a name="run-the-app-wrapping-tool"></a>executar a Ferramenta de Encapsulamento de Aplicações

1. No computador Windows onde instalou a Ferramenta de Encapsulamento de Aplicações, abra uma janela do PowerShell.

2. Na pasta onde instalou a ferramenta, importe o módulo do PowerShell da Ferramenta de Encapsulamento de Aplicações:

   ```PowerShell
   Import-Module .\IntuneAppWrappingTool.psm1
   ```

3. Execute a ferramenta utilizando o comando **invoke-AppWrappingTool** cuja sintaxe de utilização está indicada em seguida:

   ```PowerShell
   Invoke-AppWrappingTool [-InputPath] <String> [-OutputPath] <String> -KeyStorePath <String> -KeyStorePassword <SecureString>
   -KeyAlias <String> -KeyPassword <SecureString> [-SigAlg <String>] [<CommonParameters>]
   ```

   A seguinte tabela explica detalhadamente as propriedades do comando **invoke-AppWrappingTool**:

|Propriedade|Informações|Exemplo|
|-------------|--------------------|---------|
|**-InputPath**&lt;String&gt;|Caminho da aplicação Android de origem (.apk).| |
 |**-OutputPath**&lt;String&gt;|Caminho para a aplicação Android de saída. Se este for o mesmo caminho de diretório como o InputPath, o empacotamento irá falhar.| |
|**-KeyStorePath**&lt;String&gt;|Caminho para o ficheiro de keystore que tem o par de chaves pública/privada para assinatura.|Por predefinição, os ficheiros de keystore são armazenados em "C:\Program Files (x86)\Java\jreX.X.X_XX\bin." |
|**-KeyStorePassword**&lt;SecureString&gt;|Palavra-passe utilizada para desencriptar o keystore. O Android requer que todos os pacotes de aplicações (. apk) estejam assinados. Utilize a ferramenta de chave Java para gerar a KeyStorePassword. Leia mais acerca da [KeyStore](https://docs.oracle.com/javase/7/docs/api/java/security/KeyStore.html) de Java aqui.| |
|**-KeyAlias**&lt;String&gt;|Nome da chave a ser utilizada para assinatura.| |
|**-KeyPassword**&lt;SecureString&gt;|Palavra-passe utilizada para desencriptar a chave privada que vai ser utilizada para assinatura.| |
|**-SigAlg**&lt;SecureString&gt;| (Opcional) O nome do algoritmo de assinatura a ser utilizado na assinatura. O algoritmo tem de ser compatível com a chave privada.|Exemplos: SHA256withRSA, SHA1withRSA|
|**-UseMinAPILevelForNativeMultiDex**| Adicional Use esse sinalizador para aumentar o nível de API mínimo do aplicativo Android de origem para 21. Esse sinalizador solicitará a confirmação, pois limitará quem pode instalar este aplicativo. Os usuários podem ignorar a caixa de diálogo de confirmação acrescentando o parâmetro "-Confirm: $false" ao comando do PowerShell. O sinalizador só deve ser usado por clientes em aplicativos com a API mínima < 21 que falha ao encapsular com êxito devido a erros de estouro de DEX. | |
| **&lt;CommonParameters&gt;** | (Opcional) O comando suporta parâmetros comuns do PowerShell, como verboso e depuração. |


- Para obter uma lista de parâmetros comuns, consulte o [Centro de Scripts da Microsoft](https://technet.microsoft.com/library/hh847884.aspx).

- Para ver informações de utilização detalhadas da ferramenta, introduza o comando:

    ```PowerShell
    Help Invoke-AppWrappingTool
    ```

**Example:**

Importe o módulo PowerShell.

```PowerShell
Import-Module "C:\Program Files (x86)\Microsoft Intune Mobile Application Management\Android\App Wrapping Tool\IntuneAppWrappingTool.psm1"
```

Execute a Ferramenta de Encapsulamento de Aplicações na aplicação nativa HelloWorld.apk.

```PowerShell
invoke-AppWrappingTool -InputPath .\app\HelloWorld.apk -OutputPath .\app_wrapped\HelloWorld_wrapped.apk -KeyStorePath "C:\Program Files (x86)\Java\jre1.8.0_91\bin\mykeystorefile" -keyAlias mykeyalias -SigAlg SHA1withRSA -Verbose
```

Ser-lhe-ão solicitadas a **KeyStorePassword** e a **KeyPassword**. Introduza as credenciais que utilizou para criar o ficheiro de keystore.

A aplicação encapsulada e um ficheiro de registos são gerados e guardados no caminho de saída que tiver especificado.

## <a name="how-often-should-i-rewrap-my-android-application-with-the-intune-app-wrapping-tool"></a>Com que frequência devo encapsular novamente a minha aplicação Android com a Ferramenta de Encapsulamento de Aplicações do Intune?
Os principais cenários nos quais teria de encapsular novamente as suas aplicações são os seguintes:
* A própria aplicação lançou uma nova versão. A versão anterior da aplicação foi encapsulada e carregada para a consola do Intune.
* A Ferramenta de Encapsulamento de Aplicações do Intune para Android lançou uma nova versão com correções de erros importantes ou funcionalidades específicas e novas da política de proteção de aplicações do Intune. Isto ocorre a cada 6 a 8 semanas através do repositório do GitHub para a [Ferramenta de Encapsulamento de Aplicações do Microsoft Intune para Android](https://github.com/msintuneappsdk/intune-app-wrapping-tool-android).

As melhores práticas para encapsular novamente incluem: 
* Manter certificados de assinatura utilizados durante o processo de compilação, veja [Reutilizar certificados de assinatura e encapsular aplicações](app-wrapper-prepare-android.md#reusing-signing-certificates-and-wrapping-apps)

## <a name="reusing-signing-certificates-and-wrapping-apps"></a>Reutilizar certificados de assinatura e encapsular aplicações
O Android exige que todas as aplicações sejam assinadas por um certificado válido para poderem ser instaladas em dispositivos Android.

As aplicações encapsuladas podem ser assinadas como parte do processo de encapsulamento ou *após* o encapsulamento através das ferramentas de assinatura existentes (todas as informações sobre a assinatura na aplicação anteriores ao encapsulamento serão eliminadas). Se possível, as informações sobre a assinatura que já foram utilizadas durante o processo de criação devem ser utilizadas durante o encapsulamento. Em certas organizações, tal poderá exigir que trabalhe com o proprietário das informações de armazenamento de chaves (por exemplo, a equipa de desenvolvimento da aplicação). 

Se o certificado de assinatura não puder ser utilizado ou a aplicação não tiver sido implementada antes, pode criar um novo certificado de assinatura ao seguir as instruções no [Guia para Programadores Android](https://developer.android.com/studio/publish/app-signing.html#signing-manually).

Se a aplicação já tiver sido implementada anteriormente com um certificado de assinatura diferente, não poderá ser carregada para o Intune após a atualização. Os cenários de atualização da aplicação serão interrompidos se a aplicação for assinada com um certificado diferente daquele com que foi criada. Como tal, todos os novos certificados de assinatura devem ser mantidos para as atualizações de aplicações. 

## <a name="security-considerations-for-running-the-app-wrapping-tool"></a>Considerações de segurança para executar a Ferramenta de Encapsulamento de Aplicações
Para impedir potenciais ataques de spoofing, divulgação de informações e ataques de elevação de privilégios:

- Certifique-se de que a aplicação de linha de negócio de entrada (LOB), a aplicação de saída e a Java KeyStore se encontram no mesmo computador Windows onde é executada a Ferramenta de Encapsulamento de Aplicações.

- Importe a aplicação de saída para o Intune no computador onde a ferramenta está a ser executada. Veja [keytool](https://docs.oracle.com/javase/8/docs/technotes/tools/unix/keytool.html) para obter mais informações sobre a ferramenta de chave Java.

- Se a aplicação de saída e a ferramenta estiverem num caminho UNC (Universal Naming Convention), mas não estiver a executar a ferramenta e os ficheiros de entrada no mesmo computador, configure o ambiente de forma a torná-lo seguro com a [Segurança IPsec](https://wikipedia.org/wiki/IPsec) ou a [assinatura do protocolo SMB (Server Message Block)](https://support.microsoft.com/kb/887429).

- Certifique-se de que a aplicação vem de uma origem fidedigna.

- Proteja o diretório de saída que tem a aplicação encapsulada. Considere utilizar um diretório de nível de utilizador para a saída.

## <a name="see-also"></a>Consulte também
- [Decidir como preparar as aplicações para a gestão de aplicações móveis com o Microsoft Intune](../developer/apps-prepare-mobile-application-management.md)

- [Guia para programadores do SDK da Aplicação do Microsoft Intune para Android](../developer/app-sdk-android.md)
