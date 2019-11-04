---
title: Registrar o dispositivo iOS ou iPadOS com Portal da Empresa do Intune e Entrust Datacard
description: Registre um dispositivo iOS ou iPadOS e configure a autenticação de credenciais derivadas com Entrust Datacard.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/31/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
searchScope:
- User help
ROBOTS: ''
ms.reviewer: tisilver
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: bfafa4f35d0b8f1255d66a70c3f7cd0acf01a889
ms.sourcegitcommit: 60f0ff6d2efbae0f2ce14b9a9f3f9267309e209b
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73415590"
---
# <a name="set-up-ios-or-ipados-device-with-company-portal-and-entrust-datacard"></a>Configurar o dispositivo iOS ou iPadOS com Portal da Empresa e Entrust Datacard

Registre seu dispositivo com o aplicativo Portal da Empresa do Intune para obter acesso seguro e móvel ao email, aos arquivos e aos aplicativos da sua organização. Depois que o dispositivo for registrado, ele será *gerenciado*. Sua organização pode atribuir políticas e aplicativos ao dispositivo por meio de um provedor de MDM (gerenciamento de dispositivo móvel), como o Intune.  

Durante o registro, você também instalará uma credencial derivada em seu dispositivo. Sua organização pode exigir que você use a credencial derivada como um método de autenticação ao acessar recursos ou para assinar e criptografar emails. 

Provavelmente, você precisará configurar uma credencial derivada se usar um cartão inteligente para:  

* Entrar em aplicativos escolares ou de trabalho, Wi-Fi e redes virtuais privadas (VPN)
* Assinar e criptografar emails escolares ou de trabalho usando certificados S/MIME  

Neste artigo, você vai:  

   * Registre um dispositivo iOS ou iPadOS móvel com Portal da Empresa do Intune.  
   * Obtenha uma credencial derivada do provedor de credenciais derivadas da sua organização, [Entrust Datacard](https://www.entrustdatacard.com/).  

### <a name="what-are-derived-credentials"></a>O que são credenciais derivadas?  
Uma credencial derivada é um certificado derivado de suas credenciais de cartão inteligente e instalado em seu dispositivo. Ele concede acesso remoto a recursos de trabalho, impedindo que usuários não autorizados acessem informações confidenciais.  

As credenciais derivadas são usadas para: 
* Autentique alunos e funcionários que se conectam a aplicativos escolares ou de trabalho, Wi-Fi e VPN
* Assinar e criptografar emails escolares ou de trabalho com certificados S/MIME

As credenciais derivadas são uma implementação das diretrizes do National Institute of Standards and Technology (NIST) para as credenciais de PIV (verificação de identidade pessoal) derivadas como parte da publicação especial (SP) 800-157.  

## <a name="prerequisites"></a>Pré-requisitos

 Para concluir o registro, você deve ter:

* Cartão inteligente ou de estudante fornecido pelo trabalho
* Acesso a um computador ou quiosque no qual você pode entrar com seu cartão inteligente
* Seu dispositivo móvel
* O aplicativo Portal da Empresa do Intune para iOS e iPadOS instalado em seu dispositivo  


## <a name="enroll-device"></a>Registrar dispositivo  
1. Abra o aplicativo Portal da Empresa para iOS/iPadOS em seu dispositivo móvel e entre com sua conta corporativa.  

2. Anote o código da tela.  

    ![Exemplo de imagem do aplicativo Portal da Empresa com código e mensagem na tela.](./media/copy-code-intercede.png)   

3. Alterne para o dispositivo habilitado para cartão inteligente e vá para https://microsoft.com/devicelogin. 
4. Insira o código que você anotou anteriormente.  

    ![Captura de tela de exemplo do prompt "inserir código" do site da Portal da Empresa.](./media/enter-code-intercede.png)   

5. Insira seu cartão inteligente para entrar.   
6. Retorne ao aplicativo Portal da Empresa em seu dispositivo móvel e siga as instruções na tela para registrar seu dispositivo.  
7. Após a conclusão do registro, Portal da Empresa o notificará para configurar seu cartão inteligente. Toque na notificação. Se você não receber uma notificação, verifique seu email.   

    ![Captura de tela de exemplo da notificação por push Portal da Empresa no dispositivo página inicial.](./media/action-required-in-app-intercede.png)  

8. Na tela de **configuração de acesso a cartão inteligente móvel** :   
    a. Toque no link para as instruções de configuração da sua organização. Se sua organização não fornecer instruções adicionais, você será enviado para este artigo.  
    b. Toque em **Iniciar**.  

    ![A captura de tela de exemplo do Portal da Empresa configurar o acesso do cartão inteligente móvel.](./media/smart-card-info-intercede.png)

9. Alterne para o dispositivo habilitado para cartão inteligente e abra IdentityGuard. 
10. Localize a área de entrada de credencial inteligente e selecione o botão entrar.  
11. Quando for solicitado a selecionar um certificado, escolha suas credenciais de cartão inteligente. Em seguida, selecione **OK**. 
12. Insira o PIN do cartão inteligente.  
13. Você será solicitado a escolher em uma lista de ações. Selecione aquela que permite que você se registre em uma credencial móvel inteligente derivada. O link ou botão pode dizer **que gostaria de se inscrever para uma credencial de cartão inteligente móvel derivada.**  
14. Selecione que você baixou e instalou com êxito o aplicativo habilitado para credencial inteligente. Em seguida, continue na próxima tela.   
15. Insira informações sobre sua credencial de cartão inteligente derivada.  
    a. Para o nome da identidade, insira qualquer nome, como *Entrust derivada creds*.  
    b. No menu suspenso, selecione **Entrust IdentityGudard móvel Smart Credential**.  
    c. Vá para a próxima tela. Você verá um código QR com uma senha numérica sob ele.  

16. Retorne ao seu dispositivo móvel. Na tela Portal da Empresa > **obter código QR** , toque em **continuar**. 

    ![A captura de tela de exemplo da Portal da Empresa obter o código QR.](./media/get-qr-code-intercede.png)  
17. Toque em **usar câmera** > **OK**.  

    ![Captura de tela de exemplo de um prompt de Portal da Empresa, solicitando permissão para permitir o acesso à câmera.](./media/allow-cp-camera-access-intercede.png)  
18. Digitalize a imagem do código QR que está no dispositivo habilitado para cartão inteligente.  
19. Insira a senha numérica que aparece sob o código QR.  

    ![Captura de tela de exemplo do campo Portal da Empresa senha necessária, digite a senha.](./media/enter-password-derived-credentials.png)   

20. Aguarde Portal da Empresa concluir a configuração do dispositivo.  


## <a name="next-steps"></a>Próximos passos  
Após a conclusão do registro, você terá acesso aos recursos de trabalho, como email, Wi-Fi e quaisquer aplicativos disponibilizados pela sua organização. Para obter mais informações sobre como obter, Pesquisar, instalar e desinstalar aplicativos no Portal da Empresa consulte:

* [Gerenciar aplicativos do site Portal da Empresa](manage-apps-cpweb.md)  
* [Utilizar aplicações geridas no dispositivo](use-managed-apps-on-your-device-ios.md)  

Ainda precisa de ajuda? Contacte o suporte da empresa. Para encontrar as informações de contacto dele, verifique o [site do Portal da Empresa](https://go.microsoft.com/fwlink/?linkid=2010980).  
