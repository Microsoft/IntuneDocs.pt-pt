---
title: Importar definições de Wi-Fi do Windows 8.1 e posterior
titleSuffix: Microsoft Intune
description: Como importar definições de Wi-Fi do Windows para um perfil Wi-Fi do Intune.
keywords: ''
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 03/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 033b60fded23f5a1dac5c8ff93716dac77c56fe2
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/16/2018
---
# <a name="import-wi-fi-settings-for-windows-81-and-later-devices-in-microsoft-intune"></a>Importar definições de Wi-Fi do Windows 8.1 e de dispositivos posteriores no Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Para dispositivos a executar o Windows 8.1, o Windows 10 ou Windows 10 Mobile ou o Windows Holographic for Business, pode importar um perfil de configuração Wi-Fi anteriormente exportado para um ficheiro.

## <a name="export-wi-fi-settings-from-a-windows-device"></a>Exportar definições de Wi-Fi a partir de um dispositivo Windows

No Windows, utilize o utilitário **netsh wlan** para exportar um perfil de Wi-Fi existente para um ficheiro XML, que pode ser lido pelo Intune. A chave tem de ser exportada em texto simples para utilizar o perfil com êxito.

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
