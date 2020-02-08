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
ms.openlocfilehash: d965ac35719d809ab922d28f76dec1754e9a4c6b
ms.sourcegitcommit: 9b29478f815e10c46c8030abe0146d601ce0e28c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/06/2020
ms.locfileid: "77051631"
---
# <a name="how-to-manage-ios-and-macos-apps-purchased-through-apple-volume-purchase-program-with-microsoft-intune"></a>Como gerenciar aplicativos iOS e macOS adquiridos por meio de Apple Volume Purchase Program com Microsoft Intune


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

A Apple permite-lhe adquirir várias licenças para uma aplicação que pretende utilizar na sua organização em dispositivos iOS e macOS utilizando o [Apple Business Manager](https://business.apple.com/) ou o Apple School [Manager](https://school.apple.com/). Depois disso, pode sincronizar as informações de compra em volume com o Intune e controlar a utilização da aplicação comprada em volume. A compra de licenças de aplicativos ajuda você a gerenciar aplicativos de forma eficiente em sua empresa e a manter a propriedade e o controle de aplicativos comprados. 

Microsoft Intune ajuda a gerenciar aplicativos adquiridos por meio deste programa:

- Sincronização de tokens de local que você baixa do Apple Business Manager.
- Acompanhando quantas licenças estão disponíveis e foram usadas para aplicativos comprados.
- Ajudando você a instalar aplicativos até o número de licenças que possui.

Além disso, você pode sincronizar, gerenciar e atribuir livros adquiridos por meio do Apple Business Manager com o Intune para dispositivos iOS. Para obter mais informações, veja [Como gerir eBooks do iOS comprados através de um programa de compra em volume](vpp-ebooks-ios.md).

## <a name="what-are-location-tokens"></a>O que são tokens de localização?
Os tokens de localização também são conhecidos como tokens do VPP (Volume Purchase Program). Esses tokens são usados para atribuir e gerenciar licenças adquiridas usando o Apple Business Manager. Os gerenciadores de conteúdo podem comprar e associar licenças com tokens de localização aos quais têm permissões no Apple Business Manager. Esses tokens de localização são então baixados do Apple Business Manager e carregados no Microsoft Intune. O Microsoft Intune dá suporte ao carregamento de vários tokens de local por locatário. Cada token é válido durante um ano.

## <a name="how-are-purchased-apps-licensed"></a>Como os aplicativos adquiridos são licenciados?
Os aplicativos comprados podem ser atribuídos a grupos usando dois tipos de licenças que a Apple oferece para dispositivos iOS e macOS.

|   | Licenciamento de dispositivo | Licenciamento do Utilizador |
|-----|------------------|----------------|
| **Inscrição na App Store** | Não é necessário. | Cada usuário final deve usar uma ID da Apple exclusiva quando solicitado a entrar na loja de aplicativos. |
| **Configuração do dispositivo bloqueando o acesso à App Store** | Os aplicativos podem ser instalados e atualizados usando Portal da Empresa. | O convite para ingressar no Apple VPP requer acesso à loja de aplicativos. Se você tiver definido uma política para desabilitar a loja de aplicativos, o licenciamento do usuário para aplicativos VPP não funcionará. |
| **Atualização automática de aplicativos** | Tal como configurado pela administração Intune nas definições de token Apple VPP onde é **necessário**o tipo de **atribuição** da aplicação . <br> <br> Se o tipo de **atribuição** estiver **disponível para dispositivos matriculados,** as atualizações de aplicações disponíveis podem ser instaladas a partir do Portal da Empresa. | Conforme configurado pelo usuário final nas configurações pessoais da loja de aplicativos. Isso não pode ser gerenciado pelo administrador do Intune. |
| **Inscrição do Utilizador** | Não suportada. | Com suporte usando IDs da Apple gerenciadas. |
| **Livros** | Não suportada. | Suportado. |
| **Licenças utilizadas** | 1 licença por dispositivo. A licença está associada ao dispositivo. | 1 licença para até 5 dispositivos usando a mesma ID pessoal da Apple. A licença está associada ao usuário. <br> <br> Um usuário final associado a uma ID pessoal da Apple e uma ID da Apple gerenciada no Intune consome duas licenças de aplicativo.|
| **Migração de licenças** | Os aplicativos podem migrar silenciosamente de licenças de usuário para dispositivo. | Os aplicativos não podem migrar de licenças de dispositivo para usuário. |

> [!NOTE]  
> Portal da Empresa não mostra aplicativos licenciados para dispositivos em dispositivos de registro do usuário porque somente aplicativos licenciados pelo usuário podem ser instalados em dispositivos de registro do usuário.

## <a name="what-app-types-are-supported"></a>Quais tipos de aplicativos têm suporte?
Você pode comprar e distribuir aplicativos públicos e privados usando o Apple Business Manager.
- **Aplicativos de loja:** Utilizando o Apple Business Manager, os Gestores de Conteúdos podem comprar aplicações gratuitas e pagas que estejam disponíveis na App Store.
- **Aplicativos personalizados:** Utilizando o Apple Business Manager, os Gestores de Conteúdos também podem comprar Aplicações Personalizadas disponibilizadas em privado para a sua organização. Esses aplicativos são adaptados às necessidades específicas de sua organização pelos desenvolvedores com os quais você trabalha diretamente. Saiba mais sobre [como distribuir Aplicativos Personalizados.](https://developer.apple.com/business/custom-apps/)

## <a name="prerequisites"></a>Pré-requisitos
- Um [Gestor de Negócios da Apple](https://business.apple.com/) ou O Gestor da Apple [School](https://school.apple.com/) conta para a sua organização. 
- Licenças de aplicativo adquiridas atribuídas a um ou mais tokens de local. 
- Tokens de local baixados. 

> [!IMPORTANT]
> - Um token de local só pode ser usado com uma solução de gerenciamento de dispositivo de cada vez. Antes de começar a usar aplicativos comprados com o Intune, revogue e remova qualquer token de local existente usado com outro fornecedor de MDM (gerenciamento de dispositivo móvel). 
> - Um token de local só tem suporte para uso em um locatário do Intune por vez. Não reutilize o mesmo token para vários locatários do Intune.
> - Por padrão, o Intune sincroniza os tokens de localização com a Apple duas vezes por dia. Você pode iniciar uma sincronização manual a qualquer momento no Intune.
> - Depois de importar o token de localização para o Intune, não importe o mesmo token para qualquer outra solução de gerenciamento de dispositivo. Se o fizer, pode perder atribuições de licenças e registos de utilizadores.

## <a name="migrate-from-volume-purchase-program-vpp-to-apps-and-books"></a>Migrar do VPP (programa de compra de volume) para aplicativos e livros
Se a sua organização ainda não emigrou para o Apple Business Manager ou Apple School Manager, reveja as [orientações da Apple sobre a migração para Apps e Livros](https://support.apple.com/HT208257) antes de continuar a gerir aplicações adquiridas no Intune.

> [!IMPORTANT]
> - Para obter a melhor experiência de migração, migre apenas um comprador VPP por local. Se cada comprador migrar para um local exclusivo, todas as licenças — atribuídas e não atribuídas — mudarão para aplicativos e livros.
> - Não exclua o token VPP herdado existente no Intune ou em aplicativos e atribuições associadas ao token VPP herdado existente no Intune. Essas ações exigirão que todas as atribuições de aplicativo sejam recriadas no Intune.

Migre o conteúdo e os tokens de VPP adquiridos existentes para aplicativos e livros no Apple Business Manager ou Apple School Manager da seguinte maneira:

1. Convide compradores VPP para ingressar na sua organização e direcionar cada usuário para selecionar um local exclusivo. 
2. Verifique se todos os compradores do VPP na sua organização concluíram a etapa 1 antes de continuar.
3. Verifique se todos os aplicativos e licenças adquiridos foram migrados para aplicativos e livros no Apple Business Manager ou Apple School Manager.
4. Descarregue o novo token de localização indo para **apple business (ou school) Manager** > **Definições** > **Apps and Books** > My Server **Tokens**.
5. Atualização da localização token no Microsoft Endpoint Manager Admin Center indo para a **administração de inquilinos** > **Conectores e tokens** > **tokens Apple VPP** e sincronizar o token.

## <a name="upload-an-apple-vpp-or-location-token"></a>Carregar um token de localização ou VPP da Apple

1. Inscreva-se no [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).
3. Selecione **a administração do Tenant** > **Conectores e fichas** > **fichas Apple VPP.**
4. No painel da lista de tokens VPP, selecione **Criar**.
5. No painel **Criar token VPP**, especifique as seguintes informações:
    - **Arquivo de fichas VPP** - Se ainda não o fez, inscreva-se no Apple Business Manager ou no Apple School Manager. Após a inscrição, transfira o token VPP da Apple para a sua conta e selecione-o aqui.
    - **Apple ID** - Introduza o ID da Apple gerido da conta associada ao token carregado.
    - **Assuma o controlo do símbolo de outro MDM** - Definindo esta opção para **sim** permite que o símbolo seja reatribuído a Intune a partir de outra solução DEMDM.
    - **Token Name** - Um campo administrativo para definir o nome do símbolo.    
    - **País/Região** - Selecione a loja país/região vPP.  O Intune sincroniza aplicativos VPP para todas as localidades do repositório de país/região do VPP especificado.
        > [!WARNING]  
        > A alteração do país/região atualizará os metadados dos aplicativos e a URL da loja de aplicativos na próxima sincronização com o serviço Apple para aplicativos criados com esse token. O aplicativo não será atualizado se não existir no novo armazenamento de país/região.

    - **Tipo de conta VPP** – Escolha entre **Empresas** ou **Educação**.
    - **Atualizações automáticas da aplicação** – selecione **Ativado** ou **Desativado** para ativar as atualizações automáticas. Quando ativado, o Intune deteta as atualizações de aplicações VPP no interior da loja de aplicações e emite-as automaticamente para o dispositivo quando este entra. 
        
        > [!NOTE] 
        > As atualizações automáticas da aplicação para aplicações VPP da Apple irão atualizar automaticamente apenas as aplicações implementadas com intenção de instalação **Necessária**. Para aplicações implementadas com a intenção de instalação **disponível,** a atualização automática gera uma mensagem de estado para o administrador de TI informando que uma nova versão da aplicação está disponível. Essa mensagem de status é visível selecionando o aplicativo, selecionando status de instalação do dispositivo e verificando os detalhes do status.  

    - **Concedo à Microsoft permissão para enviar informações de utilizador e dispositivo saqueadas para a Apple.** - Deve selecionar **que concordo em** prosseguir. Para rever os dados que a Microsoft envia para a Apple, consulte [data Intune envia para a Apple](~/protect/data-intune-sends-to-apple.md).

6. Quando tiver terminado, selecione **Criar**. O token é apresentado no painel da lista de tokens.

## <a name="synchronize-a-vpp-token"></a>Sincronizar um token VPP
Pode sincronizar os nomes das aplicações, metadados e informações de licença para as suas aplicações adquiridas em Intune, escolhendo **o Sync** para um token selecionado.

## <a name="assign-a-volume-purchased-app"></a>Atribuir um aplicativo adquirido por volume

1. Selecione **Apps** > **Todas as aplicações.**
2. No painel da lista de aplicações, selecione aquela que pretende atribuir e, em seguida, selecione **Atribuições**.
3. No painel **Nome da aplicação** - **Atribuições**, selecione **Adicionar grupo** e, em seguida, no painel **Adicionar grupo**, selecione um **Tipo de atribuição** e selecione o utilizador ou grupos de dispositivos do Azure AD aos quais pretende atribuir a aplicação.
5. Para cada grupo que escolheu, selecione as seguintes definições:
    - **Tipo** – decida se a aplicação estará **Disponível** (os utilizadores finais podem instalar a aplicação a partir do Portal da Empresa) ou será **Obrigatória** (a aplicação será automaticamente instalada nos dispositivos dos utilizadores finais).
    - **Tipo de licença** – escolha entre o **Licenciamento de utilizadores** e o **Licenciamento de dispositivos**.
6. Assim que tiver terminado, escolha **Guardar**.


>[!NOTE]
>A intenção Implementação disponível não é suportada para grupos de dispositivos, apenas os grupos de utilizadores são suportados. A lista de aplicações apresentada está associada a um token. Se tiver uma aplicação que está associada a múltiplos tokens VPP, verá a mesma aplicação apresentada múltiplas vezes (uma para cada token).

> [!NOTE]  
> Intune (ou qualquer outro MDM) não instala aplicações VPP. Em vez disso, a Intune liga-se à sua conta VPP e diz à Apple quais as licenças de aplicação para atribuir a que dispositivos. A partir daí, toda a instalação real é manuseada entre a Apple e o dispositivo.
> 
> [Referência do Protocolo apple MDM, página 135](https://developer.apple.com/business/documentation/MDM-Protocol-Reference.pdf)

## <a name="end-user-prompts-for-vpp"></a>Pedidos de Utilizador Final de VPP

O utilizador final irá receber pedidos de instalação de aplicações VPP em vários cenários. A seguinte tabela explica cada condição:

| # | Cenário                                | Convite para Apple VPP                              | Pedido de instalação da aplicação | Pedido de ID Apple |
|---|--------------------------------------------------|-------------------------------------------------------------------------------------------------|---------------------------------------------|-----------------------------------|
| 1 | BYOD – usuário licenciado (não dispositivo de registro de usuário)                             | S                                                                                               | S                                           | S                                 |
| 2 | Corp – utilizador com licença (dispositivo não supervisionado)     | S                                                                                               | S                                           | S                                 |
| 3 | Corp – utilizador com licença (dispositivo supervisionado)         | S                                                                                               | N                                           | S                                 |
| 4 | BYOD – dispositivo com licença                           | N                                                                                               | S                                           | N                                 |
| 5 | CORP – dispositivo com licença (dispositivo não supervisionado)                           | N                                                                                               | S                                           | N                                 |
| 6 | CORP – dispositivo com licença (dispositivo supervisionado)                           | N                                                                                               | N                                           | N                                 |
| 7 | Modo de local público (dispositivo supervisionado) – dispositivo com licença | N                                                                                               | N                                           | N                                 |
| 8 | Modo de local público (dispositivo supervisionado) – utilizador com licença   | --- | ---                                          | ---                                |

> [!Note]  
> Não é recomendável atribuir aplicativos VPP a dispositivos de modo de quiosque usando o licenciamento do usuário.

## <a name="revoking-app-licenses"></a>Revogando licenças de aplicativo

Você pode revogar todas as licenças de aplicativo VPP (programa de compra por volume) do iOS ou macOS com base em um determinado dispositivo, usuário ou aplicativo.  Mas há algumas diferenças entre as plataformas iOS e macOS. 

|   | iOS | macOS |
|-----|------------------|----------------|
| **Remover a atribuição de aplicativos** | Ao remover uma aplicação que foi atribuída a um utilizador, o Intune recupera a licença do dispositivo ou utilizador e desinstala a aplicação do dispositivo. | Quando você remove um aplicativo que foi atribuído a um usuário, o Intune recupera a licença de usuário ou dispositivo. O aplicativo não é desinstalado do dispositivo. |
| **Revogar licença de aplicação** | Revogar uma licença de aplicativo recupera a licença do aplicativo do usuário ou do dispositivo. Tem de alterar a atribuição para **Desinstalar** para remover a aplicação do dispositivo. | Revogar uma licença de aplicativo recupera a licença do aplicativo do usuário ou do dispositivo. O aplicativo macOS com licença revogada permanece utilizável no dispositivo, mas não pode ser atualizado até que uma licença seja reatribuída ao usuário ou dispositivo. De acordo com a Apple, esses aplicativos são removidos após um período de carência de 30 dias. No entanto, a Apple não fornece um meio para o Intune remover o aplicativo usando a ação de atribuição de desinstalação.

>[!NOTE]
> - O Intune recupera licenças de aplicativo quando um funcionário sai da empresa e não faz mais parte dos grupos do AAD.
> - Ao atribuir uma aplicação adquirida com intenção **de Desinstalar,** intune tanto reclama a licença como desinstala a app.
> - As licenças de aplicativo não são recuperadas quando um dispositivo é removido do gerenciamento do Intune. 

## <a name="deleting-vpp-tokens"></a>Excluindo tokens VPP
<!-- 820879 -->  
Você pode excluir um token VPP (programa de compra por volume) da Apple usando o console do. Tal poderá ser preciso quando tiver ocorrências duplicadas de um token de VPP. Eliminar um token irá eliminar também todas as atribuições e aplicações associadas. No entanto, eliminar um token não revoga as licenças das aplicações nem desinstala as aplicações. 

>[!NOTE]
>O Intune não pode revogar licenças de aplicações após um token ser eliminado. 

<!-- 820870 -->  
Para revogar a licença de todas as aplicações VPP de um determinado token VPP, tem de revogar primeiro todas as licenças de aplicações associadas ao token e, em seguida, eliminar o token.

## <a name="renewing-app-licenses"></a>Renovar licenças de aplicação

Você pode renovar um token de VPP da Apple baixando um novo token do Apple Business Manager ou Apple School Manager e atualizando o token existente no Intune.

## <a name="deleting-a-vpp-app"></a>Excluindo um aplicativo VPP

Atualmente, não é possível eliminar uma aplicação VPP do iOS no Microsoft Intune.

## <a name="assigning-custom-role-permissions-for-vpp"></a>Atribuindo permissões de função personalizada para VPP

O acesso a tokens de VPP da Apple e aplicativos de VPP pode ser controlado independentemente usando permissões atribuídas a funções de administrador personalizadas no Intune.

* Para permitir uma função personalizada intune para gerir tokens Apple VPP em **Apps** > **tokens Apple VPP**, atribuir permissões para **aplicações geridas**.
* Para permitir uma função personalizada intune para gerir aplicações adquiridas usando tokens iOS VPP em **Apps** > **Todas as aplicações**, atribuir permissões para **aplicações Móveis.** 

## <a name="additional-information"></a>Informações adicionais

A Apple fornece assistência direta para criar e renovar tokens VPP. Para obter mais informações, veja [Distribuir conteúdos pelos utilizadores com o Volume Purchase Program (VPP)](https://go.microsoft.com/fwlink/?linkid=2014661) como parte da documentação da Apple. 

Se **Atribuído ao MDM externo** for indicado no portal do Intune, o Administrador tem de remover o token VPP da MDM de terceiros antes de utilizar o token VPP no Intune.

## <a name="frequently-asked-questions"></a>Perguntas mais frequentes

### <a name="how-many-tokens-can-i-upload"></a>Quantos tokens posso carregar?
Você pode carregar até 3.000 tokens no Intune.

### <a name="how-long-does-the-portal-take-to-update-the-license-count-once-an-app-is-installed-or-removed-from-the-device"></a>Quanto tempo demora o portal a atualizar a contagem de licenças depois de uma aplicação ser instalada ou removida do dispositivo?
A licença deverá ser atualizada dentro de algumas horas após a instalação ou desinstalação de uma aplicação. Tenha em atenção que mesmo se o utilizador final remover a aplicação do dispositivo, a licença continuará atribuída a esse utilizador ou dispositivo.

### <a name="is-it-possible-to-oversubscribe-an-app-and-if-so-in-what-circumstance"></a>É possível exceder as capacidades de subscrição de uma aplicação e em que circunstâncias poderia isso acontecer?
Sim. O administrador do Intune pode exceder as capacidades de subscrição de uma aplicação. Por exemplo, se o administrador adquirir 100 licenças para a aplicação XYZ e, em seguida, direcionar a aplicação para um grupo com 500 membros. Os primeiros 100 membros (utilizadores ou dispositivos) irão ter uma licença atribuída, mas a atribuição de licenças aos restantes membros falhará.


## <a name="next-steps"></a>Próximos passos

Veja [Como monitorizar aplicações](apps-monitor.md) para obter informações que o ajudam a monitorizar as atribuições de aplicações.

Veja [como resolver aplicações](~/apps/troubleshoot-app-install.md) para obter informações sobre problemas relacionados com aplicações.
