---
title: "Inscrever dispositivos iOS com o Assistente de Configuração | Microsoft Intune"
description: "Inscreva dispositivos iOS pertencentes à empresa com a ferramenta Apple Configurator para repor as predefinições de fábrica do dispositivo e prepará-lo para executar o Assistente de Configuração."
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/20/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 46e5b027-4280-4809-b45f-651a6ab6d0cd
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: e2daff5dae435df55c866adbf602f554500d50e0
ms.openlocfilehash: 45aa4511945ab4763dc0dc35baefe47887e561bb


---

# Inscrever dispositivos iOS com o Apple Configurator utilizando o Assistente de Configuração
O Intune suporta a inscrição de dispositivos iOS pertencentes à empresa com a ferramenta [Apple Configurator](http://go.microsoft.com/fwlink/?LinkId=518017) em execução num computador Mac. Este processo efetua a reposição de fábrica do dispositivo e prepara-o para executar o Assistente de Configuração pelo novo utilizador do dispositivo com as políticas da empresa pré-instaladas.


## Inscrição do Assistente de Configuração para dispositivos iOS com Microsoft Intune
Através do Apple Configurator pode repor as definições de fábrica dos dispositivos iOS e prepará-los para serem configurados pelo novo utilizador do dispositivo.  Este método requer que ligue o dispositivo iOS através de USB a um computador Mac para configurar a inscrição empresarial e parte do princípio de que está a utilizar o Apple Configurator 2.0. A maioria dos cenários exige que a política aplicada ao dispositivo iOS inclua **afinidade de utilizador** para ativar a aplicação Portal da Empresa do Intune.

**Pré-requisitos**
* [Inscrição de iOS ativada](set-up-ios-and-mac-management-with-microsoft-intune.md) mediante a instalação de um certificado APNs.
* Acesso físico aos dispositivos iOS - a configuração dos dispositivos tem de ser anulada (reposição de fábrica) sem proteção por palavra-passe
* Números de série de dispositivos - [como obter um número de série iOS](https://support.apple.com/en-us/HT204308)
* Cabos de ligação USB
* Computador Mac com o [Apple Configurator 2.0](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12)


1.  **Criar um grupo de dispositivos móveis** (opcional) Se a sua empresa precisar de grupos de dispositivos móveis para ajudar a gerir dispositivos, crie-os. [Utilize grupos para gerir utilizadores e dispositivos com o Microsoft Intune](use-groups-to-manage-users-and-devices-with-microsoft-intune.md).

2.  **Criar um perfil para dispositivos** Um perfil de inscrição de dispositivos especifica as definições aplicadas a um grupo de dispositivos. Se ainda não tiver nenhum, crie um perfil de inscrição de dispositivos para os dispositivos iOS inscritos através do Apple Configurator.

    1.  Na [consola de administração do Microsoft Intune](http://manage.microsoft.com) vá para **Política** &gt; **Inscrição de Dispositivos da Empresa** e, em seguida, selecione **Adicionar…**.
    ![Criar perfil de inscrição de dispositivos](../media/pol-sa-corp-enroll.png)

    2.  Introduza os detalhes dos perfis de dispositivo:

        -   **Nome** - nome do perfil de inscrição de dispositivos. (Não é visível para os utilizadores)

        -   **Descrição** - descrição do perfil de inscrição de dispositivos. (Não é visível para os utilizadores)

        -   **Detalhes de Inscrição** - especifica a forma como os dispositivos são inscritos.

            -   **Pedido de afinidade de utilizador** – O dispositivo tem de ser afiliado a um utilizador durante a configuração inicial e, em seguida, receber permissões para aceder ao e-mail e aos dados da empresa em nome do utilizador. A **afinidade de utilizador** deve ser configurada para dispositivos geridos por DEP que pertencem aos utilizadores e que precisam de utilizar o portal da empresa (por exemplo, para instalar aplicações).

            -   **Sem afinidade de utilizador** – O dispositivo não está afiliado a um utilizador. Utilize esta afiliação em dispositivos que efetuem tarefas sem aceder aos dados de utilizador locais. As aplicações que requerem afiliação de utilizadores, incluindo a aplicação Portal da Empresa utilizada para instalar aplicações de linha de negócio, não irão funcionar.

        -   **Pré-atribuição de grupos de dispositivos** - todos os dispositivos com este perfil implementado irão inicialmente pertencer a este grupo. Pode reatribuir dispositivos depois da inscrição.

            [!INCLUDE[groups deprecated](../includes/group-deprecation.md)]

          -  **Device Enrollment Program** - o Device Enrollment Program (DEP) da Apple não pode ser utilizado com a inscrição do Assistente de Configuração. Certifique-se de que a alternância de modo está definida como **desativar**.

    3.  Clique em **Guardar Perfil** para adicionar o perfil.

3.  **Adicionar dispositivos iOS para inscrição com o Assistente de Configuração** Na [consola de administração do Microsoft Intune](http://manage.microsoft.com) vá para **Grupos** &gt; **Todos os Dispositivos** &gt; **Todos os Dispositivos Pertencentes à Empresa** &gt; **Todos os Dispositivos** e, em seguida, selecione **Adicionar dispositivos…**. Pode adicionar dispositivos de duas formas:

    ![Caixa de diálogo Adicionar dispositivos](../media/pol-SA-enroll-iOS-SetupAssistant.png)

    -   **Carregue um ficheiro CSV que contenha números de série** - crie uma lista de valores separados por vírgulas (.csv) de duas colunas sem cabeçalho, limitada até 5000 dispositivos ou 5 MB por ficheiro .csv.

        |||
        |-|-|
        |&lt;Série n.º 1&gt;|&lt;Detalhes do Dispositivo n.º 1&gt;|
        |&lt;Série n.º2&gt;|&lt;Detalhes do Dispositivo n.º 2&gt;|
        Se visualizar este ficheiro .csv num editor de texto, este é apresentado como:

        ```
        0000000,PO 1234
        111111111,PO 1234
        ```

    -   **Adicionar manualmente os detalhes de dispositivos** - introduza o número de série e os detalhes de um máximo de cinco dispositivos

    > [!NOTE]
    > Posteriormente, se tiver de remover dispositivos pertencentes à empresa da gestão do Intune, poderá ter de remover o número de série do dispositivo do Intune no grupo de dispositivos **Por Número de Série do iOS** em **Dispositivos Pré-inscritos Empresariais** para desativar a inscrição do dispositivo.  Se o Intune efetuar um procedimento de recuperação após desastre na altura da remoção dos números de série, terá de verificar que apenas os números de série dos dispositivos ativos estão presentes nesse grupo.

    Escolha **Seguinte**.

4.  **Selecionar os dispositivos a inscrever** Confirme os dispositivos a inscrever. Os números de série já inscritos ou inscritos através de outros meios não podem ser importados. Selecione **Seguinte** para continuar.

5.  **Atribuir o perfil** Especifique o perfil a atribuir aos dispositivos adicionados a partir da lista de perfis disponíveis, consulte os **Detalhes do perfil de inscrição**, e, em seguida, escolha **Concluir**. Os dispositivos adicionados manualmente podem ser atribuídos a qualquer perfil de inscrição.

6.  **Exportar um perfil para implementar nos dispositivos iOS** Na [consola de administração do Microsoft Intune](http://manage.microsoft.com) vá para **Política** &gt; **Inscrição de Dispositivos da Empresa** e, em seguida, selecione o perfil de dispositivo a implementar nos dispositivos móveis. Selecione **Exportar...** na barra de tarefas. Copie e guarde o **URL do Perfil**. Irá carregá-lo no Apple Configurator mais tarde para definir o perfil do Intune utilizado pelos dispositivos iOS.
    Para suportar o Apple Configurator 2, o URL do Perfil 2.0 tem de ser editado. Substitua
    ```
    https://manage.microsoft.com/EnrollmentServer/Discovery.svc/iOS/ESProxy?id=
    ```
    com o

    ```
    https://appleconfigurator2.manage.microsoft.com/MDMServiceConfig?id=
    ```

   No procedimento seguinte, irá carregar o URL deste perfil para o serviço DEP da Apple com o Apple Configurator para definir o perfil do Intune utilizado pelos dispositivos iOS.



7.  **Preparar o dispositivo com o Apple Configurator** Os dispositivos iOS são ligados ao computador Mac e inscritos na gestão de dispositivos móveis.

    1.  Num computador Mac, abra o **Apple Configurator 2**. Na barra de menus, selecione **Apple Configurator 2** e selecione **Preferências**.

         > [!WARNING]
         > Os dispositivos serão repostos para as configurações de fábrica durante o processo de inscrição. Como melhor prática, reponha o dispositivo e ligue-o. Como melhor prática, os dispositivos deverão aparecer no ecrã **Hello** quando liga o dispositivo.

    2. No painel de preferências, selecione **Servidores** e selecione o símbolo de "+" por baixo do painel da esquerda para iniciar o assistente do Servidor MDM. Escolha **Seguinte**.

    3. Introduza o **Nome** e o **URL de Inscrição** para o servidor MDM a partir do passo 6 acima. Para o URL de Inscrição, introduza o URL do perfil de inscrição exportado do Intune. Escolha **Seguinte**.  

       Se receber um aviso a indicar "URL do servidor não verificado", pode ignorar o aviso em segurança. Para continuar, selecione **Seguinte** até que o assistente esteja concluído.

    4.  Ligue os dispositivos móveis iOS ao computador Apple com um adaptador USB.

        > [!WARNING]
        > Os dispositivos serão repostos para as configurações de fábrica durante o processo de inscrição. Como melhor prática, reponha o dispositivo e ligue-o. Como melhor prática, os dispositivos deverão aparecer no ecrã **Hello** quando inicia o Assistente de Configuração.

    5.  Selecione **Preparar**. No painel **Preparar o Dispositivo iOS**, selecione **Manual** e selecione **Seguinte**.

    6. No painel **Inscrever no servidor MDM**, selecione o nome do servidor que criou e selecione **Seguinte**.

    7. No painel **Supervisionar Dispositivos**, selecione o nível de supervisão e, em seguida, selecione **Seguinte**.

    8. No painel **Criar uma Organização**, escolha a **Organização** ou crie uma nova organização e, em seguida, selecione **Seguinte**.

    9. No painel **Configurar Assistente de Configuração iOS**, escolha os passos apresentados ao utilizador e, em seguida, selecione **Preparar**. Se lhe for pedido, autentique para atualizar as definições de fidedignidade.  

    10. Quando concluir a preparação do dispositivo iOS, pode desligar o cabo USB.  

8.  **Distribuir os dispositivos** Os dispositivos estão agora prontos para a inscrição empresarial. Desligue os dispositivos e distribua-os pelos utilizadores. Quando o dispositivo estiver ligado, será iniciado o Assistente de Configuração.



### Consulte também
[Prepare-se para inscrever dispositivos](get-ready-to-enroll-devices-in-microsoft-intune.md)



<!--HONumber=Sep16_HO2-->


