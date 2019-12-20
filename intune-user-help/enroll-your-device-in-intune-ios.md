---
title: Configurar o acesso do dispositivo iOS aos recursos da empresa | Microsoft Docs
description: Descreve como fazer com que o dispositivo iOS seja gerido pelo Intune
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 12/18/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: 6eeec7aa-1b07-4ce3-894c-13e09b89bdd4
searchScope:
- User help
ROBOTS: ''
ms.reviewer: tisilv
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: cbe0ca9991f427e11d72d85814bcd2d1b8882494
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/19/2019
ms.locfileid: "75205144"
---
# <a name="set-up-ios-device-access-to-your-company-resources"></a>Configurar o acesso do dispositivo iOS aos recursos da empresa  

Inscreva o seu dispositivo iOS na aplicação Portal da Empresa do Intune para obter acesso seguro ao e-mail, ficheiros e aplicações da sua organização.

Depois que o dispositivo for registrado, ele será *gerenciado*. Sua organização pode atribuir políticas e aplicativos ao dispositivo por meio de um provedor de MDM (gerenciamento de dispositivo móvel), como o Intune.  

> [!NOTE]
> Não vendemos nenhum dado coletado por nosso serviço para terceiros por qualquer motivo.  

Para manter o acesso a informações corporativas ou de estudante do seu dispositivo, você precisará configurar seu dispositivo para corresponder às configurações preferenciais da sua organização. Este artigo descreve como usar Portal da Empresa para registrar seu dispositivo e manter os requisitos de configuração da sua organização.  
</br>
> [!VIDEO https://www.youtube.com/embed/mJyv6YcHi7c?rel=0]

> [!NOTE]
> Se tentou aceder ao e-mail da empresa na aplicação Mail e recebeu uma mensagem para ter o dispositivo gerido, está no sítio certo. Siga as instruções abaixo para obter acesso ao seu e-mail e a outros recursos empresariais no seu dispositivo iOS.  


## <a name="what-to-expect-from-the-company-portal-app"></a>O que esperar da aplicação Portal da Empresa  

### <a name="security"></a>Segurança  
Durante a configuração inicial, a aplicação requer que se autentique na sua organização. Em seguida, informa-o de quaisquer definições do dispositivo que tenha de atualizar. Muitas vezes, por exemplo, as organizações definem requisitos de palavra-passe com limites de carateres mínimos e máximos que terá de cumprir.

### <a name="protection"></a>Protection  
Após a inscrição do seu dispositivo, a aplicação Portal da Empresa irá continuar a garantir que o mesmo se encontra protegido. Se, por exemplo, instalar uma aplicação de uma origem não fidedigna, a aplicação Portal da Empresa irá alertá-lo e, por vezes, revogar o acesso aos dados da empresa. Esse tipo de política é comum em organizações e geralmente exige que você desinstale o aplicativo não confiável antes de poder obter acesso.  

### <a name="setting-notifications"></a>Definir as notificações  
Se, após a inscrição, a sua organização aplicar um novo requisito de segurança, como a autenticação multifator, a aplicação Portal da Empresa irá notificá-lo. Terá a oportunidade de ajustar as suas definições para que possa continuar a trabalhar a partir do seu dispositivo.  

Para obter mais informações sobre a inscrição, veja [O que acontece quando instalo a aplicação Portal da Empresa e inscrevo o meu dispositivo?](https://docs.microsoft.com//intune-user-help/what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-ios)  

## <a name="enroll-your-ios-device"></a>Registrar seu dispositivo iOS  

Vá para a loja de aplicativos para baixar e instalar o [aplicativo portal da empresa do Intune](install-and-sign-in-to-the-intune-company-portal-app-ios.md) em seu dispositivo. Você também precisará manter uma conexão Wi-Fi e ter acesso ao Safari durante o registro. 

A pausa por mais de alguns minutos durante o registro pode fazer com que o aplicativo feche ou encerre a instalação. Se isso acontecer, abra o aplicativo Portal da Empresa e tente novamente.  

1. Abra Portal da Empresa e entre com sua conta corporativa ou de estudante.  

2. Quando solicitado a receber notificações de Portal da Empresa, toque em **permitir.** Portal da Empresa usa notificações para alertar se, por exemplo, as configurações do dispositivo precisarem ser atualizadas.  

3. Na tela **Configurar acesso** , selecione **Iniciar.**   

    ![Captura de tela de exemplo do Portal da Empresa "configurar acesso".](./media/ios-enrollment-checklist-1909.PNG)  

4. A tela **selecionar dispositivo e tipo de registro** é exibida e solicita o tipo de dispositivo.  
    * Toque **(organização) possui este dispositivo** se você recebeu seu dispositivo da sua organização. Em seguida, pule para [proteger o dispositivo inteiro](###secure-entire-device) neste artigo para concluir a instalação.  
    * Toque em **eu proprietário deste dispositivo** se você estiver usando um dispositivo pessoal que trouxe de casa. Em seguida, continue para a próxima etapa.  

    Se você não vir essa tela, pule para [proteger o dispositivo inteiro](enroll-your-device-in-intune-ios.md#secure-entire-device) para concluir a instalação.  
    
    ![Exemplo de captura de tela de Portal da Empresa "selecionar dispositivo e tipo de registro", opções de tipo de dispositivo.](./media/ios-device-type-1909.PNG)  


5. Escolha como proteger os dados em seu dispositivo depois que ele for registrado.  
    * Toque em **proteger todo o dispositivo** para proteger todos os aplicativos e dados no dispositivo. Em seguida, vá para [proteger o dispositivo inteiro](enroll-your-device-in-intune-ios.md#secure-entire-device) para concluir a instalação.
    * Toque em **proteger aplicativos e dados relacionados ao trabalho somente** para proteger somente os aplicativos e dados que você acessa com sua conta corporativa. Em seguida, vá para [proteger dados e aplicativos relacionados ao trabalho](enroll-your-device-in-intune-ios.md#secure-work-related-apps-and-data).  

    ![Exemplo de captura de tela de Portal da Empresa "selecionar dispositivo e tipo de registro", opções de tipo de registro.](./media/ios-enrollment-type-1909.PNG)  


### <a name="secure-entire-device"></a>Proteger o dispositivo inteiro  

1. Na tela **Gerenciamento e privacidade do dispositivo** , leia a lista de informações do dispositivo que sua organização pode e não consegue ver. Em seguida, toque em **continuar**.  


 > [!IMPORTANT]
> Essas próximas etapas e telas serão diferentes dependendo da versão do iOS. Siga as etapas para sua versão do iOS. 

2. O Safari abre o site Portal da Empresa em seu dispositivo. Quando for solicitado a baixar o perfil de configuração, toque em **permitir**. Se você estiver em um dispositivo que executa o:  
    * iOS 12,2 e posterior: quando o download estiver concluído, toque em **fechar**. Em seguida, continue na etapa 3.  
    * iOS 12,1 e anterior: quando o download for concluído, você será redirecionado automaticamente para o aplicativo de configurações. Pule para a etapa 4.  
 
    Se você tocar acidentalmente em **ignorar**, atualize a página. Você será solicitado a abrir o aplicativo Portal da Empresa. Quando estiver lá, toque em **baixar novamente**.

  > [!NOTE]
  > Você deve instalar o perfil de gerenciamento conforme descrito nas próximas etapas dentro de 8 minutos para baixá-lo. Se você não fizer isso, o perfil será removido e você precisará reiniciar o registro.  

3. Quando for solicitado a abrir Portal da Empresa, toque em **abrir**. Leia as informações na tela **como instalar o perfil de gerenciamento** .  

4. Vá para o aplicativo Configurações e toque **em registrar em < nome da organização >** ou **perfil baixado**.  

    ![Captura de tela de exemplo do aplicativo de configurações, opção registrar na organização.](./media/enroll-in-organization-ios-1909.PNG)  

   Se nenhuma das opções aparecer, vá para **geral** > **perfis & gerenciamento de dispositivo**> perfil de **Gerenciamento**. Se você ainda não vir um perfil de gerenciamento, talvez seja necessário baixá-lo novamente.  

5. Toque em **Instalar**.  
    
6. Insira a senha do dispositivo. Em seguida, toque em **instalar**.    

7. A próxima tela é um aviso padrão do sistema sobre o gerenciamento de dispositivos. Para continuar a instalação, toque em **instalar**. Se for solicitado a confiar no gerenciamento remoto, toque em **confiar**.  

8. Após a conclusão da instalação, toque em **concluído**. Para verificar se o perfil foi instalado, acesse os **perfis &** configurações de gerenciamento de dispositivo. Você deve ver o perfil listado em **Gerenciamento de dispositivo móvel**.   

    ![Captura de tela de exemplo do aplicativo de configurações, perfis & configurações de gerenciamento de dispositivo, mostrando o perfil de gerenciamento.](./media/ios-12-cp-enroll-1904.PNG)  

9. Retorne ao aplicativo Portal da Empresa. Portal da Empresa começará a sincronizar e a configurar seu dispositivo. Portal da Empresa pode solicitar que você atualize configurações de dispositivo adicionais. Se tiver, toque em **continuar**.  

10. Você saberá que a instalação está completa quando todos os itens na lista mostrarem uma marca de seleção verde. Toque em **Concluído**.   

> [!Note]
> Se sua organização monitora os limites de voz e de dados, ou fornece um dispositivo de propriedade da empresa, você pode ter algumas etapas a serem concluídas. Se você for solicitado a instalar o aplicativo **Datalert** , consulte [registrando seu dispositivo no gerenciamento de despesas de telecomunicações](enroll-your-device-with-telecom-expense-management-ios.md). Se sua organização fizer parte do Programa de registro de dispositivos da Apple, descubra [como registrar seu dispositivo de propriedade da empresa](enroll-your-device-dep-ios.md).  

### <a name="secure-work-related-apps-and-data"></a>Proteger aplicativos e dados relacionados ao trabalho  
1. A tela **baixar Microsoft Authenticator** é exibida (se você já tiver o autenticador, não verá essa tela, portanto, pule para a etapa 2).  
    1. Toque em **baixar na loja de aplicativos**.
    2. Quando a loja de aplicativos abrir, instale o aplicativo. 
    3. Volte para Portal da Empresa e toque em **continuar**.    
    
   Depois de instalar o Microsoft Authenticator, você não precisará fazer mais nada com o aplicativo. Ele só precisa estar presente em seu dispositivo. 

   ![Captura de tela de exemplo de Portal da Empresa, "baixar Microsoft Authenticator".](./media/download-ms-authenticator-1909.PNG)  

2. Na tela **Gerenciamento e privacidade do dispositivo** , leia a lista de informações do dispositivo que sua organização pode e não consegue ver. Em seguida, toque em **continuar**.  


 > [!IMPORTANT]
> Essas próximas etapas e telas serão diferentes dependendo da versão do iOS. Siga as etapas para sua versão do iOS. 

3. O Safari abre o site Portal da Empresa em seu dispositivo. Quando for solicitado a baixar o perfil de configuração, toque em **permitir**. Se você estiver em um dispositivo que executa o:  
    * iOS 12,2 e posterior: quando o download estiver concluído, toque em **fechar**. Em seguida, continue na etapa 4.  
    * iOS 12,1 e anterior: quando o download for concluído, você será redirecionado automaticamente para o aplicativo de configurações. Vá para a etapa 5.  
 
    Se você tocar acidentalmente em **ignorar**, atualize a página. Você será solicitado a abrir o aplicativo Portal da Empresa. No aplicativo, você pode tocar em **baixar novamente**.

  > [!NOTE]
  > Você deve instalar o perfil de gerenciamento conforme descrito nas próximas etapas dentro de 8 minutos para baixá-lo. Se você não fizer isso, o perfil será removido e você precisará reiniciar o registro.  

4. Quando for solicitado a abrir Portal da Empresa, toque em **abrir**. Leia as informações na tela **como instalar o perfil de gerenciamento** . 

5. Vá para o aplicativo Configurações e toque **em registrar em < nome da organização >** ou **perfil baixado**.  

    ![Captura de tela de exemplo do aplicativo de configurações, opção registrar na organização.](./media/enroll-in-organization-ios-1909.PNG)  

   Se nenhuma das opções aparecer, vá para **geral** > **perfis & gerenciamento de dispositivo**> perfil de **Gerenciamento**. Se você ainda não vir um perfil de gerenciamento, talvez seja necessário baixá-lo novamente.   


6. Na tela de **registro do usuário** , toque em **registrar meu iPhone**.  

    ![Captura de tela de exemplo do aplicativo de configurações, de registro de usuário, realçando o botão registrar.](./media/user-enrollment-information-1909.PNG)  

7. Insira a senha do dispositivo. Em seguida, toque em **instalar**.  

8. Na tela de **entrada** , insira a senha para sua ID da Apple gerenciada. Na maioria dos casos, essas credenciais serão as mesmas que você usa para entrar em sua conta corporativa ou de estudante, a menos que sua organização tenha fornecido um conjunto diferente de credenciais. 
9. Toque **em entrar**.  
10. Uma mensagem de êxito aparecerá brevemente na tela depois que o perfil for instalado. Para verificar se o perfil está instalado, acesse os **perfis & gerenciamento de dispositivo** configurações. Você deve ver o perfil listado em **Gerenciamento de dispositivo móvel.**  

    ![Captura de tela de exemplo do aplicativo de configurações, perfis & configurações de gerenciamento de dispositivo, mostrando o perfil de gerenciamento.](./media/ios-12-cp-enroll-1904.PNG)  

11. Retorne ao aplicativo Portal da Empresa. Portal da Empresa começará a sincronizar e a configurar seu dispositivo. Portal da Empresa pode solicitar que você atualize configurações de dispositivo adicionais. Se tiver, toque em **continuar**.    

12. Você saberá que a instalação está completa quando todos os itens na lista mostrarem uma marca de seleção verde. Toque em **concluído**.  

## <a name="it-administrator-support"></a>Suporte do administrador de ti  
Se você for um administrador de ti e estiver em problemas ao registrar dispositivos, consulte [Solucionando problemas de registro de dispositivo IOS no Microsoft Intune](https://support.microsoft.com/en-us/help/4039809). Este artigo lista os erros comuns, suas causas e as etapas para resolvê-los.  

## <a name="next-steps"></a>Próximos passos  
Encontre aplicativos que irão ajudá-lo no trabalho ou na escola. Saiba [como os aplicativos são disponibilizados](use-managed-apps-on-your-device-ios.md) para você por meio de portal da empresa.  

Ainda precisa de ajuda? Contacte o suporte da empresa. Pode encontrar as informações de contacto no [Site do Portal da Empresa](https://go.microsoft.com/fwlink/?linkid=2010980).  
