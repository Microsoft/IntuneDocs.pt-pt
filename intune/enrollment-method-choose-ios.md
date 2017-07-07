---
title: Escolher como inscrever dispositivos iOS no Intune
titleSuffix: Intune Azure preview
description: "Pré-visualização do Azure no Intune: saiba como configurar a inscrição de dispositivos iOS no Microsoft Intune."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e6c0a430-1851-4108-812a-87e0fc2623b5
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: ee0ecf26a333ec441eb95e79473a9bf405e4120c
ms.contentlocale: pt-pt
ms.lasthandoff: 05/23/2017


---

# <a name="choose-how-to-enroll-ios-devices"></a>Escolher como inscrever dispositivos iOS

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

Este tópico descreve os métodos que podem servir para inscrever dispositivos iOS e os pré-requisitos para a inscrição.

Utilize as seguintes informações para decidir qual o método a utilizar para inscrever dispositivos iOS. Todos os métodos que se seguem, exceto o BYOD, são de inscrição de dispositivos propriedade da empresa.

**Pré-requisito:** é necessário um [Certificado do serviço Apple Push Notification](apple-mdm-push-certificate-get.md).

## <a name="user-owned-ios-devices-byod"></a>Dispositivos iOS propriedade do utilizador (BYOD)

Se os utilizadores quiserem inscrever os dispositivos pessoais BYOD (traga o seu próprio dispositivo), o único método de inscrição disponível é ao transferir a aplicação do Portal da Empresa para iOS a partir da App Store e seguir as instruções de inscrição na aplicação. Uma vez inscritos, os utilizadores podem ligar-se à rede da empresa, associar o domínio ou o Azure Active Directory e obter acesso aos recursos empresariais. Pode bloquear a inscrição de dispositivos iOS pessoais. Veja [Set device type restrictions (Definir restrições de tipos de dispositivos)](enrollment-restrictions-set.md#set-device-type-restrictions) para obter instruções.

## <a name="apple-configurator"></a>Apple Configurator

Pode inscrever dispositivos iOS ao exportar um perfil de Inscrição Empresarial e, em seguida, ligar esses dispositivos móveis a um Mac com o [Apple Configurator](http://go.microsoft.com/fwlink/?LinkId=518017). O Apple Configurator suporta duas formas de inscrição:

- **Inscrição com o Assistente de Configuração**: repõe o dispositivo para as definições de fábrica e prepara-o para a configuração por parte do novo utilizador do dispositivo. Este método requer que o administrador ligue o dispositivo iOS por USB a um computador Mac com o Apple Configurator para pré-configurar a inscrição. Em seguida, são entregues dispositivos aos respetivos utilizadores, que executam o processo do Assistente de Configuração. Este processo configura o dispositivo com as credenciais da escola ou do trabalho do utilizador e conclui o processo de inscrição. Para obter mais informações, veja [Inscrever dispositivos iOS com o Apple Configurator e o Assistente de Configuração](apple-configurator-setup-assistant-enroll-ios.md).

- **Inscrição Direta**: cria um ficheiro compatível com o Apple Configurator para utilização durante a preparação do dispositivo. Não é realizada a reposição de fábrica no dispositivo inscrito e não existe nenhuma afiliação de utilizadores. Para inscrever os dispositivos, o administrador tem de ligar o dispositivo iOS por USB a um computador Mac com o Apple Configurator. Para obter mais informações, veja [Inscrever dispositivos iOS com o Apple Configurator e a Inscrição Direta](apple-configurator-direct-enroll-ios.md).

## <a name="use-the-device-enrollment-program-dep"></a>Utilizar o Programa de Inscrição de Dispositivos (DEP)

O DEP implementa um perfil de inscrição “por ondas eletromagnéticas” para dispositivos que são adquiridos através do DEP. Quando um utilizador executa o Assistente de Configuração no dispositivo, este é inscrito no Intune. Os utilizadores não podem anular a inscrição de dispositivos inscritos através do DEP. Para obter mais informações, veja [Inscrever dispositivos iOS do Programa de Inscrição de Dispositivos](device-enrollment-program-enroll-ios.md).

## <a name="use-the-device-enrollment-manager-dem"></a>Utilizar o gestor de inscrição de dispositivos (DEM)
O gestor de inscrição de dispositivos é um tipo de conta de utilizador que pode inscrever e gerir até mil dispositivos. Pode adicionar utilizadores existentes à conta DEM de forma a conceder-lhes estas capacidades. Cada dispositivo que o utilizador DEM inscreve utiliza uma licença individual do Intune. Para obter mais informações, veja [Inscrever dispositivos com o gestor de inscrição de dispositivos](device-enrollment-manager-enroll.md).
