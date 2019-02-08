---
title: Dados JAMF Pro envia para o Intune | Microsoft Intune
description: Lista de dados que o Jamf Pro envia para o Microsoft Intune
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/16/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: elocholi
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 114a5c09ed99b5debe9a13692b8a5400c04382df
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/07/2019
ms.locfileid: "55833723"
---
# <a name="data-jamf-pro-sends-to-intune"></a>Dados que o Jamf Pro envia para o Intune

Quando utiliza [Jamf Pro](https://www.jamf.com) para gerir os seus Macs os utilizadores finais com o Intune, o Jamf Pro recolhe informações de inventário sobre dispositivos macOS geridos. O Jamf Pro reporta as seguintes informações ao Intune:

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
* SO
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

Obtenha informações sobre como [remover um dispositivo gerido por Jamf na documentação do Jamf Pro](https://www.jamf.com/jamf-nation/articles/80/unmanaging-computers-while-preserving-their-inventory-information). Também pode enviar um pedido de suporte para o [suporte do Jamf](https://www.jamf.com/support/) para obter ajuda adicional. 

