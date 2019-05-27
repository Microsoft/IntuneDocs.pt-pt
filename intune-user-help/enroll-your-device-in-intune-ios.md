---
title: Configurar o acesso do dispositivo iOS aos recursos da empresa | Microsoft Docs
description: Descreve como fazer com que o dispositivo iOS seja gerido pelo Intune
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 05/24/2019
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
ms.openlocfilehash: bef0eb545f5f0ca0f85365a08e6bc5d726d6979e
ms.sourcegitcommit: d258bcf6716c8a2589d3f8dada819905ee80f233
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/24/2019
ms.locfileid: "66196862"
---
# <a name="set-up-ios-device-access-to-your-company-resources"></a>Configurar o acesso do dispositivo iOS aos recursos da empresa  

Inscreva o seu dispositivo iOS na aplicação Portal da Empresa do Intune para obter acesso seguro ao e-mail, ficheiros e aplicações da sua organização.

Depois do dispositivo está inscrito, torna-se *geridos*. Sua organização pode atribuir políticas e aplicações para o dispositivo através de um fornecedor de gestão (MDM) de dispositivos móveis, como o Intune.  

Para manter o acesso ao trabalho ou escola informações a partir do seu dispositivo, terá de configurar o seu dispositivo para corresponder as definições preferenciais da sua organização. Este artigo descreve como utilizar o Portal da empresa para inscrever-se a que dispositivos e manter os requisitos de definição de sua organização.  
</br>
> [!VIDEO https://www.youtube.com/embed/mJyv6YcHi7c?rel=0]

> [!NOTE]
> Se tentou aceder ao e-mail da empresa na aplicação Mail e recebeu uma mensagem para ter o dispositivo gerido, está no sítio certo. Siga as instruções abaixo para obter acesso ao seu e-mail e a outros recursos empresariais no seu dispositivo iOS.  

## <a name="what-to-expect-from-the-company-portal-app"></a>O que esperar da aplicação Portal da Empresa  

### <a name="security"></a>Segurança  
Durante a configuração inicial, a aplicação requer que se autentique na sua organização. Em seguida, informa-o de quaisquer definições do dispositivo que tenha de atualizar. Muitas vezes, por exemplo, as organizações definem requisitos de palavra-passe com limites de carateres mínimos e máximos que terá de cumprir.

### <a name="protection"></a>Protection  
Após a inscrição do seu dispositivo, a aplicação Portal da Empresa irá continuar a garantir que o mesmo se encontra protegido. Se, por exemplo, instalar uma aplicação de uma origem não fidedigna, a aplicação Portal da Empresa irá alertá-lo e, por vezes, revogar o acesso aos dados da empresa. Esse tipo de política é comum em organizações e, muitas vezes, tem de desinstalar a aplicação não fidedigna antes de pode recuperar o acesso.  

### <a name="setting-notifications"></a>Definir as notificações  
Se, após a inscrição, a sua organização aplicar um novo requisito de segurança, como a autenticação multifator, a aplicação Portal da Empresa irá notificá-lo. Terá a oportunidade de ajustar as suas definições para que possa continuar a trabalhar a partir do seu dispositivo.  

Para obter mais informações sobre a inscrição, veja [O que acontece quando instalo a aplicação Portal da Empresa e inscrevo o meu dispositivo?](https://docs.microsoft.com//intune-user-help/what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-ios)  

## <a name="enroll-your-ios-device"></a>Inscrever o dispositivo iOS  

Aceda à loja de aplicações para transferir e instalar o [aplicação Portal da empresa do Intune](install-and-sign-in-to-the-intune-company-portal-app-ios.md) no seu dispositivo. Também precisará de manter uma ligação Wi-Fi e ter acesso para o Safari durante a inscrição. 

Colocar em pausa durante mais de alguns minutos, durante a inscrição poderá fazer com que o aplicativo fechar ou terminar a configuração. Se isto acontecer, abra a aplicação Portal da empresa e tente novamente.  

1. Abra o Portal da empresa e inicie sessão com a sua conta escolar ou profissional. 

    ![Captura de ecrã do exemplo de aplicação do Portal da empresa, de início de sessão.](./media/ios-01-cp-enroll-1903.PNG)  

2. Quando lhe for pedido para receber notificações do Portal da empresa, toque em **permitir.** Portal da empresa utiliza notificações para alertá-lo se, por exemplo, definições do dispositivo tem de ser atualizado. 

    ![Captura de ecrã de exemplo da home page do Portal da empresa, a linha de "Notificações".](./media/ios-04-cp-enroll-1903.PNG)  

3. Sobre o **configurar o acesso** ecrã, selecione **começar.**  

     ![Captura de ecrã de exemplo do Portal da empresa, o ecrã de "Configurar o acesso".](./media/ios-05-cp-enroll-1903.PNG)  

4. Ler a lista de sua organização pode e não é possível ver as informações do dispositivo. Em seguida, toque **continuar**.  

5. Leia as instruções sobre a **o que se segue?** ecrã. Quando estiver pronto para transferir e instalar o perfil de gestão, toque em **continuar**.  

 > [!IMPORTANT]
> Estes passos e telas seguinte irão variar dependendo da versão do iOS. Siga os passos para a sua versão do iOS. 

6. Safari é aberto o site do Portal da empresa no seu dispositivo. Quando lhe for pedido para transferir o perfil de configuração, toque em **permitir**. Se estiver num dispositivo com:  
    * iOS 12.2 e posterior: Quando o download estiver concluído, toque em **feito.** Continue para o passo 7 neste artigo.
    * iOS 12.1 e versões anteriores: Será automaticamente redirecionado para a aplicação de definições. Avance para o passo 8 neste artigo.  
 
    Se tocar acidentalmente **ignorar**, atualize a página. Será solicitado para abrir a aplicação Portal da empresa. A partir da aplicação, pode tocar **transferir novamente**.

  > [!NOTE]
  > Tem de instalar o perfil de gestão, conforme descrito nos passos seguintes em menos de 8 minutos baixá-lo. Se não o fizer, o perfil será removido e terá de reiniciar a inscrição.  

7. iOS 12.2 e mais tarde apenas: Quando lhe for pedido para abrir o Portal da empresa, toque em **abra**. O **instalar o perfil de gestão** ecrã apresenta os passos para instalar o perfil.

    ![Captura de ecrã de exemplo do Portal da empresa, ecrã instalar perfil de gestão.](./media/ios-1904-settings-icon.PNG)  

8. Vá para a aplicação de definições e toque em **perfil transferido**.  

    Se **perfil transferido** não são apresentados como uma opção, aceda à **gerais** > **perfis**. Se não vir o perfil, terá de transferi-lo novamente.  

    ![Captura de ecrã de exemplo da aplicação de definições, perfil transferido definição.](./media/ios-1904-settings-badge.PNG)  

9. Toque em **Instalar**.  
    
10. Introduza a palavra-passe do dispositivo. Em seguida, toque **instalar**.    

    ![Captura de ecrã da aplicação de definições, o ecrã instalar perfil, com um cursor no exemplo a * * * * de instalação botão.](./media/ios-1904-password-install.PNG)  


11. A próxima tela é um aviso de sistema padrão para gestão de dispositivos. Para continuar com a instalação, toque em **instalar**. Se lhe for pedido para a gestão remota de confiança, toque em **confiança**.  

    ![Captura de ecrã do exemplo de aplicação de definições, o ecrã de aviso de sistema padrão para o certificado de raiz e gestão de dispositivos móveis.](./media/ios-15-cp-enroll-1903.PNG)  

12. Após a conclusão da instalação, toque em **feito**. Para verificar se o perfil foi instalado, vá para o **perfis e gestão de dispositivos** definições. Deverá ver o perfil listado na **gestão de dispositivos móveis**.   

    ![Captura de ecrã de exemplo da aplicação de definições, perfis e gestão de dispositivos definições, que mostra o perfil de gestão.](./media/ios-00-cp-enroll-1903.PNG)  

13. Regresse à aplicação Portal da empresa. Portal da empresa irá começar a sincronizar e configurar o dispositivo. Portal da empresa poderá pedir-lhe para atualizar as definições adicionais do dispositivo. Se, toque **continuar**.  

    ![Captura de ecrã de exemplo do Portal da empresa, o ecrã "Configurar o acesso ao", com um triângulo amarelo junto à definição requisito.](./media/ios-12-cp-enroll-1903.PNG)  

14. Saberá que a instalação está concluída quando todos os itens na lista de mostram um círculo verde. Toque em **Concluído**.   
    
    ![Captura de ecrã de exemplo do Portal da empresa, "está tudo pronto!" ecrã que mostra todos os círculos verde.](./media/ios-13-cp-enroll-1903.PNG)  

> [!Note]
> Se sua organização monitoriza os limites de voz e dados, ou fornece-lhe um dispositivo da empresa, pode ter mais algumas etapas para concluir. Se lhe for pedido para instalar o **Datalert** aplicação, veja [inscrever o seu dispositivo na gestão de despesas de telecomunicações](enroll-your-device-with-telecom-expense-management-ios.md). Se sua organização faz parte do programa de inscrição de dispositivos da Apple, Descubra [como inscrever o dispositivo pertencentes à empresa](enroll-your-device-dep-ios.md).  

## <a name="it-administrator-support"></a>Suporte de administrador de TI  
Se for um administrador de TI e executar em problemas ao inscrever dispositivos, veja [resolução de problemas de inscrição de dispositivos iOS no Microsoft Intune](https://support.microsoft.com/en-us/help/4039809). Este artigo lista erros comuns, suas causas e passos para resolvê-los.  

## <a name="next-steps"></a>Passos Seguintes  
Encontre aplicações que lhe ajudarão no trabalho ou escola. Saiba mais [como aplicações são disponibilizadas](use-managed-apps-on-your-device-ios.md) para si através do Portal da empresa.  

Ainda precisa de ajuda? Contacte o suporte da empresa. Pode encontrar as informações de contacto no [Site do Portal da Empresa](https://go.microsoft.com/fwlink/?linkid=2010980).  
