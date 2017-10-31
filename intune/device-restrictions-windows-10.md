---
title: "Definições de restrição de dispositivos no Intune para dispositivos Windows 10"
titlesuffix: Azure portal
description: "Saiba quais são as definições do Intune que pode utilizar para controlar as definições dos dispositivos e a funcionalidade em dispositivos Windows 10.\""
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 08/23/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 89f2d806-2e97-430c-a9a1-70688269627f
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 759207adf49308dcd4e6253627e4a1213be22904
ms.sourcegitcommit: 2e77fe177a3df1dfe48e72f4c2bfaa1f0494c621
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/19/2017
---
# <a name="windows-10-and-later-device-restriction-settings-in-microsoft-intune"></a>Definições de restrição de dispositivos Windows 10 e posterior no Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

## <a name="general"></a>Geral
-   **Captura de ecrã (apenas dispositivos móveis)** – permite que o utilizador faça uma captura do ecrã do dispositivo como uma imagem.
-   **Copiar e colar (apenas dispositivos móveis)** – Permita ações de copiar e colar entre aplicações no dispositivo.
-   **Anular inscrições manualmente** – Permite que o utilizador elimine manualmente a conta da área de trabalho do dispositivo.
-   **Instalação do certificado de raiz manual (apenas dispositivos móveis)** – impede o utilizador de instalar manualmente os certificados de raiz e os certificados CAP intermédios.
-   **Submissão de dados de diagnóstico** – Os valores possíveis são:
    -       **Nenhum** – Não são enviados dados à Microsoft
    -       **Básico** – São enviadas à Microsoft informações limitadas
    -       **Melhorado** – São enviados à Microsoft dados de diagnóstico melhorados
    -       **Completo** – Envia os mesmos dados que Melhorado, juntamente com dados adicionais sobre o estado do dispositivo
-   **Câmara** – Permita ou bloqueie a utilização da câmara no dispositivo.
-   **Sincronização de ficheiros do OneDrive** – impede o dispositivo de sincronizar ficheiros no OneDrive.
-   **Armazenamento amovível** – especifica se os dispositivos de armazenamento externo, como os cartões SD, podem ser utilizados no dispositivo.
-   **Geolocalização** – Especifica se o dispositivo pode utilizar informações de serviços de localização.
-   **Partilha da Internet** – Permite a utilização da partilha de ligação à Internet no dispositivo.
-   **Reposição do telefone** – Controla se o utilizador pode fazer uma reposição de fábrica do dispositivo.
-   **Ligação USB (apenas para dispositivos móveis)** – controla se os dispositivos podem aceder a dispositivos de armazenamento externo através de uma ligação USB.
-   **Modo antirroubo (apenas para dispositivos móveis)** – configure se o Modo antirroubo do Windows está ativado.
-   **Cortana** – Ative ou desative o assistente de voz Cortana.
-   **Gravação de voz (apenas para dispositivos móveis)** – permite ou bloqueia a utilização do gravador de voz do dispositivo.
-   **Modificação do nome do dispositivo** – impede o utilizador final de alterar o nome do dispositivo (apenas no Windows 10 Mobile)
-   **Adicionar pacotes de aprovisionamento** – bloqueia o agente de configuração do tempo de execução que instala os pacotes de aprovisionamento.
-   **Remover pacotes de aprovisionamento** – bloqueia o agente de configuração do tempo de execução que remove os pacotes de aprovisionamento.
-   **Deteção de dispositivos** – bloqueie a deteção de um dispositivo por outros dispositivos.
-   **Comutador de Tarefa (apenas para dispositivos móveis)** – bloqueia o comutador de tarefa no dispositivo.
-   **Caixa de diálogo de erro de cartão SIM (apenas para dispositivos móveis)** – impedirá que uma mensagem de erro seja apresentada no dispositivo se nenhum cartão SIM for detetado.


## <a name="password"></a>Palavra-passe
-   **Palavra-passe** – exija que o utilizador final introduza uma palavra-passe para aceder ao dispositivo.
    -   **Tipo obrigatório de palavra-passe** – Especifica se a palavra-passe tem de ser apenas numérica ou alfanumérica.
    -   **Comprimento mínimo da palavra-passe** – Aplica-se apenas ao Windows 10 Mobile.
    -   **Número de falhas de início de sessão antes de eliminar os dados do dispositivo** – Para dispositivos com o Windows 10: se o dispositivo tiver o BitLocker ativado, será colocado no modo de recuperação do BitLocker após o início de sessão falhar o número de vezes que especificar. Se o dispositivo não tiver o BitLocker ativado, esta definição não se aplica.
Para dispositivos com o Windows 10 Mobile: após o início de sessão falhar o número de vezes que especificar, o dispositivo será apagado.
    -   **Máximo de minutos de inatividade até o ecrã bloquear** – Especifica o período de tempo durante o qual um dispositivo tem de estar inativo até o ecrã ser bloqueado.
    -   **Expiração de palavra-passe (dias)** – Especifica o período de tempo após o qual a palavra-passe do dispositivo tem de ser alterada.
    -   **Impedir a reutilização de palavras-passe anteriores** – Especifica o número de palavras-passe utilizadas anteriormente que são memorizadas pelo dispositivo.
    -   **Exigir palavra-passe quando o dispositivo regressa do estado de inatividade (apenas para dispositivos móveis)** – Especifica que o utilizador tem de introduzir uma palavra-passe para desbloquear o dispositivo (apenas no Windows 10 Mobile).
    -   **Palavras-passe simples** – permite a utilização de palavras-passe simples, como 1111 e 1234. Esta definição também permite ou bloqueia a utilização de palavras-passe por imagem do Windows.
-   **Encriptação** – Ative a encriptação nos dispositivos visados.

## <a name="personalization"></a>Personalização

-   **URL da imagem de fundo do ambiente de trabalho (apenas no ambiente de trabalho)** – especifique o URL para uma imagem em formato PNG, JPG ou JPEG que pretenda utilizar como a imagem de fundo do ambiente de trabalho do Windows. Os utilizadores não poderão alterá-la.

## <a name="privacy"></a>Privacidade

-   **Personalização de entrada** – não permite a utilização de serviços de fala baseados na cloud para a Cortana, o ditado ou aplicações da Loja Microsoft. Se permitir estes serviços, a Microsoft recolherá os dados de voz para melhorar o serviço.
-   **Aceitação automática de pedidos de consentimento do utilizador de emparelhamento e privacidade** – permite que o Windows aceite automaticamente as mensagens de consentimento de emparelhamento e privacidade ao executar as aplicações.


## <a name="locked-screen-experience"></a>Experiência de ecrã bloqueado


-   **Notificações do centro de ações (apenas para dispositivos móveis)** – permite a apresentação de notificações do Centro de Ações no ecrã de bloqueio do dispositivo (apenas no Windows 10 Mobile).
-   **URL da imagem do ecrã bloqueado (Apenas para ambiente de trabalho)** – especifique o URL para uma imagem em formato PNG, JPG ou JPEG que será utilizada como a imagem de fundo do ecrã bloqueado do Windows. Os utilizadores não poderão alterá-la.
-   **Tempo limite do ecrã configurável pelo utilizador (apenas para dispositivos móveis)** – permite que os utilizadores configurem a quantidade de tempo 
-   **Cortana no ecrã bloqueado (apenas no ambiente de trabalho)** – não permite que o utilizador interaja com a Cortana quando o dispositivo tiver o ecrã bloqueado (apenas para computadores com o Windows 10).
-   **Notificações de alerta no ecrã bloqueado** – bloqueia a apresentação de mensagens de alerta no ecrã de bloqueio do dispositivo.
-   **Tempo limite de ecrã (apenas para dispositivos móveis)** – especifica o tempo em segundos depois de o ecrã bloquear em que se irá desligar.



## <a name="app-store"></a>Loja de Aplicações

-   **Loja de aplicações (apenas dispositivos móveis)** – Permita ou bloqueie a utilização da loja de aplicações em dispositivos Windows 10 Mobile.
-   **Atualização automática de aplicações a partir da loja** – permite que as aplicações instaladas a partir da Loja Microsoft sejam atualizadas automaticamente.
-   **Instalação de aplicação fidedigna** – permite que as aplicações assinadas com um certificado fidedigno sejam sideloaded.
-   **Desbloqueio de programador** – permita as definições de programador do Windows, tais como permitir que as aplicações de sideload sejam modificadas pelo utilizador final.
-   **Dados da aplicação do utilizador partilhados** – permite que as aplicações partilhem dados entre os diferentes utilizadores no mesmo dispositivo.
-   **Utilizar apenas loja privada** – ative esta opção para permitir que apenas os utilizadores finais transfiram aplicações a partir da loja privada.
-   **Lançamento de aplicação originado pela loja** – utilizado para desativar todas as aplicações que foram previamente instaladas no dispositivo ou transferidas a partir da Loja Microsoft.
-   **Instalar dados da aplicação no volume de sistema** – impede que as aplicações armazenem dados no volume do sistema do dispositivo.
-   **Instalar dados da aplicação na unidade do sistema** – impede que as aplicações armazenem dados na unidade do sistema do dispositivo.
-   **Gravador de Jogo (apenas no ambiente de trabalho)** – configura se a gravação e a difusão de jogos são permitidas.
-   **Aplicações apenas a partir da loja** – configura se os utilizadores podem instalar aplicações de outros locais que não a loja de aplicações.



## <a name="edge-browser"></a>Browser Edge
-   **Browser Microsoft Edge (apenas dispositivos móveis)** – Permita a utilização do browser Edge no dispositivo.
-   **Lista pendente da barra de endereço (apenas no ambiente de trabalho)** – utilize isto para impedir o Edge de apresentar uma lista de sugestões numa lista pendente à medida que escreve. Isto ajuda a minimizar a utilização da largura de banda de rede entre o Edge e os serviços Microsoft.
-   **Sincronizar favoritos entre browsers da Microsoft (apenas no ambiente de trabalho)** – permite que o Windows sincronize os favoritos entre o Internet Explorer e o Edge.
-   **Enviar cabeçalhos Do Not Track** – Configura o browser Edge para enviar cabeçalhos Do Not Track para sites que os utilizadores visitam.
-   **Cookies** – Permite que o browser guarde cookies de Internet no dispositivo.
-   **JavaScript** – Permite que scripts, como JavaScript, sejam executados no browser Edge.
-   **Pop-ups** – bloqueia as janelas pop-up no browser (Aplica-se apenas ao ambiente de trabalho do Windows 10).
-   **Sugestões de pesquisa** – Permite que o motor de busca sugira sites à medida que escreve expressões de pesquisa.
-   **Enviar tráfego da intranet para o Internet Explorer** – permite que os utilizadores abram sites da intranet no Internet Explorer (apenas no ambiente de trabalho do Windows 10).
-   **Preenchimento automático** – permite que os utilizadores alterem as definições da conclusão automática no browser (apenas no ambiente de trabalho do Windows 10).
-   **Gestor de Palavras-passe** – Ative ou desative a funcionalidade Gestor de Palavras-passe do Microsoft Edge.
-   **Localização da lista de sites do Modo Empresarial** – Especifica onde encontrar a lista de sites que abrem no modo Empresarial. Os utilizadores não podem editar esta lista.<br>(apenas para computadores com o Windows 10).
-   **Ferramentas de programação** – impeça que o utilizador final abra as ferramentas de programação do Edge.
-   **Extensões** – permita que o utilizador final instale as extensões do Edge no dispositivo.
-   **Navegação InPrivate** – impeça que o utilizador final abra sessões de navegação InPrivate.
-   **Mostrar a página de primeira execução** – impede a apresentação da página de introdução na primeira vez que executa o Edge.
    -   **Primeiro URL executado** – especifica o URL que é apresentado na primeira vez que um utilizador executa o Edge (apenas no Windows 10 Mobile).
-   **Home Pages** – adicione uma lista de sites que pretende utilizar como home pages no browser Edge (apenas no ambiente de trabalho).
-   **Alterações à página inicial** – permite que os utilizadores alterem as páginas iniciais apresentadas quando o Edge é aberto. Utilize a definição Home Pages para criar a página, ou lista de páginas, que é apresentada quando o Edge é iniciado.
-   **Bloquear acesso a sinalizadores** – impeça que o utilizador final aceda à página about:flags no Edge, que contém as definições experimentais e de programação.
-   **Endereço IP do anfitrião local WebRtc** – impeça que o endereço IP de localhost dos utilizadores seja apresentado quando realizar chamadas telefónicas através do protocolo RTC da Web.
-   **Motor de busca predefinido** – especifique o motor de busca predefinido a ser utilizado. Os utilizadores finais podem alterar este valor em qualquer altura.
-   **Limpar dados de navegação à saída** – limpa o histórico e os dados de navegação quando o utilizador sai do Edge.
-   **Recolha de dados do Mosaico Dinâmico** – impede o Windows de recolher informações do Mosaico Dinâmico quando um utilizador afixa um site ao menu inicial do Edge.

## <a name="edge-browser-smartscreen"></a>SmartScreen do Browser Edge

-   **SmartScreen** – ativa ou desativa o SmartScreen, que bloqueia sites fraudulentos.
-   **Ignorar pedido do smart screen** – permita que o utilizador final ignore os avisos do filtro SmartScreen sobre sites potencialmente maliciosos.
-   **Ignorar pedido do smart screen para ficheiros** – permita que o utilizador final ignore os avisos do filtro SmartScreen sobre a transferência de ficheiros potencialmente maliciosos.

## <a name="search"></a>Procura
- **Pesquisa Segura (apenas para dispositivos móveis)** – controle o modo como a Cortana filtra o conteúdo para adultos nos resultados da pesquisa. Pode selecionar **Rigoroso**, **Moderado** ou permitir que o utilizador final escolha as suas próprias definições.

## <a name="cloud-and-storage"></a>Cloud e Armazenamento
-   **Conta Microsoft** – Permite que o utilizador associe uma conta Microsoft ao dispositivo.
-   **Conta não Microsoft** – Permite que o utilizador adicione contas de e-mail ao dispositivo que não estão associadas a uma conta Microsoft.
-   **Sincronização de definições para a conta Microsoft** – Permita que as definições do dispositivo e de aplicações associadas a uma conta Microsoft sejam sincronizadas entre dispositivos.

## <a name="cellular-and-connectivity"></a>Rede Móvel e Conectividade

-   **Canal de dados da rede móvel** – impede os utilizadores de utilizarem os dados (por exemplo, ao navegarem na Web) quando estão ligados a uma rede móvel. 
-   **Roaming de dados** – Permita roaming entre redes ao aceder a dados.
-   **VPN na rede celular** – Controla se o dispositivo pode aceder a ligações VPN quando ligado a uma rede celular.
-   **Roaming de VPN na rede celular** – Controla se o dispositivo pode aceder a ligações VPN quando está em roaming numa rede celular.
-   **Bluetooth** – Controla se o utilizador pode ativar e configurar Bluetooth do dispositivo.
-   **Deteção de Bluetooth** – Permite que este dispositivo seja detetado por outros dispositivos com Bluetooth ativado.
-   **Pré-emparelhamento de bluetooth** – permite-lhe configurar dispositivos Bluetooth específicos para que sejam emparelhados automaticamente com um dispositivo anfitrião.
-   **Publicidade do Bluetooth** – Permite que o dispositivo receba anúncios através de Bluetooth.
-   **Serviço de dispositivos ligados** – permite-lhe escolher se quer permitir o serviço de dispositivos ligados, que ativa a deteção e ligação a outros dispositivos Bluetooth.
-   **NFC** – Permite que o utilizador ative e configure funções de Comunicações de Proximidade no dispositivo.
-   **Wi-Fi** – Permite que o utilizador ative e configure Wi-Fi no dispositivo (apenas no Windows 10 Mobile).
-   **Ligar automaticamente a hotspots Wi-Fi** – Permite que o dispositivo ligue automaticamente a hotspots Wi-Fi gratuitos e aceite automaticamente os termos e condições da ligação.
-   **Configuração de Wi-Fi manual** – Controla se o utilizador pode configurar as suas próprias ligações Wi-Fi ou se este pode utilizar apenas as ligações configuradas por um perfil Wi-Fi (apenas no Windows 10 Mobile).
-   **Intervalo de Deteção do Wi-Fi** – especifique a frequência de deteção de redes Wi-Fi por parte dos dispositivos. Especifique um valor de 1 (mais frequente) a 500 (menos frequente).
-   **Serviços Bluetooth permitidos** – especifique, como cadeias hexadecimais, uma lista de perfis e serviços Bluetooth permitidos.


## <a name="control-panel-and-settings"></a>Painel de Controlo e Definições

-   **Aplicação de definições** – bloqueie o acesso à aplicação de definições do Windows.
    -   **Sistema** – bloqueia o acesso à área do sistema da aplicação de definições.
        -   **Modificação das definições de energia e suspensão (apenas no ambiente de trabalho)** – impede o utilizador final de alterar as definições de energia e suspensão no dispositivo.
    -   **Dispositivos** – bloqueia o acesso à área de dispositivos da aplicação de definições.
    -   **Rede e Internet** – bloqueia o acesso à área da Internet e da rede da aplicação de definições.
    -   **Personalização** – bloqueia o acesso à área de personalização da aplicação de definições.
    -   **Contas** – bloqueia o acesso à área das contas da aplicação de definições.
    -   **Hora e Idioma** – bloqueia o acesso à área da hora e do idioma da aplicação de definições.
        -   **Modificação da Hora do Sistema** –impede o utilizador final de alterar a data e a hora do dispositivo.
        -   **Modificação de definições de região (apenas no ambiente de trabalho)** – impede o utilizador final de alterar as definições de região no dispositivo.
        -   **Modificação das definições de idioma (apenas no ambiente de trabalho)** – impede o utilizador de alterar as definições de idioma no dispositivo.
    -   **Jogos** – bloqueia o acesso à aplicação Jogos nas Definições.
    -   **Facilidade de Acesso** – bloqueia o acesso à área de facilidade de acesso da aplicação de definições.
    -   **Privacidade** – bloqueia o acesso à área de privacidade da aplicação de definições.
    -   **Atualização e Segurança** – bloqueia o acesso à área das atualizações e de segurança da aplicação de definições.

## <a name="defender"></a>Defender

-   **Monitorização em tempo real** – Permite a análise em tempo real de software maligno, spyware e outro software indesejável.
-   **Monitorização de comportamento** – Permite que o Defender verifique a existência de determinados padrões conhecidos de atividade suspeita nos dispositivos.
-   **Network Inspection System (NIS)** – o NIS ajuda a proteger os dispositivos contra exploits baseados na rede. Utiliza as assinaturas de vulnerabilidades conhecidas do Microsoft Endpoint Protection Center para ajudar a detetar e bloquear tráfego malicioso.
-   **Analisar todas as transferências** – Controla se o Defender analisa todos os ficheiros transferidos da Internet.
-   **Analisar scripts carregados em browsers da Microsoft** – Permite que o Defender analise scripts que são utilizados no Internet Explorer.
-   **Acesso do utilizador final ao Defender**  – Controla se a interface de utilizador do Windows Defender está ocultada dos utilizadores finais.
Quando esta definição for alterada, será aplicada da próxima vez que o PC do utilizador final for reiniciado.
-   **Intervalo de atualização de assinatura (em horas)** – especifique o intervalo no qual o Defender verifica a existência de novos ficheiros de assinatura.
-   **Monitorizar a atividade dos ficheiros e programas** – Permite que o Defender monitorize a atividade de ficheiros e programas nos dispositivos.
-   **Dias a aguardar antes de eliminar o software malicioso em quarentena** – Permite que o Defender continue a controlar o software maligno resolvido durante o número de dias que especificar, para que possa verificar manualmente os dispositivos afetados anteriormente. Se definir o número de dias como **0**, o software maligno permanece na pasta Quarentena e não é removido automaticamente.
-   **Limite de utilização da CPU durante uma análise** – Permite limitar a quantidade de CPU que as análises estão autorizadas a utilizar (de **1** a **100**).
-   **Analisar ficheiros de arquivo** – Permite que o Defender analise ficheiros arquivados, tais como ficheiros Zip ou Cab.
-   **Analisar mensagens de correio recebidas** – Permite que o Defender analise mensagens de e-mail quando chegam ao dispositivo.
-   **Analisar unidades amovíveis durante uma análise completa** – Permite que o Defender analise unidades amovíveis, como pens USB.
-   **Analisar unidades de rede mapeadas durante uma análise completa** – Permite que o Defender analise ficheiros em unidades de rede mapeadas.<br>Se os ficheiros na unidade forem só de leitura, o Defender não conseguirá remover software maligno encontrado nos mesmos.
-   **Analisar ficheiros abertos a partir de pastas de rede** – permite que o Defender analise ficheiros em unidades de rede partilhadas (por exemplo, os ficheiros acedidos a partir de um caminho UNC).
Se os ficheiros na unidade forem só de leitura, o Defender não conseguirá remover software maligno encontrado nos mesmos.
-   **Proteção da cloud** – Permite ou impede que o Serviço de Proteção Ativa Microsoft receba informações sobre a atividade de software maligno nos dispositivos geridos por si. Estas informações são utilizadas para melhorar o serviço no futuro.
-   **Avisar os utilizadores antes da submissão de exemplo** – controla se ficheiros potencialmente maliciosos que possam necessitar de análise adicional são automaticamente enviados à Microsoft.
-   **Hora a realizar uma análise rápida diária** – Permite agendar uma análise rápida que ocorre diariamente à hora que selecionar.
-   **Tipo de análise do sistema a realizar** – permite-lhe especificar o nível de análise a realizar quando agendar uma análise do sistema.
-   **Detetar aplicações potencialmente indesejadas**  – selecione o nível de proteção quando o Windows detetar aplicações potencialmente indesejadas de entre as opções:
        - **Bloquear**
        - **Auditar** Para obter mais informações sobre aplicações potencialmente indesejadas, veja [este tópico](https://docs.microsoft.com/windows/threat-protection/windows-defender-antivirus/detect-block-potentially-unwanted-apps-windows-defender-antivirus).
-   **Ações sobre ameaças de software maligno detetadas** – ative esta opção para especificar as ações que o Defender deve executar para cada nível de ameaça que detetar (Baixo, Moderado, Alto e Grave). As ações que pode realizar são:
    -   **Limpar**
    -   **Quarentena**
    -   **Remove**
    -   **Permitir**
    -   **Definido pelo utilizador**
    -   **Bloquear**



## <a name="defender-exclusions"></a>Exclusões do Defender

-   **Ficheiros e pastas a excluir de análises e da proteção em tempo real** – Adiciona um ou mais ficheiros e pastas, como **C:\Path** ou **%ProgramFiles%\Path\filename.exe**, à lista de exclusões. Estes ficheiros e pastas não são incluídos em análises em tempo real ou agendadas.
-   **Extensões de ficheiros a excluir de análises e da proteção em tempo real** – Adicione uma ou mais extensões de ficheiro, como **jpg** ou **txt**, à lista de exclusões. Os ficheiros com estas extensões não são incluídos em análises em tempo real ou agendadas.
-   **Processos a excluir de análises e da proteção em tempo real** – Adicione um ou mais processos do tipo **.exe**, **.com** ou **.scr** à lista de exclusões. Estes processos não são incluídos em análises agendadas ou em tempo real.


## <a name="network-proxy"></a>Proxy de rede

-   **Detetar automaticamente as definições de proxy** – se esta opção estiver ativada, o dispositivo tenta localizar o caminho de um script de PAC.
-   **Utilizar script de proxy** – selecione esta opção se pretender especificar um caminho para um script de PAC para configurar o servidor proxy.
    -   **URL do endereço do script de configuração** – introduza o URL de um script de PAC que pretende utilizar para configurar o servidor proxy.
-   **Utilizar servidor proxy manual** – selecione esta opção se pretende introduzir manualmente as informações do servidor proxy.
    -   **Endereço** – introduza o nome ou o endereço IP do servidor proxy.
    -   **Número de porta** – introduza o número de porta do servidor proxy.
    -   **Exceções de proxy** – introduza os URLs que não podem utilizar o servidor proxy. Utilize um ponto e vírgula para separar cada item.
    -   **Ignorar servidor proxy para endereço local** – se não quiser utilizar o servidor proxy para endereços locais na sua intranet, ative esta opção.


## <a name="windows-spotlight"></a>Destaque do Windows


- **Destaque do Windows** – utilize esta definição para bloquear todas as funcionalidades do Destaque do Windows em dispositivos com o Windows 10. Se bloquear esta definição, as seguintes definições não estarão disponíveis.
    - **Destaque do Windows no ecrã de bloqueio** – impede o Destaque do Windows de apresentar informações no ecrã de bloqueio do dispositivo.
    - **Sugestões de terceiros no Destaque do Windows** – impede o Destaque do Windows de sugerir conteúdos que não tenham sido publicados pela Microsoft.
    - **Funcionalidades do Consumidor** – permite-lhe bloquear funcionalidades do consumidor como sugestões do menu Iniciar e notificações de associação.
    - **Sugestões do Windows** – permite-lhe bloquear a apresentação de sugestões pop-up no Windows.
    - **Destaque do Windows no centro de ação** – bloqueia a apresentação de sugestões do Destaque do Windows, como uma nova aplicação ou conteúdos de segurança, no Windows Action Center.
    - **Personalização do Destaque do Windows** – impede que o Destaque do Windows personalize os resultados com base na utilização de um dispositivo.
    - **Experiência de boas-vindas do Windows** – impede a apresentação da experiência de boas-vindas do Windows que mostra informações sobre funcionalidades novas e atualizadas.


## <a name="projection"></a>Projeção

- **Intervenção do utilizador a partir dos recetores de ecrã sem fios** – bloqueia a intervenção do utilizador a partir dos recetores de ecrã sem fios.
- **Projeção para este PC** – impede outros dispositivos de detetarem este PC para projeção.
- **Exigir PIN para emparelhamento** – exija um PIN ao estabelecer ligação a um dispositivo de projeção.

## <a name="start"></a>Iniciar,

- **Remover aplicações da barra de tarefas** – impeça que o utilizador remova aplicações do menu Iniciar.
- **Documentos em Iniciar** – oculte ou mostre a pasta Documentos no menu Iniciar do Windows.
- **Transferências em Iniciar** – oculte ou mostre a pasta Transferências no menu Iniciar do Windows.
- **Explorador de Ficheiros em Iniciar** – oculte ou mostre a aplicação Explorador de Ficheiros no menu Iniciar do Windows.
- **Grupo Doméstico em Iniciar** – oculte ou mostre a pasta Grupo Doméstico no menu Iniciar do Windows.
- **Música em Iniciar** – oculte ou mostre a pasta Música no menu Iniciar do Windows.
- **Rede em Iniciar** – oculte ou mostre a pasta Rede no menu Iniciar do Windows.
- **Pasta Pessoal em Iniciar** – oculte ou mostre a pasta Pessoal no menu Iniciar do Windows.
- **Imagens em Iniciar** – oculte ou mostre a pasta das imagens no menu Iniciar do Windows.
- **Definições em Iniciar** – oculte ou mostre a aplicação Definições no menu Iniciar do Windows.
- **Vídeos em Iniciar** – oculte ou mostre a pasta dos vídeos no menu Iniciar do Windows.
