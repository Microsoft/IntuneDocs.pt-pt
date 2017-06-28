---
title: "Bloqueio remoto e reposição do código de acesso"
description: "O Intune fornece funcionalidades de bloqueio remoto e de reposição do código de acesso."
keywords: 
author: NathBarn
ms.author: NathBarn
manager: angrobe
ms.date: 03/06/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 970f8c81-7c7f-4789-9ed4-2133d50b9db6
ms.reviewer: chrisgre
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: df3c42d8b52d1a01ddab82727e707639d5f77c16
ms.openlocfilehash: f43c2fb3c2aaff43aaef8cb033185c8c517d83a0
ms.contentlocale: pt-pt
ms.lasthandoff: 06/08/2017

---
# <a name="help-protect-your-devices-with-remote-lock-and-passcode-reset"></a>Ajudar a proteger os seus dispositivos através do bloqueio remoto e da reposição do código de acesso

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

O Microsoft Intune fornece funcionalidades de bloqueio remoto e de reposição do código de acesso.

## <a name="lock-a-device-remotely"></a>Bloquear remotamente um dispositivo
Se um utilizador perder um dispositivo, pode bloquear o mesmo remotamente. É necessário que o dispositivo já tenha um PIN ou código de acesso definido para que possa utilizar o bloqueio remoto.

A tabela seguinte indica como o bloqueio remoto funciona em diferentes plataformas móveis.

|Plataforma|Bloqueio remoto|
|------------|---------------|
|macOS|Não suportado|
|iOS|Suportado|
|Android|Suportado|
|Android for Work|Suportado|
|Windows 10 (dispositivo móvel)|Suportado|
|Windows 10 (computador)|Não suportado|
|Windows Phone 8 e Windows Phone 8.1|Suportado|
|Windows RT 8.1 e Windows RT|Suportado se o utilizador atual do dispositivo for o mesmo utilizador que inscreveu o dispositivo.|
|Windows 8.1|Suportado se o utilizador atual do dispositivo for o mesmo utilizador que inscreveu o dispositivo.|

O bloqueio remoto não é suportado para PCs Windows inscritos com o cliente de software do Intune.

### <a name="lock-a-mobile-device-remotely-through-the-intune-console"></a>Bloquear um dispositivo móvel remotamente através da consola do Intune

1.  Na [consola de administrador do Intune](https://manage.microsoft.com/), selecione **Grupos** &gt; **Todos os Dispositivos** &gt; **Todos os Dispositivos Móveis**.

2.  Escolha **Todos os Dispositivos Geridos Diretamente** para os dispositivos inscritos no Intune ou em **Todos os Dispositivos Geridos do Exchange ActiveSync**.

    > [!TIP]
    > Também pode navegar para um dispositivo por utilizador. Escolha **Todos os Utilizadores**. Na página propriedades do utilizador, selecione **Dispositivos** e, em seguida, selecione o nome do dispositivo móvel que pretende bloquear.

3.  Na lista, escolha o dispositivo ou dispositivos que pretende bloquear. Na barra de tarefas, selecione **Tarefas Remotas** e selecione **Bloqueio Remoto**.

## <a name="reset-the-passcode-on-a-device"></a>Repor o código de acesso num dispositivo
Se um utilizador se esquecer de um código de acesso, pode ajudá-lo ao remover o código de acesso de um dispositivo ou ao aplicar um novo código de acesso temporário num dispositivo. A seguinte tabela indica como a reposição de códigos de acesso funciona em diferentes plataformas móveis.

|Plataforma|Repor código de acesso|
|------------|------------------|
|macOS|Não suportado|
|iOS|Suportado para a eliminação do código de acesso de um dispositivo. Não cria um novo código de acesso temporário.|
|Android|Suportado em versões anteriores ao Android 7.0. Cria um código de acesso temporário.|
|Android for Work|Não suportado|
|Windows 10 Mobile|Suportado para a versão de Criativos do Windows 10 e dispositivos móveis posteriores associados ao Azure AD.|
|Windows Phone 8 e Windows Phone 8.1|Suportado|
|Windows RT 8.1|Não Suportado|
|Windows 8.1|Não Suportado|
|Computadores com o Windows 10|Não Suportado|

A reposição do código de acesso não é suportada para PCs Windows inscritos com o cliente de software do Intune.

### <a name="reset-a-passcode"></a>Repor um código de acesso

1.  Na [consola de administrador do Intune](https://manage.microsoft.com/), selecione **Grupos** &gt; **Todos os Dispositivos** &gt; **Todos os Dispositivos Móveis**.

2.  Escolha **Todos os Dispositivos Geridos Diretamente** para os dispositivos inscritos no Intune ou em **Todos os Dispositivos Geridos do Exchange ActiveSync**.

    > [!TIP]
    > Também pode navegar para um dispositivo por utilizador. Clique em **Todos os Utilizadores**. Na página de propriedades do utilizador, clique em **Dispositivos** e, em seguida, clique no nome do dispositivo móvel pretende apagar.

3.  Na lista, escolha o dispositivo ou dispositivos que pretende bloquear. Na barra de tarefas, selecione **Tarefas Remotas** e selecione **Reposição do Código de Acesso**.


### <a name="see-also"></a>Consulte também
[Extinguir dispositivos](retire-devices-from-microsoft-intune-management.md) e [Eliminação Seletiva do Windows para Gestão de Dados do Dispositivo](http://technet.microsoft.com/library/dn486874.aspx)

