---
title: Configurar o acesso do dispositivo iOS aos recursos da empresa | Microsoft Docs
description: Descreve como fazer com que o dispositivo iOS seja gerido pelo Intune
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 03/26/2019
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
ms.openlocfilehash: ee0f438d929abd6b5b90acbaeeddc41e3ce11f98
ms.sourcegitcommit: 44095bbd1502b02201a01604531f4105401fbb92
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/27/2019
ms.locfileid: "58490647"
---
# <a name="set-up-ios-device-access-to-your-company-resources"></a>Configurar o acesso do dispositivo iOS aos recursos da empresa  

Inscreva o seu dispositivo iOS na aplicação Portal da Empresa do Intune para obter acesso seguro ao e-mail, ficheiros e aplicações da sua organização.

Antes de poder aceder a dados proprietários de um dispositivo pessoal ou empresarial, tem de obter o dispositivo seja gerido. Depois do dispositivo fica gerido, sua organização vai atribuir políticas e aplicações para o dispositivo através de um fornecedor de gestão (MDM) de dispositivos móveis, como o Intune. 

Para manter o acesso às informações do trabalho ou da escola a partir do seu dispositivo, tem de o configurar para corresponder às definições preferenciais da sua organização. Este artigo descreve como utilizar o Portal da empresa para inscrever-se a que dispositivos e manter os requisitos de definição de sua organização. 

> [!NOTE]
> Se tentou aceder ao e-mail da empresa na aplicação Mail e recebeu uma mensagem para ter o dispositivo gerido, está no sítio certo. Siga as instruções abaixo para obter acesso ao seu e-mail e a outros recursos empresariais no seu dispositivo iOS.  

## <a name="what-to-expect-from-the-company-portal-app"></a>O que esperar da aplicação Portal da Empresa  

### <a name="security"></a>Segurança  
Durante a configuração inicial, a aplicação requer que se autentique na sua organização. Em seguida, informa-o de quaisquer definições do dispositivo que tenha de atualizar. Muitas vezes, por exemplo, as organizações definem requisitos de palavra-passe com limites de carateres mínimos e máximos que terá de cumprir.     

### <a name="protection"></a>Protection  
Após a inscrição do seu dispositivo, a aplicação Portal da Empresa irá continuar a garantir que o mesmo se encontra protegido. Se, por exemplo, instalar uma aplicação de uma origem não fidedigna, a aplicação Portal da Empresa irá alertá-lo e, por vezes, revogar o acesso aos dados da empresa. Uma política como esta é comum em organizações e, muitas vezes, tem de desinstalar a aplicação não fidedigna antes de pode recuperar o acesso.  

### <a name="setting-notifications"></a>Definir as notificações  
Se, após a inscrição, a sua organização aplicar um novo requisito de segurança, como a autenticação multifator, a aplicação Portal da Empresa irá notificá-lo. Terá a oportunidade de ajustar as suas definições para que possa continuar a trabalhar a partir do seu dispositivo.  

Para obter mais informações sobre a inscrição, veja [O que acontece quando instalo a aplicação Portal da Empresa e inscrevo o meu dispositivo?](https://docs.microsoft.com//intune-user-help/what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-ios)  

## <a name="enroll-your-ios-device"></a>Inscrever o dispositivo iOS   

> [!IMPORTANT]
> As capturas de ecrã nesta secção mostram a experiência para dispositivos com o iOS versão 12.1 e versões anteriores. Quando aplicável, incluímos instruções específicas para a versão do iOS 12.2 e posteriores. Se notar que a sua experiência é diferente da capturas de tela exibidas, consulte as 12.2 instruções.      

Aceda à loja de aplicações para transferir e instalar o [aplicação Portal da empresa do Intune](install-and-sign-in-to-the-intune-company-portal-app-ios.md) para o seu dispositivo. Durante a inscrição, terá também uma ligação Wi-Fi e acesso para o Safari. 

Se colocar em pausa durante mais de alguns minutos, durante a inscrição, a aplicação poderá fechar ou terminar a configuração. Se isto acontecer, abra a aplicação Portal da empresa e tente novamente.  

1. Abra o Portal da empresa e inicie sessão com a sua conta escolar ou profissional. 

    ![Captura de ecrã do exemplo de aplicação do Portal da empresa, de início de sessão.](./media/ios-01-cp-enroll-1903.PNG)  

2. Quando lhe for pedido para receber notificações do Portal da empresa, toque em **permitir.** Portal da empresa utiliza notificações para alertá-lo se, por exemplo, definições do dispositivo tem de ser atualizado. 

    ![Captura de ecrã de exemplo da home page do Portal da empresa, a linha de "Notificações".](./media/ios-04-cp-enroll-1903.PNG)  

3. Sobre o **configurar o acesso** ecrã, selecione **começar.**  

     ![Captura de ecrã de exemplo do Portal da empresa, o ecrã de "Configurar o acesso".](./media/ios-05-cp-enroll-1903.PNG)  

4. Ler a lista de sua organização pode e não é possível ver as informações do dispositivo. [Detalhes adicionais sobre este tópico](what-info-can-your-company-see-when-you-enroll-your-device-in-Intune.md) podem ser encontrados através do **Saiba mais** ligação. Quando tiver terminado, toque em **continuar**.  

    ![Captura de ecrã do exemplo de aplicação do Portal da empresa, "O que pode a minha organização ver", com o botão continuar.](./media/ios-06-cp-enroll-1903.PNG)  
 
5. O **o que se segue?** ecrã resume os passos restantes. Estes passos podem ser diferentes dependendo da versão do iOS. 
    * **iOS 12.2 e posterior**: sua experiência em vez disso, pode solicitar a:  

        a. **Permitir a transferência do perfil de gestão**: O browser abrir o site do Portal da empresa e pedir-lhe para permitir a transferência. A transferência será guardada na sua aplicação de definições.  

        b. **Abra a aplicação de definições e instalar o perfil**: Precisará aceder à aplicação definições e instalar o perfil de gestão.  

        c. **Regressar à aplicação Portal da empresa**: Precisará regressar à aplicação Portal da empresa para concluir a configuração.  

    Quando estiver pronto para transferir o perfil de gestão, toque em **continuar**.  

6. Safari é aberto o site do Portal da empresa. Quando lhe for pedido para transferir o perfil de configuração, toque em **permitir**.  
    * **iOS 12.2 e posterior**: Aguarde que o perfil para serem transferidas no Safari e toque em **feito**. Em seguida, abra a **definições** aplicação no seu dispositivo.  

    > [!IMPORTANT]
    > É preciso ir para o **definições** aplicação e instalar este perfil em menos de 8 minutos baixá-lo. Se não o fizer, o perfil será removido e terá de reiniciar a inscrição. 

7. Na **configurações** aplicação, toque em **instalar perfil transferido** > **instalar**. Se **instalar o perfil transferido** não são apresentados como uma opção, aceda à **gerais** > **perfis**. Se não vir o perfil, terá de transferi-lo novamente.  

    ![Captura de ecrã de exemplo da aplicação de definições, definição de instalar o perfil transferido, com um destaque vermelha que indica um perfil recentemente transferido.](./media/ios-10-cp-enroll-1903.PNG)  
    
8. Se lhe for pedido, introduza a palavra-passe do dispositivo. Em seguida, toque **instalar**.      

9. A próxima tela é um aviso de sistema padrão para gestão de dispositivos. Para saber mais sobre o que sua organização pode e não pode ver no seu dispositivo, veja o relevante [artigo do docs Intune](what-info-can-your-company-see-when-you-enroll-your-device-in-Intune.md). Para continuar com a instalação, toque em **instalar**. Se lhe for pedido para gestão remota de confiança, toque em **confiança**.  

    ![Captura de ecrã do exemplo de aplicação de definições, o ecrã de aviso de sistema padrão para o certificado de raiz e gestão de dispositivos móveis.](./media/ios-15-cp-enroll-1903.PNG)  

10. Após a conclusão da instalação, toque em **feito**. Para verificar se o perfil foi instalado, vá para o **perfis e gestão de dispositivos** definições. Deverá ver o perfil listado na **gestão de dispositivos móveis**.   

    ![Captura de ecrã de exemplo da aplicação de definições, perfis e gestão de dispositivos definições, que mostra o perfil de gestão.](./media/ios-00-cp-enroll-1903.PNG)  


11. Retorno para o **Portal da empresa** aplicação. Portal da empresa irá começar a sincronizar e configurar o dispositivo. Portal da empresa poderá pedir-lhe para atualizar as definições adicionais do dispositivo. Se, toque **continuar**.

    ![Captura de ecrã de exemplo do Portal da empresa, o ecrã "Configurar o acesso ao", com um triângulo amarelo junto à definição requisito.](./media/ios-12-cp-enroll-1903.PNG)  

12. Saberá que a instalação está concluída quando todos os itens na lista de mostram um círculo verde. Toque em **Concluído**.  
    
    ![Captura de ecrã de exemplo do Portal da empresa, "está tudo pronto!" ecrã que mostra todos os círculos verde.](./media/ios-13-cp-enroll-1903.PNG)  

> [!Note]
> Se sua organização monitoriza os limites de voz e dados, ou fornece-lhe um dispositivo da empresa, pode ter mais algumas etapas para concluir. Se lhe for pedido para instalar o **Datalert** aplicação, veja [inscrever o seu dispositivo na gestão de despesas de telecomunicações](enroll-your-device-with-telecom-expense-management-ios.md). Se sua organização faz parte do programa de inscrição de dispositivos da Apple, Descubra [como inscrever o dispositivo pertencentes à empresa](enroll-your-device-dep-ios.md).  

## <a name="next-steps"></a>Passos Seguintes  
Encontre aplicações que lhe ajudarão no trabalho ou escola. Saiba mais [como aplicações são disponibilizadas](use-managed-apps-on-your-device-ios.md) para si através do Portal da empresa.  

Ainda precisa de ajuda? Contacte o suporte da empresa. Pode encontrar as informações de contacto no [Site do Portal da Empresa](https://go.microsoft.com/fwlink/?linkid=2010980).  
