---
title: Definir a autoridade de gestão de dispositivos móveis
titlesuffix: Microsoft Intune
description: Definir a autoridade de gestão de dispositivos móveis no Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/30/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 8deff871-5dff-4767-9484-647428998d82
ms.reviewer: damionw
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3457a8314136bac864324dc9baa72ca586bdb7a3
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/14/2019
ms.locfileid: "57460908"
---
# <a name="set-the-mobile-device-management-authority"></a>Definir a autoridade de gestão de dispositivos móveis

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

A definição da autoridade de gestão de dispositivos móveis (MDM) determina como gere os seus dispositivos. Como administrador de TI, tem de definir uma autoridade de MDM antes de os utilizadores poderem inscrever dispositivos para gestão.

As configurações possíveis são:

- **Intune Autónomo** – gestão apenas na cloud, que configura através do portal do Azure. Inclui o conjunto completo das funcionalidades que o Intune oferece. [Defina a autoridade de MDM na consola do Intune](#set-mdm-authority-to-intune).

- **Intune Híbrido** – integração da solução cloud do Intune com o System Center Configuration Manager. Configura o Intune com a consola do Configuration Manager. [Defina a autoridade de MDM no Configuration Manager](https://docs.microsoft.com/sccm/mdm/deploy-use/configure-intune-subscription). 

    > [!Important]
    >A inclusão de novos clientes de MDM híbrida será desativada numa versão futura. Para obter mais informações, consulte a [mover da gestão de dispositivos móveis híbrida para o Intune no Azure](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Move-from-Hybrid-Mobile-Device-Management-to-Intune-on-Azure/ba-p/280150) postagem de blog.

- **Gestão de Dispositivos Móveis para o Office 365** – integração do Office 365 com a solução cloud do Intune. Configurar o Intune a partir do seu centro de administração do Microsoft 365. Inclui um subconjunto das funcionalidades que estão disponíveis com o Intune Autónomo. Defina a autoridade MDM no Centro de administração do Microsoft 365.

> [!IMPORTANT]
> No Configuration Manager versão 1610 ou posterior e no Microsoft Intune versão 1705, pode alterar a autoridade MDM sem ter de contactar o Suporte da Microsoft e sem ter de anular a inscrição e inscrever novamente os seus dispositivos geridos existentes. Para obter detalhes, consulte [preparar a alteração da autoridade de MDM para o Configuration Manager](mdm-authority-set.md#prepare-to-change-the-mdm-authority-to-configuration-manager).

## <a name="set-mdm-authority-to-intune"></a>Definir a autoridade de MDM como o Intune

Se ainda não configurou a autoridade de MDM, siga os passos abaixo. Para mudar de uma autoridade de MDM para outra, veja a secção [Alterar a autoridade de MDM](#prepare-to-change-the-mdm-authority-to-configuration-manager) abaixo.

1. Inicie sessão no [Portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços** > **Intune**. O Intune encontra-se na secção **Monitorização + Gestão**.
3. Selecione a faixa cor de laranja para abrir a definição **Autoridade de Gestão de Dispositivos Móveis**. A faixa cor de laranja só é apresentada se ainda não tiver configurado a autoridade de MDM.
4. Em **Autoridade de Gestão de Dispositivos Móveis**, selecione a sua autoridade de MDM a partir das seguintes opções:
   - **Autoridade de MDM do Intune**
   - **Autoridade MDM do Configuration Manager**
   - **Nenhum**

   ![Captura de ecrã do ecrã Definir a autoridade de gestão de dispositivos móveis do Intune](media/set-mdm-auth.png)

   Uma mensagem indica que definiu com êxito a autoridade de MDM como o Intune.

### <a name="workflow-of-intune-administration-ui"></a>Fluxo de trabalho da IU de Administração do Intune
Quando a gestão de dispositivos Android ou Apple está ativada, o Intune envia informações sobre o dispositivo e o utilizador para se integrar com estes serviços de terceiros e gerir os respetivos dispositivos.

Os cenários que acrescentam uma janela de consentimento para partilhar dados são incluídos quando:
- Ativa os perfis de trabalho do Android.
- Ativar e carregar certificados Push de MDM da Apple.
- Ativar qualquer um dos serviços da Apple, tal como o Programa de Registo de Aparelho, o School Manager e o Programa de Compras em Volume.

Em cada caso, o consentimento está estritamente relacionado com a execução de um serviço de gestão de dispositivos móveis. Por exemplo, confirmar que um administrador de TI autorizou a inscrição de dispositivos Google ou Apple. A documentação que aborda as informações que serão partilhadas quando o novo fluxo de trabalho for disponibilizado está disponível nas seguintes localizações:
- [Dados que o Intune envia para a Google](https://aka.ms/Data-intune-sends-to-google)
- [Dados que o Intune envia para a Apple](https://aka.ms/data-intune-sends-to-apple)

## <a name="key-considerations"></a>Considerações-chave
Depois de mudar para a nova autoridade de MDM, provavelmente haverá um tempo de transição (até oito horas) até que o dispositivo faça o registo e sincronize com o serviço. Tem de configurar as definições na nova autoridade de MDM (híbrida) para garantir que os dispositivos inscritos continuam a ser geridos e protegidos depois da alteração. 
- Depois da alteração, os dispositivos têm de se ligar ao serviço para que as definições da nova autoridade de MDM (Intune autónomo) substituam as definições existentes no dispositivo.
- Depois de alterar a autoridade de MDM, algumas definições básicas (como perfis) da autoridade de MDM (Intune autónomo) anterior permanecerão no dispositivo até sete dias ou até que o dispositivo se ligue ao serviço pela primeira vez. Recomendamos que configure as aplicações e definições (políticas, perfis, aplicações, etc.) na nova autoridade de MDM (híbrida) assim que possível e implemente as definições nos grupos de utilizadores que contêm utilizadores com dispositivos inscritos existentes. Assim que um dispositivo se ligar ao serviço após a alteração da autoridade de MDM, irá receber as novas definições da nova autoridade de MDM e impedir lacunas na gestão e proteção.
- Quando existem as mesmas categorias de dispositivo no Intune e no Configuration Manager, as atribuições de categoria de dispositivo para dispositivos não são transferidas depois de mudar para a nova autoridade de MDM. Para continuar a utilizar as categorias de dispositivo, os dispositivos migrados têm de ser adicionados manualmente às coleções adequadas depois de a autoridade de MDM ser alterada e os dispositivos são apresentados na consola do Configuration Manager.
- Os dispositivos que não têm utilizadores associados (normalmente, no Programa de Registo de Aparelho iOS ou em cenários de inscrição em massa) não são migrados para a nova autoridade de MDM. Para mover estes dispositivos para a nova autoridade de MDM, terá de contactar o suporte para obter assistência.

## <a name="prepare-to-change-the-mdm-authority-to-configuration-manager"></a>Preparar para mudar a autoridade de MDM para o Configuration Manager

Reveja as seguintes informações para preparar a alteração para a autoridade de MDM:
- Tem de ter o Configuration Manager versão 1610 ou superior para ter a opção de alterar a autoridade de MDM.
- Depois de mudar para a nova autoridade de MDM, o dispositivo poderá demorar até oito horas a ligar ao serviço.
- Crie uma coleção de utilizadores do Configuration Manager com todos os utilizadores atualmente geridos pelo Intune autónomo que irá utilizar quando configurar a subscrição do Intune na consola do Configuration Manager. Esta coleção ajuda a garantir que o utilizador e os dispositivos terão uma licença do Configuration Manager atribuída e serão geridos no ambiente híbrido, após a alteração para a autoridade de MDM.
- Certifique-se de que o Administrador de TI também está nesta coleção.  
- Antes da alteração, a Autoridade de MDM será apresentada como **Definida como o Microsoft Intune** (autónomo) na consola de administração do Intune.
- A autoridade de MDM deverá apresentar **Definida como o Microsoft Intune** (inquilino autónomo) na consola de administração do Microsoft Intune antes da alteração da autoridade de MDM.
    > [!NOTE]    
    > Se a sua autoridade de MDM apresentar **Gerida pelo Intune e Office 365**, os seus dispositivos MDM geridos pelo Office 365 deixarão de ser geridos quando alterar a sua autoridade de MDM para o **Configuration Manager** (híbrido). Recomendamos que atribua a esses utilizadores licenças do Intune ou do Enterprise Mobility Suite antes de alterar a autoridade de MDM.   

- Na [consola de administração do Microsoft Intune](http://manage.microsoft.com), remova a função Gestor de Inscrições de dispositivos. Para obter detalhes, veja [Eliminar um gestor de inscrição de dispositivos do Intune](device-enrollment-manager-enroll.md#remove-device-enrollment-manager-permissions).
- Desative todos os mapeamentos de grupo de dispositivos configurados. Para obter detalhes, veja [Categorizar os dispositivos com o mapeamento de grupo de dispositivos no Microsoft Intune](device-group-mapping.md).
- Os utilizadores finais não deverão sentir impactos evidentes durante a alteração da autoridade de MDM. No entanto, aconselhamos que informe os utilizadores desta alteração para garantir que os respetivos dispositivos estão ligados e que se ligam ao serviço logo após a alteração. Esta precaução garante que liga e regista no serviço o máximo de dispositivos através da nova autoridade o mais rapidamente possível.
- Se estiver a utilizar o Intune autónomo para gerir dispositivos iOS antes da alteração da autoridade de MDM, terá de garantir que renova e utiliza o mesmo certificado de serviço Apple Push Notification (APNs) utilizado anteriormente no Intune para voltar a configurar o inquilino no Configuration Manager (híbrido).    

    > [!IMPORTANT]  
    > Se for utilizado um certificado do APNs para um inquilino híbrido, TODOS os dispositivos iOS inscritos anteriormente deixarão de estar inscritos, pelo que terá de realizar o processo para voltar a inscrevê-los. Antes de efetuar a alteração da autoridade de MDM, certifique-se de que sabe exatamente qual o certificado do APNs que utilizou para gerir os dispositivos iOS no Intune. Encontre o mesmo certificado listado no Portal Apple Push Certificates (https://identity.apple.com)) e certifique-se de que o utilizador cujo ID Apple foi utilizado para criar o certificado do APNs original é identificado e está disponível para renovar o mesmo certificado do APNs como parte da alteração para a nova autoridade de MDM.

## <a name="change-the-mdm-authority-to-configuration-manager"></a>Alterar a autoridade de MDM para o Configuration Manager

1. Na consola do Configuration Manager, aceda a **Administração** &gt;  **Descrição geral** &gt; **Serviços Cloud** &gt; **Subscrição do Microsoft Intune** e selecione para adicionar uma subscrição do Intune.
2. Inicie sessão no inquilino do Intune que utilizou originalmente quando definiu a autoridade de MDM no Intune e clique em **Seguinte**.
3. Selecione **Alterar a minha autoridade de MDM para o Configuration Manager** e clique em **Seguinte**.
4. Selecione a coleção de utilizadores que contém todos os utilizadores que continuam a ser geridos pela nova autoridade de MDM híbrida.
5. Clique em **seguinte** e conclua o assistente. A autoridade de MDM é agora alterada para o **Configuration Manager**.
6. Inicie sessão na [consola de administração do Microsoft Intune](http://manage.microsoft.com) com o mesmo inquilino do Intune e confirme que a autoridade de MDM foi alterada para **Definir para o Configuration Manager**.
7. Após mudar a autoridade de MDM para o Configuration Manager, pode configurar a [inscrição de dispositivos iOS](https://docs.microsoft.com/sccm/mdm/deploy-use/enroll-hybrid-ios-mac) e [inscrição de dispositivos Android](https://docs.microsoft.com/sccm/mdm/deploy-use/enroll-hybrid-android).
8. Na consola do Configuration Manager, configure e implemente as novas definições e aplicações da nova autoridade de MDM (híbrida).

Da próxima vez que os dispositivos se ligarem ao serviço, as novas definições serão recebidas e sincronizadas a partir da nova autoridade de MDM.

## <a name="change-mdm-authority-to-office-365"></a>Mudar a autoridade de MDM para o Office 365

Para ativar a MDM do Office 365 para além do seu Serviço do Intune existente, aceda a [https://protection.office.com](https://protection.office.com), selecione **Prevenção Contra Perda de Dados** > **Políticas de Segurança de Dispositivos** > **Ver lista de Dispositivos Geridos** > **Vamos começar**.

Para obter mais informações, veja [Set up Mobile Device Management (MDM) in Office 365](https://support.office.com/en-us/article/Set-up-Mobile-Device-Management-MDM-in-Office-365-dd892318-bc44-4eb1-af00-9db5430be3cd) (Configurar a Gestão de Dispositivos Móveis [MDM] no Office 365).

Se quiser que os utilizadores finais sejam geridos apenas pela MDM do Office 365, remova todas as licenças do Intune e/ou Enterprise Mobility + Security atribuídas após ativar a MDM do Office 365.

## <a name="mobile-device-cleanup-after-mdm-certificate-expiration"></a>Limpeza de dispositivos móveis após a expiração do certificado MDM

O certificado MDM é renovado automaticamente quando os dispositivos móveis estão a comunicar com o serviço do Intune. Se os dispositivos móveis forem eliminados ou não conseguirem comunicar com o serviço do Intune durante um determinado período de tempo, o certificado MDM não será renovado. O dispositivo é removido do portal do Azure 180 dias depois da expiração do certificado MDM.

## <a name="remove-mdm-authority"></a>Remover a autoridade de MDM

A autoridade de MDM não pode ser novamente alterada para Desconhecida. A autoridade de MDM é utilizada pelos servidores da Microsoft para determinar com que portal os dispositivos inscritos comunicam (ConfigMGR, Azure Intune, MDM do Office 365).

## <a name="what-to-expect-after-changing-the-mdm-authority"></a>O que esperar depois de alterar a autoridade de MDM

- Quando o serviço do Intune deteta a alteração da autoridade de MDM de um inquilino, envia uma mensagem de notificação para todos os dispositivos inscritos se registarem e sincronizarem com o serviço (esta notificação não está incluída no registo agendado com regularidade). Portanto, depois de a autoridade de MDM do inquilino ser alterada do Intune autónomo para híbrido, todos os dispositivos ligados e online serão ligados ao serviço, receberão a nova autoridade de MDM e serão geridos de forma híbrida. A gestão e proteção destes dispositivos é contínua.
- Mesmo nos dispositivos ligados e online durante (ou pouco depois) a alteração da autoridade de MDM, irá ocorrer um atraso de até oito horas (consoante a hora do próximo registo regular agendado) até que os dispositivos sejam registados com o serviço da nova autoridade de MDM.    

  > [!IMPORTANT]    
  > Entre o momento em que altera a autoridade de MDM e o momento em que o certificado do APNs renovado é carregado para a nova autoridade, as novas inscrições e registos de dispositivos iOS falham. Como tal, é importante que reveja e carregue o certificado do APNs para a nova autoridade o mais rapidamente possível após a alteração da autoridade de MDM.

- Os utilizadores podem mudar rapidamente para a nova autoridade de MDM ao iniciar manualmente um registo do dispositivo no serviço. Os utilizadores podem fazer facilmente esta alteração através da aplicação Portal da Empresa e ao iniciar uma verificação da conformidade do dispositivo.
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

## <a name="next-steps"></a>Passos Seguintes

Com a autoridade de MDM definida, pode começar a [inscrever dispositivos](device-enrollment.md).
