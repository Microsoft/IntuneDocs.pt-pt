---
title: Eliminação seletiva de dados através de ações de acesso das políticas de proteção de aplicações
titleSuffix: Microsoft Intune
description: Saiba como eliminar seletivamente os dados através de ações de acesso das políticas de proteção de aplicações no Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/03/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f5ca557e-a8e1-4720-b06e-837c4f0bc3ca
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 2cfd426a0ae7165a7aae60a90d104852fd834db6
ms.sourcegitcommit: 98b444468df3fb2a6e8977ce5eb9d238610d4398
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/07/2018
ms.locfileid: "37909121"
---
# <a name="selectively-wipe-data-using-app-protection-policy-access-actions-in-intune"></a>Eliminação seletiva de dados através de ações de acesso das políticas de proteção de aplicações no Intune

Ao utilizar as políticas de proteção de aplicações do Intune, pode configurar definições para impedir que os utilizadores finais acedam a uma conta ou aplicação empresarial. Estas definições destinam-se aos requisitos de acesso e relocalização de dados definidos pela sua organização em casos de, por exemplo, dispositivos desbloqueados por jailbreak e versões de SO mínimas.
 
Com estas definições, pode eliminar dados da empresa explicitamente do dispositivo do utilizador final como uma ação a ser realizada em caso de não conformidade. Em algumas definições, será possível configurar múltiplas ações, como impedir o acesso e eliminar os dados com base em diferentes valores especificados.

## <a name="create-an-app-protection-policy-using-access-actions"></a>Criar uma política de proteção de aplicações com ações de acesso

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços** > **Intune**.  
    O Intune encontra-se na secção **Monitorização + Gestão**.
3. No painel **Intune**, selecione **Aplicações móveis** > **Políticas de proteção de aplicações**.
4. Clique em **Adicionar uma política** (também pode editar uma política existente). 
5. Clique em **Configurar definições obrigatórias** para ver a lista de definições disponíveis a configurar para a política. 
6. Ao deslocar-se para baixo no painel **Definições**, verá uma secção denominada **Ações de Acesso** com uma tabela editável.

    ![Captura de ecrã a mostrar as ações de acesso de proteção de aplicações do Intune](./media/apps-selective-wipe-access-actions01.png)

7. Selecione uma **Definição** e introduza o **Valor** que os utilizadores têm de cumprir para iniciar sessão na sua aplicação da empresa. 
8. Selecione a **Ação** a realizar se os utilizadores não cumprirem os seus requisitos. Em alguns casos, é possível configurar múltiplas ações para uma única definição. Para obter mais informações, veja [Como criar e atribuir políticas de proteção de aplicações](app-protection-policies.md).

>[!NOTE]
> Para utilizar a definição **Modelos de dispositivos**, introduza uma lista de identificadores de modelos separados por ponto e vírgula. 

## <a name="policy-settings"></a>Definições de política 

A tabela das definições de políticas de proteção de aplicações apresenta colunas para a **Definição**, o **Valor** e a **Ação**.

Para iOS, poderá configurar ações para as seguintes definições a partir da lista pendente **Definição**:
-  Máximo de tentativas de PIN
-  Período de tolerância offline
-  Dispositivos com jailbreak/rooting
-  Versão mínima do SO
-  Versão mínima da aplicação
-  Versão mínima do SDK
-  Modelos de dispositivos

Para Android, poderá configurar ações para as seguintes definições a partir da lista pendente **Definição**:
-  Máximo de tentativas de PIN
-  Período de tolerância offline
-  Dispositivos com jailbreak/rooting
-  Versão mínima do SO
-  Versão mínima da aplicação
-  Versão mínima da correção
-  Fabricantes de dispositivos

Por predefinição, a tabela terá linhas povoadas como definições configuradas para **Período de tolerância offline** e **Máximo de tentativas de PIN**, se a definição **Requerer PIN para acesso** estiver definida como **Sim**.
 
Para configurar uma definição, selecione uma definição na lista pendente da coluna **Definição**. Depois de selecionar uma definição, a caixa de texto editável ficará ativa na coluna **Valor** da mesma linha, se for necessário definir um valor. Além disso, a lista pendente ficará ativa na coluna **Ação** com o conjunto de ações de iniciação condicional aplicáveis à definição. 

A seguinte lista apresenta as ações comuns:
-  **Bloquear acesso** – impedir o utilizador final de aceder à aplicação da empresa.
-  **Apagar dados** – apagar os dados da empresa do dispositivo do utilizador final.
-  **Avisar** – apresentar uma caixa de diálogo com uma mensagem de aviso para o utilizador final.

### <a name="additional-settings-and-actions"></a>Definições e ações adicionais 

Em alguns casos, como a definição **Versão mínima do SO**, pode configurar a definição para realizar todas as ações aplicáveis com base em números de versão diferentes. 

![Captura de ecrã a mostrar as ações de acesso de proteção de aplicações do Intune – Versão mínima do SO](./media/apps-selective-wipe-access-actions05.png)

Depois de ter configurado totalmente uma definição, a linha será apresentada numa vista só de leitura e estará disponível para editar em qualquer altura. A linha também parecerá ter uma lista pendente disponível para seleção na coluna **Definição**. As definições que já tenham sido configuradas e que não permitam múltiplas ações não estarão disponíveis para seleção na lista pendente.

## <a name="next-steps"></a>Próximos passos

Para obter mais informações sobre as políticas de proteção de aplicações do Intune, veja:
- [Como criar e atribuir políticas de proteção de aplicações](app-protection-policies.md)
- [Definições de políticas de proteção de aplicações iOS](app-protection-policy-settings-ios.md)
- [Definições de políticas de proteção de aplicações Android no Microsoft Intune](app-protection-policy-settings-android.md) 


