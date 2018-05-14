---
title: Adicionar proteção de ponto final no Windows 10 no Microsoft Intune – Azure | Microsoft Docs
description: Em dispositivos com o Windows 10, utilize ou configure definições de proteção de ponto final para ativar a funcionalidade Windows Defender, incluindo o Application Guard, Firewall, SmartScreen, encriptação e BitLocker, Exploit Guard, Controlo de Aplicações, Centro de Segurança e segurança em dispositivos locais no Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/23/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 3af7c91b-8292-4c7e-8d25-8834fcf3517a
ms.reviewer: ilwu
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 22eceb7792aee714fb728d64d8bec2ae8db4167c
ms.sourcegitcommit: 401cedcd7acc6cb3a6f18d4679bdadb0e0cdf443
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/28/2018
---
# <a name="endpoint-protection-settings-for-windows-10-and-later-in-intune"></a>Definições de proteção de ponto final para o Windows 10 (e versões posteriores) no Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

O perfil de proteção de ponto final permite-lhe controlar as funcionalidades de segurança em dispositivos com Windows 10, como o BitLocker e o Windows Defender.

Utilize as informações neste artigo para saber como criar perfis de proteção de ponto final.

> [!NOTE]
> Estas definições não são suportadas nas edições Home e Professional do Windows 10.

## <a name="windows-defender-application-guard"></a>Windows Defender Application Guard

Ao utilizar o Microsoft Edge, o Windows Defender Application Guard protege o ambiente de sites que ainda não foram definidos como fidedignos pela sua organização. Quando os utilizadores visitam sites que não estão listados no seu limite de rede isolada, os sites são abertos numa sessão de navegação virtual no Hyper-V. Os sites fidedignos são definidos por um limite de rede, que pode ser configurado na Configuração do Dispositivo. 

O Application Guard só está disponível para dispositivos com o Windows 10 (64 bits). Se utilizar este perfil, instalará um componente do Win32 para ativar o Application Guard.

- **Application Guard**: abra sites não aprovados num contentor de navegação virtualizado Hyper-V.
- **Comportamento da área de transferência**: escolha que ações Copiar e Colar são permitidas entre o PC local e o browser virtual do Application Guard.
- **Conteúdos externos em sites de empresa**: impeça que os conteúdos de sites não aprovados sejam carregados.
- **Imprimir a partir do browser virtual**: permita que impressoras de rede, locais, XPS e/ou PDF imprimam conteúdos a partir do browser virtual.
- **Recolher registos**: recolha registos de eventos que ocorrem numa sessão de navegação do Application Guard.
- **Reter dados do browser gerados pelo utilizador**: guarde os dados do utilizador (por exemplo, palavras-passe, favoritos e cookies) que são criados durante uma sessão de navegação virtual do Application Guard.
- **Aceleração de gráficos**: carregue sites com grande intensidade de gráficos mais rapidamente, ao trabalhar dentro da sessão de navegação virtual do Application Guard. Os sites carregam mais rapidamente se ativar o acesso a uma unidade de processamento de gráficos virtual.
- **Transferir ficheiros para o sistema de ficheiros anfitrião**: permita que os utilizadores transfiram ficheiros do browser virtualizado para o sistema operativo anfitrião.

## <a name="windows-defender-firewall"></a>Firewall do Windows Defender

### <a name="global-settings"></a>Definições globais

Estas definições são aplicáveis a todos os tipos de rede.

- **Protocolo FTP (File Transfer Protocol)**: bloqueie o FTP com monitorização de estado.
- **Tempo de inatividade de associação de segurança antes da eliminação**: as associações de segurança são eliminadas quando o tráfego de rede não é detetado durante *n* segundos.
- **Codificação de chave pré-partilhada**: codifique chaves pré-partilhadas com UTF-8.
- **Isenções de IPsec**: configure o tráfego específico para ser isento de IPsec, incluindo **Códigos do tipo IPv6 ICMPde deteção da vizinhança**, **ICMP**, **Códigos do tipo IPv6 ICMP de deteção de router** e **Tráfego de rede de IPv4 e IPv6 DHCP**.
- **Verificação da lista de revogação de certificados**: defina um valor para a forma como a verificação da lista de revogação de certificados é imposta, incluindo **Desativar a verificação de CRL**, **Falhar a verificação de CRL apenas no certificado revogado** e **Falhar a verificação de CRL em qualquer erro encontrado**.
- **Fazer corresponder oportunisticamente ao conjunto de autenticação por módulo de keying**: defina módulos de keying para ignorar o conjunto de autenticação completo se não suportarem todos os pacotes de autenticação nesse conjunto.
- **Pacotes de colocação**: especifique como o dimensionamento do software do lado de receção é ativado para a receção encriptada e o reencaminhamento de texto não encriptado para o cenário de gateway de túnel IPsec. Esta definição garante que o pedido de pacote é preservado.

### <a name="network-settings"></a>Definições de rede

Estas definições são aplicáveis a tipos de rede específicos, incluindo **Rede de domínio (área de trabalho)**, **Rede privada (detetável)** e **Rede pública (não detetável)**.

#### <a name="general-settings"></a>Definições gerais

- **Firewall do Windows Defender**: permita que esta definição bloqueie o tráfego de rede.
- **Modo furtivo**: impeça a Firewall de funcionar no modo furtivo. Esta definição também lhe permite bloquear a **Exceção de pacotes seguros com IPsec**.
- **Blindada**: se ativar esta definição, a definição de firewall bloqueará todo o tráfego de entrada.
- **Respostas unicast às difusões multicast**: bloqueie respostas unicast às difusões multicast. Normalmente, não quer receber respostas unicast para mensagens multicast ou de difusão. Essas respostas podem indicar um ataque denial of service (DOS) ou um atacante a tentar sondar um computador conhecido.
- **Notificações de entrada**: impeça que as notificações sejam apresentadas aos utilizadores quando uma aplicação é impedida de escutar numa porta.
- **Ação predefinida para ligações de entrada**: bloqueie a ação predefinida que a firewall realiza em ligações de entrada.

#### <a name="rule-merging"></a>Intercalação de regras

- **Regras de Firewall do Windows Defender de aplicação autorizada do arquivo local**: aplique regras de firewall autorizadas no arquivo local a serem reconhecidas e executadas.
- **Regras de Firewall do Windows Defender de portas globais do arquivo local**: aplique regras de firewall de portas globais no arquivo local a serem reconhecidas e executadas.
- **Regras de Firewall do Windows Defender do arquivo local**: aplique regras de firewall globais no arquivo local a serem reconhecidas e executadas.
- **Regras de IPsec do arquivo local**: aplique regras de segurança de ligação do arquivo local, independentemente do esquema ou das versões de regras de segurança da ligação.

## <a name="windows-defender-smartscreen-settings"></a>Definições do Windows Defender SmartScreen

- **SmartScreen para aplicações e ficheiros**: ative o Windows SmartScreen para a execução de ficheiros e aplicações em execução.
- **Execução de ficheiros não verificados**: não permita que o utilizador final execute ficheiros que não foram verificados pelo Windows SmartScreen.

## <a name="windows-encryption"></a>Encriptação do Windows

### <a name="windows-settings"></a>Definições do Windows

As duas definições seguintes aplicam-se a todas as versões do Windows 10:

- **Encriptar dispositivos**: se ativada, é pedido aos utilizadores que ativem a encriptação de dispositivos. Adicionalmente, é-lhes pedido que confirmem que a encriptação de outro fornecedor não foi ativada. Se a encriptação do Windows for ativada enquanto outro método de encriptação estiver ativo, o dispositivo pode tornar-se instável.
- **Encriptar cartão de armazenamento**: ative esta definição para encriptar todos os cartões de armazenamento amovíveis utilizados pelo dispositivo.


### <a name="bitlocker-base-settings"></a>Definições base do BitLocker

As definições base são definições de BitLocker universais para todos os tipos de unidades de dados. As definições de Política de Grupo do BitLocker gerem as tarefas de encriptação ou opções de configuração de unidades que o utilizador final pode modificar para todos os tipos de unidades de dados.

- **Aviso de encriptação de outro disco**: desative a mensagem de aviso de encriptação de outro disco nos computadores dos utilizadores finais.
- **Configurar métodos de encriptação**: ative esta definição para configurar algoritmos de encriptação do sistema operativo, dos dados e das unidades amovíveis.
  - **Encriptação de unidades de sistema operativo**: selecione o método de encriptação das unidades de sistema operativo. Recomendamos que utilize o algoritmo XTS-AES.
  - **Encriptação de unidades de dados fixas**: escolha o método de encriptação das unidades de dados fixas (incorporadas). Recomendamos que utilize o algoritmo XTS-AES.
  - **Encriptação de unidades de dados amovíveis**: selecione o método de encriptação das unidades de dados amovíveis. Se a unidade amovível for utilizada com dispositivos que não executam o Windows 10, recomendamos que utilize o algoritmo AES-CBC.

### <a name="bitlocker-os-drive-settings"></a>Definições de unidades de SO do BitLocker

Estas definições aplicam-se especificamente a unidades de dados do sistema operativo.

- **Autenticação adicional no arranque**: configure os requisitos de autenticação do arranque do computador, incluindo a utilização do Trusted Platform Module (TPM).
  - **BitLocker com chip do TPM não compatível**
  - **Arranque do TPM compatível**: escolha permitir, não permitir ou exigir o chip do TPM.
  - **PIN de arranque do TPM compatível**: escolha permitir, não permitir ou exigir um PIN de arranque com o chip do TPM.
  - **Chave de arranque do TPM compatível**: escolha permitir, não permitir ou exigir uma chave de arranque com o chip do TPM.
  - **PIN e chave de arranque do TPM compatível**: escolha permitir, não permitir ou exigir um PIN e uma chave de arranque com o chip do TPM.
- **Comprimento Mínimo do PIN** : ative esta definição para configurar um comprimento mínimo para o PIN de arranque do TPM.
  - **Carateres mínimos**: introduza o número de carateres necessários para o PIN de arranque de **4**-**20**.
- **Recuperação da unidade de SO**: ative esta definição para controlar a forma como as unidades de sistema operativo protegidas pelo BitLocker são recuperadas quando as informações de arranque necessárias não estão disponíveis.
  - **Agente de recuperação de dados baseada em certificados**: ative esta definição se quiser que os agentes de recuperação de dados possam ser utilizados com as unidades de sistema operativo protegidas pelo BitLocker.
  - **Criação de palavra-passe de recuperação pelo utilizador**: escolha se é permitido, não permitido ou exigido aos utilizadores gerarem uma palavra-passe de recuperação de 48 dígitos.
  - **Criação de chave de recuperação pelo utilizador**: escolha se é permitido, não permitido ou exigido aos utilizadores gerarem uma chave de recuperação de 256 bits.
  - **Opções de recuperação no assistente de configuração do BitLocker**: ative esta definição para impedir que os utilizadores vejam ou alterem as opções de recuperação quando ativam o BitLocker.
  - **Guardar as informações de recuperação do BitLocker no AD DS**: permite o armazenamento das informações de recuperação do BitLocker no Active Directory.
  - **Informações de recuperação do BitLocker armazenadas no AD DS**: configure que partes das informações de recuperação do BitLocker são armazenadas no Active Directory. Escolha entre:
    - **Palavras-passe de recuperação de cópia de segurança e pacotes de chaves**
    - **Apenas palavras-passe de recuperação de cópia de segurança**
  - **Armazenar as informações de recuperação no AD DS antes de ativar o BitLocker**: ative esta definição para impedir os utilizadores de ativarem o BitLocker, a menos que o dispositivo esteja associado a um domínio e as informações de recuperação do BitLocker estejam armazenadas com êxito no Active Directory.
- **Mensagem de recuperação de pré-arranque e o URL**: ative esta definição para configurar a mensagem e o URL que são apresentados no ecrã de pré-arranque de recuperação da chave.
  - **Mensagem de recuperação de pré-arranque**: configure de que forma é que a mensagem de recuperação de pré-arranque é apresentada aos utilizadores. Escolha entre:
    - **Utilizar mensagem de recuperação predefinida e URL**
    - **Utilizar mensagem de recuperação vazia e URL**
    - **Utilizar mensagem de recuperação personalizada**
    - **Utilizador URL de recuperação personalizada**

### <a name="bitlocker-fixed-data-drive-settings"></a>Definições de unidades de dados fixas do BitLocker

- **Acesso de escrita para unidade de dados fixa não protegida pelo BitLocker**: se ativada, a proteção do BitLocker tem de ser ativada em todas as unidades de dados incorporadas ou fixas para que possa escrever nelas.
- **Recuperação de unidade fixa**: ative esta definição para controlar a forma como as unidades fixas protegidas pelo BitLocker são recuperadas quando as informações de arranque necessárias não estão disponíveis.
  - **Agente de recuperação de dados**: ative esta definição se quiser que os agentes de recuperação de dados sejam utilizados com as unidades fixas protegidas pelo BitLocker.
  - **Criação de palavra-passe de recuperação pelo utilizador**: configure se é permitido, não permitido ou exigido aos utilizadores gerarem uma palavra-passe de recuperação de 48 dígitos.  
  - **Criação da chave de recuperação pelo utilizador**: configure se é permitido, não permitido ou exigido aos utilizadores gerarem uma chave de recuperação de 256 bits.
  - **Opções de recuperação no assistente de configuração do BitLocker**: ative esta definição para impedir que os utilizadores vejam ou alterem as opções de recuperação quando ativam o BitLocker.
  - **Guardar as informações de recuperação do BitLocker no AD DS**: permite o armazenamento das informações de recuperação do BitLocker no Active Directory.
  - **Informações de recuperação do BitLocker para o AD DS**: configure que partes das informações de recuperação do BitLocker são armazenadas no Active Directory. Escolha entre:
    - **Palavras-passe de recuperação de cópia de segurança e pacotes de chaves**
    - **Apenas palavras-passe de recuperação de cópia de segurança**
  - **Armazenar as informações de recuperação no AD DS antes de ativar o BitLocker**: ative esta definição para impedir os utilizadores de ativarem o BitLocker, a menos que o dispositivo esteja associado a um domínio e as informações de recuperação do BitLocker tenham sido armazenadas com êxito no Active Directory.

### <a name="bitlocker-removable-data-drive-settings"></a>Definições de unidades de dados removíveis do BitLocker

- **Acesso de escrita para a unidade de dados amovível não protegida pelo BitLocker**: especifique se a encriptação do BitLocker é necessária para as unidades de armazenamento amovíveis.
  - **Acesso de escrita para dispositivos configurados noutra organização**: especifique se é permitido escrever nas unidades de dados amovíveis que pertencem a outra organização.

## <a name="windows-defender-exploit-guard"></a>Windows Defender Exploit Guard

Utilize o [Windows Defender Exploit Guard](https://docs.microsoft.com/windows/threat-protection/windows-defender-exploit-guard/windows-defender-exploit-guard) para gerir e reduzir a superfície de ataque de aplicações utilizadas pelos seus funcionários.

### <a name="attack-surface-reduction"></a>Redução da Superfície de Ataque

- **Marcar o roubo de credenciais do sistema de autoridade de segurança local do Windows**

Ajude a [impedir as ações e aplicações](https://docs.microsoft.com/windows/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard) que são normalmente utilizadas por software maligno para explorar falhas de segurança e infetar computadores.

#### <a name="rules-to-prevent-office-macro-threats"></a>Regras para impedir ameaças macro do Office

Impeça as aplicações do Office de realizarem as seguintes ações:

- **Aplicações do Office a injetar noutros processos (sem exceções)**
- **Aplicações/macros do Office a criar conteúdo executável**
- **Aplicações do Office a iniciar processos subordinados**
- **Importações do Win32 provenientes de código macro do Office**

#### <a name="rules-to-prevent-script-threats"></a>Regras para impedir ameaças de script

Bloqueie os itens seguintes para impedir ameaças de script:

- **Código macro js/vbs/ps/ oculto**
- **js/vbs a executar payload transferido da Internet (sem exceções)**
- **Processo de criação de comandos PSExec e WMI**
- **Processos não fidedignos e não assinados que executam a partir de USB**
- **Ficheiros executáveis que não correspondam a uma prevalência, idade ou lista de critérios de confiança**

#### <a name="rules-to-prevent-email-threats"></a>Regras para impedir ameaças de e-mail

Bloqueie o seguinte para impedir ameaças de e-mail:

- **Execução de conteúdo executável (exe, dll, ps, js, vbs, etc.) retirado do e-mail (webmail/cliente de correio) (sem exceções)**

#### <a name="rules-to-protect-against-ransomware"></a>Regras para proteger contra ransomware
- **Proteção de ransomware avançada**

> [!TIP]
> O artigo [Reduce attack surfaces with Windows Defender Exploit Guard (Reduzir a ocorrência de ataques com o Windows Defender Exploit Guard)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard) fornece mais detalhes sobre estas regras.

#### <a name="attack-surface-reduction-exceptions"></a>Exceções da Redução da Superfície de Ataque

- **Ficheiros e pastas a excluir das regras de redução de superfície de ataque**: importe/adicione uma lista de localizações a excluir das regras configuradas.

### <a name="controlled-folder-access"></a>Acesso a pastas controladas

Ajude a proteger dados valiosos de ameaças e aplicações malignas, tal como ransomware.

- **Proteção de pastas**: proteja ficheiros e pastas de alterações indesejadas por parte de aplicações malignas. Pode importar uma **Lista de aplicações que têm acesso a pastas protegidas** ou adicioná-las manualmente. Também pode adicionar uma **Lista de pastas adicionais que necessitam ser protegidas** com um carregamento ou adicioná-las manualmente.

### <a name="network-filtering"></a>Filtragem de rede

Bloqueie ligações de saída de qualquer aplicação para endereços IP/domínios com baixa reputação.

### <a name="exploit-protection"></a>Exploit Protection

Bloqueie a **Edição da interface do Exploit Protection por parte dos utilizadores** ao carregar um ficheiro XML que lhe permite configurar a memória, controlar o fluxo e as restrições de políticas. As definições no ficheiro XML podem servir para proteger uma aplicação de exploits.

Para ativar o Exploit Protection, crie um ficheiro XML que represente as definições de mitigação de sistema e aplicação à sua escolha. Pode fazê-lo ao utilizar um de dois métodos:

 1. PowerShell: utilize um ou mais dos cmdlets Get-ProcessMitigation, Set-ProcessMitigation e ConvertTo-ProcessMitigationPolicy do PowerShell. Os cmdlets configuram definições de mitigação e exportam uma representação XML deles.

 2. IU do Centro de Segurança do Windows Defender: no Centro de Segurança do Windows Defender, clique no controlo de browser e na aplicação e, em seguida, desloque-se para a parte inferior do ecrã resultante para localizar o Exploit Protection. Em primeiro lugar, utilize as definições do sistema e os separadores das definições de programa para configurar definições de atenuação. Em seguida, localize a ligação de definições de Exportação na parte inferior do ecrã para exportar uma representação XML dos mesmos.

## <a name="windows-defender-application-control"></a>Controlo de Aplicações do Windows Defender

Utilize as **Políticas de integridade do código de controlo de aplicações** para escolher as aplicações adicionais que precisam de ser auditadas ou que podem ser consideradas de confiança para serem executadas pelo Controlo de Aplicações do Windows Defender. Os componentes do Windows e todas as aplicações da Microsoft Store são automaticamente considerados de confiança para serem executados.

As aplicações não são bloqueadas quando são executadas no modo **apenas auditoria**. O modo **Apenas auditoria** regista todos os eventos nos registos do cliente local.

Uma vez ativado, o Controlo de Aplicações só poderá ser desativado ao alterar o modo de **Impor** para **Apenas auditoria**. Se alterar do modo de **Impor** para **Não Configurado** o Controlo de Aplicações continuará a ser imposto nos dispositivos atribuídos.

## <a name="windows-defender-credential-guard"></a>Windows Defender Credential Guard
O Windows Defender Credential Guard protege contra ataques de roubo de credenciais. Isola os segredos para permitir o acesso apenas a software de sistema com privilégios.

As definições do **Credential Guard** incluem:

- **Desativado**: desativará o Credential Guard remotamente se este tiver sido ativado antes através da opção **Ativado sem bloqueio UEFI**.
- **Ativado com bloqueio UEFI**: garante que o Credential Guard não pode ser desativado remotamente com a chave de registo ou através da utilização da Política de Grupo.

    > [!NOTE]
    > Se utilizar esta definição e, em seguida, quiser desativar o Credential Guard, terá de definir a Política de Grupo como **Desativado**. Além disso, tem de limpar fisicamente as informações de configuração de UEFI de cada computador. Enquanto a configuração da UEFI persistir, o Credential Guard estará ativado.

- **Ativado sem bloqueio UEFI**: permite que o Credential Guard seja desativado remotamente através da utilização da Política de Grupo. Os dispositivos que utilizam esta definição têm de ter a versão 1511 ou mais recente do Windows 10.

Quando ativar o Credential Guard, as seguintes funcionalidades necessárias também são ativadas:

- **Segurança baseada em Virtualização** (VBS): é ativada durante o próximo reinício. A segurança baseada em Virtualização utiliza o Windows Hypervisor para dar suporte aos serviços de segurança e requer o Windows Hypervisor.
- **Reinício Seguro com o Acesso Direto à Memória**: ativa a VBS com o Arranque Seguro e as proteções do acesso direto à memória (DMA). As proteções de DMA necessitam de suporte de hardware e são ativadas apenas em dispositivos configurados corretamente.

## <a name="windows-defender-security-center"></a>Centro de Segurança do Windows Defender

A aplicação Centro de Segurança do Windows Defender funciona como uma aplicação ou processo separado de cada uma das funcionalidades individuais. Apresenta notificações através do Centro de Ação. Atua como um recoletor ou único local para ver o estado e realizar configurações para cada uma das funcionalidades. Saiba mais na documentação do [Windows Defender](https://docs.microsoft.com/windows/threat-protection/windows-defender-security-center/windows-defender-security-center).

#### <a name="windows-defender-security-center-app-and-notifications"></a>Aplicações e notificações do Centro de Segurança do Windows Defender

Bloqueie o acesso de utilizadores finais a várias áreas da aplicação Centro de Segurança do Windows Defender. Ocultar uma secção também irá bloquear notificações relacionadas.

- **Proteção contra vírus e ameaças**
- **Desempenho e estado de funcionamento do dispositivo**
- **Firewall e proteção da rede**
- **Controlo de aplicações e browsers**
- **Opções de família**
- **Notificações das áreas apresentadas da aplicação**: escolha quais as notificações a apresentar aos utilizadores finais. As notificações não críticas incluem resumos de atividade do Antivírus do Windows Defender, incluindo notificações quando as análises forem concluídas. Todas as outras notificações são consideradas críticas.

#### <a name="it-contact-information"></a>Informação de contacto de TI

Forneça as informações de contacto de TI para que sejam apresentadas na aplicação Centro de Segurança do Windows Defender e nas notificações da aplicação. Pode optar por **Mostrar na aplicação e nas notificações**, **Mostrar apenas na aplicação**, **Mostrar apenas nas notificações** ou **Não mostrar**. Tem de introduzir o **Nome da organização de TI** e, pelo menos, uma das seguintes opções de contacto:

- **Número de telefone ou ID do Skype do departamento de TI**
- **Endereço de e-mail do departamento de TI**
- **URL do site de suporte de TI**

## <a name="local-device-security-options"></a>Opções de segurança do dispositivo local

Utilize estas opções para configurar as definições da segurança local em dispositivos Windows 10.

### <a name="accounts"></a>Contas

- **Adicionar novas contas Microsoft**: impede que os utilizadores adicionem novas contas Microsoft a este computador.
- **Início de sessão remoto sem palavra-passe**: permita que as contas locais que não estejam protegidas por palavra-passe iniciem sessão a partir de localizações que não sejam o dispositivo físico.

#### <a name="admin"></a>Administração

- **Conta de administrador local**: determine se a Conta de administrador local está ativada ou desativada.
- **Mudar o nome da conta de administrador**: defina um nome de conta diferente para ser associado ao identificador de segurança (SID) da Conta de administrador.

#### <a name="guest"></a>Convidado

- **Conta de convidado**: determine se a Conta de convidado está ativada ou desativada.
- **Mudar o nome da conta de convidado**: defina um nome de conta diferente para ser associado ao identificador de segurança (SID) da Conta de convidado.

### <a name="devices"></a>Dispositivos

- **Desancorar o dispositivo sem início de sessão**: impeça que um computador portátil seja desancorado sem ter de iniciar sessão.
- **Instalar os controladores de impressora para impressoras partilhadas**: restrinja a instalação de controladores de impressora como parte da ligação a uma impressora partilhada apenas para os administradores.
- **Restringir o acesso de CD-ROM ao utilizador ativo local**: a ativação desta definição permite que apenas o utilizador com sessão iniciada de forma interativa aceda ao suporte de dados CD-ROM
- **Formatar e ejetar o suporte de dados amovível**: defina quem tem permissão para formatar e ejetar o suporte de dados NTFS amovível:
  - **Não configurado**
  - **Administradores e Utilizadores Avançados**
  - **Administradores e Utilizadores Interativos**

### <a name="interactive-logon"></a>Início de sessão interativo

- **Minutos de inatividade do ecrã bloqueado até que a proteção de ecrã seja ativada**: defina o máximo de minutos de inatividade no ecrã de início de sessão do ambiente de trabalho interativo até que a proteção de ecrã seja executada.
- **Exigir CTRL + ALT + DEL para iniciar sessão**: exija que sejam premidas as teclas CTRL + ALT + DEL para um utilizador poder iniciar sessão.
- **Comportamento de remoção do smart card**: determina o que acontece quando o smart card de um utilizador com sessão iniciada é removido do leitor de Smart Card.
As [opções LocalPoliciesSecurity](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-localpoliciessecurityoptions#localpoliciessecurityoptions-interactivelogon-smartcardremovalbehavior) proporcionam mais detalhes.

#### <a name="display"></a>Apresentar

- **Informações do utilizador no ecrã de bloqueio**: configure as informações de utilizador que são apresentadas quando a sessão está bloqueada. Se não estiverem configuradas, serão apresentados o nome a apresentar do utilizador, o domínio e o nome de utilizador.
  - **Apenas o nome a apresentar do utilizador**
  - **Não apresentar informações do utilizador**
  - **Não configuradas**: o nome a apresentar do utilizador, o domínio e o nome de utilizador
- **Ocultar último utilizador com sessão iniciada**: não apresente o nome de utilizador da última pessoa que iniciou sessão neste dispositivo.
- **Ocultar o nome de utilizador no início de sessão**: não apresentar o nome de utilizador da pessoa a iniciar sessão neste dispositivo depois de as credenciais serem introduzidas e antes de o ambiente de trabalho do dispositivo ser apresentado.
- **Título da mensagem do início de sessão**: defina o título da mensagem para os utilizadores que tentam iniciar sessão.
- **Texto da mensagem do início de sessão**: defina o texto da mensagem para os utilizadores que tentam iniciar sessão.

### <a name="network-access-and-security"></a>Acesso à rede e segurança

- **Acesso anónimo a Pipes Nomeados e Partilhas**: restringe o acesso anónimo às definições Pipe Nomeado e Partilha. Aplica-se as definições que podem ser acedidas anonimamente.
- **Enumeração anónima de contas SAM**: permite que os utilizadores anónimos enumerem as contas SAM. O Windows permite que os utilizadores anónimos enumerem os nomes das contas de domínio e das partilhas de rede.
- **Enumeração anónima de contas e partilhas SAM**: pode bloquear a enumeração anónima de contas e partilhas SAM. O Windows permite que os utilizadores anónimos enumerem os nomes das contas de domínio e das partilhas de rede.
- **Valor hash do LAN Manager armazenado na alteração de palavra-passe**: na próxima alteração de palavra-passe, escolha se o valor hash do LAN Manager (LM) da nova palavra-passe é armazenado. Não é armazenado por predefinição.
- **Pedidos de autenticação PKU2U**: bloqueie os pedidos de autenticação PKU2U neste dispositivo para utilizar identidades online.
- **Restringir ligações remotas de RPC a SAM**: edite a cadeia de Linguagem de Definição de Descritor de Segurança predefinida para permitir ou negar a utilizadores e grupos a realização de chamadas remotas para SAM.
- **Descritor de segurança**

### <a name="recovery-console-and-shutdown"></a>Consola de recuperação e encerramento

- **Limpar o ficheiro de paginação de memória virtual ao encerrar**: limpe o ficheiro de paginação de memória virtual quando o dispositivo for desligado.
- **Encerramento sem início de sessão**: bloqueie a opção para encerrar o computador a partir do ecrã de início de sessão do Windows. Neste caso, os utilizadores têm de conseguir iniciar sessão com êxito no computador e antes de fazerem um encerramento do sistema.

### <a name="user-account-control"></a>Controlo de conta de utilizador

- **Integridade de UIA sem localização segura**: permita que as aplicações de localizações não seguras no sistema de ficheiros sejam executadas com o nível de integridade UIAccess.
- **Virtualizar falhas de escrita nos ficheiros e registo em locais por utilizador**: determine se as falhas de escrita de aplicações são redirecionadas para localizações definidas de sistemas de ficheiros e registo. Em alternativa, faça com que a aplicação falhe.
- **Elevar apenas ficheiros executáveis assinados e validados**: imponha a validação do caminho da certificação PKI de um determinado ficheiro executável para permitir a sua execução.

#### <a name="uia-elevation-prompt-behavior-settings"></a>Definições do comportamento do pedido de elevação UIA

- **Pedido de elevação para administradores**: defina o comportamento do pedido de elevação para administradores no Modo de Aprovação de Administrador:
  - **Elevar sem perguntar**
  - **Pedir credenciais no ambiente de trabalho seguro**
  - **Pedir consentimento no ambiente de trabalho seguro**
  - **Pedir credenciais**
  - **Pedir consentimento**
  - **Não configurado**: Pedir consentimento para binários que não sejam Windows
- **Pedido de elevação para utilizadores padrão**: defina o comportamento do pedido de elevação para utilizadores padrão:
  - **Negar automaticamente pedidos de elevação**
  - **Pedir credenciais no ambiente de trabalho seguro**
  - **Não configurado**: Pedir credenciais
- **Encaminhar pedidos de elevação para o ambiente de trabalho interativo do utilizador**: ative todos os pedidos de elevação para aceder ao ambiente do utilizador interativo em vez do ambiente de trabalho seguro. São utilizadas as definições de política de comportamento de pedidos para administradores e utilizadores padrão.
- **Pedido elevado para instalações de aplicações**: as instalações de aplicações que requerem privilégios elevados pedirão as credenciais de administrador.
- **Pedido de elevação UIA sem ambiente de trabalho seguro**: permita que as aplicações UIAccess façam pedidos de elevação sem utilizar o ambiente de trabalho seguro.

#### <a name="admin-approval-mode-settings"></a>Definições do Modo de Aprovação de Administrador

- **Modo de Aprovação de Administrador para Administrador Incorporado**: define se a conta do administrador incorporado utiliza o Modo de Aprovação de Administrador ou executa todas as aplicações com todos os privilégios de administrador.
- **Executar todos os administradores no Modo de Aprovação de Administrador**: defina se o Modo de Aprovação de Administrador e todas as definições de política UAC estão ativadas.

### <a name="microsoft-network-client"></a>Cliente de Rede da Microsoft

- **Assinar digitalmente comunicações (se o servidor concordar)**: determina se o cliente SMB tenta negociar a assinatura de pacotes SMB. Quando ativada (predefinição), o cliente de rede da Microsoft pede ao servidor para executar a assinatura de pacotes SMB após a configuração da sessão. Se a assinatura de pacotes tiver sido ativada no servidor, a assinatura de pacotes será negociada. Se esta política estiver desativada, o cliente SMB nunca negociará a assinatura de pacotes SMB.
- **Enviar palavra-passe não encriptada para servidores SMB de terceiros**: quando ativada, o redirecionador do protocolo SMB (Server Message Block) tem permissão para enviar palavras-passe de texto simples para servidores SMB que não sejam da Microsoft e que não suportam a encriptação da palavras-passe durante a autenticação.

### <a name="microsoft-network-server"></a>Servidor de Rede da Microsoft

- **Assinar digitalmente comunicações (se o cliente concordar)**: determina se o servidor SMB negoceia a assinatura de pacotes SMB com clientes que a peçam. Quando ativada, o servidor de rede da Microsoft negoceia a assinatura de pacotes SMB conforme pedido pelo cliente. Ou seja, se a assinatura de pacotes estiver ativada no cliente, a assinatura de pacotes será negociada. Se estiver desativada (predefinição), o cliente SMB nunca negoceirá a assinatura de pacotes SMB.
- **Assinar digitalmente comunicações (sempre)**: determina se o componente do servidor SMB necessita da assinatura de pacotes. Quando ativada, o servidor de rede da Microsoft não comunica com um cliente de rede da Microsoft, a menos que o cliente aceite executar a assinatura de pacotes SMB. Quando desativada (predefinição), a assinatura de pacotes SMB é negociada entre o cliente e o servidor.

## <a name="next-steps"></a>Próximos passos

Para atribuir este perfil a grupos, veja [Como atribuir perfis de dispositivo](device-profile-assign.md).
