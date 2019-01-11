---
title: Personalizar o ecrã de bloqueio em dispositivos iOS com Microsoft Intune – Azure | Documentos da Microsoft
titlesuffix: ''
description: Saiba que definições do Microsoft Intune que pode utilizar para apresentar informações no ecrã de bloqueio do dispositivo iOS com as definições de configuração de dispositivos partilhados para iOS.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/12/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 9f4d75d795421c761398f349c324b498fd21ca01
ms.sourcegitcommit: 4a7421470569ce4efe848633bd36d5946f44fc8d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/10/2019
ms.locfileid: "54203081"
---
# <a name="add-custom-messages-to-lock-screen-and-login-window-on-ios-devices-using-microsoft-intune"></a>Adicionar mensagens personalizadas para bloquear a janela de tela e início de sessão em dispositivos iOS com o Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Este artigo mostra-lhe as definições do Microsoft Intune que pode utilizar para apresentar as informações na iOS dispositivo bloquear ecrã e início de sessão janela. 

Utilize estas definições para mostrar uma mensagem personalizada ou de texto no ecrã de bloqueio e a janela de início de sessão. Por exemplo, pode introduzir uma mensagem "Se perdido, devolver a..." e informações de etiqueta de recursos.

Estas definições suportam dispositivos supervisionados com o iOS 9.3 e posterior.

## <a name="create-the-profile"></a>Criar o perfil

1. Na [Portal do Azure](https://portal.azure.com), selecione **todos os serviços** > Filtrar **Intune** > selecione **Intune**.
2. Selecione **Configuração do dispositivo** > **Perfis** > **Criar perfil**.
3. Introduza um **Nome** e uma **Descrição** para o perfil.
4. Na **plataforma**, selecione **iOS**. Na **tipo de perfil**, selecione **funcionalidades do dispositivo**.
5. Na **configurações**, selecione **mensagem de ecrã de bloqueio (apenas supervisionado)**. Configure as seguintes definições:

    - **Informações da etiqueta de recursos**: Introduza as informações sobre a etiqueta de recursos do dispositivo. Por exemplo, introduza `123xyz`.

        O texto que introduzir é mostrado no ecrã de bloqueio e a janela de início de sessão no dispositivo.

    - **Nota de rodapé de ecrã de bloqueio**: Se o dispositivo é perdido ou roubado, introduza uma nota que poderá ajudar à devolução do dispositivo. Pode introduzir qualquer texto que pretende no campo. Por exemplo, introduza algo como `If found, call Contoso at ...`.

    Tokens de dispositivo também podem ser utilizados para adicionar informações específicas do dispositivo para estes campos. Por exemplo, para mostrar o número de série, introduza `Serial Number: {{serialnumber}}`. No ecrã de bloqueio, o texto mostra semelhante `Serial Number 123456789ABC`. Ao introduzir as variáveis, não se esqueça de utilizar chavetas `{{ }}`. [Tokens de configuração de aplicação](app-configuration-policies-use-ios.md#tokens-used-in-the-property-list) inclui uma lista de variáveis que podem ser utilizados. Também pode utilizar `deviceName` ou qualquer outro valor específicos do dispositivo.

6. Quando terminar, selecione **OK** > **OK** > **criar**. Seu perfil é apresentado na lista.

## <a name="next-steps"></a>Passos Seguintes

O perfil está criado, mas ainda não está ativo. Em seguida, [atribuir o perfil](device-profile-assign.md) e [monitorizar o estado](device-profile-monitor.md).
