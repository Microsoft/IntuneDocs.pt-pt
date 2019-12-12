---
title: Configurar a inscrição para dispositivos macOS
titleSuffix: Microsoft Intune
description: Saiba como configurar a inscrição para dispositivos macOS no Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/14/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 46429114-2e26-4ba7-aa21-b2b1a5643e01
ms.reviewer: tisilver
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 684e9602e66842e26a7f8e233a8cee6db73f132d
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/05/2019
ms.locfileid: "74098196"
---
# <a name="set-up-enrollment-for-macos-devices-in-intune"></a>Configurar a inscrição para dispositivos macOS no Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

O Intune permite-lhe gerir dispositivos macOS para conceder aos utilizadores acesso a e-mail e aplicações empresariais.

Enquanto administrador do Intune, pode configurar a inscrição para dispositivos macOS pessoais e pertencentes à empresa ("Bring Your Own Device" ou BYOD). 

## <a name="prerequisites"></a>Pré-requisitos

Antes de configurar a inscrição de dispositivos macOS, tem de cumprir os seguintes pré-requisitos:

- [Verifique se o dispositivo está qualificado para o registro de dispositivo da Apple](https://support.apple.com/en-us/HT204142#eligibility).
- [Configurar domínios](../fundamentals/custom-domain-name-configure.md)
- [Definir a Autoridade de MDM](../fundamentals/mdm-authority-set.md)
- [Criar grupos](../fundamentals/groups-add.md)
- [Configurar o Portal da Empresa](../apps/company-portal-app.md)
- Atribuir licenças de utilizador no [Centro de administração do Microsoft 365](https://go.microsoft.com/fwlink/p/?LinkId=698854)
- [Obter um certificado push de MDM da Apple](../enrollment/apple-mdm-push-certificate-get.md)

## <a name="user-owned-macos-devices-byod"></a>Dispositivos Mac OS propriedade do utilizador (BYOD)

Você pode permitir que os usuários registrem seus próprios dispositivos pessoais no gerenciamento do Intune. Isso é conhecido como "Traga seu próprio dispositivo" ou BYOD. Depois de concluir os pré-requisitos e as licenças de usuário atribuídas, os usuários poderão registrar seus dispositivos:
- Aceder ao [site do Portal da Empresa](https://portal.manage.microsoft.com) ou ao
- baixando o aplicativo Mac Portal da Empresa em [aka.ms/EnrollMyMac](https://aka.ms/EnrollMyMac).

Você também pode enviar aos usuários um link para as etapas de registro online: [registrar seu dispositivo MacOS no Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-macos).

Para obter informações sobre outras tarefas do utilizador final, veja estes artigos:

- [Recursos sobre a experiência do utilizador final com o Microsoft Intune](../fundamentals/end-user-educate.md)
- [Utilizar o dispositivo macOS com o Intune](/intune-user-help/using-your-macos-device-with-intune)

## <a name="company-owned-macos-devices"></a>Dispositivos macOS pertencentes à empresa
Para as organizações que compram dispositivos para os respetivos utilizadores, o Intune suporta os seguintes métodos de inscrição de dispositivos macOS pertencentes à empresa:
- [Programa de Registo de Aparelho (DEP) da Apple](device-enrollment-program-enroll-macos.md): as organizações podem adquirir dispositivos macOS através do Programa de Inscrição de Dispositivos (DEP) da Apple. O DEP permite-lhe implementar um perfil de inscrição através de uma ligação sem fios para incluir os dispositivos na gestão.
- [Gestor de inscrições de dispositivos (DEM)](device-enrollment-manager-enroll.md): pode utilizar uma conta DEM para inscrever até 1000 dispositivos.

## <a name="block-macos-enrollment"></a>Bloquear a inscrição de dispositivos macOS
Por predefinição, o Intune permite a inscrição de dispositivos macOS. Para impedir a inscrição de dispositivos macOS, veja [Set device type restrictions (Definir restrições de tipos de dispositivos)](enrollment-restrictions-set.md).

## <a name="enroll-virtual-macos-machines-for-testing"></a>Inscrever máquinas virtuais macOS para teste

> [!NOTE]
> As máquinas virtuais macOS são suportadas apenas para teste. Não deve utilizar máquinas virtuais macOS como dispositivos de produção para os seus utilizadores finais. 

Pode inscrever máquinas virtuais macOS para teste com o Parallels Desktop ou a VMware Fusion. 

Para o Parallels Desktop, precisa de definir o tipo de hardware e o número de série das máquinas virtuais, para que o Intune possa reorganizá-las. Siga as instruções do Parallels para definir o tipo de hardware e o [número de série](http://kb.parallels.com/123455) para configurar as definições necessárias para o teste. Recomendamos que faça corresponder o tipo de hardware do dispositivo a executar as máquinas virtuais ao tipo de hardware das máquinas virtuais que está a criar. Pode encontrar este tipo de hardware em **Menu Apple** > **Acerca deste Mac** > **Relatório do Sistema** > **Identificador de Modelo**. 

Para a VMware Fusion, precisa de [editar o ficheiro .vmx](https://kb.vmware.com/s/article/1014782) para definir o número de série e o modelo de hardware da máquina virtual. Recomendamos que faça corresponder o tipo de hardware do dispositivo a executar as máquinas virtuais ao tipo de hardware das máquinas virtuais que está a criar. Pode encontrar este tipo de hardware em **Menu Apple** > **Acerca deste Mac** > **Relatório do Sistema** > **Identificador de Modelo**. 

## <a name="user-approved-enrollment"></a>Inscrição do Utilizador Aprovado
A inscrição na MDM do Utilizador Aprovado é um tipo de inscrição de macOS que pode utilizar para gerir determinadas definições relacionadas com a segurança. Para obter mais informações, veja a [documentação de suporte da Apple](https://support.apple.com/HT208019).

A partir de novembro de 2019, todos os novos registros do macOS do usuário serão aprovados, pois o usuário deve instalar manualmente o perfil de gerenciamento para se registrar com êxito. Durante [o processo de registro](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-macos-cp), o usuário instalará o perfil de gerenciamento da Apple em **preferências do sistema** > **perfis**.  As instruções para instalar o perfil de gerenciamento estão disponíveis no aplicativo macOS Portal da Empresa.

Os dispositivos registrados antes de novembro de 2019 podem não ser aprovados pelo usuário se o usuário não aprovar manualmente o perfil de gerenciamento. No entanto, os usuários podem voltar e aprovar o perfil de gerenciamento acessando **preferências do sistema** > **perfis** > escolher o **perfil de gerenciamento** > **aprovar**.

### <a name="find-out-if-a-device-is-user-approved"></a>Descubra se um dispositivo foi aprovado pelo usuário
1. Entre no centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Escolha **dispositivos** > **todos os dispositivos**> escolha o dispositivo > **hardware**.
3. Verifique o campo **registro aprovado pelo usuário** .


## <a name="next-steps"></a>Próximos passos

Assim que os dispositivos macOS forem inscritos, pode [criar definições personalizadas para dispositivos macOS](../configuration/custom-settings-macos.md).
