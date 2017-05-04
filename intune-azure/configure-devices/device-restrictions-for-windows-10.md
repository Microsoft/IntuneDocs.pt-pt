---
title: "Definições de restrição de dispositivos no Intune para dispositivos Windows 10"
titleSuffix: Intune Azure preview
description: "Pré-visualização do Azure no Intune: saiba que definições do Intune pode utilizar para controlar as definições dos dispositivos e a funcionalidade em dispositivos Windows 10."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 89f2d806-2e97-430c-a9a1-70688269627f
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: e5dd7cb5b320df7f443b52a1b502027fa3c4acaf
ms.openlocfilehash: 43c2c517dffbb6b2e7b654c5ca8a0ad9062683eb
ms.lasthandoff: 04/19/2017


---

# <a name="windows-10-and-later-device-restriction-settings-in-microsoft-intune"></a>Definições de restrição de dispositivos Windows 10 e posterior no Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

## <a name="general"></a>Geral
-     **Captura de ecrã (apenas dispositivos móveis)** – permite que o utilizador faça uma captura do ecrã do dispositivo como uma imagem.
-     **Copiar e colar (apenas dispositivos móveis)** – Permita ações de copiar e colar entre aplicações no dispositivo.
-     **Anular inscrições manualmente** – Permite que o utilizador elimine manualmente a conta da área de trabalho do dispositivo.
-     **Instalação do certificado de raiz manual (apenas dispositivos móveis)** – impede o utilizador de instalar manualmente os certificados de raiz e os certificados CAP intermédios.
-     **Submissão de dados de diagnóstico** – Os valores possíveis são:
    -         **Nenhum** – Não são enviados dados à Microsoft
    -         **Básico** – São enviadas à Microsoft informações limitadas
    -         **Melhorado** – São enviados à Microsoft dados de diagnóstico melhorados
    -         **Completo** – Envia os mesmos dados que Melhorado, juntamente com dados adicionais sobre o estado do dispositivo
-     **Câmara** – Permita ou bloqueie a utilização da câmara no dispositivo.
-     **Sincronização de ficheiros do OneDrive** – impede o dispositivo de sincronizar ficheiros no OneDrive.
-     **Armazenamento amovível** – Especifica se os dispositivos de armazenamento externo, como um cartão SD, podem ser utilizados com o dispositivo.
-     **Geolocalização** – Especifica se o dispositivo pode utilizar informações de serviços de localização.
-     **Partilha da Internet** – Permite a utilização da partilha de ligação à Internet no dispositivo.
-     **Reposição do telefone** – Controla se o utilizador pode fazer uma reposição de fábrica do dispositivo.
-     **Ligação USB (apenas para dispositivos móveis)** – controla se os dispositivos podem aceder a dispositivos de armazenamento externo através de uma ligação USB.
-     **Modo antirroubo (apenas para dispositivos móveis)** – configure se o Modo antirroubo do Windows está ativado.
-     **Notificações do centro de ação (apenas para dispositivos móveis)** – ative ou desative as notificações do centro de ação no ecrã de bloqueio do dispositivo (apenas no Windows 10 Mobile).
-     **Cortana** – Ative ou desative o assistente de voz Cortana.
-     **Gravação de voz (apenas para dispositivos móveis)** – permita ou bloqueie a utilização do gravador de voz do dispositivo.
-     **Modificação das definições de energia e suspensão (apenas no ambiente de trabalho)** – impede o utilizador final de alterar as definições de energia e suspensão no dispositivo.
-     **Modificação de definições de região (apenas no ambiente de trabalho)** – impede o utilizador final de alterar as definições de região no dispositivo.
-     **Modificação das definições de idioma (apenas no ambiente de trabalho)** – impede o utilizador de alterar as definições de idioma no dispositivo.
-     **Modificação da Hora do Sistema** –impede o utilizador final de alterar a data e a hora do dispositivo.
-     **Modificação do nome do dispositivo** – impede o utilizador final de alterar o nome do dispositivo.
-     **Adicionar pacotes de aprovisionamento** – bloqueia o agente de configuração do tempo de execução que instala os pacotes de aprovisionamento.
-     **Remover pacotes de aprovisionamento** – bloqueia o agente de configuração do tempo de execução que remove os pacotes de aprovisionamento.
-     **Deteção de dispositivos** – bloqueie a deteção de um dispositivo por outros dispositivos.
-     **Comutador de Tarefa (apenas para dispositivos móveis)** – bloqueia o comutador de tarefa no dispositivo.
-     **Caixa de diálogo de erro de cartão SIM (apenas para dispositivos móveis)** – impedirá que uma mensagem de erro seja apresentada no dispositivo se nenhum cartão SIM for detetado.


## <a name="password"></a>Palavra-passe
-     **Palavra-passe** – exija que o utilizador final introduza uma palavra-passe para aceder ao dispositivo.
    -     **Tipo obrigatório de palavra-passe** – Especifica se a palavra-passe tem de ser apenas numérica ou alfanumérica.
    -     **Comprimento mínimo da palavra-passe** – Aplica-se apenas ao Windows 10 Mobile.
    -     **Número de falhas de início de sessão antes de eliminar os dados do dispositivo** – Para dispositivos com o Windows 10: se o dispositivo tiver o BitLocker ativado, será colocado no modo de recuperação do BitLocker após o início de sessão falhar o número de vezes que especificar. Se o dispositivo não tiver o BitLocker ativado, esta definição não se aplica.
Para dispositivos com o Windows 10 Mobile: após o início de sessão falhar o número de vezes que especificar, o dispositivo será apagado.
    -     **Máximo de minutos de inatividade até o ecrã bloquear** – Especifica o período de tempo durante o qual um dispositivo tem de estar inativo até o ecrã ser bloqueado.
    -     **Expiração de palavra-passe (dias)** – Especifica o período de tempo após o qual a palavra-passe do dispositivo tem de ser alterada.
    -     **Impedir a reutilização de palavras-passe anteriores** – Especifica o número de palavras-passe utilizadas anteriormente que são memorizadas pelo dispositivo.
    -     **Exigir palavra-passe quando o dispositivo regressa do estado de inatividade** – Especifica que o utilizador tem de introduzir uma palavra-passe para desbloquear o dispositivo (apenas no Windows 10 Mobile).
-     **Encriptação** – Ative a encriptação em dispositivos visados (apenas no Windows 10 Mobile).

## <a name="personalization"></a>Personalização

-     **URL da imagem de fundo do ambiente de trabalho (Apenas para ambiente de trabalho)** – especifique o URL para uma imagem em formato PNG, JPG ou JPEG que será utilizada como a imagem de fundo do ambiente de trabalho do Windows. Os utilizadores não poderão alterá-la.

## <a name="locked-screen-experience"></a>Experiência de ecrã bloqueado

-     **URL da imagem do ecrã bloqueado (Apenas para ambiente de trabalho)** – especifique o URL para uma imagem em formato PNG, JPG ou JPEG que será utilizada como a imagem de fundo do ecrã bloqueado do Windows. Os utilizadores não poderão alterá-la.


## <a name="app-store"></a>App Store

-     **App Store (apenas dispositivos móveis)** – Permita ou bloqueie a utilização da loja de aplicações em dispositivos Windows 10 Mobile.
-     **Atualização automática de aplicações a partir da loja** – permite que as aplicações instaladas a partir da Loja Windows sejam atualizadas automaticamente.
-     **Instalação de aplicação fidedigna** – permite que as aplicações assinadas com um certificado fidedigno sejam sideloaded.
-     **Desbloqueio de programador** – permita as definições de programador do Windows, tais como permitir que as aplicações de sideload sejam modificadas pelo utilizador final.
-     **Dados da aplicação do utilizador partilhados** – permite que as aplicações partilhem dados entre os diferentes utilizadores no mesmo dispositivo.
-     **Utilizar apenas loja privada** – ative esta opção para permitir que apenas os utilizadores finais transfiram aplicações a partir da loja privada.
-     **Lançamento de aplicação originado pela loja** – utilizado para desativar todas as aplicações que foram previamente instaladas no dispositivo ou transferidas a partir da Loja Windows.
-     **Instalar dados da aplicação no volume de sistema** – impede que as aplicações armazenem dados no volume do sistema do dispositivo.
-     **Instalar dados da aplicação na unidade do sistema** – impede que as aplicações armazenem dados na unidade do sistema do dispositivo.
-     **Gravador de Jogo (apenas no ambiente de trabalho)** – configura se a gravação e a difusão de jogos são permitidas.



## <a name="edge-browser"></a>Browser Edge
-     **Browser Microsoft Edge (apenas dispositivos móveis)** – Permita a utilização do browser Edge no dispositivo.
-     **SmartScreen** – Ativa ou desativa o SmartScreen, que bloqueia sites fraudulentos.
-     **Enviar cabeçalhos Do Not Track** – Configura o browser Edge para enviar cabeçalhos Do Not Track para sites que os utilizadores visitam.
-     **Cookies** – Permite que o browser guarde cookies de Internet no dispositivo.
-     **JavaScript** – Permite que scripts, como JavaScript, sejam executados no browser Edge.
-     **Pop-ups** – bloqueia as janelas pop-up no browser (Aplica-se apenas ao ambiente de trabalho do Windows 10).
-     **Sugestões de pesquisa** – Permite que o motor de busca sugira sites à medida que escreve expressões de pesquisa.
-     **Enviar tráfego da intranet para o Internet Explorer** – permite que os utilizadores abram sites da intranet no Internet Explorer (apenas no ambiente de trabalho do Windows 10).
-     **Preenchimento automático** – permite que os utilizadores alterem as definições da conclusão automática no browser (apenas no ambiente de trabalho do Windows 10).
-     **Gestor de Palavras-passe** – Ative ou desative a funcionalidade Gestor de Palavras-passe do Microsoft Edge.
-     **Localização da lista de sites do Modo Empresarial** – Especifica onde encontrar a lista de sites que abrem no modo Empresarial. Os utilizadores não podem editar esta lista.<br>(apenas para computadores com o Windows 10).
-     **Ferramentas de programação** – impeça que o utilizador final abra as ferramentas de programação do Edge.
-     **Extensões** – permita que o utilizador final instale as extensões do Edge no dispositivo.
-     **Navegação InPrivate** – impeça que o utilizador final abra sessões de navegação InPrivate.
-     **Execute primeiro o URL** – introduza o URL que o browser Edge irá abrir na primeira vez que for executado (apenas para dispositivos móveis).
-     **Páginas iniciais** – adicione uma lista de sites que serão utilizados como páginas iniciais no browser Edge (apenas no ambiente de trabalho).
-     **Bloquear acesso a sinalizadores** – impeça que o utilizador final aceda à página about:flags no Edge, que contém as definições experimentais e de programação.
-     **Ignorar pedido do smart screen** – permita que o utilizador final ignore os avisos do filtro SmartScreen sobre sites potencialmente maliciosos.
-     **Ignorar pedido do smart screen para ficheiros** – permita que o utilizador final ignore os avisos do filtro SmartScreen sobre a transferência de ficheiros potencialmente maliciosos.
-     **Endereço IP do anfitrião local WebRtc** – impeça que o endereço IP de localhost dos utilizadores seja apresentado quando realizar chamadas telefónicas através do protocolo RTC da Web.
-     **Motor de busca predefinido** – especifique o motor de busca predefinido a ser utilizado. Os utilizadores finais podem alterar este valor em qualquer altura.

## <a name="search"></a>Procura
- **Pesquisa Segura (apenas para dispositivos móveis)** – controle o modo como a Cortana filtra o conteúdo para adultos nos resultados da pesquisa. Pode selecionar **Rigoroso**, **Moderado** ou permitir que o utilizador final escolha as suas próprias definições.

## <a name="cloud-and-storage"></a>Cloud e Armazenamento
-     **Conta Microsoft** – Permite que o utilizador associe uma conta Microsoft ao dispositivo.
-     **Conta não Microsoft** – Permite que o utilizador adicione contas de e-mail ao dispositivo que não estão associadas a uma conta Microsoft.
-     **Sincronização de definições para a conta Microsoft** – Permita que as definições do dispositivo e de aplicações associadas a uma conta Microsoft sejam sincronizadas entre dispositivos.

## <a name="cellular-and-connectivity"></a>Rede Móvel e Conectividade
-     **Roaming de dados** – Permita roaming entre redes ao aceder a dados.
-     **VPN na rede celular** – Controla se o dispositivo pode aceder a ligações VPN quando ligado a uma rede celular.
-     **Roaming de VPN na rede celular** – Controla se o dispositivo pode aceder a ligações VPN quando está em roaming numa rede celular.
-     **Bluetooth** – Controla se o utilizador pode ativar e configurar Bluetooth do dispositivo.
-     **Deteção de Bluetooth** – Permite que este dispositivo seja detetado por outros dispositivos com Bluetooth ativado.
-     **Publicidade do Bluetooth** – Permite que o dispositivo receba anúncios através de Bluetooth.
-     **Nome do dispositivo com Bluetooth** – permite-lhe especificar o nome do dispositivo com Bluetooth.
-     **NFC** – Permite que o utilizador ative e configure funções de Comunicações de Proximidade no dispositivo.
-     **Wi-Fi** – Permite que o utilizador ative e configure Wi-Fi no dispositivo (apenas no Windows 10 Mobile).
-     **Ligar automaticamente a hotspots Wi-Fi** – Permite que o dispositivo ligue automaticamente a hotspots Wi-Fi gratuitos e aceite automaticamente os termos e condições da ligação.
-     **Configuração de Wi-Fi manual** – Controla se o utilizador pode configurar as suas próprias ligações Wi-Fi ou se este pode utilizar apenas as ligações configuradas por um perfil Wi-Fi (apenas no Windows 10 Mobile).
-     **Intervalo de Deteção do Wi-Fi** – especifique a frequência de deteção de redes Wi-Fi por parte dos dispositivos.

## <a name="control-panel-and-settings"></a>Painel de Controlo e Definições

-     **Aplicação de definições** – bloqueie o acesso à aplicação de definições do Windows.
    -     **Sistema** – bloqueia o acesso à área do sistema da aplicação de definições.
    -     **Dispositivos** – bloqueia o acesso à área de dispositivos da aplicação de definições.
    -     **Rede e Internet** – bloqueia o acesso à área da Internet e da rede da aplicação de definições.
    -     **Personalização** – bloqueia o acesso à área de personalização da aplicação de definições.
    -     **Contas** – bloqueia o acesso à área das contas da aplicação de definições.
    -     **Hora e Idioma** – bloqueia o acesso à área da hora e do idioma da aplicação de definições.
    -     **Facilidade de Acesso** – bloqueia o acesso à área de facilidade de acesso da aplicação de definições.
    -     **Privacidade** – bloqueia o acesso à área de privacidade da aplicação de definições.
    -     **Atualização e Segurança** – bloqueia o acesso à área das atualizações e de segurança da aplicação de definições.

## <a name="defender"></a>Defender

-     **Monitorização em tempo real** – Permite a análise em tempo real de software maligno, spyware e outro software indesejável.
-     **Monitorização de comportamento** – Permite que o Defender verifique a existência de determinados padrões conhecidos de atividade suspeita nos dispositivos.
-     **Sistema de Inspeção de Rede (NIS)** – O Sistema de Inspeção de Rede (NIS) ajuda a proteger os dispositivos contra exploits baseados na rede, com as assinaturas de vulnerabilidades conhecidas do Microsoft Endpoint Protection Center para ajudar a detetar e a bloquear tráfego malicioso.
-     **Analisar todas as transferências** – Controla se o Defender analisa todos os ficheiros transferidos da Internet.
-     **Analisar scripts carregados em browsers da Microsoft** – Permite que o Defender analise scripts que são utilizados no Internet Explorer.
-     **Acesso do utilizador final ao Defender** – Controla se a interface de utilizador do Windows Defender está ocultada dos utilizadores finais.
Quando esta definição é alterada, será aplicada da próxima vez que o PC do utilizador final for reiniciado.
-     **Intervalo de atualização de assinatura (em horas)** – Especifique o intervalo no qual o Defender irá verificar a existência de novos ficheiros de assinatura.
-     **Monitorizar a atividade dos ficheiros e programas** – Permite que o Defender monitorize a atividade de ficheiros e programas nos dispositivos.
-     **Dias a aguardar antes de eliminar o software malicioso em quarentena** – Permite que o Defender continue a controlar o software maligno resolvido durante o número de dias que especificar, para que possa verificar manualmente os dispositivos afetados anteriormente. Se definir o número de dias como **0**, o software maligno permanece na pasta Quarentena e não é removido automaticamente.
-     **Limite de utilização da CPU durante uma análise** – Permite limitar a quantidade de CPU que as análises estão autorizadas a utilizar (de **1** a **100**).
-     **Analisar ficheiros de arquivo** – Permite que o Defender analise ficheiros arquivados, tais como ficheiros Zip ou Cab.
-     **Analisar mensagens de correio recebidas** – Permite que o Defender analise mensagens de e-mail quando chegam ao dispositivo.
-     **Analisar unidades amovíveis durante uma análise completa** – Permite que o Defender analise unidades amovíveis, como pens USB.
-     **Analisar unidades de rede mapeadas durante uma análise completa** – Permite que o Defender analise ficheiros em unidades de rede mapeadas.<br>Se os ficheiros na unidade forem só de leitura, o Defender não conseguirá remover qualquer software maligno encontrado nos mesmos.
-     **Analisar ficheiros abertos a partir de pastas de rede** – Permite que o Defender analise ficheiros em unidades de rede partilhadas (por exemplo, as unidades acedidas a partir de um caminho UNC).
Se os ficheiros na unidade forem só de leitura, o Defender não conseguirá remover qualquer software maligno encontrado nos mesmos.
-     **Proteção da cloud** – Permite ou impede que o Serviço de Proteção Ativa Microsoft receba informações sobre a atividade de software maligno nos dispositivos geridos por si. Estas informações são utilizadas para melhorar o serviço no futuro.
-     **Avisar os utilizadores antes da submissão de exemplo** – Controla se os ficheiros que possam exigir análise adicional pela Microsoft para determinar se são maliciosos são automaticamente enviados à Microsoft.
-     **Hora a realizar uma análise rápida diária** – Permite agendar uma análise rápida que ocorre diariamente à hora que selecionar.
-     **Tipo de análise do sistema a realizar** –Permite-lhe especificar o nível de análise a realizar quando agendar uma análise do sistema.

## <a name="defender-exclusions"></a>Exclusões do Defender

-     **Ficheiros e pastas a excluir de análises e da proteção em tempo real** – Adiciona um ou mais ficheiros e pastas, como **C:\Path** ou **%ProgramFiles%\Path\filename.exe**, à lista de exclusões. Estes ficheiros e pastas não são incluídos em análises em tempo real ou agendadas.
-     **Extensões de ficheiros a excluir de análises e da proteção em tempo real** – Adicione uma ou mais extensões de ficheiro, como **jpg** ou **txt**, à lista de exclusões. Os ficheiros com estas extensões não são incluídos em análises em tempo real ou agendadas.
-     **Processos a excluir de análises e da proteção em tempo real** – Adicione um ou mais processos do tipo **.exe**, **.com** ou **.scr** à lista de exclusões. Estes processos não serão incluídos em análises em tempo real ou agendadas.


## <a name="network-proxy"></a>Proxy de rede

-     **Detetar automaticamente as definições de proxy** – se a opção estiver ativada, o dispositivo tentará localizar o caminho para um script de PAC.
-     **Utilizar script de proxy** – selecione esta opção se pretender especificar um caminho para um script de PAC para configurar o servidor proxy.
    -     **URL do endereço do script de configuração** – introduza o URL de um script de PAC que pretende utilizar para configurar o servidor proxy.
-     **Utilizar servidor proxy manual** – selecione esta opção se pretende introduzir manualmente as informações do servidor proxy.
    -     **Endereço** – introduza o nome ou o endereço IP do servidor proxy.
    -     **Número de porta** – introduza o número de porta do servidor proxy.
    -     **Exceções de proxy** – introduza os URLs que não podem utilizar o servidor proxy. Utilize um ponto e vírgula para separar cada item.
    -     **Ignorar servidor proxy para endereço local** – ative esta opção se não pretender utilizar o servidor proxy para endereços locais na sua intranet.


## <a name="windows-spotlight"></a>Destaque do Windows

-     **Destaque do Windows** – permita ou bloqueie o Destaque do Windows, que proporciona funcionalidades como sugestões e truques, mensagens no Ecrã de bloqueio do Windows e muito mais.
    -     **Sugestões do Windows** – permite-lhe bloquear a apresentação de sugestões pop-up no Windows.
    -     **Funcionalidades do Consumidor** – permite-lhe bloquear funcionalidades do consumidor como sugestões do menu Iniciar e notificações de associação.

## <a name="display"></a>Apresentar

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
