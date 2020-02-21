---
title: Configurar a integração de Proteção contra Ameaças Móveis wandera com Intune
titleSuffix: Intune on Azure
description: Como configurar a solução Wandera Mobile Threat Protection com a Microsoft Intune para controlar o acesso de dispositivos móveis aos seus recursos corporativos.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 12/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: d90e3757ced90bea21e4033b6baa93bfa201b1f2
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514222"
---
# <a name="integrate-wandera-mobile-threat-protection-with-intune"></a>Integrar a Wandera Mobile Threat Protection com Intune  

Complete os seguintes passos para integrar a solução Wandera Mobile Threat Defense com intune.  

> [!NOTE]
> Este fornecedor de Defesa de Ameaças Móveis não é suportado para dispositivos não matriculados.

## <a name="before-you-begin"></a>Antes de começar  

Antes de iniciar o processo de integração do Wandera com o Intune, certifique-se de que tem os seguintes pré-requisitos no lugar:
- Subscrição do Microsoft Intune  
- Credenciais de administrador do Azure Active Directory para conceder as seguintes permissões:  
  - Iniciar sessão e ler o perfil de utilizador  
  - Aceder ao diretório como o utilizador com sessão iniciada  
  - Ler dados do diretório  
  - Enviar informações do dispositivo para o Intune  

- Assinatura Wandera:
  - Uma ou mais contas Wandera que são licenciadas para emM Connect  
  - Uma conta com privilégios de super administrador em Wandera  
 
### <a name="wandera-mobile-threat-defense-app-authorization"></a>Autorização de aplicação wandera Mobile Threat Defense  

O processo de autorização da aplicação Wandera Mobile Threat Defense:  
- Permitir que o serviço wandera mobile threat defense comunique informações relacionadas com o estado de saúde do dispositivo de volta ao Intune.  
- A Wandera sincroniza-se com a adesão do Grupo de Inscrição da AD Azure para preencher a base de dados do seu dispositivo.  
- Permita que o portal de administração Wandera RADAR utilize o Letreiro Único Azure AD (SSO).  
- Permita que a aplicação Wandera Mobile Threat Defense assine a utilização do Azure AD SSO.  


## <a name="set-up-wandera-mobile-threat-defense-integration"></a>Criar a integração da Defesa de Ameaças Móveis Wandera  
A configuração do *EMM Connect* for Wandera requer um processo de configuração único que completa nas consolas Intune e Wandera. O processo de configuração demora cerca de 15 minutos. Pode completar a configuração sem coordenação com a sua conta técnica Wandera ou representante de suporte.  

### <a name="enable-support-for-wandera-in-intune"></a>Ativar suporte para Wandera em Intune

1. Inscreva-se no centro de administração do [Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selecione **a administração do Inquilino** > **Conectores e fichas** > **Defesa de Ameaças Móveis** > **Adicionar**.
3. Na página **Add Connector,** utilize o dropdown e selecione **Wandera**. E, em seguida, **selecione Criar**.  
4. No painel de Defesa de Ameaças Móveis, selecione o Conector **Wandera** MTD da lista de conectores para abrir o painel de *conectores Editar.* **Selecione Abra a consola de administração Wandera** para abrir o [RADAR,](https://radar.wandera.com/login)a consola de administração Wandera e inscreva-se. 
5. Na consola Wandera, vá a **Definições** > **Integração EMM**, e selecione o separador **EMM Connect.** Utilize a queda do *Fornecedor EMM* e selecione *Microsoft Intune*.

   ![Selecione Intune](./media/wandera-mtd-connector-integration/set-up-intune-in-radar.png)

6. Selecione **permissões de Grant** para abrir uma ligação ao portal Intune. Inscreva-se utilizando as suas credenciais de administração Intune, selecione a caixa de verificação **e,** em seguida, aceite o pedido de permissões.  

   ![Aceitar permissões](./media/wandera-mtd-connector-integration/permissions.png) 

7. A Wandera completa a ligação e devolve-o à consola de administração RADAR. Repita o processo para **conceder** acesso para configurações adicionais, conforme necessário.  

   ![Integrações e permissões](./media/wandera-mtd-connector-integration/integrations-and-permissions.png) 

8. Enquanto estiver na consola RADAR, copie o nome do grupo **SyncOnly** que aparece abaixo da **etiqueta EMM**. Você usará este nome para configurar um grupo em Intune para sincronização com Wandera.

   ![Grupo de sincronização](./media/wandera-mtd-connector-integration/sync-group-name.png) 

9. Volte à consola [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) e edite o Conector Wandera MTD. Detete os toggles disponíveis para **On**e **guarde** a configuração.  

   ![Ativar wandera](./media/wandera-mtd-connector-integration/enable-wandera.png) 

Intune e Wandera estão agora ligados.  

## <a name="configure-the-wandera-applications-and-synchronization-group"></a>Configure as aplicações wandera e o grupo de sincronização  
Para implementar o Wandera, irá adicionar as aplicações móveis Wandera para as plataformas que utiliza (iOS e Android) ao Intune e atribuí-las a um grupo específico para sincronização; o grupo *SyncOnly.* 

As seguintes secções e procedimentos irão guiá-lo através deste processo.

Para mais informações sobre este processo a partir de Wandera, inscreva-se no Wandera [RADAR](https://radar.wandera.com/login). Vá a **Definições** > **Integração EMM,** selecione o separador Push da **aplicação** e, em seguida, selecione **Microsoft Intune**. O separador Push app atualiza com instruções específicas para Intune.  

### <a name="add-the-wandera-apps"></a>Adicione as aplicações Wandera  
Crie aplicações para clientes em Intune para implementar a aplicação Wandera para dispositivos Android e iOS/iPadOS. Consulte [aplicativos MTD adicionais](mtd-apps-ios-app-configuration-policy-add-assign.md) para os procedimentos e detalhes personalizados específicos das aplicações Wandera.  

Depois de criar as apps, volte aqui para criar o grupo de sincronização e atribuir as aplicações.

### <a name="create-the-synchronization-group-and-assign-the-apps"></a>Crie o grupo de sincronização e atribua as aplicações

1. Obtenha o nome do grupo **SyncOnly** que aparece abaixo da **etiqueta EMM** a partir da consola Wandera RADAR. Pode ter guardado este nome durante o passo 7, ao mesmo tempo que [permitiu o apoio ao Wandera em Intune](#enable-support-for-wandera-in-intune). Use este nome como o nome do grupo em Intune para sincronização wandera.  

2. No centro de administração do Endpoint Manager, vá a **Grupos** e selecione **Novo grupo**. Especifique o seguinte para configurar o grupo de sincronização para utilização pela Wandera:
   - **Tipo de grupo**: **Segurança**
   - **Nome do grupo**: Especifique o nome **SyncOnly** que recuperou da consola de administração Wandera RADAR.

   ![configurar o grupo de sincronização](./media/wandera-mtd-connector-integration/configure-sync-group.png)

3. Selecione **Membros** e atribua grupos que incluam os dispositivos Android e iOS/iPadOS que pretende utilizar com o Wandera.

4. Selecione **Criar** para salvar o grupo.

Para mais informações, consulte [aplicações de implementação](../apps/apps-deploy.md)

### <a name="assign-the-wandera-apps-to-the-synchronization-group"></a>Atribuir as aplicações Wandera ao grupo de sincronização  
Repita o seguinte procedimento para a aplicação Wandera que criou para iOS/iPadOS e para Android.

1. Inscreva-se no centro de administração do [Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selecione **Apps** > **Todas as aplicações** e selecione a aplicação Wandera.
3. Selecione **Atribuições** e, em **seguida, Adicionar grupo**.  
4. No painel do *grupo Adicionar,* para selecionar o tipo de *atribuição* **necessário**.
5. Selecione **grupos incluídos**e, em seguida, **selecione grupos para incluir**. Especifique o grupo que criou para a sincronização do Wandera e, em seguida, clique em **Select** > **OK** > **OK**. Selecione **Guardar** para completar a atribuição do grupo. 

## <a name="next-steps"></a>Passos Seguintes  
Agora que configuraste a Integração, podes começar a configurar políticas, configurar um acesso condicional avançado e ver relatórios na consola de administração wandera. Para saber mais sobre gestão e configuração do Wandera, consulte o Guia de Arranque do Centro de [Apoio](https://radar.wandera.com/?return_to=https://wandera.force.com/Customer/s/getting-started) na documentação Wandera. 
