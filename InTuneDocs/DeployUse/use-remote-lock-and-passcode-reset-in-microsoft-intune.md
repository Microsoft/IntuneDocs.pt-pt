---
title: "Utilizar o bloqueio remoto e a reposição do código de acesso | Microsoft Intune"
description: "O Intune fornece funcionalidades de bloqueio remoto e de reposição do código de acesso."
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/21/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 970f8c81-7c7f-4789-9ed4-2133d50b9db6
ms.reviewer: chrisgre
translationtype: Human Translation
ms.sourcegitcommit: 899f50cfec9e7c20d2981c077f93e0fccf37dc2b
ms.openlocfilehash: 0b52bd8360f11e226674aefe80a578c451c2679d

---
# Ajudar a proteger os seus dispositivos através do bloqueio remoto e da reposição do código de acesso
O Microsoft Intune fornece funcionalidades de bloqueio remoto e de reposição do código de acesso.

## Bloquear remotamente um dispositivo
Se um utilizador perder o respetivo dispositivo, pode bloquear o mesmo remotamente. A tabela abaixo indica como o bloqueio remoto funciona em diferentes plataformas móveis. O bloqueio remoto não é suportado

|Plataforma|Bloqueio remoto|
|------------|---------------|
|iOS|Suportado|
|Android|Suportado|
|Windows 10 e Windows 10 Mobile|Suportado|
|Windows Phone 8 e Windows Phone 8.1|Suportado|
|Windows RT 8.1 e Windows RT|Suportado se o utilizador atual do dispositivo for o mesmo utilizador que inscreveu o dispositivo.|
|Windows 8,1|Suportado se o utilizador atual do dispositivo for o mesmo utilizador que inscreveu o dispositivo.|

O bloqueio remoto não é suportado para PCs Windows inscritos com o cliente de software do Intune.

### Para bloquear um dispositivo móvel remotamente através da consola do Intune

1.  Na [consola de administrador do Intune](https://manage.microsoft.com/), selecione **Grupos** &gt; **Todos os Dispositivos** &gt; **Todos os Dispositivos Móveis**.

2.  Escolha **Todos os Dispositivos Geridos Diretamente** para os dispositivos inscritos no Intune ou em **Todos os Dispositivos Geridos do Exchange ActiveSync**.

    > [!TIP]
    > Também pode navegar para um dispositivo por utilizador. Escolha **Todos os Utilizadores**. Na página propriedades do utilizador, escolha **Dispositivos** e, em seguida, escolha o nome do dispositivo móvel que pretende apagar.

3.  Na lista, escolha o dispositivo ou dispositivos que pretende bloquear. Na barra de tarefas, escolha **Tarefas Remotas** e selecione **Bloqueio Remoto**.

## Repor o código de acesso num dispositivo
Se um utilizador se esquecer do respetivo código de acesso, pode ajudá-lo ao remover o código de acesso de um dispositivo ou ao aplicar um novo código de acesso temporário num dispositivo. A tabela abaixo indica como a reposição de códigos de acesso funciona em diferentes plataformas móveis.

|Plataforma|Repor código de acesso|
|------------|------------------|
|iOS|Suportado para a eliminação do código de acesso de um dispositivo. Não cria um novo código de acesso temporário.|
|Android|Suportado e é criado um código de acesso temporário.|
|Windows 10 Mobile|Suportado|
|Windows Phone 8 e Windows Phone 8.1|Suportado|
|Windows RT 8.1 e Windows RT|Não Suportado|
|Windows 8,1|Não Suportado|

A reposição do código de acesso não é suportada para PCs Windows inscritos com o cliente de software do Intune.

### Para repor um código de acesso

1.  Na [consola de administrador do Intune](https://manage.microsoft.com/), selecione **Grupos** &gt; **Todos os Dispositivos** &gt; **Todos os Dispositivos Móveis**.

2.  Escolha **Todos os Dispositivos Geridos Diretamente** para os dispositivos inscritos no Intune ou em **Todos os Dispositivos Geridos do Exchange ActiveSync**.

    > [!TIP]
    > Também pode navegar para um dispositivo por utilizador. Clique em **Todos os Utilizadores**. Na página de propriedades do utilizador, clique em **Dispositivos** e, em seguida, clique no nome do dispositivo móvel pretende apagar.

3.  Na lista, escolha o dispositivo ou dispositivos que pretende bloquear. Na barra de tarefas, escolha **Tarefas Remotas** e selecione **Reposição do Código de Acesso**.


### Consulte também
[Extinguir dispositivos](retire-devices-from-microsoft-intune-management.md)
[Eliminação Seletiva do Windows para Gestão de Dados do Dispositivo](http://technet.microsoft.com/library/dn486874.aspx)



<!--HONumber=Sep16_HO2-->


