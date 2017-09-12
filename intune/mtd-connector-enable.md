---
title: "Ativar o conector da Defesa Contra Ameaças para Dispositivos Móveis com o Intune"
titlesuffix: Azure portal
description: "Ative o conector da Defesa Contra Ameaças para Dispositivos Móveis no Intune."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/21/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: dbb6a37e-ba47-4b69-922c-d25e66c279f6
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 3ed7ac5467fe3a37a133aac61a9ccffe2e6119e6
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/09/2017
---
# <a name="enable-mobile-threat-defense-in-intune"></a>Ativar a Defesa Contra Ameaças para Dispositivos Móveis no Intune

> [!NOTE] 
> Este tópico aplica-se a todos os parceiros de Defesa Contra Ameaças para Dispositivos Móveis.

Para ativar a ligação da Defesa contra Ameaças para Dispositivos Móveis (MTD) no Intune, já deve ter configurado o Conector do Intune na consola da solução de MTD.

## <a name="to-enable-the-mtd-connector"></a>Para ativar o conector da MTD

1. Aceda ao [portal do Azure](https://portal.azure.com) e inicie sessão com as credenciais do Intune. Depois de iniciar sessão com êxito, verá o **Dashboard do Azure**.

2. No **Dashboard do Azure**, escolha **Mais serviços**, no menu à esquerda e, em seguida, escreva **Intune** no filtro da caixa de texto.

3. Selecione **Intune** e o **Dashboard do Intune** será aberto.

4. No **Dashboard do Intune**, selecione **Conformidade do dispositivo** e, em seguida, **Proteção Contra Ameaças para Dispositivos Móveis**, na secção **Configuração**.

5. No painel **Defesa Contra Ameaças para Dispositivos Móveis**, selecione **Adicionar**.

6. Selecione a sua solução de MTD, como o **conector de Defesa Contra Ameaças para Dispositivos Móveis a configurar** na lista pendente.

    ![Configuração da MTD do Intune no portal do Azure](./media/enable-mtd-connector-1.png)

7. Ative as opções de alternância de acordo com os requisitos da sua organização.

## <a name="mtd-toggle-options"></a>Opções de alternância da MTD

Pode decidir quais as opções de alternância da MTD que necessita de ativar de acordo com os requisitos da sua organização. Seguem-se mais detalhes:

- **Ligar dispositivos Android 4.1 ou posterior à MTD do [nome do parceiro MTD] for Work**: quando ativa esta opção, pode ter dispositivos Android 4.1 ou posterior a comunicar riscos de segurança para o Intune.
    - **Marcar como não conforme se não forem recebidos dados**: se o Intune não receber dados sobre um dispositivo nesta plataforma a partir do parceiro MTD, considere o dispositivo como não conforme.
<br></br>
- **Ligar dispositivos iOS 8.0 ou posterior à MTD do [nome do parceiro MTD] for Work**: quando ativa esta opção, pode ter dispositivos Android 4.1 ou posterior a comunicar riscos de segurança para o Intune.
    - **Marcar como não conforme se não forem recebidos dados**: se o Intune não receber dados sobre um dispositivo nesta plataforma a partir do parceiro MTD, considere o dispositivo como não conforme.
<br></br>
- **Bloquear versões do SO não suportadas**: bloquear se o dispositivo estiver a executar um sistema operativo inferior à versão mínima suportada.

- **Número de dias até o parceiro ficar não responsivo**: número de dias de inatividade antes de o Intune considerar o parceiro como não responsivo devido a perda da ligação. O Intune ignora o estado de conformidade para parceiros MTD não responsivos.

> [!IMPORTANT] 
> Tem de adicionar e atribuir aplicações de MTD antes de criar a conformidade do dispositivo e as regras da política de acesso condicional. Isto garante que a aplicação de MTD está pronta e disponível para os utilizadores finais instalarem antes de poderem aceder ao e-mail ou a outros recursos da empresa.

> [!TIP]
> Pode ver o **Estado da ligação** e a hora da **Última sincronização** entre o Intune e o parceiro MTD no painel de Defesa Contra Ameaças para Dispositivos Móveis.

## <a name="next-steps"></a>Próximos passos

[Criar a política de conformidade de dispositivos da Defesa Contra Ameaças para Dispositivos Móveis com o Intune](mtd-device-compliance-policy-create.md)
