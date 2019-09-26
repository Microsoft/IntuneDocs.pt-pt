---
title: Criar política de acesso condicional do Exchange
titleSuffix: Microsoft Intune
description: Configure o acesso condicional para o Exchange local e o Exchange Online dedicado herdado no Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 09/19/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 127dafcb-3f30-4745-a561-f62c9f095907
ms.reviewer: stama
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0b53f3dc338f543468984df362b22f6b88ee5c53
ms.sourcegitcommit: 1494ff4b33c13a87f20e0f3315da79a3567db96e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/20/2019
ms.locfileid: "71304054"
---
# <a name="create-a-conditional-access-policy-for-exchange-on-premises-and-legacy-exchange-online-dedicated"></a>Criar uma política de acesso condicional para o Exchange local e o Exchange Online dedicado herdado

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Este artigo mostra como configurar o acesso condicional para o Exchange local com base na conformidade do dispositivo.

Se tiver um ambiente do Exchange Online Dedicado e precisar de saber se está na configuração nova ou legada, contacte o seu gestor de conta. Para controlar o acesso de email ao Exchange local ou ao seu ambiente herdado do Exchange Online dedicado, configure o acesso condicional para o Exchange local no Intune.

## <a name="before-you-begin"></a>Antes de começar

Para poder configurar o acesso condicional, verifique se as seguintes configurações existem:

- Sua versão do Exchange é **exchange 2010 SP1 ou posterior**. Matriz de Servidor de Acesso de Cliente (CAS) do Exchange Server é suportada.

- Você instalou e usa o [Exchange Active Sync Exchange Connector local](exchange-connector-install.md), que conecta o Intune ao Exchange local.

    >[!IMPORTANT]  
    >O Intune suporta múltiplos Exchange Connectors no local por subscrição.  No entanto, cada Exchange Connector local é específico a um único locatário do Intune e não pode ser usado com nenhum outro locatário.  Se tiver mais do que uma organização do Exchange no local, pode configurar um conector separado para cada organização do Exchange.

- O conector para uma organização do Exchange local pode ser instalado em qualquer máquina, desde que o computador possa se comunicar com o Exchange Server.

- Este conector suporta o **ambiente do Exchange CAS**. O Intune dá suporte à instalação do conector no servidor CAS do Exchange diretamente, mas é recomendável instalá-lo em um computador separado devido à carga adicional que o conector coloca no servidor. Quando configurar o conector, tem de configurá-lo para comunicar com um dos servidores do Exchange CAS.

- O **Exchange ActiveSync** tem de ser configurado com a autenticação baseada em certificado ou com a entrada de credenciais de utilizador.

- Quando as políticas de acesso condicional são configuradas e direcionadas a um usuário, antes que um usuário possa se conectar ao seu email, o **dispositivo** que ele usa deve ser:
  - **Inscrito** no Intune ou ser um PC associado a um domínio.
  - **Registado no Azure Active Directory**. Além disso, o ID do Exchange ActiveSync do cliente tem de ser registado no Azure Active Directory.

- O Serviço de Registo de Dispositivos do Azure AD (DRS) é automaticamente ativado para os clientes do Intune e do Office 365. Os clientes que já implantaram o serviço de registro de dispositivo do ADFS não veem os dispositivos registrados em seus Active Directory locais. **Isto não é aplicável a PC com Windows ou a dispositivos Windows Phone**.

- **Conforme** com todas as políticas de conformidade implementadas nesse dispositivo.

- Se o dispositivo não atender às configurações de acesso condicional, o usuário receberá uma das seguintes mensagens de erro ao entrar:
  - Se o dispositivo não estiver registrado no Intune, ou não estiver registrada no Azure Active Directory, uma mensagem será exibida com instruções sobre como instalar o aplicativo Portal da Empresa, registrar o dispositivo e ativar o email. Este processo também associa o ID do Exchange ActiveSync do dispositivo ao registo do dispositivo no Azure Active Directory.
  - Se o dispositivo não estiver em conformidade, será exibida uma mensagem que direciona o usuário para o site Portal da Empresa do Intune ou o aplicativo Portal da Empresa em que ele pode encontrar informações sobre o problema e como corrigi-lo.

### <a name="support-for-mobile-devices"></a>Suporte para dispositivos móveis

- Windows Phone 8.1 e posterior
- Aplicação de e-mail nativa no iOS.
- Clientes de correio EAS, como o Gmail para Android 4 ou posterior.
- **Dispositivos de perfil de trabalho do Android** para clientes de email do EAS: Somente o **gmail** e o **nove funcionam para Android Enterprise** no **perfil de trabalho** têm suporte em dispositivos de perfil de trabalho do Android. Para que o acesso condicional funcione com perfis de trabalho do Android, você deve implantar um perfil de email para o Gmail ou nove trabalho para o aplicativo Android Enterprise e também implantar esses aplicativos como uma instalação necessária.

> [!NOTE]
> Não há suporte para o Microsoft Outlook para Android e iOS por meio do Exchange local Connector. Se você quiser aproveitar Azure Active Directory políticas de acesso condicional e Proteção de Aplicativo do Intune políticas com o Outlook para iOS e Android para suas caixas de correio locais, consulte [usando a autenticação moderna híbrida com o Outlook para IOS e Android](https://docs.microsoft.com/Exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth) . 

### <a name="support-for-pcs"></a>Suporte de PCs

O aplicativo de **email** nativo no Windows 8.1 e posterior (quando registrado no MDM com o Intune)

## <a name="configure-exchange-on-premises-access"></a>Configurar o acesso ao Exchange no local

Antes de poder usar o procedimento a seguir para configurar o controle de acesso local do Exchange, você deve instalar e configurar pelo menos um [Exchange Connector local do Intune](exchange-connector-install.md) para o Exchange local.

1. Entrar no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)

2. Acesse **acesso do Exchange**e, em seguida, selecione **Exchange local Access**. 

3. No painel **acesso local do Exchange** , escolha **Sim** para habilitar o *controle de acesso local do Exchange*.

4. Em **atribuição**, escolha **Selecionar grupos para incluir**e, em seguida, selecione um ou mais grupos para configurar o acesso. 

   Os membros dos grupos selecionados têm a política de acesso condicional para o acesso local do Exchange aplicado a eles. Os usuários que recebem essa política devem registrar seus dispositivos no Intune e estar em conformidade com os perfis de conformidade antes que possam acessar o Exchange no local.

5. Para excluir grupos, escolha **Selecionar grupos a serem excluídos**e, em seguida, selecione um ou mais grupos isentos de requisitos para registrar dispositivos e estar em conformidade com os perfis de conformidade antes de acessar o Exchange no local. 

6. Em seguida, defina as configurações para o Exchange Connector local do Intune.  Em **instalação** no **painel acesso do Exchange**, selecione **conector local do Exchange ActiveSync** e, em seguida, selecione o conector para a organização do Exchange que você deseja configurar.

7. Em **configurações**, escolha **notificações de usuário** para modificar a mensagem de email padrão que é enviada aos usuários se seu dispositivo não estiver em conformidade e se quiser acessar o Exchange no local. O modelo de mensagem utiliza Linguagem de markup.  Também pode ver a pré-visualização do aspeto da mensagem à medida que escreve.
   > [!TIP]
   > Para saber mais sobre a Linguagem de markup, veja este [artigo](https://en.wikipedia.org/wiki/Markup_language) da Wikipédia.
 
   Selecione **OK** para salvar suas edições para concluir a configuração do acesso local do Exchange.

8. Em seguida, selecione **Configurações avançadas de acesso de Exchange Active Sync** para abrir o painel *Configurações avançadas de acesso do Exchange ActiveSync* , em que você configura as regras de acesso do dispositivo:  

   - Para **acesso a dispositivo não gerenciado**, defina a regra padrão global para acesso de dispositivos que não são afetados pelo acesso condicional ou outras regras:

     - **Permitir acesso** – todos os dispositivos podem acessar o Exchange no local imediatamente. Os dispositivos que pertencem aos usuários nos grupos configurados como incluídos no procedimento anterior serão bloqueados se forem avaliados posteriormente como não compatíveis com as políticas compatíveis ou não registrados no Intune.

     - **Bloquear o acesso** e a **quarentena** – todos os dispositivos são imediatamente impedidos de acessar o Exchange no local inicialmente. Os dispositivos que pertencem aos usuários nos grupos configurados como incluídos no procedimento anterior obtêm acesso após o registro do dispositivo no Intune e são avaliados como compatíveis. 

       Dispositivos Android que *não* executam o Samsung Knox Standard não dão suporte a essa configuração e estão sempre bloqueados.

   -  Para **exceções de plataforma de dispositivo**, selecione **Adicionar**e, em seguida, especifique os detalhes da plataforma conforme necessário para seu ambiente. 
   
      Se a configuração de **acesso do dispositivo não gerenciado** estiver definida como **bloqueada**, os dispositivos registrados e compatíveis serão permitidos mesmo se houver uma exceção de plataforma para bloqueá-los.  
   
   Selecione **OK** para salvar suas edições.

9. Selecione **salvar** para salvar a política de acesso condicional do Exchange.

Em seguida, crie uma política de conformidade e atribua-a aos usuários do Intune para avaliar seus dispositivos móveis, consulte [introdução à conformidade do dispositivo](device-compliance-get-started.md).

## <a name="see-also"></a>Consulte também

[Solucionando problemas do Exchange Connector local do Intune no Microsoft Intune](https://support.microsoft.com/help/4471887)
