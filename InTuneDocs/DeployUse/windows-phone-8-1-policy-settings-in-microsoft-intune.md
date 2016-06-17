---
# required metadata

title: Definições de política do Windows Phone 8.1 | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 83f7469c-272e-43f2-8139-b0d7bc34f43f

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Definições de política do Windows Phone 8.1 no Microsoft Intune

## Definições de configuração geral

Utilize a **Política de configuração geral para Windows Phone (Windows Phone 8.1 e posterior)** do Microsoft Intune para configurar as definições seguintes para dispositivos Windows Phone 8.1:

-   **Definições de segurança do dispositivo móvel** – Escolha de uma lista de definições predefinidas que permitem controlar uma série de funcionalidades e a funcionalidade do dispositivo.

-   **Aplicações compatíveis e não compatíveis** - Especifique uma lista de aplicações que são compatíveis ou não compatíveis na sua empresa. Os dispositivos Windows Phone podem bloquear ou permitir a instalação destas aplicações.

### Definições de aplicabilidade

|Nome da definição|Detalhes|
|----------------|----------------------------------|
|**Aplicar todas as configurações ao Windows 10**|Permite que as definições nesta política sejam aplicadas aos dispositivos Windows 10 Mobile, além dos dispositivos Windows Phone 8.1.|

### Definições de palavra-passe

|Nome da definição|Detalhes|Windows Phone 8|Windows Phone 8.1|
|----------------|-----------------------------------------|
|**Palavra-passe obrigatória para desbloquear os dispositivos móveis**|Especifica se os utilizadores têm de introduzir uma palavra-passe para aceder aos respetivos dispositivos.|Sim|Sim|
|**Tipo obrigatório de palavra-passe**|Especifica o tipo de palavra-passe que será necessária, como apenas numérica ou alfanumérica.|Sim|Sim|
|**Tipo de palavra-passe obrigatório – Número mínimo de conjuntos de carateres**|Existem quatro conjuntos de carateres, letras minúsculas, letras maiúsculas, números e símbolos. Esta definição especifica quantos conjuntos de carateres diferentes têm de ser incluídos na palavra-passe). (No entanto, para dispositivos iOS, isto especifica o número de carateres de símbolos que têm de ser incluídos na palavra-passe)|Sim|Sim|
|**Comprimento mínimo da palavra-passe**|Especifica o número mínimo de carateres necessários na palavra-passe.|Sim|Sim|
|**Permitir palavras-passe simples**|As palavras-passes simples incluem "0000" e "1234"|Sim|Sim|
|**Número de falhas de início de sessão consecutivas a permitir antes do dispositivo ser apagado**|Especifica o número de vezes que uma palavra-passe incorreta pode ser memorizada antes de o dispositivo ser apagado.|Sim|Sim|
|**Minutos de inatividade antes de o ecrã se desligar**|Especifica a quantidade de tempo que um dispositivo tem de permanecer inativo antes de o ecrã ser bloqueado automaticamente.|Sim|Sim|
|**Expiração da Palavra-passe (dias)**|Especifica o número de dias antes de ser necessário alterar a palavra-passe do dispositivo.|Sim|Sim|
|**Memorizar histórico de palavras-passe**|Especifica se as palavras-passe utilizadas anteriormente são memorizadas para impedir que o utilizador as utilize novamente.|Sim|Sim|
|**Memorizar histórico de palavras-passe** – **Evita a reutilização de palavras-passe anteriores**|Especifica quantas palavras-passe utilizadas anteriormente podem ser memorizadas.|Sim|Sim|

### Definições de encriptação

|Nome da definição|Detalhes|Windows Phone 8|Windows Phone 8.1|
|----------------|-----------------------------------------|
|**Encriptação obrigatória no dispositivo móvel**|Requer que os dados nos dispositivos móveis suportados sejam encriptados.<br>Para dispositivos Windows Phone 8, tem de definir esta opção como **Sim**.|Sim|Sim|

### Definições do sistema

|Nome da definição|Detalhes|Windows Phone 8|Windows Phone 8.1|
|----------------|-----------------------------------------|
|**Permitir captura de ecrã**|Permite ao utilizador capturar o conteúdo do ecrã como um ficheiro de imagem.|Não|Sim|
|**Permitir submissão de dados de diagnóstico**|Permite ao dispositivo enviar informações de diagnóstico para a Microsoft.|Não|Sim|

### Definições da nuvem – contas e sincronização

|Nome da definição|Detalhes|Windows Phone 8|Windows Phone 8.1|
|----------------|-----------------------------------------|
|**Permitir conta Microsoft**|Permite a uma conta da Microsoft estar ligada ao dispositivo móvel.|Não|Sim|

### Definições de e-mail

|Nome da definição|Detalhes|Windows Phone 8|Windows Phone 8.1|
|----------------|-----------------------------------------|
|**Permitir contas de e-mail personalizadas**|Permite ao dispositivo ligar a contas de e-mail não Microsoft.|Não|Sim|

### Definições da aplicação - browser

|Nome da definição|Detalhes|Windows Phone 8|Windows Phone 8.1|
|----------------|-----------------------------------------|
|**Permitir browser**|Permite ou bloqueia o browser incorporado nos dispositivos.|Não|Sim|

### Definições da aplicação - aplicações

|Nome da definição|Detalhes|Windows Phone 8|Windows Phone 8.1|
|----------------|-----------------------------------------|
|**Permitir loja de aplicações**|Permite aos utilizadores ligar à loja de aplicações a partir do dispositivo.|Não|Sim|

### Definições das capacidades do dispositivo - hardware

|Nome da definição|Detalhes|Windows Phone 8|Windows Phone 8.1|
|----------------|-----------------------------------------|
|**Permitir câmara**|Permite ou bloqueia a câmara do dispositivo.|Não|Sim|
|**Permitir armazenamento amovível**|Permite ao dispositivo utilizar armazenamento amovível, por exemplo, um cartão SD.|Sim|Sim|
|**Permitir Wi-Fi**|Ativa ou desativa a funcionalidade Wi-Fi do dispositivo.|Não|Sim|
|**Permitir partilha de Wi-Fi**|Permite a utilização de tethering Wi-Fi no dispositivo.|Não|Sim
|**Permitir ligação automática a hotspots Wi-Fi**|Permite ao dispositivo ligar automaticamente a hotspots Wi-Fi gratuitos e aceitar automaticamente quaisquer termos de utilização.|Não|Sim|
|**Permitir relatórios de hotspots Wi-Fi**|Envia informações sobre ligações Wi-Fi para ajudar a detetar ligações próximas.|Não|Sim|
|**Permitir geolocalização**|Permite ao dispositivo utilizar informações de localização.|Não|Sim|
|**Permitir NFC**|Permite operações que utilizam comunicação de proximidade.|Não|Sim|
|**Permitir Bluetooth**|Ativa ou desativa a funcionalidade Bluetooth do dispositivo.|Não|Sim|

### Definições das capacidades do dispositivo - funcionalidades

|Nome da definição|Detalhes|Windows Phone 8|Windows Phone 8.1|
|----------------|-----------------------------------------|
|**Permitir copiar e colar**|Permite a funcionalidade de copiar e colar nos dispositivos.|Não|Sim|

### Definições para aplicações compatíveis e não compatíveis
Na lista **Aplicações Conformes e &amp;Não Conformes**, especifique uma lista de aplicações conformes ou não conformes com as informações seguintes:

> [!NOTE]
> Uma única política só pode conter uma lista de aplicações compatíveis ou uma lista de aplicações não compatíveis. Não é possível especificar ambas na mesma política.

|Nome da definição|Detalhes|
|----------------|--------------------|
|**Impedir que os dispositivos abram as aplicações indicadas**|Indica as aplicações que não são geridas pelo Intune e para as quais os utilizadores não têm permissão para instalar e executar.|
|**Permitir que os dispositivos instalem apenas as aplicações indicadas**|Indica as aplicações que os utilizadores têm permissão para instalar. Os utilizadores não podem instalar outras aplicações. As aplicações geridas pelo Intune são automaticamente permitidas.|
|**Adicionar**|Adiciona uma aplicação à lista selecionada. Especifique um nome à sua escolha, o fabricante da aplicação (opcional) e o URL para a aplicação na loja de aplicações. Para obter mais ajuda, consulte Como especificar URLs para lojas de aplicações mais adiante neste tópico.
|**Importar Aplicações**|Importa uma lista de aplicações especificadas num ficheiro de valores separados por vírgulas. Utilize o formato, o nome da aplicação, o fabricante e o URL da aplicação no ficheiro.|
|**Editar**|Permite-lhe editar o nome, o fabricante e o URL da aplicação selecionada.|
|**Eliminar**|Elimina a aplicação selecionada da lista.|
> [!IMPORTANT] Se especificar uma lista de aplicações permitidas para dispositivos Windows Phone 8.1, tem de adicionar a aplicação Portal da Empresa a esta lista ou a mesma será bloqueada.


### Informações de referência para aplicações compatíveis e não compatíveis

#### Como especificar URLs para lojas de aplicações
Para especificar um URL de aplicação na lista de aplicações compatíveis e não compatíveis, utilize o seguinte formato:

Na página [Aplicações+Jogos do Windows Phone](http://www.windowsphone.com/en-us/store/overview) , procure a aplicação que pretende utilizar.

Abra a página da aplicação e copie o URL para a área de transferência. Agora pode utilizar este URL na lista de aplicações compatíveis ou na lista de aplicações não compatíveis.

**Exemplo:** Procure a aplicação Skype na loja. O URL a utilizar será **http://www.windowsphone.com/pt-pt/store/app/skype/c3f8e570-68b3-4d6a-bdbb-c0a3f4360a51**.

## Definições de política personalizada 
Utilize a **Política de configuração personalizada do Windows Phone** do Microsoft Intune para implementar as definições OMA-URI (Open Mobile Alliance Uniform Resource Identifier) que podem ser utilizadas para controlar as funcionalidades nos dispositivos **Windows Phone 8.1**. Tratam-se de definições padrão utilizadas por inúmeros fabricantes de dispositivos móveis para controlar as funcionalidades dos dispositivos.

Esta capacidade destina-se a permitir a implementação de definições do Windows Phone que não são configuráveis com uma política de configuração geral do Intune. Para informações sobre as definições que pode configurar com estas políticas, consulte [Gerir as definições e funcionalidades nos seus dispositivos com as políticas do Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).

Para obter ajuda sobre como criar configurações de URI OMA para dispositivos Windows Phone, consulte a [Documentação do protocolo de MDM do Windows Phone 8.1](http://technet.microsoft.com/library/dn499787.aspx).

### Definições gerais

|Nome da definição|Detalhes|
|----------------|--------------------|
|**Nome**|Introduza um nome exclusivo para a política para o ajudar a identificá-la na consola do Intune.|
|**Descrição**|Indique uma descrição geral da política e outras informações relevantes que poderão ajudá-lo a localizá-la.|

### Definições OMA-URI

Na secção **Definições OMA-URI**, clique em **Adicionar** para adicionar uma definição. Também pode editar ou eliminar definições existentes.

Na caixa de diálogo **Adicionar ou Editar Definição OMA-URI**, especifique as seguintes informações:

|Nome da definição|Detalhes|
    |--------|--------------------|
    |**Nome da definição**|Introduza um nome exclusivo para a definição OMA-URI para o ajudar a identificá-la na lista de definições.|
    |**Descrição da definição**|Indique uma descrição geral da definição e outras informações relevantes para o ajudar a localizá-la.|
    |**Tipo de dados**|Selecione o tipo de data em que especificará esta definição OMA-URI. Escolha entre:<br /><br />-   **Cadeia**<br />-   **Cadeia (XML)**<br />-   **Data e Hora**<br />-   **Número inteiro**<br />-   **Vírgula flutuante**<br />-   **Booleano**|
    |**OMA-URI (Sensível às Maiúsculas e Minúsculas)**|Especifique o OMA-URI para o qual pretende fornecer uma definição.|
    |**Valor**|Indique o valor a associar ao OMA-URI especificado anteriormente.|

### Consulte também
[Gerir definições e funcionalidades nos seus dispositivos com as políticas do Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)



<!--HONumber=May16_HO2-->


