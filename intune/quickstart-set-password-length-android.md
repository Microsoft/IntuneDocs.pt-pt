---
title: 'Guia de Início Rápido: criar uma política de conformidade de palavra-passe para dispositivos Android'
titlesuffix: Microsoft Intune
description: Neste guia de início rápido, irá utilizar o Microsoft Intune para definir o comprimento da palavra-passe obrigatório para dispositivos Android.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/09/2018
ms.topic: quickstart
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 81b4fa08-5333-4c54-9f49-8db5f6984ed2
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 438121e0375559455547f4cc5453d272576681ca
ms.sourcegitcommit: 4c4e87cb0d8906085fcb7cdd170bd6b0cfeb23ff
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/10/2018
ms.locfileid: "51510810"
---
# <a name="quickstart-create-a-password-compliance-policy-for-android-devices"></a>Guia de Início Rápido: criar uma política de conformidade de palavra-passe para dispositivos Android

Neste início rápido, vai utilizar o Microsoft Intune para exigir aos utilizadores de dispositivos Android da sua força de trabalho que introduzam uma palavra-passe com um comprimento específico antes de lhes conceder acesso às informações nos dispositivos Android. 

Uma política de conformidade de dispositivos do Intune especifica as regras e definições que os dispositivos têm de cumprir para serem considerados conformes. Pode utilizar estas políticas de conformidade com acesso condicional para permitir ou bloquear o acesso a recursos da empresa. Também pode obter relatórios de dispositivos e agir relativamente a situações de não conformidade.

> [!IMPORTANT]
> Além das definições da palavra-passe, deve também considerar outras definições de segurança do sistema para proteger a sua força de trabalho. Para obter mais informações, veja [Definições de segurança do sistema](compliance-policy-create-android-for-work.md#system-security-settings).

Se não tiver uma subscrição do Intune, [inscreva-se numa conta de avaliação gratuita](free-trial-sign-up.md).

## <a name="sign-in-to-intune"></a>Iniciar sessão no Intune

Inicie sessão no [Intune](https://aka.ms/intuneportal) enquanto Administrador Global ou Administrador de Serviços do Intune. 

## <a name="create-a-device-compliance-policy"></a>Criar uma política de conformidade de dispositivo

Neste guia de início rápido, irá utilizar o Intune para exigir aos utilizadores de dispositivos Android da sua força de trabalho que introduzam uma palavra-passe com um comprimento específico antes de lhes conceder acesso às informações nos respetivos dispositivos Android.

1. No Intune, selecione **Conformidade do dispositivo** > **Políticas** > **Criar Política**.
2. Adicione **Conformidade do Android** como o **Nome**. Adicione também uma **Descrição**.
3. Em **Plataforma**, selecione **Android**. 
4. Selecione **Definições** > **Segurança do Sistema** para apresentar o painel **Segurança do Sistema** Android.
5. Clique em **Exigir** junto a **Exigir uma palavra-passe para desbloquear os dispositivos móveis**.
6. Introduza o algarismo **6** junto a **Comprimento mínimo da palavra-passe**. 

    ![Captura de ecrã da criação de um grupo no Microsoft Intune](media/quickstart-set-password-length-android/quickstart-set-password-length-android-01.png)

7. Quando terminar, clique em **OK** > **OK** > **Criar** para criar a política.

Quando tiver criado a política com êxito, esta será apresentada na sua lista de políticas de conformidade do dispositivo. 

## <a name="clean-up-resources"></a>Limpar recursos

Quando já não for necessária, elimine a política. Para tal, selecione a política de conformidade e clique em **Eliminar**.

## <a name="next-steps"></a>Próximos passos

Neste início rápido, utilizou o Intune para criar uma política de conformidade para os dispositivos Android da sua força de trabalho para exigir uma palavra-passe de, pelo menos, seis carateres de comprimento. Para obter mais informações sobre a criação de políticas de conformidade, veja [Introdução às políticas de conformidade de dispositivos no Intune](device-compliance-get-started.md).

Para seguir esta série de guias de início rápido do Intune, continue para o próximo guia de início rápido.

> [!div class="nextstepaction"]
> [Guia de Início Rápido: enviar notificações para dispositivos não conformes](quickstart-send-notification.md)
