---
title: Como os utilizadores de dispositivos iOS obtêm as aplicações
description: Métodos para disponibilizar aplicações iOS aos utilizadores finais
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 05/07/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 7e3135c1-df26-48c9-aa4c-cdab6168897a
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: cc298691ea3df923d1804005be61217325f52112
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72510264"
---
# <a name="how-your-ios-users-get-their-apps"></a>Como os utilizadores de dispositivos iOS obtêm as aplicações

[!INCLUDE [both-portals](../../intune-classic/includes/note-for-both-portals.md)]

Utilize estas informações para saber como e onde é que os seus utilizadores finais podem obter as aplicações que distribuir através do Microsoft Intune.

**Aplicações obrigatórias** – aplicações exigidas pelo administrador e que são instaladas nos dispositivos com envolvimento mínimo do utilizador, dependendo da plataforma.

**Aplicações disponíveis** – aplicações fornecidas na lista de aplicações do Portal da Empresa e que os utilizadores podem optar por instalar.

**Aplicações geridas** – aplicações que podem ser geridas através de políticas e foram "encapsuladas" pelo Intune ou incorporadas no Intune App Software Development Kit (SDK). Estas aplicações podem ser geridas pelo Intune e podem ser-lhes aplicadas políticas de proteção de aplicações.

**Aplicativos não gerenciados**– aplicativos que os usuários podem baixar da iOS App Store que não estão integrados com o SDK de aplicativos do Intune. O Intune não tem nenhum controle sobre a distribuição, o gerenciamento ou o apagamento seletivo desses aplicativos.  

As restrições da Apple proíbem as aplicações da App Store geridas e as aplicações de linha de negócio de serem indicadas na aplicação Portal da Empresa. Para resolver este problema, os mosaicos na aplicação Portal da Empresa para iOS direcionam os utilizadores para diferentes vistas numa única localização (o site do Portal da Empresa) para todas as suas aplicações.

Os utilizadores inscritos obtêm as respetivas aplicações ao tocar nos seguintes mosaicos no ecrã Aplicações da aplicação Portal da Empresa:

- **Todas as Aplicações** direciona para uma lista de todas as aplicações no separador TODOS do [Site do Portal da Empresa](https://portal.manage.microsoft.com).

- **Aplicações Em Destaque** direciona os utilizadores para o separador EM DESTAQUE do site do Portal da Empresa.

- **Categorias** direciona para o separador CATEGORIAS do site do Portal da Empresa.


![Ecrã das aplicações do Portal da Empresa para iOS](./media/end-user-apps-ios/ios-cp-app-main-apps-screen.png)

Para obter mais informações sobre como adicionar aplicações, veja [Como adicionar uma aplicação ao Microsoft Intune](../apps/apps-add.md).

## <a name="see-also"></a>Consulte também
[Como os utilizadores de dispositivos Android obtêm as aplicações](end-user-apps-android.md)

[Como os utilizadores de dispositivos Windows obtêm as aplicações](end-user-apps-windows.md)