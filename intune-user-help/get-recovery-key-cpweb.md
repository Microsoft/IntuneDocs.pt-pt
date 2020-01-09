---
title: Obter uma chave de recuperação para um dispositivo macOS do site Portal da Empresa do Intune
description: Exiba a chave de recuperação para um dispositivo macOS gerenciado e registrado.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 12/04/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: ''
searchScope:
- User help
ROBOTS: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 44026c379a763db2cc43912e4ef09ae542fbe7db
ms.sourcegitcommit: 8d7406b75ef0d75cc2ed03b1a5e5f74ff10b98c0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/03/2020
ms.locfileid: "75654005"
---
# <a name="get-a-recovery-key-for-a-macos-device"></a>Obter uma chave de recuperação para um dispositivo macOS

Use o site Portal da Empresa para obter uma chave de recuperação para seu dispositivo macOS bloqueado. Se você esquecer a senha do dispositivo, poderá entrar no Portal da Empresa de outro dispositivo para recuperar a chave.  

## <a name="get-recovery-key-from-company-portal-website"></a>Obter chave de recuperação do site Portal da Empresa

Essa opção está disponível para dispositivos que foram criptografados por sua organização usando o FileVault. Ele não está disponível para dispositivos que você criptografou pessoalmente.

1. Em qualquer dispositivo, entre no site do [portal da empresa](https://portal.manage.microsoft.com) e selecione o botão de **menu** > **dispositivos**.  
2. Selecione o dispositivo macOS criptografado.  
3. Selecione **obter chave de recuperação**.  

    ![Captura de tela do site Portal da Empresa, realçando obter a seção chave de recuperação.](./media/1907-recovery2-cpweb-intune.PNG)  

4. Sua chave de recuperação será exibida.

    ![Captura de tela de Portal da Empresa site, mostrando a chave de recuperação.](./media/1907-recovery-cpweb-intune.PNG)  

    Por motivos de segurança, a chave desaparecerá após cinco minutos. Para ver a chave novamente, selecione **obter chave de recuperação**.

Se uma chave não for encontrada, mas seu dispositivo estiver criptografado corretamente, entre em contato com o pessoal de suporte da sua organização. Para encontrar as informações de contacto dele, verifique o [Web site do Portal da Empresa](https://go.microsoft.com/fwlink/?linkid=2010980).  

## <a name="get-recovery-key-from-company-portal-app-for-ios"></a>Obter chave de recuperação do aplicativo Portal da Empresa para iOS

Você pode recuperar sua chave de recuperação pessoal (FileVault Key) usando o aplicativo Portal da Empresa para iOS. O dispositivo que tem a chave de recuperação pessoal deve ser registrado com o Intune e criptografado com o FileVault por meio do Intune. Essa opção não está disponível para dispositivos que você criptografou pessoalmente. 

Usando o aplicativo Portal da Empresa, você pode abrir o modo de exibição da Web do Safari e recuperar sua chave de recuperação pessoal. 

1. Abra Portal da Empresa.
2. Clique em **obter chave de recuperação**.

    ![Captura de tela do aplicativo Portal da Empresa para iOS, mostrando a chave de recuperação](./media/get-recovery-key-cpweb-02.png)  

O site Portal da Empresa é aberto no Safari Web View e exibe a chave. 

## <a name="it-pro-support"></a>Suporte profissional de ti

Se você for uma pessoa de suporte de ti e quiser configurar e gerenciar a criptografia FileVault para dispositivos macOS, consulte [usar a criptografia de dispositivo com o Intune](/intune/protect/encrypt-devices).

## <a name="next-steps"></a>Próximos passos

Descubra o que mais você pode fazer no site Portal da Empresa. Consulte [usando o site Portal da empresa do Intune](using-the-intune-company-portal-website.md) para obter a lista de ações.  

Ainda precisa de ajuda? Entre em contato com seu profissional de suporte de ti. Para encontrar as informações de contacto dele, verifique o [Web site do Portal da Empresa](https://go.microsoft.com/fwlink/?linkid=2010980).  
