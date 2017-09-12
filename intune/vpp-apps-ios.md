---
title: "Gerir aplicações iOS compradas em grandes volumes"
titlesuffix: Azure portal
description: "Saiba como pode sincronizar as aplicações que comprou em volume na loja iOS para o Intune e, em seguida, gerir e controlar a utilização das mesmas.\""
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 08/18/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 51d45ce2-d81b-4584-8bc4-568c8c62653d
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: addcc2c9a939b8dc62d708b3f9f000cb7c09cef3
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/09/2017
---
# <a name="how-to-manage-ios-apps-you-purchased-through-a-volume-purchase-program-with-microsoft-intune"></a>Como gerir aplicações iOS compradas através de um programa de compra em grandes volumes com o Microsoft Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

A iOS App Store permite-lhe comprar várias licenças para uma aplicação que pretende executar na sua empresa. Comprar múltiplas cópias de uma aplicação ajuda a reduzir a sobrecarga administrativa de controlar múltiplas cópias adquiridas de aplicações.

O Microsoft Intune ajuda-o a gerir aplicações adquiridas através desse programa ao:

- Comunicar informações de licenças a partir da App Store
- Controlar o número de licenças que utilizou
- Ajudá-lo a não instalar mais cópias de uma aplicação do que as que tem

Existem dois métodos que pode utilizar para atribuir as aplicações compradas em volume:

### <a name="device-licensing"></a>Licenciamento de dispositivos

Quando atribui uma aplicação a dispositivos, é utilizada uma licença de aplicação que permanece associada ao dispositivo ao qual foi atribuída.
Quando atribui aplicações compradas em volume a um dispositivo, o utilizador final do dispositivo não tem de fornecer um ID Apple para aceder à loja. 



### <a name="user-licensing"></a>Licenciamento de utilizadores

Quando atribui uma aplicação a utilizadores, é utilizada uma licença de aplicação que é associada ao utilizador. A aplicação pode ser executada em múltiplos dispositivos do utilizador (com um limite controlado pela Apple).
Ao atribuir uma aplicação comprada em volume a utilizadores, cada utilizador final tem de ter um ID Apple exclusivo válido para aceder à App Store.


Além disso, pode sincronizar, gerir e atribuir livros que tenha comprado na loja do Apple Volume Purchase Program com o Intune. Para obter mais informações, veja [Como gerir eBooks do iOS comprados através de um programa de compra em volume](vpp-ebooks-ios.md).


## <a name="manage-volume-purchased-apps-for-ios-devices"></a>Gerir aplicações compradas em volume para dispositivos iOS
Compre múltiplas licenças para aplicações iOS através do [Apple Volume Purchase Program for Business](http://www.apple.com/business/vpp/) ou do [Apple Volume Purchase Program for Education](http://volume.itunes.apple.com/us/store). Este processo envolve configurar uma conta VPP da Apple no site da Apple e carregar o token VPP da Apple para o Intune.  Depois disso, pode sincronizar as informações de compra em volume com o Intune e controlar a utilização da aplicação comprada em volume.

## <a name="before-you-start"></a>Antes de começar
Antes de começar, tem de obter um token VPP da Apple e carregá-lo para a sua conta do Intune. Além disso, deve compreender os seguintes critérios:

* Pode associar vários tokens de programa de compra em volume à sua conta do Intune.
* Se tiver utilizado anteriormente um token VPP com outro produto, tem de gerar um novo token para utilizar com o Intune.
* Cada token é válido durante um ano.
* Por predefinição, o Intune sincroniza-se com o serviço Apple VPP duas vezes por dia. Pode iniciar uma sincronização manual em qualquer altura.
* Antes de começar a utilizar o VPP iOS com o Intune, remova as contas de utilizador VPP existentes criadas com outros fornecedores de gestão de dispositivos móveis (MDM). O Intune não sincroniza essas contas de utilizador no serviço como medida de segurança. O Intune só sincroniza os dados do serviço Apple VPP que foram criados pelo Intune.
* O Intune suporta a adição de até 256 tokens VPP.
* Se atribuir uma aplicação comprada em volume a um dispositivo inscrito através de um Perfil de Inscrição de Dispositivos ou do Apple Configurator, apenas as aplicações que são direcionadas para dispositivos funcionam. Não pode direcionar as aplicações compradas em volume para utilizadores de um dispositivo DEP, que não têm afinidade de utilizador.
Isto deve-se ao facto de o licenciamento de utilizadores do VPP para iOS permitir a inscrição de milhares de dispositivos com a mesma conta de utilizador. O licenciamento de utilizadores do VPP para iOS permite a um utilizador final instalar uma aplicação em entre 5 a 10 dispositivos.
Isto significa que os primeiros dispositivos DEM inscritos instalam a aplicação do VPP através do licenciamento de utilizadores e que os outros dispositivos não receberão a aplicação.
* Um token VPP só é suportado para utilização numa conta do Intune de cada vez. Não reutilize um token VPP em múltiplos inquilinos do Intune.
* Ao atribuir aplicações VPP com o modelo de licenciamento de utilizadores a utilizadores ou dispositivos (com a afinidade de utilizador), cada utilizador do Intune tem de estar associado a um endereço de e-mail ou ID Apple exclusivo quando aceitar os termos e condições da Apple no respetivo dispositivo.
Certifique-se de que, ao configurar um dispositivo para um novo utilizador do Intune, o configura com o endereço de e-mail ou ID Apple exclusivo desse utilizador. O endereço de e-mail ou ID Apple e o utilizador do Intune formam um par exclusivo e podem ser utilizados em até 5 dispositivos.

>[!IMPORTANT]
>Após importar o token VPP para o Intune, não importe o mesmo token para nenhuma outra solução de gestão de dispositivos. Se o fizer, pode perder atribuições de licenças e registos de utilizadores.

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

1.  Na carga de trabalho **Aplicações Móveis**, selecione **Gerir** > **Licenças de Aplicação**.
2.  No painel da lista de aplicações, selecione aquela que pretende atribuir e, em seguida, selecione "**...**" > **Atribuir Grupos**.
3.  No painel *<app name>* - **Atribuições**, selecione **Gerir** > **Atribuições**.
4.  Clique em **Selecionar Grupos** e, em seguida, no painel **Selecionar grupos**, selecione o utilizador ou grupos de dispositivos do Azure AD aos quais pretende atribuir a aplicação.
5.  Para cada grupo que escolheu, selecione as seguintes definições:
    - **Tipo** – decida se a aplicação estará **Disponível** (os utilizadores finais podem instalar a aplicação a partir do Portal da Empresa) ou será **Obrigatória** (a aplicação será automaticamente instalada nos dispositivos dos utilizadores finais).
    - **Tipo de licença** – escolha entre o **Licenciamento de utilizadores** e o **Licenciamento de dispositivos**.
6.  Assim que tiver terminado, escolha **Guardar**.


>[!NOTE]
>A lista de aplicações apresentada está associada a um token. Se tiver uma aplicação que está associada a múltiplos tokens VPP, verá a mesma aplicação apresentada múltiplas vezes (uma para cada token).

## <a name="further-information"></a>Informações adicionais

Para recuperar uma licença, tem de alterar a ação de atribuição para Desinstalar. A licença será recuperada quando desinstalar a aplicação. Se remover uma aplicação associada a um utilizador, o Intune tenta recuperar todas as licenças das aplicações associadas ao mesmo.

Quando um utilizador com um dispositivo elegível tenta instalar uma aplicação do VPP num dispositivo pela primeira vez, é-lhe pedido para aderir ao Apple Volume Purchase Program. O utilizador tem de o fazer antes de continuar a instalação da aplicação. O convite para aderir ao Apple Volume Purchase Program exige que o utilizador possa utilizar a aplicação iTunes no dispositivo iOS. Se tiver definido uma política para desativar a aplicação da Loja do iTunes, o licenciamento baseado no utilizador para aplicações VPP não funciona. A solução é permitir a aplicação iTunes ao remover a política ou utilizar o licenciamento baseado no dispositivo.



## <a name="next-steps"></a>Próximos passos

Veja [Como monitorizar aplicações](apps-monitor.md) para obter informações que o ajudam a monitorizar as atribuições de aplicações.