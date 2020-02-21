---
title: Configurar o Microsoft Intune
description: Requisitos e pré-requisitos para começar a utilizar a sua subscrição do Intune
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/20/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d158503c-1276-422b-ab81-5f66c1cd7e7a
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: b12781c55abc3ce7d9e964b0f139fc4c1d1fd69b
ms.sourcegitcommit: 67f926ba83f8a955e16b741a610ad84d6044f8f9
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/21/2020
ms.locfileid: "77529367"
---
# <a name="set-up-intune"></a>Configurar o Intune

Estes passos de configuração ajudam-no a ativar a gestão de dispositivos móveis (MDM) ao utilizar o Intune. Os dispositivos têm de ser geridos antes de poder conceder acesso aos recursos da empresa por parte dos utilizadores ou gerir as definições nos dispositivos.

Alguns passos, como configurar uma subscrição do Intune e definir a autoridade de MDM, são obrigatórios na maioria dos cenários. Outros passos, tal como configurar um domínio personalizado ou adicionar aplicações, são opcionais, consoante as necessidades da sua empresa.

Se está atualmente a utilizar o Microsoft Endpoint Configuration Manager para gerir computadores e servidores, pode anexar o [Gestor de Configuração em nuvem com cogestão](https://docs.microsoft.com/configmgr/comanage/overview).

>[!TIP]
>Se comprar pelo menos 150 licenças do Intune num plano elegível, pode utilizar o *Benefício do FastTrack Center*. Com este serviço, os especialistas da Microsoft trabalham consigo para preparar o seu ambiente para o Intune. Veja [Benefícios do FastTrack Center do Enterprise Mobility + Security (EMS)](https://docs.microsoft.com/enterprise-mobility-security/Solutions/enterprise-mobility-fasttrack-program).

| Passos | Estado  |
|---|---|
|   1   | [Configurações suportadas](supported-devices-browsers.md) – o que precisa de saber antes de começar. Estão incluídos os requisitos de rede e as configurações suportadas.|
|   2   |  [Iniciar sessão no Intune](account-sign-up.md) – inicie sessão na sua subscrição da avaliação gratuita ou crie uma nova subscrição do Intune. |
|   3   | [Configurar o nome de domínio](custom-domain-name-configure.md) – configure o registo de DNS para associar o nome da sua empresa ao Intune. Assim, os utilizadores verão um domínio familiar ao ligar ao Intune e ao utilizar os recursos. |
|   4   | [Adicione utilizadores](users-add.md) e [grupos](../groups-add.md) - Adicione utilizadores e grupos ou ligue o Ative Directory para sincronizar com o Intune. Obrigatório, a menos que o seus dispositivos sejam dispositivos quiosque "sem utilizador". Os grupos são utilizados para atribuir aplicações, definições e outros recursos.|
|   5   | [Atribuir licenças](../licenses-assign.md) – dê aos utilizadores permissão para utilizarem o Intune. Cada utilizador ou dispositivo sem utilizador necessita de uma licença do Intune para aceder ao serviço. |
|   6   | [Despfique a autoridade do MDM](../mdm-authority-set.md) - Utilize grupos de utilizadores e dispositivos para simplificar as tarefas de gestão. Os grupos são utilizados para atribuir aplicações, definições e outros recursos. |
|   7   | [Adicionar aplicações](../apps/apps-add.md) – as aplicações podem ser atribuídas a grupos e instaladas automática ou opcionalmente. |
|   8   | [Configurar dispositivos](../configuration/device-profiles.md) – configure os perfis que gerem as definições dos dispositivos. Os perfis dos dispositivos podem pré-configurar as definições de e-mail, VPN, Wi-Fi e funcionalidades dos dispositivos. Também podem restringir os dispositivos para ajudar a protegê-los, assim como aos dados. |
|   9   |  [Personalizar o Portal da Empresa](../apps/company-portal-app.md) – personalize o Portal da Empresa do Intune que os utilizadores utilizam para inscrever dispositivos e instalar aplicações. Estas definições são apresentadas na aplicação Portal da Empresa e no site Portal da Empresa do Intune.       |
|  10   | Ativar a [inscrição](mdm-authority-set.md) do dispositivo - Enable Intune gestão de dispositivos iOS/iPadOS, Windows, Android e Mac, definindo a autoridade do MDM e permitindo plataformas específicas. |
|  11   |  [Configurar políticas de aplicações](../apps/app-protection-policy.md) – forneça definições específicas com base nas políticas de proteção de aplicações no Microsoft Intune. |
