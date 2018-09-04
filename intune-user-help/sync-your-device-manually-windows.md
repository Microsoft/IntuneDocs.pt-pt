---
title: Sincronizar o seu dispositivo Windows manualmente | Documentos da Microsoft
description: ''
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 07/24/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
searchScope:
- User help
ROBOTS: ''
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 0a8a9de8d09c71fdf49b7565f1dd4a3114ef0c46
ms.sourcegitcommit: 490365fb8b5405f323b4358fb1ec9dfdd9ff2d58
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/29/2018
ms.locfileid: "43150570"
---
# <a name="sync-your-windows-device-manually"></a>Sincronizar o seu dispositivo Windows manualmente

Quando a velocidade de instalação da aplicação estiver abaixo do ideal, inicie a sincronização manual do dispositivo. A sincronização manual força o seu dispositivo a ligar-se ao Intune para obter as comunicações e atualizações mais recentes. A velocidade de instalação pode aumentar após a sincronização do dispositivo estar concluída.

O Intune suporta a sincronização manual a partir da aplicação Portal da Empresa, da barra de tarefas do ambiente de trabalho ou do Menu Iniciar e da aplicação Definições do dispositivo. 

A funcionalidade da aplicação Portal da Empresa é suportada em dispositivos com o Windows 10 a executar a Atualização para Criativos (1703) ou superior. 
* [Sincronizar a partir da aplicação Portal da Empresa](#Sync-from-Company-Portal-app-for-Windows)  

Todos os dispositivos Windows podem ser sincronizados a partir da aplicação Definições do dispositivo, incluindo:

* [Computadores com o Windows 10](#windows-10-desktop)  
* [Microsoft HoloLens](#microsoft-hololens)   
* [Windows 10 Mobile](#windows-10-mobile)  
* [Windows Phone 8.1](#windows-phone-81)    

## <a name="sync-directly-from-company-portal-app-for-windows"></a>Sincronizar diretamente a partir da aplicação Portal da Empresa para Windows
Conclua estes passos para sincronizar manualmente qualquer dispositivo com o Windows 10 e executar a Atualização para Criativos (versão 1703) ou superior.

1.  Abra a aplicação Portal da Empresa no dispositivo.

2.  Selecione **Definições** > **Sincronizar**.

    ![Captura de ecrã da home page da aplicação Portal da Empresa, com a opção Definições realçada](./media/RS1_homePage_settings_04.png)  
    
    ![Captura de ecrã da página de definições da aplicação Portal da Empresa, com o botão Sincronizar realçado](./media/RS1_settingspage_sync05.png)  

## <a name="sync-from-device-taskbar-or-start-menu"></a>Sincronizar a partir da barra de tarefas do dispositivo ou do menu Iniciar   

Também pode aceder ao controlo de sincronização fora da aplicação, a partir do ambiente de trabalho do dispositivo. Este procedimento será útil se tiver a aplicação afixada diretamente na barra de tarefas ou no menu Iniciar e quiser sincronizar rapidamente.  

1. Localize o ícone da aplicação Portal da Empresa na barra de tarefas ou no menu Iniciar.  
2. Clique com o botão direito do rato no ícone da aplicação para que seja apresentado o menu (também denominado lista de atalhos).  

    ![Captura de ecrã a mostrar a barra de tarefas do Windows no ambiente de trabalho de um dispositivo. Clicou-se no ícone da aplicação Portal da Empresa para mostrar um menu com as opções “Afixar na barra de tarefas”, “Fechar janela” e “Sincronizar este dispositivo”.](./media/sync-device-from-start-menu-1807.png)  

3. Selecione **Sincronizar este dispositivo**. A aplicação Portal da Empresa é aberta na página **Definições** e inicia a sincronização.  

## <a name="sync-from-settings-app"></a>Sincronizar a partir da Aplicação Definições 
Conclua estes passos para sincronizar manualmente os seus dispositivos Microsoft HoloLens, Windows 10, Windows 10 Mobile ou Windows Phone 8.1 a partir da aplicação Definições.  

### <a name="windows-10-desktop"></a>Computadores com o Windows 10
1. No seu dispositivo, selecione **Iniciar** > **Definições**.

2. Selecione **Contas**.

    ![Selecionar Contas na página Definições](./media/win10pc-sync-2-settings-accounts.png)  

3. Existem múltiplas versões do Windows 10 para computador. Compare o seu ecrã com as capturas de ecrã abaixo para determinar que passos deve seguir. 

    * Se o seu ecrã disser **Aceder a profiss./ escolar**, avance para os passos em [Acesso profissional ou escolar](#access-work-or-school).

    ![A opção Aceder a profiss./ escolar na aplicação Definições](./media/w10-enroll-rs1-connect-to-work-or-school.png)  

    * Se o seu ecrã disser **Acesso a trabalho**, avance para os passos em [Acesso a trabalho](#work-access).  

    ![Selecionar o acesso de trabalho como tipo de conta](./media/win10pc-sync-3-work-access.png)

#### <a name="access-work-or-school-steps"></a>Passos para o acesso profissional ou escolar

1. Clique em **Aceder a profiss./ escolar**.

    ![Captura de ecrã a mostrar a opção Aceder a profiss./ escolar](./media/w10-enroll-rs1-connect-to-work-or-school.png)  

2. Selecione a conta que tem um ícone de mala. Se não vir esta conta, a sua empresa pode ter configurado as suas definições de uma forma diferente. Em alternativa, clique na conta que tem o logótipo da Microsoft.

     ![Selecione o nome da sua conta junto à pasta ou ao logótipo da Microsoft](./media/win10pc-rs1-sync-info-button.png)

3. Clique em **Informações**. 

4. Clique em **Sincronizar**. 

#### <a name="work-access-steps"></a>Passos para o acesso profissional

1.  Clique em **Acesso a trabalho**.

    ![Selecionar o acesso de trabalho como tipo de conta](./media/win10pc-sync-3-work-access.png)

2. Em **Inscrever-se na gestão de dispositivos**, selecione o nome da sua empresa.

    ![Selecionar o nome da empresa para a gestão de dispositivos](./media/win10pc-sync-4-tap-com-name.png)

3. Clique em **Sincronizar**. O botão permanece desativado até a sincronização estar concluída.

    ![Selecionar o botão sincronizar](./media/win10pc-sync-5-tap-sync.png)  


### <a name="windows-10-mobile"></a>Windows 10 Mobile

   1. No seu dispositivo, aceda a **Todas as aplicações** > **Definições** > **Contas**.

       ![Selecionar Contas no ecrã Definições](./media/win10m-sync-1-settings-accounts.png)

   2. Selecione **Acesso a trabalho**.

       ![Selecionar o acesso de trabalho como tipo de conta](./media/win10m-sync-2-work-access.png)

   3. Em **Inscrever-se na gestão de dispositivos**, selecione o nome da sua empresa.

       ![Selecionar o nome da empresa para a gestão de dispositivos](./media/win10m-sync-3-tap-comp-name.png)

   4. Selecione o ícone **Sincronizar**. O botão permanece desativado até a sincronização estar concluída.

       ![Selecionar o ícone Sincronizar](./media/win10m-sync-4-tap-sync.png)  
### <a name="microsoft-hololens"></a>Microsoft HoloLens  
Estas instruções aplicam-se a dispositivos HoloLens a executar a Atualização de Aniversário do Windows 10 (também conhecido como RS1). 
1.  Abra a aplicação Definições no seu dispositivo.  

2.  Selecione **Contas** > **Acesso a Trabalho**.  
    ![Captura de ecrã da aplicação Definições do HoloLens com a ligação Contas realçada](./media/RS1_holoLens_SettingsRS1_Accounts_06.png)  

3.  Selecione a sua conta ligada > **Sincronizar**. ![Captura de ecrã da aplicação Definições do HoloLens com o botão Sincronizar realçado](./media/RS1_holoLens_SyncRS1_Sync_08.png)  

### <a name="windows-phone-81"></a>Windows Phone 8.1

1. Aceda a **Todas as aplicações** > **Definições** > **área de trabalho**.

    ![Lista de definições](./media/wp81-1-sync-settings-workplace.png)

2. Selecione o nome da sua empresa.

    ![Selecionar o nome da empresa para a conta de área de trabalho](./media/wp81-2-sync-tap-compname.png)

3. Selecione o ícone **Sincronizar**.

    ![Selecionar o ícone Sincronizar](./media/wp81-3-sync-tap-sync-button.png)

Ainda precisa de ajuda? Contacte o suporte da empresa. Para encontrar as informações de contacto dele, verifique o [site do Portal da Empresa](https://go.microsoft.com/fwlink/?linkid=2010980).
