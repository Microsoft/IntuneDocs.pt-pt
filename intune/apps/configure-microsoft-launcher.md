---
title: Configurar o iniciador da Microsoft para Android Enterprise com o Intune
titleSuffix: ''
description: Use as políticas de configuração do Intune com o iniciador Microsoft.
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
ms.openlocfilehash: 1dc2e2ce7e19933accdb1063ccacf99fa3f54b09
ms.sourcegitcommit: 73b362173929f59e9df57e54e76d19834f155433
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/27/2019
ms.locfileid: "74563957"
---
# <a name="configure-microsoft-launcher"></a>Configurar o Microsoft Launcher

O Microsoft Launcher é um aplicativo Android que permite que os usuários personalizem seu telefone, permaneçam organizados em trânsito e façam a transferência do trabalho de seu telefone para seu PC. 

Em dispositivos Android Enterprise totalmente gerenciados, o iniciador permite que os administradores de ti corporativos personalizem as telas home do dispositivo gerenciado selecionando as posições de papel de parede, aplicativos e ícone. Isso padroniza a aparência de todos os dispositivos Android gerenciados em diferentes dispositivos OEM e versões do sistema. 

## <a name="how-to-configure-the-microsoft-managed-home-screen-app"></a>Como configurar o aplicativo de tela inicial gerenciado pela Microsoft 

Navegue até o [centro de administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) e selecione **aplicativos** > **políticas de configuração de aplicativo**. Adicione uma política de configuração para **dispositivos gerenciados** que executam o **Android** e escolha **Microsoft Launcher** como o aplicativo associado. Clique em **definições de configuração** para definir as diferentes configurações de tela inicial gerenciada disponíveis. 

## <a name="choosing-a-configuration-settings-format"></a>Escolhendo um formato de definições de configuração 

Há dois métodos que você pode usar para definir definições de configuração para a tela inicial gerenciada: 

- O **Designer de configuração** permite que você defina as configurações com uma interface de usuário fácil de usar que permite ativar ou desativar recursos e definir valores. Nesse método, há algumas chaves de configuração desabilitadas com o tipo de valor BundleArray. Essas chaves de configuração só podem ser configuradas digitando dados JSON. 

- Os **dados JSON** permitem que você defina todas as chaves de configuração possíveis usando um script JSON. 

Se você adicionar propriedades com o **Designer de configuração**, poderá converter automaticamente essas propriedades em JSON selecionando **inserir dados JSON** na lista suspensa formato de definições de **configuração** , conforme mostrado abaixo.

   ![Formato das definições de configuração – usar o designer de configuração](./media/configure-microsoft-launcher/configure-microsoft-launcher-01.png)

## <a name="using-configuration-designer"></a>Usando o designer de configuração

O designer de configuração permite que você selecione configurações preenchidas previamente e seus valores associados.

   ![Formato de definições de configuração – inserir dados JSON](./media/configure-microsoft-launcher/configure-microsoft-launcher-02.png)

A tabela a seguir lista as chaves de configuração disponíveis do Microsoft Launcher, tipos de valor, valores padrão e descrições. A descrição fornece o comportamento de dispositivo esperado com base nos valores selecionados. As chaves de configuração que estão desabilitadas no designer de configuração não estão listadas na tabela.

|    Chave de Configuração    |    Tipo de valor    |    Valor predefinido    |    Description     |
|---------------------------------------------------|------------------|---------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    Tipo de registro    |    Cadeia     |    Os    |    Permite que você defina o tipo de registro ao qual essa política deve ser aplicada. Atualmente, o valor **padrão** refere-se a **CorporateOwnedBuisnessOnly**. Não há outros tipos de registro com suporte no momento.        Nome da chave JSON: management_mode_key        |
|    Alteração de usuário da ordem do aplicativo de tela inicial permitida    |    Booleano    |    Verdadeiro    |    Permite que você especifique se a configuração de **pedido do aplicativo de tela inicial** pode ser alterada pelo usuário final.<ul><li>Se definido como **true**, a ordem do aplicativo definida na política será imposta somente para a implantação inicial. Subsequentemente, a política não será imposta para respeitar as alterações que o usuário possa ter feito.</li><li>Se definido como **false**, a ordem do aplicativo será imposta a cada sincronização.</li></ul><br>**Observação:** A ordem do aplicativo de tela inicial só pode ser configurada por meio do editor de JSON.<br><br>Nome da chave JSON:<br>`com.microsoft.launcher.HomeScreen.AppOrder.UserChangeAllowed`    |
|    Definir tamanho da grade    |    Cadeia    |    Automático    |    Permite definir o tamanho da grade para que os aplicativos sejam posicionados na tela inicial. Você pode definir o número de linhas e colunas do aplicativo para definir o tamanho da grade no seguinte formato: `columns;rows`. Se você definir o tamanho da grade, o número máximo de aplicativos que serão mostrados em uma linha na tela inicial será o número de linhas que você definiu e o número máximo de aplicativos que serão mostrados em uma coluna na tela inicial seria o número de colunas que você definiu.<br><br>        Nome da chave JSON:<br>`com.microsoft.launcher.HomeScreen.GridSize`    |
|    Definir papel de parede do dispositivo    |    Cadeia    |    nulo    |    Permite definir um papel de parede de sua escolha digitando a URL da imagem que você deseja definir como um papel de parede.<br><br>Nome da chave JSON:<br>`com.microsoft.launcher.Wallpaper.URL`    |
|    Definir permissão de alteração de usuário de papel de parede de dispositivo    |    Booleano    |    Verdadeiro    |    Permite especificar se a configuração definir papel de parede do dispositivo pode ser alterada pelo usuário final.<ul><li>Se definido como **true**, o papel de parede na política só será imposto para a implantação inicial. Subsequentemente, a política não será imposta para respeitar as alterações que o usuário possa ter feito.</li><li>Se definido como **false**, o papel de parede será aplicado a cada sincronização.</li></ul><br>Nome da chave JSON:<br>`com.microsoft.launcher.Wallpaper.URL.UserChangeAllowed`        |
|    Habilitar feed    |    Booleano    |    Verdadeiro    |    Permite habilitar o feed do iniciador no dispositivo quando o usuário passa o dedo para a direita na tela inicial.<ul><li>Se definido como **true**, o feed será habilitado.</li><li>Se definido como **false**, o feed será desabilitado.</li></ul><br>Nome da chave JSON:<br>`com.microsoft.launcher.Feed.Enabled`    |
|    Ativação do feed habilitar alteração do usuário    |    Booleano    |    Verdadeiro    |     Permite que você especifique se a configuração **habilitar feed** pode ser alterada pelo usuário final.<ul><li>Se definido como **true**, o feed só será imposto para a implantação inicial. Subsequentemente, a política não será imposta para respeitar as alterações que o usuário possa ter feito.</li><li>Se definido como **false**, o feed será aplicado a cada sincronização.</li></ul><br>Nome da chave JSON:`com.microsoft.launcher.Feed.Enabled.UserChangeAllowed`    |

## <a name="enter-json-data"></a>Inserir dados JSON

Insira dados JSON para definir todas as configurações disponíveis para o Microsoft Launcher, bem como as configurações desabilitadas no **Designer de configuração**, conforme mostrado abaixo.

   ![Designer de configuração-dados JSON](./media/configure-microsoft-launcher/configure-microsoft-launcher-03.png)

Além da lista de configurações configuráveis listadas na tabela do designer de configuração (acima), a tabela a seguir fornece as chaves de configuração que você só pode configurar por meio de dados JSON.

|    Chave de Configuração    |    Tipo de valor    |    Valor predefinido    |    Description     |
|----------------------------------------------------------------------------------------------------|-------------------|-------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    Definir os aplicativos listados como permitidos<br>Chave JSON:`com.microsoft.launcher.HomeScreen.Applications`    |    BundleArray    | Consulte: [set Allow-listed applications](configure-microsoft-launcher.md#set-allow-listed-applications)</sup>    |    Permite que você defina o conjunto de aplicativos visíveis na tela inicial de entre os aplicativos instalados no dispositivo. Você pode definir os aplicativos inserindo o nome do pacote de aplicativo dos aplicativos que você gostaria de tornar visíveis, por exemplo, `com.android.settings` tornaria as configurações acessíveis na tela inicial. Os aplicativos que você permite-listar nesta seção já devem estar instalados no dispositivo para que fiquem visíveis na tela inicial.<p>Properties<ul><li>**Pacote:** O nome do pacote de aplicativos</li><li>**Classe:** A atividade do aplicativo, que é específica para uma determinada página de aplicativo. Ele usará a página de aplicativo padrão se esse valor estiver vazio.</li></ul>      |
|    Ordem do aplicativo de tela inicial<br>Chave JSON: `com.microsoft.launcher.HomeScreen.AppOrder`    |    BundleArray    |    Consulte: [ordem do aplicativo de tela inicial](configure-microsoft-launcher.md#home-screen-app-order)      |    Permite que você especifique a ordem do aplicativo na tela inicial.<p>Properties<br><ul><li>**Tipo:** O único tipo com suporte é `application`.</li><li>**Posição:** O ícone do aplicativo slot na tela inicial. Isso começa na posição 1 na parte superior esquerda e vai da esquerda para a direita, de cima para baixo.</li><li>**Pacote:** O nome do pacote de aplicativos.</li><li>**Classe:** A atividade do aplicativo, que é específica para uma determinada página de aplicativo. A página de aplicativo padrão será usada se esse valor estiver vazio.</li></ul>    |

### <a name="set-allow-listed-applications"></a>Definir os aplicativos listados como permitidos

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

### <a name="home-screen-app-order"></a>Ordem do aplicativo de tela inicial

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

Este é um exemplo de script JSON com todas as chaves de configuração disponíveis incluídas:

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

- Para obter mais informações sobre dispositivos Android Enterprise totalmente gerenciados, consulte [Configurar o registro do Intune do Android Enterprise gerenciar totalmente os dispositivos](../enrollment/android-fully-managed-enroll.md).
