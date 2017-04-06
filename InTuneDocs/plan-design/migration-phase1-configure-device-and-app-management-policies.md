---
title: "Configurar políticas de gestão de aplicações e de conformidade do dispositivo durante uma migração do Intune | Documentos da Microsoft"
description: "O objetivo deste artigo é proporcionar os passos necessários para configurar as políticas de gestão de aplicações e de conformidade do dispositivo durante uma migração do Intune."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/24/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0062d08e-e5b3-4f73-8b64-5ad95adbe945
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: ab5aa4e12d951d818c5afb4e1ac5e866b05733fb
ms.openlocfilehash: 5904b117ccab9046d2afde4a761b4724431a6302
ms.lasthandoff: 03/27/2017


---

# <a name="phase-1-configure-device-compliance-and-app-management-policies"></a>Fase 1: Configurar políticas de gestão de aplicações e de conformidade do dispositivo

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

O objetivo principal durante a migração para o Intune é ter todos os dispositivos inscritos e em conformidade com as políticas. As políticas de dispositivo não só o ajudam a gerir dispositivos de utilizador único pertencentes à empresa, como também dispositivos pessoais (BYOD) e partilhados, tais como quiosques, máquinas de pontos de venda, tablets partilhados por vários estudantes numa sala de aula ou dispositivos sem utilizador (apenas iOS).

Cada plataforma do dispositivo poderá oferecer definições diferentes, mas as políticas de dispositivos do Intune trabalham com cada plataforma do dispositivo ao proporcionar as seguintes capacidades de gestão de dispositivos móveis:

-   Regular o número de dispositivos que cada utilizador inscreve.

-   Gerir as definições de dispositivos (por exemplo, a encriptação ao nível do dispositivo, o comprimento da palavra-passe, a utilização da câmara).

-   Disponibilizar aplicações, perfis de e-mail, perfis da VPN, etc.

-   Avaliar os critérios ao nível do dispositivo das políticas de conformidade de segurança.

> [!IMPORTANT]
> As políticas de gestão de dispositivos não são atribuídas diretamente aos dispositivos ou utilizadores individuais, mas, em vez disso, são atribuídas a grupos de utilizadores. As políticas podem ser aplicadas diretamente a um grupo de utilizadores (ou seja, ao dispositivo do utilizador) ou podem ser aplicadas a um grupo de dispositivos (ou seja, aos membros do grupo).

## <a name="task-list-for-device-compliance-policies"></a>Lista de tarefas das políticas de conformidade de dispositivo

### <a name="task-1-add-device-groups-optional"></a>Tarefa 1: Adicionar grupos de dispositivos (opcional)

O [portal clássico do Intune](https://manage.microsoft.com/) dá-lhe a possibilidade de criar grupos de dispositivos, quando tiver de realizar uma variedade de tarefas administrativas com base na identidade de dispositivo, em vez da identidade do utilizador.

Os grupos de dispositivos são úteis para a gestão de dispositivos sem utilizadores dedicados, tais como dispositivos de local público ou dispositivos partilhados por trabalhadores de turnos ou atribuídos a uma localização específica.

Ao configurar grupos de dispositivos antes da inscrição de dispositivos, pode tirar partido das categorias de dispositivos para os agrupar automaticamente após a inscrição e receber automaticamente as políticas de dispositivos do grupo.

-   Saiba [como adicionar grupos de dispositivos](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-5).

-   Saiba [como configurar categorias de dispositivos](https://docs.microsoft.com/intune/deploy-use/categorize-devices-with-device-group-mapping-in-microsoft-intune).

### <a name="task-2-use-resource-access-profiles-wi-fi-vpn-and-email-certificates"></a>Tarefa 2: Utilizar perfis de acesso a recursos (certificados de e-mail, Wi-Fi e VPN)

Certificados de aprovisionamento dos perfis de acesso a recursos e configurações de acesso a dispositivos inscritos.

Como foi anteriormente abordado na secção Avaliar requisitos de MDM, precisará de ter uma [infraestrutura PKI no local](https://docs.microsoft.com/intune/deploy-use/secure-resource-access-with-certificate-profiles) para implementar certificados de e-mail, Wi-Fi e VPN se estiver a utilizar a autenticação baseada em certificados.

#### <a name="direct-import-of-resource-access-profiles-optional"></a>Importação direta de perfis de acesso a recursos (opcional)

Se a sua solução MDM existente proporcionar um mecanismo para exportar perfis de VPN, Wi-Fi e e-mail para o formato XML, poderá conseguir tirar partido do ficheiro XML e importá-lo para o Intune ao utilizar o OMA-URI para criar perfis personalizados para dispositivos iOS, Android e Windows.

-   Saiba como adicionar uma política personalizada para dispositivos [iOS](https://docs.microsoft.com/intune/deploy-use/ios-policy-settings-in-microsoft-intune), [Android](https://docs.microsoft.com/intune/deploy-use/android-policy-settings-in-microsoft-intune) e [Windows](https://docs.microsoft.com/intune/deploy-use/windows-10-policy-settings-in-microsoft-intune).

### <a name="task-3-create-and-deploy-device-configuration-profiles"></a>Tarefa 3: Criar e implementar perfis de configuração de dispositivos

Tem de criar um perfil de configuração de dispositivos para impor definições ao nível do dispositivo, por exemplo: desativar a câmara, a loja de aplicações, configurar o modo de aplicação única, o ecrã principal, etc.

- Saiba mais sobre os [perfis de configuração de dispositivos](https://docs.microsoft.com/intune-azure/configure-devices/how-to-create-device-profiles).

####  <a name="direct-import-of-ios-configuration-profiles-optional"></a>Importação direta de perfis de configuração do iOS (opcional)

-   **Perfis de iOS do Apple Configurator (iOS 7.1 e posterior):** se a sua solução de MDM existente utilizar perfis do Apple Configurator (ficheiros .mobileconfig), o Intune poderá importá-los diretamente como políticas de configuração personalizadas.

-   **Políticas de Configuração da Aplicação Móvel do iOS:** se a sua solução de MDM existente utilizar políticas de Configuração da Aplicação Móvel do iOS, o Intune poderá importá-las diretamente, desde que cumpram o formato XML especificado pela Apple para as listas de propriedades.

- Saiba como adicionar uma política personalizada para [iOS](https://docs.microsoft.com/intune/deploy-use/ios-policy-settings-in-microsoft-intune#custom-policy-settings)

### <a name="task-4-create-and-deploy-device-compliance-policies-optional"></a>Tarefa 4: Criar e implementar políticas de conformidade do dispositivo (opcional)

As políticas de conformidade do dispositivo avaliam as definições dedicadas à segurança e disponibilizam relatórios que mostram se os dispositivos estão ou não em conformidade com os padrões empresariais. As políticas de conformidade do dispositivo avaliam fatores de segurança, tais como:

-   Comprimento do PIN

-   Estado Jailbreak

-   Versão do SO

Veja recursos adicionais para as definições de conformidade do dispositivo:

-   Saiba mais sobre as [políticas de conformidade do dispositivo](https://docs.microsoft.com/intune/deploy-use/introduction-to-device-compliance-policies-in-microsoft-intune).

-   Saiba [como criar uma política de conformidade do dispositivo](https://docs.microsoft.com/intune/deploy-use/create-a-device-compliance-policy-in-microsoft-intune).

### <a name="task-5-publish-and-deploy-apps"></a>Tarefa 5: Publicar e implementar Aplicações

Ao utilizar o Intune MDM, pode aprovisionar aplicações ao exigir a sua instalação automática ou ao disponibilizá-las no Portal da Empresa.

-   Saiba [como adicionar aplicações](https://docs.microsoft.com/intune/deploy-use/add-apps).

-   Saiba [como implementar aplicações](https://docs.microsoft.com/intune/deploy-use/deploy-apps).

### <a name="task-6-enable-device-enrollment"></a>Tarefa 6: Ativar a inscrição de dispositivos

A inscrição estabelece a gestão ao aprovisionar o controlo no dispositivo.

-   Saiba [como se preparar para inscrever dispositivos pessoais do utilizador pertencentes à empresa](https://docs.microsoft.com/intune/deploy-use/enroll-devices-in-microsoft-intune).

-   Saiba [como inscrever dispositivos pertencentes à empresa](https://docs.microsoft.com/intune/deploy-use/manage-corporate-owned-devices).

Se precisar de inscrever dispositivos partilhados ou sem utilizador, poderá utilizar uma [conta de gestor de inscrição de dispositivos (DEM)](https://docs.microsoft.com/intune/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune).

## <a name="next-steps"></a>Próximos passos 

[Fase 1: Configurar Políticas de Proteção de Aplicações (opcional)](https://docs.microsoft.com/intune/plan-design/migration-phase1-configure-app-protection-policies)

