---
# required metadata

title: Inscrição direta para dispositivos iOS com o Microsoft Intune | Microsoft Intune
description:
keywords:
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: a692b90c-72ae-47d1-ba9c-67a2e2576cc2

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Inscrever diretamente dispositivos iOS com o Apple Configurator
O Intune suporta a inscrição de dispositivos iOS pertencentes à empresa com a ferramenta [Apple Configurator](http://go.microsoft.com/fwlink/?LinkId=518017) em execução num computador Mac. Este processo não efetua a reposição de fábrica do dispositivo e inscreve o dispositivo com uma política predefinida. Este método destina-se a dispositivos **Sem afinidade de utilizadores** e requer que ligue o dispositivo iOS através de USB a um computador Mac para configurar a inscrição empresarial. A aplicação Portal da Empresa não é suportada para os dispositivos inscritos através de inscrição direta. Esta instrução parte do princípio de que está a utilizar o Apple Configurator 2.0 no computador Mac.

1.  Criar um perfil para dispositivos Um perfil de inscrição de dispositivos especifica as definições aplicadas aos dispositivos.

    #### Se ainda não tiver nenhum, crie um perfil de inscrição de dispositivos para os dispositivos iOS inscritos através do Apple Configurator.

    1.  Para criar um perfil

        ![Na [consola de administração do Microsoft Intune](http://manage.microsoft.com), aceda a **Política** &gt; **Inscrição de Dispositivos da Empresa** e, em seguida, clique em **Adicionar…**](../media/pol-sa-corp-enroll.png)

    2.  Página de criação de perfil de inscrição de dispositivos móveis

        -   Introduza os detalhes dos perfis de dispositivo: **Nome** - nome do perfil de inscrição de dispositivos.

        -   Não é visível para os utilizadores. **Descrição** - descrição do perfil de inscrição de dispositivos.

        -   Não é visível para os utilizadores. **Afiliação de utilizadores** - especifica a forma como os dispositivos são inscritos.

        -   Para a Inscrição Direta, selecione **Sem afinidade de utilizador** **Pré-atribuição de grupos de dispositivos** – todos os dispositivos com este perfil implementado irão inicialmente pertencer a este grupo.

    3.  Pode reatribuir dispositivos depois da inscrição.

2.  Clique em **Guardar Perfil** para adicionar o perfil.

    ![Adicionar dispositivos iOS para inscrever com o Apple Configurator](../media/pol-SA-enroll-iOS-SetupAssistant.png)

      Na [consola de administração do Microsoft Intune](http://manage.microsoft.com), aceda a **Grupos** &gt; **Todos os Dispositivos** &gt; **Dispositivos pré-inscritos da empresa** &gt; **Por número de série iOS** e, em seguida, faça clique em **Adicionar dispositivos…**

    -   Assistente de configuração de iOS

        |||
        |-|-|
        |&lt;Pode adicionar dispositivos de duas formas:&gt;|&lt;**Carregue um ficheiro CSV que contenha números de série** - crie uma lista de valores separados por vírgulas (.csv) de duas colunas sem cabeçalho, limitada até 5000 dispositivos ou 5 MB por ficheiro .csv.&gt;|
        |&lt;Série n.º 1&gt;|&lt;Detalhes do Dispositivo n.º 1&gt;|
        Série n.º2

        ```
        0000000,PO 1234
        111111111,PO 1234
        ```

    -   Detalhes do Dispositivo n.º 2

    > [!NOTE]
    > Se visualizar este ficheiro .csv num editor de texto, este é apresentado como:  **Adicione manualmente os detalhes do dispositivo** - introduza o número de série e os detalhes de até cinco dispositivos e clique em **Seguinte**

3.  Posteriormente, se tiver de remover da gestão do Intune dispositivos pertencentes à empresa, tem de remover o número de série do dispositivo do Intune no grupo **Dispositivos pertencentes à empresa** para desativar a inscrição de dispositivos. Se o Intune efetuar um procedimento de recuperação após desastre na altura da remoção dos números de série, terá de verificar que apenas os números de série dos dispositivos ativos estão presentes nesse grupo. Selecionar os dispositivos a inscrever

4.  Confirme os dispositivos a inscrever. Os números de série já inscritos ou inscritos através de outros meios não podem ser importados.

5.  Clique em **Seguinte** para continuar. Atribuir o perfil Especifique o perfil a atribuir aos dispositivos adicionados a partir da lista de perfis disponíveis, consulte os **Detalhes do perfil de inscrição**e, em seguida, clique em **Concluir**. Os dispositivos adicionados manualmente podem ser atribuídos a qualquer perfil de inscrição. Selecionar um perfil a implementar nos dispositivos iOS

6.  Na [consola de administração do Microsoft Intune](http://manage.microsoft.com), aceda a **Política** &gt; **Inscrição de Dispositivos da Empresa** e, em seguida, selecione o perfil de dispositivo a implementar nos dispositivos móveis.
    > [!NOTE]
    > Este perfil deve ser o mesmo perfil que atribuiu para implementar no passo anterior. Clique em **Exportar...**
7.  na barra de tarefas.

    1.  Clique em **Transferir perfil** e guarde o ficheiro .mobileconfig transferido.

    2.  Transferir o ficheiro Copie o ficheiro .mobileconfig transferido para um computador Mac.

    3.  O URL do perfil de inscrição é válido durante duas semanas a partir do momento em que é exportado. Após duas semanas, tem de exportar um novo URL de perfil de inscrição para inscrever dispositivos iOS com o Assistente de Configuração. Preparar o dispositivo com o Apple Configurator

    4.  Os dispositivos iOS são ligados ao computador Mac e inscritos na gestão de dispositivos móveis. Num computador Mac, inicie o **Apple Configurator 2.0**  Ligue o dispositivo iOS ao computador Mac com um cabo USB.

8.  Feche **Fotografias**, o **iTunes** e outras aplicações que abrem para o dispositivo quando o dispositivo é detetado. No Apple Configurator, clique uma vez no dispositivo iOS ligado e, em seguida, clique no botão **Adicionar**.  As opções que podem ser adicionadas ao dispositivo aparecem na lista pendente.

    ###### Clique em **Perfis**

    1.  Utilize o seletor de ficheiros para selecionar o ficheiro .mobileconfig que exportou a partir do Intune e, em seguida, clique em **Adicionar**.

    2.  O perfil é adicionado ao dispositivo.

    3.  Se o dispositivo for **Sem supervisão**, a instalação irá necessitar de aceitação no dispositivo.

    4.  Instalar o perfil

    5.  Está pronto para instalar o perfil no dispositivo iOS.

    6.  O dispositivo já tem de ter concluído o Assistente de Configuração e estar pronto a utilizar.

9. Se o registo implicar implementações de aplicações, o dispositivo deve ter um ID Apple configurado porque as implementações de aplicações irão exigir que tenha um ID Apple registado na App Store. Concluir a aceitação do perfil para dispositivos iOS sem supervisão

10. Desbloqueie o dispositivo iOS.


### Na caixa de diálogo **Instalar perfil** de **Perfil de gestão**, toque em **Instalar**
[Forneça o **Código de Acesso do Dispositivo** ou o **ID Apple**, se necessário.](get-ready-to-enroll-devices-in-microsoft-intune.md)


<!--HONumber=May16_HO2-->


