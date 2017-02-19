---
title: "Ativar a regra de proteção do dispositivo | Documentos da Microsoft"
description: "Ative a regra de proteção contra ameaças móveis na política de conformidade do dispositivo."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c951692d-6538-46c0-a9f0-d607ded189ae
ms.reviewer: sandera
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 9f05e516723976dcf6862475dbb78f9dce2913be
ms.openlocfilehash: 08edca426901eda3017bf17dda3b330dd186ce58


---

# <a name="enable-device-threat-protection-rule-in-the-compliance-policy"></a>Ativar a regra de proteção contra ameaças de dispositivo na política de conformidade

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

O Intune com proteção contra ameaças móveis do Lookout permite detetar ameaças em dispositivos móveis e avaliar o risco nesses dispositivos. Pode criar uma regra de política de conformidade que avalie o risco para determinar se o dispositivo está em conformidade. Em seguida, pode utilizar a política de acesso condicional para bloquear o acesso aos serviços com base na conformidade do dispositivo.

Pré-requisitos da política de conformidade com a proteção contra ameaças de dispositivos do Lookout:

- [Configurar a subscrição da proteção contra ameaças de dispositivos do Lookout](set-up-your-subscription-with-lookout-mtp.md)
- [Ativar a ligação Lookout no Intune](enable-lookout-mtp-connection-in-intune.md)
- [Configurar a aplicação Lookout for Work](configure-and-deploy-lookout-for-work-apps.md)

Como parte da configuração da proteção contra ameaças de dispositivos do Lookout, na [consola do Lookout](https://aad.lookout.com), criou uma política que classifica as várias ameaças como sendo de nível alto, médio e baixo. Na política de conformidade do Intune, configurará o nível de ameaça máximo permitido.

1. Na [consola do administrador do Intune](https://manage.microsoft.com), aceda à página **Políticas de Conformidade**. Pode utilizar uma política de conformidade existente ou criar uma política nova. Aceda a **Estado de Funcionamento do Dispositivo** e ative a opção **Proteção contra Ameaças de Dispositivos**.
  ![captura de ecrã que apresenta as definições da regra de proteção contra ameaças de dispositivos](../media/mtp/mtp-compliance-policy-rule.png)

2. Selecione o **Nível de Ameaça Máximo permitido**:
  * **Nenhum (Seguro)**: este é o nível mais seguro.  O dispositivo não pode aceder aos recursos da empresa se contiver ameaças.  Se forem encontradas ameaças, o dispositivo será avaliado como não conforme.  
  * **Baixo**: o dispositivo está em conformidade se só estiverem presentes ameaças de nível baixo. Qualquer nível mais alto coloca o dispositivo num estado de não conforme.
  * **Médio**: o dispositivo está em conformidade se as ameaças encontradas forem de nível baixo ou médio. Se forem detetadas ameaças de nível alto, o dispositivo será determinado como não conforme.
  * **Alto**: este é o nível menos seguro. Este nível permite que todos os níveis de ameaça estejam presentes e utiliza a proteção contra ameaças móveis do Lookout apenas para a criação de relatórios.

![captura de ecrã que apresenta a opção do nível de ameaça nas definições da regra de proteção contra ameaças de dispositivos](../media/mtp/mtp-compliance-policy-setting.png)

Se criar políticas de acesso condicional para o Office 365 ou outros serviços, esta avaliação de conformidade é analisada e os dispositivos que não estiverem conformes não poderão aceder a esses serviços até que a ameaça esteja resolvida.

## <a name="monitor-device-threats"></a>Monitorizar ameaças a dispositivos
Para ver o estado de conformidade de um dispositivo, aceda à [consola do administrador do Intune](https://manage.microsoft.com) e consulte **Todos os Dispositivos**.

![captura de ecrã da página do dispositivo na consola de administração do Intune que apresenta o estado de conformidade de um dispositivo](../media/mtp/mtp-device-status-intune-console.png)

## <a name="next-steps"></a>Passos seguintes
* Criar uma política de acesso condicional
  * [Exchange Online](restrict-access-to-exchange-online-with-microsoft-intune.md)
  * [Exchange no local](restrict-access-to-exchange-onpremises-with-microsoft-intune.md)
  * [SharePoint Online](restrict-access-to-sharepoint-online-with-microsoft-intune.md)
  * [Skype para Empresas Online](restrict-access-to-skype-for-business-online-with-microsoft-intune.md)
  * [Dynamics CRM](restrict-access-to-dynamics-crm-online-with-microsoft-intune.md)



<!--HONumber=Jan17_HO4-->

