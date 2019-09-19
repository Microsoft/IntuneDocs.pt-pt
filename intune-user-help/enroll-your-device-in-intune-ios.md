---
title: Configurar o acesso do dispositivo iOS aos recursos da empresa | Microsoft Docs
description: Descreve como fazer com que o dispositivo iOS seja gerido pelo Intune
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 09/12/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 6eeec7aa-1b07-4ce3-894c-13e09b89bdd4
searchScope:
- User help
ROBOTS: ''
ms.reviewer: tisilv
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: f207f1f94d34e6aa1768bb5ae0f5179710839c71
ms.sourcegitcommit: 8934b1abec96e18cee15a77107d37551766f7666
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/18/2019
ms.locfileid: "71099859"
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

    ![Captura de tela de exemplo do aplicativo Portal da Empresa, entrar.](./media/ios-01-cp-enroll-1904.PNG)  

2. Quando solicitado a receber notificações de Portal da Empresa, toque em **permitir.** Portal da Empresa usa notificações para alertar se, por exemplo, as configurações do dispositivo precisarem ser atualizadas. 

    ![Captura de tela de exemplo de Portal da Empresa home page, prompt "notificações".](./media/ios-02-cp-enroll-1904.PNG)  

3. Na tela **Configurar acesso** , selecione **Iniciar.**  

     ![Captura de tela de exemplo do Portal da Empresa "configurar acesso".](./media/ios-03-cp-enroll-1904.PNG)  

4. Leia a lista de informações de dispositivo que sua organização pode e não consegue ver. Em seguida, toque em **continuar**.  

5. Leia as instruções na tela **o que vem a seguir** . Quando estiver pronto para baixar e instalar o perfil de gerenciamento, toque em **continuar**.  

 > [!IMPORTANT]
> Essas próximas etapas e telas serão diferentes dependendo da versão do iOS. Siga as etapas para sua versão do iOS. 

6. O Safari abre o site Portal da Empresa em seu dispositivo. Quando for solicitado a baixar o perfil de configuração, toque em **permitir**. Se você estiver em um dispositivo que executa o:  
    * iOS 12,2 e posterior: Quando o download for concluído, toque em **concluído.** Continue na etapa 7 neste artigo.
    * iOS 12,1 e anterior: Você será redirecionado automaticamente para o aplicativo de configurações. Pule para a etapa 8 neste artigo.  
 
    Se você tocar acidentalmente em **ignorar**, atualize a página. Você será solicitado a abrir o aplicativo Portal da Empresa. No aplicativo, você pode tocar em **baixar novamente**.

  > [!NOTE]
  > Você deve instalar o perfil de gerenciamento conforme descrito nas próximas etapas dentro de 8 minutos para baixá-lo. Se você não fizer isso, o perfil será removido e você precisará reiniciar o registro.  

7. iOS 12,2 e posterior somente: Quando for solicitado a abrir Portal da Empresa, toque em **abrir**. A tela **instalando o perfil de gerenciamento** lista as etapas para instalar o perfil.

    ![Captura de tela de exemplo de Portal da Empresa, instalação do perfil de gerenciamento.](./media/ios-07-cp-enroll-1904.PNG)  

8. Vá para o aplicativo Configurações e toque em **perfil baixado**.  

    Se o **perfil baixado** não aparecer como uma opção, vá para**perfis** **gerais** > . Se você ainda não vir o perfil, talvez seja necessário baixá-lo novamente.  

    ![Captura de tela de exemplo do aplicativo de configurações, configuração de perfil baixado.](./media/ios-1904-settings-badge.PNG)  

9. Toque em **Instalar**.  
    
10. Insira a senha do dispositivo. Em seguida, toque em **instalar**.    

    ![Captura de tela de exemplo do aplicativo configurações, instalação de perfil, com um cursor no botão * * instalar * *.](./media/ios-10-cp-enroll-1904.PNG)  


11. A próxima tela é um aviso padrão do sistema para o gerenciamento de dispositivos. Para continuar a instalação, toque em **instalar**. Se for solicitado a confiar no gerenciamento remoto, toque em **confiar**.  

    ![Captura de tela de exemplo do aplicativo de configurações, telas de aviso do sistema padrão para certificado raiz e gerenciamento de dispositivo móvel.](./media/ios-11-cp-enroll-1904.PNG)  

12. Após a conclusão da instalação, toque em **concluído**. Para verificar se o perfil foi instalado, acesse os **perfis &** configurações de gerenciamento de dispositivo. Você deve ver o perfil listado em **Gerenciamento de dispositivo móvel**.   

    ![Captura de tela de exemplo do aplicativo de configurações, perfis & configurações de gerenciamento de dispositivo, mostrando o perfil de gerenciamento.](./media/ios-12-cp-enroll-1904.PNG)  

13. Retorne ao aplicativo Portal da Empresa. Portal da Empresa começará a sincronizar e a configurar seu dispositivo. Portal da Empresa pode solicitar que você atualize configurações de dispositivo adicionais. Se tiver, toque em **continuar**.  

    ![Captura de tela de exemplo do Portal da Empresa "configurar acesso", com triângulo amarelo ao lado de definir requisito.](./media/ios-13-cp-enroll-1904.PNG)  

14. Você saberá que a instalação está completa quando todos os itens na lista mostrarem um círculo verde. Toque em **Concluído**.   
    
    ![Captura de tela de exemplo de Portal da Empresa, "você está pronto!" tela, mostrando todos os círculos verdes.](./media/ios-14-cp-enroll-1904.PNG)  

> [!Note]
> Se sua organização monitora os limites de voz e de dados, ou fornece um dispositivo de propriedade da empresa, você pode ter algumas etapas a serem concluídas. Se você for solicitado a instalar o aplicativo **Datalert** , consulte [registrando seu dispositivo no gerenciamento de despesas de telecomunicações](enroll-your-device-with-telecom-expense-management-ios.md). Se sua organização fizer parte do Programa de registro de dispositivos da Apple, descubra [como registrar seu dispositivo de propriedade da empresa](enroll-your-device-dep-ios.md).  

## <a name="it-administrator-support"></a>Suporte do administrador de ti  
Se você for um administrador de ti e estiver em problemas ao registrar dispositivos, consulte [Solucionando problemas de registro de dispositivo IOS no Microsoft Intune](https://support.microsoft.com/en-us/help/4039809). Este artigo lista os erros comuns, suas causas e as etapas para resolvê-los.  

## <a name="next-steps"></a>Passos Seguintes  
Encontre aplicativos que irão ajudá-lo no trabalho ou na escola. Saiba [como os aplicativos são disponibilizados](use-managed-apps-on-your-device-ios.md) para você por meio de portal da empresa.  

Ainda precisa de ajuda? Contacte o suporte da empresa. Pode encontrar as informações de contacto no [Site do Portal da Empresa](https://go.microsoft.com/fwlink/?linkid=2010980).  
