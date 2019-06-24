---
title: Localize o utilizador primário de um dispositivo do Microsoft Intune.
titleSuffix: ''
description: Encontre o utilizador principal (ou afinidade dispositivo / utilizador) de um dispositivo do Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b6a20ccec2ef0cbaba87637b3c44c2cc2be094ab
ms.sourcegitcommit: b3a1c5b0b24f0e52cf318defe10f3d27a2770009
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/21/2019
ms.locfileid: "67322875"
---
# <a name="find-the-primary-user-of-an-intune-device"></a>Encontre o utilizador primário de um dispositivo do Intune

Utilizador primário, também conhecido como afinidade dispositivo / utilizador, é uma propriedade de cada dispositivo do Intune. Um dispositivo do Intune pode ter zero ou um utilizador primário atribuído. Quando não existe nenhum utilizador primário atribuído, o dispositivo é referido como um "dispositivo partilhado".

## <a name="how-to-find-a-devices-primary-user"></a>Como localizar o utilizador primário de um dispositivo

1. Inicie sessão no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Escolher **dispositivos** > Escolha um dispositivo.
3. Sobre o **descrição geral** página, selecione **ver mais** e verá que o utilizador primário listado.

## <a name="what-is-the-primary-user"></a>O que é o utilizador primário?
A propriedade de utilizador principal é usada para mapear um utilizador do Intune licenciado para os dispositivos no:
- A aplicação do Portal da empresa
- Web site do utilizador final
- IT profissionais experiências, como resolução de problemas de páginas no portal do Azure. Essas páginas mapeiam as contas de utilizador para dispositivos com o utilizador primário.    

### <a name="company-portal-app"></a>Aplicação Portal da Empresa
A aplicação Portal da empresa espera que a conta de utilizador que iniciou sessão no Portal da empresa é o utilizador primário desse dispositivo. Se outro utilizador tiver sido atribuído como o utilizador primário, o Portal da empresa mostra um aviso:

"Este dispositivo já está atribuído a alguém na sua organização. Suporte da empresa do contacto como se pode tornar o utilizador do dispositivo primário. Pode continuar a utilizar o Portal da empresa mas funcionalidade estará limitada".

Se um dispositivo do Intune não tem nenhum utilizador primário atribuído, em seguida, a aplicação Portal da empresa detectá-lo como um dispositivo partilhado. Dispositivos partilhados são identificáveis visualmente com uma etiqueta "partilhada" que aparece no mosaico do dispositivo. Neste modo, o Portal da empresa ainda pode ser utilizado para pedir e instalar aplicações disponíveis. No entanto, ações de Self-serviços (reposição/renomear/extinção) não estão disponíveis.  

A aparecer no Portal da empresa nos dispositivos partilhados, tem de atribuir as aplicações disponíveis para um grupo de utilizadores. Eles vai ser instalados no contexto do sistema ou no contexto de utilizador, dependendo de como a aplicação foi configurada pelo administrador de TI. Para obter mais informações sobre o contexto de aplicação, consulte [instalação de aplicações em dispositivos Windows 10](apps-windows-10-app-deploy.md#installing-apps-on-windows-10-devices). Versão 10.3.4651.0 do Portal da empresa ou posterior é necessário para utilizar esta funcionalidade.


## <a name="who-is-assigned-as-the-primary-user"></a>Quem é atribuído como o utilizador primário?
O Intune adiciona automaticamente utilizador primário aos dispositivos durante ou logo após a inscrição. O método de inscrição determina quando o utilizador primário é adicionado a um dispositivo.

| Plataforma | Método de inscrição | Utilizador primário atribuído | Utilizador primário é atribuído |
| ---- | ---- | ---- | ---- |
| Windows | Adicionar profissional ou escolar (controlada pelo usuário) | Inscrição de utilizador | Durante a inscrição |   
| Windows | Modernos aplicação início de sessão (controlada pelo usuário) | Inscrição de utilizador | Durante a inscrição | 
| Windows | Inscreva-se no MDM apenas (controlada pelo usuário) | Inscrição de utilizador | Durante a inscrição | 
| Windows | Associação do Azure AD (de experiência de caixa) | Inscrição de utilizador | Durante a inscrição | 
| Windows | Associação do Azure AD, (Autopilot para fora da experiência) | Inscrição de utilizador | Durante a inscrição | 
| Windows | Inscreva-se no MDM apenas | Inscrição de utilizador | Durante a inscrição | 
| Windows | Híbrido AADJ + GPO a inscrição automática | Primeiro utilizador que inicie sessão | Quando o primeiro utilizador inicia sessão | 
| Windows | Cogestão | Primeiro utilizador que inicie sessão | Quando o primeiro utilizador inicia sessão | 
| Windows | Associação do Azure AD, (token de inscrição em massa) | Nenhum | Não aplicável | 
| Windows | Associação do Azure AD, (modo de Self-implementação do Autopilot) | Nenhum | Não aplicável | 
| Para várias plataformas | Inscrição de orientado por utilizadores com a aplicação Portal da empresa | Inscrição de utilizador | Durante a inscrição |
| Para várias plataformas | Gestor de inscrição de dispositivos (DEM) | Inscrição de utilizador DEM | Durante a inscrição |
| iOS, macOS | Apple automatizada de inscrição de dispositivos (DEP com afinidade do utilizador | Inscrição de utilizador | Durante a inscrição |
| iOS, macOS | Apple automatizada de inscrição de dispositivos (DEP sem afinidade do utilizador) | Nenhuma | Não aplicável |
| Android | Android dispositivos dedicados pertencentes à empresa | Nenhum | Não aplicável |

## <a name="primary-user-and-azure-ad-device-owner"></a>Utilizador primário e o proprietário do dispositivo do Azure AD
Em alguns casos, o utilizador primário do Intune pode ser diferente do dispositivo do Azure AD **proprietário** propriedade (visível sob **dispositivos** > **dispositivos do Azure AD**). O proprietário do dispositivo do Azure AD é adicionado durante o registo de um dispositivo no Azure Active Directory.

## <a name="next-steps"></a>Passos Seguintes
[Gerir os seus dispositivos do Intune.](device-management.md)
