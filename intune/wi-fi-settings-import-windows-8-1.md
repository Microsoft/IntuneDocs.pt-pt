---
title: "Importar definições de Wi-Fi do Windows 8.1 e posterior"
titleSuffix: Azure portal
description: "Como importar definições de Wi-Fi do Windows para um perfil Wi-Fi do Intune.\""
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 1/25/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 5b4b77f9c9c1c957e3332c20e010a5e8e8ec2b56
ms.sourcegitcommit: 93622d740cbd12043eedc25a9699cc4256e23e7e
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/01/2018
---
# <a name="how-to-import-wi-fi-settings-for-windows-81-and-later-devices-in-microsoft-intune"></a>Como importar as definições de Wi-Fi do Windows 8.1 e de dispositivos posteriores para o Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Para dispositivos a executar o Windows 8.1, o Windows 10 ou Windows 10 Mobile ou o Windows Holographic for Business, pode importar um perfil de configuração Wi-Fi anteriormente exportado para um ficheiro.

## <a name="export-wi-fi-settings-from-a-windows-device"></a>Exportar definições de Wi-Fi a partir de um dispositivo Windows

No Windows, utilize o utilitário **netsh wlan** para exportar um perfil de Wi-Fi existente para um ficheiro XML, que pode ser lido pelo Intune. Num computador Windows que já tenha o perfil de Wi-Fi necessário instalado, siga este procedimento.
1. Crie uma pasta local para os perfis Wi-Fi exportados, como **c:\WiFi**.
1. Abra uma Linha de Comandos como administrador.
1. Execute o comando **netsh wlan show profiles** e tome nota do nome do perfil que pretende exportar. Neste exemplo, o nome do perfil é **WiFiName**.
1. Execute o comando **netsh wlan export profile name="ProfileName" folder=c:\Wifi**. Esta ação cria um ficheiro do perfil Wi-Fi com o nome **Wi-Fi-WiFiName.xml** na pasta de destino.

## <a name="import-the-wi-fi-settings-into-intune"></a>Importar as definições de Wi-Fi para o Intune

1. Inicie sessão no portal do Azure.
2. Escolha **Mais Serviços** > **Monitorização + Gestão** > **Intune**.
3. No painel **Intune**, escolha **Configuração do dispositivo**.
2. No painel **Configuração do Dispositivo**, escolha **Gerir** > **Perfis**.
3. No painel de perfis, clique em **Criar Perfil**.
4. No painel **Criar Perfil**, introduza um **Nome** e uma **Descrição** para o perfil de restrição de dispositivos.

   > [!WARNING]
   > O nome **tem** de ser igual ao atributo no perfil Wi-Fi xml, caso contrário ocorrerá uma falha.

5. Na lista pendente **Plataforma**, escolha **Windows 8.1 e posterior**.
6. Na lista pendente **Perfil**, escolha **Importação de Wi-Fi**.
7. No painel **Wi-Fi Básico**, configure as seguintes definições:
    - **Nome da ligação** – Introduza o nome da ligação Wi-Fi. Este nome é apresentado aos utilizadores finais ao procurarem redes Wi-Fi disponíveis.
    - **XML do perfil** – Clique no botão Procurar para selecionar o ficheiro XML que contém as definições de perfil de Wi-Fi a importar para o Intune.
    - **Conteúdo do ficheiro** – Apresenta o código XML do perfil de configuração que selecionou.
8. Quando tiver terminado, volte ao painel **Criar Perfil** e clique em **Criar**.

O perfil é criado e apresentado no painel da lista de perfis.
