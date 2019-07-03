---
title: Configurar a integração de Wandera Mobile Threat Protection com o Intune
titleSuffix: Intune on Azure
description: Como configurar a solução de Wandera Mobile Threat Protection com o Microsoft Intune para controlar o acesso de dispositivos móveis aos seus recursos empresariais.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: e4f2969c6bb7f15022990aa99bbf20e94588406e
ms.sourcegitcommit: 84c79ceea27f7411528defc5ee8ba35ae2bf473c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/02/2019
ms.locfileid: "67512292"
---
# <a name="integrate-wandera-mobile-threat-protection-with-intune"></a>Integrar Wandera Mobile Threat Protection com o Intune  

Conclua os seguintes passos para integrar a solução de Wandera Mobile Threat Defense com o Intune.  

## <a name="before-you-begin"></a>Antes de começar  

Antes de começar o processo de integração Wandera com o Intune, certifique-se que tem os seguintes pré-requisitos:
- Subscrição do Microsoft Intune  
- Credenciais de administrador do Azure Active Directory para conceder as seguintes permissões:  
  - Iniciar sessão e ler o perfil de utilizador  
  - Aceder ao diretório como o utilizador com sessão iniciada  
  - Ler dados do diretório  
  - Enviar informações do dispositivo para o Intune  

- Subscrição de Wandera:
  - Uma ou mais contas de Wandera estão licenciadas para ligar de EMM  
  - Uma conta com privilégios de administrador Super no Wandera  
 
### <a name="wandera-mobile-threat-defense-app-authorization"></a>Autorização da aplicação Wandera Mobile Threat Defense  

O processo de autorização do Wandera Mobile Threat Defense aplicação:  
- Permitir que o serviço de Wandera Mobile Threat Defense comunicar informações relacionadas com o estado de funcionamento do dispositivo ao Intune.  
- Wandera sincroniza com a associação de grupo de inscrição do Azure AD para povoar a base de dados do seu dispositivo.  
- Permitir que o portal de administração de Wandera RADAR utilizar o Azure AD único início de sessão (SSO).  
- Permitir que a aplicação de Wandera Mobile Threat Defense iniciar sessão com o SSO do Azure AD.  


## <a name="set-up-wandera-mobile-threat-defense-integration"></a>Configurar a integração de Wandera Mobile Threat Defense  
Configuração do *EMM ligar* para Wandera requer uma configuração única processar que concluir nas consolas do Intune e Wandera. O processo de configuração demora cerca de 15 minutos. Pode concluir a configuração sem coordenação com a sua conta técnica Wandera ou representante de suporte.  

### <a name="enable-support-for-wandera-in-intune"></a>Ativar o suporte para Wandera no Intune
1. Inicie sessão no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) e aceda à **conformidade do dispositivo** > **Mobile Threat Defense** > e selecione **adicionar**.

2. Sobre o **adicionar conector** página, utilize a lista pendente e selecione **Wandera**. E, em seguida, selecione **criar**.  

3. No painel de defesa contra ameaças móveis, selecione o **Wandera** conector de MTD, na lista de conectores para abrir o *editar conector* painel. Selecione **abra a consola de administração Wandera** para abrir [RADAR](https://radar.wandera.com/login), a consola de administração de Wandera e início de sessão. 

4. Na consola do Wandera, aceda a **configurações** > **integração de EMM**e selecione o **EMM ligar** separador. Utilize o *fornecedor de EMM* menu pendente e selecione *Microsoft Intune*.

   ![Selecione o Intune](media/wandera-mtd-connector-integration/set-up-intune-in-radar.png)

5. Selecione **conceder permissões** para abrir uma ligação ao portal do Intune. Inicie sessão com as credenciais de administrador do Intune, selecione a caixa de verificação e, em seguida **Accept** solicitar as permissões.  

   ![Aceitar as permissões](media/wandera-mtd-connector-integration/permissions.png) 

6. Wandera a ligação de conclusão e volta para a consola de administração RADAR. Repita o processo para **concessão** aceder para configurações adicionais, conforme necessário.  

   ![Integrações e permissões](media/wandera-mtd-connector-integration/integrations-and-permissions.png) 

7. Embora, na consola do RADAR, copie o nome do **SyncOnly** grupo que aparece abaixo **EMM etiqueta**. Irá utilizar este nome para configurar um grupo no Intune para a sincronização com Wandera.

   ![Integrações e permissões](media/wandera-mtd-connector-integration/sync-group-name.png) 

8. Retorno para o [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) consola e editar o conector de MTD Wandera. Definir os botões de alternar disponíveis **nos**e o **guardar** a configuração.  

   ![Ativar Wandera](media/wandera-mtd-connector-integration/enable-wandera.png) 

O Intune e Wandera estão agora ligado.  

## <a name="configure-the-wandera-applications-and-synchronization-group"></a>Configurar o Wandera aplicativos e o grupo de sincronização  
Para implementar Wandera, irá adicionar as aplicações móveis Wandera para as plataformas utiliza (iOS e Android) para o Intune e atribuí-las a um grupo específico para a sincronização; o *SyncOnly* grupo. 

As seguintes secções e procedimentos irão guiá-lo por meio desse processo.

Para obter mais informações sobre este processo de Wandera, inicie sessão no Wandera [RADAR](https://radar.wandera.com/login). Aceda a **configurações** > **integração de EMM**, selecione o **Push da aplicação** separador e, em seguida, selecione **Microsoft Intune**. As atualizações de separador de emissão de aplicação com as instruções que são específicas para o Intune.  

### <a name="add-the-wandera-apps"></a>Adicionar as aplicações de Wandera  
Crie aplicações de cliente no Intune para implementar a aplicação de Wandera em dispositivos Android e iOS. Ver [aplicações de MTD adicionar](mtd-apps-ios-app-configuration-policy-add-assign.md) para os procedimentos e detalhes personalizadas específicas para as aplicações de Wandera.  

Depois de criar as aplicações, volte aqui para criar o grupo de sincronização e atribuir as aplicações dos nossos dias.  


### <a name="create-the-synchronization-group-and-assign-the-apps"></a>Criar o grupo de sincronização e atribuir as aplicações

1. Obter o nome da **SyncOnly** grupo que aparece abaixo **EMM etiqueta** no RADAR Wandera consola. Pode guardar este nome durante o passo 7 enquanto [ativar o suporte para Wandera no Intune](#enable-support-for-wandera-in-intune). Utilize este nome como o nome do grupo no Intune para a sincronização de Wandera.  

2. Na consola do Intune, aceda a **grupos** e selecione **novo grupo**. Especifique o seguinte para configurar o grupo de sincronização para utilização por Wandera:
   - **Tipo de grupo**: **Segurança**
   - **Nome do grupo**: Especifique a **SyncOnly** nome obtidos a partir da consola de administração Wandera RADAR.

   ![configurar o grupo de sincronização](media/wandera-mtd-connector-integration/configure-sync-group.png)

3. Selecione **membros** e atribuir grupos que incluem os dispositivos Android e iOS que pretende utilizar com Wandera.

4. Selecione **criar** para guardar o grupo.

Para obter mais informações, consulte [implementar aplicações](apps-deploy.md)

### <a name="assign-the-wandera-apps-to-the-synchronization-group"></a>Atribuir as aplicações de Wandera para o grupo de sincronização  
Repita o procedimento seguinte para a aplicação de Wandera que criou para iOS e Android.

1. Inicie sessão no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) e aceda à **aplicações de cliente** > **aplicações** e selecione a aplicação de Wandera.  

2. Selecione **atribuições** e, em seguida **adicionar grupo**.  

3. Sobre o *adicionar grupo* painel, para *tipo de atribuição* selecionar **necessário**.

4. Selecione **incluído grupos**e, em seguida **selecionar grupos para incluir**. Especifique o grupo que criou para a sincronização de Wandera e, em seguida, clique em **selecionar** > **OK** > **OK**. Selecione **guardar** para concluir a atribuição de grupo.  
 

## <a name="next-steps"></a>Próximos Passos  
Agora que configurou a integração, pode começar a configurar as políticas, configurar o acesso condicional avançado e ver relatórios na consola de administração de Wandera. Para obter mais informações sobre gerir e configurar Wandera, consulte a [suporte Center guia de introdução](https://radar.wandera.com/?return_to=https://wandera.force.com/Customer/s/getting-started) na documentação do Wandera.  
 