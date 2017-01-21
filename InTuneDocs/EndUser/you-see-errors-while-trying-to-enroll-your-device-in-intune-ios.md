---
title: "Obtém erros quando tenta inscrever o dispositivo iOS no Intune | Documentos da Microsoft"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 12/02/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 92a8d06d-0ecb-4912-898b-993e8eaf4e58
searchScope:
- Company Portal
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: esmich
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b6d5ea579b675d85d4404f289db83055642ffddd
ms.openlocfilehash: 9da632e906a1486ac705a0af99179ce9669c8a24


---

# <a name="you-see-errors-while-trying-to-enroll-your-ios-device-in-intune"></a>Obtém erros quando tenta inscrever o dispositivo iOS no Intune

A tabela seguinte indica os erros que poderá ver quando inscrever o seu dispositivo iOS no Intune. Partilhe esta ligação com o administrador de TI. Para encontrar as informações de contacto dele, verifique o [site do Portal da Empresa](http://portal.manage.microsoft.com).

|Mensagem de erro|Problema|O que dizer ao administrador de TI|
|-----------------|---------|----------------------------------------------------------------------------------------------------------------------------------------------------------------|
|NoEnrollmentPolicy|Nenhuma política de inscrição|Verifique se todos os pré-requisitos de inscrição, como o certificado do Serviço Apple Push Notification (APNs), foram configurados e se a opção "iOS como plataforma" está ativada. Para obter instruções, veja [Configurar a gestão de dispositivos iOS e Mac](/intune/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune).|
|DeviceCapReached|Já tem demasiados dispositivos móveis inscritos.|O utilizador tem de remover um dos seus dispositivos móveis atualmente inscritos do Portal da Empresa antes de inscrever outro. Consulte as instruções para o tipo de dispositivo que está a utilizar: [Android](unenroll-your-device-from-intune-android.md), [iOS](unenroll-your-device-from-intune-ios.md), [Windows](unenroll-your-device-from-intune-windows.md).|
|APNSCertificateNotValid|Existe um problema com o certificado que permite que o seu dispositivo móvel comunique com a rede da sua empresa.<br /><br />Contacte os administradores de TI, informe-os de que recebeu a mensagem **APNSCertificateNotValid** quando tentou inscrever o seu dispositivo móvel e peça-lhes para verem a resolução nesta tabela.|O Serviço Apple Push Notification (APNs) disponibiliza um canal para entrar em contacto com os dispositivos iOS inscritos. Se os passos para obter um certificado APNs não forem efetuados ou o certificado APNs tiver expirado, as tentativas de inscrição falharão e será apresentada esta mensagem.<br /><br />Reveja as informações sobre como configurar utilizadores em [Sincronizar o Active Directory e adicionar utilizadores ao Intune](/Intune/Get-Started/start-with-a-paid-subscription-to-microsoft-intune-step-3) e em [Organizar utilizadores e dispositivos](/Intune/Get-Started/start-with-a-paid-subscription-to-microsoft-intune-step-5).|
|AccountNotOnboarded|Existe um problema com o certificado que permite que o seu dispositivo móvel comunique com a rede da sua empresa.<br /><br />Contacte os administradores de TI, informe-os de que recebeu a mensagem **APNSNotOnboarded** quando tentou inscrever o seu dispositivo móvel e peça-lhes para verem a resolução nesta tabela.|O Serviço Apple Push Notification (APNs) disponibiliza um canal para entrar em contacto com os dispositivos iOS inscritos. Se os passos para obter um certificado APNs não forem efetuados ou o certificado APNs tiver expirado, as tentativas de inscrição falharão e será apresentada esta mensagem.<br /><br />Para obter mais informações, reveja [Configurar a gestão de iOS e Mac com o Microsoft Intune](/Intune/Deploy-use/set-up-ios-and-mac-management-with-microsoft-intune).|
|DeviceTypeNotSupported|Poderá ter tentado inscrever através de um dispositivo não iOS. O tipo de dispositivo móvel que está a tentar inscrever não é suportado.<br /><br />Certifique-se de que o dispositivo está a executar a versão 8.0 do iOS ou posterior.<br /><br />Contacte os administradores de TI, informe-os de que recebeu a mensagem **DeviceTypeNotSupported** quando tentou inscrever o seu dispositivo móvel e peça-lhes para verem a resolução nesta tabela.|Certifique-se de que o dispositivo do utilizador está a executar a versão 8.0 do iOS ou posterior.|
|UserLicenseTypeInvalid|Não pode inscrever o seu dispositivo móvel porque a sua conta de utilizador ainda não é um membro de um grupo de utilizadores necessário.<br /><br />Contacte os administradores de TI, informe-os de que recebeu a mensagem **UserLicenseTypeInvalid** quando tentou inscrever o seu dispositivo móvel e peça-lhes para verem a resolução nesta tabela.|Para poderem inscrever os respetivos dispositivos, os utilizadores têm de ser membros do grupo de utilizadores correto. Esta mensagem indica que têm o tipo de licença errado para a autoridade de gestão de dispositivos móveis designada. Por exemplo, se o Intune foi designado como autoridade de gestão de dispositivos móveis e estiverem a utilizar uma licença do System Center 2012 R2 Configuration Manager, será obtido este erro.<br /><br />Reveja o seguinte para mais informações:<br /><br />Veja [Configurar a gestão de iOS e Mac com o Microsoft Intune](/Intune/Deploy-use/set-up-ios-and-mac-management-with-microsoft-intune) e as informações sobre como configurar utilizadores em [Sincronizar o Active Directory e adicionar utilizadores ao Intune](/Intune/Get-Started/start-with-a-paid-subscription-to-microsoft-intune-step-3) e [Organizar utilizadores e dispositivos](/Intune/Get-Started/start-with-a-paid-subscription-to-microsoft-intune-step-5).|
|MdmAuthorityNotDefined|O administrador de TI precisa de configurar a forma como os dispositivos móveis existentes na sua empresa são geridos.<br /><br />Contacte os administradores de TI, informe-os de que recebeu a mensagem **MdmAuthorityNotDefined** quando tentou inscrever o seu dispositivo móvel e peça-lhes para verem a resolução nesta tabela.|A autoridade de gestão de dispositivos móveis não foi designada no Intune.<br /><br />Reveja o primeiro item na secção "Passo 6: inscrever dispositivos móveis e instalar uma aplicação", em [Começar com uma versão de avaliação de 30 dias do Microsoft Intune](/Intune/Understand-explore/get-started-with-a-30-day-trial-of-microsoft-intune).|



<!--HONumber=Dec16_HO2-->


