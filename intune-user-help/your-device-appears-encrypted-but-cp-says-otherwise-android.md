---
title: O dispositivo Android parece estar encriptado | Microsoft Docs
description: Resolver o status de criptografia no aplicativo Portal da Empresa e Microsoft Intune
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 08/14/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: ba593c08-1a78-4013-8525-b45a948772ec
searchScope:
- User help
ROBOTS: ''
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: af1c7d1f9d8236fd95413317acefbe8887d90f47
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72507677"
---
# <a name="device-encrypted-but-apps-say-otherwise"></a>Dispositivo criptografado, mas aplicativos dizem de outra forma

Se Portal da Empresa ou o aplicativo Microsoft Intune dizer que seu dispositivo não está criptografado, mas você tem certeza de que está, tente as etapas neste artigo.  

## <a name="add-a-startup-pin"></a>Adicionar um PIN de arranque

Determinados dispositivos Android exigem que crie um PIN de arranque para garantir que o dispositivo está seguro. O local dessa configuração estará no aplicativo de **configurações** do seu dispositivo. O nome e o local da configuração podem variar. Por exemplo, no Samsung Galaxy S7, a configuração é conhecida como **inicialização segura**. Para habilitá-lo e criar uma senha, vá para **configurações** > **tela de bloqueio e segurança** > **inicialização segura**.  

## <a name="encrypt-the-entire-device"></a>Encriptar todo o dispositivo

Esta seção se aplica somente ao aplicativo Portal da Empresa. Alguns dispositivos permitem-lhe optar por encriptar todo o dispositivo ou apenas o espaço utilizado do mesmo. Escolha a opção para criptografar o dispositivo inteiro. Se você tiver selecionado criptografar apenas o espaço usado:

1. [Remova este dispositivo da portal da empresa](unenroll-your-device-from-intune-android.md).
2. Descriptografar o espaço usado.  
3. Criptografar todo o dispositivo.  
4. Registre novamente o dispositivo.  

## <a name="downgrade-your-version-of-android"></a>Mudar a versão do Android para uma versão anterior

Esta seção se aplica somente ao aplicativo Portal da Empresa. Se o seu dispositivo oferecer a opção de fazer downgrade para o Android 6,0 e posterior, faça isso. Há um risco de perda de dados se você tentar fazer downgrade de seu dispositivo. Em alternativa, recomendamos que contacte o suporte da empresa para resolver este problema. Obtenha informações de contato para o suporte de sua empresa no [site Portal da empresa](https://go.microsoft.com/fwlink/?linkid=2010980).  

## <a name="specific-manufacturer-issues"></a>Problemas de um fabricante específico

Alguns dispositivos Android na versão 7,0 e posteriores criptografam dados de maneiras inconsistentes com determinados padrões da plataforma Android. Esses métodos de criptografia colocam as informações do dispositivo em risco. Como resultado, esses dispositivos não têm suporte.

Para obter uma lista não completa de dispositivos Android com suporte, consulte o artigo [sistemas operacionais e navegadores com suporte no Intune](https://docs.microsoft.com/intune/fundamentals/supported-devices-browsers#supported-samsung-knox-standard-devices). Se o dispositivo não estiver listado, consulte o fabricante do dispositivo ou contate a pessoa de suporte.

> [!Note]
> A Microsoft trabalha com os fabricantes para resolver quaisquer problemas que encontrarmos durante o teste ou que os usuários se reportam a nós. Atualizaremos este artigo sempre que estiverem disponíveis novas informações.

## <a name="update-devices"></a>Atualizar dispositivos

Se você não atualizou seu dispositivo para a versão mais recente do Android, vá para o aplicativo de **configurações** do dispositivo e selecione **Atualizar**.  

## <a name="next-steps"></a>Próximos passos

Ainda precisa de ajuda? Contacte o suporte da empresa (verifique as informações de contacto no [site do Portal da Empresa](https://go.microsoft.com/fwlink/?linkid=2010980)) ou escreva para a <a href="mailto:wintunedroidfbk@microsoft.com?subject=I'm having trouble with enrolling my Android device&body=Describe the issue you're experiencing here.">equipa Android da Microsoft</a>.  
