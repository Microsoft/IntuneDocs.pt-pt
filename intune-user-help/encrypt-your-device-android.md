---
title: Encriptar o dispositivo Android do Intune | Documentos da Microsoft
description: Passos para ativar a criptografia de dispositivo Android quando necessário pelo Intune
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/19/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d4430e92-04cc-48e9-a77a-81b95a90b6b3
searchScope:
- User help
ROBOTS: ''
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 58217b6088669a7387ed7452f0ec81ae4a04b60c
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "61497180"
---
# <a name="encrypting-your-android-device"></a>Encriptar o seu dispositivo Android

Encriptação de dispositivos protege seus ficheiros e pastas contra acesso não autorizado se o dispositivo é perdido ou roubado. Depois de ativar a encriptação de dispositivos, apenas indivíduos com a palavra-passe correta ou o pin será capazes de iniciar sessão no seu dispositivo. 

Antes de poder aceder a recursos escolares ou profissionais, sua organização poderá exigir que encripte o seu dispositivo Android. Alguns dispositivos Android mais recentes são criptografados por padrão, out-of-the-box.  

## <a name="turn-on-encryption"></a>Ativar a criptografia

Se o Portal da empresa ou a aplicação Microsoft Intune pede-lhe para encriptar o seu dispositivo, conclua os passos seguintes. 

> [!Note]
> Não pode ser encriptada a Huawei, Vivo e OPPO, determinada dispositivos Android. Saiba mais [aqui](your-device-appears-encrypted-but-cp-says-otherwise-android.md).  

1.  Defina um bloqueio de ecrã do dispositivo.  
    a. Aceda a **configurações** > **bloqueio de ecrã e segurança** > **tipo de bloqueio de ecrã**.  
    b. Selecione **PIN**, **palavra-passe**, ou **padrão**.  
    c. Siga as instruções na tela para configurar o bloqueio de ecrã.  

2. Volte ao **bloqueio de ecrã e segurança** e selecione **arranque seguro**.
3. Escolher **exigir PIN quando o dispositivo ativa** > **OK**.
4. Introduza o PIN para confirmar e encriptar o seu dispositivo.
5. Abra a aplicação Portal da empresa ou o Microsoft Intune.
    * Utilizadores do Portal da empresa: Selecione o seu dispositivo e toque em **Verifique as definições do dispositivo**. 
    * Utilizadores do Microsoft Intune: Terá que esperar até as atualizações de página, mas quando isso acontece, o estado de encriptação deve ser alterado para em conformidade.  

Dispositivos Android 4.4 e anteriores talvez não tenham o **arranque seguro** opção. Nesse caso, conclua os seguintes passos para encriptar o seu dispositivo.

1. Aceda a **configurações** > **segurança** > **encriptar o dispositivo**. As etiquetas na tela variam entre os dispositivos Android. Se não vir a **encriptar dispositivo** opção, check-in:
    * **Armazenamento** > **encriptação de armazenamento**
    * **Armazenamento** > **bloquear ecrã e segurança** > **outras definições de segurança** 

2. Siga as instruções no ecrã. Durante a encriptação, o dispositivo foi reiniciado diversas vezes.
3. Abra a aplicação Portal da empresa ou o Microsoft Intune.
    * Utilizadores do Portal da empresa: Selecione o seu dispositivo e toque em **Verifique as definições do dispositivo**.  
    * Utilizadores do Microsoft Intune: Terá que esperar até as atualizações de página, mas quando isso acontece, o estado de encriptação deve ser alterado para em conformidade.

## <a name="troubleshoot"></a>Resolução de problemas  
**Problema**: Já já encriptou o seu dispositivo e

- O botão de encriptação está desativado.
- Vê uma mensagem a indicar que ainda tem de encriptar.
- Obtém erros quando tenta utilizar a aplicação Portal da empresa ou o Microsoft Intune.

**Coisas a experimentar**

- Certifique-se de que o seu dispositivo está carregado e ligado.  
- Confirme se definiu uma palavra-passe ou um PIN no dispositivo.  

Ainda precisa de ajuda? Contacte o suporte da empresa (verifique as informações de contacto no [site do Portal da Empresa](https://go.microsoft.com/fwlink/?linkid=2010980)) ou escreva para a <a href="mailto:wintunedroidfbk@microsoft.com?subject=I'm having trouble with encryption on my Android device&body=Describe the issue you're experiencing here.">equipa Android da Microsoft</a>.  
