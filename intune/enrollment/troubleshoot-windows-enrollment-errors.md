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
ms.subservice: enrollment
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: mghadial
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0e4f8768129ab035b4a935a900f62ab6f3379edd
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/05/2019
ms.locfileid: "74832649"
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
- Quando começou o problema? O registro já funcionou? 
- Qual plataforma (Android, iOS, Windows) tem o problema?
- Quantos usuários são afetados? Todos os usuários foram afetados ou apenas alguns?
- Quantos dispositivos são afetados? Todos os dispositivos foram afetados ou apenas alguns?
- O que é a autoridade de MDM? Se for System Center Configuration Manager, qual versão do Configuration Manager você está usando?
- Como o registro está sendo executado? Ele é "Traga seu próprio dispositivo" (BYOD) ou DEP (Programa de registro de dispositivos da Apple) com perfis de registro?

## <a name="error-messages"></a>Mensagens de erro

### <a name="this-user-is-not-authorized-to-enroll"></a>Este usuário não está autorizado a se registrar.

Erro 0x801c003: "este usuário não está autorizado a se registrar. Você pode tentar fazer isso novamente ou entrar em contato com o administrador do sistema com o código de erro (0x801c0003). "
Erro 80180003: "algo deu errado. Este usuário não está autorizado a se registrar. Você pode tentar fazer isso novamente ou entrar em contato com o administrador do sistema com o código de erro 80180003. "

**Causa:** Qualquer uma das seguintes condições: 

- O usuário já registrou o número máximo de dispositivos permitidos no Intune.    
- O dispositivo está bloqueado pelas restrições de tipo de dispositivo.    
- O computador está executando o Windows 10 Home. No entanto, o registro no Intune ou ingressar no Azure AD só tem suporte no Windows 10 pro e em edições superiores.

#### <a name="resolution"></a>Resolução
Há várias soluções possíveis para esse problema:

##### <a name="remove-devices-that-were-enrolled"></a>Remover dispositivos que foram registrados
1. Entre no centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).    
2. Vá para **usuários** > **todos os usuários**.    
3. Selecione a conta de usuário afetada e clique em **dispositivos**.    
4. Selecione qualquer dispositivo não utilizado ou indesejado e clique em **excluir**. 

##### <a name="increase-the-device-enrollment-limit"></a>Aumentar o limite de registro do dispositivo

> [!NOTE]
> Esse método aumenta o limite de registro de dispositivo para todos os usuários, não apenas o usuário afetado.

1. Entre no centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Vá para **dispositivos** > **restrições de registro** > **padrão** (em restrições de **limite de dispositivo**) > **Propriedades** > **Editar** (ao lado do **limite de dispositivo**) > aumentar o limite de **dispositivo** (máximo de 15) > **revisão + salvar**.    
 

##### <a name="check-device-type-restrictions"></a>Verificar restrições de tipo de dispositivo
1. Entre no centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) com uma conta de administrador global.
2. Vá para **dispositivos** > **restrições de registro**e selecione a restrição **padrão** em **restrições de tipo de dispositivo**.    
3. Selecione **plataformas**e, em seguida, selecione **permitir** para **Windows (MDM)** .

    > [!IMPORTANT]
    > Se a configuração atual já for **permitir**, altere-a para **Bloquear**, salve a configuração e, em seguida, altere-a novamente para **permitir** e salve a configuração novamente. Isso redefine a configuração de registro.

4. Aguarde aproximadamente 15 minutos e, em seguida, registre o dispositivo afetado novamente.    

##### <a name="upgrade-windows-10-home"></a>Atualizar o Windows 10 Home
[Atualize o Windows 10 Home para Windows 10 pro](https://support.microsoft.com/help/12384/windows-10-upgrading-home-to-pro) ou uma edição superior. 



### <a name="this-user-is-not-allowed-to-enroll"></a>Este usuário não tem permissão para se registrar.

Erro 0x801c0003: "este usuário não tem permissão para se registrar. Você pode tentar novamente ou entrar em contato com o administrador do sistema com o código de erro 801c0003. "

**Causa:** A configuração **usuários podem ingressar dispositivos no Azure ad** está definida como **nenhum**. Isso impede que novos usuários ingressem seus dispositivos no Azure AD. Portanto, o registro do Intune falha.

#### <a name="resolution"></a>Resolução
1. Entre no [portal do Azure](https://portal.azure.com/) como administrador.    
2. Vá para **Azure Active Directory** **dispositivos** >  > **configurações do dispositivo**.    
3. Definir **os usuários podem unir dispositivos ao Azure ad** a **todos**.    
4. Registre o dispositivo novamente.   

### <a name="the-device-is-already-enrolled"></a>O dispositivo já está registrado.

Erro 8018000a: "algo deu errado. O dispositivo já está registrado.  Você pode entrar em contato com o administrador do sistema com o código de erro 8018000a. "

**Causa:** Uma das seguintes condições é verdadeira:
- Um usuário diferente já registrou o dispositivo no Intune ou ingressou no dispositivo no Azure AD. Para determinar se esse é o caso, acesse **configurações** > **contas** > **acesso de trabalho**. Procure uma mensagem semelhante à seguinte: "outro usuário no sistema já está conectado a um trabalho ou escola. Remova essa conexão corporativa ou de estudante e tente novamente. "    
- O agente cliente do Configuration Manager está instalado no computador.    

#### <a name="resolution"></a>Resolução

Use um dos seguintes métodos para resolver esse problema:

##### <a name="remove-the-other-work-or-school-account"></a>Remover a outra conta corporativa ou de estudante
1. Saia do Windows e entre usando a outra conta que registrou ou ingressou no dispositivo.    
2. Acesse **configurações** > **contas** > **acesso de trabalho**e, em seguida, remova a conta corporativa ou de estudante.
3. Saia do Windows e entre usando sua conta.    
4. Registre o dispositivo no Intune ou Ingresse o dispositivo no Azure AD. 

##### <a name="remove-the-configuration-manager-client"></a>Remover o cliente Configuration Manager
Remova o cliente de Configuration Manager e, em seguida, registre o dispositivo novamente.



### <a name="this-account-is-not-allowed-on-this-phone"></a>Esta conta não é permitida neste telefone.

Erro: "esta conta não é permitida neste telefone. Verifique se as informações fornecidas estão corretas e tente novamente ou solicite suporte de sua empresa. "

**Causa:** O usuário que tentou registrar o dispositivo não tem uma licença do Intune válida.

#### <a name="resolution"></a>Resolução
Atribua uma licença válida do Intune ao usuário e, em seguida, registre o dispositivo.


### <a name="looks-like-the-mdm-terms-of-use-endpoint-is-not-correctly-configured"></a>Parece que o ponto de extremidade de termos de uso do MDM não está configurado corretamente.

**Causa:** Uma das seguintes condições é verdadeira: 
 - Você usa o MDM (gerenciamento de dispositivo móvel) para o Office 365 e o Intune no locatário, e o usuário que tenta registrar o dispositivo não tem uma licença do Intune válida ou uma licença do Office 365.     
- Os termos e condições do MDM no Azure AD estão em branco ou não contêm a URL correta.    

#### <a name="resolution"></a>Resolução

Para corrigir esse problema, use um dos seguintes métodos: 
 
##### <a name="assign-a-valid-license-to-the-user"></a>Atribuir uma licença válida ao usuário
Vá para o [centro de administração do Microsoft 365](https://portal.office.com/adminportal/home)e atribua uma licença do Intune ou do Office 365 ao usuário.

##### <a name="correct-the-mdm-terms-of-use-url"></a>Corrigir a URL dos termos de uso do MDM
  1. Entre no [portal do Azure](https://portal.azure.com/)e, em seguida, selecione **Azure Active Directory**.    
  2. Selecione **mobilidade (MDM e MAM)** e, em seguida, clique em **Microsoft Intune**.    
  3. Selecione **restaurar URLs de MDM padrão**, verifique se a **URL dos termos de uso do MDM** está definida como **https://portal.manage.microsoft.com/TermsofUse.aspx** .    
  4. Escolha **Guardar**.    


### <a name="something-went-wrong"></a>Ocorreu um problema.

Erro 80180026: "algo deu errado. Confirme se você está usando as informações de entrada corretas e se sua organização usa esse recurso. Você pode tentar fazer isso novamente ou entrar em contato com o administrador do sistema com o código de erro 80180026. "

**Causa:** Esse erro pode ocorrer quando você tenta ingressar um computador com Windows 10 no Azure AD e as duas condições a seguir são verdadeiras: 
- O registro automático do MDM está habilitado no Azure.    
- O cliente de computador do Intune (agente de PC do Intune) ou o agente cliente do Configuration Manager está instalado no computador com Windows 10.

#### <a name="resolution"></a>Resolução
Use um dos seguintes métodos para resolver esse problema:

##### <a name="disable-mdm-automatic-enrollment-in-azure"></a>Desabilite o registro automático do MDM no Azure.
1. Inicie sessão no [portal do Azure](https://portal.azure.com/).    
2. Vá para **Azure Active Directory** > **Mobility (MDM e MAM)**  > **Microsoft Intune**.    
3. Defina o **escopo de usuário do MDM** como **nenhum**e, em seguida, clique em **salvar**.    
     
##### <a name="uninstall"></a>Desinstalar
Desinstale o cliente de computador do Intune ou o agente cliente Configuration Manager do computador.    

### <a name="the-software-cannot-be-installed"></a>O software não pode ser instalado.

Erro: "o software não pode ser instalado, 0x80cf4017."

**Causa:** O software cliente está desatualizado.

#### <a name="resolution"></a>Resolução
1. Inicie sessão em [https://admin.manage.microsoft.com](https://admin.manage.microsoft.com).    
2. Vá para **administrador** > **download do software cliente**e clique em **baixar software cliente**.    
3. Salve o pacote de instalação e, em seguida, instale o software cliente. 


### <a name="the-account-certificate-is-not-valid-and-may-be-expired"></a>O certificado da conta não é válido e pode estar expirado.

Erro: "o certificado da conta não é válido e pode estar expirado, 0x80cf4017."

**Causa:** O software cliente está desatualizado.

#### <a name="resolution"></a>Resolução
1. Inicie sessão em [https://admin.manage.microsoft.com](https://admin.manage.microsoft.com).    
2. Vá para **administrador** > **download do software cliente**e clique em **baixar software cliente**.    
3. Salve o pacote de instalação e, em seguida, instale o software cliente.    

### <a name="your-organization-does-not-support-this-version-of-windows"></a>Sua organização não dá suporte a esta versão do Windows. 

Erro: "houve um problema. Sua organização não dá suporte a esta versão do Windows.  (0x80180014) "

**Causa:** O registro de MDM do Windows está desabilitado no seu locatário do Intune.

#### <a name="resolution"></a>Resolução
Para corrigir esse problema em um ambiente autônomo do Intune, siga estas etapas: 
 
1. No [centro de administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), escolha **dispositivos** > **restrições de registro** > escolha um tipo de dispositivo restrição.    
2. Escolha **propriedades** > **Editar** (ao lado de **configurações de plataforma**) > **permitir** para **Windows (MDM)** .    
3. Clique em **examinar + salvar**.    
 
Para corrigir esse problema no MDM híbrido com o Intune e o Configuration Manager, siga estas etapas: 
1. Abra a consola do Configuration Manager.    
2. Selecione **Administração**e, em seguida, selecione **serviços de nuvem**.    
3. Clique com o botão direito do mouse em **Microsoft Intune assinatura**e selecione **Configurar plataformas > Windows**.    
4. Marque **habilitar registro do Windows** > **aplicar** > **OK**.  


### <a name="a-setup-failure-has-occurred-during-bulk-enrollment"></a>Ocorreu uma falha na instalação durante o registro em massa.

**Causa:** As contas de usuário do Azure AD no pacote de conta (Package_GUID) para o respectivo pacote de provisionamento não têm permissão para ingressar dispositivos no Azure AD. Essas contas do Azure AD são criadas automaticamente quando você configura um pacote de provisionamento com o Windows Configuration designer (WCD) ou o aplicativo configurar PCs de estudante, e essas contas são usadas para unir os dispositivos ao Azure AD.

#### <a name="resolution"></a>Resolução
1. Entre no [portal do Azure](https://portal.azure.com/) como administrador.    
2. Vá para **Azure Active Directory dispositivos > > configurações do dispositivo**.    
3. Definir **usuários pode unir dispositivos ao Azure ad** a **todos** ou **selecionados**.

   Se você escolher **selecionado**, clique em **selecionado**e, em seguida, clique em **adicionar membros** para adicionar todos os usuários que podem ingressar seus dispositivos no Azure AD. Verifique se todas as contas do Azure AD para o pacote de provisionamento foram adicionadas.
 
Para obter mais informações sobre como criar um pacote de provisionamento para o Windows Configuration designer, consulte [criar um pacote de provisionamento para Windows 10](https://docs.microsoft.com/windows/configuration/provisioning-packages/provisioning-create-package).

Para obter mais informações sobre o aplicativo configurar PCs escolares, consulte [usar o aplicativo configurar PCs escolares](https://docs.microsoft.com/education/windows/use-set-up-school-pcs-app).


### <a name="auto-mdm-enroll-failed"></a>Registro de MDM automático: falha 

Ao tentar registrar um dispositivo Windows 10 automaticamente usando Política de Grupo, você enfrenta os seguintes problemas: 
- No Agendador de Tarefas, em **Microsoft** > **Windows** > **EnterpriseMgmt**, o resultado da última execução do **agendamento criado pelo cliente de registro para registrar-se automaticamente no MDM da** tarefa do AAD é o seguinte: **evento 76 registro de MDM automático: falha (código de erro Win32 desconhecido: 0x8018002b)**       
- No Visualizador de Eventos, o evento a seguir é registrado em **logs de aplicativos e serviços/Microsoft/Windows/DeviceManagement-Enterprise-Diagnostics-Provider/admin**:   
    ```asciidoc
    Log Name: Microsoft-Windows-DeviceManagement-Enterprise-Diagnostics-Provider/Admin
    Source: DeviceManagement-Enterprise-Diagnostics-Provider
    Event ID: 76
    Level: Error
    Description: Auto MDM Enroll: Failed (Unknown Win32 Error code: 0x80180002b)
    ```
**Causa:** Uma das seguintes condições é verdadeira: 
- O UPN contém um domínio não verificado ou não roteável, como. local (como joe@contoso.local).    
- O **escopo de usuário do MDM** está definido como **nenhum**. 

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

Se o **escopo de usuário do MDM** for definido como **nenhum**, siga estas etapas: 
 
1. Entre no [portal do Azure](https://portal.azure.com/)e, em seguida, selecione **Azure Active Directory**.
2. Selecione **mobilidade (MDM e MAM)** e, em seguida, selecione **Microsoft Intune**.    
3. Defina o **escopo de usuário do MDM** como **todos**. Ou defina o **escopo de usuário do MDM** para **alguns**e selecione os grupos que podem registrar automaticamente seus dispositivos Windows 10.    
4. Defina o **escopo de usuário do MAM** como **nenhum**.


### <a name="an-error-occurred-while-creating-autopilot-profile"></a>Ocorreu um erro ao criar o perfil do AutoPilot.

**Causa:** O formato de nomenclatura especificado do modelo de nome do dispositivo não atende aos requisitos. Por exemplo, você usa letras minúsculas para a macro serial, como% serial% em vez de% SERIAL%.

#### <a name="resolution"></a>Resolução

Certifique-se de que o formato de nomenclatura atenda aos seguintes requisitos:

- Crie um nome exclusivo para seus dispositivos. Os nomes devem ter 15 caracteres ou menos e podem conter letras (a-z, A-Z), números (0-9) e hifens (‐).
- Não podem conter apenas números.
- Os nomes não podem conter espaço em branco.
- Use a macro% SERIAL% para adicionar um número de série específico de hardware. Ou use o% RAND: < # of digits >% macro para adicionar uma cadeia de caracteres aleatória de números, a cadeia de caracteres contém < # de dígitos > dígitos. Por exemplo, MYPC-% RAND: 6% gera um nome como MYPC-123456.

### <a name="something-went-wrong-oobeidps"></a>Ocorreu um problema. OOBEIDPS.

**Causa:** Esse problema ocorre se houver um proxy, firewall ou outro dispositivo de rede que está bloqueando o acesso ao IdP (provedor de identidade).

#### <a name="resolution"></a>Resolução
Verifique se o acesso necessário aos serviços baseados na Internet para o piloto automático não está bloqueado. Para obter mais informações, consulte [requisitos de rede do Windows AutoPilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-autopilot-requirements-network).


### <a name="registering-your-device-for-mobile-management-failed3-0x801c03ea"></a>Registrando seu dispositivo para o gerenciamento móvel (com falha: 3, 0x801C03EA).

**Causa:** O dispositivo tem um chip TPM que dá suporte à versão 2,0, mas ainda não foi atualizado para a versão 2,0.

#### <a name="resolution"></a>Resolução
Atualize o chip do TPM para a versão 2,0.

Se o problema persistir, verifique se o mesmo dispositivo está em dois grupos atribuídos, com cada grupo sendo atribuído a um perfil de piloto automático diferente. Se estiver em dois grupos, determine qual perfil do AutoPilot deve ser aplicado ao dispositivo e, em seguida, remova a atribuição do outro perfil.

Para obter mais informações sobre como implantar um dispositivo Windows no modo de quiosque com o piloto automático, consulte [implantando um quiosque usando o Windows AutoPilot](https://blogs.technet.microsoft.com/mniehaus/2018/06/07/deploying-a-kiosk-using-windows-autopilot/).


### <a name="securing-your-hardware-failed-0x800705b4"></a>Protegendo seu hardware (com falha: 0x800705b4).

Erro 800705b4: 
```
Securing your hardware (Failed: 0x800705b4)
Joining your organization's network (Previous step failed)
Registering your device for mobile management (Previous step failed)
```

**Causa:** O dispositivo Windows de destino não atende a nenhum dos seguintes requisitos:

- O dispositivo deve ter um chip TPM 2,0 físico. Dispositivos com TPMs virtuais (por exemplo, VMs do Hyper-V) ou chips do TPM 1,2 não funcionam com o modo de implantação automática.
- O dispositivo deve estar executando uma das seguintes versões do Windows:
    - Windows 10 Build 1703 ou uma versão posterior.
    - Se o ingresso no Azure AD híbrido for usado, o Windows 10 Build 1809 ou uma versão posterior.


#### <a name="resolution"></a>Resolução
Verifique se o dispositivo de destino atende aos dois requisitos descritos na seção **causa** .

Para obter mais informações sobre como implantar um dispositivo Windows no modo de quiosque com o piloto automático, consulte [implantando um quiosque usando o Windows AutoPilot](https://blogs.technet.microsoft.com/mniehaus/2018/06/07/deploying-a-kiosk-using-windows-autopilot/).


### <a name="something-went-wrong-error-code-80070774"></a>Ocorreu um problema. Código de erro 80070774.

Erro 0x80070774: algo deu errado. Confirme se você está usando as informações de entrada corretas e se sua organização usa esse recurso. Você pode tentar fazer isso novamente ou entrar em contato com o administrador do sistema com o código de erro 80070774.

Normalmente, esse problema ocorre antes de o dispositivo ser reiniciado em um cenário híbrido do Azure AD Pilot, quando o dispositivo atinge o tempo limite durante a tela de entrada inicial. Isso significa que o controlador de domínio não pode ser encontrado ou alcançado com êxito devido a problemas de conectividade. Ou que o dispositivo entrou em um estado que não pode ingressar no domínio.

**Causa:** A causa mais comum é que a junção híbrida do Azure AD está sendo usada e o recurso atribuir usuário está configurado no perfil do AutoPilot. O uso do recurso atribuir usuário executa uma junção do Azure AD no dispositivo durante a tela de entrada inicial que coloca o dispositivo em um estado em que ele não pode ingressar no seu domínio local. Portanto, o recurso atribuir usuário deve ser usado somente em cenários de ingresso automático no Azure AD padrão.  O recurso não deve ser usado em cenários de junção híbridas do Azure AD.

#### <a name="resolution"></a>Resolução

1. No [centro de administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), escolha **dispositivos** de ** > dispositivos Windows > ** **Windows**.
2. Selecione o dispositivo que está enfrentando o problema > clique nas reticências (...) no lado mais à direita.
3. Selecione **Cancelar atribuição de usuário** e aguarde a conclusão do processo.
4. Verifique se o perfil de AutoPilot do Azure AD híbrido foi atribuído antes de tentar novamente o OOBE.

#### <a name="second-resolution"></a>Segunda resolução
Se o problema persistir, no servidor que hospeda o conector do Intune ingressar no domínio offline, verifique se a ID do evento 30312 está registrada no log do serviço do conector do ODJ. O evento 30312 é semelhante ao seguinte:

```
Log Name:      ODJ Connector Service
Source:        ODJ Connector Service Source
Event ID:      30132
Level:         Error
Description:
{
          "Metric":{
                   "Dimensions":{
                             "RequestId":"<RequestId>",
                             "DeviceId":"<DeviceId>",
                             "DomainName":"contoso.com",
                             "ErrorCode":"5",
                             "RetryCount":"1",
                              "ErrorDescription":"Failed to get the ODJ Blob. The ODJ connector does not have sufficient privileges to complete the operation",
                              "InstanceId":"<InstanceId>",
                              "DiagnosticCode":"0x00000800",
                              "DiagnosticText":"Failed to get the ODJ Blob. The ODJ connector does not have sufficient privileges to complete the operation [Exception Message: \"DiagnosticException: 0x00000800. Failed to get the ODJ Blob. The ODJ connector does not have sufficient privileges to complete the operation\"] [Exception Message: \"Failed to call NetProvisionComputerAccount machineName=<ComputerName>\"]"
                   },
                   "Name":"RequestOfflineDomainJoinBlob_Failure",
                   "Value":0
          }
}
```

Esse problema é geralmente causado pela delegação incorreta de permissões para a unidade organizacional em que os dispositivos do Windows AutoPilot são criados. Para obter mais informações, consulte [aumentar o limite de conta de computador na unidade organizacional](windows-autopilot-hybrid.md#increase-the-computer-account-limit-in-the-organizational-unit).

1. Abra **Active Directory usuários e computadores (DSA. msc)** .
2. Clique com o botão direito do mouse na unidade organizacional que será usada para criar computadores ingressados no Azure AD híbrido > **delegar controle**.
3. No assistente **de delegação de controle** , selecione **avançar** > **Adicionar** > **tipos de objeto**.
4. No painel **tipos de objeto** , marque a caixa de seleção **computadores** > **OK**.
5. No painel **Selecionar usuários**, **computadores**ou **grupos** , na caixa **Inserir os nomes de objeto a serem selecionados** , digite o nome do computador onde o conector está instalado.
6. Selecione **verificar nomes** para validar sua entrada > **OK** > **Avançar**.
7. Selecione **criar uma tarefa personalizada para delegar** > **Avançar**.
8. Marque a caixa de seleção **apenas os seguintes objetos na pasta** e, em seguida, marque as caixas de seleção **objetos de computador**, **criar objetos selecionados nesta pasta**e **excluir objetos selecionados nesta pasta** .
9. Selecione **Seguinte**.
10. Em **permissões**, marque a caixa de seleção **controle total** . Essa ação seleciona todas as outras opções.
11. Selecione **Seguinte** > **Concluir**.

## <a name="next-steps"></a>Próximos passos

- [Resolução de problemas de inscrição de dispositivos no Intune](../troubleshoot-device-enrollment-in-intune.md)
- [Faça uma pergunta no fórum do Intune](https://social.technet.microsoft.com/Forums/%7Blang-locale%7D/home?category=microsoftintune&filter=alltypes&sort=lastpostdesc)
- [Consulte o blog da equipe de suporte do Microsoft Intune](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/bg-p/IntuneCustomerSuccess)
- [Confira o blog do Microsoft Enterprise Mobility e segurança](https://techcommunity.microsoft.com/t5/Azure-Active-Directory-Identity/Announcing-the-public-preview-of-Azure-AD-group-based-license/ba-p/245210)
- [Obter suporte para Microsoft Intune](../fundamentals/get-support.md)
- [Localizar erros de registro de cogerenciamento](https://docs.microsoft.com/sccm/comanage/how-to-monitor#enrollment-errors)