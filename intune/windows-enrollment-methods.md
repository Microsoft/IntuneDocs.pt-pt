---
title: Métodos de inscrição do Intune para dispositivos Windows
titleSuffix: Microsoft Intune
description: Conheça as diferentes formas de poder inscrever dispositivos Windows no Intune
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/02/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: ''
ms.openlocfilehash: 346b74871b7519e03ca3e68061f690ef1a4e6d6a
ms.sourcegitcommit: 55323746ca3c1c66326f1453ba66ded9c1b73b0e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/02/2019
ms.locfileid: "58867578"
---
# <a name="intune-enrollment-methods-for-windows-devices"></a>Métodos de inscrição do Intune para dispositivos Windows

Para gerir dispositivos no Intune, dispositivos primeiro têm de estar inscritos no serviço do Intune. Ambos pessoais e dispositivos pertencentes à empresa podem ser inscritos para gestão do Intune. 

Existem duas formas de os dispositivos inscritos no Intune:
- Os utilizadores podem inscrever seus PCs Windows 
- Os administradores podem configurar políticas para forçar a inscrição automática sem qualquer envolvimento do utilizador

## <a name="user-self-enrollment-in-intune"></a>Autoinscrição do utilizador no Intune

Os utilizadores podem inscrever os dispositivos Windows, utilizando qualquer um dos seguintes métodos:

- [Traga o seu próprio dispositivo (BYOD)](https://docs.microsoft.com/intune-user-help/enroll-windows-10-device): Os utilizadores inscrevem os respetivos dispositivos pessoais ao optar por ligar um **profissionais e escolares** conta a partir **definições** do dispositivo. Este processo:
    - Regista o dispositivo com o Azure Active Directory para obter acesso aos recursos da empresa, como o e-mail.
    - Inscreve o dispositivo no Intune como um dispositivo de propriedade pessoal (BYOD).
Se um administrador tiver configurado a inscrição automática (disponível com as assinaturas premium do Azure AD), o utilizador só tem de introduzir as respetivas credenciais de uma vez. Caso contrário, será necessário inscrever em separado através de inscrição de apenas de MDM e reintroduza as respetivas credenciais.  
- **Inscrição de MDM apenas** permite que os utilizadores inscrever um grupo de trabalho existente, Active Directory, ou associados ao Azure Active directory PC no Intune. Os utilizadores inscrever a partir das definições do PC Windows existente. Este método não é recomendado porque ele não registar o dispositivo no Azure Active Directory. Ele também impede a utilização de recursos, como o acesso condicional.
- [Associação do Azure do Active Directory (Azure AD)](https://docs.microsoft.com/azure/active-directory/user-help/user-help-join-device-on-network) - associar o dispositivo com o Azure Active Directory e permite aos utilizadores iniciar sessão no Windows com as credenciais do Azure AD. Se a inscrição automática estiver ativada, o dispositivo é inscrito automaticamente no Intune. A vantagem de inscrição automática é um processo passo a passo para o utilizador. Caso contrário, será necessário inscrever em separado através de inscrição de apenas de MDM e reintroduza as respetivas credenciais. Os utilizadores inscrever desta forma, durante o OOBE inicial do Windows ou a partir das definições. O dispositivo é marcado como um dispositivo propriedade da empresa no Intune.
- [Autopilot](enrollment-autopilot.md) – automatiza a associação do Azure AD e inscreve novos dispositivos pertencentes à empresa no Intune. Esse método simplifica a experiência de out-of-box e remove a necessidade de aplicar imagens de sistema operativo personalizadas nos dispositivos. Quando os administradores utilizam o Intune para gerir dispositivos Autopilot, podem gerir as políticas, perfis, aplicações e muito mais depois de serem inscritos.  Existem dois tipos de implementação do Autopilot: [Modo de implementação automática](https://docs.microsoft.com/windows/deployment/windows-autopilot/self-deploying) (para quiosques, digital signage ou um dispositivo partilhado) e [modo de usuário controlado por](https://docs.microsoft.com/windows/deployment/windows-autopilot/user-driven) (para usuários tradicionais). 

## <a name="administrator-based-enrollment-in-intune"></a>Com base no administrador de inscrição no Intune

Os administradores podem configurar os seguintes métodos de inscrição, que não exigem nenhuma interação do utilizador:

- [Associação do híbrida do Azure AD](https://docs.microsoft.com/windows/client-management/mdm/enroll-a-windows-10-device-automatically-using-group-policy) permite aos administradores configurar a política de grupo do Active Directory para inscrever automaticamente dispositivos que estão associados ao Azure AD híbrido. 
- [Gestor de configuração de cogestão](https://docs.microsoft.com/sccm/comanage/overview) permite aos administradores inscrever dispositivos existentes do Configuration Manager geridos no Intune para obter os benefícios duplos do Intune e Configuration Manager. 
- [Gestor de inscrição de dispositivos](device-enrollment-manager-enroll.md) (DEM) é uma conta de serviço especiais. Contas DEM tem as permissões que permitem que os utilizadores autorizados inscrever e gerir múltiplos dispositivos pertencentes à empresa. Estes tipos de dispositivo são ideais, por exemplo, para aplicações de utilitários ou ponto de venda, mas não para utilizadores que necessitem de aceder a recursos de e-mail ou da empresa. Além disso, este método não permite a utilização de recursos, como o acesso condicional. 
- [Inscrição em massa](windows-bulk-enroll.md) permite que um utilizador autorizado, um grande número de novos dispositivos pertencentes à empresa ao Azure Active Directory e ao Intune. Criar um pacote de aprovisionamento com a aplicação Windows Configuration Designer (WCD). Em seguida, através de USB a experiência de suporte de dados durante o OOBE inicial do Windows ou do PC do Windows existente, instalar o pacote de aprovisionamento para inscrever automaticamente os dispositivos no Intune. 

## <a name="next-steps"></a>Passos Seguintes

[Saiba as capacidades dos métodos de inscrição do Windows](enrollment-method-capab.md)