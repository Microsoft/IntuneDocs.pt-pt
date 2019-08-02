---
title: Solucionando problemas de registro de dispositivo Windows no Microsoft Intune
titleSuffix: Microsoft Intune
description: Sugestões para solucionar alguns dos problemas mais comuns ao registrar dispositivos Windows no Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/29/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: mghadial
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d76b9581cac6e9d74e83ce50400e14468a13d3e6
ms.sourcegitcommit: c715c93bb242f4fe44bbdf2fd585909854ed72b6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/30/2019
ms.locfileid: "68664179"
---
# <a name="troubleshoot-windows-device-enrollment-problems-in-microsoft-intune"></a>Solucionar problemas de registro de dispositivo Windows no Microsoft Intune

Este artigo ajuda os administradores do Intune a entender e solucionar problemas ao registrar dispositivos Windows no Intune.

## <a name="prerequisites"></a>Pré-requisitos
Antes de iniciar a solução de problemas, é importante coletar algumas informações básicas. Essas informações podem ajudá-lo a entender melhor o problema e reduzir o tempo para encontrar uma resolução.

Colete as seguintes informações sobre o problema:
- Uma licença válida do Intune foi atribuída ao usuário? Antes que os usuários possam registrar seus dispositivos, eles devem ter a licença necessária atribuída.
- A atualização mais recente está instalada no dispositivo Windows? Alguns recursos do Intune funcionam apenas com a versão mais recente do Windows. Há muitas correções para problemas conhecidos disponíveis por meio de Windows Update. A aplicação de todas as atualizações mais recentes geralmente corrige um problema de registro do dispositivo Windows. 
- Qual é a mensagem de erro exata?
- Onde você vê a mensagem de erro?
- Quando o problema foi iniciado? O registro já funcionou? 
- Qual plataforma (Android, iOS, Windows) tem o problema?
- Quantos usuários são afetados? Todos os usuários foram afetados ou apenas alguns?
- Quantos dispositivos são afetados? Todos os dispositivos foram afetados ou apenas alguns?
- O que é a autoridade de MDM? Se for System Center Configuration Manager, qual versão do Configuration Manager você está usando?
- Como o registro está sendo executado? Ele é "Traga seu próprio dispositivo" (BYOD) ou DEP (Programa de registro de dispositivos da Apple) com perfis de registro?

## <a name="error-messages"></a>Mensagens de erro

### <a name="this-user-is-not-authorized-to-enroll"></a>Este usuário não está autorizado a se registrar.

Erro 0x801c003: "Este usuário não está autorizado a se registrar. Você pode tentar fazer isso novamente ou entrar em contato com o administrador do sistema com o código de erro (0x801c0003). "
Erro 80180003: "Algo deu errado. Este usuário não está autorizado a se registrar. Você pode tentar fazer isso novamente ou entrar em contato com o administrador do sistema com o código de erro 80180003. "

**Faz** Qualquer uma das seguintes condições: 

- O usuário já registrou o número máximo de dispositivos permitidos no Intune.    
- O dispositivo está bloqueado pelas restrições de tipo de dispositivo.    
- O computador está executando o Windows 10 Home. No entanto, o registro no Intune ou ingressar no Azure AD só tem suporte no Windows 10 pro e em edições superiores.

#### <a name="resolution"></a>Resolução
Há várias soluções possíveis para esse problema:

##### <a name="remove-devices-that-were-enrolled"></a>Remover dispositivos que foram registrados
1. Inicie sessão no [portal do Azure](https://portal.azure.com/?Microsoft_Intune=1&Microsoft_Intune_DeviceSettings=true&Microsoft_Intune_Enrollment=true&Microsoft_Intune_Apps=true&Microsoft_Intune_Devices=true#blade/Microsoft_Intune_DeviceSettings/ExtensionLandingBlade/overview).    
2. Vá para **usuários** > **todos os usuários**.    
3. Selecione a conta de usuário afetada e clique em **dispositivos**.    
4. Selecione qualquer dispositivo não utilizado ou indesejado e clique em **excluir**. 

##### <a name="increase-thedevice-enrollment-limit"></a>Aumentar o limite de registro do dispositivo

> [!NOTE]
> Esse método aumenta o limite de registro de dispositivo para todos os usuários, não apenas o usuário afetado.

1. Inicie sessão no [portal do Azure](https://portal.azure.com/?Microsoft_Intune=1&Microsoft_Intune_DeviceSettings=true&Microsoft_Intune_Enrollment=true&Microsoft_Intune_Apps=true&Microsoft_Intune_Devices=true#blade/Microsoft_Intune_DeviceSettings/ExtensionLandingBlade/overview).
2. Vá para **registro** >de dispositivo **restrições de registro**e selecione **restrições de limite de dispositivo**.    
3. Aumente o valor do **limite do dispositivo**. 

##### <a name="checkdevice-type-restrictions"></a>Verificar restrições de tipo de dispositivo
1. Entre no [portal](https://portal.azure.com/?Microsoft_Intune=1&Microsoft_Intune_DeviceSettings=true&Microsoft_Intune_Enrollment=true&Microsoft_Intune_Apps=true&Microsoft_Intune_Devices=true#blade/Microsoft_Intune_DeviceSettings/ExtensionLandingBlade/overview) do Intune com uma conta de administrador global.
2. Vá para **registro** > de dispositivo**restrições de registro**e selecione a restrição **padrão** em **restrições de tipo de dispositivo**.    
3. Selecione **plataformas**e, em seguida, selecione **permitir** para **Windows (MDM)** .

    > [!IMPORTANT]
    > Se a configuração atual já for **permitir**, altere-a para **Bloquear**, salve a configuração e, em seguida, altere-a novamente para **permitir** e salve a configuração novamente. Isso redefine a configuração de registro.

4. Aguarde aproximadamente 15 minutos e, em seguida, registre o dispositivo afetado novamente.    

##### <a name="upgrade-windows-10-home"></a>Atualizar o Windows 10 Home
[Atualize o Windows 10 Home para Windows 10 pro](https://support.microsoft.com/help/12384/windows-10-upgrading-home-to-pro) ou uma edição superior. 



### <a name="this-user-is-not-allowed-to-enroll"></a>Este usuário não tem permissão para se registrar.

Erro 0x801c0003: "Este usuário não tem permissão para se registrar. Você pode tentar novamente ou entrar em contato com o administrador do sistema com o código de erro 801c0003. "

**Faz** A configuração **usuários podem ingressar dispositivos no Azure ad** está definida como **nenhum**. Isso impede que novos usuários ingressem seus dispositivos no Azure AD. Portanto, o registro do Intune falha.

#### <a name="resolution"></a>Resolução
1. Entre no [portal do Azure](https://portal.azure.com/) como administrador.    
2. Vá para **Azure Active Directory** > **dispositivos**configuraçõesdedispositivo. >     
3. Definir **os usuários podem unir dispositivos ao Azure ad** a **todos**.    
4. Registre o dispositivo novamente.   

### <a name="the-device-is-already-enrolled"></a>O dispositivo já está registrado.

Erro 8018000a: "Algo deu errado. O dispositivo já está registrado.  Você pode entrar em contato com o administrador do sistema com o código de erro 8018000a. "

**Faz** Uma das seguintes condições é verdadeira:
- Um usuário diferente já registrou o dispositivo no Intune ou ingressou no dispositivo no Azure AD. Para determinar se esse é o caso, vá para **configurações** > **contas** > **acesso corporativo**. Procure uma mensagem semelhante à seguinte: "Outro usuário no sistema já está conectado a um trabalho ou escola. Remova essa conexão corporativa ou de estudante e tente novamente. "    
- O agente cliente do Configuration Manager está instalado no computador.    

#### <a name="resolution"></a>Resolução

Use um dos seguintes métodos para resolver esse problema:

##### <a name="remove-the-other-work-or-school-account"></a>Remover a outra conta corporativa ou de estudante
1. Saia do Windows e entre usando a outra conta que registrou ou ingressou no dispositivo.    
2. Vá para **configurações** > **contas** > **acesso de trabalho**e, em seguida, remova a conta corporativa ou de estudante.
3. Saia do Windows e entre usando sua conta.    
4. Registre o dispositivo no Intune ou Ingresse o dispositivo no Azure AD. 

##### <a name="remove-the-configuration-manager-client"></a>Remover o cliente Configuration Manager
Remova o cliente de Configuration Manager e, em seguida, registre o dispositivo novamente.



### <a name="this-account-is-not-allowed-on-this-phone"></a>Esta conta não é permitida neste telefone.

Erro: "Esta conta não é permitida neste telefone. Verifique se as informações fornecidas estão corretas e tente novamente ou solicite suporte de sua empresa. "

**Faz** O usuário que tentou registrar o dispositivo não tem uma licença do Intune válida.

#### <a name="resolution"></a>Resolução
Atribua uma licença válida do Intune ao usuário e, em seguida, registre o dispositivo.


### <a name="looks-like-the-mdm-terms-of-use-endpoint-is-not-correctly-configured"></a>Parece que o ponto de extremidade de termos de uso do MDM não está configurado corretamente.

**Faz** Uma das seguintes condições é verdadeira: 
 - Você usa o MDM (gerenciamento de dispositivo móvel) para o Office 365 e o Intune no locatário, e o usuário que tenta registrar o dispositivo não tem uma licença do Intune válida ou uma licença do Office 365.     
- Os termos e condições do MDM no Azure AD estão em branco ou não contêm a URL correta.    

#### <a name="resolution"></a>Resolução

Para corrigir esse problema, use um dos seguintes métodos: 
 
##### <a name="assign-a-valid-license-to-the-user"></a>Atribuir uma licença válida ao usuário
Vá para o [centro de administração do Microsoft 365](https://portal.office.com/adminportal/home)e atribua uma licença do Intune ou do Office 365 ao usuário.

##### <a name="correct-themdm-terms-of-use-url"></a>Corrigir a URL dos termos de uso do MDM
  1. Entre no [portal do Azure](https://portal.azure.com/)e, em seguida, selecione **Azure Active Directory**.    
  2. Selecione **mobilidade (MDM e MAM)** e, em seguida, clique em **Microsoft Intune**.    
  3. Selecione **restaurar URLs de MDM padrão**, verifique se a **URL dos termos de uso do MDM** está definida como **https://portal.manage.microsoft.com/TermsofUse.aspx** .    
  4. Escolha **Guardar**.    


### <a name="something-went-wrong"></a>Algo deu errado.

Erro 80180026: "Algo deu errado. Confirme se você está usando as informações de entrada corretas e se sua organização usa esse recurso. Você pode tentar fazer isso novamente ou entrar em contato com o administrador do sistema com o código de erro 80180026. "

**Faz** Esse erro pode ocorrer quando você tenta ingressar um computador com Windows 10 no Azure AD e as duas condições a seguir são verdadeiras: 
- O registro automático do MDM está habilitado no Azure.    
- O cliente de computador do Intune (agente de PC do Intune) ou o agente cliente do Configuration Manager está instalado no computador com Windows 10.

#### <a name="resolution"></a>Resolução
Use um dos seguintes métodos para resolver esse problema:

##### <a name="disablemdm-automatic-enrollment-in-azure"></a>Desabilite o registro automático do MDM no Azure.
1. Entre no [portal do Azure](https://portal.azure.com/).    
2. Vá para **Azure Active Directory** > **mobilidade (MDM e MAM)**  > **Microsoft Intune**.    
3. Defina o **escopo de usuário do MDM** como **nenhum**e, em seguida, clique em **salvar**.    
     
##### <a name="uninstall"></a>Desinstalar
Desinstale o cliente de computador do Intune ou o agente cliente Configuration Manager do computador.    

### <a name="the-software-cannot-be-installed"></a>O software não pode ser instalado.

Erro: "O software não pode ser instalado, 0x80cf4017."

**Faz** O software cliente está desatualizado.

#### <a name="resolution"></a>Resolução
1. Entre no [https://admin.manage.microsoft.com](https://admin.manage.microsoft.com).    
2. Acesse **Administração** > **software cliente download**e clique em **baixar software cliente**.    
3. Salve o pacote de instalação e, em seguida, instale o software cliente. 


### <a name="the-account-certificate-is-not-valid-and-may-be-expired"></a>O certificado da conta não é válido e pode estar expirado.

Erro: "O certificado de conta não é válido e pode estar expirado, 0x80cf4017."

**Faz** O software cliente está desatualizado.

#### <a name="resolution"></a>Resolução
1. Entre no [https://admin.manage.microsoft.com](https://admin.manage.microsoft.com).    
2. Acesse **Administração** > **software cliente download**e clique em **baixar software cliente**.    
3. Salve o pacote de instalação e, em seguida, instale o software cliente.    

### <a name="your-organization-does-not-support-this-version-of-windows"></a>Sua organização não dá suporte a esta versão do Windows. 

Erro: "Houve um problema. Sua organização não dá suporte a esta versão do Windows.  (0x80180014) "

**Faz** O registro de MDM do Windows está desabilitado no seu locatário do Intune.

#### <a name="resolution"></a>Resolução
Para corrigir esse problema em um ambiente autônomo do Intune, siga estas etapas: 
 
1. Entre no [portal do Azure](https://portal.azure.com/) como administrador.    
2. Selecione **Intune** à esquerda e vá para **registro** > de dispositivo**restrições de registro**.    
3. Em **restrições de tipo de dispositivo**, clique em **plataformas**e selecione **permitir** para **Windows (MDM)** .    
4. Clique em **Guardar**.    
 
Para corrigir esse problema no MDM híbrido com o Intune e o Configuration Manager, siga estas etapas: 
1. Abra o console do Configuration Manager.    
2. Selecione **Administração**e, em seguida, selecione **serviços de nuvem**.    
3. Clique com o botão direito do mouse em **Microsoft Intune assinatura**e selecione **Configurar plataformas > Windows**.    
4. Marque **habilitar registro** > do Windows**aplicar** > **OK**.  


### <a name="a-setup-failure-has-occurred-during-bulk-enrollment"></a>Ocorreu uma falha na instalação durante o registro em massa.

**Faz** As contas de usuário do Azure AD no pacote de conta (Package_GUID) para o respectivo pacote de provisionamento não têm permissão para ingressar dispositivos no Azure AD. Essas contas do Azure AD são criadas automaticamente quando você configura um pacote de provisionamento com o Windows Configuration designer (WCD) ou o aplicativo configurar PCs de estudante, e essas contas são usadas para unir os dispositivos ao Azure AD.

#### <a name="resolution"></a>Resolução
1. Entre no [portal do Azure](https://portal.azure.com/) como administrador.    
2. Vá para **Azure Active Directory dispositivos > > configurações do dispositivo**.    
3. Definir **usuários pode unir dispositivos ao Azure ad** a **todos** ou **selecionados**.

   Se você escolher **selecionado**, clique em **selecionado**e, em seguida, clique em **adicionar membros** para adicionar todos os usuários que podem ingressar seus dispositivos no Azure AD. Verifique se todas as contas do Azure AD para o pacote de provisionamento foram adicionadas.
 
Para obter mais informações sobre como criar um pacote de provisionamento para o Windows Configuration designer, consulte [criar um pacote de provisionamento para Windows 10](https://docs.microsoft.com/windows/configuration/provisioning-packages/provisioning-create-package).

Para obter mais informações sobre o aplicativo configurar PCs escolares, consulte [usar o aplicativo configurar PCs escolares](https://docs.microsoft.com/education/windows/use-set-up-school-pcs-app).


### <a name="auto-mdm-enroll-failed"></a>Registro automático de MDM: Com Falhas 

Ao tentar registrar um dispositivo Windows 10 automaticamente usando Política de Grupo, você enfrenta os seguintes problemas: 
- No Agendador de tarefas, no **Microsoft** > **Windows** > **EnterpriseMgmt**, o resultado da última execução do **agendamento criado pelo cliente de registro para registrar-se automaticamente no MDM da tarefa do AAD** é o seguinte: **Registro de MDM automático do evento 76: Falha (código de erro Win32 desconhecido: 0x8018002b)**       
- No Visualizador de Eventos, o evento a seguir é registrado em **logs de aplicativos e serviços/Microsoft/Windows/DeviceManagement-Enterprise-Diagnostics-Provider/admin**:   
    ```asciidoc
    Log Name: Microsoft-Windows-DeviceManagement-Enterprise-Diagnostics-Provider/Admin
    Source: DeviceManagement-Enterprise-Diagnostics-Provider
    Event ID: 76
    Level: Error
    Description: Auto MDM Enroll: Failed (Unknown Win32 Error code: 0x80180002b)
    ```
**Faz** Uma das seguintes condições é verdadeira: 
- O UPN contém um domínio não verificado ou não roteável, como. local (como joe@contoso.local).    
- **O escopo** de usuário do MDM está definido como **nenhum**. 

#### <a name="resolution"></a>Resolução
Se o UPN contiver um domínio não verificado ou não roteável, siga estas etapas: 

1. No servidor em que Active Directory Domain Services (AD DS) é executado, abra **Active Directory usuários e computadores** digitando **DSA. msc** na caixa de diálogo **executar** e, em seguida, clique em **OK**.    
2. Clique em **usuários** em seu domínio e, em seguida, faça o seguinte:  
    - Se houver apenas um usuário afetado, clique com o botão direito do mouse no usuário e clique em **Propriedades**. Na guia **conta** , na lista suspensa sufixo UPN, em **nome de logon do usuário**, selecione um sufixo UPN válido, como contoso.com, e clique em **OK**.    
    - Se houver vários usuários afetados, selecione os usuários, no menu **ação** , clique em **Propriedades**. Na guia **conta** , marque a caixa de seleção **sufixo UPN** , selecione um sufixo upn válido, como contoso.com na lista suspensa, e clique em **OK**.
3. Aguarde a próxima sincronização ou Force uma sincronização Delta do servidor de sincronização executando os seguintes comandos em um prompt do PowerShell com privilégios elevados:
    ```powershell
    Import-Module ADSync
    Start-ADSyncSyncCycle -PolicyType Delta
    ```

Se o **escopo** de usuário do MDM for definido como **nenhum**, siga estas etapas: 
 
1. Entre no [portal do Azure](https://portal.azure.com/)e, em seguida, selecione **Azure Active Directory**.
2. Selecione **mobilidade (MDM e MAM)** e, em seguida, selecione **Microsoft Intune**.    
3. Defina o **escopo de usuário do MDM** como **todos**. Ou defina o **escopo de usuário do MDM** para **alguns**e selecione os grupos que podem registrar automaticamente seus dispositivos Windows 10.    
4. Defina o **escopo de usuário do MAM** como **nenhum**.


## <a name="next-steps"></a>Passos seguintes

- [Resolução de problemas de inscrição de dispositivos no Intune](troubleshoot-device-enrollment-in-intune.md)
- [Faça uma pergunta no fórum do Intune](https://social.technet.microsoft.com/Forums/%7Blang-locale%7D/home?category=microsoftintune&filter=alltypes&sort=lastpostdesc)
- [Consulte o blog da equipe de suporte do Microsoft Intune](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/bg-p/IntuneCustomerSuccess)
- [Confira o blog do Microsoft Enterprise Mobility e segurança](https://techcommunity.microsoft.com/t5/Azure-Active-Directory-Identity/Announcing-the-public-preview-of-Azure-AD-group-based-license/ba-p/245210)
- [Obter suporte para Microsoft Intune](https://docs.microsoft.com/intune/get-support) 