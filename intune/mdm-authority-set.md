---
title: Definir a autoridade de gestão de dispositivos móveis
titleSuffix: Microsoft Intune
description: Definir a autoridade de gestão de dispositivos móveis no Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 8deff871-5dff-4767-9484-647428998d82
ms.reviewer: damionw
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 534c51112345ea9300f3258c2600990896042b64
ms.sourcegitcommit: 6b5907046f920279bbda3ee6c93e98594624c05c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/19/2019
ms.locfileid: "71299177"
---
# <a name="set-the-mobile-device-management-authority"></a>Definir a autoridade de gestão de dispositivos móveis

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

A definição da autoridade de gestão de dispositivos móveis (MDM) determina como gere os seus dispositivos. Como administrador de TI, tem de definir uma autoridade de MDM antes de os utilizadores poderem inscrever dispositivos para gestão.

As configurações possíveis são:

- **Intune Autónomo** – gestão apenas na cloud, que configura através do portal do Azure. Inclui o conjunto completo das funcionalidades que o Intune oferece. [Defina a autoridade de MDM na consola do Intune](#set-mdm-authority-to-intune).

- **Cogestão do Intune** – integração da solução cloud do Intune com o System Center Configuration Manager para os dispositivos Windows 10. Configura o Intune com a consola do Configuration Manager. [Configurar a inscrição automática de dispositivos no Intune](https://docs.microsoft.com/sccm/comanage/tutorial-co-manage-clients#configure-auto-enrollment-of-devices-to-intune). 

    > [!Important]
    >A inclusão de novos clientes da MDM híbrida foi preterida. Para obter mais informações, veja a mensagem de blogue [Move from Hybrid Mobile Device Management to Intune on Azure](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Move-from-Hybrid-Mobile-Device-Management-to-Intune-on-Azure/ba-p/280150) (Mudar da Gestão de Dispositivos Móveis Híbrida para o Intune no Azure).

- **Gestão de Dispositivos Móveis para o Office 365** – integração do Office 365 com a solução cloud do Intune. Deve configurar o Intune no centro de administração do Microsoft 365. Inclui um subconjunto das funcionalidades que estão disponíveis com o Intune Autónomo. Defina a autoridade de MDM no centro de administração do Microsoft 365.

- **Coexistência de MDM do Office 365** Você pode ativar e usar o MDM para Office 365 e o Intune simultaneamente no seu locatário e definir a autoridade de gerenciamento para o Intune ou MDM para o Office 365 para cada usuário para ditar qual serviço será usado para gerenciar seus dispositivos móveis. A autoridade de gerenciamento do usuário é definida com base na licença atribuída ao usuário. Para obter mais informações, consulte [Microsoft Intune coexistência com o MDM para Office 365](https://blogs.technet.microsoft.com/configmgrdogs/2016/01/04/microsoft-intune-co-existence-with-mdm-for-office-365)

## <a name="set-mdm-authority-to-intune"></a>Definir a autoridade de MDM como o Intune

Se ainda não configurou a autoridade de MDM, siga os passos abaixo. Para alterar do SCCM, consulte [migrar usuários e dispositivos do MDM híbrido para o Intune autônomo](https://docs.microsoft.com/sccm/mdm/deploy-use/migrate-hybridmdm-to-intunesa).

1. No [Intune na portal do Azure](https://aka.ms/intuneportal), selecione a faixa laranja para abrir a configuração **autoridade de gerenciamento de dispositivo móvel** . A faixa cor de laranja só é apresentada se ainda não tiver configurado a autoridade de MDM.
2. Em **Autoridade de Gestão de Dispositivos Móveis**, selecione a sua autoridade de MDM a partir das seguintes opções:
   - **Autoridade de MDM do Intune**
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

## <a name="change-mdm-authority-to-office-365"></a>Mudar a autoridade de MDM para o Office 365

Para ativar o MDM do Office 365 (ou para habilitar a coexistência de MDM além do serviço do Intune existente) [https://protection.office.com](https://protection.office.com), vá para, escolha **prevenção** >  de perda de dados**políticas** > **de segurança de dispositivo exibir lista de dispositivos gerenciados** Vamos começar.  > 

Para obter mais informações, veja [Set up Mobile Device Management (MDM) in Office 365](https://support.office.com/en-us/article/Set-up-Mobile-Device-Management-MDM-in-Office-365-dd892318-bc44-4eb1-af00-9db5430be3cd) (Configurar a Gestão de Dispositivos Móveis [MDM] no Office 365).

Se quiser que os utilizadores finais sejam geridos apenas pela MDM do Office 365, remova todas as licenças do Intune e/ou Enterprise Mobility + Security atribuídas após ativar a MDM do Office 365.

## <a name="mobile-device-cleanup-after-mdm-certificate-expiration"></a>Limpeza de dispositivos móveis após a expiração do certificado MDM

O certificado MDM é renovado automaticamente quando os dispositivos móveis estão a comunicar com o serviço do Intune. Se os dispositivos móveis forem eliminados ou não conseguirem comunicar com o serviço do Intune durante um determinado período de tempo, o certificado MDM não será renovado. O dispositivo é removido do portal do Azure 180 dias depois da expiração do certificado MDM.

## <a name="remove-mdm-authority"></a>Remover a autoridade de MDM

A autoridade de MDM não pode ser novamente alterada para Desconhecida. A autoridade de MDM é usada pelo serviço para determinar a quais dispositivos registrados no portal o relatório (Microsoft Intune ou o MDM do Office 365).

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

- Depois de alterar a autoridade de MDM, execute os seguintes passos para verificar se os dispositivos foram inscritos com êxito na nova autoridade:   
  - Inscrever um novo dispositivo
  - Certifique-se de que o dispositivo inscrito recentemente é apresentado na consola do Configuration Manager.
  - Execute uma ação para o dispositivo, como o Bloqueio Remoto, a partir da consola de administração. Se tiver êxito, significa que o dispositivo está a ser gerido pela nova autoridade de MDM.
- Se tiver problemas com dispositivos específicos, pode anular a inscrição e inscrever novamente os dispositivos para ligá-los à nova autoridade e geri-los o mais rapidamente possível.

## <a name="next-steps"></a>Passos Seguintes

Com a autoridade de MDM definida, pode começar a [inscrever dispositivos](device-enrollment.md).
