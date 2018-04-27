---
title: Monitorizar políticas de conformidade de dispositivos do Microsoft Intune
titlesuffix: ''
description: Utilize o dashboard de conformidade do dispositivo para monitorizar a conformidade global de dispositivos, ver relatórios e ver a conformidade do dispositivo por política e por definição.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 2/27/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: c4c3c3a2d73c6390ef5761f1bd0b12fe55855c6e
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/26/2018
---
# <a name="monitor-intune-device-compliance-policies"></a>Monitorizar as políticas de conformidade do Dispositivo do Intune

Os relatórios de conformidade ajudam os administradores a analisarem a postura de conformidade dos dispositivos na sua organização e a resolver rapidamente problemas relacionados com a compatibilidade encontrados por utilizadores dentro da organização. Pode ver informações sobre o estado de conformidade geral dos dispositivos, o estado de conformidade de uma definição individual, o estado de conformidade de uma política individual e explorar a fundo os dispositivos individuais para ver as definições e as políticas específicas que afetam o dispositivo.

> [!NOTE]
> Em março, iremos apresentar algumas melhorias de segurança no serviço Intune, com base no seu feedback. Dependendo da forma como as suas políticas de conformidade foram configuradas, poderá ter de tomar medidas para evitar que os seus utilizadores finais percam o acesso ao e-mail. Para obter detalhes, veja [Melhorias de segurança futuras](https://blogs.technet.microsoft.com/intunesupport/2018/02/09/updated-upcoming-security-enhancements-in-the-intune-service/).

## <a name="before-you-begin"></a>Antes de começar

Siga estes passos para encontrar o **Dashboard de conformidade do Dispositivo do Intune** no portal do Azure:

1.  Aceda ao [portal do Azure](https://portal.azure.com) e inicie sessão com as credenciais do Intune.

2.  Selecione **Todos os serviços** no menu à esquerda e, em seguida, escreva **Intune** no filtro da caixa de texto.

3.  Escolha **Intune** &gt; **Conformidade do dispositivo** &gt; **Descrição geral** e, em seguida, o **Dashboard de conformidade do dispositivo** é aberto.

> [!IMPORTANT]
> Os dispositivos têm de ser inscritos no Intune para receberem políticas de conformidade do dispositivo.

## <a name="device-compliance-dashboard"></a>Dashboard de conformidade do dispositivo

No **Dashboard de conformidade do dispositivo**, pode monitorizar os estados da política de Conformidade do dispositivo, que proporciona relatórios diferentes dentro de mosaicos diferentes que lhe indicam a postura de conformidade dos dispositivos na sua organização. Pode ver os seguintes relatórios:

-   Conformidade do dispositivo global agregada

-   Conformidade do dispositivo por política

-   Conformidade do dispositivo por definição

![Imagem que mostra o Dashboard de conformidade do dispositivo](./media/idc-1.png)

Também pode ver as definições e políticas de conformidade específicas que se aplicam a um dispositivo individual e o estado de conformidade final para cada uma dessas definições no dispositivo.

### <a name="overall-device-compliance-aggregate-report"></a>Relatório da conformidade do dispositivo global agregada

É um gráfico em anel que mostra o estado da conformidade agregada de todos os dispositivos inscritos no Intune. Os estados de conformidade do dispositivo são mantidos em duas bases de dados diferentes, Intune e Azure Active Directory. Veja a seguir mais detalhes sobre os estados da política de conformidade do dispositivo:

-   **Conforme**: o dispositivo aplicou com êxito uma ou mais definições de política de conformidade do dispositivo visadas pelo administrador.

-   **Não conforme:** o dispositivo não conseguiu aplicar uma ou mais definições de política de conformidade do dispositivo visadas pelo administrador ou o utilizador ainda não está a cumprir as políticas visadas pelo administrador.

-   **Período de tolerância:** o dispositivo foi visado pelo administrador com uma ou mais definições de política de conformidade do dispositivo, mas o utilizador ainda não aplicou as políticas, o que significa que o dispositivo não está conforme, mas está no período de tolerância definido pelo administrador.

    -   Saiba mais sobre as Ações para dispositivos não conformes.

-   **Dispositivo não sincronizado:** o dispositivo não comunicou o seu estado de política de conformidade do dispositivo devido a um dos motivos seguintes:

    -   **Desconhecido**: o dispositivo está offline ou não conseguiu comunicar com o Intune ou o Azure AD por outros motivos.

    -   **Erro**: o dispositivo não conseguiu comunicar com o Intune e o Azure AD e recebeu uma mensagem de erro com o motivo.

> [!IMPORTANT]
> Os dispositivos que estão inscritos no Intune, mas não visados pelas políticas de conformidade do dispositivo, são incluídos neste relatório sob o registo **Conforme**.

#### <a name="drill-down-option"></a>Opção de desagregação

No **Dashboard de conformidade do dispositivo**, se clicar no mosaico Conformidade do dispositivo, pode desagregar o **estado de conformidade**, o **alias de e-mail do utilizador**, o **modelo do dispositivo** e a **localização** específicos para cada dispositivo que foi visado pelas políticas de conformidade do dispositivo.

![Imagem que mostra a desagregação do Dashboard de conformidade do dispositivo](./media/idc-2.png)

Se precisar de mais detalhes sobre um utilizador específico, pode filtrar o relatório de gráfico de Conformidade do dispositivo ao escrever o alias de e-mail do utilizador.

![Imagem que mostra o utilizador específico do Dashboard de conformidade do dispositivo](./media/idc-3.png)

Também pode clicar nos diferentes estados de conformidade no gráfico de Conformidade do dispositivo para ver mais detalhes sobre os estados da política de conformidade dos dispositivos do utilizador.

![Imagem que mostra estados diferentes do Dashboard de conformidade do dispositivo](./media/idc-4.png)

#### <a name="filter"></a>Filtro

Se clicar no botão **Filtrar**, é apresentada a lista de filtros com as seguintes opções:

-   Model

    -   Cadeia da caixa de texto a aceitar a pesquisa gratuita
<br></br>
-   Platform

    -   Android

    -   iOS

    -   macOS

    -   Windows

    -   Windows Phone

-   Estado

    -   Compatível

    -   Não Conforme

    -   No Período de tolerância

    -   Desconhecido

    -   Error

Se clicar no botão **Atualizar**, a lista de opções deve fechar-se e os resultados devem ser atualizados de acordo com os critérios do filtro selecionado.

##### <a name="device-details"></a>Detalhes do dispositivo

Clicar num dispositivo abre o **Painel de Dispositivos** com o dispositivo selecionado, o que fornece mais detalhes sobre a definição de política de conformidade do dispositivo aplicada para esse dispositivo.

Quando clica na definição da política do dispositivo, pode ver que o nome da política de conformidade do dispositivo originou essa definição de conformidade do dispositivo visada pelo administrador.

### <a name="devices-without-compliance-policy"></a>Dispositivos sem política de conformidade
Este relatório identifica dispositivos que não têm políticas de conformidade atribuídas. Com a introdução da definição de segurança que marca todos os dispositivos sem políticas de conformidade como "não compatível", é importante conseguir identificar esses dispositivos. Em seguida, pode atribuir pelo menos uma política de conformidade aos mesmos.

> [!NOTE]
> A nova definição de segurança é configurável no portal do Intune. Selecione **Conformidade do dispositivo** e, em **Configuração**, selecione **Definições de política de conformidade**. Em seguida, utilize o botão de alternar para definir a opção **Marcar os dispositivos sem política de conformidade atribuída como** para **Compatível** ou **Não compatível**. Saiba mais sobre esta [melhoria de segurança no serviço Intune](https://blogs.technet.microsoft.com/intunesupport/2018/02/09/updated-upcoming-security-enhancements-in-the-intune-service/).

![Imagem a mostrar o relatório de Dispositivos sem política de conformidade](./media/idc-12.png)

O mosaico **Dispositivos sem política de conformidade** está disponível a partir do dashboard Conformidade do dispositivo e mostra todos os dispositivos sem uma política de conformidade, o utilizador do dispositivo, o estado de conformidade e o modelo do dispositivo.

> [!NOTE]
> Os utilizadores com uma política de conformidade de qualquer tipo não serão apresentados no relatório, independentemente da plataforma do dispositivo. Por exemplo, se tiver atribuído inadvertidamente uma política de conformidade para Windows a um utilizador com um dispositivo Android, o dispositivo não será apresentado no relatório. No entanto, o Intune irá considerar esse dispositivo Android não conforme. Para evitar problemas, recomendamos que crie políticas para cada plataforma de dispositivo e que as implemente para todos os utilizadores.

### <a name="per-policy-device-compliance-report"></a>Relatório de conformidade do dispositivo por política

Este relatório apresenta a vista da política por conformidade e o número total de dispositivos em cada estado de conformidade. O mosaico **Conformidade com a política** está disponível no **Dashboard Conformidade do dispositivo** e mostra todas as políticas criadas anteriormente pelo administrador, as plataformas em que a política está aplicada, o número de dispositivos conformes e o número de dispositivos não conformes.

![Imagem que mostra o Relatório de conformidade do dispositivo por política](./media/idc-8.png)

Depois de clicar no mosaico Conformidade de política, clique numa das políticas de conformidade do dispositivo e pode ver o **estado de conformidade**, o **alias de e-mail do utilizador**, o **modelo do dispositivo** e a **localização** para cada dispositivo que foi visado por essa política de conformidade do dispositivo.

## <a name="setting-compliance-report"></a>Relatório de conformidade com as definições

Este relatório permite-lhe ver o número total de dispositivos em cada estado de conformidade por definição de conformidade. O título **Conformidade das definições** está disponível no **Dashboard de conformidade do dispositivo** e mostra todas as definições da política de conformidade do dispositivo de todas as políticas de conformidade do dispositivo criadas pelo administrador, as plataformas nas quais as definições de política foram aplicadas e o número de dispositivos não conformes.

![Imagem que mostra o Relatório de conformidade do dispositivo por definição](./media/idc-10.png)

Depois de clicar no mosaico Conformidade das definições, clique numa das definições da política de conformidade do dispositivo para poder ver o **estado de conformidade**, o **alias de e-mail do utilizador**, o **modelo do dispositivo** e a **localização** de cada dispositivo que foi visado por essa definição de política de conformidade do dispositivo.
