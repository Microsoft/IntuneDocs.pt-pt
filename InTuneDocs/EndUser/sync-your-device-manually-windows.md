---
title: Sincronizar o seu dispositivo Windows manualmente | Microsoft Intune
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 10/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 443c6de7-5187-4dc4-b844-6085a0c659bd
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: priyar
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9ddbcde20fac83289c4622f69538ff00fa0cb65b
ms.openlocfilehash: 2fad0ea18485290a513d175fecf0a4947786e5eb


---


# <a name="sync-your-windows-device-manually"></a>Sincronizar o seu dispositivo Windows manualmente
Caso a instalação da sua aplicação esteja a demorar muito tempo, pode tentar sincronizar manualmente o seu dispositivo Windows. A sincronização manual poderá ajudar a acelerar a instalação.

Apenas as seguintes versões são suportadas. Se o seu dispositivo não estiver na lista, a sincronização não é suportada. Utilize as instruções que correspondem ao tipo de dispositivo que tem.

* [Windows 10 Mobile](#windows-10-mobile)
* [Windows 10 Desktop](#windows-10-desktop)
* [Windows Phone 8.1](#windows-phone-8-1)


## <a name="windows-10-mobile"></a>Windows 10 Mobile
Para sincronizar manualmente o seu dispositivo Windows 10 Mobile para acelerar uma instalação de aplicações lenta:

1. Aceda a **Todas as aplicações** > **Definições** > **Contas**.

    ![Selecionar Contas no ecrã Definições](./media/win10m-sync-1-settings-accounts.png)

2. Selecione **Acesso de trabalho**.

    ![Selecionar o acesso de trabalho como tipo de conta](./media/win10m-sync-2-work-access.png)

3. Em **Inscrever na gestão de dispositivos**, selecione o nome da sua empresa.

    ![Selecionar o nome da empresa para a gestão de dispositivos](./media/win10m-sync-3-tap-comp-name.png)

4. Selecione o ícone **Sincronizar**.

    ![Selecionar o ícone Sincronizar](./media/win10m-sync-4-tap-sync.png)

    É apresentada a mensagem "Estamos a sincronizar a sua conta" na parte superior do ecrã. O botão **Sincronizar** aparece a cinzento até que seja concluída a sincronização do dispositivo.

## <a name="windows-10-desktop"></a>Windows 10 Desktop
Existe mais do que uma versão do Windows 10, pelo que existem dois conjuntos de passos. Para saber que passos que deve utilizar, observe as capturas de ecrã e, em seguida, siga os passos que se parecem com o que vê no seu dispositivo. 

1. Selecione o botão **Iniciar** e, em seguida, selecione **Definições**.

    ![O botão Iniciar](./media/win10pc-sync-1-start-button.png)

2. Na página **Definições**, selecione **Contas**.

    ![Selecionar Contas no ecrã Definições](./media/win10pc-sync-2-settings-accounts.png)

3. Observe os dois ecrãs seguintes e veja qual deles se parece com o que vê no seu dispositivo. Siga os passos que acompanham o ecrã que aparece no seu dispositivo.

    Se vir este ecrã, que mostra "Acesso profissional ou escolar", siga as instruções em [Passos a seguir se vir Acesso profissional ou escolar](#steps-to-follow-if-you-see-access-work-or-school).

    ![Passos de sincronização a seguir se vir Acesso profissional ou escolar](./media/w10-enroll-rs1-connect-to-work-or-school.png)

    Se vir este ecrã, que mostra "Acesso de trabalho", siga os passos em [Passos a seguir se vir Acesso profissional ou escolar](#steps-to-follow-if-you-see-your-account).

    ![Selecionar o acesso de trabalho como tipo de conta](./media/win10pc-sync-3-work-access.png) 

### <a name="steps-to-follow-if-you-see-access-work-or-school"></a>Passos a seguir se vir Acesso profissional ou escolar

1. Na página **Contas**, selecione **Acesso profissional ou escolar**.

    ![Selecionar Acesso profissional ou escolar](./media/w10-enroll-rs1-connect-to-work-or-school.png)

2. Selecione a sua conta escolar ou profissional. Dependendo da configuração que o administrador de TI efetuou, poderá ver duas contas com aspeto semelhante ao exemplo mostrado abaixo. Uma conta tem uma pasta junto à mesma, e a outra conta tem o logótipo da Microsoft. 

    - Se vir a conta com a pasta, selecione-a e procure o botão **Informações** sob a mesma. 
    - Se vir apenas a conta com o logótipo da Microsoft, selecione a conta e procure o botão **Informações** sob a mesma.

    ![Selecione o nome da sua conta junto à pasta ou ao logótipo da Microsoft](./media/win10pc-rs1-sync-info-button.png)

3. Selecione o botão **Informações**. É aberta uma caixa de diálogo semelhante à do exemplo abaixo.

    ![Selecione o nome da sua conta junto à pasta ou ao logótipo da Microsoft](./media/win10pc-rs1-sync-button.png)

4. Selecione o botão**Sincronizar**. O seu dispositivo será sincronizado com o Intune.

### <a name="steps-to-follow-if-you-see-work-access"></a>Passos a seguir se vir Acesso de trabalho
    
1. Na página **Contas**, selecione **Acesso de trabalho**.

    ![Selecionar o acesso de trabalho como tipo de conta](./media/win10pc-sync-3-work-access.png)

2. Na secção **Inscrever na gestão de dispositivos**, selecione o nome da sua empresa.

    ![Selecionar o nome da empresa para a gestão de dispositivos](./media/win10pc-sync-4-tap-com-name.png)

3. Selecione o botão**Sincronizar**.

    ![Selecionar o botão sincronizar](./media/win10pc-sync-5-tap-sync.png)

   O botão fica a cinzento até a sincronização estar concluída.

## <a name="windows-phone-81"></a>Windows Phone 8.1
Para sincronizar manualmente o seu dispositivo Windows Phone 8.1 para acelerar uma instalação de aplicações lenta:

1. Aceda a **Todas as aplicações** > **Definições** > **área de trabalho**.

    ![Lista de definições](./media/wp81-1-sync-settings-workplace.png)

2. Selecione o nome da sua empresa.

    ![Selecionar o nome da empresa para a conta de área de trabalho](./media/wp81-2-sync-tap-compname.png)

3. Selecione o ícone **Sincronizar**.

    ![Selecionar o ícone Sincronizar](./media/wp81-3-sync-tap-sync-button.png)

   É apresentada a mensagem "Estamos a sincronizar a sua conta" na parte superior do ecrã até que seja concluída a sincronização do dispositivo.

Ainda precisa de ajuda? Contacte o administrador de TI. Para encontrar as informações de contacto dele, verifique o [site do Portal da Empresa](http://portal.manage.microsoft.com).



<!--HONumber=Nov16_HO1-->


