---
title: Gerenciar aplicativos Apple adquiridos por volume
titleSuffix: Microsoft Intune
description: Saiba mais sobre como você pode sincronizar aplicativos comprados em volume da loja de aplicativos iOS e macOS no Microsoft Intune e, em seguida, gerenciar e controlar seu uso.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/17/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 51d45ce2-d81b-4584-8bc4-568c8c62653d
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 01c95e1961871f33a3d8ed8c0b6c22502faca3a9
ms.sourcegitcommit: 8d7406b75ef0d75cc2ed03b1a5e5f74ff10b98c0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/03/2020
ms.locfileid: "75654027"
---
# <a name="how-to-manage-ios-and-macos-apps-purchased-through-apple-volume-purchase-program-with-microsoft-intune"></a>Como gerenciar aplicativos iOS e macOS adquiridos por meio de Apple Volume Purchase Program com Microsoft Intune


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

A Apple permite que você compre várias licenças para um aplicativo que você deseja executar em sua empresa em dispositivos iOS e macOS. A compra de várias cópias ajuda-o a gerir aplicações na sua empresa de forma eficiente.

O Microsoft Intune ajuda-o a gerir várias cópias de aplicações compradas através desse programa ao:

- Comunicar informações sobre a licença a partir da App Store.
- Controlar o número de licenças que utilizou.
- Ajudá-lo a não instalar mais cópias da aplicação do que as que tem.

Existem dois métodos que pode utilizar para atribuir as aplicações compradas em volume:

## <a name="device-licensing"></a>Licenciamento de dispositivos

Quando atribui uma aplicação a dispositivos, é utilizada uma licença de aplicação que permanece associada ao dispositivo ao qual foi atribuída.

Quando atribui aplicações compradas em volume a um dispositivo, o utilizador final do dispositivo não tem de fornecer um ID Apple para aceder à loja.

## <a name="user-licensing"></a>Licenciamento de utilizadores

Quando atribui uma aplicação a um utilizador, é utilizada uma licença de aplicação que é associada ao utilizador. O aplicativo pode ser executado em até 5 dispositivos que o usuário possui (o limite do dispositivo é controlado pela Apple).

Ao atribuir uma aplicação comprada em volume a utilizadores, cada utilizador final tem de ter um ID Apple exclusivo válido para aceder à App Store.

Além disso, você pode sincronizar, gerenciar e atribuir livros adquiridos no repositório VPP (programa de compra por volume) da Apple com o Intune para dispositivos iOS. Para obter mais informações, veja [Como gerir eBooks do iOS comprados através de um programa de compra em volume](vpp-ebooks-ios.md).

## <a name="manage-volume-purchased-apps-for-ios-and-macos-devices"></a>Gerenciar aplicativos adquiridos por volume para dispositivos iOS e macOS

### <a name="supports-apple-volume-purchase-program-volume-purchased-apps"></a>Dá suporte a Apple Volume Purchase Program aplicativos adquiridos por volume

Compre várias licenças para aplicativos iOS e macOS por meio do [Apple Volume Purchase Program for Business](https://www.apple.com/business/vpp/) ou da [Apple Volume Purchase Program para educação](https://volume.itunes.apple.com/us/store). Este processo envolve configurar uma conta VPP da Apple no site da Apple e carregar o token VPP da Apple para o Intune.  Depois disso, pode sincronizar as informações de compra em volume com o Intune e controlar a utilização da aplicação comprada em volume.

### <a name="supports-business-to-business-volume-purchased-apps"></a>Dá suporte a aplicativos comprados por volume entre empresas

Além disso, os desenvolvedores de terceiros também podem distribuir de forma privada aplicativos ao programa de compra por volume autorizado para membros comerciais especificados no App Store Connect. Estes membros do VPP for Business podem iniciar sessão na Loja de Aplicações do Volume Purchase Program e comprar as suas aplicações. As aplicações do VPP for Business compradas pelo utilizador final irão sincronizar com os respetivos inquilinos do Intune.

## <a name="before-you-start"></a>Antes de começar
Antes de começar, tem de obter um token VPP da Apple e carregá-lo para a sua conta do Intune. Além disso, deve compreender os seguintes critérios:

* Pode associar múltiplos tokens VPP à sua conta do Intune.
* Se tiver utilizado anteriormente um token VPP com outro produto, tem de gerar um novo token para utilizar com o Intune.
* Cada token é válido durante um ano.
* Por predefinição, o Intune sincroniza-se com o serviço Apple VPP duas vezes por dia. Pode iniciar uma sincronização manual em qualquer altura.
* Antes de começar a utilizar o Apple VPP com o Intune, remova as contas de utilizador do VPP existentes criadas com outros fornecedores de gestão de dispositivos móveis (MDM). O Intune não sincroniza essas contas de utilizador no serviço como medida de segurança. O Intune só sincroniza os dados do serviço Apple VPP que foram criados pelo Intune.
* O programa de Perfil de Inscrição de Dispositivos (DEP) da Apple automatiza a inscrição da gestão de dispositivos móveis (MDM). Com o DEP, pode configurar dispositivos de empresa sem lhes tocar. Pode inscrever-se no programa de DEP com a mesma conta de agente de programa que utilizou com o VPP da Apple. O ID do Programa de Implementação da Apple é exclusivo para os programas listados no site de [Programas de Implementação da Apple](https://deploy.apple.com) e não pode ser utilizado para iniciar sessão nos serviços da Apple, tais como a Loja do iTunes.
* Ao atribuir aplicações VPP com o modelo de licenciamento de utilizadores a utilizadores ou dispositivos (com a afinidade de utilizador), cada utilizador do Intune tem de estar associado a um endereço de e-mail ou ID Apple exclusivo quando aceitar os termos e condições da Apple no respetivo dispositivo.
* Certifique-se de que, ao configurar um dispositivo para um novo utilizador do Intune, o configura com o endereço de e-mail ou ID Apple exclusivo desse utilizador. O endereço de e-mail ou ID Apple e o utilizador do Intune formam um par exclusivo e podem ser utilizados em até cinco dispositivos.
* Um token VPP só é suportado para utilização numa conta do Intune de cada vez. Não reutilize um token VPP em múltiplos inquilinos do Intune.

>[!IMPORTANT]
>Após importar o token VPP para o Intune, não importe o mesmo token para nenhuma outra solução de gestão de dispositivos. Se o fizer, pode perder atribuições de licenças e registos de utilizadores.

## <a name="to-get-and-upload-an-apple-vpp-token"></a>Para obter e carregar um token Apple VPP

1. Entre no centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
3. Selecione **Administração de locatários** > **conectores e tokens** > **tokens de VPP da Apple**.
4. No painel da lista de tokens VPP, selecione **Criar**.
5. No painel **Criar token VPP**, especifique as seguintes informações:
    - **Ficheiro de token VPP** – se ainda não o fez, inscreva-se no Volume Purchase Program for Business ou no Volume Purchase Program for Education. Após a inscrição, transfira o token VPP da Apple para a sua conta e selecione-o aqui.
    - **ID Apple** – Introduza o ID Apple da conta associada ao programa de compra em volume.
    - **Assuma o controle do token de outro MDM** -definir essa opção como **Sim** permite que o token seja reatribuído ao Intune de outro MDM.
    - **Nome do token** – um campo administrativo para definir o nome do token.    
    - **País/região** -selecione o repositório de país/região do VPP.  O Intune sincroniza aplicativos VPP para todas as localidades do repositório de país/região do VPP especificado.
        > [!WARNING]  
        > A alteração do país/região atualizará os metadados dos aplicativos e a URL de armazenamento na próxima sincronização com o serviço Apple para aplicativos criados com esse token. O aplicativo não será atualizado se não existir no novo armazenamento de país/região.

    - **Tipo de conta VPP** – Escolha entre **Empresas** ou **Educação**.
    - **Atualizações automáticas da aplicação** – selecione **Ativado** ou **Desativado** para ativar as atualizações automáticas. Quando ativado, o Intune deteta as atualizações de aplicações VPP no interior da loja de aplicações e emite-as automaticamente para o dispositivo quando este entra. As atualizações automáticas da aplicação para aplicações VPP da Apple irão atualizar automaticamente apenas as aplicações implementadas com intenção de instalação **Necessária**. Para aplicativos implantados com a intenção de instalação **disponível** , o usuário verá que o aplicativo não está instalado no portal da empresa, embora uma versão anterior do aplicativo esteja instalada. Nesse caso, o usuário pode reinstalar o aplicativo clicando em **instalar** na tela de detalhes do aplicativo no aplicativo portal da empresa para instalar a versão mais recente do aplicativo. Observe que para dispositivos iOS registrados pelo usuário, os usuários finais continuarão a ver todos os aplicativos VPP licenciados pelo usuário dentro do Portal da Empresa. 

        > [!NOTE]
        > As atualizações automáticas do aplicativo funcionam para aplicativos licenciados de dispositivo e de usuário para iOS 11,0 e superior ou macOS 10,12 e superior.

    - **Eu granto a permissão da Microsoft para enviar informações do usuário e do dispositivo para a Apple.** -Você deve selecionar **concordo** para continuar. Para examinar quais dados o Microsoft envia à Apple, consulte [Data Intune SENDs to Apple](~/protect/data-intune-sends-to-apple.md).

6. Quando tiver terminado, selecione **Criar**.

O token é apresentado no painel da lista de tokens.

Pode sincronizar os dados retidos pela Apple com o Intune em qualquer altura, selecionando **Sincronizar agora**.

## <a name="to-assign-a-volume-purchased-app"></a>Para atribuir uma aplicação comprada em volume

1. Selecione **aplicativos** > **todos os aplicativos**.
2. No painel da lista de aplicações, selecione aquela que pretende atribuir e, em seguida, selecione **Atribuições**.
3. No painel ***Nome da aplicação*** - **Atribuições**, selecione **Adicionar grupo** e, em seguida, no painel **Adicionar grupo**, selecione um **Tipo de atribuição** e selecione o utilizador ou grupos de dispositivos do Azure AD aos quais pretende atribuir a aplicação.
5. Para cada grupo que escolheu, selecione as seguintes definições:
    - **Tipo** – decida se a aplicação estará **Disponível** (os utilizadores finais podem instalar a aplicação a partir do Portal da Empresa) ou será **Obrigatória** (a aplicação será automaticamente instalada nos dispositivos dos utilizadores finais).
    - **Tipo de licença** – escolha entre o **Licenciamento de utilizadores** e o **Licenciamento de dispositivos**.
6. Assim que tiver terminado, escolha **Guardar**.


>[!NOTE]
>A intenção Implementação disponível não é suportada para grupos de dispositivos, apenas os grupos de utilizadores são suportados. A lista de aplicações apresentada está associada a um token. Se tiver uma aplicação que está associada a múltiplos tokens VPP, verá a mesma aplicação apresentada múltiplas vezes (uma para cada token).

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

## <a name="revoking-app-licenses"></a>Revogando licenças de aplicativo

Você pode revogar todas as licenças de aplicativo VPP (programa de compra por volume) do iOS ou macOS com base em um determinado dispositivo, usuário ou aplicativo.  Mas há algumas diferenças entre as plataformas iOS e macOS. 

### <a name="revoking-app-licenses-on-ios"></a>Revogando licenças de aplicativo no iOS
Pode notificar os utilizadores quando uma aplicação já não estiver atribuída aos mesmos. Mas a revogação de uma licença de aplicativo não desinstalará o aplicativo VPP relacionado do dispositivo. Para desinstalar uma aplicação VPP e recuperar a licença de uma aplicação atribuída a um utilizador ou dispositivo, tem de alterar a ação de atribuição para **Desinstalar**. Ao remover uma aplicação que foi atribuída a um utilizador, o Intune recupera a licença do dispositivo ou utilizador e desinstala a aplicação do dispositivo. A contagem de licenças recuperadas será refletida no nó **Aplicações Licenciadas** na carga de trabalho **Aplicação** do Intune. Depois que um aplicativo VPP tiver sido desinstalado e a licença do aplicativo tiver sido recuperada, você poderá optar por atribuir a licença do aplicativo a outro usuário ou dispositivo.


### <a name="revoking-app-licenses-on-macos"></a>Revogando licenças de aplicativo no macOS
Revogar uma licença de aplicativo não desinstala o aplicativo VPP do dispositivo. Quando você revoga uma licença de aplicativo que foi atribuída a um usuário, o Intune recupera a licença de usuário ou dispositivo. O aplicativo macOS com licença revogada permanece utilizável no dispositivo, mas não pode ser atualizado até que uma licença seja reatribuída ao usuário ou dispositivo. De acordo com a Apple, esses aplicativos são removidos após um período de carência de 30 dias. No entanto, a Apple não fornece um meio para o Intune remover o aplicativo usando a ação de atribuição de **desinstalação** . Mas você pode optar por atribuir a licença de aplicativo recuperada a outro usuário ou dispositivo.

>[!NOTE]
>O Intune recuperará licenças de aplicativo VPP licenciadas para o usuário iOS e macOS quando um funcionário sair da empresa e não fizer mais parte dos grupos do AAD.

## <a name="deleting-vpp-tokens"></a>Excluindo tokens VPP
<!-- 820879 -->  
Você pode excluir um token VPP (programa de compra por volume) da Apple usando o console do. Tal poderá ser preciso quando tiver ocorrências duplicadas de um token de VPP. Eliminar um token irá eliminar também todas as atribuições e aplicações associadas. No entanto, eliminar um token não revoga as licenças das aplicações nem desinstala as aplicações. 

>[!NOTE]
>O Intune não pode revogar licenças de aplicações após um token ser eliminado. 

<!-- 820870 -->  
Para revogar a licença de todas as aplicações VPP de um determinado token VPP, tem de revogar primeiro todas as licenças de aplicações associadas ao token e, em seguida, eliminar o token.

## <a name="renewing-app-licenses"></a>Renovar licenças de aplicação

Pode renovar um token de VPP da Apple ao transferir um novo token a partir do portal do Programa de Compras em Volume da Apple e atualizar o token existente no Intune.

## <a name="deleting-a-vpp-app"></a>Excluindo um aplicativo VPP

Atualmente, não é possível eliminar uma aplicação VPP do iOS no Microsoft Intune.

## <a name="assigning-custom-role-permissions-for-vpp"></a>Atribuindo permissões de função personalizada para VPP

O acesso a tokens de VPP da Apple e aplicativos de VPP pode ser controlado independentemente usando permissões atribuídas a funções de administrador personalizadas no Intune.

* Para permitir que uma função personalizada do Intune gerencie tokens de VPP da Apple em **aplicativos** > **tokens de VPP da Apple**, atribua permissões para **aplicativos gerenciados**.
* Para permitir que uma função personalizada do Intune Gerencie aplicativos adquiridos usando tokens VPP do iOS em **aplicativos** > **todos os aplicativos**, atribua permissões para **aplicativos móveis**. 

## <a name="additional-information"></a>Informações adicionais

Quando um utilizador com um dispositivo elegível tenta instalar uma aplicação do VPP num dispositivo pela primeira vez, é-lhe pedido para aderir ao Apple Volume Purchase Program. O utilizador tem de o fazer antes de continuar a instalação da aplicação. O convite para ingressar no Apple Volume Purchase Program exige que o usuário possa usar o aplicativo App Store no dispositivo iOS ou macOS. Se você tiver definido uma política para desabilitar o aplicativo da App Store, o licenciamento baseado no usuário para aplicativos VPP não funcionará. A solução é permitir o aplicativo da App Store removendo a política ou usar o licenciamento baseado em dispositivo.

A Apple fornece assistência direta para criar e renovar tokens VPP. Para obter mais informações, veja [Distribuir conteúdos pelos utilizadores com o Volume Purchase Program (VPP)](https://go.microsoft.com/fwlink/?linkid=2014661) como parte da documentação da Apple. 

Se **Atribuído ao MDM externo** for indicado no portal do Intune, o Administrador tem de remover o token VPP da MDM de terceiros antes de utilizar o token VPP no Intune.

## <a name="frequently-asked-questions"></a>Perguntas mais frequentes

### <a name="how-long-does-the-portal-take-to-update-the-license-count-once-an-app-is-installed-or-removed-from-the-device"></a>Quanto tempo demora o portal a atualizar a contagem de licenças depois de uma aplicação ser instalada ou removida do dispositivo?
A licença deverá ser atualizada dentro de algumas horas após a instalação ou desinstalação de uma aplicação. Tenha em atenção que mesmo se o utilizador final remover a aplicação do dispositivo, a licença continuará atribuída a esse utilizador ou dispositivo.

### <a name="is-it-possible-to-oversubscribe-an-app-and-if-so-in-what-circumstance"></a>É possível exceder as capacidades de subscrição de uma aplicação e em que circunstâncias poderia isso acontecer?
Sim. O administrador do Intune pode exceder as capacidades de subscrição de uma aplicação. Por exemplo, se o administrador adquirir 100 licenças para a aplicação XYZ e, em seguida, direcionar a aplicação para um grupo com 500 membros. Os primeiros 100 membros (utilizadores ou dispositivos) irão ter uma licença atribuída, mas a atribuição de licenças aos restantes membros falhará.

### <a name="how-frequently-does-intune-sync-vpp-tokens-with-apple"></a>Com que frequência o Intune sincroniza tokens VPP com a Apple?
O Intune sincroniza tokens VPP e licenças duas vezes por dia com a Apple. O administrador do Intune pode iniciar uma sincronização manual em **aplicativos** > **TOKENs de VPP da Apple**.

## <a name="next-steps"></a>Próximos passos

Veja [Como monitorizar aplicações](apps-monitor.md) para obter informações que o ajudam a monitorizar as atribuições de aplicações.
