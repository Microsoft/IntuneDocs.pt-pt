---
title: "Definições de restrições de dispositivos do Intune para Android | Pré-visualização do Azure no Intune | Documentos da Microsoft"
description: "Pré-visualização do Azure no Intune: saiba que definições do Intune pode utilizar para controlar as definições dos dispositivos e a funcionalidade em dispositivos Android."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/23/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6bdf714a-5d93-485c-8b52-513635c60cb6
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 74023866802eb4c13e7e9ff97e8048afe7d62409
ms.openlocfilehash: 40e04f1f8e7972bcd72cceae272d8295a496df7a


---

# <a name="android-and-samsung-knox-standard-device-restriction-settings-in-intune-azure-preview"></a>Definições de restrições de dispositivos do Android e Samsung KNOX Standard na pré-visualização do Azure no Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

## <a name="general"></a>Geral
-   **Câmara** – Permite a utilização da câmara do dispositivo.
-   **Copiar e colar** – Permite as funções de copiar e colar no dispositivo.
-   **Partilha de área de transferência entre aplicações** – Permite a utilização da área de transferência para copiar e colar entre aplicações (apenas no Samsung KNOX Standard).
-   **Submissão de dados de diagnóstico** – Impede o utilizador de submeter dados de diagnóstico a partir do dispositivo.    
-   **Reposição de fábrica** – Permite ao utilizador realizar uma reposição de fábrica no dispositivo.
-   **Geolocalização** – Permite que o dispositivo utilize informações de localização (apenas no Samsung KNOX Standard).
-   **Desligar** – Permite ao utilizador desligar o dispositivo.<br>Se esta definição estiver desativada, a definição **Número de falhas de início de sessão antes da eliminação de dados no dispositivo** dos dispositivos Samsung KNOX Standard não funcionará.
-   **Captura de ecrã** – Permite ao utilizador capturar o conteúdo do ecrã como uma imagem.
-   **Assistente de voz** – Permite a utilização do software do assistente de voz do dispositivo (apenas no Samsung KNOX Standard).
-   **YouTube** – Permite a utilização da aplicação do YouTube no dispositivo (apenas no Samsung KNOX Standard).

## <a name="password"></a>Palavra-passe
-   **Palavra-passe obrigatória** – Exija que o utilizador final introduza uma palavra-passe para aceder ao dispositivo.
-   **Comprimento mínimo da palavra-passe** –Introduza o comprimento mínimo da palavra-passe que um utilizador tem de configurar (entre 4 e 16 carateres).
-   **Máximo de minutos de inatividade até o ecrã bloquear** – Especifica o número de minutos de inatividade antes de o dispositivo bloquear automaticamente.
-   **Número de falhas de início de sessão antes de eliminar os dados do dispositivo** – Especifica o número de falhas de início de sessão consecutivas a permitir antes de os dados do dispositivo serem apagados.
-   **Expiração de palavra-passe (dias)** – Especifica o número de dias antes de ser preciso alterar a palavra-passe do dispositivo.
-   **Tipo obrigatório de palavra-passe** – Especifica o nível de complexidade da palavra-passe exigido e se podem ser utilizados dispositivos biométricos.
-   **Impedir a reutilização de palavras-passe anteriores** – Impede que o utilizador final crie uma palavra-passe que já tenha utilizado antes.
-   **Desbloqueio por impressão digital** – Permite a utilização de uma impressão digital para desbloquear os dispositivos suportados.
-   **Smart Lock e outros agentes de fidedignidade** – Permite-lhe controlar a funcionalidade Smart Lock em dispositivos Android compatíveis (Samsung KNOX Standard 5.0 e posterior). Esta capacidade de telefone, por vezes conhecida como agente de confiança, permite desativar ou ignorar a palavra-passe de bloqueio do ecrã do dispositivo se o dispositivo estiver numa localização fidedigna (por exemplo, quando está ligado a um dispositivo Bluetooth específico ou quando está próximo de uma etiqueta NFC). Pode utilizar esta definição para impedir que os utilizadores configurem o Smart Lock.
-   **Encriptação** – Requer que os ficheiros no dispositivo estejam encriptados.

## <a name="google-play-store"></a>Google Play Store

-   **Google Play Store** – Permite ao utilizador aceder à Google Play Store no dispositivo (apenas no Samsung KNOX Standard).

## <a name="restricted-apps"></a>Aplicações restritas

Na lista de aplicações restritas, pode configurar uma das seguintes listas:

Uma lista de **Aplicações proibidas** – Indique as aplicações (não geridas pelo Intune) que os utilizadores não têm permissão para instalar e executar.
Uma lista de **Aplicações aprovadas** – Indique as aplicações que os utilizadores têm permissão para instalar. Para permanecerem compatíveis, os utilizadores não têm de instalar aplicações que não estejam listadas. As aplicações geridas pelo Intune são automaticamente permitidas.
Os perfis de dispositivo que contêm as definições de aplicações restritas têm de ser implementados em grupos de utilizadores.

Para configurar a lista, clique em **Adicionar** e, em seguida, especifique um nome à sua escolha, o fabricante da aplicação (opcional) e o URL para a aplicação na loja de aplicações.

### <a name="how-to-specify-the-url-to-an-app-in-the-store"></a>Como especificar o URL para uma aplicação na loja

Para especificar um URL de aplicação na lista de aplicações conformes e não conformes, siga os seguintes passos:

Na [secção Aplicações do Google Play](https://play.google.com/store/apps), procure a aplicação que pretende utilizar.

Abra a página de instalação da aplicação e copie o URL para a área de transferência. Agora pode utilizar este URL na lista de aplicações conformes ou na lista de aplicações não conformes.

Exemplo: procure Microsoft Office Mobile no Google Play. O URL a utilizar será **https://play.google.com/store/apps/details?id=com.microsoft.office.officehub&hl=pt**.

### <a name="additional-options"></a>Opções adicionais

Também pode clicar em **Importar** para preencher a lista a partir de um ficheiro csv, no formato <*url da aplicação*>, <*nome da aplicação*>, <*publicador da aplicação*> ou clicar em **Exportar** para criar um ficheiro csv que contenha o conteúdo da lista de aplicações restritas no mesmo formato.      

## <a name="browser"></a>Browser
-   **Browser** – Especifica se o browser predefinido do dispositivo pode ser utilizado.
-   **Preenchimento automático** – Permite a utilização da função de preenchimento automático do browser.
-   **Cookies** – Permite que o browser do dispositivo utilize cookies.
-   **JavaScript** – Permite que o browser do dispositivo execute scripts em Java.
-   **Pop-ups** – Permite a utilização do bloqueador de janelas pop-up no browser.

## <a name="cloud-and-storage"></a>Cloud e Armazenamento
-   **Cópia de segurança do Google** – Permite a utilização da cópia de segurança do Google.
-   **Sincronização automática da Conta Google** – Permite que as definições da Conta Google sejam sincronizadas automaticamente.
-   **Armazenamento amovível** – Permite que o dispositivo utilize armazenamento amovível, como um cartão SD (apenas no Samsung KNOX Standard).
-   **Encriptação em cartões de armazenamento** – Especifica se o cartão de armazenamento do dispositivo tem de estar encriptado.

## <a name="cellular-and-connectivity"></a>Rede Móvel e Conectividade
-   **Roaming de dados** – Permita o roaming de dados quando o dispositivo estiver numa rede celular (apenas no Samsung KNOX Standard).
-   **Mensagens SMS/MMS** – Permite a utilização de mensagens SMS e MMS no dispositivo (apenas no Samsung KNOX Standard).
-   **Marcação por voz** – Ativa ou desativa a funcionalidade de marcação por voz do dispositivo (apenas no Samsung KNOX Standard).
-   **Chamadas em roaming** – Permite chamadas em roaming quando o dispositivo estiver numa rede celular (apenas no Samsung KNOX Standard).
-   **Bluetooth** – Permite a utilização do Bluetooth no dispositivo (apenas no Samsung KNOX Standard).
-   **NFC** – Permite operações que utilizam comunicação de proximidade se o dispositivo a suportar (apenas no Samsung KNOX Standard).
-   **Wi-Fi** – Permite a utilização das funções Wi-Fi do dispositivo (apenas no Samsung KNOX Standard).
-   **Tethering Wi-Fi** – Permite a utilização do tethering Wi-Fi no dispositivo (apenas no Samsung KNOX Standard).

## <a name="kiosk"></a>Kiosk
-   **Selecionar uma aplicação gerida** – Navegue até às aplicações geridas e selecione uma que possa ser executada quando o dispositivo estiver no modo de local público (as aplicações especificadas como uma ligação para a loja não são atualmente suportadas). Não será permitida a execução de outras aplicações no dispositivo.
-   **Botão de suspensão do ecrã** – Ativa ou desativa o botão suspender/reativar ecrã do dispositivo.
-   **Botões de volume** - Ativa ou desativa a utilização dos botões de volume no dispositivo.



<!--HONumber=Feb17_HO1-->


