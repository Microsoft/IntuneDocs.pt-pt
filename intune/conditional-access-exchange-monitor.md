---
title: Monitorizar o acesso condicional do Exchange no Microsoft Intune
titlesuffix: ''
description: Monitorize a conformidade do acesso condicional do Exchange Online e no Exchange no local através do portal do Azure no Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 5712682d-285b-43fd-9978-3dcfd95ec5f9
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 20a99290d2a84c22bc2bee823d7a3bb42e43aced
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/20/2018
ms.locfileid: "52180583"
---
# <a name="monitor-conditional-access-compliance-for-on-premises-exchange-and-exchange-online-in-intune"></a>Monitorizar a conformidade de acesso condicional no Exchange Online e no Exchange no local no Intune

A partir da versão 1704 do Intune, os administradores podem ver informações relacionadas com registos de dispositivo do Exchange ActiveSync que são sincronizados com o Intune através do conector do Exchange no local ou o conector de serviços do Intune (Exchange de geração de relatórios Conector online). Os relatórios de conformidade de acesso condicional fornecem um resumo dos dispositivos com diferentes Estados de sincronização:

-   **Permitir**

-   **Bloquear**

-   **Quarentena**

## <a name="to-monitor-conditional-access-compliance"></a>Para monitorizar a compatibilidade de acesso condicional

1.  Aceda ao [portal do Azure](https://portal.azure.com/) e inicie sessão com as credenciais do Intune.

2.  Depois de se com êxito, consulte a **Dashboard do Azure**.

3.  Escolher **todos os serviços** no menu à esquerda, em seguida, escreva **Intune** no filtro da caixa de texto.

4.  Escolher **Intune**, verá o **Dashboard do Intune**.

5.  Selecione **Acesso condicional** e, em seguida, selecione **Descrição Geral**.

6.  Selecione uma das três áreas (**Permitido**, **Bloqueado** ou **Quarentena**) no gráfico para ver os relatórios de conformidade de acesso condicional.

    ![Imagem do Dashboard de Acesso Condicional](./media/CA-reporting-intune-1.png)

Assim que escolher uma das três áreas, poderá ver mais detalhes sobre os dispositivos que estão a ser permitidos, bloqueados ou colocados em quarentena.

Também pode desagregar em dispositivos específicos para ver mais detalhes. Por exemplo, o dispositivo selecionado na imagem seguinte está bloqueado. O Intune dá-lhe a opção de remover os dados da empresa a partir do painel do relatório de compatibilidade de acesso condicional.

![Imagem de relatórios de detalhes de dispositivos de Acesso condicional](./media/CA-reporting-intune-3.png)

No painel Detalhes do dispositivo, pode ver mais informações:

-   **Descrição geral:** pode ver as propriedades dos dispositivos como: versão do SO, modelo do dispositivo, propriedade, número de série, fabricante do dispositivo, número de telefone e a última vez que o dispositivo deu entrada.

-   **Propriedades:** pode definir a propriedade do dispositivo (Pessoal ou Empresarial).

-   **Hardware:** indica as informações que vê na Descrição Geral e também os detalhes de armazenamento (espaço total e espaço livre), cobertura do sistema, detalhes da rede, serviço de rede e mais detalhes de bloqueio do acesso condicional.

-   **Aplicações Detetadas:** mostra todas as aplicações instaladas no dispositivo. Também pode exportar a lista de aplicações instaladas para o formato .CSV.

-   **Conformidade:** mostra todos os detalhes da política de conformidade do dispositivo.

-   **Configuração do Dispositivo:** mostra todos os detalhes de configuração do dispositivo.

-   **Acesso ao Exchange:** aqui, pode saber mais sobre o estado do dispositivo depois de aplicar as políticas de acesso condicional.
