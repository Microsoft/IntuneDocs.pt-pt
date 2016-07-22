---
title: "Definições de política do Mac OS X | Microsoft Intune"
description: 
keywords: 
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 98b2f19b-bee8-42d7-a215-a716d56a25a3
ms.reviewer: jeffgilb
ms.suite: ems
ms.sourcegitcommit: 8c1f4f209c5ec704290882b8f6f71e0b1b01d21c
ms.openlocfilehash: bbbb666fdc34a82d247d760d156d48c5ac72374c


---

# Definições de política de configuração do Mac OS X no Microsoft Intune

## Definições de política de configuração geral

Utilize a **política de configuração geral para Mac OS X** do Microsoft Intune para configurar definições para:

-   **Definições de segurança do dispositivo** – Escolha entre uma lista de predefinições que permitem controlar uma série de funcionalidades e a funcionalidade do dispositivo.

-   **Aplicações compatíveis e não compatíveis** - Especifique uma lista de aplicações que são compatíveis ou não compatíveis na sua empresa. O Relatório de Aplicações Não Conformes pode ser utilizado para ver a conformidade das aplicações especificadas na lista comparativamente às aplicações instaladas pelos utilizadores (mas não pode bloquear a instalação da aplicação).

Se a definição que procura não for apresentada nesta lista, poderá conseguir criá-la utilizando uma política personalizada de Mac OS X que permita importar as definições que criou com a ferramenta Apple Configurator. Para mais informações, consulte **Definições de política personalizada** mais adiante neste tópico.

### Definições de palavra-passe

|Nome da definição|Detalhes|
|----------------|---------------|
|**Pedir uma palavra-passe para desbloquear dispositivos**|Especifica se o utilizador tem de utilizar uma palavra-passe para aceder ao seu computador Mac. **Importante:** Ao contrário dos dispositivos iOS, nos dispositivos Mac OS X, o utilizador não é imediatamente notificado para atualizar a palavra-passe para estar em conformidade com esta definição.|
|**Tipo obrigatório de palavra-passe**|Especifica se a palavra-passe utilizada só pode ser Numérica ou se tem de ser **Alfanumérica** (conter letras e números). **Importante:** Esta definição só é suportada na versão 10.10.3 do Mac OS X e posterior.|
|**Número de carateres complexos necessários na palavra-passe**|Especifica o número de carateres complexos necessários na palavra-passe (de **0** - **4**).<br /><br />Um caráter complexo é um símbolo, tal como "**?**"|
|**Comprimento mínimo da palavra-passe**|Especifica o comprimento mínimo para a palavra-passe (entre **4** e **14** carateres).|
|**Permitir palavras-passe simples**|Permite a utilização de palavras-passe simples, tal como "**0000**" ou "**1234**".|
|**Minutos de inatividade antes da palavra-passe ser exigida**|Especifica o período de tempo durante o qual o computador tem de estar inativo antes de ser exigida uma palavra-passe para o desbloquear.|
|**Expiração da Palavra-passe (dias)**|Especifica o número de dias que decorrem antes de o utilizador ter de alterar a palavra-passe (de **1** - **255** dias).|
|**Memorizar histórico de palavras-passe**|Esta definição é utilizada para impedir que o utilizador utilize uma palavra-passe utilizada anteriormente. Quando for definida, também pode definir **Impedir a reutilização de palavras-passe anteriores** para especificar o número de palavras-passe utilizadas anteriormente que não podem ser reutilizadas (de **1** - **24**).|
|**Minutos de inatividade antes de a proteção de ecrã ser ativada**|Especifica o período de tempo durante o qual o computador tem de estar inativo antes de a proteção de ecrã ser ativada.|

### Definições para aplicações compatíveis e não compatíveis
Na lista Aplicações **Conformes e &amp;Não Conformes para Mac OS X**, ative **Definições geridas para dispositivos** e, em seguida, especifique uma lista de aplicações conformes e não conformes com as informações seguintes:

> [!NOTE]
> Uma única política só pode conter uma lista de aplicações compatíveis ou uma lista de aplicações não compatíveis. Não é possível especificar ambas na mesma política.
> 
> O Intune permite comunicar dispositivos com aplicações não conformes. Não bloqueia a instalação nem remove as aplicações não conformes.

|Nome da definição|Detalhes|
|----------------|---------------|
|**Comunicar não conformidade quando os utilizadores instalam as aplicações listadas**|Apresenta uma lista das aplicações Mac OS X que os utilizadores não têm permissão para instalar. Se os utilizadores instalarem qualquer uma destas aplicações, estas serão comunicadas nos **Relatórios de Aplicações Não Conformes**.|
|**Comunicar não conformidade quando os utilizadores instalam aplicações não listadas**|Apresenta uma lista das aplicações Mac OS X que os utilizadores têm permissão para instalar. Se os utilizadores instalarem quaisquer outras aplicações, estas serão comunicadas nos **Relatórios de Aplicações Não Conformes**.|
|**Adicionar**|Adiciona uma aplicação à lista selecionada. Especifique um nome à sua escolha, o publicador da aplicação (opcional) e o ID do pacote da aplicação. **Sugestão:** Para localizar o ID do pacote de uma aplicação, utilize os passos seguintes num computador Mac que tenha a aplicação instalada:<ol><li>Abra a pasta na qual a aplicação está instalada (por exemplo, **/Applications**)</li><li>Selecione o grupo *&lt;Nome da Aplicação&gt;***.app** e escolha **Mostrar Conteúdo do Pacote**</li><li>Abra o ficheiro **Info.plist** </li><li>Verifique o valor associado à chave **CFBundleIdentifier**</li></ol>O formato do ID do pacote é **com.contoso.appname**|
|**Importar Aplicações**|Importa uma lista de aplicações especificadas num ficheiro de valores separados por vírgulas. Utilize o formato, o nome da aplicação, o fabricante e o ID do pacote de aplicações no ficheiro.|
|**Editar**|Permite-lhe editar o nome, o fabricante e o ID do pacote de aplicações da aplicação selecionada.|
|**Eliminar**|Elimina a aplicação selecionada da lista.|
> [!TIP]
> Para obter mais informações sobre relatórios do Intune, veja [Compreender as operações do Microsoft Intune através da utilização de relatórios](understand-microsoft-intune-operations-by-using-reports.md).

> [!IMPORTANT]
> Quando um dispositivo Mac OS X está no modo de Suspensão, não é possível entregar ou inventariar políticas e perfis. Como resultado, a consola do Intune pode apresentar temporariamente o estado **Definições de política em erro** até à próxima vez que o dispositivo sair do modo de Suspensão.

### Monitorizar aplicações compatíveis e não compatíveis
Utilize os **Relatórios de Aplicações Não Conformes** para ver a conformidade das aplicações especificadas.

#### Para executar o relatório

1.  Na [consola de administração do Microsoft Intune](https://manage.microsoft.com), clique em **Relatórios** &gt; **Relatórios de Aplicações Não Conformes**.

2.  Selecione os grupos de dispositivos que pretende verificar, se pretende verificar as aplicações compatíveis, as aplicações não compatíveis ou ambas e, em seguida, clique em **Ver Relatório**.

## Definições de política personalizada do Mac OS X no Microsoft Intune
Utilize a **política de configuração personalizada para Mac OS X** do Microsoft Intune para implementar definições criadas com a [ferramenta Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) em dispositivos Mac OS X. Esta ferramenta permite criar muitas definições que controlam o funcionamento destes dispositivos e exportá-las para um perfil de configuração. Em seguida, pode importar este perfil de configuração para uma política personalizada do Mac OS X do Intune e implementar as definições em utilizadores e dispositivos da sua organização.

Esta capacidade destina-se a permitir a implementação de definições do Mac OS X que não são configuráveis com a política de configuração geral do Mac OS X do Intune.

### Pré-requisitos
Antes de começar, tem de ter instalado o Apple Configurator e criar um ficheiro de configuração com as definições que pretende implementar nos utilizadores ou dispositivos. Pode transferir e obter informações sobre o Apple Configurator na [Mac App Store](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12)

> [!NOTE]
> O Intune não comunica a conformidade de definições individuais numa política personalizada do Mac OS X. No entanto, a conformidade geral das políticas é comunicada.

### Definições gerais

|Nome da definição|Detalhes|
    |----------------|--------------------|
    |**Nome**|Introduza um nome exclusivo para a política personalizada do Mac OS X para o ajudar a identificá-la na consola do Intune.|
    |**Descrição**|Indique uma descrição geral da política personalizada do Mac OS X e outras informações relevantes que o ajudem a localizá-la.|


### Definições personalizadas

|Nome da definição|Detalhes|
    |----------------|--------------------|
    |**Nome do perfil de configuração personalizado (apresentado aos utilizadores)**|Indique um nome para a política tal como será apresentado no dispositivo e nos relatórios de políticas do Intune.|
    |**Ficheiro de perfil de configuração**|Clique em **Importar**e, em seguida, navegue até ao perfil de configuração que criou com o Apple Configurator. **Sugestão:** veja **Criar um ficheiro de perfil de configuração** neste tópico para obter ajuda na criação do perfil de configuração.|
    |**Detalhes do perfil de configuração**|Apresenta o código XML do perfil de configuração que importou.|



### Como criar um ficheiro de perfil de configuração
Pode criar o ficheiro de perfil de configuração utilizado pela política personalizada de duas formas:

-   Exporte o ficheiro (com a extensão **.mobileconfig**) da ferramenta Apple Configurator.

-   Crie o ficheiro utilizando o esquema apropriado a partir da página [Apple Configuration Profile Key Reference (Referência de Chaves de Perfis de Configuração da Apple)](https://developer.apple.com/library/ios/featuredarticles/iPhoneConfigurationProfileRef/Introduction/Introduction.html).


> [!IMPORTANT]
> Quando um dispositivo Mac OS X está no modo de Suspensão, não é possível entregar ou inventariar políticas e perfis. Como resultado, a consola do Intune pode apresentar temporariamente o estado **Definições de política em erro** até à próxima vez que o dispositivo sair do modo de Suspensão.

### Consulte também
[Gerir definições e funcionalidades nos seus dispositivos com as políticas do Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)




<!--HONumber=Jun16_HO4-->


