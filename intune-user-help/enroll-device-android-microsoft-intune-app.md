---
title: Registrar dispositivo corporativo com o aplicativo Microsoft Intune | Microsoft Docs
description: Descreve como registrar um dispositivo Android corporativo no Intune
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
ms.openlocfilehash: b23323766e91e31c48aec6a51dfae971c3a333e8
ms.sourcegitcommit: 1dc9d4e1d906fab3fc46b291c67545cfa2231660
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67735753"
---
# <a name="enroll-your-corporate-device-with-the-microsoft-intune-app"></a>Registrar seu dispositivo corporativo no aplicativo Microsoft Intune

Registre seu dispositivo Android corporativo para obter acesso seguro a emails, aplicativos e outros dados da empresa disponibilizados pela sua organização. O aplicativo Microsoft Intune dá suporte a dispositivos de propriedade corporativa que executam o Android 6,0 e posterior. Ele será instalado automaticamente em dispositivos novos e de redefinição de fábrica durante o registro. 

Há quatro maneiras de se registrar. Sua organização deve permitir que você saiba qual opção usar.
 
* NFC (comunicação a curta distância)  
* Certificado de  
* Código QR   
* Google Zero Touch  

## <a name="enroll-device"></a>Registrar dispositivo 
Conclua estas etapas para configurar e registrar seu dispositivo.  

> [!NOTE]
> A versão do Android ou o fabricante do dispositivo pode exigir que você conclua etapas adicionais que não são abordadas neste procedimento. As cores e o texto que você vê nas capturas de tela também podem aparecer diferentes em seu dispositivo.  

1. Ative seu dispositivo novo ou de redefinição de fábrica.  
2. No ecrã **Bem-vindo**, selecione o seu idioma.   Se você foi instruído a se registrar com um código QR ou NFC, siga a etapa abaixo que corresponde ao método.  
     * NFC: Toque em seu dispositivo com suporte a NFC em um dispositivo programador para se conectar à rede da sua organização. Siga os prompts na tela. Quando você chegar à tela para os termos de serviço do Chrome, continue na etapa 5.  

     * Código QR: Conclua as etapas no [registro de código QR](#qr-code-enrollment).  

     Se você foi instruído a usar outro método, continue na etapa 3.    

1. Conecte-se ao Wi-Fi e toque **em Avançar**. Siga a etapa que corresponde ao seu método de registro. 

    * Token: Quando você chegar à tela de entrada do Google, conclua as etapas em [registro de token](#token-enrollment).    
    * Google Zero Touch: Depois de se conectar ao Wi-Fi, seu dispositivo será reconhecido pela sua organização. Continue na etapa 4 e siga os prompts na tela até que a instalação seja concluída.    
 
       ![Imagem de exemplo da tela de termos do Google que você vê se estiver usando o Google Zero Touch, realçando aceitar & botão continuar.](./media/google-zero-touch-intune-app-01.png)   
   
4. Examine os termos do Google. Em seguida, toque em **aceitar &AMP; continuar**.  

      ![Imagem de exemplo da tela de termos do Google, realçando aceitar & botão continuar.](./media/fully-managed-intune-app-04.png)   

6. Examine os termos de serviço do Chrome. Em seguida, toque em **aceitar &AMP; continuar**.  

   ![Exemplo de imagem da tela de termos de serviço do Chrome, realçando aceitar & botão continuar.](./media/fully-managed-intune-app-06.png)   

7. Nas telas de entrada, entre com sua conta corporativa ou de estudante.   

    a. Insira seu email e toque **em Avançar**.      
    b. Insira sua senha e toque **em entrar**.  

8. Dependendo dos requisitos da sua organização, você poderá ser solicitado a atualizar as configurações, como o bloqueio de tela ou a criptografia. Se você vir esses prompts, toque em **definir** e siga as instruções na tela.  

   ![Exemplo de imagem de configuração da tela de telefone comercial, realçando o botão Definir.](./media/fully-managed-intune-app-10.png)   

9. Para instalar aplicativos de trabalho em seu dispositivo, toque em **instalar**. Após a conclusão da instalação, toque em **Avançar**.  

   ![Imagem de exemplo da tela configurar seu telefone comercial, realçando o botão instalar.](./media/fully-managed-intune-app-11.png)   

10. Quando você receber a mensagem de que seu dispositivo está pronto, toque em **concluído**. 

11. Vá para seus aplicativos e abra o aplicativo Microsoft Intune. Selecione **entrar**. 

12. Na tela de **acesso à instalação** , você verá uma lista de tarefas pendentes. Toque em **continuar**.  

       ![Imagem de exemplo do aplicativo Microsoft Intune, configurar a tela de acesso, mostrando as tarefas pendentes.](./media/fully-managed-intune-app-14.png)   

13. Quando o registro do dispositivo for concluído, toque em **continuar**. Microsoft Intune pode solicitar que você atualize configurações de dispositivo adicionais.   

       ![Imagem de exemplo do aplicativo Microsoft Intune, tela atualizar configurações do dispositivo.](./media/fully-managed-intune-app-15-2.png)   

14. A instalação será concluída quando todos os itens da lista mostrarem um círculo verde. Agora você pode acessar os recursos da empresa.  

       ![Imagem de exemplo do aplicativo Microsoft Intune, configurar a tela de acesso, mostrando as tarefas concluídas.](./media/fully-managed-intune-app-16.png)   


## <a name="qr-code-enrollment"></a>Registro de código QR  
Nesta seção, você examinará o código QR fornecido pela empresa.  Quando terminar, redirecionaremos você de volta para as etapas de registro do dispositivo.     
  
1. Na tela de **boas-vindas** , toque na tela cinco vezes para iniciar a configuração do código QR.  

   ![Imagem de exemplo da tela de boas-vindas de instalação do dispositivo, destacando as instruções para tocar na tela.](./media/qr-code-intune-app-01.png)  

2. Siga as instruções na tela para se conectar ao Wi-Fi.  
3. Se o dispositivo não tiver um scanner de código QR, as telas de instalação mostrarão o progresso à medida que um scanner for instalado. Aguarde pela conclusão da instalação.  
4. Quando solicitado, digitalize o código QR do perfil de registro que sua organização forneceu a você.  
5. Retorne para [registrar o dispositivo](#enroll-device), etapa 4 para continuar a instalação.  

## <a name="token-enrollment"></a>Registro de token  
Nesta seção, você inserirá o token fornecido pela empresa. Quando terminar, redirecionaremos você de volta para as etapas de registro do dispositivo.  

1. Na tela de entrada do Google, na caixa **email ou telefone** , digite **AFW # setup**. Toque em **Seguinte**. 

   ![Imagem de exemplo da tela de entrada do Google, mostrando que "AFW # Setup" é digitado em campo.](./media/token-intune-app-01.png)   

2. Escolha **instalar** para o aplicativo de **política de dispositivo Android** . Continue a instalação. Dependendo do seu dispositivo, talvez seja necessário examinar e aceitar termos adicionais.    

3. Na tela **registrar este dispositivo** , selecione **Avançar**.  

   ![Imagem de exemplo da tela registrar este dispositivo. Mostra a ilustração de um código QR; realça o botão Avançar.](./media/token-intune-app-02.png)  

4. Selecione **Inserir código**.

   ![Captura de tela de exemplo de um scanner de código QR ativo. Realces inserir botão de código.](./media/token-intune-app-03.png)  

5. Na tela **examinar ou inserir código** , digite o código que sua organização forneceu a você.  Clique depois em **Seguinte**.  

   ![Imagem de exemplo da tela de verificação ou de inserção de código, realçando o botão Avançar.](./media/token-intune-app-04.png)  

6. Retorne para [registrar o dispositivo](#enroll-device), etapa 4 para continuar a instalação.  



## <a name="next-steps"></a>Passos seguintes   
Ainda precisa de ajuda? Contacte o suporte da empresa (verifique as informações de contacto no [site do Portal da Empresa](https://go.microsoft.com/fwlink/?linkid=2010980)) ou escreva para a <a href="mailto:wintunedroidfbk@microsoft.com?subject=I'm having trouble with enrolling my Android device&body=Describe the issue you're experiencing here.">equipa Android da Microsoft</a>.  
