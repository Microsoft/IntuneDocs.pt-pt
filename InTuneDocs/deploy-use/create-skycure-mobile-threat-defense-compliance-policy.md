---
title: "Criar a política de conformidade da Defesa Contra Ameaças para Dispositivos Móveis do Skycure no Intune | Documentos da Microsoft"
description: "Crie a política de conformidade da Defesa Contra Ameaças para Dispositivos Móveis do Skycure na consola clássica do Intune."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/16/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 56ff1728-1119-4e8a-aae6-ed5c7fafa052
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: ab6d9b6b296fb4e1fb0aaa9496fede28976728dc
ms.openlocfilehash: a2597a43e48d8cdde6c29070986528dcba473d8e
ms.lasthandoff: 04/14/2017


---

# <a name="create-skycure-mobile-threat-defense-compliance-policy"></a>Criar a política de conformidade da Defesa Contra Ameaças para Dispositivos Móveis do Skycure

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

O Intune com a Defesa Contra Ameaças para Dispositivos Móveis do Skycure permite detetar ameaças em dispositivos móveis e avaliar o risco nesses dispositivos. Pode criar uma regra de política de conformidade do Intune que avalie o risco para determinar se o dispositivo está conforme. Em seguida, pode utilizar a política de acesso condicional para bloquear o acesso aos serviços com base na conformidade do dispositivo.

## <a name="before-you-begin"></a>Antes de começar

Pré-requisitos da política de conformidade com a proteção contra ameaças de dispositivos do Skycure:

-   [Configurar a integração do Skycure com o Intune](https://docs.microsoft.com/intune/deploy-use/setup-the-skycure-integration-with-Intune)

-   [Ativar a ligação do Skycure no Intune](https://docs.microsoft.com/intune/deploy-use/enable-skycure-mobile-threat-defense-in-intune)

Como parte da Defesa Contra Ameaças para Dispositivos Móveis do Skycure, na consola do Lookout, criou uma política que classifica as várias ameaças como sendo de nível alto, médio e baixo. Na política de conformidade do Intune, precisa agora de definir o nível de ameaça máximo permitido.

## <a name="to-create-skycure-compliance-policy"></a>Para criar a política de conformidade do Skycure

1.  Aceda à [consola clássica do Intune](https://manage.microsoft.com/) e introduza as suas credenciais.

2.  Escolha **Política** &gt; **Políticas de Conformidade**. Pode utilizar uma política de conformidade existente ou criar uma política nova.

3.  Escolha **Adicionar** &gt; **Estado de Funcionamento do Dispositivo** e, em seguida, ative **Proteção Contra Ameaças de Dispositivos**.

4.  Selecione o **Nível de Ameaça Máximo permitido**:

    a.  **Nenhum (Seguro)**: este é o nível mais seguro. O dispositivo não pode aceder aos recursos da empresa se contiver ameaças. Se forem encontradas ameaças, o dispositivo será avaliado como não conforme.

    b.  **Baixo**: o dispositivo está em conformidade se só estiverem presentes ameaças de nível baixo. Qualquer nível mais alto coloca o dispositivo num estado de não conforme.

    c.  **Médio**: o dispositivo está em conformidade se as ameaças encontradas forem de nível baixo ou médio. Se forem detetadas ameaças de nível alto, o dispositivo será determinado como não conforme.

    d.  **Alto**: este é o nível menos seguro. Este nível permite que todos os níveis de ameaça estejam presentes e utiliza a defesa contra ameaças para dispositivos móveis do Skycure apenas para a criação de relatórios.

> [!IMPORTANT] 
> Se criar políticas de acesso condicional para o Office 365 ou outros serviços, esta avaliação de conformidade é analisada e os dispositivos que não estiverem conformes não poderão aceder a esses serviços até que a ameaça esteja resolvida.

## <a name="span-idmonitor-device-threats-classanchorspan-idnext-steps-classanchorspan-idtoc477360344-classanchorspanspanspannext-steps"></a><span id="monitor-device-threats" class="anchor"><span id="next-steps" class="anchor"><span id="_Toc477360344" class="anchor"></span></span></span>Passos seguintes

-   Crie uma política de acesso condicional para:

    -   [Exchange Online](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-exchange-online-with-microsoft-intune)
    -   [Exchange no local](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-exchange-onpremises-with-microsoft-intune)
    -   [SharePoint Online](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-sharepoint-online-with-microsoft-intune)
    -   [Skype para Empresas Online](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-skype-for-business-online-with-microsoft-intune)
    -   [Dynamics CRM](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-dynamics-crm-online-with-microsoft-intune)

