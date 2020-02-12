---
title: Configure Microsoft Launcher para Android Enterprise com Intune
titleSuffix: ''
description: Utilize as políticas de configuração Intune com o Microsoft Launcher.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: priyar
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b0145a17434d8b309806f468bf066d54ae117144
ms.sourcegitcommit: 1aaff35fddb3d06458d739968d28971fed0bb2ba
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/12/2020
ms.locfileid: "77155365"
---
# <a name="configure-microsoft-launcher"></a>Configurar o Microsoft Launcher

O Microsoft Launcher é uma aplicação Android que permite aos utilizadores personalizar o seu telemóvel, manter-se organizado em movimento e transferir de trabalhar do seu telemóvel para o seu PC. 

Em dispositivos totalmente geridos pelo Android Enterprise, o Launcher permite que os administradores de TI da empresa personalizem ecrãs domésticos geridos do dispositivo, selecionando as posições de papel de parede, apps e ícones. Isto normaliza a aparência e a sensação de todos os dispositivos Android geridos em diferentes dispositivos OEM e versões do sistema. 

## <a name="how-to-configure-the-microsoft-launcher-app"></a>Como configurar a aplicação Microsoft Launcher 

Navegue para o [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) e selecione **Apps** > políticas de **configuração**de apps . Adicione uma política de configuração para **dispositivos geridos** que executem **o Android** e escolha o **Microsoft Launcher** como aplicação associada. Clique nas definições de **Configuração** para configurar as diferentes definições disponíveis do Microsoft Launcher. 

## <a name="choosing-a-configuration-settings-format"></a>Escolher um formato de configuração 

Existem dois métodos que pode utilizar para definir as definições de configuração para o Microsoft Launcher: 

- O designer de **configuração** permite-lhe configurar as definições com um UI fácil de usar que lhe permite alternar as funcionalidades dentro ou fora e definir valores. Neste método, existem algumas teclas de configuração desativadas com o tipo de valor BundleArray. Estas teclas de configuração só podem ser configuradas através da introdução de dados JSON. 

- Os **dados da JSON** permitem definir todas as chaves de configuração possíveis utilizando um script JSON. 

Se adicionar propriedades ao Designer de **Configuração,** pode converter automaticamente estas propriedades para JSON selecionando **os dados do Enter JSON** a partir da lista de definições de **configuração** como mostrado abaixo.

   ![Formato de configuração de configurações - Use designer de configuração](./media/configure-microsoft-launcher/configure-microsoft-launcher-01.png)

## <a name="using-configuration-designer"></a>Usando o Designer de Configuração

O designer de configuração permite-lhe selecionar configurações pré-povoadas e os seus valores associados.

   ![Formato de configuração - Introduza os dados da JSON](./media/configure-microsoft-launcher/configure-microsoft-launcher-02.png)

A tabela que se segue lista as teclas de configuração disponíveis do Microsoft Launcher, tipos de valor, valores predefinidos e descrições. A descrição fornece o comportamento esperado do dispositivo com base nos valores selecionados. As teclas de configuração que são desativadas no Designer de Configuração não estão listadas na tabela.

|    Chave de Configuração    |    Tipo de valor    |    Valor predefinido    |    Descrição     |
|---------------------------------------------------|------------------|---------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    Tipo de inscrição    |    Cadeia     |    Predefinição    |    Permite-lhe definir o tipo de inscrição a que esta política deve aplicar-se. Atualmente, o valor **Default** refere-se a **CorporateOwnedBuisnessOnly**. Não existem outros tipos de matrículas suportados neste momento.        Nome-chave JSON: management_mode_key        |
|    Mudança permitida por ordem de aplicação de tela inicial    |    Booleano    |    Verdadeiro    |    Permite especificar se a definição de Pedido de **Aplicações** de Ecrã Inicial pode ser alterada pelo utilizador final.<ul><li>Se definido para **True**, a ordem da aplicação definida na política só será aplicada para a implementação inicial. Posteriormente, a política não será aplicada para respeitar quaisquer alterações que o utilizador possa ter feito.</li><li>Se definido para **Falso,** a ordem da aplicação será executada em cada sincronização.</li></ul><br>**Nota:** A aplicação de ecrã inicial só pode ser configurada através do editor da JSON.<br><br>Nome-chave JSON:<br>`com.microsoft.launcher.HomeScreen.AppOrder.UserChangeAllowed`    |
|    Definir tamanho da grelha    |    Cadeia    |    Automático    |    Permite-lhe definir o tamanho da grelha para as aplicações serem posicionadas no ecrã principal. Pode definir o número de linhas e colunas de aplicações para definir o tamanho da grelha no seguinte formato: `columns;rows`. Se definir o tamanho da grelha, o número máximo de aplicações que serão mostradas em linha no ecrã principal seria o número de linhas que definiu e o número máximo de aplicações que serão mostradas numa coluna no ecrã principal seria o número de colunas que definiu.<br><br>        Nome-chave JSON:<br>`com.microsoft.launcher.HomeScreen.GridSize`    |
|    Definir papel de parede do dispositivo    |    Cadeia    |    Null    |    Permite-lhe definir um papel de parede à sua escolha, entrando no URL da imagem que pretende definir como papel de parede.<br><br>Nome-chave JSON:<br>`com.microsoft.launcher.Wallpaper.URL`    |
|    Definir mudança de utilizador de papel de parede de dispositivo permitido    |    Booleano    |    Verdadeiro    |    Permite especificar se a definição de papel de parede do dispositivo definido pode ser alterada pelo utilizador final.<ul><li>Se for definido como **Verdadeiro,** o papel de parede da política só será aplicado para a implantação inicial. Posteriormente, a política não será aplicada para respeitar quaisquer alterações que o utilizador possa ter feito.</li><li>Se definido para **Falso,** o papel de parede será aplicado em cada sincronização.</li></ul><br>Nome-chave JSON:<br>`com.microsoft.launcher.Wallpaper.URL.UserChangeAllowed`        |
|    Alimentação ativa    |    Booleano    |    Verdadeiro    |    Permite ativar o feed do lançador do dispositivo quando o utilizador passa para a direita no ecrã principal.<ul><li>Se for definido para **True,** o feed será ativado.</li><li>Se for definido como **Falso,** o feed será desativado.</li></ul><br>Nome-chave JSON:<br>`com.microsoft.launcher.Feed.Enabled`    |
|    Alimentação ativar a mudança de utilizador permitida    |    Booleano    |    Verdadeiro    |     Permite especificar se a definição de **Feed Enable** pode ser alterada pelo utilizador final.<ul><li>Se definido para **True,** o feed só será aplicado para a implementação inicial. Posteriormente, a política não será aplicada para respeitar quaisquer alterações que o utilizador possa ter feito.</li><li>Se definido para **Falso,** o feed será aplicado em cada sincronização.</li></ul><br>Nome-chave JSON:`com.microsoft.launcher.Feed.Enabled.UserChangeAllowed`    |

## <a name="enter-json-data"></a>Insira dados da JSON

Introduza os dados da JSON para configurar todas as definições disponíveis para o Microsoft Launcher, bem como as definições desativadas no Designer de **Configuração,** como mostrado abaixo.

   ![Designer de Configuração - Dados JSON](./media/configure-microsoft-launcher/configure-microsoft-launcher-03.png)

Além da lista de configurações configuráveis listadas na tabela 'Configuração Designer' (acima), a tabela seguinte fornece as teclas de configuração que só pode configurar através de dados jSON.

|    Chave de Configuração    |    Tipo de valor    |    Valor predefinido    |    Descrição     |
|----------------------------------------------------------------------------------------------------|-------------------|-------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    Definir aplicações listadas por permitir<br>Tecla JSON:`com.microsoft.launcher.HomeScreen.Applications`    |    BundleArray    | Ver: [Definir aplicações listadas por permitir](configure-microsoft-launcher.md#set-allow-listed-applications)</sup>    |    Permite definir o conjunto de aplicações visíveis no ecrã principal entre as aplicações instaladas no dispositivo. Pode definir as aplicações ao introduzir o nome do pacote de aplicações das aplicações que gostaria de tornar visíveis, por exemplo, `com.android.settings` tornariaas as definições acessíveis no ecrã principal. As aplicações que permite listar nesta secção já devem ser instaladas no dispositivo para serem visíveis no ecrã principal.<p>Propriedades:<ul><li>**Pacote:** O nome do pacote de candidatura</li><li>**Classe:** A atividade da aplicação, que é específica para uma determinada página de aplicações. Utilizaria a página de aplicações padrão se este valor estiver vazio.</li></ul>      |
|    Ordem de aplicação de tela principal<br>Tecla JSON: `com.microsoft.launcher.HomeScreen.AppOrder`    |    BundleArray    |    Ver: Pedido de [aplicação de ecrã inicial](configure-microsoft-launcher.md#home-screen-app-order)      |    Permite especificar a encomenda da aplicação no ecrã principal.<p>Propriedades:<br><ul><li>**Tipo:** O único tipo suportado é `application`.</li><li>**Posição:** A ranhura do ícone da aplicação no ecrã principal. Isto começa a partir da posição 1 na parte superior esquerda, e vai da esquerda para a direita, de cima para baixo.</li><li>**Pacote:** O nome do pacote de candidatura.</li><li>**Classe:** A atividade da aplicação, que é específica para uma determinada página de aplicações. A página de aplicações padrão será usada se este valor estiver vazio.</li></ul>    |

### <a name="set-allow-listed-applications"></a>Definir aplicações listadas por permitir

```JSON
{
    "key": "com.microsoft.launcher.HomeScreen.Applications",
    "valueBundleArray": 
    [
        {
            "managedProperty": [
                {
                    "key": "package",
                    "valueString": ""
                },
                {
                    "key": "class",
                    "valueString": ""
                }
            ]
        }
    ]
}
```

### <a name="home-screen-app-order"></a>Ordem de aplicativo de tela principal

```JSON
{
    "key": "com.microsoft.launcher.HomeScreen.AppOrder",
    "valueBundleArray": 
    [
        {
            "managedProperty": [
                {
                    "key": "type",
                    "valueString": "application"
                },
                {
                    "key": "position",
                    "valueInteger": 0
                },
                {
                    "key": "package",
                    "valueString": ""
                },
                {
                    "key": "class",
                    "valueString": ""
                }
            ]
        }
    ]
}
```

Segue-se um exemplo de script JSON com todas as chaves de configuração disponíveis incluídas:

```JSON
{
    "kind": "androidenterprise#managedConfiguration", 
    "productId": "app:com.microsoft.launcher", 
    "managedProperty": [
        {
            "key": "management_mode_key", 
            "valueString": "Default"
        }, 
        {
            "key": "com.microsoft.launcher.Feed.Enable.UserChangeAllowed", 
            "valueBool": false
        }, 
        {
            "key": "com.microsoft.launcher.Feed.Enable", 
            "valueBool": true
        }, 
        {
            "key": "com.microsoft.launcher.Wallpaper.Url.UserChangeAllowed", 
            "valueBool": false
        }, 
        {
            "key": "com.microsoft.launcher.Wallpaper.Url", 
            "valueBool": "http://www.contoso.com/wallpaper.png"
        }, 
        {
            "key": "com.microsoft.launcher.HomeScreen.GridSize", 
            "valueString": "5;5"
        }, 
        {
            "key": "com.microsoft.launcher.HomeScreen.Applications", 
            "valueBundleArray": [
                {
                    "managedProperty": [
                        {
                            "key": "package", 
                            "valueString": "com.ups.mobile.android"
                        }, 
                        {
                            "key": "class", 
                            "valueString": ""
                        }
                    ]
                }, 
                {
                    "managedProperty": [
                        {
                            "key": "package", 
                            "valueString": "com.microsoft.teams"
                        }, 
                        {
                            "key": "class", 
                            "valueString": ""
                        }
                    ]
                }, 
                {
                    "managedProperty": [
                        {
                            "key": "package", 
                            "valueString": "com.microsoft.bing"
                        }, 
                        {
                            "key": "class", 
                            "valueString": ""
                        }
                    ]
                }
            ]
        }, 
        {
            "key": "com.microsoft.launcher.HomeScreen.AppOrder.UserChangeAllowed", 
            "valueBool": false
        }, 
        {
            "key": "com.microsoft.launcher.HomeScreen.AppOrder", 
            "valueBundleArray": [
                {
                    "managedProperty": [
                        {
                            "key": "type", 
                            "valueString": "application"
                        }, 
                        {
                            "key": "position", 
                            "valueInteger": 17
                        }, 
                        {
                            "key": "package", 
                            "valueString": "com.ups.mobile.android"
                        }, 
                        {
                            "key": "class", 
                            "valueString": ""
                        }
                    ]
                }, 
                {
                    "managedProperty": [
                        {
                            "key": "type", 
                            "valueString": "application"
                        }, 
                        {
                            "key": "position", 
                            "valueInteger": 18
                        }, 
                        {
                            "key": "package", 
                            "valueString": "com.microsoft.teams"
                        }, 
                        {
                            "key": "class", 
                            "valueString": ""
                        }
                    ]
                }, 
                {
                    "managedProperty": [
                        {
                            "key": "type", 
                            "valueString": "application"
                        }, 
                        {
                            "key": "position", 
                            "valueInteger": 19
                        }, 
                        {
                            "key": "package", 
                            "valueString": "com.microsoft.bing"
                        }, 
                        {
                            "key": "class", 
                            "valueString": ""
                        }
                    ]
                }
            ]
        }
    ]
}
```

## <a name="next-steps"></a>Próximos passos

- Para obter mais informações sobre dispositivos geridos pelo Android Enterprise, consulte [a inscrição intune do Android Enterprise na sua plena gestão de dispositivos.](../enrollment/android-fully-managed-enroll.md)
