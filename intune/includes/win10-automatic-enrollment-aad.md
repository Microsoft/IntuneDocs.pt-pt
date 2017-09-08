## <a name="enable-windows-10-automatic-enrollment"></a>Ativar a inscrição automática de dispositivos Windows 10

A inscrição automática permite que os utilizadores inscrevam os respetivos dispositivos com Windows 10 no Intune. Para se inscreverem, os utilizadores adicionam as respetivas contas profissionais aos dispositivos pessoais ou associam os dispositivos pertencentes à empresa ao Azure Active Directory. Em segundo plano, o dispositivo é registado e associa-se ao Azure Active Directory. Depois de registado, o dispositivo é gerido com o Intune.

**Pré-requisitos**
- Subscrição do Azure Active Directory Premium ([subscrição de avaliação](http://go.microsoft.com/fwlink/?LinkID=816845))
- Subscrição do Microsoft Intune


### <a name="configure-automatic-mdm-enrollment"></a>Configurar a inscrição MDM automática

1. Inicie sessão no [portal do Azure](https://portal.azure.com) e selecione **Azure Active Directory**.

  ![Captura de ecrã do portal do Azure](../media/auto-enroll-azure-main.png)

2. Selecione **Mobilidade (MDM e MAM)**.

  ![Captura de ecrã do portal do Azure](../media/auto-enroll-mdm.png)

3. Selecione **Microsoft Intune**.

  ![Captura de ecrã do portal do Azure](../media/auto-enroll-intune.png)

4. Configure **Âmbito do Utilizador de MDM**. Especifique os dispositivos de utilizadores que devem ser geridos pelo Microsoft Intune. Os dispositivos com Windows 10 podem ser automaticamente inscritos na gestão com o Microsoft Intune.

  - **Nenhum**
  - **Alguns**
  - **Todos**

   ![Captura de ecrã do portal do Azure](../media/auto-enroll-scope.png)

5. Utilize os valores predefinidos para os seguintes URLs:
    - **URL dos Termos de utilização de MDM**
    - **URL de Deteção de MDM**
    - **URL de Conformidade de MDM**

    > [!IMPORTANT]
    > Se o **âmbito do utilizador MAM** e a inscrição na MDM automática (**âmbito do utilizador MDM**) estiverem ativados num grupo, apenas a MAM será ativada. Apenas a MAM será adicionada para os utilizadores nesse grupo quando estes associarem o respetivo dispositivo pessoal à área de trabalho. Os dispositivos não são automaticamente inscritos na MDM.

6. Selecione **Guardar**.

Por predefinição, a autenticação de dois fatores não está ativada para o serviço. No entanto, é recomendada a autenticação de dois fatores ao registar um dispositivo. Para ativar a autenticação de dois fatores, configure um fornecedor de autenticação de dois fatores no AD e configure as contas de utilizador para a autenticação multifator. Veja [Introdução ao Servidor Multi-Factor Authentication do Microsoft Azure](https://docs.microsoft.com/azure/multi-factor-authentication/multi-factor-authentication-get-started-cloud).
