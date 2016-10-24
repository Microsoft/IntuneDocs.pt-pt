---
title: "Preparar as aplicações para gestão de aplicações móveis | Microsoft Intune"
description: "As informações neste tópico ajudam-no a decidir quando deve utilizar a ferramenta de encapsulamento de aplicações e o SDK da Aplicação para permitir que as suas aplicações de linha de negócio personalizadas utilizem políticas de gestão de aplicações móveis."
keywords: 
author: karthikaraman
ms.author: karaman
manager: angrobe
ms.date: 09/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 29e22121-8268-48b5-a671-f940a6be1d24
ms.reviewer: oldang
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: df1b58d5ce94c985e71f3afbe228dba9438040dc
ms.openlocfilehash: d79c498fd775ee9b3d59761fec2fe6ebba116d6d


---

# Decidir como preparar as aplicações para a gestão de aplicações móveis com o Microsoft Intune
Pode utilizar a Ferramenta de Encapsulamento de Aplicações do Intune ou o SDK da Aplicação do Intune para ativar as suas aplicações para que utilizem políticas de gestão de aplicações móveis (MAM). Utilize estas informações para saber mais sobre estes dois métodos e como os utilizar.

## Ferramenta de Encapsulamento de Aplicações do Intune
A Ferramenta de Encapsulamento de Aplicações é utilizada, principalmente, para aplicações internas de linha de negócio (LOB). A ferramenta é uma aplicação de linha de comandos que cria um wrapper em torno da aplicação, que permite que a aplicação seja, então, gerida por uma política de gestão de aplicações móveis do Intune. 

Não precisa do código de origem para utilizar a ferramenta, mas precisa das credenciais de início de sessão.  Para obter mais informações sobre as credenciais de início de sessão, consulte o [Blogue do Intune](https://blogs.technet.microsoft.com/enterprisemobility/2015/02/25/how-to-obtain-the-prerequisites-for-the-intune-app-wrapping-tool-for-ios/). Para ver a documentação da Ferramenta de Encapsulamento de Aplicações, consulte [Ferramenta de encapsulamento de aplicações Android](prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md) e [Ferramenta de Encapsulamento de Aplicações iOS](prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md).

A Ferramenta de Encapsulamento de Aplicações **não** suporta aplicações na App Store da Apple nem na Google Play Store ou determinadas funcionalidades que requerem a integração do programador (veja a seguinte tabela de comparação de funcionalidades).

Deve utilizar a Ferramenta de Encapsulamento de Aplicações, em vez do SDK, se a aplicação já tiver sido escrita ou se o código de origem não estiver disponível.

**Para mais informações sobre a Ferramenta de Encapsulamento de Aplicações para a MAM de dispositivos que não estão inscritos no Intune, consulte [Proteger aplicações de linha de negócio e dados em dispositivos não inscritos no Microsoft Intune](protect-line-of-business-apps-and-data-on-devices-not-enrolled-in-microsoft-intune.md)**.

### Plataformas de desenvolvimento de aplicações suportadas

|**Ferramenta de Encapsulamento de Aplicações** | **Xamarin** |**Cordova** |
|------|----|----|
|**iOS** |Sim|Sim|
|**Android**| Não |Sim|

## SDK da Aplicação do Intune
O SDK da Aplicação do Intune foi concebido principalmente para clientes com aplicações na App Store da Apple e/ou na Google Play Store e que pretendem conseguir gerir essas aplicações no Intune. No entanto, qualquer aplicação pode tirar partido da integração com o SDK, inclusive as aplicações de linha de negócio.

Para mais informações sobre o SDK, consulte [Descrição Geral](/intune/develop/intune-app-sdk). Para começar a utilizar o SDK, consulte [Introdução ao Microsoft Intune App SDK](/intune/develop/intune-app-sdk-get-started).

### Plataformas de desenvolvimento de aplicações suportadas

|**SDK da Aplicação do Intune** |**Xamarin** |**Cordova**
|------|----|----|
|**iOS**|Sim – utilizar o componente do Xamarin do SDK da Aplicação do Intune|Sim – utilizar o plug-in do Cordova do SDK da Aplicação do Intune|
|**Android**| Sim – utilizar o Componente do Xamarin do SDK da Aplicação do Intune|Sim – utilizar o plug-in do Cordova do SDK da Aplicação do Intune|

## Comparação de funcionalidades
Esta tabela lista as definições que pode utilizar no SDK da Aplicação e na Ferramenta de Encapsulamento de Aplicações.

> [!NOTE]
> A Ferramenta de Encapsulamento de Aplicações pode ser utilizada com o Intune Autónomo ou o Intune com o Configuration Manager.

|Funcionalidade|SDK da Aplicação|Ferramenta de Encapsulamento de Aplicações|
|-----------|---------------------|-----------|
|Restringir o conteúdo Web a apresentar num browser gerido pela empresa|X|X|
|Impedir cópias de segurança do Android, do iTunes ou do iCloud|X|X|
|Permitir que a aplicação transfira dados para outras aplicações|X|X|
|Permitir que a aplicação receba dados de outras aplicações|X|X|
|Restringir as operações de corte, cópia e colagem com outras aplicações|X|X|
|Exigir PIN simples para acesso|X|X|
|Substituir o PIN da aplicação incorporado pelo PIN do Intune|X||
|Especificar o número de tentativas antes da redefinição do PIN|X|X|
|Requer identificação digital em vez de PIN (iOS apenas)<br></br>**Nota:** apenas disponível em ambientes de MAM.|X||
|Exigir credenciais da empresa para obter acesso|X|X|
|Bloquear a execução de aplicações geridas em dispositivos com jailbreak ou root|X|X|
|Encriptar dados da aplicação|X|X|
|Verificar novamente os requisitos de acesso após um número de minutos especificado|X|X|
|Especificar o período de tolerância offline|X|X|
|Bloquear captura de ecrã (apenas Android)|X|X|
|Eliminação Completa|X|X|
|Apagar Seletivo <br></br>**Nota:** no iOS, se o perfil de gestão for removido, a aplicação também é removida.|X||
|Impedir "Guardar como" |X||
|Suporte para Identidades Múltiplas|X||
|Suporte para MAM sem a inscrição de dispositivos|X|X|
### Consulte também

[Ferramenta de encapsulamento de aplicações do Android](prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md)</br>
[Ferramenta de encapsulamento de aplicações](prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md)</br>
[Utilizar o SDK para ativar aplicações para gestão de aplicações móveis](use-the-sdk-to-enable-apps-for-mobile-application-management.md)



<!--HONumber=Sep16_HO4-->


