---
title: Registre seu dispositivo macOS fornecido pela organização no gerenciamento | Microsoft Docs
description: Descreve como registrar um dispositivo macOS no Intune que foi adquirido e fornecido pela sua organização.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 08/29/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
searchScope:
- User help
ROBOTS: ''
ms.reviewer: japoehlm
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9c20ad54f71eb44f69638eacd4ae1c3796771896
ms.sourcegitcommit: 45d7c76e760c5117bf134fb57f7e248e5b6c4ad5
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72314659"
---
# <a name="enroll-your-organization-provided-macos-device-in-management"></a>Registre seu dispositivo macOS fornecido pela organização no gerenciamento

Saiba como obter seu novo dispositivo macOS gerenciado no Intune.  

Os dispositivos que são fornecidos pelo seu trabalho ou escola geralmente são pré-configurados antes de você recebê-los. Sua organização enviará essas configurações pré-configuradas para seu dispositivo depois que você ativá-la e entrar pela primeira vez. Depois que o dispositivo concluir a instalação, você receberá acesso aos seus recursos corporativos ou de estudante.

Para iniciar a configuração de gerenciamento, ligue o dispositivo e entre com suas credenciais corporativas ou de estudante. O restante deste artigo descreve as etapas e telas que você verá ao percorrer o assistente de configuração.

## <a name="what-is-apple-dep"></a>O que é o Apple DEP?

Sua organização pode ter comprado seus dispositivos por meio de algo chamado DEP ( *Apple programa de registro de dispositivos* ). A Apple DEP permite que as organizações comprem grandes quantidades de dispositivos iOS ou macOS. As organizações podem configurar e gerenciar esses dispositivos em seu provedor de gerenciamento de dispositivos móveis preferido, como o Intune. Se você for um administrador e quiser mais informações sobre o DEP da Apple, consulte [registrar automaticamente dispositivos MacOS com o programa de registro de dispositivos da Apple](https://docs.microsoft.com/intune/enrollment/device-enrollment-program-enroll-macos).  

## <a name="get-your-device-managed"></a>Obter seu dispositivo gerenciado

Conclua as etapas a seguir para registrar seu dispositivo macOS no gerenciamento do. Se você estiver usando seu próprio dispositivo, em vez de um dispositivo fornecido pela organização, siga as etapas para [dispositivos pessoais e traga seu próprio](enroll-your-device-in-intune-macos-cp.md).  

1. Ligue seu dispositivo macOS.
2. Escolha seu país/região e clique em **continuar**.  

   ![Captura de tela de boas-vindas do assistente de configuração de dispositivo macOS, mostrando uma lista de idiomas dos quais selecionar.](./media/macos-dep-welcome-1808.png)
3. Escolha um layout de teclado. A lista mostra uma ou mais opções com base no país/região selecionado. Para ver todas as opções de layout, independentemente de seu país/região selecionado, clique em **Mostrar tudo**. Quando terminar, clique em **continuar.**  

   ![Captura de tela de layout de teclado do assistente de configuração de dispositivo macOS, mostrando uma lista de idiomas de teclado para seleção, uma opção Mostrar tudo desmarcada e um botão voltar e continuar.](./media/macos-dep-keyboard-1808.png)  
4. Selecione sua rede Wi-Fi. Você deve ter uma conexão com a Internet para continuar a instalação. Se você não vir sua rede ou se precisar se conectar por uma rede com fio, clique em **outras opções de rede**. Quando terminar, clique em **continuar**.  

   ![Captura de tela do assistente de configuração de dispositivo macOS selecione sua rede Wi-Fi, mostrando uma lista de redes disponíveis para escolher. Também mostra um botão de outras opções de rede, botão voltar e botão continuar.](./media/macos-dep-wifi-1808.png)  
5. Depois que você estiver conectado ao Wi-Fi, a tela **gerenciamento remoto** será exibida. O gerenciamento remoto permite que o administrador da sua organização configure remotamente seu dispositivo com contas, configurações, aplicativos e redes exigidas pela empresa. Leia a explicação do gerenciamento remoto para ajudá-lo a entender como seu dispositivo é gerenciado. Em seguida, clique em **Continuar**.  

   ![Instantâneo da tela de gerenciamento remoto do assistente de configuração de dispositivo macOS, com texto explicando o gerenciamento remoto e um link para a documentação para obter mais informações. Também mostra um botão voltar e o botão continuar.](./media/macos-dep-remote-management-1-1808.png)  
6. Quando solicitado, entre com sua conta corporativa ou de estudante. Depois que você estiver autenticado, o dispositivo instalará um perfil de gerenciamento. O perfil configura e habilita o acesso aos recursos da sua organização.  
7. Leia sobre o ícone de privacidade de & de dados da Apple para que você possa identificar posteriormente quando informações pessoais estiverem sendo coletadas. Em seguida, clique em **Continuar**.  

   ![Captura de tela dos dados do assistente de configuração de dispositivo macOS & a exibição de privacidade, mostrando uma ilustração de duas pessoas agitando as mãos e descrevendo o uso de informações pessoais da Apple. Também mostra um botão voltar e continuar.](./media/macos-dep-apple-data-privacy-1808.png)  
8. Depois que o dispositivo for registrado, você poderá ter etapas adicionais para concluir. As etapas que você vê dependem de como a sua organização personalizou a experiência de instalação. Ele pode exigir que você:
    * Entrar em uma conta da Apple
    * Concordar com os termos e condições
    * Criar uma conta de computador
    * Percorrer uma instalação expressa
    * Configurar seu Mac

## <a name="get-the-company-portal-app"></a>Obter o aplicativo Portal da Empresa

Baixe o aplicativo Portal da Empresa do Intune para macOS em seu dispositivo. O aplicativo permite que você monitore, sincronize, adicione e remova seu dispositivo do gerenciamento e instale aplicativos. Estas etapas também descrevem como registrar seu dispositivo com o Portal da Empresa.

1. Em seu dispositivo macOS, vá para [https://portal.manage.microsoft.com/EnrollmentRedirect.aspx](https://portal.manage.microsoft.com/EnrollmentRedirect.aspx).
2. Entre no site do Portal da Empresa com sua conta corporativa ou de estudante. 
3. Clique em **obter o aplicativo** para baixar o instalador do portal da empresa para MacOS.
4. Quando solicitado, abra o arquivo. pkg e conclua as etapas de instalação.
5. Abra o aplicativo Portal da Empresa e entre com sua conta corporativa ou de estudante.
6. Localize seu dispositivo e clique em **registrar**.
7. Clique em **continuar** > **concluído**. Agora, seu dispositivo deve aparecer no aplicativo Portal da Empresa como um dispositivo corporativo e compatível.

Ainda precisa de ajuda? Entre em contato com o suporte de sua empresa. Para obter informações de contato, consulte o [site Portal da empresa](https://go.microsoft.com/fwlink/?linkid=2010980).
