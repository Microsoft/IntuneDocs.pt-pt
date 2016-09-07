---
title: "Obtém erros quando tenta inscrever o dispositivo iOS no Intune | Microsoft Intune"
description: 
keywords: 
author: Staciebarker
manager: angrobe
ms.date: 08/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 92a8d06d-0ecb-4912-898b-993e8eaf4e58
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: esmich
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 38301b4e6964550008b08e99bf7016f1cc2561c3
ms.openlocfilehash: e2493f93c08aaf7c10c47a0835de498349799e28


---


# Obtém erros quando tenta inscrever o dispositivo iOS no Intune

A tabela seguinte indica os erros que poderá ver quando inscrever o seu dispositivo iOS no Intune. Partilhe esta ligação com o administrador de TI. Para encontrar as informações de contacto dele, verifique o [Web site do Portal da Empresa](http://portal.manage.microsoft.com).

|Mensagem de erro|Problema|O que dizer ao administrador de TI|
|-----------------|---------|----------------------------------------------------------------------------------------------------------------------------------------------------------------|
|NoEnrollmentPolicy|Nenhuma política de inscrição|Verifique se todos os pré-requisitos de inscrição foram configurados, como o certificado do APN, e se "iOS como plataforma" está ativado. Para obter instruções, veja [Configurar a gestão de dispositivos iOS e Mac](/intune/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune).|
|DeviceCapReached|Já tem demasiados dispositivos móveis inscritos.|O utilizador tem de remover um dos seus dispositivos móveis atualmente inscritos do Portal da Empresa antes de inscrever outro. Consulte as instruções para o tipo de dispositivo que está a utilizar: [Android](unenroll-your-device-from-intune-android.md), [iOS](unenroll-your-device-from-intune-ios.md), [Windows](unenroll-your-device-from-intune-windows.md).|
|APNSCertificateNotValid|Existe um problema com o certificado que permite que o seu dispositivo móvel comunique com a rede da sua empresa.<br /><br />Contacte os administradores de TI e informe-os de que recebeu a mensagem **APNSCertificateNotValid** enquanto tentava inscrever o seu dispositivo móvel e peça-lhes para verem a resolução nesta tabela.|O Serviço Apple Push Notification (APNS) disponibiliza um canal para entrar em contacto com os dispositivos iOS inscritos. Se os passos para obter um certificado do APNS não forem efetuados ou o certificado APNS tiver expirado, as tentativas de inscrição falharão e será apresentada esta mensagem.<br /><br />Reveja as informações sobre a configuração de utilizadores em [Sync Active Directory and add users to Intune (Sincronizar o Active Directory e adicionar utilizadores ao Intune)](/Intune/Get-Started/start-with-a-paid-subscription-to-microsoft-intune-step-3) e em [Organizar utilizadores e dispositivos](/Intune/Get-Started/start-with-a-paid-subscription-to-microsoft-intune-step-5).|
|AccountNotOnboarded|Existe um problema com o certificado que permite que o seu dispositivo móvel comunique com a rede da sua empresa.<br /><br />Contacte os administradores de TI e informe-os de que recebeu a mensagem **APNSNotOnboarded** enquanto tentava inscrever o seu dispositivo móvel e peça-lhes para verem a resolução nesta tabela.|O Serviço Apple Push Notification (APNS) disponibiliza um canal para entrar em contacto com os dispositivos iOS inscritos. Se os passos para obter um certificado do APNS não forem efetuados ou o certificado APNS tiver expirado, as tentativas de inscrição falharão e será apresentada esta mensagem.<br /><br />Para obter mais informações, reveja [Configurar a gestão de iOS e Mac com o Microsoft Intune](/Intune/Deploy-use/set-up-ios-and-mac-management-with-microsoft-intune).|
|DeviceTypeNotSupported|Poderá ter tentado inscrever através de um dispositivo não iOS. O tipo de dispositivo móvel que está a tentar inscrever não é suportado.<br /><br />Certifique-se de que o dispositivo está a executar a versão 7.1 do iOS ou posterior.<br /><br />Contacte os administradores de TI e informe-os de que recebeu a mensagem **DeviceTypeNotSupported** enquanto tentava inscrever o seu dispositivo móvel e peça-lhes para verem a resolução nesta tabela.|Certifique-se de que o dispositivo do utilizador está a executar a versão 7.1 do iOS ou posterior.|
|UserLicenseTypeInvalid|Não pode inscrever o seu dispositivo móvel porque a sua conta de utilizador ainda não é um membro de um grupo de utilizadores necessário.<br /><br />Contacte os administradores de TI e informe-os de que recebeu a mensagem **UserLicenseTypeInvalid** enquanto tentava inscrever o seu dispositivo móvel e peça-lhes para verem a resolução nesta tabela.|Antes de os utilizadores poderem inscrever os respetivos dispositivos, têm de ser membros do grupo de utilizadores correto. Esta mensagem indica que têm o tipo de licença errado para a autoridade de gestão de dispositivos móveis designada. Por exemplo, se o Intune foi designado como autoridade de gestão de dispositivos móveis e estiverem a utilizar uma licença do System Center 2012 R2 Configuration Manager, será obtido este erro.<br /><br />Reveja o seguinte para mais informações:<br /><br />Reveja [Set up iOS and Mac management with Microsoft Intune (Configurar a gestão de iOS e Mac com o Microsoft Intune)](/Intune/Deploy-use/set-up-ios-and-mac-management-with-microsoft-intune) e as informações sobre como configurar utilizadores em [Sync Active Directory and add users to Intune (Sincronizar o Active Directory e adicionar utilizadores ao Intune)] (/Intune/Get-Started/start-with-a-paid-subscription-to-microsoft-intune-step-3 e em [Organizar utilizadores e dispositivos](/Intune/Get-Started/start-with-a-paid-subscription-to-microsoft-intune-step-5).|
|MdmAuthorityNotDefined|O seu administrador de TI precisa de configurar a forma como os dispositivos móveis existentes na sua empresa são geridos.<br /><br />Contacte os administradores de TI e informe-os de que recebeu a mensagem **MdmAuthorityNotDefined** enquanto tentava inscrever o seu dispositivo móvel e peça-lhes para verem a resolução nesta tabela.|A autoridade de gestão de dispositivos móveis não foi designada no Intune.<br /><br />Reveja o primeiro item na secção "Step 6: Enroll mobile devices and install an app (Passo 6: inscrever dispositivos móveis e instalar aplicações"), em [Get started with a 30-day trial of Microsoft Intune (Começar com uma versão de avaliação de 30 dias do Microsoft Intune)](/Intune/Understand-explore/get-started-with-a-30-day-trial-of-microsoft-intune).|





<!--HONumber=Aug16_HO5-->


