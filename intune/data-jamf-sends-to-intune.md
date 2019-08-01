---
title: O data JAMF pro envia ao Intune
titleSuffix: Microsoft Intune
description: Examine a lista de dados que o JAMF pro envia para Microsoft Intune ao integrar o JAMF pro para gerenciar Macs com o Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: elocholi
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: ce9a92a9fffad13c6723504735b1b1cb9442f61f
ms.sourcegitcommit: 864fdf995c2b41f104a98a7e2665088c2864774f
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/31/2019
ms.locfileid: "68680023"
---
# <a name="data-jamf-pro-sends-to-intune"></a>Dados que o Jamf Pro envia para o Intune

Quando você usa o [JAMF pro](https://www.jamf.com) para gerenciar seus Macs de usuários finais com o Intune, o JAMF pro captura informações de inventário sobre dispositivos MacOS gerenciados. 

## <a name="data"></a>Data  
O Jamf Pro reporta as seguintes informações ao Intune:  

* ID do Azure AD do Dispositivo
* Estado de Inventário do JAMF (estado de inventário de um computador registado através do Jamf Pro nas últimas 24 horas)
* Versão do SO
* ID do Azure AD do Utilizador
* Dados encriptados (FileVault 2)
* Estado do Controlador de Chamadas
* Palavra-passe: número mínimo de conjuntos de carateres
* Expiração da Palavra-passe (dias)
* Tipo de Palavra-passe – simples, alfanumérico ou desconhecido
* Impedir o Início de Sessão Automático
* Comprimento do Código de Acesso Necessário
* Palavra-passe: número de palavras-passe anteriores para impedir a reutilização
* Proteção da Integridade do Sistema
* Hora do Último Registo
* Tipo de Arquitetura
* Ranhuras de RAM Disponíveis
* Capacidade de Bateria
* ROM de Arranque
* Velocidade do Barramento
* Tamanho da Cache
* Nome do dispositivo
* Associação a um Domínio
* ID do Jamf
* Endereço MAC
* Criar
* Modelo
* Identificador do Modelo
* Velocidade da NIC
* Número de Núcleos
* Número de Processadores
* OS
* Plataforma
* Velocidade do Processador
* Tipo de processador
* Endereço MAC Secundário
* Número de Série
* Versão do SMC
* Total de RAM
* UDID
* E-mail do Utilizador

Pode remover um dispositivo gerido por Jamf a partir da consola do Intune ao selecionar **Eliminar** na vista **Todos os dispositivos**. A eliminação de dispositivos em massa pode ser ativada ao selecionar múltiplos dispositivos e clicar em **Eliminar**.

## <a name="next-steps"></a>Passos Seguintes
Obtenha informações sobre como [remover um dispositivo gerido por Jamf na documentação do Jamf Pro](https://www.jamf.com/jamf-nation/articles/80/unmanaging-computers-while-preserving-their-inventory-information). Também pode enviar um pedido de suporte para o [suporte do Jamf](https://www.jamf.com/support/) para obter ajuda adicional. 

