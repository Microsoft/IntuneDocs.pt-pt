---
title: Adicionar manualmente a aplicação Portal da Empresa do Windows 10
titleSuffix: Microsoft Intune
description: Saiba como adicionar manualmente a aplicação Portal da Empresa do Windows 10.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/06/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: bfe1a2d3-f611-4dbb-adef-c0dff4d7b810
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f2c7e449e9931bccd5e736bd09c33e0b42c623e9
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/16/2018
---
# <a name="manually-add-the-windows-10-company-portal-app-using-microsoft-intune"></a>Adicionar manualmente a aplicação Portal da Empresa do Windows 10 com o Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Os utilizadores finais podem instalar a aplicação Portal da Empresa a partir da Loja Microsoft para gerir dispositivos e instalar aplicações. No entanto, se as suas necessidades empresariais incluírem a atribuição da aplicação Portal da Empresa, poderá atribuir manualmente a aplicação Portal da Empresa do Windows 10 diretamente a partir do Intune, mesmo que não tenha integrado o Intune com a Loja Microsoft para Empresas.

 > [!NOTE]
 > Esta opção precisará da atribuição das atualizações manuais sempre que uma atualização da aplicação for disponibilizada.

## <a name="configure-settings-to-show-offline-apps"></a>Configurar definições para mostrar as aplicações offline
1. Aceda a [Microsoft Store para Empresas](https://www.microsoft.com/business-store) e certifique-se de que iniciou sessão com a sua conta de administrador.
2. Selecione o separador **Gerir** perto da parte superior da janela.
3. Selecione **Definições** na coluna de navegação esquerda.
4. Defina **Mostrar aplicações offline** na secção **Experiências de compras** para **Ativado**. Serão apresentadas as aplicações licenciadas offline na Microsoft Store para Empresas.

## <a name="download-the-offline-company-portal-app"></a>Transferir a aplicação offline Portal da Empresa
1. Procure e selecione a aplicação **Portal da Empresa**.
2. Defina o **Tipo de licença** para **Offline**.
3. Clique em **Obter a aplicação** para adquirir e adicionar a aplicação offline Portal da Empresa ao seu inventário.
4. Clique em **Gerir** na página da aplicação **Portal da Empresa**.
5. Selecione **Todos os dispositivos Windows 10** como a **Plataforma** e, em seguida, selecione a **Versão mínima** adequada, a **Arquitetura** e os valores de metadados** da aplicação Transferir. 
6. Clique em **Transferir** para guardar o ficheiro no seu computador local.

    ![Imagem de Todos os dispositivos Windows 10 e detalhes do pacote de Arquitetura X86 para Transferência](./media/Win10CP-all-devices.png)

7. Transfira todos os pacotes em “Arquiteturas necessárias”. Esta ação deve ser feita para as arquiteturas x86, x64 e ARM, resultando num total de doze pacotes.
8. Antes de carregar a aplicação Portal da Empresa para o Intune, crie uma pasta (por exemplo, C:\Portal da Empresa) com os pacotes estruturados da seguinte forma:
   - Coloque o pacote do Portal da Empresa na pasta C:\Portal da Empresa. Crie também uma subpasta Dependências nesta localização.  

     ![Imagem da pasta Dependências guardada com o ficheiro APPXBUN](./media/Win10CP-Dependencies-save.png)

   - Coloque os pacotes de dependências na pasta *Dependências*. 

     > [!NOTE]
     > Se as dependências não forem colocadas no formato correto, o Intune não conseguirá reconhecer e carregar os ficheiros durante o carregamento do pacote, o que fará com que o carregamento falhe e apresente um erro.

9. Regresse ao Microsoft Intune no portal do Azure.
10. Carregue a aplicação Portal da Empresa como uma nova aplicação. Atribua-a como uma aplicação obrigatória para o conjunto de utilizadores visados pretendido.  

Para obter mais informações sobre como o Intune processa as dependências de aplicações Universais, veja [Deploying an appxbundle with dependencies via Microsoft Intune MDM (Implementar um appxbundle com dependências através da MDM do Microsoft Intune) ](https://blogs.technet.microsoft.com/configmgrdogs/2016/11/30/deploying-an-appxbundle-with-dependencies-via-microsoft-intune-mdm/).  

## <a name="how-do-i-update-the-company-portal-on-my-users-devices-if-they-have-already-installed-the-older-apps-from-the-store"></a>Como atualizo o Portal da Empresa nos dispositivos dos meus utilizadores se já tiverem instalado as aplicações mais antigas da loja?
Se os utilizadores já tiverem instalado as aplicações Portal da Empresa do Windows 8.1 ou Windows Phone 8.1 a partir da Loja, estas deverão ser atualizadas automaticamente para a nova versão sem ser preciso realizar qualquer ação da sua parte ou do utilizador. Se a atualização não ocorrer, peça aos utilizadores para verificarem se ativaram as atualizações automáticas para as aplicações da Loja nos dispositivos.   

## <a name="how-do-i-upgrade-my-sideloaded-windows-81-company-portal-app-to-the-windows-10-company-portal-app"></a>Como atualizo a minha aplicação Portal da Empresa do Windows 8.1 de sideload para a aplicação Portal da Empresa do Windows 10?
O nosso caminho de migração recomendado consiste em eliminar a atribuição da aplicação Portal da Empresa do Windows 8.1 através da definição da ação de atribuição como "Desinstalar". Uma vez aplicada esta definição, a aplicação Portal da Empresa do Windows 10 pode ser atribuída através de qualquer uma das opções acima.  

Se precisar de carregar a aplicação em sideload e tiver atribuído o Portal da Empresa do Windows 8.1 sem o assinar com o Certificado da Symantec, siga os passos na secção Atribuir diretamente através do Intune acima para concluir a atualização da versão.

Se precisar de carregar a aplicação em sideload e tiver assinado e atribuído o Portal da Empresa do Windows 8.1 com o certificado de assinatura de código da Symantec, siga os passos da secção abaixo.  

## <a name="how-do-i-upgrade-my-signed-and-sideloaded-windows-phone-81-company-portal-app-or-windows-81-company-portal-app-to-the-windows-10-company-portal-app"></a>Como atualizo a minha aplicação Portal da Empresa do Windows Phone 8.1 ou do Windows 8.1 de sideload e assinada para a aplicação Portal da Empresa do Windows 10?
O nosso caminho de migração recomendado consiste em eliminar a atribuição existente da aplicação Portal da Empresa do Windows Phone 8.1 ou do Windows 8.1 através da definição da ação de atribuição como “Desinstalar”. Uma vez aplicada esta definição, a aplicação Portal da Empresa do Windows 10 pode ser atribuída normalmente.  

Caso contrário, a aplicação Portal da Empresa do Windows 10 terá de ser corretamente atualizada e assinada para garantir que o caminho de atualização é respeitado.  

Se a aplicação Portal da Empresa do Windows 10 estiver assinada e atribuída desta forma, terá de repetir este processo para cada nova atualização de aplicação disponibilizada na loja. A aplicação não será automaticamente atualizada quando a loja é atualizada.  

Veja a seguir como pode assinar e atribuir a aplicação desta forma:

1. Transfira o Script de Assinatura da Aplicação Portal da Empresa do Windows 10 do Microsoft Intune a partir de [https://aka.ms/win10cpscript](https://aka.ms/win10cpscript).  Este script requer que o Windows SDK para o Windows 10 esteja instalado no computador anfitrião. Para transferir o Windows SDK para Windows 10, aceda a [https://go.microsoft.com/fwlink/?LinkId=619296](https://go.microsoft.com/fwlink/?LinkId=619296).
2. Transfira a aplicação Portal da Empresa do Windows 10 na Loja Microsoft para Empresas, conforme detalhado acima.  
3. Execute o script com os parâmetros de entrada detalhados no cabeçalho do script para assinar a aplicação Portal da Empresa do Windows 10 (extraída abaixo). As dependências não precisam de ser transmitidas para o script. Só são precisas quando a aplicação está a ser carregada para a Consola de Administração do Intune.

|       Parâmetro       |                                                                        Descrição                                                                        |
|-----------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|
| InputWin10AppxBundle  |                                                  O caminho onde está localizado o ficheiro appxbundle de origem                                                  |
| OutputWin10AppxBundle | O caminho de saída do ficheiro appxbundle assinado.  Win81Appx O caminho onde o ficheiro do Portal da Empresa Windows 8.1 ou Windows Phone 8.1 (.APPX) está localizado. |
|      PfxFilePath      |                                       O caminho do ficheiro Certificado de Assinatura de Código de Dispositivo Móvel Empresarial da Symantec (.PFX).                                        |
|      PfxPassword      |                                         A palavra-passe do Certificado de Assinatura de Código de Dispositivo Móvel Empresarial da Symantec.                                          |
|      PublisherId      |          O ID de Publicador da empresa. Se estiver ausente, é utilizado o campo "Assunto" do Certificado de Assinatura de Código de Dispositivo Móvel Empresarial da Symantec.           |
|        SdkPath        |     O caminho da pasta raiz do Windows SDK para Windows 10. Este argumento é opcional e assume a predefinição de ${env:ProgramFiles(x86)}\Windows Kits\10     |

O script irá transmitir a versão assinada da aplicação Portal da Empresa do Windows 10 após a respetiva execução. Em seguida, pode atribuir a versão assinada da aplicação como uma aplicação LOB através do Intune, que irá atualizar as versões atualmente atribuídas a esta aplicação nova.  

## <a name="next-steps"></a>Próximos passos

- [Como atribuir aplicações a grupos](apps-deploy.md)

