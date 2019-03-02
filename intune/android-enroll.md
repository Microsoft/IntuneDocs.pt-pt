---
title: Inscrever dispositivos Android no Intune
titlesuffix: Microsoft Intune
description: Saiba como inscrever dispositivos Android no Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 12/31/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f276d98c-b077-452a-8835-41919d674db5
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2a9fcb83855e4075ea76cfdb8ed594d5b2c2af94
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/02/2019
ms.locfileid: "57229705"
---
# <a name="enroll-android-devices"></a>Inscrever dispositivos Android

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Como administrador do Intune, pode gerir os seguintes dispositivos Android:
- Dispositivos Android, incluindo dispositivos Samsung Knox Standard.
- Android dispositivos de empresa, incluindo:
    - **Dispositivos de perfil de trabalho do Android Enterprise**: Dispositivos pessoais concedida permissão para aceder a dados empresariais. Os administradores podem gerir contas de trabalho, aplicações e dados. Dados pessoais no dispositivo são mantidos separados dos dados de trabalho e os administradores não controlam configurações pessoais ou dados. 
    - **Dispositivos dedicados do Android Enterprise**: Dispositivos de utilização única, empresa, como digital signage, impressão de permissão ou gestão de inventário. Os administradores bloqueiam a utilização de um conjunto limitado de aplicações e ligações Web num dispositivo. Além disso, também impede os utilizadores de adicionarem outras aplicações ou de efetuarem outras ações no dispositivo.
    - **Android Enterprise dispositivos totalmente geridos**: Utilizador único pertencentes à empresa, os dispositivos utilizados exclusivamente para o trabalho e pessoais não utilizar. Os administradores podem gerir todo o dispositivo e impor controlos de política indisponíveis para perfis de trabalho. 

## <a name="prerequisite"></a>Pré-requisito

Para se preparar para gerir dispositivos móveis, tem de definir a autoridade de gestão de dispositivos móveis (MDM) para o **Microsoft Intune**. Veja [Set the MDM authority (Definir a autoridade de MDM)](mdm-authority-set.md) para obter instruções. Este item só é definido uma vez, quando está a configurar pela primeira vez o Intune para a gestão de dispositivos móveis.

## <a name="set-up-android-enrollment"></a>Configurar inscrição do Android

Por predefinição, o Intune permite a inscrição de dispositivos Android e Samsung Knox Standard. Depois de cumprir o pré-requisito, os administradores só precisam de [informar os utilizadores de como devem inscrever os seus dispositivos](/intune-user-help/enroll-your-device-in-intune-android).

Depois de um utilizador concluir a inscrição, pode começar a gerir os respetivos dispositivos no Intune, incluindo [atribuir políticas de conformidade](compliance-policy-create-android.md), [gerir aplicações](app-management.md) e mais.

Para obter informações sobre outras tarefas do utilizador, veja estes artigos:

- [Recursos sobre a experiência do utilizador final com o Microsoft Intune](end-user-educate.md)
- [Utilizar o dispositivo Android com o Intune](https://docs.microsoft.com/intune-user-help/using-your-android-device-with-intune)

Para impedir a inscrição de dispositivos Android ou apenas de dispositivos Android pessoais, veja [Set device type restrictions (Definir restrições de tipos de dispositivos)](enrollment-restrictions-set.md).

## <a name="set-up-android-enterprise-enrollment"></a>Configurar a inscrição do Android Enterprise

Android Enterprise oferece um conjunto de opções de inscrição que fornecer aos utilizadores com os recursos mais atualizados e seguros. Opções de inscrição do Android Enterprise incluem o perfil de trabalho, dispositivos totalmente geridos e dedicados.

- [Configurar inscrições de perfil de trabalho do Android Enterprise](android-work-profile-enroll.md)
- [Configurar inscrições de dispositivos Android Enterprise dedicado](android-kiosk-enroll.md)
- [Configurar inscrições do Android Enterprise totalmente gerido](android-fully-managed-enroll.md)

## <a name="end-user-experience-when-enrolling-a-samsung-knox-device"></a>Experiência de utilizador final ao inscrever um dispositivo Samsung Knox

Dispositivos Samsung Knox Standard são suportados para gestão de vários utilizadores pelo Intune. Isto significa que os utilizadores podem iniciar e terminar sessão num dispositivo com as respetivas credenciais do Azure AD. O dispositivo é gerido centralmente independentemente de estar a ser utilizado. Quando os utilizadores iniciam sessão, têm acesso às aplicações e, além disso, obtêm as políticas aplicadas às mesmas. Quando os utilizadores iniciam sessão todos os dados de aplicação está desmarcada.

Existem várias considerações a ter em conta ao inscrever dispositivos Samsung Knox:
-   Mesmo que nenhuma política exija um PIN, o dispositivo tem de ter um PIN de pelo menos quatro dígitos para concluir a inscrição. Se o dispositivo não tiver um PIN, será pedido ao utilizador para criar um.
-   Não é necessária nenhuma interação do utilizador para os Certificados de Associação à Área de Trabalho (WPJ).
-   É pedido ao utilizador que indique as informações de Inscrição do Serviço e o que a aplicação pode fazer.
-   É pedido ao utilizador que indique as informações de Inscrição do Knox e o que o Knox pode fazer.
-   Se uma Política de Encriptação for imposta, os utilizadores terão de definir uma palavra-passe Complexa de Seis Carateres para o código de acesso do dispositivo.
-   Não existem pedidos de utilizador adicionais para instalar certificados enviados por um serviço de Acesso aos Recursos da Empresa.
- Alguns dispositivos Knox mais antigos irão pedir ao utilizador para fornecer certificados adicionais utilizados para o Acesso aos Recursos da Empresa.
- Se um dispositivo Samsung Mini não conseguir instalar a WPJ e apresentar o erro **Certificado Não Encontrado** ou **Não é Possível Registar o Dispositivo**, instale as Atualizações de Firmware do Samsung mais recentes.

## <a name="next-steps"></a>Passos Seguintes

- [Configurar inscrições de perfil de trabalho do Android Enterprise](android-work-profile-enroll.md)
- [Configurar inscrições de dispositivos Android Enterprise dedicado](android-kiosk-enroll.md)
- [Configurar inscrições do Android Enterprise totalmente gerido](android-fully-managed-enroll.md)
