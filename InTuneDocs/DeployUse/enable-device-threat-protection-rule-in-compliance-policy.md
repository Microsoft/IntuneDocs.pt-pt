---
title: "Ativar a regra de proteção do dispositivo na política de conformidade | Microsoft Intune"
description: "Ative a regra de proteção contra ameaças móveis na política de conformidade do dispositivo."
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 09/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c951692d-6538-46c0-a9f0-d607ded189ae
ms.reviewer: sandera
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 686321a1c19acb9a3a7e262822b11304d07adb40
ms.openlocfilehash: 3e6aef013ae8764d9b031e880c333e184191feb4


---

# <a name="enable-device-threat-protection-rule-in-the-compliance-policy"></a>Ativar a regra de proteção contra ameaças de dispositivo na política de conformidade
O Intune com o Lookout Mobile Threat Protection permite-lhe detetar ameaças e avaliar os riscos no dispositivo. Pode criar uma regra da política de conformidade para incluir a avaliação de riscos para determinar se o dispositivo está em conformidade. Pode utilizar a política de acesso condicional para permitir ou bloquear o acesso ao Exchange, o SharePoint e outros serviços com base na conformidade do dispositivo.

Para que a deteção de ameaças de dispositivos do Lookout influencie a política de conformidade do dispositivo:

* A regra de **Proteção Contra Ameaças de Dispositivos** tem de ser ativada na política de conformidade.

* A página **Estado do Lookout** na **Consola de Administrador do Intune** tem de apresentar a opção **Ativado**. Consulte [Enable Lookout MTP connection in Intune (Ativar a ligação do Lookout MTP ao Intune – em inglês)](enable-lookout-mtp-connection-in-intune.md) para obter mais detalhes e instruções sobre como ativar a integração do Lookout.


Antes de criar uma regra de proteção contra ameaças de dispositivos na política de conformidade, recomendamos que [configure a sua subscrição para a proteção contra ameaças de dispositivos do Lookout](set-up-your-subscription-with-lookout-mtp.md), [ative a ligação do Lookout no Intune](enable-lookout-mtp-connection-in-intune.md) e [configure a aplicação Lookout for Work](configure-and-deploy-lookout-for-work-apps.md). A regra de conformidade é aplicada apenas quando a configuração estiver concluída.

Para ativar a regra de proteção contra ameaças de dispositivos, pode utilizar uma política de conformidade existente ou pode criar uma política nova.

Como parte da configuração da proteção contra ameaças de dispositivos do Lookout, na [consola do Lookout](https://aad.lookout.com), criou uma política que classifica as várias ameaças nos níveis alto, médio e baixo. Na política de conformidade do Intune irá utilizar o nível de ameaça para configurar qual o nível de ameaça máximo permitido.

Na página **Políticas de Conformidade** na **Consola de administrador do Intune**, aceda a **Estado de Funcionamento do Dispositivo** e ative a regra **Proteção Contra Ameaças de Dispositivos** através da opção de alternar. Em seguida selecione o nível de ameaça máximo permitido, que será um dos seguintes:
* **Nenhum (seguro)**: este é o nível mais seguro.  Isto significa que o dispositivo não pode ter nenhuma ameaça.  Se for encontrado qualquer nível de ameaças, o dispositivo é avaliado como não conforme.  
* **Baixo**: o dispositivo é avaliado como conforme se só estiverem presentes ameaças de nível baixo. Qualquer nível mais alto coloca o dispositivo num estado de não conforme.
* **Médio**: o dispositivo é avaliado como conforme se as ameaças encontradas forem de nível baixo ou médio. Se forem detetadas ameaças de nível alto, o dispositivo será determinado como não conforme.
* **Alto**: este é o nível menos seguro. Essencialmente, este nível permite todos os níveis de ameaças e possivelmente só será útil se estiver a utilizar esta solução apenas para a criação de relatórios.

![captura de ecrã que apresenta as definições da regra de proteção contra ameaças de dispositivos ](../media/mtp/mtp-compliance-policy-rule.png)

![captura de ecrã que apresenta a opção do nível de ameaça nas definições da regra de proteção contra ameaças de dispositivos](../media/mtp/mtp-compliance-policy-setting.png)

Se criar políticas de acesso condicional para o Office 365 ou outros serviços, a avaliação de compatibilidade é considerada e os dispositivos que não estiverem conformes serão bloqueados de aceder a recursos da empresa até que a ameaça esteja resolvida.

Poderá ver o estado de conformidade de um dispositivo na página **Todos os Dispositivos** da **Consola de administrador do Intune**.

![captura de ecrã da página do dispositivo na consola de administração do Intune que apresenta o estado de conformidade de um dispositivo](../media/mtp/mtp-device-status-intune-console.png)

## <a name="next-steps"></a>Passos seguintes
* Criar uma política de acesso condicional
  * [Exchange Online](restrict-access-to-exchange-online-with-microsoft-intune.md)
  * [Exchange no local](restrict-access-to-exchange-onpremises-with-microsoft-intune.md)
  * [SharePoint Online](restrict-access-to-sharepoint-online-with-microsoft-intune.md)
  * [Skype para Empresas Online](restrict-access-to-skype-for-business-online-with-microsoft-intune.md)
  * [Dynamics CRM](restrict-access-to-dynamics-crm-online-with-microsoft-intune.md)



<!--HONumber=Nov16_HO5-->


