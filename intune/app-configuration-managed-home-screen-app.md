---
title: Configurar o ecrã principal aplicação gerida por Microsoft
titleSuffix: Microsoft Intune
description: Saiba como configurar a aplicação Microsoft Managed home page ecrã.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 05/16/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 865c7f03-f525-4dfa-b3a8-d088a9106502
ms.reviewer: chmaguir
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: fd8de55acf8fa24db005f7725502b691f9f0adbb
ms.sourcegitcommit: dfcf80a91792715404dc021c8684866c8b0a27e1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2019
ms.locfileid: "65816305"
---
# <a name="configure-the-microsoft-managed-home-screen-app-for-android-enterprise"></a>Configurar o Microsoft Managed app de ecrã principal do Android Enterprise

A tela geridas base é o aplicativo usado para dispositivos Android Enterprise dedicados pertencentes à empresa inscritos através do Intune e em execução no modo de quiosque de várias aplicações. Para estes dispositivos, a tela geridos home page atua como iniciador para outras aplicações aprovadas executar com base no mesmo. O ecrã geridos home page fornece os administradores de TI a capacidade de personalizar os seus dispositivos e para restringir as capacidades que o utilizador final pode aceder. 

## <a name="when-to-configure-the-microsoft-managed-home-screen-app"></a>Quando configurar a aplicação Microsoft Managed home page ecrã

Normalmente, se as definições estão disponíveis para si através da configuração do dispositivo, configure as definições de existir. Ao fazer por isso, irá poupar tempo, minimizar erros e lhe dará uma melhor experiência de suporte do Intune. No entanto, algumas das configurações geridas tela home page só estão atualmente disponíveis através da **políticas de configuração de aplicação** painel na consola do Intune. Utilize este documento para saber como configurar as definições diferentes usando o designer de configuração ou um script JSON. 

> [!NOTE]
> Ele é atualmente possível e recomendado, para definir listado permitir aplicações e afixado ligações web por meio **aplicações de cliente** e **configuração do dispositivo**. Para obter a lista completa das definições disponíveis na **configuração do dispositivo** que afetam geridos tela home page, consulte [dedicado definições do dispositivo](device-restrictions-android-for-work.md#dedicated-device-settings).  

Em primeiro lugar, navegue para a consola do Intune no portal do Azure e aceda a **aplicações de cliente** > **políticas de configuração de aplicação**. Adicionar uma política de configuração para **dispositivos geridos** em execução **Android** e escolha **geridos tela home page** como a aplicação associada. Clique em **definições de configuração** para configurar as definições de geridos home page ecrã disponíveis diferentes. 

## <a name="choosing-a-configuration-settings-format"></a>Escolher um formato de definições de configuração

Existem dois métodos que pode utilizar para configurar definições de configuração para gerido tela home page:

- **Estruturador de configuração** permite-lhe configurar as definições com uma interface do Usuário de fácil de usar que permite-lhe ativar as funcionalidades ou desativar e definir valores. Nesse método, existem algumas chaves de configuração desativadas com o tipo de valor `BundleArray`. Essas chaves de configuração só podem ser configuradas ao introduzir dados JSON. 
- **Dados JSON** permite-lhe definir todas as chaves de configuração possíveis usando um script JSON. 

Se adicionar propriedades com o estruturador de configuração, pode converter automaticamente estas propriedades JSON, selecionando **dados JSON introduza** partir a **formato das definições de configuração** lista pendente.

![Opções de formato de definição de captura de ecrã de configuração](./media/app-configuration-managed-home-screen-app/app-configuration-managed-home-screen-app_01.png)

## <a name="using-configuration-designer"></a>Usando o Designer de configuração

Estruturador de configuração permite-lhe selecionar definições pré-preenchidos e seus valores associados. 

![Captura de ecrã das definições de configuração foi adicionado](./media/app-configuration-managed-home-screen-app/app-configuration-managed-home-screen-app_02.png)

A tabela seguinte lista as chaves de configuração disponíveis geridos tela home page, tipos de valor, valores padrão e descrições. A descrição apresenta o comportamento esperado do dispositivo com base nos valores selecionados. Chaves de configuração que estão desativadas no Designer de configuração não estão listadas na tabela.

| Chave de configuração | Tipo de valor | Valor Predefinido | Descrição |
|---------------------------------------------------------------------------------------------------------------------------|-------------|------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Defina o tamanho da grelha | Cadeia de caracteres | Automático | Permite-lhe definir o tamanho de grade para aplicações posicionado no ecrã principal do gerido. Pode definir o número de linhas de aplicação e colunas para definir o tamanho de grade no seguinte formato `rows;columns`. Se definir o tamanho de grade, o número máximo de aplicações que serão mostrados numa linha no ecrã inicial seria o número de linhas, definir e o número máximo de aplicações que serão mostrados numa coluna na tela inicial seria o número de colunas definidas. |
| Ativar o cabeçalho de ecrã | Bool | VERDADEIRO | Permite que o cabeçalho da parte superior para diferentes vistas que a tela inicial gerida oferece, como os cartões de feeds ou feeds. Se ativar esta definição, os utilizadores de dispositivos irão ver o cabeçalho. |
| Ativar a barra de estado do dispositivo | Bool | VERDADEIRO | Permite que a barra de status na tela inicial (barra superior que apresenta ligações atuais como Wi-Fi e etc.). Se ativar esta chave de configuração, o utilizador final será capaz de ver os ícones apresentados nas barras de estado que representam as ligações e aplicações do Active Directory. |
| Ativar o destaque de notificações | Bool | FALSO | Permite que o destaque de notificação para os ícones da aplicação que mostra o número de novas notificações na aplicação. Se ativar esta definição, os utilizadores finais irão ver os destaques de notificação em aplicações que tenham notificações não lidas. Se mantiver essa configuração chave desativado, o utilizador final não verão qualquer notificação com distintivo para aplicações que podem ter notificações não lidas. |
| Ecrã principal de bloqueio | Bool | VERDADEIRO | Remove a capacidade do utilizador final para mover os ícones da aplicação no ecrã inicial. Se ativar esta chave de configuração, os ícones de aplicação no ecrã principal fica bloqueados e o utilizador final não seria capaz de arrastar e soltar para posições de grade diferente do ecrã inicial. Se ativado `false`, os utilizadores finais poderão ser movido entre os ícones de aplicação e a ligação Web a tela geridos home page.  |
| Definir o papel de parede de dispositivo | Cadeia de caracteres | Predefinição | Permite-lhe definir um papel de parede de sua preferência ao introduzir o URL da imagem que pretende definir como uma imagem de fundo. |
| Defina o tamanho de ícone de aplicação | inteiro | 2 | Permite-lhe definir o tamanho de ícone de aplicações apresentada no ecrã inicial. Pode escolher os seguintes valores nesta configuração para diferentes tamanhos - 0 (mais pequeno), 1 (pequeno), 2 (Regular), 3 (grande) e 4 (maior). |
| Ícone de pasta do conjunto de aplicações | inteiro | 0 | Pode definir a aparência das pastas de aplicação no ecrã inicial. Pode escolher a aparência dos seguintes valores: Square(0) escuro;   Circle(1) escuro; Square(2) claro; Luz Circle(3). |
| Ativar gestos | Bool | FALSO | Ative a capacidade do utilizador final de atribuir ações diferentes gestos, como percorra a cópia de segurança e arraste para baixo. Se desativar esta chave de configuração, os utilizadores finais só poderá para a direita de passar o dedo se houver uma segunda página e voltar à home page. |
| Ativar o deslocamento vertical | Bool | FALSO | Permite a rolagem vertical no ecrã principal do gerido. Se ativar esta chave de configuração, o utilizador final só será capaz de navegar para páginas diferentes verticalmente em vez de passando o dedo horizontalmente. |
| Tema de ecrã principal do conjunto | cadeia | Theme.Light.Blue | Permite-lhe escolher o tema para a tela inicial de um conjunto predefinido de temas com diferentes cores. Pode escolher os temas seguintes ao introduzir o valor de cadeia de caracteres no seguinte formato.   Theme.Light.Green. Onde light pode ser substituído por escuro para um tema escuro e verde pode ser substituído por azul, amarelo, rosa, vermelho, laranja e Roxo. |
| Ativar a estação de ancoragem | Bool | FALSO | Permite que a seção de estação de ancoragem na aplicação na parte inferior do ecrã principal com aplicações persistentes apresentada e o ponto de entrada para todas as aplicações instaladas. Se ativar esta chave de configuração, o utilizador final será capaz de aceder a aplicações na estação de ancoragem e também acessar a seção aplicação todos os para ir para a lista de todas as aplicações instaladas nos dispositivos, independentemente de terem estado listado permitir. |
| Orientação do ecrã de conjunto | inteiro | 1 | Permite-lhe definir a orientação do ecrã principal para o modo retrato, paisagem ou permitir a rotação automática. Pode definir a orientação ao introduzir valores 1 (para o modo de vertical), 2 (para modo paisagem), 3 (para Autorotate). |
| Ativar o feed de ecrã principal | Bool | FALSO | Permite que o feed do ecrã principal, que pode ser visto ao percorrer o lado esquerdo do ecrã inicial. Este feed apresenta outro tipo de conteúdo, como notícias, calendário, com frequência as aplicações de utilizador e cartão de Assistente de voz Cortana etc. Se ativar esta opção, o utilizador final será capaz de navegar para o feed ao percorrer o lado esquerdo do ecrã principal. |
| Ativar o modo de descrição geral | Bool | FALSO | Permite que os utilizadores finais adicionar ou remover páginas diferentes do ecrã principal, que podem ser acedidos passando o dedo diretamente a partir do ecrã predefinido. Se ativar esta opção, o utilizador final será possível adicionar páginas à direita da página predefinida do ecrã inicial, também será capaz de alterar a página padrão e também poderão acessar as configurações do ecrã principal geridos. |
| Ativar a telemetria do dispositivo | Bool | FALSO | Permite que toda a telemetria que está a ser capturada para a tela inicial gerida. Se ativar esta opção, a Microsoft será capaz de capturar a telemetria de utilização do dispositivo, como o número de vezes que uma aplicação específica é iniciada neste dispositivo. |
| Definir listado permitir aplicações | bundleArray | FALSO | Permite-lhe definir o conjunto de aplicações visíveis na tela inicial de entre as aplicações instaladas no dispositivo. Pode definir as aplicações ao introduzir o nome do pacote de aplicação das aplicações que pretende tornar visíveis, por exemplo com.android.settings tornaria definições acessíveis no ecrã inicial. As aplicações que-lista de permissões nesta secção já deverá estar instalado no dispositivo para que seja visível na tela inicial. |
| Ligações da web de conjunto afixado | bundleArray | FALSO | Permite-lhe afixar sites como ícones de início rápido do ecrã principal. Com esta configuração, pode definir o URL e adicioná-lo ao ecrã principal para o utilizador final iniciar no browser com um único toque. |
| Ativar a barra de pesquisa | Bool | FALSO | Permite que a barra de pesquisa no ecrã principal. Se ativar esta opção, os utilizadores do dispositivo Verão a barra de pesquisa do ecrã principal em que este seria capaz de introduzir que querem pesquisar na web. |
| Desativar aplicação de definições | Bool | FALSO | Desativa a página de definições para a tela geridos home page. Se desativar isso, o utilizador final do dispositivo não será capaz de fazer para as definições do Managed home page ecrã. |
| Ativar a proteção de tela | Bool | FALSO | Para ativar o modo de proteção de tela ou não. Se definido como true, pode configurar **screen_saver_image**, **screen_saver_show_time**, **inactive_time_to_show_screen_saver**, e **media_detect_ screen_saver**. |
| Imagem de proteção de ecrã | cadeia |   | Defina o URL da imagem de proteção de tela. Não se for definido nenhum URL, dispositivos mostrará a tela padrão quando a proteção de tela é ativada.  |
| Proteção da tela, mostrar a hora | inteiro | 0 | Dá a opção para definir o período de tempo em segundos, o dispositivo irá apresentar a proteção de tela durante o modo de proteção de tela. Se definido como 0, a proteção de ecrã será apresentado no modo de proteção de tela indefinidamente até que o dispositivo fica ativo.  |
| Tempo inativo para ativar a proteção de tela | inteiro | 30 | O número de segundos que o dispositivo está inativo antes de acionar a proteção de tela. Se definido como 0, o dispositivo nunca irá entrar em modo de proteção de tela. |
| Suporte de dados detetar antes de mostrar a proteção de tela | Bool | VERDADEIRO | Escolha se o ecrã do dispositivo deve mostrar proteção de tela se reprodução de áudio/vídeo no dispositivo. Se definido como true, o dispositivo não irá reproduzir áudio/vídeo, independentemente do valor em **inactive_time_to_show_scree_saver**. Se definido como false, ecrã do dispositivo irá mostrar a proteção de tela de acordo com o conjunto de valores no **inactive_time_to_show_screen_saver**.   |
| Ativar o botão de início virtual | Bool | FALSO | Ativar esta definição `True` para permitir que o utilizador final ter acesso a um botão de início de ecrã principal gerida que irá devolver o utilizador ao ecrã principal geridos a tarefa atual estão no.  |
| Tipo de botão de início virtual | cadeia | swipe_up | Uso **swipe_up** para botão de início de acesso com um percorra a segurança de gesto. Uso **float** para aceder a um botão de início adesivo, persistente que pode ser movido pela tela pelo utilizador final. |
| Barra de indicador da bateria e intensidade do sinal | Bool | Verdadeiro  | Ativar esta definição `True` mostra a barra de indicador de força da bateria e do sinal. |
| Palavra-passe de modo do tarefas de bloqueio de saída | Cadeia de caracteres |   | Introduza um código de 6 de 4 dígitos a utilizar para remover temporariamente fora do modo de tarefa de bloqueio para resolução de problemas. |
| Mostrar a configuração de Wi-Fi | Bool | FALSO | Ativar esta definição `True` permite que o utilizador final para ativar ou desativar Wi-Fi ou para ligar a várias redes Wi-Fi.  |
| Mostrar a definição de Bluetooth | Bool | FALSO | Ativar esta definição `True` permite que o utilizador final para ativar ou desativar o Bluetooth e ligue a dispositivos com capacidade de Bluetooth diferentes.   |

## <a name="enter-json-data"></a>Introduzir dados JSON

Introduzir dados JSON para configurar todas as definições disponíveis para gerido tela home page, bem como as definições desativadas no **estruturador de configuração**.

![Captura de ecrã dos dados JSON adicionados](./media/app-configuration-managed-home-screen-app/app-configuration-managed-home-screen-app_03.png)

Além da lista de definições configuráveis apresentadas a **estruturador de configuração** tabela (acima), a tabela seguinte fornece as chaves de configuração só pode configurar através de dados JSON.

|    Chave de configuração    |    Tipo de valor    |    Valor predefinido    |    Descrição    |
|-------------------------------------------------|--------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    Definir listado permitir aplicações    |    bundleArray    | <img alt="JSON - Example 1" src="./media/app-configuration-managed-home-screen-app/defaultvaluejson01.png" width="300"> |    Permite-lhe definir o conjunto de aplicações visíveis na tela inicial de entre as aplicações instaladas no dispositivo. Pode definir as aplicações ao introduzir o nome do pacote de aplicação das aplicações que pretende tornar visíveis, por exemplo, com.android.settings tornaria definições acessíveis no ecrã inicial. As aplicações que-lista de permissões nesta secção já deverá estar instalado no dispositivo para que seja visível na tela inicial.    |
|    Ligações da web de conjunto afixado    |    bundleArray    | <img alt="JSON - Example 2" src="./media/app-configuration-managed-home-screen-app/defaultvaluejson02.png" width="300"> |    Permite-lhe afixar sites como ícones de início rápido do ecrã principal. Com esta configuração, pode definir o URL e adicioná-lo ao ecrã principal para o utilizador final iniciar no browser com um único toque.    |
|    Criar pasta gerenciada para o agrupamento de aplicações    |    bundleArray    | <img alt="JSON - Example 3" src="./media/app-configuration-managed-home-screen-app/defaultvaluejson03.png" width="300"> |    Permite-lhe criar e atribuir um nome pastas e aplicações de grupo contidos nelas. Os utilizadores finais não será capazes de pastas de mover, mudar o nome as pastas ou mover as aplicações dentro das pastas.   Pastas aparecerá na ordem que criou e aplicações dentro das pastas serão apresentados por ordem alfabética.         Nota: devem ser atribuídas a todas as aplicações que pretende agrupar em pastas conforme necessário para o dispositivo e tem de ter sido adicionado na tela geridos home page.     |

Segue-se um exemplo de script JSON com todas as chaves de configuração disponíveis incluídas:

```json
{
    "kind": "androidenterprise#managedConfiguration",
    "productId": "com.microsoft.launcher.enterprise",
    "managedProperty": [
        {
            "key": "grid_size",
            "valueString": "Auto"
        },
        {
            "key": "keep_page_header",
            "valueBool": true
        },
        {
            "key": "keep_status_bar",
            "valueBool": true
        },
        {
            "key": "show_notification_badge",
            "valueBool": false
        },
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
            "key": "gesture_on",
            "valueBool": false
        },
        {
            "key": "vertical_scrolling",
            "valueBool": false
        },
        {
            "key": "theme",
            "valueString": "Theme.Light.Blue"
        },
        {
            "key": "dock_enable",
            "valueBool": false
        },
        {
            "key": "screen_orientation",
            "valueInteger": 1
        },
        {
            "key": "feed_enable",
            "valueBool": false
        },
        {
            "key": "allow_overview_mode",
            "valueBool": false
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
            "key": "search_bar",
            "valueBool": false
        },
        {
            "key": "hide_settings",
            "valueBool": false
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
## <a name="next-steps"></a>Passos Seguintes

- Para obter mais informações sobre os dispositivos Android Enterprise dedicado, consulte [configurar a inscrição do Intune de dispositivos empresariais Android dedicado](android-kiosk-enroll.md).
