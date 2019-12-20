---
title: Importar definições de Wi-Fi para dispositivos Windows no Microsoft Intune – Azure | Microsoft Docs
description: Exporte definições de Wi-Fi de um dispositivo Windows como um ficheiro XML através do comando netsh wlan. Em seguida, importe este ficheiro no Intune para criar um perfil Wi-Fi para dispositivos com o Windows 8.1, Windows 10 e Windows Holographic for Business.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/18/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f79ccdc71ddbfa3f25daef629515fb612de01852
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/19/2019
ms.locfileid: "75207014"
---
# <a name="import-wi-fi-settings-for-windows-devices-in-intune"></a>Importar definições de Wi-Fi para dispositivos Windows no Intune

Para dispositivos com Windows, pode importar um perfil de configuração de Wi-Fi que tenha sido anteriormente exportado para um ficheiro. **Para dispositivos com o Windows 10 e posterior, também pode [criar um perfil Wi-Fi](wi-fi-settings-windows.md) diretamente no Intune**.

Aplica-se a:  
- Windows 8.1 e posterior
- Windows 10 e posterior
- Computadores ou dispositivos móveis com o Windows 10
- Windows Holographic for Business

## <a name="export-wi-fi-settings-from-a-windows-device"></a>Exportar definições de Wi-Fi a partir de um dispositivo Windows

No Windows, utilize `netsh wlan` para exportar um perfil Wi-Fi existente para um ficheiro XML, que pode ser lido pelo Intune. A chave tem de ser exportada em texto simples para utilizar o perfil com êxito.

Num computador Windows que já tenha o perfil Wi-Fi necessário instalado, siga estes passos:

1. Crie uma pasta local para os perfis Wi-Fi exportados, como **c:\WiFi**.
2. Abra uma Linha de Comandos como administrador.
3. Execute o comando `netsh wlan show profiles`. Observe o nome do perfil que você deseja exportar. Neste exemplo, o nome do perfil é **WiFiName**.
4. Execute o comando `netsh wlan export profile name="ProfileName" folder=c:\Wifi`. Este comando o cria um ficheiro do perfil Wi-Fi com o nome **Wi-Fi-WiFiName.xml** na sua pasta de destino.

## <a name="import-the-wi-fi-settings-into-intune"></a>Importar as definições de Wi-Fi para o Intune

1. Entre no centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selecione **dispositivos** > **perfis de configuração** > **Criar perfil**.
3. Introduza as seguintes definições:

    - **Nome**: Insira um nome descritivo para o perfil. O nome **tem** de ser igual ao atributo de nome no xml de perfil Wi-Fi. Caso contrário, falhará.
    - **Descrição**: introduza uma descrição que lhe permita obter uma descrição geral da definição e outros detalhes importantes.
    - **Plataforma**: selecione **Windows 8.1 e posterior**.
    - **Tipo de perfil**: selecione **importação de Wi-Fi**.

    > [!IMPORTANT]
    > - Se estiver a exportar um perfil Wi-Fi que inclua uma chave pré-partilhada, **tem** de adicionar `key=clear` ao comando. Por exemplo, introduza: `netsh wlan export profile name="ProfileName" key=clear folder=c:\Wifi`
    > - Usar uma chave pré-compartilhada com o Windows 10 faz com que um erro de correção seja mostrado no Intune. Quando isto acontece, o perfil Wi-Fi é atribuído corretamente ao dispositivo e funciona conforme esperado.
    > - Se exportar um perfil Wi-Fi que inclua uma chave pré-partilhada, certifique-se de que o ficheiro está protegido. Como a chave se encontra em texto simples, é sua responsabilidade protegê-la.

4. Introduza as seguintes definições:

    - **Nome da ligação**: introduza um nome para a ligação Wi-Fi. Esse nome é mostrado aos usuários quando eles navegam por redes Wi-Fi disponíveis.
    - **Perfil XML**: selecione o botão procurar e selecione o arquivo XML que contém as configurações de perfil de Wi-Fi que você deseja importar.
    - **Conteúdos do ficheiro**: mostra o código XML do perfil de configuração que selecionou.

5. Selecione **OK** para guardar as alterações.
6. Quando terminar, selecione **OK** > **criar** para criar o perfil do Intune. Ao concluir, seu perfil é mostrado na lista **dispositivos – perfis de configuração** .

## <a name="next-steps"></a>Próximos passos

O perfil é criado, mas não faz nada. Em seguida, [atribua o perfil](../device-profile-assign.md) e [monitorize o estado](device-profile-monitor.md).

Consulte a [visão geral das configurações de Wi-Fi](wi-fi-settings-configure.md), incluindo outras plataformas disponíveis.
