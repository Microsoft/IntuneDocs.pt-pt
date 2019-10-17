---
title: Métodos de registro do Intune para dispositivos Windows
titleSuffix: Microsoft Intune
description: Conheça as diferentes maneiras de registrar dispositivos Windows no Intune
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/25/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: ''
ms.openlocfilehash: 59ba9ab5fb0ddeb527ed852de042568920cf38e1
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72509190"
---
# <a name="intune-enrollment-methods-for-windows-devices"></a>Métodos de registro do Intune para dispositivos Windows

Para gerenciar dispositivos no Intune, os dispositivos devem primeiro ser registrados no serviço do Intune. Dispositivos pessoais e de propriedade corporativa podem ser registrados para o gerenciamento do Intune. 

Há duas maneiras de obter os dispositivos registrados no Intune:
- Os usuários podem registrar automaticamente seus computadores Windows 
- Os administradores podem configurar políticas para forçar o registro automático sem qualquer envolvimento do usuário

## <a name="user-self-enrollment-in-intune"></a>Registro automático do usuário no Intune

Os usuários podem registrar automaticamente seu dispositivo Windows usando qualquer um destes métodos:

- [BYOD (Traga seu próprio dispositivo)](https://docs.microsoft.com/intune-user-help/enroll-windows-10-device): os usuários registram seus dispositivos de propriedade pessoal escolhendo conectar uma conta **corporativa e de estudante** das **configurações** do dispositivo. Este processo:
  - Registra o dispositivo com Azure Active Directory para obter acesso a recursos corporativos como email.
  - Registra o dispositivo no Intune como um dispositivo de propriedade pessoal (BYOD).
Se um administrador tiver configurado o registro automático (disponível com as assinaturas do Azure AD Premium), o usuário só precisará inserir suas credenciais uma vez. Caso contrário, eles terão que registrar separadamente por meio do registro somente MDM e reinserir suas credenciais.  
- O **registro somente MDM** permite que os usuários registrem um grupo de trabalho existente, Active Directory ou um PC ingressado no Azure Active Directory no Intune. Os usuários se registram a partir de configurações no computador Windows existente. Esse método não é recomendado porque não registra o dispositivo em Azure Active Directory. Ele também impede o uso de recursos como o acesso condicional.
- [Junção do Azure Active Directory (Azure AD)](https://docs.microsoft.com/azure/active-directory/user-help/user-help-join-device-on-network) – une o dispositivo com o Azure Active Directory e permite que os usuários entrem no Windows com suas credenciais do Azure AD. Se o registro automático estiver habilitado, o dispositivo será registrado automaticamente no Intune. O benefício do registro automático é um processo de etapa única para o usuário. Caso contrário, eles terão que registrar separadamente por meio do registro somente MDM e reinserir suas credenciais. Os usuários se registram dessa forma durante as configurações iniciais do Windows OOBE ou from. O dispositivo está marcado como um dispositivo de propriedade corporativa no Intune.
- [AutoPilot](enrollment-autopilot.md) – automatiza o ingresso no Azure AD e registra novos dispositivos corporativos no Intune. Esse método simplifica a experiência inicial no uso e elimina a necessidade de aplicar imagens personalizadas do sistema operacional nos dispositivos. Quando os administradores usam o Intune para gerenciar dispositivos de piloto automático, eles podem gerenciar políticas, perfis, aplicativos e muito mais depois que eles são registrados.  Há quatro tipos de implantação automática de piloto: [modo de autoimplantação](https://docs.microsoft.com/windows/deployment/windows-autopilot/self-deploying) (para quiosques, pôsteres digitais ou um dispositivo compartilhado), [modo controlado pelo usuário](https://docs.microsoft.com/windows/deployment/windows-autopilot/user-driven) (para usuários tradicionais), [White diferenciada] (https://docs.microsoft.com/windows/deployment/windows-autopilot/white-glove) permite que os parceiros ou a equipe de ti desprovisionem previamente um PC com Windows 10 para que ele seja totalmente configurado e pronto para os negócios e [piloto automático para dispositivos existentes] (https://docs.microsoft.com/windows/deployment/windows-autopilot/existing-devices) permite que você implante facilmente a versão mais recente do Windows 10 em seus dispositivos existentes.

## <a name="administrator-based-enrollment-in-intune"></a>Registro baseado em administrador no Intune

Os administradores podem configurar os seguintes métodos de registro que não exigem interação do usuário:

- O [ingresso no Azure ad híbrido](https://docs.microsoft.com/windows/client-management/mdm/enroll-a-windows-10-device-automatically-using-group-policy) permite que os administradores configurem Active Directory política de grupo para registrar automaticamente os dispositivos que são ingressados no Azure ad híbrido. 
- [Configuration Manager cogerenciamento](https://docs.microsoft.com/sccm/comanage/overview) permite que os administradores registrem seus dispositivos Configuration Manager gerenciados existentes no Intune para obter os benefícios duplos do Intune e Configuration Manager. 
- O DEM ( [Gerenciador de registro de dispositivo](device-enrollment-manager-enroll.md) ) é uma conta de serviço especial. As contas do DEM têm permissões que permitem que usuários autorizados registrem e gerenciem vários dispositivos de propriedade corporativa. Estes tipos de dispositivo são ideais, por exemplo, para aplicações de utilitários ou ponto de venda, mas não para utilizadores que necessitem de aceder a recursos de e-mail ou da empresa. Esse método não permite o uso de recursos como o acesso condicional. 
- O [registro em massa](../windows-bulk-enroll.md) permite que um usuário autorizado ingresse em um grande número de novos dispositivos corporativos para Azure Active Directory e o Intune. Você cria um pacote de provisionamento com o aplicativo do Windows Configuration designer (WCD). Em seguida, usando a mídia USB durante a experiência inicial do Windows OOBE ou do computador Windows existente, você instala o pacote de provisionamento para registrar automaticamente os dispositivos no Intune. Esse método não permite o uso de acesso condicional. 
- O [registro de dispositivos Windows IOT Core](https://docs.microsoft.com/windows/iot-core/manage-your-device/intunedeviceenrollment) é realizado usando o painel do Windows IOT Core para preparar o dispositivo e, em seguida, usar o designer de configuração do Windows para criar um pacote de provisionamento. Em seguida, usando mídia de cartão SD durante a inicialização inicial, ele instala o pacote de provisionamento para registrar automaticamente os dispositivos no Intune.

## <a name="next-steps"></a>Próximos passos

[Conheça os recursos dos métodos de registro do Windows](enrollment-method-capab.md)
