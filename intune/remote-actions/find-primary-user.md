---
title: Localize o usuário primário de um dispositivo Microsoft Intune.
titleSuffix: ''
description: Localize o usuário primário (ou a afinidade de dispositivo de usuário) de um dispositivo do Intune.
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
ms.openlocfilehash: 3d8aadbd876ea03da0f16acea82b71ebd85cf9be
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/05/2019
ms.locfileid: "73712245"
---
# <a name="find-the-primary-user-of-an-intune-device"></a>Localizar o usuário primário de um dispositivo do Intune

O usuário primário, também conhecido como afinidade de dispositivo de usuário, é uma propriedade de cada dispositivo do Intune. Um dispositivo do Intune pode ter zero ou um usuário primário atribuído a ele. Quando não há nenhum usuário primário atribuído, o dispositivo é chamado de "dispositivo compartilhado".

## <a name="how-to-find-a-devices-primary-user"></a>Como localizar o usuário primário de um dispositivo

1. Entre no centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Escolha **dispositivos** > escolha um dispositivo.
3. Na página **visão geral** , escolha **Ver mais** e você verá o usuário primário listado.

## <a name="what-is-the-primary-user"></a>O que é o usuário principal?
A propriedade usuário primário é usada para mapear um usuário do Intune licenciado para seus dispositivos no:
- O aplicativo Portal da Empresa
- Site do usuário final
- Experiências de profissionais de ti, como as páginas de solução de problemas no portal do Azure. Essas páginas mapeiam contas de usuário para dispositivos usando o usuário primário.    

### <a name="company-portal-app"></a>Aplicação Portal da Empresa
O aplicativo Portal da Empresa espera que a conta de usuário que entrou no Portal da Empresa seja o usuário principal desse dispositivo. Se outro usuário tiver sido atribuído como o usuário primário, o Portal da Empresa mostrará um aviso:

"Este dispositivo já está atribuído a alguém em sua organização. Contate o suporte da empresa sobre como se tornar o usuário do dispositivo primário. Você pode continuar a usar Portal da Empresa, mas a funcionalidade será limitada. "

Se um dispositivo do Intune não tiver um usuário primário atribuído, o aplicativo Portal da Empresa o detectará como um dispositivo compartilhado. Os dispositivos compartilhados são visualmente identificáveis com um rótulo "compartilhado" que aparece no bloco do dispositivo. Nesse modo, o Portal da Empresa ainda pode ser usado para solicitar e instalar aplicativos disponíveis. No entanto, as ações de autoatendimento (redefinir/renomear/desativar) não estão disponíveis.  

Para aparecer na Portal da Empresa em dispositivos compartilhados, os aplicativos disponíveis devem ser atribuídos a um grupo de usuários. Eles serão instalados no contexto do sistema ou no contexto do usuário, dependendo de como o aplicativo foi configurado pelo administrador de ti. Para obter mais informações sobre o contexto do aplicativo, consulte [Instalando aplicativos em dispositivos Windows 10](../apps/apps-windows-10-app-deploy.md). Portal da Empresa versão 10.3.4651.0 ou posterior é necessária para usar esse recurso.


## <a name="who-is-assigned-as-the-primary-user"></a>Quem é atribuído como o usuário primário?
O Intune adiciona automaticamente o usuário primário aos dispositivos durante ou logo após o registro. O método de registro determina quando o usuário primário é adicionado a um dispositivo.

| Platform | Método de inscrição | Usuário primário atribuído | O usuário primário é atribuído |
| ---- | ---- | ---- | ---- |
| Windows | Adicionar trabalho ou escola (orientado pelo usuário) | Registrando usuário | Durante o registro |   
| Windows | Entrada de aplicativo moderno (orientada pelo usuário) | Registrando usuário | Durante o registro | 
| Windows | Registrar somente no MDM (orientado pelo usuário) | Registrando usuário | Durante o registro | 
| Windows | Ingresso no Azure AD (experiência inicial na caixa) | Registrando usuário | Durante o registro | 
| Windows | Ingresso no Azure AD (autoteste de experiência inicial do box) | Registrando usuário | Durante o registro | 
| Windows | Registrar somente no MDM | Registrando usuário | Durante o registro | 
| Windows | AADJ híbrido + GPO de registro automático | Primeiro usuário a entrar no Windows | Quando o primeiro usuário entra no Windows| 
| Windows | Cogestão | Primeiro usuário a entrar no Windows | Quando o primeiro usuário entra no Windows | 
| Windows | Ingresso no Azure AD (token de registro em massa) | Nenhum | Not applicable | 
| Windows | Ingresso no Azure AD (modo de autoimplantação do autoteste) | Nenhum | Not applicable | 
| Multiplataformas | Registro controlado pelo usuário com o aplicativo Portal da Empresa | Registrando usuário | Durante o registro |
| Multiplataformas | Gerenciador de registro de dispositivo (DEM) | Registrando usuário do DEM | Durante o registro |
| iOS, macOS | Registro de dispositivo automatizado da Apple (DEP com afinidade de usuário | Registrando usuário | Durante o registro |
| iOS, macOS | Registro de dispositivo automatizado da Apple (DEP sem afinidade de usuário) | Nenhum | Not applicable |
| Android | Dispositivos Android de propriedade corporativa, dedicados | Nenhum | Not applicable |

## <a name="primary-user-and-azure-ad-device-owner"></a>Usuário primário e proprietário do dispositivo do Azure AD
Em alguns casos, o usuário principal do Intune pode ser diferente da propriedade **proprietário** do dispositivo do Azure AD (visível em **dispositivos** > **dispositivos do Azure ad**). O proprietário do dispositivo do Azure AD é adicionado durante o registro de um dispositivo no Azure Active Directory.

## <a name="next-steps"></a>Próximos passos
[Gerencie seus dispositivos do Intune.](device-management.md)
