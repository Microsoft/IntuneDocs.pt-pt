---
title: Integrar o Jamf Pro com o Microsoft Intune para conformidade
titleSuffix: Microsoft Intune
description: Use Microsoft Intune políticas de conformidade com Azure Active Directory acesso condicional para ajudar a integrar e proteger dispositivos gerenciados por JAMF.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 4b6dcbcc-4661-4463-9a36-698d673502c6
ms.reviewer: elocholi
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 59edb9956ee117e0dbdb9d90a4fd4ef313fd5c66
ms.sourcegitcommit: 2fddb293d37453736ffa54692d03eca642f3ab58
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/22/2019
ms.locfileid: "74390469"
---
# <a name="integrate-jamf-pro-with-intune-for-compliance"></a>Integrar o Jamf Pro com o Intune para conformidade

Quando sua organização usa o [JAMF pro](https://www.jamf.com) para gerenciar dispositivos MacOS, você pode usar Microsoft Intune políticas de conformidade com o acesso condicional do Azure Active Directory (AD do Azure) para garantir que os dispositivos em sua organização estejam em conformidade antes que possam acessar os recursos da empresa. Este artigo o ajudará a configurar a integração do JAMF com o Intune.

Quando o JAMF pro integra-se com o Intune, você pode sincronizar os dados de inventário de dispositivos macOS com o Intune, por meio do Azure AD. Em seguida, o mecanismo de conformidade do Intune analisa os dados de inventário para gerar um relatório. A análise do Intune é combinada com inteligência sobre a identidade do Azure AD do usuário do dispositivo para impulsionar a imposição por meio de acesso condicional. Os dispositivos que são compatíveis com as políticas de acesso condicional podem obter acesso aos recursos protegidos da empresa.

Depois de configurar a integração, você [configurará o JAMF e o Intune para impor a conformidade com o acesso condicional](conditional-access-assign-jamf.md) em dispositivos gerenciados pelo JAMF.

## <a name="prerequisites"></a>Pré-requisitos

### <a name="products-and-services"></a>Produtos e serviços

Você precisa do seguinte para configurar o acesso condicional com o JAMF pro:

- Jamf Pro 10.1.0 ou posterior
- [Aplicação Portal da Empresa para macOS](https://aka.ms/macoscompanyportal)
- dispositivos macOS com OS X 10,12 Yosemite ou posterior

### <a name="network-ports"></a>Portas de rede

<!-- source: https://support.microsoft.com/en-us/help/4519171/troubleshoot-problems-when-integrating-jamf-with-microsoft-intune -->
As portas a seguir devem estar acessíveis para que o JAMF e o Intune sejam integrados corretamente:

- **Intune**: porta 443
- **Apple**: portas 2195, 2196 e 5223 (notificações por push para o Intune)
- **JAMF**: portas 80 e 5223

Para permitir que o APNS funcione corretamente na rede, você também deve habilitar conexões de saída para e redirecionar de:

- o bloco Apple 17.0.0.0/8 sobre as portas TCP 5223 e 443 de todas as redes cliente.
- portas 2195 e 2196 de servidores JAMF pro.  

Para obter mais informações sobre essas portas, consulte os seguintes artigos:

- [Largura de banda e requisitos de configuração de rede do Intune](../fundamentals/network-bandwidth-use.md).
- [Portas de rede usadas pelo JAMF pro](https://www.jamf.com/jamf-nation/articles/34/network-ports-used-by-jamf-pro) no JAMF.com.
- [Portas TCP e UDP usadas por produtos de software da Apple](https://support.apple.com/HT202944) no support.Apple.com

## <a name="connect-intune-to-jamf-pro"></a>Conectar o Intune ao JAMF pro

Para conectar o Intune ao JAMF pro:

1. Crie um novo aplicativo no Azure.
2. Habilite o Intune para integrar com o JAMF pro.
3. Configure o acesso condicional no JAMF pro.

### <a name="create-an-application-in-azure-active-directory"></a>Criar um aplicativo no Azure Active Directory

1. Na [portal do Azure](https://portal.azure.com), acesse **Azure Active Directory** > **registros de aplicativo**e, em seguida, selecione **novo registro**.

2. Na página **registrar um aplicativo** , especifique os seguintes detalhes:

   - Na seção **nome** , insira um nome de aplicativo significativo, por exemplo, **JAMF acesso condicional**.
   - Para a seção **tipos de conta com suporte** , selecione **contas em qualquer diretório organizacional**.
   - Para **URI de redirecionamento**, deixe o padrão da Web e, em seguida, ESPECIFIQUE a URL para sua instância do JAMF pro.

3. Selecione **registrar** para criar o aplicativo e abrir a página **visão geral** do novo aplicativo.

4. Na página **visão geral** do aplicativo, copie o valor da **ID do aplicativo (cliente)** e registre-o para uso posterior. Você precisará desse valor em procedimentos posteriores.

5. Selecione **certificados & segredos** em **gerenciar**. Selecione o botão **novo segredo do cliente** . Insira um valor em **Descrição**, selecione qualquer opção para **expirar** e escolha **Adicionar**.

   > [!IMPORTANT]
   > Antes de sair dessa página, copie o valor do segredo do cliente e registre-o para uso posterior. Você precisará desse valor em procedimentos posteriores. Esse valor não está disponível novamente, sem recriar o registro do aplicativo.

6. Selecione **permissões de API** em **gerenciar**. Selecione as permissões existentes e, em seguida, selecione **remover permissão** para excluir essas permissões. A remoção de todas as permissões existentes é necessária, pois você adicionará uma nova permissão e o aplicativo só funcionará se tiver a única permissão necessária.

7. Para atribuir uma nova permissão, selecione **Adicionar uma permissão**. Na página **solicitar permissões de API** , selecione **Intune**e, em seguida, selecione **permissões de aplicativo**. Marque somente a caixa de seleção para **update_device_attributes**.

   Selecione **adicionar permissão** para salvar essa configuração.

8. Na página **permissões de API** , selecione **conceder consentimento de administrador para _\<seu > de locatário_** e, em seguida, selecione **Sim**.  Depois que o aplicativo é registrado com êxito, as permissões de API devem ser exibidas da seguinte maneira:

   ![Permissões com êxito](./media/conditional-access-integrate-jamf/sucessfull-app-registration.png)

   O processo de registro do aplicativo no Azure AD foi concluído.

    > [!NOTE]
    > Se o segredo do cliente expirar, você deverá criar um novo segredo do cliente no Azure e, em seguida, atualizar os dados de acesso condicional no JAMF pro. O Azure permite que você tenha o antigo segredo e a nova chave ativas para evitar interrupções de serviço.

### <a name="enable-intune-to-integrate-with-jamf-pro"></a>Integrar o Intune com o Jamf Pro

1. Entre no centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Selecione **Administração de locatários** > **conectores e tokens** > **Gerenciamento de dispositivo de parceiro**.

3. Habilite o *conector de conformidade para JAMF* colando a ID do aplicativo que você salvou durante o procedimento anterior no campo **especificar a id do aplicativo Azure Active Directory para JAMF** .

4. Selecione **Guardar**.

### <a name="configure-microsoft-intune-integration-in-jamf-pro"></a>Configurar a Integração do Microsoft Intune no Jamf Pro

1. Ative a conexão no console do JAMF pro:

   1. Abra o console do JAMF pro e navegue até **Gerenciamento Global** > **acesso condicional**. Clique no botão **Editar** na guia **integração com o MacOS Intune** .
   2. Marque a caixa de seleção **habilitar integração do Intune para MacOS**.
   3. Forneça as informações necessárias sobre seu locatário do Azure, incluindo o **local**, o **nome de domínio**, a **ID do aplicativo**e o valor para o segredo do *cliente* que você salvou quando criou o aplicativo no Azure AD.
   4. Selecione **Guardar**. O JAMF pro testa suas configurações e verifica seu sucesso.

   Retorne à página de **Gerenciamento de dispositivo de parceiro** no Intune para concluir a configuração.

2. No Intune, vá para a página de **Gerenciamento de dispositivos do parceiro** . Em **configurações do conector** , configure grupos para atribuição:

   - Selecione **incluir** e especifique quais grupos de usuários você deseja direcionar para o registro do MacOS com JAMF.
   - Use **excluir** para selecionar grupos de usuários que não serão registrados com o JAMF e, em vez disso, registrará seus Macs diretamente com o Intune.

   As substituições de *exclusão* *incluem*, o que significa que qualquer dispositivo em ambos os grupos é excluído do JAMF e direcionado para o registro com o Intune.

   >[!NOTE]
   > Esse método de inclusão e exclusão de grupos de usuários afeta a experiência de registro do usuário. Qualquer usuário com um Mac que já esteja registrado no JAMF ou no Intune, que é direcionado para registrar com o outro MDM, deve cancelar o registro de seu dispositivo e registrá-lo novamente com o novo MDM antes que o gerenciamento do dispositivo funcione corretamente.

3. Selecione **avaliar** para determinar quantos dispositivos serão registrados com o JAMF, com base nas suas configurações de grupo.

4. Selecione **salvar** quando estiver pronto para aplicar a configuração.

5. Para continuar, você precisará usar [o JAMF para implantar o portal da empresa para Mac](conditional-access-assign-jamf.md#deploy-the-company-portal-app-for-macos-in-jamf-pro) para que os usuários possam registrar seus dispositivos no Intune.

## <a name="set-up-compliance-policies-and-register-devices"></a>Definir as políticas de conformidade e registar dispositivos

Depois de configurar a integração entre o Intune e o JAMF, você precisa [aplicar políticas de conformidade a dispositivos gerenciados por JAMF](conditional-access-assign-jamf.md).

## <a name="disconnect-jamf-pro-and-intune"></a>Desconectar o JAMF pro e o Intune

Se você não usar mais o JAMF pro para gerenciar Macs em sua organização e quiser que os usuários sejam gerenciados pelo Intune, deverá remover a conexão entre o JAMF pro e o Intune. Remova a conexão usando o console do JAMF pro.

1. No JAMF pro, acesse **Gerenciamento Global** > **acesso condicional**. Na guia **integração do Intune no MacOS** , selecione **Editar**.

2. Desmarque a caixa de seleção **habilitar integração do Intune para MacOS** .

3. Selecione **Guardar**. O JAMF pro envia sua configuração para o Intune e a integração será encerrada.

4. Entre no centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

5. Selecione **Administração de locatários** > **conectores e tokens** > **Gerenciamento de dispositivo de parceiro** para verificar se o status agora está **encerrado**.

   > [!NOTE]
   > Os dispositivos Mac da sua organização serão removidos na data (3 meses) mostrados no console.

## <a name="next-steps"></a>Passos Seguintes

- [Aplicar políticas de conformidade a dispositivos geridos pelo Jamf](conditional-access-assign-jamf.md)
- [JAMF de dados enviados ao Intune](data-jamf-sends-to-intune.md)
