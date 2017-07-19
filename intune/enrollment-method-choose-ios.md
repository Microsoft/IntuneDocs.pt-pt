---
title: Escolher como inscrever dispositivos iOS no Intune
titleSuffix: Intune on Azure
description: "Saiba como configurar a inscrição de dispositivos iOS no Microsoft Intune.\""
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 06/28/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e6c0a430-1851-4108-812a-87e0fc2623b5
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 092f582cf30210858bd8cdd3879edfa873523ccb
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/01/2017
---
# <a name="choose-how-to-enroll-ios-and-macos-devices"></a>Escolher como inscrever dispositivos iOS e Mac OS

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Este tópico descreve os métodos que um administrador de TI pode utilizar para ativar a inscrição de dispositivos iOS no Intune.

Utilize as seguintes informações para decidir qual o método a utilizar para inscrever dispositivos iOS. Todos os métodos que se seguem, exceto o BYOD, são de inscrição de dispositivos propriedade da empresa.

**Pré-requisito:** é necessário um [Certificado do serviço Apple Push Notification](apple-mdm-push-certificate-get.md).

## <a name="user-owned-ios-devices-byod"></a>Dispositivos iOS propriedade do utilizador (BYOD)

Se os utilizadores quiserem inscrever os dispositivos pessoais BYOD (traga o seu próprio dispositivo), podem transferir a aplicação Portal da Empresa para iOS a partir da App Store e seguir as instruções de inscrição na aplicação. Uma vez inscritos, os utilizadores podem ligar-se à rede da empresa, associar o domínio ou o Azure Active Directory e obter acesso aos recursos empresariais. Para ativar o conjunto de funcionalidades BYOD, o único requisito é um [Certificado de serviço Apple Push Notification](apple-mdm-push-certificate-get.md). Pode igualmente bloquear a inscrição de dispositivos iOS pessoais. Veja [Set device type restrictions (Definir restrições de tipos de dispositivos)](enrollment-restrictions-set.md) para obter instruções.

## <a name="user-owned-macos-devices-byod"></a>Dispositivos Mac OS propriedade do utilizador (BYOD)

Pode ativar a inscrição de dispositivos Mac OS. Para ativar a inscrição de macOS, o único requisito é um [Certificado de serviço Apple Push Notification](apple-mdm-push-certificate-get.md). Para obter mais informações, veja [Inscrever dispositivos Mac OS](./macos-enroll.md)

## <a name="enrollment-program-with-apple"></a>Programa de inscrição com a Apple
A Apple oferece programas de compras de dispositivos que incluem a infraestrutura de inscrição e gestão de dispositivos. Um dispositivo comprado através de um desses programas pode ser inscrito em massa através de uma ligação sem fios, ao atribuir números de série do dispositivo para gestão com o Intune.

- **Programa de Inscrição de Dispositivos (DEM)** – O programa de inscrição de dispositivos da Apple para organizações e empresas. Para obter mais informações, veja [Inscrever dispositivos iOS do Programa de Inscrição de Dispositivos](device-enrollment-program-enroll-ios.md).
- **Apple School Manager** – o programa de inscrição de dispositivos da Apple para escolas. Para obter mais informações, veja [Ativar a inscrição do dispositivo iOS com o Apple School Manager](apple-school-manager-set-up-ios.md)

## <a name="apple-configurator"></a>Apple Configurator

É possível inscrever dispositivos iOS ao exportar um perfil de Inscrição Empresarial e, em seguida, ligar esses dispositivos móveis a um Mac com o Apple Configurator. O Apple Configurator suporta duas formas de inscrição:

- **Inscrição com o Assistente de Configuração**: repõe o dispositivo para as definições de fábrica e prepara-o para a configuração por parte do novo utilizador do dispositivo. Este método requer que o administrador ligue o dispositivo iOS por USB a um computador Mac com o Apple Configurator para pré-configurar a inscrição. Em seguida, são entregues dispositivos aos respetivos utilizadores, que executam o processo do Assistente de Configuração quando os dispositivos iniciam pela primeira vez. Este processo configura o dispositivo com as credenciais da escola ou do trabalho do utilizador e conclui o processo de inscrição. Para obter mais informações, veja [Inscrever dispositivos iOS com o Apple Configurator e o Assistente de Configuração](apple-configurator-setup-assistant-enroll-ios.md).

- **Inscrição Direta**: cria um ficheiro compatível com o Apple Configurator para utilização durante a preparação do dispositivo. Não é realizada a reposição de fábrica no dispositivo inscrito e não existe nenhuma afiliação de utilizadores. Para inscrever os dispositivos, o administrador tem de ligar o dispositivo iOS por USB a um computador Mac com o Apple Configurator. Para obter mais informações, veja [Inscrever dispositivos iOS com o Apple Configurator e a Inscrição Direta](apple-configurator-direct-enroll-ios.md).

## <a name="use-the-device-enrollment-program-dep"></a>Utilizar o Programa de Inscrição de Dispositivos (DEP)

O DEP implementa um perfil de inscrição “por ondas eletromagnéticas” para dispositivos que são adquiridos através do DEP. Quando um utilizador executa o Assistente de Configuração no dispositivo quando inicia pela primeira vez, este é inscrito no Intune. Para obter mais informações, veja [Inscrever dispositivos iOS do Programa de Inscrição de Dispositivos](device-enrollment-program-enroll-ios.md).

## <a name="use-the-device-enrollment-manager-dem"></a>Utilizar o gestor de inscrição de dispositivos (DEM)
O gestor de inscrição de dispositivos é uma conta de utilizador genérica que pode inscrever e gerir até 1000 dispositivos. Os dispositivos geridos pelo DEM não podem ter afinidade de utilizador para que o dispositivo nunca tenha um proprietário. Fornece permissões do DEM a um utilizador do Intune para atribuir-lhe essas capacidades. Cada dispositivo que o utilizador DEM inscreve utiliza uma licença do Intune. Para obter mais informações, veja [Inscrever dispositivos com o gestor de inscrição de dispositivos](device-enrollment-manager-enroll.md).
