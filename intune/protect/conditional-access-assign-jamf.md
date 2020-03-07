---
title: Política de conformidade do dispositivo para dispositivos Jamf
titleSuffix: Microsoft Intune
description: Utilize as políticas de conformidade do Microsoft Intune com o Azure Ative Directory Conditional Access para ajudar a proteger dispositivos geridos pelo Jamf.
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
ms.assetid: c87fd2bd-7f53-4f1b-b985-c34f2d85a7bc
ms.reviewer: elocholi
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b09b30fd32caace9ed3259350c01548d5e5fae15
ms.sourcegitcommit: 25e4847ead0f56c269cfefe1e01c1b9106a28cf1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/05/2020
ms.locfileid: "78369999"
---
# <a name="enforce-compliance-on-macs-managed-with-jamf-pro"></a>Impor a conformidade em Macs geridos com o Jamf Pro

Quando integrar o Jamf Pro com o [Intune,](conditional-access-integrate-jamf.md)pode utilizar políticas de Acesso Condicional para impor o cumprimento dos seus dispositivos Mac com os seus requisitos organizacionais.  Este artigo irá ajudá-lo com as seguintes tarefas:  

- Criar políticas de acesso condicional.
- Configure o Jamf Pro para implementar a aplicação Intune Company Portal para dispositivos que gere com o Jamf.
- Configure os dispositivos para se registar em Azure AD quando o utilizador do dispositivo iniciar a sua entrada na aplicação Portal da Empresa que eles iniciam dentro da aplicação Jamf Self Service. O registo do dispositivo estabelece uma identidade em Azure AD que permite que o dispositivo seja avaliado pelas políticas de Acesso Condicional para acesso aos recursos da empresa.  
 
Os procedimentos deste artigo requerem acesso às consolas Intune e Jamf Pro.

## <a name="set-up-device-compliance-policies-in-intune"></a>Configurar políticas de conformidade de dispositivos no Intune

1. Inscreva-se no [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Selecione **Dispositivos** > políticas de **conformidade**. Se estiver a utilizar uma política previamente criada, selecione essa política na consola e, em seguida, vá para o próximo passo deste procedimento. Para criar uma nova política, selecione **Create Policy** e, em seguida, especifique detalhes para uma política com uma *Plataforma* de **macOS**. Configure *Configurar Definições* e *Ações para o incumprimento* do cumprimento dos seus requisitos organizacionais e, em seguida, selecione **Criar** para salvar a apólice.

3. Sobre as políticas *Painel de visão geral,* selecione **Atribuições**. Utilize as opções disponíveis para configurar quais os utilizadores e grupos de segurança do Azure Ative Directory (Azure AD) que recebem esta política. A integração do Jamf com a Intune não suporta a política de conformidade que visa grupos de dispositivos.

4. Quando selecionar **Save**, a política é implementada para os utilizadores.  

As políticas que implementa visam os dispositivos que são utilizados pelos utilizadores designados. Estes dispositivos são avaliados para o cumprimento. Os dispositivos conformes são marcados como conformes para a definição "*Exigir que o dispositivo seja marcado como conforme*" em Azure AD.  

> [!NOTE]
> O Intune exige que a encriptação total do disco esteja em conformidade.

## <a name="deploy-the-company-portal-app-for-macos-in-jamf-pro"></a>Implementar a aplicação Portal da Empresa para macOS no Jamf Pro

Crie uma política no Jamf Pro para implementar o Portal da Empresa Intune. Esta política implementa a aplicação portal da empresa para que esteja disponível no Jamf Self Service. Crie esta política antes de criar uma política no Jamf Pro para que os utilizadores registem dispositivos com a AD Azure.  

Para completar o seguinte procedimento, precisa de acesso a um dispositivo macOS e ao portal Jamf Pro. 

### <a name="to-deploy-the-company-portal-app"></a>Para implementar a aplicação portal da empresa  

1. Num dispositivo macOS, descarregue mas não instale a versão atual da aplicação Portal da [Empresa para o macOS.](https://go.microsoft.com/fwlink/?linkid=862280) Só precisa de uma cópia da aplicação para que possa fazer o upload da aplicação para o Jamf Pro.  

2. Abra o Jamf Pro e vá à **gestão de computadores** > **Pacotes.**

3. Crie um novo pacote com a aplicação Portal da Empresa para o macOS e, em seguida, selecione **Save**.

4. Abra **Computadores** > **Políticas** e, em seguida, selecione **Novo**.

5. Utilize o payload **Geral** para configurar as definições da política. Estas definições deverão ser:
   - Acionador: selecione **Inscrição Completa** e **Inscrição Periódica**
   - Frequência de execução: selecione **Uma por computador**

6. Selecione o payload **Pacotes** e clique em **Configurar**.

7. Clique em **Adicionar** para selecionar o pacote com a aplicação Portal da Empresa.

8. Selecione **Instalar** a partir do menu pop-up **Action.**
9. Configure as definições do pacote.

10. Selecione o separador **Scope** para especificar em que computadores a aplicação Portal da Empresa deve instalar. Selecione **Guardar**. A política funciona em dispositivos com âmbito de aplicação da próxima vez que o gatilho selecionado ocorrer no computador e os critérios na carga **geral** forem cumpridos.

## <a name="create-a-policy-in-jamf-pro-to-have-users-register-their-devices-with-azure-active-directory"></a>Criar uma política no Jamf Pro para que os utilizadores registem os respetivos dispositivos com o Azure Active Directory  

Depois de [implementar o Portal da Empresa](conditional-access-assign-jamf.md#deploy-the-company-portal-app-for-macos-in-jamf-pro) para o macOS através do Jamf Pro Self Service, pode criar a política Jamf Pro que regista o dispositivo de um utilizador com a AD Azure. 

O registo do dispositivo requer que um utilizador do dispositivo selecione manualmente a aplicação Intune Company Portal a partir do Jamf Self Service. Recomendamos que [contacte os seus utilizadores finais](../fundamentals/end-user-educate.md) através de e-mail, notificações do Jamf Pro ou qualquer outro método que a sua organização utilize para os direcionar para completar esta ação para que os seus dispositivos sejam registados. 

> [!WARNING]
> O lançamento manual da aplicação Portal da Empresa (como as aplicações Aplicações ou Transferências) não regista o dispositivo. Se o utilizador do dispositivo lançar manualmente o Portal da Empresa, verá um aviso, **'AccountNotOnboarded'.**

### <a name="to-create-the-registration-policy"></a>Para criar a política de registo  

1. No Jamf Pro, vá ao **Computers** > **Policies**, e depois crie uma nova política para o registo de dispositivos.

2. Configure o payload **Integração do Microsoft Intune**, incluindo o acionamento e a frequência de execução.

3. Selecione o separador **Scope** e, em seguida, scope a política para todos os dispositivos direcionados.

4. Selecione o separador **Self Service** para disponibilizar a apólice no Jamf Self Service. Inclua a política na categoria **Conformidade do Dispositivo**. Clique em **Guardar**.

## <a name="validate-intune-and-jamf-integration"></a>Validar a integração intune e jamf  

Utilize a consola Jamf Pro para confirmar que a comunicação entre o Jamf Pro e o Microsoft Intune é bem sucedida. 

- No Jamf Pro, vá a **Definições** > **Global Management** > **Microsoft Intune Integration**, e, em seguida, selecione **Test**.

    A consola exibe uma mensagem com o sucesso ou falha da ligação.  

Se o teste de ligação da consola Jamf Pro falhar, reveja a configuração do Jamf. 


## <a name="removing-a-jamf-managed-device-from-intune"></a>Remover um dispositivo gerido por Jamf do Intune

Para remover um dispositivo gerido pelo Jamf, abra o Microsoft Endpoint Manager Admin Center e selecione **Dispositivos** > **Todos os dispositivos,** selecione o dispositivo e, em seguida, selecione **Delete**.  A eliminação de dispositivos em massa pode ser ativada ao selecionar múltiplos dispositivos e clicar em **Eliminar**.

Obtenha informações sobre como remover um dispositivo gerido pelo [Jamf nos docs Jamf Pro](https://www.jamf.com/jamf-nation/articles/80/unmanaging-computers-while-preserving-their-inventory-information). Também pode apresentar um bilhete de apoio com suporte ao [Jamf](https://www.jamf.com/support/) para obter ajuda adicional. 

## <a name="next-steps"></a>Próximos passos

- [Acesso Condicional no Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)
- [Começar com Acesso Condicional no Diretório Ativo Azure](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal-get-started)
