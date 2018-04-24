---
title: Configurar a gestão de Android
description: Ative a gestão de dispositivos móveis (MDM) para Android e dispositivos KNOX Standard com o Microsoft Intune.
keywords: ''
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 03/20/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: dbe5cad1-3e0d-41a9-966b-738156089700
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: lacranda
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: d1245f5644b24d258f8542252f8910789b63ba02
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/16/2018
---
# <a name="set-up-android-device-management"></a>Configurar a gestão de dispositivos Android

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Como administrador do Intune, pode ativar a gestão de dispositivos Android, incluindo dispositivos Samsung Knox Standard a partir do Portal da Empresa. Os utilizadores podem então inscrever os respetivos dispositivos com a aplicação Portal da Empresa disponível no Google Play.

Por predefinição, é permitido inscrever dispositivos Android no Intune. Para bloquear a inscrição de dispositivos Android, inicie sessão no [Portal de administração do Microsoft Intune](https://manage.microsoft.com) com as suas credenciais de administrador. Selecione **Admin** > **Gestão de Dispositivos Móveis** > **Regras de Inscrição** e, em seguida, desmarque a caixa de verificação **Permitir dispositivos Android**.

1. **Configurar o Intune**<br>
   Se ainda não o fez, prepare a gestão de dispositivos móveis ao [definir a autoridade de gestão de dispositivos móveis](prerequisites-for-enrollment.md#step-2-set-mdm-authority) como **Microsoft Intune** e ao configurar a MDM.

2. **Inscrição de dispositivos Android ativada**<br>
   Não são necessárias configurações adicionais na consola do Intune para ativar a inscrição de dispositivos móveis Android.

3. **Indique aos utilizadores como devem inscrever os respetivos dispositivos para poderem aceder aos recursos da empresa.**

   Para obter instruções de inscrição do utilizador final, veja [Inscrever o dispositivo Android no Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android). O processo de inscrição informa os utilizadores sobre o que podem esperar e o que os administradores de TI podem e não podem ver nos respetivos dispositivos.

   Para obter informações sobre outras tarefas do utilizador final, veja estes artigos:
   - [Recursos sobre a experiência do utilizador final com o Microsoft Intune](/intune/end-user-educate)
   - [Orientações para o utilizador final sobre os dispositivos Android](https://docs.microsoft.com/intune-user-help/using-your-android-device-with-intune)

Devido ao facto de a Google Play Store não estar disponível na China, os dispositivos Android têm de obter o Portal da Empresa a partir das lojas de aplicações chinesas. A aplicação Portal da Empresa para Android estará disponível para transferência através das seguintes lojas:
* [Baidu](https://go.microsoft.com/fwlink/?linkid=836946)
* [Huawei](https://go.microsoft.com/fwlink/?linkid=836948)
* [Tencent](https://go.microsoft.com/fwlink/?linkid=836949)
* [Wandoujia](https://go.microsoft.com/fwlink/?linkid=836950)
* [Xiaomi](https://go.microsoft.com/fwlink/?linkid=836947)

A aplicação Portal da Empresa para Android utiliza os Serviços do Google Play para comunicar com o serviço Microsoft Intune. Uma vez que os Serviços do Google Play ainda não estão disponíveis na China, pode demorar até 8 horas a concluir a realização de qualquer uma das seguintes tarefas. 

|Consola de Administração do Intune| Aplicação Portal da Empresa do Intune para Android |Site do Portal da Empresa do Intune|   
|---|---|---|
|Eliminação completa| Remover um dispositivo remoto| Remover dispositivo (local e remoto)|
|Eliminação seletiva| Repor dispositivo| Repor dispositivo|
|Implementações de aplicações novas ou atualizadas| Instalar aplicações de linha de negócio disponíveis| Repor código de acesso do dispositivo|
|Bloqueio remoto|||
|Repor código de acesso|||

### <a name="see-also"></a>Consulte também
[Pré-requisitos para a inscrição de dispositivos no Microsoft Intune](prerequisites-for-enrollment.md)
