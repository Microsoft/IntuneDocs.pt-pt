---
title: Gerir aplicações compradas em volume da Apple
titleSuffix: Microsoft Intune
description: Saiba como pode sincronizar aplicações que adquiriu em volume a partir de iOS/iPadOS e macOS App Store no Microsoft Intune e, em seguida, gerir e rastrear a sua utilização.
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
ms.openlocfilehash: 9127ee06bc2125f476c18e9b8e46a127e48d0245
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/20/2020
ms.locfileid: "77513406"
---
# <a name="how-to-manage-ios-and-macos-apps-purchased-through-apple-volume-purchase-program-with-microsoft-intune"></a>Como gerir aplicações iOS e macOS adquiridas através do Apple Volume Purchase Program com a Microsoft Intune


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

A Apple permite-lhe adquirir várias licenças para uma aplicação que pretende utilizar na sua organização em dispositivos iOS/iPadOS e macOS utilizando [o Apple Business Manager](https://business.apple.com/) ou o Apple School [Manager](https://school.apple.com/). Depois disso, pode sincronizar as informações de compra em volume com o Intune e controlar a utilização da aplicação comprada em volume. Comprar licenças de aplicações ajuda-o a gerir eficientemente as aplicações dentro da sua empresa e a manter a propriedade e o controlo das aplicações adquiridas. 

O Microsoft Intune ajuda-o a gerir as aplicações adquiridas através deste programa por:

- Sincronizar a localização tokens que você descarrega do Apple Business Manager.
- Rastreando quantas licenças estão disponíveis e foram usadas para aplicações adquiridas.
- Ajudá-lo a instalar apps até ao número de licenças que possui.

Além disso, pode sincronizar, gerir e atribuir livros que adquiriu ao Apple Business Manager com o Intune para dispositivos iOS/iPadOS. Para mais informações, consulte [Como gerir os iOS/iPadOS eBooks que adquiriu através de um programa de compra de volume](vpp-ebooks-ios.md).

## <a name="what-are-location-tokens"></a>O que são fichas de localização?
As fichas de localização também são conhecidas como fichas do Programa de Compra de Volume (VPP). Estes tokens são usados para atribuir e gerir licenças adquiridas usando o Apple Business Manager. Os Gestores de Conteúdos podem adquirir e associar licenças com fichas de localização a que têm permissões no Apple Business Manager. Estes tokens de localização são então descarregados do Apple Business Manager e enviados no Microsoft Intune. O Microsoft Intune suporta o upload de várias fichas de localização por inquilino. Cada token é válido durante um ano.

## <a name="how-are-purchased-apps-licensed"></a>Como são licenciadas as aplicações adquiridas?
As aplicações adquiridas podem ser atribuídas a grupos que utilizam dois tipos de licenças que a Apple oferece para dispositivos iOS/iPadOS e macOS.

|   | Licenciamento de Dispositivos | Licenciamento do Utilizador |
|-----|------------------|----------------|
| **Inscrição na App Store** | Não é necessário. | Cada utilizador final deve utilizar um ID apple único quando solicitado para iniciar sessão na App Store. |
| **Configuração do dispositivo bloqueando o acesso à App Store** | As aplicações podem ser instaladas e atualizadas através do Portal da Empresa. | O convite para aderir à Apple VPP requer acesso à App Store. Se definiu uma política para desativar a App Store, o licenciamento de utilizadores para aplicações VPP não funcionará. |
| **Atualização automática de aplicativos** | Tal como configurado pela administração Intune nas definições de token Apple VPP onde é **necessário**o tipo de **atribuição** da aplicação . <br> <br> Se o tipo de **atribuição** estiver **disponível para dispositivos matriculados,** as atualizações de aplicações disponíveis podem ser instaladas a partir do Portal da Empresa. | Tal como configurado pelo utilizador final nas definições pessoais da App Store. Isto não pode ser gerido pela administração Intune. |
| **Inscrição do Utilizador** | Não suportada. | Suportado usando IDs de Apple geridos. |
| **Livros** | Não suportada. | Suportado. |
| **Licenças utilizadas** | 1 licença por dispositivo. A licença está associada ao dispositivo. | 1 licença para até 5 dispositivos utilizando o mesmo APPLE ID pessoal. A licença está associada ao utilizador. <br> <br> Um utilizador final associado a um Apple ID pessoal e a um ID da Apple gerido no Intune consome 2 licenças de aplicações.|
| **Migração de licenças** | As aplicações podem migrar silenciosamente de licenças de utilizador para dispositivo. | As aplicações não podem migrar de dispositivo para licenças de utilizador. |

> [!NOTE]  
> O Portal da Empresa não mostra aplicações licenciadas por dispositivos de inscrição de utilizadores, uma vez que só as aplicações licenciadas pelo utilizador podem ser instaladas em dispositivos de inscrição do utilizador.

## <a name="what-app-types-are-supported"></a>Que tipos de aplicativos são suportados?
Pode comprar e distribuir aplicações públicas e privadas utilizando o Apple Business Manager.
- **Aplicativos de loja:** Utilizando o Apple Business Manager, os Gestores de Conteúdos podem comprar aplicações gratuitas e pagas que estejam disponíveis na App Store.
- **Aplicativos personalizados:** Utilizando o Apple Business Manager, os Gestores de Conteúdos também podem comprar Aplicações Personalizadas disponibilizadas em privado para a sua organização. Estas aplicações são adaptadas às necessidades específicas da sua organização por desenvolvedores com os quais trabalha diretamente. Saiba mais sobre [como distribuir Aplicativos Personalizados.](https://developer.apple.com/business/custom-apps/)

## <a name="prerequisites"></a>Pré-requisitos
- Um [Gestor de Negócios da Apple](https://business.apple.com/) ou O Gestor da Apple [School](https://school.apple.com/) conta para a sua organização. 
- Licenças de aplicativos adquiridas atribuídas a um ou mais fichas de localização. 
- Fichas de localização descarregadas. 

> [!IMPORTANT]
> - Um símbolo de localização só pode ser usado com uma solução de gestão de dispositivode cada vez. Antes de começar a utilizar aplicações adquiridas com o Intune, revogue e remova quaisquer fichas de localização existentes utilizadas com outro fornecedor de gestão de dispositivos móveis (MDM). 
> - Um símbolo de localização só é suportado para uso em um inquilino Intune de cada vez. Não reutilize o mesmo símbolo para vários inquilinos intune.
> - Por padrão, Intune sincroniza os tokens de localização com a Apple duas vezes por dia. Pode iniciar uma sincronização manual a qualquer momento a partir de Intune.
> - Depois de ter importado a ficha de localização para Intune, não importe o mesmo símbolo para qualquer outra solução de gestão de dispositivos. Se o fizer, pode perder atribuições de licenças e registos de utilizadores.

## <a name="migrate-from-volume-purchase-program-vpp-to-apps-and-books"></a>Migrar do Programa de Compra de Volume (VPP) para Apps e Livros
Se a sua organização ainda não emigrou para o Apple Business Manager ou Apple School Manager, reveja as [orientações da Apple sobre a migração para Apps e Livros](https://support.apple.com/HT208257) antes de continuar a gerir aplicações adquiridas no Intune.

> [!IMPORTANT]
> - Para obter a melhor experiência de migração, emigrar apenas um comprador de VPP por local. Se cada comprador migrar para um local único, todas as licenças - atribuídas e não atribuídas - passarão para Apps e Livros.
> - Não elimine o token vPP existente em Intune ou aplicações e atribuições associadas ao legado existente de VPP token em Intune. Estas ações exigirão que todas as atribuições de aplicações sejam recriadas no Intune.

Migrar os conteúdos e fichas vPP adquiridos existentes para Apps e Livros no Apple Business Manager ou Apple School Manager da seguinte forma:

1. Convide os compradores de VPP a juntarem-se à sua organização e direcione cada utilizador para selecionar uma localização única. 
2. Certifique-se de que todos os compradores de VPP dentro da sua organização completaram o passo 1 antes de prosseguir.
3. Verifique se todas as aplicações e licenças adquiridas migraram para Apps e Livros no Apple Business Manager ou Apple School Manager.
4. Descarregue o novo token de localização indo para **apple business (ou school) Manager** > **Definições** > **Apps and Books** > My Server **Tokens**.
5. Atualização da localização token no Microsoft Endpoint Manager Admin Center indo para a **administração de inquilinos** > **Conectores e tokens** > **tokens Apple VPP** e sincronizar o token.

## <a name="upload-an-apple-vpp-or-location-token"></a>Faça upload de um Apple VPP ou ficha de localização

1. Inscreva-se no [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).
3. Selecione **a administração do Tenant** > **Conectores e fichas** > **fichas Apple VPP.**
4. No painel da lista de tokens VPP, selecione **Criar**.
5. No painel **Criar token VPP**, especifique as seguintes informações:
    - **Arquivo de fichas VPP** - Se ainda não o fez, inscreva-se no Apple Business Manager ou no Apple School Manager. Após a inscrição, transfira o token VPP da Apple para a sua conta e selecione-o aqui.
    - **Apple ID** - Introduza o ID da Apple gerido da conta associada ao token carregado.
    - **Assuma o controlo do símbolo de outro MDM** - Definindo esta opção para **sim** permite que o símbolo seja reatribuído a Intune a partir de outra solução DEMDM.
    - **Token Name** - Um campo administrativo para definir o nome do símbolo.    
    - **País/Região** - Selecione a loja país/região vPP.  Intune sincroniza aplicativos VPP para todos os locais da loja de país/região De VPP especificada.
        > [!WARNING]  
        > A mudança do país/região irá atualizar os metadados das aplicações e o URL da App Store na próxima sincronização com o serviço Apple para aplicações criadas com este token. A aplicação não será atualizada se não existir na nova loja país/região.

    - **Tipo de conta VPP** – Escolha entre **Empresas** ou **Educação**.
    - **Atualizações automáticas da aplicação** – selecione **Ativado** ou **Desativado** para ativar as atualizações automáticas. Quando ativado, o Intune deteta as atualizações de aplicações VPP no interior da loja de aplicações e emite-as automaticamente para o dispositivo quando este entra. 
        
        > [!NOTE] 
        > As atualizações automáticas da aplicação para aplicações VPP da Apple irão atualizar automaticamente apenas as aplicações implementadas com intenção de instalação **Necessária**. Para aplicações implementadas com a intenção de instalação **disponível,** a atualização automática gera uma mensagem de estado para o administrador de TI informando que uma nova versão da aplicação está disponível. Esta mensagem de estado é visível selecionando a aplicação, selecionando o Estado de Instalação do Dispositivo e verificando os Detalhes do Estado.  

    - **Concedo à Microsoft permissão para enviar informações de utilizador e dispositivo saqueadas para a Apple.** - Deve selecionar **que concordo em** prosseguir. Para rever os dados que a Microsoft envia para a Apple, consulte [data Intune envia para a Apple](~/protect/data-intune-sends-to-apple.md).

6. Quando tiver terminado, selecione **Criar**. O token é apresentado no painel da lista de tokens.

## <a name="synchronize-a-vpp-token"></a>Sincronizar um símbolo vPP
Pode sincronizar os nomes das aplicações, metadados e informações de licença para as suas aplicações adquiridas em Intune, escolhendo **o Sync** para um token selecionado.

## <a name="assign-a-volume-purchased-app"></a>Atribuir uma aplicação comprada em volume

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
| 1 | BYOD – utilizador licenciado (não dispositivo de inscrição do utilizador)                             | S                                                                                               | S                                           | S                                 |
| 2 | Corp – utilizador com licença (dispositivo não supervisionado)     | S                                                                                               | S                                           | S                                 |
| 3 | Corp – utilizador com licença (dispositivo supervisionado)         | S                                                                                               | N                                           | S                                 |
| 4 | BYOD – dispositivo com licença                           | N                                                                                               | S                                           | N                                 |
| 5 | CORP – dispositivo com licença (dispositivo não supervisionado)                           | N                                                                                               | S                                           | N                                 |
| 6 | CORP – dispositivo com licença (dispositivo supervisionado)                           | N                                                                                               | N                                           | N                                 |
| 7 | Modo de local público (dispositivo supervisionado) – dispositivo com licença | N                                                                                               | N                                           | N                                 |
| 8 | Modo de local público (dispositivo supervisionado) – utilizador com licença   | --- | ---                                          | ---                                |

> [!Note]  
> Não é aconselhável atribuir aplicações VPP a dispositivos de modo quiosque utilizando o licenciamento do utilizador.

## <a name="revoking-app-licenses"></a>Revogar licenças de aplicações

Pode revogar todas as licenças de aplicações associadas iOS/iPadOS ou macOS (VPP) com base num determinado dispositivo, utilizador ou app.  Mas existem algumas diferenças entre as plataformas iOS/iPadOS e macOS. 

|   | iOS/iPadOS | macOS |
|-----|------------------|----------------|
| **Remover a atribuição de aplicativos** | Ao remover uma aplicação que foi atribuída a um utilizador, o Intune recupera a licença do dispositivo ou utilizador e desinstala a aplicação do dispositivo. | Ao remover uma aplicação que foi atribuída a um utilizador, intune reclama a licença de utilizador ou dispositivo. A aplicação não está desinstalada a partir do dispositivo. |
| **Revogar licença de aplicação** | Revogar uma licença de aplicação recupera a licença da aplicação do utilizador ou dispositivo. Tem de alterar a atribuição para **Desinstalar** para remover a aplicação do dispositivo. | Revogar uma licença de aplicação recupera a licença da aplicação do utilizador ou dispositivo. A aplicação macOS com licença revogada permanece utilizável no dispositivo, mas não pode ser atualizada até que uma licença seja reatribuída ao utilizador ou dispositivo. De acordo com a Apple, estas aplicações são removidas após um período de carência de 30 dias. No entanto, a Apple não fornece um meio para a Intune remover a aplicação utilizando a ação de desinstalação de tarefas.

>[!NOTE]
> - Intune reclama licenças de aplicações quando um empregado deixa a empresa e já não faz parte dos grupos AAD.
> - Ao atribuir uma aplicação adquirida com intenção **de Desinstalar,** intune tanto reclama a licença como desinstala a app.
> - As licenças de aplicações não são recuperadas quando um dispositivo é removido da gestão intune. 

## <a name="deleting-vpp-tokens"></a>Apagar fichas vPP
<!-- 820879 -->  
Pode eliminar um token do Apple Volume Purchase Ing (VPP) utilizando a consola. Tal poderá ser preciso quando tiver ocorrências duplicadas de um token de VPP. Eliminar um token irá eliminar também todas as atribuições e aplicações associadas. No entanto, eliminar um token não revoga as licenças das aplicações nem desinstala as aplicações. 

>[!NOTE]
>O Intune não pode revogar licenças de aplicações após um token ser eliminado. 

<!-- 820870 -->  
Para revogar a licença de todas as aplicações VPP de um determinado token VPP, tem de revogar primeiro todas as licenças de aplicações associadas ao token e, em seguida, eliminar o token.

## <a name="renewing-app-licenses"></a>Renovar licenças de aplicação

Você pode renovar um token Apple VPP descarregando um novo token do Apple Business Manager ou Apple School Manager e atualizando o token existente em Intune.

## <a name="deleting-a-vpp-app"></a>Apagar uma aplicação VPP

Atualmente, não é possível eliminar uma aplicação VPP iOS/iPadOS do Microsoft Intune.

## <a name="assigning-custom-role-permissions-for-vpp"></a>Atribuição de permissões de funções personalizadas para VPP

O acesso a tokens Apple VPP e aplicações VPP pode ser controlado de forma independente usando permissões atribuídas a funções de administrador personalizado no Intune.

* Para permitir uma função personalizada intune para gerir tokens Apple VPP em **Apps** > **tokens Apple VPP**, atribuir permissões para **aplicações geridas**.
* Para permitir uma função personalizada intune para gerir aplicações adquiridas usando tokens vPP iOS/iPadOS no âmbito de **Apps** > **Todas as aplicações,** atribuir permissões para **aplicações Móveis.** 

## <a name="additional-information"></a>Informações adicionais

A Apple fornece assistência direta para criar e renovar tokens VPP. Para obter mais informações, veja [Distribuir conteúdos pelos utilizadores com o Volume Purchase Program (VPP)](https://go.microsoft.com/fwlink/?linkid=2014661) como parte da documentação da Apple. 

Se **Atribuído ao MDM externo** for indicado no portal do Intune, o Administrador tem de remover o token VPP da MDM de terceiros antes de utilizar o token VPP no Intune.

## <a name="frequently-asked-questions"></a>Perguntas mais frequentes

### <a name="how-many-tokens-can-i-upload"></a>Quantas fichas posso carregar?
Pode carregar até 3.000 fichas em Intune.

### <a name="how-long-does-the-portal-take-to-update-the-license-count-once-an-app-is-installed-or-removed-from-the-device"></a>Quanto tempo demora o portal a atualizar a contagem de licenças depois de uma aplicação ser instalada ou removida do dispositivo?
A licença deverá ser atualizada dentro de algumas horas após a instalação ou desinstalação de uma aplicação. Tenha em atenção que mesmo se o utilizador final remover a aplicação do dispositivo, a licença continuará atribuída a esse utilizador ou dispositivo.

### <a name="is-it-possible-to-oversubscribe-an-app-and-if-so-in-what-circumstance"></a>É possível exceder as capacidades de subscrição de uma aplicação e em que circunstâncias poderia isso acontecer?
Sim. O administrador do Intune pode exceder as capacidades de subscrição de uma aplicação. Por exemplo, se o administrador adquirir 100 licenças para a aplicação XYZ e, em seguida, direcionar a aplicação para um grupo com 500 membros. Os primeiros 100 membros (utilizadores ou dispositivos) irão ter uma licença atribuída, mas a atribuição de licenças aos restantes membros falhará.


## <a name="next-steps"></a>Próximos passos

Veja [Como monitorizar aplicações](apps-monitor.md) para obter informações que o ajudam a monitorizar as atribuições de aplicações.

Veja [como resolver aplicações](~/apps/troubleshoot-app-install.md) para obter informações sobre problemas relacionados com aplicações.
