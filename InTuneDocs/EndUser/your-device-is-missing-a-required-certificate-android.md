---
title: "O dispositivo tem um certificado necessário em falta | Microsoft Intune"
description: 
keywords: 
author: staciebarker
manager: angrobe
ms.date: 7/7/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9081b1d8-50e8-4bc2-ba37-766421364213
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: arnab
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 38301b4e6964550008b08e99bf7016f1cc2561c3
ms.openlocfilehash: 6740962e55b1232330c6fab43ce1250a54e3a97b


---


# O dispositivo tem um certificado necessário em falta


## Está em falta um certificado no dispositivo que, geralmente, vem instalado no telemóvel
Se o dispositivo Android não estiver inscrito no Intune e não tiver um certificado que geralmente é instalado no seu telemóvel, não será possível iniciar sessão na aplicação do Portal da Empresa Android. Ao tentar iniciar sessão, verá a seguinte mensagem:

![screenshot-error-message-about-missing-certificate](./media/andr-cert_install-1-cert_missing.png)

Para resolver este problema e obter o certificado necessário:

1.  Num browser, navegue para esta [página de certificado Digicert](https://www.digicert.com/digicert-root-certificates.htm).

2.  Encontre e descarregue o certificado de Root da CyberTrust Baltimore (https://www.digicert.com/CACerts/BaltimoreCyberTrustRoot.crt).

3.  Arraste para baixo a partir da parte superior para abrir as notificações e toque em **BaltimoreCyberTrustRoot.crt** na lista de notificações.

4.  No diálogo **Nomear o certificado**, aceite o nome de certificado predefinido.

5. Certifique-se de que a **Utilização da Credencial** está definida como **Utilizada para VPN e aplicações** e, em seguida, toque em **OK**.

    ![screenshot-certificate-name-dialog-showing-baltimore-certificate-name](./media/andr-cert_install-2-add_cert_name.png)

6. Feche o browser e a aplicação do Portal da Empresa.

7. Reabra a aplicação do Portal da Empresa. Agora deverá conseguir iniciar sessão na aplicação do Portal da Empresa. Se precisar de ajuda, contacte o administrador de TI.

## Está em falta um certificado no dispositivo de que o administrador de TI precisa
Se o seu dispositivo Android não estiver inscrito no Intune e não tiver um determinado certificado de que o seu administrador de TI precisa, não poderá iniciar sessão na aplicação do Portal da Empresa para Android. Ao tentar iniciar sessão, verá a seguinte mensagem:

![screenshot-error-message-about-missing-certificate](./media/andr-cert_install-1-cert_missing.png)

>[!NOTE]
> Se já tiver visto uma mensagem a dizer “certificado em falta” e tiver seguido os passos em [Está em falta um certificado no dispositivo que, geralmente, vem instalado no telemóvel](#your-device-is-missing-a-certificate-that-usually-comes-installed-on-your-phone), não há problema. A mensagem e o certificado em causa são diferentes destes, pelo que pode avançar e seguir os passos nesta secção para obter o certificado em falta.

Para resolver este problema e obter o certificado necessário, tem de seguir dois passos principais:

- Identificar o certificado em falta ao procurar num PC da escola ou empresa.
- Utilizar o dispositivo para transferir o certificado em falta na Internet.

### Identificar o certificado em falta ao procurar num PC da escola ou empresa

1. Num PC, abra o Internet Explorer. Se não tiver um PC para utilizar para esta finalidade, contacte o administrador de TI. Para encontrar as informações de contacto dele, verifique o [Web site do Portal da Empresa](http://portal.manage.microsoft.com).

2. Aceda ao [Web site do Portal da Empresa](http://portal.manage.microsoft.com) e inicie sessão com as credenciais profissionais ou escolares.

3. Na extremidade mais à direita da barra de endereço do browser, clique no símbolo semelhante a um cadeado, conforme mostrado abaixo. Se não vir o símbolo de cadeado, pare e contacte o administrador de TI. O cadeado significa que tem sessão iniciada em segurança, pelo que só deve avançar se ver este símbolo.

    ![screenshot-internet-explorer-address-bar-padlock-symbol](./media/andr-missing-cert-ie-padlock-symbol.png)

4. Clique em **Ver certificados**.

    ![screenshot-internet-explorer-view-certificates-button-on-website-identification-dialog](./media/andr-missg-cert-ie-view-cert-button.png)

5. Na caixa de diálogo **Certificado**, clique no separador **Caminho do certificado** e identifique o certificado que tem de obter a partir da Internet. O nome do certificado necessário estará na mesma posição que aquele que está realçado na captura de ecrã de exemplo anterior.

### Transferir e instalar o certificado em falta no dispositivo móvel Android

1. Num motor de busca como o Bing ou o Google, procure o nome do certificado em falta que identificou na secção anterior. O certificado pode terminar com diferentes "extensões," como ".crt", “.pem", etc.

2. Transfira o certificado de raiz do Web site.

3. Depois de transferido o certificado, arraste desde a parte superior do dispositivo para baixo para abrir as notificações e toque no nome do certificado na lista de notificações.

4. Na caixa de diálogo **Nomear o Certificado**, aceite o nome predefinido do certificado.

5. Certifique-se de que a **Utilização da Credencial** está definida como **Utilizada para VPN e aplicações** e, em seguida, toque em **OK**.

    ![screenshot-certificate-name-dialog-showing-certificate-name](./media/andr-missing-cert-cert-name.png)

6. Feche a aplicação do Portal da Empresa.

7. Reabra a aplicação do Portal da Empresa. Agora deverá conseguir iniciar sessão na aplicação do Portal da Empresa. Se precisar de ajuda, contacte o administrador de TI.

Se vir a mesma mensagem que diz "certificado em falta", como mostrado acima, e já tiver seguido os passos anteriores, significa que, provavelmente, ainda há outro certificado que o seu administrador de TI o vai ter de ajudar a instalar. Contacte o administrador de TI e dê-lhe esta [ligação](/intune/troubleshoot/troubleshoot-device-enrollment-in-intune#android-certificate-issues), que contém os passos para ajudar a resolver o problema.





<!--HONumber=Aug16_HO5-->


