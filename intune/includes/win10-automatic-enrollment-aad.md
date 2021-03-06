---
ms.openlocfilehash: 748141dc494e28f25a09039a7a500411af76ace7
ms.sourcegitcommit: 52475fcd8d05d2f6b858d780ebb3d88eaadb0849
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/15/2020
ms.locfileid: "76037731"
---
## <a name="enable-windows-10-automatic-enrollment"></a>Ativar a inscrição automática de dispositivos Windows 10

A inscrição automática permite que os utilizadores inscrevam os respetivos dispositivos com Windows 10 no Intune. Para se inscreverem, os utilizadores adicionam as respetivas contas profissionais aos dispositivos pessoais ou associam os dispositivos pertencentes à empresa ao Azure Active Directory. Em segundo plano, o dispositivo é registado e associa-se ao Azure Active Directory. Depois de registado, o dispositivo é gerido com o Intune.

**Pré-requisitos**

- Subscrição do Azure Active Directory Premium ([subscrição de avaliação](https://go.microsoft.com/fwlink/?LinkID=816845))
- Subscrição do Microsoft Intune

### <a name="configure-automatic-mdm-enrollment"></a>Configurar a inscrição MDM automática

1. Inicie sessão no [portal do Azure](https://portal.azure.com) e selecione **Azure Active Directory**.

   ![Captura de ecrã do portal do Azure](../enrollment/media/windows-enroll/auto-enroll-azure-main.png)

2. Selecione **Mobilidade (MDM e MAM)** .

   ![Captura de ecrã do portal do Azure](../enrollment/media/windows-enroll/auto-enroll-mdm.png)

3. Selecione **Microsoft Intune**.

   ![Captura de ecrã do portal do Azure](../enrollment/media/windows-enroll/auto-enroll-intune.png)

4. Configure **Âmbito do Utilizador de MDM**. Especifique os dispositivos de utilizadores que devem ser geridos pelo Microsoft Intune. Os dispositivos com Windows 10 podem ser automaticamente inscritos na gestão com o Microsoft Intune.

   - **Nenhum** – Inscrição automática de MDM desativada
   - **Alguns** – Selecione os **Grupos** que podem inscrever automaticamente os dispositivos Windows 10
   - **Todos** – Todos os utilizadores podem inscrever automaticamente os dispositivos Windows 10

      > [!IMPORTANT]
      > Para dispositivos BYOD, o escopo de usuário MAM terá precedência se o escopo do usuário de MAM e o escopo do usuário do MDM (registro automático do MDM) estiverem habilitados para todos os usuários (ou os mesmos grupos de usuários). O dispositivo usará as políticas de WIP (proteção de informações do Windows) (se você as configurou) em vez de ser registrado em MDM.
      >
      > Para dispositivos corporativos, o escopo de usuário do MDM terá precedência se ambos os escopos estiverem habilitados. Os dispositivos obtêm MDM registrado.

   > [!NOTE]
   > O escopo de usuário do MDM deve ser definido como um grupo do Azure AD que contém objetos de usuário.

   ![Captura de ecrã do portal do Azure](../enrollment/media/windows-enroll/auto-enroll-scope.png)

5. Utilize os valores predefinidos para os seguintes URLs:
    - **URL dos Termos de utilização de MDM**
    - **URL de Deteção de MDM**
    - **URL de Conformidade de MDM**

6. Selecione **Guardar**.

Por predefinição, a autenticação de dois fatores não está ativada para o serviço. No entanto, é recomendada a autenticação de dois fatores ao registar um dispositivo. Para ativar a autenticação de dois fatores, configure um fornecedor de autenticação de dois fatores no AD e configure as contas de utilizador para a autenticação multifator. Veja [Introdução ao Servidor Multi-Factor Authentication do Microsoft Azure](https://docs.microsoft.com/azure/multi-factor-authentication/multi-factor-authentication-get-started-cloud).
