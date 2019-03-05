---
title: Definições de proteção para dispositivos Windows 10 no Microsoft Intune – Azure | Documentos da Microsoft
description: Em dispositivos com o Windows 10, utilize ou configure definições de proteção de ponto final para ativar a funcionalidade Windows Defender, incluindo o Application Guard, Firewall, SmartScreen, encriptação e BitLocker, Exploit Guard, Controlo de Aplicações, Centro de Segurança e segurança em dispositivos locais no Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/04/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 3af7c91b-8292-4c7e-8d25-8834fcf3517a
ms.reviewer: ilwu
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4794adda447754b5dc72ff1b320ec69553a8b55a
ms.sourcegitcommit: e8c32bd6db2560570d1e1733f999ae3b2c026908
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/04/2019
ms.locfileid: "57305515"
---
# <a name="windows-10-and-later-settings-to-protect-devices-using-intune"></a>Definições de 10 (e posteriores) do Windows para proteger os dispositivos com o Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

O Microsoft Intune inclui várias definições para o ajudar a proteger os seus dispositivos. Este artigo descreve todas as configurações que pode habilitar e configurar no Windows 10 e dispositivos mais recentes. Estas definições são criadas num perfil de configuração da proteção de ponto final, no Intune para controlo de segurança, inclusive BitLocker e o Windows Defender.

Para configurar o antivírus do Windows Defender, consulte [restrições de dispositivos Windows 10](device-restrictions-windows-10.md#windows-defender-antivirus).

## <a name="before-you-begin"></a>Antes de começar

[Criar um perfil de configuração de dispositivo de proteção de ponto final](endpoint-protection-configure.md).

## <a name="windows-defender-application-guard"></a>Windows Defender Application Guard

Suportado nas seguintes edições do Windows 10:

- Empresarial
- Profissional

Ao utilizar o Microsoft Edge, o Windows Defender Application Guard protege o seu ambiente contra sites que a sua organização não considera como sendo de confiança. Quando os utilizadores visitam sites que não estão listados no seu limite de rede isolada, os sites abertos numa sessão de navegação virtual do Hyper-V. Sites fidedignos são definidos por um limite de rede, o que são configurados na configuração do dispositivo.

O Application Guard só está disponível para dispositivos com o Windows 10 (64 bits). Se utilizar este perfil, instalará um componente do Win32 para ativar o Application Guard.

- **Application Guard**: **Ativado para o Edge** para ativar esta funcionalidade, o que abre sites não fidedignos num contentor de navegação virtualizado Hyper-V. **Não configurado** (predefinição), significa que qualquer site (fidedignos e não fidedignas) abre-se no dispositivo.
- **Comportamento de área de transferência**: Escolha que ações de copiar/colar são permitidas entre o PC local e o browser virtual do Application Guard.
- **Conteúdo externo em sites de empresa**: **Bloco** conteúdo de sites não aprovados sejam carregados. A opção **Não configurado** (predefinição) significa que podem ser abertos sites não empresariais no dispositivo.
- **Imprimir a partir do virtual browser**: Escolher **permitir** local PDF, XPS, assim, e impressoras de rede podem imprimir conteúdo a partir do virtual browser. A opção **Não configurado** (predefinição) desativa todas as funcionalidades de impressão.
- **Recolher registos**: **Permitir** para recolher registos de eventos que ocorrem numa sessão de navegação do Application Guard. A opção **Não configurado** (predefinição) não recolhe registos na sessão de navegação.
- **Reter dados do browser gerados pelo utilizador**: **Permitir** guarda os dados de utilizador (por exemplo, as palavras-passe, Favoritos e cookies) que são criados durante uma sessão de navegação virtual do Application Guard. A opção **Não configurado** (predefinição) elimina os dados e ficheiros transferidos pelos utilizadores quando o dispositivo é reiniciado ou quando um utilizador termina a sessão.
- **Aceleração de gráficos**: Escolher **ativar** para carregar sites de grande intensidade de gráficos e vídeo mais rápido ao obter acesso a uma unidade de processamento de gráficos virtual. A opção **Não configurado** (predefinição) utiliza o CPU do dispositivo para gráficos; não utiliza a unidade de processamento gráfico virtual.
- **Transferir ficheiros para o sistema de ficheiros anfitrião**: **Ativar** para que os utilizadores transferem ficheiros do browser virtualizado para o sistema operativo anfitrião. A opção **Não configurado** (predefinição) mantém os ficheiros no dispositivo e não transfere ficheiros para o sistema de ficheiros anfitrião.

## <a name="windows-defender-firewall"></a>Firewall do Windows Defender

Suportado nas seguintes edições do Windows 10:
- Casa
- Profissional
- Empresa
- Empresarial
- Educação
- móvel
- Mobile Enterprise

### <a name="global-settings"></a>Definições globais

Estas definições são aplicáveis a todos os tipos de rede.

- **Protocolo de transferência de ficheiros**: **Bloco** para desativar o FTP com monitorização de estado. Com a opção **Não configurado** (predefinição), a firewall filtra o FTP com monitorização de estado para permitir ligações secundárias.
- **Tempo de inatividade de associação de segurança antes da eliminação**: As associações de segurança são eliminadas quando o tráfego de rede não é detetado durante *n* segundos. Introduza um tempo inativo em segundos.
- **Codificação de chave pré-partilhada**: Escolher **ativar** usar codificação principais do pré-partilhadas utilizando UTF-8. A opção **Não configurado** (predefinição) utiliza o valor do arquivo no local.
- **Isenções de IPsec**: Configurar o tráfego específico para ser isento de IPsec, incluindo:
  - **Descoberta de vizinho de códigos do tipo IPv6 ICMP**
  - **ICMP**
  - **Descoberta de router de códigos do tipo IPv6 ICMP**
  - **Tráfego de rede de IPv4 e IPv6 DHCP**
- **Verificação da lista de revogação de certificado**: Escolha a forma como o dispositivo verifica a lista de revogação de certificados. As opções incluem **verificação de CRL desativar**, **verificação falhar CRL apenas no certificado revogado**, e **verificação de CRL falhar em qualquer erro encontrado**.
- **Fazer corresponder oportunisticamente ao conjunto de autenticação por módulo de keying**: **Ativar** para módulos de keying devem ignorar apenas os pacotes de autenticação que eles não oferecem suporte. Com a opção **Não configurado**, os módulos de keying TÊM de ignorar todo o conjunto de autenticação se não suportarem todos os conjuntos de autenticação especificados no conjunto.
- **Pacotes de colocação**: Introduza a como o dimensionamento no lado do recebimento de software está ativado para a receção encriptada e desmarque o reencaminhamento de texto para o cenário de gateway de túnel IPsec. Esta definição confirma que o pedido de pacote é preservado.

### <a name="network-settings"></a>Definições de rede

Estas definições são aplicáveis a tipos de rede específicos, incluindo **Rede de domínio (área de trabalho)**, **Rede privada (detetável)** e **Rede pública (não detetável)**.

#### <a name="general-settings"></a>Definições gerais

- **Firewall do Windows Defender**: Escolher **ativar** para ativar a firewall e a segurança avançada. A opção **Não configurado** (predefinição) permite todo o tráfego de rede, independentemente de outras definições de políticas.
- **O modo invisível**: **Bloco** a firewall de funcionar no modo invisível. Esta definição também lhe permite bloquear a **Exceção de pacotes seguros com IPsec**. A opção **Não configurado** (predefinição) opera a firewall em modo furtivo, o que ajuda a impedir respostas a pedidos de pesquisa.
- **Blindada**: **Bloco** desativa esta funcionalidade. A opção **Não configurado** (predefinição) ativa esta definição. Quando esta definição e a Firewall do Windows Defender estão ativadas, todo o tráfego recebido é bloqueado, independentemente de outras definições de políticas.
- **Respostas unicast às difusões multicast**: Quando definido como **bloco**, desativa respostas unicast às difusões multicast. Normalmente, não quer receber respostas unicast para mensagens multicast ou de difusão. Essas respostas podem indicar uma negação de ataques de serviço (DOS), ou por um atacante a tentar sondar um computador conhecido. A opção **Não configurado** (predefinição) ativa esta definição.
- **Notificações de entrada**: Quando definido como **bloco**, ele oculta notificações aos utilizadores quando uma aplicação é impedida de escutar numa porta. A opção **Não configurado** (predefinição) ativa esta definição e poderá mostrar uma notificação aos utilizadores quando uma aplicação é impedida de escutar numa porta.
- **Ação para ligações de entrada predefinida**: Quando definido como **bloco**, a ação de firewall padrão não está a ser executada em ligações de entrada. Quando definida para **Não configurado** (predefinição), a ação predefinida da firewall é executada em ligações de receção.

#### <a name="rule-merging"></a>Intercalação de regras

- **Autorizado regras de Firewall do Windows Defender de aplicação do arquivo local**: Escolher **ativar** para aplicar regras de firewall no arquivo local, para que eles são reconhecidos e executados. Quando definida para **Não configurado** (predefinição), as regras de firewall da aplicação autorizadas no arquivo local são ignoradas e não são impostas.
- **Regras de Firewall do Windows Defender de portas globais do arquivo local**: Escolher **ativar** para aplicar regras de firewall de portas globais no arquivo local a serem reconhecidas e executadas. Quando definida para **Não configurado** (predefinição), as regras de firewall da porta global no arquivo local são ignoradas e não são impostas.
- **Regras de Firewall do Windows Defender do arquivo local**: Escolher **ativar** para aplicar regras de firewall no arquivo local a serem reconhecidas e executadas. Quando definida para **Não configurado** (predefinição), as regras de firewall do arquivo local são ignoradas e não são impostas.
- **Regras de IPsec do arquivo local**: Escolher **ativar** para aplicar regras de segurança de ligação do arquivo local, independentemente do esquema ou ligação versões de regra de segurança. Quando definida para **Não configurado** (predefinição), as regras de segurança de ligação do arquivo local são ignoradas e não são impostas, independentemente da versão do esquema e versão da regra de segurança da ligação.

## <a name="windows-defender-smartscreen-settings"></a>Definições do Windows Defender SmartScreen

Suportado nas seguintes edições do Windows 10 com o Microsoft Edge instalado:
- Casa
- Profissional
- Empresa
- Empresarial
- Educação
- móvel
- Mobile Enterprise

**Definições**:

- **SmartScreen para aplicações e ficheiros**: **Ativar** Windows SmartScreen para execução de ficheiros e aplicações em execução. O SmartScreen é um componente anti-phishing e anti-malware baseado na cloud. A opção **Não configurado** (predefinição) desativa o SmartScreen.
- **Execução de ficheiros de verificados**: **Bloco** os utilizadores finais a execução de ficheiros que ainda não foram verificados pelo Windows SmartScreen. A opção **Não configurado** (predefinição) desativa esta funcionalidade e permite que os utilizadores finais executem ficheiros não verificados.

## <a name="windows-encryption"></a>Encriptação do Windows

### <a name="windows-settings"></a>Definições do Windows

Suportado nas seguintes edições do Windows 10:

- Profissional
- Empresa
- Empresarial
- Educação
- móvel
- Mobile Enterprise

**Definições**:

- **Encriptar dispositivos**: **Exigir** para solicitar aos utilizadores para ativar a encriptação de dispositivo. Consoante a edição do Windows e configuração do sistema, poderá ser pedido aos utilizadores:  
  - Que confirmem que a encriptação de outro fornecedor não foi ativada
  - Que desativem a Encriptação de Unidade BitLocker e, em seguida, voltem a ativar o BitLocker
    
    Se a encriptação do Windows for ativada enquanto outro método de encriptação estiver ativo, o dispositivo pode tornar-se instável. 
- **Encriptar cartão de armazenamento (apenas móvel)**: **Exigir** para encriptar os cartões de memória utilizados pelo dispositivo. A opção **Não configurado** (predefinição) não necessita da encriptação dos cartões de armazenamento e não pede ao utilizador para a ativar. Esta definição só se aplica a dispositivos com o Windows 10 Mobile.

### <a name="bitlocker-base-settings"></a>Definições base do BitLocker

Suportado nas seguintes edições do Windows 10:

- Empresarial
- Educação
- móvel
- Mobile Enterprise
- Profissional

As definições base são definições de BitLocker universais para todos os tipos de unidades de dados. Estas definições gerem as tarefas de encriptação ou opções de configuração de unidades que o utilizador final pode modificar para todos os tipos de unidades de dados.

- **Aviso para a encriptação de outro disco**: Selecione **bloco** para desativar a mensagem de aviso se for de outro serviço de encriptação de disco no dispositivo. A opção **Não configurado** (predefinição) permite que o aviso seja apresentado.
    - **Permitir que usuários padrão ativar a encriptação durante a associação do Azure AD**: Quando escolhe **permitir**, padrão utilizadores/não-administradores podem ativar a encriptação BitLocker quando o utilizador tem sessão iniciado. Esta definição aplica-se apenas a dispositivos do Azure associados de diretório Active Directory (Azure ADJ). **Não configurado** apenas permite que os administradores ativar a encriptação de disco BitLocker no dispositivo.
      
      Esta definição aplica-se apenas a dispositivos do Azure associados de diretório Active Directory (Azure ADJ). Também requer que o **aviso para a encriptação de outro disco** definição estar definida como **bloco**.
- **Configurar métodos de encriptação**: **Ativar** esta definição para configurar algoritmos de encriptação para o sistema operativo, dados e unidades amovíveis. Quando definida para **Não configurado** (predefinição), o BitLocker utiliza o algoritmo XTS-AES de 128 bits como o método de encriptação predefinido ou utiliza o método de encriptação especificado por qualquer script de configuração.
  - **Encriptação para o sistema operativo unidades**: Escolha o método de encriptação para unidades de sistema operativo. Recomendamos que utilize o algoritmo XTS-AES.
  - **Encriptação para unidades de dados fixas**: Escolha o método de encriptação para unidades de dados (interno) fixo. Recomendamos que utilize o algoritmo XTS-AES.
  - **Encriptação para unidades de dados removíveis**: Escolha o método de encriptação para unidades de dados amovíveis. Se a unidade amovível for utilizada com dispositivos que não executam o Windows 10, recomendamos que utilize o algoritmo AES-CBC.

### <a name="bitlocker-os-drive-settings"></a>Definições de unidades de SO do BitLocker
Suportado nas seguintes edições do Windows 10:

- Empresarial
- Educação
- móvel
- Mobile Enterprise
- Profissional

Estas definições aplicam-se especificamente a unidades de dados do sistema operativo.

- **Autenticação adicional no arranque**: Selecione **requerem** para configurar os requisitos de autenticação para o arranque do computador, incluindo a utilização do Trusted Platform Module (TPM). Selecione **Não configurado** (predefinição) para configurar apenas opções básicas em dispositivos com um TPM.
  - **BitLocker com chip do TPM não compatível**: **Bloco** (desabilitar) usando o BitLocker quando um dispositivo não tem um chip TPM compatível. Quando definida para **Não configurado**, os utilizadores podem usar o BitLocker sem um chip TPM compatível. O BitLocker poderá precisar de uma palavra-passe ou de uma chave de arranque.
  - **Arranque do TPM compatível**: Opte por permitir, não permitir ou exigir o chip do TPM.
  - **PIN de arranque do TPM compatível**: Opte por permitir, não permitir ou exigir a utilizar um PIN de arranque do TPM. Para ativar um PIN de arranque, é necessária interação por parte do utilizador final. 
  - **Chave de arranque do TPM compatível**: Opte por permitir, não permitir ou exigir a utilizar uma chave de arranque do TPM. Para ativar uma chave de arranque, é necessária interação por parte do utilizador final. 
  - **Chave de arranque do TPM compatível e PIN**: Opte por permitir, não permitir ou exigir a utilizar uma chave de arranque e de PIN com o chip do TPM. Para ativar uma chave e PIN de arranque, é necessária interação por parte do utilizador final.
- **Comprimento mínimo do PIN**: **Ativar** esta definição para configurar um comprimento mínimo para o PIN de arranque do TPM. Quando definida para **Não configurado** (predefinição), os utilizadores podem configurar um PIN de arranque entre 6 e 20 dígitos.
  - **Carateres mínimos**: Introduza o número de carateres necessários para o PIN de arranque de **4**-**20**.
- **Recuperação da unidade de SO**: **Ativar** esta definição para controlar o sistema operativo protegidas como BitLocker unidades recuperar, quando as informações de arranque necessárias não estão disponíveis. Quando definida para **Não configurado** (predefinição), as operações de recuperação predefinidas são suportadas pela recuperação do BitLocker. Por predefinição, é permitido um DRA, as opções de recuperação são escolhidas pelo utilizador, incluindo a palavra-passe de recuperação e a chave de recuperação, e informações de recuperação não não uma cópia de segurança para o AD DS.
  - **Agente de recuperação de dados baseada em certificado**: Quando definido como **bloco**, não é possível utilizar o agente de recuperação de dados com unidades de SO protegidas pelo BitLocker. Defina esta opção para **Não configurado** (predefinição) para ativar esta definição para permitir que os agentes de recuperação de dados possam ser utilizados com as unidades de sistema operativo protegidas pelo BitLocker.
  - **Criação de utilizador de palavra-passe de recuperação**: Escolha se os utilizadores são permitidos, necessário ou não permissão para gerar uma palavra-passe de recuperação de 48 dígitos.
  - **Criação do utilizador da chave de recuperação**: Escolha se os utilizadores são permitidos, necessário ou não permissão para gerar uma chave de recuperação de 256 bits.
  - **Opções de recuperação no Assistente de configuração do BitLocker**: Defina como **bloco** para que os utilizadores não podem ver e alterar as opções de recuperação. Quando definida para **Não configurado** (predefinição), os utilizadores podem ver e alterar as opções de recuperação ao ativarem o BitLocker.
  - **Guardar as informações de recuperação do BitLocker para o AD DS**: Escolher **ativar** para armazenar as informações de recuperação do BitLocker para Azure Active Directory (AAD). Quando definida para **Não configurado** (predefinição), as informações de recuperação não são armazenadas no Azure Active Directory.
  - **Recuperação do BitLocker informações armazenadas no AD DS**: Configure que partes das informações de recuperação do BitLocker são armazenadas no Azure AD. Escolha entre:
    - **Palavras-passe de recuperação de cópia de segurança e pacotes de chaves**
    - **Apenas palavras-passe de recuperação de cópia de segurança**
  - **Store informações de recuperação no AD DS antes de ativar o BitLocker**: **Exigir** esta definição para impedir os utilizadores de ativarem o BitLocker, a menos que as informações de recuperação do BitLocker estejam armazenadas com êxito no Azure Active Directory (AD). **Não configurado** (predefinição) permite aos utilizadores ativar o BitLocker, mesmo que as informações de recuperação com êxito não estão armazenadas no Azure AD.
- **De pré-arranque mensagem de recuperação e o URL**: **Ativar** esta definição para configurar a mensagem e o URL que são apresentados no ecrã de recuperação de chave de pré-arranque. A opção **Não configurado** (predefinição) desativa esta funcionalidade.
  - **Mensagem de recuperação de pré-arranque**: Configure a forma como a mensagem de recuperação de pré-arranque é apresentado aos utilizadores. Escolha entre:
    - **Utilizar mensagem de recuperação predefinida e URL**
    - **Utilizar mensagem de recuperação vazia e URL**
    - **Utilizar mensagem de recuperação personalizada**
    - **Utilizador URL de recuperação personalizada**

### <a name="bitlocker-fixed-data-drive-settings"></a>Definições de unidades de dados fixas do BitLocker

Suportado nas seguintes edições do Windows 10:

- Empresarial
- Educação
- móvel
- Mobile Enterprise
- Profissional

**Definições**:

- **Acesso de escrita para unidade de dados fixa não protegida pelo BitLocker**: Defina como **bloco** para lhe conceder acesso só de leitura às unidades de dados que não são protegidas pelo BitLocker. Quando **não configurado** do (predefinição), existem acesso de leitura e escrita para unidades de dados que não são protegidas pelo BitLocker.
- **Recuperação de unidade fixa**: **Ativar** esta definição para controlar como as unidades fixas protegidas pelo BitLocker recuperar quando as informações de arranque necessárias não estão disponíveis. A opção **Não configurado** (predefinição) desativa esta funcionalidade.
  - **Agente de recuperação de dados**: **Bloco** unidades Editor de políticas de fixas da utilização do agente de recuperação de dados com protegidas pelo BitLocker. A opção **Não configurado** (predefinição) permite a utilização de agentes de recuperação de dados com unidades fixas protegidas pelo BitLocker.
  - **Criação de utilizador de palavra-passe de recuperação**: Configure se os utilizadores são permitidos, necessário ou não permissão para gerar uma palavra-passe de recuperação de 48 dígitos.  
  - **Criação do utilizador da chave de recuperação**: Configure se os utilizadores são permitidos, necessário ou não permissão para gerar uma chave de recuperação de 256 bits.
  - **Opções de recuperação no Assistente de configuração do BitLocker**: Defina como **bloco** para que os utilizadores não podem ver e alterar as opções de recuperação. Quando definida para **Não configurado** (predefinição), os utilizadores podem ver e alterar as opções de recuperação ao ativarem o BitLocker.
  - **Guardar as informações de recuperação do BitLocker para o Azure Active Directory**: Escolher **ativar** para armazenar as informações de recuperação do BitLocker no Azure Active Directory (Azure AD). Quando **não configurado** (predefinição), as informações de recuperação não estão armazenadas no Azure AD.
  - **Recuperação do BitLocker informações armazenadas para o Azure Active Directory**: Configure que partes das informações de recuperação do BitLocker são armazenadas no Azure AD. As opções são:
    - **Palavras-passe de recuperação de cópia de segurança e pacotes de chaves**
    - **Apenas palavras-passe de recuperação de cópia de segurança**
  - **Store informações de recuperação no Azure Active Directory antes de ativar o BitLocker**: **Exigir** esta definição para impedir os utilizadores de ativarem o BitLocker, a menos que as informações de recuperação do BitLocker estejam armazenadas com êxito no Azure AD. **Não configurado** (predefinição) permite aos utilizadores ativar o BitLocker, mesmo que as informações de recuperação não estejam armazenadas com êxito no Azure AD.

### <a name="bitlocker-removable-data-drive-settings"></a>Definições de unidades de dados removíveis do BitLocker

Suportado nas seguintes edições do Windows 10:

- Empresarial
- Educação
- móvel
- Mobile Enterprise
- Profissional

**Definições**:

- **Acesso de escrita para unidade de dados removível não protegida pelo BitLocker**: Defina como **bloco** para lhe conceder acesso só de leitura às unidades de dados que não são protegidas pelo BitLocker. Quando **não configurado** do (predefinição), existem acesso de leitura e escrita para unidades de dados que não são protegidas pelo BitLocker.
  - **Acesso de escrita para dispositivos configurados noutra organização**: **Bloco** permite o acesso de escrita para dispositivos configurados noutra organização. **Não configurado** (predefinição) impede o acesso de escrita.

## <a name="windows-defender-exploit-guard"></a>Windows Defender Exploit Guard

Suportado nas seguintes edições do Windows 10:

- Casa
- Profissional
- Empresa
- Empresarial
- Educação
- móvel
- Mobile Enterprise

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

#### <a name="rules-to-protect-against-ransomware"></a>Regras para proteger contra Ransomware
- **Proteção de ransomware avançada**

> [!TIP]
> O artigo [Reduce attack surfaces with Windows Defender Exploit Guard (Reduzir a ocorrência de ataques com o Windows Defender Exploit Guard)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard) fornece mais detalhes sobre estas regras.

#### <a name="attack-surface-reduction-exceptions"></a>Exceções da Redução da Superfície de Ataque

- **Regras da redução de superfície de ficheiros e pastas a excluir de ataque**: Importe/adicione uma lista de localizações a excluir das regras configuradas.

> [!IMPORTANT]
> Para permitir a instalação adequada e a execução de aplicações LOB do departamento de Win32, definições de antimalware devem excluir os seguintes diretórios sejam analisadas:<p>
> **No X64 máquinas cliente**:<br>
> *C:\Program ficheiros (x86) \Microsoft Intune gestão Extension\Content*<br>
> *C:\windows\IMECache*
>  
> **Em X86 máquinas cliente**:<br>
> *C:\Program Files\Microsoft Intune gestão Extension\Content*<br>
> *C:\windows\IMECache*

### <a name="controlled-folder-access"></a>Acesso a pastas controladas

Ajude a proteger dados valiosos de ameaças e aplicações malignas, tal como ransomware.

- **Proteção de pastas**: Proteger ficheiros e pastas contra alterações indesejadas por aplicações maliciosas. Pode importar uma **Lista de aplicações que têm acesso a pastas protegidas** ou adicioná-las manualmente. Também pode adicionar uma **Lista de pastas adicionais que necessitam ser protegidas** com um carregamento ou adicioná-las manualmente.

### <a name="network-filtering"></a>Filtragem de rede

- **Proteção de rede**: Protege ligações de saída de qualquer aplicação para endereços IP com baixa reputação ou domínios. A intenção é proteger os utilizadores finais das aplicações com acesso atos fraudulentos de phishing, sites que hospedam a exploração e conteúdo malicioso na Internet. Também evita que os browsers de terceiros de se ligar a sites perigosos.

  As opções são:

  - A opção **Não configurado** (predefinição) desativa esta funcionalidade. Utilizadores e aplicações não são impedidas de se ligar a domínios perigosos. Os administradores não é possível ver essa atividade no Centro de segurança do Windows Defender.
  - **Ativar** ativa a proteção de rede e os utilizadores de blocos e aplicações de se ligar a domínios perigosos. Os administradores podem ver esta atividade no Centro de segurança do Windows Defender.
  - **Apenas auditoria**: Utilizadores e aplicações não são impedidas de se ligar a domínios perigosos. Os administradores podem ver esta atividade no Centro de segurança do Windows Defender.

  [Defender/EnableNetworkProtection CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-enablenetworkprotection)

### <a name="exploit-protection"></a>Exploit Protection

Para utilizar a proteção de exploração, crie um ficheiro XML que inclui as definições de mitigação de sistema e da aplicação que pretende. Existem dois métodos:

 1. PowerShell: Utilize um ou mais dos cmdlets Get-ProcessMitigation, Set-ProcessMitigation e ConvertTo-ProcessMitigationPolicy do PowerShell. Os cmdlets configuram definições de mitigação e exportam uma representação XML deles.

 2. Interface do Usuário do Centro de segurança do Windows Defender: No Centro de segurança do Windows Defender, clique no controlo de browser e de aplicação e, em seguida, desloque-se para a parte inferior do ecrã resultante para localizar o Exploit Protection. Em primeiro lugar, utilize as definições do sistema e os separadores das definições de programa para configurar definições de atenuação. Em seguida, localize a ligação de definições de Exportação na parte inferior do ecrã para exportar uma representação XML dos mesmos.

Bloqueie a **Edição da interface do Exploit Protection por parte dos utilizadores** ao carregar um ficheiro XML que lhe permite configurar a memória, controlar o fluxo e as restrições de políticas. As definições no ficheiro XML podem servir para proteger uma aplicação de exploits. A opção **Não configurado** (predefinição) não aplica uma configuração personalizada. 

## <a name="windows-defender-application-control"></a>Controlo de Aplicações do Windows Defender

Suportado nas seguintes edições do Windows 10:

**Gestão de Dispositivos Móveis (MDM)**: 
- Profissional
- Empresa
- Empresarial
- Educação
- móvel
- Mobile Enterprise

**Gestão de políticas de grupo**: 
- Empresarial

Utilize as **Políticas de integridade do código de controlo de aplicações** para escolher as aplicações adicionais que são auditadas ou que são consideradas de confiança para serem executadas pelo Controlo de Aplicações do Windows Defender. Os componentes do Windows e todas as aplicações da Microsoft Store são automaticamente considerados de confiança para serem executados.

As aplicações não são bloqueadas quando são executadas no modo **apenas auditoria**. O modo **Apenas auditoria** regista todos os eventos nos registos do cliente local.

Uma vez ativado, o Controlo de Aplicações só poderá ser desativado ao alterar o modo de **Impor** para **Apenas auditoria**. Se alterar do modo de **Impor** para **Não Configurado** o Controlo de Aplicações continuará a ser imposto nos dispositivos atribuídos.

## <a name="windows-defender-credential-guard"></a>Windows Defender Credential Guard

Suportado nas seguintes edições do Windows 10:

- Empresarial

O Windows Defender Credential Guard protege contra ataques de roubo de credenciais. Isola os segredos para permitir o acesso apenas a software de sistema com privilégios.

As definições do **Credential Guard** incluem:

- **Desativar**: Desativa o Credential Guard remotamente, se ele tiver sido ativado com o **ativada sem bloqueio UEFI** opção.

- **Ativar com bloqueio UEFI**: Credential Guard não pode ser desativado remotamente com uma chave de registo ou política de grupo.

    > [!NOTE]
    > Se utilizar esta definição e, em seguida, quiser desativar o Credential Guard, terá de definir a Política de Grupo como **Desativado**. Além disso, tem de limpar fisicamente as informações de configuração de UEFI de cada computador. Enquanto a configuração da UEFI persistir, o Credential Guard estará ativado.

- **Ativar sem bloqueio UEFI**: Permite que o Credential Guard seja desativado remotamente através da política de grupo. Os dispositivos que utilizam esta definição têm de ter a versão 1511 ou mais recente do Windows 10.

Quando ativar o Credential Guard, as seguintes funcionalidades necessárias também são ativadas:

- **Segurança baseada em Virtualização** (VBS): Ativa durante a próxima reinicialização. A segurança baseada em Virtualização utiliza o Windows Hypervisor para dar suporte aos serviços de segurança e requer o Windows Hypervisor.
- **Arranque com o acesso de memória do seguro**: Ativa o VBS com a inicialização segura e proteções de acesso (DMA) de memória direto. As proteções de DMA necessitam de suporte de hardware e são ativadas apenas em dispositivos configurados corretamente.

## <a name="windows-defender-security-center"></a>Centro de Segurança do Windows Defender

Suportado nas seguintes edições do Windows 10:

- Casa
- Profissional
- Empresa
- Empresarial
- Educação
- móvel
- Mobile Enterprise

O Centro de Segurança do Windows Defender funciona como uma aplicação ou processo separado de cada uma das funcionalidades individuais. Apresenta notificações através do Centro de Ação. Ele atua como um recoletor ou único local para ver o estado e executar alguma configuração para cada uma das funcionalidades. Saiba mais na documentação do [Windows Defender](https://docs.microsoft.com/windows/threat-protection/windows-defender-security-center/windows-defender-security-center).

#### <a name="windows-defender-security-center-app-and-notifications"></a>Aplicações e notificações do Centro de Segurança do Windows Defender

Bloqueie o acesso de utilizadores finais a várias áreas da aplicação Centro de Segurança do Windows Defender. Ocultar uma secção também bloqueia notificações relacionadas.

- **Proteção contra vírus e ameaças**
- **Desempenho e estado de funcionamento do dispositivo**
- **Firewall e proteção da rede**
- **Controlo de aplicações e browsers**
- **Opções de família**
- **Notificações das áreas apresentadas da aplicação**: Escolha quais as notificações a apresentar aos utilizadores finais. As notificações não críticas incluem resumos de atividade do Antivírus do Windows Defender, incluindo notificações quando as análises forem concluídas. Todas as outras notificações são consideradas críticas.

#### <a name="it-contact-information"></a>Informação de contacto de TI

Forneça as informações de contacto de TI para que sejam apresentadas na aplicação Centro de Segurança do Windows Defender e nas notificações da aplicação. Pode optar por **Mostrar na aplicação e nas notificações**, **Mostrar apenas na aplicação**, **Mostrar apenas nas notificações** ou **Não mostrar**. Introduza o **Nome da organização de TI** e pelo menos uma das seguintes opções de contacto:

- **Número de telefone ou ID do Skype do departamento de TI**
- **Endereço de e-mail do departamento de TI**
- **URL do site de suporte de TI**

## <a name="local-device-security-options"></a>Opções de segurança do dispositivo local

Suportado nas seguintes edições do Windows 10:
 
- Casa
- Profissional
- Empresa
- Empresarial
- Educação

Utilize estas opções para configurar as definições da segurança local em dispositivos Windows 10.

### <a name="accounts"></a>Contas

- **Adicionar novas contas Microsoft**: Defina como **bloco** para impedir que os utilizadores adicionem novas contas Microsoft ao dispositivo. Quando definida para **Não configurado** (predefinição), os utilizadores podem utilizar contas Microsoft no dispositivo.
- **Início de sessão remoto sem palavra-passe**: **Bloco** permite que apenas as contas locais com palavras-passe em branco para iniciar sessão com o teclado do dispositivo. A opção **Não configurado** (predefinição) permite que as contas locais com palavras-passe vazias iniciem sessão em localizações que não o dispositivo físico.

#### <a name="admin"></a>administrador

- **Conta de administrador local**: Defina como **ativado** para permitir que a conta de administrador local. Defina para **Não configurado** (predefinição) para desativar a conta de administrador local.
- **Mudar o nome da conta de administrador**: Defina um nome de conta diferente para ser associado ao identificador de segurança (SID) da conta de administrador.

#### <a name="guest"></a>Convidado

- **Conta de convidado**: Defina como **ativado** para permitir que a conta de convidado locais. Defina para **Não configurado** (predefinição) para desativar a conta de convidado local.
- **Mudar o nome da conta de convidado**: Defina um nome de conta diferente para ser associado ao identificador de segurança (SID) para a conta de convidado.

### <a name="devices"></a>Dispositivos

- **Desancorar dispositivo sem início de sessão**: Defina como **bloco** para que os usuários podem pressionar física do dispositivo portátil encaixado ejetar botão para desencaixar com segurança no dispositivo. A opção **Não configurado** (predefinição) exige que o utilizador inicie sessão no dispositivo e receba permissão para o desancorar.
- **Instalar controladores de impressora para impressoras partilhadas**: Quando **ativado**, qualquer usuário pode instalar um driver de impressora como parte da ligação a uma impressora partilhada. Quando definida para **Não configurado** (predefinição), apenas os Administradores podem instalar um controlador de impressora como parte da ligação a uma impressora partilhada.
- **Restringir o acesso de CD-ROM ao utilizador ativo local**: Quando **ativado**, apenas o utilizador de forma interativa com sessão iniciada pode usar a mídia de CD-ROM. Se esta política estiver ativada e ninguém tiver sessão iniciada de forma interativa, a unidade de CD-ROM será acedida através da rede. Quando definida para **Não configurado** (predefinição), qualquer pessoa têm acesso à unidade de CD-ROM.
- **Formatar e ejetar suporte amovível**: Defina quem tem permissão para formatar e ejetar suportes NTFS amovíveis:
  - **Não configurado**
  - **Administradores**
  - **Administradores e Utilizadores Avançados**
  - **Administradores e Utilizadores Interativos**

### <a name="interactive-logon"></a>Início de sessão interativo

- **Minutos de bloqueio de inatividade do ecrã quando ativa a proteção de tela**: Introduza o máximo de minutos de inatividade no ecrã de início de sessão do ambiente de trabalho interativo até que a proteção de tela é iniciado.
- **Exigir CTRL + ALT + DEL para logon**: Defina como **ativar** para premir CTRL + ALT + DEL não é necessária para os utilizadores iniciem sessão. Defina para **Não configurado** (predefinição) para que os utilizadores tenham de premir Ctrl+Alt+Delete para iniciarem sessão no Windows.
- **Comportamento de remoção do smart card**: Determina o que acontece quando o smart card para um utilizador com sessão iniciada é removido de leitor de smart card. As opções são:

  - **Bloquear estação de trabalho**: A estação de trabalho é bloqueada quando o smart card é removido. Esta opção permite que os utilizadores saiam da área, levem os seus smart cards e permaneçam numa sessão protegida.
  - **Forçar fim da sessão**: O utilizador é terminado automaticamente quando o smart card é removido.
  - **Desligar se uma sessão de serviços de ambiente de trabalho remoto**: Remoção do smart card termina a sessão sem fazer logoff do usuário. Esta opção permite que o utilizador insira o smart card e retome a sessão mais tarde, ou noutro computador com um leitor de smart cards, sem ter de iniciar sessão novamente. Se a sessão for local, esta política funciona da mesma forma que Bloquear Estação de Trabalho.

    As [opções LocalPoliciesSecurity](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-localpoliciessecurityoptions#localpoliciessecurityoptions-interactivelogon-smartcardremovalbehavior) proporcionam mais detalhes.

#### <a name="display"></a>Apresentar

- **Informações de utilizador no ecrã de bloqueio**: Configure as informações de utilizador que são apresentadas quando a sessão está bloqueada. Se não estiverem configuradas, serão apresentados o nome a apresentar do utilizador, o domínio e o nome de utilizador.
  - **Não configurado**  
  - **O nome a apresentar do utilizador, o domínio e o nome de utilizador**
  - **Apenas o nome a apresentar do utilizador**
  - **Não apresentar informações do utilizador**
- **Ocultar último utilizador com sessão iniciada**: **Ativar** oculta o nome de utilizador. A opção **Não configurado** (predefinição) mostra o nome de utilizador.
- **Ocultar nome de utilizador no início de sessão**: **Ativar** oculta o nome de utilizador. A opção **Não configurado** (predefinição) mostra o nome de utilizador.
- **Título da mensagem de início de sessão**: Defina o título de mensagem para os utilizadores a iniciar sessão.
- **Texto da mensagem de início de sessão**: Defina o texto da mensagem para os utilizadores a iniciar sessão.

### <a name="network-access-and-security"></a>Acesso à rede e segurança

- **Acesso anónimo a Pipes nomeados e partilhas**: **Não configurado** (predefinição) restringe o acesso anónimo a partilhas e configurações de Pipe nomeado. Aplica-se as definições que podem ser acedidas anonimamente.
- **Enumeração anónima de contas SAM**: **Permitir** aos utilizadores anónimos enumerem as contas SAM. O Windows permite que os utilizadores anónimos enumerem os nomes das contas de domínio e das partilhas de rede.
- **Enumeração anónima de contas e partilhas SAM**: **Não configurado** (predefinição) significa que os usuários anônimos podem enumerar os nomes de contas de domínio e partilhas de rede. Para impedir a enumeração anónima de contas e partilhas SAM, defina como **Bloquear**.
- **Valor de hash do LAN Manager armazenado na alteração de palavra-passe**: Na próxima alteração de palavra-passe, optar por **permitir** do LM (LAN Manager) para armazenar o valor de hash da palavra-passe nova. Quando definida para **Não configurado** (predefinição), o valor hash não é armazenado.
- **Pedidos de autenticação PKU2U**: **Bloco** pedidos de autenticação PKU2U para o dispositivo para utilizar identidades online. **Não configurado** (predefinição) permite estes pedidos.
- **Restringir ligações remotas de RPC a SAM**: Defina como **permitir** para negar a utilizadores e grupos de fazer chamadas remotas de RPC para a segurança Gestor de contas (SAM), que armazena as contas de utilizador e palavras-passe. **Permitir** também permite que altere a cadeia de linguagem de definição de descritor de segurança (SDDL) predefinida para explicitamente permitir ou negar utilizadores e grupos para tornar essas chamadas remotas. **Não configurado** (predefinição) utiliza o descritor de segurança padrão e pode permitir que os utilizadores e grupos fazer chamadas RPC remotas para SAM.
  - **Descritor de segurança**

### <a name="recovery-console-and-shutdown"></a>Consola de recuperação e encerramento

- **Ficheiro de paginação de memória clara do virtual ao encerrar**: Defina como **ativar** para limpar o ficheiro de paginação de memória virtual quando o dispositivo estiver desligado. A opção **Não configurado** (predefinição) não limpa a memória virtual.
- **Encerrar sem registo em**: **Bloco** oculta a opção de encerrar no ecrã de início de sessão de Windows. Os utilizadores têm de iniciar sessão no dispositivo e, em seguida, encerrar. **Não configurado** (predefinição) permite aos utilizadores encerrar o dispositivo a partir do início de sessão do Windows no ecrã.

### <a name="user-account-control"></a>Controlo de conta de utilizador

- **Integridade de UIA sem localização segura**: Quando definido como **bloco**, as aplicações numa localização segura no sistema de arquivos são executadas apenas com integridade UIAccess. A opção **Não configurado** (predefinição) permite que as aplicações sejam executadas com o nível de integridade UIAccess, mesmo que não estejam numa localização segura no sistema de ficheiros.
- **Virtualizar falhas de escrita de arquivo e Registro para locais por usuário**: Quando definido como **ativado**, aplicativos que gravar dados protegidos localizações falhar. Quando definido como **não configurado** (predefinição), escrita de aplicativo redirecionadas falhas em tempo de execução para localizações de utilizador definidas para o sistema de ficheiros e registo.
- **Elevar apenas ficheiros executáveis assinados e validados**: Defina como **ativado** para impor a validação de caminho de certificação PKI para um ficheiro executável antes de ser executado. Defina para **Não configurado** (predefinição) para não impor a validação do caminho da certificação PKI antes da execução de um ficheiro executável.

#### <a name="uia-elevation-prompt-behavior-settings"></a>Definições do comportamento do pedido de elevação UIA

- **Solicitação de elevação para administradores**: Defina o comportamento do prompt de elevação para administradores no modo de aprovação de administrador:
  - **Elevar sem perguntar**
  - **Pedir credenciais no ambiente de trabalho seguro**
  - **Pedir consentimento no ambiente de trabalho seguro**
  - **Pedir credenciais**
  - **Pedir consentimento**
  - **Não configurado**: Pedir consentimento para binários não-Windows
- **Solicitação de elevação para usuários padrão**: Defina o comportamento do prompt de elevação para usuários padrão:
  - **Negar automaticamente pedidos de elevação**
  - **Pedir credenciais no ambiente de trabalho seguro**
  - **Não configurado**: Pedir credenciais
- **Encaminhar pedidos de elevação para área de trabalho interativa do usuário**: **Ativar** para que todos os pedidos de elevação para área de trabalho do utilizador interativo, não o ambiente de trabalho seguro. São utilizadas todas as definições de política de comportamento de pedidos para administradores e utilizadores padrão. A opção **Não configurado** (predefinição) obriga que todos os pedidos de elevação sejam encaminhados para o ambiente de trabalho seguro, independentemente das definições de política de comportamento de pedidos para administradores e utilizadores padrão.
- **Linha de comandos elevada para instalações de aplicações**: Quando definido como **ativado**, pacotes de instalação de aplicações não são detetados ou prompt de elevação. Quando definida para **Não configurado** (predefinição), é pedido um nome de utilizador e palavra-passe administrativos ao utilizador quando um pacote de instalação de aplicações exige privilégios elevados.
- **Solicitação de elevação UIA sem ambiente de trabalho seguro**: **Ativar** para permitir que aplicações UIAccess para elevação, sem utilizar a área de trabalho protegida. Quando definida para **Não configurado** (predefinição), os pedidos de elevação utilizam um ambiente de trabalho seguro.

#### <a name="admin-approval-mode-settings"></a>Definições do Modo de Aprovação de Administrador

- **Aprovação de administrador para administrador incorporado de modo**: **Ativado** permite que a conta interna de administrador utilizar o modo de aprovação de administrador. Qualquer operação que necessite de elevação de privilégios pede ao utilizador para aprovar a operação. A opção **Não configurado** (predefinição) executa todas as aplicações com privilégios de administrador totais.
- **Executar todos os administradores no modo de aprovação de administrador**: Defina como **ativado** desativar o modo de aprovação de administrador e todos os relacionados com as definições de política do UAC. A opção **Não configurado** (predefinição) ativa o Modo de Aprovação de Administrador.

### <a name="microsoft-network-client"></a>Cliente de Rede da Microsoft

- **Assinar digitalmente comunicações (se o servidor concordar)**: Determina se o cliente SMB negocia a assinatura de pacotes SMB. Quando definida como **Não configurado** ou ativada (predefinição), o cliente de rede da Microsoft pede ao servidor para executar a assinatura de pacotes SMB após a configuração da sessão. Se a assinatura de pacotes estiver ativada no servidor, a assinatura de pacotes será negociada. Se estiver definida como **Desativado**, o cliente SMB nunca negociará a assinatura de pacotes SMB.
- **Enviar palavra-passe não encriptada para servidores SMB de terceiros**: Quando definido como **ativar**, o redirecionador de bloco de mensagem de servidor (SMB) pode enviar palavras-passe de texto sem formatação para servidores SMB não Microsoft que não suportam a encriptação de palavra-passe durante a autenticação. Quando definida para **Não configurado** (predefinição), as palavras-passe são encriptadas.

### <a name="microsoft-network-server"></a>Servidor de Rede da Microsoft

- **Assinar digitalmente comunicações (se o cliente concordar)**: Determina se o servidor do SMB negocia com clientes solicitação-la de assinatura de pacotes SMB. Quando definida para **Ativar**, o servidor de rede da Microsoft negoceia a assinatura de pacotes SMB conforme pedido pelo cliente. Ou seja, se a assinatura de pacotes estiver ativada no cliente, a assinatura de pacotes será negociada. Quando **Não configurado** ou desativado (predefinição), o cliente SMB nunca negociará a assinatura de pacotes SMB.
- **Assinar digitalmente comunicações (sempre)**: Determina se a assinatura de pacotes é exigido pelo componente de servidor SMB. Quando definida para **Ativar**, o servidor de rede da Microsoft não comunica com um cliente de rede da Microsoft, a menos que o cliente aceite assinar pacotes SMB. Quando definida para **Não configurado** ou desativado (predefinição), a assinatura de pacotes SMB é negociada entre o cliente e o servidor.

## <a name="next-steps"></a>Passos Seguintes

O perfil está criado, mas ainda não está ativo. Em seguida, [atribuir o perfil](device-profile-assign.md), e [monitorizar o estado](device-profile-monitor.md).

Configurar as definições de proteção de ponto final no [macOS](endpoint-protection-macos.md) dispositivos.
