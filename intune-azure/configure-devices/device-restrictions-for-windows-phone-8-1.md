---
title: "Definições de restrições de dispositivos do Intune para Windows Phone 8.1 | Pré-visualização do Azure no Intune | Documentos da Microsoft"
description: "Pré-visualização do Azure no Intune: saiba que definições do Intune pode utilizar para controlar as definições dos dispositivos e a funcionalidade em dispositivos Windows Phone 8.1."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/23/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c2d42714-49ca-43b3-b080-2e67a4268198
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 8640f60ddafd41826edaf781fbdb1fa76fe5c7e6
ms.openlocfilehash: a24e4a58d0938778efc89fa473864100e698bea8


---

# <a name="windows-phone-81-device-restriction-settings-in-intune-azure-preview"></a>Definições de restrições de dispositivos Windows Phone 8.1 na pré-visualização do Azure no Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

## <a name="general"></a>Geral
-   **Aplicar todas as definições apenas ao Windows Phone 8.1** – Esta é uma definição que pode configurar no portal clássico do Intune. No portal do Azure, esta definição não pode ser alterada. Se esta definição estiver definida como **Configurada**, as definições só serão aplicadas a dispositivos com o Windows Phone 8.1. Se estiver definida como **Não configurada**, estas definições também serão aplicadas a dispositivos com o Windows 10 Mobile.
-   **Câmara** – Permite ou bloqueia a câmara do dispositivo.
-   **Copiar e colar** – Permite ou bloqueia a funcionalidade de copiar e colar nos dispositivos.
-   **Armazenamento amovível** – Permite ao dispositivo utilizar armazenamento amovível, como cartões SD.
-   **Geolocalização** – Permite ao dispositivo utilizar informações de localização.
-   **Conta Microsoft** – Permita ou bloqueie a ligação de uma conta Microsoft ao dispositivo por parte do utilizador.
-   **Captura de ecrã** – Permite ao utilizador capturar o conteúdo do ecrã como um ficheiro de imagem.
-   **Submissão de dados de diagnóstico** – Permite ao dispositivo enviar informações de diagnóstico para a Microsoft.
-   **Sincronização de contas de e-mail personalizadas** – Permite ao dispositivo ligar-se a contas de e-mail não Microsoft.

## <a name="password"></a>Palavra-passe
-   **Aplicar todas as definições apenas ao Windows Phone 8.1** – Esta é uma definição que pode configurar no portal clássico do Intune. No portal do Azure, esta definição não pode ser alterada. Se esta definição estiver definida como **Configurada**, as definições só serão aplicadas a dispositivos com o Windows Phone 8.1. Se estiver definida como **Não configurada**, estas definições também serão aplicadas a dispositivos com o Windows 10 Mobile.
-   **Palavra-passe obrigatória** – Exija que o utilizador final introduza uma palavra-passe para aceder ao dispositivo.
    -   **Tipo obrigatório de palavra-passe** – Especifica o tipo de palavra-passe que será necessária, como alfanumérica ou apenas numérica.
    -   **Comprimento mínimo da palavra-passe** – Especifica o número mínimo de carateres necessários na palavra-passe.
    -   **Palavras-passe simples** – Especifica que se pode utilizar palavras-passe simples, como “0000” e “1234”.
    -   **Número de falhas de início de sessão antes de eliminar os dados do dispositivo** – Especifica o número de vezes que uma palavra-passe incorreta pode ser introduzida antes de os dados do dispositivo serem eliminados.
    -   **Máximo de minutos de inatividade até o ecrã bloquear** – Especifica a quantidade de tempo durante o qual um dispositivo tem de permanecer inativo até o ecrã ser automaticamente bloqueado.
    -   **Expiração de palavra-passe (dias)** – Especifica o número de dias antes de ser preciso alterar a palavra-passe do dispositivo.
    -   **Impedir a reutilização de palavras-passe anteriores** – Especifica quantas palavras-passe utilizadas anteriormente podem ser memorizadas.
-   **Encriptação** – Requer que os dados nos dispositivos móveis suportados sejam encriptados.

## <a name="app-store"></a>App Store
-   **Aplicar todas as definições apenas ao Windows Phone 8.1** – Esta é uma definição que pode configurar no portal clássico do Intune. No portal do Azure, esta definição não pode ser alterada. Se esta definição estiver definida como **Configurada**, as definições só serão aplicadas a dispositivos com o Windows Phone 8.1. Se estiver definida como **Não configurada**, estas definições também serão aplicadas a dispositivos com o Windows 10 Mobile.
-   **Loja de aplicações** – Permite que os utilizadores se liguem à loja de aplicações a partir do dispositivo.

## <a name="restricted-apps"></a>Aplicações restritas

-   **Aplicar todas as definições apenas ao Windows Phone 8.1** – Esta é uma definição que pode configurar no portal clássico do Intune. No portal do Azure, esta definição não pode ser alterada. Se esta definição estiver definida como **Configurada**, as definições só serão aplicadas a dispositivos com o Windows Phone 8.1. Se estiver definida como **Não configurada**, estas definições também serão aplicadas a dispositivos com o Windows 10 Mobile.

Na lista de aplicações restritas, pode configurar uma das seguintes listas:

Uma lista de **Aplicações bloqueadas** – Indique as aplicações (não geridas pelo Intune) que os utilizadores não têm permissão para instalar e executar.
Uma lista de **Aplicações permitidas** – Indique as aplicações que os utilizadores têm permissão para instalar. As aplicações geridas pelo Intune são automaticamente permitidas.

Para configurar a lista, clique em **Adicionar** e, em seguida, especifique um nome à sua escolha, o fabricante da aplicação (opcional) e o URL para a aplicação na loja de aplicações.

### <a name="how-to-specify-the-url-to-an-app-in-the-store"></a>Como especificar o URL para uma aplicação na loja

Para especificar um URL de aplicação na lista de aplicações permitidas e bloqueadas, utilize o seguinte formato:

Na página [Loja Windows Phone](https://www.microsoft.com/store/apps/windows-phone), procure a aplicação que pretende utilizar.

Abra a página da aplicação e copie o URL para a área de transferência. Agora, pode utilizar este URL na lista de aplicações permitidas ou bloqueadas.

Exemplo: procure a aplicação Skype na loja. O URL a utilizar será **http://www.windowsphone.com/pt-pt/store/app/skype/c3f8e570-68b3-4d6a-bdbb-c0a3f4360a51**.



### <a name="additional-options"></a>Opções adicionais

Também pode clicar em **Importar** para preencher a lista a partir de um ficheiro csv, no formato <*url da aplicação*>, <*nome da aplicação*>, <*publicador da aplicação*> ou clicar em **Exportar** para criar um ficheiro csv que contenha o conteúdo da lista de aplicações restritas no mesmo formato.


## <a name="browser"></a>Browser
-   **Aplicar todas as definições apenas ao Windows Phone 8.1** – Esta é uma definição que pode configurar no portal clássico do Intune. No portal do Azure, esta definição não pode ser alterada. Se esta definição estiver definida como **Configurada**, as definições só serão aplicadas a dispositivos com o Windows Phone 8.1. Se estiver definida como **Não configurada**, estas definições também serão aplicadas a dispositivos com o Windows 10 Mobile.
-   **Browser** – Permite ou bloqueia o browser incorporado nos dispositivos.

## <a name="cellular-and-connectivity"></a>Rede Móvel e Conectividade
-   **Aplicar todas as definições apenas ao Windows Phone 8.1** – Esta é uma definição que pode configurar no portal clássico do Intune. No portal do Azure, esta definição não pode ser alterada. Se esta definição estiver definida como **Configurada**, as definições só serão aplicadas a dispositivos com o Windows Phone 8.1. Se estiver definida como **Não configurada**, estas definições também serão aplicadas a dispositivos com o Windows 10 Mobile.
-   **Wi-Fi** – Ativa ou desativa a funcionalidade Wi-Fi do dispositivo.
-   **Tethering Wi-Fi** – Permite a utilização de tethering Wi-Fi no dispositivo.
-   **Ligar automaticamente a hotspots Wi-Fi** – Permite ao dispositivo ligar-se automaticamente a hotspots Wi-Fi gratuitos e aceitar automaticamente quaisquer termos de utilização.
-   **Relatórios de hotspots de Wi-Fi** – Envia informações sobre ligações Wi-Fi para ajudar o utilizador a detetar ligações próximas.
-   **NFC** – Ativa ou desativa operações que utilizam a comunicação de proximidade em dispositivos que a suportam.
-   **Bluetooth** – Ativa ou desativa a funcionalidade Bluetooth do dispositivo.



<!--HONumber=Feb17_HO1-->


