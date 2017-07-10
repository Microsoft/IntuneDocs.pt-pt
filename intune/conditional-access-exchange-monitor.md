---
title: Monitorizar a compatibilidade de acesso condicional no Exchange Online e no Exchange no local
titleSuffix: Intune on Azure
description: "Monitorizar a compatibilidade de acesso condicional no Exchange Online e no Exchange no local através do portal do Azure no Intune"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 04/24/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5712682d-285b-43fd-9978-3dcfd95ec5f9
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 2ec9bcc605486258203f49f9f7631bd2a04cdf22
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/01/2017
---
# <a name="monitor-conditional-access-compliance-for-on-premises-exchange-and-exchange-online-in-intune"></a>Monitorizar a conformidade de acesso condicional no Exchange Online e no Exchange no local no Intune

A partir da versão 1704 do Intune, os administradores podem ver informações de relatórios relacionadas com os registos de dispositivos do Exchange ActiveSync que são sincronizados com o Intune através do Exchange Connector no local ou do conector de serviços do Intune (conector do Exchange Online). O relatório de compatibilidade de acesso condicional apresenta um resumo dos dispositivos com diferentes estados de sincronização:

-   **Permitir**

-   **Bloquear**

-   **Quarentena**

## <a name="to-monitor-conditional-access-compliance"></a>Para monitorizar a compatibilidade de acesso condicional

1.  Aceda ao [portal do Azure](https://portal.azure.com/) e inicie sessão com as credenciais do Intune.

2.  Depois de iniciar sessão com êxito, verá o **Dashboard do Azure**.

3.  Selecione **Mais serviços** no menu à esquerda e, em seguida, escreva **Intune** no filtro da caixa de texto.

4.  Escolha **Intune**, será apresentado o **Dashboard do Intune**.

5.  Escolha **Acesso Condicional** e, em seguida, escolha **Descrição Geral**.

6.  Escolha uma das três áreas (**Bloqueado**, **Quarentena** ou **Permitido**) no gráfico para ver os relatórios de conformidade de acesso condicional.

    ![Dashboard de Acesso Condicional](./media/CA-reporting-intune-1.png)

Assim que escolher uma das três áreas, pode ver mais detalhes sobre os dispositivos que estão a ser permitidos, bloqueados ou colocados em quarentena.

Também pode consultar mais detalhes nos dispositivos específicos. Por exemplo, o dispositivo selecionado na imagem abaixo está bloqueado. O Intune dá-lhe a opção de remoção dos dados da empresa a partir do painel do relatório de compatibilidade de acesso condicional.

![Relatórios de detalhes de dispositivos de acesso condicional](./media/CA-reporting-intune-3.png)

No painel de detalhes do dispositivo, pode ver mais informações:

-   **Descrição geral:** pode ver as propriedades dos dispositivos como: versão do SO, modelo do dispositivo, propriedade, número de série, fabricante do dispositivo, número de telefone e a última vez que o dispositivo deu entrada.

-   **Propriedades:** pode definir a propriedade do dispositivo (Pessoal ou Empresarial).

-   **Hardware:** indica as informações que vê na Descrição Geral e também os detalhes de armazenamento (espaço total e espaço livre), cobertura do sistema, detalhes da rede, serviço de rede e mais detalhes de bloqueio do acesso condicional.

-   **Aplicações Detetadas:** mostra todas as aplicações instaladas no dispositivo. Também pode exportar a lista de aplicações instaladas para o formato .CSV.

-   **Conformidade:** mostra todos os detalhes da política de conformidade do dispositivo.

-   **Configuração do Dispositivo:** mostra todos os detalhes de configuração do dispositivo.

-   **Acesso ao Exchange:** aqui, pode saber mais sobre o estado do dispositivo depois de aplicar as políticas de acesso condicional.
