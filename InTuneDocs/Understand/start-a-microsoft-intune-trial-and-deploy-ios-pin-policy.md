---
# required metadata

title: Iniciar uma versão de avaliação do Microsoft Intune e implementar a política de PIN para iOS | Microsoft Intune
description:
keywords:
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 06cb9a73-0f17-44b3-b334-86c98020316e

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Iniciar uma versão de avaliação do Microsoft Intune e implementar a política de PIN para iOS
Estas instruções passo a passo ajudam-no a configurar uma avaliação experimental do Intune e uma política de PIN para dispositivos iOS. Para obter uma lista de outras tarefas de avaliação do Intune comuns que pode experimentar, consulte [Tarefas de avaliação comuns do Microsoft Intune](common-microsoft-intune-evaluation-tasks.md)



## Rever pré-requisitos para esta tarefa

-   PC com Windows com o Internet Explorer - para fazer tarefas administrativas

-   Dispositivo iOS 7.1 ou posterior para testar a validação da política de utilizador

-   Telefonar para se autenticar a si próprio durante a inscrição na avaliação gratuita

## Criar uma conta de avaliação gratuita do Intune
> Se já tiver uma subscrição do Intune, ignore esta secção e avance para a seguinte.

1.  Num PC Windows, clique com o botão direito do rato em **Internet Explorer** (IE) e selecione **Navegação InPrivate**

    ![Iniciar navegação InPrivate](../media/30-day-trial-walkthrus/30day-start-trial-1-InPrivate.png)

2.  Aceda ao [portal de inscrição do Intune](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1), forneça as informações pedidas e clique em **Seguinte**

    ![Registar-se numa conta](../media/30-day-trial-walkthrus/30day-start-trial-2-abt-you.png)

3.  Introduza um ID e uma palavra-passe de utilizador para a sua conta de administração e clique em **Seguinte**. Irá utilizar este ID para iniciar sessão no portal do Intune e fazer as tarefas administrativas.

    ![Criar um ID](../media/30-day-trial-walkthrus/30day-start-trial-3-createID.png)

4.  Introduza o seu número de telemóvel e clique em **Enviar mensagem de texto** para validar o número.

    ![Validar os seus detalhes](../media/30-day-trial-walkthrus/30day-start-trial-4-textme.png)

5.  Guarde as informações que aparecem no ecrã e clique em **Está pronto para começar…**

    ![Pronto para começar](../media/30-day-trial-walkthrus/30day-start-trial-5-ReadyToGo.png)

## Criar um utilizador de teste

1.  Num PC com Windows, clique em **Iniciar** para aceder à página de gestão de utilizadores.

    ![Aceder à página de gestão de utilizadores](../media/30-day-trial-walkthrus/30day-crt-user-6-click-start.png)

2.  Clique no botão **+** para adicionar um utilizador.

    ![Adicionar um utilizador](../media/30-day-trial-walkthrus/30day-crt-user-7-click-plus.png)

3.  Na página **Criar nova conta de utilizador**:

    1.  Forneça as informações do utilizador de teste.

    2.  Selecione a opção **Escrever palavra-passe**.

    3.  Limpe a caixa de verificação **Fazer com que esta pessoa altere a palavra-passe da próxima vez que iniciar sessão**.

    4.  Clique em **Criar**

    ![Criar uma nova conta de utilizador](../media/30-day-trial-walkthrus/30day-crt-user-8-add-user-info.png)

4.  Na página de confirmação da criação do utilizador, clique em **Fechar**

    ![Página de confirmação da criação do utilizador](../media/30-day-trial-walkthrus/30day-crt-user-9-close-confirm.png)

5.  Clique no botão **Atualizar** para ver o utilizador de teste que criou.

    ![Confirmação da conta](../media/30-day-trial-walkthrus/30day-crt-user-10-refresh-user.png)

## Configurar uma política de PIN para iOS para o utilizador de teste

1.  Num PC com Windows, defina o Intune para ser a autoridade MDM:

    1.  Aceda à [Consola de gestão do Intune](http://manage.microsoft.com/), inicie sessão com a sua conta de administrador e clique em **Começar a Gerir Dispositivos Móveis**. É aberta a página Autoridade de Gestão de Dispositivos Móveis.

        ![Começar a utilizar a consola do Intune](../media/30-day-trial-walkthrus/30day-cfg-pol-11-start-mg-mobl-dev.png)

    2.  Clique na ligação **Definir Autoridade de Gestão de Dispositivos Móveis**.

        ![Definir a autoridade de gestão de dispositivos móveis](../media/30-day-trial-walkthrus/30day-cfg-pol-12-link-set-mdm.png)

2.  Ativar os dispositivos iOS para inscrição. Este processo configura um certificado fidedigno entre o serviço Apple Push Notification (APNs) e a sua subscrição do Intune.

    1.  Clique em **Ativar a plataforma iOS e Mac OS X**

        ![Ativar a inscrição de iOS e Mac OS X](../media/30-day-trial-walkthrus/30day-cfg-pol-13-enbl-ios-plat.png)

    2.  Clique em **Transferir o Pedido de Certificado do APNs**

        ![Transferir o certificado do APNs](../media/30-day-trial-walkthrus/30day-cfg-pol-14-dwnld-cert-reqst.png)

    3.  Especifique um nome de ficheiro e uma localização para a Solicitação de Assinatura de Certificado (CSR) e clique em **Guardar**. Este ficheiro contém a chave pública que corresponde a uma chave privada presente na sua subscrição do Intune.

        ![Especificar o pedido de assinatura do certificado](../media/30-day-trial-walkthrus/30day-cfg-pol-15-cert-name-loc.png)

    4.  Clique no **portal Certificados Apple Push** para abrir um novo separador.

        ![Aceder à página de certificados do APNs](../media/30-day-trial-walkthrus/30day-cfg-pol-16-cert-portl-link.png)

    5.  Introduza o seu ID e a sua palavra-passe da Apple e clique em **Iniciar sessão**. Este ID pode ser o que utiliza no seu dispositivo iOS para obter aplicações a partir da iOS App Store.

        ![Inicie sessão no portal Apple Push Certificates](../media/30-day-trial-walkthrus/30day-cfg-pol-17-id-passw-signin.png)

    6.  Clique em **Criar Certificado**

        ![Certificado um certificado do APNs](../media/30-day-trial-walkthrus/30day-cfg-pol-18-create-cert.png)

    7.  Leia os Termos de Utilização da Apple, selecione a caixa de verificação e clique em **Aceitar**

        ![Aceitar os termos](../media/30-day-trial-walkthrus/30day-cfg-pol-19-TOU.png)

    8.  Clique em **Procurar**

        ![Navegar para onde guardou o certificado](../media/30-day-trial-walkthrus/30day-cfg-pol-20-browse.png)

    9. Selecione o ficheiro CSR que guardou anteriormente e clique em **Abrir**

        ![Abrir o certificado](../media/30-day-trial-walkthrus/30day-cfg-pol-21-CSRfile-open.png)

    10. Clique no botão **Carregar**.

        ![Carregar o certificado](../media/30-day-trial-walkthrus/30day-cfg-pol-22-upld-reqst.png)

    11. Quando lhe for pedido para transferir um ficheiro JSON, clique em **Guardar como**

        ![Guardar o ficheiro JSON](../media/30-day-trial-walkthrus/30day-cfg-pol-23-json-saveas.png)

    12. Especifique uma localização para o ficheiro JSON e clique em **Guardar**

        ![Especificar onde pretende guardar o ficheiro JSON](../media/30-day-trial-walkthrus/30day-cfg-pol-24-json-save-loc.png)

        Se a página não redirecionar automaticamente após alguns segundos, clique em **Cancelar**

        ![Cancelar se a página não redirecionar](../media/30-day-trial-walkthrus/30day-cfg-pol-25-json-pg-cancel.png)

    13. Para obter o ficheiro de certificado criado recentemente, clique em **Transferir**

        ![Transferir o certificado](../media/30-day-trial-walkthrus/30day-cfg-pol-26-dwnld-retrv-cert.png)

    14. Quando lhe for pedido para transferir um ficheiro PEM, clique em **Guardar como**

        ![Transferir o ficheiro PEM](../media/30-day-trial-walkthrus/30day-cfg-pol-27-pem-saveas.png)

    15. Especifique uma localização para o ficheiro PEM e clique em **Guardar**

        ![Guardar o ficheiro PEM](../media/30-day-trial-walkthrus/30day-cfg-pol-28-pem-save-loc.png)

    16. Regresse ao separador Consola de Gestão do Intune e clique em **Carregar o Certificado do APNs**

        ![Carregar o certificado do APNs](../media/30-day-trial-walkthrus/30day-cfg-pol-29-upld-cert.png)

    17. Introduza o seu ID Apple e clique em **Procurar**

        ![Introduzir o ID Apple](../media/30-day-trial-walkthrus/30day-cfg-pol-30-app-id-browse.png)

    18. Selecione o ficheiro PEM que acabou de guardar e clique em **Abrir**

        ![Abrir o ficheiro PEM](../media/30-day-trial-walkthrus/30day-cfg-pol-31-sel-pem-open.png)

    19. Clique em **Carregar**

        ![Carregar o ficheiro PEM](../media/30-day-trial-walkthrus/30day-cfg-pol-32-pem-upload.png)

        O certificado do APNs está agora configurado.

        ![Configuração do certificado do APNs concluída](../media/30-day-trial-walkthrus/30day-cfg-pol-33-apns-confgd.png)

3.  Criar um grupo de utilizadores de teste para a segmentação da política:

    1.  No painel esquerdo, clique em **Grupos**

        ![Abrir Grupos](../media/30-day-trial-walkthrus/30day-cfg-pol-34-clk-groups.png)

    2.  Clique em **Criar Grupo**, na extremidade direita

        ![Criar um grupo](../media/30-day-trial-walkthrus/30day-cfg-pol-35-crt-group.png)

    3.  Dê um nome ao grupo, selecione **Todos os Utilizadores** como o grupo principal e clique em **Seguinte**

        ![Selecionar Todos os Utilizadores no grupo principal](../media/30-day-trial-walkthrus/30day-cfg-pol-36-name-group.png)

    4.  No campo **Iniciar associação ao grupo com**, selecione **Todos os Utilizadores no Grupo Principal** e clique em **Concluir**

        ![Iniciar associação ao grupo com o grupo principal](../media/30-day-trial-walkthrus/30day-cfg-pol-37-all-users-group.png)

4.  Criar uma política de PIN para iOS e segmentá-la para o grupo de utilizadores de teste:

    1.  No painel esquerdo, clique em **Política**

        ![Área de trabalho Abrir política](../media/30-day-trial-walkthrus/30day-cfg-pol-38-clk-policy.png)

    2.  Clique em **Adicionar Política**, na extremidade direita

        ![Adicionar uma política](../media/30-day-trial-walkthrus/30day-cfg-pol-39-add-policy.png)

    3.  Expanda o nó iOS, selecione a linha **Configuração Geral** e clique em **Criar Política**

        ![Criar uma política de configuração geral para iOS](../media/30-day-trial-walkthrus/30day-cfg-pol-40-gen_cfg_pol.png)

    4.  Escreva um nome para a política, ative a opção **Pedir palavra-passe para desbloquear dispositivos móveis** e defina o **Comprimento mínimo da palavra-passe** como **4**

        ![Configurar definições de palavra-passe](../media/30-day-trial-walkthrus/30day-cfg-pol-41-name-policy.png)

    5.  Clique em **Sim** para implementar a política.

        ![Implementar política](../media/30-day-trial-walkthrus/30day-cfg-pol-42-yes-deploy-pol.png)

    6.  Clique no grupo de utilizadores que criou anteriormente, clique em **Adicionar** e clique em **OK**

        ![Selecionar grupo para a política](../media/30-day-trial-walkthrus/30day-cfg-pol-43-add-pol-to-grp.png)

        Tem agora uma política de PIN para iOS direcionada para o grupo de utilizadores de teste.

        ![Configuração da política concluída](../media/30-day-trial-walkthrus/30day-cfg-pol-44-policy-applied.png)

## Confirmar que a política é aplicada a um dispositivo iOS

1.  Num iPad, inicie a iOS App Store, instale a aplicação gratuita **Portal da Empresa do Microsoft Intune** e abra-a.

    ![Instalar portal da empresa](../media/30-day-trial-walkthrus/30day-cfg-pol-45-cportal-installed.png)

2.  Introduza o nome e a palavra-passe da conta de utilizador de teste e toque em **Iniciar sessão**

    ![Fornecer as suas credenciais](../media/30-day-trial-walkthrus/30day-cfg-pol-46-cportal-signin.png)

3.  Toque em **Inscrever** para começar a inscrever o dispositivo no Intune.

    ![Iniciar inscrição](../media/30-day-trial-walkthrus/30day-cfg-pol-47-tap-enroll.jpg)

4.  No ecrã **Instalar Perfil**, toque em **Instalar**

    ![Instalar um perfil](../media/30-day-trial-walkthrus/30day-cfg-pol-48-profile-install-1.jpg)

5.  Na caixa de diálogo **Instalar Perfil**, toque em **Instalar**

    ![Continuar a instalação do perfil](../media/30-day-trial-walkthrus/30day-cfg-pol-49-profile-install-2.jpg)

6.  No ecrã **Aviso**, toque em **Instalar**

    ![Aceitar a mensagem de aviso](../media/30-day-trial-walkthrus/30day-cfg-pol-50-warning-install-3.png)

7.  Na caixa de diálogo **Gestão Remota**, toque em **Confiar**

    ![Gestão remota de confiança](../media/30-day-trial-walkthrus/30day-cfg-pol-51-remt-mgmt-trust.jpg)

8.  Depois de concluída a instalação do perfil de gestão, toque em **Concluído**. A inscrição agora está concluída.

    ![Inscrição concluída](../media/30-day-trial-walkthrus/30day-cfg-pol-52-profile-done.jpg)

9. Quando a inscrição estiver concluída, toque em **OK** e feche a aplicação do Portal da Empresa.

    ![Toque em OK para fechar a aplicação Portal da Empresa](../media/30-day-trial-walkthrus/30day-cfg-pol-53-devc-enrolled-ok.png)

10. Quando lhe for pedido para configurar um código de acesso, toque em **Continuar**

    ![Aceitar o pedido para configurar o código de acesso](../media/30-day-trial-walkthrus/30day-cfg-pol-54-passcode-req-cont.png)

11. Introduza o código de acesso, toque em **Continuar**, introduza novamente o código de acesso e toque em **Guardar**

    ![Fornecer um código de acesso](../media/30-day-trial-walkthrus/30day-cfg-pol-55-passcode-enter.jpg)

12. Prima o botão de energia para bloquear o iPad, deslize para o desbloquear e verá que agora precisa de introduzir o código de acesso para o desbloquear.

### Consulte também
[Guia de avaliação do Intune](get-started-with-a-30-day-trial-of-microsoft-intune.md)


<!--HONumber=May16_HO2-->


