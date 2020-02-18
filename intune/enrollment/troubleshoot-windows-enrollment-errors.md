---
title: Problemas de resolução de problemas de registo de dispositivos Windows no Microsoft Intune
titleSuffix: Microsoft Intune
description: Sugestões para resolver problemas quando se matriculam dispositivos Windows em Intune.
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
ms.openlocfilehash: 70b7fbaa29434c775720ab423f38e29bc329861a
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/17/2020
ms.locfileid: "77415162"
---
# <a name="troubleshoot-windows-device-enrollment-problems-in-microsoft-intune"></a>Problemas de resolução de problemas de registo de dispositivos Windows em Microsoft Intune

Este artigo ajuda os administradores intune a compreender e a resolver problemas ao inscrever dispositivos Windows em Intune.

## <a name="prerequisites"></a>Pré-requisitos
Antes de começar a resolver problemas, é importante recolher algumainformação básica. Esta informação pode ajudá-lo a entender melhor o problema e reduzir o tempo para encontrar uma resolução.

Recolher as seguintes informações sobre o problema:
- Uma licença Intune válida é atribuída ao utilizador? Antes de os utilizadores poderem inscrever os seus dispositivos, devem ter a licença necessária atribuída.
- A mais recente atualização está instalada no dispositivo Windows? Algumas funcionalidades em Intune funcionam apenas com a versão mais recente do Windows. Existem muitas correções para problemas conhecidos disponíveis através do Windows Update. Aplicar todas as atualizações mais recentes corrige frequentemente um problema de inscrição de dispositivos Windows. 
- Qual é a mensagem exata de erro?
- Onde vê a mensagem de erro?
- Quando começou o problema? A inscrição já funcionou? 
- Que plataforma (Android, iOS/iPadOS, Windows) tem o problema?
- Quantos utilizadores são afetados? Todos os utilizadores são afetados ou apenas alguns?
- Quantos dispositivos são afetados? Todos os dispositivos são afetados ou apenas alguns?
- O que é a autoridade do MDM?
- Como é que as inscrições estão a ser realizadas? É "Bring your own device" (BYOD) ou Apple Device Registration Program (DEP) com perfis de inscrição?

## <a name="error-messages"></a>Mensagens de erro

### <a name="this-user-is-not-authorized-to-enroll"></a>Este utilizador não está autorizado a inscrever-se.

Erro 0x801c003: "Este utilizador não está autorizado a inscrever-se. Pode tentar fazê-lo novamente ou contactar o administrador do sistema com o código de erro (0x801c0003)."
Erro 80180003: "Algo correu mal. Este utilizador não está autorizado a inscrever-se. Pode tentar fazer isto novamente ou contactar o administrador do seu sistema com o código de erro 80180003."

**Causa:** Qualquer uma das seguintes condições: 

- O utilizador já inscreveu o número máximo de dispositivos permitidos em Intune.    
- O dispositivo está bloqueado pelas restrições do tipo de dispositivo.    
- O computador está a executar o Windows 10 Home. No entanto, inscrever-se em Intune ou aderir ao Azure AD só é suportado no Windows 10 Pro e edições superiores.

#### <a name="resolution"></a>Resolução
Existem várias soluções possíveis para esta questão:

##### <a name="remove-devices-that-were-enrolled"></a>Remova os dispositivos que estavam matriculados
1. Inscreva-se no [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).    
2. Vá ao **Utilizador** > **todos os utilizadores**.    
3. Selecione a conta de utilizador afetada e, em seguida, clique em **Dispositivos**.    
4. Selecione quaisquer dispositivos não utilizados ou indesejados e, em seguida, clique em **Eliminar**. 

##### <a name="increase-the-device-enrollment-limit"></a>Aumentar o limite de inscrição do dispositivo

> [!NOTE]
> Este método aumenta o limite de inscrição do dispositivo para todos os utilizadores, e não apenas para o utilizador afetado.

1. Inscreva-se no [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Vá para **dispositivos** > Restrições de **inscrição** > **Padrão** (sob restrições de limite de **dispositivo)** > **Propriedades** > **Editar** (ao lado do limite do **dispositivo)** > aumente o limite de **dispositivo** (máximo 15)> Review + **Save**.    
 

##### <a name="check-device-type-restrictions"></a>Verifique as restrições de tipo de dispositivo
1. Inscreva-se no [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) com uma conta de administrador global.
2. Vá aos **Dispositivos** > restrições de **inscrição**e, em seguida, selecione a restrição **predefinida** sob **restrições**do tipo de dispositivo .    
3. Selecione **Plataformas**, e, em seguida, selecione **Permitir** para **Windows (MDM)** .

    > [!IMPORTANT]
    > Se a definição atual já estiver **permitida**, mude-a para **Bloquear,** guarde a definição e, em seguida, mude-a de volta para **Permitir** e guarde novamente a regulação. Isto reinicia a definição de inscrição.

4. Aguarde aproximadamente 15 minutos e, em seguida, volte a inscrever o dispositivo afetado.    

##### <a name="upgrade-windows-10-home"></a>Atualizar o Windows 10 Home
[Atualize o Windows 10 Home para o Windows 10 Pro](https://support.microsoft.com/help/12384/windows-10-upgrading-home-to-pro) ou uma edição superior. 



### <a name="this-user-is-not-allowed-to-enroll"></a>Este utilizador não está autorizado a inscrever-se.

Erro 0x801c0003: "Este utilizador não está autorizado a inscrever-se. Pode tentar novamente ou contactar o administrador do seu sistema com o código de erro 801c0003."

**Causa:** Os Utilizadores podem juntar dispositivos à definição **de AD Azure** está definido para **Nenhum**. Isto impede que novos utilizadores se juntem aos seus dispositivos na Azure AD. Portanto, a inscrição intune falha.

#### <a name="resolution"></a>Resolução
1. Inscreva-se no [portal Azure](https://portal.azure.com/) como administrador.    
2. Vá ao **Azure Ative Directory** > **Devices** > Definições de **dispositivos**.    
3. Definir **Os utilizadores podem juntar dispositivos ao Azure AD** a **Todos**.    
4. Inscreva o dispositivo novamente.   

### <a name="the-device-is-already-enrolled"></a>O dispositivo já está matriculado.

Erro 8018000a: "Algo correu mal. O dispositivo já está matriculado.  Pode contactar o administrador do seu sistema com o código de erro 8018000a."

**Causa:** Uma das seguintes condições é verdadeira:
- Um utilizador diferente já inscreveu o dispositivo em Intune ou juntou-se ao dispositivo para a Azure AD. Para determinar se é esse o caso, aceda a **Definições** > **Contas** > **Acesso ao Trabalho**. Procure uma mensagem semelhante à seguinte: "Outro utilizador no sistema já está ligado a uma obra ou escola. Por favor, remova o trabalho ou a ligação escolar e tente novamente."    

#### <a name="resolution"></a>Resolução

Utilize um dos seguintes métodos para resolver esta questão:

##### <a name="remove-the-other-work-or-school-account"></a>Remover o outro trabalho ou conta escolar
1. Assine por fora do Windows e, em seguida, inscreva-se utilizando a outra conta que inscreveu ou juntou-se ao dispositivo.    
2. Vá a **Definições** > **Contas** > Acesso ao **Trabalho**e, em seguida, remova o trabalho ou a conta escolar.
3. Assine por fora do Windows e, em seguida, inscreva-se usando a sua conta.    
4. Inscreva o dispositivo em Intune ou junte o dispositivo à Azure AD. 



### <a name="this-account-is-not-allowed-on-this-phone"></a>Esta conta não é permitida neste telefone.

Erro: "Esta conta não é permitida neste telefone. Certifique-se de que as informações fornecidas estão corretas e, em seguida, tente novamente ou solicite apoio à sua empresa."

**Causa:** O utilizador que tentou inscrever o dispositivo não tem uma licença Intune válida.

#### <a name="resolution"></a>Resolução
Atribuir uma licença Intune válida ao utilizador e, em seguida, inscrever o dispositivo.


### <a name="looks-like-the-mdm-terms-of-use-endpoint-is-not-correctly-configured"></a>Parece que o ponto final do MDM Termos de Utilização não está corretamente configurado.

**Causa:** Uma das seguintes condições é verdadeira: 
 - Utiliza tanto a Mobile Device Management (MDM) para o Office 365 como para o Intune no inquilino, e o utilizador que tente inscrever o dispositivo não tem uma licença Intune válida ou uma licença do Office 365.     
- Os termos e condições do MDM em Azure AD estão em branco ou não contêm o URL correto.    

#### <a name="resolution"></a>Resolução

Para corrigir este problema, utilize um dos seguintes métodos: 
 
##### <a name="assign-a-valid-license-to-the-user"></a>Atribuir uma licença válida ao utilizador
Vá ao [Microsoft 365 Admin Center](https://portal.office.com/adminportal/home), e depois atribua uma licença Intune ou uma Licença Office 365 ao utilizador.

##### <a name="correct-the-mdm-terms-of-use-url"></a>Corrija os termos de URL de utilização do MDM
  1. Inscreva-se no [portal Azure](https://portal.azure.com/)e, em seguida, selecione **Azure Ative Directory**.    
  2. Selecione **Mobility (MDM e MAM)** e, em seguida, clique **em Microsoft Intune**.    
  3. Selecione **Restaurar URLs DE MDM predefinidos,** verifique se os **termos de UTILIZAÇÃO do MDM** estão definidos para **https://portal.manage.microsoft.com/TermsofUse.aspx** .    
  4. Escolha **Guardar**.    


### <a name="something-went-wrong"></a>Alguma coisa correu mal.

Erro 80180026: "Algo correu mal. Confirme que está a usar as informações corretas de início de sessão e que a sua organização utiliza esta funcionalidade. Pode tentar fazer isto novamente ou contactar o administrador do seu sistema com o código de erro 80180026."

**Causa:** Este erro pode ocorrer quando se tenta juntar a um computador Windows 10 para a AD Azure e ambas as seguintes condições são verdadeiras: 
- A inscrição automática do MDM está ativada em Azure.    
- O cliente intune PC (agente intune PC) está instalado no computador Do Windows 10.

#### <a name="resolution"></a>Resolução
Utilize um dos seguintes métodos para abordar esta questão:

##### <a name="disable-mdm-automatic-enrollment-in-azure"></a>Desative a inscrição automática do MDM em Azure.
1. Inicie sessão no [portal do Azure](https://portal.azure.com/).    
2. Vá ao **Azure Ative Directory** > **Mobility (MDM e MAM)**  > **Microsoft Intune**.    
3. Desloque o âmbito do **utilizador do MDM** para **Nenhum,** e, em seguida, clique em **Guardar**.    
     
##### <a name="uninstall"></a>Desinstalar
Desinstale o agente cliente intune PC do computador.    

### <a name="the-software-cannot-be-installed"></a>O software não pode ser instalado.

Erro: "O software não pode ser instalado, 0x80cf4017."

**Causa:** O software do cliente está desatualizado.

#### <a name="resolution"></a>Resolução
1. Inscreva-se na [https://admin.manage.microsoft.com](https://admin.manage.microsoft.com).    
2. Vá ao **Admin** > **Descarregamento**de Software cliente, e depois clique em **Descarregar software de cliente**.    
3. Guarde o pacote de instalação e, em seguida, instale o software do cliente. 


### <a name="the-account-certificate-is-not-valid-and-may-be-expired"></a>O certificado de conta não é válido e pode ser expirado.

Erro: "O certificado de conta não é válido e pode ser expirado, 0x80cf4017."

**Causa:** O software do cliente está desatualizado.

#### <a name="resolution"></a>Resolução
1. Inscreva-se na [https://admin.manage.microsoft.com](https://admin.manage.microsoft.com).    
2. Vá ao **Admin** > **Descarregamento**de Software cliente, e depois clique em **Descarregar software de cliente**.    
3. Guarde o pacote de instalação e, em seguida, instale o software do cliente.    

### <a name="your-organization-does-not-support-this-version-of-windows"></a>A sua organização não suporta esta versão do Windows. 

Erro: "Houve um problema. A sua organização não suporta esta versão do Windows.  (0x80180014)"

**Causa:** A inscrição no Windows MDM é desativada no seu inquilino Intune.

#### <a name="resolution"></a>Resolução
Para corrigir esta questão num ambiente autónomo intune, siga estes passos: 
 
1. No [Microsoft Endpoint Manager Admin Center,](https://go.microsoft.com/fwlink/?linkid=2109431)escolhe **dispositivos** > restrições de **inscrição** > escolha uma restrição do tipo de dispositivo.    
2. Escolha **propriedades** > **Editar** (ao lado das definições da **Plataforma)** > **Permitir** o **Windows (MDM)** .    
3. Clique em **Rever + Guardar**.    

### <a name="a-setup-failure-has-occurred-during-bulk-enrollment"></a>Ocorreu uma falha de configuração durante a matrícula a granel.

**Causa:** As contas de utilizador da AD Azure no pacote de conta (Package_GUID) para o respetivo pacote de provisionamento não estão autorizadas a aderir a dispositivos à Azure AD. Estas contas Azure AD são criadas automaticamente quando configura um pacote de provisionamento com o Windows Configuration Designer (WCD) ou a aplicação set up School PCs, e estas contas são então usadas para aderir aos dispositivos para a AD Azure.

#### <a name="resolution"></a>Resolução
1. Inscreva-se no [portal Azure](https://portal.azure.com/) como administrador.    
2. Vá ao **Azure Ative Directory > Dispositivos > Definições**de dispositivos .    
3. Definir **os utilizadores podem juntar dispositivos ao Azure AD** para **todos** ou **selecionados**.

   Se escolher **Selecionados,** clique em **Select ,** e clique em Adicionar **Membros** para adicionar todos os utilizadores que possam aderir aos seus dispositivos ao Azure AD. Certifique-se de que todas as contas da AD Azure para o pacote de provisionamento são adicionadas.
 
Para obter mais informações sobre como criar um pacote de provisionamento para o Windows Configuration Designer, consulte Criar um pacote de [provisionamento para o Windows 10](https://docs.microsoft.com/windows/configuration/provisioning-packages/provisioning-create-package).

Para obter mais informações sobre a aplicação set up School PCs, consulte [Use a app set up School PCs](https://docs.microsoft.com/education/windows/use-set-up-school-pcs-app).


### <a name="auto-mdm-enroll-failed"></a>Inscrição auto MDM: Falhado 

Quando tenta inscrever um dispositivo Windows 10 automaticamente utilizando a Política de Grupo, experimenta os seguintes problemas: 
- No Programador de Tarefas, no âmbito do **Microsoft** > **Windows** > **EnterpriseMgmt,** o resultado final da **Lista criada pelo cliente de inscrição automática para inscrição automática no MDM a partir da tarefa AAD** é o seguinte: Evento **76 Auto MDM Enroll: Failed (Unknown Win32 Error code: 0x8018002b)**       
- No Evento Viewer, o seguinte evento é registado em **Registos de Aplicações e Serviços/Microsoft/Windows/DeviceManagement-Enterprise-Diagnostics-Provider/Admin**:   
    ```asciidoc
    Log Name: Microsoft-Windows-DeviceManagement-Enterprise-Diagnostics-Provider/Admin
    Source: DeviceManagement-Enterprise-Diagnostics-Provider
    Event ID: 76
    Level: Error
    Description: Auto MDM Enroll: Failed (Unknown Win32 Error code: 0x80180002b)
    ```
**Causa:** Uma das seguintes condições é verdadeira: 
- A UPN contém um domínio não verificado ou não-repreensível, como .local (como joe@contoso.local).    
- **O âmbito** do utilizador do MDM está definido para **Nenhum**. 

#### <a name="resolution"></a>Resolução
Se a UPN contiver um domínio não verificado ou não repreensível, siga estes passos: 

1. No servidor em que os Serviços de Domínio de Diretório Ativo (AD DS) funcionam, abra **utilizadores e computadores de diretório ativo** digitando **dsa.msc** no diálogo **Executar** e, em seguida, clique EM **OK**.    
2. Clique em **Utilizadores** sob o seu domínio e, em seguida, faça o seguinte:  
    - Se houver apenas um utilizador afetado, clique no utilizador e clique em **Propriedades**. No separador **Conta,** na lista de drop-down upn sob o nome de início de **suposição do Utilizador,** selecione um sufixo UPN válido como contoso.com e, em seguida, clique **EM OK**.    
    - Se existirem vários utilizadores afetados, selecione os utilizadores, no menu **Ação,** clique em **Propriedades**. No separador **Conta,** selecione a caixa de verificação de **sufixo UPN,** selecione um sufixo UPN válido, como contoso.com na lista de drop-down e, em seguida, clique em **OK**.
3. Aguarde a próxima sincronização, ou force um Delta Sync do Servidor de Sincronização executando os seguintes comandos num pedido elevado de PowerShell:
    ```powershell
    Import-Module ADSync
    Start-ADSyncSyncCycle -PolicyType Delta
    ```

Se o âmbito do **utilizador do MDM** estiver definido para **Nenhum,** siga estes passos: 
 
1. Inscreva-se no [portal Azure](https://portal.azure.com/)e, em seguida, selecione **Azure Ative Directory**.
2. Selecione **Mobility (MDM e MAM)** e, em seguida, selecione **Microsoft Intune**.    
3. Detete o âmbito do **utilizador do MDM** para **Todos**. Ou, definir o âmbito do **utilizador do MDM** para **Alguns**, e selecionar os Grupos que podem inscrever automaticamente os seus dispositivos Windows 10.    
4. Desdefinir o âmbito do **utilizador MAM** para **nenhum**.


### <a name="an-error-occurred-while-creating-autopilot-profile"></a>Ocorreu um erro ao criar o perfil do Piloto Automático.

**Causa:** O formato de nome especificado do modelo de nome do dispositivo não satisfaz os requisitos. Por exemplo, utiliza minúsculas para a macro em série, como %serial% em vez de %SERIAL%.

#### <a name="resolution"></a>Resolução

Certifique-se de que o formato de nomeação satisfaz os seguintes requisitos:

- Crie um nome único para os seus dispositivos. Os nomes devem ter 15 caracteres ou menos, e podem conter letras (a-z, A-Z), números (0-9) e hífenes (‐).
- Não podem conter apenas números.
- Os nomes não contêm espaço em branco.
- Utilize a macro %SERIAL% para adicionar um número de série específico para hardware. Ou, use o %RAND:<# de dígitos>% macro para adicionar uma série aleatória de números, a corda contém <# de dígitos> dígitos. Por exemplo, MYPC-%RAND:6% gera um nome como MYPC-123456.

### <a name="something-went-wrong-oobeidps"></a>Alguma coisa correu mal. OOBEIDPS.

**Causa:** Este problema ocorre se houver um proxy, firewall ou outro dispositivo de rede que esteja bloqueando o acesso ao Fornecedor de Identidade (IdP).

#### <a name="resolution"></a>Resolução
Certifique-se de que o acesso necessário aos serviços baseados na Internet para o Autopilot não está bloqueado. Para mais informações, consulte [os requisitos](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-autopilot-requirements-network)de rede do Windows Autopilot .


### <a name="registering-your-device-for-mobile-management-failed3-0x801c03ea"></a>Registar o seu dispositivo para gestão móvel (Failed:3, 0x801C03EA).

**Causa:** O dispositivo tem um chip TPM que suporta a versão 2.0, mas ainda não foi atualizado para a versão 2.0.

#### <a name="resolution"></a>Resolução
Atualize o chip TPM para a versão 2.0.

Se o problema persistir, verifique se o mesmo dispositivo se encontra em dois grupos atribuídos, sendo atribuído a cada grupo um perfil autopiloto diferente. Se estiver em dois grupos, determine qual o perfil do Autopilot a aplicar ao dispositivo e, em seguida, remova a atribuição do outro perfil.

Para obter mais informações sobre como implementar um dispositivo Windows em modo de quiosque com o Autopilot, consulte [a implementação de um quiosque utilizando](https://blogs.technet.microsoft.com/mniehaus/2018/06/07/deploying-a-kiosk-using-windows-autopilot/)o Windows Autopilot .


### <a name="securing-your-hardware-failed-0x800705b4"></a>Assegurar o seu hardware (Falhado: 0x800705b4).

Erro 800705b4: 
```
Securing your hardware (Failed: 0x800705b4)
Joining your organization's network (Previous step failed)
Registering your device for mobile management (Previous step failed)
```

**Causa:** O dispositivo Windows direcionado não satisfaz nenhum dos seguintes requisitos:

- O aparelho deve ter um chip TPM 2.0 físico. Os dispositivos com TPMs virtuais (por exemplo, VMs Hiper-V) ou chips TPM 1.2 não funcionam com o modo de auto-implantação.
- O dispositivo deve estar a executar uma das seguintes versões do Windows:
    - O Windows 10 constrói 1703 ou uma versão posterior.
    - Se for utilizado o Hybrid Azure AD Join, o Windows 10 constrói 1809 ou uma versão posterior.


#### <a name="resolution"></a>Resolução
Certifique-se de que o dispositivo-alvo satisfaz os dois requisitos descritos na secção **Causa.**

Para obter mais informações sobre como implementar um dispositivo Windows em modo de quiosque com o Autopilot, consulte [a implementação de um quiosque utilizando](https://blogs.technet.microsoft.com/mniehaus/2018/06/07/deploying-a-kiosk-using-windows-autopilot/)o Windows Autopilot .


### <a name="something-went-wrong-error-code-80070774"></a>Alguma coisa correu mal. Código de Erro 80070774.

Erro 0x800707774: Algo correu mal. Confirme que está a usar as informações corretas de início de sessão e que a sua organização utiliza esta funcionalidade. Pode tentar fazer isto novamente ou contactar o administrador do sistema com o código de erro 80070774.

Este problema ocorre tipicamente antes de o dispositivo ser reiniciado num cenário de Piloto Automático AD Hybrid Azure, quando o dispositivo se estem durante o sinal inicial no ecrã. Significa que o controlador de domínio não pode ser encontrado ou alcançado com sucesso devido a problemas de conectividade. Ou que o dispositivo entrou num estado que não pode aderir ao domínio.

**Causa:** A causa mais comum é que o Hybrid Azure AD Join está a ser utilizado e a funcionalidade de utilizador da Atribuição está configurada no perfil autopiloto. A utilização da função de utilizador Dasign executa uma adesão do Azure AD ao dispositivo durante o ecrã de início de início de sessão que coloca o dispositivo num estado em que não pode aderir ao seu domínio no local. Por isso, a função de utilizador atribuir apenas deve ser utilizada em cenários padrão de AD AD Join Autopilot.  A funcionalidade não deve ser utilizada em cenários de AD Hybrid Azure Join.

#### <a name="resolution"></a>Resolução

1. No [Microsoft Endpoint Manager Admin Center,](https://go.microsoft.com/fwlink/?linkid=2109431)escolha > **Dispositivos** > **dispositivos Windows** > **Windows**.
2. Selecione o dispositivo que está experimentando o problema > clique na elipse (...) no lado mais direito.
3. Selecione **Unassign user** e aguarde que o processo termine.
4. Verifique se o perfil híbrido Azure AD Autopilot é atribuído antes de voltar a tentar o OOBE.

#### <a name="second-resolution"></a>Segunda resolução
Se o problema persistir, no servidor que acolhe o Conector Offline De Ligação de Domínio, verifique se o Id do evento 30312 está registado dentro do registo do Serviço de Conector ODJ. O evento 30312 assemelha-se ao seguinte:

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

Este problema é geralmente causado pela delegação incorreta de permissões à unidade organizacional onde são criados os dispositivos Do MÉBPiloto Windows. Para mais informações, consulte [Aumentar o limite da conta informática na Unidade Organizacional](windows-autopilot-hybrid.md#increase-the-computer-account-limit-in-the-organizational-unit).

1. Aberto **Utilizadores e Computadores de Diretório Ativo (DSA.msc)** .
2. Clique na unidade organizacional que utilizará para criar computadores híbridos ligados a AD > Controlo de **Delegados**.
3. Na **delegação de controlo,** selecione **Next** > **Adicionar** tipos de **objetos** > .
4. No painel Tipos de **Objetos,** selecione a caixa de verificação **de computadores** > **OK**.
5. Nos **Utilizadores Selecionados,** **Computadores,** ou Painel **de Grupos,** no **painel de objetos Insira para selecionar** a caixa, introduza o nome do computador onde o Conector está instalado.
6. Selecione **Ver Nomes** para validar a sua entrada > **OK** > **Seguinte**.
7. Selecione **Criar uma tarefa personalizada para delegar** > **Seguinte**.
8. Selecione os **seguintes objetos na** caixa de verificação da pasta e, em seguida, selecione os **objetos do Computador**, **Crie objetos selecionados nesta pasta**e **elimine os objetos selecionados nesta pasta** verifique as caixas de verificação.
9. Selecione **Seguinte**.
10. Em **Permissões,** selecione a caixa de verificação **De Controlo Completo.** Esta ação seleciona todas as outras opções.
11. Selecione **Next** > **Finish**.

## <a name="next-steps"></a>Próximos passos

- [Resolução de problemas de inscrição de dispositivos no Intune](../troubleshoot-device-enrollment-in-intune.md)
- [Faça uma pergunta sobre o fórum Intune](https://social.technet.microsoft.com/Forums/%7Blang-locale%7D/home?category=microsoftintune&filter=alltypes&sort=lastpostdesc)
- [Consulte o Blog da Equipa de Suporte Intune da Microsoft](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/bg-p/IntuneCustomerSuccess)
- [Consulte o Microsoft Enterprise Mobility and Security Blog](https://techcommunity.microsoft.com/t5/Azure-Active-Directory-Identity/Announcing-the-public-preview-of-Azure-AD-group-based-license/ba-p/245210)
- [Obtenha suporte para Microsoft Intune](../fundamentals/get-support.md)
- [Encontre erros de inscrição de cogestão](https://docs.microsoft.com/configmgr/comanage/how-to-monitor#enrollment-errors)
