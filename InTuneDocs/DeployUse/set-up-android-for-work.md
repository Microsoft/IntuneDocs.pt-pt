---
title: "Configurar a gestão do Android for Work | Microsoft Intune"
description: "Ative a gestão de dispositivos móveis (MDM) para dispositivos Android for Work com o Microsoft Intune."
keywords: 
author: NathBarn
manager: angrobe
ms.date: 10/12/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b2fdcea9-9ad7-4d73-88e2-854b7a774bb2
translationtype: Human Translation
ms.sourcegitcommit: 519b66c94f3d056e060ed11e1a3d7d6d118a94fb
ms.openlocfilehash: 5f48303dd28627f961f8c2cfd38f8977354e2724


---

# Ativar a inscrição de dispositivos Android for Work

Para ativar a gestão de dispositivos Android for Work, tem de adicionar um enlace do Android for Work para Intune. Para inscrever dispositivos que suportam o Android for Work mas que foram anteriormente inscritos como um dispositivos Android normal, a inscrição dos dispositivos tem de ser anulada e, em seguida efetuada novamente.

## Adicionar o Enlace do Android for Work para Intune

1. **Configurar o Intune**<br>
Se ainda não o fez, prepare a gestão de dispositivos móveis ao [definir a autoridade de gestão de dispositivos móveis](prerequisites-for-enrollment.md#set-mobile-device-management-authority) como **Microsoft Intune** e ao configurar a MDM.

2. **Configurar o enlace do Android for Work**<br>
    Enquanto utilizador administrativo, abra a [consola de administração do Microsoft Intune](http://manage.microsoft.com), aceda a **Administração** &gt; **Gestão de Dispositivos Móveis** &gt; **Android for Work** e clique em **Configurar** para abrir o site do Android for Work do Google Play. Esta ação irá abrir um novo separador no seu browser.

3. **Iniciar sessão no Google**<br>
   Na página de início de sessão do Google, entre com a conta Google que será associada a todas as tarefas de gestão do Android for Work deste inquilino. Esta conta pode ser uma conta Google partilhada entre os administradores que gerem o Intune. Esta é a conta Google que a sua organização utiliza para gerir e publicar aplicações na consola Play for Work.

4. **Fornecer detalhes da Organização**<br>
   Na opção **Nome da organização** forneça o nome da sua empresa. A opção **Fornecedor de Gestão de mobilidade de empresas (EMM)** deverá apresentar o valor *Microsoft Intune*. Concorde com o contrato Android for Work e, em seguida, clique em **Confirmar**. O seu pedido será processado.

## Especificar as Definições de Inscrição do Android for Work
   O Android for Work só é suportado em determinados dispositivos Android. Veja os [requisitos Android for Work](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012 style="target=new_window") da Google.  Qualquer dispositivo que suporte o Android for Work também irá suportar a gestão Android convencional.  O Intune permite-lhe especificar como os dispositivos que suportam o Android for Work devem ser geridos:

   - **Gerir todos os dispositivos como Android** – (desativado) todos os dispositivos Android, incluindo os dispositivos que suportam o Android for Work, serão inscritos como dispositivos Android convencionais.
   - **Gerir dispositivos suportados como Android for Work** – (ativado) todos os dispositivos que suportam o Android for Work são inscritos como dispositivos Android for Work. Qualquer dispositivo Android que não suporte o Android for Work é inscrito como um dispositivo Android convencional.
   - **Gerir dispositivos suportados para utilizadores apenas nestes grupos de utilizadores como Android for Work** – (em teste) permite-lhe direcionar a gestão do Android for Work a um conjunto limitado de utilizadores. Apenas os membros destes grupos selecionados que inscrevam um dispositivo que suporte o Android for Work são inscritos como dispositivos Android for Work. Todos os outros dispositivos são inscritos como dispositivos Android.

## Próximos passos para Android for Work
Após configurar as definições e o enlace Android for Work, pode gerir o seguinte:
- [Implementar aplicações Android for Work](android-for-work-apps.md)
- [Adicionar políticas de configuração Android for Work](android-for-work-policy-settings-in-microsoft-intune.md)

## Anular o enlace da conta administrativa do Android for Work

Pode desativar a gestão e inscrição do Android for Work. Ao clicar em **Anular o enlace** remove todos os dispositivos Android for Work inscritos e remove a relação entre a conta Android for Work e o Intune.

### Como anular o enlace de uma conta Android for Work

1. **Anular o enlace do Android for Work**<br>
    Enquanto utilizador administrativo, abra a [consola de administração do Microsoft Intune](http://manage.microsoft.com), aceda a **Administração** &gt; **Gestão de Dispositivos Móveis** &gt; **Android for Work** e clique em **Anular enlace**.

2. **Concorde com a eliminação do enlace do Android for Work**<br>
  Clique em **Sim** para eliminar o enlace e anular a inscrição de todos os dispositivos Android for Work do Intune.



<!--HONumber=Oct16_HO2-->


