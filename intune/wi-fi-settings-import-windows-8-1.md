---
title: Importar definições de Wi-Fi para dispositivos Windows no Microsoft Intune – Azure | Microsoft Docs
description: Exporte definições de Wi-Fi de um dispositivo Windows como um ficheiro XML através do comando netsh wlan. Em seguida, importe este ficheiro no Intune para criar um perfil Wi-Fi para dispositivos com o Windows 8.1, Windows 10 e Windows Holographic for Business.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 07/18/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 6ce5cdd9509ed3407491714ccfa853613eb43973
ms.sourcegitcommit: e8e8164586508f94704a09c2e27950fe6ff184c3
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/27/2018
ms.locfileid: "39321140"
---
# <a name="import-wi-fi-settings-for-windows-devices-in-intune"></a>Importar definições de Wi-Fi para dispositivos Windows no Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Para dispositivos com Windows, pode importar um perfil de configuração de Wi-Fi que tenha sido anteriormente exportado para um ficheiro. **Para dispositivos com o Windows 10 e posterior, pode [criar um perfil Wi-Fi](wi-fi-settings-windows.md) diretamente no Intune**.

Aplica-se a:  
- Windows 8.1 e posterior
- Windows 10 e posterior
- Computadores ou dispositivos móveis com o Windows 10
- Windows Holographic for Business

## <a name="export-wi-fi-settings-from-a-windows-device"></a>Exportar definições de Wi-Fi a partir de um dispositivo Windows

No Windows, utilize o comando **netsh wlan** para exportar um perfil Wi-Fi existente para um ficheiro XML, que pode ser lido pelo Intune. A chave tem de ser exportada em texto simples para utilizar o perfil com êxito.

Num computador Windows que já tenha o perfil Wi-Fi necessário instalado, siga estes passos:

1. Crie uma pasta local para os perfis Wi-Fi exportados, como **c:\WiFi**.
2. Abra uma Linha de Comandos como administrador.
3. Execute o comando `netsh wlan show profiles` e tome nota do nome do perfil que pretende exportar. Neste exemplo, o nome do perfil é **WiFiName**.
4. Execute o comando `netsh wlan export profile name="ProfileName" folder=c:\Wifi`. Esta ação cria um ficheiro do perfil Wi-Fi com o nome **Wi-Fi-WiFiName.xml** na sua pasta de destino.

## <a name="import-the-wi-fi-settings-into-intune"></a>Importar as definições de Wi-Fi para o Intune

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços**, filtre por **Intune** e selecione **Microsoft Intune**.
3. Selecione **Configuração do dispositivo** > **Perfis** > **Criar perfil**.
4. Introduza um **Nome** e uma **Descrição** para o perfil de restrição de dispositivos.

    > [!IMPORTANT]
    > - O nome **tem** de ser igual ao atributo de nome no xml de perfil Wi-Fi. Caso contrário, falhará.
    > - Se estiver a exportar um perfil Wi-Fi que inclua uma chave pré-partilhada, **tem** de adicionar `key=clear` ao comando. Por exemplo, introduza: `netsh wlan export profile name="ProfileName" key=clear folder=c:\Wifi`
    > - A utilização de uma chave pré-partilhada no Windows 10 faz com que seja apresentado um erro de remediação no Intune. Quando isto acontece, o perfil Wi-Fi é atribuído corretamente ao dispositivo e funciona conforme esperado.
    > - Se exportar um perfil Wi-Fi que inclua uma chave pré-partilhada, certifique-se de que o ficheiro está protegido. Como a chave se encontra em texto simples, é sua responsabilidade protegê-la.

5. Em **Plataforma**, selecione **Windows 8.1 e versões posteriores**.
6. Em **Tipo de perfil**, selecione **Wi-Fi importado**.
7. Configure as seguintes definições:
  - **Nome da ligação**: introduza um nome para a ligação Wi-Fi. Este nome é apresentado aos utilizadores finais ao procurarem redes Wi-Fi disponíveis.
  - **XML do perfil**: selecione o botão Procurar para selecionar o ficheiro XML que contém as definições do perfil Wi-Fi a importar para o Intune.
  - **Conteúdos do ficheiro**: mostra o código XML do perfil de configuração que selecionou.
8. Quando terminar, selecione **OK** e, em seguida, selecione a opção para **Criar** o perfil.

O perfil será criado e apresentado na lista de perfis.
