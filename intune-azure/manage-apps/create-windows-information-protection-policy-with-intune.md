---
title: "Criar e implementar a política de proteção de aplicações do Windows Information Protection (WIP) com o Intune | Microsoft Docs"
titleSuffix: Intune Azure preview
description: "Criar e implementar a política de proteção de aplicações do WIP com o Intune"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 04/25/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4e3627bd-a9fd-49bc-b95e-9b7532f0ed55
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 5f172290d493717308446c4f9e2313a03ba8f3aa
ms.openlocfilehash: 164518c320ba3d82abf101e76d911b7424f2f6cd
ms.lasthandoff: 04/27/2017


---

# <a name="create-and-deploy-windows-information-protection-wip-app-protection-policy-with-intune"></a>Criar e implementar a política de proteção de aplicações do Windows Information Protection (WIP) com o Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

A partir da versão 1704 do Intune, pode utilizar as políticas de proteção de aplicações com o Windows 10 na gestão de aplicações móveis (MAM) sem o cenário de inscrição.

## <a name="before-you-begin"></a>Antes de começar

Vamos falar sobre alguns conceitos ao adicionar uma política WIP.

### <a name="list-of-allowed-and-exempt-apps"></a>Lista de aplicações Permitidas e Excluídas

-   **Aplicações permitidas:** são as aplicações que precisam de cumprir esta política.

-   **Aplicações excluídas:** estas aplicações estão excluídas desta política e podem aceder aos dados empresariais sem restrições.

### <a name="types-of-apps"></a>Tipos de aplicações

-   **Aplicações recomendadas:** uma lista de aplicações preenchida previamente (na sua maioria do Microsoft Office) que os administradores podem facilmente importar para a política.

-   **Aplicações da loja:** o administrador pode adicionar qualquer aplicação da Loja Windows à política.

-   **Aplicações de ambiente de trabalho do Windows:** o administrador pode adicionar qualquer aplicação de ambiente de trabalho do Windows à política (por exemplo, exe, dll, etc.)

## <a name="pre-requisites"></a>Pré-requisitos

Para poder criar uma política de proteção de aplicações do WIP, tem de configurar o fornecedor de MAM.

-   Saiba mais sobre [como configurar o fornecedor de MAM com o Intune](https://docs.microsoft.com/intune-azure/manage-apps/get-ready-to-configure-app-protection-policies-for-windows-10).

Além disso, tem de ter o seguinte:

-   Licença do [Azure AD Premium](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium).
-   [Atualização para Criativos do Windows](https://blogs.windows.com/windowsexperience/2017/04/11/how-to-get-the-windows-10-creators-update/#o61bC2PdrHslHG5J.97)

> [!IMPORTANT]
> O WIP não suporta várias identidades, apenas pode existir uma identidade gerida de cada vez.

## <a name="to-add-a-wip-policy"></a>Para adicionar uma política WIP

Depois de configurar o Intune na sua organização, pode criar uma política específica do WIP através do [portal do Azure](https://docs.microsoft.com/intune/deploy-use/azure-portal-for-microsoft-intune-mam-policies).

1.  Aceda ao **dashboard da gestão de aplicações móveis do Intune**, escolha **Todas as definições** e, em seguida, escolha **Política da aplicação**.

2.  No painel **Política da aplicação**, escolha **Adicionar uma política** e, em seguida, introduza os seguintes valores:

    a.  **Nome:** introduza um nome (obrigatório) para a nova política.

    b.  **Descrição:** escreva uma descrição opcional.

    c.  **Plataforma:** escolha o **Windows 10** como a plataforma suportada para a política de proteção de aplicações.

    d.  **Estado de inscrição:** escolha **Sem inscrição** como o estado de inscrição da política.

3.  Selecione **Criar**. A política é criada e é apresentada na tabela no painel **Política da Aplicação**.

## <a name="to-add-recommended-apps-to-your-allowed-apps-list"></a>Para adicionar aplicações recomendadas à lista de Aplicações permitidas

1.  No painel **Política da aplicação**, escolha o nome da política e, em seguida, escolha **Aplicações permitidas** no painel **Adicionar uma política**. É apresentado o painel **Aplicações permitidas**, onde poderá ver todas as aplicações que já estão incluídas na lista para esta política de proteção de aplicações.

2.  No painel **Aplicações permitidas**, escolha **Adicionar aplicações**. É apresentado o painel **Adicionar aplicações**, onde pode ver todas as aplicações que fazem parte desta lista.

3.  Selecione todas as aplicações que pretende que acedam aos dados da sua empresa e, em seguida, escolha **OK**. O painel **Aplicações permitidas** é atualizado mostrando-lhe todas as aplicações selecionadas.

## <a name="add-a-store-app-to-your-allowed-apps-list"></a>Adicionar uma aplicação da Loja à lista de Aplicações permitidas

**Para adicionar uma aplicação da Loja**

1.  No painel **Política da aplicação**, escolha o nome da política e, em seguida, escolha **Aplicações permitidas** no menu que aparece a mostrar todas as aplicações que já estão incluídas na lista para esta política de proteção de aplicações.

2.  No painel **Aplicações permitidas**, escolha **Adicionar aplicações**.

3.  No painel **Adicionar aplicações**, escolha **Aplicações da Loja** na lista pendente. O painel muda para mostrar as caixas para adicionar o nome de um **publicador** e de uma **aplicação**.

4.  Escreva o nome da aplicação e o nome do publicador e, em seguida, escolha **OK**.

    > [!TIP]
    > Eis o exemplo de uma aplicação, onde o **Publicador** é *NE=Microsoft Corporation, O=Microsoft Corporation, L=Redmond, E=Washington, P=EUA* e o **nome** do Produto é *Microsoft.MicrosoftAppForWindows*.

5.  Após introduzir as informações nos campos, selecione **OK** para adicionar a aplicação à lista de **Aplicações permitidas**.

> [!NOTE]
> Para adicionar várias aplicações da Loja ao mesmo tempo, pode clicar no menu **(…)** no final da linha da aplicação e, em seguida, continue a adicionar mais aplicações. Quando tiver terminado, escolha **OK**.

## <a name="add-a-desktop-app-to-your-allowed-apps-list"></a>Adicionar uma Aplicação de ambiente de trabalho à lista de Aplicações permitidas

**Para adicionar uma Aplicação de ambiente de trabalho**

1.  No painel **Política da aplicação**, escolha o nome da política e, em seguida, escolha **Aplicações permitidas**. É apresentado o painel **Aplicações permitidas**, onde pode ver todas as aplicações que já estão incluídas na lista para esta política de proteção de aplicações.

2.  No painel **Aplicações permitidas**, escolha **Adicionar aplicações**.

3.  No painel **Adicionar aplicações**, escolha **Aplicações de ambiente de trabalho** na lista pendente.

4.  Após introduzir as informações nos campos, selecione **OK** para adicionar a aplicação à lista de **Aplicações permitidas**.

> [!NOTE]
> Para adicionar várias **Aplicações de ambiente de trabalho** ao mesmo tempo, pode clicar no menu **(…)** no final da linha da aplicação e, em seguida, continue a adicionar mais aplicações. Quando tiver terminado, escolha **OK**.

## <a name="windows-information-protection-wip-learning"></a>Aprendizagem do Windows Information Protection (WIP)

Depois de adicionar as aplicações que pretende proteger com o WIP, tem de aplicar um modo de proteção através da **Aprendizagem de WIP**.

### <a name="before-you-begin"></a>Antes de começar

A Aprendizagem do Windows Information Protection (WIP) é um relatório que permite aos administradores monitorizarem as aplicações desconhecidas do WIP. As aplicações desconhecidas são as aplicações que não foram implementadas pelo departamento de TI da sua organização. O administrador pode exportar estas aplicações a partir do relatório e adicioná-las às políticas do WIP para evitar a interrupção da produtividade antes de imporem o WIP no modo “Ocultar Substituição”.

Recomendamos que comece com **Silencioso** ou **Permitir Substituições** enquanto verifica com um pequeno grupo que tem as aplicações corretas na lista de aplicações permitidas. Depois de terminar, pode alterar a política de imposição final, **Ocultar Substituições**.

#### <a name="what-the-protection-modes-are"></a>Quais são os modos de proteção?

- **Ocultar Substituições:**
    - O WIP procura práticas de partilha de dados inadequadas e impede o utilizador de concluir a ação.
    - Estas práticas podem incluir a partilha de informações em aplicações não protegidas pela empresa e a partilha de dados empresariais entre outras pessoas e dispositivos fora da sua organização.
<br></br>

- **Permitir Substituições:**
    - O WIP procura partilhas de dados inadequadas e avisará os utilizadores se estes realizarem alguma ação considerada potencialmente insegura.
    - No entanto, este modo permite ao utilizador substituir a política e partilhar os dados, registando a ação no registo de auditorias.
<br></br>
- **Silencioso:**
    - O WIP é executado no modo silencioso e regista as partilhas de dados inadequadas sem bloquear nada que pedisse a interação do funcionário durante o modo Permitir Substituição.
    - As ações não permitidas, tais como aplicações que estejam a tentar aceder inadequadamente a um recurso de rede ou a dados protegidos pelo WIP, continuam a ser interrompidas.
<br></br>
- **Desativado (não recomendado):**
    - O WIP está desativado e não ajuda a proteger ou a auditar os seus dados.
    - Depois de desativar o WIP, é realizada uma tentativa para desencriptar quaisquer ficheiros etiquetados pelo WIP nas unidades ligadas localmente. Tenha em atenção que as informações sobre a política e a desencriptação anteriores não serão automaticamente reaplicadas se ativar novamente a proteção do WIP.

### <a name="to-add-a-protection-mode"></a>Para adicionar um modo de proteção

1.  No painel **Política da aplicação**, escolha o nome da política e, em seguida, clique em **Definições necessárias** no painel **Adicionar Política**.

    ![Captura de ecrã do Modo de Aprendizagem](../media/AppManagement/learning-mode-sc1.png)

1.  Escolha **Guardar**.

### <a name="to-use-wip-learning"></a>Para utilizar a Aprendizagem de WIP

1. Aceda ao Dashboard do Azure.

2. Selecione **Mais serviços** no menu à esquerda e, em seguida, escreva **Intune** no filtro da caixa de texto.

3. Escolha **Intune**, quando o **Dashboard do Intune** for apresentado, escolha **Aplicações Móveis**.

4. Escolha **Aprendizagem de WIP**, na secção **Monitor**. Pode ver as aplicações desconhecidas registadas pela Aprendizagem de WIP.

> [!IMPORTANT]
> Depois de as aplicações aparecerem no relatório de registo da Aprendizagem de WIP, pode adicioná-las às políticas de proteção de aplicações.

## <a name="to-deploy-your-wip-app-protection-policy"></a>Para implementar a política de proteção de aplicações do WIP

> [!IMPORTANT]
> Tal aplica-se ao WIP com a gestão de aplicações móveis (MAM) sem o cenário de inscrição.

Depois de criar a política de proteção de aplicações do WIP, tem de a implementar na sua organização através da MAM.

1.  No painel **Política da aplicação**, escolha a política de proteção de aplicações criada recentemente, escolha **Grupos de utilizadores** e, em seguida, escolha **Adicionar grupo de utilizadores**.

    É apresentada uma lista de grupos de utilizadores, composta por todos os grupos de segurança no Azure Active Directory, no painel **Adicionar grupo de utilizadores**.

1.  Selecione o grupo ao qual pretende que a política seja aplicada e, em seguida, clique em **Selecionar** para a implementar.

