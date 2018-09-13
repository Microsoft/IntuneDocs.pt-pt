---
title: Definições de quiosque para Android no Microsoft Intune – Azure | Microsoft Docs
description: Configure os seus dispositivos de quiosque do Android como quiosques de uma aplicação e de várias aplicações.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 7/5/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: cef98527ee2c281547f8046f3c6f08275d8f0807
ms.sourcegitcommit: e814cfbbefe818be3254ef6f859a7bf5f5b99123
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/31/2018
ms.locfileid: "43329388"
---
# <a name="kiosk-settings-for-android-devices-in-intune"></a>Definições de quiosque para dispositivos Android no Intune

Pode configurar um dispositivo no modo de quiosque de uma aplicação ou de várias aplicações com as definições de configuração do dispositivo. Quando um dispositivo estiver no modo de quiosque, a utilização do dispositivo será limitada às aplicações ou ligações Web definidas pelo perfil de restrição. 

## <a name="restrict-an-android-kiosk-device-to-a-single-app"></a>Restringir um dispositivo de quiosque do Android a uma aplicação

Se o perfil de restrição de um dispositivo de quiosque estiver definido como **Modo de quiosque** = **quiosque de uma aplicação**, os utilizadores só poderão aceder a uma aplicação. Quando um dispositivo configurado neste modo é iniciado, a aplicação específica também é iniciada. Os utilizadores não podem abrir novas aplicações ou mudar a aplicação em execução.

1. Certifique-se de que a aplicação que pretende que seja utilizada no dispositivo de quiosque foi [implementada no dispositivo](apps-deploy.md) e de que atribuiu a aplicação ao grupo de dispositivos que criou para os seus dispositivos de quiosque.
2. Aceda ao [portal do Intune](https://portal.azure.com) e selecione **Configuração do dispositivo** > **Perfis** > **Criar perfil**.
3. No painel **Criar perfil**, defina os seguintes campos:
     - **Nome**
     - **Plataforma**: Android Enterprise
     - **Tipo de perfil**: Proprietário do dispositivo apenas > Restrições do dispositivo
4. Selecione **Definições** > **Quiosque**.
5. Para **Modo de quiosque**, selecione **Quiosque de uma aplicação**.
6. Escolha **Selecione uma aplicação gerida** e, em seguida, selecione a aplicação gerida Google Play que pretende que seja a única aplicação disponível para dispositivos com este perfil.
7. Selecione **OK** > **OK** > **OK** > **Criar**.
8. Selecione o perfil que acabou de criar > **Atribuições**.
9. Em **Atribuir a**, selecione **Grupos selecionados**.
10. Escolha **Selecionar grupos para incluir** > selecione o grupo de dispositivos que criou para os seus dispositivos de quiosque > **Selecionar**.

## <a name="restrict-a-kiosk-device-to-a-set-of-apps-or-web-links"></a>Restringir um dispositivo de quiosque a um conjunto de aplicações ou ligações Web

Se o perfil de restrição de um dispositivo de quiosque estiver definido como **Modo de quiosque** = **quiosque de várias aplicações**, os utilizadores só poderão aceder ao número limitado de aplicações que configurar. Também pode definir um conjunto de ligações Web que os utilizadores podem visitar. Quando a política é aplicada, os utilizadores veem os ícones das aplicações permitidas no ecrã principal.

Para definir um dispositivo de quiosque do Android para múltiplas aplicações, siga estes passos principais:

1. [Importar e implementar a aplicação Ecrã Inicial Gerido a partir do Google Play gerido](#import-and -deploy-the-managed-home-screen-app)
2. [Adicionar e atribuir aplicações que podem ser utilizadas no modo de quiosque](#add-and-assign-apps-that-can-be-used-in-kiosk-mode)
3. (Opcional) [Adicionar ligações Web que podem ser utilizadas no modo de quiosque](#add-web-links-that-can-be-used-in-kiosk-mode)

### <a name="import-and-deply-the-managed-home-screen-app"></a>Importar e implementar a aplicação Ecrã Inicial Gerido

1. Navegue até à [página Ecrã Inicial Gerido no Google Play](https://play.google.com/work/apps/details?id=com.microsoft.launcher.enterprise) e inicie sessão com a mesma conta que utiliza para outras aplicações geridas do Google Play.
2. Selecione **Aprovar**.
3. Aceda ao [portal do Intune](https://portal.azure.com) e selecione **Aplicações do cliente** > **Google Play Gerida** > **Sincronizar**.
4. Selecione **Aplicações**  > **Ecrã Inicial Gerido** > **Atribuições** > **Adicionar grupo**.
5. Em **Tipo de atribuição**, selecione **Necessário**.
6. Selecione **Grupos incluídos** > **Selecionar grupos para incluir** > selecione o grupo de dispositivos que criou para os seus dispositivos de quiosque > **Selecionar** > **OK** > **OK** > **Guardar**.

### <a name="add-and-assign-apps-that-can-be-used-in-kiosk-mode"></a>Adicionar e atribuir aplicações que podem ser utilizadas no modo de quiosque

Para cada aplicação que pretende disponibilizar nos dispositivos de quiosque, siga estes passos:

1. [Adicione a aplicação ao Intune](store-apps-android.md).
2. Selecione **Aplicações do cliente** > **Aplicações** > selecione a aplicação > **Atribuições** > **Adicionar grupo**.
3. Em **Tipo de atribuição**, selecione **Necessário**.
4. Selecione **Grupos incluídos** > **Selecionar grupos para incluir** > selecione o grupo de dispositivos que criou para os seus dispositivos de quiosque > **Selecionar** > **OK** > **OK** > **Guardar**.

### <a name="add-web-links-that-can-be-used-in-kiosk-mode"></a>Adicionar ligações Web que podem ser utilizadas no modo de quiosque

1. Aceda ao [portal do Intune](https://portal.azure.com) e selecione **Aplicações do cliente** > **Aplicações** > **Adicionar**.
2. Em **Tipo de aplicação**, selecione **Ligação Web**.
3. Selecione **Configurar** e forneça as informações necessárias. Não precisa de adicionar uma imagem de logótipo porque será obtida automaticamente do favicon.ico do site.
4. Selecione **OK** > **Adicionar**.

Certifique-se de que implementou uma aplicação de browser para os dispositivos de quiosque com as [Aplicações Móveis](apps-add.md).

### <a name="create-a-multi-app-kiosk-profile"></a>Criar um perfil de quiosque de várias aplicações

1. Aceda ao [portal do Intune](https://portal.azure.com) e selecione **Configuração do dispositivo** > **Perfis** > **Criar perfil**.
3. No painel **Criar perfil**, defina os seguintes campos:
     - **Nome**: escreva um nome intuitivo
     - **Plataforma**: Android Enterprise
     - **Tipo de perfil**: Proprietário do dispositivo apenas > Restrições do dispositivo
4. Selecione **Definições** > **Quiosque**.
5. Para **Modo de quiosque**, selecione **Quiosque de várias aplicações**.
6. Selecione **Adicionar** e, em seguida, selecione as aplicações ou ligações Web que pretende disponibilizar para dispositivos com este perfil.
7. Selecione **OK** > **OK** > **OK** > **Criar**.
8. Selecione o perfil que acabou de criar > **Atribuições**.
9. Em **Atribuir a**, selecione **Grupos selecionados**.
10. Escolha **Selecionar grupos para incluir** > selecione o grupo de dispositivos que criou para os seus dispositivos de quiosque > **Selecionar** > **Guardar**.

## <a name="next-steps"></a>Passos seguintes
[Atribua o perfil](device-profile-assign.md) e [monitorize o respetivo estado](device-profile-monitor.md).
