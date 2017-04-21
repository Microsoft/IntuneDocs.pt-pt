---
title: "Como adicionar aplicações da loja Windows ao Intune"
titleSuffix: Intune Azure preview
description: "Pré-visualização do Azure no Intune: saiba como adicionar aplicações da loja Windows ao Intune."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 03/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 07241b6d-86d8-4abb-83a2-3fc5feae5788
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 195a7333e09f3a269b5ff10c51e0cfb3e7d10bdc
ms.openlocfilehash: 3e363183f3ac33e4cde1060fb141f5e4eb7d566c
ms.lasthandoff: 04/04/2017

---

# <a name="how-to-add-windows-store-apps-to-microsoft-intune"></a>Como adicionar aplicações da loja Windows ao Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]


1. Inicie sessão no portal do Azure.
2. Escolha **Mais Serviços** > **Monitorização + Gestão** > **Intune**.
3. No painel **Intune**, escolha **Gerir aplicações**.
4. Na carga de trabalho **Aplicações móveis**, escolha **Gerir** > **Aplicações**.
5. Acima da lista de aplicações, escolha **Adicionar**.
6. No painel **Adicionar Aplicação**, escolha **Informações da Aplicação**.
7. No painel **Editar Aplicação**, configure as informações seguintes. Quando tiver terminado, clique em **Adicionar**. Consoante a aplicação que tenha escolhido, alguns dos valores neste painel podem ter sido preenchidos automaticamente:
    - **Nome da Aplicação** – Introduza o nome da aplicação tal como será apresentado no portal da empresa. Certifique-se de que todos os nomes de aplicações que utiliza são exclusivos. Se o mesmo nome de aplicação existir duas vezes, apenas uma das aplicações será apresentada aos utilizadores no portal da empresa.
    - **Descrição da Aplicação** – Introduza uma descrição para a aplicação. A descrição será apresentada aos utilizadores no portal da empresa.
    - **Publicador** - Introduza o nome do publicador da aplicação.
    - **URL da loja de aplicações** – Introduza o URL da loja de aplicações da aplicação que pretende criar.
    - **Sistema Operativo Mínimo** – Na lista, escolha a versão mínima do sistema operativo no qual a aplicação pode ser instalada. Se atribuir a aplicação a um dispositivo com um sistema operativo anterior, não será instalada.
    - **Categoria (opcional)** – Selecione uma ou mais categorias das aplicações incorporadas, ou uma categoria criada por si. Isto irá permitir que os utilizadores encontrem a aplicação mais facilmente quando procurarem no portal da empresa.
    - **Apresentar esta aplicação em destaque no Portal da Empresa** – Apresente a aplicação de forma destacada na página principal do portal da empresa quando os utilizadores procurarem aplicações.
    - **URL de Informações** – Opcionalmente, introduza o URL de um site que contenha informações sobre esta aplicação. O URL será apresentado aos utilizadores no portal da empresa.
    - **URL de Privacidade** – Opcionalmente, introduza um URL para um site que contenha informações sobre a privacidade desta aplicação. O URL será apresentado aos utilizadores no portal da empresa.
    - **Programador** – Opcionalmente, introduza o nome do programador da aplicação.
    - **Proprietário** – Opcionalmente, introduza um nome para o proprietário desta aplicação, por exemplo, **Departamento de RH**.
    - **Notas** – Introduza quaisquer notas que pretenda associar esta aplicação.
    - **Carregar Ícone** – Carregue um ícone que será associado à aplicação. Este é o ícone que será apresentado com a aplicação quando os utilizadores procurarem no portal da empresa.
8. Quando terminar, no painel **Adicionar Aplicação**, escolha **Guardar**.

A aplicação que criou será apresentada na lista de aplicações onde a pode atribuir aos grupos que escolher. Para obter ajuda, veja [Como atribuir aplicações a grupos](/intune-azure/manage-apps/deploy-apps).

## <a name="manually-deploy-windows-10-company-portal-app"></a>Implementar manualmente a aplicação Portal da Empresa do Windows 10
Os utilizadores finais podem instalar a aplicação Portal da Empresa a partir da Loja Windows para gerir dispositivos e instalar aplicações. No entanto, se as suas necessidades empresariais incluírem a implementação da aplicação Portal da Empresa, pode implementar a aplicação Portal da Empresa do Windows 10 diretamente a partir do Intune, mesmo que não tenha integrado o Intune com a Loja Windows para Empresas.

 > [!NOTE]
 > Esta opção precisará da implementação das atualizações manuais sempre que uma atualização da aplicação for disponibilizada.

1. Inicie sessão na sua conta na [Loja Windows para Empresas](https://www.microsoft.com/business-store) e compre a versão da **licença offline** da aplicação Portal da Empresa.  
2. Assim que a aplicação tiver sido comprada, selecione a aplicação na página **Inventário**.  
3. Selecione **Todos os dispositivos Windows 10** como a **Plataforma** e, em seguida, a **Arquitetura** adequada e transfira. Não é preciso um ficheiro de licença de aplicação para esta aplicação.
![Imagem de Todos os dispositivos Windows 10 e detalhes do Pacote de Arquitetura X86 para Transferência](../media/Win10CP-all-devices.png)
4. Transfira todos os pacotes em “Arquiteturas necessárias”. Esta ação deve ser feita para as arquiteturas x86, x64 e ARM, resultando num total de nove pacotes, conforme mostrado abaixo.

![Imagem dos ficheiros de dependência para Transferência ](../media/Win10CP-dependent-files.png)
5. Antes de carregar a aplicação Portal da Empresa para o Intune, crie uma pasta (por exemplo, C:\Portal da Empresa) com os pacotes estruturados da seguinte forma:
  1. Coloque o pacote do Portal da Empresa na pasta C:\Portal da Empresa. Crie também uma subpasta Dependências nesta localização.  
  ![Imagem da pasta Dependências guardada com o ficheiro APPXBUN](../media/Win10CP-Dependencies-save.png)
  2. Coloque os nove pacotes de dependências na pasta Dependências.  
  Se as dependências não forem colocadas neste formato, o Intune não poderá reconhecê-los e carregá-los durante o carregamento do pacote, o que fará com que o carregamento falhe com o seguinte erro.  
  ![A dependência de aplicação do Windows para este instalador de software não foi encontrada na pasta da aplicação. Pode continuar a criar e a implementar esta aplicação, mas só será executada quando a dependência de aplicação do Windows em falta for disponibilizada.](../media/Win10CP-error-message.png)
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

1. Transfira o Script de Assinatura da Aplicação Portal da Empresa do Windows 10 do Microsoft Intune a partir de [https://aka.ms/win10cpscript](https://aka.ms/win10cpscript).  Este script requer que o Windows SDK para o Windows 10 esteja instalado no computador anfitrião. Para transferir o Windows SDK para o Windows 10, visite [https://go.microsoft.com/fwlink/?LinkId=619296](https://go.microsoft.com/fwlink/?LinkId=619296).
2. Transfira a aplicação Portal da Empresa do Windows 10 na Loja Windows para Empresas, conforme detalhado acima.  
3. Execute o script com os parâmetros de entrada detalhados no cabeçalho do script para assinar a aplicação Portal da Empresa do Windows 10 (extraída abaixo). As dependências não precisam de ser transmitidas para o script. Só são precisas quando a aplicação está a ser carregada para a Consola de Administração do Intune.

|Parâmetro | Descrição|
| ------------- | ------------- |
|InputWin10AppxBundle |O caminho onde está localizado o ficheiro appxbundle de origem |
|OutputWin10AppxBundle |O caminho de saída do ficheiro appxbundle assinado.  Win81Appx O caminho onde o ficheiro do Portal da Empresa Windows 8.1 ou Windows Phone 8.1 (.APPX) está localizado.|
|PfxFilePath |O caminho do ficheiro Certificado de Assinatura de Código de Dispositivo Móvel Empresarial da Symantec (.PFX). |
|PfxPassword| A palavra-passe do Certificado de Assinatura de Código de Dispositivo Móvel Empresarial da Symantec. |
|PublisherId |O ID de Publicador da empresa. Se estiver ausente, é utilizado o campo "Assunto" do Certificado de Assinatura de Código de Dispositivo Móvel Empresarial da Symantec.|
|SdkPath | O caminho da pasta raiz do Windows SDK para Windows 10. Este argumento é opcional e assume a predefinição de ${env:ProgramFiles(x86)}\Windows Kits\10|
O script irá transmitir a versão assinada da aplicação Portal da Empresa do Windows 10 após a respetiva execução. Em seguida, pode implementar a versão assinada da aplicação como uma aplicação de LOB através do Intune, que irá atualizar as versões atualmente implementadas para esta aplicação nova.  

