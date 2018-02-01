---
title: "Inscrever o dispositivo iOS na gestão de despesas de telecomunicações com o Intune"
description: "Saiba como inscrever um dispositivo iOS na gestão de despesas de telecomunicações."
keywords: 
author: barlanmsft
ms.author: barlan
manager: dougeby
ms.date: 04/19/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6d8c6372-f2ce-4558-8886-1d7c1966699c
searchScope:
- User help
ROBOTS: 
ms.reviewer: sumitp
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 90b07e1f18ab3cb9c74337e2a3538f186f4ea52a
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/25/2018
---
# <a name="enroll-your-ios-device-in-telecom-expense-management"></a>Inscrever o dispositivo iOS na gestão de despesas de telecomunicações

A sua organização poderá estar a utilizar software de gestão de despesas de telecomunicações para garantir que os planos de voz e de dados estão a ser utilizados dentro dos limites aceitáveis. Depois de concluir a inscrição do dispositivo, ser-lhe-á solicitado que selecione a melhor categoria para esse dispositivo.

  ![Uma captura do ecrã “selecionar a melhor categoria para um dispositivo” num dispositivo iOS. Mostra uma seleção de inscrição empresarial ou pessoal.](./media/ios-enroll-10-tem-select-best-category.png)

Selecione a opção adequada para receber uma notificação e instalar a aplicação [ __Datalert__ ](https://itunes.apple.com/app/datalert/id771029268?mt=8) a partir da App Store. A aplicação Datalert é o modo como a sua organização pode medir a utilização de dados. Se a sua organização configurou a opção de inscrição escolar ou profissional da Microsoft, precisará de iniciar sessão com a conta escolar ou profissional. Se ainda não tiver ativado esta opção, terá de indicar informações como o número de telefone e verificar o dispositivo através de um código para se inscrever no serviço Datalert da aplicação.

  ![Uma captura do ecrã de boas-vindas da aplicação Datalert, que lhe pede para se deslocar para o ecrã seguinte depois de apresentar uma breve explicação sobre como a aplicação Datalert pode tirar o máximo partido do seu plano de dados.](./media/ios-enroll-11-tem-datalert-setup.png)

## <a name="enroll-into-datalert-using-your-microsoft-work-or-school-account"></a>Inscrever-se no Datalert através da conta escolar ou profissional da Microsoft

> [!NOTE]
> Tem de ter a aplicação [Microsoft Authenticator](https://docs.microsoft.com/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to) instalada e ativa no telemóvel para se inscrever desta forma.

1. Selecione __Inscrever-se com a conta Microsoft__.

  ![Uma imagem do ecrã Definições da aplicação Datalert, que apresenta um campo de número de telefone para inscrever um dispositivo na metade superior do ecrã e “inscrever-se com conta Microsoft” na parte inferior, desde que tenha uma conta do Microsoft Office 365 e uma subscrição do Intune.](./media/ios-enroll-11a-tem-datalert-enroll-msft-account.png)

2. Receberá uma notificação a indicar que __“Datalert” pretende abrir o “Authenticator”__. Selecione __Abrir__.

  ![Uma imagem do pop-up a pedir ao utilizador para abrir a aplicação Authenticator a pedido da aplicação Datalert.](./media/ios-enroll-11b-tem-datalert-open-authenticator.png)

3. Inicie sessão com a __conta escolar ou profissional da Microsoft__. A configuração do Datalert irá funcionar durante alguns minutos e, em seguida, deverá ser concluída. Toque em __Concluir__ quando terminar.

## <a name="enroll-into-datalert-using-your-phone-number"></a>Inscrever-se no Datalert através do número de telefone

1. Indique o número de telefone do seu dispositivo.

  ![Uma captura de ecrã da aplicação Datalert a solicitar um número de telefone.](./media/ios-enroll-12-tem-datalert-phone-number.png)

2. Em seguida, receberá um código de verificação através de uma mensagem SMS. Indique o código e toque em __OK__.

  ![Uma captura de ecrã da aplicação Datalert a solicitar um código de verificação por SMS.](./media/ios-enroll-13-tem-datalert-sms.png)

3. Depois de indicar o código de verificação, a configuração da aplicação Datalert é concluída. Toque em __Concluir__ para poder monitorizar os dados da aplicação Datalert.

  ![Uma captura de ecrã da aplicação Datalert a monitorizar a utilização de dados de hoje.](./media/ios-enroll-14-tem-datalert-monitoring-active.png)

Depois de se inscrever, começa a ver a utilização de dados na aplicação Datalert.

Ainda precisa de ajuda? Contacte o suporte da empresa. Para encontrar as informações de contacto dele, verifique o [site do Portal da Empresa](https://portal.manage.microsoft.com#HelpDeskDialog).
