---
title: Início Rápido – Configurar a inscrição automática no Intune
description: 'Início Rápido: configurar a inscrição automática para dispositivos Windows 10 no Intune.'
services: microsoft-intune
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: quickstart
ms.date: 09/21/2018
ms.author: erikje
ms.openlocfilehash: 3b713f090fb6ada884a269e286f55f6e1b1087c4
ms.sourcegitcommit: 27eed5aba5c8bfafb079171081b68f75a6cbffaf
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/22/2018
ms.locfileid: "46581780"
---
# <a name="quickstart-set-up-automatic-enrollment-for-windows-10-devices"></a>Início Rápido: configurar a inscrição automática para dispositivos com o Windows 10

Neste início rápido, vai configurar o Microsoft Intune para inscrever dispositivos automaticamente mediante o início de sessão de utilizadores específicos em dispositivos com o Windows 10.

Se não tiver uma subscrição do Intune, [inscreva-se numa conta de avaliação gratuita](free-trial-sign-up.md).

## <a name="prerequisites"></a>Pré-requisitos

- Para concluir este início rápido, tem primeiro de [criar um utilizador](quickstart-create-user.md) e [criar um grupo](quickstart-create-group.md).

## <a name="sign-in-to-intune"></a>Iniciar sessão no Intune

Inicie sessão no [Intune](https://aka.ms/intuneportal) enquanto Administrador Global ou Administrador de Serviços do Intune.

## <a name="set-up-windows-10-automatic-enrollment"></a>Configurar a inscrição automática de dispositivos Windows 10

Neste exemplo, vai utilizar a inscrição na MDM para que seja possível inscrever automaticamente dispositivos empresariais e BYOD.

1. No Azure, selecione **Azure Active Directory** > **Mobilidade (MDM e MAM)** > **Microsoft Intune** > **Alguns**.
![Browser](media/quickstart-setup-auto-enrollment/setup-automatic-enrollment-win10.png)
2. Selecione **Selecionar grupos** > **Técnicos de Teste da Contoso** > **Selecionar**.
3. Utilize os valores predefinidos para os seguintes URLs:
    - URL dos termos de utilização da MDM
    - URL de deteção da MDM
    - URL de conformidade da MDM
4. Escolha **Guardar**.
5. Inicie sessão como utilizador no grupo num dispositivo com o Windows 10 e siga as instruções.

## <a name="clean-up-resources"></a>Limpar recursos

Para reconfigurar a inscrição automática do Intune, veja [Configurar a inscrição para dispositivos Windows](windows-enroll.md).

## <a name="next-steps"></a>Próximos passos

Neste início rápido, aprendeu a configurar a inscrição automática para dispositivos com o Windows 10. Pode aprender outras formas de inscrição de dispositivos em todas as plataformas.

> [!div class="nextstepaction"]
> [Artigo O que é a inscrição de dispositivos?](device-enrollment.md)