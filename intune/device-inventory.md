---
title: Ver detalhes de dispositivos com o Microsoft Intune – Azure | Microsoft Docs
description: Veja os detalhes do seu dispositivo, incluindo sistemas operativos, espaço de armazenamento, fabricante e modelo. Obtenha uma lista de aplicações instaladas, verifique as políticas de conformidade e configure o TeamViewer com o Microsoft Intune no Azure. Semelhante a ver o inventário dos dispositivos que gere.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: e71c6bdb-d75c-404f-8e38-24a663be81c2
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 404fb301d9ab749f887840208e12388e12d79db4
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/16/2018
---
# <a name="see-device-details-in-intune"></a>Consultar os detalhes do dispositivo no Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

A funcionalidade **Dispositivos** fornece detalhes adicionais para os dispositivos que gere, incluindo o respetivo hardware e as aplicações instaladas.

Este artigo mostra como ver todos os seus dispositivos e as respetivas propriedades no portal do Azure.

## <a name="view-the-device-details"></a>Ver os detalhes do dispositivo

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços**, filtre por **Intune** e selecione **Microsoft Intune**.
3. Selecione **Dispositivos** > **Todos os dispositivos** e selecione um dos seus dispositivos apresentados para abrir os respetivos detalhes:

   - **Descrição Geral**: mostra o nome do dispositivo e apresenta uma lista de algumas propriedades chave do dispositivo, incluindo se é um dispositivo BYOD (Bring Your Own Device), quando foi registado e mais. Selecione **Mais** para:
     - Remover dados da empresa
     - Eliminar o dispositivo
     - Bloquear o dispositivo remotamente
     - Apagar
     - Iniciar uma sessão de assistência remota
   - Utilize as **Propriedades** para atribuir uma [categoria de dispositivo que tenha criado](device-group-mapping.md) e alterar a propriedade do dispositivo para um dispositivo pessoal ou um dispositivo da empresa.
   - **Hardware**: inclui muitos detalhes sobre o dispositivo, incluindo o ID do dispositivo, o sistema operativo e a versão, o espaço de armazenamento, o modelo e o fabricante, as definições de acesso condicional e mais detalhes.
   - **Aplicações detetadas**: apresenta uma lista de todas as aplicações que o Intune encontrou instaladas no dispositivo e das versões das aplicações. Também pode **Exportar** a lista de aplicações para um ficheiro .csv.
   - **Conformidade do dispositivo**: apresenta uma lista de todas as políticas de conformidade atribuídas e indica se o dispositivo está ou não em conformidade.
   - **Configuração do dispositivo**: mostra todas as políticas de configuração de dispositivos atribuídas ao dispositivo e indica se a política foi concluída com êxito ou falhou.

O Intune recolhe uma lista de aplicações apenas nos dispositivos pertencentes à empresa. As aplicações não são verificadas nos dispositivos pessoais. Para PCs com o Windows 10, apenas é apresentada a lista de aplicações modernas em dispositivos pertencentes à empresa. O Intune não recolhe informações de aplicações Win32 no dispositivo. Consoante a utilização da operadora pelos dispositivos, nem todas as aplicações devem ser recolhidas.

## <a name="next-steps"></a>Próximos passos
Veja o que mais pode fazer para [gerir os seus dispositivos](device-management.md) com o Intune.