---
title: Configurar o aplicativo de tela inicial gerenciado pela Microsoft
titleSuffix: Microsoft Intune
description: Saiba como configurar o aplicativo de tela inicial gerenciado pela Microsoft.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/23/2019
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
ms.openlocfilehash: e97e88ad78e1b914543b7fa283f47863dce185fc
ms.sourcegitcommit: 25acfc88b366d2da71c37d354a0238e4f1168325
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/23/2019
ms.locfileid: "72813468"
---
# <a name="configure-the-microsoft-managed-home-screen-app-for-android-enterprise"></a>Configurar o aplicativo de tela inicial gerenciado pela Microsoft para Android Enterprise

A tela inicial gerenciada é o aplicativo usado para dispositivos Android Enterprise dedicados corporativos registrados por meio do Intune e executados no modo de quiosque de vários aplicativos. Para esses dispositivos, a tela inicial gerenciada age como o iniciador para que outros aplicativos aprovados sejam executados sobre ele. A tela inicial gerenciada fornece aos administradores de ti a capacidade de personalizar seus dispositivos e restringir os recursos que o usuário final pode acessar. 

## <a name="when-to-configure-the-microsoft-managed-home-screen-app"></a>Quando configurar o aplicativo de tela inicial gerenciado pela Microsoft

Normalmente, se as configurações estiverem disponíveis para você por meio da configuração do dispositivo, defina as configurações ali. Isso poupará tempo, minimizará erros e dará uma experiência de suporte do Intune melhor. No entanto, algumas das configurações da tela inicial gerenciada estão atualmente disponíveis apenas por meio da folha **políticas de configuração de aplicativo** no console do Intune. Use este documento para saber como definir as configurações diferentes usando o designer de configuração ou um script JSON. 

> [!NOTE]
> Atualmente, ele é possível e pode ser avisado para definir os aplicativos listados e os links da Web fixados por meio de **aplicativos cliente** e **configuração de dispositivo**. Para obter a lista completa de configurações disponíveis na **configuração do dispositivo** que afeta a tela inicial gerenciada, consulte Configurações de [dispositivo dedicadas](../configuration/device-restrictions-android-for-work.md#dedicated-device-settings).  

Primeiro, navegue até o console do Intune em portal do Azure e vá para **aplicativos cliente** > **políticas de configuração de aplicativo**. Adicione uma política de configuração para **dispositivos gerenciados** que executam o **Android** e escolha a **tela inicial gerenciada** como o aplicativo associado. Clique em **definições de configuração** para definir as diferentes configurações de tela inicial gerenciada disponíveis. 

## <a name="choosing-a-configuration-settings-format"></a>Escolhendo um formato de definições de configuração

Há dois métodos que você pode usar para definir definições de configuração para a tela inicial gerenciada:

- O **Designer de configuração** permite que você defina as configurações com uma interface de usuário fácil de usar que permite ativar ou desativar recursos e definir valores. Nesse método, há algumas chaves de configuração desabilitadas com o tipo de valor `BundleArray`. Essas chaves de configuração só podem ser configuradas digitando dados JSON. 
- Os **dados JSON** permitem que você defina todas as chaves de configuração possíveis usando um script JSON. 

Se você adicionar propriedades com o designer de configuração, poderá converter automaticamente essas propriedades em JSON selecionando **inserir dados JSON** na lista suspensa **formato de definições de configuração** .

![Captura de tela das opções de formato de definição de configuração](./media/app-configuration-managed-home-screen-app/app-configuration-managed-home-screen-app_01.png)

## <a name="using-configuration-designer"></a>Usando o designer de configuração

O designer de configuração permite que você selecione configurações preenchidas previamente e seus valores associados. 

![Captura de tela de definições de configuração adicionadas](./media/app-configuration-managed-home-screen-app/app-configuration-managed-home-screen-app_02.png)

A tabela a seguir lista as chaves de configuração, os tipos de valor, os valores padrão e as descrições da tela inicial gerenciada. A descrição fornece o comportamento de dispositivo esperado com base nos valores selecionados. As chaves de configuração que estão desabilitadas no designer de configuração não estão listadas na tabela.

| Chave de configuração | Tipo de Valor | Valor Predefinido | Description |
|---------------------------------------------------------------------------------------------------------------------------|-------------|------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Definir tamanho da grade | cadeia | Automático | Permite definir o tamanho da grade para que os aplicativos sejam posicionados na tela inicial gerenciada. Você pode definir o número de linhas e colunas do aplicativo para definir o tamanho da grade no seguinte formato `columns;rows`. Se você definir o tamanho da grade, o número máximo de aplicativos que serão mostrados em uma linha na tela inicial será o número de linhas que você definiu e o número máximo de aplicativos que serão mostrados em uma coluna na tela inicial seria o número de colunas que você definiu. |
| Habilitar notificação de notificações | bool | FOR | Habilita o crachá de notificação para ícones de aplicativo que mostra o número de novas notificações no aplicativo. Se você habilitar essa configuração, os usuários finais verão selos de notificação em aplicativos que têm notificações não lidas. Se você mantiver essa chave de configuração desabilitada, o usuário final não verá nenhuma notificação para aplicativos que possam ter notificações não lidas. |
| Bloquear tela inicial | bool | TRUE | Remove a capacidade do usuário final de mover os ícones do aplicativo na tela inicial. Se você habilitar essa chave de configuração, os ícones do aplicativo na tela inicial serão bloqueados e o usuário final não poderá arrastar e soltar para diferentes posições de grade da tela inicial. Se for transformada em `false`, os usuários finais poderão se mover pelos ícones de aplicativo e weblink na tela inicial gerenciada.  |
| Definir papel de parede do dispositivo | cadeia | Os | Permite definir um papel de parede de sua escolha digitando a URL da imagem que você deseja definir como um papel de parede. |
| Definir o tamanho do ícone do aplicativo | número inteiro | 2 | Permite definir o tamanho do ícone para os aplicativos exibidos na tela inicial. Você pode escolher os seguintes valores nessa configuração para tamanhos diferentes-0 (menor), 1 (pequeno), 2 (regular), 3 (grande) e 4 (maior). |
| Definir ícone de pasta de aplicativo | número inteiro | 0 | Permite que você defina a aparência das pastas de aplicativo na tela inicial. Você pode escolher a aparência dos seguintes valores: quadrado escuro (0);   Círculo escuro (1); Quadrado claro (2); Círculo claro (3). |
| Definir orientação da tela | número inteiro | 1 | Permite definir a orientação da tela inicial como modo retrato, modo paisagem ou permitir giro automático. Você pode definir a orientação inserindo os valores 1 (para o modo retrato), 2 (para o modo paisagem), 3 (para rotação automática). |
| Habilitar telemetria do dispositivo | bool | FOR | Habilita toda a telemetria que está sendo capturada para a tela inicial gerenciada. Se você habilitar isso, a Microsoft poderá capturar a telemetria de uso do dispositivo, como o número de vezes que um determinado aplicativo é iniciado nesse dispositivo. |
| Definir os aplicativos listados como permitidos | bundleArray | FOR | Permite que você defina o conjunto de aplicativos visíveis na tela inicial de entre os aplicativos instalados no dispositivo. Você pode definir os aplicativos inserindo o nome do pacote de aplicativo dos aplicativos que você gostaria de tornar visíveis, por exemplo, com. Microsoft. emmx tornaria as configurações acessíveis na tela inicial. Os aplicativos que você permite-listar nesta seção já devem estar instalados no dispositivo para que fiquem visíveis na tela inicial. |
| Definir links da Web fixados | bundleArray | FOR | Permite que você fixe sites como ícones de início rápido na tela inicial. Com essa configuração, você pode definir a URL e adicioná-la à tela inicial para o usuário final iniciar no navegador com um único toque. |
| Habilitar proteção de tela | bool | FOR | Para habilitar o modo de proteção de tela ou não. Se definido como true, você pode configurar **screen_saver_image**, **screen_saver_show_time**, **inactive_time_to_show_screen_saver**e **media_detect_screen_saver**. |
| Imagem de proteção de tela | cadeia |   | Defina a URL da imagem de proteção de tela. Se nenhuma URL for definida, os dispositivos mostrarão a imagem de proteção de tela padrão quando a proteção de tela for ativada. A imagem padrão mostra o ícone do aplicativo de tela inicial gerenciado.  |
| Proteção de tela mostrar hora | número inteiro | 0 | Fornece a opção para definir a quantidade de tempo em segundos que o dispositivo exibirá a proteção de tela durante o modo de proteção de tela. Se definido como 0, a proteção de tela será mostrada no modo de proteção de tela indefinidamente até que o dispositivo se torne ativo.  |
| Tempo inativo para habilitar a proteção de tela | número inteiro | 30 | O número de segundos que o dispositivo fica inativo antes de disparar a proteção de tela. Se definido como 0, o dispositivo nunca entrará no modo de proteção de tela. |
| Detecção de mídia antes de mostrar a proteção de tela | bool | TRUE | Escolha se a tela do dispositivo deverá mostrar a proteção de tela se o áudio/vídeo estiver sendo reproduzido no dispositivo. Se definido como true, o dispositivo não reproduzirá áudio/vídeo, independentemente do valor em **inactive_time_to_show_scree_saver**. Se definido como false, a tela do dispositivo mostrará a proteção de tela de acordo com o valor definido em **inactive_time_to_show_screen_saver**.   |
| Botão habilitar página inicial virtual | bool | FOR | Mude essa configuração para `True` para permitir que o usuário final tenha acesso a um botão Home da tela inicial gerenciada que retornará o usuário para a tela inicial gerenciada da tarefa atual em que eles estão.  |
| Tipo de botão de página inicial virtual | cadeia | swipe_up | Use **swipe_up** para acessar o botão página inicial com um gesto de deslizar para cima. Use **float** para acessar um botão doméstico permanente e persistente que pode ser movido pela tela pelo usuário final. |
| Barra de indicadores de intensidade de sinal e bateria | bool | Verdadeiro  | A desativação dessa configuração para `True` mostra a barra de indicadores de intensidade de sinal e bateria. |
| Sair da senha do modo de tarefa de bloqueio | cadeia |   | Insira um código de 4-6 dígitos a ser usado para descartar temporariamente o modo de tarefa de bloqueio para solução de problemas. |
| Mostrar configuração de Wi-Fi | bool | FOR | A desativação dessa configuração para `True` permite que o usuário final ligue ou desative o Wi-Fi ou conecte-se a redes Wi-Fi diferentes.  |
| Mostrar configuração de Bluetooth | bool | FOR | A desativação dessa configuração para `True` permite que o usuário final ative ou desative o Bluetooth e se conecte a diferentes dispositivos compatíveis com Bluetooth.   |
| Os aplicativos na pasta são ordenados por nome | bool | TRUE | A desativação dessa configuração para `False` permite que os itens em uma pasta apareçam na ordem em que são especificados. Caso contrário, eles serão exibidos na pasta em ordem alfabética.   |
| Pedido de aplicativo habilitado | bool | FOR | A desativação dessa configuração para `True` permite que a capacidade de definir a ordem dos aplicativos, Weblinks e pastas na tela inicial gerenciada. Uma vez habilitado, defina a ordenação com **app_order**. o usuário final ativar ou desativar o Bluetooth e conectar-se a dispositivos compatíveis com Bluetooth diferentes.   |
| Ordem do aplicativo | bundleArray | FOR | Permite que você especifique a ordem dos aplicativos, Weblinks e pastas na tela inicial gerenciada. Para usar essa configuração, a **tela bloquear página inicial** deve ser habilitada, **definir o tamanho da grade** deve ser definido e a ordem do **aplicativo habilitada** deve ser definida como `True`.   |

## <a name="enter-json-data"></a>Inserir dados JSON

Insira dados JSON para definir todas as configurações disponíveis para a tela inicial gerenciada, bem como as configurações desabilitadas no **Designer de configuração**.

![Captura de tela de dados JSON adicionados](./media/app-configuration-managed-home-screen-app/app-configuration-managed-home-screen-app_03.png)

Além da lista de configurações configuráveis listadas na tabela do **Designer de configuração** (acima), a tabela a seguir fornece as chaves de configuração que você só pode configurar por meio de dados JSON.

|    Chave de configuração    |    Tipo de valor    |    Valor padrão    |    Description    |
|-------------------------------------------------|--------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    Definir os aplicativos listados como permitidos    |    bundleArray    | <img alt="JSON - Example 1" src="./media/app-configuration-managed-home-screen-app/defaultvaluejson01.png" width="300"> |    Permite que você defina o conjunto de aplicativos visíveis na tela inicial de entre os aplicativos instalados no dispositivo. Você pode definir os aplicativos inserindo o nome do pacote de aplicativo dos aplicativos que você gostaria de tornar visíveis, por exemplo, com. Android. as configurações tornarão as configurações acessíveis na tela inicial. Os aplicativos que você permite-listar nesta seção já devem estar instalados no dispositivo para que fiquem visíveis na tela inicial.    |
|    Definir links da Web fixados    |    bundleArray    | <img alt="JSON - Example 2" src="./media/app-configuration-managed-home-screen-app/defaultvaluejson02.png" width="300"> |    Permite que você fixe sites como ícones de início rápido na tela inicial. Com essa configuração, você pode definir a URL e adicioná-la à tela inicial para o usuário final iniciar no navegador com um único toque.    |
|    Criar pasta gerenciada para agrupar aplicativos    |    bundleArray    | <img alt="JSON - Example 3" src="./media/app-configuration-managed-home-screen-app/defaultvaluejson03.png" width="300"> |    Permite criar e nomear pastas e agrupar aplicativos nessas pastas. Os usuários finais não poderão mover pastas, renomear as pastas ou mover os aplicativos dentro das pastas.   As pastas serão exibidas na ordem criada e os aplicativos nas pastas serão exibidos em ordem alfabética.         Observação: todos os aplicativos que você deseja agrupar em pastas devem ser atribuídos conforme necessário para o dispositivo e devem ter sido adicionados à tela inicial gerenciada.     |

Este é um exemplo de script JSON com todas as chaves de configuração disponíveis incluídas:

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

## <a name="googles-android-device-policy-app"></a>Aplicativo de política de dispositivo Android do Google
O aplicativo de tela inicial gerenciado agora fornece acesso ao aplicativo de política de dispositivo Android do Google. O aplicativo de tela inicial gerenciado é um iniciador personalizado usado para dispositivos registrados no Intune como dispositivos do Android Enterprise (AE) dedicados usando o modo de quiosque de vários aplicativos. Você pode acessar o aplicativo de política de dispositivo Android ou orientar os usuários para o aplicativo de política de dispositivo Android, para fins de suporte e depuração. Esse recurso de inicialização está disponível no momento em que o dispositivo é registrado e bloqueado na tela inicial gerenciada. Nenhuma instalação adicional é necessária para usar essa funcionalidade.

## <a name="managed-home-screen-debug-screen"></a>Tela de depuração da tela inicial gerenciada
Você pode acessar a tela de depuração da tela inicial gerenciada clicando no botão **voltar** até que a tela de depuração seja exibida (clique no botão **voltar** 15 vezes ou mais). Nessa tela de depuração, você pode iniciar o aplicativo de política de dispositivo do Android, exibir e carregar logs ou pausar temporariamente o modo de quiosque para atualizar o dispositivo. Para obter mais informações sobre como pausar o modo de quiosque, consulte o item **sair do modo de quiosque** nas configurações do [dispositivo dedicado](../configuration/device-restrictions-android-for-work.md#dedicated-device-settings)do Android Enterprise.

## <a name="next-steps"></a>Próximos passos

- Para obter mais informações sobre dispositivos Android Enterprise dedicados, consulte [Configurar o registro do Intune de dispositivos Android Enterprise dedicados](../enrollment/android-kiosk-enroll.md).
