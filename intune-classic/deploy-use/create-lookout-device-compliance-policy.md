---
title: "Ativar a regra de proteção do dispositivo"
description: "Ative a regra de proteção contra ameaças móveis na política de conformidade do dispositivo."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/21/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c951692d-6538-46c0-a9f0-d607ded189ae
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: sandera
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: f649227c6ad49cd9c788e75097bc4a5eeb71f350
ms.sourcegitcommit: 468480b61110ca81f737582ebbefd4efda6fd667
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/30/2018
---
# <a name="create-lookout-device-compliance-policy-in-intune"></a>Criar Política de conformidade do dispositivo do Lookout no Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

O Intune com a Defesa Contra Ameaças para Dispositivos Móveis do Lookout permite detetar ameaças em dispositivos móveis e avaliar o risco nesses dispositivos. Pode criar uma regra de política de conformidade que avalie o risco para determinar se o dispositivo está em conformidade. Em seguida, pode utilizar a política de acesso condicional para bloquear o acesso aos serviços com base na conformidade do dispositivo.

Pré-requisitos da política de conformidade com a Defesa Contra Ameaças para Dispositivos Móveis do Lookout:

- [Configurar a subscrição da Defesa Contra Ameaças para Dispositivos Móveis do Lookout](setup-your-lookout-mtd-subscription.md)
- [Ativar a ligação Lookout no Intune](enable-lookout-mtd-connection.md)
- [Configurar e implementar a aplicação Lookout for Work](configure-deploy-lookout-for-work-app.md)

Como parte da configuração da Defesa Contra Ameaças para Dispositivos Móveis do Lookout, na [Consola do Lookout](https://aad.lookout.com), criou uma política que classifica as várias ameaças como sendo de nível alto, médio e baixo. Na política de conformidade do Intune, configurará o nível de ameaça máximo permitido.

1. Na [consola do administrador do Intune](https://manage.microsoft.com), aceda à página **Políticas de Conformidade**. Pode utilizar uma política de conformidade existente ou criar uma política nova. Aceda a **Estado de Funcionamento do Dispositivo** e ative a opção **Proteção contra Ameaças de Dispositivos**.
  ![captura de ecrã que apresenta as definições da regra de proteção contra ameaças de dispositivos](../media/mtp/mtp-compliance-policy-rule.png)

2. Selecione o **Nível de Ameaça Máximo permitido**:
  * **Nenhum (Seguro)**: este é o nível mais seguro.  O dispositivo não pode aceder aos recursos da empresa se contiver ameaças.  Se forem detetadas ameaças, o dispositivo será avaliado como não conforme.  
  * **Baixo**: o dispositivo está em conformidade se só estiverem presentes ameaças de nível baixo. Qualquer nível mais alto coloca o dispositivo num estado de não conforme.
  * **Médio**: o dispositivo está em conformidade se as ameaças encontradas forem de nível baixo ou médio. Se forem detetadas ameaças de nível alto, o estado do dispositivo será determinado como não conforme.
  * **Alto**: este é o nível menos seguro. Este nível permite que todos os níveis de ameaça estejam presentes e utiliza a proteção contra ameaças móveis do Lookout apenas para a criação de relatórios.

![captura de ecrã que apresenta a opção do nível de ameaça nas definições da regra de proteção contra ameaças de dispositivos](../media/mtp/mtp-compliance-policy-setting.png)

Se criar políticas de acesso condicional para o Office 365 ou outros serviços, esta avaliação de conformidade é analisada e os dispositivos que não estiverem conformes não poderão aceder a esses serviços até que a ameaça esteja resolvida.

## <a name="monitor-device-threats"></a>Monitorizar ameaças a dispositivos
Para ver o estado de conformidade de um dispositivo, aceda à [consola do administrador do Intune](https://manage.microsoft.com) e consulte **Todos os Dispositivos**.

![captura de ecrã da página do dispositivo na consola de administração do Intune que apresenta o estado de conformidade de um dispositivo](../media/mtp/mtp-device-status-intune-console.png)

## <a name="next-steps"></a>Próximos passos
* Criar uma política de acesso condicional
  * [Exchange Online](restrict-access-to-exchange-online-with-microsoft-intune.md)
  * [Exchange no local](restrict-access-to-exchange-onpremises-with-microsoft-intune.md)
  * [SharePoint Online](restrict-access-to-sharepoint-online-with-microsoft-intune.md)
  * [Skype para Empresas Online](restrict-access-to-skype-for-business-online-with-microsoft-intune.md)
  * [Dynamics CRM](restrict-access-to-dynamics-crm-online-with-microsoft-intune.md)
