---
title: Configurar a integração do Sophos Mobile com o Intune
titleSuffix: Intune on Azure
description: Como configurar a solução de Sophos Mobile com o Microsoft Intune para controlar o acesso de dispositivos móveis aos seus recursos empresariais.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 04/30/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: ec60a618280caf6a5b7ef242c192cc64b5d839de
ms.sourcegitcommit: 84c79ceea27f7411528defc5ee8ba35ae2bf473c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/02/2019
ms.locfileid: "67511902"
---
# <a name="integrate-sophos-mobile-with-intune"></a>Integrar o Sophos Mobile com o Intune  

Conclua os seguintes passos para integrar a solução de Sophos Mobile Threat Defense com o Intune.  

## <a name="before-you-begin"></a>Antes de começar  

Antes de iniciar o processo de integração Sophos Mobile com o Intune, certifique-se de que tem o seguinte:  
- Subscrição do Microsoft Intune  
- Credenciais de administrador do Azure Active Directory para conceder as seguintes permissões:  
  - Iniciar sessão e ler o perfil de utilizador  
  - Aceder ao diretório como o utilizador com sessão iniciada  
  - Ler dados do diretório  
  - Enviar informações do dispositivo para o Intune  
- Credenciais de administrador para aceder à consola de administração do Sophos Mobile.  


### <a name="sophos-mobile-app-authorization"></a>Autorização da aplicação móvel da Sophos  
  
O processo de autorização de aplicações móveis do Sophos segue:  
- Permitir que o serviço Sophos Mobile comunique informações relacionadas com o estado de funcionamento do dispositivo ao Intune.  
- Sophos Mobile sincroniza com a associação de grupo de inscrição do Azure AD para povoar a base de dados do seu dispositivo.  
- Permitir que o Sophos Mobile consola de administração para utilizar o início de sessão do Azure AD único (SSO).  
- Permitir que a aplicação de Sophos Mobile iniciar sessão com o SSO do Azure AD.  


## <a name="to-set-up-sophos-mobile-integration"></a>Para configurar a integração do Mobile da Sophos  

1. Inicie sessão para o [portal do Azure]( https://portal.azure.com/), aceda **Intune** > **conformidade de dispositivos** > **Mobile Threat Defense** > e selecione **adicionar**.  
2. Sobre o **adicionar conector** página, utilize a lista pendente e selecione **Sophos**. E, em seguida, selecione **criar**.  
3. Selecione a ligação *abra a consola de administração do Sophos*.  
4. Inicie sessão para o [consola de administração do Sophos](https://central.sophos.com/) com as suas credenciais do Sophos.  
5. Aceda a **Mobile** > **definições** > **configuração** > **Sophos configuração**.  
6. Sobre o **configuração Sophos** página, selecione a **MTD do Intune** separador.  
   ![Configuração da Sophos](./media/sophos-mtd-connector-integration/sophos-setup.png) 
 
7. Selecione **vincular**e, em seguida, selecione **Sim**. Sophos liga-se ao Intune e requer que inicie sessão sua subscrição do Intune. 
8. Na janela de autenticação do Microsoft Intune, introduza as suas credenciais do Intune e **Accept** as permissões do pedido para *Sophos Mobile Thread Defense*.  
   ![Autenticação do Intune](./media/sophos-mtd-connector-integration/intune-authentication.png)

9. Sobre o **configuração Sophos** página, selecione **guardar** para concluir a configuração do Intune:  
   ![Guardar a configuração da Sophos](./media/sophos-mtd-connector-integration/save-sophos-configuration.png)  

1. Quando a mensagem **Integração Bem-sucedida** for apresentada, significa que a integração foi concluída.  
1. Na consola do Intune, Sophos agora está disponível.  


## <a name="next-steps"></a>Próximos Passos  
[Configurar aplicações de cliente da Sophos](mtd-apps-ios-app-configuration-policy-add-assign.md)
