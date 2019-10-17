---
title: Configurar Microsoft Intune
description: Requisitos e pré-requisitos para começar a utilizar a sua subscrição do Intune
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/24/2018
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
ms.openlocfilehash: 7a45160fc0e728b4c53590455a2bd0b5d904ddb1
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72504893"
---
# <a name="set-up-intune"></a>Configurar o Intune

Estes passos de configuração ajudam-no a ativar a gestão de dispositivos móveis (MDM) ao utilizar o Intune. Os dispositivos têm de ser geridos antes de poder conceder acesso aos recursos da empresa por parte dos utilizadores ou gerir as definições nos dispositivos.

Alguns passos, como configurar uma subscrição do Intune e definir a autoridade de MDM, são obrigatórios na maioria dos cenários. Outros passos, tal como configurar um domínio personalizado ou adicionar aplicações, são opcionais, consoante as necessidades da sua empresa.

Se estiver usando o Microsoft System Center Configuration Manager no momento para gerenciar computadores e servidores, você poderá [anexar a nuvem Configuration Manager com o cogerenciamento](https://docs.microsoft.com/sccm/comanage/overview).

>[!TIP]
>Se comprar pelo menos 150 licenças do Intune num plano elegível, pode utilizar o *Benefício do FastTrack Center*. Com este serviço, os especialistas da Microsoft trabalham consigo para preparar o seu ambiente para o Intune. Veja [Benefícios do FastTrack Center do Enterprise Mobility + Security (EMS)](https://docs.microsoft.com/enterprise-mobility-security/Solutions/enterprise-mobility-fasttrack-program).



| Passos |                                                                                                                       Estado                                                                                                                       |
|-------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   1   |                                        [Configurações suportadas](supported-devices-browsers.md) – o que precisa de saber antes de começar. Estão incluídos os requisitos de rede e as configurações suportadas.                                         |
|   2   |                                                                 [Iniciar sessão no Intune](account-sign-up.md) – inicie sessão na sua subscrição da avaliação gratuita ou crie uma nova subscrição do Intune.                                                                  |
|   3   |                [Configurar o nome de domínio](custom-domain-name-configure.md) – configure o registo de DNS para associar o nome da sua empresa ao Intune. Assim, os utilizadores verão um domínio familiar ao ligar ao Intune e ao utilizar os recursos.                |
|   4   |                                   [Adicionar utilizadores](users-add.md) – adicione utilizadores manualmente ou associe o Active Directory para sincronizar os utilizadores com o Intune. Obrigatório, a menos que o seus dispositivos sejam dispositivos quiosque "sem utilizador".                                    |
|   5   |                                            [Atribuir licenças](../licenses-assign.md) – dê aos utilizadores permissão para utilizarem o Intune. Cada utilizador ou dispositivo sem utilizador necessita de uma licença do Intune para aceder ao serviço.                                             |
|   6   |                                               [Adicionar grupos](../groups-add.md) – utilize grupos de utilizadores e dispositivos para simplificar as tarefas de gestão. Os grupos são utilizados para atribuir aplicações, definições e outros recursos.                                                |
|   7   |                                                                        [Adicionar aplicações](../apps/apps-add.md) – as aplicações podem ser atribuídas a grupos e instaladas automática ou opcionalmente.                                                                         |
|   8   | [Configurar dispositivos](../configuration/device-profiles.md) – configure os perfis que gerem as definições dos dispositivos. Os perfis dos dispositivos podem pré-configurar as definições de e-mail, VPN, Wi-Fi e funcionalidades dos dispositivos. Também podem restringir os dispositivos para ajudar a protegê-los, assim como aos dados. |
|   9   |       [Personalizar o Portal da Empresa](../apps/company-portal-app.md) – personalize o Portal da Empresa do Intune que os utilizadores utilizam para inscrever dispositivos e instalar aplicações. Estas definições são apresentadas na aplicação Portal da Empresa e no site Portal da Empresa do Intune.       |
|  10   |                                [Ativar a inscrição de dispositivos](mdm-authority-set.md) – ative a gestão do Intune em dispositivos iOS, Windows, Android e Mac ao definir a autoridade de MDM e ao ativar plataformas específicas.                                 |
|  11   |                                                        [Configurar políticas de aplicações](../apps/app-protection-policy.md) – forneça definições específicas com base nas políticas de proteção de aplicações no Microsoft Intune.                                                         |
