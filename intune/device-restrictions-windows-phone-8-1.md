---
title: "Definições de restrição de dispositivos no Microsoft Intune para dispositivos Windows Phone 8.1"
titleSuffix: 
description: "Saiba que definições do Intune pode utilizar para controlar as definições e funcionalidades em dispositivos Windows Phone 8.1."
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/6/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 808c8e9ac1ef944b69ae8e548c62d4c6366820d0
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/08/2018
---
# <a name="microsoft-intune-windows-phone-81-device-restriction-settings"></a>Definições de restrição de dispositivos Windows Phone 8.1 no Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Este artigo mostra-lhe as definições de restrição de dispositivos do Microsoft Intune que pode configurar para dispositivos Windows Phone 8.1.


## <a name="general"></a>Geral

-   **Câmara** – Permite ou bloqueia a câmara do dispositivo.
-   **Copiar e colar** – Permite ou bloqueia a funcionalidade de copiar e colar nos dispositivos.
-   **Armazenamento amovível** – Permite ao dispositivo utilizar armazenamento amovível, como cartões SD.
-   **Geolocalização** – Permite ao dispositivo utilizar informações de localização.
-   **Conta Microsoft** – Permita ou bloqueie a ligação de uma conta Microsoft ao dispositivo por parte do utilizador.
-   **Captura de ecrã** – Permite ao utilizador capturar o conteúdo do ecrã como um ficheiro de imagem.
-   **Submissão de dados de diagnóstico** – Permite ao dispositivo enviar informações de diagnóstico para a Microsoft.
-   **Sincronização de contas de e-mail personalizadas** – Permite ao dispositivo ligar-se a contas de e-mail não Microsoft.

## <a name="password"></a>Palavra-passe

-   **Palavra-passe** – Exija que o utilizador final introduza uma palavra-passe para aceder ao dispositivo.
    -   **Tipo de palavra-passe necessária** – Especifica o tipo de palavra-passe que será necessária, como alfanumérica ou apenas numérica.
    -   **Comprimento mínimo da palavra-passe** – Especifica o número mínimo de carateres necessários na palavra-passe.
    -   **Palavras-passe simples** – Especifica que se pode utilizar palavras-passe simples, como “0000” e “1234”.
    -   **Número de falhas de início de sessão antes de eliminar os dados do dispositivo** – Especifica o número de vezes que uma palavra-passe incorreta pode ser introduzida antes de os dados do dispositivo serem eliminados.
    -   **Máximo de minutos de inatividade até o ecrã bloquear** – Especifica a quantidade de tempo durante o qual um dispositivo tem de permanecer inativo até o ecrã ser automaticamente bloqueado.
    -   **Expiração de palavra-passe (dias)** – Especifica o número de dias antes de ser preciso alterar a palavra-passe do dispositivo.
    -   **Impedir a reutilização de palavras-passe anteriores** – Especifica quantas palavras-passe utilizadas anteriormente podem ser memorizadas.
-   **Encriptação** – Requer que os dados nos dispositivos móveis suportados sejam encriptados.

## <a name="app-store"></a>App Store

-   **Loja de aplicações** – Permite que os utilizadores se liguem à loja de aplicações a partir do dispositivo.

## <a name="restricted-apps"></a>Aplicações restritas

Na lista de aplicações restritas, pode configurar uma das seguintes listas:

Uma lista de **Aplicações bloqueadas** – Indique as aplicações (não geridas pelo Intune) que os utilizadores não têm permissão para instalar e executar.
Uma lista de **Aplicações permitidas** – Indique as aplicações que os utilizadores têm permissão para instalar. As aplicações geridas pelo Intune são automaticamente permitidas.

Para configurar a lista, clique em **Adicionar** e, em seguida, especifique um nome à sua escolha, o fabricante da aplicação (opcional) e o URL para a aplicação na loja de aplicações.

### <a name="how-to-specify-the-url-to-an-app-in-the-store"></a>Como especificar o URL para uma aplicação na loja

Para especificar um URL de aplicação na lista de aplicações permitidas e bloqueadas, utilize o seguinte formato:

Na página [Loja Windows Phone](https://www.microsoft.com/store/apps/windows-phone), procure a aplicação que pretende utilizar.

Abra a página da aplicação e copie o URL para a área de transferência. Agora, pode utilizar este URL na lista de aplicações permitidas ou bloqueadas.

Exemplo: procure a aplicação Skype na loja. O URL a utilizar será **http://www.windowsphone.com/store/app/skype/c3f8e570-68b3-4d6a-bdbb-c0a3f4360a51**.



### <a name="additional-options"></a>Opções adicionais

Também pode clicar em **Importar** para preencher a lista a partir de um ficheiro csv, no formato <*url da aplicação*>, <*nome da aplicação*>, <app publisher> ou clicar em **Exportar** para criar um ficheiro csv que inclua o conteúdo da lista de aplicações restritas no mesmo formato.


## <a name="browser"></a>Browser

-   **Browser** – Permite ou bloqueia o browser incorporado nos dispositivos.

## <a name="cellular-and-connectivity"></a>Rede Móvel e Conectividade

-   **Wi-Fi** – Ativa ou desativa a funcionalidade Wi-Fi do dispositivo.
-   **Tethering Wi-Fi** – Permite a utilização de tethering Wi-Fi no dispositivo.
-   **Ligar automaticamente a hotspots Wi-Fi** – Permite ao dispositivo ligar-se automaticamente a hotspots Wi-Fi gratuitos e aceitar automaticamente quaisquer termos de utilização.
-   **Relatórios de hotspots de Wi-Fi** – Envia informações sobre ligações Wi-Fi para ajudar o utilizador a detetar ligações próximas.
-   **NFC** – Ativa ou desativa operações que utilizam a comunicação de proximidade em dispositivos que a suportam.
-   **Bluetooth** – Ativa ou desativa a funcionalidade Bluetooth do dispositivo.
