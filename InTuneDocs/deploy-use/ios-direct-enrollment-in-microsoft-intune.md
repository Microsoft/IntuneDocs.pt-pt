---
title: "Inscrição direta para dispositivos iOS | Documentos da Microsoft"
description: "Utilize a ferramenta Apple Configurator para inscrever diretamente dispositivos iOS pertencentes à empresa com uma política predefinida ao ligá-los por USB a um computador Mac."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 01/29/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a692b90c-72ae-47d1-ba9c-67a2e2576cc2
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 8b2bd3ecba0b597bc742ea08872ffe8fc58155cf
ms.openlocfilehash: ee0320db2c4a1a977326f62fcd20597fa39aba24
ms.lasthandoff: 04/24/2017


---

# <a name="directly-enroll-ios-devices-by-using-apple-configurator"></a>Inscrever diretamente dispositivos iOS ao utilizar o Apple Configurator

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

O Intune suporta a inscrição de dispositivos iOS propriedade da empresa com a ferramenta [Apple Configurator](http://go.microsoft.com/fwlink/?LinkId=518017) em execução num computador Mac. Este processo não efetua a reposição de fábrica do dispositivo e inscreve o dispositivo com uma política predefinida. Este método destina-se a dispositivos **Sem afinidade de utilizadores** e requer que ligue o dispositivo iOS através de USB a um computador Mac para configurar a inscrição empresarial.

Quando estiver a inscrever diretamente dispositivos iOS, pode inscrever um dispositivo sem adquirir o número de série do mesmo. Também pode dar um nome ao dispositivo para fins de identificação antes de o Intune capturar o nome do dispositivo durante a inscrição. A aplicação Portal da Empresa não é suportada para os dispositivos inscritos diretamente. Esta instrução parte do princípio de que está a utilizar o Apple Configurator 2.0 no computador Mac.

>[!NOTE]
>Este método de inscrição não pode ser utilizado com o método do [gestor de inscrição de dispositivos](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md).

1.  Se ainda não tiver nenhum, crie um perfil de inscrição de dispositivos para os dispositivos iOS inscritos através do Apple Configurator. Um perfil de inscrição de dispositivos especifica as definições aplicadas aos dispositivos.

    1.  Na [consola de administração do Microsoft Intune](https://manage.microsoft.com) aceda a **Policy** &gt; **Corporate Device Enrollment** e, em seguida, selecione **Add**.

        ![Página de criação de perfil de inscrição de dispositivos móveis](../media/pol-sa-corp-enroll.png)

    2.  Introduza os detalhes dos perfis de dispositivo:

        -   **Nome**: o nome do perfil de inscrição de dispositivos. Não é visível para os utilizadores.

        -   **Descrição**: a descrição do perfil de inscrição do dispositivo. Não é visível para os utilizadores.

        -   **Afiliação de utilizadores**: especifica a forma como os dispositivos são inscritos. Para a Inscrição Direta, selecione **Sem afinidade de utilizador**.

        -   **Pré-atribuição de grupos de dispositivos**: todos os dispositivos com este perfil irão inicialmente pertencer a este grupo. Pode reatribuir dispositivos depois da inscrição.

            [!INCLUDE[groups deprecated](../includes/group-deprecation.md)]

    3.  Clique em **Guardar Perfil** para adicionar o perfil.

5.  Exportar um perfil como .mobileconfig para implementar em dispositivos iOS:

    1.   Selecione o perfil de dispositivo que criou.

    2.   Selecione **Exportar** na barra de tarefas.

    3.   Clique em **Transferir perfil** e guarde o ficheiro .mobileconfig transferido.

6.  Transfira o ficheiro ao copiar o ficheiro .mobileconfig transferido para um computador Mac.
    > [!NOTE]
    > O URL do perfil de inscrição é válido durante duas semanas a partir do momento em que é exportado. Após duas semanas, tem de exportar um novo URL de perfil de inscrição para inscrever dispositivos iOS com o Assistente de Configuração.

7.  Preparar o dispositivo com o Apple Configurator. Os dispositivos iOS são ligados ao computador Mac e inscritos na gestão de dispositivos móveis.

    1.  Num computador Mac, abra o **Apple Configurator 2.0**.

    2.  Ligue o dispositivo iOS ao computador Mac com um cabo USB. Feche **Fotografias**, o **iTunes** e outras aplicações que abrem para o dispositivo quando o dispositivo é detetado.

    3.  No Apple Configurator, selecione o dispositivo iOS ligado e, em seguida, selecione o botão **Adicionar**. As opções que podem ser adicionadas ao dispositivo aparecem na lista pendente. Selecione **Perfis**.

    4.  Utilize o seletor de ficheiros para selecionar o ficheiro .mobileconfig que exportou a partir do Intune e, em seguida, selecione **Adicionar**. O perfil é adicionado ao dispositivo.  Se o dispositivo for **Sem supervisão**, a instalação irá necessitar de aceitação no dispositivo.

8.  Está pronto para instalar o perfil no dispositivo iOS. O dispositivo já tem de ter concluído o Assistente de Configuração e estar pronto a utilizar. Se o registo implicar implementações de aplicações, o dispositivo deve ter um ID Apple configurado porque as implementações de aplicações irão exigir que tenha um ID Apple registado na App Store.

    1.  Desbloqueie o dispositivo iOS.

    2.  Na caixa de diálogo **Instalar perfil** de **Perfil de gestão**, selecione **Instalar**.

    3.  Forneça o **Código de Acesso do Dispositivo** ou o **ID Apple**, se necessário.

    4.  Aceite o **Aviso** e selecione **Instalar**.

    5.  Aceite o **Aviso Remoto** e selecione **Confiar**.

    6.  Quando a caixa **Perfil instalado** confirmar que o perfil foi **Instalado**, selecione **Concluído**.

9.  No dispositivo iOS, abra as **Definições** e aceda a **Geral** &gt; **Gestão de Dispositivos** &gt; **Perfil de Gestão**. Confirme que a instalação do perfil se encontra na lista e verifique as restrições de política do iOS e as aplicações instaladas. As restrições de política e as aplicações poderão demorar até 10 minutos a aparecer no dispositivo.

10.  Distribua os dispositivos. O dispositivo iOS está agora inscrito no Intune e gerido.

