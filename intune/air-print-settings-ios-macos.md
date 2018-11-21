---
title: Definições do AirPrint do Intune para dispositivos iOS e macOS
titlesuffix: Microsoft Intune
description: Saiba como pode utilizar o Microsoft Intune para ajudar a ligar automaticamente os dispositivos iOS e macOS a impressoras compatíveis com o AirPrint.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/27/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 712a79fb-14ef-4f6b-aba5-1dfca900afd2
ms.reviewer: karanda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 850c61868cc5404d1645482a6998856e465b4070
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/20/2018
ms.locfileid: "52186295"
---
# <a name="airprint-settings-for-ios-and-macos-devices"></a>Definições do AirPrint para dispositivos iOS e macOS

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Utilize estas definições para configurar os dispositivos iOS e macOS para se ligarem automaticamente às impressoras compatíveis com o AirPrint na sua rede. Precisa do endereço IP e do caminho de recurso das impressoras para continuar.

## <a name="find-airprint-printer-information"></a>Localizar informações sobre a impressora com o AirPrint

Utilize este procedimento para adicionar informações do AirPrint ao payload do AirPrint para que os utilizadores de dispositivos iOS possam imprimir em impressoras conhecidas com o AirPrint.

1. Num Mac que esteja ligado à mesma rede local (sub-rede) que as impressoras com o AirPrint, abra o Terminal (em **/Applications/Utilities**)
2. No Terminal, escreva **ippfind** e, em seguida, prima Enter.
3. Tome nota das eventuais informações sobre a impressora que o comando devolve, por exemplo: **ipp://myprinter.local.:631/ipp/port1**. A primeira parte das informações é o nome da impressora e a última parte é o caminho do recurso.
4. No Terminal, escreva **ping myprinter.local** e, em seguida, prima Enter.
5. Tome nota das informações sobre o endereço IP devolvidas pelo comando como, por exemplo, **PING myprinter.local (10.50.25.21)**.
6. Por fim, utilize o endereço IP e o caminho do recurso nas definições de payload do AirPrint. Um exemplo de um endereço IP poderá ser **10.50.25.21** e um exemplo de um caminho do recurso poderá ser **/ipp/port1**.

## <a name="configure-an-airprint-profile"></a>Configurar um perfil do AirPrint

1. A partir do [Intune no Portal do Azure](https://portal.azure.com), navegue para [**Funcionalidades do dispositivo** na área de configuração do dispositivo](device-features-configure.md). 
1. No painel **Funcionalidades do dispositivo**, selecione **AirPrint**.
2. No painel **AirPrint**, para adicionar um destino do AirPrint, introduza o respetivo **endereço IP** e o **caminho do recurso** e, em seguida, clique em **Adicionar**.
3. Continue a adicionar destinos, conforme necessário. Quando terminar, escolha **OK**.

Também pode importar uma lista de impressoras de um ficheiro de valores separados por vírgulas (.csv) ou exportar a lista.


## <a name="next-steps"></a>Passos Seguintes

Agora pode atribuir o perfil do dispositivo aos grupos que selecionar. Para obter detalhes, veja [Como atribuir perfis de dispositivo](device-profile-assign.md).