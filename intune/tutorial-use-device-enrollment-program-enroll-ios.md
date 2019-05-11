---
title: Tutorial - utilize o Gestor de negócios da Apple ou o programa de inscrição de dispositivos para inscrever dispositivos iOS no Intune
titleSuffix: Microsoft Intune
description: Neste tutorial, vai configurar funcionalidades de inscrição de dispositivos da empresa da Apple do ABM para inscrever dispositivos iOS no Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/30/2019
ms.topic: tutorial
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
Customer intent: As an Intune admin, I want to set up the Apple's corporate device enrollment features so that corporate devices can automatically enroll in Intune.
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0e006ce1be5a19d0557ef0a5d6046afea2c13986
ms.sourcegitcommit: dde4b8788e96563edeab63f612347fa222d8ced0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/06/2019
ms.locfileid: "65135164"
---
# <a name="tutorial-use-apples-corpoate-device-enrollment-features-in-apple-business-manager-abm-to-enroll-ios-devices-in-intune"></a>Tutorial: Utilizar funcionalidades de inscrição de dispositivos de Corpoate da Apple no Gestor de negócios da Apple (ABM) para inscrever dispositivos iOS no Intune
As funcionalidades de inscrição de dispositivos no Gestor de negócios do Apple simplifica a inscrição de dispositivos. O Intune também suporta mais antigo portal de programa de inscrição de dispositivos (DEP) da Apple, mas é recomendável que comece do zero com o Gestor de negócios da Apple. Com o Microsoft Intune e a inscrição de dispositivos empresariais da Apple, os dispositivos são inscritos automaticamente em segurança na primeira vez que o usuário ativa o dispositivo. Portanto pode enviar dispositivos para muitos usuários sem ter de configurar individualmente cada dispositivo. 

Neste tutorial, ficará a saber como:
> [!div class="checklist"]
> * Obtenha o token de uma inscrição de dispositivos da Apple
> * Sincronizar dispositivos geridos para o Intune
> * Criar um perfil de inscrição
> * Atribuir o perfil de inscrição aos dispositivos

Se não tiver uma subscrição do Intune, [inscreva-se numa conta de avaliação gratuita](free-trial-sign-up.md).

## <a name="prerequisites"></a>Pré-requisitos
- Dispositivos adquiridos através do [gerente de negócios da Apple](https://business.apple.com) ou [programa de inscrição de dispositivos da Apple](http://deploy.apple.com)
- Definir o [autoridade de gestão de dispositivos móveis](mdm-authority-set.md)
- Obter um [certificado Push de MDM da Apple](apple-mdm-push-certificate-get.md)

## <a name="get-an-apple-device-enrollment-token"></a>Obtenha o token de uma inscrição de dispositivos da Apple
Antes de inscrever dispositivos iOS com funcionalidades de inscrição da empresa da Apple, precisa de um ficheiro de token (. pem) de inscrição de dispositivos da Apple. Este token permite ao Intune sincronizar informações sobre os dispositivos da Apple propriedade da empresa. Também permite ao Intune carregar perfis de inscrição para a Apple e atribuir dispositivos a esses perfis.

Utilize o portal do DEP ou do ABM para criar um token de inscrição de dispositivos. Também é usar os portais para atribuir dispositivos ao Intune para gestão.

1. No [Intune no portal do Azure](https://aka.ms/intuneportal), selecione **Inscrição de dispositivos** > **Inscrição da Apple** > **Tokens do Programa de Inscrição** > **Adicionar**.

2. Conceda permissão à Microsoft para enviar informações sobre o utilizador e o dispositivo à Apple, ao selecionar **Concordo**.

   ![Captura de ecrã a mostrar o painel Token do Programa de Inscrição, na área de trabalho Certificados da Apple, para transferir a chave pública.](./media/device-enrollment-program-enroll-ios-newui/add-enrollment-program-token-pane.png)

3. Selecione **Transferir a chave pública** para transferir e guardar o ficheiro da chave de encriptação (.pem) localmente. O ficheiro. pem é utilizado para pedir um certificado de relação de confiança a partir do portal do ABM ou DEP.

4. Selecione **Criar um token para o Programa de Registo de Aparelho da Apple** para abrir o portal Programa de Implementação da Apple e inicie sessão com o Apple ID da sua empresa. Pode utilizar este Apple ID para renovar o seu token DEP.

5.  No [portal dos Programas de Implementação](https://deploy.apple.com) da Apple, selecione **Começar** em **Programa de Registo de Aparelho**. O processo pode ser ligeiramente diferente do que os seguintes passos na [gerente de negócios de Apple](https://business.apple.com).

4. Na página **Gerir Servidores**, selecione **Adicionar Servidor MDM**.

5. Para **nome do servidor MDM**, introduza *TestMDMServer* e, em seguida, escolha **seguinte**. O nome do servidor é uma referência para identificar o servidor de gestão de dispositivos móveis (MDM). Não é o nome ou URL do servidor do Microsoft Intune.

6. A caixa de diálogo **Adicionar &lt;NomeDoServidor&gt;** é aberta e pede para **Atualizar a Chave Pública**. Selecione **Escolher ficheiro...** para carregar o ficheiro .pem e, em seguida, selecione **Seguinte**.

6. Aceda a **programas de implementação** > **programa de inscrição de dispositivos** > **gerir dispositivos**.
7. Sob **selecionar dispositivos por**, escolha **número de série**. <!--ask Tiffany about this-->

8. Em **Selecionar Ação**, selecione **Atribuir ao Servidor**, selecione o &lt;NomeDoServidor&gt; especificado no Microsoft Intune e, em seguida, selecione **OK**. O portal da Apple atribui os dispositivos especificados para o servidor do Intune para gestão e, em seguida, apresenta a mensagem **Atribuição Concluída**.

   No portal da Apple, aceda a **Programas de Implementação** &gt; **Programa de Inscrição de Dispositivos** &gt; **Ver Histórico de Atribuições** para ver uma lista de dispositivos e a respetiva atribuição de servidores MDM.

9. Para referência futura, no Intune no portal do Azure, forneça o ID Apple utilizado para criar este token.

    ![Captura de ecrã a mostrar a especificação do ID Apple utilizado para criar o token do programa de inscrição e o acesso ao token do programa de inscrição.](./media/device-enrollment-program-enroll-ios/image03.png)

10. Na caixa **Token da Apple**, procure o ficheiro de certificado (.pem), escolha **Abrir** e, em seguida, escolha **Criar**. 

11. Se gostaria de aplicar etiquetas de âmbito a que os administradores têm acesso a este token de limite, selecione os âmbitos.

## <a name="create-an-apple-enrollment-profile"></a>Criar um perfil de inscrição da Apple
Agora que instalou o seu token, pode criar um perfil de inscrição para dispositivos iOS pertencentes à empresa. Um perfil de inscrição de dispositivos especifica as definições aplicadas a um grupo de dispositivos durante a inscrição.

1. No Intune no portal do Azure, escolha **Inscrição de dispositivos** > **Inscrição da Apple** > **Tokens do programa de inscrição**.

2. Selecione o token que acabou de instalar, escolha **perfis** > **criar perfil**.

3. Sob **criar perfil**, introduza *TestDEPProfile* para **nome** e *teste de DEP para dispositivos iOS* para **descrição** . Os utilizadores não verão estes detalhes.

4. Escolher **iOS** sob **plataforma**.

5. Determinar se pretende que os dispositivos a inscrever com ou sem **afinidade de utilizador**. Afinidade de utilizador destina-se a dispositivos que irão ser utilizados por determinados usuários. Se seus usuários desejarão utilizar o Portal da empresa para serviços como a instalação de aplicações, escolha **inscrever com afinidade de utilizador**. Se os utilizadores não é necessário o Portal da empresa ou se pretender aprovisionar o dispositivo para muitos usuários, escolha **inscrever com afinidade de utilizador**.

6. Se optar por inscrever com afinidade do utilizador, determine se pretende autenticar no Portal da empresa ou o Assistente de configuração da Apple. Se gostaria de utilizar o multi-factor Authentication, permitir que os utilizadores alterar as palavras-passe no primeiro início de sessão ou pedir aos utilizadores para repor as palavras-passe expiradas durante a inscrição, escolha **Sim** sob **autenticar com o Portal, em vez do Assistente de configuração do Apple da empresa**. Se se sente confortável usar o Apple do fornecido a autenticação básica HTTP através do Assistente de configuração do Apple, escolha **não**.

7. Se optar por inscrever com afinidade de utilizador e autenticar com o Portal da empresa, determine se pretende instalar o Portal da empresa com o da Apple Volume Purchase Program (VPP). Se instalar o Portal da empresa com um token VPP, o utilizador não terá de introduzir um Apple ID e a palavra-passe para transferir o Portal da empresa a partir da loja de aplicações durante a inscrição. Escolher **Token de utilização:** sob **instalar o Portal da empresa com o VPP** para selecionar um token VPP que tenha licenças gratuitas do Portal da empresa disponíveis. Se não pretender utilizar o VPP para implementar o Portal da empresa, escolha **não utilizar o VPP** sob **instalar o Portal da empresa com o VPP**. 

8. Se optar por inscrever com afinidade do utilizador, autenticar com o Portal da empresa e instalar o Portal da empresa com o VPP, decida se pretende executar o Portal da empresa no modo de aplicação única até que a autenticação. Esta definição permite-lhe garantir que o utilizador não terá acesso a outras aplicações até que ele termina a inscrição empresarial. Se desejar impedir o utilizador para este fluxo até que a inscrição ser concluída, escolha **Sim** sob **executar o Portal de empresa na autenticação em modo de aplicação única**. 

9. Escolher **definições de gestão de dispositivos** e escolha **Sim** sob **supervisionado**. Dispositivos supervisionados dão-lhe a maioria das opções de gestão para os seus dispositivos iOS empresariais.

10. Escolher **Sim** sob **bloqueado inscrição** para garantir que os utilizadores não é possível remover a gestão do dispositivo da empresa. 

11. Escolha uma opção sob **sincronizar com computadores** para determinar se os dispositivos iOS conseguirá sincronizar com computadores.

12. Por predefinição, a Apple nomeia o dispositivo com o tipo de dispositivo (ou seja, iPad). Se gostaria de fornecer um modelo de outro nome, escolha **Sim** sob **aplicar modelo de nome de dispositivo**. Introduza o nome que pretende aplicar aos dispositivos, onde as cadeias de caracteres *{{SERIAL}}* e *{{DEVICETYPE}}* substituirá o número de série de cada dispositivo e o tipo de dispositivo. Caso contrário, escolha **não** sob **aplicar modelo de nome de dispositivo**.

13. Escolha **OK**.

14. Escolher **personalização do Assistente de configuração** e introduza *departamento Tutorial* para **nome do departamento**. Esta cadeia é que os utilizadores veem quando estes tocam **sobre a configuração** durante a ativação do dispositivo.

15. Sob **telefone do departamento**, introduza um número de telefone. Este número é apresentado quando os utilizadores tocam no **precisa de ajuda** botão durante a ativação.

16. Pode **mostrar** ou **ocultar** uma variedade de ecrãs durante a ativação do dispositivo. Para a experiência totalmente integrada de inscrição, todos os ecrãs de definir como **ocultar**.

17. Selecione **OK** > **Criar**.

## <a name="sync-managed-devices-to-intune"></a>Sincronizar dispositivos geridos para o Intune

Depois de configurar um token do programa de inscrição com o portal DEP, ASM ou ABM e atribuir dispositivos lá para o servidor MDM, pode esperar para estes dispositivos sincronizar com o serviço do Intune ou emitir manualmente uma sincronização. Sem uma sincronização manual, dispositivos podem demorar até 24 horas a aparecer no portal do Azure.

1. No Intune no portal do Azure, selecione **inscrição de dispositivos** > **inscrição da Apple** > **tokens do programa de inscrição** > Escolha um token no a lista > **dispositivos** > **sincronização**.

## <a name="assign-an-enrollment-profile-to-ios-devices"></a>Atribuir um perfil de inscrição para dispositivos iOS

Tem de atribuir um perfil do programa de inscrição aos dispositivos para poder inscrevê-los. Estes dispositivos são sincronizados para o Intune a partir da Apple e tem de ser atribuídos para o token do servidor MDM adequado no portal do ABM, ASM ou DEP.

1. No Intune no portal do Azure, selecione **inscrição de dispositivos** > **inscrição da Apple** > **tokens do programa de inscrição** > Escolha o seu token na lista.
2. Escolha **Dispositivos** > escolha dispositivos na lista > **Atribuir perfil**.
3. Em **Atribuir perfil**, escolha um perfil para os dispositivos > **Atribuir**.

## <a name="distribute-devices-to-users"></a>Distribuir dispositivos pelos utilizadores

Definiu até o gerenciamento e sincronização entre a Apple e o Intune e atribuiu um perfil para permitir a sua inscrição de dispositivos do DEP. Agora pode distribuir os dispositivos aos utilizadores. Os dispositivos com afinidade do utilizador necessitam que seja atribuída uma licença do Intune a cada utilizador.

## <a name="next-steps"></a>Passos Seguintes

Pode encontrar mais informações sobre outras opções disponíveis para inscrever dispositivos iOS.

> [!div class="nextstepaction"]
> [Artigo de inscrição de DEP do iOS aprofundada](device-enrollment-program-enroll-ios.md)

<!--commenting out because inaccurate>
## Clean up resources
<!--If you don't want to use iOS corporate enrolled devices anymore, you can delete them.>
<!--- If the devices are enrolled in Intune, you must first [delete them from the Azure Active Directory portal](devices-wipe.md#delete-devices-from-the-azure-active-directory-portal).>
