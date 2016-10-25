---
title: "Encapsular aplicações Android com a Ferramenta de Encapsulamento de Aplicações | Microsoft Intune"
description: "Utilize as informações neste tópico para saber como pode encapsular as suas aplicações Android sem modificar os próprios códigos. Prepare as aplicações para que possa aplicar políticas de gestão de aplicações móveis."
keywords: 
author: karthikaraman
ms.author: karaman
manager: angrobe
ms.date: 09/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e9c349c8-51ae-4d73-b74a-6173728a520b
ms.reviewer: oldang
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: fe3a9f2fd9ce9a3c3f776dcfd9ad3347a63d0fc1
ms.openlocfilehash: e623755cf926020bcb66d8a6d40e5cce9b46b0ae


---

# Preparar as aplicações Android para gestão de aplicações móveis com a Ferramenta de Encapsulamento de Aplicações do Intune
Utilize a **Ferramenta de Encapsulamento de Aplicações do Microsoft Intune para Android** para modificar o comportamento das suas aplicações Android internas ao restringir funcionalidades da aplicação sem alterar o código da aplicação em si.

A ferramenta é uma aplicação de linha de comandos do Windows executada no PowerShell, que cria um "encapsulamento" em torno da aplicação Android. Quando a aplicação estiver encapsulada, pode alterar a funcionalidade da aplicação ao configurar [políticas de gestão de aplicações móveis](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md) no Intune.


Antes de executar a ferramenta, consulte as [Considerações de segurança para executar a ferramenta de encapsulamento de aplicações](#security-considerations-for-running-the-app-wrapping-tool). Para transferir a ferramenta, aceda à [Ferramenta de Encapsulamento de Aplicações do Microsoft Intune para Android](https://github.com/msintuneappsdk/intune-app-wrapping-tool-android) no GitHub.



## Passo 1: cumprir os pré-requisitos de utilização da ferramenta de encapsulamento de aplicações

-   Tem de executar a ferramenta de encapsulamento de aplicações num computador Windows com o Windows 7 ou posterior.

-   A aplicação de entrada tem de ser um pacote de aplicação Android válido com a extensão de ficheiro **.apk** e:

    -   Não pode ser encriptada

    -   Não pode ter sido encapsulada anteriormente pela Ferramenta de Encapsulamento de Aplicações
    -   Tem de ter sido escrita para Android 4.0 ou posterior

-   A aplicação tem de ter sido programada pela sua empresa ou para a mesma. Não pode utilizar esta ferramenta em aplicações transferidas a partir da Google Play Store.

-   Para executar a ferramenta de encapsulamento de aplicações, tem de instalar a versão mais recente do [Ambiente de Tempo de Execução Java](http://java.com/download/) e, em seguida, certificar-se de que a variável de caminho Java foi definida como **C:\ProgramData\Oracle\Java\javapath** nas variáveis do seu ambiente do Windows. Para obter mais ajuda, consulte a [documentação do Java](http://java.com/download/help/).

    > [!NOTE]
    > Nalguns casos, a versão de 32 bits do Java pode originar problemas de memória. Recomendamos que instale a versão de 64 bits.

- O Android exige que todos os pacotes de aplicação (.apks) sejam assinados. Utilize a Ferramenta de Chave Java para gerar as credenciais necessárias para assinar a aplicação de saída encapsulada. Por exemplo, o comando abaixo utiliza o executável Java **keytool.exe** para gerar chaves que podem ser utilizadas pela ferramenta de encapsulamento de aplicações para assinar a aplicação de saída encapsulada.

    ```
    keytool.exe -genkeypair -v -keystore mykeystorefile -alias mykeyalias -keyalg RSA -keysize 2048 -validity 50000
    ```
    Este exemplo gera um par de chaves (uma chave pública e uma chave privada associada com 2048-bits de tamanho) através do algoritmo RSA e, em seguida, encapsula a chave pública num certificado X.509 v3 autoassinado, que é armazenado como uma cadeia de certificado de elemento único. Esta cadeia de certificado e a chave privada são armazenadas numa nova entrada de keystore denominada "mykeystorefile" e identificada pelo alias "mykeyalias." A entrada de keystore é válida durante 50 000 dias.

    O comando irá pedir-lhe para fornecer palavras-passe para a chave e para a keystore. Utilize palavras-passe seguras e difíceis de adivinhar mas das quais se lembre, uma vez que irá precisar delas mais tarde para executar a ferramenta de encapsulamento de aplicações.

    Para obter documentação detalhada, leia mais acerca da [keytool](http://docs.oracle.com/javase/6/docs/technotes/tools/windows/keytool.html) de Java e da [KeyStore](https://docs.oracle.com/javase/7/docs/api/java/security/KeyStore.html) de Java no site de documentação da Oracle.

## Passo 2: instalar a ferramenta de encapsulamento de aplicações

1.  A partir do [repositório GitHub ](https://github.com/msintuneappsdk/intune-app-wrapping-tool-android), transfira e abra o ficheiro de instalação **InstallAWT.exe** da Ferramenta de Encapsulamento do Intune para Android num computador Windows.

2.  Aceite o contrato de licença e conclua a instalação.

Não se esqueça da pasta na qual instalou a ferramenta. A localização predefinida é: **C:\Program Files (x86)\Microsoft Intune Mobile Application Management\Android\App Wrapping Tool**.

## Passo 3: executar a ferramenta de encapsulamento de aplicações

1.  No computador Windows onde instalou a ferramenta de encapsulamento de aplicações, abra uma janela do PowerShell no modo de administrador.

2.  Na pasta onde instalou a ferramenta, importe o módulo do PowerShell da ferramenta de encapsulamento de aplicações:

    ```
    Import-Module .\IntuneAppWrappingTool.psm1
    ```

3.  Execute a ferramenta utilizando o comando **invoke-AppWrappingTool** cuja sintaxe de utilização está indicada abaixo:
    ```
    Invoke-AppWrappingTool [-InputPath] <String> [-OutputPath] <String> -KeyStorePath <String> -KeyStorePassword <SecureString>
    -KeyAlias <String> -KeyPassword <SecureString> [-SigAlg <String>] [<CommonParameters>]
    ```

 A seguinte tabela explica detalhadamente as propriedades do comando **invoke-AppWrappingTool**:

|Propriedade|Informações|Exemplo|
|-------------|--------------------|---------|
|**-InputPath**&lt;String&gt;|Caminho da aplicação Android de origem (.apk).| |
|**-OutputPath**&lt;String&gt;|Caminho para a aplicação Android de "saída". Se este for o mesmo caminho de diretório como o InputPath, o empacotamento irá falhar.| |
|**-KeyStorePath**&lt;String&gt;|Caminho para o ficheiro de keystore que contém o par de chaves pública/privada para assinatura.|Por predefinição, os ficheiros de keystore são armazenados em "C:\Program Files (x86)\Java\jreX.X.X_XX\bin." |
|**-KeyStorePassword**&lt;SecureString&gt;|Palavra-passe utilizada para desencriptar o keystore. O Android requer que todos os pacotes de aplicações (. apk) estejam assinados. Utilize a Ferramenta de Chave Java para gerar a KeyStorePassword. Leia mais acerca da [keystore](https://docs.oracle.com/javase/7/docs/api/java/security/KeyStore.html) de Java aqui.| |
|**-KeyAlias**&lt;String&gt;|Nome da chave a ser utilizada para assinatura.| |
|**-KeyPassword**&lt;SecureString&gt;|Palavra-passe utilizada para desencriptar a chave privada que vai ser utilizada para assinatura.| |
|**-SigAlg**&lt;SecureString&gt;| (Opcional) O nome do algoritmo de assinatura a ser utilizado na assinatura. O algoritmo tem de ser compatível com a chave privada.|Exemplos: SHA256withRSA, SHA1withRSA, MD5withRSA|
| **&lt;CommonParameters&gt;** | (Opcional) O comando suporta parâmetros comuns do PowerShell, por exemplo, verboso, depuração, etc. |


- Para obter uma lista de parâmetros comuns, consulte o [Centro de Scripts da Microsoft](https://technet.microsoft.com/library/hh847884.aspx).

- Para ver informações de utilização detalhadas da ferramenta, introduza o comando:

    ```
    Help Invoke-AppWrappingTool
    ```

**Exemplo:**

Importe o módulo PowerShell.
```
Import-Module "C:\Program Files (x86)\Microsoft Intune Mobile Application Management\Android\App Wrapping Tool\IntuneAppWrappingTool.psm1" 
```
Execute a ferramenta de encapsulamento de aplicação na aplicação nativa **HelloWorld.apk**. 
```
invoke-AppWrappingTool -InputPath .\app\HelloWorld.apk -OutputPath .\app_wrapped\HelloWorld_wrapped.apk -KeyStorePath "C:\Program Files (x86)\Java\jre1.8.0_91\bin\mykeystorefile" -keyAlias mykeyalias -SigAlg SHA1withRSA -Verbose
```

Ser-lhe-ão solicitadas a **KeyStorePassword** e a **KeyPassword**. Introduza as credenciais que utilizou para criar o ficheiro de keystore.

A aplicação encapsulada é gerada e guardada juntamente com um ficheiro de registo no caminho de saída que tiver especificado.

## Considerações de segurança para executar a ferramenta de encapsulamento de aplicações
Para impedir potenciais ataques de spoofing, divulgação de informações e ataques de elevação de privilégios:

-   Certifique-se de que a aplicação de linha de negócio de entrada (LOB), a aplicação de saída e a Java KeyStore se encontram no mesmo computador Windows onde é executada a ferramenta de encapsulamento de aplicações.

-   Importe a aplicação de saída para a consola do Intune no computador onde a ferramenta está a ser executada. Veja [keytool](https://docs.oracle.com/javase/8/docs/technotes/tools/unix/keytool.html) para obter mais informações sobre o Java keytool.

-   Se a aplicação de saída e a ferramenta estiverem num caminho UNC (Universal Naming Convention), mas não estiver a executar a ferramenta e os ficheiros de entrada no mesmo computador, configure o ambiente de forma a torná-lo seguro com a [Segurança IPsec](http://en.wikipedia.org/wiki/IPsec) ou a [assinatura do protocolo SMB (Server Message Block)](https://support.microsoft.com/en-us/kb/887429).

-   Certifique-se de que a aplicação vem de uma origem fidedigna.

-   Proteja o diretório de saída que contém a aplicação encapsulada. Considere utilizar um diretório de nível de utilizador para a saída.



### Consulte também
- [Decidir como preparar as aplicações para a gestão de aplicações móveis com o Microsoft Intune](decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune.md)

- [Utilizar o SDK para ativar aplicações para gestão de aplicações móveis](use-the-sdk-to-enable-apps-for-mobile-application-management.md)



<!--HONumber=Oct16_HO2-->


