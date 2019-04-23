---
title: O dispositivo Android parece estar encriptado | Microsoft Docs
description: Resolver o estado de encriptação na aplicação Portal da empresa e o Microsoft Intune
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/19/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ba593c08-1a78-4013-8525-b45a948772ec
searchScope:
- User help
ROBOTS: ''
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: f8c35400f37ab4ddee275cf23f7a50f280322e3b
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "61501583"
---
# <a name="device-encrypted-but-apps-say-otherwise"></a>Dispositivo encriptados mas aplicações dizer que caso contrário

Se o Portal da empresa ou a aplicação Microsoft Intune dizer que o dispositivo não está encriptado, mas tem a certeza de que é, tente os passos neste artigo.  

## <a name="add-a-startup-pin"></a>Adicionar um PIN de arranque

Determinados dispositivos Android exigem que crie um PIN de arranque para garantir que o dispositivo está seguro. A localização desta definição será-se no seu dispositivo **definições** aplicação. O nome e a localização da definição de podem variar. Por exemplo, no Galaxy S7 da Samsung, a definição é referida como **arranque seguro**. Para ativá-la e criar um código de acesso, aceda a **configurações** > **ecrã de bloqueio e segurança** > **arranque seguro**.  

## <a name="encrypt-the-entire-device"></a>Encriptar todo o dispositivo

Esta secção aplica-se apenas a aplicação Portal da empresa. Alguns dispositivos permitem-lhe optar por encriptar todo o dispositivo ou apenas o espaço utilizado do mesmo. Escolha a opção para encriptar todo o dispositivo. Se tiver selecionado para criptografar apenas o espaço utilizado:

1. [Remover este dispositivo do Portal da empresa](unenroll-your-device-from-intune-android.md).
2. Desencripte o espaço utilizado.  
3. Encripte todo o dispositivo.  
4. Voltar a inscrever o dispositivo.  

## <a name="downgrade-your-version-of-android"></a>Mudar a versão do Android para uma versão anterior

Esta secção aplica-se apenas a aplicação Portal da empresa. Se o dispositivo oferece-lhe a opção para mudar para o Android 6.0 e posterior para, em seguida, fazê-lo. Existe um risco de perda de dados se tentar mudar o seu dispositivo. Em alternativa, recomendamos que contacte o suporte da empresa para resolver este problema. Obtenha informações de contacto de suporte da empresa sobre o [site do Portal da empresa](https://go.microsoft.com/fwlink/?linkid=2010980).  

## <a name="specific-manufacturer-issues"></a>Problemas de um fabricante específico

Alguns dispositivos Android com a versão 7.0 e posterior encriptam dados de forma inconsistente com determinadas normas da plataforma Android. Estes dispositivos poderão parecer encriptados mesmo quando são novos. O Intune reconhece que os métodos de encriptação destes dispositivos colocam as informações do mesmo em risco. Este risco está principalmente associado a utilizadores mal intencionados que têm acesso físico ao dispositivo.

> [!Note]
> A Microsoft trabalha com os fabricantes para abordar quaisquer problemas encontrados durante os testes ou comunicados pelos utilizadores. Atualizaremos este artigo sempre que estiverem disponíveis novas informações. 

## <a name="update-known-devices"></a>Atualizar dispositivos conhecidos   

Se não tiver atualizado o seu dispositivo para a versão mais recente do Android, aceda ao seu dispositivo **configurações** aplicação e selecione **atualização**. Estes dispositivos podem não aparecer em conformidade até que Atualize-as.  

- Huawei Honor 8
- Huawei P9

## <a name="known-devices-that-always-appear-encrypted"></a>Dispositivos conhecidos que aparecem sempre encriptados  
Os seguintes dispositivos serão exibidas sempre encriptados e não podem ser utilizados para aceder a recursos da empresa. Para aceder a recursos da empresa, tem de utilizar um dispositivo diferente.  

- Huawei Mate 8
- Dispositivos OPPO
- Dispositivos vivo
- Smartphones Xiaomi Mi  

## <a name="next-steps"></a>Passos Seguintes   
Ainda precisa de ajuda? Contacte o suporte da empresa (verifique as informações de contacto no [site do Portal da Empresa](https://go.microsoft.com/fwlink/?linkid=2010980)) ou escreva para a <a href="mailto:wintunedroidfbk@microsoft.com?subject=I'm having trouble with enrolling my Android device&body=Describe the issue you're experiencing here.">equipa Android da Microsoft</a>.  