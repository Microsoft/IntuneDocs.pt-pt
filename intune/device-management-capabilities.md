---
title: Funcionalidades de gestão de dispositivos no Microsoft Intune
description: Leia este tópico para saber como o Intune o pode ajudar a gerir os dispositivos que inscrever.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/16/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 293fa40b59d0005f60aad45a3fc42d3dd790857d
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "61510151"
---
# <a name="enrolled-device-management-capabilities-of-microsoft-intune"></a>Funcionalidades de gestão de dispositivos inscritos do Microsoft Intune

O Microsoft Intune permite gerir uma vasta gama de dispositivos ao *inscrevê-los* no serviço. Pode inscrever você mesmo alguns tipos de dispositivo ou podem fazê-lo os utilizadores através da aplicação *portal da empresa*. A inscrição permite que eles procurar e instalar aplicações, certifique-se de que os dispositivos estão em conformidade com as políticas da empresa e contacte o suporte de TI.

Este artigo apresenta uma lista completa das funcionalidades após a inscrição dos dispositivos.

Gestão, o inventário, implementação de aplicações, aprovisionamento e a extinção são processados através do Intune no portal do Azure.

Os utilizadores obtêm acesso ao portal da empresa que lhes permite instalar aplicações, inscrever e remover dispositivos e contactar o respetivo departamento de TI ou suporte técnico.



## <a name="device-security-and-configuration"></a>Configuração e segurança dos dispositivos

|Funcionalidade|Detalhes|Mais informações|
|--------------|-----------|--------------------|
|Políticas de configuração<br><br>Políticas personalizadas| Permite gerir diversas definições e funcionalidades nos dispositivos móveis na sua organização. Por exemplo, pode exigir uma palavra-passe, limitar o número de tentativas falhadas, limitar a quantidade de tempo antes do ecrã bloquear, definir o tempo de expiração da palavra-passe e impedir palavras-passe utilizadas anteriormente. Também pode controlar a utilização das funcionalidades de hardware e software, tais como a câmara do dispositivo ou o browser.<br><br>Utilize políticas personalizadas quando as políticas de configuração não contêm as definições que necessita. Para dispositivos iOS, pode importar definições que exportou da ferramenta Apple Configurator. Para outros dispositivos, pode utilizar as definições Open Mobile Alliance Uniform Resource Identifier (OMA-URI) para configurar definições e funcionalidades do dispositivo.|[Gerir definições e funcionalidades nos seus dispositivos com as políticas do Microsoft Intune](device-compliance-get-started.md)|
|Eliminação e Bloqueio Remotos e Reposição do Código de Acesso|Apaga dados confidenciais quando um dispositivo é perdido ou roubado. Por exemplo, pode bloquear remotamente o dispositivo, restaurá-lo para as definições de fábrica ou apagar apenas dados empresariais.<br><br>Pode repor códigos de acesso se os utilizadores perderem acesso ao respetivo dispositivo, bloquear dispositivos perdidos ou roubados ou até mesmo apagar dados de dispositivos perdidos ou roubados.|Ajudar a proteger os seus dispositivos com o [bloqueio remoto](device-remote-lock.md) e [repor código de acesso](device-passcode-reset.md)|
|Modo de local público|Permite-lhe bloquear determinadas funcionalidades de dispositivos móveis, como a captura de ecrã e o botão ligar/desligar. Também permite restringir os dispositivos para que executem uma única aplicação especificada por si. |[Definições de política de configuração do iOS no Microsoft Intune](device-restrictions-ios.md)|

## <a name="app-management"></a>Gestão de aplicações

|Funcionalidade|Detalhes|Mais informações|
|--------------|-----------|--------------------|
|Implementação e gestão de aplicações|Fornece uma série de ferramentas para ajudá-lo a gerir aplicações móveis ao longo do respetivo ciclo de vida, incluindo a implementação de aplicações a partir de ficheiros de instalação e lojas de aplicações, monitorização detalhada do estado das aplicações e remoção de aplicações.|[Implementar aplicações no Microsoft Intune](apps-deploy.md)|
|Aplicações compatíveis e incompatíveis|Permite-lhe especificar listas de aplicações em conformidade (que os utilizadores têm permissão para instalar) e não conformes (que os utilizadores não têm permissão para instalar).|[Definições de política do iOS no Microsoft Intune](device-restrictions-ios.md)|
|Gestão de aplicações móveis|Configure restrições para aplicações utilizando a gestão de aplicações móveis para todos os dispositivos geridos e não geridos com o Intune. Pode aumentar a segurança dos dados da empresa, restringindo operações como copiar e colar, cópia de segurança externa de dados e a transferência de dados entre aplicações.|[Configurar e implementar as políticas de gestão de aplicações móveis na consola do Microsoft Intune](app-wrapper-prepare-android.md)|
|Configuração de aplicação móvel iOS|Utiliza políticas de configuração de aplicações móveis para fornecer definições para aplicações iOS que poderão ser necessárias quando o utilizador executar a aplicação. Por exemplo, uma aplicação pode requerer que o utilizador especifique um número de porta ou informações de início de sessão. Pode simplificar a configuração de aplicação e reduzir o número de chamadas de suporte.|[Configurar aplicações iOS com políticas de configuração de aplicações móveis no Microsoft Intune](app-configuration-policies-use-ios.md)|
|Perfis de aprovisionamento de aplicações móveis iOS|Ajuda a implementar perfis de aprovisionamento nas aplicações iOS que estão prestes a expirar. |[Utilizar políticas de perfil de aprovisionamento móvel de iOS para impedir as aplicações de expirar](app-provisioning-profile-ios.md)|
|Browser gerido|Configura as políticas de browser gerido para controlar os sites que os utilizadores do dispositivo podem visitar. Para além disso, também pode aplicar políticas de gestão de aplicações móveis para o browser gerido.|[Gerir o acesso à Internet através de políticas de browser gerido com o Microsoft Intune](app-configuration-managed-browser.md)|
|Windows Hello para Empresas|Permite efetuar a integração com o Windows Hello para Empresas, que é um método de início de sessão alternativo para o Windows 10 que utiliza o Active Directory ou o Azure Active Directory para substituir palavras-passe, smart cards ou smart cards virtuais.|[Controlar as definições do Windows Hello para Empresas em dispositivos com o Microsoft Intune](windows-hello.md)|
|Aplicações adquiridas em grandes volumes|Ajuda-o a gerir aplicações compradas através de um programa de compra em grandes volumes, ao importar as informações da licença a partir da loja de aplicações, ao controlar a quantidade de licenças que utilizou e ao impedir que instale mais cópias da sua aplicação do que as que tem.|[Gerir aplicações compradas em grandes volumes com o Microsoft Intune](vpp-apps.md)|

## <a name="company-resource-access"></a>Acesso aos recursos da empresa

|Funcionalidade|Detalhes|Mais informações|
|--------------|-----------|--------------------|
|Perfis de certificados|Cria e implementa perfis de certificados fidedignos e certificados de protocolo SCEP (Simple Certificate Enrollment Protocol) que podem ser utilizados para proteger e autenticar perfis de Wi-Fi, VPN e e-mail.|[Proteger o acesso a recursos com perfis de certificados no Microsoft Intune](certificates-configure.md)|
|Perfis de Wi-Fi|Implementa definições de rede sem fios aos seus utilizadores. Ao implementar estas definições, estará a minimizar o esforço do utilizador para se ligar à rede da empresa.|[Ligações Wi-Fi no Microsoft Intune](wi-fi-settings-configure.md)|
|Perfis de e-mail|Cria e implementa definições de e-mail nos dispositivos, para que os utilizadores podem aceder a e-mail empresarial nos respetivos dispositivos pessoais sem qualquer configuração necessária por parte dos mesmos.|[Configurar o acesso a e-mail empresarial através de perfis de e-mail com o Microsoft Intune](email-settings-configure.md)|
|Perfis da VPN|Implementa definições da VPN nos utilizadores e dispositivos na sua organização. Ao implementar estas definições, estará a minimizar o esforço do utilizador para se ligar aos recursos na rede da empresa.|[Ligações VPN no Microsoft Intune](device-profiles.md#vpn)|
|Políticas de acesso condicional|Gere o acesso ao e-mail do Microsoft Exchange e ao SharePoint Online a partir de dispositivos que não são geridos pelo Intune.|[Restringir o acesso ao e-mail e ao SharePoint com o Microsoft Intune](app-based-conditional-access-intune.md)|

## <a name="next-steps"></a>Passos Seguintes

[Ver uma lista de dispositivos que pode gerir](device-management.md).
