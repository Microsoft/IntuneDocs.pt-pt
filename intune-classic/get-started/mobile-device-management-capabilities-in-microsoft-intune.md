---
title: "Funcionalidades de gestão de dispositivos inscritos"
description: "Leia este tópico para saber como o Intune o pode ajudar a gerir os dispositivos que inscrever."
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 12/12/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f23b3ee7-78da-4e53-9fc2-78e58401bcf9
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: angrobe
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 59bbc6d9a4170b504e3a5bb3dfe688332a0063f2
ms.sourcegitcommit: 22ab1c6a6bfeb4fef9850d12b29829c3fecbbeed
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/12/2018
---
# <a name="enrolled-device-management-capabilities-of-microsoft-intune"></a>Funcionalidades de gestão de dispositivos inscritos do Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

O Microsoft Intune permite gerir uma vasta gama de dispositivos ao *inscrevê-los* no serviço. Pode inscrever você mesmo alguns tipos de dispositivo ou podem fazê-lo os utilizadores através da aplicação *portal da empresa*. Isto também permite efetuar operações como procurar e instalar aplicações, garantindo que os dispositivos estão em conformidade com as políticas da empresa, bem como contactar o suporte de TI.

Este tópico apresenta uma lista completa das funcionalidades após a inscrição do seu dispositivo.

A gestão, o inventário, a implementação de aplicações, o aprovisionamento e a extinção são processados através da consola de administração do Intune. Os utilizadores obtêm acesso ao portal da empresa que lhes permite instalar aplicações, inscrever e remover dispositivos e contactar o respetivo departamento de TI ou suporte técnico.



## <a name="device-security-and-configuration"></a>Configuração e segurança dos dispositivos

|Funcionalidade|Detalhes|Mais informações|
|--------------|-----------|--------------------|
|Políticas de configuração<br><br>Políticas personalizadas| Permite gerir diversas definições e funcionalidades nos dispositivos móveis na sua organização. Por exemplo, pode exigir uma palavra-passe, limitar o número de tentativas falhadas, limitar a quantidade de tempo antes do ecrã bloquear, definir o tempo de expiração da palavra-passe e impedir palavras-passe utilizadas anteriormente. Também pode controlar a utilização das funcionalidades de hardware e software, tais como a câmara do dispositivo ou o browser.<br><br>Utilize políticas personalizadas quando as políticas de configuração não contêm as definições necessárias. Para dispositivos iOS, pode importar definições que exportou da ferramenta Apple Configurator. Para outros dispositivos, pode utilizar as definições Open Mobile Alliance Uniform Resource Identifier (OMA-URI) para configurar definições e funcionalidades do dispositivo.|[Gerir definições e funcionalidades nos seus dispositivos com as políticas do Microsoft Intune](/intune-classic/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies)|
|Eliminação e Bloqueio Remotos e Reposição do Código de Acesso|Apaga dados confidenciais quando um dispositivo é perdido ou roubado. Por exemplo, pode bloquear remotamente o dispositivo, restaurá-lo para as definições de fábrica ou apagar apenas dados empresariais.<br><br>Pode repor códigos de acesso se os utilizadores perderem acesso ao respetivo dispositivo, bloquear dispositivos perdidos ou roubados ou até mesmo apagar dados de dispositivos perdidos ou roubados.|[Ajudar a proteger os seus dispositivos através do bloqueio remoto e da reposição do código de acesso](/intune-classic/deploy-use/retire-devices-from-microsoft-intune-management)|
|Modo de local público|Permite-lhe bloquear determinadas funcionalidades de dispositivos móveis, como a captura de ecrã e o botão ligar/desligar. Também permite restringir os dispositivos para que executem uma única aplicação especificada por si.|[Definições de política de configuração do iOS no Microsoft Intune](/intune-classic/deploy-use/ios-policy-settings-in-microsoft-intune)|

## <a name="app-management"></a>Gestão de aplicações

|Funcionalidade|Detalhes|Mais informações|
|--------------|-----------|--------------------|
|Implementação e gestão de aplicações|Fornece uma série de ferramentas para ajudá-lo a gerir aplicações móveis ao longo do respetivo ciclo de vida, incluindo a implementação de aplicações a partir de ficheiros de instalação e lojas de aplicações, monitorização detalhada do estado das aplicações e remoção de aplicações.|[Implementar aplicações no Microsoft Intune](/intune-classic/deploy-use/deploy-apps)|
|Aplicações compatíveis e incompatíveis|Permite-lhe especificar listas de aplicações em conformidade (que os utilizadores têm permissão para instalar) e não conformes (que os utilizadores não têm permissão para instalar).|[Definições de política do iOS no Microsoft Intune](/intune-classic/deploy-use/ios-policy-settings-in-microsoft-intune)|
|Gestão de aplicações móveis|Configure restrições para aplicações utilizando a gestão de aplicações móveis para todos os dispositivos geridos e não geridos com o Intune. Isto ajuda a aumentar a segurança dos dados da sua empresa, restringindo operações como a ação copiar e colar, efetuar cópias de segurança externas de dados e a transferência de dados entre aplicações.|[Configurar e implementar as políticas de gestão de aplicações móveis na consola do Microsoft Intune](/intune/app-wrapper-prepare-android)|
|Configuração de aplicação móvel iOS|Utiliza políticas de configuração de aplicações móveis para fornecer definições para aplicações iOS que poderão ser necessárias quando o utilizador executar a aplicação. Por exemplo, uma aplicação pode requerer que o utilizador especifique um número de porta ou informações de início de sessão. Isto pode ajudar a simplificar a configuração de aplicações e reduzir o número de chamadas para o suporte técnico.|[Configurar aplicações iOS com políticas de configuração de aplicações móveis no Microsoft Intune](/intune-classic/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune)|
|Perfis de aprovisionamento de aplicações móveis iOS|Ajuda a implementar perfis de aprovisionamento nas aplicações iOS que estão prestes a expirar. |[Utilizar políticas de perfil de aprovisionamento móvel de iOS para impedir as aplicações de expirar](/intune-classic/deploy-use/ios-mobile-app-provisioning-profiles)|
|Browser gerido|Configura as políticas de browser gerido para controlar os sites que os utilizadores do dispositivo podem visitar. Para além disso, também pode aplicar políticas de gestão de aplicações móveis para o browser gerido.|[Gerir o acesso à Internet através de políticas de browser gerido com o Microsoft Intune](/intune-classic/deploy-use/manage-internet-access-using-managed-browser-policies)|
|Windows Hello para Empresas|Permite efetuar a integração com o Windows Hello para Empresas, que é um método de início de sessão alternativo para o Windows 10 que utiliza o Active Directory ou o Azure Active Directory para substituir palavras-passe, smart cards ou smart cards virtuais.|[Controlar as definições do Windows Hello para Empresas em dispositivos com o Microsoft Intune](/intune-classic/deploy-use/control-microsoft-passport-settings-on-devices-with-microsoft-intune)|
|Aplicações adquiridas em grandes volumes|Ajuda-o a gerir aplicações compradas através de um programa de compra em grandes volumes, ao importar as informações da licença a partir da loja de aplicações, ao controlar a quantidade de licenças que utilizou e ao impedir que instale mais cópias da sua aplicação do que as que tem.|[Gerir aplicações compradas em grandes volumes com o Microsoft Intune](/intune-classic/deploy-use/manage-volume-purchased-apps-in-microsoft-intune)|

## <a name="company-resource-access"></a>Acesso aos recursos da empresa

|Funcionalidade|Detalhes|Mais informações|
|--------------|-----------|--------------------|
|Perfis de certificados|Cria e implementa perfis de certificados fidedignos e certificados de protocolo SCEP (Simple Certificate Enrollment Protocol) que podem ser utilizados para proteger e autenticar perfis de Wi-Fi, VPN e e-mail.|[Proteger o acesso a recursos com perfis de certificados no Microsoft Intune](/intune-classic/deploy-use/secure-resource-access-with-certificate-profiles)|
|Perfis de Wi-Fi|Implementa definições de rede sem fios aos seus utilizadores. Ao implementar estas definições, estará a minimizar o esforço do utilizador para se ligar à rede da empresa.|[Ligações Wi-Fi no Microsoft Intune](/intune-classic/deploy-use/wi-fi-connections-in-microsoft-intune)|
|Perfis de e-mail|Cria e implementa definições de e-mail nos dispositivos. Isto significa que os utilizadores podem aceder ao e-mail da empresa nos seus dispositivos pessoais sem terem de efetuar qualquer configuração.|[Configurar o acesso a e-mail empresarial através de perfis de e-mail com o Microsoft Intune](/intune-classic/deploy-use/configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune)|
|Perfis da VPN|Implementa definições da VPN nos utilizadores e dispositivos na sua organização. Ao implementar estas definições, estará a minimizar o esforço do utilizador para se ligar aos recursos na rede da empresa.|[Ligações VPN no Microsoft Intune](/intune-classic/deploy-use/vpn-connections-in-microsoft-intune)|
|Políticas de acesso condicional|Gere o acesso ao e-mail do Microsoft Exchange e ao SharePoint Online a partir de dispositivos que não são geridos pelo Intune.|[Restringir o acesso ao e-mail e ao SharePoint com o Microsoft Intune](/intune-classic/deploy-use/restrict-access-to-email-and-o365-services-with-microsoft-intune)|

## <a name="inventory-and-reporting"></a>Inventário e criar relatórios

|Funcionalidade|Detalhes|Mais informações|
|--------------|-----------|--------------------|
|Inventário e criar relatórios|Encontra informações sobre os dispositivos que gere e o software que os dispositivos estão a utilizar.|[Compreender os seus dispositivos com o inventário no Microsoft Intune](/intune-classic/deploy-use/understand-your-devices-with-inventory-in-microsoft-intune)|
