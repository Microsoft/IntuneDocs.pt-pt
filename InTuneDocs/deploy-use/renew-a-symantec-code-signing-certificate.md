---
title: "Renovar um certificado empresarial de assinatura com código da Symantec para utilizar com o Intune | Documentos da Microsoft"
description: "Documentação de orientação para renovar os certificados da Symantec utilizado para gerir determinados dispositivos móveis Windows e Windows Phone"
keywords: 
author: staciebarker
ms.author: stabar
manager: angerobe
ms.date: 07/25/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c4813044-a925-4273-b0ec-e992fd55850a
ms.reviewer: damionw
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 928e4e8097b9cd326e0863a45b183226a7eae056
ms.openlocfilehash: acd1ab3a988adc4fee2a57ff4be82bac8e92a435


---

# <a name="renew-a-symantec-enterprise-code-signing-certificate-for-windows-devices"></a>Renovar um certificado empresarial de assinatura com código da Symantec para dispositivos Windows

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

O certificado da Symantec utilizado para implementar aplicações para dispositivos móveis Windows e Windows Phone tem de ser renovado periodicamente.

## <a name="how-to-renew-the-symantec-enterprise-code-signing-certificate"></a>Como renovar o certificado empresarial de assinatura com código da Symantec

1.  Procure um e-mail de renovação enviado pela Symantec cerca de 14 dias antes da expiração do certificado. Este e-mail contém instruções da Symantec sobre como renovar o seu certificado empresarial.

    Para obter informações adicionais sobre os certificados da Symantec, aceda a [www.symantec.com](http://www.symantec.com) ou ligue para o 1-877-438-8776 ou 1-650-426-3400.

2.  Aceda ao site (exemplo: [https://products.websecurity.symantec.com/orders/enrollment/microsoftCert.do](https://products.websecurity.symantec.com/orders/enrollment/microsoftCert.do)) e inicie sessão com o ID de publicador da Symantec e o endereço de e-mail associado ao certificado. Lembre-se de utilizar o mesmo computador para iniciar a renovação e para transferir o certificado.

3.  Após a aprovação e pagamento da renovação, transfira o certificado.

## <a name="how-to-install-the-updated-certificate-for-windows-phone-80"></a>Como instalar o certificado atualizado para Windows Phone 8.0

1.  Transfira e assine o Portal da Empresa do Windows Phone mais recente, localizado em [http://www.microsoft.com/en-us/download/details.aspx?id=36060](http://www.microsoft.com/en-us/download/details.aspx?id=36060).

2.  Abra a Consola de Administração do Intune ([https://admin.manage.microsoft.com](https://admin.manage.microsoft.com)) e aceda a **Admin**, **Mobile Device Management** &gt; **Windows Phone** e clique em **Upload Signed App**.

3.  Carregue o Portal da Empresa que acabou de assinar. Irá precisar do ficheiro SSP.xap recentemente assinado e do novo ficheiro .PFX que recebeu da Symantec ou do token de inscrição da aplicação que foi criado com este novo ficheiro .PFX.

4.  Quando o carregamento estiver concluído, remova a antiga versão do Portal da Empresa na área de trabalho **Software** da Consola de Gestão do Intune.

5.  Assine novamente todas as aplicações empresariais de linha de negócio com o mesmo certificado e carregue e substitua as aplicações existentes.

Atualmente, fornecer um ficheiro SSP.xap assinado é a única forma de fornecer o certificado de assinatura de código atualizado. Para suportar aplicações de linha de negócio assinadas, tem de assinar e carregar uma aplicação Portal da Empresa, não obstante os utilizadores instalarem a aplicação Portal da Empresa a partir da loja.

## <a name="how-to-install-the-updated-certificate-for-windows-phone-81-and-later-devices"></a>Como instalar o certificado atualizado para Windows Phone 8.1 e dispositivos posteriores

1.  Transfira e assine o Portal da Empresa do Windows Phone mais recente a partir do Centro de Transferências, localizado em [http://www.microsoft.com/en-us/download/details.aspx?id=36060](http://www.microsoft.com/en-us/download/details.aspx?id=36060).

2.  Abra a [Consola de Administração do Intune](https://admin.manage.microsoft.com) (https://admin.manage.microsoft.com) e aceda a **Admin** &gt; **Mobile Device Management** &gt; **Windows Phone** e clique em **Upload Signed App**.

3.  Carregue o Portal da Empresa que acabou de assinar. Irá precisar do ficheiro SSP.xap recentemente assinado e do novo ficheiro .PFX que recebeu da Symantec ou do token de inscrição da aplicação que foi criado com este novo ficheiro .PFX.

4.  Quando o carregamento estiver concluído, remova a versão antiga do Portal da Empresa na área de trabalho **Software**  .

5.  Assine todas as aplicações empresariais de linha de negócio novas e atualizadas com o novo certificado. Não é necessário voltar a assinar e a implementar as aplicações existentes.


### <a name="see-also"></a>Consulte também
[Configurar a gestão do Windows Phone 8.0](set-up-windows-phone-8.0-management-with-microsoft-intune.md)
[Configurar a gestão do Windows Phone](set-up-windows-phone-management-with-microsoft-intune.md)



<!--HONumber=Dec16_HO2-->


