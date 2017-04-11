---
title: "Problemas conhecidos na Pré-visualização do Microsoft Intune"
titleSuffix: Intune Azure preview
description: "Pré-visualização do Azure no Intune: leia sobre os problemas conhecidos na pré-visualização"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/06/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f33a6645-a57e-4424-a1e9-0ce932ea83c5
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: b6c245d60c661c04b4c4d29c9bdcdd752254d978
ms.openlocfilehash: ec3f87994b19591bda4ec201eac3c839798d634c
ms.lasthandoff: 03/15/2017


---

# <a name="known-issues-in-the-microsoft-intune-preview"></a>Problemas conhecidos na pré-visualização do Microsoft Intune


[!INCLUDE[azure_preview](../includes/azure_preview.md)]


Utilize este tópico para saber mais sobre os problemas conhecidos na pré-visualização do Intune.

Se quiser comunicar um erro que não se encontra listado aqui, [abra um pedido de suporte](https://docs.microsoft.com/intune/troubleshoot/how-to-get-support-for-microsoft-intune).

Se quiser pedir uma nova funcionalidade para adicionar ao Intune, considere o preenchimento de um relatório no nosso site [Uservoice](https://microsoftintune.uservoice.com/forums/291681-ideas/category/189016-azure-admin-console).

## <a name="administration-and-accounts"></a>Administração e contas

- Os Administradores Globais (também designados por Administradores Inquilinos) podem continuar a realizar tarefas diárias de administração sem uma licença separada do Intune ou do Enterprise Mobility Suite (EMS). No entanto, se os Administradores Globais pretenderem utilizar o serviço, como, por exemplo, para inscrever os seus próprios dispositivos, um dispositivo da empresa ou utilizar o Portal da Empresa do Intune, precisarão de uma licença do Intune ou do EMS como qualquer outro utilizador.

## <a name="apple-enrollment-profile-migration"></a>Migração de perfis de inscrição da Apple
- Nos próximos meses, o Intune vai ativar a gestão de inscrições do Apple Configurator e do Programa de Inscrição de Dispositivos Apple através do novo Portal do Azure. Se eliminar o token do Programa de Inscrição de Dispositivos da Apple e não carregar um token atualizado, o token original será restaurado no novo Portal do Azure como parte da migração da sua conta do Intune. Para remover este token e impedir a inscrição do DEP, basta eliminar o token no Portal do Azure. 

