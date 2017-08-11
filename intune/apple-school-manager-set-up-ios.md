---
title: "Configurar a inscrição do Programa do Apple School Manager para dispositivos iOS"
titleSuffix: Intune on Azure
description: "Saiba como configurar a inscrição do programa do Apple School Manager para dispositivos iOS da empresa com o Intune\""
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 07/21/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7981a9c0-168e-4c54-9afd-ac51e895042c
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 7079a22afc04b5674eb8f12a2833961e86939a28
ms.sourcegitcommit: 79116d4c7f11bafc7c444fc9f5af80fa0b21224e
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/03/2017
---
# <a name="enable-ios-device-enrollment-with-apple-school-manager"></a>Ativar inscrição do dispositivo iOS com o Apple School Manager

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Este tópico ajuda os administradores de TI a ativar a inscrição de dispositivos iOS para dispositivos comprados através do programa [Apple School Manager](https://school.apple.com/). O Microsoft Intune pode implementar um perfil de inscrição via ligação sem fios que inscreve dispositivos associados ao Apple School Manager para gestão. O administrador nunca precisa de tocar em cada dispositivo gerido. O perfil de inscrição inclui definições de gestão que são aplicadas aos dispositivos durante a inscrição, incluindo opções do Assistente de Configuração.

**Passos de Inscrição no Apple School Manager**
1. [Obter um token do Apple School Manager e atribuir dispositivos](#get-the-apple-token-and-assign-devices)
2. [Criar um perfil de inscrição](#create-an-apple-enrollment-profile)
3. [Ligar a Sincronização de Dados da Escola](#connect-school-data-sync) (Opcional)
4. [Sincronizar dispositivos geridos pelo Apple School Manager](#sync-managed-devices)
5. [Atribuir o perfil do Apple School Manager aos dispositivos](#assign-a-profile-to-devices)
6. [Distribuir os dispositivos pelos utilizadores](#distribute-devices-to-users)

>[!NOTE]
>A inscrição do Apple School Manager não pode ser utilizada com o [DEP da Apple](device-enrollment-program-enroll-ios.md) ou com o [gestor de inscrição de dispositivos](device-enrollment-manager-enroll.md).

## <a name="get-the-apple-token-and-assign-devices"></a>Obter o token da Apple e atribuir dispositivos

Para poder inscrever dispositivos iOS da empresa através do Apple School Manager, precisa de ter um ficheiro de token (.p7m) da Apple. Este token permite que o Intune sincronize as informações sobre os dispositivos que participam no Apple School Manager. Também permite ao Intune efetuar carregamentos do perfil de inscrição para a Apple e atribuir dispositivos a esses perfis. Enquanto estiver no portal da Apple, também pode atribuir números de série de dispositivos para gerir.

**Pré-requisitos**
- [Certificado Push de MDM da Apple](apple-mdm-push-certificate-get.md)
- Inscrição na [Apple School Management](http://school.apple.com)

**Passo 1. transfira um certificado de chave pública do Intune, que é obrigatório para criar um token da Apple.**<br>
1. No [portal do Intune](https://aka.ms/intuneportal) no Azure, selecione **Inscrição de dispositivos** e, em seguida, **Token do programa de inscrição**.
2. No painel **Token do programa de inscrição**, selecione **Transferir a chave pública** para transferir e guardar o ficheiro da chave de encriptação (.pem) localmente. O ficheiro .pem é utilizado para pedir um certificado de relação de confiança a partir do portal do Apple School Manager.

**Passo 2: transfira um token e atribua dispositivos.**<br>
Selecione **Criar um token através do Apple School Manager** e inicie sessão com o ID Apple da sua empresa. Pode utilizar este ID Apple para renovar o seu token do Apple School Manager.

   1.  No [portal do Apple School Manager](https://school.apple.com), aceda aos **Servidores de MDM** e, em seguida, selecione **Adicionar Servidor de MDM** (superior direito).
   2.  Introduza o **Nome do Servidor de MDM**. O nome do servidor é uma referência para identificar o servidor de gestão de dispositivos móveis (MDM). Não é o nome nem o URL do Microsoft Intune.
   3.  Selecione **Carregar Ficheiro...**  no portal da Apple, procure o ficheiro .pem e selecione **Guardar Servidor de MDM** (inferior direito).
   4.  Selecione **Obter Token** e, em seguida, transfira o ficheiro do token do servidor (.p7m) para o computador.
   5. Vá para **Atribuições de Dispositivo** e **Escolher Dispositivo** através da introdução manual dos **Números de Série**, **Número do Pedido** ou **Carregar Ficheiro CSV**.
   6.   Escolha a ação **Atribuir ao servidor** e selecione o **Servidor de MDM** que criou.
   7. Especifique como irá **Escolher Dispositivos** e, em seguida, forneça as informações e detalhes do dispositivo.
   8. Selecione **Atribuir ao Servidor**, selecione o &lt;NomeDoServidor&gt; especificado para o Microsoft Intune e, em seguida, selecione **OK**.

**Passo 3: introduza o ID Apple utilizado para criar o seu token do Apple School Manager.**<br>Este ID deve ser utilizado para renovar o seu token do Apple School Manager e é armazenado para referência futura.

**Passo 4: localize e carregue o token.**<br>
Aceda ao ficheiro de certificado (.p7m), escolha **Abrir** e, em seguida, escolha **Carregar**. O Intune sincroniza automaticamente os seus dispositivos associados ao Apple School Manager da Apple.

## <a name="create-an-apple-enrollment-profile"></a>Criar um perfil de inscrição da Apple
Um perfil de inscrição de dispositivos especifica as definições aplicadas a um grupo de dispositivos durante a inscrição.

1. No portal do Intune, escolha **Inscrição de dispositivos** e, em seguida, **Inscrição da Apple**.
2. Em **Programa de Inscrição**, selecione **Perfis do Programa de Inscrição**.
3. No painel **Perfis do Programa de Inscrição**, selecione **Criar**.
4. No painel **Criar Perfil de Inscrição**, introduza um **Nome** e uma **Descrição** para o perfil apresentado no portal do Intune.
5. Na **Afinidade de Utilizador**, escolha se os dispositivos com este perfil se inscrevem com ou sem a afinidade do utilizador.

 - **Inscrever com afinidade do utilizador** – associa o dispositivo a um utilizador durante a configuração.

 >[!NOTE]
 >A autenticação multifator (MFA) não funciona durante a inscrição em dispositivos associados ao Apple School Manager com afinidade de utilizador. Depois da inscrição, a MFA funciona conforme esperado nestes dispositivos.

  O modo iPad Partilhado do Apple School Manager exige que o utilizador se inscreva sem a afinidade de utilizador.

 >[!NOTE]
    >O Apple School Manager com afinidade de utilizador necessita da ativação de um [ponto final de Nome de Utilizador/Misto WS-Trust 1.3](https://technet.microsoft.com/library/adfs2-help-endpoints) para pedir o token de utilizador. [Saiba mais sobre o WS-Trust 1.3](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint).

 - **Inscrever sem afinidade do utilizador** – O dispositivo não está afiliado a um utilizador. Utilize esta afiliação em dispositivos que efetuem tarefas sem aceder aos dados de utilizador locais. As aplicações que necessitarem de afinidade de utilizador (incluindo a aplicação Portal da Empresa utilizada para instalar aplicações de linha de negócio) não irão funcionar.

6. Selecione **Definições de Gestão de Dispositivos**. Estes itens são definidos durante a ativação e exigem uma reposição de fábrica para alteração. Configure as seguintes definições de perfil e, em seguida, selecione **Guardar**:

    - **Supervisionado** – um modo de gestão que ativa mais opções de gestão e desativa o Bloqueio de Ativação por predefinição. Se deixar a caixa de verificação em branco, fica com capacidades de gestão limitadas.

    - **Inscrição bloqueada** – (requer Modo de Gestão = Supervisionado) Desativa as definições de iOS que poderiam permitir a remoção do perfil de gestão. Se deixar a caixa de verificação em branco, permitirá que o perfil de gestão seja removido do menu Definições.

  - **iPad Partilhado** – (É necessário **Inscrever com Afinidade de Utilizador** e o modo **Supervisionado**.) Permite que múltiplos utilizadores iniciem sessão nos iPads inscritos com um ID Apple gerido. Os Apple IDs geridos são criados no portal do Apple School Manager.

  >[!NOTE]
  >Se o modo **Afinidade de Utilizador** for definido para **Com afinidade de utilizador** ou o modo **Supervisionado** for definido para **Desativado**, o modo iPad Partilhado será desativado para o perfil da inscrição.

  - **Utilizadores Máximos em Cache** – (Requer **iPad Partilhado** = **Sim**) Cria uma partição no dispositivo para cada utilizador. O valor recomendado é o número de alunos que provavelmente utilizará o dispositivo num período de tempo. Por exemplo, se seis alunos utilizam o dispositivo regularmente durante a semana, defina este número para seis.  

    - **Permitir Emparelhamento** – especifica se os dispositivos iOS se podem sincronizar com computadores. Se escolher **Permitir o Apple Configurator por certificado**, terá de escolher um certificado em **Certificados do Apple Configurator**.

    - **Certificados do Apple Configurator** – Se escolheu **Permitir o Apple Configurator por certificado** em **Permitir Emparelhamento**, selecione um Certificado do Apple Configurator a importar.

7. Selecione **Definições do Assistente de Configuração**, configure as seguintes definições de perfil e, em seguida, selecione **Guardar**:

    - **Nome do Departamento** – Aparece quando os utilizadores tocam em **Sobre a Configuração de** durante a ativação.

    - **Telefone do Departamento** – Aparece quando o utilizador clica no botão Preciso de ajuda durante a ativação.
    - **Opções do Assistente de Configuração** – Se excluídas das opções do Assistente de Configuração, estas definições podem ser configuradas mais tarde no menu **Definições** de iOS.
        - **Código de Acesso** – pedido de código de acesso durante a ativação. Solicite sempre um código de acesso, a menos que o dispositivo esteja protegido ou tenha o acesso controlado de outra forma (ou seja, modo de local público que restringe o dispositivo a uma aplicação).
        - **Serviços de Localização** – se ativado, o Assistente de Configuração solicita o serviço durante a ativação
        - **Restaurar** – se estiver ativado, o Assistente de Configuração solicita a cópia de segurança de iCloud durante a ativação
        - **Apple ID** – Se estiver ativado, o iOS pede aos utilizadores um Apple ID quando o Intune tenta instalar uma aplicação sem um ID. É necessário um Apple ID para transferir aplicações iOS da App Store, incluindo as aplicações instaladas pelo Intune.
        - **Termos e Condições** – se ativado, o Assistente de Configuração solicita aos utilizadores que aceitem os termos e condições da Apple durante a ativação
        - **Touch ID** – se ativado, o Assistente de Configuração solicita este serviço durante a ativação
        - **Apple Pay** – se ativado, o Assistente de Configuração solicita este serviço durante a ativação
        - **Zoom** – se ativado, o Assistente de Configuração solicita este serviço durante a ativação
        - **Siri** – se ativado, o Assistente de Configuração solicita este serviço durante a ativação
        - **Dados de Diagnóstico** – Se ativado, o Assistente de Configuração solicita este serviço durante a ativação

8. Para guardar as definições de perfil, selecione **Criar**, no painel **Criar Perfil de Inscrição**.

## <a name="connect-school-data-sync"></a>Ligar a Sincronização de Dados da Escola
(Opcional) O Apple School Manager suporta a sincronização de dados de lista de turma para o Azure Active Directory (AD) ao utilizar o Microsoft School Data Sync (SDS). Conclua os seguintes passos para utilizar SDS para sincronizar os dados da escola.

1. No painel **Token do Programa de Inscrição**, selecione a faixa de informações a azul ou **Ligar SDS**.
2. Selecione **Permitir que a Sincronização de Dados da Escola da Microsoft utilize este token** ao definir como **Permitir**. Esta configuração permite que o Intune se ligue à SDS no Office 365.
3. Para ativar uma ligação entre o Apple School Manager e o Azure AD, selecione **Configurar o Microsoft School Data Sync**. Saiba mais sobre [como configurar a Sincronização de Dados da Escola](https://support.office.com/article/Install-the-School-Data-Sync-Toolkit-8e27426c-8c46-416e-b0df-c29b5f3f62e1).
4. Clique em **OK** para guardar e continuar.

## <a name="sync-managed-devices"></a>Sincronizar dispositivos geridos
Agora que foi atribuída a permissão ao Intune para gerir os dispositivos associados ao Apple School Manager, pode sincronizar o Intune com o serviço Apple para ver os dispositivos geridos no portal do Intune.

1. No portal do Intune, escolha **Inscrição de dispositivos** e, em seguida, **Inscrição da Apple**.
2. Em **Programa de Inscrição de Dispositivos**, selecione **Sincronizar**. A barra de progresso mostra a quantidade de tempo que tem de aguardar até pedir novamente a Sincronização.

    Para estar em conformidade com os termos da Apple para o tráfego aceitável, o Intune impõe as seguintes restrições:
     -  As sincronizações completas não podem ser executadas mais do que uma vez a cada sete dias. Durante uma sincronização completa, o Intune atualiza cada número de série que a Apple tenha atribuído ao Intune, quer o número tenha sido ou não sincronizado anteriormente. Se for tentada uma sincronização completa no prazo de sete dias após a sincronização completa anterior, o Intune apenas atualiza os números de série que ainda não estejam listados no Intune.
     -  São atribuídos 15 minutos a qualquer pedido de sincronização para ser concluído. Durante este tempo ou até o pedido ser concluído com êxito, o botão **Sync (Sincronizar)** está desativado.

>[!NOTE]
>Também pode atribuir números de série do Apple School Manager aos perfis do painel **Programa de Inscrição de Dispositivos**.

## <a name="assign-a-profile-to-devices"></a>Atribuir um perfil a dispositivos
É necessário atribuir um perfil do programa de inscrição aos dispositivos associados ao Apple School Manager geridos pelo Intune antes de estes serem inscritos.

1. No portal do Intune, selecione **Inscrição de dispositivos** > **Inscrição da Apple** e, em seguida, selecione **Perfis do Programa de Inscrição**.
2. Na lista de **Perfis do Programa de Inscrição**, selecione o perfil que pretende atribuir aos dispositivos e, em seguida, selecione **Atribuições de Dispositivos**
3. Selecione **Atribuir** e, em seguida, selecione os dispositivos associados ao Apple School Manager que pretende atribuir a este perfil. Pode filtrar para ver os dispositivos disponíveis:
  - **não atribuído**
  - **qualquer**
  - **&lt;Nome do perfil do Apple School Manager&gt;**
4. Selecione os dispositivos que pretende gerir. A caixa de seleção acima da coluna seleciona até 1000 dispositivos listados. Clique em **Atribuir**. Para inscrever um número superior a 1000 dispositivos, repita os passos de atribuição até que todos os dispositivos tenham um perfil de inscrição associado.

## <a name="distribute-devices-to-users"></a>Distribuir dispositivos pelos utilizadores

Já pode distribuir os dispositivos pertencentes à empresa aos utilizadores. Quando um dispositivo iOS associado ao Apple School Manager é ligado, é inscrito na gestão pelo Intune. Se o dispositivo foi ativado e estiver a ser utilizado, não poderá aplicar o perfil até ser realizada uma reposição de fábrica no dispositivo.

### <a name="how-users-install-and-use-the-company-portal-on-their-devices"></a>Como os utilizadores instalam e utilizam o Portal da Empresa nos dispositivos deles

Os dispositivos configurados com a afinidade de utilizador podem instalar e executar a aplicação Portal da Empresa para transferir aplicações e gerir dispositivos. Assim que os utilizadores recebem os respetivos dispositivos, têm de executar o Assistente de Configuração e instalar a aplicação Portal da Empresa.
