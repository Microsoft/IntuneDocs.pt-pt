---
title: "Inscrever dispositivos iOS – Programa de Registo de Aparelho"
titleSuffix: Intune Azure preview
description: "Pré-visualização do Azure no Intune: saiba como inscrever dispositivos iOS pertencentes à empresa através do Programa de Registo de aparelho."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 04/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7981a9c0-168e-4c54-9afd-ac51e895042c
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 5144b9e7c17a3323667b9ca68cb47829d69866c3
ms.contentlocale: pt-pt
ms.lasthandoff: 05/23/2017


---

# <a name="enroll-ios-devices-using-device-enrollment-program"></a>Inscrever dispositivos iOS com o Programa de Registo de Aparelho

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

Este tópico ajuda os administradores de TI a inscrever dispositivos iOS da empresa comprados através do [Programa de Registo de Aparelho (DEP) da Apple ](https://deploy.apple.com). O Microsoft Intune pode implementar um perfil de inscrição que inscreve o DEP "over the air", pelo que o administrador não precisa de mexer em cada dispositivo gerido. Um perfil de DEP contém definições de gestão que deve aplicar a dispositivos durante a inscrição. O pacote de inscrição pode incluir opções do Assistente de Configuração do dispositivo.

>[!NOTE]
>A inscrição no DEP não pode ser utilizada com o [gestor de inscrição de dispositivos](device-enrollment-manager-enroll.md).
>Além disso, se os utilizadores inscreverem os dispositivos iOS através da aplicação Portal da Empresa e os números de série dos mesmos forem posteriormente importados e lhes for atribuído um perfil de DEP, a inscrição do dispositivo no Intune será anulada.

**Passos para Inscrição no DEP**
1. [Obter um token DEP da Apple](#get-the-apple-dep-certificate)
2. [Criar um perfil de DEP](#create-an-apple-dep-profile)
3. [Atribuir números de série do DEP da Apple ao seu servidor do Intune](#assign-apple-dep-serial-numbers-to-your-mdm-server)
4. [Sincronizar dispositivos geridos pelo DEP](#synchronize-dep-managed-devices)
5. [Atribuir o perfil de DEP aos dispositivos](#assign-a-dep-profile-to-devices)
6. [Distribuir os dispositivos pelos utilizadores](#distribute-devices-to-users)

## <a name="get-the-apple-dep-certificate"></a>Para obter um certificado do DEP da Apple
Para poder inscrever dispositivos iOS da empresa com o Programa de Registo de Aparelho (DEP) da Apple, precisa de um ficheiro de certificado (.p7m) do DEP da Apple. Este token permite ao Intune sincronizar informações sobre os dispositivos propriedade da empresa participantes no DEP. Também permite ao Intune efetuar carregamentos do perfil de inscrição para a Apple e atribuir dispositivos a esses perfis.

Para dispositivos iOS da empresa com o DEP, a sua organização tem de aderir ao Apple DEP e obter dispositivos através desse programa. Os detalhes desse processo estão disponíveis em: https://deploy.apple.com. Entre as vantagens do programa incluem-se a configuração automatizada de dispositivos sem utilizar um cabo USB para ligar cada dispositivo a um computador.

> [!NOTE]
> Se o seu inquilino do Intune tiver sido migrado a partir da consola clássica do Intune para o portal do Azure e tiver eliminado um token DEP da Apple da consola de administração do Intune durante o período de migração, o token DEP poderá ter sido restaurado para a sua conta do Intune. Pode eliminar novamente o token DEP do portal do Azure.

**Passo 1. Transfira um certificado de chave pública do Intune obrigatório para criar um token DEP da Apple.**<br>
1. No portal do Azure, selecione **Mais Serviços** > **Monitorização + Gestão** > **Intune**. No painel do Intune, selecione **Inscrição de dispositivos** > **Token DEP da Apple**.
2. Selecione **Transferir a chave pública** para transferir e guardar o ficheiro da chave de encriptação (.pem) localmente. O ficheiro .pem é utilizado para pedir um certificado de relação de confiança a partir do portal do Programa de Registo de Aparelho da Apple.

**Passo 2: Transfira um token DEP da Apple a partir do site da Apple adequado.**<br>
Selecione [Criar um token DEP através de Programas de Implementação da Apple](https://deploy.apple.com) (https://deploy.apple.com) e inicie sessão com o ID Apple da sua empresa. Pode utilizar este Apple ID para renovar o seu token DEP.

   1.  No [Portal do Programa de Registo de Aparelho](https://deploy.apple.com) da Apple, aceda a **Programa de Registo de Aparelho** &gt; **Manage Servers** (Gerir Servidores) e, em seguida, selecione **Add MDM Server** (Adicionar Servidor MDM).
   2.  Introduza o **Nome do Servidor MDM** e, em seguida, selecione **Seguinte**. O nome do servidor é uma referência para identificar o servidor de gestão de dispositivos móveis (MDM). Não é o nome nem o URL do Microsoft Intune.
   3.  É aberta a caixa de diálogo **Adicionar &lt;NomeDoServidor&gt;**. Selecione **Escolher Ficheiro…** para carregar o ficheiro .pem e, em seguida, selecione **Seguinte**.
   4.  A caixa de diálogo **Adicionar &lt;NomeDoServidor&gt;** mostra uma ligação para o **Token do Seu Servidor**. Transfira o ficheiro do token do servidor (.p7m) para o seu computador e, em seguida, selecione **Concluído**.

**Passo 3: Introduza o ID Apple que serviu para criar o seu token DEP da Apple. Este ID pode servir para renovar o seu token DEP da Apple.**

**Passo 4: Navegue para o seu token DEP da Apple para carregar. O Intune sincronizará automaticamente com a sua conta de DEP.**<br>
Aceda ao ficheiro de certificado (.pem), escolha **Abrir** e, em seguida, escolha **Carregar**. Com o certificado push, o Intune pode inscrever e gerir dispositivos iOS ao enviar políticas para dispositivos móveis inscritos.

## <a name="create-an-apple-dep-profile"></a>Criar um perfil de DEP da Apple

Um perfil de inscrição de dispositivos especifica as definições aplicadas a um grupo de dispositivos. Os seguintes passos mostram como criar um perfil de inscrição de dispositivos para os dispositivos iOS inscritos através do DEP.

1. No portal do Azure, selecione **Mais Serviços** > **Monitorização + Gestão** > **Intune**.
2. No painel do Intune, escolha **Inscrição de dispositivos** e, em seguida, **Inscrição da Apple**.
3. Em **Definições do Programa de Registo de Aparelho (DEP) da Apple**, selecione **Perfis de DEP**.
4. No painel **Perfis de DEP da Apple**, selecione **Criar**.
5. No painel **Criar Perfil de Inscrição**, introduza um nome e uma descrição para o perfil.
6. Na **Afinidade de Utilizador**, escolha se os dispositivos com este perfil se vão inscrever com ou sem a afinidade do utilizador.

 - **Inscrever com afinidade do utilizador** – O dispositivo tem de ser afiliado a um utilizador durante a configuração inicial e, em seguida, pode receber permissões para aceder ao e-mail e aos dados da empresa. Escolha afinidade de utilizador para dispositivos geridos por DEP que pertencem aos utilizadores e que precisam de utilizar o portal da empresa para serviços como a instalação de aplicações. Tenha em atenção que a Autenticação multifator (MFA) não funciona durante a inscrição em dispositivos DEP com afinidade de utilizador. Depois da inscrição, a MFA funciona conforme esperado nestes dispositivos. Durante a inscrição em dispositivos DEP, não pode ser pedida a alteração da palavra-passe aos novos utilizadores que tenham de alterar a palavra-passe no primeiro início de sessão. Além disso, não será pedido aos utilizadores cujas palavras-passe expiraram que reponham a palavra-passe durante a inscrição DEP e os mesmos terão de repor a palavra-passe a partir de um dispositivo diferente.

    >[!NOTE]
    >O DEP com afinidade de utilizador requer a ativação de um [ponto final de Nome de Utilizador/Misto WS-Trust 1.3](https://technet.microsoft.com/en-us/library/adfs2-help-endpoints) para pedir o token de utilizador. [Saiba mais sobre o WS-Trust 1.3](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint).

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
Para gerir os dispositivos, tem de atribuir ao servidor MDM do Intune os números de série deles no portal Web do DEP da Apple.

1. Aceda ao [Portal do Programa de Inscrição de Dispositivos](https://deploy.apple.com) (https://deploy.apple.com) e inicie sessão com o ID Apple da sua empresa.

2. Aceda a **Programa de Implementação** &gt; **Programa de Inscrição de Dispositivos** &gt; **Gerir Dispositivos**.

3. Especifique como irá **Escolher Dispositivos** e, em seguida, indique as informações do dispositivo e especifique os detalhes pelo **Número de Série**e **Número da Encomenda**do dispositivo, ou como **Carregar Ficheiro CSV**.

4. Selecione **Atribuir ao Servidor**, selecione o &lt;NomeDoServidor&gt; especificado para o Microsoft Intune e, em seguida, selecione **OK**.

## <a name="synchronize-dep-managed-devices"></a>Sincronizar dispositivos geridos por DEP
Agora que foi atribuída a permissão ao Intune para gerir os dispositivos DEP, pode sincronizar o Intune com o serviço DEP para ver os dispositivos geridos no portal do Intune.

1. No portal do Azure, selecione **Mais Serviços** > **Monitorização + Gestão** > **Intune**.

2. No painel do Intune do portal do Azure, escolha **Inscrição de dispositivos** e, em seguida, **Inscrição da Apple**.

3. Em **Definições do Programa de Registo de Aparelho (DEP) da Apple**, selecione **Números de Série de DEP**.

4. No painel **Números de Série do DEP da Apple**, selecione **Sincronização**.

5. No painel **Sincronização**, selecione **Pedir Sincronização**. A barra de progresso mostra a quantidade de tempo que tem de aguardar até pedir novamente a Sincronização.

    Para estar em conformidade com os termos da Apple para o tráfego DEP aceitável, o Intune impõe as seguintes restrições:
     -    Uma sincronização completa do DEP não pode ser executada mais do que uma vez a cada sete dias. Durante uma sincronização completa, o Intune atualiza cada número de série que a Apple tenha atribuído ao Intune, quer o número tenha sido ou não sincronizado anteriormente. Se for tentada uma sincronização completa no prazo de sete dias após a sincronização completa anterior, o Intune apenas atualiza os números de série que ainda não estejam listados no Intune.
     -    São atribuídos 10 minutos a qualquer pedido de sincronização para ser concluído. Durante este tempo ou até o pedido ser concluído com êxito, o botão **Sync (Sincronizar)** está desativado.

>[!NOTE]
>Também pode atribuir números de série do DEP aos perfis no painel **Números de Série do DEP da Apple**.

## <a name="assign-a-dep-profile-to-devices"></a>Atribuir um perfil de DEP aos dispositivos
Tem de atribuir um perfil de DEP aos dispositivos DEP geridos pelo Intune antes de os poder inscrever.

1. No portal do Azure, selecione **Mais Serviços** > **Monitorização + Gestão** > **Intune**.

2. No painel do Intune do portal do Azure, escolha **Inscrição de dispositivos** > **Inscrição da Apple** e, em seguida, selecione **Perfis de DEP**.

3. Na lista de **Perfis de Inscrição de DEP da Apple**, selecione o perfil que pretende atribuir aos dispositivos e, em seguida, selecione **Atribuições de Dispositivos**

4. Selecione **Atribuir** e, em seguida, selecione os dispositivos DEP aos quais pretende atribuir este perfil. Pode filtrar para ver os dispositivos DEP disponíveis:
  - **não atribuído**
  - **qualquer**
  - **&lt;nome do perfil de DEP&gt;**

  ![Captura de ecrã do botão Atribuir para atribuir o perfil de DEP no portal do Intune](media/dep-profile-assignment.png)

5. Selecione os dispositivos que pretende gerir. A caixa de verificação acima da coluna selecionará até 1000 dispositivos listados. Em seguida, clique em **Atribuir**. Para inscrever mais de 1000 dispositivos, repita os passos de atribuição até que seja atribuído um perfil de DEP a todos os dispositivos.

## <a name="distribute-devices-to-users"></a>Distribuir dispositivos pelos utilizadores

Já pode distribuir os dispositivos pertencentes à empresa aos utilizadores. Quando um dispositivo DEP iOS é ligado, será inscrito para gestão pelo Intune. Se o dispositivo foi ativado e estiver a ser utilizado, não poderá aplicar o perfil até ser realizada uma reposição de fábrica no dispositivo.

Ver [Como dar formação aos seus utilizadores finais sobre o Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/how-to-educate-your-end-users-about-microsoft-intune). Também pode direcionar os utilizadores finais para [Utilizar o seu dispositivo iOS ou macOS com o Intune](https://docs.microsoft.com/intune/deploy-use/how-to-educate-your-end-users-about-microsoft-intune) 

### <a name="how-users-install-and-use-the-company-portal-on-their-devices"></a>Como os utilizadores instalam e utilizam o Portal da Empresa nos dispositivos deles

Os dispositivos configurados com a afinidade de utilizador podem instalar e executar a aplicação Portal da Empresa para transferir aplicações e gerir dispositivos. Assim que os utilizadores recebem os dispositivos, têm de executar os passos adicionais descritos abaixo para concluir o Assistente de Configuração e instalar a aplicação Portal da Empresa.

