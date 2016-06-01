---
# required metadata

title: Inscrição do Assistente de Configuração para dispositivos iOS com Microsoft Intune | Microsoft Intune
description:
keywords:
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 46e5b027-4280-4809-b45f-651a6ab6d0cd

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Inscrever dispositivos iOS com o Apple Configurator utilizando o Assistente de Configuração
O Intune suporta a inscrição de dispositivos iOS pertencentes à empresa com a ferramenta [Apple Configurator](http://go.microsoft.com/fwlink/?LinkId=518017) em execução num computador Mac. Este processo efetua a reposição de fábrica do dispositivo e prepara-o para executar o Assistente de Configuração pelo novo utilizador do dispositivo com as políticas da empresa pré-instaladas.


## Inscrição do Assistente de Configuração para dispositivos iOS com Microsoft Intune
Através do Apple Configurator pode repor as definições de fábrica dos dispositivos iOS e prepará-los para serem configurados pelo novo utilizador do dispositivo.  Este método requer que ligue o dispositivo iOS através de USB a um computador Mac para configurar a inscrição empresarial e parte do princípio de que está a utilizar o Apple Configurator 2.0. A maioria dos cenários exige que a política aplicada ao dispositivo iOS inclua *afinidade de utilizador* para ativar a aplicação Portal da Empresa do Intune.

**Pré-requisitos**
* Acesso físico aos dispositivos iOS - a configuração dos dispositivos tem de ser anulada (reposição de fábrica) sem proteção por palavra-passe
* Números de série de dispositivos - [como obter um número de série iOS](https://support.apple.com/en-us/HT204308)
* Cabos de ligação USB
* Computador Mac com o [Apple Configurator 2.0](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12)


1.  **Criar um grupo de dispositivos móveis** (Opcional) Se a sua empresa precisar de grupos de dispositivos móveis para ajudar a gerir dispositivos, crie-os.

2.  Utilizar grupos para gerir utilizadores e dispositivos com o Microsoft Intune Criar um perfil para dispositivos

    ###### Um perfil de inscrição de dispositivos especifica as definições aplicadas a um grupo de dispositivos.

    1.  Se ainda não tiver nenhum, crie um perfil de inscrição de dispositivos para os dispositivos iOS inscritos através do Apple Configurator.

    ![Para criar um perfil](../media/pol-sa-corp-enroll.png)

    2.  Na [consola de administração do Microsoft Intune](http://manage.microsoft.com), aceda a **Política** &gt; **Dispositivos Pertencentes à Empresa** e, em seguida, clique em **Adicionar…**

        -   Criar perfil de inscrição de dispositivos Introduza os detalhes dos perfis de dispositivo:

        -   **Nome** - nome do perfil de inscrição de dispositivos. (Não é visível para os utilizadores)

        -   **Descrição** - descrição do perfil de inscrição de dispositivos.

            -   (Não é visível para os utilizadores) **Detalhes de Inscrição** - especifica a forma como os dispositivos são inscritos.
            **Pedido de afinidade de utilizadores** - o dispositivo iOS pode ser afiliado a um utilizador durante a configuração inicial e, em seguida, obter permissões para aceder ao e-mail e aos dados da empresa em nome do utilizador.

                -   Para a maioria dos cenários do Assistente de Configuração, utilize **Pedido de afinidade de utilizadores** Este modo suporta vários cenários:

                -   **Dispositivo pessoal pertencente à empresa** - "Choose Your Own Device" (CYOD) É semelhante aos dispositivos pessoais ou de propriedade privada, mas o administrador tem determinados privilégios, incluindo a permissão para eliminar, repor, administrar e anular a inscrição do dispositivo. O utilizador do dispositivo pode instalar aplicações e tem a maioria das outras permissões para utilização do dispositivo não bloqueadas pela política de gestão. **Conta do gestor da inscrição de dispositivos** - o dispositivo é inscrito através de uma conta de administrador do Intune especial.

            -   Pode ser gerida como uma conta privada, mas apenas um utilizador que conheça as credenciais do gestor de inscrições pode instalar aplicações, apagar, repor, administrar e anular a inscrição do dispositivo. Para obter informações sobre como inscrever um dispositivo partilhado por vários utilizadores através de uma conta comum, consulte o artigo [Inscrever dispositivos pertencentes à empresa com o Gestor de Inscrição de Dispositivos no Microsoft Intune](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md) **Sem afinidade de utilizadores** - o dispositivo não tem utilizadores.

        -   Utilize esta afiliação em dispositivos que efetuem tarefas sem aceder aos dados de utilizador locais. As aplicações que precisam de afiliação de utilizadores são desativadas ou não funcionam.

          -  **Pré-atribuição de grupos de dispositivos** - todos os dispositivos com este perfil implementado irão inicialmente pertencer a este grupo. Pode reatribuir dispositivos depois da inscrição.

    3.  **Device Enrollment Program** - o Device Enrollment Program (DEP) da Apple não pode ser utilizado com a inscrição do Assistente de Configuração.

3.  Certifique-se de que o botão de alternar está definido como **desativar** Clique em **Guardar Perfil** para adicionar o perfil.

    ![Adicionar dispositivos iOS para inscrição com o Assistente de Configuração](../media/pol-SA-enroll-iOS-SetupAssistant.png)

    -   Na [consola de administração do Microsoft Intune](http://manage.microsoft.com), aceda a **Grupos** &gt; **Todos os Dispositivos** &gt; **Todos os Dispositivos Pertencentes à Empresa** &gt; **Todos os Dispositivos** e, em seguida, clique em **Adicionar dispositivos…**.

        |||
        |-|-|
        |&lt;Pode adicionar dispositivos de duas formas:&gt;|&lt;Caixa de diálogo Adicionar dispositivos&gt;|
        |&lt;**Carregue um ficheiro CSV que contenha números de série** - crie uma lista de valores separados por vírgulas (.csv) de duas colunas sem cabeçalho, limitada até 5000 dispositivos ou 5 MB por ficheiro .csv.&gt;|&lt;Série n.º 1&gt;|
        Detalhes do Dispositivo n.º 1

        ```
        0000000,PO 1234
        111111111,PO 1234
        ```

    -   Série n.º2

    > [!NOTE]
    > Detalhes do Dispositivo n.º 2  Se visualizar este ficheiro .csv num editor de texto, este é apresentado como:

    **Adicionar manualmente os detalhes de dispositivos** - introduza o número de série e os detalhes de um máximo de cinco dispositivos

4.  Posteriormente, se tiver de remover dispositivos pertencentes à empresa da gestão do Intune, poderá ter de remover o número de série do dispositivo do Intune no grupo **Dispositivos pertencentes à empresa** para desativar a inscrição de dispositivos. Se o Intune efetuar um procedimento de recuperação após desastre na altura da remoção dos números de série, terá de verificar que apenas os números de série dos dispositivos ativos estão presentes nesse grupo. Em seguida, clique em **Seguinte**

5.  Selecionar os dispositivos a inscrever Confirme os dispositivos a inscrever.

6.  Os números de série já inscritos ou inscritos através de outros meios não podem ser importados. Clique em **Seguinte** para continuar. Atribuir o perfil Especifique o perfil a atribuir aos dispositivos adicionados a partir da lista de perfis disponíveis, consulte os **Detalhes do perfil de inscrição**e, em seguida, clique em **Concluir**. Os dispositivos adicionados manualmente podem ser atribuídos a qualquer perfil de inscrição.
    Exportar um perfil a implementar nos dispositivos iOS Na [consola de administração do Microsoft Intune](http://manage.microsoft.com), aceda a **Política** &gt; **Inscrição de Dispositivos da Empresa** e, em seguida, selecione o perfil de dispositivo a implementar nos dispositivos móveis.
    ```
    https://manage.microsoft.com/EnrollmentServer/Discovery.svc/iOS/ESProxy?id=
    ```
    Clique em **Exportar...**

    ```
    https://appleconfigurator2.manage.microsoft.com/MDMServiceConfig?id=
    ```

   na barra de tarefas.

    > [!NOTE]
    > Copie e guarde o **URL do Perfil**. Irá carregá-lo no Apple Configurator mais tarde para definir o perfil do Intune utilizado pelos dispositivos iOS.

7.  Para suportar o Apple Configurator 2, o URL do Perfil 2.0 tem de ser editado.

    1.  Substitua com o

         > [!WARNING]
         > No procedimento seguinte, irá carregar o URL deste perfil para o serviço DEP da Apple com o Apple Configurator para definir o perfil do Intune utilizado pelos dispositivos iOS. O URL do perfil de inscrição é válido durante duas semanas a partir do momento em que é exportado. Após as duas semanas, terá de exportar um novo URL de perfil de inscrição para inscrever dispositivos iOS com o Assistente de Configuração.

    2. Preparar o dispositivo com o Apple Configurator Os dispositivos iOS são ligados ao computador Mac e inscritos na gestão de dispositivos móveis.

    3. Num computador Mac, abra o **Apple Configurator 2**. Na barra de menus, clique em **Apple Configurator 2** e clique em **Preferências** Os dispositivos serão repostos para as configurações de fábrica durante o processo de inscrição.  

       Como melhor prática, reponha o dispositivo e ligue-o. Como melhor prática, os dispositivos deverão aparecer no ecrã **Hello** quando liga o dispositivo. No painel de preferências, selecione **Servidores** e clique no símbolo de "+" por baixo do painel da esquerda para iniciar o assistente do Servidor MDM.

    4.  Clique em **Seguinte** Introduza o **Nome** e o **URL de Inscrição** para o servidor MDM a partir do passo 6 acima. Para o URL de Inscrição, introduza o URL do perfil de inscrição exportado do Intune.

    5.  Clique em **Seguinte**

        > [!WARNING]
        > Se receber um aviso sobre requisitos de perfil de confiança para Apple TV, pode cancelar em segurança a opção **Perfil de Confiança**, clicando no "X" cinzento. Também pode ignorar em segurança qualquer aviso de certificado de âncora. Para continuar, clique em **Seguinte** até que o assistente esteja concluído.

    6.  No painel **Servidores**, clique em "Editar" ao lado do perfil do novo servidor. Certifique-se de que o URL de Inscrição corresponde exatamente ao URL exportado do Intune.

    7. Se for diferente, reintroduza o URL original e **Guarde** o perfil de inscrição exportado do Intune.

    8. Ligue os dispositivos móveis iOS ao computador Apple com um adaptador USB.

    9. Os dispositivos serão repostos para as configurações de fábrica durante o processo de inscrição.

    10. Como melhor prática, reponha o dispositivo e ligue-o. Como melhor prática, os dispositivos deverão aparecer no ecrã **Hello** quando inicia o Assistente de Configuração.  

    11. Clique em **Preparar**.  

8.  No painel **Preparar o Dispositivo iOS**, selecione **Manual** e clique em **Seguinte** No painel **Inscrever no servidor MDM**, selecione o nome do servidor que criou e clique em **Seguinte** No painel **Supervisionar Dispositivos**, selecione o nível de supervisão e, em seguida, clique em **Seguinte**



### No painel **Criar uma Organização**, escolha a **Organização** ou crie uma nova organização e, em seguida, clique em **Seguinte**
[No painel **Configurar Assistente de Configuração iOS**, escolha os passos apresentados ao utilizador e, em seguida, clique em **Preparar**.](get-ready-to-enroll-devices-in-microsoft-intune.md)


<!--HONumber=May16_HO2-->


