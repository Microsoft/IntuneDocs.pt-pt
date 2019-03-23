---
title: Monitorizar o acesso condicional do Exchange no Microsoft Intune | Microsoft Intune
description: Monitorize a conformidade do acesso condicional do Exchange Online e no Exchange no local através do portal do Azure no Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/22/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5712682d-285b-43fd-9978-3dcfd95ec5f9
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8ebca668ba3e02ec6088bb72370d7d5061241627
ms.sourcegitcommit: 1069b3b1ed593c94af725300aafd52610c7d8f04
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2019
ms.locfileid: "58394933"
---
# <a name="monitor-conditional-access-compliance-for-exchange-on-premises-in-intune"></a>Monitorizar a conformidade de acesso condicional do Exchange no local no Intune

Os administradores do Intune, pode ver relatórios relacionados com registos de dispositivo do Exchange ActiveSync que são sincronizados com o Intune através do conector do Exchange no local. O relatório de compatibilidade de acesso condicional apresenta um resumo dos dispositivos com diferentes estados de sincronização:

- **Permitir**

- **Bloquear**

- **Quarentena**

## <a name="to-monitor-conditional-access-compliance"></a>Para monitorizar a compatibilidade de acesso condicional

1. Inicie sessão no [Intune](https://aka.ms/intuneportal)e aceda à **acesso condicional**, em seguida, escolha **descrição geral**.

2. Selecione uma das três áreas (**Permitido**, **Bloqueado** ou **Quarentena**) no gráfico para ver os relatórios de conformidade de acesso condicional.

   ![Imagem do Dashboard de Acesso Condicional](./media/CA-reporting-intune-1.png)

Assim que escolher uma das três áreas, poderá ver mais detalhes sobre os dispositivos que estão a ser permitidos, bloqueados ou colocados em quarentena.

Também pode consultar mais detalhes nos dispositivos específicos. Por exemplo, o dispositivo selecionado na imagem seguinte está bloqueado. O Intune dá-lhe a opção de remover os dados da empresa a partir do painel do relatório de compatibilidade de acesso condicional.

![Imagem de relatórios de detalhes de dispositivos de Acesso condicional](./media/CA-reporting-intune-3.png)

No painel Detalhes do dispositivo, pode ver mais informações:

- **Descrição geral:** Pode ver as propriedades dos dispositivos como: Versão do SO, modelo do dispositivo, propriedade, número de série, fabricante do dispositivo, número de telefone e última vez que o dispositivo deu entrado.

- **Propriedades:** Pode definir a propriedade do dispositivo (pessoal ou empresarial).

- **Hardware:** Ele fornece as informações que vê na descrição geral e também os detalhes de armazenamento (espaço total e espaço livre), cobertura do sistema, detalhes da rede, serviço de rede e mais acesso condicional a bloquear detalhes.

- **Aplicações detetadas:** Mostra todas as aplicações instaladas no dispositivo. Também pode exportar a lista de aplicações instaladas para o formato .CSV.

- **Conformidade:** Ela mostra a conformidade do dispositivo todos os detalhes da política.

- **Configuração do dispositivo:** Mostra todos os detalhes de configuração do dispositivo.

- **Acesso do Exchange:** Aqui pode saber mais sobre o estado do dispositivo depois de aplicar políticas de acesso condicional.
