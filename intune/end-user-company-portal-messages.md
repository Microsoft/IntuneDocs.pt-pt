---
title: Mensagens do Portal da Empresa que os utilizadores poderão ver nos dispositivos
titlesuffix: Microsoft Intune
description: Compreenda as diferentes mensagens que os utilizadores finais poderão ver no Portal da Empresa.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 03/09/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 3df993aa-48c5-4799-b68d-c85fe4f7b02c
ms.reviewer: aanavath
ms.suite: ems
ms.openlocfilehash: 3ed729e437fcdbc4352bf5fa8ceada4ddf336708
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/16/2018
ms.locfileid: "31025812"
---
# <a name="help-end-users-understand-company-portal-app-messages"></a>Ajudar os utilizadores finais a compreender as mensagens da aplicação Portal da Empresa

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

> [!NOTE]
> As seguintes informações aplicam-se apenas a dispositivos com o Android 6.0 e posterior.

Compreenda as diferentes mensagens de aplicações que os utilizadores finais poderão ver no Portal da Empresa. Estas mensagens de aplicações são normalmente apresentadas em diferentes fases do processo de inscrição. Saiba onde as mensagens são apresentadas, o que significam e o que acontece se os utilizadores negarem o acesso. Para além disso, saiba como melhor explicar estas mensagens aos utilizadores.

- __Permitir que o Portal da Empresa efetue e faça a gestão de chamadas telefónicas?__
- __Permitir que o Portal da Empresa aceda às fotografias, multimédia e ficheiros no dispositivo?__

## <a name="allow-company-portal-to-make-and-manage-phone-calls"></a>Permitir que o Portal da Empresa efetue e faça a gestão de chamadas telefónicas?

### <a name="where-it-appears"></a>Onde aparece
A mensagem **Permitir que o Portal da Empresa efetue e faça a gestão de chamadas telefónicas?** é apresentada quando os utilizadores tocam em **Inscrever** na aplicação Portal da Empresa quando inscrevem os dispositivos.

### <a name="what-it-means"></a>O que significa
Ao aceitarem este pedido, os utilizadores permitem que os números IMEI e de telefone do dispositivo sejam enviados para o serviço Intune. Estes números serão apresentados na consola de administração na página __Hardware__.

> [!NOTE]
> **A aplicação Portal da Empresa nunca efetua ou gere chamadas telefónicas!** O texto da mensagem é controlado pelo Google e não pode ser alterado.

Para ver a página **Hardware**, tem de aceder a **Grupos** > **Todos os dispositivos móveis** > **Dispositivos**. Selecione o dispositivo do utilizador e aceda a **Ver Propriedades** > **Hardware**.

### <a name="what-happens-if-users-deny-access"></a>O que acontece se os utilizadores recusarem o acesso
Se os utilizadores negarem o acesso, poderão continuar a utilizar a aplicação Portal da Empresa e a inscrever os dispositivos. No entanto, o número IMEI e o número de telefone do dispositivo estarão em branco na página __Hardware__ na consola de administração. Na segunda vez que os utilizadores iniciarem sessão na aplicação Portal da Empresa após negarem o acesso, a mensagem mostrará uma caixa de verificação **Não voltar a perguntar**, que os utilizadores podem selecionar para que a mensagem não volte a aparecer.

Se os utilizadores permitirem o acesso, mas o negarem mais tarde, a mensagem é apresentada quando os utilizadores iniciarem sessão novamente na aplicação Portal da Empresa depois da inscrição.

Se, posteriormente, os utilizadores decidirem permitir o acesso, poderão aceder a **Definições** > **Aplicações** > **Portal da Empresa** > **Permissões** > **Telemóvel** e ativar a opção.

### <a name="how-to-explain-this-to-your-users"></a>Como explicar esta questão aos utilizadores
Para obterem mais informações, indique aos utilizadores para acederem a [Inscrever o dispositivo Android no Intune](/intune-user-help/enroll-your-device-in-intune-android).

## <a name="allow-company-portal-to-access-your-contacts"></a>Permitir que o Portal da Empresa aceda aos seus contactos?

### <a name="where-it-appears"></a>Onde aparece
A mensagem **Permitir que o Portal da Empresa aceda aos seus contactos?** é apresentada quando os utilizadores tocam em **Inscrever** na aplicação Portal da Empresa quando inscrevem os dispositivos.

### <a name="what-it-means"></a>O que significa
Ao aceitarem este pedido, os utilizadores permitem que o Intune crie a conta profissional deles e faça a gestão da identidade do Azure Active Directory que está registada para o utilizador nesse dispositivo.

> [!NOTE]
> **A Microsoft nunca acede aos seus contactos!** O texto da mensagem é controlado pelo Google e não pode ser alterado.

### <a name="what-happens-if-users-deny-access"></a>O que acontece se os utilizadores recusarem o acesso
Se os utilizadores negarem o acesso, o respetivo dispositivo não será inscrito no Intune e não pode ser gerido. Na segunda vez que os utilizadores iniciarem sessão na aplicação Portal da Empresa após negarem o acesso, a mensagem mostrará uma caixa de verificação **Não voltar a perguntar**, que os utilizadores podem selecionar para que a mensagem não volte a aparecer.

Se os utilizadores permitirem o acesso, mas o negarem mais tarde, a mensagem é apresentada quando os utilizadores iniciarem sessão novamente na aplicação Portal da Empresa depois da inscrição.

Se, posteriormente, os utilizadores decidirem permitir o acesso, poderão aceder a **Definições** > **Aplicações** > **Portal da Empresa** > **Permissões** > **Telemóvel** e ativar a opção.

### <a name="how-to-explain-this-to-your-users"></a>Como explicar esta questão aos utilizadores
Para obterem mais informações, indique aos utilizadores para acederem a [Inscrever o dispositivo Android no Intune](/intune-user-help/enroll-your-device-in-intune-android).

## <a name="allow-company-portal-to-access-photos-media-and-files-on-your-device"></a>Permitir que o Portal da Empresa aceda às fotografias, multimédia e ficheiros no seu dispositivo?

### <a name="where-it-appears"></a>Onde aparece
A mensagem **Permitir que o Portal da Empresa aceda às fotografias, multimédia e ficheiros no dispositivo?** é apresentada quando os utilizadores tocam em **Enviar Dados** para enviar os registos de dados para o administrador de TI.

### <a name="what-it-means"></a>O que significa
Ao aceitar esta mensagem, os utilizadores permitem que o dispositivo escreva registos de dados no cartão SD do mesmo. Esses registos também podem ser movidos através de um cabo USB.   

> [!NOTE]
> **A aplicação Portal da Empresa nunca acede às fotografias, multimédia e ficheiros dos utilizadores!** O texto da mensagem é controlado pelo Google e não pode ser alterado.

### <a name="what-happens-if-users-deny-access"></a>O que acontece se os utilizadores recusarem o acesso
Se os utilizadores negarem o acesso, podem ainda enviar registos de dados por e-mail, mas os registos não serão copiados para o cartão SD do dispositivo.

Na segunda vez que os utilizadores iniciam sessão na aplicação Portal da Empresa após negarem o acesso, a mensagem mostra uma caixa de verificação **Não voltar a perguntar**, que os utilizadores podem selecionar para que a mensagem não volte a aparecer. Se os utilizadores permitirem o acesso, mas o negarem mais tarde, a mensagem é apresentada quando os utilizadores tentarem enviar registos. Contudo, se posteriormente os utilizadores decidirem permitir o acesso, podem aceder a **Definições** > **Aplicações** > **Portal da Empresa** > **Permissões** > **Armazenamento** e, em seguida, ativar a permissão.


### <a name="how-to-explain-this-to-your-users"></a>Como explicar esta questão aos utilizadores
Indique aos utilizadores para acederem a [Enviar registos para o administrador de TI por e-mail](/intune-user-help/send-logs-to-your-it-admin-by-email-android). 

## <a name="your-company-support-needs-to-give-you-access-to-company-resources"></a>O suporte da sua empresa tem de lhe conceder acesso aos recursos da empresa

### <a name="where-it-appears"></a>Onde aparece
Se não tiver adicionado a aplicação Portal da Empresa à lista de **Aplicações permitidas** ou **Aplicações excluídas** e um utilizador tentar iniciar sessão, não irá conseguir. Será apresentada a seguinte mensagem:

> **O suporte da sua empresa tem de lhe conceder acesso aos recursos da empresa**  
> A sua empresa está a utilizar políticas do Windows Information Protection para proteger o seu dispositivo. O suporte da sua empresa terá de se certificar de que permite o acesso a esses recursos por parte do Portal da Empresa.

### <a name="what-it-means"></a>O que significa

Adicione o Portal da Empresa à lista de **Aplicações permitidas** ou **Aplicações excluídas** na política de proteção de aplicações Windows Information Protection (WIP). Para obter mais informações, veja [Criar e implementar a política de proteção de aplicações do Windows Information Protection (WIP) com o Intune](/intune-classic/deploy-use/create-windows-information-protection-policy-with-intune).

### <a name="see-also"></a>Consulte também
[O que dizer aos utilizadores finais sobre a utilização do Intune](end-user-educate.md)
