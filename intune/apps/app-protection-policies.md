---
title: Criar e implementar políticas de proteção de aplicações
titleSuffix: Microsoft Intune
description: Este tópico descreve como criar e atribuir políticas de proteção de aplicações (APP) do Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/03/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f31b2964-e932-4cee-95c4-8d5506966c85
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0c8507f98a757f2f80580014eab3589da12f8de8
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72499197"
---
# <a name="how-to-create-and-assign-app-protection-policies"></a>Como criar e atribuir políticas de proteção de aplicações

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Saiba como criar e atribuir políticas de proteção de aplicações do Microsoft Intune aos seus utilizadores. Este tópico também descreve como fazer alterações a políticas existentes.

## <a name="before-you-begin"></a>Antes de começar

As políticas de proteção de aplicações podem ser aplicadas às aplicações em execução nos dispositivos que podem ou não ser geridos pelo Intune. Para obter uma descrição mais detalhada acerca do funcionamento das políticas de proteção de aplicações e dos cenários que são suportados pelas políticas de proteção de aplicações do Intune, veja [O que são políticas de proteção de aplicações do Microsoft Intune?](app-protection-policy.md)

Se estiver a procurar uma lista de MAM com aplicações suportadas, veja as [Listas de aplicações de MAM](https://www.microsoft.com/cloud-platform/microsoft-intune-apps).

Para obter mais informações sobre como adicionar as aplicações de linha de negócio (LOB) da sua organização ao Microsoft Intune, para se preparar para as políticas de proteção de aplicações, veja [Adicionar aplicações ao Microsoft Intune](apps-add.md).

## <a name="create-an-app-protection-policy"></a>Criar uma política de proteção de aplicações
1. No portal do Intune, aceda a **Aplicações do cliente** > **Políticas de proteção de aplicações**. Esta seleção abre o painel **Políticas de proteção de aplicações**, onde pode criar novas políticas e editar as já existentes.
2. Selecione **Criar Política**.

   ![Captura de ecrã do painel "Adicionar uma política"](./media/app-protection-policies/app-protection-add-policy.png)

3. Especifique um nome para a política, adicione uma pequena descrição e selecione o tipo de plataforma para a sua política. Pode criar mais de uma política para cada plataforma.

4. Selecione **Aplicações** para abrir o painel **Aplicações** onde é apresentada uma lista de aplicações disponíveis. Selecione uma ou mais aplicações na lista que pretende associar à política que está a criar. Selecione pelo menos uma aplicação para criar uma política.  

5. Após escolher as aplicações, selecione a opção **Selecionar** para guardar a sua seleção.

6. No painel **Adicionar uma política**, selecione **Configurar definições obrigatórias** para abrir as **Definições**.

   Existem três categorias de definições de política:
   - **Proteção de dados** – este grupo inclui os controlos de prevenção de perda de dados (DLP), como as restrições das operações de cortar, copiar, colar e guardar como. Estas definições determinam como os utilizadores interagem com os dados nas aplicações.
   - **Requisitos de acesso**: este grupo contém as opções de PIN por aplicação que determinam como o utilizador final utiliza as aplicações num contexto de trabalho.  
   - **Iniciação condicional**: este grupo guarda definições como as definições de SO mínimo, de deteção de dispositivos desbloqueados por jailbreak ou rooting e de períodos de tolerância offline.

   Para começar, as definições de política têm valores predefinidos. Se os valores predefinidos cumprirem os seus requisitos, não precisa de fazer alterações.

   > [!TIP]
   > Estas definições de política apenas são impostas quando utilizar aplicações no contexto profissional. Quando os utilizadores finais utilizam a aplicação para realizar uma tarefa pessoal, estes não são afetados por estas políticas. Tenha em atenção que, ao criar um novo ficheiro, este é considerado um ficheiro pessoal. 

7. Selecione **OK** para guardar esta configuração. Está agora novamente no painel **Adicionar uma política**.
8. Selecione **Criar** para criar a política e guardar as suas definições.

As novas políticas que criar não serão implementadas para utilizadores até que o faça manualmente. Para implementar uma política, veja a secção [Implementar uma política para utilizadores](app-protection-policies.md#deploy-a-policy-to-users).

## <a name="deploy-a-policy-to-users"></a>Implementar uma política para utilizadores

1. No painel **Políticas de proteção de aplicações**, selecione uma política.

2. No painel ***Proteção de Aplicações do Intune**, selecione **Atribuições** para abrir o painel **Proteção de Aplicações do Intune – Atribuições**. No separador *Incluir*, clique em **Selecionar grupos para incluir**. 

   ![Captura de ecrã do painel Atribuições com o menu Selecionar grupos a incluir](./media/app-protection-policies/app-protection-policy-add-users.png)

3. É apresentada uma lista de todos os grupos de segurança no seu **Azure Active Directory**. Selecione os grupos de utilizadores aos quais pretende aplicar esta política e, em seguida, clique em **Selecionar**. 

    ![Captura de ecrã do painel Adicionar grupo de utilizadores com a lista de utilizadores do Microsoft Azure AD](./media/app-protection-policies/azure-ad-user-group-list.png)

4. Depois de incluir e excluir grupos, selecione **Guardar** para guardar a configuração e implementar a política para os utilizadores. Se tiver selecionado **Eliminar** antes de guardar a configuração, serão eliminadas todas as alterações feitas nos separadores *Incluir* e *Excluir*.   
 
     ![Captura de ecrã que mostra as opções Guardar e Eliminar](./media/app-protection-policies/save-assignment.png)
  
Acabou de criar uma política e de a implementar para os utilizadores.

Apenas os utilizadores a que foram atribuídas licenças do Microsoft Intune são afetados pela política. Os utilizadores no grupo de segurança selecionado a quem não foi atribuída uma licença do Intune não são afetados.

>[!IMPORTANT]
> Se estiver a utilizar o Intune com o Configuration Manager para gerir os seus dispositivos, a política só é aplicada aos utilizadores diretamente no grupo que selecionou. Os membros dos grupos subordinados aninhados dentro do grupo que selecionou não são afetados.

Os utilizadores finais podem transferir as aplicações a partir da Apple Store ou do Google Play. Para obter mais informações, consulte:
* [O que esperar quando a aplicação Android é gerida por políticas de proteção de aplicações](../fundamentals/end-user-mam-apps-android.md)
* [O que esperar quando a sua aplicação iOS é gerida por políticas de proteção de aplicações](../fundamentals/end-user-mam-apps-ios.md)

## <a name="change-existing-policies"></a>Alterar políticas existentes
Pode editar uma política existente e aplicá-la aos utilizadores visados. No entanto, quando alterar as políticas existentes, os utilizadores que já tiverem sessão iniciada nas aplicações não verão as alterações durante um período de oito horas.

Para ver o efeito das alterações imediatamente, o utilizador final tem de terminar sessão na aplicação e voltar a iniciar sessão.

### <a name="to-change-the-list-of-apps-associated-with-the-policy"></a>Para alterar a lista de aplicações associadas à política

1. No painel **Políticas de proteção de aplicações**, selecione a política que pretende alterar.

2. No painel *Proteção de Aplicações do Intune*, selecione **Aplicações alvo** para abrir a lista de aplicações.

3. Remova ou adicione aplicações a partir da lista e, em seguida, clique no ícone **Guardar** para guardar as alterações.

### <a name="to-change-the-list-of-user-groups"></a>Para alterar a lista de grupos de utilizadores


1. No painel **Políticas de proteção de aplicações**, selecione a política que pretende alterar.

2. No painel *Proteção de Aplicações do Intune*, selecione **Atribuições** para abrir o painel **Proteção de Aplicações do Intune – Atribuições**, que mostra a lista dos grupos de utilizadores que atualmente têm esta política.

3. Para adicionar um novo grupo de utilizadores à política, no separador *Incluir*, selecione **Selecionar grupos para incluir** e selecione o grupo de utilizadores. Escolha **Selecionar** para adicionar o grupo. 

4. Para excluir um grupo de utilizadores, no separador *Excluir*, escolha **Selecionar grupos a excluir** e selecione o grupo de utilizadores. Selecione a opção **Selecionar** para remover o grupo de utilizadores.  

5. Para eliminar grupos que foram adicionados anteriormente, no separador *Incluir* ou *Excluir*, selecione as reticências (...) e, em seguida, **Eliminar**. 

5. Quando tiver concluído as alterações às atribuições, selecione **Guardar** para guardar a configuração e implementar a política para o novo conjunto de utilizadores. Se tiver selecionado **Eliminar** antes de guardar a configuração, serão eliminadas todas as alterações feitas nos separadores *Incluir* e *Excluir*.

### <a name="to-change-policy-settings"></a>Para alterar definições de política

1. No painel **Políticas de proteção de aplicações**, selecione a política que pretende alterar.

2. No painel *Proteção de Aplicações do Intune*, selecione **Propriedades** para abrir a lista de áreas de definições que pode editar. 

3. Selecione a área de definições com as definições que pretende alterar, como **Reposicionamento de dados** ou **Requisitos de acesso**. Em seguida, altere as definições para novos valores.

4. Selecione o ícone **Guardar** para guardar as suas alterações. Repita o processo de selecionar uma área de definições, alterá-la e guardar as alterações até concluir todas as suas alterações. Em seguida, pode abrir o painel *Proteção de Aplicações do Intune – Propriedades*. 

## <a name="target-app-protection-policies-based-on-device-management-state"></a>Aplicar políticas de proteção de aplicações com base no estado de gestão do dispositivo
Em muitas organizações, é comum permitir que os utilizadores finais utilizem os dispositivos geridos pela MDM (Mobile Device Management) no Intune, como os dispositivos que são propriedade da empresa, e os dispositivos não geridos protegidos apenas com as políticas de proteção de aplicações do Intune. Os dispositivos não geridos são normalmente denominados BYOD (Bring Your Own Devices).

Uma vez que as políticas de proteção de aplicações do Intune são direcionadas para a identidade do utilizador, as definições de proteção para um utilizador podem aplicar-se a dispositivos inscritos (geridos pela MDM) e a dispositivos não inscritos (sem gestão pela MDM). Portanto, pode direcionar uma política de proteção de aplicações do Intune para dispositivos iOS e Android inscritos ou não inscritos no Intune. Você pode ter uma política de proteção para dispositivos não gerenciados em que os controles de DLP (prevenção contra perda de dados) estritos estejam em vigor e uma política de proteção separada para dispositivos gerenciados por MDM, em que os controles de DLP podem ser um pouco mais relaxados. Para obter mais informações sobre como isso funciona em dispositivos pessoais Android corporativo, consulte [políticas de proteção de aplicativo e perfis de trabalho](android-deployment-scenarios-app-protection-work-profiles.md).

Para criar estas políticas, navegue até **Aplicações do cliente** > **Políticas de proteção de aplicações** na consola do Intune e selecione **Criar Política**. Também pode editar uma política de proteção de aplicações existente. Para que a política de proteção de aplicações se aplique a dispositivos geridos e não geridos, confirme que a opção **Direcionar para todos os tipos de aplicações** está definida como **Sim**, o valor predefinido. Se quiser atribuir especificamente com base no estado de gestão, defina **Direcionar para todos os tipos de aplicações** para **Não**. 

![Captura de ecrã a mostrar o painel Adicionar uma política com a opção Direcionar para todos os tipos de aplicações](./media/app-protection-policies/app-protection-policies-target-all.png)

### <a name="app-types"></a>Tipos de aplicações

- **Aplicativos em dispositivos não gerenciados**: dispositivos não gerenciados são dispositivos em que o gerenciamento de MDM do Intune não foi detectado. Isso inclui fornecedores de MDM de terceiros.
- **Aplicativos em dispositivos gerenciados pelo Intune**: os dispositivos gerenciados são gerenciados pelo MDM do Intune.
- **Aplicativos no perfil de trabalho do Android**: dispositivos gerenciados que foram registrados como dispositivos de perfil de trabalho do Android Enterprise.

> Observação os dispositivos Android solicitarão a instalação do aplicativo Portal da Empresa do Intune, independentemente do tipo de aplicativo escolhido. Por exemplo, se você selecionar ' aplicativos em dispositivos gerenciados pelo Intune ', os usuários com dispositivos Android não gerenciados ainda serão solicitados.

Para iOS, as definições de configuração de aplicativo adicionais são necessárias para direcionar as configurações de aplicativo (política de proteção de aplicativo) para aplicativos em dispositivos registrados no Intune:

- **IntuneMAMUPN** tem de ser configurado para todas as aplicações geridas pela MDM. Para obter mais informações, veja [Como gerir a transferência de dados entre aplicações iOS no Microsoft Intune](data-transfer-between-apps-manage-ios.md#configure-user-upn-setting-for-microsoft-intune-or-third-party-emm).
- **IntuneMAMDeviceID** tem de ser configurado para todas as aplicações de terceiros e geridas pela LOB MDM. O **IntuneMAMDeviceID** deve ser configurado para o token de ID do dispositivo. Por exemplo, `key=IntuneMAMDeviceID, value={{deviceID}}`. Para obter mais informações, veja [Adicionar políticas de configuração da aplicação para dispositivos iOS geridos](app-configuration-policies-use-ios.md).
- Se apenas o **IntuneMAMDeviceID** for configurado, a aplicação do Intune irá considerar o dispositivo como não gerido.

> [!NOTE]
> Para obter informações de suporte específicas do iOS sobre as políticas de proteção de aplicações com base no estado de gestão dos dispositivos, veja [Políticas de proteção de MAM direcionadas com base no estado de gestão](../fundamentals/whats-new-archive.md#mam-protection-policies-targeted-based-on-management-state-).

## <a name="policy-settings"></a>Definições de política
Para ver uma lista completa das definições de política para iOS e Android, selecione uma das seguintes ligações:

- [Políticas para iOS](app-protection-policy-settings-ios.md)
- [Políticas para Android](app-protection-policy-settings-android.md)

## <a name="next-steps"></a>Próximos passos
[Monitorizar o estado do utilizador e de conformidade](app-protection-policies-monitor.md)

## <a name="see-also"></a>Consulte também
* [O que esperar quando a aplicação Android é gerida por políticas de proteção de aplicações](../fundamentals/end-user-mam-apps-android.md)
* [O que esperar quando a sua aplicação iOS é gerida por políticas de proteção de aplicações](../fundamentals/end-user-mam-apps-ios.md)
