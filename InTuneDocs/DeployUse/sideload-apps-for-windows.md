---
title: "Aplicações em Sideload para Windows e Windows Phone | Microsoft Intune"
description: "Saiba como assinar aplicações de linha empresarial de forma a poder utilizar o Intune para as implementar."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 11/16/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: e44f1756-52e1-4ed5-bf7d-0e80363a8674
translationtype: Human Translation
ms.sourcegitcommit: 6fcdacc4746e780dcd9a988a46a4153929516449
ms.openlocfilehash: 5debf013e4ff6c9f72eb59e31f256e00fd6f9540


---
# <a name="sign-line-of-business-apps-so-they-can-be-deployed-to-windows-devices-with-intune"></a>Assine aplicações de linha de negócio para que possam ser implementadas nos dispositivos Windows com o Intune

Enquanto administrador do Intune, pode implementar aplicações de linha de negócio (LOB) em dispositivos Windows e Windows 10 Mobile, incluindo a aplicação do Portal da Empresa. Para implementar aplicações .appx ou .xap em dispositivos Windows 10 e Windows 10 Mobile ou implementar qualquer aplicação LOB em dispositivos Windows 8.1 ou Windows Phone 8.1, tem de obter um **Certificado de Assinatura de Código de Dispositivo Móvel Empresarial da Symantec**. Apenas o certificado da Symantec é considerado fidedigno para essas aplicações para os respetivos dispositivos do Windows. Pode utilizar a sua própria autoridade de certificação para aplicações do Windows 10 e aplicações "universais". Este certificado é necessário para:

-   Assine a aplicação do Portal da Empresa para a implementação de PCs Windows, dispositivos Windows 10 Mobile e dispositivos Windows Phone

-   Assine aplicações de linha de negócio para que o Intune as possa implementar em dispositivos Windows

Os passos abaixo irão ajudá-lo a obter o certificado obrigatório e a assinar as aplicações. Precisará de uma conta do Windows Phone Dev Center e de comprar um certificado da Symantec.


1. **Aderir ao Windows Phone Dev Center**<br>
   Adira ao [Windows Phone Dev Center](http://go.microsoft.com/fwlink/?LinkId=268442) ao utilizar as informações de conta empresarial quando iniciar sessão para comprar a sua conta de empresa. Este pedido terá de ser autorizado por um responsável da empresa antes de poder receber um certificado de assinatura com código.

2. **Obter um certificado empresarial da Symantec**<br>
  Compre um certificado no [Web site da Symantec](http://go.microsoft.com/fwlink/?LinkId=268441) com o seu ID da Symantec. Depois de comprar o certificado, o aprovador da empresa que tiver designado na sua conta do Windows Phone Dev Center receberá uma mensagem de e-mail a solicitar a aprovação do pedido de certificado. Para mais informações sobre o requisito do certificado da Symantec, consulte as FAQ sobre a inscrição de dispositivos Windows [Por que é que o Windows Phone precisa de um certificado da Symantec?](https://technet.microsoft.com/en-us/library/dn764959.aspx#BKMK_Symantec) FAQ de inscrição de dispositivos Windows.

3.  **Importar certificados**<br>
    Quando o pedido for aprovado, receberá um e-mail com instruções para importar os certificados. Siga as instruções no e-mail para importar os certificados.

4.  **Verificar os certificados importados**<br>
    Para verificar se os certificados foram corretamente importados, vá para o snap-in **Certificados**, clique com o botão direito do rato em **Certificados** e selecione **Localizar Certificados**. No campo **Contém** , escreva “Symantec” e clique em **Localizar Agora**. Os certificados que importou deverão ser apresentados nos resultados.

    ![Localizar o certificado da Symantec](../media/wit.gif)

5. **Exportar um certificado de assinatura**<br>
    Após verificar que os certificados estão presentes, pode exportar o ficheiro .pfx para assinar o portal da empresa. Selecione o certificado da Symantec com “assinatura com código” como o **Objetivo a que se destina**. Clique com o botão direito do rato no certificado de assinatura com código e selecione **Exportar**.

    ![Exportar o certificado de assinatura](../media/wit-walk-cert2.gif)

    No **Assistente para Exportar Certificados**, selecione **Sim, exportar a chave privada** e, em seguida, clique em **Seguinte**. **Selecione Personal Information Exchange –PKCS #12 (.PFX)** e marque **Incluir todos os certificados no caminho de certificação, se possível**. Conclua o assistente. Para mais informações, consulte o artigo [Como Exportar um Certificado com a Chave Privada](http://go.microsoft.com/fwlink/?LinkID=203031).

6.  **Carregar a aplicação para o Intune**<br>
    Carregue o ficheiro assinado da aplicação e o seu certificado de assinatura com código para disponibilizar a aplicação aos seus utilizadores finais.

    1.  Na [consola de administração do Intune](http://manage.microsoft.com), clique em **Administração** &gt; **Windows Phone**.

    2.  Clique em **Carregar o Ficheiro Assinado da Aplicação** e inicie sessão com o seu ID de Administrador do Intune.

    3.  Adicione o ficheiro de certificado (.pfx) que exportou para o **Certificado de assinatura com código** e crie uma palavra-passe para o certificado.

    4.  Conclua o assistente.

## <a name="example-download-sign-and-deploy-the-company-portal-app-for-windows-devices"></a>Exemplo: transferir, assinar e implementar a aplicação do Portal da Empresa para dispositivos Windows

Pode implementar a aplicação do Portal da Empresa em dispositivos Windows, incluindo Windows Phone e Windows 10 Mobile, com o Intune em vez de instalá-la a partir da Loja Windows. Tem de transferir a aplicação do Portal da Empresa e assiná-la com o seu certificado.  Isto apenas é necessário se os utilizadores não utilizarem a Loja da Empresa e pretender implementar o Portal da Empresa em dispositivos Windows Phone 8.1.


1.  **Transferir o Portal da Empresa**

    Para implementar a aplicação do Portal da Empresa com o Intune, pode transferir a [Aplicação Portal da Empresa do Microsoft Intune para Windows Phone 8.1](http://go.microsoft.com/fwlink/?LinkId=615799) a partir do Centro de Transferências e execute o ficheiro de extração automática (.exe). Este ficheiro contém dois ficheiros:

    -   CompanyPortal.appx – a aplicação de instalação do Portal da Empresa para Windows Phone 8.1

    -   WinPhoneCompanyPortal.ps1 – um script do PowerShell que pode utilizar para assinar o ficheiro de aplicação do Portal da Empresa, para que possa ser implementado em dispositivos Windows Phone 8.1

    Em alternativa, pode transferir o Portal da Empresa do Windows Phone 8.1 (pacote com licença offline) a partir da [Loja Windows para Empresas](http://businessstore.microsoft.com/). A aplicação do Portal da Empresa terá de ser adquirida com uma licença offline e o pacote apropriado transferido para utilização offline. As listagens das plataformas Windows 8 e Windows Phone 8 na seleção mencionam as respetivas plataformas 8.1 homólogas.

2.  **Transferir o Windows Phone SDK** Transfira o Windows Phone SDK 8.0 (http://go.microsoft.com/fwlink/?LinkId=615570) e instale o SDK no seu computador. Este SDK é necessário para gerar um token de inscrição de aplicações.

3.  **Gerar um ficheiro AETX** Faça a gestão de um ficheiro de token de inscrição de aplicações (.aetx) a partir do ficheiro PFX da Symantec com o AETGenerator.exe, que faz parte do Windows Phone SDK 8.0. Para obter instruções sobre como criar um ficheiro AETX, consulte [How to generate an application enrollment token for Windows Phone](https://msdn.microsoft.com/library/windows/apps/jj735576.aspx)(Como gerar um token de inscrição de aplicações para Windows Phone)

4.  **Transferir o Windows SDK para Windows 8.1** Transfira e instale e o [Windows Phone SDK](http://go.microsoft.com/fwlink/?LinkId=613525) (http://go.microsoft.com/fwlink/?LinkId=613525). Tenha em atenção que o script do PowerShell incluído com a aplicação Portal da Empresa utiliza a localização de instalação predefinida, `${env:ProgramFiles(x86)}\Windows Kits\8.1`. Se instalar noutra localização, tem de incluí-la num parâmetro de cmdlet.

5.  **Assinar a aplicação com código através do PowerShell** Na qualidade de administrador, abra o **Windows PowerShell** no computador anfitrião instalado com o Windows SDK, o Certificado de Assinatura de Código de Dispositivo Móvel Empresarial da Symantec, navegue para o ficheiro Sign-WinPhoneCompanyPortal.ps1 e execute o script.

    **Exemplo 1**

    ```
    .\Sign-WinPhoneCompanyPortal.ps1 -InputAppx 'C:\temp\CompanyPortal.appx' -OutputAppx 'C:\temp\CompanyPortalEnterpriseSigned.appx' -PfxFilePath 'C:\signing\cert.pfx' -PfxPassword '1234' -AetxPath 'C:\signing\cert.aetx'
    ```
    Este exemplo assina o CompanyPortal.appx em C:\temp\ e produz o CompanyPortalEnterpriseSigned.appx. Seria utilizada a palavra-passe 1234 do PFX e seria lido o ID de publicador do ficheiro PFX. Também lê o ID empresarial do ficheiro cert.aetx.

    **Exemplo 2**

    ```
    .\Sign-WinPhoneCompanyPortal.ps1 -InputAppx 'C:\temp\CompanyPortal.appx' -OutputAppx 'C:\temp\CompanyPortalEnterpriseSigned.appx' -PfxFilePath 'C:\signing\cert.pfx' -PfxPassword '1234' -PublisherId 'OID.0.9.2342.19200300.100.1.1=1000000001, CN="Test, Inc.", OU=Test 1' -EnterpriseId 1000000001
    ```
    Este exemplo assina o CompanyPortal.appx em C:\temp\ e produz o CompanyPortalEnterpriseSigned.appx. Seria utilizada a palavra-passe 1234 do PFX e seria utilizado o ID de publicador especificado.

    **Parâmetros:**

    -   `-InputAppx` – o caminho local do ficheiro CompanyPortal.appx entre plicas. Por exemplo, 'C:\temp\CompanyPortal.appx'

    -   `-OutputAppx` – o caminho local e o nome do ficheiro da aplicação Portal da Empresa assinada entre plicas. Por exemplo, 'C:\temp\CompanyPortalEnterpriseSigned.appx'

    -   `-PfxFilePath` – o caminho local e o nome do ficheiro do ficheiro PFX exportado do certificado da Symantec. Por exemplo, 'C:\signing\cert.pfx'

    -   `-PfxPassword` – a palavra-passe utilizada para assinar o ficheiro PFX entre plicas. Por exemplo, '1234'

    -   `-AetxPath` – o caminho local do ficheiro .aetx que é utilizado para ler o ID empresarial quando o argumento "EnterpriseId" não está definido. O argumento ou o EnterpriseId têm de ser fornecidos. Por exemplo, 'C:\signing\cert.aetx'

    -   `-PublisherId` – O ID de Publicador da empresa. Se estiver ausente, é utilizado o campo "Assunto" do Certificado de Assinatura de Código de Dispositivo Móvel Empresarial da Symantec. Por exemplo, 'OID.0.9.2342.19200300.100.1.1=1000000001, CN="Test, Inc.", OU=Test 1'

    -   `-SdkPath` – O caminho para a pasta raiz do Windows SDK para Windows 8.1. Este argumento é opcional e está predefinido para ${env:ProgramFiles(x86)}\Windows Kits\8.1.

    -   `-EnterpriseId` – O ID empresarial. O argumento ou o "AetxPath" têm de ser fornecidos. Se este argumento não for fornecido, o ID empresarial é lido a partir do ficheiro AETX. For example, 1000000001

6.  Implemente a aplicação Portal da Empresa do Windows Phone 8.1 (SSP.appx). Para obter orientações, veja [Implementar aplicações no Microsoft Intune](deploy-apps-in-microsoft-intune.md).

## <a name="how-to-renew-the-symantec-enterprise-code-signing-certificate"></a>Como renovar o certificado empresarial de assinatura com código da Symantec

O certificado da Symantec utilizado para implementar aplicações para dispositivos móveis Windows e Windows Phone tem de ser renovado periodicamente.

1.  Procure um e-mail de renovação enviado pela Symantec cerca de 14 dias antes da expiração do certificado. Este e-mail contém instruções da Symantec sobre como renovar o seu certificado empresarial.

    Para obter informações adicionais sobre os certificados da Symantec, aceda a [www.symantec.com](http://www.symantec.com) ou ligue para o 1-877-438-8776 ou 1-650-426-3400.

2.  Aceda ao Web site (exemplo: [https://products.websecurity.symantec.com/orders/enrollment/microsoftCert.do](https://products.websecurity.symantec.com/orders/enrollment/microsoftCert.do)) e inicie sessão com o ID de publicador da Symantec e o endereço de e-mail associado ao certificado. Lembre-se de utilizar o mesmo computador para iniciar a renovação e para transferir o certificado.

3.  Após a aprovação e pagamento da renovação, transfira o certificado.

### <a name="how-to-install-the-updated-certificate-for-line-of-business-lob-apps"></a>Como instalar o certificado atualizado para aplicações de linha de negócio (LOB)

1.  Assine a versão mais recente da sua aplicação de linha de negócio.

2.  Abra a [Consola de Administração do Intune](https://admin.manage.microsoft.com) (https://admin.manage.microsoft.com) e aceda a **Admin** &gt; **Mobile Device Management** &gt; **Windows Phone** e clique em **Upload Signed App**.

3.  Carregue o Portal da Empresa que acabou de assinar. Irá precisar do ficheiro SSP.xap recentemente assinado e do novo ficheiro .PFX que recebeu da Symantec ou do token de inscrição da aplicação que foi criado com este novo ficheiro .PFX.

4.  Quando o carregamento estiver concluído, remova a versão antiga do Portal da Empresa na área de trabalho **Software**  .

5.  Assine todas as aplicações empresariais de linha de negócio novas e atualizadas com o novo certificado. Não é necessário voltar a assinar e a implementar as aplicações existentes.



<!--HONumber=Nov16_HO3-->


