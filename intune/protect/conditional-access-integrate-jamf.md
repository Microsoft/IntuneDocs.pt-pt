---
title: Integre o JAMF pro ao Microsoft Intune para fins de conformidade
titleSuffix: Microsoft Intune
description: Use Microsoft Intune políticas de conformidade com Azure Active Directory acesso condicional para ajudar a integrar e proteger dispositivos gerenciados por JAMF.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 09/20/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 4b6dcbcc-4661-4463-9a36-698d673502c6
ms.reviewer: elocholi
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 09566e314f801c0de3f371384126cf672403b6a3
ms.sourcegitcommit: dd6755383ba89824d1cc128698a65fde6bb2de55
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/14/2019
ms.locfileid: "72306646"
---
# <a name="integrate-jamf-pro-with-intune-for-compliance"></a>Integrar o JAMF pro ao Intune para conformidade

Aplica-se a: Intune no portal do Azure

Quando sua organização usa o [JAMF pro](https://www.jamf.com) para gerenciar dispositivos MacOS, você pode usar Microsoft Intune políticas de conformidade com acesso condicional do Azure Active Directory (AD do Azure) para garantir que os dispositivos em sua organização estejam em conformidade antes que possam acessar recursos da empresa. Este artigo o ajudará a configurar a integração do JAMF com o Intune.

Quando o JAMF pro integra-se com o Intune, você pode sincronizar os dados de inventário de dispositivos macOS com o Intune, por meio do Azure AD. Em seguida, o mecanismo de conformidade do Intune analisa os dados de inventário para gerar um relatório. A análise do Intune é combinada com inteligência sobre a identidade do Azure AD do usuário do dispositivo para impulsionar a imposição por meio de acesso condicional. Os dispositivos que são compatíveis com as políticas de acesso condicional podem obter acesso aos recursos protegidos da empresa.

Depois de configurar a integração, você [configurará o JAMF e o Intune para impor a conformidade com o acesso condicional](conditional-access-assign-jamf.md) em dispositivos gerenciados pelo JAMF.  


## <a name="prerequisites"></a>Pré-requisitos

### <a name="products-and-services"></a>Produtos e serviços
Você precisa do seguinte para configurar o acesso condicional com o JAMF pro:

- JAMF Pro 10.1.0 ou posterior
- [Portal da Empresa aplicativo para macOS](https://aka.ms/macoscompanyportal)
- dispositivos macOS com OS X 10,11 Yosemite ou posterior

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

## <a name="create-an-application-in-azure-active-directory"></a>Criar uma Aplicação no Azure Active Directory

1. Na [portal do Azure](https://portal.azure.com), acesse **Azure Active Directory** **registros do aplicativo** >  e, em seguida, selecione **novo registro**. 

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

7. Para atribuir uma nova permissão, selecione **Adicionar uma permissão**. Na página **solicitar permissões de API** , selecione **Intune**e, em seguida, selecione **permissões de aplicativo**. Selecione apenas a caixa de seleção para **update_device_attributes**.  

   Selecione **adicionar permissão** para salvar essa configuração.  

8. Na página **permissões de API** , selecione * * conceder consentimento de administrador para o locatário * \<your > * * * e, em seguida, selecione **Sim**.  Depois que o aplicativo é registrado com êxito, as permissões de API devem aparecer da seguinte maneira: permissões de ![Successful @ no__t-1

   O processo de registro do aplicativo no Azure AD foi concluído.


    > [!NOTE]
    > Se o segredo do cliente expirar, você deverá criar um novo segredo do cliente no Azure e, em seguida, atualizar os dados de acesso condicional no JAMF pro. O Azure permite que você tenha o antigo segredo e a nova chave ativas para evitar interrupções de serviço.

## <a name="enable-intune-to-integrate-with-jamf-pro"></a>Habilitar o Intune para integrar com o JAMF pro

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)e vá para **Microsoft Intune** >  conformidade do**dispositivo** >  gerenciamento de**dispositivo do parceiro**.

2. Habilite o conector de conformidade para JAMF colando a ID do aplicativo que você salvou durante o procedimento anterior no campo **ID do aplicativo do Jamf Azure Active Directory** .

3. Selecione **Guardar**.

## <a name="configure-microsoft-intune-integration-in-jamf-pro"></a>Configurar a integração de Microsoft Intune no JAMF pro

1. No JAMF pro, navegue até **Gerenciamento Global** > **acesso condicional**. Clique no botão **Editar** na guia **integração com o MacOS Intune** .

2. Marque a caixa de seleção **habilitar integração do Intune para MacOS**.

3. Forneça as informações necessárias sobre seu locatário do Azure, incluindo o **local**, o **nome de domínio**, a **ID do aplicativo**e o valor para o segredo do *cliente* que você salvou quando criou o aplicativo no Azure AD.  

4. Selecione **Guardar**. O JAMF pro testa suas configurações e verifica seu sucesso.

## <a name="set-up-compliance-policies-and-register-devices"></a>Configurar políticas de conformidade e registrar dispositivos

Depois de configurar a integração entre o Intune e o JAMF, você precisa [aplicar políticas de conformidade a dispositivos gerenciados por JAMF](conditional-access-assign-jamf.md).


## <a name="disconnect-jamf-pro-and-intune"></a>Desconectar o JAMF pro e o Intune 

Se você não usar mais o JAMF pro para gerenciar Macs em sua organização e quiser que os usuários sejam gerenciados pelo Intune, deverá remover a conexão entre o JAMF pro e o Intune. Remova a conexão usando o console do JAMF pro. 

1. No JAMF pro, acesse **Gerenciamento Global** > **acesso condicional**. Na guia **integração do Intune no MacOS** , selecione **Editar**.
2. Desmarque a caixa de seleção **habilitar integração do Intune para MacOS** .
3. Selecione **Guardar**. O JAMF pro envia sua configuração para o Intune e a integração será encerrada.
4. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973). Vá para **Microsoft Intune** > **conformidade de dispositivo** > **Gerenciamento de dispositivo de parceiro** para verificar se o status agora está **encerrado**. 

   > [!NOTE]
   > Os dispositivos Mac da sua organização serão removidos na data (3 meses) mostrados no console. 

## <a name="next-steps"></a>Passos seguintes

- [Aplicar políticas de conformidade a dispositivos gerenciados por JAMF](conditional-access-assign-jamf.md)
- [JAMF de dados enviados ao Intune](data-jamf-sends-to-intune.md)
