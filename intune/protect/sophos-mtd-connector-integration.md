---
title: Configurar a integração do Sophos Mobile com o Intune
titleSuffix: Intune on Azure
description: Como configurar a solução do Sophos Mobile com o Microsoft Intune para controlar o acesso de dispositivos móveis aos seus recursos corporativos.
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
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71731884"
---
# <a name="integrate-sophos-mobile-with-intune"></a>Integre o Sophos Mobile ao Intune  

Conclua as etapas a seguir para integrar a solução de defesa contra ameaças móveis do Sophos com o Intune.  

## <a name="before-you-begin"></a>Antes de começar  

Antes de iniciar o processo de integração do Sophos Mobile com o Intune, verifique se você tem o seguinte:  
- Subscrição do Microsoft Intune  
- Credenciais de administrador do Azure Active Directory para conceder as seguintes permissões:  
  - Iniciar sessão e ler o perfil de utilizador  
  - Aceder ao diretório como o utilizador com sessão iniciada  
  - Ler dados do diretório  
  - Enviar informações do dispositivo para o Intune  
- Credenciais de administrador para acessar o Sophos Mobile admin console.  


### <a name="sophos-mobile-app-authorization"></a>Autorização do aplicativo móvel do Sophos  
  
O processo de autorização do aplicativo móvel do Sophos segue:  
- Permitir que o serviço de serviços móveis do Sophos comunique informações relacionadas ao estado de integridade do dispositivo de volta para o Intune.  
- O Sophos Mobile sincroniza com a associação do grupo de registros do Azure AD para preencher o banco de dados do dispositivo.  
- Permita que o console de administração do Sophos Mobile use o SSO (logon único) do Azure AD.  
- Permitir que o aplicativo móvel do Sophos entre usando o SSO do Azure AD.  


## <a name="to-set-up-sophos-mobile-integration"></a>Para configurar a integração do Sophos Mobile  

1. Entre no [portal do Azure]( https://portal.azure.com/), acesse **Intune** > **conformidade do dispositivo** > **defesa contra ameaças móveis** > e selecione **Adicionar**.  
2. Na página **Adicionar conector** , use a lista suspensa e selecione **Sophos**. E, em seguida, selecione **criar**.  
3. Selecione o link *abrir o console de administração do Sophos*.  
4. Entre no console de [Administração do Sophos](https://central.sophos.com/) com suas credenciais do Sophos.  
5. Acesse**as configurações**do @no__t **móvel**-1  > **instalação** > **configuração do Sophos**.  
6. Na página **configuração do Sophos** , selecione a guia **MTD do Intune** .  
   instalação do ![Sophos @ no__t-1 
 
7. Selecione **associar**e, em seguida, selecione **Sim**. O Sophos se conecta ao Intune e exige que você entre em sua assinatura do Intune. 
8. Na janela de autenticação Microsoft Intune, insira suas credenciais do Intune e **aceite** a solicitação de permissões para a *defesa de threads móveis do Sophos*.  
   autenticação ![Intune @ no__t-1

9. Na página **configuração do Sophos** , selecione **salvar** para concluir a configuração do Intune:  
   instalação do @no__t 0Save Sophos @ no__t-1  

1. Quando a mensagem **Integração Bem-sucedida** for apresentada, significa que a integração foi concluída.  
1. No console do Intune, o Sophos agora está disponível.  


## <a name="next-steps"></a>Próximos Passos  
[Configurar aplicativos cliente do Sophos](mtd-apps-ios-app-configuration-policy-add-assign.md)
