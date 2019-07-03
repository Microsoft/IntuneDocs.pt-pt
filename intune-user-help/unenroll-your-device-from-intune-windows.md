---
title: Remover o seu dispositivo Windows da gestão do Intune
description: Descreve como remover um dispositivo Windows da gestão do Intune
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/03/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 018bda65-7238-41f5-b92a-e5f67b7fe085
searchScope:
- User help
ROBOTS: ''
ms.reviewer: jieyang
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 68cec5d8594d832a405daa1228e77a51283a7c92
ms.sourcegitcommit: 7315fe72b7e55c5dcffc6d87f185f3c2cded9028
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/02/2019
ms.locfileid: "67529509"
---
# <a name="remove-your-windows-device-from-management"></a>Remover o seu dispositivo Windows da gestão

Remova um dispositivo Windows registado da gestão quando já não quiser ou não precisar de:  
* Utilizar o seu dispositivo no trabalho ou na escola. 
* Aceder ao e-mail, aplicações e outros recursos escolares ou profissionais.

Depois de anular o registo do dispositivo, vai perder o acesso do dispositivo aos recursos da escola ou do trabalho. Pode remover os seguintes dispositivos Windows da gestão.  
* Dispositivos com o Windows 10 
* Computadores com o Windows 8.1
* Telemóvel com o Windows 8.1
 
Para obter mais informações sobre o que acontece após remover o seu dispositivo da gestão, veja [O que acontece se remover o dispositivo do Intune](what-happens-if-you-unenroll-your-device-from-intune-windows.md).  

## <a name="remove-your-windows-10-device"></a>Remover o seu dispositivo com o Windows 10
Conclua os seguintes passos para remover um dispositivo com o Windows 10 da gestão.

### <a name="remove-in-company-portal-app-home-page"></a>Remover na aplicação Portal da Empresa, **home page**  

1. Abra a aplicação Portal da Empresa.
2. Na **Home page**, aceda à secção **My Devices** (Os Meus Dispositivos).
3. Selecione o dispositivo que pretende remover.
3. No canto superior direito da aplicação, selecione o ícone **Ver mais**.
4. Selecione **Remover**. 
5. Para confirmar a remoção do dispositivo, selecione **Remove** (Remover).  

### <a name="remove-in-company-portal-app-device-context-menu"></a>Remover na aplicação Portal da Empresa, menu de contexto do dispositivo  

1. Abra a aplicação Portal da Empresa e aceda a **My Devices** (Os Meus Dispositivos).

    ![Captura de ecrã de exemplo da aplicação Portal da Empresa para Windows, home page, com destaque da secção My Devices (Os Meus Dispositivos).](./media/1809_CheckAccess_Context_Select_Device.png)

2. Clique com o botão direito do rato ou mantenha premido qualquer dispositivo para abrir o respetivo [menu de contexto](https://docs.microsoft.com//windows/uwp/design/controls-and-patterns/menus).  

3. Selecione **Remover**.  

    ![Captura de ecrã de exemplo da aplicação Portal da Empresa para Windows, home page. O menu de contexto do dispositivo está visível na secção **My Devices** (Os Meus Dispositivos) da página e mostra as ações "Rename" (Mudar o nome), "Remove" (Remover) e "Check access" (Verificar acesso).](./media/1809_DeviceContextMenu_Windows_CP.png)  

5. Na confirmação, clique em **Learn More** (Saber Mais) para saber como o acesso aos recursos da escola ou do trabalho pode ser alterado. Para confirmar a remoção do dispositivo, selecione **Remove** (Remover).   

     ![Captura de ecrã de exemplo da aplicação Portal da Empresa para Windows, home page. O campo Rename (Mudar o nome) aparece sobre o dispositivo onde o utilizador pode escrever um novo nome e clicar em Rename (Mudar o nome) ou Cancel (Cancelar).](./media/1808_RemoveDevice_Popup.png)  


### <a name="remove-in-device-settings-app"></a>Remover na aplicação Definições do dispositivo
1. Abra a aplicação Definições. 
2. Vá para **Contas** > **Acesso profissional ou escolar**.
3. Selecione a conta ligada que pretende remover e, em seguida, selecione **Desligar**.
4. Para confirmar a remoção do dispositivo, selecione **Sim**.

## <a name="remove-your-windows-81-computer"></a>Remover o seu computador com o Windows 8.1
Conclua os seguintes passos para remover um computador com o Windows 8.1 do Intune.

1.  Aceda a **Definições do PC** > **Rede** > **Área de Trabalho**.
2.  Em **Associação à Área de Trabalho**, selecione **Sair**.
3.  Em **Ativar gestão de dispositivos**, selecione **Desativar**.
4.  Na janela de pop-up que é aberta, selecione **Desativar**.

## <a name="remove-your-windows-81-phone"></a>Remover o seu telemóvel com o Windows 8.1
Conclua os seguintes passos para remover um telemóvel com o Windows 8.1 do Intune.

1.  Aceda a **Definições** > **Área de Trabalho**.
2.  Toque na conta da área de trabalho cuja inscrição quer anular.
3.  Toque em **Eliminar**, na parte inferior do ecrã.
4.  Na caixa de diálogo **Eliminar conta**, toque em **Eliminar**.  
## <a name="removing-your-personal-information-after-removing-the-company-portal"></a>Remover as suas informações pessoais depois de remover o Portal da Empresa  

Existem dois tipos de dados que o Portal da Empresa armazena no seu dispositivo Windows:

- **Os registos de diagnóstico**: Dados de atividade de aplicações padrão que a Microsoft recolhe. Isto é eliminado automaticamente quando desinstala a aplicação Portal da Empresa. Os dados de atividade de aplicações são, por exemplo, dados sobre o tempo durante o qual a aplicação esteve aberta ou se a aplicação falhou.
- **Cache do aplicativo**: Suporta ficheiros que são necessários para a aplicação funcione, por exemplo, ícones e definições.

Para eliminar a cache e os registos armazenados, siga um dos seguintes passos:

* [Desinstalar a aplicação Portal da Empresa](https://support.microsoft.com/help/4028003/windows-10-uninstall-apps-and-programs) 

* Repor a aplicação Portal da Empresa. Abra a aplicação **Definições** e selecione **Aplicações** > **Portal da Empresa** > **Opções avançadas** > **Repor**. 

Ainda precisa de ajuda? Contacte o suporte da empresa. Para encontrar as informações de contacto dele, verifique o [site do Portal da Empresa](https://go.microsoft.com/fwlink/?linkid=2010980).
