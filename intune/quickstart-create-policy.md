---
title: 'Início Rápido: adicionar uma política de conformidade para dispositivos com o Windows 10'
description: Utilize este início rápido para criar políticas para ajudar a proteger dados empresariais e gerir os dispositivos que os utilizadores finais utilizam para aceder aos recursos da empresa. Em seguida, atribua as políticas aos grupos.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/21/2018
ms.topic: quickstart
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 1ac74ba5-7441-44ac-98b5-9d8bb8899747
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 73e1e0a27d128d567a924e6f2b343026b11f1a44
ms.sourcegitcommit: 27eed5aba5c8bfafb079171081b68f75a6cbffaf
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/22/2018
ms.locfileid: "46581783"
---
# <a name="quickstart-add-a-device-compliance-policy-for-a-windows-10-device"></a>Início Rápido: adicionar uma política de conformidade para dispositivos com o Windows 10
Uma política de conformidade de dispositivos do Intune para Windows especifica as regras e definições que os dispositivos Windows têm de cumprir para serem considerados como estando em conformidade. Pode utilizar estas políticas com [acesso condicional](https://docs.microsoft.com/intune/conditional-access) para permitir ou bloquear o acesso a recursos da empresa. Também pode obter relatórios de dispositivos e agir relativamente a situações de não conformidade.

Neste início rápido, vai criar uma política de conformidade para dispositivos com o Windows 10 e atribuir a política a um grupo de dispositivos.

Se não tiver uma subscrição do Intune, [inscreva-se numa conta de avaliação gratuita](free-trial-sign-up.md).

## <a name="prerequisites"></a>Pré-requisitos
- Para concluir este início rápido, tem primeiro de [criar um utilizador](quickstart-create-user.md) e [criar um grupo](quickstart-create-group.md).


## <a name="sign-in-to-intune"></a>Iniciar sessão no Intune
Inicie sessão no [Intune](https://aka.ms/intuneportal) enquanto Administrador Global ou Administrador de Serviços do Intune.

## <a name="create-a-device-compliance-policy"></a>Criar uma política de conformidade de dispositivo
1. Selecione **Conformidade do dispositivo** > **Políticas** > **Criar Política**.
2. Introduza **Conformidade do Windows 10** em **Nome** e **Política de conformidade de exemplo para o Windows 10** para **Descrição**.
3. Em **Plataforma**, selecione **Windows 10 e posterior**.
4. Em **Definições**, selecione **Segurança do Sistema** e, em seguida, defina **Exigir uma palavra-passe para desbloquear os dispositivos móveis** para **Exigir**. Quando terminar de configurar a sua política, selecione **OK**.
   ![Política de conformidade](/intune/media/quickstart-create-policy/compliance-policy.png)
5. Feche o painel **Política de conformidade do Windows 10**. 
6. No painel **Criar política**, selecione **Criar**. Este passo cria a política e indica a sua política em **Conformidade do dispositivo** > **Políticas**.
7. Selecione a nova política e, em seguida, **Atribuições**. Pode incluir ou excluir grupos de segurança do Azure Active Directory (AD).
8. Selecione **Grupos selecionados** para ver os seus grupos de segurança do Azure AD existentes. Selecione **Técnicos de Teste da Contoso** e **Guardar** para implementar a política aos utilizadores no grupo. Se não tiver criado este grupo em [Criar um grupo](quickstart-create-group.md), pode utilizar o grupo da sua preferência. 

## <a name="clean-up-resources"></a>Limpar recursos
Quando já não for necessária, elimine a política. Para tal, selecione a política **Conformidade do Windows 10** e clique em **Eliminar**. 

## <a name="next-steps"></a>Próximos passos
Neste início rápido, criou e atribuiu uma política de conformidade de dispositivos simples. Para inscrever um dispositivo com o Windows 10 para receber a política, avance para o início rápido para configurar a inscrição automática. 
 
> [!div class="nextstepaction"]
> [Configurar a inscrição automática](quickstart-setup-auto-enrollment.md)