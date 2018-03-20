---
title: "Criar uma política de acesso condicional do Exchange"
titlesuffix: Microsoft Intune
description: Configure o acesso condicional no Exchange no local e no Exchange Online Dedicado legado no Intune.
keywords: 
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 127dafcb-3f30-4745-a561-f62c9f095907
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 4cfe5916668de6d8bb3c42f2fd6afb6221bbc07e
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/08/2018
---
# <a name="create-a-conditional-access-policy-for-exchange-on-premises-and-legacy-exchange-online-dedicated"></a>Criar uma política de acesso condicional no Exchange no local e no Exchange Online Dedicado legado

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Este artigo mostra-lhe como configurar o acesso condicional do Exchange no local com base na conformidade do dispositivo.

Se tiver um ambiente do Exchange Online Dedicado e precisar de saber se está na configuração nova ou legada, contacte o seu gestor de conta. Para controlar o acesso ao e-mail no Exchange no local ou no ambiente do Exchange Online Dedicado legado, configure o acesso condicional para o Exchange no local no Intune.

## <a name="before-you-begin"></a>Antes de começar

Para poder configurar o acesso condicional, verifique o seguinte:

- A sua versão do Exchange tem de ser o **Exchange 2010 SP1 ou posterior**. Matriz de Servidor de Acesso de Cliente (CAS) do Exchange Server é suportada.

- Tem de utilizar o [Exchange Connector do Exchange Active Sync no local](exchange-connector-install.md), que liga o Intune ao Exchange no local.

    >[!IMPORTANT]
    >O conector do Exchange no local é específico do seu inquilino do Intune e não pode ser utilizado com nenhum outro inquilino. Deve também assegurar que o conector do Exchange do seu inquilino está instalado **em apenas um computador**.

- O conector pode ser instalado em qualquer máquina, desde que a máquina possa comunicar com o servidor do Exchange.

- Este conector suporta o **ambiente do Exchange CAS**. Pode instalar tecnicamente o conector no servidor do Exchange CAS diretamente se quiser, mas não é recomendável, uma vez que aumenta a carga no servidor. Quando configurar o conector, tem de configurá-lo para comunicar com um dos servidores do Exchange CAS.

- O **Exchange ActiveSync** tem de ser configurado com a autenticação baseada em certificado ou com a entrada de credenciais de utilizador.

- Quando as políticas de acesso condicional são configuradas e direcionadas para um utilizador, antes de um utilizador poder ligar ao respetivo e-mail, o **dispositivo** que utiliza tem de ser:
    - **Inscrito** no Intune ou ser um PC associado a um domínio.
    - **Registado no Azure Active Directory**. Além disso, o ID do Exchange ActiveSync do cliente tem de ser registado no Azure Active Directory.
<br></br>
- O AAD DRS será automaticamente ativado para os clientes do Intune e do Office 365. Os clientes que já implementaram o Serviço de Registos de Dispositivos do ADFS não verão dispositivos registados no respetivo Active Directory no local. **Isto não é aplicável a PC com Windows ou a dispositivos Windows Phone**.

- **Conforme** com todas as políticas de conformidade implementadas nesse dispositivo.

- Se o dispositivo não estiver em conformidade com as definições de acesso condicional, será apresentada ao utilizador uma das mensagens seguintes quando iniciar sessão:
    - Se o dispositivo não estiver inscrito no Intune ou não estiver registado no Azure Active Directory, será apresentada uma mensagem com instruções sobre como instalar a aplicação Portal da Empresa, como inscrever o dispositivo e como ativar o e-mail. Este processo também associa o ID do Exchange ActiveSync do dispositivo ao registo do dispositivo no Azure Active Directory.
    - Se o dispositivo não estiver em conformidade, será apresentada uma mensagem que direciona o utilizador para o site do Portal da Empresa do Intune ou para a aplicação Portal da Empresa, onde pode obter informações sobre o problema e como resolvê-lo.

### <a name="support-for-mobile-devices"></a>Suporte para dispositivos móveis

- Windows Phone 8.1 e posterior
- Aplicação de e-mail nativa no iOS.
- Clientes de correio EAS, como o Gmail para Android 4 ou posterior.
- Clientes de correio EAS em **dispositivos Android for Work:** apenas as aplicações **Gmail** e **Nine Work** são suportadas no **perfil de trabalho** em dispositivos Android for Work. Para obter acesso condicional ao seu trabalho com o Android for Work, tem de implementar um perfil de e-mail para a aplicação Gmail ou Nine Work, bem como implementar essas aplicações como uma instalação obrigatória.

> [!NOTE]
> A aplicação Microsoft Outlook não é suportada no Android e iOS. 

### <a name="support-for-pcs"></a>Suporte de PCs

A aplicação **Correio** nativa no Windows 8.1 e posterior (quando inscrita através do Intune)


## <a name="configure-exchange-on-premises-access"></a>Configurar o acesso ao Exchange no local

1. Aceda ao [portal do Azure](https://portal.azure.com/) e inicie sessão com as credenciais do Intune.

1. Depois de iniciar sessão com êxito, verá o **Dashboard do Azure**.

1. Selecione **Todos os serviços** no menu à esquerda e, em seguida, escreva **Intune** no filtro da caixa de texto.

1. Escolha **Intune**, será apresentado o **Dashboard do Intune**.

1. Selecione **Acesso no local**. O painel **Acesso no local** mostra o estado da política de acesso condicional e os dispositivos que são afetados pelo mesma.

1. Em **Gerir**, escolha **Acesso no local ao Exchange**.

1. No painel **Acesso no local ao Exchange**, selecione **Sim** para ativar o controlo de acesso no local ao Exchange.

    > [!NOTE]
    > Se não tiver configurado o conector do Exchange Active Sync no local, esta opção estará desativada.  Primeiro tem de instalar e configurar este conector antes de ativar o acesso condicional do Exchange no local. Para obter mais detalhes, veja [Instalar o Exchange Connector no Local do Intune](exchange-connector-install.md)

1. Em **Atribuição**, selecione **Grupos Incluídos**.  Utilize o grupo de utilizadores de segurança ao qual deve ser aplicado o acesso condicional. Esta ação requer que os utilizadores inscrevam os dispositivos no Intune e que estejam em conformidade com os perfis de conformidade.

1. Se quiser excluir um determinado grupo de utilizadores, poderá fazê-lo ao escolher **Grupos Excluídos** e selecionar um grupo de utilizadores que pretende que fique isento da obrigatoriedade de inscrição e conformidade dos dispositivos.

1. Em **Definições**, escolha **Notificações do utilizador** para modificar a mensagem de e-mail predefinida. Esta mensagem será enviada aos utilizadores se eles quiserem aceder ao Exchange no local, mas o dispositivo deles não estiver em conformidade. O modelo de mensagem utiliza Linguagem de markup.  Também pode ver a pré-visualização do aspeto da mensagem à medida que escreve.
    > [!TIP]
    > Para saber mais sobre a Linguagem de markup, veja este [artigo](https://en.wikipedia.org/wiki/Markup_language) da Wikipédia.

1. No painel **Definições avançadas de acesso do Exchange Active Sync**, predefina a regra global para o acesso a partir dos dispositivos que não são geridos pelo Intune e para as regras de nível da plataforma, tal como é descrito nos dois passos que se seguem.

1. Em dispositivos que não são afetados pelo acesso condicional ou outras regras, pode optar por permitir que acedam ao Exchange ou bloqueá-lo.

   - Quando definir esta opção para permitir o acesso, todos os dispositivos poderão aceder ao Exchange no local imediatamente.  Os dispositivos que pertencem aos utilizadores nos **Grupos Incluídos** serão bloqueados se forem subsequentemente avaliados como não conformes com as políticas de conformidade ou não estiverem inscritos no Intune.
   - Quando definir esta opção para bloquear o acesso, todos os dispositivos serão imediatamente impedidos de aceder ao Exchange no local inicialmente.  Os dispositivos que pertencem aos utilizadores nos **Grupos Incluídos** obterão acesso assim que o dispositivo for inscrito no Intune e avaliado como estando em conformidade. Os dispositivos Android que não executem o Samsung Knox Standard estarão sempre bloqueados, porque não suportam esta definição.

1. Em **Exceções da plataforma do dispositivo**, selecione **Adicionar** para especificar as plataformas. Se a definição **acesso de dispositivo não gerido** estiver configurada como **bloqueado**, os dispositivos que estão inscritos e em conformidade terão permissão, mesmo que exista uma exceção de plataforma para bloquear. Selecione **OK** para guardar as definições.

1. No painel **No local**, clique em **Guardar** para guardar a política de acesso condicional.

## <a name="create-azure-ad-conditional-access-policies-in-intune"></a>Criar políticas de Acesso condicional do Azure AD no Intune

A partir da versão 1704 do Intune, os administradores podem criar políticas de acesso condicional do Azure AD a partir do Intune no portal do Azure, pelo que não precisa de alternar entre as cargas de trabalho do Azure e do Intune.

> [!IMPORTANT]
> Tem de ter uma licença do Azure AD Premium para criar políticas de acesso condicional do Azure AD a partir do Intune no portal do Azure.

### <a name="to-create-azure-ad-conditional-access-policy"></a>Para criar uma política de acesso condicional do Azure AD

1. No **Dashboard do Intune**, escolha **Acesso condicional**.

2. No painel **Políticas**, selecione **Nova política** para criar a sua nova política de acesso condicional do Azure AD.

## <a name="see-also"></a>Consulte também

[Acesso Condicional no Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access)
