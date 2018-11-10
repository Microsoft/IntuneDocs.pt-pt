---
title: Inscrever dispositivos iOS – Programa de Registo de Aparelho
titleSuffix: Microsoft Intune
description: Saiba como inscrever dispositivos iOS pertencentes à empresa através do Programa de Registo de Aparelho.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/04/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 7ddbf360-0c61-11e8-ba89-0ed5f89f718b
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: af1804f657041055467e302c4dc8913e1035749d
ms.sourcegitcommit: 28262384ec94e43970cc7a33e5d9063972bdf468
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/04/2018
ms.locfileid: "48799664"
---
# <a name="automatically-enroll-ios-devices-with-apples-device-enrollment-program"></a>Inscrever automaticamente dispositivos iOS com o Programa de Inscrição de Dispositivos da Apple

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Este artigo ajuda-o a ativar a inscrição de dispositivos iOS para dispositivos adquiridos através do [Programa de Registo de Aparelho (DEP)](https://deploy.apple.com) da Apple. Pode ativar a inscrição de DEP para um grande número de dispositivos de forma remota. Pode enviar dispositivos, como iPhones e iPads, diretamente aos utilizadores. Quando o utilizador ativar o dispositivo, o Assistente de Configuração será executado com as predefinições configuradas e o dispositivo será inscrito na gestão.

Para ativar a inscrição DEP, deve utilizar os portais do Intune e do Apple DEP. É necessária uma lista de números de série ou um número de encomenda para poder atribuir dispositivos ao Intune para gestão. São criados os perfis de inscrição DEP com as definições aplicadas aos dispositivos durante a inscrição.

A propósito, a inscrição DEP não funciona com o [gestor de inscrição de dispositivos](device-enrollment-manager-enroll.md).

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
- [Autoridade MDM](mdm-authority-set.md)
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
2.  No [portal dos Programas de Implementação](https://deploy.apple.com) da Apple, selecione **Começar** em **Programa de Registo de Aparelho**.

3. Na página **Gerir Servidores**, selecione **Adicionar Servidor MDM**.
4. Introduza o **Nome do Servidor MDM** e, em seguida, selecione **Seguinte**. O nome do servidor é uma referência para identificar o servidor de gestão de dispositivos móveis (MDM). Não é o nome nem o URL do Microsoft Intune.

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

### <a name="step-4-upload-your-token"></a>Passo 4: Carregue o seu token.
Na caixa **Token da Apple**, procure o ficheiro de certificado (.pem), escolha **Abrir** e, em seguida, escolha **Criar**. Com o certificado push, o Intune pode inscrever e gerir dispositivos iOS ao enviar políticas para dispositivos móveis inscritos. O Intune é sincronizado automaticamente na Apple para que possa ver a conta do seu programa de inscrição.

## <a name="create-an-apple-enrollment-profile"></a>Criar um perfil de inscrição da Apple

Agora que instalou o seu token, pode criar um perfil de inscrição para dispositivos DEP. Um perfil de inscrição de dispositivos especifica as definições aplicadas a um grupo de dispositivos durante a inscrição.

1. No Intune no portal do Azure, escolha **Inscrição de dispositivos** > **Inscrição da Apple** > **Tokens do programa de inscrição**.
2. Selecione um token, escolha **Perfis** e, em seguida, escolha **Criar perfil**.

    ![Crie uma captura de ecrã de perfil.](./media/device-enrollment-program-enroll-ios/image04.png)

3. Em **Criar Perfil**, introduza um **Nome** e uma **Descrição** para o perfil para efeitos administrativos. Os utilizadores não verão estes detalhes. Pode utilizar este campo **Nome** para criar um grupo dinâmico no Azure Active Directory. Utilize o nome de perfil para definir o parâmetro enrollmentProfileName para atribuir dispositivos com este perfil de inscrição. Saiba mais sobre os [grupos dinâmicos do Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-groups-dynamic-membership-azure-portal#using-attributes-to-create-rules-for-device-objects).

    ![Nome do perfil e descrição.](./media/device-enrollment-program-enroll-ios/image05.png)

4. Na **Afinidade do Utilizador**, escolha se os dispositivos com este perfil têm de ser inscritos com ou sem um utilizador atribuído.
    - **Inscrever com Afinidade de Utilizador**: selecione esta opção para os dispositivos que pertençam aos utilizadores e que queiram utilizar o Portal da Empresa para serviços como a instalação de aplicações. Se estiver a utilizar o ADFS e o perfil de inscrição tiver **Autenticar com o Portal da Empresa em vez do Assistente de Configuração** definido como **Não**, o [ponto final WS-Trust 1.3 Username/Mixed](https://technet.microsoft.com/library/adfs2-help-endpoints) [Saiba mais](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint) é necessário.

    - **Inscrever sem Afinidade do Utilizador** – escolha esta opção para dispositivos não associados a um único utilizador. Utilize esta opção para dispositivos que realizem tarefas sem aceder aos dados de utilizador locais. As aplicações, como o Portal da Empresa, não funcionam.

5. Se tiver escolhido **Inscrever com Afinidade do Utilizador**, tem a opção para permitir que os utilizadores se autentiquem com o Portal da Empresa em vez do Assistente de Configuração da Apple.

    ![Autentique com o Portal da Empresa.](./media/device-enrollment-program-enroll-ios/authenticatewithcompanyportal.png)

    > [!NOTE]
    > Se quiser realizar alguma das seguintes ações, defina **Autenticar com o Portal da Empresa em vez do Assistente de Configuração da Apple** para **Sim**.
    >    - utilizar a autenticação multifator
    >    - pedir aos utilizadores para alterar a palavra-passe ao iniciar sessão pela primeira vez
    >    - Pedir aos utilizadores para reporem as respetivas palavras-passe expiradas durante a inscrição
    >
    > Estas ações não são suportadas durante a autenticação com o Assistente de Configuração da Apple.

6. Se selecionar **Sim** em **Autenticar com o Portal da Empresa em vez do Assistente de Configuração da Apple**, pode optar por utilizar um token do Programa de Compras em Volume (VPP) para instalar automaticamente o Portal da Empresa no dispositivo sem que o utilizador tenha de fornecer um ID Apple. Para instalar o Portal da Empresa com um token VPP, selecione um token em **Instalar Portal da Empresa com o VPP**. Certifique-se de que o token não expira e que tem licenças de dispositivos suficientes para a aplicação Portal da Empresa. Se o token expirar ou esgotar as licenças, o Intune irá instalar o Portal da Empresa a partir da App Store e irá pedir um ID Apple.

    ![Captura de ecrã a mostrar a opção Instalar Portal da Empresa com o VPP.](./media/device-enrollment-program-enroll-ios/install-cp-with-vpp.png)

7. Se tiver selecionado um token para **Instalar Portal da Empresa com o VPP**, pode bloquear imediatamente o dispositivo no Modo de Aplicação Única (nomeadamente, a aplicação Portal da Empresa) após a conclusão do Assistente de Configuração. Selecione **Sim** para **Execute o Portal da Empresa no Modo de Aplicação Única até à autenticação** para definir esta opção. Para utilizar o dispositivo, tem de autenticar primeiro o utilizador ao iniciar sessão com o Portal da Empresa.
    Esta funcionalidade funciona melhor com o iOS 11.3.1 e versões posteriores. Ao utilizar versões mais antigas, a instalação poderá demorar bastante tempo.

8. Escolha **Definições de Gestão de Dispositivos** e selecione se quer ou não que os dispositivos com este perfil sejam supervisionados.

    ![Captura de ecrã a mostrar a opção Definições de Gestão de Dispositivos.](./media/device-enrollment-program-enroll-ios/devicemanagementsettingsblade.png)

    Os dispositivos **supervisionados** proporcionam mais opções de gestão e desativam o Bloqueio de Ativação por predefinição. A Microsoft recomenda a utilização do DEP como o mecanismo para ativar o modo supervisionado, especialmente para as organizações que estiverem a implementar um grande número de dispositivos iOS.

    Os utilizadores são notificados de que os seus dispositivos são supervisionados de duas formas:

   - O ecrã de bloqueio indica: "Este iPhone é gerido pelo Contoso."
   - O ecrã **Definições** > **Geral** > **Acerca de** indica: "Este iPhone é supervisionado. A Contoso consegue monitorizar o seu tráfego de Internet e localizar este dispositivo."

     > [!NOTE]
     > Um dispositivo inscrito sem supervisão só pode ser reposto para supervisionado com o Apple Configurator. Repor o dispositivo desta forma requer ligar um dispositivo iOS a um Mac com um cabo USB. Saiba mais sobre este assunto nos [documentos do Apple Configurator](http://help.apple.com/configurator/mac/2.3).

9. Escolha se quer ou não a inscrição bloqueada para dispositivos com este perfil. A **Inscrição bloqueada** desativa as definições do iOS que permitem que o perfil de gestão seja removido do menu **Definições**. Após a inscrição de dispositivos, não poderá alterar esta definição sem apagar os dados do dispositivo. Esses dispositivos têm de ter o Modo de Gestão **Supervisionado** definido como *Sim*. 

10. Escolha se quer ou não que os dispositivos com este perfil consigam **Sincronizar com computadores**. Se escolher **Permitir o Apple Configurator por certificado**, terá de escolher um certificado em **Certificados do Apple Configurator**.

11. Se tiver escolhido **Permitir o Apple Configurator por certificado** no passo anterior, escolha um Certificado do Apple Configurator a importar.

12. Selecione **OK**.

13. Selecione **Personalização do Assistente de Configuração** para configurar as seguintes definições de perfil: ![Personalização do Assistente de Configuração](./media/device-enrollment-program-enroll-ios/setupassistantcustom.png).


    | Definições do departamento | Descrição |
    |---|---|
    | <strong>Nome do Departamento</strong> | É apresentado quando os utilizadores tocam em <strong>Acerca da Configuração</strong> durante a ativação. |
    |    <strong>Número de Telefone do Departamento</strong>     | Aparece quando o utilizador clica no botão <strong>Preciso de Ajuda</strong> durante a ativação. |

  Pode optar por mostrar ou ocultar vários ecrãs do Assistente de Configuração no dispositivo quando o utilizador o configurar.
  - Se selecionar **Ocultar**, o ecrã não será apresentado durante a configuração. Depois de configurar o dispositivo, o utilizador ainda pode aceder ao menu **Definições** para configurar a funcionalidade.
  - Se selecionar **Mostrar**, o ecrã será apresentado durante a configuração. Por vezes, o utilizador pode ignorar o ecrã sem realizar qualquer ação. No entanto, terá a possibilidade de aceder ao menu **Definições** do dispositivo para configurar a funcionalidade. 


    | Definições do ecrã Assistente de Configuração | Se selecionar **Mostrar**, durante a configuração, o dispositivo irá… |
    |------------------------------------------|------------------------------------------|
    | <strong>Código de Acesso</strong> | Pedir um código de acesso ao utilizador. Solicite sempre um código de acesso, a menos que o dispositivo esteja protegido ou tenha o acesso controlado de outra forma (ou seja, modo de local público que restringe o dispositivo a uma aplicação). |
    | <strong>Serviços de Localização</strong> | Pedir ao utilizador a respetiva localização. |
    | <strong>Restaurar</strong> | Apresentar o ecrã **Aplicações e Dados**. Este ecrã permite que o utilizador opte por restaurar ou transferir os dados da Cópia de Segurança do iCloud quando configurar o dispositivo. |
    | <strong>iCloud e Apple ID</strong> | Apresentar ao utilizador as opções para iniciar sessão com o respetivo **ID Apple** e utilizar o **iCloud**.                         |
    | <strong>Termos e Condições</strong> | Pedir ao utilizador para aceitar os termos e condições da Apple. |
    | <strong>Touch ID</strong> | Apresentar ao utilizador a opção para configurar a identificação através de impressão digital no dispositivo. |
    | <strong>Apple Pay</strong> | Apresentar ao utilizador a opção para configurar o Apple Pay no dispositivo. |
    | <strong>Zoom</strong> | Apresentar ao utilizador a opção para aumentar o zoom quando este configurar o dispositivo. |
    | <strong>Siri</strong> | Apresentar ao utilizador a opção para configurar o Siri. |
    | <strong>Dados de Diagnóstico</strong> | Apresentar o ecrã **Diagnósticos** ao utilizador. Este ecrã permite que o utilizador opte por enviar dados de diagnóstico para a Apple. |


14. Selecione **OK**.

15. Para guardar o perfil, escolha **Criar**.

## <a name="sync-managed-devices"></a>Sincronizar dispositivos geridos
Agora que o Intune tem permissão para gerir os seus dispositivos, pode sincronizar o Intune com a Apple para ver os seus dispositivos geridos no Intune no portal do Azure.

1. No Intune no portal do Azure, escolha **Inscrição de dispositivos** > **Inscrição da Apple** > **Tokens do programa de inscrição** > escolha um token na lista > **Dispositivos** > **Sincronizar**. ![Captura de ecrã a mostrar o nó Dispositivos do Programa de Inscrição selecionado e a opção Sincronizar ligação a ser selecionada.](./media/device-enrollment-program-enroll-ios/image06.png)

   Para cumprir os termos da Apple para um tráfego aceitável do programa de inscrição, o Intune impõe as seguintes restrições:
   - As sincronizações completas não podem ser executadas mais do que uma vez a cada sete dias. Durante uma sincronização completa, o Intune obtém a lista atualizada completa de números de série atribuídos ao servidor de MDM da Apple ligado ao Intune. Depois de um dispositivo do Programa de Registo ser eliminado do portal do Intune sem a inscrição no servidor de MDM da Apple ser anulada no portal de DEP, o mesmo não voltará a ser importado para o Intune até a sincronização completa ser executada.   
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
    ![Captura de ecrã a mostrar a criação de um novo token.](./media/device-enrollment-program-enroll-ios/renewtoken.png)

8. Carregue o token transferido recentemente.  
9. Selecione **Renovar token**. Verá a confirmação de que o token foi renovado.   
    ![Captura de ecrã a mostrar a confirmação.](./media/device-enrollment-program-enroll-ios/confirmation.png)
