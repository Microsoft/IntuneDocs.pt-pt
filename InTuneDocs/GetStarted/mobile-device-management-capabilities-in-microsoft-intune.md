---
title: "Funcionalidades de gestão de dispositivos móveis | Microsoft Intune"
description: "Leia este tópico para saber como o Intune o pode ajudar a gerir os dispositivos móveis que inscrever no serviço."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 07/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f23b3ee7-78da-4e53-9fc2-78e58401bcf9
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 6716a3d1fb53dc3de0189f637d5664d0a2023d05
ms.openlocfilehash: 720112c7c20883200557510da2a42ee402eff50a


---
# Funcionalidades de gestão de dispositivos móveis do Microsoft Intune

O Microsoft Intune permite gerir uma vasta gama de dispositivos ao *inscrevê-los* no serviço. Os utilizadores podem utilizar um *portal da empresa* para efetuar várias operações, como inscrever os respetivos dispositivos, procurar e instalar aplicações, assegurar que o dispositivo está em conformidade com as políticas da empresa e contactar o respetivo suporte de TI.
Este tópico apresenta uma lista completa das funcionalidades que a inscrição de dispositivos fornece.

A gestão, o inventário, a implementação de aplicações, o aprovisionamento e a extinção são processados através da consola de administração do Intune. Os utilizadores obtêm acesso ao portal da empresa que lhes permite instalar aplicações, inscrever e remover dispositivos e obter ajuda para contactarem o respetivo departamento de TI ou suporte técnico.



## Configuração e segurança dos dispositivos

|Funcionalidade|Detalhes|Mais informações|
|--------------|-----------|--------------------|
|Políticas de configuração<br><br>Políticas personalizadas|As políticas de configuração de dispositivos móveis permitem-lhe gerir diversas definições e funcionalidades dos dispositivos móveis da sua organização. Por exemplo, pode exigir uma palavra-passe, limitar o número de tentativas falhadas, limitar os minutos antes do ecrã bloquear, definir o tempo de expiração da palavra-passe e impedir palavras-passe utilizadas anteriormente. Também pode controlar a utilização das funcionalidades de hardware e software, tais como a câmara do dispositivo ou o browser<br><br>Utilize políticas personalizadas quando as políticas de configuração não contêm a definição necessária. Para dispositivos iOS, pode importar definições que exportou da Ferramenta Apple Configurator. Para outros dispositivos, pode utilizar as definições OMA-URI para configurar definições e funcionalidades do dispositivo.|[Gerir definições e funcionalidades nos seus dispositivos com as políticas do Microsoft Intune](/intune/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies)<br />|
|Eliminação e Bloqueio Remotos e Reposição do Código de Acesso|Apague dados confidenciais quando um dispositivo é perdido ou roubado. Por exemplo, pode bloquear remotamente o dispositivo, restaurá-lo para as definições de fábrica ou apagar apenas dados empresariais.<br>Pode repor códigos de acesso se os utilizadores perderem acesso ao respetivo dispositivo, bloquear dispositivos perdidos ou roubados ou até mesmo apagar dados de dispositivos perdidos ou roubados.|[Ajudar a proteger os seus dispositivos através do bloqueio remoto e da reposição do código de acesso](/intune/deploy-use/use-remote-lock-and-passcode-reset-in-microsoft-intune) e [Extinguir dispositivos da gestão do Intune](/intune/deploy-use/retire-devices-from-microsoft-intune-management)|
|Modo de local público|Permite-lhe bloquear determinadas funcionalidades de dispositivos móveis, como a captura de ecrã e o botão ligar/desligar. Também permite restringir os dispositivos para que executem uma única aplicação especificada por si.|[Definições de política de configuração do iOS no Microsoft Intune](/intune/deploy-use/ios-policy-settings-in-microsoft-intune)|

## Gestão de aplicações

|Funcionalidade|Detalhes|Mais informações|
|--------------|-----------|--------------------|
|Implementação e gestão de aplicações|Fornece uma série de ferramentas para ajudá-lo a gerir aplicações móveis ao longo do respetivo ciclo de vida, incluindo a implementação de aplicações a partir de ficheiros de instalação e lojas de aplicações, monitorização detalhada do estado das aplicações e remoção de aplicações.|[Implementar aplicações no Microsoft Intune](/intune/deploy-use/deploy-apps)|
|Aplicações compatíveis e incompatíveis|Permite-lhe especificar listas de aplicações compatíveis (que os utilizadores podem instalar) e incompatíveis (que não podem ser instaladas pelos utilizadores).|[Definições de política do iOS no Microsoft Intune](/intune/deploy-use/ios-policy-settings-in-microsoft-intune)|
|Gestão de aplicações móveis|Configure restrições para aplicações utilizando a gestão de aplicações móveis para dispositivos que gere com o Intune, bem como para dispositivos que não são geridos pelo Intune. Isto ajuda a aumentar a segurança dos dados da sua empresa, restringindo operações como a ação copiar e colar, efetuar cópias de segurança externas de dados e a transferência de dados entre aplicações.|[Configure and deploy mobile application management policies in the Microsoft Intune console](/intune/deploy-use/configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console)<br><br>[Criar e implementar políticas de gestão de aplicações móveis com o Microsoft Intune](/intune/deploy-use/create-and-deploy-mobile-app-management-policies-with-microsoft-intune)<br /><br />[Preparar as aplicações iOS para a gestão de aplicações móveis com a Ferramenta de Encapsulamento de Aplicações do Microsoft Intune](/intune/deploy-use/prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool)<br /><br />[Preparar as aplicações Android para a gestão de aplicações móveis com a Ferramenta de Encapsulamento de Aplicações do Microsoft Intune](/intune/deploy-use/prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool)|
|Configuração de aplicação móvel iOS|Utilize políticas de configuração de aplicações móveis para fornecer definições para aplicações iOS que poderão ser necessárias quando o utilizador executar a aplicação. Por exemplo, uma aplicação pode requerer que o utilizador especifique um número de porta ou informações de início de sessão. Isto pode ajudar a simplificar a configuração de aplicações e reduzir o número de chamadas para o suporte técnico.|[Configurar aplicações iOS com políticas de configuração de aplicações móveis no Microsoft Intune](/intune/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune)|
|Perfis de aprovisionamento de aplicações móveis iOS|O Intune proporciona-lhe as ferramentas para implementar proativamente perfis nas aplicações iOS que estão prestes a expirar.|[Utilizar políticas de perfil de aprovisionamento móvel de iOS para impedir as aplicações de expirar](/intune/deploy-use/ios-mobile-app-provisioning-profiles)|
|Browser gerido|Após implementar o browser gerido para os utilizadores, pode configurar a política para browsers geridos para controlar os sites que esses utilizadores podem visitar. Para além disso, também pode aplicar políticas de gestão de aplicações móveis para o browser gerido.|[Gerir o acesso à Internet através de políticas de browser gerido com o Microsoft Intune](/intune/deploy-use/manage-internet-access-using-managed-browser-policies)|
|Microsoft Passport|O Intune permite efetuar a integração com o Microsoft Passport for Work, que é um método de início de sessão alternativo para Windows 10 que utiliza o Active Directory ou uma conta do Azure Active Directory para substituir uma palavra-passe, um smart card ou um smart card virtual.|[Controlar as definições do Microsoft Passport em dispositivos com o Microsoft Intune](/intune/deploy-use/control-microsoft-passport-settings-on-devices-with-microsoft-intune)|

## Acesso aos recursos da empresa

|Funcionalidade|Detalhes|Mais informações|
|--------------|-----------|--------------------|
|Perfis de certificados|Crie e implemente perfis de certificados fidedignos e certificados de protocolo SCEP (Simple Certificate Enrollment Protocol) que podem ser utilizados para ajudar a proteger e autenticar perfis de Wi-Fi, VPN e e-mail.|[Proteger o acesso a recursos com perfis de certificados no Microsoft Intune](/intune/deploy-use/secure-resource-access-with-certificate-profiles)|
|Perfis de Wi-Fi|Implemente definições de rede sem fios aos seus utilizadores. Ao implementar estas definições, estará a minimizar o esforço do utilizador final para se ligar à rede empresarial.|[Ligações Wi-Fi no Microsoft Intune](/intune/deploy-use/wi-fi-connections-in-microsoft-intune)|
|Perfis de e-mail|Crie e implemente definições de e-mail para dispositivos. Para permitir que os utilizadores acedam a e-mails da empresa nos seus dispositivos pessoais sem precisarem de efetuar qualquer configuração.|[Configurar o acesso a e-mail empresarial através de perfis de e-mail com o Microsoft Intune](/intune/deploy-use/configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune)|
|Perfis da VPN|Implemente definições da VPN para os utilizadores e dispositivos na sua organização. Ao implementar estas definições, estará a minimizar o esforço do utilizador final para se ligar aos recursos na rede da empresa.|[Ligações VPN no Microsoft Intune](/intune/deploy-use/vpn-connections-in-microsoft-intune)|
|Políticas de acesso condicional|Efetue a gestão do acesso ao e-mail do Microsoft Exchange e ao SharePoint Online a partir de dispositivos que não são geridos pelo Intune.|[Restringir o acesso ao e-mail e ao SharePoint com o Microsoft Intune](/intune/deploy-use/restrict-access-to-email-and-o365-services-with-microsoft-intune)|

## Inventário e criar relatórios

|Funcionalidade|Detalhes|Mais informações|
|--------------|-----------|--------------------|
|Inventário e criar relatórios|Encontre informações sobre os dispositivos que gere e o software que estão a utilizar.|[Compreender os seus dispositivos com o inventário no Microsoft Intune](/intune/deploy-use/understand-your-devices-with-inventory-in-microsoft-intune)|


### Consulte também
[Funções de gestão de computadores com Windows no Microsoft Intune](windows-pc-management-capabilities-in-microsoft-intune.md)



<!--HONumber=Jul16_HO4-->


