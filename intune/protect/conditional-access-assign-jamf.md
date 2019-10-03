---
title: Política de conformidade do dispositivo para dispositivos Jamf
titleSuffix: Microsoft Intune
description: Use Microsoft Intune políticas de conformidade com Azure Active Directory acesso condicional para ajudar a proteger dispositivos gerenciados por JAMF.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/02/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: c87fd2bd-7f53-4f1b-b985-c34f2d85a7bc
ms.reviewer: elocholi
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 74ee1eaf0581c4500830514fa9ad272f0de09d3b
ms.sourcegitcommit: f04e21ec459998922ba9c7091ab5f8efafd8a01c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71813985"
---
# <a name="enforce-compliance-on-macs-managed-with-jamf-pro"></a>Impor a conformidade em Macs geridos com o Jamf Pro

Ao [integrar o JAMF pro ao Intune](conditional-access-integrate-jamf.md), você pode usar políticas de acesso condicional para impor a conformidade em seus dispositivos Mac com seus requisitos organizacionais.  Este artigo o ajudará com as seguintes tarefas:  

- Criar políticas de acesso condicional.
- Configure o JAMF pro para implantar o aplicativo Portal da Empresa do Intune em dispositivos gerenciados com o JAMF.
- Configure dispositivos para se registrarem com o Azure AD quando o usuário do dispositivo entrar no aplicativo Portal da Empresa ele iniciará no aplicativo de autoatendimento do JAMF. O registro de dispositivo estabelece uma identidade no Azure AD que permite que o dispositivo seja avaliado por políticas de acesso condicional para acesso aos recursos da empresa.  
 
Os procedimentos neste artigo exigem acesso aos consoles do Intune e do JAMF pro.

## <a name="set-up-device-compliance-policies-in-intune"></a>Configurar políticas de conformidade de dispositivos no Intune

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) e vá para **conformidade do dispositivo** > **políticas**. 
2. Se você estiver usando uma política criada anteriormente, selecione essa política no console do e vá para a próxima etapa deste procedimento.  
   
   Selecione **criar política** e especifique os detalhes de uma política com uma *plataforma* **MacOS**. Defina *as configurações e as* *ações de não conformidade* para atender aos requisitos organizacionais e, em seguida, selecione **criar** para salvar a política.

3. No painel *visão geral* de políticas, selecione **atribuições**. Use as opções disponíveis para configurar quais usuários do Azure Active Directory (Azure AD) e grupos de segurança recebem essa política. A integração do JAMF com o Intune não oferece suporte à política de conformidade direcionada a grupos de dispositivos. 

4. Quando você seleciona **salvar**, a política é implantada para os usuários.  

As políticas que você implanta são direcionadas aos dispositivos que são usados pelos usuários atribuídos. Esses dispositivos são avaliados quanto à conformidade. Os dispositivos em conformidade são marcados como compatíveis para a configuração "exigir que o*dispositivo seja marcado como em conformidade*" no Azure AD.  

> [!NOTE]
> O Intune exige que a encriptação total do disco esteja em conformidade.

## <a name="deploy-the-company-portal-app-for-macos-in-jamf-pro"></a>Implementar a aplicação Portal da Empresa para macOS no Jamf Pro

Crie uma política no JAMF pro para implantar o Portal da Empresa do Intune. Esta política implanta o aplicativo do portal da empresa para que ele esteja disponível no autoatendimento JAMF. Crie essa política antes de criar a política no JAMF pro para que os usuários registrem dispositivos com o Azure AD.  

Para concluir o procedimento a seguir, você precisa ter acesso a um dispositivo macOS e ao portal do JAMF pro. 

### <a name="to-deploy-the-company-portal-app"></a>Para implantar o aplicativo do portal da empresa  

1. Em um dispositivo macOS, baixe, mas não instale a versão atual do [aplicativo portal da empresa para MacOS](https://go.microsoft.com/fwlink/?linkid=862280). Você só precisa de uma cópia do aplicativo para que possa carregar o aplicativo no JAMF pro.  

2. Abra o JAMF pro e vá para **Gerenciamento do computador** > **pacotes**.

3. Crie um novo pacote com o aplicativo Portal da Empresa para macOS e, em seguida, selecione **salvar**.

4. Abra **Computadores** > **Políticas** e, em seguida, selecione **Novo**.

5. Utilize o payload **Geral** para configurar as definições da política. Estas definições deverão ser:
   - Acionador: selecione **Inscrição Completa** e **Inscrição Periódica**
   - Frequência de execução: selecione **Uma por computador**

6. Selecione o payload **Pacotes** e clique em **Configurar**.

7. Clique em **Adicionar** para selecionar o pacote com a aplicação Portal da Empresa.

8. Selecione **instalar** no menu pop-up **ação** .
9. Configure as definições do pacote.

10. Selecione a guia **escopo** para especificar em quais computadores o aplicativo portal da empresa deve ser instalado. Selecione **Guardar**. A política será executada em dispositivos com escopo na próxima vez que o gatilho selecionado ocorrer no computador e os critérios na carga **geral** forem atendidos.

## <a name="create-a-policy-in-jamf-pro-to-have-users-register-their-devices-with-azure-active-directory"></a>Criar uma política no Jamf Pro para que os utilizadores registem os respetivos dispositivos com o Azure Active Directory  

Depois de [implantar o portal da empresa](conditional-access-assign-jamf.md#deploy-the-company-portal-app-for-macos-in-jamf-pro) para MacOS por meio do JAMF pro Self Service, você pode criar a política do JAMF pro que registra o dispositivo do usuário com o Azure AD. 

O registro de dispositivo requer que um usuário de dispositivo selecione manualmente o aplicativo de Portal da Empresa do Intune de dentro do JAMF self service. Recomendamos que você [entre em contato com seus usuários finais](../fundamentals/end-user-educate.md) por email, notificações do JAMF pro ou qualquer outro método que sua organização Use para direcioná-los para concluir esta ação para que seus dispositivos sejam registrados. 

> [!WARNING]
> Iniciar o aplicativo Portal da Empresa manualmente (por exemplo, a partir de pastas de aplicativos ou downloads) não registrará o dispositivo. Se o usuário do dispositivo iniciar o Portal da Empresa manualmente, ele verá um aviso, **' AccountNotOnboarded '** .

### <a name="to-create-the-registration-policy"></a>Para criar a política de registro  

1. No JAMF pro, vá para **computadores** > **políticas**e, em seguida, crie uma nova política para o registro do dispositivo.

2. Configure o payload **Integração do Microsoft Intune**, incluindo o acionamento e a frequência de execução.

3. Selecione a guia **escopo** e, em seguida, escopo a política para todos os dispositivos de destino.

4. Selecione a guia **autoatendimento** para tornar a política disponível no autoatendimento JAMF. Inclua a política na categoria **Conformidade do Dispositivo**. Clique em **Guardar**.

## <a name="validate-intune-and-jamf-integration"></a>Validar a integração do Intune e do JAMF  

Use o console do JAMF pro para confirmar se a comunicação entre o JAMF pro e o Microsoft Intune foi bem-sucedida. 

- No JAMF pro, acesse **configurações** > **gerenciamento global** > **Microsoft Intune integração**e, em seguida, selecione **testar**. 

    O console exibe uma mensagem com o êxito ou a falha da conexão.  

Se o teste de conexão do console do JAMF pro falhar, examine a configuração do JAMF. 


## <a name="removing-a-jamf-managed-device-from-intune"></a>Remover um dispositivo gerido por Jamf do Intune

Pode remover um dispositivo gerido por Jamf a partir da consola do Intune ao selecionar **Eliminar** na vista **Todos os dispositivos**. A eliminação de dispositivos em massa pode ser ativada ao selecionar múltiplos dispositivos e clicar em **Eliminar**.

Obtenha informações sobre como [remover um dispositivo gerido por Jamf na documentação do Jamf Pro](https://www.jamf.com/jamf-nation/articles/80/unmanaging-computers-while-preserving-their-inventory-information). Também pode enviar um pedido de suporte para o [suporte do Jamf](https://www.jamf.com/support/) para obter ajuda adicional. 

## <a name="next-steps"></a>Passos seguintes

- [Acesso Condicional no Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)
- [Introdução ao acesso condicional no Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal-get-started)
