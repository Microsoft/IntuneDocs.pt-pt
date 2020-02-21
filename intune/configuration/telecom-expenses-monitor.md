---
title: Criar um serviço de gestão de despesas de telecomunicações na Microsoft Intune - Azure Microsoft Docs
titleSuffix: ''
description: Integre o Microsoft Intune com o serviço de gestão de despesas de telecomunicações Saaswedo para monitorizar a utilização de dados e definir limiares ou limites em dispositivos Android, iOS e iPadOS.
keywords: Saaswedo
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/18/2020
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
ms.openlocfilehash: e6c4d08d1010654a16e13981a0d3353b2418524a
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/20/2020
ms.locfileid: "77512879"
---
# <a name="set-up-a-telecom-expense-management-service-in-intune"></a>Configurar um serviço de gestão de despesas de telecomunicações no Intune

Utilizando o Intune, pode gerir as despesas de telecomunicações a partir do uso de dados em dispositivos móveis propriedade da organização. Intune integra-se com a gestão das despesas de [telecomunicações Datalert](http://datalert.biz/get-started)da Saaswedo. A Datalert é uma solução de gestão de despesas de telecomunicações em tempo real que gere o uso de dados de telecomunicações. Pode ajudar a evitar dados dispendiosos e inesperados e taxas de roaming para os seus dispositivos geridos pelo Intune.

A integração com o Datalert pode definir, monitorizar e impor limites de roaming e utilização de dados domésticos. Quando os limites excedem os seus limiares definidos, os alertas são automaticamente acionados. Também pode configurar o serviço para aplicar diferentes ações, tais como desativar o roaming ou exceder o limiar, a indivíduos ou grupos. A consola de gestão Datalert inclui relatórios que mostram a utilização de dados e informações de monitorização.

A imagem que se segue mostra como intune se integra com Datalert:

  ![Diagrama da integração do Intune com o Datalert](./media/telecom-expenses-monitor/tem-datalert-intune-solution-diagram.png)

Para utilizar o serviço Datalert com Intune, existem algumas definições de configuração em Datalert e Intune. Este artigo mostra-lhe como:

- Configure as definições na consola Datalert para ligar o serviço Datalert ao Intune.
- Confirme que esta ligação está ativa e ativada no Intune.
- Utilize o Intune para adicionar a aplicação Datalert aos seus dispositivos.
- Desligue o serviço Datalert e para Intune (opcional).

## <a name="supported-platforms"></a>Plataformas suportadas

- Android 4.4 e dispositivos mais recentes que são capazes de Knox (Samsung)

  [As versões Android que suportam o Knox](https://seap.samsung.com/faq/what-versions-android-support-knox-standard-and-knox-premium-sdks-0) (abre o site da Samsung) listam as versões suportadas pelo Knox.

- iOS 8.0 e mais recente
- iPadOS 13.0 e mais recente

## <a name="prerequisites"></a>Pré-requisitos

- Uma subscrição do Microsoft Intune e acesso ao centro de administração do [Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431)
- Uma subscrição da [Datalert](http://www.datalert.biz/) (abre o site da Datalert)

## <a name="telecom-expense-management-providers"></a>Prestadores de gestão de despesas de telecomunicações

Intune integra-se com o seguinte prestador de gestão de despesas de telecomunicações:

- Serviço de gestão de despesas de [telecomunicações Saaswedo Datalert](http://www.datalert.biz/) (abre o site da Datalert)

## <a name="deploy-the-intune-and-datalert-solution"></a>Implementar a solução Intune e Datalert

### <a name="step-1-connect-the-datalert-service-to-intune"></a>Passo 1: Ligue o serviço Datalert ao Intune

1. Inscreva-se na consola de gestão Datalert com credenciais de administrador.

2. Na consola, vá ao separador **Definições** > **MDM**.

3. Selecione **Desbloquear**. Desbloquear o **desbloqueio** permite-lhe alterar ou atualizar as definições na página.

4. Intune **/ Datalert Connection** > **Server MDM,** selecione **Microsoft Intune**.

5. Para **o domínio Azure AD,** insira a sua identificação de inquilino Azure. Selecione **Ligação**.

    Quando selecionar **Ligação,** o serviço Datalert faz o check-in com o Intune. Confirma que não existem ligações da Talert existentes. Após alguns momentos, aparece um sinal da Microsoft na página, seguido da autenticação Datalert Azure.

6. Na página de autenticação da Microsoft, selecione **Aceitar**.

    És redirecionado para uma página de **agradecimento** da Datalert que fecha depois de alguns momentos. Datalert valida a ligação e mostra marcas de verificação verdes ao lado dos itens que validaram. Se a validação falhar, verá uma mensagem a vermelho. Contacte o suporte da Datalert para obter ajuda.

    A imagem que se segue mostra as marcas de verificação verde quando a ligação é bem sucedida:

      ![Página do Datalert a mostrar uma ligação estabelecida com êxito](./media/telecom-expenses-monitor/tem-datalert-connection.png)

7. Na **Aplicação Datalert / Consentimento ADAL,** desloque o interruptor para **Ligar**. Na página de autenticação da Microsoft, selecione **Aceitar**.

    És redirecionado para uma página de **agradecimento** da Datalert que fecha depois de alguns momentos. Datalert valida a ligação e mostra marcas de verificação verdes ao lado dos itens que validaram. Se a validação falhar, verá uma mensagem a vermelho. Contacte o suporte da Datalert para obter ajuda.

    A imagem que se segue mostra as marcas de verificação verde quando a ligação é bem sucedida:

      ![Página do Datalert a mostrar uma ligação estabelecida com êxito](./media/telecom-expenses-monitor/tem-datalert-adal-consent.png)

8. Na **gestão de perfis do MDM (opcional),** desloque o interruptor para **Ligar**. Esta definição permite que o Datalert leia os perfis disponíveis em Intune para ajudá-lo a configurar políticas. 

    Na página de autenticação da Microsoft, selecione **Aceitar**.

    És redirecionado para uma página de **agradecimento** da Datalert que fecha depois de alguns momentos. Datalert valida a ligação e mostra marcas de verificação verdes ao lado dos itens que validaram. Se a validação falhar, verá uma mensagem a vermelho. Contacte o suporte da Datalert para obter ajuda.

    A imagem que se segue mostra as marcas de verificação verde quando a ligação é bem sucedida:

   ![Página do Datalert a mostrar uma ligação estabelecida com êxito](./media/telecom-expenses-monitor/tem-datalert-mdm-profiles.png)

### <a name="step-2-confirm-telecom-expense-management-is-active-in-intune"></a>Passo 2: Confirmar que a gestão das despesas das telecomunicações está ativa em Intune

Depois de completar o Passo 1, a sua ligação está ativada automaticamente. Em Intune, o estado de ligação mostra **Ativo**. Para confirmar que o estado está ativo, utilize os seguintes passos:

1. Inscreva-se no centro de administração do [Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Selecione **a administração do Inquilino** > **Conectores e fichas** > **Gestão de Despesas de Telecomunicações.** Procure o estado de ligação **Ativa:**

   ![Página do Intune a mostrar o estado de ligação Ativo do Datalert](./media/telecom-expenses-monitor/tem-azure-portal-enable-service.png)

### <a name="step-3-deploy-the-datalert-app-to-devices"></a>Passo 3: Implementar a app Datalert para dispositivos

Para confirmar que o uso de dados a partir de apenas linhas pertencentes à organização é recolhido, certifique-se de:

- Crie categorias de dispositivos em Intune.
- Direcione a aplicação Datalert apenas para telefones organizacionais.

Esta secção lista estes passos.

#### <a name="create-device-categories-and-device-groups-mapped-to-your-categories"></a>Crie categorias de dispositivos e grupos de dispositivos mapeados para as suas categorias

Dependendo das suas necessidades organizacionais, crie pelo menos duas categorias de dispositivos, como Corporate e Personal. Em seguida, crie grupos de dispositivos dinâmicos para cada categoria. Se necessário, pode criar categorias adicionais para a sua organização.

Para criar categorias de dispositivos em Intune, consulte [os dispositivos de mapa para grupos](../enrollment/device-group-mapping.md).

Estas categorias são mostradas aos utilizadores durante a inscrição[(matricular dispositivos Android).](../enrollment/android-enroll.md) Dependendo da categoria que os utilizadores escolherem, o dispositivo matriculado é transferido para o grupo de dispositivos correspondente.

  ![Captura de ecrã do painel Adicionar uma política](./media/telecom-expenses-monitor/tem-dynamic-membership-rules.png)

#### <a name="add-the-datalert-app-to-intune"></a>Adicione a app Datalert ao Intune

Os seguintes passos adicionam a aplicação Datalert. Como exemplo, é utilizado o iOS/iPadOS. [Adicione aplicativos](../apps/apps-add.md) e [use tags](../fundamentals/scope-tags.md) de âmbito têm informações mais específicas sobre estes passos.

1. No centro de administração do [Microsoft Endpoint Manager,](https://go.microsoft.com/fwlink/?linkid=2109431)selecione **Apps** > Todas **as aplicações** > **Add**.

2. Selecione o seu **tipo de app**. Por exemplo, para iOS/iPadOS, selecione **App de loja - iOS/iPadOS**.

3. Em **Search the App Store**, escreva **Datalert** para encontrar a aplicação Datalert.

4. Escolha a app **Datalert** > **Selecione:**

   ![Adicione a app datalert da loja de aplicações às aplicações do cliente Intune](./media/telecom-expenses-monitor/tem-select-app-from-apple-app-store.png)

5. Insira quaisquer propriedades adicionais, tais como informações de aplicações e etiquetas de âmbito:

   ![Insira as propriedades da aplicação, incluindo o nome, descrição, escolha o S, e mais configurações para a app em Intune](./media/telecom-expenses-monitor/tem-steps-to-create-the-app.png)

6. Selecione **OK** > **Adicionar** para guardar as suas alterações. A aplicação Datalert está na lista.

#### <a name="assign-the-datalert-app-to-the-corporate-device-group"></a>Atribuir a aplicação Datalert ao grupo de dispositivos da empresa

1. Em **Apps** > **Todas as aplicações**, selecione a aplicação Datalert que adicionou no passo anterior.

2. Selecione **Atribuições** > **Adicionar grupo**. Escolha como a aplicação é atribuída. [Atribuir aplicativos a grupos em Intune](../apps/apps-deploy.md) tem mais detalhes sobre estas configurações.

    Nestes passos, optará por tornar a instalação da aplicação necessária ou opcional para o grupo. O exemplo seguinte mostra a instalação conforme necessário. Quando necessário, os utilizadores devem instalar a aplicação Datalert depois de matricularem o seu dispositivo.

   ![Captura de ecrã do painel Adicionar uma política](./media/telecom-expenses-monitor/tem-assign-datalert-app-to-device-group.png)

### <a name="step-4-add-organization-phone-lines-to-the-datalert-console"></a>Passo 4: Adicionar linhas telefónicas da organização à consola Datalert

Os serviços Intune e Datalert estão agora configurados para comunicar uns com os outros. Em seguida, adicione as linhas telefónicas pagas da sua organização à consola Datalert. E, insira limiares e ações para quaisquer violações de uso celular ou de roaming. Pode adicionar manualmente linhas telefónicas pagas corporativas à consola Datalert ou adicioná-las automaticamente depois de o dispositivo estar matriculado no Intune.

Para definir estes itens, vá à [configuração da Datalert para](http://www.datalert.fr/microsoft-intune/intune-setup) o Microsoft Intune (abre o site da Datalert). Sob o separador **Definições,** siga os passos do assistente de configuração.

  ![Captura de ecrã do painel Adicionar uma política](./media/telecom-expenses-monitor/tem-add-phone-lines-to-datalert-console.png)

O serviço Datalert está agora ativo. Começa a monitorizar o uso de dados e a desativar dados celulares e de roaming em dispositivos que excedem os limites de utilização configurados.

## <a name="end-user-enrollment"></a>Inscrição do utilizador final

Para a experiência do utilizador final, os seguintes artigos podem ajudar:

- [Inscreva o seu dispositivo iOS/iPadOS na gestão de despesas de telecomunicações](https://docs.microsoft.com/intune-user-help/enroll-your-device-with-telecom-expense-management-ios)
- [Inscrever o dispositivo Android na gestão de despesas de telecomunicações](https://docs.microsoft.com/intune-user-help/enroll-your-device-with-telecom-expense-management-android)

## <a name="turn-off-the-datalert-service"></a>Desligue o serviço Datalert

1. No centro de administração do [Microsoft Endpoint Manager,](https://go.microsoft.com/fwlink/?linkid=2109431)selecione a **administração do Inquilino** > **Conectores e fichas** > Gestão de Despesas de **Telecomunicações.**
2. Configurar **a Gestão de Despesas de Telecomunicações e bloquear dados celulares ou de roaming em dispositivos que excedam as quotas** de utilização que configura para **desativar**.
3. **Guarde** as suas alterações.

> [!IMPORTANT]
> Se desativar o serviço Datalert em Intune:
>
> - Todas as ações que são aplicadas aos dispositivos devido a violações passadas dos limites de utilização, são desfeitas.
> - Os utilizadores deixam de estar bloqueados em relação ao acesso a dados e roaming.
> - Intune ainda recebe os sinais vindos do serviço, mas Intune ignora os sinais.

## <a name="next-steps"></a>Próximos passos

O relatório de utilização de dados está disponível na consola de gestão Datalert da Saaswedo.
