---
title: Início Rápido – Definir um comprimento da palavra-passe obrigatório para dispositivos Android
titlesuffix: Microsoft Intune
description: Neste início rápido, vai utilizar o Microsoft Intune para definir um comprimento da palavra-passe obrigatório para dispositivos Android.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/17/2018
ms.topic: quickstart
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 81b4fa08-5333-4c54-9f49-8db5f6984ed2
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f925df731c3ddd45b13d976b0686d76d941c71e6
ms.sourcegitcommit: 2e88ec7a412a2db35034d30a70d20a5014ddddee
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/17/2018
ms.locfileid: "49395300"
---
# <a name="quickstart-set-a-required-password-length-for-android-devices"></a>Início Rápido: Definir um comprimento da palavra-passe obrigatório para dispositivos Android

Neste início rápido, vai utilizar o Microsoft Intune para exigir aos utilizadores de dispositivos Android da sua força de trabalho que introduzam uma palavra-passe com um comprimento específico antes de lhes conceder acesso às informações nos dispositivos Android. 

> [!IMPORTANT]
> Além das definições da palavra-passe, deve também considerar outras definições de segurança do sistema para proteger a sua força de trabalho. Para obter mais informações, veja [Definições de segurança do sistema](compliance-policy-create-android-for-work.md#system-security-settings).

Se não tiver uma subscrição do Intune, [inscreva-se numa conta de avaliação gratuita](free-trial-sign-up.md).

## <a name="sign-in-to-intune"></a>Iniciar sessão no Intune

Inicie sessão no [Intune](https://aka.ms/intuneportal) enquanto Administrador Global ou Administrador de Serviços do Intune. O Intune encontra-se no portal do Azure. Para aceder ao Intune, selecione **Todos os serviços** > **Intune**. O Intune encontra-se na secção **Monitorização + Gestão**.

## <a name="create-a-device-compliance-policy"></a>Criar uma política de conformidade de dispositivo
1. Assim que tiver aberto o painel **Microsoft Intune**, selecione **Conformidade do dispositivo** > **Políticas** > **Criar Política**.
2. Adicione **Conformidade do Android** como o **Nome**. Adicione também uma **Descrição**.
3. Em **Plataforma**, selecione **Android**. 
4. Selecione **Definições** > **Segurança do Sistema** para apresentar o painel **Segurança do Sistema** Android.
5. Na secção **Palavra-passe**, junto a **Palavra-passe obrigatória para desbloquear os dispositivos móveis**, clique em **Exigir**.
6. Junto a **Comprimento mínimo da palavra-passe**, introduza **6**.  

    ![Captura de ecrã da criação de um grupo no Microsoft Intune](./media/quickstart-set-password-length-android-01.png)

7. Quando terminar, clique em **OK** para fechar o painel **Segurança do Sistema**. 
8. Clique em **OK** para fechar o painel **Política de conformidade do Android**. 
9. Clique em **Criar** para criar a política.

Quando tiver criado a política com êxito, será apresentada na lista de **Conformidade do dispositivo – Políticas**. 

## <a name="next-steps"></a>Próximos passos

Neste início rápido, utilizou o Intune para criar uma política de conformidade para os dispositivos Android da sua força de trabalho para exigir uma palavra-passe de, pelo menos, seis carateres de comprimento.

> [!div class="nextstepaction"]
> [Configurar a inscrição automática](quickstart-setup-auto-enrollment.md)
