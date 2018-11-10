---
title: Gerir aplicações iOS compradas em volume no Microsoft Intune
titlesuffix: ''
description: Saiba como pode sincronizar as aplicações que comprou em volume na loja iOS para o Microsoft Intune e, em seguida, gerir e controlar a utilização das mesmas.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/29/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 51d45ce2-d81b-4584-8bc4-568c8c62653d
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: fc7aac337c01db3098be5f699db22c3a81c6eb75
ms.sourcegitcommit: 5c2a70180cb69049c73c9e55d36a51e9d6619049
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/30/2018
ms.locfileid: "50236617"
---
# <a name="how-to-manage-ios-apps-purchased-through-a-volume-purchase-program-with-microsoft-intune"></a>Como gerir aplicações iOS compradas através de um programa de compra em grandes volumes com o Microsoft Intune


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

A iOS App Store permite-lhe comprar várias licenças para uma aplicação que pretende executar na sua empresa. A compra de várias cópias ajuda-o a gerir aplicações na sua empresa de forma eficiente.

O Microsoft Intune ajuda-o a gerir várias cópias de aplicações compradas através desse programa ao:

- Comunicar informações sobre a licença a partir da App Store.
- Controlar o número de licenças que utilizou.
- Ajudá-lo a não instalar mais cópias da aplicação do que as que tem.

Existem dois métodos que pode utilizar para atribuir as aplicações compradas em volume:

### <a name="device-licensing"></a>Licenciamento de dispositivos

Quando atribui uma aplicação a dispositivos, é utilizada uma licença de aplicação que permanece associada ao dispositivo ao qual foi atribuída.

Quando atribui aplicações compradas em volume a um dispositivo, o utilizador final do dispositivo não tem de fornecer um ID Apple para aceder à loja.

### <a name="user-licensing"></a>Licenciamento de utilizadores

Quando atribui uma aplicação a um utilizador, é utilizada uma licença de aplicação que é associada ao utilizador. A aplicação pode ser executada em múltiplos dispositivos do utilizador (com um limite controlado pela Apple).

Ao atribuir uma aplicação comprada em volume a utilizadores, cada utilizador final tem de ter um ID Apple exclusivo válido para aceder à App Store.

Além disso, pode sincronizar, gerir e atribuir livros que tenha comprado na loja do Apple Volume Purchase Program (VPP) com o Intune. Para obter mais informações, veja [Como gerir eBooks do iOS comprados através de um programa de compra em volume](vpp-ebooks-ios.md).

## <a name="manage-volume-purchased-apps-for-ios-devices"></a>Gerir aplicações compradas em grandes volumes para dispositivos iOS

### <a name="supports-apple-volume-purchase-program-volume-purchased-apps-for-ios-devices"></a>Suporta as aplicações compradas em volume do Apple Volume Purchase Program para dispositivos iOS

Compre múltiplas licenças para aplicações iOS através do [Apple Volume Purchase Program for Business](http://www.apple.com/business/vpp/) ou do [Apple Volume Purchase Program for Education](http://volume.itunes.apple.com/us/store). Este processo envolve configurar uma conta VPP da Apple no site da Apple e carregar o token VPP da Apple para o Intune.  Depois disso, pode sincronizar as informações de compra em volume com o Intune e controlar a utilização da aplicação comprada em volume.

### <a name="supports-business-to-business-volume-purchased-apps-for-ios-devices"></a>Suporta as aplicações compradas em volume de empresa-empresa para dispositivos iOS

Além disso, os programadores de terceiros também podem distribuir em privado aplicações aos membros autorizados do Volume Purchase Program for Business especificados no iTunes Connect. Estes membros do VPP for Business podem iniciar sessão na Loja de Aplicações do Volume Purchase Program e comprar as suas aplicações. As aplicações do VPP for Business compradas pelo utilizador final irão sincronizar com os respetivos inquilinos do Intune.

## <a name="before-you-start"></a>Antes de começar
Antes de começar, tem de obter um token VPP da Apple e carregá-lo para a sua conta do Intune. Além disso, deve compreender os seguintes critérios:

* Pode associar múltiplos tokens VPP à sua conta do Intune.
* Se tiver utilizado anteriormente um token VPP com outro produto, tem de gerar um novo token para utilizar com o Intune.
* Cada token é válido durante um ano.
* Por predefinição, o Intune sincroniza-se com o serviço Apple VPP duas vezes por dia. Pode iniciar uma sincronização manual em qualquer altura.
* Antes de começar a utilizar o Apple VPP com o Intune, remova as contas de utilizador do VPP existentes criadas com outros fornecedores de gestão de dispositivos móveis (MDM). O Intune não sincroniza essas contas de utilizador no serviço como medida de segurança. O Intune só sincroniza os dados do serviço Apple VPP que foram criados pelo Intune.
* O Intune suporta a adição de até 256 tokens VPP.
* O programa de Perfil de Inscrição de Dispositivos (DEP) da Apple automatiza a inscrição da gestão de dispositivos móveis (MDM). Com o DEP, pode configurar dispositivos de empresa sem lhes tocar. Pode inscrever-se no programa de DEP com a mesma conta de agente de programa que utilizou com o VPP da Apple. O ID do Programa de Implementação da Apple é exclusivo para os programas listados no site de [Programas de Implementação da Apple](https://deploy.apple.com) e não pode ser utilizado para iniciar sessão nos serviços da Apple, tais como a Loja do iTunes.
* Ao atribuir aplicações VPP com o modelo de licenciamento de utilizadores a utilizadores ou dispositivos (com a afinidade de utilizador), cada utilizador do Intune tem de estar associado a um endereço de e-mail ou ID Apple exclusivo quando aceitar os termos e condições da Apple no respetivo dispositivo.
* Certifique-se de que, ao configurar um dispositivo para um novo utilizador do Intune, o configura com o endereço de e-mail ou ID Apple exclusivo desse utilizador. O endereço de e-mail ou ID Apple e o utilizador do Intune formam um par exclusivo e podem ser utilizados em até cinco dispositivos.
* Um token VPP só é suportado para utilização numa conta do Intune de cada vez. Não reutilize um token VPP em múltiplos inquilinos do Intune.

>[!IMPORTANT]
>Após importar o token VPP para o Intune, não importe o mesmo token para nenhuma outra solução de gestão de dispositivos. Se o fizer, pode perder atribuições de licenças e registos de utilizadores.

## <a name="to-get-and-upload-an-apple-vpp-token"></a>Para obter e carregar um token Apple VPP

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços** > **Intune**. O Intune encontra-se na secção **Monitorização + Gestão**.
3.  No painel **Intune**, selecione **Aplicações do cliente** > **Tokens iOS VPP** em **Configurar**.
4.  No painel da lista de tokens VPP, selecione **Criar**.
5. No painel **Criar token VPP**, especifique as seguintes informações:
    - **Ficheiro de token VPP** – se ainda não o fez, inscreva-se no Volume Purchase Program for Business ou no Volume Purchase Program for Education. Após a inscrição, transfira o token VPP da Apple para a sua conta e selecione-o aqui.
    - **ID Apple** – Introduza o ID Apple da conta associada ao programa de compra em volume.
    - **Pais/Região** – selecione a loja do país do VPP.  O Intune sincroniza as aplicações VPP para todas as regiões a partir da loja do país do VPP especificada.
        > [!WARNING]  
        > Alterar o país irá atualizar o URL da loja e os metadados das aplicações na próxima sincronização com o serviço da Apple para aplicações criadas com este token. A aplicação não será atualizada se não existir na loja do novo país.

    - **Tipo de conta VPP** – Escolha entre **Empresas** ou **Educação**.
    - **Atualizações automáticas da aplicação** – selecione **Ativado** ou **Desativado** para ativar as atualizações automáticas. Quando ativado, o Intune deteta as atualizações de aplicações VPP no interior da loja de aplicações e emite-as automaticamente para o dispositivo quando este entra. As atualizações automáticas da aplicação para aplicações VPP da Apple irão atualizar automaticamente apenas as aplicações implementadas com intenção de instalação **Necessária**. Para aplicações implementadas com intenção de instalação **Disponível**, a atualização automática gera uma notificação para o utilizador (o administrador) informando-o de que está disponível uma versão nova da aplicação. O utilizador tem de clicar em instalar para instalar a versão mais recente da aplicação. Além disso, o utilizador irá ver que a aplicação está como não instalada no Portal da Empresa, mesmo que esteja instalada uma versão anterior da aplicação. Neste caso, o utilizador pode reinstalar a aplicação.
    
        > [!NOTE]
        > As atualizações automáticas da aplicação funcionam em aplicações licenciadas para o dispositivo e o utilizador para o iOS Versão 11.0 e versões superiores.
6. Quando tiver terminado, selecione **Criar**.

O token é apresentado no painel da lista de tokens.

Pode sincronizar os dados retidos pela Apple com o Intune em qualquer altura, selecionando **Sincronizar agora**.

## <a name="to-assign-a-volume-purchased-app"></a>Para atribuir uma aplicação comprada em volume

1.  No painel **Intune**, selecione **Aplicações do cliente** > **Aplicações** em **Gerir**.
2.  No painel da lista de aplicações, selecione aquela que pretende atribuir e, em seguida, selecione **Atribuições**.
3.  No painel ***Nome da aplicação*** - **Atribuições**, selecione **Adicionar grupo** e, em seguida, no painel **Adicionar grupo**, selecione um **Tipo de atribuição** e selecione o utilizador ou grupos de dispositivos do Azure AD aos quais pretende atribuir a aplicação.
5.  Para cada grupo que escolheu, selecione as seguintes definições:
    - **Tipo** – decida se a aplicação estará **Disponível** (os utilizadores finais podem instalar a aplicação a partir do Portal da Empresa) ou será **Obrigatória** (a aplicação será automaticamente instalada nos dispositivos dos utilizadores finais).
    - **Tipo de licença** – escolha entre o **Licenciamento de utilizadores** e o **Licenciamento de dispositivos**.
6.  Assim que tiver terminado, escolha **Guardar**.


>[!NOTE]
>A lista de aplicações apresentada está associada a um token. Se tiver uma aplicação que está associada a múltiplos tokens VPP, verá a mesma aplicação apresentada múltiplas vezes (uma para cada token).

## <a name="end-user-prompts-for-vpp"></a>Pedidos de Utilizador Final de VPP

O utilizador final irá receber pedidos de instalação de aplicações VPP em vários cenários. A seguinte tabela explica cada condição:

| # | Cenário                                | Convite para Apple VPP                              | Pedido de instalação da aplicação | Pedido de ID Apple |
|---|--------------------------------------------------|-------------------------------------------------------------------------------------------------|---------------------------------------------|-----------------------------------|
| 1 | BYOD – utilizador com licença                             | S                                                                                               | S                                           | S                                 |
| 2 | Corp – utilizador com licença (dispositivo não supervisionado)     | S                                                                                               | S                                           | S                                 |
| 3 | Corp – utilizador com licença (dispositivo supervisionado)         | S                                                                                               | N                                           | S                                 |
| 4 | BYOD – dispositivo com licença                           | N                                                                                               | S                                           | N                                 |
| 5 | CORP – dispositivo com licença (dispositivo não supervisionado)                           | N                                                                                               | S                                           | N                                 |
| 6 | CORP – dispositivo com licença (dispositivo supervisionado)                           | N                                                                                               | N                                           | N                                 |
| 7 | Modo de local público (dispositivo supervisionado) – dispositivo com licença | N                                                                                               | N                                           | N                                 |
| 8 | Modo de local público (dispositivo supervisionado) – utilizador com licença   | --- | ---                                          | ---                                |

> [!Note]  
> Não é recomendável atribuir aplicações VPP a dispositivos no modo de local público com licenciamento de utilizadores do VPP.

## <a name="revoking-app-licenses-and-deleting-tokens"></a>Revogar licenças de aplicações e eliminar tokens 

Pode revogar todas as licenças de aplicações VPP (programa de compras em volume) para iOS associadas com base num determinado dispositivo, utilizador ou aplicação. Pode notificar os utilizadores quando uma aplicação já não estiver atribuída aos mesmos. Revogar a licença de uma aplicação não desinstala a aplicação VPP relacionada do dispositivo. Para desinstalar uma aplicação VPP e recuperar a licença de uma aplicação atribuída a um utilizador ou dispositivo, tem de alterar a ação de atribuição para **Desinstalar**. Ao remover uma aplicação que foi atribuída a um utilizador, o Intune recupera a licença do dispositivo ou utilizador e desinstala a aplicação do dispositivo. A contagem de licenças recuperadas será refletida no nó **Aplicações Licenciadas** na carga de trabalho **Aplicação** do Intune. Assim que uma aplicação VPP for desinstalada e a licença da aplicação for recuperada, pode optar por atribuir a licença da aplicação a outro utilizador ou dispositivo. 

>[!NOTE]
>O Intune irá obter todas as licenças de aplicações VPP para iOS quando um funcionário sair da empresa e já não fizer parte dos grupos do AAD.

<!-- 820879 -->  
Pode eliminar um token VPP (Programa Comprado em Volume) para iOS através da consola. Tal poderá ser preciso quando tiver ocorrências duplicadas de um token de VPP. Eliminar um token irá eliminar também todas as atribuições e aplicações associadas. No entanto, eliminar um token não revoga as licenças das aplicações nem desinstala as aplicações. 

>[!NOTE]
>O Intune não pode revogar licenças de aplicações após um token ser eliminado. 

<!-- 820870 -->  
Para revogar a licença de todas as aplicações VPP de um determinado token VPP, tem de revogar primeiro todas as licenças de aplicações associadas ao token e, em seguida, eliminar o token.

## <a name="renewing-app-licenses"></a>Renovar licenças de aplicação

Pode renovar um token de VPP da Apple ao transferir um novo token a partir do portal do Programa de Compras em Volume da Apple e atualizar o token existente no Intune.

## <a name="deleting-an-ios-vpp-app"></a>Eliminar uma aplicação VPP do iOS

Atualmente, não é possível eliminar uma aplicação VPP do iOS no Microsoft Intune.

## <a name="additional-information"></a>Informações adicionais

Quando um utilizador com um dispositivo elegível tenta instalar uma aplicação do VPP num dispositivo pela primeira vez, é-lhe pedido para aderir ao Apple Volume Purchase Program. O utilizador tem de o fazer antes de continuar a instalação da aplicação. O convite para aderir ao Apple Volume Purchase Program exige que o utilizador possa utilizar a aplicação iTunes no dispositivo iOS. Se tiver definido uma política para desativar a aplicação da Loja do iTunes, o licenciamento baseado no utilizador para aplicações VPP não funciona. A solução é permitir a aplicação iTunes ao remover a política ou utilizar o licenciamento baseado no dispositivo.

A Apple fornece assistência direta para criar e renovar tokens VPP. Para obter mais informações, veja [Distribuir conteúdos pelos utilizadores com o Volume Purchase Program (VPP)](https://go.microsoft.com/fwlink/?linkid=2014661) como parte da documentação da Apple. 

Se **Atribuído ao MDM externo** for indicado no portal do Intune, o Administrador tem de remover o token VPP da MDM de terceiros antes de utilizar o token VPP no Intune.

## <a name="frequently-asked-questions"></a>Perguntas mais frequentes

#### <a name="how-long-does-the-portal-take-to-update-the-license-count-once-an-app-is-installed-or-removed-from-the-device"></a>Quanto tempo demora o portal a atualizar a contagem de licenças depois de uma aplicação ser instalada ou removida do dispositivo?
A licença deverá ser atualizada dentro de algumas horas após a instalação ou desinstalação de uma aplicação. Tenha em atenção que mesmo se o utilizador final remover a aplicação do dispositivo, a licença continuará atribuída a esse utilizador ou dispositivo.

#### <a name="is-it-possible-to-oversubscribe-an-app-and-if-so-in-what-circumstance"></a>É possível exceder as capacidades de subscrição de uma aplicação e em que circunstâncias poderia isso acontecer?
Sim. O administrador do Intune pode exceder as capacidades de subscrição de uma aplicação. Por exemplo, se o administrador adquirir 100 licenças para a aplicação XYZ e, em seguida, direcionar a aplicação para um grupo com 500 membros. Os primeiros 100 membros (utilizadores ou dispositivos) irão ter uma licença atribuída, mas a atribuição de licenças aos restantes membros falhará.

#### <a name="i-understand-intune-automatically-syncs-app-licenses-each-day-with-apple-is-that-correct"></a>É verdade que o Intune sincroniza automaticamente as licenças de aplicação com a Apple todos os dias?
O Intune sincroniza as licenças de aplicação com a Apple duas vezes por dia.

## <a name="next-steps"></a>Passos seguintes

Veja [Como monitorizar aplicações](apps-monitor.md) para obter informações que o ajudam a monitorizar as atribuições de aplicações.
