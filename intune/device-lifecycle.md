---
title: "Descrição geral do ciclo de vida de MDM do Microsoft Intune"
description: "Saiba como o Intune o ajuda a gerir dispositivos através do respetivo ciclo de vida, desde a inscrição até à configuração e à eventual extinção."
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/2/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 8755faef07e6ddae2177a2fc2453e15f1ea0fefe
ms.sourcegitcommit: 7e5c4d43cbd757342cb731bf691ef3891b0792b5
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/05/2018
---
# <a name="overview-of-the-microsoft-intune-mobile-device-management-mdm-lifecycle"></a>Descrição geral do ciclo de vida da gestão de dispositivos móveis (MDM) do Microsoft Intune

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

Todos os dispositivos que gere têm um *ciclo de vida*. O Intune pode ajudá-lo a gerir este ciclo de vida desde a inscrição até à configuração, proteção e extinção do dispositivo quando já não for necessário.

![Ciclo de vida do dispositivo](./media/device-lifecycle.png "ciclo de vida do dispositivo do Intune")

## <a name="enroll"></a>Inscrever
As atuais estratégias de gestão de dispositivos móveis (MDM) lidam com uma variedade de telemóveis, tablets e PCs (iOS, Android, Windows e Mac OS X). Se precisar de ter a capacidade de gerir o dispositivo, o que é normalmente o caso dos dispositivos pertencentes à empresa, o primeiro passo consiste em [configurar a inscrição do dispositivo](device-enrollment.md) ([Portal clássico](/intune-classic/deploy-use/enroll-devices-in-microsoft-intune)). Também pode gerir PCs Windows, inscrevendo-os no Intune (MDM) ou [instalando o software de cliente do Intune](/intune-classic/deploy-use/manage-windows-pcs-with-microsoft-intune).

## <a name="configure"></a>Configurar
Inscrever os seus dispositivos é apenas o primeiro passo. Para tirar partido de tudo o que o Intune oferece e para garantir que os seus dispositivos estão protegidos e em conformidade com as normas da empresa, pode escolher de entre um vasto leque de políticas. Estas permitem-lhe configurar quase todos os aspetos do funcionamento dos dispositivos geridos. Por exemplo, os utilizadores devem ter palavras-passe em dispositivos que tenham dados da empresa? Pode pedir uma. Tem Wi-Fi da empresa? Pode configurá-la automaticamente. Eis os tipos de opções de configuração disponíveis:

- [**Configuração do dispositivo**](device-profiles.md) ([Portal clássico](/intune-classic/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies)). Estas políticas permitem-lhe configurar o modo de funcionamento das funcionalidades e capacidades dos dispositivos que gere. Por exemplo, pode exigir a utilização de uma palavra-passe em Windows Phones ou desativar a utilização da câmara em iPhones.
- [**Acesso a recursos da empresa**](device-profiles.md) ([Portal clássico](/intune-classic/deploy-use/enable-access-to-company-resources-with-microsoft-intune)). Permitir que os utilizadores acedam ao seu trabalho nos respetivos dispositivos pessoais pode apresentar desafios. Por exemplo, como é que garante que todos os dispositivos que precisam de aceder ao e-mail da empresa estão configurados corretamente? Como pode garantir que os utilizadores conseguem aceder à rede da empresa com uma ligação VPN sem terem de conhecer as definições necessárias tantas vezes complexas? O Intune pode ajudar a reduzir este fardo, configurando automaticamente os dispositivos que gere para aceder a recursos comuns da empresa.
- [**Políticas de gestão de PCs Windows (com o software de cliente Intune)**](/intune-classic/deploy-use/common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client). Embora a inscrição de PCs Windows no Intune lhe dê mais capacidades de gestão de dispositivos, o Intune continua a suportar a gestão de PCs Windows com o software de cliente Intune. Se precisar de informações sobre algumas das tarefas que pode realizar com PCs, comece por aqui.

## <a name="protect"></a>Proteger
No mundo de TI moderno, proteger os dispositivos contra acesso não autorizado é uma das tarefas mais importantes que tem de realizar. Para além dos itens no passo **Configurar** do ciclo de vida do dispositivo, o Intune fornece mais capacidades que ajudam a proteger os dispositivos que gere contra acesso não autorizado ou ataques maliciosos:
- [**Autenticação multifator**](/intune-classic/deploy-use/protect-your-devices-with-microsoft-intune). Adicionar mais uma camada de autenticação aos inícios de sessão do utilizador pode ajudar a tornar os dispositivos ainda mais seguros. Muitos dispositivos suportam a autenticação multifator que requer um segundo nível de autenticação, como uma chamada telefónica ou mensagem de texto, antes de os utilizadores poderem aceder aos mesmos.
- [**Definições do Windows Hello para Empresas**](windows-hello.md) ([Portal clássico](/intune-classic/deploy-use/control-microsoft-passport-settings-on-devices-with-microsoft-intune)). O Windows Hello para Empresas é um método de início de sessão alternativo que permite que os utilizadores utilizem um *gesto*, tal como uma identificação digital ou o Windows Hello para iniciar sessão, sem ser necessário uma palavra-passe.
- [**Políticas para proteger PCs Windows (com o software de cliente Intune)**](/intune-classic/deploy-use/policies-to-protect-windows-pcs-in-microsoft-intune). Quando gere PCs Windows com o software de cliente Intune, estão disponíveis políticas que lhe permitem controlar as definições de Endpoint Protection, atualizações de software e Firewall do Windows nos PCs que gere.

## <a name="retire"></a>Extinguir
Quando um dispositivo é perdido ou roubado, quando tem de ser substituído ou quando os utilizadores passam a ter outro cargo, geralmente está na altura de [extinguir ou limpar](device-management.md) ([Portal clássico](/intune-classic/deploy-use/use-remote-wipe-to-help-protect-data-using-microsoft-intune)) o dispositivo. Pode fazê-lo de várias formas, desde repor o dispositivo, removê-lo da gestão ou eliminar os dados empresariais contidos no mesmo.
