---
title: Início Rápido – criar e atribuir uma função personalizada no Intune
description: Início Rápido – criar e atribuir uma função personalizada a um gestor de dispositivos remotos.
services: microsoft-intune
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: quickstart
ms.date: 09/21/2018
ms.author: erikje
ms.openlocfilehash: 66426e9e22c2624b9828440906e3b1b947f4b60a
ms.sourcegitcommit: 27eed5aba5c8bfafb079171081b68f75a6cbffaf
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/22/2018
ms.locfileid: "46581804"
---
# <a name="quickstart-create-and-assign-a-custom-role"></a>Início Rápido: criar e atribuir uma função personalizada

Neste início rápido do Intune, vai criar e atribuir uma função personalizada com permissões específicas a um serviço de segurança operacional. Em seguida, vai atribuir a função a um grupo desses operadores. Há várias funções predefinidas que pode utilizar de imediato. Contudo, ao criar funções personalizadas como esta, tem controlo de acesso preciso em relação a todas as partes de seu sistema de gestão de dispositivos móveis.

Se não tiver uma subscrição do Intune, [inscreva-se numa conta de avaliação gratuita](free-trial-sign-up.md).

## <a name="prerequisites"></a>Pré-requisitos

- Para concluir este início rápido, terá de [criar um grupo](quickstart-create-group.md).

## <a name="sign-in-to-intune"></a>Iniciar sessão no Intune

Inicie sessão no [Intune](https://aka.ms/intuneportal) enquanto Administrador Global ou Administrador de Serviços do Intune.

## <a name="create-a-custom-role"></a>Criar uma função personalizada

Quando cria uma função personalizada, pode definir permissões para um amplo conjunto de ações. Para a função de operações de segurança, vamos definir algumas permissões de Leitura para que o operador possa rever as configurações e políticas de um dispositivo.

1. No Intune, selecione **Funções** > **Todas as funções** > **Adicionar**.
![Browser](media/quickstart-create-custom-role/add-custom-role.png)
2. Em **Adicionar função personalizada**, na caixa **Nome**, introduza *Operações de segurança*.
3. Na caixa **Descrição**, introduza *Esta função permite que um operador de segurança monitorize informações de configuração e compatibilidade de dispositivos*.
4. Selecione **Configurar** > **Identificadores de dispositivo da empresa** > **Sim** junto a **Leitura** > **OK**.
![Browser](media/quickstart-create-custom-role/corp-device-id-read.png)
5. Selecione **Políticas de conformidade de dispositivos** > **Sim** junto a **Leitura** > **OK**.
6. Selecione **Configurações de dispositivos** > **Sim** junto a **Leitura** > **OK**.
7. Selecione **Organização** > **Sim** junto a **Leitura** > **OK**.
8. Selecione **OK** > **Criar**.

## <a name="assign-the-role-to-a-group"></a>Atribuir a função a um grupo

Antes de o seu operador de segurança poder utilizar as novas permissões, tem de atribuir a função a um grupo que contenha o utilizador de segurança.

1. No Intune, selecione **Funções** > **Todas as funções** > **Suporte técnico de dispositivos remotos**.
2. Em **Funções do Intune**, selecione **Atribuições** > **Atribuir**.
3. Na caixa **Nome da atribuição**, introduza *Operador de segurança*.
4. Selecione **Membro (Grupos)** > **Adicionar**.
5. Selecione o grupo **Técnicos de Teste da Contoso**.
6. Selecione **Selecionar** > **OK**.
7. Selecione **Âmbito (Grupos)** > **Selecionar grupos para incluir** > **Técnicos de Teste da Contoso**.
8. Selecione **Selecionar** > **OK** > **OK**.

Agora todos os elementos do grupo são membros da função *Operações de segurança* e podem rever as seguintes informações sobre um dispositivo: identificadores de dispositivo da empresa, políticas de conformidade do dispositivo, configurações do dispositivo e informações sobre a organização.

## <a name="clean-up-resources"></a>Limpar recursos

Se não quiser continuar a utilizar a nova função personalizada, pode eliminá-la. Selecione **Funções** > **Todas as funções** > selecione as reticências que se encontram junto à função > **Eliminar**.

## <a name="next-steps"></a>Próximos passos

Neste início rápido, criou uma função de operações de segurança personalizada e atribui-a a um grupo. Pode saber mais sobre problemas de segurança no artigo que se segue.

> [!div class="nextstepaction"]
> [Introdução às políticas de conformidade de dispositivos](device-compliance-get-started.md)
