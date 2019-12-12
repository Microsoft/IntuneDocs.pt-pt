---
title: Criar e implementar políticas de proteção de aplicações
titleSuffix: Microsoft Intune
description: Este tópico descreve como criar e atribuir políticas de proteção de aplicações (APP) do Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
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
ms.openlocfilehash: 8657b6fa8110b4ea4bbf8ec0841d69197624dd9f
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/05/2019
ms.locfileid: "74563715"
---
# <a name="how-to-create-and-assign-app-protection-policies"></a>Como criar e atribuir políticas de proteção de aplicações

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Saiba como criar e atribuir Microsoft Intune aplicativo (políticas de proteção de aplicativo) para usuários da sua organização. Este tópico também descreve como fazer alterações a políticas existentes.

## <a name="before-you-begin"></a>Antes de começar

As políticas de proteção de aplicações podem ser aplicadas às aplicações em execução nos dispositivos que podem ou não ser geridos pelo Intune. Para obter uma descrição mais detalhada acerca do funcionamento das políticas de proteção de aplicações e dos cenários que são suportados pelas políticas de proteção de aplicações do Intune, veja [O que são políticas de proteção de aplicações do Microsoft Intune?](app-protection-policy.md)

Se estiver a procurar uma lista de MAM com aplicações suportadas, veja as [Listas de aplicações de MAM](https://www.microsoft.com/cloud-platform/microsoft-intune-apps).

Para obter mais informações sobre como adicionar as aplicações de linha de negócio (LOB) da sua organização ao Microsoft Intune, para se preparar para as políticas de proteção de aplicações, veja [Adicionar aplicações ao Microsoft Intune](apps-add.md).

## <a name="app-protection-policies-for-iosipados-and-android-apps"></a>Políticas de proteção de aplicativo para aplicativos iOS/iPadOS e Android

Quando você cria uma política de proteção de aplicativo para aplicativos iOS/iPadOS e Android, segue um fluxo de processo moderno do Intune que resulta em uma nova política de proteção de aplicativo.

### <a name="create-an-iosipados-or-android-app-protection-policy"></a>Criar uma política de proteção de aplicativo iOS/iPadOS ou Android
1. Entre no centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. No portal do Intune, escolha **aplicativos** > **políticas de proteção de aplicativo**. Esta seleção abre o painel **Políticas de proteção de aplicações**, onde pode criar novas políticas e editar as já existentes.
3. Selecione **criar política** e selecione **Ios/iPadOS** ou **Android**. O painel **criar política** é exibido.
4. Na página **noções básicas** , adicione os seguintes valores:

    | Valor | Description |
    |--------------|------------------------------------------------|
    | Nome | O nome desta política de proteção de aplicativo. |
    | Description | Adicional A descrição desta política de proteção de aplicativo. |


    O valor da **plataforma** é definido com base na sua escolha acima.

    ![Captura de tela da página noções básicas do painel criar política](~/apps/media/app-protection-policies/app-protection-add-policies-01.png)

5. Clique em **Avançar** para exibir a página de **aplicativos** .<br>
    A página **aplicativos** permite que você escolha como deseja aplicar essa política a aplicativos em diferentes dispositivos. Você deve adicionar pelo menos um aplicativo.<p>
    
    | Valor/opção | Description |
    |-------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | Direcionar para aplicativos em todos os tipos de dispositivos | Use esta opção para direcionar sua política para aplicativos em dispositivos de qualquer estado de gerenciamento. Escolha **não** para direcionar aplicativos em tipos de dispositivos específicos. Para obter informações, consulte [políticas de proteção de aplicativo de destino com base no estado do gerenciamento de dispositivos](#target-app-protection-policies-based-on-device-management-state) |
    |     Tipos de dispositivo | Use esta opção para especificar se essa política se aplica a dispositivos gerenciados ou dispositivos não gerenciados do MDM. Para as políticas de aplicativo iOS, selecione de dispositivos não **gerenciados** e **gerenciáveis** . Para políticas de aplicativo Android, selecione de **não gerenciado**, **administrador de dispositivo Android**e **Android Enterprise**.  |
    | Aplicações públicas | Clique em **selecionar aplicativos públicos** para escolher os aplicativos a serem direcionados. |
    | Aplicativos personalizados | Clique em **selecionar aplicativos personalizados** para selecionar aplicativos personalizados para direcionar com base em uma ID de pacote. |
    
    Os aplicativos que você selecionou aparecerão na lista de aplicativos públicos e personalizados. 
6. Clique em **Avançar** para exibir a página **proteção de dados** .<br>
    Esta página fornece configurações para controles DLP (prevenção contra perda de dados), incluindo restrições de recortar, copiar, colar e salvar como. Essas configurações determinam como os usuários interagem com os dados nos aplicativos que essa política de proteção de aplicativo aplica.

    **Configurações de proteção de dados**:<br>
    - **proteção de dados Ios/iPadOS** -para obter informações, consulte [configurações de política de proteção de aplicativo IOS – proteção de dados](~/apps/app-protection-policy-settings-ios.md#data-protection).
    - **Proteção de dados do Android** -para obter informações, consulte [configurações de política de proteção de aplicativo Android – proteção de dados](~/apps/app-protection-policy-settings-android.md#data-protection).

7. Clique em **Avançar** para exibir a página **requisitos de acesso** .<br>
    Esta página fornece configurações para permitir que você configure os requisitos de PIN e credenciais que os usuários devem atender para acessar aplicativos em um contexto de trabalho. 
 
    **Configurações de requisitos de acesso**:<br>
    - **requisitos de acesso do IOS/iPadOS** -para obter informações, consulte [configurações de política de proteção de aplicativo IOS-requisitos de acesso](~/apps/app-protection-policy-settings-ios.md#access-requirements).
    - **Requisitos de acesso do Android** -para obter informações, consulte [configurações de política de proteção de aplicativo Android – requisitos de acesso](~/apps/app-protection-policy-settings-android.md#access-requirements).

8. Clique em **Avançar** para exibir a página de **inicialização condicional** .<br>
    Esta página fornece configurações para definir os requisitos de segurança de entrada para sua política de proteção de aplicativo. Selecione uma **Definição** e introduza o **Valor** que os utilizadores têm de cumprir para iniciar sessão na sua aplicação da empresa. Em seguida, selecione a **ação** que você deseja executar se os usuários não atenderem às suas necessidades. Em alguns casos, é possível configurar múltiplas ações para uma única definição.

    **Configurações de inicialização condicional**:<br>
    - **inicialização condicional de Ios/iPadOS** -para obter informações, consulte [configurações de política de proteção de aplicativo IOS – inicialização condicional](~/apps/app-protection-policy-settings-ios.md#conditional-launch).
    - **Inicialização condicional do Android** -para obter informações, consulte [configurações de política de proteção de aplicativo do Android – inicialização condicional](~/apps/app-protection-policy-settings-android.md#conditional-launch).

9. Clique em **Avançar** para exibir a página **atribuições** .<br>
   A página **atribuições** permite atribuir a política de proteção de aplicativo a grupos de usuários.
   
    >[!IMPORTANT]
    > Se estiver a utilizar o Intune com o Configuration Manager para gerir os seus dispositivos, a política só é aplicada aos utilizadores diretamente no grupo que selecionou. Os membros dos grupos subordinados aninhados dentro do grupo que selecionou não são afetados.

10. Clique em **Avançar: examinar + criar** para revisar os valores e as configurações que você inseriu para essa política de proteção de aplicativo.

11. Quando terminar, clique em **criar** para criar a política de proteção de aplicativo no Intune. 

    > [!TIP]
    > Estas definições de política apenas são impostas quando utilizar aplicações no contexto profissional. Quando os utilizadores finais utilizam a aplicação para realizar uma tarefa pessoal, estes não são afetados por estas políticas. Tenha em atenção que, ao criar um novo ficheiro, este é considerado um ficheiro pessoal. 

Os utilizadores finais podem transferir as aplicações a partir da Apple Store ou do Google Play. Para obter mais informações, consulte:
* [O que esperar quando a aplicação Android é gerida por políticas de proteção de aplicações](../fundamentals/end-user-mam-apps-android.md)
* [O que esperar quando a sua aplicação iOS é gerida por políticas de proteção de aplicações](../fundamentals/end-user-mam-apps-ios.md)

## <a name="change-existing-policies"></a>Alterar políticas existentes
Pode editar uma política existente e aplicá-la aos utilizadores visados. No entanto, quando alterar as políticas existentes, os utilizadores que já tiverem sessão iniciada nas aplicações não verão as alterações durante um período de oito horas.

Para ver o efeito das alterações imediatamente, o utilizador final tem de terminar sessão na aplicação e voltar a iniciar sessão.

### <a name="to-change-the-list-of-apps-associated-with-the-policy"></a>Para alterar a lista de aplicações associadas à política

1. No painel **Políticas de proteção de aplicações**, selecione a política que pretende alterar.

2. No painel *proteção de aplicativo do Intune* , selecione **Propriedades**.

3. Ao lado da seção intitulada *aplicativos*, selecione **Editar**.

4. A página **aplicativos** permite que você escolha como deseja aplicar essa política a aplicativos em diferentes dispositivos. Você deve adicionar pelo menos um aplicativo.<p>
    
    | Valor/opção | Description |
    |-------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | Direcionar para aplicativos em todos os tipos de dispositivos | Use esta opção para direcionar sua política para aplicativos em dispositivos de qualquer estado de gerenciamento. Escolha **não** para direcionar aplicativos em tipos de dispositivos específicos. Para obter informações, consulte [políticas de proteção de aplicativo de destino com base no estado do gerenciamento de dispositivos](#target-app-protection-policies-based-on-device-management-state) |
    |     Tipos de dispositivo | Use esta opção para especificar se essa política se aplica a dispositivos gerenciados ou dispositivos não gerenciados do MDM. Para as políticas de aplicativo iOS, selecione de dispositivos não **gerenciados** e **gerenciáveis** . Para políticas de aplicativo Android, selecione de **não gerenciado**, **administrador de dispositivo Android**e **Android Enterprise**.  |
    | Aplicações públicas | Clique em **selecionar aplicativos públicos** para escolher os aplicativos a serem direcionados. |
    | Aplicativos personalizados | Clique em **selecionar aplicativos personalizados** para selecionar aplicativos personalizados para direcionar com base em uma ID de pacote. |

    Os aplicativos que você selecionou aparecerão na lista de aplicativos públicos e personalizados. 

5. Clique em **examinar + criar** para examinar os aplicativos selecionados para esta política.

6. Quando terminar, clique em **salvar** para atualizar a política de proteção de aplicativo.
 
#### <a name="to-change-the-list-of-user-groups"></a>Para alterar a lista de grupos de utilizadores

1. No painel **Políticas de proteção de aplicações**, selecione a política que pretende alterar.

2. No painel *proteção de aplicativo do Intune* , selecione **Propriedades**.

3. Ao lado da seção intitulada *atribuições*, selecione **Editar**.

4. Para adicionar um novo grupo de utilizadores à política, no separador *Incluir*, selecione **Selecionar grupos para incluir** e selecione o grupo de utilizadores. Escolha **Selecionar** para adicionar o grupo. 

5. Para excluir um grupo de utilizadores, no separador *Excluir*, escolha **Selecionar grupos a excluir** e selecione o grupo de utilizadores. Selecione a opção **Selecionar** para remover o grupo de utilizadores.  

6. Para eliminar grupos que foram adicionados anteriormente, no separador *Incluir* ou *Excluir*, selecione as reticências (...) e, em seguida, **Eliminar**.

7. Clique em **examinar + criar** para examinar os grupos de usuários selecionados para esta política.

8. Quando tiver concluído as alterações às atribuições, selecione **Guardar** para guardar a configuração e implementar a política para o novo conjunto de utilizadores. Se você selecionar **Cancelar** antes de salvar sua configuração, descartará todas as alterações feitas nas guias *incluir* e *excluir* .

### <a name="to-change-policy-settings"></a>Para alterar definições de política

1. No painel **Políticas de proteção de aplicações**, selecione a política que pretende alterar.

2. No painel *proteção de aplicativo do Intune* , selecione **Propriedades**.

3. Ao lado da seção correspondente às configurações que você deseja alterar, selecione **Editar**. Em seguida, altere as definições para novos valores.

7. Clique em **examinar + criar** para examinar as configurações atualizadas para esta política.

4. Selecione **salvar** para salvar as alterações. Repita o processo de selecionar uma área de definições, alterá-la e guardar as alterações até concluir todas as suas alterações. Em seguida, pode abrir o painel *Proteção de Aplicações do Intune – Propriedades*. 

## <a name="target-app-protection-policies-based-on-device-management-state"></a>Aplicar políticas de proteção de aplicações com base no estado de gestão do dispositivo
Em muitas organizações, é comum permitir que os utilizadores finais utilizem os dispositivos geridos pela MDM (Mobile Device Management) no Intune, como os dispositivos que são propriedade da empresa, e os dispositivos não geridos protegidos apenas com as políticas de proteção de aplicações do Intune. Os dispositivos não geridos são normalmente denominados BYOD (Bring Your Own Devices).

Uma vez que as políticas de proteção de aplicações do Intune são direcionadas para a identidade do utilizador, as definições de proteção para um utilizador podem aplicar-se a dispositivos inscritos (geridos pela MDM) e a dispositivos não inscritos (sem gestão pela MDM). Portanto, pode direcionar uma política de proteção de aplicações do Intune para dispositivos iOS e Android inscritos ou não inscritos no Intune. Você pode ter uma política de proteção para dispositivos não gerenciados em que os controles de DLP (prevenção contra perda de dados) estritos estejam em vigor e uma política de proteção separada para dispositivos gerenciados por MDM, em que os controles de DLP podem ser um pouco mais relaxados. Para obter mais informações sobre como isso funciona em dispositivos pessoais Android Enterprise, consulte [políticas de proteção de aplicativo e perfis de trabalho](android-deployment-scenarios-app-protection-work-profiles.md).

Para criar essas políticas, navegue até **aplicativos** > **políticas de proteção de aplicativo** no console do Intune e, em seguida, selecione **criar política**. Também pode editar uma política de proteção de aplicações existente. Para que a política de proteção do aplicativo se aplique a dispositivos gerenciados e não gerenciados, navegue até a página de **aplicativos** e confirme se o **destino para aplicativos em todos os tipos de dispositivos** está definido como **Sim**, o valor padrão. Se você quiser atribuir de maneira granular com base no estado de gerenciamento, defina **destino como aplicativos em todos os tipos de dispositivo** como **não**. 

### <a name="device-types"></a>Tipos de dispositivo

- Não **gerenciado**: dispositivos não gerenciados são dispositivos nos quais o gerenciamento de MDM do Intune não foi detectado. Isso inclui dispositivos gerenciados por fornecedores de MDM de terceiros.
- **Dispositivos gerenciados pelo Intune**: os dispositivos gerenciados são gerenciados pelo MDM do Intune.
- **Administrador de dispositivo Android**: dispositivos gerenciados pelo Intune usando a API de administração de dispositivo Android.
- **Android Enterprise**: dispositivos gerenciados pelo Intune usando perfis de trabalho do Android Enterprise ou gerenciamento de dispositivo completo do Android Enterprise.

> [!NOTE]
> Os dispositivos Android solicitarão a instalação do aplicativo Portal da Empresa do Intune, independentemente do tipo de dispositivo escolhido. Por exemplo, se você selecionar "Android Enterprise", os usuários com dispositivos Android não gerenciados ainda serão solicitados.

Para iOS, as definições de configuração de aplicativo adicionais são necessárias para direcionar as configurações de aplicativo (política de proteção de aplicativo) para aplicativos em dispositivos registrados no Intune:

- **IntuneMAMUPN** tem de ser configurado para todas as aplicações geridas pela MDM. Para obter mais informações, veja [Como gerir a transferência de dados entre aplicações iOS no Microsoft Intune](data-transfer-between-apps-manage-ios.md#configure-user-upn-setting-for-microsoft-intune-or-third-party-emm).
- O **IntuneMAMDeviceID** deve ser configurado para todos os aplicativos gerenciados de MDM de linha de negócios e de terceiros. O **IntuneMAMDeviceID** deve ser configurado para o token de ID do dispositivo. Por exemplo, `key=IntuneMAMDeviceID, value={{deviceID}}`. Para obter mais informações, veja [Adicionar políticas de configuração da aplicação para dispositivos iOS geridos](app-configuration-policies-use-ios.md).
- Se apenas o **IntuneMAMDeviceID** for configurado, a aplicação do Intune irá considerar o dispositivo como não gerido.

> [!NOTE]
> Para obter informações de suporte específicas do iOS sobre as políticas de proteção de aplicações com base no estado de gestão dos dispositivos, veja [Políticas de proteção de MAM direcionadas com base no estado de gestão](../fundamentals/whats-new-archive.md#mam-protection-policies-targeted-based-on-management-state).

## <a name="policy-settings"></a>Definições de política
Para ver uma lista completa das definições de política para iOS e Android, selecione uma das seguintes ligações:

- [Políticas para iOS](app-protection-policy-settings-ios.md)
- [Políticas para Android](app-protection-policy-settings-android.md)

## <a name="next-steps"></a>Próximos passos
[Monitorizar o estado do utilizador e de conformidade](app-protection-policies-monitor.md)

## <a name="see-also"></a>Consulte também
* [O que esperar quando a aplicação Android é gerida por políticas de proteção de aplicações](../fundamentals/end-user-mam-apps-android.md)
* [O que esperar quando a sua aplicação iOS é gerida por políticas de proteção de aplicações](../fundamentals/end-user-mam-apps-ios.md)
