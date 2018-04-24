---
title: Alterar a sua autoridade de MDM para o Configuration Manager (MDM híbrida)
description: Saiba como alterar a autoridade de MDM do Intune autónomo para o Configuration Manager (MDM híbrida).
keywords: ''
author: dougeby
manager: dougeby
ms.date: 10/04/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f1b4bce3-7932-4a0d-aa92-6dacc7060f42
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: dc73befb46f1f159d9a8c023bb5604517b9f73f4
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/16/2018
---
# <a name="change-the-mdm-authority"></a>Alterar a autoridade de MDM
A partir da versão 1610 do Configuration Manager pode alterar a sua autoridade de MDM sem ter de contactar o Suporte da Microsoft e sem ter de anular a inscrição e inscrever novamente os seus dispositivos geridos existentes. Este tópico fornece os passos para alterar um inquilino existente do Microsoft Intune configurado no Intune e com a autoridade de MDM definida como **Microsoft Intune** (autónomo) para o **Configuration Manager** (MDM híbrida) sem que seja necessário anular a inscrição e reinscrever dispositivos geridos existentes.

> [!Note]    
> Se quiser alterar um inquilino existente do Microsoft Intune configurado na consola do Configuration Manager (híbrido) e com a autoridade de MDM definida como **Configuration Manager** (híbrido) para o **Microsoft Intune** (autónomo), veja [Alterar a autoridade de MDM no Configuration Manager (MDM híbrida) para o Intune autónomo](https://docs.microsoft.com/sccm/mdm/deploy-use/change-mdm-authority). 


## <a name="key-considerations"></a>Considerações-chave
Depois de mudar para a nova autoridade de MDM, provavelmente haverá um tempo de transição (até oito horas) até que o dispositivo faça o registo e sincronize com o serviço. Tem de configurar as definições na nova autoridade de MDM (híbrida) para garantir que os dispositivos inscritos continuam a ser geridos e protegidos depois da alteração. 
- Depois da alteração, os dispositivos têm de se ligar ao serviço para que as definições da nova autoridade de MDM (Intune autónomo) substituam as definições existentes no dispositivo.
- Depois de alterar a autoridade de MDM, algumas definições básicas (como perfis) da autoridade de MDM (Intune autónomo) anterior permanecerão no dispositivo até sete dias ou até que o dispositivo se ligue ao serviço pela primeira vez. Recomendamos que configure as aplicações e definições (políticas, perfis, aplicações, etc.) na nova autoridade de MDM (híbrida) assim que possível e implemente as definições nos grupos de utilizadores que contêm utilizadores com dispositivos inscritos existentes. Assim que um dispositivo se ligar ao serviço após a alteração da autoridade de MDM, irá receber as novas definições da nova autoridade de MDM e impedir lacunas na gestão e proteção.
- Quando existem as mesmas categorias de dispositivo no Intune e no Configuration Manager, as atribuições de categoria de dispositivo para dispositivos não são transferidas depois de mudar para a nova autoridade de MDM. Para continuar a utilizar as categorias de dispositivo, os dispositivos migrados têm de ser adicionados manualmente às coleções adequadas depois de a autoridade de MDM ser alterada e os dispositivos são apresentados na consola do Configuration Manager.
- Os dispositivos que não têm utilizadores associados (normalmente, no Programa de Registo de Aparelho iOS ou em cenários de inscrição em massa) não são migrados para a nova autoridade de MDM. Para mover estes dispositivos para a nova autoridade de MDM, terá de contactar o suporte para obter assistência.

## <a name="prepare-to-change-the-mdm-authority-to-configuration-manager-hybrid"></a>Preparar a alteração da autoridade de MDM para o Configuration Manager (híbrido)
Reveja as seguintes informações para preparar a alteração para a autoridade de MDM:
- Tem de ter o Configuration Manager versão 1610 ou superior para ter a opção de alterar a autoridade de MDM.
- Depois de mudar para a nova autoridade de MDM, o dispositivo poderá demorar até oito horas a ligar ao serviço.
- Crie uma coleção de utilizadores do Configuration Manager com todos os utilizadores atualmente geridos pelo Intune autónomo que irá utilizar quando configurar a subscrição do Intune na consola do Configuration Manager. Isto ajuda a garantir que o utilizador e os respetivos dispositivos terão uma licença do Configuration Manager atribuída e serão geridos no ambiente híbrido, após a alteração para a autoridade de MDM.
- Certifique-se de que o Administrador de TI também está nesta coleção.  
- Antes da alteração, a Autoridade de MDM será apresentada como **Definida como o Microsoft Intune** (autónomo) na consola de administração do Intune.
- A autoridade de MDM deverá apresentar **Definida como o Microsoft Intune** (inquilino autónomo) na consola de administração do Microsoft Intune antes da alteração da autoridade de MDM.
    > [!NOTE]    
    > Se a sua autoridade de MDM apresentar **Gerida pelo Intune e Office 365**, os seus dispositivos MDM geridos pelo Office 365 deixarão de ser geridos quando alterar a sua autoridade de MDM para o **Configuration Manager** (híbrido). Recomendamos que atribua a esses utilizadores licenças do Intune ou do Enterprise Mobility Suite antes de alterar a autoridade de MDM.   

- Na [consola de administração do Microsoft Intune](http://manage.microsoft.com), remova a função Gestor de Inscrições de dispositivos. Para obter detalhes, veja [Eliminar um gestor de inscrição de dispositivos do Intune](/intune-classic/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune#delete-a-device-enrollment-manager-from-intune).
- Desative todos os mapeamentos de grupo de dispositivos configurados. Para obter detalhes, veja [Categorizar os dispositivos com o mapeamento de grupo de dispositivos no Microsoft Intune](/intune-classic/deploy-use/categorize-devices-with-device-group-mapping-in-microsoft-intune).
- Os utilizadores finais não deverão sentir impactos evidentes durante a alteração da autoridade de MDM. No entanto, aconselhamos que informe os utilizadores desta alteração para garantir que os respetivos dispositivos estão ligados e que se ligam ao serviço logo após a alteração. Isto garante que liga e regista no serviço o máximo de dispositivos através da nova autoridade o mais rapidamente possível.
- Se estiver a utilizar o Intune autónomo para gerir dispositivos iOS antes da alteração da autoridade de MDM, tem de certificar-se de que renova e utiliza o mesmo certificado de serviço Apple Push Notification (APNs) utilizado anteriormente para voltar a configurar o inquilino no Configuration Manager (híbrido).    

    > [!IMPORTANT]  
    > Se for utilizado um certificado do APNs para um inquilino híbrido, TODOS os dispositivos iOS inscritos anteriormente deixarão de estar inscritos, pelo que terá de realizar o processo para voltar a inscrevê-los. Antes de efetuar a alteração da autoridade de MDM, certifique-se de que sabe exatamente qual o certificado do APNs que utilizou para gerir os dispositivos iOS no Intune. Encontre o mesmo certificado listado no Portal Apple Push Certificates (https://identity.apple.com)) e certifique-se de que o utilizador cujo ID Apple foi utilizado para criar o certificado do APNs original é identificado e está disponível para renovar o mesmo certificado do APNs como parte da alteração para a nova autoridade de MDM.  

## <a name="change-the-mdm-authority-to-configuration-manager"></a>Alterar a autoridade de MDM para o Configuration Manager
O processo de alteração da autoridade de MDM para o Configuration Manager (híbrido) inclui os seguintes passos gerais:  
- Na consola do Configuration Manager, adicione a subscrição do Microsoft Intune.
- Configure o certificado do APNs da Apple através do mesmo certificado do APNs que renovou.
- Na consola do Configuration Manager, configure e implemente as novas definições e aplicações da nova autoridade de MDM (híbrida).
- Da próxima vez que os dispositivos se ligarem ao serviço, as novas definições serão recebidas e sincronizadas a partir da nova autoridade de MDM.

#### <a name="to-change-the-mdm-authority-to-configuration-manager"></a>Para alterar a autoridade de MDM para o Configuration Manager
1. Na consola do Configuration Manager, aceda a **Administração** &gt;  **Descrição geral** &gt; **Serviços Cloud** &gt; **Subscrição do Microsoft Intune** e selecione para adicionar uma subscrição do Intune.
2. Inicie sessão no inquilino do Intune que utilizou originalmente quando definiu a autoridade de MDM no Intune e clique em **Seguinte**.
3. Selecione **Alterar a minha autoridade de MDM para o Configuration Manager** e clique em **Seguinte**.
4. Selecione a coleção de utilizadores que contém todos os utilizadores que continuam a ser geridos pela nova autoridade de MDM híbrida.
5. Clique em **Seguinte** e conclua o assistente. A autoridade de MDM é agora alterada para o **Configuration Manager**.
6. Inicie sessão na [consola de administração do Microsoft Intune](http://manage.microsoft.com) com o mesmo inquilino do Intune e confirme que a autoridade de MDM foi alterada para **Definir para o Configuration Manager**.


## <a name="enable-ios-enrollment"></a>Ativar a inscrição iOS
Quando tiver dispositivos iOS, tem de configurar o certificado do APNs no Configuration Manager.

#### <a name="to-enable-ios-enrollment-and-configure-the-apns-certificate"></a>Para ativar a inscrição iOS e configurar o certificado do APNs

1. **Transferir uma solicitação de assinatura de certificado**

   1. Na consola do Configuration Manager, aceda a **Administração** &gt; **Serviços Cloud** &gt; **Subscrições do Microsoft Intune** e selecione **Criar pedido de certificado do APNs** para abrir a caixa de diálogo **Solicitação de Assinatura de Certificado do Serviço Apple Push Notification**.  
   2. **Navegue** para o caminho onde pretende guardar o ficheiro de pedido de assinatura de certificado novo (.csr). Guarde o ficheiro de pedido de assinatura de certificado (.csr) localmente.  
   3. Clique em **Transferir**. O novo ficheiro .csr do Microsoft Intune é transferido e guardado pelo Configuration Manager.   

      > [!IMPORTANT]
      > Tem de transferir uma nova solicitação de assinatura de certificado. Não utilize um ficheiro existente para não ocorrer uma falha.  

2. Aceda ao [Portal Apple Push Certificates](http://go.microsoft.com/fwlink/?LinkId=269844) e inicie sessão com o **mesmo** ID Apple que utilizou anteriormente para criar e renovar o certificado do APNs utilizado no Intune autónomo.

   ![Página de início de sessão do Portal Apple Push Certificates](../media/mdm-change-apns-portal.png)

3. Selecione o certificado do APNs que utilizou no Intune autónomo e, em seguida, clique em **Renovar**.

    ![Caixa de diálogo Renovar APNs](../media/mdm-change-renew-apns.png)

4. Selecione o ficheiro da solicitação de assinatura do certificado (.csr) do APNs que transferiu localmente e, em seguida, clique em **Carregar**.

    ![Página de início de sessão do Portal Apple Push Certificates](../media/mdm-change-renew-apns-upload.png)
 
5. Selecione o mesmo APNs e, em seguida, clique em **Transferir**. Transfira o certificado de APNs (.pem) e guarde o ficheiro localmente.  

    ![Página de início de sessão do Portal Apple Push Certificates](../media/mdm-change-renew-apns-download.png)

6. Carregue o certificado do APNs renovado para o inquilino híbrido através do mesmo ID Apple que utilizou anteriormente.

    1.  Na consola do Configuration Manager, aceda a **Administração** &gt; **Serviços Cloud** &gt; **Subscrição do Microsoft Intune** e selecione **Configurar Plataformas** &gt; **iOS**.  
    2.  Na caixa de diálogo **Propriedade da Subscrição do Microsoft Intune**, selecione o separador **Certificado do APNs** e clique para selecionar a caixa de verificação **Ativar inscrição iOS e Mac OS X (MDM)**.  
    3.  Clique em **Procurar**e aceda ao ficheiro do certificado APNs (.cer) transferido a partir da Apple. O Configuration Manager apresenta as informações do certificado APNs. Clique em **OK** para guardar o certificado APNs no Intune.  

        ![Página de propriedades da Subscrição do Intune – iOS](../media/mdm-change-subscription-properties-ios.png)

## <a name="enable-android-enrollment"></a>Ativar inscrição Android
1. Na consola do Configuration Manager, aceda a **Administração** &gt; **Serviços Cloud** &gt; **Subscrição do Microsoft Intune** e selecione **Configurar Plataformas** &gt; **Android**.  
2. Selecione **Ativar inscrição Android** e clique em **OK**.

### <a name="enable-windows-enrollment"></a>Ativar inscrição Windows
1. Na consola do Configuration Manager, aceda a **Administração** &gt; **Serviços Cloud** &gt; **Subscrição do Microsoft Intune** e selecione **Configurar Plataformas** &gt; **Windows**.  
2. Selecione **Ativar inscrição Windows** e clique em **OK**.

### <a name="enable-windows-phone-enrollment"></a>Ativar inscrição Windows Phone
1. Na consola do Configuration Manager, aceda a **Administração** &gt; **Serviços Cloud** &gt; **Subscrição do Microsoft Intune** e selecione **Configurar Plataformas** &gt; **Windows Phone**.  
2. Selecione a plataforma que pretende ativar e clique em **OK**.


## <a name="next-steps"></a>Próximos passos
Depois de concluir a alteração da autoridade de MDM, reveja os seguintes passos:
- Quando o serviço do Intune deteta a alteração da autoridade de MDM de um inquilino, envia uma mensagem de notificação para todos os dispositivos inscritos se registarem e sincronizarem com o serviço (isto não está incluído no registo agendado com regularidade). Portanto, depois de a autoridade de MDM do inquilino ser alterada do Intune autónomo para híbrido, todos os dispositivos ligados e online serão ligados ao serviço, receberão a nova autoridade de MDM e serão geridos de forma híbrida. A gestão e proteção destes dispositivos é contínua.
- Mesmo nos dispositivos ligados e online durante (ou pouco depois) a alteração da autoridade de MDM, irá ocorrer um atraso de até oito horas (consoante a hora do próximo registo regular agendado) até que os dispositivos sejam registados com o serviço da nova autoridade de MDM.    

  > [!IMPORTANT]    
  > Entre o momento em que altera a autoridade de MDM e o momento em que o certificado do APNs renovado é carregado para a nova autoridade, as novas inscrições e registos de dispositivos iOS falham. Por conseguinte, é importante que reveja e carregue o certificado do APNs para a nova autoridade o mais rapidamente possível após a alteração da autoridade de MDM.

- Os utilizadores podem mudar rapidamente para a nova autoridade de MDM ao iniciar manualmente um registo do dispositivo no serviço. Os utilizadores podem fazê-lo facilmente através da aplicação Portal da Empresa e ao iniciar uma verificação da conformidade do dispositivo.
- Para verificar se está tudo a funcionar corretamente após o registo e sincronização dos dispositivos com o serviço e da alteração da autoridade de MDM, procure os dispositivos na consola do Configuration Manager. Os dispositivos geridos anteriormente pelo Intune são agora apresentados como dispositivos geridos na consola do Configuration Manager.    
- Existe um período provisório em que um dispositivo está offline durante a alteração da autoridade de MDM e em que esse dispositivo é registado no serviço. Para ajudar a garantir que o dispositivo permanece protegido e funcional durante este período provisório, os seguintes perfis permanecem no dispositivo até sete dias (ou até que o serviço seja ligado à nova autoridade de MDM e receba as novas definições que substituirão as existentes):
    - Perfil e-mail
    - Perfil VPN
    - Perfil certificado
    - Perfil Wi-Fi
    - Perfis de configuração
- Depois de mudar para a nova autoridade de MDM, poderá demorar uma semana até que os dados de conformidade sejam corretamente apresentados na consola de administração do Microsoft Intune. No entanto, os estados de conformidade no Azure Active Directory e no dispositivo serão exatos para que o dispositivo permaneça protegido.
- Certifique-se de que as novas definições têm o mesmo nome que as definições antigas para garantir que as mesmas são substituídas. Caso contrário, os dispositivos poderão ficar com políticas e perfis redundantes.    

  > [!TIP]    
  > Como melhor prática, deve criar todas as implementações, configurações e definições de gestão pouco depois de concluir a alteração da autoridade de MDM. Isto ajuda a garantir que os dispositivos estão protegidos e são geridos ativamente durante o período provisório.

-  Depois de alterar a autoridade de MDM, execute os seguintes passos para verificar se os dispositivos foram inscritos com êxito na nova autoridade:   
    - Inscrever um novo dispositivo
    - Certifique-se de que o dispositivo inscrito recentemente é apresentado na consola do Configuration Manager.
    - Execute uma ação para o dispositivo, como o Bloqueio Remoto, a partir da consola de administração. Se tiver êxito, significa que o dispositivo está a ser gerido pela nova autoridade de MDM.
- Se tiver problemas com dispositivos específicos, pode anular a inscrição e inscrever novamente os dispositivos para ligá-los à nova autoridade e geri-los o mais rapidamente possível.