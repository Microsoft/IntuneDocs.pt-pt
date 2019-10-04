---
title: Aplicativos para ambientes GCC de alta e DoD
titleSuffix: Microsoft Intune
description: Saiba mais sobre aplicativos que envolvem ambientes GCC de alta e DoD usando o Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/02/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 29329f86-1aa5-434f-9925-8dc28bf35348
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4d414899b6146afbe2c5ac119193fe0e59aa719b
ms.sourcegitcommit: 223d64a72ec85fe222f5bb10639da729368e6d57
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/04/2019
ms.locfileid: "71939979"
---
# <a name="deploying-apps-using-intune-on-the-gcc-high-and-dod-environments"></a>Implantando aplicativos usando o Intune nos ambientes GCC de alta e DoD 

Microsoft Intune pode ser usado por administradores de locatários para distribuir aplicativos à sua força de funcionários. A força de funcionários é o funcionário da empresa, os usuários dos aplicativos. Há muitos tipos de aplicativos que podem ser implantados do Intune em ambientes GCC de alta ou DoD. Se um administrador precisar carregar e distribuir um aplicativo do Windows destinado a um público com GCC alto ou DoD que seja personalizado, criado por fornecedores terceirizados ou como um aplicativo offline baixado do [Microsoft Store for Business](https://businessstore.microsoft.com/store), o administrador poderá optar por Distribua-o como um [aplicativo de linha de negócios](apps-add.md#app-types-in-microsoft-intune).  

> [!NOTE]
> Para ambientes comerciais, um administrador de locatário pode sincronizar seu armazenamento para empresas com o Intune, no entanto, para ambientes GCC de alta e DoD, esse serviço não está disponível. Os administradores nessa situação devem implantar um aplicativo carregando diretamente no Intune.  

## <a name="add-line-of-business-apps-using-intune"></a>Adicionar aplicativos de linha de negócios usando o Intune 

Para adicionar um aplicativo de linha de negócios destinado a um ambiente de GCC alto ou DoD usando o Intune, você pode seguir as instruções do [aplicativo LOB do Windows](lob-apps-windows.md) . Você pode optar por implantar o Portal da Empresa primeiro do Microsoft Store para empresas. Se você optar por usar o Portal da Empresa, poderá instalar e implantar o Portal da Empresa manualmente. Para obter mais informações, consulte [como configurar o aplicativo de portal da empresa de Microsoft Intune](company-portal-app.md). 

## <a name="distribute-offline-apps-from-the-store-for-business-using-intune"></a>Distribuir aplicativos offline da loja para empresas usando o Intune  

Se você precisar [baixar um aplicativo licenciado offline](https://docs.microsoft.com/microsoft-store/distribute-offline-apps#download-an-offline-licensed-app) da Microsoft Store para empresas, siga estas etapas para baixar o aplicativo: 

1. Entre na [loja para empresas](https://businessstore.microsoft.com/).
2. Selecione **gerenciar** **configurações**de  > .
3. Em **experiência de compra**, defina **Mostrar aplicativos offline** como **ativado**.

Ao comprar aplicativos, se uma versão offline estiver disponível, você poderá optar por alterar o tipo de licença para offline. Depois de obter o aplicativo, você pode gerenciá-lo selecionando **gerenciar**produtos  >  **& serviços** na [loja para empresas](https://businessstore.microsoft.com/). Além disso, você pode baixar o aplicativo e suas dependências. Em seguida, você pode implantar esse aplicativo baixado (e suas dependências) para usuários usando o Intune.  

## <a name="syncing-intune-to-the-store-for-business"></a>Sincronizando o Intune com a loja para empresas 

Em um ambiente comercial (não governamental), um administrador pode sincronizar o Intune com o Microsoft Store para negócios. Esse não é um recurso disponível nos ambientes do governo. Para obter detalhes sobre as diferenças entre o Intune em ambientes comerciais e o Intune para ambientes do governo, consulte [Enterprise Mobility + Security para a descrição do serviço do governo dos EUA](https://docs.microsoft.com/enterprise-mobility-security/solutions/ems-govt-service-description).  

Para sincronizar o Intune com sua conta do Store for Business, consulte [como gerenciar aplicativos adquiridos na Microsoft Store for Business com Microsoft Intune](windows-store-for-business.md).  

## <a name="compliance"></a>Conformidade 

Examine as declarações de privacidade e conformidade dos aplicativos e compare-os com os requisitos de conformidade, segurança e privacidade de sua organização ao avaliar o uso apropriado desses serviços.   

## <a name="next-steps"></a>Passos seguintes

Para saber mais sobre como implantar e atribuir aplicativos, confira [atribuir aplicativos a grupos com Microsoft Intune](apps-deploy.md).

 
