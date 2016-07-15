---
title: "Definições de política de configuração do Windows Team | Microsoft Intune"
description: 
keywords: 
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 38194ef3-e26e-4682-958d-14b395fccba1
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 42e21b802fb605c98f688485c3b77703b3950e94
ms.openlocfilehash: b08d52289b94429b1328a7470469a7efdf4d46a7


---

# Definições de política de configuração do Windows Team no Microsoft Intune
Utilize a **Política de configuração geral do Windows 10 Team** do Microsoft Intune para configurar definições para dispositivos Windows 10 Team inscritos, como o Microsoft Surface Hub.

|Nome da definição|Detalhes|
|----------------|-----------|
|**Permitir ao ecrã ser reativado automaticamente quando alguém está na sala**|Permite ao dispositivo ser reativado automaticamente quando o respetivo sensor deteta alguém na sala.|
|**Exigir PIN para projeção sem fios**|Especifica se deve introduzir um PIN antes de poder utilizar as capacidades de projeção sem fios do dispositivo.|
|**Definir uma janela de manutenção para atualizações ao dispositivo**|Configura a janela quando podem ocorrer atualizações ao dispositivo. Pode configurar a hora de início da janela e a duração (de 1 a 5 horas).|
|**Ativar as Informações Operacionais do Azure**|As Informações Operacionais do Azure, parte do conjunto de aplicações Microsoft Operations Manager, recolhe, armazena e analisa os dados dos ficheiros de registo a partir de dispositivos Windows 10 Team.<br /><br />Para ligar às Informações Operacionais do Azure, tem de especificar um **ID da Área de Trabalho** e uma **Chave da Área de Trabalho**.|
|**Ativar projeção sem fios Miracast**|Ative esta opção se pretender permitir que o dispositivo Windows 10 Team utilize dispositivos preparados para Miracast para projeção.<br /><br />Se ativar esta opção, em **Escolher canal Miracast**, selecione o canal Miracast utilizado para projetar conteúdo.|
|**Escolher as informações de reunião apresentadas no ecrã de boas-vindas**|Se ativar esta opção, pode escolher as informações que serão apresentadas no mosaico **Reuniões** do ecrã **Bem-vindo**. É possível:<br /><br />-   **Mostrar apenas organizador e hora**<br />-   **Mostrar organizador, hora e assunto (assunto oculto para reuniões privadas)**|
|**URL da imagem de fundo do ecrã de bloqueio**|Ative esta definição para apresentar um fundo personalizado do ecrã **Bem-vindo** dos dispositivos Windows 10 Team a partir do URL especificado.<br /><br />A imagem tem de estar no formato PNG e o URL tem de começar por **https://**.|


### Consulte também
[Gerir definições e funcionalidades nos seus dispositivos com as políticas do Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)




<!--HONumber=Jun16_HO4-->


