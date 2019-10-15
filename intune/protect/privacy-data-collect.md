---
title: Coleta de dados no Intune
titleSuffix: Microsoft Intune
description: Saiba como os dados pessoais são coletados no Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/18/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d1171740-936d-46a5-af37-f418bd6fa63e
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: cd1d0de4b1ae930ebeff07539f9cfa8848f0b7ce
ms.sourcegitcommit: dd6755383ba89824d1cc128698a65fde6bb2de55
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/14/2019
ms.locfileid: "72306912"
---
# <a name="data-collection-in-intune"></a>Coleta de dados no Intune

Quando os usuários registram seus dispositivos corporativos ou pessoais usando o Intune, o Intune coleta e compartilha alguns dados pessoais. O Intune coleta dados pessoais das seguintes fontes:

- O uso do administrador do Intune no portal do Azure.
- Dispositivos de usuário final (quando eles se registram no gerenciamento do Intune e durante o uso).
- Contas de cliente em serviços de terceiros (de acordo com as instruções do administrador).
- Informações de diagnóstico, desempenho e uso.

A partir dessas fontes, o Intune coleta informações que se enquadram nas três categorias a seguir: [identificadas](#identified-data), [pseudônimos](#pseudonymized-data)e [agregadas](#aggregated-data).

> [!NOTE]
> Não vendemos nenhum dado coletado por nosso serviço para terceiros por qualquer motivo.

## <a name="identified-data"></a>Dados identificados

A maioria dos dados pessoais coletados pelo Intune são dados identificados. Esses dados estão vinculados a um usuário, dispositivo ou aplicativo e são essenciais para a natureza do gerenciamento. Os dados identificados são usados para gerenciar o dispositivo e os aplicativos do usuário e para provisionar o serviço do Intune.

Os dados identificados coletados pelo Intune podem incluir, mas não estão limitados a: 

- Informações do usuário
  - Exibição de nome/usuário do proprietário (o nome do usuário registrado no Azure, conforme identificado por theAzureUserID)
  - Nome principal do usuário ou endereço de email
  - Identificações de usuário de terceiros (como Appleid)
- Informações de inventário de hardware
  - Nome do dispositivo
  - Fabricante
  - Sistema operativo
  - Número de série
  - Número IMEI
  - Endereço IP
  - MacAddress Wi-Fi
  - ICCID
  - Número de telefone
- Informações do log de auditoria, incluindo dados sobre as atividades a seguir
  - Gerir
  - Create
  - Atualizar (editar)
  - Eliminar
  - Atribuir
  - Tarefas remotas
- Informações de suporte
  - Informações de contato (nome, número de telefone, endereço de email)
  - Discussões por email com o suporte da Microsoft, produtos e/ou membros da equipe de experiência do cliente
- Informações de controle de acesso (o Intune usa esses dados para gerenciar o acesso a funções administrativas e funções por meio de recursos como o [controle de acesso baseado em função](../fundamentals/role-based-access-control.md).
  - Autenticadores estáticos (senha do cliente)
  - Chaves de privacidade para certificados 
- Informações de administrador e conta
  - Nome e sobrenome do usuário administrador
  - Nome de usuário do administrador
  - UPN (email)
  - Número de telefone
  - Endereço de email do proprietário da conta
  - ID de Active Directory de cada administrador de ti do cliente
  - Dados de pagamento para cobrança de cliente
  - Chave de subscrição
- Inventário de aplicativos, como
  - Nome do aplicativo
  - versão
  - ID do aplicativo
  - Tamanho
  - local de instalação
  - Os dados de inventário de aplicativos são coletados somente quando marcados pelo administrador como um dispositivo corporativo ou o recurso de aplicativo em conformidade está ativado.  
- IDs de locatário de terceiros do cliente, como a ID da Apple. 

## <a name="pseudonymized-data"></a>Dados do pseudônimos

Os dados do pseudônimos são associados a um identificador exclusivo, normalmente um número gerado pelo sistema que não pode, por sua própria, identificar uma pessoa individual, mas é usado para entregar os serviços corporativos aos usuários. 

Os dados do pseudônimos coletados pelo Intune podem incluir, mas não estão limitados a: 

- Dados de diagnóstico, desempenho e uso vinculados a um usuário e/ou dispositivo
  - O número de vezes que um recurso é usado
  - Os comandos fornecidos para o recurso
  - Tempo de resposta de um serviço
  - Taxas de sucesso de instalações e outros processos
  - Erros de aplicativo do portal da empresa do Intune
  - Identificadores de usuário e dispositivo
  - Identificadores para referência, correlação, fins de gerenciamento 
- Os dados do dispositivo não estão vinculados a um dispositivo ou usuário (se esses dados estiverem vinculados a um dispositivo ou usuário, o Intune o tratará como dados identificados)
  - ID do dispositivo do Intune
  - ID do dispositivo Azure Active Directory
  - ID de gerenciamento de dispositivo do Intune
  - ID do inquilino
  - ID da Conta
  - ID do dispositivo EAS
  - IDs específicas da plataforma
  - Appleid para dispositivos iOS
  - Endereço MAC para dispositivos Mac
  - ID do Windows para dispositivos Windows
- Informações do aplicativo gerenciado
  - ID do aplicativo gerenciado
  - Marca de dispositivo de aplicativo gerenciado
  - ID de gerenciamento de dispositivo do Intune
  - ID do dispositivo Azure Active Directory
  - Chaves de criptografia

## <a name="aggregated-data"></a>Dados agregados

Os dados agregados são usados para provisionar e aprimorar o serviço do Intune. 

Os dados agregados coletados pelo Intune podem incluir, mas não estão limitados a: 

- Dados de uso do administrador de todos os locatários do Intune (por exemplo, controles de administração selecionados ao interagir com o console de administração)
- Informações da conta do locatário (esses dados estão disponíveis na folha do Intune)
  - Número de dispositivos ou usuários registrados
  - Número de plataformas de dispositivo identificadas  
  - Número de dispositivos instalados
  - installedDeviceCount: o número de dispositivos nos quais o aplicativo está instalado.
  - notApplicableDeviceCount: o número de dispositivos para os quais o aplicativo não é aplicável.
  - notInstalledDeviceCount: o número de dispositivos para os quais o aplicativo é aplicável, mas não está instalado.
  - pendingInstallDeviceCount: o numerador de dispositivos para os quais o aplicativo é aplicável e a instalação está pendente.

## <a name="next-steps"></a>Passos seguintes

Saiba mais sobre como o Intune [armazena e processa](privacy-data-store-process.md) e [compartilha](privacy-data-secure-share.md) dados pessoais. 
