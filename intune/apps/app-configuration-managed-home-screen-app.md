---
title: Configure a aplicação de ecrã doméstico gerido pela Microsoft
titleSuffix: Microsoft Intune
description: Saiba como configurar a aplicação de Ecrã Home Gerido pela Microsoft.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/27/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 865c7f03-f525-4dfa-b3a8-d088a9106502
ms.reviewer: chmaguir
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4a9372a67dc0f45e256c3eba9b816db866e23998
ms.sourcegitcommit: 045ca42cad6f86024af9a38a380535f42a6b4bef
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/28/2020
ms.locfileid: "77781808"
---
# <a name="configure-the-microsoft-managed-home-screen-app-for-android-enterprise"></a>Configure o aplicativo de ecrã home gerido pela Microsoft para Android Enterprise

O Managed Home Screen é a aplicação utilizada para dispositivos dedicados ao Android Enterprise, de propriedade corporativa, matriculados via Intune e em funcionamento em modo quiosque multi-aplicações. Para estes dispositivos, o Ecrã Home Gerido funciona como o lançador para outras aplicações aprovadas para funcionar em cima dele. O Managed Home Screen fornece aos administradores de TI a capacidade de personalizar os seus dispositivos e restringir as capacidades a que o utilizador final pode aceder. 

## <a name="when-to-configure-the-microsoft-managed-home-screen-app"></a>Quando configurar a aplicação de Ecrã Home Gerido pela Microsoft

Normalmente, se as definições estiverem disponíveis através da configuração do Dispositivo, configure as definições. Ao fazê-lo, poupar-lhe-á tempo, minimizará os erros e dar-lhe-á uma melhor experiência de suporte intune. No entanto, algumas das definições de Ecrã Home Gerido estão atualmente disponíveis apenas através do painel de definição de **aplicações** na consola Intune. Utilize este documento para aprender a configurar as diferentes definições, utilizando o designer de configuração ou um script JSON. 

> [!NOTE]
> Atualmente é possível, e aconselhável, definir aplicações listadas por permitir e ligações web fixas através de **Apps** e **configuração do Dispositivo**. Para obter a lista completa de definições disponíveis na **configuração do Dispositivo** que impactam o Ecrã Home Gerido, consulte [as definições do dispositivo dedicado](../configuration/device-restrictions-android-for-work.md#dedicated-device-settings).  

Em primeiro lugar, navegue para o [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) e selecione **Apps** > políticas de **configuração**de apps . Adicione uma política de configuração para **dispositivos geridos** que executem **o Android** e escolha o Ecrã **Home Gerido** como aplicação associada. Clique nas definições de **Configuração** para configurar as diferentes definições de Ecrã Home Gerido disponíveis. 

## <a name="choosing-a-configuration-settings-format"></a>Escolher um formato de configuração

Existem dois métodos que pode utilizar para definir definições de configuração para ecrã principal gerido:

- O designer de **configuração** permite-lhe configurar as definições com um UI fácil de usar que lhe permite alternar as funcionalidades dentro ou fora e definir valores. Neste método, existem algumas teclas de configuração desativadas com tipo de valor `BundleArray`. Estas teclas de configuração só podem ser configuradas através da introdução de dados JSON. 
- Os **dados da JSON** permitem definir todas as chaves de configuração possíveis utilizando um script JSON. 

Se adicionar propriedades ao Designer de Configuração, pode converter automaticamente estas propriedades para JSON selecionando **dados do Enter JSON** a partir da definição de configuração de **definição.**

![Screenshot das opções de formato de configuração de configuração](./media/app-configuration-managed-home-screen-app/app-configuration-managed-home-screen-app_01.png)

## <a name="using-configuration-designer"></a>Usando o Designer de Configuração

O designer de configuração permite-lhe selecionar configurações pré-povoadas e os seus valores associados. 

![Screenshot de definições de configuração adicionadas](./media/app-configuration-managed-home-screen-app/app-configuration-managed-home-screen-app_02.png)

A tabela seguinte lista as teclas de configuração disponíveis do Ecrã Home Gerido, tipos de valor, valores predefinidos e descrições. A descrição fornece o comportamento esperado do dispositivo com base nos valores selecionados. As teclas de configuração que são desativadas no Designer de Configuração não estão listadas na tabela.

| Chave de configuração | Tipo de Valor | Valor Predefinido | Description |
|---------------------------------------------------------------------------------------------------------------------------|-------------|------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Definir tamanho da grelha | cadeia | Automático | Permite-lhe definir o tamanho da grelha para as aplicações serem posicionadas no ecrã principal gerido. Pode definir o número de linhas e colunas de aplicações para definir o tamanho da grelha no formato seguinte `columns;rows`. Se definir o tamanho da grelha, o número máximo de aplicações que serão mostradas em linha no ecrã principal seria o número de linhas que definiu e o número máximo de aplicações que serão mostradas numa coluna no ecrã principal seria o número de colunas que definiu. |
| Ativar o crachá de notificações | bool | FALSO | Permite o crachá de notificação para ícones de aplicações que mostram o número de novas notificações na aplicação. Se ativar esta definição, os utilizadores finais verão crachás de notificação em aplicações que tenham notificações não lidas. Se mantiver esta chave de configuração desativada, o utilizador final não verá nenhuma notificação insígnada a apps que possam ter notificações não lidas. |
| Tela principal de bloqueio | bool | TRUE | Remove a capacidade do utilizador final de se mover em torno dos ícones da aplicação no ecrã principal. Se ativar esta chave de configuração, os ícones da aplicação no ecrã principal serão bloqueados e o utilizador final não será capaz de arrastar e cair para diferentes posições de grelha do ecrã principal. Se forem virados para `false`, os utilizadores finais poderão mover-se em torno da aplicação e os ícones weblink no Ecrã Home Gerido.  |
| Definir papel de parede do dispositivo | cadeia | Predefinição | Permite-lhe definir um papel de parede à sua escolha, entrando no URL da imagem que pretende definir como papel de parede. |
| Definir tamanho do ícone da aplicação | número inteiro | 2 | Permite-lhe definir o tamanho do ícone para aplicações exibidas no ecrã principal. Pode escolher os seguintes valores nesta configuração para diferentes tamanhos - 0 (Menores), 1 (Pequeno), 2 (Regular), 3 (Grande) e 4 (Maior). |
| Definir ícone de pasta de aplicativo | número inteiro | 0 | Permite definir a aparência das pastas de aplicações no ecrã principal. Pode escolher a aparência a partir dos seguintes valores: Dark Square(0);   Círculo Escuro(1); Praça da Luz(2); Círculo de luz (3). |
| Definir orientação do ecrã | número inteiro | 1 | Permite-lhe definir a orientação do ecrã principal para o modo de retrato, modo paisagístico ou permitir a rotação automática. Pode definir a orientação inserindo os valores 1 (para o modo retrato), 2 (para modo paisagístico), 3 (para Autorotate). |
| Ativar a telemetria do dispositivo | bool | FALSO | Permite toda a telemetria que está a ser captada para o ecrã principal gerido. Se o ativar, a Microsoft poderá capturar a telemetria de utilização do dispositivo, como o número de vezes que uma determinada aplicação é lançada neste dispositivo. |
| Definir aplicações listadas por permitir | BundleArray | FALSO | Permite definir o conjunto de aplicações visíveis no ecrã principal entre as aplicações instaladas no dispositivo. Pode definir as aplicações ao introduzir o nome do pacote de aplicações das aplicações que gostaria de tornar visíveis, por exemplo com.microsoft.emmx tornaria as definições acessíveis no ecrã principal. As aplicações que permite listar nesta secção já devem ser instaladas no dispositivo para serem visíveis no ecrã principal. |
| Definir links web fixados | BundleArray | FALSO | Permite-lhe fixar websites como ícones de lançamento rápido no ecrã principal. Com esta configuração, pode definir o URL e adicioná-lo ao ecrã principal para o utilizador final lançar no navegador com um único toque. |
| Ativar o protetor de ecrã | bool | FALSO | Para ativar o modo de poupança de ecrã ou não. Se for verdade, pode configurar **screen_saver_image,** **screen_saver_show_time,** **inative_time_to_show_screen_saver**e **media_detect_screen_saver.** |
| Imagem de poupança de tela | cadeia |   | Delineie o URL da imagem de poupança de ecrã. Se não for definido nenhum URL, os dispositivos mostrarão a imagem de poupança de ecrã predefinido quando o protetor de ecrã for ativado. A imagem padrão mostra o ícone da aplicação Managed Home Screen.  |
| Tempo de programa de poupança de ecrã | número inteiro | 0 | Dá opção para definir o tempo em segundos que o dispositivo irá exibir o protetor de ecrã durante o modo de poupança de ecrã. Se definido para 0, o protetor de ecrã mostrará indefinidamente no modo de poupança de ecrã até que o dispositivo se torne ativo.  |
| Tempo inativo para ativar o protetor de ecrã | número inteiro | 30 | O número de segundos em que o dispositivo está inativo antes de acionar o protetor de ecrã. Se definido para 0, o dispositivo nunca entrará no modo de poupança de ecrã. |
| Os meios de deteção dos meios de comunicação antes de mostrar em si o protetor de ecrã | bool | TRUE | Escolha se o ecrã do dispositivo deve mostrar o protetor de ecrã se o áudio/vídeo estiver a ser reproduzido no dispositivo. Se for definido como verdadeiro, o dispositivo não reproduzirá áudio/vídeo, independentemente do valor em **inative_time_to_show_scree_saver**. Se for definido como falso, o ecrã do dispositivo mostrará o protetor de ecrã de acordo com o valor definido em **inative_time_to_show_screen_saver**.   |
| Ativar botão doméstico virtual | bool | FALSO | Rode esta definição para `True` para permitir ao utilizador final ter acesso a um botão home Screen gerido que devolverá o utilizador ao Ecrã Home Gerido a partir da tarefa atual em que se encontra.  |
| Tipo de botão doméstico virtual | cadeia | swipe_up | Use **swipe_up** para aceder ao botão de casa com um gesto de swipe up. Utilize **boia** para aceder a um botão caseiro pegajoso e persistente que pode ser movido em torno do ecrã pelo utilizador final. |
| Barra indicadora de resistência à bateria e sinal | bool | Verdadeiro  | Rodar esta definição para `True` mostra a barra indicadora de força da bateria e do sinal. |
| Palavra-passe do modo de tarefa de bloqueio de saída | cadeia |   | Introduza um código de 4-6 dígitos para utilizar para abandonar temporariamente o modo de tarefa de bloqueio para resolução de problemas. |
| Mostrar definição wi-fi | bool | FALSO | A rotação desta definição para `True` permite ao utilizador final ligar ou desligar o Wi-Fi ou ligar-se a diferentes redes Wi-Fi.  |
| Mostrar a definição Bluetooth | bool | FALSO | Rodar esta definição para `True` permite ao utilizador final ligar ou desligar bluetooth e ligar-se a diferentes dispositivos com bluetooth.   |
| As aplicações na pasta são encomendadas pelo nome | bool | TRUE | A viragem desta definição para `False` permite que os itens de uma pasta apareçam na ordem em que são especificados. Caso contrário, aparecerão na pasta alfabeticamente.   |
| Ordem de aplicação ativada | bool | FALSO | Mudar esta definição para `True` permite a capacidade de definir a ordem das aplicações, weblinks e pastas no Ecrã Inicial Gerido. Uma vez ativado, delineie a encomenda com **app_order**.o utilizador final para ligar ou desligar Bluetooth e ligar-se a diferentes dispositivos com Bluetooth.   |
| Pedido de candidatura | BundleArray | FALSO | Permite especificar a ordem das aplicações, weblinks e pastas no Ecrã Inicial Gerido. Para utilizar esta definição, o **ecrã principal do bloqueio** deve ser ativado, definir o tamanho da **grelha** deve ser definido e a ordem de **aplicação ativada** deve ser definida para `True`.   |

## <a name="enter-json-data"></a>Insira dados da JSON

Introduza os dados da JSON para configurar todas as definições disponíveis para o Ecrã Home Gerido, bem como as definições desativadas no Designer de **Configuração**.

![Screenshot de dados adicionais da JSON](./media/app-configuration-managed-home-screen-app/app-configuration-managed-home-screen-app_03.png)

Além da lista de configurações configuráveis listadas na tabela **'Configuração Designer'** (acima), a tabela seguinte fornece as teclas de configuração que só pode configurar através de dados jSON.

|    Chave de configuração    |    Tipo de valor    |    Valor Predefinido    |    Description    |
|-------------------------------------------------|--------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    Definir aplicações listadas por permitir    |    BundleArray    | <img alt="JSON - Example 1" src="./media/app-configuration-managed-home-screen-app/defaultvaluejson01.png" width="300"> |    Permite definir o conjunto de aplicações visíveis no ecrã principal entre as aplicações instaladas no dispositivo. Pode definir as aplicações ao introduzir o nome do pacote de aplicações das aplicações que gostaria de tornar visíveis, por exemplo, com.android.definições tornariam as definições acessíveis no ecrã principal. As aplicações que permite listar nesta secção já devem ser instaladas no dispositivo para serem visíveis no ecrã principal.    |
|    Definir links web fixados    |    BundleArray    | <img alt="JSON - Example 2" src="./media/app-configuration-managed-home-screen-app/defaultvaluejson02.png" width="300"> |    Permite-lhe fixar websites como ícones de lançamento rápido no ecrã principal. Com esta configuração, pode definir o URL e adicioná-lo ao ecrã principal para o utilizador final lançar no navegador com um único toque.    |
|    Criar pasta gerida para agrupar aplicações    |    BundleArray    | <img alt="JSON - Example 3" src="./media/app-configuration-managed-home-screen-app/defaultvaluejson03.png" width="300"> |    Permite-lhe criar e nomear pastas e aplicações de grupo dentro destas pastas. Os utilizadores finais não poderão mover pastas, mudar o nome das pastas ou mover as aplicações dentro das pastas.   As pastas aparecerão na ordem criada e as aplicações dentro das pastas aparecerão alfabeticamente.         Nota: todas as aplicações que pretende agrupar em pastas devem ser atribuídas conforme necessário ao dispositivo e devem ter sido adicionadas ao Ecrã Inicial Gerido.     |

Segue-se um exemplo de script JSON com todas as chaves de configuração disponíveis incluídas:

```json
{
    "kind": "androidenterprise#managedConfiguration",
    "productId": "com.microsoft.launcher.enterprise",
    "managedProperty": [
        {
            "key": "lock_home_screen",
            "valueBool": true
        },
        {
            "key": "wallpaper",
            "valueString": "default"
        },
        {
            "key": "icon_size",
            "valueInteger": 2
        },
        {
            "key": "app_folder_icon",
            "valueInteger": 0
        },
        {
            "key": "screen_orientation",
            "valueInteger": 1
        },
        {
            "key": "enable_telemetry",
            "valueBool": false
        },
        {
            "key": "applications",
            "valueBundleArray": [
                {
                    "managedProperty": [
                        {
                            "key": "package",
                            "valueString": “app package name here”
                        }
                    ]
                }
            ]
        },
        {
            "key": "weblinks",
            "valueBundleArray": [
                {
                    "managedProperty": [
                        {
                            "key": "link",
                            "valueString": “link here”
                        },
                        {
                            "key": "label",
                            "valueString": “weblink label here”
                        }
                    ]
                }
            ]
        },
        {
            "key": "show_virtual_home",
            "valueBool": false
        },
        {
            "key": "virtual_home_type",
            "valueString": "swipe_up"
        },
        {
            "key": "show_virtual_status_bar",
            "valueBool": true
        },
        {
            "key": "exit_lock_task_mode_code",
            "valueString": ""
        },
        {
            "key": "show_wifi_setting",
            "valueBool": false
        },
        {
            "key": "show_bluetooth_setting",
            "valueBool": false
        },
        {
            "key": "grid_size",
            "valueString": "4;5"
        },
        {
            "key": "app_order_enabled",
            "valueBool": true
        },
        {
            "key": "apps_in_folder_ordered_by_name",
            "valueBool": true
        },
        {
            "key": "app_orders",
            "valueBundleArray": [
                {
                    "managedProperty": [
                        {
                            "key": "package",
                            "valueString": "com.Microsoft.emmx"
                        },
                        {
                            "key": "type",
                            "valueString": "application"
                        },
                        {
                            "key": "container",
                            "valueInteger": 1
                        },
                        {
                            "key": "position",
                            "valueInteger": 1
                        }
                    ]
                },
                {
                    "managedProperty": [
                        {
                            "key": "folder_name",
                            "valueString": "Work"
                        },
                        {
                            "key": "type",
                            "valueString": "managed_folder"
                        },
                        {
                            "key": "container",
                            "valueInteger": 1
                        },
                        {
                            "key": "position",
                            "valueInteger": 2
                        }
                    ]
                },
                {
                    "managedProperty": [
                        {
                            "key": "package",
                            "valueString": "com.microsoft.launcher.enterprise"
                        },
                        {
                            "key": "type",
                            "valueString": "application"
                        },
                        {
                            "key": "class",
                            "valueString": "com.microsoft.launcher.launcher"
                        },
                        {
                            "key": "container",
                            "valueInteger": 1
                        },
                        {
                            "key": "position",
                            "valueInteger": 3
                        }
                    ]
                }
            ]
        },
        {
            "key": "managed_folders",
            "valueBundleArray": [
                {
                    "managedProperty": [
                        {
                            "key": "folder_name",
                            "valueString": "Folder name here"
                        },
                        {
                            "key": "applications",
                            "valueBundleArray": [
                                {
                                    "managedProperty": [
                                        {
                                            "key": "package",
                                            "valueString": "com.microsoft.emmx"
                                        }
                                    ]
                                },
                                {
                                    "managedProperty": [
                                        {
                                            "key": "package",
                                            "valueString": "com.microsoft.bing"
                                        }
                                    ]
                                },
                                {
                                    "managedProperty": [
                                        {
                                            "key": "link",
                                            "valueString": "https://microsoft.com/"
                                        }
                                    ]
                                }
                            ]
                        }
                    ]
                },
                {
                    "managedProperty": [
                        {
                            "key": "folder_name",
                            "valueString": "Example folder name 2"
                        },
                        {
                            "key": "applications",
                            "valueBundleArray": [
                                {
                                    "managedProperty": [
                                        {
                                            "key": "package",
                                            "valueString": "com.microsoft.office.word"
                                        }
                                    ]
                                }
                            ]
                        }
                    ]
                }
            ]
        }
    ]
}
```

## <a name="googles-android-device-policy-app"></a>Aplicação política de dispositivos Android da Google
A aplicação Managed Home Screen agora fornece acesso à aplicação Política de Dispositivos Android da Google. A aplicação Managed Home Screen é um lançador personalizado utilizado para dispositivos matriculados em Intune como dispositivos dedicados ao Android Enterprise (AE) utilizando o modo de quiosque multi-app. Pode aceder à aplicação Android Device Policy ou orientar os utilizadores para a aplicação Política de Dispositivos Android, para fins de suporte e depuração. Esta capacidade de lançamento está disponível no momento em que o dispositivo se inscreve e bloqueia no Ecrã Home Gerido. Não são necessárias instalações adicionais para utilizar esta funcionalidade.

## <a name="managed-home-screen-debug-screen"></a>Ecrã de depuração de Ecrã Doméstico Gerido
Pode aceder ao ecrã de depuração do Ecrã Home Gerido clicando no botão **traseiro** até que o ecrã de depuração seja visualizado (clique no botão **de trás** 15 vezes ou mais). A partir deste ecrã de depuração, é possível lançar a aplicação De Política de Dispositivos Android, visualizar e carregar registos, ou interromper temporariamente o modo de quiosque para atualizar o dispositivo. Para obter mais informações sobre o modo de pausa do quiosque, consulte o item do **modo de quiosque Leave** nas [definições do dispositivo dedicado](../configuration/device-restrictions-android-for-work.md#dedicated-device-settings)ao Android Enterprise .

## <a name="next-steps"></a>Próximos passos

- Para obter mais informações sobre dispositivos dedicados ao Android Enterprise, consulte [A inscrição intune de dispositivos dedicados ao Android Enterprise.](../enrollment/android-kiosk-enroll.md)
