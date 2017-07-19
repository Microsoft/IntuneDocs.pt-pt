---
title: "Inscrever dispositivos iOS – Programa de Registo de Aparelho"
titleSuffix: Intune on Azure
description: "Saiba como inscrever dispositivos iOS pertencentes à empresa através do Programa de Inscrição de Dispositivos.\""
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 06/30/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7981a9c0-168e-4c54-9afd-ac51e895042c
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f509f5332b2f8b5f6745816f8795a9a54c10ce2d
ms.sourcegitcommit: fd2e8f6f8761fdd65b49f6e4223c2d4a013dd6d9
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/03/2017
---
# <a name="set-up-ios-device-enrollment-with-device-enrollment-program"></a>Configurar a inscrição de dispositivos iOS com o Programa de Inscrição de Dispositivos

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Este tópico ajuda os administradores de TI a ativar a inscrição de dispositivos iOS para dispositivos adquiridos através do [ Programa de Inscrição de Dispositivos (DEP)](https://deploy.apple.com) da Apple. O Microsoft Intune pode implementar um perfil de inscrição através de uma rede sem fios para dispositivos adquiridos através do DEP. O administrador nunca precisa de tocar em cada dispositivo gerido. Um perfil de DEP inclui definições de gestão que são aplicadas aos dispositivos durante a inscrição, incluindo opções do Assistente de Configuração.

Para ativar a inscrição DEP, deve utilizar os portais do Intune e do Apple DEP. Também é necessária uma lista ou número da nota de encomenda dos seus dispositivos DEP para que os possa atribuir para gestão ao Intune no portal da Apple.

>[!NOTE]
>A inscrição no DEP não pode ser utilizada com o [gestor de inscrição de dispositivos](device-enrollment-manager-enroll.md).

**Passo para ativar programas de inscrição da Apple**
1. [Obter um token DEP da Apple e atribuir dispositivos](#get-the-apple-dep-certificate)
2. [Criar um perfil de inscrição](#create-anapple-enrollment-profile)
3. [Sincronizar dispositivos geridos pelo DEP](#sync-dep-managed-devices)
4. [Atribuir o perfil de DEP aos dispositivos](#assign-a-dep-profile-to-devices)
5. [Distribuir os dispositivos pelos utilizadores](#distribute-devices-to-users)

## <a name="get-the-apple-dep-token"></a>Obter o token DEP da Apple

Para poder inscrever dispositivos iOS da empresa através do Programa de Inscrição de Dispositivos (DEP) da Apple, precisa de ter um ficheiro de token DEP (.p7m) da Apple. Este token permite ao Intune sincronizar informações sobre os dispositivos propriedade da empresa participantes no DEP. Também permite ao Intune efetuar carregamentos do perfil de inscrição para a Apple e atribuir dispositivos a esses perfis.

> [!NOTE]
> Se o seu inquilino do Intune tiver sido migrado a partir da consola clássica do Intune para o portal do Azure e tiver eliminado um token DEP da Apple da consola de administração do Intune durante o período de migração, o token DEP poderá ter sido restaurado para a sua conta do Intune. Pode eliminar novamente o token DEP do portal do Azure.

**Pré-requisitos**
- [Certificado Push de MDM da Apple](apple-mdm-push-certificate-get.md)
- Inscrição no [Programa de Inscrição de Dispositivos da Apple](http://deploy.apple.com)

**Passo 1. Transfira um certificado de chave pública do Intune obrigatório para criar um token DEP da Apple.**<br>
1. No portal do Intune, selecione **Inscrição de dispositivos** e, em seguida, selecione **Inscrição da Apple** e **Token do Programa de Inscrição**.
![Captura de ecrã a mostrar o painel Token do Programa de Inscrição na área de trabalho Certificados da Apple.](./media/enrollment-program-token-add.png)
2. Selecione **Transferir a chave pública** para transferir e guardar o ficheiro da chave de encriptação (.pem) localmente. O ficheiro .pem é utilizado para pedir um certificado de relação de confiança a partir do portal do Programa de Inscrição de Dispositivos da Apple.
![Captura de ecrã a mostrar o painel Token do Programa de Inscrição, na área de trabalho Certificados da Apple, para transferir a chave pública.](./media/enrollment-program-token-download.png)

**Passo 2: Crie e transfira um token DEP da Apple.**<br>
Selecione **Criar um token através do Programa de Inscrição de Dispositivos da Apple** para abrir o portal Programa de Implementação da Apple e inicie sessão com o ID Apple da sua empresa. Pode utilizar este Apple ID para renovar o seu token DEP.
  ![Captura de ecrã a mostrar o painel Token do Programa de Inscrição na área de trabalho Certificados da Apple.](./media/enrollment-program-token-create.png)

  ![Captura de ecrã a mostrar o painel Token do Programa de Inscrição, na área de trabalho Certificados da Apple, para transferir a chave pública.](./media/enrollment-program-token-sign.png)
   1.  No portal dos [Programas de Implementação](https://deploy.apple.com) da Apple, selecione **Começar** em **Programa de Registo de Dispositivos**.
   ![Captura de ecrã a mostrar o painel Programa de Registo, ao clicar na opção Começar no Programa de Registo de Dispositivos.](./media/enrollment-program-token-started.png)
   2. Na página **Gerir Servidores**, selecione **Adicionar Servidor MDM**.
   3. Introduza o **Nome do Servidor MDM** e, em seguida, selecione **Seguinte**. O nome do servidor é uma referência para identificar o servidor de gestão de dispositivos móveis (MDM). Não é o nome nem o URL do Microsoft Intune.

   ![Captura de ecrã a mostrar a ação de adicionar um nome de servidor MDM para DEP e, em seguida, clicar em Seguinte.](./media/enrollment-program-token-add-server.png)
   4.  A caixa de diálogo **Adicionar &lt;NomeDoServidor&gt;** é aberta e pede para **Atualizar a Chave Pública**. Selecione **Escolher Ficheiro…** para carregar o ficheiro .pem e, em seguida, selecione **Seguinte**.
   ![Captura de ecrã a mostrar a ação de selecionar o botão de ficheiros de chave pública e, em seguida, clicar em Seguinte.](./media/enrollment-program-token-choose-file.png)
   4.  A caixa de diálogo **Adicionar &lt;NomeDoServidor&gt;** mostra uma ligação para o **Token do Seu Servidor**. Transfira o ficheiro do token do servidor (.p7m) para o seu computador e, em seguida, selecione **Concluído**.
   ![Captura de ecrã a mostrar a ação de selecionar o botão de ficheiros de chave pública e, em seguida, clicar em Seguinte.](./media/enrollment-program-token-your-token.png)
   5. Aceda a **Programas de Implementação** &gt; **Programa de Inscrição de Dispositivos** &gt; **Gerir Dispositivos**.
   6. Em **Selecionar Dispositivos Por**, especifique a forma como os dispositivos são identificados:
    - **Número de Série**
    - **Número da Encomenda**
    - **Carregar Ficheiro CSV**.

   ![Captura de ecrã a mostrar a especificação de dispositivos selecionados pelo número de série, a definição da ação de seleção como Atribuir ao servidor e a seleção do nome do servidor.](./media/enrollment-program-token-specify-serial.png)

   7. Em **Selecionar Ação**, selecione **Atribuir ao Servidor**, selecione o &lt;NomeDoServidor&gt; especificado no Microsoft Intune e, em seguida, selecione **OK**. O portal da Apple atribui os dispositivos especificados para o servidor do Intune para gestão e, em seguida, apresenta a mensagem **Atribuição Concluída**.

   No portal da Apple, aceda a **Programas de Implementação** &gt; **Programa de Inscrição de Dispositivos** &gt; **Ver Histórico de Atribuições** para ver uma lista de dispositivos e a respetiva atribuição de servidores MDM.

**Passo 3: Introduza o ID Apple utilizado para criar o token do seu programa de inscrição.**<br>No portal do Intune, forneça o ID Apple para referência futura. Utilize este ID para renovar o token do seu programa de inscrição, de forma a evitar ter de reinscrever todos os seus dispositivos.
![Captura de ecrã a mostrar a especificação do ID Apple utilizado para criar o token do programa de inscrição e o acesso ao token do programa de inscrição.](./media/enrollment-program-token-apple-id.png)
**Passo 4. Aceda ao token do programa de inscrição para atualizar.**<br>
Aceda ao ficheiro de certificado (.pem), escolha **Abrir** e, em seguida, escolha **Carregar**. Com o certificado push, o Intune pode inscrever e gerir dispositivos iOS ao enviar políticas para dispositivos móveis inscritos. O Intune é sincronizado automaticamente na Apple para que possa ver a conta do seu programa de inscrição.

## <a name="create-an-apple-enrollment-profile"></a>Criar um perfil de inscrição da Apple

Um perfil de inscrição de dispositivos especifica as definições aplicadas a um grupo de dispositivos durante a inscrição.

1. No portal do Intune, escolha **Inscrição de dispositivos** e, em seguida, **Inscrição da Apple**.
2. Em **Programa de Inscrição da Apple**, selecione **Perfis do Programa de Inscrição** e, em seguida, selecione **Criar** no painel **Perfis do Programa de Inscrição**.
![Captura de ecrã a mostrar a criação de uma ligação para gerar um novo perfil do programa de inscrição.](./media/enrollment-program-profile-create.png)
3. No painel **Criar Perfil de Inscrição**, introduza um **Nome** e **Descrição** para o perfil para efeitos administrativos. Os utilizadores não verão estes detalhes.
![Captura de ecrã a mostrar a especificação da descrição do nome e, em seguida, a seleção da opção Inscrever com afinidade do utilizador para criar um novo perfil do programa de inscrição.](./media/enrollment-program-profile-name.png)
Na **Afinidade de Utilizador**, escolha se os dispositivos com este perfil se inscrevem com ou sem a afinidade do utilizador.

 - **Inscrever com afinidade do utilizador** – os utilizadores são associados aos dispositivos durante a configuração e passam assim a ter permissão para aceder aos dados e e-mails da empresa. Selecione **afinidade do utilizador** para os dispositivos que pertençam aos utilizadores e que precisem de utilizar o portal da empresa para utilizar serviços como a instalação de aplicações.

<<<<<<< CABEÇALHO
 > [!NOTE]
 > A autenticação multifator (MFA) não funciona durante a inscrição em dispositivos geridos por um programa de inscrição com afinidade do utilizador. Depois da inscrição, a MFA funciona conforme esperado nestes dispositivos. Durante a inscrição em dispositivos, não pode ser pedida a alteração da palavra-passe aos novos utilizadores que tenham de alterar a palavra-passe no primeiro início de sessão. Além disso, não é pedido aos utilizadores com palavras-passe expiradas que reponham a palavra-passe durante a inscrição e estes terão de repor a palavra-passe a partir de um dispositivo diferente.

 >[!NOTE]
 >A gestão de programas de inscrição com afinidade de utilizador necessita que o [ponto final WS-Trust 1.3 Username/Mixed](https://technet.microsoft.com/library/adfs2-help-endpoints) seja ativado para pedir o token de utilizador. [Saiba mais sobre o WS-Trust 1.3](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint).
=======
    >[!NOTE]
    >O DEP com afinidade de utilizador requer a ativação de um [ponto final de Nome de Utilizador/Misto WS-Trust 1.3](https://technet.microsoft.com/library/adfs2-help-endpoints) para pedir o token de utilizador. [Saiba mais sobre o WS-Trust 1.3](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint).
>>>>>>> 0c3fe0dee88e8ef4d8ad8ad28c0f8957831dd5b3

 - **Inscrever sem afinidade do utilizador** – O dispositivo não está afiliado a um utilizador. Utilize esta afiliação em dispositivos que efetuem tarefas sem aceder aos dados de utilizador locais. As aplicações que requerem afiliação de utilizadores (incluindo a aplicação Portal da Empresa utilizada para instalar aplicações de linha de negócio) não irão funcionar.

4. Selecione **Definições da Gestão de Dispositivos** para configurar as seguintes definições de perfil: ![Captura de ecrã a mostrar a seleção do modo de gestão com as opções Supervisionado, Inscrição Bloqueada e Permitir Emparelhamento definidas como Recusar Tudo e os Certificados do Apple Configurator desativados num novo perfil do programa de inscrição.](./media/enrollment-program-profile-mode.png)
    - **Supervisionado** – um modo de gestão que ativa mais opções de gestão e desativa o Bloqueio de Ativação por predefinição. Se deixar a caixa de verificação em branco, fica com capacidades de gestão limitadas.

    - **Inscrição bloqueada** – (requer Modo de Gestão = Supervisionado) Desativa as definições de iOS que poderiam permitir a remoção do perfil de gestão. Se deixar a caixa de verificação em branco, permitirá que o perfil de gestão seja removido do menu Definições. Este item é definido durante a ativação e não pode ser alterado sem uma reposição de fábrica.

    - **Permitir Emparelhamento** – especifica se os dispositivos iOS podem sincronizar com computadores. Se escolher **Permitir o Apple Configurator por certificado**, terá de escolher um certificado em **Certificados do Apple Configurator**.

    - **Certificados do Apple Configurator** – Se escolheu **Permitir o Apple Configurator por certificado** em **Permitir Emparelhamento**, selecione um Certificado do Apple Configurator a importar.

  Escolha **Guardar**.

5. Selecione **Definições do Assistente de Configuração** para configurar as seguintes definições do perfil: ![captura de ecrã a mostrar a seleção das definições de configuração, com as definições disponíveis para um perfil de programa de inscrição.](./media/enrollment-program-profile-settings.png)
    - **Nome do Departamento** – Aparece quando os utilizadores tocam em **Sobre a Configuração de** durante a ativação.

    - **Telefone do Departamento** – Aparece quando o utilizador clica no botão Preciso de ajuda durante a ativação.
    - **Opções do Assistente de Configuração** – estas definições opcionais podem ser configuradas mais tarde no menu **Definições** de iOS.
        - **Código de Acesso** – pedido de código de acesso durante a ativação. Solicite sempre um código de acesso, a menos que o dispositivo esteja protegido ou tenha o acesso controlado de outra forma (ou seja, modo de local público que restringe o dispositivo a uma aplicação).
        - **Serviços de Localização** – se ativado, o Assistente de Configuração solicita o serviço durante a ativação
        - **Restaurar** – se estiver ativado, o Assistente de Configuração solicita a cópia de segurança de iCloud durante a ativação
        - **Apple ID** – Se estiver ativado, o iOS pede aos utilizadores um Apple ID quando o Intune tenta instalar uma aplicação sem um ID. É necessário um ID Apple para transferir aplicações iOS da App Store, incluindo as aplicações instaladas pelo Intune.
        - **Termos e Condições** – se ativado, o Assistente de Configuração solicita aos utilizadores que aceitem os termos e condições da Apple durante a ativação
        - **Touch ID** – se ativado, o Assistente de Configuração solicita este serviço durante a ativação
        - **Apple Pay** – se ativado, o Assistente de Configuração solicita este serviço durante a ativação
        - **Zoom** – se ativado, o Assistente de Configuração solicita este serviço durante a ativação
        - **Siri** – se ativado, o Assistente de Configuração solicita este serviço durante a ativação
        - **Dados de Diagnóstico** – Se ativado, o Assistente de Configuração solicita este serviço durante a ativação

    Escolha **Guardar**.
9. Para guardar as definições de perfil, selecione **Criar**, no painel **Criar Perfil de Inscrição**. O perfil de inscrição é apresentado na lista de Perfis de Inscrição do Programa de Inscrição da Apple.

## <a name="sync-managed-devices"></a>Sincronizar dispositivos geridos
Agora que o Intune tem permissão para gerir os seus dispositivos, pode sincronizar o Intune com a Apple para ver os seus dispositivos geridos no portal do Intune.

1. No portal do Intune, selecione **Inscrição de dispositivos** &gt; **Inscrição da Apple** &gt; **Dispositivos do Programa de Inscrição**.
2. Em **Dispositivos do Programa de Inscrição**, selecione **Sincronizar**. O painel **Sincronizar** é apresentado.
![Captura de ecrã a mostrar o nó Dispositivos do Programa de Inscrição selecionado e a opção Sincronizar ligação a ser selecionada.](./media/enrollment-program-device-sync.png)
3. No painel **Sincronização**, selecione **Pedir Sincronização**. A barra de progresso mostra a quantidade de tempo que tem de aguardar até pedir novamente a Sincronização.
![Captura de ecrã a mostrar o painel Sincronizar, com a ligação Pedido de sincronização a ser selecionada.](./media/enrollment-program-device-request-sync.png)
    Para cumprir os termos da Apple para um tráfego aceitável do programa de inscrição, o Intune impõe as seguintes restrições:
     -  As sincronizações completas não podem ser executadas mais do que uma vez a cada sete dias. Durante uma sincronização completa, o Intune atualiza cada número de série que a Apple tenha atribuído ao Intune, quer o número tenha sido ou não sincronizado anteriormente. Se for tentada uma sincronização completa no prazo de sete dias após a sincronização completa anterior, o Intune apenas atualiza os números de série que ainda não estejam listados no Intune.
     -  São atribuídos 15 minutos a qualquer pedido de sincronização para ser concluído. Durante este tempo ou até o pedido ser concluído com êxito, o botão **Sync (Sincronizar)** está desativado.
4. Na área de trabalho Dispositivos do Programa de Inscrição, selecione **Atualizar** para ver os seus dispositivos.

## <a name="assign-an-enrollment-profile-to-devices"></a>Atribuir um perfil de inscrição a dispositivos
É necessário atribuir um perfil do programa de inscrição aos dispositivos geridos pelo Intune antes de estes serem inscritos.

>[!NOTE]
>Também pode atribuir números de série a perfis a partir do painel **Números de Série da Apple**.

1. No portal do Intune, selecione **Inscrição de dispositivos** > **Inscrição da Apple** e, em seguida, selecione **Perfis do Programa de Inscrição**.
2. Na lista **Perfis do Programa de Inscrição**, selecione o perfil que pretende atribuir aos dispositivos e, em seguida, selecione **Atribuir dispositivos**.
![Captura de ecrã a mostrar o painel Sincronizar, com a ligação Pedido de sincronização a ser selecionada.](./media/enrollment-program-device-assign.png)
3. Selecione **Atribuir** e, em seguida, selecione os dispositivos aos quais pretende atribuir este perfil. Pode filtrar para ver os dispositivos disponíveis:
  - **não atribuído**
  - **qualquer**
  - **&lt;nome do perfil&gt;**
4. Selecione os dispositivos que pretende gerir. A caixa de verificação acima da coluna selecionará até 1000 dispositivos listados. Em seguida, clique em **Atribuir**. Para inscrever um número superior a 1000 dispositivos, repita os passos de atribuição até que todos os dispositivos tenham um perfil de inscrição associado.

  ![Captura de ecrã a mostrar o botão Atribuir um perfil do programa de inscrição no portal do Intune](media/dep-profile-assignment.png)

## <a name="end-user-experience-with-managed-devices"></a>Experiência do utilizador final com dispositivos geridos

Agora pode distribuir os dispositivos aos utilizadores. Os dispositivos com afinidade do utilizador necessitam que seja atribuída uma licença do Intune a cada utilizador. Se o dispositivo foi ativado e estiver a ser utilizado, não poderá aplicar o perfil até ser realizada uma reposição de fábrica no dispositivo. Quando o dispositivo iOS gerido por um programa de inscrição estiver ativado, o utilizador verá o seguinte:  

1. **Configurar o dispositivo iOS** – os utilizadores poderão selecionar uma das seguintes opções:
  - **Configurar como um novo dispositivo**
  - **Restaurar a partir do iCloud**
  - **Restaurar a partir do iTunes**
2. Os utilizadores são informados de que a **Microsoft irá configurar automaticamente o seu dispositivo.** São igualmente necessários os seguintes detalhes de configuração adicionais:

  **A configuração permite que a Microsoft faça a gestão deste dispositivo através de uma ligação sem fios.**

  **Um administrador pode ajudá-lo a configurar contas de e-mail e de rede, instalar e configurar aplicações e ainda gerir definições de forma remota.**

  **Um administrador pode desativar funcionalidades, instalar e remover aplicações, monitorizar e restringir o seu tráfego de Internet e apagar o dispositivo em causa de forma remota.**

  **A configuração é fornecida pela:<br> MicrosoftIntune iOS Team<br> One Microsoft Way, Redmond, WA 98052 (E.U.A.)**

3. Será pedido aos utilizadores que introduzam o nome de utilizador e palavra-passe da respetiva conta escolar ou profissional.
4. Será pedido aos utilizadores que introduzam o respetivo ID Apple. O ID Apple é necessário para instalar a aplicação Portal da Empresa do Intune, entre outras. Depois de fornecer as credenciais, o dispositivo irá instalar um perfil de gestão que não pode ser removido. O perfil de gestão do Intune é apresentado em **Definições** > **Geral** > **Gestão de Dispositivos** no dispositivo.

Agora, os utilizadores poderão concluir a configuração do respetivo dispositivo da empresa ao utilizar o Portal da Empresa do Intune ou o Assistente de Configuração da Apple.
