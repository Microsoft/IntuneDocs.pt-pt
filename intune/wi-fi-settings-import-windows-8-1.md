---
title: "Importar definições de Wi-Fi do Windows 8.1 e posterior"
titleSuffix: Intune Azure preview
description: "Pré-visualização do Azure no Intune: como importar definições de Wi-Fi do Windows para um perfil Wi-Fi do Intune."
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2c4e9b19-b268-4f6d-9663-7cdbe4e4a8dd
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 80181ce809265dc4289e56ef65aff66214d2e765
ms.contentlocale: pt-pt
ms.lasthandoff: 05/23/2017


---

# <a name="how-to-import-wi-fi-settings-for-windows-81-and-later-devices-in-microsoft-intune"></a>Como importar as definições de Wi-Fi do Windows 8.1 e de dispositivos posteriores para o Microsoft Intune

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

Para dispositivos com Windows 8.1 ou Windows 10 Desktop ou Mobile, pode importar um perfil de configuração de Wi-Fi que tenha sido exportado anteriormente para um ficheiro.

## <a name="export-wi-fi-settings-from-a-windows-device"></a>Exportar definições de Wi-Fi a partir de um dispositivo Windows

No Windows, utilize o utilitário **netsh wlan** para exportar um perfil de Wi-Fi existente para um ficheiro XML, que pode ser lido pelo Intune. Num computador Windows que já tenha o perfil de Wi-Fi necessário instalado, siga este procedimento.
1. Crie uma pasta local para os perfis Wi-Fi exportados, como **c:\WiFi**.
1. Abra uma Linha de Comandos como administrador.
1. Execute o comando **netsh wlan show profiles** e tome nota do nome do perfil que pretende exportar. Neste exemplo, o nome do perfil é **WiFiName**.
1. Execute o comando **netsh wlan export profile name="ProfileName" folder=c:\Wifi**. Esta ação criará um ficheiro do perfil Wi-Fi com o nome **Wi-Fi-WiFiName.xml** na pasta de destino.

## <a name="import-the-wi-fi-settings-into-intune"></a>Importar as definições de Wi-Fi para o Intune

1. Inicie sessão no portal do Azure.
2. Escolha **Mais Serviços** > **Outros** > **Intune**.
3. No painel **Intune**, escolha **Configuração do dispositivo**.
2. No painel **Configuração do Dispositivo**, escolha **Gerir** > **Perfis**.
3. No painel de perfis, clique em **Criar Perfil**.
4. No painel **Criar Perfil**, introduza um **Nome** e uma **Descrição** para o perfil de restrição de dispositivos.
5. Na lista pendente **Plataforma**, escolha **Windows 8.1 e posterior**.
6. Na lista pendente **erfil**, escolha **Importação de Wi-Fi**.
7. No painel **Wi-Fi Básico**, configure as seguintes opções:
    - **Nome da ligação** – Introduza o nome da ligação Wi-Fi. Este nome será apresentado aos utilizadores finais quando procurarem redes Wi-Fi disponíveis.
    - **XML do perfil** – Clique no botão Procurar para selecionar o ficheiro XML que contém as definições de perfil de Wi-Fi a importar para o Intune.
    - **Conteúdo do ficheiro** – Apresenta o código XML do perfil de configuração que selecionou.
8. Quando tiver terminado, volte ao painel **Criar Perfil** e clique em **Criar**.

O perfil será criado e é apresentado no painel da lista de perfis.
