---
title: Aplicativos Sideload Windows e Windows Phone
titleSuffix: Microsoft Intune
description: Saiba como assinar aplicações de linha empresarial de forma a poder utilizar o Intune para as implementar.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/23/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: e44f1756-52e1-4ed5-bf7d-0e80363a8674
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 03b8f050dc6232b87d1149aff0a93cd7b06839cd
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/26/2020
ms.locfileid: "76755413"
---
# <a name="sign-line-of-business-apps-so-they-can-be-deployed-to-windows-devices-with-intune"></a>Assine aplicações de linha de negócio para que possam ser implementadas nos dispositivos Windows com o Intune

Como administrador intune, pode implementar aplicações universais de linha de negócio (LOB) para o Windows 8.1 Desktop ou dispositivos Windows 10 Desktop & Mobile, incluindo a aplicação Portal da Empresa. Para implementar *aplicações .appx* para windows 8.1 Desktop ou Windows 10 Desktop & Mobile dispositivos, pode utilizar um certificado de assinatura de código a partir de uma autoridade de certificação pública já confiada pelos seus dispositivos Windows, ou pode utilizar a sua própria autoridade de certificados.

 > [!NOTE]
 > O Windows 8.1 Desktop requer uma política da empresa que permita a sideloading ou a utilização de Teclas de carregamento lateral (ativadas automaticamente para dispositivos de domínio). Para mais informações, consulte [o Windows 8 sideloading](https://blogs.technet.microsoft.com/scd-odtsp/2012/09/27/windows-8-sideloading-requirements-from-technet/).

## <a name="windows-10-sideloading"></a>Carga lateral do Windows 10

No Windows 10, o sideloading é diferente do que nas versões anteriores do Windows:

- Pode desbloquear um dispositivo para asideloading utilizando uma política de empresa. Intune fornece uma política de config de dispositivo chamada "Instalação de aplicações fidedignas". Defini-lo para <allow> é tudo o que é necessário para dispositivos que já confiam no certificado usado para assinar a app appx.

- Não são necessários certificados telefónicos symantec e chaves de licença de carregamento lateral. No entanto, se não estiver disponível uma autoridade de certificados no local, poderá ter de obter um certificado de assinatura de código junto de uma autoridade de certificação pública. Para mais informações, consulte [Introdução à Assinatura de Código](https://docs.microsoft.com/windows/desktop/SecCrypto/cryptography-tools#introduction-to-code-signing).

### <a name="code-sign-your-app"></a>Código assine a sua aplicação

O primeiro passo é codificar o seu pacote appx. Para mais detalhes, consulte o [pacote de aplicativos Sign usando signTool](https://docs.microsoft.com/windows/uwp/packaging/sign-app-package-using-signtool).

### <a name="upload-your-app"></a>Faça upload da sua aplicação

Em seguida, tem de carregar o ficheiro appx assinado. Para mais detalhes, consulte [Adicionar uma aplicação de linha de negócio do Windows ao Microsoft Intune](lob-apps-windows.md).

Se implementar a aplicação conforme necessário aos utilizadores ou dispositivos, então não precisa da aplicação Portal da Empresa Inutne. No entanto, se implementar a aplicação como disponível para os utilizadores, poderá utilizar a aplicação Portal da Empresa a partir da Public Microsoft Store, utilizar a aplicação Portal da Empresa a partir da Loja Privada da Microsoft para negócios, ou terá de assinar e implementar manualmente a Intune Company Aplicativo portal.

### <a name="upload-the-code-signing-certificate"></a>Faça upload do certificado de assinatura de código

Se o seu dispositivo Windows 10 ainda não confiar na autoridade do certificado, depois de ter assinado o seu pacote appx e o ter enviado para o serviço Intune, tem de enviar o certificado de assinatura de código para o portal Intune:

1. Entre no centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Clique na **administração do Inquilino** > **Conectores e fichas** > **empresa do Windows certifcates**.
3. Selecione um ficheiro sob **o ficheiro de certificado de assinatura de Código**.
4. Selecione o ficheiro *.cer* e clique em **Abrir**.
5. Clique em **Carregar** para adicionar o seu ficheiro de certificado ao Intune.

Agora, qualquer dispositivo Windows 10 Desktop & Mobile com uma implementação de appx pelo serviço Intune irá automaticamente descarregar o certificado de empresa correspondente e a aplicação será autorizada a ser lançada após a instalação.

Intune apenas implementa o mais recente ficheiro .cer que foi carregado. Se tiver vários ficheiros appx criados por diferentes desenvolvedores que não estejam associados à sua organização, então terá de os ter a fornecer ficheiros appx não assinados para assinar com o seu certificado, ou fornecer-lhes o certificado de assinatura de código utilizado por sua organização.

## <a name="how-to-renew-the-symantec-enterprise-code-signing-certificate"></a>Como renovar o certificado empresarial de assinatura com código da Symantec

O certificado utilizado para implementar aplicações móveis Windows Phone 8.1 foi descontinuado em 28 de fevereiro de 2019 e já não está disponível para renovação da Symantec. Se estiver a implementar o dispositivo WIndows 10, pode continuar a utilizar certificados de assinatura de código Symantec Desktop Enterprise seguindo as instruções de [sideloading do Windows 10.](app-sideload-windows.md#windows-10-sideloading)

## <a name="how-to-install-the-updated-certificate-for-line-of-business-lob-apps"></a>Como instalar o certificado atualizado para aplicações de linha de negócio (LOB)

Wnodows Phone 8.1

O serviço Intune já não pode implementar aplicações LOB para esta plataforma uma vez que o certificado de assinatura de código Symantec Mobile Enterprise existente expira. Ainda será possível carregar ficheiros XAP/APPX não assinados utilizando um cartão SD ou descarregando o ficheiro para o dispositivo. Para mais informações, consulte [como instalar ficheiros XAP no Windows Phone](https://answers.microsoft.com/en-us/mobiledevices/forum/mdlumia-mdapps/how-to-install-xap-file-in-windows-phone-8/da09ee72-51ae-407c-9b85-bc148df89280).

Windows 8.1 Desktop/Windows 10 Desktop & Mobile

Se o período cert tiver expirado, os ficheiros appx podem parar de ser lançados. Deve obter um novo ficheiro .cer e seguir as instruções para assinar código sintetizado cada ficheiro appx implementado e recarregar todos os ficheiros appx e o ficheiro .cer atualizado para a secção de Certificados empresariais do Windows do portal Intune

## <a name="manually-deploy-windows-10-company-portal-app"></a>Implementar manualmente a aplicação Portal da Empresa do Windows 10

Se não quiser fornecer acesso à Microsoft Store, pode implementar manualmente a aplicação Portal da Empresa Do Windows 10 diretamente do Intune, mesmo que não tenha integrado o Intune com a Microsoft Store for Business (MSFB). Em alternativa, se se integrou, poderá implementar a aplicação Portal da Empresa utilizando [aplicações de implementação utilizando o MSFB](store-apps-windows.md).

 > [!NOTE]
 > Esta opção precisará da implementação das atualizações manuais sempre que uma atualização da aplicação for disponibilizada.

1. Inscreva-se na sua conta na [Microsoft Store for Business](https://www.microsoft.com/business-store) e adquira a versão de licença **offline** da aplicação Portal da Empresa.  
2. Assim que a aplicação tiver sido comprada, selecione a aplicação na página **Inventário**.  
3. Selecione **Todos os dispositivos Windows 10** como a **Plataforma** e, em seguida, a **Arquitetura** adequada e transfira. Não é preciso um ficheiro de licença de aplicação para esta aplicação.
   imagem ![dos detalhes do pacote Windows 10 X86 para download](./media/app-sideload-windows/Win10CP-all-devices.png)
4. Transfira todos os pacotes em “Arquiteturas necessárias”. Esta ação deve ser feita para as arquiteturas x86, x64 e ARM, resultando num total de nove pacotes, conforme mostrado abaixo.

   ![Imagem dos ficheiros de dependência para Transferência ](./media/app-sideload-windows/Win10CP-dependent-files.png)
5. Antes de carregar a aplicação Portal da Empresa para o Intune, crie uma pasta (por exemplo, C:\Portal da Empresa) com os pacotes estruturados da seguinte forma:
   1. Coloque o pacote do Portal da Empresa na pasta C:\Portal da Empresa. Crie também uma subpasta Dependências nesta localização.  
      ![Imagem da pasta Dependências guardada com o ficheiro APPXBUN](./media/app-sideload-windows/Win10CP-Dependencies-save.png)
   2. Coloque os nove pacotes de dependências na pasta Dependências.  
      Se as dependências não forem colocadas neste formato, o Intune não poderá reconhecê-los e carregá-los durante o carregamento do pacote, o que fará com que o carregamento falhe com o seguinte erro.  
      <img alt="Error message - The Windows app dependency must be provided." src="./media/app-sideload-windows/Win10CP-error-message.png" width="200">
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

|       Parâmetro       |                                                                    Description                                                                    |
|-----------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|
| InputWin10AppxBundle  |                                             O caminho onde está localizado o ficheiro appxbundle de origem.                                              |
| OutputWin10AppxBundle |                                                  O caminho de saída do ficheiro appxbundle assinado.                                                  |
|       Win81Appx       |                          O caminho onde o ficheiro do Portal da Empresa Windows 8.1 ou Windows Phone 8.1 (.APPX) está localizado.                           |
|      PfxFilePath      |                                   O caminho do ficheiro Certificado de Assinatura de Código de Dispositivo Móvel Empresarial da Symantec (.PFX).                                    |
|      PfxPassword      |                                     A palavra-passe do Certificado de Assinatura de Código de Dispositivo Móvel Empresarial da Symantec.                                      |
|      PublisherId      |      O ID de Publicador da empresa. Se estiver ausente, é utilizado o campo "Assunto" do Certificado de Assinatura de Código de Dispositivo Móvel Empresarial da Symantec.       |
|        SdkPath        | O caminho da pasta raiz do Windows SDK para Windows 10. Este argumento é opcional e assume a predefinição de ${env:ProgramFiles(x86)}\Windows Kits\10 |

O script irá transmitir a versão assinada da aplicação Portal da Empresa do Windows 10 após a respetiva execução. Em seguida, pode implementar a versão assinada da aplicação como uma aplicação de LOB através do Intune, que irá atualizar as versões atualmente implementadas para esta aplicação nova.  
