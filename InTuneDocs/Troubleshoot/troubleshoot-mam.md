---
title:
- "Resolução de problemas de gestão de aplicações móveis | Microsoft Intune"
description: 
keywords: 
author: karaman
manager: angerobe
ms.date: 09/12/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: cd5a0a3b-0013-4be3-a233-ce6e9083149f
translationtype: Human Translation
ms.sourcegitcommit: 9cfb3694b2fae919fd0554a6e21b497cdcf19c72
ms.openlocfilehash: f33e8de82ee07bb4571a5bfaff63af72f9086376


---

# Resolução de problemas de gestão de aplicações móveis

Se tiver problemas com a gestão de aplicações móveis, pode começar aqui. Este tópico contém alguns problemas comuns que poderá encontrar juntamente com as soluções.


**Problema:** a MAM sem Política de inscrição a partir da consola do Azure não se está a aplicar à aplicação Skype para Empresas em dispositivos iOS e Android.

Resolução: o Skype para Empresas tem de ser configurado para autenticação moderna.  Siga as instruções em [Enable your tenant for modern authentication (Ativar o seu inquilino para autenticação moderna – em inglês)](http://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx) para configurar a autenticação moderna para o Skype.

**Problema:** a MAM sem Políticas de inscrição não se está a aplicar a qualquer aplicação do Office suportada [https://www.microsoft.com/en-us/cloud-platform/microsoft-intune-partners] para qualquer utilizador.
 
Resolução: confirme que o utilizador está licenciado para o Intune.  

**Problema:** o utilizador de administração de TI não consegue configurar políticas de MAM no Portal do Azure

Resolução: as funções seguintes têm acesso ao Portal do Azure:

- Administrador global, que pode configurar no [Portal do Office](http://portal.office.com/)
- Proprietário, que pode configurar no [Portal do Azure](https://portal.azure.com/).
- Contribuinte, que pode configurar no [Portal do Azure](https://portal.azure.com/).

Consulte [Configurar políticas de gestão de aplicações móveis com o Microsoft Intune](https://docs.microsoft.com/en-us/intune/deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune) para obter ajuda para configurar estas funções. 

**Problema:** o relatório da aplicação não mostra os utilizadores para os quais direcionámos recentemente a política de MAM.

Resolução: se uma política de MAM for direcionada recentemente para um utilizador, pode demorar até 24 horas para esse utilizador ser apresentado em relatórios como um utilizador de destino. 

**Problema:** as alterações/atualizações de políticas podem demorar até 8 horas para serem aplicadas.  

Resolução: o utilizador final pode terminar sessão na aplicação e voltar a iniciar sessão para forçar a sincronização com o serviço.  

**Problema:** a política de MAM não se está a aplicar a dispositivos DEP da Apple

Resolução: certifique-se de que está a utilizar a Afinidade de Utilizador com o Programa de Inscrição de Dispositivos Apple (DEP). A Afinidade de Utilizador é necessária para qualquer aplicação que exija autenticação do utilizador no DEP.
Consulte [Inscrever dispositivos iOS pertencentes à empresa através do Programa de Inscrição de Dispositivos](https://docs.microsoft.com/en-us/intune/deploy-use/ios-device-enrollment-program-in-microsoft-intune) para obter mais informações sobre a inscrição do DEP para iOS.


### Consulte também
- [Validar a configuração de gestão de aplicações móveis](https://docs.microsoft.com/en-us/intune/deploy-use/validate-mobile-application-management)
- [Configurar políticas de gestão de aplicações móveis com o Microsoft Intune](https://docs.microsoft.com/en-us/intune/deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune) 





<!--HONumber=Sep16_HO2-->


