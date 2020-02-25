---
title: Adicione e atribua a aplicação Portal da Empresa do Windows 10 para dispositivos aprovisionados em Piloto Automático
titleSuffix: Microsoft Intune
description: Adicione e atribua a aplicação Portal da Empresa do Windows 10 ao Intune para dispositivos aprovisionados por Piloto Automático.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/21/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c13d8d774037f0d2db5832af7f39c864330fef30
ms.sourcegitcommit: 47c9af81c385c7e893fe5a85eb79cf08e69e6831
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/25/2020
ms.locfileid: "77579769"
---
# <a name="add-and-assign-the-windows-10-company-portal-app-for-autopilot-provisioned-devices"></a>Adicione e atribua a aplicação Portal da Empresa do Windows 10 para dispositivos aprovisionados em Piloto Automático

Para gerir dispositivos e instalar aplicações, os seus utilizadores podem utilizar a aplicação Portal da Empresa. Pode atribuir a aplicação Portal da Empresa Do Windows 10 diretamente do Intune. 

## <a name="prerequisites"></a>Pré-requisitos

Para dispositivos de pilotamento do Windows 10, recomenda-se que associe a sua conta Microsoft Store para Negócios com o Intune. Para mais informações, consulte [como gerir as aplicações adquiridas](~/apps/windows-store-for-business.md)em volume na Microsoft Store for Business com o Microsoft Intune .

O Portal da Empresa (Offline) é escolhido para ser instalado utilizando os passos abaixo. A aplicação Portal da Empresa será instalada no contexto do dispositivo quando atribuída ao grupo Autopilot e será instalada no dispositivo antes de o utilizador iniciar o seu login. 

## <a name="configure-settings-to-show-offline-apps"></a>Configurar definições para mostrar as aplicações offline
1. Inicie sessão na [Microsoft Store para Empresas](https://www.microsoft.com/business-store) com a sua conta de administrador.
2. Selecione o separador **Gerir** perto da parte superior da janela.
3. No painel esquerdo, selecione **Definições**.
4. Em **Experiência de compras**, defina **Mostrar aplicações offline** para **Ativado**.  
    As aplicações offline licenciadas serão apresentadas.

## <a name="get-the-offline-company-portal-app"></a>Obtenha a aplicação offline Company Portal
1. Procure e, em seguida, selecione a aplicação **Portal da Empresa**.
2. Defina o **Tipo de licença** para **Offline**.
3. Selecione **Obter a aplicação** para adquirir e adicionar a aplicação offline Portal da Empresa ao seu inventário.

## <a name="assign-the-company-portal-app"></a>Atribuir a app Portal da Empresa
1. Inscreva-se no centro de administração do [Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) com a sua conta de administração. 
2. Selecione o separador **apps** no painel certo. 
3. Em **by plataforma,** selecione **Windows**. 
4. Selecione **Portal da Empresa (Offline)**.   
5. Deve esperar que o calendário de sincronização esteja completo ou faça uma sincronização manual do centro de administração do Microsoft Endpoint Manager.
6. Atribuir a aplicação Portal da Empresa como uma aplicação necessária aos grupos de dispositivos de piloto automático selecionados.

## <a name="next-steps"></a>Próximos passos

- Para saber mais sobre a atribuição de apps, consulte [as aplicações de atribuição para grupos.](apps-deploy.md)

