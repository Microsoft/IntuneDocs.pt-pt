---
title: Inscrições de dispositivos Windows no Portal da Empresa Intune Microsoft Docs
description: Começar a inscrever um dispositivo Windows no Portal da Empresa
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 05/24/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: 36250832-c6fd-4e8d-b681-de735023ebc3
searchScope:
- User help
ROBOTS: ''
ms.reviewer: jieyang
ms.suite: ems
ms.custom: intune-enduser
ms.collection: ''
ms.openlocfilehash: 86c158f73d820fa2e719fe92b884c77f315fcb94
ms.sourcegitcommit: 25e4847ead0f56c269cfefe1e01c1b9106a28cf1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/05/2020
ms.locfileid: "78369076"
---
# <a name="windows-device-enrollment-in-intune-company-portal"></a>Inscrição de dispositivos Windows no Portal da Empresa Intune  

Inscreva o seu dispositivo Windows na aplicação Intune Company Portal para obter acesso seguro a aplicações, e-mails e ficheiros escolares. Se a sua organização necessitar ou recomendar determinadas aplicações, como o Office ou o OneDrive, receberá-as durante a inscrição, ou estará disponível no Portal da Empresa após a inscrição.  

Pode inscrever dispositivos Windows 10 através do site *ou* app do Portal da Empresa. Se estiver a inscrever um dispositivo com uma versão anterior do Windows, tem de inscrever o dispositivo através do site do Portal da Empresa.  

## <a name="install-company-portal-app"></a>Instalar app Portal da Empresa  
Pode já ter a aplicação Portal da Empresa instalada no seu dispositivo. Consulte a aplicação na sua lista __de aplicações All.__  Se não vir o Portal da Empresa na sua lista de aplicações, siga estes passos para instalá-lo.  

1. Abra a **Microsoft Store** no seu dispositivo.

2. No campo **de Pesquisa,** digite **portal da empresa.**

3. Na lista de resultados, selecione **Portal da Empresa** > **Instalar**.

4. Selecione **Instalar** ou **Gratuito**. Não há diferença entre estas duas opções; as palavras aparecem com base na forma como a sua organização criou a aplicação.  

## <a name="find-windows-10-version-number"></a>Encontre o número da versão do Windows 10  
Os passos de inscrição diferem para diferentes versões dos dispositivos Windows 10. Os seguintes passos descrevem como encontrar o número da versão no ambiente de trabalho e dispositivos móveis do Windows 10. Depois de conhecer a sua versão, continue com os passos de inscrição recomendados.  

### <a name="windows-10-desktop-devices"></a>Dispositivos com o Windows 10 Desktop  

1. Aceda a **Iniciar**.

2. Na barra de pesquisa, escreva a frase "sobre o seu PC". Selecione __Sobre o seu PC__ a partir dos resultados.  


   ![definições de pesquisa para Sobre o seu PC](media/searching_for_about_your_pc.png)  

3. Desloque-se para **as especificações do Windows** para encontrar a **versão** do Windows 10 que está instalada no seu PC.  


   ![Sobre o Seu PC com o Windows 10](media/settings_about_pc.png)  

4. Se a sua versão é  

    * __1607 ou mais tarde:__ Inscreva o seu dispositivo através das [ **Definições** > **Conta** > **Trabalho** ](enroll-windows-10-device.md#enroll-windows-10-version-1607-and-later-device)de acesso ou rota escolar .   
    * __1511 ou mais cedo:__ Inscreva o seu dispositivo através da [ **Definição** > **Conta** > a sua rota **das suas contas** ](enroll-windows-10-device.md#enroll-windows-10-version-1511-and-earlier-device).  

### <a name="windows-10-mobile-devices"></a>Dispositivos com o Windows 10 Mobile

1. Vá a __Todas as aplicações__ e selecione a aplicação __Definições.__
2. Selecione __Sistema__ > __Acerca de__.
3. Em __informações do Dispositivo,__ encontre a __versão__.  
4. Se a sua versão é  

    * __1607 ou mais tarde:__ Inscreva o seu dispositivo utilizando as [ **Definições** > **Trabalho** ](enroll-windows-10-device.md#enroll-windows-10-version-1607-and-later-device)de Acesso ou rota escolar .   
    * __1511 ou mais cedo:__ Inscreva o seu dispositivo utilizando a rota [ **Definições** > **Contas** ](enroll-windows-10-device.md#enroll-windows-10-version-1511-and-earlier-device).  

## <a name="enroll-non-windows-10-devices"></a>Inscreva dispositivos não Windows 10  
Utilize os seguintes artigos para inscrever outros dispositivos Windows suportados através do site do Portal da Empresa:   
* [Janela 8.1. ou dispositivo Windows RT 8.1](enroll-your-W81-or-rt81-windows.md)  
* [Dispositivo Windows Phone 8.1](enroll-your-wp81-windows.md)    

## <a name="it-administrator-support"></a>Suporte do administrador de TI  
Se for um administrador de TI e tiver problemas durante a inscrição de dispositivos, consulte problemas de [inscrição de dispositivos do Windows em Microsoft Intune](https://support.microsoft.com/help/4469913). Este artigo enumera erros comuns, as suas causas e passos para os resolver.  

## <a name="next-steps"></a>Próximos passos  
Agora que conhece os dispositivos suportados e o número da versão do Windows 10, proceda ao artigo de inscrição recomendado.  
 
Para obter mais informações sobre a gestão de dispositivos, portal da empresa, e como ambos são utilizados nas escolas e no trabalho, consulte os seguintes artigos:  
* [Utilize dispositivos geridos para aceder ao trabalho ou ao recurso escolar](use-managed-devices-to-get-work-done.md)  
* [O que acontece quando se matricula o seu dispositivo em Intune](what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-windows.md)  
* [Que informação pode a minha organização ver quando matriculo o meu dispositivo?](what-info-can-your-company-see-when-you-enroll-your-device-in-intune.md)  

Precisa de ajuda? Contacte o suporte da empresa. [Vá ao site do Portal da Empresa](https://go.microsoft.com/fwlink/?linkid=2010980) para encontrar as informações de contacto de TI da sua organização.  
