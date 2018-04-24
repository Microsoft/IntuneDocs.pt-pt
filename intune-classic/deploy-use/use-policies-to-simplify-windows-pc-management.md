---
title: Utilizar políticas para simplificar a gestão de PCs Windows
description: Descreve as políticas de gestão de PCs Windows e as definições do Microsoft Intune Center.
keywords: ''
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 12/15/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f0afda7e-f4c3-4bcd-b4bf-4304103cf73e
ms.reviewer: owenyen
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 519d6d3c9bef29bb7990fd8e0df28bb15e5c48e7
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/16/2018
---
# <a name="use-policies-to-simplify-windows-pc-management"></a>Utilizar políticas para simplificar a gestão de PCs Windows

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Para gerir computadores Windows como PCs ao executar o cliente de software do Intune nos mesmos, só pode utilizar as políticas em **Gestão de Computadores** na consola de administração do Intune. Todas as outras políticas listadas na consola de administração destinam-se apenas a dispositivos móveis. Através das políticas de **Gestão de Computadores**, pode configurar as definições no Microsoft Intune Center, controlar as atualizações nos PCs e configurar a Firewall do Windows para PCs.

![Modelo de políticas para PCs Windows](../media/pc_policy_template.png)

### <a name="manage-the-microsoft-intune-center"></a>Gerir o Centro do Microsoft Intune
Os utilizadores veem o cliente de software do Intune como o **Microsoft Intune Center**. O Centro do Microsoft Intune permite aos utilizadores:

-   Obter aplicações a partir do portal da empresa.

-   Procurar atualizações.

-   Gerir o Endpoint Protection do Microsoft Intune.

-  Pedir assistência remota.

O Centro do Microsoft Intune é instalado em todos os computadores geridos. Pode configurar as seguintes definições numa política do Intune e estas serão apresentadas aos utilizadores no Centro do Microsoft Intune:

|Definição de política|Detalhes|
|------------------|--------------------|
|**Nome**|O nome do administrador que gere o computador.<br />Comprimento máximo: 40 carateres|
|**Número de telefone**|O número de telefone do administrador que gere o computador.<br />Comprimento máximo: 20 carateres|
|**Endereço de e-mail**|O endereço de e-mail do administrador que gere o computador.<br />Comprimento máximo: 40 carateres|
|**Nome do site**|O nome do seu site de suporte para utilizadores.<br />>Comprimento máximo: 40 carateres|
|**URL do site**|O URL do seu site de suporte.<br />Comprimento máximo: 150 carateres|
|**Notas**|Uma nota que é apresentada aos utilizadores.<br />Comprimento máximo: 120 carateres|

Consulte os seguintes recursos para obter informações sobre as políticas e definições que pode configurar para PCs Windows:

- [Manter os PCs Windows atualizados com atualizações de software no Microsoft Intune](keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md) – estas políticas verificam os computadores geridos e transferem atualizações de software da Microsoft e de terceiros. Estas atualizações não incluem atualizações do SO (por exemplo, atualizar do Windows 7 para o Windows 10 ou atualizações de uma versão do Windows 10 para uma versão posterior).

- [Ajudar a proteger os PCs Windows com o Endpoint Protection para o Microsoft Intune](help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md) – estas definições incluem agendamentos de análises e ações a efetuar quando for detetado software maligno.

- [Ajudar a proteger os PCs Windows que utilizam políticas da Firewall do Windows no Microsoft Intune](help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune.md) – estas políticas simplificam a administração das definições da Firewall do Windows nos computadores geridos.


### <a name="see-also"></a>Consulte também

[Tarefas de gestão comuns de PCs Windows com o cliente de software do Intune](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)
