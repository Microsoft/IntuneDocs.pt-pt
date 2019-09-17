---
title: Integrar o Jamf Pro com o Microsoft Intune para conformidade
titleSuffix: Microsoft Intune
description: Use Microsoft Intune políticas de conformidade com Azure Active Directory acesso condicional para ajudar a proteger dispositivos gerenciados por JAMF.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 05/16/2019
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
ms.openlocfilehash: b439067d06cf49a4ff83288e109d1fccd3801106
ms.sourcegitcommit: 3db8af810b95c3a6ed3f8cc00f6ce79076ebb9db
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/16/2019
ms.locfileid: "71012519"
---
# <a name="integrate-jamf-pro-with-intune-for-compliance"></a>Integrar o Jamf Pro com o Intune para conformidade

Aplica-se a: Intune no portal do Azure

Se sua organização usa o [JAMF pro](https://www.jamf.com) para gerenciar seus Macs de usuários finais, você pode usar Microsoft Intune políticas de conformidade com Azure Active Directory acesso condicional para garantir que os dispositivos em sua organização estejam em conformidade.

## <a name="prerequisites"></a>Pré-requisitos

Você precisa do seguinte para configurar o acesso condicional com o JAMF pro:

- Jamf Pro 10.1.0 ou posterior
- [Aplicação Portal da Empresa para macOS](https://aka.ms/macoscompanyportal)
- Dispositivos macOS com OS X 10.11 Yosemite ou posterior

## <a name="connect-intune-to-jamf-pro"></a>Conectar o Intune ao JAMF pro

Para conectar o Intune ao JAMF pro:

1. Crie um novo aplicativo no Azure.
2. Habilite o Intune para integrar com o JAMF pro.
3. Configure o acesso condicional no JAMF pro.

## <a name="create-an-application-in-azure-active-directory"></a>Criar um aplicativo no Azure Active Directory

1. Na [portal do Azure](https://portal.azure.com), vá para **Azure Active Directory** > **registros de aplicativo**e, em seguida, selecione **novo registro**. 

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

8. Na página **permissões de API** , selecione **conceder consentimento de administrador para a Microsoft**e, em seguida, selecione **Sim**.  

   O processo de registro do aplicativo no Azure AD foi concluído.


    > [!NOTE]
    > Se o segredo do cliente expirar, você deverá criar um novo segredo do cliente no Azure e, em seguida, atualizar os dados de acesso condicional no JAMF pro. O Azure permite que você tenha o antigo segredo e a nova chave ativas para evitar interrupções de serviço.

## <a name="enable-intune-to-integrate-with-jamf-pro"></a>Integrar o Intune com o Jamf Pro

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)e vá para **Microsoft Intune** > **Gerenciamento de dispositivos do parceiro**de**conformidade** > do dispositivo.

2. Habilite o conector de conformidade para JAMF colando a ID do aplicativo que você salvou durante o procedimento anterior no campo **ID do aplicativo do Jamf Azure Active Directory** .

3. Selecione **Guardar**.

## <a name="configure-microsoft-intune-integration-in-jamf-pro"></a>Configurar a Integração do Microsoft Intune no Jamf Pro

1. No Jamf Pro, navegue para **Gestão Global** > **Acesso Condicional**. Clique no botão **Editar** na guia **integração com o MacOS Intune** .

2. Marque a caixa de seleção **habilitar integração do Intune para MacOS**.

3. Forneça as informações necessárias sobre seu locatário do Azure, incluindo o **local**, o **nome de domínio**, a **ID do aplicativo**e o valor para o segredo do *cliente* que você salvou quando criou o aplicativo no Azure AD.  

4. Selecione **Guardar**. O JAMF pro testa suas configurações e verifica seu sucesso.

## <a name="set-up-compliance-policies-and-register-devices"></a>Definir as políticas de conformidade e registar dispositivos

Depois de configurar a integração entre o Intune e o JAMF, você precisa [aplicar políticas de conformidade a dispositivos gerenciados por JAMF](conditional-access-assign-jamf.md).

## <a name="disconnect-jamf-pro-and-intune"></a>Desconectar o JAMF pro e o Intune 

Se você não usar mais o JAMF pro para gerenciar Macs em sua organização e quiser que os usuários sejam gerenciados pelo Intune, deverá remover a conexão entre o JAMF pro e o Intune. Remova a conexão usando o console do JAMF pro. 

1. No JAMF pro, acesse **Gerenciamento** > global**acesso condicional**. Na guia **integração do Intune no MacOS** , selecione **Editar**.
2. Desmarque a caixa de seleção **habilitar integração do Intune para MacOS** .
3. Selecione **Guardar**. O JAMF pro envia sua configuração para o Intune e a integração será encerrada.
4. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973). Vá para **Microsoft Intune** > **Gerenciamento de dispositivo de parceiro** de conformidade > do**dispositivo**para verificar se o status agora está **encerrado**. 

   > [!NOTE]
   > Os dispositivos Mac da sua organização serão removidos na data (3 meses) mostrados no console. 

## <a name="next-steps"></a>Passos seguintes

- [Aplicar políticas de conformidade a dispositivos geridos pelo Jamf](conditional-access-assign-jamf.md)
- [JAMF de dados enviados ao Intune](data-jamf-sends-to-intune.md)
