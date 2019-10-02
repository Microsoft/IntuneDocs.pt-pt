---
title: Sideload aplicativos Windows e Windows Phone
titleSuffix: Microsoft Intune
description: Saiba como assinar aplicações de linha empresarial de forma a poder utilizar o Intune para as implementar.
keywords: ''
author: erikre
ms.author: erikre
manager: dougeby
ms.date: 09/24/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: e44f1756-52e1-4ed5-bf7d-0e80363a8674
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: c1d039d5be449d1c1b8cc13e69b84e1bd7f7dd2b
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71731288"
---
# <a name="sign-line-of-business-apps-so-they-can-be-deployed-to-windows-devices-with-intune"></a>Assine aplicações de linha de negócio para que possam ser implementadas nos dispositivos Windows com o Intune

[!INCLUDE [both-portals](../../intune-classic/includes/note-for-both-portals.md)]

Como administrador do Intune, você pode implantar aplicativos universais de linha de negócios (LOB) para Windows 8.1 desktop ou Windows 10 desktop & dispositivos móveis, incluindo o aplicativo Portal da Empresa. Para implantar aplicativos. Appx no Windows 8.1 desktop ou no Windows 10 desktop & dispositivos móveis, você pode usar o certificado de assinatura de código de uma autoridade de certificação pública já confiável por seus dispositivos Windows ou pode usar sua própria autoridade de certificação.

 > [!NOTE]
 > Windows 8.1 Desktop requer uma política corporativa para habilitar o Sideload ou o uso de chaves de Sideload (habilitadas automaticamente para dispositivos ingressados no domínio). Para obter mais informações, consulte [Sideload do Windows 8](https://blogs.technet.microsoft.com/scd-odtsp/2012/09/27/windows-8-sideloading-requirements-from-technet/).

## <a name="windows-10-sideloading"></a>Sideload do Windows 10

No Windows 10, o Sideload é diferente em versões anteriores do Windows:

- Você pode desbloquear um dispositivo para Sideload usando uma política corporativa. O Intune fornece uma política de configuração de dispositivo chamada "instalação de aplicativo confiável". Definir isso como <allow> é tudo o que é necessário para dispositivos que já confiam no certificado usado para assinar o aplicativo AppX.

- Os certificados de telefone da Symantec e as chaves de licença de Sideload não são necessários. No entanto, se uma autoridade de certificação local não estiver disponível, talvez seja necessário obter um certificado de assinatura de código de uma autoridade de certificação pública. Para obter mais informações, consulte [introdução à assinatura de código](https://docs.microsoft.com/windows/desktop/SecCrypto/cryptography-tools#introduction-to-code-signing).

### <a name="code-sign-your-app"></a>Assinar o código do seu aplicativo

A primeira etapa é assinar o código do seu pacote Appx. Para obter detalhes, consulte [assinar o pacote do aplicativo usando Signtool](https://docs.microsoft.com/windows/uwp/packaging/sign-app-package-using-signtool).

### <a name="upload-your-app"></a>Carregar seu aplicativo

Em seguida, você deve carregar o arquivo Appx assinado. Para obter detalhes, consulte [Adicionar um aplicativo de linha de negócios do Windows para Microsoft Intune](lob-apps-windows.md).

Se você implantar o aplicativo conforme necessário para usuários ou dispositivos, não precisará do aplicativo Inutne Portal da Empresa. No entanto, se você implantar o aplicativo como disponível para os usuários, eles poderão usar o aplicativo Portal da Empresa da Microsoft Store pública, usar o aplicativo Portal da Empresa do Microsoft Store particular para empresas ou você precisará assinar e implantar manualmente a empresa do Intune Aplicativo do Portal.

### <a name="upload-the-code-signing-certificate"></a>Carregar o certificado de assinatura de código

Se o seu dispositivo Windows 10 ainda não confiar na autoridade de certificação, depois de assinar o pacote Appx e carregá-lo no serviço do Intune, você precisará carregar o certificado de assinatura de código no portal do Intune:
1. Clique em aplicativos cliente
2. Clique em certificados corporativos do Windows
3. Selecione ' selecionar um arquivo ' em certificado de assinatura de código
4. Selecione o arquivo. cer e clique em carregar

Agora, qualquer dispositivo Windows 10 desktop & Mobile com uma implantação Appx pelo serviço Intune baixará automaticamente o certificado corporativo correspondente e o aplicativo poderá ser iniciado após a instalação.

O Intune implanta apenas o arquivo. cer mais recente que foi carregado. Se você tiver vários arquivos Appx criados por diferentes desenvolvedores que não estão associados à sua organização, será necessário fazer com que eles forneçam arquivos Appx não assinados para assinatura com seu certificado ou forneçam a eles o certificado de assinatura de código usado pelo sua organização.

## <a name="how-to-renew-the-symantec-enterprise-code-signing-certificate"></a>Como renovar o certificado empresarial de assinatura com código da Symantec

O certificado usado para implantar Windows Phone aplicativos móveis 8,1 foi descontinuado em 28 2019 de fevereiro e não está mais disponível para renovação da Symantec. Se você estiver implantando no WIndows 10 Mobile, poderá continuar a usar os certificados de assinatura de código do Symantec Desktop Enterprise seguindo as instruções de [Sideload do Windows 10](app-sideload-windows.md#windows-10-sideloading) .

## <a name="how-to-install-the-updated-certificate-for-line-of-business-lob-apps"></a>Como instalar o certificado atualizado para aplicações de linha de negócio (LOB)

Windows Phone 8.1

O serviço do Intune não poderá mais implantar aplicativos LOB para essa plataforma depois que o certificado de assinatura de código existente do Symantec Mobile Enterprise expirar. Ainda será possível Sideload arquivos XAP/APPX não assinados usando um cartão SD ou baixando o arquivo para o dispositivo. Para obter mais informações, consulte [como instalar arquivos XAP no Windows Phone](https://answers.microsoft.com/en-us/mobiledevices/forum/mdlumia-mdapps/how-to-install-xap-file-in-windows-phone-8/da09ee72-51ae-407c-9b85-bc148df89280).

Windows 8.1 desktop/Windows 10 desktop & Mobile

Se o período de certificado tiver expirado, os arquivos Appx poderão parar de ser iniciados. Você deve obter um novo arquivo. cer e seguir as instruções para assinar o código de cada arquivo Appx implantado e carregar novamente todos os arquivos Appx e o arquivo. cer atualizado na seção certificados empresariais do Windows do portal do Intune

## <a name="manually-deploy-windows-10-company-portal-app"></a>Implementar manualmente a aplicação Portal da Empresa do Windows 10
Se você não quiser fornecer acesso ao Microsoft Store, poderá implantar manualmente o aplicativo do Windows 10 Portal da Empresa diretamente do Intune, mesmo se não tiver integrado o Intune com o Microsoft Store for Business (MSFB). Como alternativa, se você tiver integrado, poderá implantar o aplicativo Portal da Empresa usando [implantar aplicativos usando o MSFB](store-apps-windows.md).

 > [!NOTE]
 > Esta opção precisará da implementação das atualizações manuais sempre que uma atualização da aplicação for disponibilizada.

1. Entre em sua conta no [Microsoft Store for Business](https://www.microsoft.com/business-store) e adquira a versão de **licença offline** do aplicativo portal da empresa.  
2. Assim que a aplicação tiver sido comprada, selecione a aplicação na página **Inventário**.  
3. Selecione **Todos os dispositivos Windows 10** como a **Plataforma** e, em seguida, a **Arquitetura** adequada e transfira. Não é preciso um ficheiro de licença de aplicação para esta aplicação.
   ![Imagem dos detalhes do pacote do Windows 10 x86 para download](./media/app-sideload-windows/Win10CP-all-devices.png)
4. Transfira todos os pacotes em “Arquiteturas necessárias”. Esta ação deve ser feita para as arquiteturas x86, x64 e ARM, resultando num total de nove pacotes, conforme mostrado abaixo.

   ![Imagem dos ficheiros de dependência para Transferência ](./media/app-sideload-windows/Win10CP-dependent-files.png)
5. Antes de carregar a aplicação Portal da Empresa para o Intune, crie uma pasta (por exemplo, C:\Portal da Empresa) com os pacotes estruturados da seguinte forma:
   1. Coloque o pacote do Portal da Empresa na pasta C:\Portal da Empresa. Crie também uma subpasta Dependências nesta localização.  
      ![Imagem da pasta Dependências guardada com o ficheiro APPXBUN](./media/app-sideload-windows/Win10CP-Dependencies-save.png)
   2. Coloque os nove pacotes de dependências na pasta Dependências.  
      Se as dependências não forem colocadas neste formato, o Intune não poderá reconhecê-los e carregá-los durante o carregamento do pacote, o que fará com que o carregamento falhe com o seguinte erro.  
      ![Mensagem de erro-a dependência de aplicativo do Windows deve ser fornecida.](./media/app-sideload-windows/Win10CP-error-message.png)
6. Volte ao Intune e, em seguida, carregue a aplicação Portal da Empresa como uma nova aplicação. Implemente-a como uma aplicação obrigatória para o conjunto de utilizadores de destino pretendido.  

Para obter mais informações sobre como o Intune processa as dependências de aplicações Universais, veja [Deploying an appxbundle with dependencies via Microsoft Intune MDM (Implementar um appxbundle com dependências através da MDM do Microsoft Intune) ](https://blogs.technet.microsoft.com/configmgrdogs/2016/11/30/deploying-an-appxbundle-with-dependencies-via-microsoft-intune-mdm/).  

### <a name="how-do-i-update-the-company-portal-on-my-users-devices-if-they-have-already-installed-the-older-apps-from-the-store"></a>Como atualizo o Portal da Empresa nos dispositivos dos meus utilizadores se já tiverem instalado as aplicações mais antigas da loja?
Se os utilizadores já tiverem instalado as aplicações Portal da Empresa do Windows 8.1 ou Windows Phone 8.1 a partir da Loja, estas deverão ser atualizadas automaticamente para a nova versão sem ser preciso realizar qualquer ação da sua parte ou do utilizador. Se a atualização não ocorrer, peça aos utilizadores para verificarem se ativaram as atualizações automáticas para as aplicações da Loja nos dispositivos.   

### <a name="how-do-i-upgrade-my-sideloaded-windows-81-company-portal-app-to-the-windows-10-company-portal-app"></a>Como atualizo a minha aplicação Portal da Empresa do Windows 8.1 de sideload para a aplicação Portal da Empresa do Windows 10?
O nosso caminho de migração recomendado consiste em eliminar a implementação da aplicação Portal da Empresa do Windows 8.1 através da definição da ação de implementação como “Desinstalar”. Em seguida, a aplicação Portal da Empresa do Windows 10 pode ser implementada através de qualquer uma das opções acima.  

Se precisar de carregar a aplicação em sideload e tiver implementado o Portal da Empresa do Windows 8.1 sem a assinar com o Certificado da Symantec, siga os passos na secção Implementar diretamente através do Intune acima para concluir a atualização.

Se precisar de carregar a aplicação em sideload e tiver assinado e implementado o Portal da Empresa do Windows 8.1 com o certificado de assinatura de código da Symantec, siga os passos da secção abaixo.  

### <a name="how-do-i-upgrade-my-signed-and-sideloaded-windows-phone-81-company-portal-app-or-windows-81-company-portal-app-to-the-windows-10-company-portal-app"></a>Como atualizo a minha aplicação Portal da Empresa do Windows Phone 8.1 ou do Windows 8.1 de sideload e assinada para a aplicação Portal da Empresa do Windows 10?
O nosso caminho de migração recomendado consiste em eliminar a implementação existente da aplicação Portal da Empresa do Windows Phone 8.1 ou do Windows 8.1 através da definição da ação de implementação como “Desinstalar”. Em seguida, a aplicação Portal da Empresa do Windows 10 poderá ser implementada normalmente.  

Caso contrário, a aplicação Portal da Empresa do Windows 10 terá de ser corretamente atualizada e assinada para garantir que o caminho de atualização é respeitado.  

Se a aplicação Portal da Empresa do Windows 10 estiver assinada e implementada desta forma, terá de repetir este processo para cada nova atualização de aplicação disponibilizada na loja. A aplicação não será automaticamente atualizada quando a loja é atualizada.  

Veja a seguir como pode assinar e implementar a aplicação desta forma:

1. Transfira o Script de Assinatura da Aplicação Portal da Empresa do Windows 10 do Microsoft Intune a partir de [https://aka.ms/win10cpscript](https://aka.ms/win10cpscript).  Este script requer que o Windows SDK para o Windows 10 esteja instalado no computador anfitrião. Para transferir o Windows SDK para Windows 10, aceda a [https://go.microsoft.com/fwlink/?LinkId=619296](https://go.microsoft.com/fwlink/?LinkId=619296).
2. Transfira a aplicação Portal da Empresa do Windows 10 na Loja Microsoft para Empresas, conforme detalhado acima.  
3. Execute o script com os parâmetros de entrada detalhados no cabeçalho do script para assinar a aplicação Portal da Empresa do Windows 10 (extraída abaixo). As dependências não precisam de ser transmitidas para o script. Só são precisas quando a aplicação está a ser carregada para a Consola de Administração do Intune.

|       Parâmetro       |                                                                    Descrição                                                                    |
|-----------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|
| InputWin10AppxBundle  |                                             O caminho onde está localizado o ficheiro appxbundle de origem.                                              |
| OutputWin10AppxBundle |                                                  O caminho de saída do ficheiro appxbundle assinado.                                                  |
|       Win81Appx       |                          O caminho onde o ficheiro do Portal da Empresa Windows 8.1 ou Windows Phone 8.1 (.APPX) está localizado.                           |
|      PfxFilePath      |                                   O caminho do ficheiro Certificado de Assinatura de Código de Dispositivo Móvel Empresarial da Symantec (.PFX).                                    |
|      PfxPassword      |                                     A palavra-passe do Certificado de Assinatura de Código de Dispositivo Móvel Empresarial da Symantec.                                      |
|      PublisherId      |      O ID de Publicador da empresa. Se estiver ausente, é utilizado o campo "Assunto" do Certificado de Assinatura de Código de Dispositivo Móvel Empresarial da Symantec.       |
|        SdkPath        | O caminho da pasta raiz do Windows SDK para Windows 10. Este argumento é opcional e assume a predefinição de ${env:ProgramFiles(x86)}\Windows Kits\10 |

O script irá transmitir a versão assinada da aplicação Portal da Empresa do Windows 10 após a respetiva execução. Em seguida, pode implementar a versão assinada da aplicação como uma aplicação de LOB através do Intune, que irá atualizar as versões atualmente implementadas para esta aplicação nova.  
