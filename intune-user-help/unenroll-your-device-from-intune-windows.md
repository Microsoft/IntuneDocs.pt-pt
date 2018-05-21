---
title: Remover o seu dispositivo Windows do Intune
description: Descreve como remover um dispositivo Windows do Intune
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 05/08/2018
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
ms.openlocfilehash: 1dd64250c1996c6b13c62f80572282d639112ba6
ms.sourcegitcommit: 8ee543c864097dc195b6f440471dca713fc21ed2
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/09/2018
---
# <a name="remove-your-windows-device-from-intune-management"></a>Remover o seu dispositivo Windows da gestão do Intune

Remova um dispositivo Windows registado do Intune quando já não quiser ou não precisar de:  
* Utilizar o seu dispositivo no trabalho ou na escola. 
* Aceder ao e-mail, aplicações e outros recursos escolares ou profissionais.

Após ser removido, não poderá aceder aos recursos escolares ou profissionais a partir do dispositivo. Os dispositivos Windows que podem ser removidos do Intune incluem:  
* Dispositivos com o Windows 10 
* Computadores com o Windows 8.1
* Dispositivos móveis com o Windows 8.1
 
Para obter mais informações sobre o que acontece após remover o seu dispositivo da gestão do Intune, veja [O que acontece se anular a inscrição do seu dispositivo Windows no Intune](what-happens-if-you-unenroll-your-device-from-intune-windows.md).

## <a name="remove-your-windows-10-device"></a>Remover o seu dispositivo com o Windows 10
Conclua os seguintes passos para remover um dispositivo com o Windows 10 do Intune.

### <a name="via-the-company-portal-app"></a>Através da aplicação Portal da Empresa

1. Abra a aplicação Portal da Empresa.
2. Inicie sessão com as credenciais da sua conta escolar ou profissional.
3. Em **Os Meus Dispositivos**, selecione o dispositivo que pretende remover.
4. No canto superior direito da aplicação, selecione o ícone **Ver mais**.
5. Selecione **Remover**. 
6. Para confirmar a remoção do dispositivo, selecione **Remover dispositivo**.

### <a name="via-device-settings-app"></a>Através da aplicação Definições do dispositivo
1. Abra a aplicação Definições. 
2. Aceda a **Contas** > **Acesso profissional ou escolar**.
3. Selecione a conta ligada que pretende remover e, em seguida, selecione **Desligar**.
4. Para confirmar a remoção do dispositivo, selecione **Sim**.

## <a name="remove-your-windows-81-computer"></a>Remover o seu computador com o Windows 8.1
Conclua os seguintes passos para remover um computador com o Windows 8.1 do Intune.

1.  Aceda a **Definições do PC** > **Rede** > **Área de Trabalho**.
2.  Em **Associação à Área de Trabalho**, selecione **Sair**.
3.  Em **Ativar gestão de dispositivos**, selecione **Desativar**.
4.  Na janela de pop-up que é aberta, selecione **Desativar**.

## <a name="remove-your-windows-81-mobile-device"></a>Remover o seu dispositivo móvel com o Windows 8.1
Conclua os seguintes passos para remover um dispositivo móvel com o Windows 8.1 do Intune.

1.  Aceda a **Definições** > **Área de Trabalho**.
2.  Toque na conta da área de trabalho cuja inscrição quer anular.
3.  Toque em **Eliminar**, na parte inferior do ecrã.
4.  Na caixa de diálogo **Eliminar conta**, toque em **Eliminar**.  
## <a name="removing-your-personal-information-after-removing-the-company-portal"></a>Remover as suas informações pessoais depois de remover o Portal da Empresa
Existem dois tipos de dados que o Portal da Empresa armazena no seu dispositivo Windows:

-   **Registos de diagnóstico**: os dados de atividade de aplicações padrão que a Microsoft recolhe são apagados automaticamente ao remover o dispositivo do Portal da Empresa. Os dados de atividade de aplicações são, por exemplo, dados sobre o tempo durante o qual a aplicação esteve aberta ou se a aplicação falhou.
-   **Cache da aplicação**: os ficheiros de suporte que são necessários para o funcionamento da aplicação, como os ícones e as definições.

Existem alguns passos que precisa de seguir para eliminar completamente estas informações.

1. Desinstalar o Portal da Empresa. [Desinstalar a aplicação Portal da Empresa](https://support.microsoft.com/help/4028003/windows-10-uninstall-apps-and-programs) irá remover alguns dos dados de aplicações armazenados no seu dispositivo.  

2. Reponha o Portal da Empresa para repor os dados de aplicações armazenados. Abra a aplicação **Definições** e selecione **Aplicações** > **Portal da Empresa** > **Opções avançadas** > **Repor**. 

Ainda precisa de ajuda? Contacte o suporte da empresa. Para encontrar as informações de contacto dele, verifique o [site do Portal da Empresa](https://portal.manage.microsoft.com#HelpDeskDialog).