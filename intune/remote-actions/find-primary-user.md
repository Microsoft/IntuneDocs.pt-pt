---
title: Encontre o utilizador principal de um dispositivo Microsoft Intune.
titleSuffix: ''
description: Encontre o utilizador principal (ou Afinidade do Dispositivo de Utilizador) de um dispositivo Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7ff03682ab406b92e3ea7f1e416188119913cc87
ms.sourcegitcommit: 5881979c45fc973cba382413eaa193d369b8dcf6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/24/2020
ms.locfileid: "77569460"
---
# <a name="find-the-primary-user-of-an-intune-device"></a>Encontre o utilizador principal de um dispositivo Intune

O utilizador principal, também conhecido como User Device Affinity, é uma propriedade de cada dispositivo Intune. Um dispositivo Intune pode ter zero ou um utilizador primário atribuído ao mesmo. Quando não há utilizador primário atribuído, o dispositivo é referido como um "Dispositivo Partilhado".

## <a name="find-a-devices-primary-user"></a>Encontre o principal utilizador de um dispositivo

1. Inscreva-se no [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Escolha **Dispositivos** > escolha um dispositivo.
3. Na página **'Visão Geral',** escolha **mais ver mais** e verá o utilizador principal listado.

## <a name="what-is-the-primary-user"></a>Qual é o utilizador principal?
A propriedade principal do utilizador é usada para mapear um utilizador Intune licenciado para os seus dispositivos em:
- A aplicação Portal da Empresa
- Website do utilizador final
- Experiências profissionais de TI, como páginas de resolução de problemas no portal Azure. Estas páginas mapeiam as contas dos utilizadores para os dispositivos utilizando o utilizador principal. 

### <a name="company-portal-app"></a>Aplicação do Portal da Empresa
A aplicação Portal da Empresa espera que a conta de utilizador que assinou no Portal da Empresa seja o principal utilizador desse dispositivo. Se outro utilizador tiver sido designado como utilizador principal, o Portal da Empresa mostra um aviso:

"Este dispositivo já está atribuído a alguém da sua organização. Contacte o suporte da empresa para se tornar o utilizador principal do dispositivo. Pode continuar a utilizar o Portal da Empresa, mas a funcionalidade será limitada."

Se um dispositivo Intune não tiver nenhum utilizador primário atribuído, então a aplicação Portal da Empresa deteta-o como um dispositivo partilhado. Os dispositivos partilhados são visualmente identificáveis com uma etiqueta "partilhada" aparecendo no azulejo do dispositivo. Neste modo, o Portal da Empresa ainda pode ser utilizado para solicitar e instalar aplicações disponíveis. No entanto, as ações de self-service (reset/rename/retire) não estão disponíveis.  

Para aparecer no Portal da Empresa em dispositivos partilhados, as aplicações disponíveis devem ser atribuídas a um grupo de utilizadores. Serão instalados no contexto do sistema ou no contexto do utilizador, dependendo da forma como a aplicação foi configurada pelo administrador de TI. Para obter mais informações sobre o contexto da aplicação, consulte [a instalação de aplicações nos dispositivos do Windows 10.](../apps/apps-windows-10-app-deploy.md) A versão 10.3.4651.0 ou posterior do Portal da Empresa é obrigada a utilizar esta funcionalidade.


## <a name="who-is-assigned-as-the-primary-user"></a>Quem é designado como o utilizador principal?
Intone automaticamente o utilizador primário aos dispositivos durante ou logo após a inscrição. O método de inscrição determina quando o utilizador primário é adicionado a um dispositivo.

| Platform | Método de inscrição | Utilizador primário atribuído | Utilizador primário é atribuído |
| ---- | ---- | ---- | ---- |
| Windows | Adicionar trabalho ou escola (orientado pelo utilizador) | Utilizador inscrito | Durante a inscrição |   
| Windows | Inscrição na Aplicação Moderna (orientada pelo utilizador) | Utilizador inscrito | Durante a inscrição | 
| Windows | Matricule-se apenas no MDM (acionado pelo utilizador) | Utilizador inscrito | Durante a inscrição | 
| Windows | Azure AD junta-se (fora da experiência box) | Utilizador inscrito | Durante a inscrição | 
| Windows | Azure AD junta-se (Autopilot fora da experiência box) | Utilizador inscrito | Durante a inscrição | 
| Windows | Matricule-se apenas no MDM | Utilizador inscrito | Durante a inscrição | 
| Windows | Híbrido AADJ + GPO de inscrição automática | Primeiro utilizador a iniciar sessão no Windows | Quando o primeiro utilizador entra no Windows| 
| Windows | Cogestão | Primeiro utilizador a iniciar sessão no Windows | Quando o primeiro utilizador entra no Windows | 
| Windows | Azure AD junta-se (símbolo de inscrição a granel) | Nenhum | Não aplicável | 
| Windows | AD Azure (modo de auto-implantação autopiloto) | Nenhum | Não aplicável | 
| Plataforma cruzada | Inscrição orientada pelo utilizador com App Portal da Empresa | Utilizador inscrito | Durante a inscrição |
| Plataforma cruzada | Gestor de Inscrição de Dispositivos (DEM) | Inscrição do utilizador DEM | Durante a inscrição |
| iOS/iPadOS, macOS | Apple Automated Device Matricula (DEP com afinidade do utilizador | Utilizador inscrito | Durante a inscrição |
| iOS/iPadOS, macOS | Apple Automated Device Registration (DEP sem afinidade do utilizador) | Nenhum | Não aplicável |
| Android | Dispositivos Android Corporate-Owned, dedicados | Nenhum | Não aplicável |

## <a name="primary-user-and-azure-ad-device-owner"></a>Utilizador primário e proprietário de dispositivo saqueado do Azure
Em alguns casos, o utilizador primário intune pode ser diferente da propriedade do **Dispositivo** AD Azure (visível em **dispositivos** > **Dispositivos AD Azure).** O proprietário do Dispositivo AD Azure é adicionado durante a inscrição de um dispositivo no Diretório Ativo Azure.

## <a name="next-steps"></a>Próximos passos
[Gerencie os seus dispositivos Intune.](device-management.md)
