---
title: Configurar a sua integração do Lookout com o Microsoft Intune
titleSuffix: Microsoft Intune
description: Saiba como integrar o Intune com o Lookout Mobile Endpoint Security, como uma solução de defesa contra ameaças móveis, para controlar o acesso de dispositivos móveis aos seus recursos empresariais.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/11/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5b0d7644-3183-45ba-a165-0d82d70cb71e
ms.reviewer: davera
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: be2e9371288961d0afdf7ad6e8cfec8f734087f6
ms.sourcegitcommit: 7315fe72b7e55c5dcffc6d87f185f3c2cded9028
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/02/2019
ms.locfileid: "67529968"
---
# <a name="set-up-lookout-mobile-endpoint-security-integration-with-intune"></a>Configurar a integração do Lookout Mobile Endpoint Security com o Intune
Com um ambiente que cumpra os [pré-requisitos](lookout-mobile-threat-defense-connector.md#prerequisites), pode integrar o Lookout Mobile Endpoint Security com o Intune. As informações neste artigo irão guiá-lo na configuração de integração e configurar definições importantes no Lookout para utilização com o Intune.  

> [!IMPORTANT]
> Um inquilino do Lookout Mobile Endpoint Security que ainda não esteja associado ao seu inquilino do Azure AD não pode ser utilizado na integração com o Azure AD e o Intune. Contacte o suporte do Lookout para criar um novo inquilino do Lookout Mobile Endpoint Security. Utilize o novo inquilino para integrar os seus utilizadores do Azure AD.

## <a name="collect-azure-ad-information"></a>Recolher informações do Azure AD  
Para obter Lookout integrada com o Intune, associar o seu inquilino do Lookout Mobile Endpoint Security com a sua subscrição do Azure Active Directory (AD).

Para ativar a integração de subscrição do Lookout Mobile Endpoint Security com o Intune, forneça as seguintes informações para o suporte do Lookout (enterprisesupport@lookout.com):  

- **Inquilino do Azure AD, ID de diretório**  

- **ID de objeto de grupo do Azure AD** para o grupo com **completa** acesso à consola do Lookout Mobile Endpoint Security (MES).  
  Crie este grupo de utilizadores no Azure AD para os utilizadores que têm de conter *acesso total* para iniciar sessão para o **consola do Lookout**. Os utilizadores têm de ser membros deste grupo, ou o opcional *acesso restrito* grupo, para iniciar sessão na consola do Lookout. 

- **ID de objeto de grupo do Azure AD** para o grupo com **restritos** acesso à consola do Lookout MES *(grupo opcional)* . 
  Crie este grupo de utilizadores opcional no Azure AD para conter os utilizadores que não devem ter acesso a vários módulos relacionadas com a inscrição na consola do Lookout e a configuração. Em vez disso, estes utilizadores têm acesso só de leitura para o **política de segurança** módulo na consola do Lookout. Os utilizadores têm de ser membros deste grupo opcional, ou necessários *acesso total* grupo, para iniciar sessão na consola do Lookout.

 > [!TIP] 
 > Para obter mais detalhes sobre as permissões, consulte [este artigo](https://personal.support.lookout.com/hc/articles/114094105653) no site do Lookout.

### <a name="collect-information-from-azure-ad"></a>Recolher informações do Azure AD 

1. Inicie sessão para o [portal do Azure](https://portal.azure.com) com uma conta de Administrador Global.

2. Aceda a **do Azure Active Directory** > **propriedades** e localize seu **ID do diretório**. Utilize o *cópia* botão para copiar o ID de diretório e, em seguida, guarde-o num ficheiro de texto.

   ![Propriedades do Azure AD](./media/lookout-mtd-connector-integration/azure-ad-properties.png)  

3. Em seguida, localize o ID de grupo do Azure AD para as contas que utiliza para conceder acesso à consola do Lookout de utilizadores do Azure AD. Um grupo destina *acesso total*e o segundo grupo, para *acesso restrito* é opcional. Para obter o *ID de objeto*, para cada conta:  
   1. Aceda a **do Azure Active Directory** > **grupos** para abrir o *grupos – todos os grupos* painel.  

   2. Selecione o grupo que criou para *acesso total* para abrir o respetivo *descrição geral* painel.  

   3. Utilize o *cópia* botão para copiar o ID de objeto e, em seguida, guarde-o num ficheiro de texto.  

   4. Repita o processo para o *acesso restrito* se utilizar o grupo de grupo.  

      ![Grupo do AD Azure ID de objeto](./media/lookout-mtd-connector-integration/azure-ad-group-id.png)  

   Depois de recolher estas informações, contacte o suporte do Lookout (e-mail: enterprisesupport@lookout.com). Suporte do lookout irá funcionar com o seu contacto principal para integrar a sua subscrição e criar a sua conta do Lookout Enterprise com as informações fornecidas por si.  

## <a name="configure-your-lookout-subscription"></a>Configurar a sua subscrição do Lookout  
Após o suporte do Lookout cria a sua conta do Lookout Enterprise, o suporte do Lookout, envia um e-mail para o contacto principal para a sua empresa com uma ligação para o url de início de sessão: https://aad.lookout.com/les?action=consent. 

### <a name="initial-sign-in"></a>O início de sessão inicial  
O primeiro início de sessão na consola do Lookout MES apresenta uma página de consentimento (https://aad.lookout.com/les?action=consent). Um Administrador Global de AD do Azure apenas início de sessão e **Accept**. O início de sessão subsequente não precisa do utilizador tenha este nível de privilégio no Azure AD. 

 É apresentada uma página de consentimento. Selecione **Aceitar** para concluir o registo. 
   ![captura de ecrã da primeira início de sessão na página da consola do Lookout](./media/lookout-mtd-connector-integration/lookout_mtp_initial_login.png)

Ao aceitar e consentir, está redirecionado para a consola do Lookout.

Após o início de sessão inicial e o consentimento for concluída, os utilizadores que iniciam sessão de https://aad.lookout.com redirecionado para a consola do MES. Se ainda não foi concedido o consentimento, todas as tentativas de início de sessão resultarem num erro de início de sessão inválido.

### <a name="configure-the-intune-connector"></a>Configurar o conector do Intune  
O procedimento seguinte assume que criou anteriormente um grupo de utilizadores no Azure AD para testar a implementação do Lookout. A melhor prática é começar com um pequeno grupo de utilizadores para permitir aos administradores do Lookout e do Intune para se familiarizar com as integrações de produtos. Depois de estarem familiares, pode alargar a inscrição a grupos de utilizadores adicionais.

1. Entrar para o [consola do Lookout MES](https://aad.lookout.com) e aceda à **sistema** > **conectores**e, em seguida, selecione **adicionar conector**.  Selecione **Intune**.

   ![Imagem da consola do Lookout com a opção do Intune no separador de conectores](./media/lookout-mtd-connector-integration/lookout_mtp_setup-intune-connector.png)

2. Sobre o *Microsoft Intune* painel, selecione **definições de ligação** e especifique o **frequência do Heartbeat** em minutos. 

   ![Imagem do separador de definições de ligação com frequência do heartbeat configurado](./media/lookout-mtd-connector-integration/lookout-mtp-connection-settings.png)

3. Selecione **gestão de inscrições**e para **utilize os seguintes grupos de segurança do Azure AD para identificar dispositivos que devem estar inscritos no Lookout for Work**, especifique o *nome do grupo*de um grupo do Azure AD para utilizar com o Lookout e, em seguida, selecione **guardar alterações**.

    ![captura de ecrã da página de inscrição do conector do Intune](./media/lookout-mtd-connector-integration/lookout-mtp-enrollment.png)  

   **Sobre os grupos que utiliza**:
   - Como melhor prática, comece com um grupo de segurança do Azure AD que contém um pequeno número de utilizadores para testar a integração do Lookout.
   - O **nome do grupo** diferencia maiúsculas de minúsculas como mostra a **propriedades** do grupo de segurança no portal do Azure.  
   - Os grupos que especificou para **gestão de inscrições** definir o conjunto de utilizadores cujos dispositivos serão inscritos com o Lookout. Quando um utilizador estiver num grupo de inscrição, os dispositivos no Azure AD serão inscritos e poderão ser ativados no Lookout MES. Na primeira vez que um utilizador abre o *Lookout for Work* aplicação num dispositivo suportado, for pedidos para ativá-lo.

4. Selecione **sincronização do estado** e certifique-se a ambos *estado do dispositivo* e *estado da ameaça* são definidas como **no**.  Ambos são necessárias para a integração do Lookout Intune possa funcionar corretamente.  

5. Selecione **gerenciamento de erros**, especifique o endereço de e-mail que deve receber os relatórios de erros e, em seguida, selecione **guardar alterações**.
 
   ![Captura de ecrã da página de gestão de erros do conector do Intune](./media/lookout-mtd-connector-integration/lookout-mtp-connector-error-notifications.png)

6. Selecione **criar conector** para toda a configuração do conector. Mais tarde, quando estiver satisfeito com os resultados, pode alargar a inscrição a grupos de utilizadores adicionais.

## <a name="configure-intune-to-use-lookout-as-a-mobile-threat-defense-provider"></a>Configurar o Intune para utilizar o Lookout como um fornecedor de Mobile Threat Defense
Depois de configurar o Lookout MES, tem de definir uma conexão com o Lookout no Intune.  

1. Inicie sessão no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).

2. Aceda a **conformidade do dispositivo** > **Mobile Threat Defense** e selecione **adicionar**.

3. Sobre o *adicionar conector* painel, utilize a menu pendente e selecione **Lookout for Work**.  

4. Selecione **Criar**. Depois do conector estabelece o contacto com MES do Lookout, o *definições do conector* se tornarem disponíveis.

5. Definir **ativar a sincronização de aplicações para dispositivos iOS** ao **no**. 

6. Selecione **guardar** para concluir a configuração.  O Intune e o Lookout MES estão agora integrado e pronto para uso.


## <a name="additional-settings-in-the-lookout-mes-console"></a>Definições adicionais na consola de MES do Lookout
Seguem-se as definições adicionais que pode configurar na consola de MES do Lookout.  

### <a name="configure-enrollment-settings"></a>Configurar definições de inscrição
Na consola de MES do Lookout, selecione **System** > **gerir inscrição** > **as definições de inscrição**.  

- Para **estado desligado**, especifique o número de dias antes de um dispositivo de solução desligado é marcado como desligada.  

  Considera-se que os dispositivos desligados não estão em conformidade e o acesso às aplicações da empresa a partir dos mesmos será bloqueado com base nas políticas de acesso condicional do Intune. Pode especificar valores entre 1 e 90 dias.

  ![Definições de inscrição do lookout no módulo do sistema](./media/lookout-mtd-connector-integration/lookout-console-enrollment-settings.png)

### <a name="configure-email-notifications"></a>Configurar notificações por E-Mail
Para receber alertas por e-mail relativos a ameaças, inicie sessão para o [consola do Lookout MES](https://aad.lookout.com) com a conta de utilizador que deve receber notificações.  

- Aceda a **preferências** e, em seguida, defina as notificações que pretende receber para **ON**e, em seguida **guardar** as alterações.  

- Se já não quiser receber notificações por e-mail, defina as mesmas como **OFF** e guarde as alterações.

  ![captura de ecrã da página de preferências a apresentar da conta de utilizador](./media/lookout-mtd-connector-integration/lookout-mtp-email-notifications.png)



## <a name="configure-threat-classifications"></a>Configurar classificações de ameaças  
Lookout Mobile Endpoint Security classifica ameaças contra dispositivos móveis de vários tipos. As classificações de ameaças do Lookout têm níveis de risco predefinidos inerentes às mesmas. Os níveis de risco podem ser alterados em qualquer altura para atender às suas necessidades da empresa.

Para obter informações sobre as classificações de nível de ameaça e como gerir os níveis de risco associados a eles, consulte [referência de ameaças do Lookout](https://enterprise.support.lookout.com/hc/articles/360011812974).

>[!IMPORTANT]
> Níveis de risco são um aspecto importante do Mobile Endpoint Security, uma vez que a integração do Intune calcula a conformidade do dispositivo, de acordo com estes níveis de risco em tempo de execução.  
> 
> O administrador do Intune define uma regra na política para identificar se um dispositivo não estiver em conformidade, caso o mesmo apresente uma ameaça ativa com um nível mínimo de risco **Alto**, **Médio** ou **Baixo**. A política de classificação de ameaças do Lookout Mobile Endpoint Security unidades diretamente o cálculo da conformidade de dispositivo no Intune.  

## <a name="monitor-enrollment"></a>Inscrição de monitor
Após a configuração estiver concluída, o Lookout Mobile Endpoint Security é iniciado consultar o Azure AD para dispositivos que correspondam aos grupos de inscrição especificados.  Pode encontrar informações sobre os dispositivos inscritos, acedendo a **dispositivos** na consola de MES do Lookout.  
- Estado inicial dos dispositivos é *pendente*.  
- Atualizações, o estado do dispositivo depois do *Lookout for Work* aplicação é instalada, aberta e ativada no dispositivo.

Para obter detalhes sobre como obter o *Lookout for Work* aplicação implementada para um dispositivo, veja [adicionar aplicações Lookout for work com o Intune](mtd-apps-ios-app-configuration-policy-add-assign.md).

## <a name="next-steps"></a>Passos Seguintes

[Set up Lookout apps (Configurar aplicações do Lookout)](mtd-apps-ios-app-configuration-policy-add-assign.md)
