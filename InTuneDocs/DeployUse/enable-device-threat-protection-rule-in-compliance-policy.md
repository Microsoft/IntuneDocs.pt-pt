---
title: "Ativar a regra de proteção do dispositivo na política de conformidade | Microsoft Intune"
description: "Ative a regra de proteção contra ameaças móveis na política de conformidade do dispositivo."
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 09/13/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: c951692d-6538-46c0-a9f0-d607ded189ae
ms.reviewer: sandera
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9c2ffb5fe497d56d8250fe3dec7db606c2067a1c
ms.openlocfilehash: 761372b2c8b81699bc2584ab1ef8d0f9d523abe9


---

# Ativar a regra de proteção contra ameaças de dispositivo na política de conformidade
O Intune com o Lookout Mobile Threat Protection permite-lhe detetar ameaças e avaliar os riscos no dispositivo.  
A regra da política de conformidade permite-lhe utilizar esta avaliação de riscos para determinar se o dispositivo está em conformidade com a sua política. Pode utilizar a política de acesso condicional para permitir ou bloquear o Exchange, o SharePoint e outros serviços com base na conformidade do dispositivo.

Para que a deteção de ameaças do Lookout MTP influencie a política de conformidade do dispositivo:

1.  A regra de **Proteção Contra Ameaças de Dispositivos** tem de ser ativada na política de conformidade.

2.  A página **Estado do Lookout** na Consola de Administração do Intune deve apresentar a opção **Ativado**. Consulte [Enable Lookout MTP connection in Intune (Ativar a ligação do Lookout MTP ao Intune – em inglês)](enable-lookout-mtp-connection-in-intune.md) para obter mais detalhes e instruções sobre como ativar a integração do Lookout.


## Configurar a regra de proteção contra ameaças de dispositivos

Antes de criar uma regra de proteção contra ameaças de dispositivos na política de conformidade, recomendamos que [configure a sua subscrição com o Lookout MTP](set-up-your-subscription-with-lookout-mtp.md), [ative a ligação do Lookout no Intune](enable-lookout-mtp-connection-in-intune.md) e [configure a aplicação Lookout for Work](configure-and-deploy-lookout-for-work-apps.md). A regra de conformidade só é aplicada quando a configuração estiver concluída.

Para ativar a regra de proteção contra ameaças de dispositivos, pode utilizar uma política de conformidade existente ou pode criar uma política nova.

Como parte da configuração do Lookout MTP, na [consola do Lookout MTP](https://aad.lookout.com), criou uma política que categoriza as várias ameaças nos níveis alto, médio e baixo. Na política de conformidade do Intune irá utilizar o nível de ameaça para configurar qual o nível de ameaça máximo permitido.

Na Consola do administrador do Intune, na página da política de conformidade, aceda a **Estado de Funcionamento do Dispositivo** e ative a regra **Proteção Contra Ameaças de Dispositivos** através da opção de alternar. Em seguida selecione o nível de ameaça máximo permitido, que será um dos seguintes:
* **Nenhum (seguro)**: este é o nível mais seguro.  Isto significa que o dispositivo não pode ter nenhuma ameaça.  Se o dispositivo detetar qualquer nível de ameaças, será avaliado como não conforme.  
* **Baixo**: o dispositivo é avaliado como conforme se só estiverem presentes ameaças de nível baixo. Qualquer nível mais alto coloca o dispositivo num estado de não conforme.
* **Médio**: o dispositivo é avaliado como conforme se só estiverem presentes ameaças de nível baixo ou médio. Se forem detetadas ameaças de nível alto no dispositivo, será determinado como não conforme.
* **Alto**: este é o nível menos seguro. Essencialmente, este nível permite todos os níveis de ameaças e possivelmente só será útil se utilizar esta solução apenas para a criação de relatórios.

![captura de ecrã que apresenta as definições da regra de proteção contra ameaças de dispositivos ](../media/mtp/mtp-compliance-policy-rule.png)

![captura de ecrã que apresenta a opção do nível de ameaça nas definições da regra de proteção contra ameaças de dispositivos](../media/mtp/mtp-compliance-policy-setting.png)

Se criar políticas de acesso condicional para o O365 ou outros serviços, a avaliação de compatibilidade é considerada e os dispositivos que não estiverem conformes terão o acesso bloqueado até que a ameaça seja resolvida.

Poderá ver o estado de conformidade de um dispositivo na página Dispositivos da Consola do Administrador do Intune.

![captura de ecrã da página do dispositivo na consola de administração do Intune que apresenta o estado de conformidade de um dispositivo](../media/mtp/mtp-device-status-intune-console.png)

## Passos seguintes
* Criar uma política de acesso condicional
  * [Exchange Online](restrict-access-to-exchange-online-with-microsoft-intune.md)
  * [Exchange no local](restrict-access-to-exchange-onpremises-with-microsoft-intune.md)
  * [SharePoint Online](restrict-access-to-sharepoint-online-with-microsoft-intune.md)
  * [Skype para Empresas Online](restrict-access-to-skype-for-business-online-with-microsoft-intune,md)
  * [Dynamics CRM](restrict-access-to-dynamics-crm-online-with-microsoft-intune.md)



<!--HONumber=Sep16_HO2-->

