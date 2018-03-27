---
title: Inscrever dispositivos iOS com o Assistente de Configuração
description: Inscreva dispositivos iOS pertencentes à empresa com a ferramenta Apple Configurator para repor as predefinições de fábrica do dispositivo e prepará-lo para executar o Assistente de Configuração.
keywords: ''
author: nathbarn
ms.author: nathbarn
manager: dougeby
ms.date: 03/28/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 46e5b027-4280-4809-b45f-651a6ab6d0cd
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: a33c383cb65d0edfa94117278e3f473699588aa3
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2018
---
# <a name="enroll-ios-devices-with-apple-configurator-by-using-setup-assistant"></a>Inscrever dispositivos iOS com o Apple Configurator ao utilizar o Assistente de Configuração

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

O Intune suporta a inscrição de dispositivos iOS pertencentes à empresa com o [Apple Configurator](http://go.microsoft.com/fwlink/?LinkId=518017) em execução num computador Mac. Este processo efetua a reposição de fábrica do dispositivo e prepara-o para executar o Assistente de Configuração, ao instalar as políticas da empresa para o novo utilizador do dispositivo.

>[!NOTE]
>Este método de inscrição não pode ser utilizado com o método do [gestor de inscrição de dispositivos](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md).

Através do Apple Configurator, pode repor um dispositivo iOS para as definições de fábrica e preparar a sua configuração para o novo utilizador do dispositivo. Este método requer que ligue o dispositivo iOS a um computador Mac através de USB para configurar a inscrição empresarial e parte do princípio de que está a utilizar o Apple Configurator 2.0. A maioria dos cenários exige que a política aplicada ao dispositivo iOS inclua **afinidade de utilizador** para ativar a aplicação Portal da Empresa do Intune.

## <a name="prerequisites-for-enrolling-ios-devices-by-using-apple-configurator-with-setup-assistant"></a>Pré-requisitos para inscrever dispositivos iOS através do Apple Configurator com o Assistente de Configuração

- [Instalar um certificado do APNs](set-up-ios-and-mac-management-with-microsoft-intune.md)

- Certificar-se de que tem acesso físico aos dispositivos iOS&mdash;os dispositivos têm de ser repostos para as definições de fábrica sem proteção por palavra-passe

- Obter números de série de dispositivos&mdash;veja [Como obter um número de série iOS](https://support.apple.com/HT204308)

- Ter cabos de ligação USB disponíveis

- Ter um computador Mac com o [Apple Configurator 2.0](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12)


## <a name="steps-to-enroll-ios-devices-by-using-apple-configurator-with-setup-assistant"></a>Passos para inscrever dispositivos iOS através do Apple Configurator com o Assistente de Configuração

Os passos seguintes explicam como inscrever dispositivos iOS no "dia 0" através do Apple Configurator com o Assistente de Configuração. À medida que os dispositivos são adicionados e removidos da sua organização, é provável que repita alguns destes passos, como adicionar ou remover números de série, conforme descrito abaixo.

### <a name="create-mobile-device-groups-optional"></a>Criar grupos de dispositivos móveis (opcional)

Se a sua empresa precisar de grupos de dispositivos móveis para ajudar a gerir dispositivos, pode criá-los opcionalmente. Para saber mais, veja [Utilizar grupos para gerir utilizadores e dispositivos no Microsoft Intune](use-groups-to-manage-users-and-devices-with-microsoft-intune.md).

### <a name="create-a-profile-for-devices"></a>Criar um perfil para dispositivos

Um perfil de inscrição de dispositivos especifica as definições aplicadas a um grupo de dispositivos.

1. Na [consola de administração do Microsoft Intune](https://manage.microsoft.com) aceda a **Policy** &gt; **Corporate Device Enrollment** e, em seguida, selecione **Add**.

  ![Criar perfil de inscrição de dispositivos](../media/pol-sa-corp-enroll.png)

2. Introduza os detalhes dos perfis de dispositivo:

   -   **Name**&mdash;nome do perfil de inscrição de dispositivos (não visível para os utilizadores).

   -   **Description**&mdash;uma descrição do perfil de inscrição de dispositivos (não visível para os utilizadores).

   -   **Enrollment Details**&mdash;especifica a forma como os dispositivos são inscritos.

       -   **Prompt for user affinity**&mdash;o dispositivo tem de ser afiliado a um utilizador durante a configuração inicial e, em seguida, pode receber permissões para aceder ao e-mail e aos dados da empresa. O valor **Afinidade do utilizador** deve ser configurado para dispositivos geridos que pertencem aos utilizadores e que precisam de utilizar o portal da empresa para serviços como a instalação de aplicações.

       -   **No user affinity**&mdash;o dispositivo não está afiliado a um utilizador. Utilize esta afiliação em dispositivos que efetuem tarefas sem aceder aos dados de utilizador locais. As aplicações que requerem afiliação de utilizadores (incluindo a aplicação Portal da Empresa utilizada para instalar aplicações de linha de negócio) não irão funcionar.

   -   **Device group pre-assignment**&mdash;todos os dispositivos implementados com este perfil irão inicialmente pertencer a este grupo. Pode reatribuir dispositivos depois da inscrição.

   > [!Important]
   > As atribuições de grupos estão a ser mudadas do Intune para o Azure Active Directory. Assim que a sua conta do Intune receber a atualização aplicável, não verá a opção **Atribuir dispositivos ao seguinte grupo**. [Saiba mais](/intune-classic/deploy-use/ios-device-enrollment-program-in-microsoft-intune#changes-to-intune-group-assignments).

   -  **Device Enrollment Program**&mdash;O Device Enrollment Program (DEP) da Apple não pode ser utilizado com a inscrição do Assistente de Configuração. Certifique-se de que a alternância de modo está definida como **off**.

3.  Clique em **Save Profile** para adicionar o perfil.

### <a name="add-ios-devices-to-enroll-with-setup-assistant"></a>Adicionar dispositivos iOS para inscrição com o Assistente de Configuração

1. Na [Consola de administração do Microsoft Intune](https://manage.microsoft.com), aceda a **Groups** &gt; **All Devices** &gt; **All Corporate-owned Devices** &gt; **All Devices** e, em seguida, selecione **Add devices**.

   Pode adicionar dispositivos de duas formas:

   ![Caixa de diálogo Adicionar dispositivos](../media/pol-SA-enroll-iOS-SetupAssistant.png)

   -  **Upload a CSV file containing serial numbers**&mdash;crie uma lista de valores separados por vírgulas (.csv) de duas colunas sem cabeçalho, limitada até 5 000 dispositivos ou 5 MB por ficheiro .csv.

    |||
    |-|-|
    |&lt;Série n.º 1&gt;|&lt;Detalhes do Dispositivo n.º 1&gt;|
    |&lt;Série n.º2&gt;|&lt;Detalhes do Dispositivo n.º 2&gt;|

  Se abrir este ficheiro .csv num editor de texto, este será apresentado como:

    ```
    0000000,PO 1234
    111111111,PO 1234
    ```

  -  **Adicionar manualmente os detalhes dos dispositivos**&mdash;Introduza os números de série e todas as notas ou detalhes de até 15 dispositivos.

  Pode confirmar os números de série no painel **Review Devices**. Também pode decidir se quer substituir os **Details** dos números de série que serão importados novamente ou pode desmarcar a caixa **Overwrite** para manter os Detalhes atuais.

  > [!NOTE]
  > Na consola de administrador existente do Intune, os administradores podem aceitar detalhes associados de um CSV carregado e substituir os detalhes existentes por números de série individuais. No novo portal do Azure, apenas poderá substituir os detalhes de todos os números de série ou ignorar os novos detalhes de todos os números de série.

  > [!NOTE]
  > Posteriormente, se quiser remover dispositivos pertencentes à empresa da gestão do Intune, poderá ter de aceder ao grupo de dispositivos **Por Números de Série iOS** em **Dispositivos Pré-inscritos empresariais** e remova o número de série do dispositivo do Intune para desativar a inscrição de dispositivos. Se o Intune efetuar um procedimento de recuperação após desastre na altura em que remover os números de série, terá de verificar que apenas os números de série dos dispositivos ativos estão presentes nesse grupo.

2. Selecione **Next**.

3. Selecione os dispositivos a inscrever. Os números de série já inscritos ou inscritos através de outros meios não podem ser importados. Selecione **Next** para continuar.

### <a name="assign-a-profile"></a>Atribuir um perfil

Especifique o perfil a atribuir aos dispositivos adicionados a partir da lista de perfis disponíveis, consulte os **Enrollment profile details**e, em seguida, selecione **Finish**. Os dispositivos adicionados manualmente podem ser atribuídos a qualquer perfil de inscrição.

> [!Important]
> Atualmente, o Intune permite-lhe designar um perfil de inscrição de dispositivos “predefinido”, o que significa que os novos números de série são atribuídos automaticamente a esse perfil predefinido quando sincronizar novos números de série com o serviço da Apple. Quando o seu inquilino for migrado para o novo portal do Azure num futuro próximo, deixará de poder predefinir um perfil e de ter números de série atribuídos automaticamente a esse perfil. Em alternativa, terá de atribuir números de série a um perfil. [Saiba mais](https://docs.microsoft.com/intune/device-enrollment-program-enroll-ios)

### <a name="export-a-profile-to-deploy-to-ios-devices"></a>Exportar um perfil a implementar nos dispositivos iOS

1. Na [consola de administração do Microsoft Intune](https://manage.microsoft.com) aceda a **Policy** &gt; **Corporate Device Enrollment**e, em seguida, selecione o perfil de dispositivo a implementar nos dispositivos móveis.

2. Selecione **Export** na barra de tarefas. Copie e guarde o **URL do Perfil**. Irá carregá-lo no Apple Configurator mais tarde para definir o perfil do Intune utilizado pelos dispositivos iOS.

   No procedimento seguinte, deverá carregar o URL deste perfil no serviço da Apple com o Apple Configurator para definir o perfil do Intune utilizado pelos dispositivos iOS.

### <a name="prepare-the-device-with-apple-configurator"></a>Preparar o dispositivo com o Apple Configurator

Os dispositivos iOS são ligados ao computador Mac e inscritos na gestão de dispositivos móveis.

1.  Num computador Mac, abra o **Apple Configurator 2**. Na barra de menus, selecione **Apple Configurator 2** e selecione **Preferências**.

   > [!WARNING]
   > Os dispositivos serão repostos para as configurações de fábrica durante o processo de inscrição. Como melhor prática, reponha o dispositivo e ligue-o. Os dispositivos deverão aparecer no ecrã **Hello** quando liga o dispositivo.

2. No painel de preferências, selecione **Servidores** e selecione o símbolo de adição (+) para iniciar o assistente do Servidor MDM. Selecione **Next**.

3. Introduza o **Nome do anfitrião ou URL** e o **URL de inscrição** do servidor MDM em Inscrição do Assistente de Configuração para dispositivos iOS com Microsoft Intune. Para o URL de Inscrição, introduza o URL do perfil de inscrição exportado do Intune. Selecione **Next**.  

   Pode ignorar o aviso "URL do servidor não verificado" em segurança. Para continuar, selecione **Seguinte** até que o assistente esteja concluído.

4.  Ligue os dispositivos móveis iOS ao computador Mac com um adaptador USB.

    > [!WARNING]
    > Os dispositivos serão repostos para as configurações de fábrica durante o processo de inscrição. Como melhor prática, reponha o dispositivo e ligue-o. Os dispositivos deverão aparecer no ecrã **Hello** quando inicia o Assistente de Configuração.

5.  Selecione **Preparar**. No painel Preparar o Dispositivo iOS, selecione **Manual** e, em seguida, selecione **Seguinte**.

6. No painel Inscrever no Servidor MDM, selecione o nome do servidor que criou e selecione **Seguinte**.

7. No painel Supervisionar Dispositivos, selecione o nível de supervisão e, em seguida, selecione **Seguinte**.

8. No painel Criar uma Organização, selecione a **Organização** ou crie uma nova organização e, em seguida, selecione **Seguinte**.

9. No painel Configurar Assistente de Configuração iOS, selecione os passos a serem apresentados ao utilizador e, em seguida, selecione **Preparar**. Se lhe for pedido, autentique para atualizar as definições de fidedignidade.  

10. Quando concluir a preparação do dispositivo iOS, desligue o cabo USB.  

### <a name="distribute-devices"></a>Distribuir dispositivos

Os dispositivos estão agora prontos para a inscrição na empresa. Desligue os dispositivos e distribua-os pelos utilizadores. Quando os utilizadores ligarem os seus dispositivos, o Assistente de Configuração será iniciado.



### <a name="see-also"></a>Consulte também
[Pré-requisitos para inscrever dispositivos](prerequisites-for-enrollment.md)
