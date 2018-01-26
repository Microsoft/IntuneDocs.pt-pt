---
title: "Definições de proteção de ponto final do Intune para o Windows 10"
titlesuffix: Azure portal
description: "Saiba que definições do Intune pode utilizar para controlar as definições de proteção de ponto final, como o BitLocker, em dispositivos com o Windows 10."
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 01/16/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3af7c91b-8292-4c7e-8d25-8834fcf3517a
ms.reviewer: ilwu
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8393699a06def8f01c9f70561bb1894bb7cba04e
ms.sourcegitcommit: 967a7c23b863123398c40b812e2eb02c921a0afe
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/18/2018
---
# <a name="endpoint-protection-settings-for-windows-10-and-later-in-microsoft-intune"></a>Definições de proteção de ponto final para o Windows 10 e versões posteriores no Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

O perfil de proteção de ponto final permite-lhe controlar as funcionalidades de segurança em dispositivos com o Windows 10, como o BitLocker e o Windows Defender.

Utilize as informações neste tópico para saber como criar perfis de proteção de ponto final.

> [!Note]
> Estas definições não são suportadas nas edições Home e Professional do Windows 10.

## <a name="create-an-endpoint-protection-profile"></a>Criar um perfil de proteção de ponto final

1. Inicie sessão no portal do Azure.
2. Escolha **Mais Serviços** > **Monitorização + Gestão** > **Intune**.
3. No painel **Intune**, escolha **Configuração do dispositivo**.
2. No painel **Configuração do Dispositivo**, escolha **Gerir** > **Perfis**.
3. No painel de perfis, selecione **Criar perfil**.
4. No painel **Criar perfil**, introduza um **Nome** e uma **Descrição** para o perfil de funcionalidades de dispositivos.
5. Na lista pendente **Plataforma**, selecione **Windows 10 e posterior**.
6. Na lista pendente **Tipo de perfil**, selecione **Proteção de ponto final**.
7. Configure as definições que pretende. Utilize os detalhes neste tópico para o ajudar a compreender o que faz cada definição. Quando terminar, escolha **OK**.
8. Regresse ao painel **Criar perfil** e selecione **Criar**.

O perfil é criado e apresentado no painel da lista de perfis.

## <a name="windows-defender-application-guard"></a>Windows Defender Application Guard

O Application Guard só está disponível para dispositivos com o Windows 10 (64 bits). Com este perfil irá instalar um componente do Win32 para ativar o Application Guard.

- **Application Guard** – abra sites não aprovados num contentor de navegação virtualizado Hyper-V.
- **Comportamento da área de transferência** – escolha que ações de copiar e colar são permitidas entre o PC local e o browser virtual do Application Guard.
- **Conteúdos externos em sites de empresa** – impeça que os conteúdos de sites não aprovados sejam carregados.
- **Imprimir a partir do browser virtual** – permita que impressoras de rede, locais, XPS e/ou PDF imprimam conteúdos a partir do browser virtual.
- **Recolher registos** – recolha registos de eventos que ocorrem numa sessão de navegação do Application Guard.
- **Reter dados do browser gerados pelo utilizador** – permita que os dados do utilizador (por exemplo palavras-passe, favoritos e cookies) que são criados durante uma sessão de navegação virtual do Application Guard sejam guardados.


## <a name="windows-defender-firewall"></a>Firewall do Windows Defender

### <a name="global-settings"></a>Definições globais

Estas definições são aplicáveis a todos os tipos de rede.

- **Protocolo FTP (File Transfer Protocol)** – bloqueie o FTP com monitorização de estado.
- **Tempo de inatividade de associação de segurança antes da eliminação** – as associações de segurança são eliminadas quando o tráfego de rede não é detetado durante *n* segundos.
- **Codificação de chave pré-partilhada** – codifique chaves pré-partilhadas com UTF-8.
- **Isenções de IPsec** – configure o tráfego específico para ser isento de IPsec, incluindo **Descoberta de vizinho de códigos do tipo IPv6 ICMP**, **ICMP**, **Descoberta de router de códigos do tipo IPv6 ICMP** e **Tráfego de rede de IPv4 e IPv6 DHCP**.
- **Verificação da lista de revogação de certificado** – defina um valor para a forma como a verificação da lista de revogação de certificado é imposta, incluindo **Desativar a verificação de CRL**, **Falhar a verificação de CRL apenas no certificado revogado** e **Falhar a verificação de CRL em qualquer erro encontrado**.
- **Fazer corresponder oportunisticamente ao conjunto de autenticação por módulo de keying** – defina módulos de keying para ignorar o conjunto de autenticação completo se não suportarem todos os pacotes de autenticação nesse conjunto.
- **Pacotes de colocação** – especifique como o dimensionamento para o software do lado de receção está ativado para a receção encriptada e o reencaminhamento de texto não encriptado para o cenário de gateway de túnel IPsec. Isto garante que o pedido de pacote é preservado.

### <a name="network-settings"></a>Definições de rede

Estas definições são aplicáveis a tipos de rede específicos, incluindo **Rede de domínio (área de trabalho)**, **Rede privada (detetável)** e **Rede pública (não detetável)**.

#### <a name="general-settings"></a>Definições gerais

- **Firewall do Windows Defender** – permita que esta definição bloqueie o tráfego de rede.
- **Modo furtivo** – impeça a Firewall de funcionar no modo furtivo. Esta definição também lhe permite bloquear a **isenção de pacote seguro IPsec em modo furtivo**.
- **Blindado** – ative esta definição e a definição de firewall irá bloquear todo o tráfego de entrada.
- **Respostas unicast às difusões multicast** – bloqueie respostas unicast às difusões multicast. Geralmente, não é aconselhável receber respostas unicast às mensagens ou difusões multicast, uma vez que essas respostas podem indicar um ataque denial of service ou um atacante a tentar sondar um computador conhecido.
- **Notificações de entrada** – impeça que as notificações sejam apresentadas aos utilizadores quando uma aplicação é impedida de escutar numa porta.
- **Ação predefinida para ligações de entrada** – bloqueie a ação predefinida que a firewall realiza em ligações de entrada.

#### <a name="rule-merging"></a>Intercalação de regras

- **Regras de Firewall do Windows Defender de aplicação autorizada do arquivo local** – aplique regras de firewall autorizadas no arquivo local a serem reconhecidas e executadas.
- **Regras de Firewall do Windows Defender de portas globais do arquivo local** – aplique regras de firewall de portas globais no arquivo local a serem reconhecidas e executadas.
- **Regras de Firewall do Windows Defender do arquivo local** – aplique regras de firewall globais no arquivo local a serem reconhecidas e executadas.
- **Regras de IPsec do arquivo local** – aplique regras de segurança de ligação do arquivo local, independentemente do esquema ou das versões de regras de segurança da ligação.

## <a name="windows-defender-smartscreen-settings"></a>Definições do Windows Defender SmartScreen

- **SmartScreen para aplicações e ficheiros** – ative o Windows SmartScreen para a execução de ficheiros e aplicações em execução.
- **Execução de ficheiros não verificados** – não permita que o utilizador final execute ficheiros que não foram verificados pelo Windows SmartScreen.

## <a name="windows-encryption"></a>Encriptação do Windows

### <a name="windows-settings"></a>Definições do Windows

Estas definições aplicam-se a todas as versões do Windows 10.

- **Encriptar dispositivos** – se ativada, é pedido aos utilizadores que ativem a encriptação de dispositivos. Adicionalmente, é-lhes pedido que confirmem que a encriptação de outro fornecedor não foi ativada. Se a encriptação do Windows for ativada enquanto outro método de encriptação estiver ativo, o dispositivo pode tornar-se instável.
- **Encriptar cartão de armazenamento** – ative esta definição para encriptar todos os cartões de armazenamento amovíveis utilizados pelo dispositivo.


### <a name="bitlocker-base-settings"></a>Definições base do BitLocker

As definições base são definições de BitLocker universais para todos os tipos de unidades de dados. As definições de Política de Grupo do BitLocker gerem as tarefas de encriptação ou opções de configuração de unidades que o utilizador final pode modificar para todos os tipos de unidades de dados.

- **Aviso para a encriptação de outro disco** – desative a mensagem de aviso para a encriptação de outro disco nos computadores dos utilizadores finais.
- **Configurar métodos de encriptação** – ative esta definição para configurar algoritmos de encriptação para o sistema operativo, dados e unidades amovíveis.
    - **Encriptação para unidades de sistema operativo** – selecione o método de encriptação para as unidades de sistema operativo. Recomendamos que utilize o algoritmo XTS-AES.
    - **Encriptação para unidades de dados fixas** – selecione o método de encriptação para unidades de dados fixas (incorporadas). Recomendamos que utilize o algoritmo XTS-AES.
    - **Encriptação para unidades de dados removíveis** – selecione o método de encriptação para unidades de dados amovíveis. Se a unidade amovível for utilizada com dispositivos que não executam o Windows 10, recomendamos que utilize o algoritmo AES-CBC.

### <a name="bitlocker-os-drive-settings"></a>Definições de unidades de SO do BitLocker

Estas definições aplicam-se especificamente a unidades de dados do sistema operativo.

- **Autenticação adicional no arranque** – configure os requisitos de autenticação do arranque do computador, incluindo a utilização do Trusted Platform Module (TPM).
    - **BitLocker com chip do TPM não compatível**
    - **Arranque do TPM compatível** – configure se o chip do TPM é permitido, não permitido ou exigido.
    - **PIN de arranque do TPM compatível** – configure se utilizar um PIN de arranque com o chip do TPM é permitido, não permitido ou exigido.
    - **Chave de arranque do TPM compatível** – configure se utilizar uma chave de arranque com o chip do TPM é permitido, não permitido ou exigido.
    - **Chave e PIN de arranque do TPM compatível** – configure se utilizar uma chave e PIN de arranque com o chip do TPM é permitido, não permitido ou exigido.
- **Comprimento Mínimo do PIN** – ative esta definição para configurar um comprimento mínimo para o PIN de arranque do TPM.
    - **Carateres mínimos** – introduza o número de carateres necessários para o PIN de arranque de **4**-**20**.
- **Recuperação da unidade de SO** – ative esta definição para controlar a forma como as unidades de sistema operativo protegidas pelo BitLocker são recuperadas quando as informações de arranque necessárias não estão disponíveis.
    - **Agente de recuperação de dados baseada em certificados** – ative esta definição se quiser que os agentes de recuperação de dados possam ser utilizados com as unidades de sistema operativo protegidas pelo BitLocker.
    - **Criação de palavra-passe de recuperação pelo utilizador** – configure se é permitido, não permitido ou exigido aos utilizadores gerarem uma palavra-passe de recuperação de 48 dígitos.
    - **Criação da chave de recuperação pelo utilizador** – configure se é permitido, não permitido ou exigido aos utilizadores gerarem uma chave de recuperação de 256 bits.
    - **Opções de recuperação no assistente de configuração do BitLocker** – ative esta definição para impedir que os utilizadores vejam ou alterem opções de recuperação quando ativam o BitLocker.
    - **Guardar as informações de recuperação do BitLocker no AD DS** – permite o armazenamento das informações de recuperação do BitLocker no Active Directory.
    - **Informações de recuperação do BitLocker armazenadas no AD DS** – configure que partes das informações de recuperação do BitLocker são armazenadas no Active Directory. Escolha entre:
        - **Palavras-passe de recuperação de cópia de segurança e pacotes de chaves**
        - **Apenas palavras-passe de recuperação de cópia de segurança**
    - **Armazenar as informações de recuperação no AD DS antes de ativar o BitLocker** – ative esta definição para impedir os utilizadores de ativarem o BitLocker, a menos que o dispositivo esteja associado a um domínio e as informações de recuperação do BitLocker estejam armazenadas com êxito no Active Directory.
- **Mensagem de recuperação de pré-arranque e o URL** – ative esta definição para configurar a mensagem e o URL que são apresentados no ecrã de pré-arranque de recuperação da chave.
    - **Mensagem de recuperação de pré-arranque** – configure de que forma é que a mensagem de recuperação de pré-arranque é apresentada aos utilizadores. Escolha entre:
        - **Utilizar mensagem de recuperação predefinida e URL**
        - **Utilizar mensagem de recuperação vazia e URL**
        - **Utilizar mensagem de recuperação personalizada**
        - **Utilizador URL de recuperação personalizada**


### <a name="bitlocker-fixed-data-drive-settings"></a>Definições de unidades de dados fixas do BitLocker

- **Acesso de escrita para unidade de dados fixa não protegida pelo BitLocker** – se ativada, a proteção do BitLocker tem de ser ativada em todas as unidades de dados incorporadas ou fixas para que seja possível escrever nas mesmas.
- **Recuperação de unidade fixa**– ative esta definição para controlar a forma como as unidades fixas protegidas pelo BitLocker são recuperadas quando as informações de arranque necessárias não estão disponíveis.
    - **Agente de recuperação de dados** – ative esta definição se quiser que os agentes de recuperação de dados sejam utilizados com as unidades fixas protegidas pelo BitLocker.
    - **Criação de palavra-passe de recuperação pelo utilizador** – configure se é permitido, não permitido ou exigido aos utilizadores gerarem uma palavra-passe de recuperação de 48 dígitos.  
    - **Criação da chave de recuperação pelo utilizador** – configure se é permitido, não permitido ou exigido aos utilizadores gerarem uma chave de recuperação de 256 bits.
    - **Opções de recuperação no assistente de configuração do BitLocker** – ative esta definição para impedir que os utilizadores vejam ou alterem opções de recuperação quando ativam o BitLocker.
    - **Guardar as informações de recuperação do BitLocker no AD DS** – permite o armazenamento das informações de recuperação do BitLocker no Active Directory.
    - **Informações de recuperação do BitLocker para o AD DS** – configure que partes das informações de recuperação do BitLocker são armazenadas no Active Directory. Escolha entre:
        - **Palavras-passe de recuperação de cópia de segurança e pacotes de chaves**
        - **Apenas palavras-passe de recuperação de cópia de segurança**
    - **Armazenar as informações de recuperação no AD DS antes de ativar o BitLocker** – ative esta definição para impedir os utilizadores de ativarem o BitLocker, a menos que o dispositivo esteja associado a um domínio e as informações de recuperação do BitLocker tenham sido armazenadas com êxito no Active Directory.

### <a name="bitlocker-removable-data-drive-settings"></a>Definições de unidades de dados amovíveis do BitLocker

- **Acesso de escrita para a unidade de dados amovível não protegida pelo BitLocker** – especifique se a encriptação do BitLocker é necessária para as unidades de armazenamento amovíveis.
  - **Acesso de escrita para dispositivos configurados noutra organização** – especifique se é possível escrever nas unidades de dados amovíveis que pertencem a outra organização.

## <a name="windows-defender-exploit-guard"></a>Windows Defender Exploit Guard

Utilize o [Windows Defender Exploit Guard](https://docs.microsoft.com/windows/threat-protection/windows-defender-exploit-guard/windows-defender-exploit-guard) para gerir e reduzir a superfície de ataque de aplicações utilizadas pelos seus funcionários.

### <a name="attack-surface-reduction"></a>Redução da Superfície de Ataque

Ajude a [impedir as ações e aplicações](https://docs.microsoft.com/windows/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard) que são normalmente utilizadas por software maligno para explorar falhas de segurança e infetar computadores.

#### <a name="rules-to-prevent-office-macro-threats"></a>Regras para impedir ameaças macro do Office

Impeça as aplicações do Office de realizarem as seguintes ações:

- **Aplicações do Office a injetar noutros processos (sem exceções)**
- **Aplicações/macros do Office a criar conteúdo executável**
- **Aplicações do Office a iniciar processos subordinados**
- **Importações do Win32 provenientes de código macro do Office**

#### <a name="rules-to-prevent-script-threats"></a>Regras para impedir ameaças de script

Bloqueie estes itens para impedir ameaças de script:

- **Código macro js/vbs/ps/ oculto**
- **js/vbs a executar payload transferido da Internet (sem exceções)**

#### <a name="rules-to-prevent-email-threats"></a>Regras para impedir ameaças de e-mail

Bloqueie esta ação para impedir ameaças de e-mail:

- **Execução de conteúdo executável (exe, dll, ps, js, vbs, etc.) retirado do e-mail (webmail/cliente de correio) (sem exceções)**

#### <a name="attack-surface-reduction-exceptions"></a>Exceções da Redução da Superfície de Ataque

- **Ficheiros e pastas a excluir das regras de redução de superfície de ataque** – importe/adicione uma lista de localizações a excluir das regras configuradas.

### <a name="controlled-folder-access"></a>Acesso a pastas controladas

Ajude a proteger dados valiosos de ameaças e aplicações malignas, tal como ransomware.

- **Proteção de pastas** – proteja ficheiros e pastas de alterações indesejadas por parte de aplicações malignas. Pode importar uma **Lista de aplicações que têm acesso a pastas protegidas** ou adicioná-las manualmente. Também pode adicionar uma **Lista de pastas adicionais que necessitam ser protegidas** com um carregamento ou adicioná-las manualmente.

### <a name="network-filtering"></a>Filtragem de rede

Bloqueie ligações de saída de qualquer aplicação para endereços IP/domínios com baixa reputação.

### <a name="exploit-protection"></a>Exploit Protection

Bloqueie a **Edição da interface do Exploit Protection por parte dos utilizadores** ao carregar um ficheiro XML que lhe permite configurar a memória, controlar o fluxo e as restrições de políticas que podem ser utilizadas para proteger uma aplicação contra explorações de falhas de segurança.

Para ativar o Exploit Protection, crie um ficheiro XML que represente as definições de mitigação de sistema e aplicação à sua escolha. Pode fazê-lo ao utilizar um de dois métodos:

 1. PowerShell: utilize um ou mais dos cmdlets Get-ProcessMitigation, Set-ProcessMitigation e ConvertTo-ProcessMitigationPolicy do PowerShell para configurar definições de mitigação e exportar uma representação XML dos mesmos.

 2. IU do Centro de Segurança do Windows Defender: no Centro de Segurança do Windows Defender, clique no controlo de browser e na aplicação e, em seguida, desloque-se para a parte inferior do ecrã resultante para localizar o Exploit Protection. Em primeiro lugar, utilize as definições do sistema e os separadores das definições de programa para configurar definições de atenuação. Em seguida, localize a ligação de definições de Exportação na parte inferior do ecrã para exportar uma representação XML dos mesmos.

## <a name="windows-defender-application-control"></a>Controlo de Aplicações do Windows Defender

Utilize as **Políticas de integridade do código de controlo de aplicações** para escolher as aplicações adicionais que precisam de ser auditadas ou que podem ser consideradas de confiança para serem executadas pelo Controlo de Aplicações do Windows Defender. Os componentes do Windows e todas as aplicações da Microsoft Store são automaticamente considerados de confiança para serem executados.

As aplicações não serão bloqueadas quando são executadas no modo "apenas auditoria". O modo "apenas auditoria" regista todos os eventos nos registos do cliente local.

## <a name="windows-defender-security-center"></a>Centro de Segurança do Windows Defender

A aplicação Centro de Segurança do Windows Defender funciona como uma aplicação ou processo separado de cada uma das funcionalidades individuais e irá apresentar notificações através do Centro de Ação. Atua como um recoletor ou único local para ver o estado e realizar configurações para cada uma das funcionalidades. Saiba mais na documentação do [Windows Defender](https://docs.microsoft.com/windows/threat-protection/windows-defender-security-center/windows-defender-security-center).

#### <a name="windows-defender-security-center-app-and-notifications"></a>Aplicações e notificações do Centro de Segurança do Windows Defender

Bloqueie o acesso de utilizadores finais a várias áreas da aplicação Centro de Segurança do Windows Defender. Ocultar uma secção também irá bloquear notificações relacionadas.

- **Proteção contra vírus e ameaças**
- **Desempenho e estado de funcionamento do dispositivo**
- **Firewall e proteção da rede**
- **Controlo de aplicações e browsers**
- **Opções de família**
- **Notificações das áreas apresentadas da aplicação** – escolha quais as notificações a apresentar aos utilizadores finais. As notificações não críticas incluem resumos de atividade do Antivírus do Windows Defender, incluindo notificações quando as análises forem concluídas. Todas as outras notificações são consideradas críticas.

#### <a name="it-contact-information"></a>Informação de contacto de TI

Forneça as informações de contacto de TI para que sejam apresentadas na aplicação Centro de Segurança do Windows Defender e nas notificações da aplicação. Pode optar por **Mostrar na aplicação e nas notificações**, **Mostrar apenas na aplicação**, **Mostrar apenas nas notificações** ou **Não mostrar**. Tem de definir o **Nome da organização de TI** e, pelo menos, uma das seguintes opções de contacto:

- **Número de telefone ou ID do Skype do departamento de TI**
- **Endereço de e-mail do departamento de TI**
- **URL do site de suporte de TI**

## <a name="next-steps"></a>Próximos passos

Se quiser continuar e atribuir este perfil a grupos, veja [Como atribuir perfis de dispositivo](device-profile-assign.md).
