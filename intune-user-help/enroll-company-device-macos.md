---
title: Inscrever um dispositivo macOS fornecido pela organização para gestão | Microsoft Docs
description: Descreve como pode inscrever um dispositivo macOS no Intune que foi adquirido e fornecido pela sua organização.
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
ms.openlocfilehash: a5808a0ac80390b76058827d2ca0870249b043b9
ms.sourcegitcommit: 11cad61c565c474a8d653181675cc1109d562626
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/29/2018
ms.locfileid: "43241835"
---
# <a name="enroll-your-organization-provided-macos-device-in-management"></a>Inscrever um dispositivo macOS fornecido pela organização para gestão

Saiba como gerir o seu novo dispositivo macOS no Intune.  

Os dispositivos que são fornecidos pela sua empresa ou escola são, muitas vezes, pré-configurados antes de os receber. A sua organização enviará estas definições pré-configuradas para o seu dispositivo depois de o ligar e iniciar sessão no mesmo pela primeira vez. Assim que a configuração do seu dispositivo terminar, terá acesso aos recursos da escola ou do trabalho. 

Para iniciar a configuração da gestão, ligue o seu dispositivo e inicie sessão com as credenciais da sua conta escolar ou profissional. O resto deste artigo descreve os passos e ecrãs que irá ver à medida que avançar no Assistente de Configuração.   

## <a name="what-is-apple-dep"></a>O que é o DEP da Apple?
A sua organização poderá ter comprado os respetivos dispositivos através de algo designado por *Programa de Registo de Aparelho da Apple* (DEP). O DEP da Apple permite que as organizações comprem grandes quantidades de dispositivos iOS ou macOS. Posteriormente, podem configurar e gerir esses dispositivos no respetivo fornecedor de gestão de dispositivos móveis preferido, como o Intune. Se for administrador e quiser obter mais informações sobre o DEP da Apple, veja [Inscrever automaticamente dispositivos iOS com o Programa de Registo de Aparelho da Apple](https://docs.microsoft.com/intune/device-enrollment-program-enroll-macos).  

## <a name="set-up-your-macos-device"></a>Configurar o dispositivo macOS  
Conclua os seguintes passos para inscrever o seu dispositivo macOS para gestão. Se estiver a utilizar o seu próprio dispositivo em vez de um dispositivo fornecido pela organização, siga os passos para [dispositivos pessoais e BYOD](enroll-your-device-in-intune-macos-cp.md).  

1. Ligue o seu dispositivo macOS. 
2. Selecione o seu **Language** (Idioma) e clique em **Continue** (Continuar).  

   ![Captura do ecrã do Assistente de Configuração de dispositivos macOS "Welcome" (Bem-vindo), a mostrar uma lista dos idiomas disponíveis para seleção.](./media/macos-dep-welcome-1808.png)   
3. Selecione um esquema de teclado. A lista apresenta uma ou várias opções consoante o idioma selecionado. Para ver todas as opções de esquema, independentemente do idioma que selecionou, clique em **Show All** (Mostrar Todos). Quando tiver terminado, clique em **Continue** (Continuar).  

   ![Captura do ecrã do Assistente de Configuração de dispositivos macOS "Setup Assistant Keyboard" (Teclado do Assistente de Configuração), a mostrar uma lista de idiomas de teclado para seleção, a opção Show All (Mostrar Todos) desselecionada e os botões Back (Retroceder) e Continue (Continuar).](./media/macos-dep-keyboard-1808.png)  
4. Selecione a sua rede Wi-Fi. Tem de ter uma ligação à Internet para prosseguir com a configuração. Se não vir a sua rede ou tiver de estabelecer ligação através de uma rede com fios, clique em **Other Network Options** (Outras Opções de Rede). Quando tiver terminado, clique em **Continue** (Continuar).  

   ![Captura do ecrã do Assistente de Configuração de dispositivos macOS "Select Your Wi-Fi Network screen" (Selecione a Sua Rede Wi-Fi), a mostrar uma lista das redes disponíveis. Também mostra os botões Other Network Options (Outras Opções de Rede), Back (Retroceder) e Continue (Continuar).](./media/macos-dep-wifi-1808.png)  
5. Assim que estiver ligado ao Wi-Fi, o ecrã **Remote Management** (Gestão Remota) será apresentado. A gestão remota permite que o administrador da sua organização configure remotamente o seu dispositivo com as contas, definições, aplicações e redes exigidas pela empresa. Antes de continuar, leia a documentação para o ajudar a compreender a forma como o seu dispositivo é gerido. Em seguida, clique em **Continue** (Continuar).  

   ![Captura do ecrã do Assistente de Configuração de dispositivos macOS "Remote Management" (Gestão Remota), com uma explicação sobre a gestão remota e uma ligação para documentação com informações adicionais. Também mostrar os botões Back (Retroceder) e Continue (Continuar).](./media/macos-dep-remote-management-1-1808.png)  
6. Quando lhe for pedido, inicie sessão com a sua conta escolar ou profissional. Após a sua autenticação, o dispositivo irá instalar um perfil de gestão. O perfil configura e permite o seu acesso aos recursos da sua organização.  
7. Leia mais sobre o ícone de dados e privacidade da Apple, para que possa identificar mais tarde quando as suas informações pessoais estiverem a ser recolhidas. Em seguida, clique em **Continue** (Continuar).  

   ![Captura do ecrã do Assistente de Configuração de dispositivos macOS "Data & Privacy" (Dados e Privacidade), a mostrar uma imagem de duas pessoas a darem um aperto de mãos e a descrever a utilização informações pessoais por parte da Apple. Também mostra os botões Back (Retroceder) e Continue (Continuar).](./media/macos-dep-apple-data-privacy-1808.png)  
8. Assim que o dispositivo estiver inscrito, poderá ter de concluir alguns passos adicionais. Os passos que lhe são apresentados dependem da forma como a sua organização personalizou a experiência de configuração. Estes passos podem pedir-lhe que:
    * Inicie sessão numa conta Apple
    * Aceite os Termos e condições
    * Crie uma conta de computador
    * Conclua uma configuração rápida
    * Configure o seu Mac  
## <a name="get-the-company-portal-app"></a>Obtenha a aplicação Portal da Empresa      
Aceda à App Store para obter a aplicação Portal da Empresa do Intune no seu dispositivo. A aplicação permite-lhe monitorizar, sincronizar, adicionar e remover o seu dispositivo da gestão, bem como instalar aplicações.

Ainda precisa de ajuda? Contacte o suporte da empresa. Para encontrar as informações de contacto dele, verifique o [site do Portal da Empresa](https://go.microsoft.com/fwlink/?linkid=2010980).
