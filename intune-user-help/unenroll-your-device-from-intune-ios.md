---
title: Remover o seu dispositivo iOS do Intune | Microsoft Docs
description: Descreve como remover um dispositivo iOS do Intune
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 28914db1-3e62-45f5-9632-b0d2a808a44d
searchScope:
- User help
ROBOTS: ''
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 2df474e8b0a5af2ac294715135804ef0713a3015
ms.sourcegitcommit: 7f46e9990797bdfa669ccba2077721f1bc70c07e
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/04/2018
---
# <a name="remove-your-ios-device-from-intune"></a>Remover o seu dispositivo iOS do Intune

Quando remover o seu dispositivo iOS do Intune, este deixará de poder aceder a recursos da empresa e deixará de ser gerido pelo Intune.


## <a name="removing-the-device-from-my-devices"></a>Remover o dispositivo de Os Meus Dispositivos

Para remover o seu dispositivo do Intune, utilize estes passos ou veja este vídeo:


1.  Na aplicação Portal da Empresa, toque em **Dispositivos** e selecione o dispositivo cuja inscrição pretende anular. Se só tiver um dispositivo, quando tocar em **Dispositivos**, irá diretamente para o ecrã de detalhes do dispositivo.

2.  Junto a **MUDAR O NOME**, toque no botão de reticências > **Remover Dispositivo** > **Remover**.  

    |![Captura do ecrã Dispositivos da aplicação Portal da Empresa, a mostrar opções após o utilizador clicar em Remover. Mostra o botão "Remover Dispositivos", o botão "Reposição de Dados de Fábrica" e o botão "Cancelar".](/intune-user-help/media/cp_ios_unenroll_after_1804_001.png)|

    |![Captura do ecrã Dispositivos da aplicação Portal da Empresa, a mostrar opções após o utilizador clicar em Remover Dispositivo. Mostra o botão "Remover" realçado a vermelho e os botões "Saiba Mais" e "Cancelar" realçados a azul.](/intune-user-help/media/cp_ios_unenroll_after_1804_002.png)|


  Quando anular a inscrição do dispositivo no Intune, eis o que acontece:

  -   O seu dispositivo deixará de ser apresentado no Portal da Empresa.

  -   Deixará de poder instalar aplicações a partir do Portal da Empresa.

  -   As definições alteradas no seu dispositivo quando o adicionou (por exemplo, a desativação da câmara ou o comprimento necessário específico de uma palavra-passe) deixam de ser aplicáveis.

  -   É possível que deixe de ter acesso a alguns recursos da empresa, como partilhas de ficheiros ou sites internos, no seu dispositivo.

  -   Deixará de poder utilizar aplicações e dados da empresa no seu dispositivo.

  -   É possível que deixe de conseguir ligar-se à rede da sua empresa através de Wi-Fi ou de uma rede privada virtual (VPN).

  -   Os perfis de e-mail da empresa são removidos do dispositivo.

  -   Os dispositivos configurados apenas para e-mail não serão apresentados na aplicação Portal da Empresa ou no site.

## <a name="removing-data-collected-by-the-company-portal-app"></a>Remover dados recolhidos pela aplicação Portal da Empresa

Existem três locais onde o Portal da Empresa armazena dados locais no seu dispositivo.

-   **Registos de informações**: os dados de atividade de aplicações padrão que a Microsoft recolhe, tal como durante quanto tempo a aplicação esteve aberta ou se falhou, são apagados automaticamente quando remove o dispositivo do Portal da Empresa.

-   **Análise da Apple**: dados de atividade de falhas de aplicações padrão que a Apple recolhe. Estas informações só podem ser removidas ao repor o seu dispositivo para as definições de fábrica. Esta ação irá apagar todas as informações pessoais no seu dispositivo. Para o fazer, abra **Definições** > **Geral** > **Repor** > **Apagar Todos os Conteúdos e Definições**.

-   **Keychain**: o seu dispositivo armazena as suas palavras-passe e outras informações utilizadas para inícios de sessão no Keychain. As aplicações da Microsoft partilham as suas informações de início de sessão em aplicações desenvolvidas pela Microsoft que tem no seu dispositivo, incluindo o Microsoft Outlook e o Microsoft Authenticator. Tal como a Análise da Apple, estas informações só podem ser removidas ao repor o seu dispositivo para as definições de fábrica. Esta ação irá apagar todas as informações pessoais no seu dispositivo. Para o fazer, abra **Definições** > **Geral** > **Repor** > **Apagar Todos os Conteúdos e Definições**.


Ainda precisa de ajuda? Contacte o suporte da empresa. Para encontrar as informações de contacto dele, verifique o [site do Portal da Empresa](https://portal.manage.microsoft.com#HelpDeskDialog).
