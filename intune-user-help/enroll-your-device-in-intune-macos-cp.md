---
title: Registrar seu Mac com o Portal da Empresa do Intune | Microsoft Docs
description: Saiba como registrar seu Mac no Intune com o aplicativo Portal da Empresa.
keywords: Mac OS X, macOS, OS X
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 12/16/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: 3bb659cc-9b57-4d19-8631-2c26749fa71c
searchScope:
- User help
ROBOTS: ''
ms.reviewer: kakyker
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: f26594435689a4f7a178035264e006a497719d3e
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/19/2019
ms.locfileid: "75205506"
---
# <a name="enroll-your-macos-device-using-the-company-portal-app"></a>Registrar seu dispositivo macOS usando o aplicativo Portal da Empresa  

Registre seu dispositivo macOS com o aplicativo Portal da Empresa do Intune para obter acesso seguro ao seu email corporativo ou de estudante, arquivos e aplicativos.

Normalmente, as organizações exigem que você registre seu dispositivo antes de poder acessar dados proprietários. Depois que o dispositivo for registrado, ele será *gerenciado*. Sua organização pode atribuir políticas e aplicativos ao dispositivo por meio de um provedor de MDM (gerenciamento de dispositivo móvel), como o Intune. Para obter acesso contínuo a informações corporativas ou de estudante em seu dispositivo, você deve configurar seu dispositivo para corresponder às configurações de política da sua organização.  

Este artigo descreve como usar o aplicativo Portal da Empresa para macOS para registrar, configurar e manter seu dispositivo para que você atenda aos requisitos da sua organização.  


## <a name="what-to-expect-from-the-company-portal-app"></a>O que esperar da aplicação Portal da Empresa

Durante a configuração inicial, o aplicativo Portal da Empresa exige que você entre e se autentique com sua organização. Portal da Empresa, em seguida, o informará sobre as configurações de dispositivo que você precisa configurar para atender aos requisitos da sua organização. Muitas vezes, por exemplo, as organizações definem requisitos de palavra-passe com limites de carateres mínimos e máximos que terá de cumprir.    

Depois de registrar seu dispositivo, Portal da Empresa sempre verificará se o dispositivo está protegido de acordo com os requisitos da sua organização. Por exemplo, se você instalar um aplicativo de uma fonte não confiável, Portal da Empresa irá alertá-lo e poderá restringir o acesso aos recursos da sua organização. As políticas de proteção de aplicativo como essa são comuns. Para restabelecer o acesso, você provavelmente precisará desinstalar o aplicativo não confiável. 

Se, após o registro, sua organização impõe um novo requisito de segurança, como a autenticação multifator, Portal da Empresa notificará você. Terá a oportunidade de ajustar as suas definições para que possa continuar a trabalhar a partir do seu dispositivo.  

Para obter mais informações sobre a inscrição, veja [O que acontece quando instalo a aplicação Portal da Empresa e inscrevo o meu dispositivo?](what-happens-if-you-install-the-Company-Portal-app-and-enroll-your-device-in-intune-macos.md)  

## <a name="get-your-macos-device-managed"></a>Faça com que seu dispositivo macOS seja gerenciado  
Use as etapas a seguir para registrar seu dispositivo macOS com sua organização. Seu dispositivo deve estar executando o macOS 10,12 ou posterior.   

> [!NOTE]
> Durante esse processo, você pode ser solicitado a permitir que Portal da Empresa use informações confidenciais armazenadas em seu conjunto de chaves. Esses prompts fazem parte da segurança da Apple. Quando receber o prompt, digite sua senha de conjunto de chaves de logon e selecione **sempre permitir**. Se você pressionar **Enter** ou **retornar** no teclado, o prompt selecionará **permitir**, o que pode resultar em prompts adicionais.  

### <a name="install-company-portal-app"></a>Instalar Portal da Empresa aplicativo  
1. Vá para [registrar meu Mac](https://go.microsoft.com/fwlink/?linkid=853070).  
2. O arquivo Portal da Empresa Installer. pkg será baixado. Abra o instalador e continue as etapas. 
3. Concorde com o contrato de licença de software. 
4. Insira a senha do dispositivo ou a impressão digital registrada para instalar o software.  
5. Abra Portal da Empresa. 

> [!IMPORTANT]
> O Microsoft AutoUpdate pode abrir para atualizar seu software da Microsoft. Depois que todas as atualizações forem instaladas, abra o aplicativo Portal da Empresa. Para obter a melhor experiência de configuração, instale as versões mais recentes do Microsoft AutoUpdate e Portal da Empresa.  


### <a name="enroll-your-mac"></a>Registrar seu Mac  


1. Entre no Portal da Empresa com sua conta corporativa ou de estudante.  
2. Quando o aplicativo for aberto, selecione **Iniciar**.  
3. Examine o que sua organização pode ou não ver em seu dispositivo registrado. Em seguida, selecione **Continue** (Continuar).
4.  Se solicitado, insira a senha do dispositivo na tela **instalar perfil de gerenciamento** .

    ![Exemplo de captura de tela de Portal da Empresa, instalar o perfil de gerenciamento, realçando o prompt de senha.](./media/install-management-profile-macos-1912.PNG)   
5. Na tela **confirmar gerenciamento de dispositivo** , selecione **Abrir preferências do sistema**.  

    ![Captura de tela de exemplo de confirmação do gerenciamento de dispositivo, realçando o botão "Abrir preferências do sistema".](./media/confirm-device-management-macos-1912.PNG)  
6. As preferências do sistema do seu dispositivo serão abertas. Selecione **perfil de gerenciamento** na lista perfis de dispositivo e, em seguida, selecione **aprovar** > **aprovar**.  
    ![captura de tela de exemplo das preferências do sistema, do perfil de gerenciamento, realçando o botão "aprovar".](./media/management-profile-approve-macos-1912.PNG)   
1. Retorne para Portal da Empresa e selecione **continuar**.    
2. Sua organização pode exigir que você atualize as configurações do dispositivo. Quando você terminar de atualizar as configurações, selecione **verificar configurações**.  

    ![Exemplo de captura de tela de Portal da Empresa, atualizar configurações do dispositivo, realçando o botão "verificar configurações".](./media/update-settings-mac-1911.PNG)  
9. Quando a instalação estiver concluída, selecione **concluído**.  


 ## <a name="troubleshooting-and-feedback"></a>Solução de problemas e comentários   

Se você encontrar problemas durante o registro, acesse **ajuda** > **Enviar relatório de diagnóstico** para relatar o problema aos desenvolvedores de aplicativos da Microsoft. Essas informações são usadas para ajudar a melhorar o aplicativo. Eles também usarão essas informações para ajudar a resolver o problema se o seu pessoal de suporte de ti chegar a ele para obter ajuda.  

Depois de relatar o problema à Microsoft, você pode enviar os detalhes de sua experiência para sua pessoa de suporte de ti. Selecione **detalhes do email**. Digite o que você experimentou no corpo do email. Para localizar o endereço de email da pessoa de suporte, acesse o aplicativo Portal da Empresa > **contato**. Ou verifique o [site Portal da empresa](https://go.microsoft.com/fwlink/?linkid=2010980).  
 

Além disso, o Microsoft Intune Portal da Empresa equipe adoraria ouvir seus comentários. Acesse **ajuda** > **enviar comentários** para compartilhar seus pensamentos e ideias.  

## <a name="unverified-profiles"></a>Perfis não verificados  
Quando você exibe os perfis de MDM (gerenciamento de dispositivo móvel) instalados em **preferências do sistema** > **perfis**, alguns perfis podem mostrar um status não verificado. Desde que o perfil de gerenciamento mostre um status verificado, você não precisa se preocupar.  

O perfil de gestão é o que define a ligação de canal MDM. Desde que o perfil de gerenciamento seja verificado, todos os outros perfis entregues ao computador por meio desse canal herdarão as características de segurança do perfil de gerenciamento.  

## <a name="updating-the-company-portal-app"></a>Atualizar a aplicação Portal da Empresa

A atualização do aplicativo Portal da Empresa é feita da mesma maneira que qualquer outro aplicativo do Office, por meio do Microsoft AutoUpdate para macOS. Saiba mais sobre a [atualização de aplicativos da Microsoft para MacOS](https://support.office.com/article/Check-for-Office-for-Mac-updates-automatically-bfd1e497-c24d-4754-92ab-910a4074d7c1).  

## <a name="next-steps"></a>Passos Seguintes  
Ainda precisa de ajuda? Contacte o suporte da empresa. Para encontrar as informações de contacto dele, verifique o [site do Portal da Empresa](https://go.microsoft.com/fwlink/?linkid=2010980).  


