---
title: Inscrever o dispositivo da empresa com a aplicação Microsoft Intune | Documentos da Microsoft
description: Descreve como inscrever um dispositivo da empresa Android no Intune
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/19/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 0ed3a002-7533-4001-ae24-e10b64b66620
searchScope:
- User help
ROBOTS: ''
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7e68e404a91927192f1006626d1b865acd5eb589
ms.sourcegitcommit: d258bcf6716c8a2589d3f8dada819905ee80f233
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/24/2019
ms.locfileid: "66197052"
---
# <a name="enroll-your-corporate-device-with-the-microsoft-intune-app"></a>Inscrever o seu dispositivo da empresa com a aplicação Microsoft Intune

Inscreva o seu dispositivo Android pertencentes à empresa para obter acesso seguro ao e-mail da empresa, aplicações e outros dados que disponibiliza sua organização. A aplicação do Microsoft Intune suporta dispositivos pertencentes à empresa com o Android 6.0 e posterior. Ele será automaticamente instalado nos dispositivos novos e de reposição de fábrica durante a inscrição. 

Existem quatro maneiras de se inscrever. Sua organização deve permitir que sabe que opção de usar.
 
* Comunicação de proximidade (NFC)  
* Certificado de  
* Código QR   
* Google Zero Touch  

## <a name="enroll-device"></a>Inscrever o dispositivo 
Conclua estes passos para configurar e inscrever o seu dispositivo.  

> [!NOTE]
> O fabricante do dispositivo ou versão Android pode implicar a concluir os passos adicionais que não são abrangidos neste procedimento. As cores e texto que vê nas capturas de ecrã também poderão ser diferentes no seu dispositivo.  

1. Ative o seu dispositivo novo ou a reposição de fábrica.  
2. No ecrã **Bem-vindo**, selecione o seu idioma.   Se tiver sido instruído para inscrever-se com um código QR ou NFC, siga o passo abaixo que corresponda ao método.  
     * NFC: Toque em seu dispositivo suportado de NFC em relação a um dispositivo de programador para ligar à rede da sua organização. Siga as instruções na tela. Quando aceder ao ecrã para termos de serviço do Chrome, avance para o passo 5.  

      * Código de QR: Conclua os passos na [inscrição de código de QR](#qr-code-enrollment).  

      Se tiver sido instruído para utilizar outro método, continue para o passo 3.    

1. Ligue-se ao Wi-Fi e toque **seguinte**. Siga o passo que corresponda ao seu método de inscrição. 

    * Token: Quando o ecrã de início de sessão no Google, conclua os passos na [Token de inscrição](#token-enrollment).    
    * Google Zero Touch: Depois de ligar ao Wi-Fi, o dispositivo será reconhecido pela sua organização. Continuar para o passo 4 e siga as instruções no ecrã até que a configuração está concluída.    
 
       ![Imagem de exemplo do ecrã de termos do Google que veja se estiver a utilizar o Google Zero Touch, realce o botão Aceitar e continuar.](./media/google-zero-touch-intune-app-01.png)   
   
4. Reveja os termos da Google. Em seguida, toque **aceitar e continuar**.  

      ![Imagem de exemplo do ecrã de termos do Google, realce o botão Aceitar e continuar.](./media/fully-managed-intune-app-04.png)   

6. Reveja termos do Chrome de serviço. Em seguida, toque **aceitar e continuar**.  

   ![Imagem de exemplo do ecrã do Chrome termos de serviço, realce o botão Aceitar e continuar.](./media/fully-managed-intune-app-06.png)   

7. No início de sessão nos ecrãs, inicie sessão com a sua conta escolar ou profissional.   

    a. Introduza o seu e-mail e toque em **seguinte**.      
    b. Introduza a palavra-passe e toque em **iniciar sessão**.  

8. Dependendo das necessidades da sua organização, poderá ser pedido para atualizar as definições, como bloqueio de ecrã ou encriptação. Se vir esses prompts, toque em **definir** e siga as instruções na tela.  

   ![Imagem de exemplo do conjunto de sua tela de telefone de trabalho, realçando o botão de conjunto.](./media/fully-managed-intune-app-10.png)   

9. Para instalar aplicações de trabalho no seu dispositivo, toque **instalar**. Após a conclusão da instalação, toque em **seguinte**.  

   ![Imagem de exemplo do conjunto de sua tela de telefone de trabalho, realce o botão instalar.](./media/fully-managed-intune-app-11.png)   

10. Quando receber a mensagem de que o dispositivo está pronto, toque em **CONCLUÍDO**. 

11. Vá para as suas aplicações e abra a aplicação Microsoft Intune. Selecione **iniciar sessão**. 

12. Sobre o **configurar o acesso** ecrã, verá uma lista de tarefas pendentes. Toque em **continuar**.  

       ![Imagem de exemplo de aplicação do Microsoft Intune, configure o ecrã de acesso, que mostra a tarefas pendentes.](./media/fully-managed-intune-app-14.png)   

13. Quando o registo do dispositivo estiver concluído, toque em **continuar**. Microsoft Intune pode pedir-lhe para atualizar as definições de dispositivo adicionais.   

       ![Imagem de exemplo de aplicação do Microsoft Intune, ecrã de definições do dispositivo de atualização.](./media/fully-managed-intune-app-15-2.png)   

14. A configuração está concluída quando todos os itens na lista de mostram um círculo verde. Agora pode aceder a recursos da empresa.  

       ![Imagem de exemplo de aplicação do Microsoft Intune, tarefas de configuração de ecrã de acesso, que mostra concluída.](./media/fully-managed-intune-app-16.png)   


## <a name="qr-code-enrollment"></a>Inscrição de código QR  
Nesta secção, irá analisar o código de QR fornecidos da empresa.  Quando tiver terminado, podemos irá redirecioná-lo novamente para os passos de inscrição do dispositivo.     
  
1. Sobre o **bem-vindo** ecrã, toque no ecrã de cinco vezes a configuração de código de QR de início.  

   ![Imagem de exemplo de dispositivo ecrã configuração de boas-vindas, realce de instruções para a tela de toque.](./media/qr-code-intune-app-01.png)  

2. Siga qualquer instruções na tela para ligar ao Wi-Fi.  
3. Se o dispositivo não tiver um scanner de código QR, os ecrãs de configuração irão mostrar o progresso, como um scanner é instalado. Aguarde pela conclusão da instalação.  
4. Quando lhe for pedido, analise o código de QR que sua organização lhe forneceu do perfil de inscrição.  
5. Volte ao [inscrever dispositivo](#enroll-device), passo 4 para continuar a configuração.  

## <a name="token-enrollment"></a>Inscrição de token  
Nesta secção, vai introduzir o seu token fornecido da empresa. Quando tiver terminado, podemos irá redirecioná-lo novamente para os passos de inscrição do dispositivo.  

1. No ecrã Google início de sessão, na **E-Mail ou telefone** , escreva **afw #setup**. Toque em **Seguinte**. 

   ![Imagem de exemplo do Google início de sessão de ecrã, que mostra que o "afw #setup" é escrito num campo.](./media/token-intune-app-01.png)   

2. Escolher **instale** para o **política de dispositivo Android** aplicação. Continua até a instalação. Dependendo do seu dispositivo, poderá ter de rever e aceitar os termos adicionais.    

3. Sobre o **inscrever este dispositivo** ecrã, selecione **próxima**.  

   ![Imagem de exemplo de inscrever este ecrã do dispositivo. Mostra a ilustração de um código QR; destaca o botão seguinte.](./media/token-intune-app-02.png)  

4. Selecione **introduza o código**.

   ![Captura de ecrã do exemplo de um scanner de código de QR Active Directory. Destaques do botão de código de Enter.](./media/token-intune-app-03.png)  

5. Sobre o **analisar ou introduza o código** ecrã, escreva o código que sua organização lhe forneceu.  Clique depois em **Seguinte**.  

   ![Imagem de exemplo de análise ou introduza o ecrã de código, realce o botão seguinte.](./media/token-intune-app-04.png)  

6. Volte ao [inscrever dispositivo](#enroll-device), passo 4 para continuar a configuração.  



## <a name="next-steps"></a>Passos Seguintes   
Ainda precisa de ajuda? Contacte o suporte da empresa (verifique as informações de contacto no [site do Portal da Empresa](https://go.microsoft.com/fwlink/?linkid=2010980)) ou escreva para a <a href="mailto:wintunedroidfbk@microsoft.com?subject=I'm having trouble with enrolling my Android device&body=Describe the issue you're experiencing here.">equipa Android da Microsoft</a>.  
