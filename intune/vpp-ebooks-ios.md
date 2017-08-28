---
title: Gerir eBooks do iOS comprados em volume
titleSuffix: Intune on Azure
description: "Saiba como pode sincronizar os livros que comprou em volume na loja iOS para o Intune e, em seguida, gerir e controlar a utilização deles.\""
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 08/17/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f5617074-2384-4812-b913-dc94f64c0818
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 43ab9e906f05a069b1399ab53a4861d7289b7024
ms.sourcegitcommit: 6a089eb45ea3fb18ae0b2dac96683466f52f95bf
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/18/2017
---
# <a name="how-to-manage-ios-ebooks-you-purchased-through-a-volume-purchase-program-with-microsoft-intune"></a>Como gerir eBooks do iOS comprados através de um programa de compra em grandes volumes com o Microsoft Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

O Apple Volume Purchase Program (VPP) permite-lhe comprar várias licenças para um livro que pretende distribuir aos utilizadores na sua empresa. Pode distribuir livros de lojas para Empresas ou Educação.

O Microsoft Intune ajuda-o a sincronizar, gerir e atribuir livros comprados através deste programa. Pode importar informações de licença da loja e controlar quantas licenças utilizou.

Os procedimentos para gerir livros são semelhantes à [gestão de aplicações de VPP](vpp-apps-ios.md).

## <a name="manage-volume-purchased-books-for-ios-devices"></a>Gerir livros comprados em volume para dispositivos iOS
Compra várias licenças para livros iOS através do [Apple Volume Purchase Program for Business](http://www.apple.com/business/vpp/) ou do [Apple Volume Purchase Program for Education](http://volume.itunes.apple.com/us/store). Este processo envolve configurar uma conta VPP da Apple no site da Apple e carregar o token VPP da Apple para o Intune.  Depois disso, pode sincronizar as informações de compra em volume com o Intune e controlar a utilização do livro comprado em volume.

## <a name="before-you-start"></a>Antes de começar
Antes de começar, obtenha um token VPP da Apple e carregue o mesmo para a sua conta do Intune. Além disso,

* Pode associar até 256 tokens VPP à sua conta do Intune.
* Se tiver utilizado anteriormente um token VPP com outro produto, tem de gerar um novo token para utilizar com o Intune.
* Cada token é válido durante um ano.
* Por predefinição, o Intune sincroniza-se com o serviço Apple VPP duas vezes por dia. Pode iniciar uma sincronização manual em qualquer altura.
* Após importar o token VPP para o Intune, não importe o mesmo token para nenhuma outra solução de gestão de dispositivos. Se o fizer, pode perder atribuições de licenças e registos de utilizadores.
* Para começar a utilizar os livros iOS com o Intune, remova as contas de utilizador VPP existentes criadas com outros fornecedores de gestão de dispositivos móveis (MDM). O Intune não sincroniza essas contas de utilizador no serviço como medida de segurança. O Intune só sincroniza os dados do serviço Apple VPP que foram criados pelo Intune.
* Quando atribui um livro a um dispositivo, esse dispositivo tem de ter a aplicação iBooks incorporada instalada. Caso contrário, o utilizador final terá de instalar novamente a aplicação para poder ler o livro. Atualmente, não pode utilizar o Intune para restaurar aplicações incorporadas removidas.
* Só pode atribuir livros do site do Apple Volume Purchase Program. Não pode carregar e, em seguida, atribuir livros criados internamente.
* Atualmente, não pode atribuir livros a categorias de utilizador final do mesmo modo que para as aplicações.
* Não pode recuperar uma licença quando o livro é atribuído.
* Quando um utilizador com um dispositivo elegível tenta instalar um livro VPP pela primeira vez, é necessário associar-se ao Apple Volume Purchase Program para poder instalar um livro. Também pode atribuir licenças a grupos de segurança com IDs Apple geridas. Se fizer isso, não será pedida aos utilizadores a sua ID Apple quando é instalado um livro.

## <a name="to-get-and-upload-an-apple-vpp-token"></a>Para obter e carregar um token Apple VPP

1. Inicie sessão no portal do Azure.
2. Escolha **Mais Serviços** > **Monitorização + Gestão** > **Intune**.
3. No painel **Intune**, escolha **Aplicações móveis**.
1.  Na carga de trabalho **Aplicações Móveis**, escolha **Configurar** > **Tokens iOS VPP**.
2.  No painel da lista de tokens VPP, clique em **Adicionar**.
3.  No painel **Novo Token VPP**, especifique as seguintes informações:
    - **Ficheiro de token VPP** – verifique se se inscreveu no Volume Purchase Program for Business ou no Volume Purchase Program for Education. Em seguida, transfira o token VPP da Apple para a sua conta e selecione-o aqui.
    - **ID Apple** – Introduza o ID Apple da conta associada ao programa de compra em volume.
    - **Tipo de conta VPP** – Escolha entre **Empresas** ou **Educação**.
4. Quando tiver terminado, clique em **Carregar**.

O token é apresentado no painel da lista de tokens.


Pode sincronizar os dados retidos pela Apple com o Intune em qualquer altura, selecionando **Sincronizar agora**.

## <a name="to-assign-a-volume-purchased-app"></a>Para atribuir uma aplicação comprada em volume

1. Na carga de trabalho **eBooks**, escolha **Gerir** > **Todos os eBooks**.
2. No painel da lista de livros, selecione o livro que pretende atribuir e, em seguida, selecione "**...**" > **Atribuir Grupos**.
3. No painel <*nome do livro*> – **Grupos Atribuídos**, escolha **Gerir** > **Grupos Atribuídos**.
4. Escolha **Atribuir Grupos** e, no painel **Selecionar grupos**, escolha os grupos de utilizadores do Azure AD aos quais pretende atribuir o livro. Os grupos de dispositivos não são atualmente suportados.
Selecione a ação de atribuição **Disponível** ou **Obrigatório**. 
5. Assim que tiver terminado, escolha **Guardar**.

## <a name="next-steps"></a>Próximos passos

Veja [Como monitorizar aplicações](apps-monitor.md) para obter informações que o ajudam a monitorizar as atribuições de livros.






