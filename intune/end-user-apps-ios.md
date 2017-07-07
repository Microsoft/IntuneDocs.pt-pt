---
title: "Como os utilizadores de dispositivos iOS obtêm as aplicações"
description: "Métodos para disponibilizar aplicações iOS aos utilizadores finais"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 10/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7e3135c1-df26-48c9-aa4c-cdab6168897a
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 0061d4ecd8d71f8b7363193e36b838741aa56a92
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/01/2017
---
# <a name="how-your-ios-users-get-their-apps"></a>Como os utilizadores de dispositivos iOS obtêm as aplicações

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

Utilize estas informações para saber como e onde é que os seus utilizadores finais podem obter as aplicações que distribuir através do Microsoft Intune.

**Aplicações obrigatórias** – aplicações exigidas pelo administrador e que são instaladas nos dispositivos com envolvimento mínimo do utilizador, dependendo da plataforma.

**Aplicações disponíveis** – aplicações fornecidas na lista de aplicações do Portal da Empresa e que os utilizadores podem optar por instalar.

**Aplicações geridas** – aplicações que podem ser geridas através de políticas e que foram "encapsuladas" pelo Intune ou incorporadas no Software Development Kit (SDK) da Gestão de Aplicações Móveis (MAM) do Intune. Estas aplicações podem ser geridas pelo Intune e podem ser aplicadas políticas de aplicação às mesmas.

**Aplicações não geridas** – aplicações que podem ser geridas através de políticas e que não foram encapsuladas pelo Intune ou que não incorporam o SDK de MAM do Intune. Não é possível aplicar políticas de aplicação a estas aplicações.

As restrições da Apple proíbem as aplicações da App Store geridas e as aplicações de linha de negócio de serem indicadas na aplicação Portal da Empresa. Para resolver este problema, os mosaicos na aplicação Portal da Empresa para iOS direcionam os utilizadores para diferentes vistas numa única localização (o site do Portal da Empresa) para todas as suas aplicações.

Os utilizadores inscritos obtêm as respetivas aplicações ao tocar nos seguintes mosaicos no ecrã Aplicações da aplicação Portal da Empresa:

- **Todas as Aplicações** direciona para uma lista de todas as aplicações no separador TODOS do [Site do Portal da Empresa](https://portal.manage.microsoft.com).

- **Aplicações Em Destaque** direciona os utilizadores para o separador EM DESTAQUE do site do Portal da Empresa.

- **Categorias** direciona para o separador CATEGORIAS do site do Portal da Empresa.


![Ecrã das aplicações do Portal da Empresa para iOS](./media/ios-cp-app-main-apps-screen.png)

Para obter informações sobre como adicionar aplicações e colocá-las nestes mosaicos, consulte [Adicionar aplicações a dispositivos móveis para o Intune](/intune-classic/deploy-use/add-apps-for-mobile-devices-in-microsoft-intune.md).

### <a name="see-also"></a>Consulte também
[Como os utilizadores de dispositivos Android obtêm as aplicações](end-user-apps-android.md)

[Como os utilizadores de dispositivos Windows obtêm as aplicações](end-user-apps-windows.md)
