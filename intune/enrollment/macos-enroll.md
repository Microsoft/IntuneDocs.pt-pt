---
title: Configurar a inscrição para dispositivos macOS
titleSuffix: Microsoft Intune
description: Saiba como configurar a inscrição para dispositivos macOS no Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 12/16/2019
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
ms.openlocfilehash: 9cddb9b74d9132ace07c17a3156e61148b720d66
ms.sourcegitcommit: 25e4847ead0f56c269cfefe1e01c1b9106a28cf1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/05/2020
ms.locfileid: "78369037"
---
# <a name="set-up-enrollment-for-macos-devices-in-intune"></a>Configurar a inscrição para dispositivos macOS no Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

O Intune permite-lhe gerir dispositivos macOS para conceder aos utilizadores acesso a e-mail e aplicações empresariais.

Enquanto administrador do Intune, pode configurar a inscrição para dispositivos macOS pessoais e pertencentes à empresa ("Bring Your Own Device" ou BYOD). 

## <a name="prerequisites"></a>Pré-requisitos

Antes de configurar a inscrição de dispositivos macOS, tem de cumprir os seguintes pré-requisitos:

- [Certifique-se de que o seu dispositivo é elegível para a inscrição do dispositivo Apple](https://support.apple.com/en-us/HT204142#eligibility).
- [Configurar domínios](../fundamentals/custom-domain-name-configure.md)
- [Definir a Autoridade de MDM](../fundamentals/mdm-authority-set.md)
- [Criar grupos](../fundamentals/groups-add.md)
- [Configurar o Portal da Empresa](../apps/company-portal-app.md)
- Atribuir licenças de utilizador no [Centro de administração do Microsoft 365](https://go.microsoft.com/fwlink/p/?LinkId=698854)
- [Obter um certificado push de MDM da Apple](../enrollment/apple-mdm-push-certificate-get.md)

## <a name="user-owned-macos-devices-byod"></a>Dispositivos Mac OS propriedade do utilizador (BYOD)

Pode permitir que os utilizadores inscrevam os seus próprios dispositivos pessoais na gestão intune. Isto é conhecido como "traga o seu próprio dispositivo" ou BYOD. Depois de ter preenchido os pré-requisitos e as licenças de utilizador atribuídas, os seus utilizadores podem inscrever os seus dispositivos através de:
- Aceder ao [site do Portal da Empresa](https://portal.manage.microsoft.com) ou ao
- descarregando a aplicação Mac Company Portal em [aka.ms/EnrollMyMac.](https://aka.ms/EnrollMyMac)

Também pode enviar aos seus utilizadores um link para as etapas de inscrição online: [Inscreva o seu dispositivo macOS no Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-macos).

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
 
Durante o processo de inscrição BYOD, o utilizador será solicitado a aprovar manualmente o perfil de gestão da Apple. As instruções são fornecidas na aplicação Portal da Empresa para o macOS. Embora a aprovação do perfil de gestão não seja necessária para completar a inscrição, intune recomenda inscrições aprovadas pelo utilizador. Se o utilizador não aprovar o perfil durante a inscrição, o utilizador pode ir às **Preferências** do Sistema > **Perfis,** escolher o perfil de gestão e selecionar **Aprovar**.    

### <a name="find-out-if-a-device-is-user-approved"></a>Descubra se um dispositivo é Aprovado pelo Utilizador
1. Inscreva-se no [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Escolha **Dispositivos** > **Todos os dispositivos**> escolha o dispositivo > **Hardware**.
3. Verifique o campo de **inscrição aprovado** pelo Utilizador.


## <a name="next-steps"></a>Próximos passos

Assim que os dispositivos macOS forem inscritos, pode [criar definições personalizadas para dispositivos macOS](../configuration/custom-settings-macos.md).
