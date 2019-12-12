---
title: Configurar um serviço de gerenciamento de despesas de telecomunicações no Microsoft Intune-Azure | Microsoft Docs
titleSuffix: ''
description: Integre Microsoft Intune com o serviço de gerenciamento de despesas do Saaswedo Telecom para monitorar o uso de dados e definir limites ou limites em dispositivos Android e iOS.
keywords: Saaswedo
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/05/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: b7bf5802-4b65-4aeb-ac99-8e639dd89c2a
ms.reviewer: davidra
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 340659adfa3bbd40f98ccec9d8d44e952f7ec9b9
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/05/2019
ms.locfileid: "74059927"
---
# <a name="set-up-a-telecom-expense-management-service-in-intune"></a>Configurar um serviço de gestão de despesas de telecomunicações no Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Usando o Intune, você pode gerenciar as despesas de telecomunicações do uso de dados em dispositivos móveis de propriedade da organização. O Intune integra-se ao [Gerenciamento de despesas de telecomunicações do Datalert](http://datalert.biz/get-started)da Saaswedo. O Datalert é uma solução de gerenciamento de despesas de telecomunicações em tempo real que gerencia o uso de dados de telecomunicações. Ele pode ajudar a evitar dados dispendiosos e inesperados e encargos de roaming para seus dispositivos gerenciados pelo Intune.

A integração com o Datalert pode definir, monitorar e impor limites de uso de dados em roaming e domésticos. Quando os limites excederem os limites definidos, os alertas serão disparados automaticamente. Você também pode configurar o serviço para aplicar ações diferentes, como desabilitar roaming ou exceder o limite, a indivíduos ou grupos. O console de gerenciamento do Datalert inclui relatórios que mostram o uso de dados e informações de monitoramento.

A imagem a seguir mostra como o Intune se integra ao Datalert:

  ![Diagrama da integração do Intune com o Datalert](./media/telecom-expenses-monitor/tem-datalert-intune-solution-diagram.png)

Para usar o serviço Datalert com o Intune, há algumas definições de configuração no Datalert e no Intune. Este artigo mostra-lhe como:

- Defina as configurações no console do Datalert para conectar o serviço Datalert ao Intune.
- Confirme se essa conexão está ativa e habilitada no Intune.
- Use o Intune para adicionar o aplicativo Datalert a seus dispositivos.
- Desative o serviço Datalert e o Intune (opcional).

## <a name="supported-platforms"></a>Plataformas suportadas

- Android 4,4 e dispositivos mais recentes que são compatíveis com Knox (Samsung)

  As [versões do Android que dão suporte ao Knox](https://seap.samsung.com/faq/what-versions-android-support-knox-standard-and-knox-premium-sdks-0) (abre o site da Samsung) lista as versões com suporte do Knox.

- iOS 8.0 e posterior

## <a name="prerequisites"></a>Pré-requisitos

- Uma assinatura para Microsoft Intune e acesso ao centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431)
- Uma assinatura do [Datalert](http://www.datalert.biz/) (abre o site da Datalert)

## <a name="telecom-expense-management-providers"></a>Provedores de gerenciamento de despesas de telecomunicações

O Intune integra-se com o seguinte provedor de gerenciamento de despesas de telecomunicações:

- [Serviço de gerenciamento de despesas do Saaswedo Datalert Telecom](http://www.datalert.biz/) (abre o site da Datalert)

## <a name="deploy-the-intune-and-datalert-solution"></a>Implantar a solução Intune e Datalert

### <a name="step-1-connect-the-datalert-service-to-intune"></a>Etapa 1: conectar o serviço Datalert ao Intune

1. Entre no console de gerenciamento do Datalert com as credenciais de administrador.

2. No console do, vá para a guia **configurações** > **configuração do MDM**.

3. Selecione **desbloquear**. **Desbloquear** permite que você altere ou atualize as configurações na página.

4. Na **conexão do Intune/Datalert** > **MDM do servidor**, selecione **Microsoft Intune**.

5. Para o **domínio do Azure ad**, insira sua ID de locatário do Azure. Selecione **conexão**.

    Quando você seleciona **conexão**, o serviço Datalert faz check-in com o Intune. Ele confirma que não existem conexões Datalert existentes. Após alguns instantes, uma página de entrada da Microsoft é exibida, seguida pela autenticação do Azure Datalert.

6. Na página de autenticação da Microsoft, selecione **Aceitar**.

    Você é redirecionado para uma página de **agradecimento** Datalert que fecha após alguns instantes. Datalert valida a conexão e mostra as marcas de seleção verdes ao lado dos itens validados. Se a validação falhar, você verá uma mensagem em vermelho. Contate o suporte do Datalert para obter ajuda.

    A imagem a seguir mostra as marcas de seleção verdes quando a conexão é realizada com sucesso:

      ![Página do Datalert a mostrar uma ligação estabelecida com êxito](./media/telecom-expenses-monitor/tem-datalert-connection.png)

7. No **consentimento do aplicativo Datalert/Adal**, defina a opção como **ativado**. Na página de autenticação da Microsoft, selecione **Aceitar**.

    Você é redirecionado para uma página de **agradecimento** Datalert que fecha após alguns instantes. Datalert valida a conexão e mostra as marcas de seleção verdes ao lado dos itens validados. Se a validação falhar, você verá uma mensagem em vermelho. Contate o suporte do Datalert para obter ajuda.

    A imagem a seguir mostra as marcas de seleção verdes quando a conexão é realizada com sucesso:

      ![Página do Datalert a mostrar uma ligação estabelecida com êxito](./media/telecom-expenses-monitor/tem-datalert-adal-consent.png)

8. Em **Gerenciamento de perfis do MDM (opcional)** , defina a opção para **ativado**. Essa configuração permite que o Datalert Leia os perfis disponíveis no Intune para ajudá-lo a configurar políticas. 

    Na página de autenticação da Microsoft, selecione **Aceitar**.

    Você é redirecionado para uma página de **agradecimento** Datalert que fecha após alguns instantes. Datalert valida a conexão e mostra as marcas de seleção verdes ao lado dos itens validados. Se a validação falhar, você verá uma mensagem em vermelho. Contate o suporte do Datalert para obter ajuda.

    A imagem a seguir mostra as marcas de seleção verdes quando a conexão é realizada com sucesso:

   ![Página do Datalert a mostrar uma ligação estabelecida com êxito](./media/telecom-expenses-monitor/tem-datalert-mdm-profiles.png)

### <a name="step-2-confirm-telecom-expense-management-is-active-in-intune"></a>Etapa 2: confirmar se o gerenciamento de despesas de telecomunicações está ativo no Intune

Depois de concluir a etapa 1, sua conexão será habilitada automaticamente. No Intune, o status da conexão mostra **ativo**. Para confirmar se o status está ativo, use as seguintes etapas:

1. Entre no centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Selecione **Administração de locatários** > **conectores e tokens** > **Gerenciamento de despesas de telecomunicações**. Procure o status da conexão **ativa** :

   ![Página do Intune a mostrar o estado de ligação Ativo do Datalert](./media/telecom-expenses-monitor/tem-azure-portal-enable-service.png)

### <a name="step-3-deploy-the-datalert-app-to-devices"></a>Etapa 3: implantar o aplicativo Datalert em dispositivos

Para confirmar se o uso de dados de apenas linhas de propriedade da organização é coletado, certifique-se de:

- Criar categorias de dispositivo no Intune.
- Direcione o aplicativo Datalert somente para telefones organizacionais.

Esta seção lista essas etapas.

#### <a name="create-device-categories-and-device-groups-mapped-to-your-categories"></a>Criar categorias de dispositivo e grupos de dispositivos mapeados para suas categorias

Dependendo das suas necessidades organizacionais, crie pelo menos duas categorias de dispositivo, como corporativa e pessoal. Em seguida, crie grupos de dispositivos dinâmicos para cada categoria. Se necessário, pode criar categorias adicionais para a sua organização.

Para criar categorias de dispositivo no Intune, confira [mapear dispositivos para grupos](../enrollment/device-group-mapping.md).

Essas categorias são mostradas aos usuários durante o registro ([registrar dispositivos Android](../enrollment/android-enroll.md)). Dependendo da categoria que os usuários escolhem, o dispositivo registrado é movido para o grupo de dispositivos correspondente.

  ![Captura de ecrã do painel Adicionar uma política](./media/telecom-expenses-monitor/tem-dynamic-membership-rules.png)

#### <a name="add-the-datalert-app-to-intune"></a>Adicionar o aplicativo Datalert ao Intune

As etapas a seguir adicionam o aplicativo Datalert. Por exemplo, o iOS é usado. [Adicionar aplicativos](../apps/apps-add.md) e [usar marcas de escopo](../fundamentals/scope-tags.md) têm informações mais específicas sobre essas etapas.

1. No [centro de administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), selecione **aplicativos** > **todos os aplicativos** > **Adicionar**.

2. Selecione o **tipo de aplicativo**. Por exemplo, para iOS, selecione **Store app-IOS**.

3. Em **Pesquisar na loja de aplicativos**, digite **Datalert** para localizar o aplicativo Datalert.

4. Escolha o aplicativo **Datalert** > **selecione**:

   ![Adicionar o aplicativo datalert da App Store aos aplicativos cliente do Intune](./media/telecom-expenses-monitor/tem-select-app-from-apple-app-store.png)

5. Insira todas as propriedades adicionais, como as informações do aplicativo e as marcas de escopo:

   ![Insira as propriedades do aplicativo, incluindo o nome, a descrição, escolha o sistema operacional e mais configurações para o aplicativo no Intune](./media/telecom-expenses-monitor/tem-steps-to-create-the-app.png)

6. Selecione **OK** > **Adicionar** para salvar as alterações. O aplicativo Datalert é mostrado na lista.

#### <a name="assign-the-datalert-app-to-the-corporate-device-group"></a>Atribuir a aplicação Datalert ao grupo de dispositivos da empresa

1. Em **aplicativos** > **todos os aplicativos**, selecione o aplicativo Datalert que você adicionou na etapa anterior.

2. Selecione **atribuições** > **Adicionar grupo**. Escolha como o aplicativo é atribuído. [Atribuir aplicativos a grupos no Intune](../apps/apps-deploy.md) tem mais detalhes sobre essas configurações.

    Nestas etapas, você optará por fazer com que a instalação do aplicativo seja necessária ou opcional para o grupo. O exemplo a seguir mostra a instalação conforme necessário. Quando necessário, os usuários devem instalar o aplicativo Datalert depois de registrar seu dispositivo.

   ![Captura de ecrã do painel Adicionar uma política](./media/telecom-expenses-monitor/tem-assign-datalert-app-to-device-group.png)

### <a name="step-4-add-organization-phone-lines-to-the-datalert-console"></a>Etapa 4: adicionar linhas de telefone da organização ao console do Datalert

Os serviços do Intune e do Datalert agora estão configurados para se comunicar entre si. Em seguida, adicione as linhas de telefone pagas da sua organização ao console do Datalert. E insira limites e ações para quaisquer violações de uso de celular ou roaming. Você pode adicionar manualmente linhas telefônicas pagas corporativas ao console do Datalert ou adicioná-las automaticamente depois que o dispositivo for registrado no Intune.

Para definir esses itens, vá para a [configuração do Datalert para Microsoft Intune](http://www.datalert.fr/microsoft-intune/intune-setup) (abre o site da Datalert). Na guia **configurações** , siga as etapas no assistente de instalação.

  ![Captura de ecrã do painel Adicionar uma política](./media/telecom-expenses-monitor/tem-add-phone-lines-to-datalert-console.png)

O serviço Datalert agora está ativo. Ele inicia o monitoramento do uso de dados e desabilita os dados de celular e roaming em dispositivos que excedem os limites de uso configurados.

## <a name="end-user-enrollment"></a>Registro do usuário final

Para a experiência do usuário final, os artigos a seguir podem ajudar:

- [Inscrever o dispositivo iOS na gestão de despesas de telecomunicações](https://docs.microsoft.com/intune-user-help/enroll-your-device-with-telecom-expense-management-ios)
- [Inscrever o dispositivo Android na gestão de despesas de telecomunicações](https://docs.microsoft.com/intune-user-help/enroll-your-device-with-telecom-expense-management-android)

## <a name="turn-off-the-datalert-service"></a>Desligar o serviço Datalert

1. No [centro de administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), selecione **administração de locatário** > **conectores e tokens** > gerenciamento de **despesas de telecomunicações**.
2. Defina **habilitar o gerenciamento de despesas de telecomunicações e bloquear os dados de celular ou roaming em dispositivos que excedem as cotas de uso que você configura** para **desabilitar**.
3. **Guarde** as suas alterações.

> [!IMPORTANT]
> Se você desabilitar o serviço Datalert no Intune:
>
> - Todas as ações que são aplicadas a dispositivos devido a violações passadas dos limites de uso são desfeitas.
> - Os utilizadores deixam de estar bloqueados em relação ao acesso a dados e roaming.
> - O Intune ainda recebe os sinais provenientes do serviço, mas o Intune ignora os sinais.

## <a name="next-steps"></a>Próximos passos

O relatório de uso de dados está disponível no console de gerenciamento do Datalert do Saaswedo.
