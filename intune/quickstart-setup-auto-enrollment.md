---
title: Início Rápido – Configurar a inscrição automática no Intune
description: 'Início Rápido: configurar a inscrição automática para dispositivos Windows 10 no Intune.'
services: microsoft-intune
author: ErikjeMS
ms.service: microsoft-intune
ms.localizationpriority: high
ms.topic: quickstart
ms.date: 11/05/2018
ms.author: erikje
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 810adbf06ddcd0aabb5c758f6a71c898116a9cee
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/14/2019
ms.locfileid: "57394321"
---
# <a name="quickstart-set-up-automatic-enrollment-for-windows-10-devices"></a>Início rápido: Configurar a inscrição automática para dispositivos Windows 10

Neste início rápido, vai configurar o Microsoft Intune para inscrever dispositivos automaticamente mediante o início de sessão de utilizadores específicos em dispositivos com o Windows 10.

Se não tiver uma subscrição do Intune, [inscreva-se numa conta de avaliação gratuita](free-trial-sign-up.md).

## <a name="prerequisites"></a>Pré-requisitos

- Subscrição do Microsoft Intune – [inscreva-se numa conta de avaliação gratuita](free-trial-sign-up.md).
- Para concluir este início rápido, tem primeiro de [criar um utilizador](quickstart-create-user.md) e [criar um grupo](quickstart-create-group.md).

## <a name="sign-in-to-intune"></a>Iniciar sessão no Intune

Inicie sessão no [Intune](https://aka.ms/intuneportal) enquanto Administrador Global ou Administrador de Serviços do Intune.

## <a name="set-up-windows-10-automatic-enrollment"></a>Configurar a inscrição automática de dispositivos Windows 10

Neste exemplo, irá utilizar a inscrição na MDM para que seja possível inscrever automaticamente dispositivos empresariais e BYOD. Irá inscrever-se numa subscrição gratuita do Azure Active Directory Premium.

1. No Azure, selecione **Azure Active Directory** > **Mobilidade (MDM e MAM)**.
2. Selecione **Obtenha uma versão de avaliação Premium gratuita para utilizar esta funcionalidade**. Selecionar esta opção irá permitir a inscrição automática através da versão de avaliação Premium gratuita do Azure Active Directory. 

    ![Selecione a versão de avaliação Premium gratuita do Azure Active Directory](media/quickstart-setup-auto-enrollment/quickstart-setup-auto-enrollment-01.png)

    Selecione a opção de versão de avaliação gratuita do **Enterprise Mobility + Security E5**. Além disso, tem de optar por **Ativar** a versão de avaliação gratuita.

    ![Selecione a versão de avaliação gratuita do Enterprise Mobility + Security E5](media/quickstart-setup-auto-enrollment/quickstart-setup-auto-enrollment-02.png)

3. Selecione **Microsoft Intune**. 

    ![Selecione o Microsoft Intune na lista](media/quickstart-setup-auto-enrollment/quickstart-setup-auto-enrollment-03.png)

4. Selecione **Alguns** no **âmbito de utilizadores de MDM** para utilizar a inscrição automática MDM para gerir dados empresariais nos dispositivos Windows dos seus colaboradores. A inscrição automática de MDM será configurada para os dispositivos associados a AAD e cenários de BYOD.

    ![Selecione "Alguns" na lista Configurar](media/quickstart-setup-auto-enrollment/quickstart-setup-auto-enrollment-04.png)

5. Selecione **Selecionar grupos** > **Técnicos de Teste da Contoso** > **Selecionar** como grupo atribuído.

    ![Selecione o grupo a inscrever](media/quickstart-setup-auto-enrollment/quickstart-setup-auto-enrollment-05.png)

6. Selecione **Alguns** no **Âmbito de Utilizadores de MAM** para gerir dados nos dispositivos da sua força de trabalho.
7. Selecione **Selecionar grupos** > **Técnicos de Teste da Contoso** > **Selecionar** como grupo atribuído. 
8. Utilize os valores predefinidos para os restantes valores de configuração.
9. Escolha **Guardar**.

## <a name="clean-up-resources"></a>Limpar recursos

Para reconfigurar a inscrição automática do Intune, veja [Configurar a inscrição para dispositivos Windows](windows-enroll.md).

## <a name="next-steps"></a>Passos Seguintes

Neste início rápido, aprendeu a configurar a inscrição automática para dispositivos com o Windows 10. Para obter mais informações sobre a inscrição de dispositivos, veja [O que é a inscrição de dispositivos?](device-enrollment.md)

Para seguir esta série de guias de início rápido do Intune, continue para o próximo guia de início rápido.

> [!div class="nextstepaction"]
> [Início rápido: Inscrever o seu dispositivo Windows 10](quickstart-enroll-windows-device.md)
