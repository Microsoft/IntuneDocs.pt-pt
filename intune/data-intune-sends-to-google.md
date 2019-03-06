---
title: Dados que o Intune envia para a Google
titleSuffix: Microsoft Intune
description: Lista de dados que o Intune envia para a Google.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/18/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a5c3bec4-18ed-11e8-accf-0ed5f89f718b
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2a6d99cc83be1b20ef2839acd77cb83c9d6b247e
ms.sourcegitcommit: 430b290474b11f9df87785b01edc178e6bae2049
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/05/2019
ms.locfileid: "57393574"
---
# <a name="data-intune-sends-to-google"></a>Dados que o Intune envia para a Google

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Quando a gestão de dispositivos Android Enterprise está ativada num dispositivo, o Microsoft Intune estabelece uma ligação com a Google e partilha informações do utilizador e do dispositivo com a mesma. Antes de o Microsoft Intune poder estabelecer uma ligação, tem de criar uma conta Google.

A seguinte tabela lista os dados que o Microsoft Intune envia para a Google quando a gestão de dispositivos está ativada num dispositivo:


| Dados enviados para a Google | Detalhes | Utilizado para | Exemplo |
|:---:|:---:|:---:|:---:|
| ID Empresarial | Tem origem na Google ao vincular a sua conta do Gmail ao Intune. | Identificador principal utilizado para comunicar entre o Intune e a Google.  Esta comunicação inclui a definição de políticas, a gestão de dispositivos e o vínculo/supressão do vínculo do Android Enterprise com o Intune. | Identificador exclusivo, formato de exemplo: LC04eik8a6 |
| Corpo de Política | Tem origem no Intune ao guardar uma nova política de configuração ou aplicação. | Aplicar políticas a dispositivos. | Isto é uma coleção de todas as definições configuradas para uma política de configuração ou aplicação. Isto pode conter informações de clientes, se estas forem fornecidas como parte de uma política. Por exemplo, nomes de redes, nomes de aplicações e definições específicas da aplicação. |
| Dados do Dispositivo | Os dispositivos para cenários de Perfil Profissional começam com a inscrição no Intune. Os dispositivos para cenários de Dispositivo gerido começam com a inscrição na Google. | As informações de dados do dispositivo são enviadas entre o Intune e a Google para a realização de várias ações, como a aplicação de políticas, a gestão do dispositivo e a criação geral de relatórios. | **Identificador exclusivo para representar o Nome do Dispositivo.** Exemplo: enterprises/LC04ebru7b/devices/3592d971168f9ae4<br>**Identificador exclusivo para representar o Nome do Utilizador.** Exemplo: Enterprises/LC04ebru7b/users/116838519924207449711<br>**Estado do dispositivo.** Exemplos: Ativo, desativado, aprovisionamento.<br>**Estados de conformidade.** Exemplos: Definição não suportada, aplicações obrigatórias em falta<br>**Informações de Software.** Exemplos: versões de software e nível de patch.<br>**Informações de Rede.** Exemplos: IMEI, MEID, WifiMacAddress<br>**Definições do Dispositivo.** Exemplos: Informações sobre níveis de encriptação e se o dispositivo permite aplicações desconhecidas.<br> Veja abaixo um exemplo de uma mensagem JSON. |
| Nova palavra-passe | Tem origem no Intune. | Repor o código de acesso do dispositivo. | Cadeia a representar uma nova palavra-passe. |
| Utilizador da Google | Google | Gerir o perfil profissional em cenários de Perfil Profissional (BYOD). | Identificador exclusivo para representar a conta do Gmail ligada. Exemplo: 114223373813435875042 |
| Dados da aplicação | Tem origem no Intune ao guardar a política da aplicação. |  | Cadeia do Nome da Aplicação. Exemplo: app:com.microsoft.windowsintune.companyportal |
| Conta de Serviço Empresarial | Tem origem na Google a pedido do Intune. | Utilizado para a autenticação entre o Intune e a Google para transações que envolvem o cliente. | Existem várias partes:<br> **ID Empresarial**: documentada anteriormente.<br>**UPN**: UPN gerado utilizado na autenticação em nome de um cliente.<br>Exemplo: w49d77900526190e26708c31c9e8a0@pfwp-commicrosoftonedfmdm2.google.com.iam.gserviceaccount.com<br>**chave**: Blob codificado Base64 utilizado em pedidos de autor, armazenados encriptados no serviço, mas este é o que o blob é semelhante a:<br> Identificador exclusivo para representar a chave do cliente<br>Exemplo: a70d4d53eefbd781ce7ad6a6495c65eb15e74f1f |


Para deixar de utilizar a gestão de dispositivos Android Enterprise com o Microsoft Intune e eliminar os dados, tem de desativar a gestão de dispositivos Android Enterprise do Microsoft Intune e eliminar a sua conta Google. Consulte a conta Google para saber como desempenhar a gestão da conta.


