---
title: Configurar a integração da proteção contra ameaças móveis do com o Intune
titleSuffix: Intune on Azure
description: Como configurar a solução de proteção contra ameaças móveis do enbackupa com Microsoft Intune para controlar o acesso de dispositivos móveis aos seus recursos corporativos.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: f42acb38d84394a6b61fa16072de6320b84a67b5
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72681298"
---
# <a name="integrate-wandera-mobile-threat-protection-with-intune"></a>Integre a proteção contra ameaças móveis do com o Intune  

Conclua as etapas a seguir para integrar a solução de defesa contra ameaças móveis do com o Intune.  

> [!NOTE]
> Este fornecedor de defesa contra ameaças móveis não tem suporte para dispositivos não registrados.

## <a name="before-you-begin"></a>Antes de começar  

Antes de iniciar o processo de integração do com o Intune, verifique se você tem os seguintes pré-requisitos em vigor:
- Subscrição do Microsoft Intune  
- Credenciais de administrador do Azure Active Directory para conceder as seguintes permissões:  
  - Iniciar sessão e ler o perfil de utilizador  
  - Aceder ao diretório como o utilizador com sessão iniciada  
  - Ler dados do diretório  
  - Enviar informações do dispositivo para o Intune  

- Assinatura do:
  - Uma ou mais contas de conexão IN1 que são licenciadas para o EMM Connect  
  - Uma conta com privilégios de superadministrador no  
 
### <a name="wandera-mobile-threat-defense-app-authorization"></a>Autorização do aplicativo de defesa contra ameaças móveis do  

O processo de autorização do aplicativo de defesa contra ameaças móveis do:  
- Permita que o serviço de defesa contra ameaças móveis do to the to Mobile comunique informações relacionadas ao estado de integridade do dispositivo de volta para o Intune.  
- A inscrições sincroniza com a associação do grupo de registros do Azure AD para preencher o banco de dados do dispositivo.  
- Permitir que o portal de administração de RADAR do backit use o SSO (logon único) do Azure AD.  
- Permitir que o aplicativo de defesa contra ameaças móveis do Inscreva-se entre usando o SSO do Azure AD.  


## <a name="set-up-wandera-mobile-threat-defense-integration"></a>Configurar a integração da defesa contra ameaças móveis do  
A instalação do *EMM Connect* para o backr requer um processo de configuração única que você concluiu tanto nos consoles do Intune quanto no inconnecta. O processo de configuração leva cerca de 15 minutos. Você pode concluir a configuração sem coordenação com sua conta técnica do onentrar ou representante de suporte.  

### <a name="enable-support-for-wandera-in-intune"></a>Habilitar o suporte para o no Intune
1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) e vá para **conformidade do dispositivo** > **defesa contra ameaças móveis** > e selecione **Adicionar**.

2. Na página **Adicionar conector** , use a lista suspensa **e selecione o**BackPage. E, em seguida, selecione **criar**.  

3. No painel defesa contra ameaças móveis, selecione o conector **de MTD da** lista de conectores para abrir o painel *Editar conector* . Selecione **abrir o console de administração do** onit para abrir o [radar](https://radar.wandera.com/login), o console de administração do de saída e entre. 

4. No console do backit, acesse **configurações** > **EMM integração**e selecione a guia **EMM Connect** . Use a lista suspensa *fornecedor do EMM* e selecione *Microsoft Intune*.

   ![Selecione Intune](./media/wandera-mtd-connector-integration/set-up-intune-in-radar.png)

5. Selecione **conceder permissões** para abrir uma conexão com o portal do Intune. Entre usando suas credenciais de administrador do Intune, marque a caixa de seleção e **aceite** a solicitação de permissões.  

   ![Aceitar permissões](./media/wandera-mtd-connector-integration/permissions.png) 

6. A conexão completa e retorna para o console de administração de RADAR. Repita o processo para **conceder** acesso a configurações adicionais, conforme necessário.  

   ![Integrações e permissões](./media/wandera-mtd-connector-integration/integrations-and-permissions.png) 

7. No console de RADAR, copie o nome do grupo **SyncOnly** que aparece abaixo do **EMM Label**. Você usará esse nome para configurar um grupo no Intune para sincronização com o.

   ![Grupo de sincronização](./media/wandera-mtd-connector-integration/sync-group-name.png) 

8. Retorne ao console do [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) e edite o conector do MTD. Defina as alternâncias disponíveis como **ativado**e **salve** a configuração.  

   ![Habilitar a vagaa](./media/wandera-mtd-connector-integration/enable-wandera.png) 

O Intune e o agora estão conectados.  

## <a name="configure-the-wandera-applications-and-synchronization-group"></a>Configurar os aplicativos e o grupo de sincronização do  
Para implantar o, você adicionará os aplicativos móveis do backit para as plataformas usadas (Ios e Android) no Intune e os atribuirá a um grupo específico para sincronização; o grupo *SyncOnly* . 

As seções e os procedimentos a seguir guiarão você pelo processo.

Para obter mais informações sobre esse processo do, entre no [radar](https://radar.wandera.com/login)de entrada. Vá para **configurações** > **integração do EMM**, selecione a guia **push de aplicativo** e, em seguida, selecione **Microsoft Intune**. A guia push de aplicativo é atualizada com instruções que são específicas para o Intune.  

### <a name="add-the-wandera-apps"></a>Adicionar os aplicativos do inphonea  
Crie aplicativos cliente no Intune para implantar o aplicativo do backit em dispositivos Android e iOS. Consulte [adicionar aplicativos do MTD](mtd-apps-ios-app-configuration-policy-add-assign.md) para obter os procedimentos e detalhes personalizados específicos para os aplicativos do.  

Depois de criar os aplicativos, retorne aqui para criar o grupo de sincronização e atribuir os aplicativos.  


### <a name="create-the-synchronization-group-and-assign-the-apps"></a>Criar o grupo de sincronização e atribuir os aplicativos

1. Obtenha o nome do grupo **SyncOnly** que aparece abaixo do **rótulo EMM** de dentro do console de radar do backit. Você pode ter salvo esse nome durante a etapa 7 enquanto [habilita o suporte para](#enable-support-for-wandera-in-intune)o no Intune. Use esse nome como o nome do grupo no Intune para sincronização de innovat.  

2. No console do Intune, vá para **grupos** e selecione **novo grupo**. Especifique o seguinte para configurar o grupo de sincronização para uso pelo:
   - **Tipo de grupo**: **segurança**
   - **Nome do grupo**: especifique o nome do **SyncOnly** que você recuperou do console de administração de radar do backit.

   ![configurar o grupo de sincronização](./media/wandera-mtd-connector-integration/configure-sync-group.png)

3. Selecione **Membros** e atribua grupos que incluam os dispositivos Android e Ios que você deseja usar com o.

4. Selecione **criar** para salvar o grupo.

Para obter mais informações, consulte [implantar aplicativos](../apps/apps-deploy.md)

### <a name="assign-the-wandera-apps-to-the-synchronization-group"></a>Atribuir os aplicativos do ao grupo de sincronização  
Repita o procedimento a seguir para o aplicativo do onit que você criou para iOS e para Android.

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) e vá para **aplicativos cliente** > **aplicativos** e selecione o aplicativo do backit.  

2. Selecione **atribuições** e **Adicionar grupo**.  

3. No painel *Adicionar grupo* , para *tipo de atribuição* , selecione **obrigatório**.

4. Selecione **grupos incluídos**e **selecione grupos a serem incluídos**. Especifique o grupo que você criou para a sincronização de vagaa e clique em **selecionar** > **OK** > **OK**. Selecione **salvar** para concluir a atribuição de grupo.  
 

## <a name="next-steps"></a>Passos Seguintes  
Agora que você configurou a integração, pode iniciar a configuração de políticas, configurar o acesso condicional avançado e exibir relatórios no console de administração do inicioa. Para saber mais sobre como gerenciar e configurar o, consulte o [Guia do centro de suporte introdução](https://radar.wandera.com/?return_to=https://wandera.force.com/Customer/s/getting-started) na documentação do backcenter.  
 
