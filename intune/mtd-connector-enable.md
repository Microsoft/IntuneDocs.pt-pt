---
title: Ativar o conector de defesa contra ameaças móveis no Microsoft Intune | Microsoft Intune
description: Ative o conector entre o seu parceiro de Defesa Contra Ameaças para Dispositivos Móveis (MTD) e o Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/27/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: dbb6a37e-ba47-4b69-922c-d25e66c279f6
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e19d072bcb042a0ac78acdbc5205d38958da13dc
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/07/2019
ms.locfileid: "55849525"
---
# <a name="enable-the-mobile-threat-defense-connector-in-intune"></a>Ativar o conector da Defesa Contra Ameaças para Dispositivos Móveis no Intune

> [!NOTE] 
> Este tópico aplica-se a todos os parceiros de Defesa Contra Ameaças para Dispositivos Móveis.

Durante a configuração da Defesa Contra Ameaças para Dispositivos Móveis (MTD), configurou uma política para classificar ameaças na sua consola do parceiro MTD e criou a política de conformidade de dispositivos no Intune. Se já tiver configurado o conector do Intune na consola do parceiro MTD, pode agora ativar a ligação da MTD no Intune.

## <a name="to-enable-the-mtd-connector"></a>Para ativar o conector da MTD

1. Aceda ao [portal do Azure](https://portal.azure.com) e inicie sessão com as credenciais do Intune. Depois de iniciar sessão com êxito, verá o **Dashboard do Azure**.

2. No **Dashboard do Azure**, selecione **Todos os serviços**, no menu à esquerda e, em seguida, escreva **Intune** no filtro da caixa de texto.

3. Selecione **Intune** e o **Dashboard do Intune** será aberto.

4. No **Dashboard do Intune**, selecione **Conformidade do dispositivo** e, em seguida, **Proteção Contra Ameaças para Dispositivos Móveis**, na secção **Configuração**.

5. No painel **Defesa Contra Ameaças para Dispositivos Móveis**, selecione **Adicionar**.

6. Selecione a sua solução de MTD, como o **conector de Defesa Contra Ameaças para Dispositivos Móveis a configurar** na lista pendente.

    ![Configuração da MTD do Intune no portal do Azure](./media/enable-mtd-connector-1.png)

7. Ative as opções de alternância de acordo com os requisitos da sua organização. As opções de alternância visíveis variam consoante o parceiro MTD.

## <a name="mtd-toggle-options"></a>Opções de alternância da MTD

Pode decidir quais as opções de alternância da MTD que necessita de ativar de acordo com os requisitos da sua organização. Veja a seguir mais detalhes:

- **Ligar Android 4.1 dispositivos para [nome do parceiro MTD] para o trabalho MTD**: Quando ativa esta opção, pode ter Android 4.1 dispositivos a comunicar riscos de segurança de volta para o Intune.
    - **Marcar como não conforme se não forem recebidos dados**: Se o Intune não receber dados sobre um dispositivo nesta plataforma a partir do parceiro MTD, considere o dispositivo não conforme.
<br></br>
- **Ligar dispositivos iOS 8.0 + para [nome do parceiro MTD] para o trabalho MTD**: Quando ativa esta opção, pode ter dispositivos iOS 8.0 + comunicar riscos de segurança de volta para o Intune.
    - **Marcar como não conforme se não forem recebidos dados**: Se o Intune não receber dados sobre um dispositivo nesta plataforma a partir do parceiro MTD, considere o dispositivo não conforme.
<br></br>
- **Ativar a sincronização de aplicações para dispositivos iOS**: Permite que este parceiro de defesa contra ameaças móveis solicite os metadados das aplicações iOS do Intune a utilizar para fins de análise de ameaças.

- **Bloquear versões de SO não suportadas**: Bloquear se o dispositivo está a executar um sistema operativo inferior à versão mínima suportada.

- **Número de dias até o parceiro não está a responder**: Número de dias de inatividade antes do Intune considerar o parceiro como não responsivo devido a ligação for perdida. O Intune ignora o estado de conformidade para parceiros MTD não responsivos.

> [!IMPORTANT] 
> Tem de adicionar e atribuir aplicações de MTD antes de criar a conformidade do dispositivo e as regras da política de acesso condicional. Isto garante que a aplicação de MTD está pronta e disponível para os utilizadores finais instalarem antes de poderem aceder ao e-mail ou a outros recursos da empresa.

> [!TIP]
> Pode ver o **Estado da ligação** e a hora da **Última sincronização** entre o Intune e o parceiro MTD no painel de Defesa Contra Ameaças para Dispositivos Móveis.
