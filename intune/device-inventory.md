---
title: Ver detalhes de dispositivos com o Microsoft Intune – Azure | Microsoft Docs
description: Veja os detalhes do seu dispositivo, incluindo sistemas operativos, espaço de armazenamento, fabricante e modelo. Obtenha uma lista de aplicações instaladas, verifique as políticas de conformidade e configure o TeamViewer com o Microsoft Intune no Azure. Semelhante a ver o inventário dos dispositivos que gere.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/10/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: e71c6bdb-d75c-404f-8e38-24a663be81c2
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c22822f34f426897549383df5e9c71b21b497a7e
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/14/2019
ms.locfileid: "57391204"
---
# <a name="see-device-details-in-intune"></a>Consultar os detalhes do dispositivo no Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

A funcionalidade **Dispositivos** fornece detalhes adicionais para os dispositivos que gere, incluindo o respetivo hardware e as aplicações instaladas.

Este artigo mostra como ver todos os seus dispositivos e as respetivas propriedades no portal do Azure.

## <a name="view-the-device-details"></a>Ver os detalhes do dispositivo

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços**, filtre por **Intune** e selecione **Microsoft Intune**.
3. Selecione **Dispositivos** > **Todos os dispositivos** e selecione um dos seus dispositivos apresentados para abrir os respetivos detalhes:

   - **Descrição Geral**: mostra o nome do dispositivo e apresenta uma lista de algumas propriedades chave do dispositivo, incluindo se é um dispositivo BYOD (Bring Your Own Device), quando foi registado e mais. Pode realizar as seguintes ações no dispositivo:
      - [Extinguir](devices-wipe.md#retire)
        - [Eliminação](devices-wipe.md#wipe)
        - [Bloqueio remoto](device-remote-lock.md)
        - [Sincronizar o dispositivo](device-sync.md)
        - [Repor código de acesso](device-passcode-reset.md)
        - [Reiniciar](device-restart.md) (apenas no Windows)
        - [Começar do Zero](device-fresh-start.md) (apenas no Windows)
     - Iniciar uma sessão de assistência remota
   - Utilize as **Propriedades** para atribuir uma [categoria de dispositivo que tenha criado](device-group-mapping.md) e alterar a propriedade do dispositivo para um dispositivo pessoal ou um dispositivo da empresa.
   - **Hardware**: inclui muitos detalhes sobre o dispositivo, incluindo o ID do dispositivo, o sistema operativo e a versão, o espaço de armazenamento, o modelo e o fabricante, as definições de acesso condicional e mais detalhes.
   - **Aplicações detetadas**: apresenta uma lista de todas as aplicações que o Intune encontrou instaladas no dispositivo e das versões das aplicações. Também pode **Exportar** a lista de aplicações para um ficheiro .csv. Esta lista é atualizada a cada 7 dias.
   - **Conformidade do dispositivo**: apresenta uma lista de todas as políticas de conformidade atribuídas e indica se o dispositivo está ou não em conformidade.
   - **Configuração do dispositivo**: mostra todas as políticas de configuração de dispositivos atribuídas ao dispositivo e indica se a política foi concluída com êxito ou falhou.

O Intune recolhe uma lista de aplicações apenas nos dispositivos pertencentes à empresa. As aplicações não são verificadas nos dispositivos pessoais. Para PCs com o Windows 10, apenas é apresentada a lista de aplicações modernas em dispositivos pertencentes à empresa. O Intune não recolhe informações de aplicações Win32 no dispositivo. Consoante a utilização da operadora pelos dispositivos, nem todas as aplicações devem ser recolhidas.

|Plataforma|Para dispositivos pessoais|Para dispositivos pertencentes à empresa|  
|--------------|---------------------------------|--------------------------------|  
|Windows 10 (sem o cliente do Configuration Manager)|Apenas aplicações geridas|Apenas aplicações geridas|
|Windows 8.1 (sem o cliente do Configuration Manager)|Apenas aplicações geridas|Apenas aplicações geridas|  
|Windows Phone 8|Apenas aplicações geridas|Apenas aplicações geridas|  
|Windows RT|Apenas aplicações geridas|Apenas aplicações geridas|  
|iOS|Apenas aplicações geridas|Todas as aplicações instaladas no dispositivo|
|macOS|Todas as aplicações instaladas no dispositivo|Todas as aplicações instaladas no dispositivo|  
|Android|Apenas aplicações geridas|Todas as aplicações instaladas no dispositivo|  
|Android Enterprise|Apenas aplicações geridas|Apenas as aplicações instaladas no perfil de trabalho|  

## <a name="hardware-device-details"></a>Detalhes de dispositivos de hardware
Consoante a operadora utilizada pelos dispositivos, nem todos os detalhes podem ser recolhidos

|Detalhe|Descrição|Plataforma| 
|--------------|----------------------|----|  
|Nome|O nome do dispositivo.|Windows, iOS|
|Nome da gestão|O nome do dispositivo utilizado apenas na consola. Alterar este nome não irá alterar o nome no dispositivo.|Windows, iOS|
|UDID|O Identificador de Dispositivo Exclusivo do dispositivo.|Windows, iOS|
|ID de Dispositivo do Intune|Um GUID que identifica exclusivamente o dispositivo.|Windows, iOS|
|Número de série|O número de série dado pelo fabricante do dispositivo.|Windows, iOS|
|Dispositivo partilhado|Se definido como **Sim**, o dispositivo é partilhado por mais do que um utilizador.|Windows, iOS|
|Inscrição de utilizador aprovado|Se definido como **Sim**, a inscrição do dispositivo foi aprovada pelo utilizador, o que permite aos administradores gerir determinadas definições de segurança no mesmo.|Windows, iOS|
|Sistema operativo|O sistema operativo utilizado no dispositivo.|Windows, iOS|
|Versão do sistema operativo|A versão do sistema operativo do dispositivo.|Windows, iOS|
|Idioma do sistema operativo|O idioma definido para o sistema operativo no dispositivo.|Windows, iOS|
|Espaço de armazenamento total|O espaço de armazenamento total no dispositivo (em gigabytes).|Windows, iOS|
|Espaço de armazenamento livre|O espaço de armazenamento não utilizado no dispositivo (em gigabytes).|Windows, iOS|
|IMEI|A Identidade Internacional do Equipamento Móvel do dispositivo.|Windows, iOS, Android|
|MEID|O identificador de equipamento móvel do dispositivo.|Windows, iOS, Android|
|Fabricante|O fabricante do dispositivo.|Windows, iOS, Android|
|Modelo|O modelo do dispositivo.|Windows, iOS, Android|
|Número de telefone|O número de telemóvel atribuído ao dispositivo.|Windows, iOS, Android|
|Operadora subscrita|A operadora sem fios do dispositivo.|Windows, iOS, Android|
|Tecnologia de rede móvel|O sistema de rádio utilizado pelo dispositivo.|Windows, iOS, Android|
|MAC Wi-Fi|O endereço MAC (Media Access Control) do dispositivo.|Windows, iOS, Android|
|ICCID|O Identificador de Cartão de Circuito Integrado, que é o número de identificação exclusivo de um cartão SIM.|Windows, iOS, Android|
|Data de inscrição|A data e hora em que o dispositivo foi inscrito no Intune.|Windows, iOS, Android|
|Último contacto|A data e hora em que o dispositivo foi ligado pela última vez ao Intune.|Windows, iOS, Android|
|Código para ignorar o bloqueio de ativação|O código que pode ser utilizado para ignorar o bloqueio de ativação.|Windows, iOS, Android|
|Azure AD registado|Se definido como **Sim**, o dispositivo é registado com o Azure Directory.|Windows, iOS, Android|
|Conformidade|O estado de conformidade do dispositivo.|Windows, iOS, Android|
|EAS ativado|Se definido como **Sim**, o dispositivo é sincronizado com a caixa de correio do Exchange.|Windows, iOS, Android|
|ID de ativação do EAS|O identificador do Exchange ActiveSync do dispositivo.|Windows, iOS, Android|
|Supervisionado|Se definido como **Sim**, os administradores têm controlo avançado sobre o dispositivo.|Windows, iOS, Android|
|Encriptado|Se definido como **Sim**, os dados armazenados no dispositivo são encriptados.|Windows, iOS, Android|



## <a name="next-steps"></a>Passos Seguintes
Veja o que mais pode fazer para [gerir os seus dispositivos](device-management.md) com o Intune.
