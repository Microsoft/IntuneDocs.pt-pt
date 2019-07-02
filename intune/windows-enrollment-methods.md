---
title: Métodos de inscrição do Intune para dispositivos Windows
titleSuffix: Microsoft Intune
description: Conheça as diferentes formas de poder inscrever dispositivos Windows no Intune
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/25/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: ''
ms.openlocfilehash: b8b1c47e4a2eb46bb8f7190ede351ed77a1bfef4
ms.sourcegitcommit: 116ef72b9da4d114782d4b8dd9f57556c9b01511
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/01/2019
ms.locfileid: "67494503"
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
- [Autopilot](enrollment-autopilot.md) – automatiza a associação do Azure AD e inscreve novos dispositivos pertencentes à empresa no Intune. Esse método simplifica a experiência de out-of-box e remove a necessidade de aplicar imagens de sistema operativo personalizadas nos dispositivos. Quando os administradores utilizam o Intune para gerir dispositivos Autopilot, podem gerir as políticas, perfis, aplicações e muito mais depois de serem inscritos.  Existem quatro tipos de implementação do Autopilot: [Self-implementar o modo](https://docs.microsoft.com/windows/deployment/windows-autopilot/self-deploying) (para quiosques, digital signage ou um dispositivo partilhado), [modo de usuário controlado por](https://docs.microsoft.com/windows/deployment/windows-autopilot/user-driven) (para utilizadores tradicionais), [White Glove] (https://docs.microsoft.com/windows/deployment/windows-autopilot/white-glove) permite que os parceiros ou a equipe de TI pré-aprovisionar um PC com Windows 10 por isso que a TI está completamente configurado e pronto a utilizar e [Autopilot para dispositivos existentes] (https://docs.microsoft.com/windows/deployment/windows-autopilot/existing-devices) permite-lhe facilmente implementar a versão mais recente do Windows 10 para os seus dispositivos existentes.

## <a name="administrator-based-enrollment-in-intune"></a>Com base no administrador de inscrição no Intune

Os administradores podem configurar os seguintes métodos de inscrição, que não exigem nenhuma interação do utilizador:

- [Associação do híbrida do Azure AD](https://docs.microsoft.com/windows/client-management/mdm/enroll-a-windows-10-device-automatically-using-group-policy) permite aos administradores configurar a política de grupo do Active Directory para inscrever automaticamente dispositivos que estão associados ao Azure AD híbrido. 
- [Gestor de configuração de cogestão](https://docs.microsoft.com/sccm/comanage/overview) permite aos administradores inscrever dispositivos existentes do Configuration Manager geridos no Intune para obter os benefícios duplos do Intune e Configuration Manager. 
- [Gestor de inscrição de dispositivos](device-enrollment-manager-enroll.md) (DEM) é uma conta de serviço especiais. Contas DEM tem as permissões que permitem que os utilizadores autorizados inscrever e gerir múltiplos dispositivos pertencentes à empresa. Estes tipos de dispositivo são ideais, por exemplo, para aplicações de utilitários ou ponto de venda, mas não para utilizadores que necessitem de aceder a recursos de e-mail ou da empresa. Este método não permite a utilização de recursos, como o acesso condicional. 
- [Inscrição em massa](windows-bulk-enroll.md) permite que um utilizador autorizado, um grande número de novos dispositivos pertencentes à empresa ao Azure Active Directory e ao Intune. Criar um pacote de aprovisionamento com a aplicação Windows Configuration Designer (WCD). Em seguida, através de USB a experiência de suporte de dados durante o OOBE inicial do Windows ou do PC do Windows existente, instalar o pacote de aprovisionamento para inscrever automaticamente os dispositivos no Intune. Este método não permite a utilização do acesso condicional. 
- [Inscrição de dispositivos do Windows IoT Core](https://docs.microsoft.com/windows/iot-core/manage-your-device/intunedeviceenrollment) é conseguido ao utilizar o Dashboard do Windows IoT Core para preparar o dispositivo e, em seguida, através do Windows Configuration Designer para criar um pacote de aprovisionamento. Em seguida, utilizar suportes de dados do cartão SD durante a inicialização cópia de segurança, ele instala o pacote de aprovisionamento para inscrever automaticamente os dispositivos no Intune.

## <a name="next-steps"></a>Passos Seguintes

[Saiba as capacidades dos métodos de inscrição do Windows](enrollment-method-capab.md)
