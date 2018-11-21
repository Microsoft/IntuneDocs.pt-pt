---
title: Adicionar proteção de ponto final no Windows 10 no Microsoft Intune – Azure | Microsoft Docs
description: Em dispositivos com o Windows 10, utilize ou configure definições de proteção de ponto final para ativar a funcionalidade Windows Defender, incluindo o Application Guard, Firewall, SmartScreen, encriptação e BitLocker, Exploit Guard, Controlo de Aplicações, Centro de Segurança e segurança em dispositivos locais no Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/25/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 3af7c91b-8292-4c7e-8d25-8834fcf3517a
ms.reviewer: ilwu
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: fdfe822c9633e22e611acfe7f915068a4a183ae2
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/20/2018
ms.locfileid: "52190001"
---
# <a name="endpoint-protection-settings-for-windows-10-and-later-in-intune"></a>Definições de proteção de ponto final para o Windows 10 (e versões posteriores) no Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

O perfil de proteção de ponto final permite-lhe controlar as funcionalidades de segurança em dispositivos com Windows 10, como o BitLocker e o Windows Defender.

Utilize as informações neste artigo para criar perfis de proteção de ponto final. Para configurar o Antivírus do Windows Defender, veja [Restrições de Dispositivos com o Windows 10](device-restrictions-windows-10.md#windows-defender-antivirus). 

## <a name="windows-defender-application-guard"></a>Windows Defender Application Guard

Suportado nas seguintes edições do Windows 10:

- Empresarial 
- Profissional

Ao utilizar o Microsoft Edge, o Windows Defender Application Guard protege o seu ambiente contra sites que a sua organização não considera como sendo de confiança. Quando os utilizadores visitam sites que não estão listados no seu limite de rede isolada, os sites são abertos numa sessão de navegação virtual no Hyper-V. Os sites fidedignos são definidos por um limite de rede, que pode ser configurado na Configuração do Dispositivo.

O Application Guard só está disponível para dispositivos com o Windows 10 (64 bits). Se utilizar este perfil, instalará um componente do Win32 para ativar o Application Guard.

- **Application Guard**: selecione **Ativar** para ativar esta funcionalidade, que abre sites não aprovados num contentor de navegação virtualizado do Hyper-V. A opção **Não configurado** (predefinição) significa que qualquer site (aprovado e não aprovado) é aberto no dispositivo.
- **Comportamento da área de transferência**: escolha que ações Copiar e Colar são permitidas entre o PC local e o browser virtual do Application Guard.
- **Conteúdos externos em sites de empresa**: selecione **Bloquear** para impedir que os conteúdos de sites não aprovados sejam carregados. A opção **Não configurado** (predefinição) significa que podem ser abertos sites não empresariais no dispositivo.
- **Imprimir a partir do browser virtual**: selecione **Permitir** para permitir que impressoras de rede, locais, XPS e/ou PDF imprimam conteúdos a partir do browser virtual. A opção **Não configurado** (predefinição) desativa todas as funcionalidades de impressão.
- **Recolher registos**: selecione **Permitir** para recolher registos para eventos que ocorrem numa sessão de navegação do Application Guard. A opção **Não configurado** (predefinição) não recolhe registos na sessão de navegação.
- **Reter dados do browser gerados pelo utilizador**: selecione **Permitir** para guardar os dados do utilizador (por exemplo, palavras-passe, favoritos e cookies) que são criados durante uma sessão de navegação virtual do Application Guard. A opção **Não configurado** (predefinição) elimina os dados e ficheiros transferidos pelos utilizadores quando o dispositivo é reiniciado ou quando um utilizador termina a sessão.
- **Aceleração de gráficos**: selecione **Ativar** para carregar sites e vídeos que utilizem mais gráficos mais rapidamente ao obter acesso a uma unidade de processamento gráfico virtual. A opção **Não configurado** (predefinição) utiliza o CPU do dispositivo para gráficos; não utiliza a unidade de processamento gráfico virtual.
- **Transferir ficheiros para o sistema de ficheiros anfitrião**: selecione **Ativar** para que os utilizadores possam transferir ficheiros do browser virtualizado para o sistema operativo anfitrião. A opção **Não configurado** (predefinição) mantém os ficheiros no dispositivo e não transfere ficheiros para o sistema de ficheiros anfitrião.

## <a name="windows-defender-firewall"></a>Firewall do Windows Defender

Suportado nas seguintes edições do Windows 10:
- Casa
- Profissional
- Empresa
- Empresarial
- Educação
- Mobile
- Mobile Enterprise

### <a name="global-settings"></a>Definições globais

Estas definições são aplicáveis a todos os tipos de rede.

- **Protocolo FTP (File Transfer Protocol)**: selecione **Bloquear** para desativar o FTP com monitorização de estado. Com a opção **Não configurado** (predefinição), a firewall filtra o FTP com monitorização de estado para permitir ligações secundárias.
- **Tempo de inatividade de associação de segurança antes da eliminação**: as associações de segurança são eliminadas quando o tráfego de rede não é detetado durante *n* segundos. Introduza um tempo inativo em segundos.
- **Codificação de chave pré-partilhada**: selecione **Ativar** para utilizar codificação de chave pré-partilhada através de UTF-8. A opção **Não configurado** (predefinição) utiliza o valor do arquivo no local.
- **Exceções de IPsec**: configure a exclusão de tráfego específico do IPsec, incluindo:
  - **Descoberta de vizinho de códigos do tipo IPv6 ICMP**
  - **ICMP**
  - **Descoberta de router de códigos do tipo IPv6 ICMP**
  - **Tráfego de rede de IPv4 e IPv6 DHCP**
- **Verificação da lista de revogação de certificados**: determine a forma como a verificação da lista de revogação de certificados é imposta, incluindo **Desativar a verificação de CRL**, **Falhar a verificação de CRL apenas no certificado revogado** e **Falhar a verificação de CRL em qualquer erro encontrado**.
- **Fazer corresponder oportunisticamente ao conjunto de autenticação por módulo de keying**: selecione **Ativar** para que os módulos de keying TENHAM de ignorar apenas os conjuntos de autenticação que não forem suportados. Com a opção **Não configurado**, os módulos de keying TÊM de ignorar todo o conjunto de autenticação se não suportarem todos os conjuntos de autenticação especificados no conjunto.
- **Pacotes de colocação**: especifique como o dimensionamento do software do lado de receção é ativado para a receção encriptada e o reencaminhamento de texto não encriptado para o cenário de gateway de túnel IPsec. Esta definição garante que o pedido de pacote é preservado.

### <a name="network-settings"></a>Definições de rede

Estas definições são aplicáveis a tipos de rede específicos, incluindo **Rede de domínio (área de trabalho)**, **Rede privada (detetável)** e **Rede pública (não detetável)**.

#### <a name="general-settings"></a>Definições gerais

- **Firewall do Windows Defender**: selecione **Ativar** para ativar a firewall e segurança avançada. A opção **Não configurado** (predefinição) permite todo o tráfego de rede, independentemente de outras definições de políticas.
- **Modo furtivo**: selecione **Bloquear** para impedir a firewall de funcionar no modo furtivo. Esta definição também lhe permite bloquear a **Exceção de pacotes seguros com IPsec**. A opção **Não configurado** (predefinição) opera a firewall em modo furtivo, o que ajuda a impedir respostas a pedidos de pesquisa.
- **Blindada**: selecione **Bloquear** para desativar esta funcionalidade. A opção **Não configurado** (predefinição) ativa esta definição. Quando esta definição e a Firewall do Windows Defender estão ativadas, todo o tráfego recebido é bloqueado, independentemente de outras definições de políticas.
- **Respostas unicast às difusões multicast**: quando definida para **Bloquear**, as respostas unicast às difusões multicast são desativadas. Normalmente, não quer receber respostas unicast para mensagens multicast ou de difusão. Essas respostas podem indicar um ataque denial of service (DOS) ou um atacante a tentar sondar um computador conhecido. A opção **Não configurado** (predefinição) ativa esta definição.
- **Notificações de receção**: quando definida para **Bloquear**, oculta as notificações aos utilizadores quando uma aplicação é impedida de escutar numa porta. A opção **Não configurado** (predefinição) ativa esta definição e poderá mostrar uma notificação aos utilizadores quando uma aplicação é impedida de escutar numa porta.
- **Ação predefinida para ligações de receção**: quando definida para **Bloquear** a ação predefinida da firewall é não ser executada em ligações de receção. Quando definida para **Não configurado** (predefinição), a ação predefinida da firewall é executada em ligações de receção.

#### <a name="rule-merging"></a>Intercalação de regras

- **Regras de Firewall do Windows Defender de aplicação autorizada do arquivo local**: selecione **Ativar** para aplicar regras de firewall no arquivo local para serem reconhecidas e executadas. Quando definida para **Não configurado** (predefinição), as regras de firewall da aplicação autorizadas no arquivo local são ignoradas e não são impostas.
- **Regras de Firewall do Windows Defender de portas globais do arquivo local**: selecione **Ativar** para aplicar regras de firewall de portas globais no arquivo local para serem reconhecidas e executadas. Quando definida para **Não configurado** (predefinição), as regras de firewall da porta global no arquivo local são ignoradas e não são impostas.
- **Regras de Firewall do Windows Defender do arquivo local**: selecione **Ativar** para aplicar regras de firewall globais no arquivo local para serem reconhecidas e executadas. Quando definida para **Não configurado** (predefinição), as regras de firewall do arquivo local são ignoradas e não são impostas.
- **Regras de IPsec do arquivo local**: selecione **Ativar** para aplicar regras de segurança de ligação do arquivo local, independentemente do esquema ou das versões de regras de segurança da ligação. Quando definida para **Não configurado** (predefinição), as regras de segurança de ligação do arquivo local são ignoradas e não são impostas, independentemente da versão do esquema e versão da regra de segurança da ligação.

## <a name="windows-defender-smartscreen-settings"></a>Definições do Windows Defender SmartScreen

Suportado nas seguintes edições do Windows 10 com o Microsoft Edge instalado:
- Casa
- Profissional
- Empresa
- Empresarial
- Educação
- Mobile
- Mobile Enterprise

**Definições**:

- **SmartScreen para aplicações e ficheiros**: selecione **Ativar** o Windows SmartScreen para a execução de ficheiros e aplicações em execução. O SmartScreen é um componente anti-phishing e anti-malware baseado na cloud. A opção **Não configurado** (predefinição) desativa o SmartScreen.
- **Execução de ficheiros não verificados**: selecione **Bloquear** para não permitir que os utilizadores finais executem ficheiros que não foram verificados pelo Windows SmartScreen. A opção **Não configurado** (predefinição) desativa esta funcionalidade e permite que os utilizadores finais executem ficheiros não verificados.

## <a name="windows-encryption"></a>Encriptação do Windows

### <a name="windows-settings"></a>Definições do Windows

Suportado nas seguintes edições do Windows 10:

- Profissional
- Empresa
- Empresarial
- Educação
- Mobile
- Mobile Enterprise

**Definições**:

- **Encriptar dispositivos**: selecione **Exigir** para pedir aos utilizadores que ativem a encriptação de dispositivos. Consoante a edição do Windows e configuração do sistema, poderá ser pedido aos utilizadores:  
  - Que confirmem que a encriptação de outro fornecedor não foi ativada
  - Que desativem a Encriptação de Unidade BitLocker e, em seguida, voltem a ativar o BitLocker
    
    Se a encriptação do Windows for ativada enquanto outro método de encriptação estiver ativo, o dispositivo pode tornar-se instável. 
- **Encriptar cartão de memória (apenas móvel)**: selecione **Exigir** para encriptar todos os cartões de armazenamento amovíveis utilizados pelo dispositivo. A opção **Não configurado** (predefinição) não necessita da encriptação dos cartões de armazenamento e não pede ao utilizador para a ativar. Esta definição só se aplica a dispositivos com o Windows 10 Mobile.

### <a name="bitlocker-base-settings"></a>Definições base do BitLocker

Suportado nas seguintes edições do Windows 10:

- Empresarial
- Educação
- Mobile
- Mobile Enterprise

As definições base são definições de BitLocker universais para todos os tipos de unidades de dados. Estas definições gerem as tarefas de encriptação ou opções de configuração de unidades que o utilizador final pode modificar para todos os tipos de unidades de dados.

- **Aviso para a encriptação de outro disco**: selecione **Bloquear** para desativar a mensagem de aviso se outro serviço de encriptação de disco estiver presente no dispositivo. A opção **Não configurado** (predefinição) permite que o aviso seja apresentado.
- **Configurar métodos de encriptação**: selecione **Ativar** para configurar algoritmos de encriptação do sistema operativo, dos dados e das unidades amovíveis. Quando definida para **Não configurado** (predefinição), o BitLocker utiliza o algoritmo XTS-AES de 128 bits como o método de encriptação predefinido ou utiliza o método de encriptação especificado por qualquer script de configuração.
  - **Encriptação de unidades de sistema operativo**: selecione o método de encriptação das unidades de sistema operativo. Recomendamos que utilize o algoritmo XTS-AES.
  - **Encriptação de unidades de dados fixas**: escolha o método de encriptação das unidades de dados fixas (incorporadas). Recomendamos que utilize o algoritmo XTS-AES.
  - **Encriptação de unidades de dados amovíveis**: selecione o método de encriptação das unidades de dados amovíveis. Se a unidade amovível for utilizada com dispositivos que não executam o Windows 10, recomendamos que utilize o algoritmo AES-CBC.

### <a name="bitlocker-os-drive-settings"></a>Definições de unidades de SO do BitLocker
Suportado nas seguintes edições do Windows 10:

- Empresarial
- Educação
- Mobile
- Mobile Enterprise

Estas definições aplicam-se especificamente a unidades de dados do sistema operativo.

- **Autenticação adicional no arranque**: selecione **Exigir** para configurar os requisitos de autenticação do arranque do computador, incluindo a utilização do Trusted Platform Module (TPM). Selecione **Não configurado** (predefinição) para configurar apenas opções básicas em dispositivos com um TPM.
  - **BitLocker com chip do TPM não compatível**: selecione **Bloquear** (desativar) com o BitLocker quando um dispositivo não tiver um chip TPM compatível. Quando definida para **Não configurado**, os utilizadores podem usar o BitLocker sem um chip TPM compatível. O BitLocker poderá precisar de uma palavra-passe ou de uma chave de arranque.
  - **Arranque do TPM compatível**: escolha permitir, não permitir ou exigir o chip do TPM.
  - **PIN de arranque do TPM compatível**: escolha permitir, não permitir ou exigir um PIN de arranque com o chip do TPM. Para ativar um PIN de arranque, é necessária interação por parte do utilizador final. 
  - **Chave de arranque do TPM compatível**: escolha permitir, não permitir ou exigir uma chave de arranque com o chip do TPM. Para ativar uma chave de arranque, é necessária interação por parte do utilizador final. 
  - **PIN e chave de arranque do TPM compatível**: escolha permitir, não permitir ou exigir um PIN e uma chave de arranque com o chip do TPM. Para ativar uma chave e PIN de arranque, é necessária interação por parte do utilizador final.
- **Comprimento Mínimo do PIN** : selecione **Ativar** para configurar um comprimento mínimo para o PIN de arranque do TPM. Quando definida para **Não configurado** (predefinição), os utilizadores podem configurar um PIN de arranque entre 6 e 20 dígitos.
  - **Carateres mínimos**: introduza o número de carateres necessários para o PIN de arranque de **4**-**20**.
- **Recuperação da unidade de SO**: selecione **Ativar** para controlar a forma como as unidades de sistema operativo protegidas pelo BitLocker são recuperadas quando as informações de arranque necessárias não estão disponíveis. Quando definida para **Não configurado** (predefinição), as operações de recuperação predefinidas são suportadas pela recuperação do BitLocker. Por predefinição, um DRA é permitido, as opções de recuperação são especificadas pelo utilizador, incluindo a palavra-passe e chave de recuperação e não é criada uma cópia de segurança das informações de recuperação no Active Directory Domain Services.
  - **Agente de recuperação de dados baseada em certificados**: quando definida para **Bloquear**, não pode utilizar um agente de recuperação de dados com unidades de SO protegidas pelo BitLocker. Defina esta opção para **Não configurado** (predefinição) para ativar esta definição para permitir que os agentes de recuperação de dados possam ser utilizados com as unidades de sistema operativo protegidas pelo BitLocker.
  - **Criação de palavra-passe de recuperação pelo utilizador**: escolha se é permitido, não permitido ou exigido aos utilizadores gerarem uma palavra-passe de recuperação de 48 dígitos.
  - **Criação de chave de recuperação pelo utilizador**: escolha se é permitido, não permitido ou exigido aos utilizadores gerarem uma chave de recuperação de 256 bits.
  - **Opções de recuperação no assistente de configuração do BitLocker**: defina para **Bloquear** para que os utilizadores não possam ver e alterar as opções de recuperação. Quando definida para **Não configurado** (predefinição), os utilizadores podem ver e alterar as opções de recuperação ao ativarem o BitLocker.
  - **Guardar as informações de recuperação do BitLocker no Active Directory Domain Services**: selecione **Ativar** para armazenar as informações de recuperação do BitLocker no Azure Active Directory (AAD). Quando definida para **Não configurado** (predefinição), as informações de recuperação não são armazenadas no Azure Active Directory.
  - **Informações de recuperação do BitLocker armazenadas no Active Directory Domain Services**: configure que partes das informações de recuperação do BitLocker são armazenadas no Azure Active Directory. Escolha entre:
    - **Palavras-passe de recuperação de cópia de segurança e pacotes de chaves**
    - **Apenas palavras-passe de recuperação de cópia de segurança**
  - **Armazenar informações de recuperação no Active Directory Domain Services antes de ativar o BitLocker**: selecione **Exigir** para impedir os utilizadores de ativarem o BitLocker, a menos que as informações de recuperação do BitLocker estejam armazenadas com êxito no Azure Active Directory. A opção **Não configurado** (predefinição) permite aos utilizadores ativar o BitLocker, mesmo que as informações de recuperação não estejam armazenadas com êxito no Azure Active Directory.
- **Mensagem de recuperação de pré-arranque e o URL**: selecione **Ativar** para configurar a mensagem e o URL que são apresentados no ecrã de pré-arranque de recuperação da chave. A opção **Não configurado** (predefinição) desativa esta funcionalidade.
  - **Mensagem de recuperação de pré-arranque**: configure de que forma é que a mensagem de recuperação de pré-arranque é apresentada aos utilizadores. Escolha entre:
    - **Utilizar mensagem de recuperação predefinida e URL**
    - **Utilizar mensagem de recuperação vazia e URL**
    - **Utilizar mensagem de recuperação personalizada**
    - **Utilizador URL de recuperação personalizada**

### <a name="bitlocker-fixed-data-drive-settings"></a>Definições de unidades de dados fixas do BitLocker

Suportado nas seguintes edições do Windows 10:

- Empresarial
- Educação
- Mobile
- Mobile Enterprise

**Definições**:

- **Acesso de escrita para unidades de dados fixos não protegidas pelo BitLocker**: defina para **Bloquear** para atribuir acesso só de escrita a unidades de dados não protegidas pelo BitLocker. Quando definida para **Não configurado** (predefinição), existe acesso de leitura e escrita a unidades de dados não protegidas pelo BitLocker.
- **Recuperação de unidade fixa**: selecione **Ativar** para controlar a forma como as unidades fixas protegidas pelo BitLocker são recuperadas quando as informações de arranque necessárias não estão disponíveis. A opção **Não configurado** (predefinição) desativa esta funcionalidade.
  - **Agente de recuperação de dados**: defina para **Bloquear** para impedir que o agente de recuperação de dados seja utilizado com o Editor de Políticas das unidades fixas protegidas pelo BitLocker. A opção **Não configurado** (predefinição) permite a utilização de agentes de recuperação de dados com unidades fixas protegidas pelo BitLocker.
  - **Criação de palavra-passe de recuperação pelo utilizador**: configure se é permitido, não permitido ou exigido aos utilizadores gerarem uma palavra-passe de recuperação de 48 dígitos.  
  - **Criação da chave de recuperação pelo utilizador**: configure se é permitido, não permitido ou exigido aos utilizadores gerarem uma chave de recuperação de 256 bits.
  - **Opções de recuperação no assistente de configuração do BitLocker**: defina para **Bloquear** para que os utilizadores não possam ver e alterar as opções de recuperação. Quando definida para **Não configurado** (predefinição), os utilizadores podem ver e alterar as opções de recuperação ao ativarem o BitLocker.
  - **Guardar as informações de recuperação do BitLocker no Active Directory Domain Services**: selecione **Ativar** para armazenar as informações de recuperação do BitLocker no Azure Active Directory (AAD). Quando definida para **Não configurado** (predefinição), as informações de recuperação não são armazenadas no Azure Active Directory.
  - **Informações de recuperação do BitLocker no Active Directory Domain Services**: configure que partes das informações de recuperação do BitLocker são armazenadas no Microsoft Azure Active Directory. Escolha entre:
    - **Palavras-passe de recuperação de cópia de segurança e pacotes de chaves**
    - **Apenas palavras-passe de recuperação de cópia de segurança**
  - **Armazenar informações de recuperação no Active Directory Domain Services antes de ativar o BitLocker**: selecione **Exigir** para impedir os utilizadores de ativarem o BitLocker, a menos que as informações de recuperação do BitLocker estejam armazenadas com êxito no Azure Active Directory. A opção **Não configurado** (predefinição) permite aos utilizadores ativar o BitLocker, mesmo que as informações de recuperação não estejam armazenadas com êxito no Azure Active Directory.

### <a name="bitlocker-removable-data-drive-settings"></a>Definições de unidades de dados removíveis do BitLocker

Suportado nas seguintes edições do Windows 10:

- Empresarial
- Educação
- Mobile
- Mobile Enterprise

**Definições**:

- **Acesso de escrita para a unidade de dados removível não protegida pelo BitLocker**: defina para **Bloquear** para atribuir acesso só de escrita a unidades de dados não protegidas pelo BitLocker. Quando definida para **Não configurado** (predefinição), existe acesso de leitura e escrita a unidades de dados não protegidas pelo BitLocker.
  - **Acesso de escrita para dispositivos configurados noutra organização**: definir para **Bloquear** permite o acesso de escrita para dispositivos configurados noutra organização. **Não configurado** (predefinição) impede o acesso de escrita.

## <a name="windows-defender-exploit-guard"></a>Windows Defender Exploit Guard

Suportado nas seguintes edições do Windows 10:

- Casa
- Profissional
- Empresa
- Empresarial
- Educação
- Mobile
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

- **Ficheiros e pastas a excluir das regras de redução de superfície de ataque**: importe/adicione uma lista de localizações a excluir das regras configuradas.

### <a name="controlled-folder-access"></a>Acesso a pastas controladas

Ajude a proteger dados valiosos de ameaças e aplicações malignas, tal como ransomware.

- **Proteção de pastas**: proteja ficheiros e pastas de alterações indesejadas por parte de aplicações malignas. Pode importar uma **Lista de aplicações que têm acesso a pastas protegidas** ou adicioná-las manualmente. Também pode adicionar uma **Lista de pastas adicionais que necessitam ser protegidas** com um carregamento ou adicioná-las manualmente.

### <a name="network-filtering"></a>Filtragem de rede

Bloqueie ligações de saída de qualquer aplicação para endereços IP/domínios com baixa reputação.

### <a name="exploit-protection"></a>Exploit Protection

Para ativar o Exploit Protection, crie um ficheiro XML que inclua as definições de mitigação de sistema e aplicação que pretende. Existem dois métodos:

 1. PowerShell: utilize um ou mais dos cmdlets Get-ProcessMitigation, Set-ProcessMitigation e ConvertTo-ProcessMitigationPolicy do PowerShell. Os cmdlets configuram definições de mitigação e exportam uma representação XML deles.

 2. IU do Centro de Segurança do Windows Defender: no Centro de Segurança do Windows Defender, clique no controlo de browser e na aplicação e, em seguida, desloque-se para a parte inferior do ecrã resultante para localizar o Exploit Protection. Em primeiro lugar, utilize as definições do sistema e os separadores das definições de programa para configurar definições de atenuação. Em seguida, localize a ligação de definições de Exportação na parte inferior do ecrã para exportar uma representação XML dos mesmos.

Bloqueie a **Edição da interface do Exploit Protection por parte dos utilizadores** ao carregar um ficheiro XML que lhe permite configurar a memória, controlar o fluxo e as restrições de políticas. As definições no ficheiro XML podem servir para proteger uma aplicação de exploits. A opção **Não configurado** (predefinição) não aplica uma configuração personalizada. 

## <a name="windows-defender-application-control"></a>Controlo de Aplicações do Windows Defender

Suportado nas seguintes edições do Windows 10:

**Gestão de Dispositivos Móveis (MDM)**: 
- Profissional
- Empresa
- Empresarial
- Educação
- Mobile
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

- **Desativar**: desativa o Credential Guard remotamente se este tiver sido ativado antes através da opção **Ativar sem bloqueio UEFI**.

- **Ativar com bloqueio UEFI** : o Credential Guard não pode ser desativado remotamente com uma chave de registo ou através da utilização de uma política de grupo.

    > [!NOTE]
    > Se utilizar esta definição e, em seguida, quiser desativar o Credential Guard, terá de definir a Política de Grupo como **Desativado**. Além disso, tem de limpar fisicamente as informações de configuração de UEFI de cada computador. Enquanto a configuração da UEFI persistir, o Credential Guard estará ativado.

- **Ativar sem bloqueio UEFI**: permite que o Credential Guard seja desativado remotamente através da utilização da Política de Grupo. Os dispositivos que utilizam esta definição têm de ter a versão 1511 ou mais recente do Windows 10.

Quando ativar o Credential Guard, as seguintes funcionalidades necessárias também são ativadas:

- **Segurança baseada em Virtualização** (VBS): é ativada durante o próximo reinício. A segurança baseada em Virtualização utiliza o Windows Hypervisor para dar suporte aos serviços de segurança e requer o Windows Hypervisor.
- **Reinício Seguro com o Acesso Direto à Memória**: ativa a VBS com o Arranque Seguro e as proteções do acesso direto à memória (DMA). As proteções de DMA necessitam de suporte de hardware e são ativadas apenas em dispositivos configurados corretamente.

## <a name="windows-defender-security-center"></a>Centro de Segurança do Windows Defender

Suportado nas seguintes edições do Windows 10:

- Casa
- Profissional
- Empresa
- Empresarial
- Educação
- Mobile
- Mobile Enterprise

O Centro de Segurança do Windows Defender funciona como uma aplicação ou processo separado de cada uma das funcionalidades individuais. Apresenta notificações através do Centro de Ação. Atua como um recoletor ou único local para ver o estado e realizar configurações para cada uma das funcionalidades. Saiba mais na documentação do [Windows Defender](https://docs.microsoft.com/windows/threat-protection/windows-defender-security-center/windows-defender-security-center).

#### <a name="windows-defender-security-center-app-and-notifications"></a>Aplicações e notificações do Centro de Segurança do Windows Defender

Bloqueie o acesso de utilizadores finais a várias áreas da aplicação Centro de Segurança do Windows Defender. Ocultar uma secção também bloqueia notificações relacionadas.

- **Proteção contra vírus e ameaças**
- **Desempenho e estado de funcionamento do dispositivo**
- **Firewall e proteção da rede**
- **Controlo de aplicações e browsers**
- **Opções de família**
- **Notificações das áreas apresentadas da aplicação**: escolha quais as notificações a apresentar aos utilizadores finais. As notificações não críticas incluem resumos de atividade do Antivírus do Windows Defender, incluindo notificações quando as análises forem concluídas. Todas as outras notificações são consideradas críticas.

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

- **Adicionar novas contas Microsoft**: defina para **Bloquear** para impedir que os utilizadores adicionem novas contas Microsoft ao dispositivo. Quando definida para **Não configurado** (predefinição), os utilizadores podem utilizar contas Microsoft no dispositivo.
- **Início de sessão remoto sem palavra-passe**: selecione **Ativar** para permitir que as contas locais com palavras-passe vazias iniciem sessão com o teclado do dispositivo. A opção **Não configurado** (predefinição) permite que as contas locais com palavras-passe vazias iniciem sessão em localizações que não o dispositivo físico.

#### <a name="admin"></a>Administração

- **Conta de administrador local**: defina para **Ativado** para permitir a conta de administrador local. Defina para **Não configurado** (predefinição) para desativar a conta de administrador local.
- **Mudar o nome da conta de administrador**: defina um nome de conta diferente para ser associado ao identificador de segurança (SID) da Conta de administrador.

#### <a name="guest"></a>Convidado

- **Conta de convidado**: defina para **Ativado** para permitir a conta de convidado local. Defina para **Não configurado** (predefinição) para desativar a conta de convidado local.
- **Mudar o nome da conta de convidado**: defina um nome de conta diferente para ser associado ao identificador de segurança (SID) da Conta de convidado.

### <a name="devices"></a>Dispositivos

- **Desancorar dispositivo sem início de sessão**: defina para **Bloquear** para que os utilizadores possam premir o botão de ejeção físico de um dispositivo portátil ancorado para desancorar o dispositivo com segurança. A opção **Não configurado** (predefinição) exige que o utilizador inicie sessão no dispositivo e receba permissão para o desancorar.
- **Instalar controladores de impressora para impressoras partilhadas**: quando definida como **Ativado** qualquer utilizador pode instalar um controlador de impressora como parte da ligação a uma impressora partilhada. Quando definida para **Não configurado** (predefinição), apenas os Administradores podem instalar um controlador de impressora como parte da ligação a uma impressora partilhada.
- **Restringir o acesso de CD-ROM ao utilizador ativo local**: quando definida como **Ativado**, apenas o utilizador com sessão iniciada de forma interativa pode utilizar o suporte de dados CD-ROM. Se esta política estiver ativada e ninguém tiver sessão iniciada de forma interativa, a unidade de CD-ROM será acedida através da rede. Quando definida para **Não configurado** (predefinição), qualquer pessoa têm acesso à unidade de CD-ROM.
- **Formatar e ejetar o suporte de dados amovível**: defina quem tem permissão para formatar e ejetar o suporte de dados NTFS amovível:
  - **Não configurado**
  - **Administradores**
  - **Administradores e Utilizadores Avançados**
  - **Administradores e Utilizadores Interativos**

### <a name="interactive-logon"></a>Início de sessão interativo

- **Minutos de inatividade do ecrã bloqueado até que a proteção de ecrã seja ativada**: introduza o máximo de minutos de inatividade no ecrã de início de sessão do ambiente de trabalho interativo até que a proteção de ecrã seja executada.
- **Exigir Ctrl+Alt+Delete para iniciar sessão**: defina para **Ativar** para que os utilizadores não tenham de premir Ctrl+Alt+Delete para iniciarem sessão. Defina para **Não configurado** (predefinição) para que os utilizadores tenham de premir Ctrl+Alt+Delete para iniciarem sessão no Windows.
- **Comportamento de remoção do smart card**: determina o que acontece quando o smart card de um utilizador com sessão iniciada é removido do leitor de Smart Card. As opções são:

  - **Bloquear Estação de Trabalho**: a estação de trabalho é bloqueada quando o smart card é removido. Esta opção permite que os utilizadores saiam da área, levem os seus smart cards e permaneçam numa sessão protegida.
  - **Forçar Fim da Sessão**: a sessão do utilizador é terminada automaticamente quando o smart card é removido.
  - **Desligar se existir uma sessão dos Serviços de Ambiente de Trabalho Remoto**: a remoção do smart card desliga a sessão sem terminar a sessão do utilizador. Esta opção permite que o utilizador insira o smart card e retome a sessão mais tarde, ou noutro computador com um leitor de smart cards, sem ter de iniciar sessão novamente. Se a sessão for local, esta política funciona da mesma forma que Bloquear Estação de Trabalho.

    As [opções LocalPoliciesSecurity](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-localpoliciessecurityoptions#localpoliciessecurityoptions-interactivelogon-smartcardremovalbehavior) proporcionam mais detalhes.

#### <a name="display"></a>Apresentar

- **Informações do utilizador no ecrã de bloqueio**: configure as informações de utilizador que são apresentadas quando a sessão está bloqueada. Se não estiverem configuradas, serão apresentados o nome a apresentar do utilizador, o domínio e o nome de utilizador.
  - **Não configurado**
  - **O nome a apresentar do utilizador, o domínio e o nome de utilizador**
  - **Apenas o nome a apresentar do utilizador**
  - **Não apresentar informações do utilizador**
- **Ocultar último utilizador com sessão iniciada**: selecionar **Ativar** oculta o nome de utilizador. A opção **Não configurado** (predefinição) mostra o nome de utilizador.
- **Ocultar nome de utilizador no início de sessão**: selecionar **Ativar** oculta o nome de utilizador. A opção **Não configurado** (predefinição) mostra o nome de utilizador.
- **Título de mensagem de início de sessão**: defina o título da mensagem para os utilizadores que iniciam sessão.
- **Texto de mensagem de início de sessão**: defina o texto da mensagem para os utilizadores que iniciam sessão.

### <a name="network-access-and-security"></a>Acesso à rede e segurança

- **Acesso anónimo a Pipes Nomeados e Partilhas**: **Não configurado** (predefinição) restringe o acesso anónimo às definições Pipe Nomeado e Partilha. Aplica-se as definições que podem ser acedidas anonimamente.
- **Enumeração anónima de contas SAM**: **permite** que os utilizadores anónimos enumerem as contas SAM. O Windows permite que os utilizadores anónimos enumerem os nomes das contas de domínio e das partilhas de rede.
- **Enumeração anónima de contas e partilhas SAM**: **Não configurado** (predefinição) significa que os utilizadores anónimos podem enumerar os nomes de contas de domínio e partilhas de rede. Para impedir a enumeração anónima de contas e partilhas SAM, defina como **Bloquear**.
- **Valor hash do Gestor de LAN armazenado aquando da alteração da palavra-passe**: na próxima alteração de palavra-passe, opte por **Permitir** que o Gestor de LAN (LM) armazene o valor hash da nova palavra-passe. Quando definida para **Não configurado** (predefinição), o valor hash não é armazenado.
- **Pedidos de autenticação PKU2U**: **bloquear** pedidos de autenticação PKU2U ao dispositivo para utilizar identidades online. **Não configurado** (predefinição) permite estes pedidos.
- **Restringir ligações remotas de RPC a SAM**: **permitir** que a cadeia de Linguagem de Definição de Descritor de Segurança predefinida negue a utilizadores e a grupos a realização de chamadas remotas para SAM. **Não configurado** (predefinição): a cadeia de Linguagem de Definição de Descritor de Segurança predefinida permite que os utilizadores e grupos realizem chamadas remotas para SAM.
  - **Descritor de segurança**

### <a name="recovery-console-and-shutdown"></a>Consola de recuperação e encerramento

- **Limpar ficheiro de paginação de memória virtual ao encerrar**: defina para **Ativar** para limpar o ficheiro de paginação de memória virtual quando o dispositivo for desligado. A opção **Não configurado** (predefinição) não limpa a memória virtual.
- **Encerrar sem início de sessão**: selecionar **Bloquear** oculta a opção de encerramento no ecrã de início de sessão do Windows. Os utilizadores têm de iniciar sessão no dispositivo e, em seguida, encerrar. A opção **Não configurado** (predefinição) permite aos utilizadores encerrar o dispositivo a partir do ecrã de início de sessão do Windows.

### <a name="user-account-control"></a>Controlo de conta de utilizador

- **Integridade de UIA sem localização segura**: quando definida para **Ativar**, as aplicações em localizações seguras no sistema de ficheiros são executadas apenas com o nível de integridade UIAccess. A opção **Não configurado** (predefinição) permite que as aplicações sejam executadas com o nível de integridade UIAccess, mesmo que não estejam numa localização segura no sistema de ficheiros.
- **Virtualizar falhas de escrita em ficheiros e registos a localizações por utilizador**: quando definida para **Bloquear**, as falhas de escrita de aplicações são redirecionadas na execução para localizações de utilizadores definidas para o sistema de ficheiros e registo. Quando definida para **Não configurado** (predefinição), as aplicações que escrevem dados para localizações protegidas falham.
- **Elevar apenas ficheiros executáveis assinados e validados**: defina para **Ativado** para impor a validação do caminho da certificação PKI de um ficheiro executável antes de o mesmo ser executado. Defina para **Não configurado** (predefinição) para não impor a validação do caminho da certificação PKI antes da execução de um ficheiro executável.

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
- **Encaminhar pedidos de elevação para o ambiente de trabalho interativo do utilizador**: selecione **Ativar** para que todos os pedidos de elevação sejam encaminhados para o ambiente de trabalho do utilizador interativo em vez do ambiente de trabalho seguro. São utilizadas todas as definições de política de comportamento de pedidos para administradores e utilizadores padrão. A opção **Não configurado** (predefinição) obriga que todos os pedidos de elevação sejam encaminhados para o ambiente de trabalho seguro, independentemente das definições de política de comportamento de pedidos para administradores e utilizadores padrão.
- **Pedido elevado para instalações de aplicações**: quando definida para **Bloquear**, os pacotes de instalação de aplicações não são detetados nem é efetuado um pedido de elevação. Quando definida para **Não configurado** (predefinição), é pedido um nome de utilizador e palavra-passe administrativos ao utilizador quando um pacote de instalação de aplicações exige privilégios elevados.
- **Pedido de elevação UIA sem ambiente de trabalho seguro**: selecione **Ativar** para permitir que as aplicações UIAccess façam pedidos de elevação sem utilizar o ambiente de trabalho seguro. Quando definida para **Não configurado** (predefinição), os pedidos de elevação utilizam um ambiente de trabalho seguro.

#### <a name="admin-approval-mode-settings"></a>Definições do Modo de Aprovação de Administrador

- **Modo de Aprovação de Administrador para Administrador Incorporado**: selecionar **Ativar** permite a utilização do Modo de Aprovação de Administrador por parte da conta do Administrador. Qualquer operação que necessite de elevação de privilégios pede ao utilizador para aprovar a operação. A opção **Não configurado** (predefinição) executa todas as aplicações com privilégios de administrador totais.
- **Executar todos os administradores no Modo de Aprovação de Administrador**: defina para **Bloquear** para desativar o Modo de Aprovação de Administrador e todas as definições de política UAC relacionadas. A opção **Não configurado** (predefinição) ativa o Modo de Aprovação de Administrador.

### <a name="microsoft-network-client"></a>Cliente de Rede da Microsoft

- **Assinar comunicações digitalmente (se o servidor concordar)**: determina se o cliente SMB negoceia a assinatura de pacotes SMB. Quando definida como **Não configurado** ou ativada (predefinição), o cliente de rede da Microsoft pede ao servidor para executar a assinatura de pacotes SMB após a configuração da sessão. Se a assinatura de pacotes estiver ativada no servidor, a assinatura de pacotes será negociada. Se estiver definida como **Desativado**, o cliente SMB nunca negociará a assinatura de pacotes SMB.
- **Enviar palavra-passe não encriptada para servidores SMB de terceiros**: quando definida como **Ativar**, o redirecionador do protocolo SMB (Server Message Block) pode enviar palavras-passe em texto simples para servidores SMB que não sejam da Microsoft e que não suportam a encriptação de palavras-passe durante a autenticação. Quando definida para **Não configurado** (predefinição), as palavras-passe são encriptadas.

### <a name="microsoft-network-server"></a>Servidor de Rede da Microsoft

- **Assinar digitalmente comunicações (se o cliente concordar)**: determina se o servidor SMB negoceia a assinatura de pacotes SMB com clientes que a peçam. Quando definida para **Ativar**, o servidor de rede da Microsoft negoceia a assinatura de pacotes SMB conforme pedido pelo cliente. Ou seja, se a assinatura de pacotes estiver ativada no cliente, a assinatura de pacotes será negociada. Quando **Não configurado** ou desativado (predefinição), o cliente SMB nunca negociará a assinatura de pacotes SMB.
- **Assinar digitalmente comunicações (sempre)**: determina se o componente do servidor SMB necessita da assinatura de pacotes. Quando definida para **Ativar**, o servidor de rede da Microsoft não comunica com um cliente de rede da Microsoft, a menos que o cliente aceite assinar pacotes SMB. Quando definida para **Não configurado** ou desativado (predefinição), a assinatura de pacotes SMB é negociada entre o cliente e o servidor.

## <a name="next-steps"></a>Passos Seguintes

Para atribuir este perfil a grupos, veja [Como atribuir perfis de dispositivo](device-profile-assign.md).
