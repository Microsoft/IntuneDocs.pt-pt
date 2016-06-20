---
# required metadata

title: O dispositivo tem um certificado necessário em falta | Microsoft Intune
description:
keywords:
author: staciebarker
manager: jeffgilb
ms.date: 05/05/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 9081b1d8-50e8-4bc2-ba37-766421364213

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: arnab
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# O dispositivo tem um certificado necessário em falta
Se o dispositivo Android não estiver inscrito no Intune e não tiver um certificado que geralmente é instalado no seu telemóvel, não será possível iniciar sessão na aplicação do Portal da Empresa Android. Ao tentar iniciar sessão, verá a seguinte mensagem:

![andr-cert-install-cert-missing](./media/andr-cert_install-1-cert_missing.png)

Para resolver este problema e obter o certificado necessário:

1.  Num browser, navegue para esta [página de certificado Digicert](https://www.digicert.com/digicert-root-certificates.htm).

2.  Encontre e descarregue o certificado de Root da CyberTrust Baltimore (https://www.digicert.com/CACerts/BaltimoreCyberTrustRoot.crt).

3.  Arraste para baixo a partir da parte superior para abrir as notificações e toque em **BaltimoreCyberTrustRoot.crt** na lista de notificações.

4.  No diálogo **Nomear o certificado**, aceite o nome de certificado predefinido.

5. Certifique-se de que a **Utilização da Credencial** está definida como **Utilizada para VPN e aplicações** e, em seguida, toque em **OK**.

    ![andr-cert-install-add-cert-name](./media/andr-cert_install-2-add_cert_name.png)

6. Feche o browser e a aplicação do Portal da Empresa.

7. Reabra a aplicação do Portal da Empresa. Agora deverá conseguir iniciar sessão na aplicação do Portal da Empresa. Se precisar de ajuda, contacte o administrador de TI.

Se precisar de ajuda e não encontrar as informações de contacto do seu administrador de TI, veja se estão listadas no [Web site do Portal da Empresa](http://portal.manage.microsoft.com).

<!--HONumber=Jun16_HO1-->


