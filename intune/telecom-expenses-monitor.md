---
title: Configurar um serviço de gestão de despesas de telecomunicações
titleSuffix: Microsoft Intune
description: Integre o Intune com o serviço de gestão de despesas de telecomunicações Saaswedo.
keywords: Saaswedo
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/28/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: b7bf5802-4b65-4aeb-ac99-8e639dd89c2a
ms.reviewer: sumitp
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4400688c727ca9c81b0c5662087623d64bdb07db
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/02/2019
ms.locfileid: "57238273"
---
# <a name="set-up-a-telecom-expense-management-service-in-intune"></a>Configurar um serviço de gestão de despesas de telecomunicações no Intune
[!INCLUDE [azure_portal](./includes/azure_portal.md)]

O Intune permite-lhe gerir as despesas de telecomunicações decorrentes da utilização de dados em dispositivos móveis da empresa. Para ativar esta funcionalidade, o Intune integrou-se com a solução de [gestão de despesas de telecomunicações Datalert](http://datalert.biz/get-started), do programador de software de terceiros Saaswedo. O Datalert é um software de gestão de despesas de telecomunicações que lhe permite gerir a utilização de dados de telecomunicações. Ajuda a evitar utilizações excedidas de roaming e dados dispendiosas e imprevistas dos seus dispositivos geridos pelo Intune.

A integração do Intune com o Datalert permite-lhe configurar, monitorizar e impor centralmente limites de utilização de dados nacionais e de roaming. São acionados alertas automatizados quando os limites excedem os limiares definidos. Pode configurar o serviço para aplicar medidas diferentes a indivíduos ou grupos de utilizadores finais (por exemplo, a desativação do roaming ou a ultrapassagem do limiar). Na consola de gestão Datalert poderá encontrar relatórios que disponibilizam informações de monitorização e de utilização de dados.

O seguinte diagrama ilustra a forma como o Intune se integra com o Datalert.

  ![Diagrama da integração do Intune com o Datalert](./media/tem-datalert-intune-solution-diagram.png)

Para poder utilizar o serviço Datalert com o Intune, tem de configurar as definições na consola Datalert e no Intune. A ligação tem de ser ativada para o serviço Datalert e para o Intune. Se o lado da ligação do Datalert estiver ativado, mas o lado do Intune não, o Intune recebe a comunicação, mas ignora-a.

## <a name="supported-platforms"></a>Plataformas suportadas

- Samsung Knox
- iOS 8.0 e posterior

## <a name="prerequisites"></a>Pré-requisitos

- Uma subscrição do Microsoft Intune e acesso ao portal do Azure.
- Uma subscrição do serviço de gestão de despesas de telecomunicações Datalert

## <a name="list-of-telecom-expense-management-providers"></a>Lista de fornecedores de gestão de despesas de telecomunicações

Atualmente, o Intune integra-se com os seguintes fornecedores de gestão de despesas de telecomunicações:

[Serviço de gestão de despesas de telecomunicações Datalert da Saaswedo](http://www.datalert.biz/)

## <a name="deploy-the-intune-and-datalert-integrated-solution"></a>Implementar a solução integrada do Intune com o Datalert

Antes de começar, certifique-se de que já possui uma subscrição do serviço de gestão de despesas de telecomunicações do Intune e do Datalert.

### <a name="step-1-connect-the-datalert-service-to-microsoft-intune"></a>Passo 1: Ligar o serviço Datalert ao Microsoft Intune

1. Inicie sessão na consola de gestão do Datalert com as suas credenciais de administrador.

2. Na consola de gestão do Datalert, aceda ao separador **Settings (Definições)** e, em seguida, **MDM configuration (Configuração de MDM)**.

3. Selecione **Unblock (Desbloquear)** na parte inferior da página, que lhe permite modificar as definições na página.

4. Na secção **Intune / Datalert Connection (Ligação Intune/Datalert)**, selecione **Microsoft Intune** para **Server MDM (Servidor de MDM)**.    

5. Para **Azure AD domain (Domínio do Azure AD)**, introduza o ID de inquilino do Azure e, em seguida, selecione **Connection (Ligação)**.

    Ao selecionar **Connection (Ligação)**, o serviço Datalert consulta o Intune para garantir que não existem ligações prévias do Datalert com o Intune. Alguns segundos depois, é apresentada a página de início de sessão da Microsoft, seguida da autenticação do Datalert no Azure.

6. Na página de autenticação da Microsoft, selecione **Aceitar**. É redirecionado para uma página de **Obrigado** do Datalert, que se fecha alguns segundos depois. O Datalert valida a ligação e apresenta marcas de verificação verdes junto a uma lista de itens que validou. Se a validação falhar, verá uma mensagem a vermelho e deverá contactar o Suporte do Datalert para obter ajuda.

    A seguinte captura de ecrã mostra as marcas de verificação verdes que deverão ser apresentadas assim que a ligação for estabelecida com êxito.

   ![Página do Datalert a mostrar uma ligação estabelecida com êxito](./media/tem-datalert-connection.png)

7. Na secção **Datalert App/ADAL Consent** (Consentimento da Aplicação Datalert/ADAL), defina o botão para **On (Ligado)**. Na página de autenticação da Microsoft, selecione **Aceitar**. É redirecionado para uma página de **Obrigado** do Datalert, que se fecha alguns segundos depois. O Datalert valida a ligação e apresenta marcas de verificação verdes junto a uma lista de itens que validou. Se a validação falhar, verá uma mensagem a vermelho e deverá contactar o Suporte do Datalert para obter ajuda.    

    A seguinte captura de ecrã mostra as marcas de verificação verdes que deverão ser apresentadas assim que a ligação for estabelecida com êxito.

   ![Página do Datalert a mostrar uma ligação estabelecida com êxito](./media/tem-datalert-adal-consent.png)

8. Na secção **MDM Profiles management (optional) (Gestão de Perfis MDM [opcional])**, defina o botão para **On (Ligado)** para permitir que o Datalert consulte os perfis disponíveis no Intune, para o ajudar a configurar políticas. Na página de autenticação da Microsoft, selecione **Aceitar**. É redirecionado para uma página de **Obrigado** do Datalert, que se fecha alguns segundos depois. O Datalert valida a ligação e apresenta marcas de verificação verdes junto a uma lista de itens que validou. Se a validação falhar, verá uma mensagem a vermelho e deverá contactar o Suporte do Datalert para obter ajuda.    

    A seguinte captura de ecrã mostra as marcas de verificação verdes que deverão ser apresentadas assim que a ligação for estabelecida com êxito.

   ![Página do Datalert a mostrar uma ligação estabelecida com êxito](./media/tem-datalert-mdm-profiles.png)

### <a name="step-2-check-that-the-telecom-expense-management-feature-is-active-in-intune"></a>Passo 2: Verifique se a funcionalidade de gestão de despesas de telecomunicações está ativo no Intune

Após concluir o Passo 1 descrito anteriormente, a sua ligação deverá ser ativada automaticamente e deverá ser apresentado o estado de ligação **Ativo** no portal do Azure. Estes passos mostram como pode localizar o estado **Ativo**.

1. Inicie sessão no [Portal do Azure](https://portal.azure.com).

2. Selecione **Todos os serviços** > **Intune**. O Intune encontra-se na secção **Monitorização + Gestão**.

3. No painel **Intune**, selecione **Configuração do dispositivo**.

4. No painel **Configuração do Dispositivo**, selecione **Configuração** > **Gestão de Despesas de Telecomunicações**.

   Procure o estado de ligação **Ativo** na parte superior da página.

   ![Página do Intune a mostrar o estado de ligação Ativo do Datalert](./media/tem-azure-portal-enable-service.png)

### <a name="step-3-deploy-the-datalert-app-to-corporate-enrolled-devices"></a>Passo 3: Implementar a aplicação Datalert em dispositivos inscritos da empresa

Para se certificar de que é recolhida a utilização de dados das linhas pertencentes apenas à empresa, terá de fazer duas coisas:
- criar categorias de dispositivos no Intune
- direcionar a aplicação Datalert apenas para telemóveis empresariais.

#### <a name="define-device-categories-and-device-groups-mapped-to-the-categories"></a>Definir categorias de dispositivos e grupos de dispositivos mapeados para as categorias

Conforme as necessidades da sua organização, crie pelo menos duas categorias de dispositivos (por exemplo, Empresarial e Pessoal). Em seguida, crie grupos de dispositivos dinâmicos para cada categoria. Se necessário, pode criar categorias adicionais para a sua organização.

Estas categorias serão apresentadas aos utilizadores durante a inscrição. Consoante a categoria que os utilizadores selecionarem, o dispositivo inscrito será movido para o grupo de dispositivos correspondente. Para obter passos sobre como criar categorias de dispositivos, veja [Map devices to groups (Mapear dispositivos para grupos)](device-group-mapping.md).

  ![Captura de ecrã do painel Adicionar uma política](./media/tem-dynamic-membership-rules.png)

#### <a name="create-the-datalert-app-in-intune"></a>Criar a aplicação Datalert no Intune

Siga estes passos para criar a aplicação Datalert no Intune para cada plataforma. Neste caso, utilizou-se o iOS como exemplo nestes passos.

1. No painel **Intune** do [portal do Azure](https://portal.azure.com), selecione **Aplicações do cliente**.

2. No painel **Aplicações do cliente**, selecione **Gerir** > **Aplicações**.

3. Selecione **Adicionar** para adicionar uma aplicação.

4. Selecione o tipo de aplicação. Por exemplo, para dispositivos iOS teria de selecionar **Aplicação da iOS Store**.

5. Em **Procurar na App Store**, procure a aplicação Datalert ao escrever **Datalert** na janela de pesquisa.

6. Selecione a aplicação **Datalert** e selecione **OK**.

   ![Captura de ecrã do painel Adicionar uma política](./media/tem-select-app-from-apple-app-store.png)

7. Conclua os passos restantes para criar uma aplicação para iOS.

   ![Captura de ecrã do painel Adicionar uma política](./media/tem-steps-to-create-the-app.png)

#### <a name="assign-the-datalert-app-to-the-corporate-device-group"></a>Atribuir a aplicação Datalert ao grupo de dispositivos da empresa

1. No painel **Aplicações cliente – Aplicações**, selecione a aplicação Datalert para iOS que criou no passo anterior.

2. No painel **Aplicações**, selecione **Gerir** > **Tarefas**.

3. Selecione **Adicionar grupo** e siga os passos para selecionar o grupo de dispositivos da empresa.

4. Opte por tornar a instalação da aplicação para o grupo obrigatória ou opcional. O seguinte exemplo mostra a instalação como sendo obrigatória, o que significa que os utilizadores têm de instalar a aplicação Datalert depois de instalarem o dispositivo.

   ![Captura de ecrã do painel Adicionar uma política](./media/tem-assign-datalert-app-to-device-group.png)

### <a name="step-4-add-corporate-paid-phone-lines-to-the-datalert-console"></a>Passo 4: Adicionar linhas telefónicas pagas pela empresa à consola Datalert

Acabou de configurar os serviços do Intune e do Datalert para que estes comuniquem entre si. Agora terá de adicionar as linhas telefónicas pagas da sua empresa à consola do Datalert e definir limites e ações a tomar relativamente a violações de utilização da rede móvel ou de roaming. Pode adicionar linhas telefónicas pagas pela empresa à consola Datalert manualmente ou adicioná-las automaticamente depois de o dispositivo ser inscrito no Intune.

Para definir estes itens, aceda à [página de configuração do Datalert para o Microsoft Intune](http://www.datalert.fr/microsoft-intune/intune-setup) (http://www.datalert.fr/microsoft-intune/intune-setup)) e siga os passos do assistente de configuração descritos no separador **Settings** (Definições).

  ![Captura de ecrã do painel Adicionar uma política](./media/tem-add-phone-lines-to-datalert-console.png)


O serviço Datalert está ativo e começa a monitorizar a utilização de dados e a desativar os dados de roaming e via rede móvel nos dispositivos que excedem os limites de utilização configurados.

## <a name="client-enrollment-experience"></a>Experiência de inscrição de clientes
Na experiência de inscrição de clientes, veja o seguinte:
-   [Inscrever o dispositivo iOS na gestão de despesas de telecomunicações](https://docs.microsoft.com/intune-user-help/enroll-your-device-with-telecom-expense-management-ios)
-   [Inscrever o dispositivo Android na gestão de despesas de telecomunicações](https://docs.microsoft.com/intune-user-help/enroll-your-device-with-telecom-expense-management-android)

## <a name="turning-off-the-datalert-service"></a>Desativar o serviço Datalert

Se desativar o serviço Datalert no portal do Azure:

- Todas as medidas que foram aplicadas aos dispositivos, devido a violações anteriores dos limites de utilização, serão anuladas.
- Os utilizadores deixam de estar bloqueados em relação ao acesso a dados e roaming.
- O Intune continua a receber sinais provenientes do serviço, mas ignora-os.

**Para desativar o serviço**

1. No painel **Gestão de Despesas de Telecomunicações** do portal do Azure, selecione **Desativar**.

2. Selecione **Guardar**.

## <a name="viewing-data-usage-and-roaming-reports"></a>Ver relatórios de utilização de dados e de roaming

Neste momento, os relatórios de utilização de dados só estão disponíveis na consola de gestão do Datalert da Saaswedo.

As instruções que os utilizadores finais seguirem para instalar a aplicação Datalert serão adicionadas em breve.
