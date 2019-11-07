---
title: Ver detalhes de dispositivos com o Microsoft Intune – Azure | Microsoft Docs
description: Veja os detalhes do seu dispositivo, incluindo sistemas operativos, espaço de armazenamento, fabricante e modelo. Obtenha uma lista de aplicações instaladas, verifique as políticas de conformidade e configure o TeamViewer com o Microsoft Intune no Azure. Semelhante a ver o inventário dos dispositivos que gere.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: e71c6bdb-d75c-404f-8e38-24a663be81c2
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 918468bf8948ce54082f3fccc0325db07e116966
ms.sourcegitcommit: 28622c5455adfbce25a404de4d0437fa2b5370be
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/07/2019
ms.locfileid: "73713197"
---
# <a name="see-device-details-in-intune"></a>Consultar os detalhes do dispositivo no Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

A funcionalidade **Dispositivos** fornece detalhes adicionais para os dispositivos que gere, incluindo o respetivo hardware e as aplicações instaladas.

Este artigo mostra como ver todos os seus dispositivos e as respetivas propriedades no portal do Azure.

## <a name="view-the-device-details"></a>Ver os detalhes do dispositivo

1. Entre no centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
3. Selecione **Dispositivos** > **Todos os dispositivos** e selecione um dos seus dispositivos apresentados para abrir os respetivos detalhes:

   - **Visão geral** mostra o nome do dispositivo e lista algumas das principais propriedades do dispositivo, como se ele é um dispositivo BYOD (Traga seu próprio dispositivo), o check-in-time e muito mais. Você pode fazer o seguinte no dispositivo:
      - [Extinguir](devices-wipe.md#retire)
      - [Eliminação](devices-wipe.md#wipe)
      - [Bloqueio remoto](device-remote-lock.md)
      - [Sincronizar o dispositivo](device-sync.md)
      - [Repor código de acesso](device-passcode-reset.md)
      - [Reiniciar](device-restart.md) (apenas no Windows)
      - [Começar do Zero](device-fresh-start.md) (apenas no Windows)
      - Iniciar uma sessão de assistência remota
   - Utilize as **Propriedades** para atribuir uma [categoria de dispositivo que tenha criado](../enrollment/device-group-mapping.md) e alterar a propriedade do dispositivo para um dispositivo pessoal ou um dispositivo da empresa.
   - O **hardware** inclui muitos detalhes sobre o dispositivo, como a ID do dispositivo, o sistema operacional e a versão, o espaço de armazenamento e mais detalhes.
   - **Aplicações detetadas**: apresenta uma lista de todas as aplicações que o Intune encontrou instaladas no dispositivo e das versões das aplicações. Para obter mais informações, consulte [aplicativos descobertos do Intune](../apps/app-discovered-apps.md).
   - **Conformidade do dispositivo**: apresenta uma lista de todas as políticas de conformidade atribuídas e indica se o dispositivo está ou não em conformidade.
   - **Configuração do dispositivo**: mostra todas as políticas de configuração de dispositivos atribuídas ao dispositivo e indica se a política foi concluída com êxito ou falhou.

## <a name="hardware-device-details"></a>Detalhes de dispositivos de hardware
Dependendo da operadora usada pelos dispositivos, nem todos os detalhes podem ser coletados

> [!Note]  
> O inventário de hardware e software é atualizado no serviço do Intune a cada 7 dias.

|Detalhes|Description|Platform| 
|--------------|----------------------|----|  
|Nome|O nome do dispositivo.|Windows, iOS|
|Nome da gestão|O nome do dispositivo utilizado apenas na consola. Alterar este nome não irá alterar o nome no dispositivo.|Windows, iOS|
|UDID|O Identificador de Dispositivo Exclusivo do dispositivo.|Windows, iOS|
|ID de Dispositivo do Intune|Um GUID que identifica exclusivamente o dispositivo.|Windows, iOS|
|Número de série|O número de série dado pelo fabricante do dispositivo.|Windows, iOS|
|Dispositivo partilhado|Se definido como **Sim**, o dispositivo é partilhado por mais do que um utilizador.|Windows, iOS|
|Inscrição de utilizador aprovado|Em caso **afirmativo**, o dispositivo tem o registro aprovado pelo usuário que permite que os administradores gerenciem determinadas configurações de segurança no dispositivo.|Windows, iOS|
|Sistema operativo|O sistema operativo utilizado no dispositivo.|Windows, iOS|
|Versão do sistema operativo|A versão do sistema operacional no dispositivo.|Windows, iOS|
|Idioma do sistema operativo|O idioma definido para o sistema operativo no dispositivo.|Windows, iOS|
|Número de Build|O número de Build do sistema operacional.|Android|
|Nível de patch de segurança|O nível de patch de segurança para o dispositivo.|Android|
|Espaço de armazenamento total|O espaço de armazenamento total no dispositivo (em gigabytes).|Windows, iOS|
|Espaço de armazenamento livre|O espaço de armazenamento não utilizado no dispositivo (em gigabytes).|Windows, iOS|
|IMEI|A Identidade Internacional do Equipamento Móvel do dispositivo.|Windows, iOS, Android|
|MEID|O identificador de equipamento móvel do dispositivo.|Windows, iOS, Android|
|Manufacturer|O fabricante do dispositivo.|Windows, iOS, Android|
|Model|O modelo do dispositivo.|Windows, iOS, Android|
|Número de telefone|O número de telemóvel atribuído ao dispositivo.|Windows, iOS, Android|
|Operadora subscrita|A operadora sem fios do dispositivo.|Windows, iOS, Android|
|Tecnologia de rede móvel|O sistema de rádio utilizado pelo dispositivo.|Windows, iOS, Android|
|MAC Wi-Fi|O endereço MAC (Media Access Control) do dispositivo.|Windows, iOS, Android|
|ICCID|O Identificador de Cartão de Circuito Integrado, que é o número de identificação exclusivo de um cartão SIM.|Windows, iOS, Android|
|Data de inscrição|A data e hora em que o dispositivo foi inscrito no Intune.|Windows, iOS, Android|
|Último contacto|A data e hora em que o dispositivo foi ligado pela última vez ao Intune.|Windows, iOS, Android|
|Código para ignorar o bloqueio de ativação|O código que pode ser utilizado para ignorar o bloqueio de ativação.|Windows, iOS, Android|
|Azure AD registado|Se definido como **Sim**, o dispositivo é registado com o Azure Directory.|Windows, iOS, Android|
|Registrado no Intune|Se **Sim**, o dispositivo está registrado no Intune|Windows, iOS, Android|
|Conformidade|O estado de conformidade do dispositivo.|Windows, iOS, Android|
|EAS ativado|Se definido como **Sim**, o dispositivo é sincronizado com a caixa de correio do Exchange.|Windows, iOS, Android|
|ID de ativação do EAS|O identificador do Exchange ActiveSync do dispositivo.|Windows, iOS, Android|
|Supervisionado|Se definido como **Sim**, os administradores têm controlo avançado sobre o dispositivo.|Windows, iOS, Android|
|Encriptado|Se definido como **Sim**, os dados armazenados no dispositivo são encriptados.|Windows, iOS, Android|



## <a name="next-steps"></a>Próximos passos
Veja o que mais pode fazer para [gerir os seus dispositivos](device-management.md) com o Intune.
