---
title: Gerir contratos de licença de software para PCs a executar o cliente de software do Intune
titlesuffix: Microsoft Intune
description: Utilize o Intune para gerir contratos de licença para software comprado através de contratos de Licenciamento em Volume da Microsoft e para software comprado através de outros meios.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/01/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: c59d8635-3f66-40f5-824a-a71c738e0341
ms.reviewer: owenyen
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic-keep
ms.openlocfilehash: f6559b10bb9e3c293a9719235d01d8c7b55ee62f
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/20/2018
ms.locfileid: "52185394"
---
# <a name="manage-license-agreements-for-windows-pc-software-in-microsoft-intune"></a>Gerir contratos de licença para software para computadores com Windows no Microsoft Intune

[!INCLUDE [classic-portal](includes/classic-portal.md)]

O Microsoft Intune permite-lhe adicionar e gerir informações de contratos de licença para software comprado através de contratos de Licenciamento em Volume da Microsoft. Também pode fazê-lo para software pertencente ou não à Microsoft que tenha sido comprado através de outros meios. Pode organizar estas informações em grupos lógicos.

> [!IMPORTANT]
> Esta funcionalidade é disponibilizada apenas por conveniência e a precisão não é garantida. Não deverá confiar na mesma para verificar a conformidade com contratos de Licenciamento em Volume da Microsoft. A Microsoft não irá utilizar os dados recolhidos para investigar possíveis violações ou a conformidade com contratos de licença que o utilizador possa ter connosco.
>
> As licenças que adicionar ao Intune não afetam os contratos de licença nem a elegibilidade para utilizar o software. Por exemplo, se eliminar um par licença/contrato do Intune, não elimina nem anula contratos de licença que existam entre si e a Microsoft.

Na área de trabalho **Licenças** da consola de administração do Intune, pode:

-   Adicionar e editar contratos de Licenciamento em Volume da Microsoft.

-   Adicionar e editar outros contratos de licenciamento de software.

-   Gerir licenças e grupos.

-   Comparar as informações de elegibilidade que o Intune obtém do Centro de Serviços de Licenciamento em Volume (VLSC) com o inventário do software Microsoft que o Intune deteta nos seus PCs Windows geridos.

Além disso, pode gerar relatórios que mostrem contagens de instalações e de licenças de títulos de software. Os relatórios de licenças podem ajudá-lo a avaliar a posição da licença completa para títulos de software da Microsoft ou de terceiros.

> [!TIP]
> A área de trabalho **Licenças** não é apresentada na consola do administrador enquanto não gerir, pelo menos, um PC Windows com o cliente do PC Windows com Intune.

## <a name="add-microsoft-volume-licensing-agreements"></a>Adicionar contratos de Licenciamento em Volume da Microsoft
Os contratos de Licenciamento em Volume do Intune apresentam informações de licença de software adquirido através de contratos de Licenciamento em Volume da Microsoft. Pode adicionar contratos de Licenciamento em Volume da Microsoft ao Intune ao fornecer pares correspondentes de números de contratos. Os números de contratos ou de autorização devem corresponder à licença ou aos números de inscrição corretos. Os pares de números de contrato são obtidos ao adquirir os contratos de licença a partir do [Centro de Serviço de Licenciamento em Volume (VLSC)](http://go.microsoft.com/fwlink/?LinkID=223842).

1.  Na [consola de administrador do Microsoft Intune](https://account.manage.microsoft.com/admin/default.aspx), escolha **Licenças**.

2.  Na página **Adicionar Contratos**, em **Escolher Tipo de Contrato**, selecione **Contrato de Licenciamento em Volume**.

3.  Na secção **Adicionar Detalhes do Contrato**, escolha se pretende carregar um ficheiro ou adicionar manualmente os detalhes.

    -   **Carregar um ficheiro CSV que contém detalhes do contrato**. Escolha **Procurar** e selecione o ficheiro CSV que pretende carregar.

        -   O ficheiro pode conter duas ou três colunas, dois pares de contratos sozinhos ou três, se pretender adicionar um nome amigável para cada par de contrato.

        -   O número total de carateres num par de números de contrato não pode exceder os 16 carateres ASCII.

        -   São suportados apenas carateres ASCII.

        -   Os seguintes carateres não são permitidos no nome do contrato: **~ ! @ # $ ^ &amp; &#42; ( ) = + [ ] { } \ | ; : ' " &lt; &gt; /**. São permitidos espaços no nome.

        -   O nome do ficheiro não pode ter mais de 128 carateres.

        -   O ficheiro deve conter pelo menos um par de contratos e não pode conter mais de 5.000 pares de contratos.

        **Formato do ficheiro**

        Pode criar este ficheiro adicionando os pares de contratos a um documento de texto simples num dos formatos seguintes, dependendo do tipo de organização que registou no VLSC. Especifique um par de números de contratos por linha.

        -   **Clientes Open Value:** *Número do contrato*, *repetir número do contrato*, *nome do contrato*

        -   **Clientes Open:** *Número de autorização*, *número de licença relacionado*, *nome do contrato*

        -   **Clientes Select e Enterprise:** *Número do contrato*, *número de inscrição relacionado*, *nome do contrato*

        O formulário **Adicionar Contratos** pede-lhe que procure este ficheiro quando adicionar um novo contrato.

        O exemplo seguinte mostra o conteúdo de um ficheiro .csv para um cliente Open Value.

        `01-07001, 01-07001, Office agreements`

    -   **Adicionar manualmente os detalhes do contrato**. Forneça as informações seguintes e, em seguida, escreva os pares de números de contratos nas caixas **Número de Autorização/Contrato** e **Número de Licença/Inscrição/Cliente**. Depois de escrever ambos os números, clique no ícone **Adicionar par** para os guardar e, em seguida, opcionalmente, adicione um novo par.

        -   **Nome do contrato** - Especifique um nome exclusivo para o contrato.

            O nome do contrato pode conter, no máximo, 256 carateres e não pode incluir os seguintes carateres: **~ ! @ # $ ^ &amp; &#42; ( ) = + [ ] { } \ | ; : ' " &lt; &gt; /**. São permitidos espaços no nome.

        -   **Número de Autorização/Contrato** - Introduza o número de autorização/contrato do par de licenças.

        -   **Número Licença/Inscrição/Cliente** - Introduza o número de licença/inscrição/cliente do par de licenças.

        > [!NOTE]
        > Se adicionar vários pares de números de contratos, o Intune cria um contrato com o nome que especificar e todos os pares adicionados serão uma parte desse contrato.

    Pode escolher **+** para adicionar outro par de números de contratos ou em **-** para remover um par de números de contratos que já tenha introduzido.

4.  Na área **Selecionar Grupo de Licenças**, escolha uma das opções seguintes:

    -   **Adicionar os contratos ao grupo Contratos sem Atribuição**. Selecione esta opção se não pretender adicionar novos contratos a um grupo de licenças.

    -   **Adicionar os contratos a um novo grupo de licenças**. Forneça um nome para o novo grupo de licenças.

    -   **Adicionar os contratos a um grupo de licenças existente**. Na lista **Nome do grupo**, selecione o grupo de licenças ao qual pretende adicionar os contratos.

5.  Escolha **OK**.

É apresentada a vista **Todos os Contratos** e o Intune liga-se ao VLSC da Microsoft para validar os pares de números de contratos que forneceu.

Para atualizar as informações da licença de volume após adicionar contratos de licença ao Intune, na página **Descrição Geral das Licenças**, escolha **Atualizar Agora**. Esta ação obtém as informações da licença atual a partir do [Centro de Serviços de Licenciamento em Volume da Microsoft (VLSC)](http://go.microsoft.com/fwlink/?LinkId=223842).

> [!IMPORTANT]
> Enquanto não atualizar as informações da licença de volume, poderá ver informações diferentes na lista de contratos e nas informações sobre elegibilidade na página **Descrição Geral de Contratos**.

Depois de atualizar as informações da licença de volume, pode comparar as informações da licença com o seu software da Microsoft detetado na área de trabalho **Aplicações**. Também pode executar os seguintes relatórios de licença:

-   **Relatórios de Compra de Licenças** - Permite visualizar o software licenciado em grupos de licenças selecionados para ajudá-lo a encontrar lacunas na cobertura.

-   **Relatórios de Instalação de Licenças** - Ajuda a determinar se tem cobertura de contrato de licença suficiente.

> [!NOTE]
> O **Título do Produto** apresentado em todos os contratos de Licenciamento em Volume da Microsoft **Não está disponível**.

## <a name="add-and-edit-other-software-licensing-agreements"></a>Adicionar e editar contratos de licenciamento de software
Também pode adicionar outros tipos de contratos de licença ao Intune, além dos contratos de Licenciamento em Volume da Microsoft. Estes contratos podem incluir software de terceiros ou software da Microsoft que foi adquirido através de um revendedor.

> [!IMPORTANT]
> Para poder adicionar um contrato, tem de ter, pelo menos, um PC Windows inscrito no Intune.  Além disso, é necessário que pelo menos um computador inscrito tenha carregado um pacote de software sujeito a licença que pretenda utilizar para adicionar um contrato de licença.

### <a name="to-add-other-software-agreements"></a>Para adicionar outros contratos de software

1.  Na [consola de administrador do Microsoft Intune](https://account.manage.microsoft.com/admin/default.aspx), escolha **Licenças**.

2.  Escolha **Adicionar Contratos**, na secção **Outros Contratos de Licenciamento de Software**.

3.  Selecione **Outro contrato de licenciamento de software**, na secção **Escolher Tipo de Contrato** da página **Adicionar Contratos**.

4.  Na área **Adicionar Detalhes do Contrato**, especifique o seguinte:

    -   **Agreement name** (obrigatório). O nome do contrato pode conter, no máximo, 256 carateres e não pode incluir os seguintes carateres: **~ ! @ # $ ^ &amp; &#42; ( ) = + [ ] { } \ | ; : ' " &lt; &gt; /**. São permitidos espaços no nome.

    -   **Fabricante** (obrigatório). Quando começa a escrever o nome de um fabricante, o serviço obtém todos os nomes de fabricantes que contêm as letras que escrever. Por exemplo, se escrever "soft", o serviço obtém todos os nomes de fabricantes que contêm "soft" no nome, como "Microsoft" e "Microsoft Research". Os nomes dos fabricantes são obtidos a partir do Catálogo de Recursos de Software. Tem de selecionar o fabricante antes de introduzir o título do produto.

        > [!IMPORTANT]
        > A empresa que pretende adicionar pode não aparecer nesta lista. Só é possível adicionar contratos de software para empresas já presentes no catálogo de recursos de software. No entanto, a Microsoft trabalha continuamente para adicionar os títulos de software mais populares. Se gostaria de submeter um pedido para que uma empresa seja adicionada a esta lista, pode fazê-lo no [site do UserVoice do Intune](https://microsoftintune.uservoice.com/).

    -   **Título do produto** (obrigatório). Quando começar a escrever o título de um produto, o serviço obtém todos os títulos de produtos que contêm as letras que escrever. Tem de especificar um **Fabricante** antes de especificar o **Título do produto**.

    -   **Contagem de licenças** (obrigatório). Introduza o número de licenças adquiridas.

    -   **Data de início da licença**. Introduza a data de início da cobertura da licença.

    -   **Data de fim da licença**. Introduza a data de fim da cobertura da licença.

    -   **Detalhes do contrato**. Opcionalmente, pode especificar as informações de contacto, as chaves de registo e outras informações.

5.  Na área **Selecionar Grupo de Licenças**, escolha uma das opções seguintes:

    -   Selecione **Adicionar os contratos ao grupo Contratos Não Atribuídos**, se não quiser adicionar os contratos novos a um grupo de licenças novo ou já existente. Pode adicionar os contratos a grupos de licenças definidos pelo utilizador a qualquer momento.

    -   Selecione **Adicionar os contratos a um novo grupo de licenças** para adicionar os contratos novos a um grupo de licenças novo. Ser-lhe-á pedido para indicar um nome para o novo grupo de licenças.

    -   Selecione **Adicionar os contratos a um grupo de licenças existente** para adicionar os contratos novos a um grupo de licenças existente. Na lista **Nome do grupo**, selecione o grupo de licenças ao qual pretende adicionar os contratos.

6.  Escolha **OK**.

É apresentada a lista de vista **Todos os Contratos**.

## <a name="manage-license-agreements"></a>Gerir contratos de licença
Os contratos de licenciamento de software podem ser adicionados a grupos de licenças. Pode utilizar grupos de licenças para organizar os contratos de licenças em unidades que sejam lógicas no contexto da sua organização. Além disso, pode eliminar contratos de licença que criou anteriormente.


|                            |                                                                                                                                                                                                                                                                                                                                                                          |
|----------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|            Tarefa            |                                                                                                                                                                                 Detalhes                                                                                                                                                                                  |
|   Criar um grupo de licenças   |                                                            Na página <strong>Descrição Geral</strong> da área de trabalho <strong>Licenças</strong>, escolha <strong>Criar Grupo de Licenças</strong> no menu <strong>Tarefas</strong>. <strong>Nota:</strong> pode criar um total máximo de 500 grupos de licenças.                                                             |
|   Remover um grupo de licenças   |                                                                                                      Na área de trabalho <strong>Licenças</strong>, escolha um grupo de licenças e, em seguida, escolha <strong>Editar Grupo de Licenças</strong> no menu <strong>Tarefas</strong>.                                                                                                       |
|   Eliminar um grupo de licenças   |                                 Na área de trabalho <strong>Licenças</strong>, escolha um grupo de licenças e, em seguida, escolha <strong>Eliminar Grupo de Licenças</strong> no menu <strong>Tarefas</strong>. <strong>Sugestão:</strong> As licenças que estavam no grupo eliminado são movidas para o grupo de licenças <strong>Contratos Não Atribuídos</strong>.                                 |
| Eliminar um contrato de licença | Na área de trabalho <strong>Licenças</strong>, escolha um contrato e, em seguida, escolha <strong>Eliminar</strong>. <strong>Sugestão:</strong> depois de eliminar contratos de Licenciamento em Volume, para atualizar as informações da licença, escolha <strong>Atualizar Agora</strong>, na página <strong>Descrição Geral de Licenças</strong> ou no separador <strong>Geral</strong>, se se tratar de um grupo de licenças específico. |

