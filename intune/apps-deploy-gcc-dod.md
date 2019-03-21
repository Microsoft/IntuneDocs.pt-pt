---
title: Aplicações para ambientes de GCC elevada e DoD
titlesuffix: Microsoft Intune
description: Saiba mais sobre as aplicações que envolvam ambientes de GCC elevada e DoD através do Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/18/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 29329f86-1aa5-434f-9925-8dc28bf35348
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: fb49cd97e029e45d7d098ec1898fd0e27efa1132
ms.sourcegitcommit: 4049a3aed15f2d8d21bb814410875a13f613e4ed
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/20/2019
ms.locfileid: "58283233"
---
# <a name="deploying-apps-using-intune-on-the-gcc-high-and-dod-environments"></a>Implementação de aplicações através do Intune em ambientes do DoD e GCC elevada 

Microsoft Intune pode ser utilizado por administradores de inquilinos para distribuir aplicações para a sua força de trabalho. A força de trabalho é o funcionário da empresa, os utilizadores das aplicações. Existem muitos tipos de aplicações que podem ser implementadas a partir do Intune em ambientes do DoD ou GCC elevada. Se um administrador tem de carregar e distribuir uma aplicação do Windows se destina a um GCC elevada ou o público-alvo de DoD que é personalizado, criados por fornecedores de terceiros, ou como uma aplicação offline transferido a partir da [Microsoft Store para empresas](https://businessstore.microsoft.com/store), o administrador pode optar por distribuir-o como um [aplicação de linha de negócio](apps-add.md#app-types-in-microsoft-intune).  

> [!NOTE]
> Para ambientes comerciais, o administrador de inquilinos pode sincronizar suas Store para empresas com o Intune, no entanto, para ambientes de GCC elevada e DoD, este serviço não está disponível. Os administradores nesta situação tem de implementar uma aplicação ao carregar diretamente para o Intune.  

## <a name="add-line-of-business-apps-using-intune"></a>Adicionar aplicações de linha de negócio com o Intune 

Para adicionar uma aplicação de linha de negócio se destina a um ambiente de GCC elevada ou DoD através do Intune, pode seguir a [aplicação LOB para Windows](lob-apps-windows.md) instruções. Pode optar por implementar o Portal da empresa pela primeira vez a partir da Microsoft Store para empresas. Se optar por utilizar o Portal da empresa, pode instalar manualmente e implementar o Portal da empresa. Para obter mais informações, consulte [como configurar a aplicação Portal da empresa do Microsoft Intune](company-portal-app.md). 

## <a name="distribute-offline-apps-from-the-store-for-business-using-intune"></a>Distribuir aplicações Offline a partir do Store para empresas com o Intune  

Se precisar [transferir uma aplicação licenciadas offline](https://docs.microsoft.com/microsoft-store/distribute-offline-apps#download-an-offline-licensed-app) da Microsoft Store para empresas, siga estes passos para transferir a aplicação: 

1. Inicie sessão para o [Store para empresas](https://businessstore.microsoft.com/).
2. Selecione **gerenciar** > **definições**.
3. Sob **experiência de compras**, defina **Mostrar aplicações offline** para **no**.

Quando compra para aplicações, se estiver disponível uma versão offline, pode optar por alterar o tipo de licença para offline. Depois de obter a aplicação, pode, em seguida, geri-la selecionando **Manage** > **produtos e serviços** no [Store para empresas](https://businessstore.microsoft.com/). Além disso, pode transferir a aplicação e às respetivas dependências. Em seguida, pode implementar esta aplicação transferida (e suas dependências) aos utilizadores através do Intune.  

## <a name="syncing-intune-to-the-store-for-business"></a>A sincronizar o Intune para o Store para empresas 

Num ambiente comercial (não-governamental), um administrador pode sincronizar o Intune para a Microsoft Store para empresas. Não é uma funcionalidade disponível em ambientes de administração pública. Para obter detalhes sobre as diferenças entre o Intune em ambientes comerciais e o Intune para ambientes de governo, consulte [Enterprise Mobility + Security para-na descrição do serviço governamental](https://docs.microsoft.com/enterprise-mobility-security/solutions/ems-govt-service-description).  

Para sincronizar o Intune para o Store para a conta de empresa, consulte [como gerir aplicações compradas a partir da Microsoft Store para empresas com o Microsoft Intune](windows-store-for-business.md).  

## <a name="compliance"></a>Conformidade 

Rever as declarações de privacidade e conformidade de aplicações e compará-los para os requisitos de conformidade, segurança e privacidade da sua organização quando avaliar o uso adequado desses serviços.   

## <a name="next-steps"></a>Passos Seguintes

Para saber mais sobre implantação e atribuição de aplicações, veja [atribuir aplicações a grupos com o Microsoft Intune](apps-deploy.md).

 
