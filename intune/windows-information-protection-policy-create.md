---
title: "Criar e implementar a política de proteção de aplicações do Windows Information Protection (WIP) com o Intune"
titlesuffix: Azure portal
description: "Criar e implementar a política de proteção de aplicações do WIP com o Intune"
keywords: 
author: Erikre
ms.author: erikre
manager: doubeby
ms.date: 02/16/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4e3627bd-a9fd-49bc-b95e-9b7532f0ed55
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 647e6fd129593156f2ba24299a19e96686206165
ms.sourcegitcommit: 1978a30ab1af0f43aa5f447690d0bbcdcb9b563b
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/24/2018
---
# <a name="create-and-deploy-windows-information-protection-wip-app-protection-policy-with-intune"></a>Criar e implementar a política de proteção de aplicações do Windows Information Protection (WIP) com o Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

A partir da versão 1704 do Intune, pode utilizar políticas de proteção de aplicações com o Windows 10 para proteger aplicações sem a inscrição de dispositivos.

## <a name="before-you-begin"></a>Antes de começar

Vamos falar sobre alguns conceitos ao adicionar uma política WIP.

### <a name="list-of-allowed-and-exempt-apps"></a>Lista de aplicações permitidas e excluídas

-   **Aplicações permitidas:** estas são as aplicações que precisam de cumprir esta política.

-   **Aplicações excluídas:** estas aplicações estão excluídas desta política e podem aceder aos dados empresariais sem restrições.

### <a name="types-of-apps"></a>Tipos de aplicações

-   **Aplicações recomendadas:** uma lista de aplicações preenchida previamente (na sua maioria do Microsoft Office) que pode facilmente importar para a política. <!---I really don't know what you mean by "easily import into policy"--->

-   **Aplicações da Loja:** pode adicionar qualquer aplicação da loja Windows à política.

-   **Aplicações de ambiente de trabalho do Windows:** pode adicionar qualquer aplicação de ambiente de trabalho à política (por exemplo, .exe, .dll)

## <a name="pre-requisites"></a>Pré-requisitos

Para poder criar uma política de proteção de aplicações do WIP, tem de configurar o fornecedor de MAM. Saiba mais sobre [como configurar o fornecedor de MAM com o Intune](app-protection-policies-configure-windows-10.md).

Além disso, tem de ter a seguinte licença e atualização:

-   Licença do [Azure AD Premium](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium).
-   [Atualização para Criativos do Windows](https://blogs.windows.com/windowsexperience/2017/04/11/how-to-get-the-windows-10-creators-update/#o61bC2PdrHslHG5J.97)

> [!IMPORTANT]
> O WIP não suporta várias identidades, apenas pode existir uma identidade gerida de cada vez.
<!---Should you be linking to a topic that explains what multi-identity is?--->

## <a name="to-add-a-wip-policy"></a>Para adicionar uma política WIP

Depois de configurar o Intune na sua organização, pode criar uma política específica do WIP através do [portal do Azure](https://docs.microsoft.com/intune-classic/deploy-use/azure-portal-for-microsoft-intune-mam-policies). <!---Is there an azure topic you can use instead of a classic? if not, should this topic be moved into the azure doc set?--->

1.  Aceda ao **dashboard de gestão de aplicações móveis do Intune** e selecione **Todas as definições** > **Política da aplicação**.

2.  No painel **Política da aplicação**, escolha **Adicionar uma política** e, em seguida, introduza os seguintes valores:

    a.  **Nome:** introduza um nome (obrigatório) para a nova política.

    b.  **Descrição:** escreva uma descrição opcional.

    c.  **Plataforma:** escolha o **Windows 10** como a plataforma suportada para a política de proteção de aplicações.

    d.  **Estado de inscrição:** escolha **Sem inscrição** como o estado de inscrição da política.

3.  Selecione **Criar**. A política é criada e é apresentada na tabela no painel **Política da Aplicação**.

## <a name="to-add-recommended-apps-to-your-allowed-apps-list"></a>Para adicionar aplicações recomendadas à sua lista de aplicações permitidas

1.  No painel **Política da aplicação**, escolha o nome da política e, em seguida, escolha **Aplicações permitidas** no painel **Adicionar uma política**. É apresentado o painel **Aplicações permitidas**, onde poderá ver todas as aplicações que já estão incluídas na lista para esta política de proteção de aplicações.

2.  No painel **Aplicações permitidas**, escolha **Adicionar aplicações**. É apresentada a informação **Adicionar aplicações**, onde pode ver todas as aplicações que fazem parte desta lista.

3.  Selecione todas as aplicações que pretende que acedam aos dados da sua empresa e, em seguida, escolha **OK**. O painel **Aplicações permitidas** é atualizado mostrando-lhe todas as aplicações selecionadas.

## <a name="add-a-store-app-to-your-allowed-apps-list"></a>Adicionar uma aplicação da Loja à sua lista de aplicações permitidas

**Para adicionar uma aplicação da Loja**

1.  No painel **Política da aplicação**, escolha o nome da política e, em seguida, escolha **Aplicações permitidas** no menu que aparece a mostrar todas as aplicações que já estão incluídas na lista para esta política de proteção de aplicações.

2.  No painel **Aplicações permitidas**, escolha **Adicionar aplicações**.

3.  No painel **Adicionar aplicações**, escolha **Aplicações da Loja** na lista pendente. A informação muda para mostrar as caixas para adicionar o nome de um **publicador** e de uma **aplicação**.

4.  Escreva o nome da aplicação e o nome do publicador e, em seguida, escolha **OK**.

    > [!TIP]
    > Eis o exemplo de uma aplicação, onde o **Publicador** é *NE=Microsoft Corporation, O=Microsoft Corporation, L=Redmond, E=Washington, P=EUA* e o **nome** do Produto é *Microsoft.MicrosoftAppForWindows*.

5.  Após introduzir as informações nos campos, selecione **OK** para adicionar a aplicação à lista de **Aplicações permitidas**.

> [!NOTE]
> Para adicionar várias aplicações da Loja ao mesmo tempo, pode clicar no menu **(…)** no final da linha da aplicação e, em seguida, continue a adicionar mais aplicações. Quando tiver terminado, escolha **OK**.

## <a name="add-a-desktop-app-to-your-allowed-apps-list"></a>Adicionar uma aplicação de ambiente de trabalho à sua lista de aplicações permitidas

**Para adicionar uma aplicação de ambiente de trabalho**

1.  No painel **Política da aplicação**, escolha o nome da política e, em seguida, escolha **Aplicações permitidas**. É apresentado o painel **Aplicações permitidas**, onde pode ver todas as aplicações que já estão incluídas na lista para esta política de proteção de aplicações.

2.  No painel **Aplicações permitidas**, escolha **Adicionar aplicações**.

3.  No painel **Adicionar aplicações**, escolha **Aplicações de ambiente de trabalho** na lista pendente.

4.  Após introduzir as informações nos campos, selecione **OK** para adicionar a aplicação à lista de **Aplicações permitidas**.

> [!NOTE]
> Para adicionar várias **aplicações de ambiente de trabalho** ao mesmo tempo, pode clicar no menu **(…)** no final da linha da aplicação e, em seguida, continuar a adicionar mais aplicações. Quando tiver terminado, escolha **OK**.

## <a name="wip-learning"></a>Aprendizagem de WIP
<!---You've already defined WIP earlier in the topic. You don't need to keep doing so. --->
Depois de adicionar as aplicações que pretende proteger com o WIP, tem de aplicar um modo de proteção através da **Aprendizagem de WIP**.

### <a name="before-you-begin"></a>Antes de começar

A Aprendizagem de WIP é um relatório que lhe permite monitorizar as suas aplicações com o WIP e as aplicações desconhecidas de WIP. As aplicações desconhecidas são as aplicações que não foram implementadas pelo departamento de TI da sua organização. Pode exportar estas aplicações a partir do relatório e adicioná-las às políticas do WIP para evitar a interrupção da produtividade antes de impor o WIP no modo “Bloquear”.

<!-- 1631908 --> In addition to viewing information about WIP-enabled apps, you can view a summary of the devices that have shared work data with websites. With this information, you can determine which websites should be added to group and user WIP policies. The summary shows which website URLs are accessed by WIP-enabled apps.

Quando estiver a trabalhar com aplicações com o WIP e aplicações desconhecidas de WIP, recomendamos que comece com **Silencioso** ou **Permitir Substituições** enquanto verifica com um pequeno grupo que tem as aplicações corretas na sua lista de aplicações permitidas. Depois de terminar, pode alterar a política de imposição final, **Bloquear**.

### <a name="what-are-the-protection-modes"></a>O que são os modos de proteção?

#### <a name="block"></a>Bloquear
O WIP procura práticas de partilha de dados inadequadas e impede o utilizador de concluir a ação. Estas práticas podem incluir a partilha de informações em aplicações não protegidas pela empresa e a partilha de dados empresariais entre outras pessoas e dispositivos fora da sua organização.

#### <a name="allow-overrides"></a>Permitir Substituições
O WIP procura partilhas de dados inadequadas e avisará os utilizadores quando estes realizarem alguma ação considerada potencialmente não segura. No entanto, este modo permite ao utilizador substituir a política e partilhar os dados, registando a ação no registo de auditorias.

#### <a name="silent"></a>Automática
O WIP é executado no modo silencioso e regista as partilhas de dados inadequadas sem bloquear nada que pedisse a interação do funcionário durante o modo Permitir Substituição. As ações não permitidas, tais como aplicações que estejam a tentar aceder inadequadamente a um recurso de rede ou a dados protegidos pelo WIP, continuam a ser interrompidas.

#### <a name="off-not-recommended"></a>Desativado (não recomendado)
O WIP está desativado e não ajuda a proteger ou a auditar os seus dados.

Depois de desativar o WIP, é realizada uma tentativa para desencriptar quaisquer ficheiros etiquetados pelo WIP nas unidades ligadas localmente. Tenha em atenção que as informações sobre a política e a desencriptação anteriores não serão automaticamente reaplicadas se ativar novamente a proteção do WIP.

### <a name="add-a-protection-mode"></a>Adicionar um modo de proteção

1.  No painel **Adicionar política**, selecione o nome da sua política e, em seguida, selecione **Definições necessárias**.

    ![Captura de ecrã do Modo de Aprendizagem](./media/learning-mode-sc1.png)

2.  Escolha **Guardar**.

### <a name="use-wip-learning"></a>Utilizar a Aprendizagem de WIP

1. Abra o portal do Azure. Selecione **Mais serviços**. Escreva **Intune** no filtro da caixa de texto.

3. Selecione **Intune** > **Aplicações Móveis**.

4. Selecione **Estado de proteção da aplicação** > **Relatórios** > **Aprendizagem de Windows Information Protection**.  
 
    Depois de as aplicações aparecerem no relatório de registo da Aprendizagem de WIP, pode adicioná-las às políticas de proteção de aplicações.

## <a name="allow-windows-search-indexer-to-search-encrypted-items"></a>Permitir que o Indexador do Windows Search procure itens encriptados
Permite ou proíbe a indexação de itens. Este parâmetro é para o Indexador do Windows Search, que controla a indexação de itens que são encriptados, tais como os ficheiros protegidos do Windows Information Protection (WIP).

Esta opção de política de proteção de aplicações está nas **Definições avançadas** da política do Windows Information Protection. A política de proteção de aplicações tem de ser definida para a plataforma do *Windows 10* e a política de aplicação **Estado da inscrição** tem de ser definida para **Com inscrição**. 

Quando a política está ativada, os itens protegidos pelo WIP são indexados e os respetivos metadados são armazenados numa localização não encriptada. Os metadados incluem conteúdos como o caminho do ficheiro e a data de modificação.

Quando a política está desativada, os itens protegidos pelo WIP não são indexados e não são apresentados nos resultados na Cortana ou no explorador de ficheiros. O desempenho das aplicações de fotografias e do Groove também poderá ser afetado se existirem muitos ficheiros multimédia protegidos pelo WIP no dispositivo.

## <a name="add-encrypted-file-extensions"></a>Adicionar extensões do ficheiro encriptado

Além de definir a opção **Permitir que o Indexador do Windows Search procure itens encriptados**, pode especificar uma lista de extensões de ficheiros. Os ficheiros com estas extensões são encriptados ao copiar de uma partilha do protocolo SMB (Server Message Block) dentro do limite empresarial como definido na lista de localizações de rede. Quando esta política não é especificada, é aplicado o comportamento de encriptação automática existente. Quando esta política é configurada, apenas os ficheiros com extensões na lista são encriptados.

## <a name="deploy-your-wip-app-protection-policy"></a>Implementar a política de proteção de aplicações do WIP

> [!IMPORTANT]
> Estas informações aplicam-se ao WIP sem inscrição de dispositivos.

<!---not sure why you need the Important note. Isn't this what the topic is about? app protection w/o enrollment?--->

Depois de criar a política de proteção de aplicações do WIP, tem de a implementar na sua organização através da MAM.

1.  No painel **Políticas de aplicações**, selecione a política de proteção de aplicações criada recentemente e, em seguida, selecione **Grupos de utilizadores** > **Adicionar grupo de utilizadores**.

    É apresentada uma lista de grupos de utilizadores, composta por todos os grupos de segurança no Azure Active Directory, no painel **Adicionar grupo de utilizadores**.

2.  Selecione o grupo ao qual pretende aplicar a sua política e, em seguida, escolha **Selecionar** para implementá-la.

## <a name="next-steps"></a>Passos seguintes

- Para saber mais sobre o Windows Information Protection, veja [Proteger os dados empresariais com o Windows Information Protection (WIP)](https://docs.microsoft.com/windows/security/information-protection/windows-information-protection/protect-enterprise-data-using-wip). 
