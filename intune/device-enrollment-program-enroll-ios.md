---
title: Inscrever dispositivos iOS – Programa de Registo de Aparelho
titleSuffix: Microsoft Intune
description: Saiba como inscrever dispositivos iOS pertencentes à empresa através do Programa de Registo de Aparelho.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/07/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 7ddbf360-0c61-11e8-ba89-0ed5f89f718b
ms.reviewer: tisilver
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: cd4a195af0b3be5038a34b44606abcddf02c5a1e
ms.sourcegitcommit: 74911a263944f2dbd9b754415ccda6c68dae0759
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/17/2019
ms.locfileid: "71071561"
---
# <a name="automatically-enroll-ios-devices-with-apples-device-enrollment-program"></a>Inscrever automaticamente dispositivos iOS com o Programa de Inscrição de Dispositivos da Apple

Pode configurar o Intune para inscrever os dispositivos iOS adquiridos através do [Programa de Registo de Aparelho (DEP)](https://deploy.apple.com) da Apple. O DEP permite-lhe inscrever um grande número de dispositivos de forma remota. Os dispositivos como iPhones e iPads podem ser enviados diretamente aos utilizadores. Quando o utilizador ativar o dispositivo, o Assistente de Configuração será executado com as predefinições configuradas e o dispositivo será inscrito na gestão.

Para ativar a inscrição DEP, deve utilizar os portais do Intune e do Apple DEP. É necessária uma lista de números de série ou um número de encomenda para poder atribuir dispositivos ao Intune para gestão. São criados os perfis de inscrição DEP com as definições aplicadas aos dispositivos durante a inscrição.

A propósito, a inscrição DEP não funciona com o [gestor de inscrição de dispositivos](device-enrollment-manager-enroll.md).

## <a name="dep-and-the-company-portal"></a>DEP e o Portal da Empresa
Os registros de DEP não são compatíveis com a versão da loja de aplicativos do aplicativo Portal da Empresa. Você pode conceder aos usuários acesso ao aplicativo Portal da Empresa em um dispositivo DEP. Para conceder a eles acesso, envie por push o aplicativo para o dispositivo usando **instalar portal da empresa com VPP** (Volume Purchase Program) no perfil de Dep. Para obter mais informações, consulte [registrar automaticamente dispositivos IOS com o programa de registro de dispositivos da Apple](device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile).

 Você pode instalar o aplicativo Portal da Empresa em dispositivos já registrados com o DEP. Para fazer isso, implante o aplicativo Portal da Empresa por meio do Intune com uma [política de configuração de aplicativo](app-configuration-policies-use-ios.md) aplicada.

## <a name="what-is-supervised-mode"></a>O que é o modo supervisionado?
A Apple incluiu o modo supervisionado pela primeira vez no iOS 5. Um dispositivo iOS no modo supervisionado pode ser gerido com mais controlos. Como tal, é especialmente útil para dispositivos pertencentes à empresa. Como parte do Programa de Inscrição de Dispositivos Apple (DEP), o Intune suporta a configuração de dispositivos para o modo supervisionado. 

O suporte para dispositivos DEP não supervisionados foi preterido no iOS 11. No iOS 11 e posterior, os dispositivos configurados no DEP devem sempre ser supervisionados. O sinalizador is_supervised do DEP será ignorado num lançamento futuro do iOS.

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
- [Autoridade de Gestão de Dispositivos Móveis (MDM)](mdm-authority-set.md)
- [Certificado Push de MDM da Apple](apple-mdm-push-certificate-get.md)

## <a name="get-an-apple-dep-token"></a>Obter um token DEP da Apple

Antes de poder inscrever dispositivos iOS com DEP, precisa de um ficheiro token DEP (.p7m) da Apple. Este token permite ao Intune sincronizar informações sobre os dispositivos DEP que são propriedade da sua empresa. Também permite ao Intune carregar perfis de inscrição para a Apple e atribuir dispositivos a esses perfis.

Pode utilizar o portal de DEP da Apple para criar um token DEP. Também pode utilizar o portal de DEP para atribuir dispositivos ao Intune para gestão.

> [!NOTE]
> Se eliminar o token do portal clássico do Intune antes da migração para o Azure, o Intune poderá restaurar um token DEP da Apple eliminado. Pode eliminar novamente o token DEP do portal do Azure.

### <a name="step-1-download-the-intune-public-key-certificate-required-to-create-the-token"></a>Passo 1. Transfira o certificado de chave pública do Intune, que é obrigatório para criar o token.

1. No [Intune no portal do Azure](https://aka.ms/intuneportal), selecione **Inscrição de dispositivos** > **Inscrição da Apple** > **Tokens do Programa de Inscrição** > **Adicionar**.

    ![Obtenha um token do programa de inscrição.](./media/device-enrollment-program-enroll-ios/image01.png)

2. Conceda permissão à Microsoft para enviar informações sobre o utilizador e o dispositivo à Apple, ao selecionar **Concordo**.

   ![Captura de ecrã a mostrar o painel Token do Programa de Inscrição, na área de trabalho Certificados da Apple, para transferir a chave pública.](./media/device-enrollment-program-enroll-ios-newui/add-enrollment-program-token-pane.png)

3. Selecione **Transferir a chave pública** para transferir e guardar o ficheiro da chave de encriptação (.pem) localmente. O ficheiro .pem é utilizado para pedir um certificado de relação de confiança a partir do portal do Programa de Inscrição de Dispositivos da Apple.


### <a name="step-2-use-your-key-to-download-a-token-from-apple"></a>Passo 2. Utilize a sua chave para transferir um token a partir da Apple.

1. Selecione **Criar um token para o Programa de Registo de Aparelho da Apple** para abrir o portal Programa de Implementação da Apple e inicie sessão com o Apple ID da sua empresa. Pode utilizar este Apple ID para renovar o seu token DEP.
2. No [portal dos Programas de Implementação](https://deploy.apple.com) da Apple, selecione **Começar** em **Programa de Registo de Aparelho**.

3. Na página **Gerir Servidores**, selecione **Adicionar Servidor MDM**.
4. Introduza o **Nome do Servidor MDM** e, em seguida, selecione **Seguinte**. O nome do servidor é uma referência para identificar o servidor de gestão de dispositivos móveis (MDM). Não é o nome nem o URL do servidor do Microsoft Intune.

5. A caixa de diálogo **Adicionar &lt;NomeDoServidor&gt;** é aberta e pede para **Atualizar a Chave Pública**. Selecione **Escolher Ficheiro…** para carregar o ficheiro .pem e, em seguida, selecione **Seguinte**.

6. Aceda a **Programas de Implementação** &gt; **Programa de Inscrição de Dispositivos** &gt; **Gerir Dispositivos**.
7. Em **Selecionar Dispositivos Por**, especifique a forma como os dispositivos são identificados:
    - **Número de Série**
    - **Número da Encomenda**
    - **Carregar Ficheiro CSV**.

   ![Captura de ecrã a mostrar a especificação de dispositivos selecionados pelo número de série, a definição da ação de seleção como Atribuir ao servidor e a seleção do nome do servidor.](./media/enrollment-program-token-specify-serial.png)

8. Em **Selecionar Ação**, selecione **Atribuir ao Servidor**, selecione o &lt;NomeDoServidor&gt; especificado no Microsoft Intune e, em seguida, selecione **OK**. O portal da Apple atribui os dispositivos especificados para o servidor do Intune para gestão e, em seguida, apresenta a mensagem **Atribuição Concluída**.

   No portal da Apple, aceda a **Programas de Implementação** &gt; **Programa de Inscrição de Dispositivos** &gt; **Ver Histórico de Atribuições** para ver uma lista de dispositivos e a respetiva atribuição de servidores MDM.

### <a name="step-3-save-the-apple-id-used-to-create-this-token"></a>Passo 3: Guarde o Apple ID que serviu para criar este token.

No Intune no portal do Azure, forneça o ID Apple para referência futura.

![Captura de ecrã a mostrar a especificação do ID Apple utilizado para criar o token do programa de inscrição e o acesso ao token do programa de inscrição.](./media/device-enrollment-program-enroll-ios/image03.png)

### <a name="step-4-upload-your-token-and-choose-scope-tags"></a>Passo 4: Carregue o token e escolha as etiquetas de âmbito.

1. Na caixa **Token da Apple**, procure o ficheiro de certificado (.pem) e escolha **Abrir**.
2. Se quiser aplicar [etiquetas de âmbito](scope-tags.md) a este token DEP, escolha **Âmbito (etiquetas)** e selecione as etiquetas de âmbito que pretende. As etiquetas de âmbito aplicadas a um token serão herdadas pelos perfis e dispositivos adicionados a este token.
3. Selecione **Criar**.

Com o certificado push, o Intune pode inscrever e gerir dispositivos iOS ao enviar políticas para dispositivos móveis inscritos. O Intune é sincronizado automaticamente na Apple para que possa ver a conta do seu programa de inscrição.

## <a name="create-an-apple-enrollment-profile"></a>Criar um perfil de inscrição da Apple

Agora que instalou o seu token, pode criar um perfil de inscrição para dispositivos DEP. Um perfil de inscrição de dispositivos especifica as definições aplicadas a um grupo de dispositivos durante a inscrição.

> [!NOTE]
> Os dispositivos serão bloqueados se não houver licenças Portal da Empresa suficientes para um token VPP ou se o token tiver expirado. O Intune apresentará um alerta quando um token estiver prestes a expirar ou se existirem poucas licenças.
 

1. No Intune no portal do Azure, escolha **Inscrição de dispositivos** > **Inscrição da Apple** > **Tokens do programa de inscrição**.
2. Selecione um token, escolha **perfis** > **Criar perfil** > **Ios**.

    ![Crie uma captura de ecrã de perfil.](./media/device-enrollment-program-enroll-ios/image04.png)

3. Na página **noções básicas** , insira um **nome** e uma **Descrição** para o perfil para fins administrativos. Os utilizadores não verão estes detalhes. Pode utilizar este campo **Nome** para criar um grupo dinâmico no Azure Active Directory. Utilize o nome de perfil para definir o parâmetro enrollmentProfileName para atribuir dispositivos com este perfil de inscrição. Saiba mais sobre os [grupos dinâmicos do Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership#rules-for-devices).

    ![Nome do perfil e descrição.](./media/device-enrollment-program-enroll-ios/image05.png)

4. Selecione **avançar: Configurações**de gerenciamento de dispositivo.

5. Na **Afinidade do Utilizador**, escolha se os dispositivos com este perfil têm de ser inscritos com ou sem um utilizador atribuído.
    - **Inscrever com Afinidade de Utilizador**: selecione esta opção para os dispositivos que pertençam aos utilizadores e que queiram utilizar o Portal da Empresa para serviços como a instalação de aplicações. Se estiver a utilizar o ADFS e o perfil de inscrição tiver **Autenticar com o Portal da Empresa em vez do Assistente de Configuração** definido como **Não**, o [ponto final WS-Trust 1.3 Username/Mixed](https://technet.microsoft.com/library/adfs2-help-endpoints) [Saiba mais](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint) é necessário.

    - **Inscrever sem Afinidade do Utilizador** – escolha esta opção para dispositivos não associados a um único utilizador. Use esta opção para dispositivos que não acessam dados de usuário local. As aplicações, como o Portal da Empresa, não funcionam.

5. Se tiver escolhido **Inscrever com Afinidade de Utilizador**, poderá permitir que os utilizadores se autentiquem no Portal da Empresa em vez de o fazerem no Assistente de Configuração da Apple.

    ![Autentique com o Portal da Empresa.](./media/device-enrollment-program-enroll-ios/authenticatewithcompanyportal.png)

    > [!NOTE]
    > Se você quiser fazer o seguinte, defina **selecionar onde os usuários devem se autenticar** para **portal da empresa**.
    >    - utilizar a autenticação multifator
    >    - pedir aos utilizadores para alterar a palavra-passe ao iniciar sessão pela primeira vez
    >    - Pedir aos utilizadores para reporem as respetivas palavras-passe expiradas durante a inscrição
    >
    > Estas ações não são suportadas durante a autenticação com o Assistente de Configuração da Apple.

6. Se você escolher **portal da empresa** para **selecionar onde os usuários devem se autenticar**, poderá usar um token VPP para instalar automaticamente o portal da empresa no dispositivo. Neste caso, o utilizador não tem de fornecer um ID Apple. Para instalar o Portal da Empresa com um token VPP, selecione um token em **Instalar Portal da Empresa com o VPP**. Requer que o Portal da Empresa já tenha sido adicionado ao token VPP. Não configurar uma política para exigir o aplicativo para os usuários, o Intune instalará automaticamente o Portal da Empresa em dispositivos com esse perfil de registro aplicado. Certifique-se de que o token não expira e que tem licenças de dispositivos suficientes para a aplicação Portal da Empresa. Se o token expirar ou se esgotar as licenças, o Intune instalará o Portal da Empresa a partir da App Store e pedirá um ID Apple. 

    > [!NOTE]
    > Quando **selecionar onde os usuários devem se autenticar** é **portal da empresa**, certifique-se de que o processo de registro do dispositivo seja executado nas primeiras 24 horas do portal da empresa que está sendo baixado para o dispositivo Dep. Caso contrário, o registro pode falhar e uma redefinição de fábrica será necessária para registrar o dispositivo.
    
    ![Captura de ecrã a mostrar a opção Instalar Portal da Empresa com o VPP.](./media/device-enrollment-program-enroll-ios/install-cp-with-vpp.png)

7. Se você escolheu o **Assistente de configuração** para **selecionar onde os usuários devem se autenticar**, mas também deseja usar o acesso condicional ou implantar aplicativos da empresa nos dispositivos, você deve instalar o portal da empresa nos dispositivos. Para fazer isso, escolha **Sim** para **instalar portal da empresa**.  Se você quiser que os usuários recebam o Portal da Empresa sem precisar se autenticar na App Store, opte por **instalar portal da empresa com o VPP** e selecione um token VPP. Certifique-se de que o token não expire e que você tenha licenças de dispositivo suficientes para que o aplicativo de Portal da Empresa seja implantado corretamente.

8. Se tiver escolhido um token para **Instalar o Portal da Empresa com o VPP**, poderá bloquear o dispositivo no Modo de Aplicação Única (nomeadamente, a aplicação do Portal da Empresa) logo após a conclusão do Assistente de Configuração. Selecione **Sim** para **Execute o Portal da Empresa no Modo de Aplicação Única até à autenticação** para definir esta opção. Para utilizar o dispositivo, tem de autenticar primeiro o utilizador ao iniciar sessão com o Portal da Empresa.

    A autenticação multifator não tem suporte em um único dispositivo bloqueado no modo de aplicativo único. Essa limitação existe porque o dispositivo não pode alternar para um aplicativo diferente para concluir o segundo fator de autenticação. Portanto, se você quiser autenticação multifator em um dispositivo de modo de aplicativo único, o segundo fator deverá estar em um dispositivo diferente.

    Esta funcionalidade só é suportada para iOS 11.3.1 e posterior.

   ![Captura de ecrã do modo de aplicação única.](./media/device-enrollment-program-enroll-ios/single-app-mode.png)

9. Se você quiser que os dispositivos que usam esse perfil sejam supervisionados, escolha **Sim** para **supervisionado**.

    ![Captura de ecrã a mostrar a opção Definições de Gestão de Dispositivos.](./media/device-enrollment-program-enroll-ios/supervisedmode.png)

    Os dispositivos **supervisionados** proporcionam mais opções de gestão e desativam o Bloqueio de Ativação por predefinição. A Microsoft recomenda a utilização do DEP como o mecanismo para ativar o modo supervisionado, especialmente se estiver a implementar um grande número de dispositivos iOS.

    Os utilizadores são notificados de que os seus dispositivos são supervisionados de duas formas:

   - O ecrã de bloqueio indica: “Este iPhone é gerido pelo Contoso.”
   - O ecrã **Definições** > **Geral** > **Acerca de** indica: “Este iPhone é supervisionado.” A Contoso consegue monitorizar o seu tráfego de Internet e localizar este dispositivo."

     > [!NOTE]
     > Um dispositivo inscrito sem supervisão só pode ser reposto para supervisionado com o Apple Configurator. Repor o dispositivo desta forma requer ligar um dispositivo iOS a um Mac com um cabo USB. Saiba mais sobre este assunto nos [documentos do Apple Configurator](http://help.apple.com/configurator/mac/2.3).

10. Escolha se quer a inscrição bloqueada para os dispositivos com este perfil. A **Inscrição bloqueada** desativa as definições do iOS que permitem que o perfil de gestão seja removido do menu **Definições**. Após a inscrição de dispositivos, não poderá alterar esta definição sem apagar os dados do dispositivo. Esses dispositivos têm de ter o Modo de Gestão **Supervisionado** definido como *Sim*. 

11. Escolha se quer que os dispositivos com este perfil consigam **Sincronizar com computadores**. Se escolher **Permitir o Apple Configurator por certificado**, terá de escolher um certificado em **Certificados do Apple Configurator**.

12. Se tiver escolhido **Permitir o Apple Configurator por certificado** no passo anterior, escolha um Certificado do Apple Configurator a importar.

13. Você pode especificar um formato de nomenclatura para dispositivos que são aplicados automaticamente quando eles se registram e após cada check-in sucessivo. Para criar um modelo de nomenclatura, selecione **Sim** em **Aplicar modelo de nome de dispositivo**. Em seguida, na caixa **Modelo de Nome do Dispositivo**, introduza o modelo a utilizar para os nomes com este perfil. Pode especificar um formato de modelo para incluir o tipo de dispositivo e o número de série. 

14. escolha **Seguinte: Personalização**do assistente de configuração.

15. Na página **personalização do assistente de configuração** , defina as seguintes configurações de perfil: ![Personalização do Assistente de Configuração.](./media/device-enrollment-program-enroll-ios/setupassistantcustom.png)


    | Definições do departamento | Descrição |
    |---|---|
    | <strong>Nome do Departamento</strong> | É apresentado quando os utilizadores tocam em <strong>Acerca da Configuração</strong> durante a ativação. |
    |    <strong>Número de Telefone do Departamento</strong>     | Aparece quando o utilizador clica no botão <strong>Preciso de Ajuda</strong> durante a ativação. |

    Pode optar por ocultar os ecrãs do Assistente de configuração no dispositivo durante a configuração do utilizador.
    - Se selecionar **Ocultar**, o ecrã não será apresentado durante a configuração. Depois de configurar o dispositivo, o utilizador ainda pode aceder ao menu **Definições** para configurar a funcionalidade.
    - Se selecionar **Mostrar**, o ecrã será apresentado durante a configuração. Por vezes, o utilizador pode ignorar o ecrã sem realizar qualquer ação. No entanto, terá a possibilidade de aceder ao menu **Definições** do dispositivo para configurar a funcionalidade. 


    | Definições do ecrã Assistente de Configuração | Se selecionar **Mostrar** durante a configuração, o dispositivo irá… |
    |------------------------------------------|------------------------------------------|
    | <strong>Código de Acesso</strong> | Pedir um código de acesso ao utilizador. Solicite sempre um código de acesso para os dispositivos não protegidos, a menos que o acesso seja controlado de outra forma (ou seja, modo de quiosque que restringe o dispositivo a uma aplicação). |
    | <strong>Serviços de Localização</strong> | Pedir ao utilizador a respetiva localização. |
    | <strong>Restaurar</strong> | Exibir a tela de dados do & de aplicativos. Este ecrã permite que o utilizador opte por restaurar ou transferir os dados da Cópia de Segurança do iCloud quando configurar o dispositivo. |
    | <strong>iCloud e Apple ID</strong> | Dê ao usuário as opções para entrar com sua ID da Apple e usar o iCloud.                         |
    | <strong>Termos e Condições</strong> | Pedir ao utilizador para aceitar os termos e condições da Apple. |
    | <strong>Touch ID</strong> | Apresentar ao utilizador a opção para configurar a identificação através de impressão digital no dispositivo. |
    | <strong>Apple Pay</strong> | Apresentar ao utilizador a opção para configurar o Apple Pay no dispositivo. |
    | <strong>Zoom</strong> | Apresentar ao utilizador a opção para aumentar o zoom quando este configurar o dispositivo. |
    | <strong>Siri</strong> | Apresentar ao utilizador a opção para configurar o Siri. |
    | <strong>Dados de Diagnóstico</strong> | Exiba a tela de diagnóstico para o usuário. Este ecrã permite que o utilizador opte por enviar dados de diagnóstico para a Apple. |
    | <strong>Sinal de Apresentação</strong> | Apresentar ao utilizador a opção para ativar o Sinal de Apresentação. |
    | <strong>Privacidade</strong> | Apresentar o ecrã Privacidade ao utilizador. |
    | <strong>Migração do Android</strong> | Apresentar ao utilizador a opção para migrar os dados de um dispositivo Android. |
    | <strong>iMessage e FaceTime</strong> | Dê ao usuário a opção de configurar iMessage e FaceTime. |
    | <strong>Integração</strong> | Apresentar ecrãs informativos de integração para formação do utilizador, como a Folha de Capa, o Multitasking e o Centro de Controlo. |
    | <strong>Migração de Relógio</strong> | Apresentar ao utilizador a opção para migrar os dados de um dispositivo de relógio. |
    | <strong>Tempo do Ecrã</strong> | Apresentar o ecrã Tempo do Ecrã. |
    | <strong>Atualização de Software</strong> | Apresentar o ecrã de atualização de software obrigatório. |
    | <strong>Configuração do SIM</strong> | Apresentar ao utilizador a opção para adicionar um plano de dados móveis. |
    | <strong>Aparência</strong> | Apresentar o ecrã Aspeto ao utilizador. |
    | <strong>Idioma Express</strong>| Exiba a tela da linguagem expressa para o usuário. |
    | <strong>Idioma preferencial</strong> | Dê ao usuário a opção de escolher seu **idioma preferencial**. |
    | <strong>Migração de dispositivo para dispositivo</strong> | Conceda ao usuário a opção de migrar dados de seu dispositivo antigo para este dispositivo.|
    

16. Escolha **Avançar** para ir para a página **revisar + criar** .

17. Para guardar o perfil, escolha **Criar**.

## <a name="sync-managed-devices"></a>Sincronizar dispositivos geridos
Agora que o Intune tem permissão para gerir os seus dispositivos, pode sincronizar o Intune com a Apple para ver os seus dispositivos geridos no Intune no portal do Azure.

1. No Intune no portal do Azure, escolha **Inscrição de dispositivos** > **Inscrição da Apple** > **Tokens do programa de inscrição** > escolha um token na lista > **Dispositivos** > **Sincronizar**. ![Captura de ecrã do nó Dispositivos do Programa de Inscrição e a ligação Sincronizar.](./media/device-enrollment-program-enroll-ios/image06.png)

   Para cumprir os termos da Apple para um tráfego aceitável do programa de inscrição, o Intune impõe as seguintes restrições:
   - As sincronizações completas não podem ser executadas mais do que uma vez a cada sete dias. Durante uma sincronização completa, o Intune obtém a lista atualizada completa de números de série atribuídos ao servidor de MDM da Apple ligado ao Intune. Se um dispositivo DEP for eliminado do portal do Intune, a sua atribuição deverá ser anulada no servidor MDM da Apple no portal DEP. Se a atribuição não for anulada, não será importado novamente para o Intune até que a sincronização completa seja executada.   
   - É executa automaticamente uma sincronização a cada 24 horas. Também pode sincronizar ao clicar no botão **Sincronizar** (não mais do que uma vez a cada 15 minutos). Todos os pedidos de sincronização têm 15 minutos para serem concluídos. O botão **Sincronizar** está desativado até a sincronização ser concluída. Esta sincronização irá atualizar o estado do dispositivo existente e importar novos dispositivos atribuídos ao servidor de MDM da Apple.   


## <a name="assign-an-enrollment-profile-to-devices"></a>Atribuir um perfil de inscrição a dispositivos
Tem de atribuir um perfil do programa de inscrição aos dispositivos para poder inscrevê-los.

>[!NOTE]
>Também pode atribuir números de série a perfis a partir do painel **Números de Série da Apple**.

1. No Intune no portal do Azure, escolha **Inscrição de dispositivos**  >  **Inscrição da Apple**  >  **Tokens do programa de inscrição** > escolha um token na lista.
2. Escolha **Dispositivos** > escolha dispositivos na lista > **Atribuir perfil**.
3. Em **Atribuir perfil**, escolha um perfil para os dispositivos > **Atribuir**.

### <a name="assign-a-default-profile"></a>Atribuir um perfil predefinido

Pode escolher um perfil predefinido a aplicar a todos os dispositivos que inscrever com um token específico.

1. No Intune no portal do Azure, escolha **Inscrição de dispositivos**  >  **Inscrição da Apple**  >  **Tokens do programa de inscrição** > escolha um token na lista.
2. Escolha **Definir o Perfil Predefinido**, escolha um perfil na lista pendente e, em seguida, escolha **Guardar**. Este perfil será aplicado a todos os dispositivos inscritos com o token.

## <a name="distribute-devices"></a>Distribuir dispositivos
Ativou a gestão e sincronização entre a Apple e o Intune e atribuiu um perfil para permitir a inscrição dos seus dispositivos DEP. Agora pode distribuir os dispositivos aos utilizadores. Os dispositivos com afinidade do utilizador necessitam que seja atribuída uma licença do Intune a cada utilizador. Os dispositivos sem afinidade do utilizador necessitam de uma licença de dispositivo. Um dispositivo ativado não poderá aplicar um perfil de inscrição até que os dados do mesmo sejam apagados.

Veja [Inscrever o dispositivo iOS no Intune com o Programa de Registo de Aparelho](/intune-user-help/enroll-your-device-dep-ios).

## <a name="renew-a-dep-token"></a>Renovar um token de DEP  
1. Aceda a deploy.apple.com.  
2. Em **Gerir Servidores**, selecione o servidor de MDM associado ao ficheiro de token que pretende renovar.
3. Selecione **Gerar Novo Token**.

    ![Captura de ecrã a mostrar a criação de um novo token.](./media/device-enrollment-program-enroll-ios/generatenewtoken.png)

4. Selecione **Token do Seu Servidor**.  
5. No [Intune no portal do Azure](https://aka.ms/intuneportal), selecione **Inscrição de dispositivos** > **Inscrição da Apple** > **Tokens do programa de inscrição** > selecione o token.
    ![Captura de ecrã a mostrar tokens de programas de inscrição.](./media/device-enrollment-program-enroll-ios/enrollmentprogramtokens.png)

6. Selecione **Renovar token** e introduza o ID Apple utilizado para criar o token original.  
    ![Captura de ecrã a mostrar a criação do novo token.](./media/device-enrollment-program-enroll-ios/renewtoken.png)

8. Carregue o token transferido recentemente.  
9. Selecione **Renovar token**. Verá a confirmação de que o token foi renovado.   
    ![Captura de ecrã a mostrar a confirmação.](./media/device-enrollment-program-enroll-ios/confirmation.png)
