---
title: Configurar a sua integração do Lookout com o Microsoft Intune
titleSuffix: Microsoft Intune
description: Saiba como integrar o Intune com o Mobile Endpoint Security, como uma solução de defesa contra ameaças móveis, para controlar o acesso de dispositivos móveis aos seus recursos corporativos.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/11/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5b0d7644-3183-45ba-a165-0d82d70cb71e
ms.reviewer: davera
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b4661b151493eb68cc6f71a5a77bd023ac27b826
ms.sourcegitcommit: 3ace4cba6e2f6fefa9120be3807387a49b200c9b
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/23/2019
ms.locfileid: "72810217"
---
# <a name="set-up-lookout-mobile-endpoint-security-integration-with-intune"></a>Configurar a integração de segurança de ponto de extremidade móvel com o Intune
Com um ambiente que atende aos [pré-requisitos](lookout-mobile-threat-defense-connector.md#prerequisites), você pode integrar a consulta à segurança de ponto de extremidade móvel com o Intune. As informações neste artigo o orientarão na configuração da integração e na definição de configurações importantes na consulta para uso com o Intune.  

> [!IMPORTANT]
> Um inquilino do Lookout Mobile Endpoint Security que ainda não esteja associado ao seu inquilino do Azure AD não pode ser utilizado na integração com o Azure AD e o Intune. Contacte o suporte do Lookout para criar um novo inquilino do Lookout Mobile Endpoint Security. Utilize o novo inquilino para integrar os seus utilizadores do Azure AD.

## <a name="collect-azure-ad-information"></a>Recolher informações do Azure AD  
Para fazer a consulta integrada com o Intune, você associa seu locatário de segurança de ponto de extremidade de mobilidade de consulta à sua assinatura do Azure Active Directory (AD).

Para habilitar a integração da sua consulta de assinatura do Endpoint Mobile Security com o Intune, você fornece as seguintes informações para dar suporte à consulta (enterprisesupport@lookout.com):  

- **ID do diretório de locatário do Azure AD**  

- **ID de objeto de grupo do Azure ad** para o grupo com acesso **completo** ao console do mes (Mobile Endpoint Security).  
  Você cria esse grupo de usuários no Azure AD para conter os usuários que têm *acesso completo* para entrar no **console**da consulta. Os usuários devem ser membros desse grupo ou o grupo de *acesso restrito* opcional, para entrar no console da consulta. 

- **ID de objeto de grupo do Azure ad** para o grupo com acesso **restrito** ao console mes *de consulta (grupo opcional)* . 
  Você cria esse grupo de usuários opcionais no Azure AD para conter usuários que não devem ter acesso a vários módulos relacionados à configuração e ao registro do console de consulta. Em vez disso, esses usuários têm acesso somente leitura ao módulo **política de segurança** do console de consulta. Os usuários devem ser membros desse grupo opcional, ou o grupo de *acesso completo* necessário, para entrar no console da consulta.

 > [!TIP] 
 > Para obter mais detalhes sobre as permissões, consulte [este artigo](https://personal.support.lookout.com/hc/articles/114094105653) no site do Lookout.

### <a name="collect-information-from-azure-ad"></a>Coletar informações do Azure AD 

1. Entre no [portal do Azure](https://portal.azure.com) com uma conta de administrador global.

2. Vá para **Azure Active Directory** **Propriedades**  >  e localize a **ID do diretório**. Use o botão *copiar* para copiar a ID do diretório e, em seguida, salve-a em um arquivo de texto.

   ![Propriedades do Azure AD](./media/lookout-mtd-connector-integration/azure-ad-properties.png)  

3. Em seguida, localize a ID do grupo do Azure AD para as contas que você usa para conceder aos usuários do Azure AD acesso ao console de consulta. Um grupo é para *acesso completo*e o segundo grupo, para *acesso restrito* , é opcional. Para obter a *ID de objeto*, para cada conta:  
   1. Vá para **Azure Active Directory** > **grupos** para abrir o painel *grupos – todos os grupos* .  

   2. Selecione o grupo criado para *acesso completo* para abrir seu painel *visão geral* .  

   3. Use o botão *copiar* para copiar a ID de objeto e, em seguida, salve-a em um arquivo de texto.  

   4. Repita o processo para o grupo de *acesso restrito* se você usar esse grupo.  

      ![ID do objeto do grupo do Azure AD](./media/lookout-mtd-connector-integration/azure-ad-group-id.png)  

   Depois de reunir essas informações, entre em contato com o suporte à consulta (email: enterprisesupport@lookout.com). O suporte à consulta funcionará com seu contato principal para integrar sua assinatura e criar sua conta corporativa de consulta, usando as informações fornecidas.  

## <a name="configure-your-lookout-subscription"></a>Configurar sua assinatura de consulta  

As etapas a seguir devem ser concluídas no console do administrador corporativo de consulta e permitirão uma conexão ao serviço de consulta para dispositivos registrados no Intune (via conformidade do dispositivo) **e** dispositivos não registrados (por meio de políticas de proteção de aplicativo).

Depois que o suporte à consulta criar sua conta corporativa de consulta, o suporte à consulta enviará um email para o contato principal da sua empresa com um link para a URL de entrada: https://aad.lookout.com/les?action=consent. 

### <a name="initial-sign-in"></a>Entrada inicial  
A primeira entrada no console do MES de consulta exibe uma página de consentimento (https://aad.lookout.com/les?action=consent). Um administrador global do Azure AD apenas entra e **aceita**. A entrada subsequente não exige que o usuário tenha esse nível de privilégio do Azure AD. 

 É apresentada uma página de consentimento. Selecione **Aceitar** para concluir o registo. 
   ![captura de tela da primeira página de entrada do console de consulta](./media/lookout-mtd-connector-integration/lookout_mtp_initial_login.png)

Ao aceitar e consentir, você será redirecionado para o console de consulta.

Depois que a entrada inicial e o consentimento forem concluídos, os usuários que entrarem de https://aad.lookout.com serão redirecionados para o console do MES. Se o consentimento ainda não tiver sido concedido, todas as tentativas de entrada resultarão em um erro de logon incorreto.

### <a name="configure-the-intune-connector"></a>Configurar o conector do Intune  
O procedimento a seguir pressupõe que você criou anteriormente um grupo de usuários no Azure AD para testar sua implantação de consulta. A prática recomendada é começar com um pequeno grupo de usuários para permitir que seus administradores de consulta e do Intune se familiarizem com as integrações do produto. Depois que eles estiverem familiarizados, você poderá estender o registro para grupos de usuários adicionais.

1. Entre no console do [mes](https://aad.lookout.com) de consulta e vá para**conectores**do **sistema** >  e, em seguida, selecione **Adicionar conector**.  Selecione **Intune**.

   ![Imagem do console da consulta com a opção do Intune na guia conectores](./media/lookout-mtd-connector-integration/lookout_mtp_setup-intune-connector.png)

2. No painel *Microsoft Intune* , selecione **configurações de conexão** e especifique a **frequência de pulsação** em minutos. 

   ![Imagem da guia Configurações de conexão com frequência de pulsação configurada](./media/lookout-mtd-connector-integration/lookout-mtp-connection-settings.png)

3. Selecione **Gerenciamento de registro**e, para **usar os seguintes grupos de segurança do Azure ad para identificar os dispositivos que devem ser registrados no Lookout for Work**, especifique o *nome do grupo* de um grupo do Azure ad a ser usado com a consulta e, em seguida, selecione **salvar alterações**.

    ![captura de ecrã da página de inscrição do conector do Intune](./media/lookout-mtd-connector-integration/lookout-mtp-enrollment.png)  

   **Sobre os grupos que você usa**:
   - Como prática recomendada, comece com um grupo de segurança do Azure AD que contenha um pequeno número de usuários para testar a integração de consulta.
   - O **nome do grupo** diferencia maiúsculas de minúsculas, conforme mostrado nas **Propriedades** do grupo de segurança no portal do Azure.  
   - Os grupos que você especificar para o **Gerenciamento de registro** definem o conjunto de usuários cujos dispositivos serão registrados com a consulta. Quando um usuário está em um grupo de registro, seus dispositivos no Azure AD são registrados e qualificados para ativação no MES de consulta. Na primeira vez que um usuário abre o aplicativo *Lookout for Work* em um dispositivo com suporte, ele é solicitado a ativá-lo.

4. Selecione **sincronização de estado** e verifique se o status do *dispositivo* e o status **da** *ameaça* estão definidos como ativado.  Ambos são necessários para que a integração com a consulta do Intune funcione corretamente.  

5. Selecione **Gerenciamento de erros**, especifique o endereço de email que deve receber os relatórios de erros e, em seguida, selecione **salvar alterações**.
 
   ![Captura de ecrã da página de gestão de erros do conector do Intune](./media/lookout-mtd-connector-integration/lookout-mtp-connector-error-notifications.png)

6. Selecione **criar conector** para concluir a configuração do conector. Posteriormente, quando estiver satisfeito com os resultados, você poderá estender o registro para grupos de usuários adicionais.

## <a name="configure-intune-to-use-lookout-as-a-mobile-threat-defense-provider"></a>Configurar o Intune para usar a consulta como um provedor de defesa contra ameaças móveis
Depois de configurar a consulta MES, você deve configurar uma conexão para a consulta [no Intune](https://docs.microsoft.com/en-us/intune/protect/mtd-connector-enable).  

## <a name="additional-settings-in-the-lookout-mes-console"></a>Configurações adicionais no console do MES de consulta
A seguir estão as configurações adicionais que podem ser definidas no console do MES de consulta.  

### <a name="configure-enrollment-settings"></a>Definir configurações de registro
No console do MES de consulta, selecione **sistema** > **gerenciar** **configurações de registro** > .  

- Para **status desconectado**, especifique o número de dias antes que um dispositivo não conectado seja marcado como desconectado.  

  Considera-se que os dispositivos desligados não estão em conformidade e o acesso às aplicações da empresa a partir dos mesmos será bloqueado com base nas políticas de acesso condicional do Intune. Pode especificar valores entre 1 e 90 dias.

  ![Configurações de registro de consulta no módulo do sistema](./media/lookout-mtd-connector-integration/lookout-console-enrollment-settings.png)

### <a name="configure-email-notifications"></a>Configurar notificações por email
Para receber alertas de ameaças por email, entre no [console do mes](https://aad.lookout.com) de consulta com a conta de usuário que deve receber notificações.  

- Vá para **preferências** e defina as notificações que deseja receber e, em **seguida,** **salve** as alterações.  

- Se você não deseja mais receber notificações por email, defina as notificações como **desativado** e salve suas alterações.

  ![captura de tela da página preferências com a conta de usuário exibida](./media/lookout-mtd-connector-integration/lookout-mtp-email-notifications.png)

## <a name="configure-threat-classifications"></a>Configurar classificações de ameaças  
A consulta à segurança de ponto de extremidade móvel classifica ameaças móveis de vários tipos. As classificações de ameaça de consulta têm níveis de risco padrão associados a elas. Os níveis de risco podem ser alterados a qualquer momento para atender aos requisitos da sua empresa.

Para obter informações sobre as classificações de nível de ameaça e como gerenciar os níveis de risco associados a elas, consulte [referência de ameaça de consulta](https://enterprise.support.lookout.com/hc/articles/360011812974).

>[!IMPORTANT]
> Os níveis de risco são um aspecto importante da segurança de ponto de extremidade móvel, pois a integração do Intune calcula a conformidade do dispositivo de acordo com esses níveis de risco em tempo de execução.  
> 
> O administrador do Intune define uma regra na política para identificar se um dispositivo não estiver em conformidade, caso o mesmo apresente uma ameaça ativa com um nível mínimo de risco **Alto**, **Médio** ou **Baixo**. A política de classificação de ameaças em consulta de ponto de extremidade móvel é direcionada diretamente ao cálculo de conformidade do dispositivo no Intune.  

## <a name="monitor-enrollment"></a>Monitorar registro
Após a conclusão da instalação, a consulta à segurança do ponto de extremidade móvel começa a sondar o Azure AD para dispositivos que correspondem aos grupos de registro especificados.  Você pode encontrar informações sobre dispositivos registrados acessando **dispositivos** no console do mes de consulta.  
- O status inicial de dispositivos está *pendente*.  
- O status do dispositivo é atualizado depois que o aplicativo *Lookout for Work* é instalado, aberto e ativado no dispositivo.

Para obter detalhes sobre como fazer com que o aplicativo *Lookout for Work* implantado em um dispositivo, consulte [adicionar aplicativos de consulta para trabalho com o Intune](mtd-apps-ios-app-configuration-policy-add-assign.md).

## <a name="next-steps"></a>Próximos passos

- [Configurar aplicativos de consulta para dispositivos registrados](mtd-apps-ios-app-configuration-policy-add-assign.md)
- [Configurar aplicativos de consulta para dispositivos não registrados](~/protect/mtd-add-apps-unenrolled-devices.md)
