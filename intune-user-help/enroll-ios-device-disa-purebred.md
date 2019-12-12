---
title: Registrar o dispositivo iOS ou iPadOS com Portal da Empresa do Intune e DISA purebred
description: Saiba como registrar um dispositivo iOS ou iPadOS e configurar a autenticação de credencial derivada com DISA purebred.
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
ms.openlocfilehash: 5c484b98466c1418016f4ebc6cc805e412d7891e
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/05/2019
ms.locfileid: "73415598"
---
# <a name="set-up-ios-or-ipados-device-with-company-portal-and-disa-purebred"></a>Configurar o dispositivo iOS ou iPadOS com Portal da Empresa e DISA purebred  

Registre seu dispositivo com o aplicativo Portal da Empresa do Intune para obter acesso seguro e móvel ao email, aos arquivos e aos aplicativos da sua organização. Depois que o dispositivo for registrado, ele será *gerenciado*. Sua organização pode atribuir políticas e aplicativos ao dispositivo por meio de um provedor de MDM (gerenciamento de dispositivo móvel), como o Intune.  

Durante o registro, você também instalará uma credencial derivada em seu dispositivo. Sua organização pode exigir que você use a credencial derivada como um método de autenticação ao acessar recursos ou para assinar e criptografar emails. 

Provavelmente, você precisará configurar uma credencial derivada se usar um cartão inteligente para:

* Entrar em aplicativos escolares ou de trabalho, Wi-Fi e redes virtuais privadas (VPN)
* Assinar e criptografar emails escolares ou de trabalho usando certificados S/MIME  

Neste artigo, vai:  

   * Registre um dispositivo iOS ou iPadOS móvel com Portal da Empresa do Intune.  
   * Obtenha uma credencial derivada do provedor de credenciais derivado de sua organização, [Disa purebred](https://cyber.mil/pki-pke/purebred/).  

## <a name="what-are-derived-credentials"></a>O que são credenciais derivadas?  
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

Você também precisará entrar em contato com um agente ou representante do purebred durante a instalação.      

## <a name="enroll-device"></a>Inscrever o dispositivo  
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
    b. Clique em **abrir** para abrir o aplicativo purebred.  

    ![A captura de tela de exemplo do Portal da Empresa configurar o acesso do cartão inteligente móvel.](./media/smart-card-open-disa-purebred.png)  
9. Quando solicitado a permitir que Portal da Empresa Abra o aplicativo de registro purebred, selecione **abrir**.   

    ![Exemplo de captura de tela do prompt de Portal da Empresa para abrir o aplicativo DISA purebred.](./media/open-app-prompt-disa-purbred.png)  
10. Quando o aplicativo funciona, trabalhe com o agente purebred da sua organização para configurar e baixar o perfil de configuração de pré-registro do purebred.   
11. Vá para o aplicativo Configurações > **geral** > **perfis & gerenciamento de dispositivo** > **instalar perfil** e toque em **instalar**.  
12. Insira a senha do dispositivo.  
13. Instale o perfil. Talvez seja necessário tocar em **instalar** mais de uma vez para iniciar a instalação. 
14. Retorne ao aplicativo de registro purebred. Siga as instruções do agente do purebred para continuar.  
 
15. Depois de baixar o perfil de configuração, vá para o aplicativo Configurações > **geral** > **perfis & gerenciamento de dispositivo** > **instalar perfil** e toque em **instalar**.   
16.  Insira a senha do dispositivo.
17. Instale o perfil. Talvez seja necessário tocar em **instalar** mais de uma vez para iniciar a instalação. 
18. Após a conclusão da instalação, retorne ao aplicativo Portal da Empresa.  
19.  Na tela **Configurar acesso ao cartão inteligente móvel** , toque em **continuar**.  

20. Na tela **importar certificados** , você recuperará e importará a credencial derivada Obtida de Disa purebred.  

    a. Toque em **Continuar**.   

    ![captura de tela de exemplo da exibição Portal da Empresa definir certificados de importação.](./media/import-certificate-disa-purebred.png)  
    b. Vá para a unidade iCloud **navegue** > **locais** e toque em **mais locais**.  

    ![captura de tela de exemplo da unidade iCloud, o menu procurar realçar mais locais.](./media/icloud-drive-more-locations.png)  
    c. Toque na opção para habilitar a **cadeia de chaves purebred**.  

    ![Captura de tela de exemplo da unidade iCloud, modo de exibição de navegação, realçando que a chave do purebred Key Chain está habilitada.](./media/icloud-drive-enable-purebred-keychain.png)   

    d. Toque em **pacote de credencial purebred**.  

    ![instantâneo de exemplo de uma tela do iOS com uma opção de pacote de credencial purebred selecionável.](./media/purebred-credential-package.png)  
    f. Uma lista de certificados é exibida. Selecione um e, em seguida, toque em **importar chave**.  

    ![Captura de tela de exemplo de uma lista de certificados selecionáveis, com um já selecionado.](./media/import-purebred-keychain.png) 
21. Retorne ao aplicativo Portal da Empresa e aguarde Portal da Empresa concluir a configuração do dispositivo.   

## <a name="next-steps"></a>Próximos passos  
Após a conclusão do registro, você terá acesso aos recursos de trabalho, como email, Wi-Fi e quaisquer aplicativos disponibilizados pela sua organização. Para obter mais informações sobre como obter, Pesquisar, instalar e desinstalar aplicativos no Portal da Empresa consulte:

* [Gerenciar aplicativos do site Portal da Empresa](manage-apps-cpweb.md)  
* [Utilizar aplicações geridas no dispositivo](use-managed-apps-on-your-device-ios.md)  

Ainda precisa de ajuda? Contacte o suporte da empresa. Para encontrar as informações de contacto dele, verifique o [site do Portal da Empresa](https://go.microsoft.com/fwlink/?linkid=2010980).
