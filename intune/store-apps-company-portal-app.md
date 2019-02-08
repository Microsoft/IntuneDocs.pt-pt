---
title: Adicionar manualmente a aplicação Portal da Empresa do Windows 10
titleSuffix: Microsoft Intune
description: Saiba como sua força de trabalho pode adicionar manualmente a aplicação Portal da empresa do Windows 10 a seus PCs da Microsoft Store.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/19/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: bfe1a2d3-f611-4dbb-adef-c0dff4d7b810
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d6f148c98c31f53626d78a91aacedb4c92571109
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/07/2019
ms.locfileid: "55851654"
---
# <a name="manually-add-the-windows-10-company-portal-app-by-using-microsoft-intune"></a>Adicionar manualmente a aplicação Portal da Empresa do Windows 10 através do Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Para gerir dispositivos e instalar aplicações, os seus utilizadores podem instalar pessoalmente a aplicação Portal da Empresa a partir da Microsoft Store. No entanto, se as suas necessidades empresariais incluírem a atribuição da aplicação Portal da Empresa aos utilizadores, pode atribuir manualmente a aplicação Portal da Empresa do Windows 10 diretamente a partir do Intune. Pode fazê-lo mesmo que não tenha integrado o Intune na Microsoft Store para Empresas.

 > [!NOTE]
 > A opção descrita neste artigo requer que atribua atualizações manuais sempre que a atualização de uma aplicação for lançada.

## <a name="configure-settings-to-show-offline-apps"></a>Configurar definições para mostrar as aplicações offline
1. Inicie sessão na [Microsoft Store para Empresas](https://www.microsoft.com/business-store) com a sua conta de administrador.
2. Selecione o separador **Gerir** perto da parte superior da janela.
3. No painel esquerdo, selecione **Definições**.
4. Em **Experiência de compras**, defina **Mostrar aplicações offline** para **Ativado**.  
    As aplicações offline licenciadas serão apresentadas.

## <a name="download-the-offline-company-portal-app"></a>Transferir a aplicação offline Portal da Empresa
1. Procure e, em seguida, selecione a aplicação **Portal da Empresa**.
2. Defina o **Tipo de licença** para **Offline**.
3. Selecione **Obter a aplicação** para adquirir e adicionar a aplicação offline Portal da Empresa ao seu inventário.
4. Na página da aplicação **Portal da empresa**, selecione **Gerir**.
5. Em **Plataforma**, selecione **Todos os dispositivos Windows 10**, e, em seguida, selecione a **Versão mínima** adequada, a **Arquitetura** e os valores de **metadados da aplicação Transferir**. 
6. Selecione **Transferir** para guardar o ficheiro no seu computador local.

    ![Dispositivos Windows 10, em que arquitetura é igual a X86, está selecionada](./media/Win10CP-all-devices.png)

7. Transfira todos os pacotes em "Arquiteturas necessárias" ao selecionar **Transferir**.  
    Esta ação deve ser concluída para as arquiteturas x86, x64 e ARM, e perfazer um total de 12 pacotes.
8. Antes de carregar a aplicação Portal da empresa ao Intune, crie uma pasta (por exemplo: Portal de C:\Company) com os pacotes estruturados da seguinte forma:
   - Coloque o pacote do Portal da Empresa na pasta C:\Portal da Empresa. Crie também uma subpasta *Dependências* nesta localização.  

     ![Pasta Dependências guardada com o ficheiro APPXBUN](./media/Win10CP-Dependencies-save.png)

   - Coloque os pacotes de dependências na pasta *Dependências*. 

     > [!NOTE]
     > Se as dependências não forem colocadas no formato correto, o Intune não consegue reconhecer e carregar os ficheiros durante o carregamento do pacote, o que fará com que o carregamento falhe e apresente um erro.

9. No Microsoft Intune no portal do Azure, carregue a aplicação Portal da Empresa como uma nova aplicação. 
10. Atribua a aplicação Portal da Empresa como obrigatória para o conjunto de utilizadores-alvo que selecionou.  

Para obter mais informações sobre como o Intune processa as dependências de aplicações Universais, veja [Deploying an appxbundle with dependencies via Microsoft Intune MDM](https://blogs.technet.microsoft.com/configmgrdogs/2016/11/30/deploying-an-appxbundle-with-dependencies-via-microsoft-intune-mdm/) (Implementar um appxbundle com dependências através da MDM do Microsoft Intune).  

## <a name="frequently-asked-questions"></a>Perguntas mais frequentes 
### <a name="how-do-i-update-the-company-portal-app-on-my-users-devices-if-they-have-already-installed-the-older-apps-from-the-store"></a>Como atualizo a aplicação Portal da Empresa nos dispositivos dos meus utilizadores se já tiverem instalado as aplicações mais antigas da Store?
Se os utilizadores já tiverem instalado as aplicações Portal da Empresa do Windows 8.1 ou Windows Phone 8.1 a partir da Microsoft Store, estas deverão ser atualizadas automaticamente para a versão mais recente sem ser necessária qualquer ação da sua parte ou dos utilizadores. Se a atualização não ocorrer, peça aos utilizadores para confirmarem se ativaram as atualizações automáticas para as aplicações da Store nos dispositivos.   

### <a name="how-do-i-upgrade-my-sideloaded-windows-81-company-portal-app-to-the-windows-10-company-portal-app"></a>Como atualizo a minha aplicação Portal da Empresa do Windows 8.1 de sideload para a aplicação Portal da Empresa do Windows 10?
O nosso caminho de migração recomendado consiste em eliminar a atribuição da aplicação Portal da Empresa do Windows 8.1 através da definição da ação de atribuição como **Desinstalar**. Depois de selecionar esta definição, pode atribuir a aplicação Portal da Empresa do Windows 10 através de qualquer uma das opções mencionadas anteriormente.  

Se precisar de carregar a aplicação em sideload e tiver atribuído o Portal da Empresa do Windows 8.1 sem o assinar com o Certificado da Symantec, conclua a atualização ao seguir os passos nas secções anteriores deste artigo.

Se precisar de carregar a aplicação em sideload e tiver assinado e atribuído a aplicação Portal da Empresa do Windows 8.1 com o certificado de assinatura de código da Symantec, siga os passos da secção seguinte.

### <a name="how-do-i-upgrade-my-signed-and-sideloaded-windows-phone-81-company-portal-app-or-windows-81-company-portal-app-to-the-windows-10-company-portal-app"></a>Como atualizo a minha aplicação Portal da Empresa do Windows Phone 8.1 ou do Windows 8.1 de sideload e assinada para a aplicação Portal da Empresa do Windows 10?
O nosso caminho de migração recomendado consiste em eliminar a atribuição existente da aplicação Portal da Empresa do Windows Phone 8.1 ou do Windows 8.1 através da definição da ação de atribuição como **Desinstalar**. Depois de selecionar esta definição, pode atribuir a aplicação Portal da Empresa do Windows 10 normalmente.  

Caso contrário, a aplicação Portal da Empresa do Windows 10 terá de ser corretamente atualizada e assinada para garantir que o caminho de atualização é respeitado.  

Se assinar e atribuir a aplicação Portal da Empresa do Windows 10 desta forma, terá de repetir este processo para cada nova atualização de aplicação disponibilizada na loja. A aplicação não será automaticamente atualizada quando a loja for atualizada.  

Veja a seguir como pode assinar e atribuir a aplicação desta forma:

1. Transfira o [Script de Assinatura da Aplicação Portal da Empresa do Windows 10 do Microsoft Intune](https://aka.ms/win10cpscript).  
    Este script requer que o Windows SDK para o Windows 10 esteja instalado no computador anfitrião. [Transfira o Windows SDK para Windows 10](https://go.microsoft.com/fwlink/?LinkId=619296).
2. Transfira a aplicação Portal da Empresa do Windows 10 na Microsoft Store para Empresas, conforme mencionado acima.  
3. Para assinar a aplicação Portal da Empresa do Windows 10, execute o script com os parâmetros de entrada detalhados no cabeçalho do script, conforme mostrado na seguinte tabela.  
    As dependências não precisam de ser transmitidas para o script. Estas só são necessárias quando a aplicação está a ser carregada para a Consola de Administração do Intune.

| Parâmetro |  Descrição  |
|---|---|
| InputWin10AppxBundle  |  O caminho para o ficheiro appxbundle de origem. |
| OutputWin10AppxBundle | O caminho de saída do ficheiro appxbundle assinado. 
| Win81Appx  | O caminho para o ficheiro do Portal da Empresa Windows 8.1 ou Windows Phone 8.1 (.APPX). |
| PfxFilePath  |  O caminho do ficheiro Certificado de Assinatura de Código de Dispositivo Móvel Empresarial da Symantec (.PFX).  |
| PfxPassword  | A palavra-passe do Certificado de Assinatura de Código de Dispositivo Móvel Empresarial da Symantec. |
| PublisherId | O ID de Publicador da empresa. Se estiver ausente, é utilizado o campo Assunto do Certificado de Assinatura de Código de Dispositivo Móvel Empresarial da Symantec. |
| SdkPath | O caminho da pasta raiz do Windows SDK para Windows 10. Este argumento é opcional e assume a predefinição de ${env:ProgramFiles(x86)}\Windows Kits\10.  |

Quando a execução do script tiver terminado, este irá transmitir a versão assinada da aplicação Portal da Empresa do Windows 10. Em seguida, pode atribuir a versão assinada da aplicação como uma aplicação de linha de negócio (LOB) através do Intune, que atualiza as versões atualmente atribuídas a esta aplicação nova.  

## <a name="next-steps"></a>Passos Seguintes

- [Atribuir aplicações a grupos](apps-deploy.md)

