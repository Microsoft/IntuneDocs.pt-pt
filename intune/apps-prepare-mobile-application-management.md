---
title: Preparar aplicações de linha de negócios para as políticas de proteção de aplicações
titlesuffix: Microsoft Intune
description: Utilize a ferramenta de encapsulamento de aplicações e o SDK da Aplicação para permitir que as suas aplicações de linha de negócios personalizadas utilizem políticas de proteção de aplicações no Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 05/07/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 29e22121-8268-48b5-a671-f940a6be1d24
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 5ae3b19cfe57c48ac262a376c778d7d593456991
ms.sourcegitcommit: 0f1a5d6e577915d2d748d681840ca04a0a2604dd
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/07/2018
---
# <a name="prepare-line-of-business-apps-for-app-protection-policies"></a>Preparar aplicações de linha de negócios para as políticas de proteção de aplicações

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

Pode utilizar a Ferramenta de Encapsulamento de Aplicações do Intune ou o SDK da Aplicação do Intune para ativar as suas aplicações para que utilizem políticas de proteção de aplicações. Utilize estas informações para saber mais sobre estes dois métodos e como os utilizar.

## <a name="intune-app-wrapping-tool"></a>Ferramenta de Encapsulamento de Aplicações do Intune
A Ferramenta de Encapsulamento de Aplicações é utilizada, principalmente, para aplicações internas de linha de negócio (LOB). A ferramenta é uma aplicação de linha de comandos que cria um wrapper em torno da aplicação, que permite que a aplicação seja, então, gerida por uma política de proteção de aplicações do Intune.

Não precisa do código de origem para utilizar a ferramenta, mas precisa das credenciais de início de sessão. Para obter mais informações sobre as credenciais de início de sessão, consulte o [Blogue do Intune](https://blogs.technet.microsoft.com/enterprisemobility/2015/02/25/how-to-obtain-the-prerequisites-for-the-intune-app-wrapping-tool-for-ios/). Para ver a documentação da Ferramenta de Encapsulamento de Aplicações, consulte [Ferramenta de encapsulamento de aplicações Android](app-wrapper-prepare-android.md) e [Ferramenta de Encapsulamento de Aplicações iOS](app-wrapper-prepare-ios.md).

A Ferramenta de Encapsulamento de Aplicações **não** suporta aplicações da Apple App Store ou da Google Play Store. Também não suporta determinadas funcionalidades que requerem integração do programador (consulte a tabela de comparação de funcionalidades seguinte).


Para obter mais informações sobre a Ferramenta de Encapsulamento de Aplicações para as políticas de proteção de aplicações de dispositivos que não estão inscritos no Intune, veja [Proteger aplicações de linha de negócio e dados em dispositivos não inscritos no Microsoft Intune](/intune-classic/deploy-use/protect-line-of-business-apps-and-data-on-devices-not-enrolled-in-microsoft-intune).

### <a name="reasons-to-use-the-app-wrapping-tool"></a>Motivos para utilizar a Ferramenta de Encapsulamento de Aplicações
* A aplicação não possui funcionalidades de proteção de dados incorporadas
* A aplicação é simples
* A aplicação é implementada internamente
* Não tem acesso ao código de origem da aplicação
* Não desenvolveu a aplicação
* A aplicação tem uma experiência mínima de autenticação de utilizador


### <a name="supported-app-development-platforms"></a>Plataformas de desenvolvimento de aplicações suportadas

|**Ferramenta de Encapsulamento de Aplicações** | **Xamarin** |**Cordova** |
|------|----|----|
|**iOS** |Sim|Sim|
|**Android**| Em Pré-visualização |Sim|

## <a name="intune-app-sdk"></a>SDK da Aplicação Intune
O SDK da Aplicação Intune foi concebido principalmente para clientes com aplicações na App Store da Apple ou na Google Play Store e que pretendem conseguir gerir essas aplicações no Intune. No entanto, qualquer aplicação pode tirar partido da integração com o SDK, inclusive as aplicações de linha de negócio.

Para mais informações sobre o SDK, consulte [Descrição Geral](app-sdk.md). Para começar a utilizar o SDK, consulte [Introdução ao Microsoft Intune App SDK](app-sdk-get-started.md).

### <a name="reasons-to-use-the-sdk"></a>Motivos para utilizar o SDK
* A aplicação não possui funcionalidades de proteção de dados incorporadas
* A aplicação é complexa e contém muitas experiências
* A aplicação foi implementada numa loja de aplicações públicas, tais como o Google Play ou a App Store da Apple
* É um programador de aplicações e tem a formação técnica para utilizar o SDK
* A aplicação tem outras integrações SDK
* A aplicação é frequentemente atualizada

### <a name="supported-app-development-platforms"></a>Plataformas de desenvolvimento de aplicações suportadas

|**SDK da Aplicação Intune** |**Xamarin** |**Cordova**
|------|----|----|
|**iOS**|Sim – utilizar os [Enlaces Xamarin do SDK da Aplicação Intune](app-sdk-xamarin.md).|Não|
|**Android**| Sim – utilizar os [Enlaces Xamarin do SDK da Aplicação Intune](app-sdk-xamarin.md).|Não|

## <a name="feature-comparison"></a>Comparação de funcionalidades
Esta tabela lista as definições que pode utilizar no SDK da Aplicação e na Ferramenta de Encapsulamento de Aplicações.

> [!NOTE]
> A Ferramenta de Encapsulamento de Aplicações pode ser utilizada com o Intune autónomo ou o Intune com o Configuration Manager.

|                                                         Funcionalidade                                                          | SDK da Aplicação | Ferramenta de Encapsulamento de Aplicações |
|--------------------------------------------------------------------------------------------------------------------------|---------|-------------------|
|                              Restringir o conteúdo Web a apresentar num browser gerido pela empresa                              |    X    |         X         |
|                                        Impedir cópias de segurança do Android, do iTunes ou do iCloud                                        |    X    |         X         |
|                                         Permitir que a aplicação transfira dados para outras aplicações                                         |    X    |         X         |
|                                        Permitir que a aplicação receba dados de outras aplicações                                         |    X    |         X         |
|                                      Restringir cortar, copiar e colar com outras aplicações                                       |    X    |         X         |
|                                              Exigir PIN simples para acesso                                               |    X    |         X         |
|                                         Substituir o PIN da aplicação incorporado pelo PIN do Intune                                         |    X    |                   |
|                                     Especificar o número de tentativas antes da redefinição do PIN                                      |    X    |         X         |
|                                             Permitir impressões digitais em vez do PIN                                             |    X    |         X         |
|                                         Exigir credenciais da empresa para obter acesso                                         |    X    |         X         |
|                             Bloquear a execução de aplicações geridas em dispositivos com jailbreak ou root                              |    X    |         X         |
|                                                     Encriptar dados da aplicação                                                     |    X    |         X         |
|                           Verificar novamente os requisitos de acesso após um número de minutos especificado                            |    X    |         X         |
|                                             Especificar o período de tolerância offline                                             |    X    |         X         |
|                                           Bloquear captura de ecrã (apenas Android)                                            |    X    |         X         |
|                                        Suporte para MAM sem a inscrição de dispositivos                                         |    X    |         X         |
|                                                        Eliminação Completa                                                         |    X    |         X         |
| Eliminação Seletiva <br></br><strong>Nota:</strong> no iOS, se o perfil de gestão for removido, a aplicação também é removida. |    X    |                   |
|                                                    Impedir "Guardar como"                                                     |    X    |                   |
|                                            Configuração da Aplicação de Destino                                            |    X    |                   |
|                                                Suporte para Identidades Múltiplas                                                |    X    |                   |
|                                                    Estilo Personalizável                                                    |    X    |                   |

## <a name="next-steps"></a>Próximos passos

Para saber mais sobre as políticas de proteção de aplicações e o Intune, veja os seguintes tópicos:

  -  [Ferramenta de encapsulamento de aplicações para Android](app-wrapper-prepare-android.md)</br>
  - [Ferramenta de encapsulamento de aplicações para iOS](app-wrapper-prepare-ios.md)</br>
  - [Utilizar o SDK para ativar aplicações para gestão de aplicações móveis](/intune-classic/deploy-use/use-the-sdk-to-enable-apps-for-mobile-application-management)
