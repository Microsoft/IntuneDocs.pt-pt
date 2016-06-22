---
# required metadata

title: Inscrição direta para dispositivos iOS| Microsoft Intune
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
ms.reviewer: dagerrit
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Inscrever diretamente dispositivos iOS com o Apple Configurator
O Intune suporta a inscrição de dispositivos iOS pertencentes à empresa com a ferramenta [Apple Configurator](http://go.microsoft.com/fwlink/?LinkId=518017) em execução num computador Mac. Este processo não efetua a reposição de fábrica do dispositivo e inscreve o dispositivo com uma política predefinida. Este método destina-se a dispositivos **Sem afinidade de utilizadores** e requer que ligue o dispositivo iOS através de USB a um computador Mac para configurar a inscrição empresarial. A aplicação Portal da Empresa não é suportada para os dispositivos inscritos através de inscrição direta. Esta instrução parte do princípio de que está a utilizar o Apple Configurator 2.0 no computador Mac.

1.  **Criar um perfil para dispositivos** Um perfil de inscrição de dispositivos especifica as definições aplicadas aos dispositivos. Se ainda não tiver nenhum, crie um perfil de inscrição de dispositivos para os dispositivos iOS inscritos através do Apple Configurator.

    #### Para criar um perfil

    1.  Na [consola de administração do Microsoft Intune](http://manage.microsoft.com) vá para **Política** &gt; **Inscrição de Dispositivos da Empresa** e, em seguida, selecione **Adicionar…**.

        ![Página de criação de perfil de inscrição de dispositivos móveis](../media/pol-sa-corp-enroll.png)

    2.  Introduza os detalhes dos perfis de dispositivo:

        -   **Nome** - nome do perfil de inscrição de dispositivos. Não é visível para os utilizadores.

        -   **Descrição** - descrição do perfil de inscrição de dispositivos. Não é visível para os utilizadores.

        -   **Afiliação de utilizadores** - especifica a forma como os dispositivos são inscritos. Para a Inscrição Direta, selecione **Sem afinidade de utilizador**.

        -   **Pré-atribuição de grupos de dispositivos** - todos os dispositivos com este perfil implementado irão inicialmente pertencer a este grupo. Pode reatribuir dispositivos depois da inscrição.

    3.  Clique em **Guardar Perfil** para adicionar o perfil.

5.  **Exportar um perfil como .mobileconfig para implementar em dispositivos iOS** Selecione o perfil de dispositivo que criou. Selecione **Exportar...** na barra de tarefas. Clique em **Transferir perfil** e guarde o ficheiro .mobileconfig transferido.

6.  **Transferir o ficheiro** Copie o ficheiro .mobileconfig transferido para um computador Mac.
    > [!NOTE]
    > O URL do perfil de inscrição é válido durante duas semanas a partir do momento em que é exportado. Após duas semanas, tem de exportar um novo URL de perfil de inscrição para inscrever dispositivos iOS com o Assistente de Configuração.
7.  **Preparar o dispositivo com o Apple Configurator** Os dispositivos iOS são ligados ao computador Mac e inscritos na gestão de dispositivos móveis.

    1.  Num computador Mac, inicie o **Apple Configurator 2.0**.

    2.  Ligue o dispositivo iOS ao computador Mac com um cabo USB. Feche **Fotografias**, o **iTunes** e outras aplicações que abrem para o dispositivo quando o dispositivo é detetado.

    3.  No Apple Configurator, clique uma vez no dispositivo iOS ligado e, em seguida, selecione o botão **Adicionar**. As opções que podem ser adicionadas ao dispositivo aparecem na lista pendente. Selecione **Perfis** .

    4.  Utilize o seletor de ficheiros para selecionar o ficheiro .mobileconfig que exportou a partir do Intune e, em seguida, selecione **Adicionar**. O perfil é adicionado ao dispositivo.  Se o dispositivo for **Sem supervisão**, a instalação irá necessitar de aceitação no dispositivo.

8.  **Instalar o perfil** Está pronto para instalar o perfil no dispositivo iOS. O dispositivo já tem de ter concluído o Assistente de Configuração e estar pronto a utilizar.  Se o registo implicar implementações de aplicações, o dispositivo deve ter um ID Apple configurado porque as implementações de aplicações irão exigir que tenha um ID Apple registado na App Store.

    ###### Concluir a aceitação do perfil para dispositivos iOS sem supervisão

    1.  Desbloqueie o dispositivo iOS.

    2.  Na caixa de diálogo **Instalar perfil** de **Perfil de gestão**, toque em **Instalar**.

    3.  Forneça o **Código de Acesso do Dispositivo** ou o **ID Apple**, se necessário.

    4.  Aceite o **Aviso** e toque em **Instalar**.

    5.  Aceite o **Aviso Remoto** e toque em **Confiar**.

    6.  Quando a caixa **Perfil instalado** confirmar que o perfil foi **Instalado**, selecione **Concluído**.

9. **Verificar perfil**
    No dispositivo iOS, inicie **Definições** e vá para **Geral** &gt; **Gestão de Dispositivos** &gt; **Perfil de Gestão** &gt; e confirme se a instalação do perfil está listada, verifique as restrições de política iOS e as aplicações instaladas. As restrições de política e as aplicações podem demorar até 10 minutos a aparecer no dispositivo.

10. **Distribuir dispositivos** O dispositivo iOS está agora inscrito no Intune e gerido.


### Consulte também
[Prepare-se para inscrever dispositivos](get-ready-to-enroll-devices-in-microsoft-intune.md)


<!--HONumber=Jun16_HO3-->


