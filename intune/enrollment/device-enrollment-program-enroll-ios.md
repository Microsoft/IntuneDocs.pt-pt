---
title: Inscreva dispositivos iOS/iPadOS - Programa de Inscrição de Dispositivos
titleSuffix: Microsoft Intune
description: Saiba como inscrever dispositivos iOS/iPadOS de propriedade corporativa utilizando o Programa de Inscrição de Dispositivos.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/04/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 7ddbf360-0c61-11e8-ba89-0ed5f89f718b
ms.reviewer: tisilver
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: adca40b558a75d2c080fe453218f232a37b21daa
ms.sourcegitcommit: cd90650c339795d44702e9dcd0b9679a7b438bb2
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/20/2020
ms.locfileid: "77473762"
---
# <a name="automatically-enroll-iosipados-devices-with-apples-device-enrollment-program"></a>Inscreva automaticamente dispositivos iOS/iPadOS com o Programa de Inscrição de Dispositivos da Apple

Pode configurar o Intune para inscrever dispositivos iOS/iPadOS adquiridos através do Programa de Inscrição de Dispositivos da Apple [(DEP)](https://deploy.apple.com). O DEP permite-lhe inscrever um grande número de dispositivos de forma remota. Dispositivos como iPhones, iPads e MacBooks podem ser enviados diretamente para os utilizadores. Quando o utilizador liga o dispositivo, o Assistente de Configuração, que inclui a experiência típica fora de caixa para produtos Apple, funciona com configurações pré-configuradas e o dispositivo matricula-se na gestão.

Para permitir a inscrição de DEP, utiliza os portais Intune e Apple Business Manager (ABM) ou Apple School Manager (ASM). É necessária uma lista de números de série ou um número de encomenda de compra para que possa atribuir dispositivos à Intune para gestão em ABM/ASM. Cria perfis de inscrição DEP em Intune contendo definições que são aplicadas aos dispositivos durante a inscrição. Note que a inscrição de DEP não pode ser utilizada com uma conta de gestor de [inscrição](device-enrollment-manager-enroll.md) de dispositivos.

> [!NOTE]
> O DEP define configurações do dispositivo que não podem necessariamente ser removidas pelo utilizador final. Portanto, antes de [migrar para dep,](../fundamentals/migration-guide-considerations.md)o dispositivo deve ser limpo para devolvê-lo a um estado fora da caixa (novo).

## <a name="dep-and-the-company-portal"></a>DEP e o Portal da Empresa

As matrículas do DEP não são compatíveis com a versão da app store da aplicação Portal da Empresa. Pode dar aos utilizadores acesso à aplicação Portal da Empresa num dispositivo DEP. É dever fornecer este acesso para permitir que os utilizadores escolham quais as aplicações corporativas que desejam utilizar no seu dispositivo ou utilizar a autenticação moderna para completar o processo de inscrição. 

Para permitir a autenticação moderna durante a inscrição, empurre a app para o dispositivo utilizando o Portal da **Empresa de Instalação com VPP** (Programa de Compra de Volume) no perfil DEP. Para mais informações, consulte [Automaticamente inscrever dispositivos iOS/iPadOS com o Programa de Inscrição de Dispositivos da Apple](device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile).

Para permitir que o Portal da Empresa atualize automaticamente e forneça a aplicação Portal da Empresa em dispositivos já inscritos com DEP, implemente a aplicação Portal da Empresa através do Intune como uma aplicação necessária para o Programa de Compra de Volume (VPP) com uma política de Configuração de [Aplicações](../apps/app-configuration-policies-use-ios.md) aplicada.

## <a name="what-is-supervised-mode"></a>O que é o modo supervisionado?

A Apple introduziu o modo supervisionado no iOS/iPadOS 5. Um dispositivo iOS/iPadOS em modo supervisionado pode ser gerido com mais controlos, tais como a captura de ecrã sinuoso e a instalação de aplicações a partir da App Store. Como tal, é especialmente útil para dispositivos pertencentes à empresa. Como parte do Programa de Inscrição de Dispositivos Apple (DEP), o Intune suporta a configuração de dispositivos para o modo supervisionado.

O suporte para dispositivos DEP não supervisionados foi depreciado no iOS/iPadOS 11. Nos dispositivos configurados iOS/iPadOS 11 e posteriormente, os dispositivos configurados DEP devem ser sempre supervisionados. A bandeira is_supervised DEP será ignorada numa futura versão iOS/iPadOS.

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
- [Autoridade de Gestão de Dispositivos Móveis (MDM)](../fundamentals/mdm-authority-set.md)
- [Certificado Push de MDM da Apple](apple-mdm-push-certificate-get.md)

## <a name="get-an-apple-dep-token"></a>Obter um token DEP da Apple

Antes de poder inscrever dispositivos iOS/iPadOS com DEP, precisa de um ficheiro de token (.p7m) da Apple. Este token permite ao Intune sincronizar informações sobre os dispositivos DEP que são propriedade da sua empresa. Também permite ao Intune carregar perfis de inscrição para a Apple e atribuir dispositivos a esses perfis.

Usa o portal Apple Business Manager ou apple school manager para criar um símbolo. Também utiliza o portal ABM/ASM para atribuir dispositivos à Intune para gestão.

> [!NOTE]
> Se eliminar o token do portal clássico do Intune antes da migração para o Azure, o Intune poderá restaurar um token DEP da Apple eliminado. Pode eliminar novamente o token DEP do portal do Azure.

### <a name="step-1-download-the-intune-public-key-certificate-required-to-create-the-token"></a>Passo 1. Transfira o certificado de chave pública do Intune, que é obrigatório para criar o token.

1. No [Microsoft Endpoint Manager Admin Center,](https://go.microsoft.com/fwlink/?linkid=2109431)escolha **dispositivos** > **iOS** > **iOS matricula** do iOS > Programa de **Inscrição Tokens** > **Add**.

    ![Obtenha um token do programa de inscrição.](./media/device-enrollment-program-enroll-ios/image01.png)

2. Conceda permissão à Microsoft para enviar informações sobre o utilizador e o dispositivo à Apple, ao selecionar **Concordo**.

> [!NOTE]
> Uma vez que progrida para além do passo 2 para descarregar o certificado de chave pública Intune, não feche o assistente nem navegue para longe desta página. Ao fazê-lo, invalidará o certificado que descarregou e terá de repetir este processo novamente. Se encontrar esta situação, notará normalmente que o botão Criar no separador Review + criar está acinzentado e não pode completar o processo.

   ![Captura de ecrã a mostrar o painel Token do Programa de Inscrição, na área de trabalho Certificados da Apple, para transferir a chave pública.](./media/device-enrollment-program-enroll-ios/add-enrollment-program-token-pane.png)

3. Selecione **Transferir a chave pública** para transferir e guardar o ficheiro da chave de encriptação (.pem) localmente. O ficheiro .pem é utilizado para pedir um certificado de relação de confiança a partir do portal do Programa de Registo de Aparelho da Apple.


### <a name="step-2-use-your-key-to-download-a-token-from-apple"></a>Passo 2: Utilize a sua chave para transferir um token a partir da Apple.

1. Selecione **Criar um token para o Programa de Registo de Aparelho da Apple** para abrir o portal Programa de Implementação da Apple e inicie sessão com o Apple ID da sua empresa. Pode utilizar este Apple ID para renovar o seu token DEP.
2. No [portal dos Programas de Implementação](https://deploy.apple.com) da Apple, selecione **Começar** em **Programa de Registo de Aparelho**.

3. Na página **Gerir Servidores**, selecione **Adicionar Servidor MDM**.
4. Introduza o **Nome do Servidor MDM** e, em seguida, selecione **Seguinte**. O nome do servidor é uma referência para identificar o servidor de gestão de dispositivos móveis (MDM). Não é o nome nem o URL do servidor do Microsoft Intune.

5. A caixa de diálogo **Adicionar &lt;NomeDoServidor&gt;** é aberta e pede para **Atualizar a Chave Pública**. Selecione **Escolher Ficheiro…** para carregar o ficheiro .pem e, em seguida, selecione **Seguinte**.

6. Vá aos Programas de **Implementação** &gt; Programa de **Inscrição de Dispositivos** &gt; **Gerir Dispositivos**.
7. Em **Selecionar Dispositivos Por**, especifique a forma como os dispositivos são identificados:
    - **Número de Série**
    - **Número da Encomenda**
    - **Carregar Ficheiro CSV**.

   ![Captura de ecrã a mostrar a especificação de dispositivos selecionados pelo número de série, a definição da ação de seleção como Atribuir ao servidor e a seleção do nome do servidor.](./media/device-enrollment-program-enroll-ios/enrollment-program-token-specify-serial.png)

8. Em **Selecionar Ação**, selecione **Atribuir ao Servidor**, selecione o &lt;NomeDoServidor&gt; especificado no Microsoft Intune e, em seguida, selecione **OK**. O portal da Apple atribui os dispositivos especificados para o servidor do Intune para gestão e, em seguida, apresenta a mensagem **Atribuição Concluída**.

   No portal da Apple, vá a Programas de **Implementação** &gt; Programa de **Inscrição de Dispositivos** &gt; **ver o Histórico** de Atribuição para ver uma lista de dispositivos e a sua atribuição de servidores MDM.

### <a name="step-3-save-the-apple-id-used-to-create-this-token"></a>Passo 3: Guarde o Apple ID que serviu para criar este token.

No [Microsoft Endpoint Manager Admin Center,](https://go.microsoft.com/fwlink/?linkid=2109431)forneça o Apple ID para referência futura.

![Captura de ecrã a mostrar a especificação do ID Apple utilizado para criar o token do programa de inscrição e o acesso ao token do programa de inscrição.](./media/device-enrollment-program-enroll-ios/image03.png)

### <a name="step-4-upload-your-token-and-choose-scope-tags"></a>Passo 4. Carregue o token e escolha as etiquetas de âmbito.

1. Na caixa **Token da Apple**, procure o ficheiro de certificado (.pem) e escolha **Abrir**.
2. Se quiser aplicar [etiquetas de âmbito](../fundamentals/scope-tags.md) a este token DEP, escolha **Âmbito (etiquetas)** e selecione as etiquetas de âmbito que pretende. As etiquetas de âmbito aplicadas a um token serão herdadas pelos perfis e dispositivos adicionados a este token.
3. Selecione **Criar**.

Com o certificado push, a Intune pode inscrever-se e gerir dispositivos iOS/iPadOS, pressionando a política para dispositivos móveis matriculados. O Intune é sincronizado automaticamente na Apple para que possa ver a conta do seu programa de inscrição.

## <a name="create-an-apple-enrollment-profile"></a>Criar um perfil de inscrição da Apple

Agora que instalou o seu token, pode criar um perfil de inscrição para dispositivos DEP. Um perfil de inscrição de dispositivos especifica as definições aplicadas a um grupo de dispositivos durante a inscrição. Há um limite de 100 perfis de inscrição por token DEP.

> [!NOTE]
> Os dispositivos serão bloqueados se não houver licenças suficientes do Portal da Empresa para um token VPP, ou se o token tiver expirado. O Intune apresentará um alerta quando um token estiver prestes a expirar ou se existirem poucas licenças.
 

1. No [Microsoft Endpoint Manager Admin Center,](https://go.microsoft.com/fwlink/?linkid=2109431)escolha **Dispositivos** > **iOS** > **inscrição do iOS** > **Tokens**do Programa de Inscrição .
2. Selecione um símbolo, escolha **Perfis** > **Criar perfil** > **iOS**.

    ![Crie uma captura de ecrã de perfil.](./media/device-enrollment-program-enroll-ios/image04.png)

3. Na página **Basics,** introduza um **Nome** e **Descrição** para o perfil para fins administrativos. Os utilizadores não verão estes detalhes. Pode utilizar este campo **Nome** para criar um grupo dinâmico no Azure Active Directory. Utilize o nome de perfil para definir o parâmetro enrollmentProfileName para atribuir dispositivos com este perfil de inscrição. Saiba mais sobre os [grupos dinâmicos do Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership#rules-for-devices).

    ![Nome do perfil e descrição.](./media/device-enrollment-program-enroll-ios/image05.png)

4. Selecione **Seguinte: Definições**de gestão do dispositivo .

5. Na **Afinidade do Utilizador**, escolha se os dispositivos com este perfil têm de ser inscritos com ou sem um utilizador atribuído.
    - **Inscrever com Afinidade de Utilizador**: selecione esta opção para os dispositivos que pertençam aos utilizadores e que queiram utilizar o Portal da Empresa para serviços como a instalação de aplicações. Se utilizar a ADFS e o perfil de inscrição tiver **Authenticate with Company Portal em vez de Configurar Assistente** definido para **Nº,** [WS-Trust 1.3 Username/Mixed endpoint](https://technet.microsoft.com/library/adfs2-help-endpoints) [Saiba mais.](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint)

    - **Inscrever sem Afinidade do Utilizador** – escolha esta opção para dispositivos não associados a um único utilizador. Utilize esta opção para dispositivos que não acedam aos dados dos utilizadores locais. As aplicações, como o Portal da Empresa, não funcionam.

5. Se tiver escolhido **Inscrever com Afinidade de Utilizador**, poderá permitir que os utilizadores se autentiquem no Portal da Empresa em vez de o fazerem no Assistente de Configuração da Apple.

    ![Autentique com o Portal da Empresa.](./media/device-enrollment-program-enroll-ios/authenticatewithcompanyportal.png)

    > [!NOTE]
    > Se desejar fazer alguma das seguintes coisas, desempente **se os utilizadores devem autenticar** no Portal da **Empresa**.
    >    - utilizar a autenticação multifator
    >    - pedir aos utilizadores para alterar a palavra-passe ao iniciar sessão pela primeira vez
    >    - Pedir aos utilizadores para reporem as respetivas palavras-passe expiradas durante a inscrição
    >
    > Estas ações não são suportadas durante a autenticação com o Assistente de Configuração da Apple.

6. Se escolheu o **Portal da Empresa** para Selecionar onde os utilizadores devem **autenticar,** pode utilizar um sinal VPP para instalar automaticamente o Portal da Empresa no dispositivo. Neste caso, o utilizador não tem de fornecer um ID Apple. Para instalar o Portal da Empresa com um token VPP, selecione um token em **Instalar Portal da Empresa com o VPP**. Exige que o Portal da Empresa já tenha sido adicionado ao sinal de VPP. Para garantir que a aplicação Portal da Empresa continua a ser atualizada após a inscrição, certifique-se de ter configurado uma implementação de aplicações em Intune (Intune>Client Apps). Para que a interação do utilizador não seja necessária, é provável que queira ter o Portal da Empresa como uma aplicação iOS/iPadOS VPP, torná-la uma aplicação necessária e utilizar o licenciamento do dispositivo para a atribuição. Certifique-se de que o token não expira e que tem licenças de dispositivos suficientes para a aplicação Portal da Empresa. Se o token expirar ou se esgotar as licenças, o Intune instalará o Portal da Empresa a partir da App Store e pedirá um ID Apple. 

    > [!NOTE]
    > Quando **selecionar onde os utilizadores devem autenticar** é para o Portal da **Empresa,** certifique-se de que o processo de inscrição do dispositivo é realizado nas primeiras 24 horas do portal da empresa ser descarregado para o dispositivo DEP. Caso contrário, a inscrição poderá falhar e será necessário um reset de fábrica para inscrever o dispositivo.
    
    ![Captura de ecrã a mostrar a opção Instalar Portal da Empresa com o VPP.](./media/device-enrollment-program-enroll-ios/install-cp-with-vpp.png)

7. Se escolheu o Assistente de **Configuração** para **Selecionar onde os utilizadores devem autenticar,** mas também pretende utilizar o Acesso Condicional ou implementar aplicações da empresa nos dispositivos, tem de instalar o Portal da Empresa nos dispositivos. Para isso, escolha **Sim** para **instalar o Portal da Empresa.**  Se desejar que os utilizadores recebam o Portal da Empresa sem terem de autenticar na loja de aplicações, opte por instalar o **Portal da Empresa com VPP** e selecione um símbolo VPP. Certifique-se de que o token não expira e que tem licenças de dispositivo suficientes para que a aplicação Portal da Empresa seja implementada corretamente.

8. Se tiver escolhido um token para **Instalar o Portal da Empresa com o VPP**, poderá bloquear o dispositivo no Modo de Aplicação Única (nomeadamente, a aplicação do Portal da Empresa) logo após a conclusão do Assistente de Configuração. Selecione **Sim** para **Execute o Portal da Empresa no Modo de Aplicação Única até à autenticação** para definir esta opção. Para utilizar o dispositivo, tem de autenticar primeiro o utilizador ao iniciar sessão com o Portal da Empresa.

    A autenticação de vários fatores não é suportada num único dispositivo bloqueado no Modo De Aplicação Única. Esta limitação existe porque o dispositivo não pode mudar para uma aplicação diferente para completar o segundo fator de autenticação. Portanto, se pretender autenticação multifactor num dispositivo Single App Mode, o segundo fator deve estar num dispositivo diferente.

    Esta funcionalidade só é suportada para iOS/iPadOS 11.3.1 e posteriormente.

   ![Captura de ecrã do modo de aplicação única.](./media/device-enrollment-program-enroll-ios/single-app-mode.png)

9. Se pretender que os dispositivos que utilizam este perfil sejam supervisionados, escolha **Sim** para **Supervisionado**.

    ![Captura de ecrã a mostrar a opção Definições de Gestão de Dispositivos.](./media/device-enrollment-program-enroll-ios/supervisedmode.png)

    Os dispositivos **supervisionados** proporcionam mais opções de gestão e desativam o Bloqueio de Ativação por predefinição. A Microsoft recomenda a utilização do DEP como mecanismo para ativar o modo supervisionado, especialmente se estiver a implementar um grande número de dispositivos iOS/iPadOS.

    Os utilizadores são notificados de que os seus dispositivos são supervisionados de duas formas:

   - O ecrã de bloqueio indica: "Este iPhone é gerido pelo Contoso."
   - O ecrã **Definições** > **Geral** > **Acerca de** indica: "Este iPhone é supervisionado. A Contoso consegue monitorizar o seu tráfego de Internet e localizar este dispositivo."

     > [!NOTE]
     > Um dispositivo inscrito sem supervisão só pode ser reposto para supervisionado com o Apple Configurator. A reposição do dispositivo desta forma requer ligar um dispositivo iOS/iPadOS a um Mac com um cabo USB. Saiba mais sobre este assunto nos [documentos do Apple Configurator](http://help.apple.com/configurator/mac/2.3).

10. Escolha se quer a inscrição bloqueada para os dispositivos com este perfil. **A inscrição bloqueada** desativa as definições do iOS/iPadOS que permitem remover o perfil de gestão do menu **Definições.** Após a inscrição de dispositivos, não poderá alterar esta definição sem apagar os dados do dispositivo. Esses dispositivos têm de ter o Modo de Gestão **Supervisionado** definido como *Sim*. 

11. Escolha se quer que os dispositivos com este perfil consigam **Sincronizar com computadores**. Se escolher **Permitir o Apple Configurator por certificado**, terá de escolher um certificado em **Certificados do Apple Configurator**.

12. Se tiver escolhido **Permitir o Apple Configurator por certificado** no passo anterior, escolha um Certificado do Apple Configurator a importar.

13. Pode especificar um formato de nomeação para dispositivos que é aplicado automaticamente quando se inscrevem e em cada check-in sucessivo. Para criar um modelo de nomenclatura, selecione **Sim** em **Aplicar modelo de nome de dispositivo**. Em seguida, na caixa **Modelo de Nome do Dispositivo**, introduza o modelo a utilizar para os nomes com este perfil. Pode especificar um formato de modelo para incluir o tipo de dispositivo e o número de série. 

14. Escolha **a seguir: Configuração De Personalização assistente**.

15. Na página de personalização do Assistente de **Configuração,** configure as seguintes definições de perfil: ![Configuração assistente de configuração.](./media/device-enrollment-program-enroll-ios/setupassistantcustom.png)


    | Definições do departamento | Description |
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
    | <strong>Restaurar</strong> | Exiba o ecrã apps & Data. Este ecrã permite que o utilizador opte por restaurar ou transferir os dados da Cópia de Segurança do iCloud quando configurar o dispositivo. |
    | <strong>iCloud e Apple ID</strong> | Dê ao utilizador as opções para iniciar sessão com o seu Apple ID e utilizar o iCloud.                         |
    | <strong>Termos e Condições</strong> | Pedir ao utilizador para aceitar os termos e condições da Apple. |
    | <strong>Touch ID</strong> | Apresentar ao utilizador a opção para configurar a identificação através de impressão digital no dispositivo. |
    | <strong>Apple Pay</strong> | Apresentar ao utilizador a opção para configurar o Apple Pay no dispositivo. |
    | <strong>Zoom</strong> | Apresentar ao utilizador a opção para aumentar o zoom quando este configurar o dispositivo. |
    | <strong>Siri</strong> | Apresentar ao utilizador a opção para configurar o Siri. |
    | <strong>Dados de Diagnóstico</strong> | Exiba o ecrã de Diagnóstico sintetizador ao utilizador. Este ecrã permite que o utilizador opte por enviar dados de diagnóstico para a Apple. |
    | <strong>Sinal de Apresentação</strong> | Apresentar ao utilizador a opção para ativar o Sinal de Apresentação. |
    | <strong>Privacidade</strong> | Apresentar o ecrã Privacidade ao utilizador. |
    | <strong>Migração do Android</strong> | Apresentar ao utilizador a opção para migrar os dados de um dispositivo Android. |
    | <strong>iMessage e FaceTime</strong> | Dê ao utilizador a opção de configurar o iMessage e o FaceTime. |
    | <strong>Integração</strong> | Apresentar ecrãs informativos de integração para formação do utilizador, como a Folha de Capa, o Multitasking e o Centro de Controlo. |
    | <strong>Migração de Relógio</strong> | Apresentar ao utilizador a opção para migrar os dados de um dispositivo de relógio. |
    | <strong>Tempo do Ecrã</strong> | Apresentar o ecrã Tempo do Ecrã. |
    | <strong>Atualização de Software</strong> | Apresentar o ecrã de atualização de software obrigatório. |
    | <strong>Configuração do SIM</strong> | Apresentar ao utilizador a opção para adicionar um plano de dados móveis. |
    | <strong>Aspeto</strong> | Apresentar o ecrã Aspeto ao utilizador. |
    | <strong>Idioma Expressa</strong>| Exiba o ecrã Express Language ao utilizador. |
    | <strong>Língua Preferida</strong> | Dê ao utilizador a opção de escolher o seu **Idioma Preferido**. |
    | <strong>Dispositivo para migração de dispositivos</strong> | Dê ao utilizador a opção de migrar dados do seu antigo dispositivo para este dispositivo.|
    

16. Escolha **O Próximo** para ir à página Review + **Criar.**

17. Para guardar o perfil, escolha **Criar**.

## <a name="sync-managed-devices"></a>Sincronizar dispositivos geridos
Agora que o Intune tem permissão para gerir os seus dispositivos, pode sincronizar o Intune com a Apple para ver os seus dispositivos geridos no Intune no portal do Azure.

1. No [Microsoft Endpoint Manager Admin Center,](https://go.microsoft.com/fwlink/?linkid=2109431)escolha **Dispositivos** > **iOS** > **iOS matricular** > Programa de **Inscrição Tokens** > escolha um símbolo na lista > **Dispositivos** > **Sync**. ![Screenshot do nó dos dispositivos do programa de inscrição e link Sync.](./media/device-enrollment-program-enroll-ios/image06.png)

   Para cumprir os termos da Apple para um tráfego aceitável do programa de inscrição, o Intune impõe as seguintes restrições:
   - As sincronizações completas não podem ser executadas mais do que uma vez a cada sete dias. Durante uma sincronização completa, o Intune obtém a lista atualizada completa de números de série atribuídos ao servidor de MDM da Apple ligado ao Intune. Se um dispositivo DEP for eliminado do portal do Intune, a sua atribuição deverá ser anulada no servidor MDM da Apple no portal DEP. Se a atribuição não for anulada, não será importado novamente para o Intune até que a sincronização completa seja executada.   
   - É executa automaticamente uma sincronização a cada 24 horas. Também pode sincronizar ao clicar no botão **Sincronizar** (não mais do que uma vez a cada 15 minutos). Todos os pedidos de sincronização têm 15 minutos para serem concluídos. O botão **Sincronizar** está desativado até a sincronização ser concluída. Esta sincronização irá atualizar o estado do dispositivo existente e importar novos dispositivos atribuídos ao servidor de MDM da Apple.   


## <a name="assign-an-enrollment-profile-to-devices"></a>Atribuir um perfil de inscrição a dispositivos
Tem de atribuir um perfil do programa de inscrição aos dispositivos para poder inscrevê-los.

>[!NOTE]
>Também pode atribuir números de série a perfis a partir do painel **Números de Série da Apple**.

1. No [Microsoft Endpoint Manager Admin Center,](https://go.microsoft.com/fwlink/?linkid=2109431)escolha **Dispositivos** > **iOS** > **inscrição do iOS** > Programa de **Inscrição Tokens** > escolha um símbolo na lista.
2. Escolha **Dispositivos** > escolha dispositivos na lista > **Atribuir perfil**.
3. Em **Atribuir perfil**, escolha um perfil para os dispositivos > **Atribuir**.

### <a name="assign-a-default-profile"></a>Atribuir um perfil predefinido

Pode escolher um perfil predefinido a aplicar a todos os dispositivos que inscrever com um token específico.

1. No [Microsoft Endpoint Manager Admin Center,](https://go.microsoft.com/fwlink/?linkid=2109431)escolha **Dispositivos** > **iOS** > **inscrição do iOS** > Programa de **Inscrição Tokens** > escolha um símbolo na lista.
2. Escolha **Definir o Perfil Predefinido**, escolha um perfil na lista pendente e, em seguida, escolha **Guardar**. Este perfil será aplicado a todos os dispositivos inscritos com o token.

## <a name="distribute-devices"></a>Distribuir dispositivos
Ativou a gestão e sincronização entre a Apple e o Intune e atribuiu um perfil para permitir a inscrição dos seus dispositivos DEP. Agora pode distribuir os dispositivos aos utilizadores. Os dispositivos com afinidade do utilizador necessitam que seja atribuída uma licença do Intune a cada utilizador. Os dispositivos sem afinidade do utilizador necessitam de uma licença de dispositivo. Um dispositivo ativado não poderá aplicar um perfil de inscrição até que os dados do mesmo sejam apagados.

Consulte [Inscrever o seu dispositivo iOS/iPadOS em Sintonia com o Programa de Inscrição de Dispositivos](/intune-user-help/enroll-your-device-dep-ios).

## <a name="renew-a-dep-token"></a>Renovar um token de DEP  
1. Aceda a deploy.apple.com.  
2. Em **Gerir Servidores**, selecione o servidor de MDM associado ao ficheiro de token que pretende renovar.
3. Selecione **Gerar Novo Token**.

    ![Captura de ecrã a mostrar a criação de um novo token.](./media/device-enrollment-program-enroll-ios/generatenewtoken.png)

4. Selecione **Token do Seu Servidor**.  
5. No [Microsoft Endpoint Manager Admin Center,](https://go.microsoft.com/fwlink/?linkid=2109431)escolha **Dispositivos** > **iOS** > **inscrição do iOS** > Programa de **Inscrição Tokens** > escolha o símbolo.
    ![Captura de ecrã a mostrar tokens de programas de inscrição.](./media/device-enrollment-program-enroll-ios/enrollmentprogramtokens.png)

6. Selecione **Renovar token** e introduza o ID Apple utilizado para criar o token original.  
    ![Captura de ecrã a mostrar a criação do novo token.](./media/device-enrollment-program-enroll-ios/renewtoken.png)

8. Carregue o token transferido recentemente.  
9. Selecione **Renovar token**. Verá a confirmação de que o token foi renovado.   
    ![Captura de ecrã a mostrar a confirmação.](./media/device-enrollment-program-enroll-ios/confirmation.png)
