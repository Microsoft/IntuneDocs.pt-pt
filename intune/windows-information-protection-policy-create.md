---
title: Criar e implementar a política de proteção de aplicações do Windows Information Protection (WIP)
titlesuffix: Microsoft Intune
description: Criar e implementar a política de proteção de aplicações do Windows Information Protection (WIP) com o Microsoft Intune
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/04/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4e3627bd-a9fd-49bc-b95e-9b7532f0ed55
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: c1d530059d7c5b5f759516e86d4ee3dbf8512aa5
ms.sourcegitcommit: 28262384ec94e43970cc7a33e5d9063972bdf468
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/04/2018
ms.locfileid: "48799630"
---
# <a name="create-and-deploy-windows-information-protection-wip-app-protection-policy-with-intune"></a>Criar e implementar a política de proteção de aplicações do Windows Information Protection (WIP) com o Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Pode utilizar políticas de proteção de aplicações com as aplicações do Windows 10 para proteger aplicações sem a inscrição de dispositivos.

## <a name="before-you-begin"></a>Antes de começar

Tem de compreender alguns conceitos ao adicionar uma política WIP:

### <a name="list-of-allowed-and-exempt-apps"></a>Lista de aplicações permitidas e excluídas

-   **Aplicações protegidas:** estas são as aplicações que precisam de cumprir esta política.

-   **Aplicações excluídas:** estas aplicações estão excluídas desta política e podem aceder aos dados empresariais sem restrições.

### <a name="types-of-apps"></a>Tipos de aplicações

-   **Aplicações recomendadas:** uma lista de aplicações preenchida previamente (na sua maioria do Microsoft Office) que pode facilmente importar para a política.
-   **Aplicações da Loja:** pode adicionar qualquer aplicação da loja Windows à política.
-   **Aplicações de ambiente de trabalho do Windows:** pode adicionar qualquer aplicação de ambiente de trabalho à política (por exemplo, .exe, .dll)

## <a name="prerequisites"></a>Pré-requisitos

Para poder criar uma política de proteção de aplicações do WIP, tem de configurar o fornecedor de MAM. Saiba mais sobre [como configurar o fornecedor de MAM com o Intune](app-protection-policies-configure-windows-10.md).  

> [!IMPORTANT]
> O WIP não suporta várias identidades, apenas pode existir uma identidade gerida de cada vez.

Além disso, tem de ter a seguinte licença e atualização:

-   Licença do [Azure AD Premium](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium)
-   [Atualização para Criativos do Windows](https://blogs.windows.com/windowsexperience/2017/04/11/how-to-get-the-windows-10-creators-update/#o61bC2PdrHslHG5J.97)





## <a name="to-add-a-wip-app-protection-policy"></a>Para adicionar uma política de proteção de aplicações WIP

Depois de configurar o Intune na sua organização, pode criar uma política específica do WIP.

> [!TIP]  
> Para obter informações relacionadas sobre a criação de políticas WIP do Intune, incluindo as definições disponíveis e como configurá-las, veja [Create a Windows Information Protection (WIP) policy with MAM using the Azure portal for Microsoft Intune](https://docs.microsoft.com/windows/security/information-protection/windows-information-protection/create-wip-policy-using-mam-intune-azure) (Criar uma política Windows Information Protection (WIP) com a MAM no portal do Azure para o Microsoft Intune) na biblioteca de documentação de Segurança do Windows. 


1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os Serviços** > **Intune**.
3. Selecione **Aplicações do cliente** no painel **Microsoft Intune**.
4. Selecione **Políticas de proteção de aplicações** no painel **Aplicações do cliente**.
5. Selecione **Adicionar uma política** para apresentar o painel **Adicionar uma política**.
6. Adicione os seguintes valores:
    - **Nome:** introduza um nome (obrigatório) para a nova política.
    - **Descrição:** (opcional) escreva uma descrição.
    - **Plataforma:** escolha o **Windows 10** como a plataforma suportada para a política de proteção de aplicações.
    - **Estado de inscrição:** escolha **Sem inscrição** como o estado de inscrição da política.
7.  Selecione **Criar**. A política é criada e apresentada na tabela no painel **Políticas de proteção de aplicações**.

## <a name="to-add-recommended-apps-to-your-protected-apps-list"></a>Para adicionar aplicações recomendadas à lista de aplicações protegidas

1. Selecione **Aplicações do cliente** no painel **Microsoft Intune**.
2. Selecione **Políticas de proteção de aplicações** no painel **Aplicações do cliente**.
3. No painel **Políticas de proteção de aplicações**, selecione a política que pretende modificar. O painel **Proteção de Aplicações do Intune** é apresentado.
4. Selecione **Aplicações protegidas** a partir do painel **Proteção de Aplicações do Intune**. É apresentado o painel **Aplicações protegidas**, onde pode ver todas as aplicações que já estão incluídas na lista para esta política de proteção de aplicações.
5. Selecione **Adicionar aplicações**. As informações **Adicionar aplicações** mostram uma lista de aplicações filtrada. A lista na parte superior do painel permite-lhe alterar o filtro de lista.
6. Selecione todas as aplicações que pretende que acedam aos seus dados empresariais.
7. Clique em **OK**. O painel **Aplicações protegidas** é atualizado e mostra todas as aplicações selecionadas.
8. Clique em **Guardar**.

## <a name="add-a-store-app-to-your-protected-apps-list"></a>Adicionar uma aplicação da loja à lista de aplicações protegidas

**Para adicionar uma aplicação da Loja**
1. Selecione **Aplicações do cliente** no painel **Microsoft Intune**.
2. Selecione **Políticas de proteção de aplicações** no painel **Aplicações do cliente**.
3. No painel **Políticas de proteção de aplicações**, selecione a política que pretende modificar. O painel **Proteção de Aplicações do Intune** é apresentado.
4. Selecione **Aplicações protegidas** a partir do painel **Proteção de Aplicações do Intune**. É apresentado o painel **Aplicações protegidas**, onde pode ver todas as aplicações que já estão incluídas na lista para esta política de proteção de aplicações.
5. Selecione **Adicionar aplicações**. As informações **Adicionar aplicações** mostram uma lista de aplicações filtrada. A lista na parte superior do painel permite-lhe alterar o filtro de lista.
6. A partir da lista, selecione **Aplicações da loja**.
7. Introduza os valores para **Nome**, **Fabricante**, **Nome do Produto** e **Ação**. Certifique-se de que define o valor **Ação** para **Permitir**, para que a aplicação tenha acesso aos seus dados empresariais.
9. Clique em **OK**. O painel **Aplicações protegidas** é atualizado e mostra todas as aplicações selecionadas.
10. Clique em **Guardar**.

## <a name="add-a-desktop-app-to-your-protected-apps-list"></a>Adicionar uma aplicação de ambiente de trabalho à lista de aplicações protegidas

**Para adicionar uma aplicação de ambiente de trabalho**
1. Selecione **Aplicações do cliente** no painel **Microsoft Intune**.
2. Selecione **Políticas de proteção de aplicações** no painel **Aplicações do cliente**.
3. No painel **Políticas de proteção de aplicações**, selecione a política que pretende modificar. O painel **Proteção de Aplicações do Intune** é apresentado.
4. Selecione **Aplicações protegidas** a partir do painel **Proteção de Aplicações do Intune**. É apresentado o painel **Aplicações protegidas**, onde pode ver todas as aplicações que já estão incluídas na lista para esta política de proteção de aplicações.
5. Selecione **Adicionar aplicações**. As informações **Adicionar aplicações** mostram uma lista de aplicações filtrada. A lista na parte superior do painel permite-lhe alterar o filtro de lista.
6. A partir da lista, selecione **Aplicações de ambiente de trabalho**.
7. Introduza os valores para **Nome**, **Fabricante**, **Nome do Produto**, **Ficheiro**, **Versão Mínima**, **Versão Máxima** e **Ação**. Certifique-se de que define o valor **Ação** para **Permitir**, para que a aplicação tenha acesso aos seus dados empresariais.
9. Clique em **OK**. O painel **Aplicações protegidas** é atualizado e mostra todas as aplicações selecionadas.
10. Clique em **Guardar**.

## <a name="wip-learning"></a>Aprendizagem de WIP
Depois de adicionar as aplicações que pretende proteger com o WIP, tem de aplicar um modo de proteção através da **Aprendizagem de WIP**.

### <a name="before-you-begin"></a>Antes de começar

A Aprendizagem de WIP é um relatório que lhe permite monitorizar as suas aplicações com o WIP e as aplicações desconhecidas de WIP. As aplicações desconhecidas são as aplicações que não foram implementadas pelo departamento de TI da sua organização. Pode exportar estas aplicações a partir do relatório e adicioná-las às políticas do WIP para evitar a interrupção da produtividade antes de impor o WIP no modo “Bloquear”.

<!-- 1631908 --> Além de ver informações sobre aplicações com o WIP, agora pode ver um resumo dos dispositivos que partilharam dados profissionais com sites. Com estas informações, pode determinar os sites que devem ser adicionados às políticas WIP dos grupos e dos utilizadores. O resumo mostra que URLs de sites são acedidos por aplicações com o WIP.

Quando estiver a trabalhar com aplicações com o WIP e aplicações desconhecidas de WIP, recomendamos que comece com **Silencioso** ou **Permitir Substituições** enquanto verifica com um pequeno grupo que tenha as aplicações corretas na sua lista de aplicações protegidas. Depois de terminar, pode alterar a política de imposição final, **Bloquear**.

### <a name="what-are-the-protection-modes"></a>O que são os modos de proteção?

#### <a name="block"></a>Bloqueio
O WIP procura práticas de partilha de dados inadequadas e impede o utilizador de concluir a ação. As ações bloqueadas podem incluir a partilha de informações em aplicações não protegidas pela empresa e a partilha de dados empresariais entre outras pessoas e dispositivos fora da sua organização.

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

1.  Selecione uma definição e, em seguida, selecione **Guardar**.

### <a name="use-wip-learning"></a>Utilizar a Aprendizagem de WIP

1. Abra o [portal do Azure](https://portal.azure.com). Selecione **Todos os serviços**. Escreva **Intune** no filtro da caixa de texto.

3. Selecione **Intune** > **Aplicações do Cliente**.

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

Para saber mais sobre o Windows Information Protection, veja [Proteger os dados empresariais com o Windows Information Protection (WIP)](https://docs.microsoft.com/windows/security/information-protection/windows-information-protection/protect-enterprise-data-using-wip).
