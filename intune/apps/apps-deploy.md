---
title: Atribuir aplicações a grupos no Microsoft Intune
titleSuffix: ''
description: Saiba como atribuir uma aplicação do Intune a grupos de utilizadores ou dispositivos com o Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: dc349e22-9e1c-42ba-9e70-fb2ef980ef7a
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 15d6a67cb41455a1e3c0830e9ed242bfa52b0269
ms.sourcegitcommit: c46b0c2d4507be6a2786a4ea06009b2d5aafef85
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/01/2020
ms.locfileid: "76912663"
---
# <a name="assign-apps-to-groups-with-microsoft-intune"></a>Atribuir aplicações a grupos com o Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Depois de [adicionar uma aplicação](apps-add.md) ao Microsoft Intune, pode atribuí-la a utilizadores e dispositivos. É importante que tenha em atenção que pode atribuir uma aplicação a um dispositivo quer este seja ou não gerido pelo Intune.

> [!NOTE]
> A intenção Implementação disponível não é suportada para grupos de dispositivos, apenas os grupos de utilizadores são suportados.

A seguinte tabela indica as várias opções para atribuir as aplicações a utilizadores e a dispositivos:

|   | Dispositivos inscritos com o Intune | Dispositivos não inscritos com o Intune |
|-------------------------------------------------------------------------------------------|------------------------------|----------------------------------|
| Atribuir a utilizadores | Sim | Sim |
| Atribuir a dispositivos | Sim | Não |
| Atribuir aplicações encapsuladas ou aplicações que incorporem o SDK do Intune (para políticas de proteção de aplicações) | Sim | Sim |
| Atribuir aplicações como Disponíveis | Sim | Sim |
| Atribuir aplicações como Obrigatórias | Sim | Não |
| Desinstalar aplicações | Sim | Não |
| Receber atualizações de aplicações a partir do Intune | Sim | Não |
| Os utilizadores finais instalam as aplicações disponíveis a partir da aplicação Portal da Empresa | Sim | Não |
| Os utilizadores finais instalam as aplicações disponíveis a partir do Portal da Empresa baseado na Web | Sim | Sim |

> [!NOTE]
> Atualmente, pode atribuir aplicações iOS e Android (tanto de linha de negócio como compradas na loja) a dispositivos que não estão inscritos no Intune.
>
> Para receber atualizações de aplicações em dispositivos que não estão inscritos no Intune, os utilizadores dos dispositivos têm de navegar até ao Portal da Empresa da organização e instalar as atualizações das aplicações manualmente.

## <a name="assign-an-app"></a>Atribuir uma aplicação

1. Entre no centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selecione **aplicativos** > **todos os aplicativos**.
3. No painel **Aplicações**, selecione a aplicação que quer atribuir.
4. Na secção **Gerir** do menu, selecione **Atribuições**.
5. Selecione **Adicionar Grupo** para abrir o painel **Adicionar grupo** que está relacionado com a aplicação.
6. Para a aplicação específica, selecione um **tipo de atribuição**:
   - **Disponível para dispositivos matriculados**: Atribuir a app a grupos de utilizadores que possam instalar a app a partir da aplicação ou website do Portal da Empresa.
   - **Disponível com ou sem inscrição**: atribua esta aplicação a grupos de utilizadores cujos dispositivos não estão inscritos no Intune. Os utilizadores tem de ser atribuídos a uma licença do Intune; veja [Licenças do Intune](../fundamentals/licenses.md).
   - **Obrigatório**: a aplicação é instalada em dispositivos nos grupos selecionados. Algumas plataformas podem ter mais avisos para o utilizador final confirmar antes de começar a instalação da aplicação.
   - **Desinstalar**: A aplicação não é instalada a partir de dispositivos nos grupos selecionados se a Intune tiver instalado previamente a aplicação no dispositivo através de uma atribuição "Disponível para dispositivos matriculados" ou "Obrigatório" utilizando a mesma implementação. As ligações da Web não podem ser removidas após a implementação.

     > [!NOTE]
     > **Apenas para aplicações iOS**:
     > - Para configurar o que acontece às aplicações geridas quando os dispositivos já não são geridos, pode selecionar a definição pretendida sob **desinstalar na remoção do dispositivo**. Para mais informações, consulte a [definição de desinstalação da App para aplicações geridas pelo iOS.](apps-deploy.md#app-uninstall-setting-for-ios-managed-apps)
     > - Se criou um perfil VPN iOS que contém definições VPN por app, pode selecionar o perfil VPN em **VPN**. Quando a aplicação for executada, a ligação VPN será aberta. Para obter mais informações, veja [Definições VPN para dispositivos iOS](../vpn-settings-ios.md).
     >
     > **Apenas para aplicações Android**: Se implementar uma aplicação Android como **disponível com ou sem matrícula,** o estado de reporte só estará disponível em dispositivos matriculados.
     >
     > Disponível **para dispositivos matriculados**: A aplicação só é apresentada como disponível se o utilizador que entrou no Portal da Empresa for o principal utilizador que inscreveu o dispositivo e a aplicação for aplicável ao dispositivo.

7. Selecione **Grupos Incluídos** para selecionar os grupos de utilizadores que são afetados por esta atribuição de aplicações.
8. Escolha **Selecionar** após selecionar um ou mais grupos para incluir.
9. No painel **Atribuir**, selecione **OK** para concluir a seleção de grupos incluídos.
10. Selecione **Excluir Grupos** se quiser excluir grupos de utilizadores de serem afetados por esta atribuição de aplicações.
11. Se tiver optado por excluir grupos, em **Selecionar grupos**, selecione **Selecionar**.
12. No painel **Adicionar grupo**, selecione **OK**.
13. No painel **Atribuições** de aplicações, selecione **Guardar**.

A aplicação está agora atribuída aos grupos que selecionou. Para obter mais informações sobre como incluir e excluir atribuições de aplicações, veja [Incluir e excluir atribuições de aplicações](apps-inc-exl-assignments.md).

## <a name="how-conflicts-between-app-intents-are-resolved"></a>Como são resolvidos conflitos entre objetivos de aplicações

Um único grupo é impedido de ser direcionado para múltiplas intenções de atribuição de aplicações, no entanto, se um utilizador ou um dispositivo for um membro de vários grupos que são atribuídos com diferentes intenções, resultará num conflito. Não é recomendada a criação de conflitos de atribuição de candidaturas.
A informação na tabela seguinte pode ajudá-lo a entender a intenção resultante quando ocorre um conflito:

| Objetivo do grupo 1 | Objetivo do grupo 2 | Objetivo resultante |
|-----------------------------------|-----------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|Utilizador – Necessário|Utilizador – Disponível|Necessário e Disponível|
|Utilizador – Necessário|Utilizador – Desinstalar|Necessário|
|Utilizador – Disponível|Utilizador – Desinstalar|Desinstalar|
|Utilizador – Necessário|Dispositivo – Necessário|Ambas existem, o Intune trata da intenção Necessário
|Utilizador – Necessário|Dispositivo – Desinstalar|Ambas existem, o Intune resolve a intenção Necessário
|Utilizador – Disponível|Dispositivo – Necessário|Ambas existem, o Intune resolve a intenção Necessário (Necessário e Disponível)
|Utilizador – Disponível|Dispositivo – Desinstalar|Ambas existem, o Intune resolve a intenção Disponível.<br><br>A aplicação é apresentada no Portal da Empresa.<br><br>Se a aplicação já estiver instalada (como aplicação necessária com a intenção anterior), será desinstalada.<br><br>Se o utilizador selecionar **Instalar a partir do Portal da Empresa**, a aplicação será instalada e a intenção de desinstalação não será cumprida.|
|Utilizador – Desinstalar|Dispositivo – Necessário|Ambas existem, o Intune resolve a intenção Necessário|
|Utilizador – Desinstalar|Dispositivo – Desinstalar|Ambas existem, o Intune resolve a intenção Desinstalar|
|Dispositivo – Necessário|Dispositivo – Desinstalar|Necessário|
|Utilizador – Necessário e Disponível|Utilizador – Disponível|Necessário e Disponível|
|Utilizador – Necessário e Disponível|Utilizador – Desinstalar|Necessário e Disponível|
|Utilizador – Necessário e Disponível|Dispositivo – Necessário|Ambas existem, Necessário e Disponível
|Utilizador – Necessário e Disponível|Dispositivo – Desinstalar|Ambas existem, o Intune resolve a intenção Necessário (Necessário e Disponível)
|Utilizador – Disponível sem inscrição|Utilizador – Necessário e Disponível|Necessário e Disponível
|Utilizador – Disponível sem inscrição|Utilizador – Necessário|Necessário
|Utilizador – Disponível sem inscrição|Utilizador – Disponível|Disponível|
|Utilizador – Disponível sem inscrição|Dispositivo – Necessário|Necessário e Disponível sem inscrição|
|Utilizador – Disponível sem inscrição|Dispositivo – Desinstalar|Desinstalar e Disponível sem inscrição.<br><br>Se o utilizador não tiver instalado a aplicação a partir do Portal da Empresa, a desinstalação é cumprida.<br><br>Se o utilizador instalar a aplicação a partir do Portal da Empresa, a instalação terá prioridade sobre a desinstalação.|

> [!NOTE]
> Apenas para aplicações da loja iOS geridas: quando adiciona estas aplicações ao Microsoft Intune e as atribui como **Necessário**, estas aplicações são criadas automaticamente com as intenções **Necessário** e **Disponível**.<br><br>
> As aplicações da Loja iOS (não aplicações iOS obtidas pelo VPP) que são direcionadas com a intenção necessária serão aplicadas no dispositivo quando registar o mesmo e também serão apresentadas na aplicação Portal da Empresa.<br><br>
> Quando ocorrem conflitos na **desinstalação na** definição de remoção do dispositivo, a aplicação não é removida do dispositivo quando o dispositivo já não é gerido.

## <a name="managed-google-play-app-deployment-to-unmanaged-devices"></a>Implementação de aplicações do Managed Google Play em dispositivos não geridos
Para dispositivos Android num cenário de implementação de Política de Proteção de Aplicações Sem Inscrição (APP-WE), pode utilizar o Managed Google Play para implementar aplicações da loja e aplicações de linha de negócio (LOB) para os utilizadores. As aplicações do Managed Google Play visadas como **Disponíveis com ou sem inscrição** aparecerão na aplicação da Play Store no dispositivo do utilizador final e não na aplicação do Portal da Empresa. O utilizador final irá procurar e instalar as aplicações implementadas desta maneira, na aplicação Play. Uma vez que as aplicações estão a ser instaladas a partir do Managed Google Play, o utilizador final não precisará de alterar as configurações dos dispositivos para permitir a instalação de aplicações de origens desconhecidas, o que significa que os dispositivos estarão mais seguros. Se o programador da aplicação publicar uma nova versão de uma aplicação no Play, que foi instalada no dispositivo de um utilizador, a aplicação será atualizada automaticamente pelo Play. 

Passos para atribuir uma aplicação do Managed Google Play a dispositivos não geridos:

1. Ligue o inquilino do Intune ao Managed Google Play. Se já o tiver feito para gerir o perfil de trabalho do Android Enterprise, os dispositivos dedicados ou totalmente geridos, não será necessário fazê-lo novamente.
2. Adicione aplicações a partir do Managed Google Playà consola do Intune.
3. Vise aplicações do Managed Google Play como **Disponíveis com ou sem inscrição** para o grupo de utilizadores pretendido. As opções **Obrigatório** e **Desinstalar** para aplicações visadas não são suportada para dispositivos não inscritos.
4. Atribua uma Política de Proteção de Aplicações ao grupo de utilizadores.
5. Da próxima vez que o utilizador final abrir a aplicação do Portal da Empresa, verá uma mensagem a indicar que existem aplicações disponíveis na aplicação Play Store.  O utilizador pode tocar nesta notificação para ser ir diretamente para a aplicação Play para ver as aplicações empresariais ou pode navegar para a aplicação Play Store separadamente.
6. O utilizador final pode expandir o menu de contexto dentro da aplicação Play Store e alternar entre a conta Google pessoal (onde vê as aplicações pessoais) e a conta profissional (onde verá as aplicações da loja e as aplicações LOB que lhes eram destinadas). Os utilizadores finais instalam as aplicações ao tocar em Instalar na aplicação Play Store.

Quando uma eliminação seletiva de aplicações é emitida na consola do Intune, a conta profissional será removida automaticamente da aplicação Play Store e o utilizador final, a partir desse momento, deixará de ver aplicações de trabalho no catálogo das aplicações da Play Store. Quando a conta profissional é removida de um dispositivo, as aplicações instaladas a partir da Play Store permanecerão instaladas no dispositivo e não serão desinstaladas. 

## <a name="app-uninstall-setting-for-ios-managed-apps"></a>App desinstalar definição para aplicações geridas iOS
Para dispositivos iOS, pode escolher o que acontece com as aplicações geridas para não inscrever o dispositivo a partir de Intune ou remover o perfil de gestão utilizando **desinstalar na** definição de remoção do dispositivo. Esta definição só se aplica a apps depois de o dispositivo estar matriculado e as aplicações são instaladas como geridas. A definição não pode ser configurada para aplicações web ou web links. Apenas os dados protegidos pela Mobile Application Management (MAM) são removidos após a reforma por uma Limpeza Seletiva da Aplicação.

Os valores predefinidos para a definição são pré-povoados para novas atribuições da seguinte forma:

|tipo de aplicativo iOS | Definição predefinida para "Desinstalar na remoção do dispositivo" |
|--------------------|----------------|
| App de linha de negócios | Sim |
| Aplicação da loja | Não |
| Aplicativo VPP | Não |
| Aplicação incorporada | Não |

>[!NOTE]
>Tipos de **atribuição "disponíveis":** Se estiver a atualizar esta definição para "disponíveis para dispositivos matriculados" ou "disponíveis com ou sem matrícula", os utilizadores que já tenham a app gerida não receberão a definição atualizada até sincronizarem o dispositivo com o Intune e reinstalarem a app. 
>
>**Atribuições pré-existentes:** As atribuições que existiam antes da introdução desta definição não são modificadas e todas as aplicações geridas serão removidas na remoção do dispositivo da gestão.

## <a name="next-steps"></a>Próximos passos

Para saber mais sobre a monitorização de atribuições de aplicações, veja [Como monitorizar aplicações](apps-monitor.md).
