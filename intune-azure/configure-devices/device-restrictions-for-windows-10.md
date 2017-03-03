---
title: "Definições de restrições de dispositivos do Intune para Windows 10 | Pré-visualização do Azure no Intune | Documentos da Microsoft"
description: "Pré-visualização do Azure no Intune: saiba que definições do Intune pode utilizar para controlar as definições dos dispositivos e a funcionalidade em dispositivos Windows 10."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 89f2d806-2e97-430c-a9a1-70688269627f
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b4d095506215b775d56d172e9aabae1737757310
ms.openlocfilehash: 208312eea9df0b6330e6eac9334bd63bb13624c5
ms.lasthandoff: 02/16/2017


---

# <a name="windows-10-and-later-device-restriction-settings-in-microsoft-intune"></a>Definições de restrição de dispositivos Windows 10 e posterior no Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

## <a name="general"></a>Geral
-     **Captura de ecrã** – Permite que o utilizador faça uma captura do ecrã do dispositivo como uma imagem. (Apenas Windows 10 Mobile)
-     **Copiar e colar (apenas dispositivos móveis)** – Permita ações de copiar e colar entre aplicações no dispositivo.
-     **Anular inscrições manualmente** – Permite que o utilizador elimine manualmente a conta da área de trabalho do dispositivo.
-     **Instalação do certificado de raiz manual** -     
-     **Submissão de dados de diagnóstico** – Os valores possíveis são:
    -         **Nenhum** – Não são enviados dados à Microsoft
    -         **Básico** – São enviadas à Microsoft informações limitadas
    -         **Melhorado** – São enviados à Microsoft dados de diagnóstico melhorados
    -         **Completo** – Envia os mesmos dados que Melhorado, juntamente com dados adicionais sobre o estado do dispositivo
-     **Câmara** – Permita ou bloqueie a utilização da câmara no dispositivo.
-     **Armazenamento amovível** – Especifica se os dispositivos de armazenamento externo, como um cartão SD, podem ser utilizados com o dispositivo.
-     **Geolocalização** – Especifica se o dispositivo pode utilizar informações de serviços de localização.
-     **Partilha da Internet** – Permite a utilização da partilha de ligação à Internet no dispositivo.
-     **Reposição do telefone** – Controla se o utilizador pode fazer uma reposição de fábrica do dispositivo.
-     **Ligação USB** – Controla se os dispositivos podem aceder a dispositivos de armazenamento externo através de uma ligação USB.
-     **Modo AntiTheft** – Configure se o modo Antirroubo do Windows está ativado.
-     **Notificações de centro de ação** – Ative ou desative as notificações de centro de ação no ecrã de bloqueio do dispositivo (apenas no Windows 10 Mobile).
-     **Cortana** – Ative ou desative o assistente de voz Cortana.
-     **Gravação de voz** – Permita ou bloqueie a utilização do gravador de voz do dispositivo.

## <a name="password"></a>Palavra-passe
-     **Palavra-passe obrigatória** – Exija que o utilizador final introduza uma palavra-passe para aceder ao dispositivo.
-     **Tipo obrigatório de palavra-passe** – Especifica se a palavra-passe tem de ser apenas numérica ou alfanumérica.
-     **Comprimento mínimo da palavra-passe** – Aplica-se apenas ao Windows 10 Mobile.
-     **Número de falhas de início de sessão antes de eliminar os dados do dispositivo** – Para dispositivos com o Windows 10: se o dispositivo tiver o BitLocker ativado, será colocado no modo de recuperação do BitLocker após o início de sessão falhar o número de vezes que especificar. Se o dispositivo não tiver o BitLocker ativado, esta definição não se aplica.
Para dispositivos com o Windows 10 Mobile: após o início de sessão falhar o número de vezes que especificar, o dispositivo será apagado.
-     **Máximo de minutos de inatividade até o ecrã bloquear** – Especifica o período de tempo durante o qual um dispositivo tem de estar inativo até o ecrã ser bloqueado.
-     **Expiração de palavra-passe (dias)** – Especifica o período de tempo após o qual a palavra-passe do dispositivo tem de ser alterada.
-     **Impedir a reutilização de palavras-passe anteriores** – Especifica o número de palavras-passe utilizadas anteriormente que são memorizadas pelo dispositivo.
-     **Exigir palavra-passe quando o dispositivo regressa do estado de inatividade** – Especifica que o utilizador tem de introduzir uma palavra-passe para desbloquear o dispositivo (apenas no Windows 10 Mobile).
-     **Encriptação** – Ative a encriptação em dispositivos visados (apenas no Windows 10 Mobile).
## <a name="app-store"></a>App Store

-     **App Store (apenas dispositivos móveis)** – Permita ou bloqueie a utilização da loja de aplicações em dispositivos Windows 10 Mobile.
## <a name="edge-browser"></a>Browser Edge
-     **Browser Microsoft Edge (apenas dispositivos móveis)** – Permita a utilização do browser Edge no dispositivo.
-     **SmartScreen** – Ativa ou desativa o SmartScreen, que bloqueia sites fraudulentos.
-     **Enviar cabeçalhos Do Not Track** – Configura o browser Edge para enviar cabeçalhos Do Not Track para sites que os utilizadores visitam.
-     **Cookies** – Permite que o browser guarde cookies de Internet no dispositivo.
-     **JavaScript** – Permite que scripts, como JavaScript, sejam executados no browser Edge.
-     **Pop-ups** – Bloqueia janelas pop-up no browser.<br>(Aplica-se apenas a computadores com o Windows 10).
-     **Sugestões de pesquisa** – Permite que o motor de busca sugira sites à medida que escreve expressões de pesquisa.
-     **Enviar tráfego da intranet para o Internet Explorer** – Permite que os utilizadores abram sites da intranet no Internet Explorer. <br>(apenas para computadores com o Windows 10).
-     **Preenchimento automático** – Permite que os utilizadores alterem as definições de conclusão automática no browser.<br>(apenas para computadores com o Windows 10)
-     **Gestor de Palavras-passe** – Ative ou desative a funcionalidade Gestor de Palavras-passe do Microsoft Edge.
-     **Localização da lista de sites do Modo Empresarial** – Especifica onde encontrar a lista de sites que abrem no modo Empresarial. Os utilizadores não podem editar esta lista.<br>(apenas para computadores com o Windows 10).
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
-     **NFC** – Permite que o utilizador ative e configure funções de Comunicações de Proximidade no dispositivo.
-     **Wi-Fi** – Permite que o utilizador ative e configure Wi-Fi no dispositivo (apenas no Windows 10 Mobile).
-     **Ligar automaticamente a hotspots Wi-Fi** – Permite que o dispositivo ligue automaticamente a hotspots Wi-Fi gratuitos e aceite automaticamente os termos e condições da ligação.
-     **Configuração de Wi-Fi manual** – Controla se o utilizador pode configurar as suas próprias ligações Wi-Fi ou se este pode utilizar apenas as ligações configuradas por um perfil Wi-Fi (apenas no Windows 10 Mobile).
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

