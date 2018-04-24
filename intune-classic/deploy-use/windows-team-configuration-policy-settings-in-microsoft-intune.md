---
title: Definições de política de configuração do Windows Team
description: Utilize a **Política de configuração geral do Windows 10 Team** do Microsoft Intune para configurar definições para dispositivos Windows 10 Team inscritos, como o Microsoft Surface Hub.
keywords: ''
author: vhorne
ms.author: victorh
manager: angrobe
ms.date: 12/27/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 38194ef3-e26e-4682-958d-14b395fccba1
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 70b1091cd58439b7d42eab1a612b0b63ca39103d
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/16/2018
---
# <a name="windows-team-configuration-policy-settings-in-microsoft-intune"></a>Definições de política de configuração do Windows Team no Microsoft Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Utilize a **Política de configuração geral do Windows 10 Team** do Microsoft Intune para configurar definições para dispositivos Windows 10 Team inscritos, como o Microsoft Surface Hub.


|                                  Nome da definição                                   |                                                                                                                                                                Detalhes                                                                                                                                                                |
|---------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <strong>Permitir ao ecrã ser reativado automaticamente quando alguém está na sala</strong>   |                                                                                                                         Permite ao dispositivo ser reativado automaticamente quando o respetivo sensor deteta alguém na sala.                                                                                                                          |
|              <strong>Exigir PIN para projeção sem fios</strong>               |                                                                                                             Especifica se deve introduzir um PIN antes de poder utilizar as capacidades de projeção sem fios do dispositivo.                                                                                                             |
|          <strong>Definir uma janela de manutenção para atualizações ao dispositivo</strong>           |                                                                                          Configura a janela quando podem ocorrer atualizações ao dispositivo. Pode configurar a hora de início da janela e a duração (de 1 a 5 horas).                                                                                           |
|               <strong>Ativar as Informações Operacionais do Azure</strong>                |                  As Informações Operacionais do Azure, parte do conjunto de aplicações Microsoft Operations Manager, recolhe, armazena e analisa os dados dos ficheiros de registo a partir de dispositivos Windows 10 Team.<br /><br />Para ligar às Informações Operacionais do Azure, tem de especificar um <strong>ID da Área de Trabalho</strong> e uma <strong>Chave da Área de Trabalho</strong>.                   |
|              <strong>Ativar projeção sem fios Miracast</strong>               |                                          Ative esta opção se pretender permitir que o dispositivo Windows 10 Team utilize dispositivos preparados para Miracast para projeção.<br /><br />Se ativar esta opção, em <strong>Escolher canal Miracast</strong>, selecione o canal Miracast utilizado para projetar conteúdo.                                           |
| <strong>Escolher as informações de reunião apresentadas no ecrã de boas-vindas</strong> | Se ativar esta opção, pode escolher as informações que serão apresentadas no mosaico <strong>Reuniões</strong> do ecrã <strong>Bem-vindo</strong>. É possível:<br /><br />-   <strong>Mostrar apenas organizador e hora</strong><br />-   <strong>Mostrar organizador, hora e assunto (assunto oculto para reuniões privadas)</strong> |
|                <strong>URL da imagem de fundo do ecrã de bloqueio</strong>                 |                                           Ative esta definição para apresentar um fundo personalizado do ecrã <strong>Bem-vindo</strong> dos dispositivos Windows 10 Team a partir do URL especificado.<br /><br />A imagem tem de estar no formato PNG e o URL tem de começar por <strong>https://</strong>.                                            |

### <a name="see-also"></a>Consulte também
[Gerir definições e funcionalidades nos seus dispositivos com as políticas do Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)

