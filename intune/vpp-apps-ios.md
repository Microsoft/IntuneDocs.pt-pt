---
title: "Gerir aplicações iOS compradas em grandes volumes"
titleSuffix: Intune on Azure
description: "Saiba como pode sincronizar as aplicações que comprou em volume na loja iOS para o Intune e, em seguida, gerir e controlar a utilização das mesmas.\""
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 07/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 51d45ce2-d81b-4584-8bc4-568c8c62653d
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 16b7ce81eb63a81534af2911b34904d870ac41ad
ms.sourcegitcommit: fd2e8f6f8761fdd65b49f6e4223c2d4a013dd6d9
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/03/2017
---
# <a name="how-to-manage-ios-apps-you-purchased-through-a-volume-purchase-program-with-microsoft-intune"></a>Como gerir aplicações iOS compradas através de um programa de compra em grandes volumes com o Microsoft Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

A iOS App Store permite-lhe comprar várias licenças para uma aplicação que pretende executar na sua empresa. Comprar múltiplas cópias de uma aplicação ajuda a reduzir a sobrecarga administrativa de controlar múltiplas cópias adquiridas de aplicações.

O Microsoft Intune ajuda-o a gerir aplicações adquiridas através desse programa ao:

- Importar as informações de licença a partir da loja de aplicações
- Controlar o número de licenças que utilizou
- Impedi-lo de instalar mais cópias da aplicação do que aquelas que tem

Além disso, pode sincronizar, gerir e atribuir livros que tenha comprado na loja do Apple Volume Purchase Program com o Intune. Utilize a carga de trabalho **Livros** no portal do Intune para gerir os livros. Os procedimentos para gerir livros são os mesmos que utiliza para gerir aplicações.
Para realizar este procedimento, antes de começar, é preciso carregar um token do Apple Volume Purchase Program. Atualmente, só pode atribuir livros como uma instalação **Obrigatória**.
Quando atribui um livro a um dispositivo, esse dispositivo tem de ter a aplicação iBooks incorporada instalada. Caso contrário, o utilizador final terá de instalar novamente a aplicação para ler o livro. Atualmente, não pode utilizar o Intune para restaurar aplicações incorporadas removidas.


## <a name="manage-volume-purchased-apps-for-ios-devices"></a>Gerir aplicações compradas em volume para dispositivos iOS
Compre múltiplas licenças para aplicações iOS através do [Apple Volume Purchase Program for Business](http://www.apple.com/business/vpp/) ou do [Apple Volume Purchase Program for Education](http://volume.itunes.apple.com/us/store). Este processo envolve configurar uma conta VPP da Apple no site da Apple e carregar o token VPP da Apple para o Intune.  Depois disso, pode sincronizar as informações de compra em volume com o Intune e controlar a utilização da aplicação comprada em volume.

## <a name="before-you-start"></a>Antes de começar
Antes de começar, tem de obter um token VPP da Apple e carregá-lo para a sua conta do Intune. Além disso, deve compreender os seguintes critérios:

* Pode associar vários tokens de programa de compra em volume à sua conta do Intune.
* Se tiver utilizado anteriormente um token VPP com outro produto, tem de gerar um novo token para utilizar com o Intune.
* Cada token é válido durante um ano.
* Por predefinição, o Intune sincroniza-se com o serviço Apple VPP duas vezes por dia. Pode iniciar uma sincronização manual em qualquer altura.
* Após importar o token VPP para o Intune, não importe o mesmo token para nenhuma outra solução de gestão de dispositivos. Se o fizer, pode perder atribuições de licenças e registos de utilizadores.
* Antes de começar a utilizar o VPP iOS com o Intune, remova as contas de utilizador VPP existentes criadas com outros fornecedores de gestão de dispositivos móveis (MDM). O Intune não sincroniza essas contas de utilizador no serviço como medida de segurança. O Intune só sincroniza os dados do serviço Apple VPP que foram criados pelo Intune.
* O Intune suporta a adição de até 256 tokens VPP.
* Se atribuir uma aplicação comprada em volume a um dispositivo inscrito através de um Perfil de Inscrição de Dispositivos ou do Apple Configurator, apenas as aplicações que são direcionadas para dispositivos funcionam. Não pode direcionar as aplicações compradas em volume para utilizadores de um dispositivo DEP, que não têm afinidade de utilizador.
* Um token VPP só é suportado para utilização numa conta do Intune de cada vez. Não reutilize um token VPP em múltiplos inquilinos do Intune.
* Ao atribuir aplicações VPP com o modelo de licenciamento de utilizadores a utilizadores ou dispositivos (com a afinidade de utilizador), cada utilizador do Intune tem de estar associado a um endereço de e-mail ou ID Apple exclusivo quando aceitar os termos e condições da Apple no respetivo dispositivo.
Certifique-se de que, ao configurar um dispositivo para um novo utilizador do Intune, o configura com o endereço de e-mail ou ID Apple exclusivo desse utilizador. O endereço de e-mail ou ID Apple e o utilizador do Intune formam um par exclusivo e podem ser utilizados em até 5 dispositivos.


## <a name="to-get-and-upload-an-apple-vpp-token"></a>Para obter e carregar um token Apple VPP

1. Inicie sessão no portal do Azure.
2. Escolha **Mais Serviços** > **Monitorização + Gestão** > **Intune**.
3. No painel **Intune**, escolha **Aplicações móveis**.
1.  Na carga de trabalho **Aplicações Móveis**, escolha **Configurar** > **Tokens iOS VPP**.
2.  No painel da lista de tokens VPP, clique em **Adicionar**.
3.  No painel **Novo Token VPP**, especifique as seguintes informações:
    - **Ficheiro de token VPP** – se ainda não o fez, inscreva-se no Volume Purchase Program for Business ou no Volume Purchase Program for Education. Após a inscrição, transfira o token VPP da Apple para a sua conta e selecione-o aqui.
    - **ID Apple** – Introduza o ID Apple da conta associada ao programa de compra em volume.
    - **Tipo de conta VPP** – Escolha entre **Empresas** ou **Educação**.
4. Quando tiver terminado, clique em **Carregar**.

O token é apresentado no painel da lista de tokens.


Pode sincronizar os dados retidos pela Apple com o Intune em qualquer altura, selecionando **Sincronizar agora**.

> [!NOTE]
> O Microsoft Intune só sincroniza informações de Aplicações que estejam publicamente disponíveis através da Loja do iTunes. As **Aplicações B2B Personalizadas para iOS** ainda não são suportadas. Se o seu cenário incluir tais aplicações, as informações da aplicação não serão sincronizadas.

## <a name="to-assign-a-volume-purchased-app"></a>Para atribuir uma aplicação comprada em volume

1. Na carga de trabalho **Aplicações Móveis**, escolha **Gerir** > **Aplicações Licenciadas**.
2. No painel da lista de aplicações, escolha a aplicação que quer atribuir e, em seguida, escolha “**...**” > **Atribuir Grupos**.
3. No painel <*nome da aplicação*> – **Grupos Atribuídos**, escolha **Gerir** > **Grupos Atribuídos**.
4. Selecione **Atribuir Grupos** e, em seguida, no painel **Selecionar grupos**, selecione o utilizador ou grupos de dispositivos do Azure AD aos quais pretende atribuir a aplicação.
Tem de escolher uma ação de atribuição **Obrigatória**. Além disso, as atribuições a grupos de dispositivos estão disponíveis para novos inquilinos criados após janeiro de 2017. Se o seu inquilino tiver sido criado antes desta data e não tiver a opção de atribuir aplicações do VPP a grupos de dispositivos, contacte o suporte do Intune.
5. Assim que tiver terminado, escolha **Guardar**.

>[!NOTE]
>A lista de aplicações apresentada está associada a um token. Se tiver uma aplicação que está associada a múltiplos tokens VPP, verá a mesma aplicação apresentada múltiplas vezes (uma para cada token).

Veja [Como monitorizar aplicações](apps-monitor.md) para obter informações que o ajudam a monitorizar as atribuições de aplicações.

## <a name="further-information"></a>Informações adicionais

Se atribuir a aplicação como uma instalação **Obrigatória**, é utilizada uma licença por cada utilizador que a instalar.

Para recuperar uma licença, tem de alterar a ação de atribuição para **Desinstalar**. A licença será recuperada quando desinstalar a aplicação.

Quando um utilizador com um dispositivo elegível tenta instalar uma aplicação VPP pela primeira vez, é-lhe pedido para aderir ao Apple Volume Purchase Program. O utilizador tem de o fazer antes de continuar a instalação da aplicação. O convite para aderir ao Apple Volume Purchase Program exige que o utilizador possa utilizar a aplicação iTunes no dispositivo iOS. Se tiver definido uma política para desativar a aplicação da Loja do iTunes, o licenciamento baseado no utilizador para aplicações VPP não funciona. A solução é permitir a aplicação iTunes ao remover a política ou utilizar o licenciamento baseado no dispositivo.

Quando atribui uma aplicação VPP como Disponível, a licença e o conteúdo da aplicação são atribuídos diretamente a partir da loja de aplicações.
