---
title: Importar definições de Wi-Fi para dispositivos Windows no Microsoft Intune – Azure | Microsoft Docs
description: Exporte definições de Wi-Fi de um dispositivo Windows como um ficheiro XML através do comando netsh wlan. Em seguida, importe este ficheiro no Intune para criar um perfil Wi-Fi para dispositivos com o Windows 8.1, Windows 10 e Windows Holographic for Business.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 07/18/2018
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3452eb832f31377ddc9c55c5008405cb2235569b
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "61515012"
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
3. Execute o comando `netsh wlan show profiles` e tome nota do nome do perfil que pretende exportar. Neste exemplo, o nome do perfil é **WiFiName**.
4. Execute o `netsh wlan export profile name="ProfileName" folder=c:\Wifi` comando. Este comando o cria um ficheiro do perfil Wi-Fi com o nome **Wi-Fi-WiFiName.xml** na sua pasta de destino.

## <a name="import-the-wi-fi-settings-into-intune"></a>Importar as definições de Wi-Fi para o Intune

1. No [portal do Azure](https://portal.azure.com), selecione **Todos os serviços**, filtre o **Intune** e selecione **Microsoft Intune**.
2. Selecione **Configuração do dispositivo** > **Perfis** > **Criar perfil**.
3. Introduza um **Nome** e uma **Descrição** para o perfil de restrição de dispositivos.

    > [!IMPORTANT]
    > - O nome **tem** de ser igual ao atributo de nome no xml de perfil Wi-Fi. Caso contrário, falhará.
    > - Se estiver a exportar um perfil Wi-Fi que inclua uma chave pré-partilhada, **tem** de adicionar `key=clear` ao comando. Por exemplo, introduza: `netsh wlan export profile name="ProfileName" key=clear folder=c:\Wifi`
    > - A utilização de uma chave pré-partilhada no Windows 10 faz com que seja apresentado um erro de remediação no Intune. Quando isto acontece, o perfil Wi-Fi é atribuído corretamente ao dispositivo e funciona conforme esperado.
    > - Se exportar um perfil Wi-Fi que inclua uma chave pré-partilhada, certifique-se de que o ficheiro está protegido. Como a chave se encontra em texto simples, é sua responsabilidade protegê-la.

4. Em **Plataforma**, selecione **Windows 8.1 e versões posteriores**.
5. Em **Tipo de perfil**, selecione **Wi-Fi importado**.
6. Configure as seguintes definições:
    - **Nome da ligação**: Introduza um nome para a ligação Wi-Fi. Este nome é apresentado aos utilizadores finais ao procurarem redes Wi-Fi disponíveis.
    - **XML do perfil**: Selecione o botão Procurar e selecione o ficheiro XML que contém as definições de perfil de Wi-Fi a importar.
    - **Conteúdos do ficheiro**: Mostra o código XML para o perfil de configuração que selecionou.
7. Assim que terminar, selecione **OK** > **Criar** para guardar as alterações. O perfil é criado e é apresentado na lista de perfis.

## <a name="next-steps"></a>Passos Seguintes

O perfil é criado, mas não faz nada. Em seguida, [atribua este perfil](device-profile-assign.md).

## <a name="more-resources"></a>Mais recursos

[Descrição geral das definições de Wi-Fi](wi-fi-settings-configure.md), incluindo outras plataformas disponíveis.
