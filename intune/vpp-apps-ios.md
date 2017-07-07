---
title: "Gerir aplicações compradas em volume iOS | Microsoft Docs"
titleSuffix: Intune Azure preview
description: "Pré-visualização do Azure no Intune: saiba como pode sincronizar as aplicações que comprou em volume na loja iOS para o Intune e, em seguida, gerir e controlar a utilização das mesmas."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 05/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 51d45ce2-d81b-4584-8bc4-568c8c62653d
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 3974145b4c244e251ee91a6216a79a6d8b1ad792
ms.contentlocale: pt-pt
ms.lasthandoff: 05/23/2017

---

# <a name="how-to-manage-ios-apps-you-purchased-through-a-volume-purchase-program-with-microsoft-intune"></a>Como gerir aplicações iOS compradas através de um programa de compra em grandes volumes com o Microsoft Intune


[!INCLUDE[azure_preview](./includes/azure_preview.md)]

A iOS App Store permite-lhe comprar várias licenças para uma aplicação que pretende executar na sua empresa. Isto ajuda a reduzir a sobrecarga administrativa de controlar várias cópias adquiridas de aplicações.

O Microsoft Intune ajuda-o a gerir aplicações compradas através deste programa ao importar as informações da licença a partir da loja de aplicações, ao controlar a quantidade de licenças que utilizou e ao impedir que instale mais cópias da sua aplicação do que as que tem.

Além disso, pode sincronizar, gerir e atribuir livros que tenha comprado na loja do Apple Volume Purchase Program com o Intune e atribuí-los aos utilizadores. Utilize a carga de trabalho **Livros** no portal do Intune para gerir os livros. Os procedimentos para gerir livros são os mesmos que utiliza para gerir aplicações.
Para realizar este procedimento, é preciso carregar um token do Apple Volume Purchase Program. Atualmente, só pode atribuir livros como uma instalação **Obrigatória**.
Quando atribui um livro a um dispositivo, esse dispositivo tem de ter a aplicação iBooks incorporada instalada. Caso contrário, o utilizador final tem de instalar novamente a aplicação para ler o livro. Atualmente, não pode utilizar o Intune para restaurar aplicações incorporadas removidas.


## <a name="manage-volume-purchased-apps-for-ios-devices"></a>Gerir aplicações compradas em volume para dispositivos iOS
Compra várias licenças para aplicações iOS através do [Apple Volume Purchase Program for Business](http://www.apple.com/business/vpp/) ou do [Apple Volume Purchase Program for Education](http://volume.itunes.apple.com/us/store). Isto envolve configurar uma conta VPP da Apple no site da Apple e carregar o token VPP da Apple para o Intune.  Depois disso, pode sincronizar as informações de compra em volume com o Intune e controlar a utilização da aplicação comprada em volume.

## <a name="before-you-start"></a>Antes de começar
Antes de começar, terá de obter um token VPP da Apple e carregá-lo para a sua conta do Intune. Além disso, deve compreender o seguinte:

* Pode associar vários tokens de programa de compra em volume à sua conta do Intune.
* Se tiver utilizado anteriormente um token VPP com outro produto, tem de gerar um novo token para utilizar com o Intune.
* Cada token é válido durante um ano.
* Por predefinição, o Intune sincroniza-se com o serviço Apple VPP duas vezes por dia. Pode iniciar uma sincronização manual em qualquer altura.
* Após importar o token VPP para o Intune, não importe o mesmo token para nenhuma outra solução de gestão de dispositivos. Se o fizer, pode perder atribuições de licenças e registos de utilizadores.
* Antes de começar a utilizar o VPP iOS com o Intune, remova as contas de utilizador VPP existentes criadas com outros fornecedores de gestão de dispositivos móveis (MDM). O Intune não irá sincronizar essas contas de utilizador no serviço como medida de segurança. O Intune só irá sincronizar os dados do serviço Apple VPP que foram criados pelo Intune.
* O Intune suporta a adição de até 256 tokens VPP.

## <a name="to-get-and-upload-an-apple-vpp-token"></a>Para obter e carregar um token Apple VPP

1. Inicie sessão no portal do Azure.
2. Escolha **Mais Serviços** > **Outros** > **Intune**.
3. No painel **Intune**, escolha **Aplicações móveis**.
1.  Na carga de trabalho **Aplicações Móveis**, escolha **Configurar** > **Tokens iOS VPP**.
2.  No painel da lista de tokens VPP, clique em **Adicionar**.
3.  No painel Novo Token VPP, especifique as seguintes informações:
    - **Ficheiro de token VPP** – Se ainda não o fez, inscreva-se no Volume Purchase Program for Business ou no Volume Purchase Program for Education. Após a inscrição, transfira o token VPP da Apple para a sua conta e selecione-o aqui.
    - **ID Apple** – Introduza o ID Apple da conta associada ao programa de compra em volume.
    - **Tipo de conta VPP** – Escolha entre **Empresas** ou **Educação**.
4. Quando tiver terminado, clique em **Carregar**.

O token é apresentado no painel da lista de tokens.


Pode sincronizar os dados retidos pela Apple com o Intune em qualquer altura, selecionando **Sincronizar agora**.

## <a name="to-assign-a-volume-purchased-app"></a>Para atribuir uma aplicação comprada em volume

1. Na carga de trabalho **Aplicações Móveis**, escolha **Gerir** > **Aplicações Licenciadas**.
2. No painel da lista de aplicações, escolha a aplicação que quer atribuir e, em seguida, escolha “**...**” > **Atribuir Grupos**.
3. No painel <*nome da aplicação*> – **Grupos Atribuídos**, escolha **Gerir** > **Grupos Atribuídos**.
4. Selecione **Atribuir Grupos** e, em seguida, no painel **Selecionar grupos**, selecione o utilizador ou grupos de dispositivos do Azure AD aos quais pretende atribuir a aplicação.
Tem de escolher uma ação de atribuição **Obrigatória**. Além disso, as atribuições a grupos de dispositivos estão disponíveis para novos inquilinos criados após janeiro de 2017. Se o seu inquilino tiver sido criado antes desta data e não tiver a opção de atribuir aplicações do VPP a grupos de dispositivos, contacte o suporte do Intune.
5. Assim que tiver terminado, escolha **Guardar**.

Veja [Como monitorizar aplicações](apps-monitor.md) para obter informações que o ajudam a monitorizar as atribuições de aplicações.

## <a name="further-information"></a>Informações adicionais

Se atribuir a aplicação como uma instalação **Obrigatória**, é utilizada uma licença por cada utilizador que a instalar.

Para recuperar uma licença, tem de alterar a ação de atribuição para **Desinstalar**. A licença será recuperada quando desinstalar a aplicação.

Quando um utilizador com um dispositivo elegível tenta instalar uma aplicação VPP pela primeira vez, é-lhe pedido para se associar ao Apple Volume Purchase Program. O utilizador tem de o fazer antes de continuar a instalação da aplicação.

Quando atribui uma aplicação VPP como Disponível, a licença e o conteúdo da aplicação são atribuídos diretamente a partir da loja de aplicações.
