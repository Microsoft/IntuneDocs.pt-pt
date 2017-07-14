---
title: "Enviar registos ao administrador de TI para dispositivos Windows 10 | Microsoft Docs"
description: Inscrever um dispositivo com o Windows 10 1511 no Intune
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 05/25/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 038747fb-5b52-47c4-a2b6-f9218da4cfe1
searchScope: User help
ROBOTS: 
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: be9976f03bf749222ca372040d4d936e6a8fd26b
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/01/2017
---
# <a name="send-logs-to-your-it-admin-from-the-settings-app-for-windows-10"></a>Enviar registos ao seu administrador de TI a partir da aplicação Definições para Windows 10

Se obtiver um erro enquanto estiver a utilizar o dispositivo Windows 10 gerido pela empresa, poderá ajudar o administrador de TI a resolver o problema ao enviar-lhe informações por e-mail. Estas informações encontram-se no dispositivo, num documento especial denominado _registo de diagnóstico_.

1.  Abra a aplicação **Definições** do Windows ao aceder ao **menu Iniciar** e selecione o botão **Definições**. Também pode procurar "definições" na barra de pesquisa.
2.  Vá para **Contas** > **Acesso profissional ou escolar**.
3.  Selecione “Exportar os ficheiros de registo de gestão”.

  ![O “ecrã Acesso profissional ou escolar”, que apresenta a opção Exportar sob o cabeçalho “Definições relacionadas”.](./media/w10-export-logs.png)

4. Os registos serão guardados em **C:\Users\Public\Public Documents\MDMDiagnostics**. Serão criados dois ficheiros: um é o registo em si e o outro é um documento especial que permite que o seu administrador analise os registos em programas diferentes, tais como o Microsoft Excel. Anexe ambos os ficheiros a uma mensagem de e-mail e envie o e-mail para o seu administrador. Se fizer isto mais do que uma vez, basta escolher os ficheiros do dia em que criou os registos. 

Também poderá ser necessário enviar [registos da aplicação Portal da Empresa](send-logs-to-your-it-admin-cp-windows.md) para fornecer ao seu administrador de TI mais ajuda para tentar resolver quaisquer problemas que possa encontrar. 

Ainda precisa de ajuda? Contacte o administrador de TI. Para encontrar as informações de contacto dele, verifique o [site do Portal da Empresa](http://portal.manage.microsoft.com).