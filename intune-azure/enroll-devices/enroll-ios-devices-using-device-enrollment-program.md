---
title: "Inscrever dispositivos iOS – Programa de Registo de Aparelho | Pré-visualização do Azure no Intune | Documentos da Microsoft"
description: "Pré-visualização do Azure no Intune: saiba como inscrever dispositivos iOS pertencentes à empresa através do Programa de Registo de aparelho."
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 02/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7981a9c0-168e-4c54-9afd-ac51e895042c
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: adb2fd27d7f2b3f0ef4dce6b26fcb20d74b69a00
ms.openlocfilehash: 2986e659d384eaa67b64af1ce3ae48a1ac81a600


---

# <a name="enroll-ios-devices-using-device-enrollment-program"></a>Inscrever dispositivos iOS com o Programa de Registo de Aparelho

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

O Microsoft Intune pode implementar um perfil de inscrição que inscreve os dispositivos iOS comprados através do Programa de Inscrição de Dispositivos (DEP) por ondas eletromagnéticas. Um perfil contém definições de gestão que quer aplicar a dispositivos. O pacote de inscrição pode incluir opções do Assistente de Configuração do dispositivo. Os utilizadores não podem anular a inscrição de dispositivos inscritos através do DEP.

>[!NOTE]
>Este método de inscrição não pode ser utilizado com o método do [gestor de inscrição de dispositivos](enroll-devices-using-device-enrollment-manager.md).

Para gerir dispositivos iOS propriedade da empresa com o Programa de Inscrição de Dispositivos da Apple (DEP), a sua empresa tem de se associar ao DEP da Apple e de obter dispositivos através desse programa. Os detalhes desse processo estão disponíveis em: [https://deploy.apple.com](https://deploy.apple.com) Entre as vantagens do programa incluem-se a configuração automatizada de dispositivos sem utilizar um cabo USB para ligar cada dispositivo a um computador.

Para poder inscrever dispositivos iOS pertencentes à empresa no DEP, precisa de [obter um token do DEP](get-apple-dep-token.md) da Apple. Este token permite ao Intune sincronizar informações sobre os dispositivos propriedade da empresa participantes no DEP. Também permite ao Intune efetuar carregamentos do Perfil de Inscrição para a Apple e atribuir dispositivos a esses perfis.

Para obter outros métodos para inscrever dispositivos iOS estão descritos em [Escolher como inscrever dispositivos iOS no Intune](choose-ios-enrollment-method.md).

## <a name="prerequisites"></a>Pré-requisitos

Antes de configurar a inscrição de dispositivos iOS, tem de cumprir os seguintes pré-requisitos:

- [Configurar domínios](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-2)
- [Definir a Autoridade de MDM](set-mdm-authority.md)
- [Criar grupos](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-5)
- Atribuir licenças de utilizador no [portal do Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854)
- [Obter um certificado push de MDM da Apple](get-an-apple-mdm-push-certificate.md)
- [Obter um token DEP da Apple](get-apple-dep-token.md)

## <a name="create-an-apple-dep-profile-for-devices"></a>Criar um perfil de DEP da Apple para dispositivos

Um perfil de inscrição de dispositivos especifica as definições aplicadas a um grupo de dispositivos. Os seguintes passos mostram como criar um perfil de inscrição de dispositivos para os dispositivos iOS inscritos através do DEP.

1. No portal do Azure, escolha **Mais Serviços**, introduza **Intune** na caixa de texto e, em seguida, escolha **Outros** > **Intune**.

2. No painel Intune, escolha **Inscrever dispositivos** e, em seguida, escolha **Inscrição da Apple**.

3. Em **Definições do Programa de Registo de Aparelho (DEP) da Apple**, selecione **Perfis de DEP**.

4. No painel **Perfis de DEP da Apple**, selecione **Criar**.

5. No painel **Criar Perfil de Inscrição**, introduza um nome e uma descrição para o perfil.

6. Na **Afinidade de Utilizador**, escolha se os dispositivos com este perfil se vão inscrever com ou sem a afinidade do utilizador.

 - **Inscrever com afinidade do utilizador** – O dispositivo tem de ser afiliado a um utilizador durante a configuração inicial e, em seguida, pode receber permissões para aceder ao e-mail e aos dados da empresa. Escolha afinidade de utilizador para dispositivos geridos por DEP que pertencem aos utilizadores e que precisam de utilizar o portal da empresa para serviços como a instalação de aplicações. Tenha em atenção que a Autenticação multifator (MFA) não funciona durante a inscrição em dispositivos DEP com afinidade de utilizador. Depois da inscrição, a MFA funciona conforme esperado nestes dispositivos.

    >[!NOTE]
    >O DEP com afinidade de utilizador requer a ativação de um ponto final de Nome de Utilizador/Misto WS-Trust 1.3 para pedir o token de utilizador.

 - **Inscrever sem afinidade do utilizador** – O dispositivo não está afiliado a um utilizador. Utilize esta afiliação em dispositivos que efetuem tarefas sem aceder aos dados de utilizador locais. As aplicações que requerem afiliação de utilizadores (incluindo a aplicação Portal da Empresa utilizada para instalar aplicações de linha de negócio) não irão funcionar.

7. Selecione **Definições de Gestão de Dispositivos**, configure as seguintes definições de perfil e, em seguida, selecione **Guardar**:

    - **Supervisionado** – um modo de gestão que ativa mais opções de gestão e desativa o Bloqueio de Ativação por predefinição. Se deixar a caixa de verificação em branco, fica com capacidades de gestão limitadas.

    - **Inscrição bloqueada** – (requer Modo de Gestão = Supervisionado) Desativa as definições de iOS que poderiam permitir a remoção do perfil de gestão. Se deixar a caixa de verificação em branco, permitirá que o perfil de gestão seja removido do menu Definições. Este item é definido durante a ativação e não pode ser alterado sem uma reposição de fábrica.

    - **Permitir Emparelhamento** – especifica se os dispositivos iOS se podem sincronizar com computadores. Se escolher **Permitir o Apple Configurator por certificado**, terá de escolher um certificado em **Certificados do Apple Configurator**.

    - **Certificados do Apple Configurator** – Se escolheu **Permitir o Apple Configurator por certificado** em **Permitir Emparelhamento**, selecione um Certificado do Apple Configurator a importar.

8. Selecione **Definições do Assistente de Configuração**, configure as seguintes definições de perfil e, em seguida, selecione **Guardar**:

    - **Nome do Departamento** – Aparece quando os utilizadores tocam em **Sobre a Configuração de** durante a ativação.

    - **Telefone do Departamento** – Aparece quando o utilizador clica no botão Preciso de ajuda durante a ativação.
    - **Opções do Assistente de Configuração** – estas definições opcionais podem ser configuradas mais tarde no menu **Definições** de iOS.
        - **Código de Acesso** – pedido de código de acesso durante a ativação. Solicite sempre um código de acesso, a menos que o dispositivo esteja protegido ou tenha o acesso controlado de outra forma (ou seja, modo de local público que restringe o dispositivo a uma aplicação).
        - **Serviços de Localização** – se ativado, o Assistente de Configuração solicita o serviço durante a ativação
        - **Restaurar** – se estiver ativado, o Assistente de Configuração solicita a cópia de segurança de iCloud durante a ativação
        - **ID Apple** – se estiver ativado, o iOS irá pedir aos utilizadores um ID Apple quando o Intune tenta instalar uma aplicação sem um ID. É necessário um ID Apple para transferir aplicações iOS da App Store, incluindo as instaladas pelo Intune.
        - **Termos e Condições** – se ativado, o Assistente de Configuração solicita aos utilizadores que aceitem os termos e condições da Apple durante a ativação
        - **Touch ID** – se ativado, o Assistente de Configuração solicita este serviço durante a ativação
        - **Apple Pay** – se ativado, o Assistente de Configuração solicita este serviço durante a ativação
        - **Zoom** – se ativado, o Assistente de Configuração solicita este serviço durante a ativação
        - **Siri** – se ativado, o Assistente de Configuração solicita este serviço durante a ativação
        - **Dados de Diagnóstico** – Se ativado, o Assistente de Configuração solicita este serviço durante a ativação

9. Para guardar as definições de perfil, selecione **Criar**, no painel **Criar Perfil de Inscrição**.

## <a name="assign-apple-dep-serial-numbers-to-your-mdm-server"></a>Atribuir números de série do DEP da Apple ao seu servidor MDM

1. Aceda ao [Portal do Programa de Inscrição de Dispositivos](https://deploy.apple.com) (https://deploy.apple.com) e inicie sessão com o ID Apple da sua empresa. 

2. Aceda a **Programa de Implementação** &gt; **Programa de Inscrição de Dispositivos** &gt; **Gerir Dispositivos**. 

3. Especifique como irá **Escolher Dispositivos** e, em seguida, indique as informações do dispositivo e especifique os detalhes pelo **Número de Série**e **Número da Encomenda**do dispositivo, ou como **Carregar Ficheiro CSV**. 

4. Selecione **Atribuir ao Servidor**, selecione o &lt;NomeDoServidor&gt; especificado para o Microsoft Intune e, em seguida, selecione **OK**.

## <a name="synchronize-dep-managed-devices"></a>Sincronizar dispositivos geridos por DEP

1. No painel Intune do portal do Azure, escolha **Inscrever Dispositivos** e, em seguida, escolha **Inscrição da Apple**.

2. Em **Definições do Programa de Registo de Aparelho (DEP) da Apple**, selecione **Números de Série de DEP**.

4. No painel **Números de Série do DEP da Apple**, selecione **Sincronização**.

5. No painel **Sincronização**, selecione **Pedir Sincronização**. A barra de progresso mostra a quantidade de tempo que tem de aguardar até pedir novamente a Sincronização.

    Para estar em conformidade com os termos da Apple para o tráfego DEP aceitável, o Intune impõe as seguintes restrições:
     -  Uma sincronização completa do DEP não pode ser executada mais do que uma vez a cada sete dias. Durante uma sincronização completa, o Intune atualiza cada número de série que a Apple tenha atribuído ao Intune, quer o número tenha sido ou não sincronizado anteriormente. Se for tentada uma sincronização completa no prazo de sete dias após a sincronização completa anterior, o Intune apenas atualiza os números de série que ainda não estejam listados no Intune.
     -  São atribuídos 10 minutos a qualquer pedido de sincronização para ser concluído. Durante este tempo ou até o pedido ser concluído com êxito, o botão **Sync (Sincronizar)** está desativado.

>[!NOTE]
>Também pode atribuir números de série do DEP aos perfis no painel **Números de Série do DEP da Apple**.

## <a name="distribute-devices-to-users"></a>Distribuir dispositivos pelos utilizadores

Já pode distribuir os dispositivos pertencentes à empresa aos utilizadores. Quando um dispositivo iOS é ativado, será inscrito para gestão pelo Intune.


## <a name="how-users-install-and-use-the-company-portal-on-their-devices"></a>Como os utilizadores instalam e utilizam o Portal da Empresa nos dispositivos deles

Os dispositivos configurados com a afinidade de utilizador podem instalar e executar a aplicação Portal da Empresa para transferir aplicações e gerir dispositivos. Assim que os utilizadores recebem os dispositivos, têm de executar os passos adicionais descritos abaixo para concluir o Assistente de Configuração e instalar a aplicação Portal da Empresa.

### <a name="how-users-enroll-corporate-owned-ios-devices-with-user-affinity"></a>Como os utilizadores inscrevem dispositivos iOS pertencentes à empresa com afinidade de utilizador 

1. Quando os utilizadores ligam os dispositivos, é-lhes pedido que concluam o Assistente de Configuração. Durante a configuração, os utilizadores recebem um pedido de credenciais. Terão de utilizar as credenciais (ou seja, o nome pessoal exclusivo ou UPN) associadas à subscrição no Intune.

2. Durante a configuração, os utilizadores recebem um pedido do Apple ID. Terão de fornecer um Apple ID para permitir que o dispositivo instale o Portal da Empresa. Também podem fornecer o ID no menu de definições do iOS após a conclusão da configuração.

3. Depois de concluir a configuração, os utilizadores têm de instalar a aplicação Portal da Empresa a partir da App Store.

4. Os utilizadores poderão então iniciar sessão no Portal da Empresa através do UPN utilizado quando configuraram o dispositivo.

5. Após iniciar sessão, é pedido aos utilizadores que inscrevam o dispositivo. O primeiro passo consiste em identificar o dispositivo. A aplicação apresenta uma lista de dispositivos iOS que já foram inscritos pela empresa e atribuídos à conta do Intune do utilizador. Deve escolher o dispositivo correspondente. Se este dispositivo ainda não tiver sido inscrito pela empresa, deverão escolher um novo dispositivo para continuar o fluxo de inscrição padrão.

6. No ecrã seguinte, os utilizadores confirmam o número de série do novo dispositivo. Para tal, os utilizadores selecionam uma ligação que aparece. A ligação inicia a aplicação Definições, que permite aos utilizadores verificar o número de série deles. Em seguida, os utilizadores têm de introduzir os últimos quatro carateres do número de série na aplicação Portal da Empresa.

   Este passo verifica se o dispositivo é o dispositivo da empresa inscrito no Intune. Se o número de série no dispositivo não coincidir, significa que o utilizador selecionou o dispositivo errado. O utilizador tem de voltar ao ecrã anterior e selecionar um dispositivo diferente.

7. Depois de verificar o número de série, a aplicação Portal da Empresa redireciona o utilizador para o site do Portal da Empresa para finalizar a inscrição. Em seguida, o site solicita aos utilizadores que voltem para a aplicação.

A inscrição está concluída e os utilizadores podem utilizar este dispositivo com o conjunto completo de capacidades.



<!--HONumber=Feb17_HO1-->


