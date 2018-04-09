---
title: Inscrever dispositivos iOS através do Programa de Registo de Aparelho
titlesuffix: Microsoft Intune
description: Saiba como inscrever dispositivos iOS pertencentes à empresa através do Programa de Inscrição de Dispositivos."
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/08/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 7981a9c0-168e-4c54-9afd-ac51e895042c
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 05b03502a27c244dd665363741f70a695f8e945b
ms.sourcegitcommit: a22309174e617e59ab0cdd0a55abde38711a5f35
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/23/2018
---
# <a name="automatically-enroll-ios-devices-by-using-apples-device-enrollment-program"></a>Inscrever dispositivos iOS automaticamente através do Programa de Registo de Aparelho da Apple

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

> [!NOTE]
> ### <a name="temporary-user-interface-differences"></a>Diferenças na interface de utilizador temporárias
>
>As interfaces de utilizador para as funcionalidades descritas nesta página estão a ser atualizadas. Estas atualizações estão a ser implementadas em todas as contas de utilizador até ao fim de abril.
>
>Se a página **Inscrição de dispositivos** tiver um aspeto semelhante à imagem abaixo, a sua conta ainda não foi atualizada para a nova interface de utilizador e pode utilizar esta página de ajuda.
>
>![Antiga interface de utilizador do Intune](./media/appleenroll-oldui.png)
>
>Se a página **Inscrição de dispositivos** tiver um aspeto semelhante à imagem abaixo, tem as interfaces de utilizador atualizadas.  Aceda a [esta página de ajuda](device-enrollment-program-enroll-ios-newui.md).
>
>![Nova interface de utilizador do Intune](./media/appleenroll-newui.png)

Este tópico ajuda-o a ativar a inscrição de dispositivos iOS para dispositivos adquiridos através do [Programa de Inscrição de Dispositivos (DEP)](https://deploy.apple.com) da Apple. Pode ativar a inscrição de DEP para um grande número de dispositivos de forma remota. Pode enviar dispositivos, como iPhones e iPads, diretamente aos utilizadores. Quando o utilizador ativar o dispositivo, o Assistente de Configuração será executado com as predefinições configuradas e o dispositivo será inscrito na gestão.

Para ativar a inscrição DEP, deve utilizar os portais do Intune e do Apple DEP. É necessária uma lista de números de série ou um número de encomenda para poder atribuir dispositivos ao Intune para gestão. São criados os perfis de inscrição DEP com as definições aplicadas aos dispositivos durante a inscrição.

A inscrição DEP não funciona com o [gestor de inscrição de dispositivos](device-enrollment-manager-enroll.md). Também deve ter em atenção que o macOS atualmente não suporta o DEP.

## <a name="what-is-supervised-mode"></a>O que é o modo supervisionado?
A Apple incluiu o modo supervisionado pela primeira vez no iOS 5. Um dispositivo iOS no modo supervisionado pode ser gerido com mais controlos. Como tal, é especialmente útil para dispositivos pertencentes à empresa. Como parte do Programa de Inscrição de Dispositivos Apple (DEP), o Intune suporta a configuração de dispositivos para o modo supervisionado.

<!--
**Steps to enable enrollment programs from Apple**
1. [Get an Apple DEP token and assign devices](#get-the-apple-dep-token)
2. [Create an enrollment profile](#create-an-apple-enrollment-profile)
3. [Synchronize DEP-managed devices](#sync-managed-device)
4. [Assign DEP profile to devices](#assign-an-enrollment-profile-to-devices)
5. [Distribute devices to users](#end-user-experience-with-managed-devices)
-->
## <a name="prerequisites"></a>Pré-requisitos
- Dispositivos adquiridos através do [Programa de Inscrição de Dispositivos da Apple](http://deploy.apple.com)
- [Autoridade MDM](mdm-authority-set.md)
- [Certificado Push de MDM da Apple](apple-mdm-push-certificate-get.md)

> [!NOTE]
> A autenticação multifator (MFA) não funciona durante a configuração da inscrição DEP para a afinidade do utilizador. Depois da inscrição, a MFA funciona conforme esperado nos dispositivos. Os dispositivos não pedem aos utilizadores para alterar a palavra-passe ao iniciar sessão pela primeira vez. Além disso, não é pedido aos utilizadores com palavras-passes expiradas que reponham a palavra-passe durante a inscrição. Os utilizadores terão de repor a palavra-passe a partir de um dispositivo diferente.

## <a name="get-the-apple-dep-token"></a>Obter o token DEP da Apple

Antes de poder inscrever dispositivos iOS com DEP, precisa de um ficheiro token DEP (.p7m) da Apple. Este token permite ao Intune sincronizar informações sobre os dispositivos DEP que são propriedade da sua empresa. Também permite ao Intune carregar perfis de inscrição para a Apple e atribuir dispositivos a esses perfis.

Pode utilizar o portal de DEP da Apple para criar um token DEP. Também pode utilizar o portal de DEP para atribuir dispositivos ao Intune para gestão.

> [!NOTE]
> Se eliminar o token do portal clássico do Intune antes da migração para o Azure, o Intune poderá restaurar um token DEP da Apple eliminado. Pode eliminar novamente o token DEP do portal do Azure. Pode eliminar novamente o token DEP do portal do Azure.

**Passo 1. Transfira um certificado de chave pública do Intune obrigatório para criar um token DEP da Apple.**<br>

1. No [Intune, no portal do Azure](https://aka.ms/intuneportal), selecione **Inscrição de dispositivos** > **Inscrição da Apple** > **Token do Programa de Inscrição**.

  ![Painel Token do Programa de Inscrição na área de trabalho Certificados da Apple](./media/enrollment-program-token-add.png)

2. Selecione **Transferir a chave pública** para transferir e guardar o ficheiro da chave de encriptação (.pem) localmente. O ficheiro .pem é utilizado para pedir um certificado de relação de confiança a partir do portal do Programa de Inscrição de Dispositivos da Apple.

  ![Painel Token do Programa de Inscrição na área de trabalho Certificados da Apple para transferir a chave pública](./media/enrollment-program-token-download.png)

**Passo 2: Crie e transfira um token DEP da Apple.**<br>
1. Selecione **Criar um token através do Programa de Inscrição de Dispositivos da Apple** para abrir o portal Programa de Implementação da Apple e inicie sessão com o ID Apple da sua empresa. Pode utilizar este Apple ID para renovar o seu token DEP.
2.  No [portal dos Programas de Implementação](https://deploy.apple.com) da Apple, selecione **Começar** em **Programa de Registo de Aparelho**.

3. Na página **Gerir Servidores**, selecione **Adicionar Servidor MDM**.
4. Introduza o **Nome do Servidor MDM** e, em seguida, selecione **Seguinte**. O nome do servidor é uma referência para identificar o servidor de gestão de dispositivos móveis (MDM). Não é o nome nem o URL do Microsoft Intune.

   ![Adicionar um nome do servidor de MDM para DEP e clicar em Seguinte](./media/enrollment-program-token-add-server.png)

5. A caixa de diálogo **Adicionar &lt;NomeDoServidor&gt;** é aberta e pede para **Atualizar a Chave Pública**. Selecione **Escolher Ficheiro…** para carregar o ficheiro .pem e, em seguida, selecione **Seguinte**.  

6. Aceda a **Programas de Implementação** &gt; **Programa de Inscrição de Dispositivos** &gt; **Gerir Dispositivos**.
7. Em **Selecionar Dispositivos Por**, especifique a forma como os dispositivos são identificados:
    - **Número de Série**
    - **Número da Encomenda**
    - **Carregar Ficheiro CSV**.

   ![Especificar a opção Selecionar Dispositivos Por Número de Série, definir a opção Selecionar Ação como Atribuir ao Servidor e selecionar o Nome do Servidor](./media/enrollment-program-token-specify-serial.png)

8. Em **Selecionar Ação**, selecione **Atribuir ao Servidor**, selecione o &lt;NomeDoServidor&gt; especificado no Microsoft Intune e, em seguida, selecione **OK**. O portal da Apple atribui os dispositivos especificados para o servidor do Intune para gestão e, em seguida, apresenta a mensagem **Atribuição Concluída**.

   No portal da Apple, aceda a **Programas de Implementação** &gt; **Programa de Inscrição de Dispositivos** &gt; **Ver Histórico de Atribuições** para ver uma lista de dispositivos e a respetiva atribuição de servidores MDM.

**Passo 3: Introduza o ID Apple utilizado para criar o token do seu programa de inscrição.**<br>No Intune no portal do Azure, forneça o ID Apple para referência futura.

![Especificar o ID Apple utilizado para criar o token do programa de inscrição e procurar o token](./media/enrollment-program-token-apple-id.png)

**Passo 4: Aceda ao token do programa de inscrição para atualizar.**<br>
Aceda ao ficheiro de certificado (.pem), escolha **Abrir** e, em seguida, escolha **Carregar**. Com o certificado push, o Intune pode inscrever e gerir dispositivos iOS ao enviar políticas para dispositivos móveis inscritos. O Intune é sincronizado automaticamente na Apple para que possa ver a conta do seu programa de inscrição.

## <a name="create-an-apple-enrollment-profile"></a>Criar um perfil de inscrição da Apple

Agora que instalou o seu token, pode criar um perfil de inscrição para dispositivos DEP. Um perfil de inscrição de dispositivos especifica as definições aplicadas a um grupo de dispositivos durante a inscrição.

1. No [Intune, no portal do Azure](https://aka.ms/intuneportal), selecione **Inscrição de dispositivos** > **Inscrição da Apple**.
2. Em **Programa de Inscrição da Apple**, selecione **Perfis do Programa de Inscrição** > **Criar**.
3. Em **Criar Perfil de Inscrição**, introduza um **Nome** e **Descrição** para o perfil, para efeitos administrativos. Os utilizadores não verão estes detalhes. Pode utilizar este campo **Nome** para criar um grupo dinâmico no Azure Active Directory. Utilize o nome de perfil para definir o parâmetro enrollmentProfileName para atribuir dispositivos com este perfil de inscrição. Saiba mais sobre os [grupos dinâmicos do Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-groups-dynamic-membership-azure-portal#using-attributes-to-create-rules-for-device-objects).

  Na **Afinidade de Utilizador**, escolha se os dispositivos com este perfil se inscrevem com ou sem um utilizador atribuído.

 - **Inscrever com afinidade do utilizador** – selecione esta opção para os dispositivos que pertençam aos utilizadores e que precisem de utilizar o portal da empresa para utilizar serviços como a instalação de aplicações. A afinidade do utilizador necessita do [WS-Trust 1.3 Username/Mixed endpoint](https://technet.microsoft.com/library/adfs2-help-endpoints). [Saiba mais](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint).

 - **Inscrever sem afinidade do utilizador** – selecione esta opção para dispositivos não associados a um único utilizador. Utilize esta opção para dispositivos que efetuem tarefas sem aceder aos dados de utilizador locais. As aplicações, como o Portal da Empresa, não funcionam.

4. Selecione **Definições da Gestão de Dispositivos** para configurar as seguintes definições de perfil:

  ![Seleção do modo de gestão](./media/enrollment-program-profile-mode.png)
  - **Supervisionado** – um modo de gestão que ativa mais opções de gestão e desativa o Bloqueio de Ativação por predefinição. Se deixar a caixa de verificação em branco, fica com capacidades de gestão limitadas. A Microsoft recomenda a utilização do DEP como o mecanismo para ativar o modo supervisionado, especialmente para as organizações que estiverem a implementar um grande número de dispositivos iOS.

 > [!NOTE]
 > A configuração de um dispositivo para o modo supervisionado não pode ser efetuada através do Intune depois de um dispositivo ter sido inscrito. Após a inscrição, a única forma de ativar o modo supervisionado é ao ligar um dispositivo iOS a um Mac com um cabo USB e utilizar o Apple Configurator. Esta ação irá repor o dispositivo e configurá-lo no modo supervisionado. Saiba mais sobre este assunto nos [documentos do Apple Configurator](http://help.apple.com/configurator/mac/2.3). Um dispositivo supervisionado indicará que "Este iPhone é gerido pela Contoso." no ecrã de bloqueio e "Este iPhone é supervisionado. A Contoso consegue monitorizar o seu tráfego de Internet e localizar este dispositivo." em **Definições** > **Geral** > **Acerca de**.

  - **Inscrição bloqueada** – (é necessário o Modo de Gestão = supervisionado) Desativa as definições de iOS que poderiam permitir a remoção do perfil de gestão. Se deixar a caixa de verificação em branco, permitirá que o perfil de gestão seja removido do menu Definições. Após a inscrição de dispositivos, não poderá alterar esta definição sem efetuar uma reposição de fábrica do dispositivo.

  - **Ativar iPad Partilhado** – o Programa de Registo de Aparelho da Apple não suporta iPads partilhados.

  - **Permitir Emparelhamento** – especifica se os dispositivos iOS se podem sincronizar com computadores. Se escolher **Permitir o Apple Configurator por certificado**, terá de selecionar um certificado em **Certificados do Apple Configurator**.

  - **Certificados do Apple Configurator** – Se escolheu **Permitir o Apple Configurator por certificado** em **Permitir Emparelhamento**, selecione um Certificado do Apple Configurator a importar.

  Escolha **Guardar**.

5. Selecione **Definições do Assistente de Configuração** para configurar as seguintes definições de perfil:

  ![Seleção das definições de configuração com as definições disponíveis para um novo perfil do programa de registo](./media/enrollment-program-profile-settings.png)
  - **Nome do Departamento** – Aparece quando os utilizadores tocam em **Sobre a Configuração de** durante a ativação.

  - **N.º de Telefone do Departamento** – aparece quando o utilizador clica no botão **Preciso de Ajuda** durante a ativação.
    - **Opções do Assistente de Configuração** – estas definições opcionais podem ser configuradas mais tarde no menu **Definições** de iOS.
        - **Código de Acesso**
        - **Serviços de Localização**
        - **Restaurar**
        - **Apple ID**
        - **Termos e Condições**
        - **Touch ID**
        - **Apple Pay**
        - **Zoom**
        - **Siri**
        - **Dados de Diagnóstico**

    Escolha **Guardar**.

9. Para guardar as definições de perfil, selecione **Criar**, no painel **Criar Perfil de Inscrição**. O perfil de inscrição é apresentado na lista de Perfis de Inscrição do Programa de Inscrição da Apple.

## <a name="sync-managed-devices"></a>Sincronizar dispositivos geridos
Agora que o Intune tem permissão para gerir os seus dispositivos, pode sincronizar o Intune com a Apple para ver os seus dispositivos geridos no Intune no portal do Azure.

1. No [Intune, no portal do Azure](https://aka.ms/intuneportal), selecione **Inscrição de dispositivos** > **Inscrição da Apple** > **Dispositivos do Programa de Inscrição** > **Sincronizar**. A barra de progresso mostra a quantidade de tempo que tem de aguardar até pedir novamente a Sincronização.

  ![Nó do Programa de Registo de Aparelho selecionado coma ligação Sincronizar selecionada](./media/enrollment-program-device-sync.png)

2. No painel **Sincronizar**, selecione **Pedido de Sincronização**. A barra de progresso mostra a quantidade de tempo que tem de aguardar até pedir novamente a Sincronização.

   ![Painel Sincronizar com a ligação Pedido de Sincronização selecionada](./media/enrollment-program-device-request-sync.png)

   Para cumprir os termos da Apple para um tráfego aceitável do programa de inscrição, o Intune impõe as seguintes restrições:
     -  As sincronizações completas não podem ser executadas mais do que uma vez a cada sete dias. Durante uma sincronização completa, o Intune atualiza todos os números de série da Apple atribuídos ao Intune. Se for tentada uma sincronização completa no prazo de sete dias após a sincronização completa anterior, o Intune apenas atualiza os números de série que ainda não estejam listados no Intune.
     -  São atribuídos 15 minutos a qualquer pedido de sincronização para ser concluído. Durante este tempo ou até o pedido ser concluído com êxito, o botão **Sync (Sincronizar)** está desativado.
     - O Intune sincroniza os dispositivos novos e removidos com a Apple a cada 24 horas.

3. Na área de trabalho Dispositivos do Programa de Inscrição, selecione **Atualizar** para ver os seus dispositivos.

## <a name="assign-an-enrollment-profile-to-devices"></a>Atribuir um perfil de inscrição a dispositivos
Tem de atribuir um perfil do programa de inscrição aos dispositivos para poder inscrevê-los.

>[!NOTE]
>Também pode atribuir números de série a perfis a partir do painel **Números de Série da Apple**.

1. No [Intune, no portal do Azure](https://aka.ms/intuneportal), selecione **Inscrição de dispositivos** > **Inscrição da Apple** e, em seguida, selecione **Perfis do Programa de Inscrição**.
2. Na lista **Perfis do Programa de Inscrição**, selecione o perfil que pretende atribuir aos dispositivos e, em seguida, selecione **Atribuir dispositivos**.

 ![Atribuições de Dispositivos com a opção Atribuir selecionada](./media/enrollment-program-device-assign.png)

3. Selecione **Atribuir** e, em seguida, selecione os dispositivos aos quais pretende atribuir este perfil. Pode filtrar para ver os dispositivos disponíveis:
  - **não atribuído**
  - **qualquer**
  - **&lt;nome do perfil&gt;**
4. Selecione os dispositivos que pretende gerir. A caixa de verificação acima da coluna selecionará até 1000 dispositivos listados. Em seguida, clique em **Atribuir**. Para inscrever um número superior a 1000 dispositivos, repita os passos de atribuição até que todos os dispositivos tenham um perfil de inscrição associado.

  ![Botão Atribuir para atribuir um perfil do programa de registo no Intune](media/dep-profile-assignment.png)

## <a name="distribute-devices"></a>Distribuir dispositivos
Ativou a gestão e sincronização entre a Apple e o Intune e atribuiu um perfil para permitir a inscrição dos seus dispositivos DEP. Agora pode distribuir os dispositivos aos utilizadores. Os dispositivos com afinidade do utilizador necessitam que seja atribuída uma licença do Intune a cada utilizador. Os dispositivos sem afinidade do utilizador necessitam de uma licença de dispositivo. Um dispositivo ativado não poderá aplicar um perfil de inscrição até que seja realizada uma reposição de fábrica do dispositivo.

Veja [Inscrever o dispositivo iOS no Intune com o Programa de Registo de Aparelho](/intune-user-help/enroll-your-device-dep-ios).
