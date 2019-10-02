---
title: Tutorial-usar o Apple Business Manager ou o Programa de registro de dispositivos para registrar dispositivos iOS no Intune
titleSuffix: Microsoft Intune
description: Neste tutorial, você configurará os recursos de registro de dispositivo corporativo da Apple do ABM para registrar dispositivos iOS no Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/30/2019
ms.topic: tutorial
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
Customer intent: As an Intune admin, I want to set up the Apple's corporate device enrollment features so that corporate devices can automatically enroll in Intune.
ms.collection: M365-identity-device-management
ms.openlocfilehash: e221e67afa141612d6b565a511866087ce237d25
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71729664"
---
# <a name="tutorial-use-apples-corporate-device-enrollment-features-in-apple-business-manager-abm-to-enroll-ios-devices-in-intune"></a>Destina Usar os recursos de registro de dispositivo corporativo da Apple no Apple Business Manager (ABM) para registrar dispositivos iOS no Intune
Os recursos de registro de dispositivo no Apple Business Manager simplificam o cadastramento de dispositivos. O Intune também dá suporte ao portal de DEP (Programa de registro de dispositivos mais antigo) da Apple, mas incentivamos você a começar com o Apple Business Manager. Com a Microsoft Intune e o registro de dispositivo corporativo da Apple, os dispositivos são automaticamente inscritos na primeira vez que o usuário liga o dispositivo. Portanto, você pode enviar dispositivos para muitos usuários sem precisar configurar cada dispositivo individualmente. 

Neste tutorial, ficará a saber como:
> [!div class="checklist"]
> * Obter um token de registro de dispositivo Apple
> * Sincronizar dispositivos gerenciados para o Intune
> * Criar um perfil de registro
> * Atribuir o perfil de registro a dispositivos

Se não tiver uma subscrição do Intune, [inscreva-se numa conta de avaliação gratuita](../fundamentals/free-trial-sign-up.md).

## <a name="prerequisites"></a>Pré-requisitos
- Dispositivos comprados no [Apple Business Manager](https://business.apple.com) ou na [programa de registro de dispositivos da Apple](http://deploy.apple.com)
- Definir a [autoridade de gerenciamento de dispositivo móvel](../fundamentals/mdm-authority-set.md)
- Obter um [Apple MDM Push Certificate](apple-mdm-push-certificate-get.md)

## <a name="get-an-apple-device-enrollment-token"></a>Obter um token de registro de dispositivo Apple
Antes de registrar dispositivos iOS com os recursos de registro corporativo da Apple, você precisa de um arquivo de token de registro de dispositivo Apple (. pem). Esse token permite que o Intune sincronize informações sobre dispositivos Apple que sua empresa possui. Também permite ao Intune carregar perfis de inscrição para a Apple e atribuir dispositivos a esses perfis.

Você usa o ABM ou o portal de DEP para criar um token de registro de dispositivo. Você também usa os portais para atribuir dispositivos ao Intune para gerenciamento.

1. No [Intune no portal do Azure](https://aka.ms/intuneportal), selecione **Inscrição de dispositivos** > **Inscrição da Apple** > **Tokens do Programa de Inscrição** > **Adicionar**.

2. Conceda permissão à Microsoft para enviar informações sobre o utilizador e o dispositivo à Apple, ao selecionar **Concordo**.

   ![Captura de ecrã a mostrar o painel Token do Programa de Inscrição, na área de trabalho Certificados da Apple, para transferir a chave pública.](./media/tutorial-use-device-enrollment-program-enroll-ios/add-enrollment-program-token-pane.png)

3. Selecione **Transferir a chave pública** para transferir e guardar o ficheiro da chave de encriptação (.pem) localmente. O arquivo. pem é usado para solicitar um certificado de relação de confiança do portal ABM ou DEP.

4. Selecione **Criar um token para o Programa de Registo de Aparelho da Apple** para abrir o portal Programa de Implementação da Apple e inicie sessão com o Apple ID da sua empresa. Pode utilizar este Apple ID para renovar o seu token DEP.

5. No [portal dos Programas de Implementação](https://deploy.apple.com) da Apple, selecione **Começar** em **Programa de Registo de Aparelho**. Seu processo pode ser um pouco diferente das etapas a seguir no [Apple Business Manager](https://business.apple.com).

4. Na página **Gerir Servidores**, selecione **Adicionar Servidor MDM**.

5. Para **nome do servidor MDM**, insira *TestMDMServer* e, em seguida, escolha **Avançar**. O nome do servidor é uma referência para identificar o servidor de gestão de dispositivos móveis (MDM). Não é o nome nem o URL do servidor do Microsoft Intune.

6. A caixa de diálogo **Adicionar &lt;NomeDoServidor&gt;** é aberta e pede para **Atualizar a Chave Pública**. Selecione **Escolher Ficheiro…** para carregar o ficheiro .pem e, em seguida, selecione **Seguinte**.

6. Acesse **programas de implantação** > **programa de registro de dispositivos** > **gerenciar dispositivos**.
7. Em **escolher dispositivos por**, escolha **número de série**. <!--ask Tiffany about this-->

8. Em **Selecionar Ação**, selecione **Atribuir ao Servidor**, selecione o &lt;NomeDoServidor&gt; especificado no Microsoft Intune e, em seguida, selecione **OK**. O portal da Apple atribui os dispositivos especificados para o servidor do Intune para gestão e, em seguida, apresenta a mensagem **Atribuição Concluída**.

   No portal da Apple, aceda a **Programas de Implementação** &gt; **Programa de Inscrição de Dispositivos** &gt; **Ver Histórico de Atribuições** para ver uma lista de dispositivos e a respetiva atribuição de servidores MDM.

9. Para referência futura, no Intune na portal do Azure, forneça a ID da Apple usada para criar esse token.

    ![Captura de ecrã a mostrar a especificação do ID Apple utilizado para criar o token do programa de inscrição e o acesso ao token do programa de inscrição.](./media/tutorial-use-device-enrollment-program-enroll-ios/image03.png)

10. Na caixa **Token da Apple**, procure o ficheiro de certificado (.pem), escolha **Abrir** e, em seguida, escolha **Criar**. 

11. Se você quiser aplicar marcas de escopo para limitar quais administradores têm acesso a esse token, selecione escopos.

## <a name="create-an-apple-enrollment-profile"></a>Criar um perfil de inscrição da Apple
Agora que você instalou o token, você pode criar um perfil de registro para dispositivos iOS corporativos. Um perfil de inscrição de dispositivos especifica as definições aplicadas a um grupo de dispositivos durante a inscrição.

1. No Intune no portal do Azure, escolha **Inscrição de dispositivos** > **Inscrição da Apple** > **Tokens do programa de inscrição**.

2. Selecione o token que você acabou de instalar, escolha **perfis** > **Criar perfil**.

3. Em **Criar perfil**, insira *TestDEPProfile* para **nome** e *teste DEP para dispositivos IOS* para **Descrição**. Os utilizadores não verão estes detalhes.

4. Escolha **Ios** em **plataforma**.

5. Determine se você deseja que seus dispositivos se registrem com ou sem **afinidade de usuário**. A afinidade do usuário é projetada para dispositivos que serão usados por usuários específicos. Se os usuários desejarem usar o Portal da Empresa para serviços como instalar aplicativos, escolha **registrar com afinidade de usuário**. Se os usuários não precisarem do Portal da Empresa ou se você quiser provisionar o dispositivo para muitos usuários, escolha **registrar sem afinidade de usuário**.

6. Se você optar por se registrar com a afinidade do usuário, determine se deseja autenticar com Portal da Empresa ou o assistente de configuração da Apple. Se você quiser usar a autenticação multifator, permitir que os usuários alterem senhas na primeira entrada ou solicitar que os usuários redefinam suas senhas expiradas durante o registro, escolha **Sim** em **autenticar com portal da empresa em vez de configuração da Apple Assistente**. Se você estiver familiarizado com a autenticação HTTP básica fornecida pela Apple por meio do assistente de configuração da Apple, escolha **não**.

7. Se você optar por se registrar com a afinidade do usuário e se autenticar com Portal da Empresa, determine se deseja instalar Portal da Empresa com o VPP (Volume Purchase Program) da Apple. Se você instalar o Portal da Empresa com um token VPP, o usuário não precisará inserir uma ID da Apple e uma senha para baixar o Portal da Empresa da loja de aplicativos durante o registro. Escolha **usar token:** em **instalar portal da empresa com o VPP** para selecionar um token VPP que tenha licenças gratuitas do portal da empresa disponíveis. Se você não quiser usar o VPP para implantar o Portal da Empresa, escolha **não usar VPP** em **instalar portal da empresa com o VPP**. 

8. Se você optar por se registrar com a afinidade do usuário, autenticar com Portal da Empresa e instalar Portal da Empresa com o VPP, decida se deseja executar o Portal da Empresa no modo de aplicativo único até a autenticação. Essa configuração permite que você garanta que o usuário não terá acesso a outros aplicativos até que tenha concluído o registro corporativo. Se você quiser restringir o usuário a esse fluxo até que o registro seja concluído, escolha **Sim** em **executar portal da empresa no modo de aplicativo único até a autenticação**. 

9. Escolha **configurações de gerenciamento de dispositivo** e escolha **Sim** em **supervisionado**. Os dispositivos supervisionados oferecem a você a maioria das opções de gerenciamento para seus dispositivos iOS corporativos.

10. Escolha **Sim** em **registro bloqueado** para garantir que os usuários não possam remover o gerenciamento do dispositivo corporativo. 

11. Escolha uma opção em **sincronizar com computadores** para determinar se os dispositivos IOS poderão ser sincronizados com computadores.

12. Por padrão, a Apple nomeia o dispositivo com o tipo de dispositivo (ou seja, iPad). Se você quiser fornecer um modelo de nome diferente, escolha **Sim** em **aplicar modelo de nome de dispositivo**. Insira o nome que você deseja aplicar aos dispositivos, em que as cadeias de caracteres *{{serial}}* e *{{DeviceType}}* substituirão cada número de série e tipo de dispositivo do dispositivo. Caso contrário, escolha **não** em **aplicar modelo de nome de dispositivo**.

13. Escolha **OK**.

14. Escolha **personalização do assistente de configuração** e insira o *Departamento do tutorial* para **nome do departamento**. Essa cadeia de caracteres é o que os usuários veem quando tocam na **configuração** durante a ativação do dispositivo.

15. Em **telefone do departamento**, insira um número de telefone. Esse número aparece quando os usuários tocam no botão de **ajuda necessário** durante a ativação.

16. Você pode **Mostrar** ou **ocultar** uma variedade de telas durante a ativação do dispositivo. Para obter a experiência de inscrição mais direta, defina todas as telas como **ocultar**.

17. Selecione **OK** > **Criar**.

## <a name="sync-managed-devices-to-intune"></a>Sincronizar dispositivos gerenciados para o Intune

Depois de configurar um token do programa de registro com o portal ABM, ASM ou DEP e atribuir dispositivos lá ao servidor MDM, você pode aguardar que esses dispositivos sejam sincronizados com o serviço do Intune ou enviar por push manualmente uma sincronização. Sem uma sincronização manual, os dispositivos podem levar até 24 horas para serem exibidos na portal do Azure.

1. No Intune no portal do Azure, escolha **registro de dispositivo** > **registro da Apple** > **tokens do programa de registro** > escolha um token na lista > **dispositivos** > **sincronização**.

## <a name="assign-an-enrollment-profile-to-ios-devices"></a>Atribuir um perfil de registro a dispositivos iOS

Tem de atribuir um perfil do programa de inscrição aos dispositivos para poder inscrevê-los. Esses dispositivos são sincronizados com o Intune da Apple e devem ser atribuídos ao token apropriado do servidor MDM no portal ABM, ASM ou DEP.

1. No Intune no portal do Azure, escolha **registro de dispositivo** > **registro da Apple** > **tokens do programa de registro** > escolha o token na lista.
2. Escolha **Dispositivos** > escolha dispositivos na lista > **Atribuir perfil**.
3. Em **Atribuir perfil**, escolha um perfil para os dispositivos > **Atribuir**.

## <a name="distribute-devices-to-users"></a>Distribuir dispositivos pelos utilizadores

Você configurou o gerenciamento e a sincronização entre o Apple e o Intune e atribuiu um perfil para permitir que seus dispositivos DEP se registrem. Agora pode distribuir os dispositivos aos utilizadores. Os dispositivos com afinidade do utilizador necessitam que seja atribuída uma licença do Intune a cada utilizador.

## <a name="next-steps"></a>Passos seguintes

Você pode encontrar mais informações sobre outras opções disponíveis para registrar dispositivos iOS.

> [!div class="nextstepaction"]
> [Artigo de registro de DEP do iOS detalhado](device-enrollment-program-enroll-ios.md)

<!--commenting out because inaccurate>
## Clean up resources
<!--If you don't want to use iOS corporate enrolled devices anymore, you can delete them.>
<!--- If the devices are enrolled in Intune, you must first [delete them from the Azure Active Directory portal](../remote-actions/devices-wipe.md#delete-devices-from-the-azure-active-directory-portal).>
