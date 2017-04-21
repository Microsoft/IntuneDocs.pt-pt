## <a name="enable-windows-10-automatic-enrollment"></a>Ativar a inscrição automática de dispositivos Windows 10

A inscrição automática permite aos utilizadores inscrever PCs Windows 10 e dispositivos Windows 10 Mobile pertencentes à empresa ou pessoais no Intune, ao adicionar uma conta profissional ou escolar e ao aceitar que sejam geridos. Tão simples quanto isto. Em segundo plano, o dispositivo do utilizador regista e associa-se ao Azure Active Directory. Depois de registado, o dispositivo é gerido com o Intune.

**Pré-requisitos**
- Subscrição do Azure Active Directory Premium ([subscrição de avaliação](http://go.microsoft.com/fwlink/?LinkID=816845))
- Subscrição do Microsoft Intune


### <a name="configure-automatic-mdm-enrollment"></a>Configurar a inscrição MDM automática

1. Inicie sessão no [portal de gestão do Azure](https://portal.azure.com) (https://manage.windowsazure.com) e selecione **Azure Active Directory**.

  ![Captura de ecrã do portal do Azure](../media/auto-enroll-azure-main.png)

2. Selecione **Mobilidade (MDM e MAM)**.

  ![Captura de ecrã do portal do Azure](../media/auto-enroll-mdm.png)

3. Selecione **Microsoft Intune**.

  ![Captura de ecrã do portal do Azure](../media/auto-enroll-intune.png)

4. Configure os utilizadores a serem inscritos automaticamente.

  ![Captura de ecrã do portal do Azure](../media/auto-enroll-scope.png)

  Utilize os valores predefinidos para os seguintes URLs:
  - **Inscrição MDM**
  - **Termos de Utilização de MDM**
  - **Conformidade de MDM**

5. Especifique os dispositivos de utilizadores que devem ser geridos pelo Microsoft Intune. Os dispositivos Windows 10 dos utilizadores serão automaticamente inscritos na gestão com o Microsoft Intune.

  - **Todos**
  - **GRUPOS**
  - **Nenhum**

6. Selecione **Guardar**.
