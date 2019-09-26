---
title: Definir termos e condições no Microsoft Intune
titleSuffix: ''
description: Defina os termos e condições que os utilizadores veem no Portal da Empresa do Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/20/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 4a3a11a8-9c0c-4334-8c6b-6fea4d0a2efb
ms.reviewer: amyro
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6d05b811ed371755ea61481a7b6e26f9fc43adee
ms.sourcegitcommit: c19584b36448bbd4c8638d7cab552fe9b3eb3408
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/20/2019
ms.locfileid: "71302848"
---
# <a name="terms-and-conditions-for-user-access"></a>Termos e condições de acesso de utilizador

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Enquanto administrador do Intune, pode exigir que os utilizadores aceitem os termos e condições da sua empresa antes de utilizarem o Portal da Empresa para:
- inscrever dispositivos
- aceder a recursos como aplicações e e-mail da empresa.

A configuração dos termos e condições é opcional.

Pode criar vários conjuntos de termos e atribuí-los a diferentes grupos, tal como para suportar outros idiomas.

Existem duas formas de criar os termos e condições da sua empresa:
- com o Intune, conforme descrito neste artigo.
- usando o [recurso Azure Active Directory termos de uso](https://docs.microsoft.com/azure/active-directory/governance/active-directory-tou)

Para saber qual método é melhor para você, confira a [postagem do blog sobre como escolher a solução de termos certos para a sua organização](https://go.microsoft.com/fwlink/?linkid=2010506&clcid=0x409). 

## <a name="create-terms-and-conditions"></a>Criar termos e condições
Conclua estes passos para criar os termos e condições. O nome a apresentar e a descrição são para utilização administrativa enquanto as propriedades dos termos são apresentadas aos utilizadores no Portal da Empresa.

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. No painel **Intune**, selecione **Inscrição de dispositivos** > **Termos e Condições**.
3. Selecione **Criar**.
4. Na página **noções básicas** , especifique as seguintes informações:

   - **Nome**: o nome dos termos no portal do Azure. Os utilizadores não veem este nome.
   - **Descrição**: detalhes opcionais que ajudam a identificar este conjunto de termos no portal do Azure.

    ![Captura de tela da portal do Azure mostrando a página noções básicas para termos e condições](media/terms-basics-page.png)

5. Escolha **Avançar** para ir para a página **termos** e forneça as seguintes informações:

   - **Título**: o nome dos termos que os utilizadores veem no Portal da Empresa acima do **Resumo**.
   - **Termos e Condições**: os termos e condições que os utilizadores veem e devem aceitar ou rejeitar.
   - **Resumo dos Termos**: texto que explica o que significa quando os utilizadores aceitam os termos. Por exemplo, "Ao inscrever o dispositivo, aceita os termos de utilização definidos pela Contoso. Leia atentamente os termos antes de continuar”.

6. Escolha **Avançar** para ir para a página **marcas de escopo** .

7. Escolha **selecionar marcas de escopo**, selecione as marcas de escopo que você deseja atribuir a estes termos e condições e, em seguida, escolha **selecionar**. 

8. Escolha **Avançar** para ir para a página **atribuições** e escolha uma das seguintes opções para **atribuir a**:
    - **Todos os usuários**: Escolha esta opção para atribuir esses termos e condições a todos os usuários.
    - **Selecionar grupos**: Escolha esta opção para atribuir esses termos e condições a todos os grupos que você identificar escolhendo **Selecionar grupos a serem incluídos**.

9. Escolha **Avançar** > **criar**.

## <a name="see-how-terms-are-displayed-to-your-users"></a>Ver como os termos são apresentados para os utilizadores
O exemplo a seguir mostra o **Título** e o **Resumo de Termos** na consola de administração e no Portal da Empresa.

![Captura de ecrã do Título e do Resumo dos Termos na consola de administração e no Portal da Empresa.](./media/terms-summary-terms.png)

O exemplo a seguir mostra os termos e as condições na consola de administração e no Portal da Empresa.

![Captura de ecrã dos termos e das condições na consola de administração e no Portal da Empresa.](./media/terms-properties-terms.png)


## <a name="monitor-terms-and-conditions"></a>Monitorizar os termos e as condições

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973). 
1. No painel Intune, selecione **Inscrição de dispositivos** > **Termos e Condições**.
2. Na lista de termos e condições, selecione os termos cuja aceitação pretende ver > **Relatórios de Aceitação**.

## <a name="work-with-multiple-versions-of-terms-and-conditions"></a>Trabalhar com múltiplas versões de termos e condições
Pode editar os seus termos e condições e gerir as respetivas versões. Sempre que fizer uma alteração significativa aos seus termos e condições, deve:
- aumentar o número da versão.
- exigir que os usuários aceitem os novos termos e condições

Mantenha o número da versão atual se, por exemplo, você estiver corrigindo erros de digitação ou alterando a formatação.

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).

2. No painel Intune, selecione **Inscrição de dispositivos** > **Termos e Condições** > selecione os termos e condições que pretende modificar > **Propriedades**.

4. No painel **Propriedades**, selecione **Termos e Condições** e, em seguida, modifique o **Título**, **Resumo dos Termos** e **Termos e Condições**, conforme necessário. Se os utilizadores tiverem de voltar a aceitar os novos termos devido às alterações que fez, selecione **Exigir que os utilizadores voltem a aceitar e incrementem o número da versão para**

4. Selecione **OK** > **Guardar**.

Os utilizadores só precisam de aceitar os termos e as condições atualizados uma vez. Os utilizadores com vários dispositivos não precisam de aceitar os termos e condições em cada dispositivo.
