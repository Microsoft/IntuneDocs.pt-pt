---
title: "Configurar a gestão de dispositivos Windows com o Microsoft Intune | Microsoft Intune"
description: "Ative a gestão de dispositivos móveis (MDM) para PCs Windows, incluindo dispositivos Windows 10, com o Microsoft Intune."
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/25/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9a18c0fe-9f03-4e84-a4d0-b63821bf5d25
ms.reviewer: damionw
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 06d6c8ce97ba6a259055e94f0eba87f7c5a96531
ms.openlocfilehash: fae2aa496ec38d9ddc2cb6800bed10ccb32fd154


---

# Configurar a gestão de dispositivos Windows
Para configurar o seu dispositivo Windows, pode encontrar ajuda [aqui](../enduser/using-your-windows-device-with-intune.md).

Com o Intune, pode ativar BYOD ("bring your own device") na inscrição de dispositivos PC Windows para dar acesso às aplicações e ao e-mail da empresa. Utilizado com o Azure Active Directory, o BYOD também proporciona uma forma rápida e automática de adicionar novos dispositivos Windows 10 para gestão e de obter acesso a recursos da empresa sem ter de recriar a imagem do computador. Após a inscrição, os utilizadores podem iniciar sessão e pode ser utilizada a consola de administração do Intune para segmentar políticas, aplicações e definições para os dispositivos deles. Também poderá querer [configurar a gestão do Windows Phone com o Microsoft Intune](set-up-windows-phone-management-with-microsoft-intune.md) ou [gerir computadores com o software de cliente do Intune](manage-windows-pcs-with-microsoft-intune.md) com o cliente do Intune.

A criação de um CNAME DNS ajuda os utilizadores a ligar e a inscrever-se no Intune sem que seja necessário introduzir um nome de servidor.

### Configurar a gestão de dispositivos Windows

  1.  Crie um registo de recursos DNS **CNAME** para o domínio da sua empresa. Por exemplo, se o Web site da sua empresa fosse contoso.com, criaria um CNAME em DNS que redirecionaria EnterpriseEnrollment.contoso.com para EnterpriseEnrollment-s.manage.microsoft.com. Embora a entrada DNS CNAME seja opcional para a inscrição de dispositivos Windows, recomenda-se que crie um ou mais registos quando for necessário, para facilitar o processo de inscrição destes dispositivos. Se não for encontrado nenhum registo CNAME, é pedido ao utilizador que introduza o nome do servidor de MDM manualmente.

  Se existir mais do que um domínio verificado, crie um registo CNAME para cada domínio. Os registos de recursos CNAME têm de conter as seguintes informações:

  |TIPO|Nome do anfitrião|Aponta para|TTL|
  |--------|-------------|-------------|-------|
  |CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com |1 Hora|
  |CNAME|EnterpriseRegistration.company_domain.com|EnterpriseRegistration.windows.net|1 Hora|

  As alterações ao registo DNS podem demorar até 72 horas a serem propagadas. Não é possível verificar a alteração de DNS no Intune até o registo DNS ser propagado.

  **EnterpriseEnrollment-s.manage.microsoft.com** – Suporta o redirecionamento para o serviço Intune com reconhecimento de domínio a partir do nome de domínio do e-mail

  **EnterpriseRegistration.windows.net** – Suporta os dispositivos Windows 8.1 e Windows 10 Mobile que serão registados no Azure Active Directory utilizando a respetiva conta escolar ou profissional

  2.  Na [consola de administração do Intune](http://manage.microsoft.com), clique em **Administração** &gt; **Gestão de Dispositivos Móveis** &gt; **Windows**.
  ![Caixa de diálogo da gestão de dispositivos Windows](../media/enroll-intune-winenr.png)

  3.  Introduza o URL do domínio verificado do site da empresa na caixa **Especificar o nome de um domínio verificado** e, em seguida, clique em **Testar Deteção Automática**.

  4.  Os seus utilizadores terão de saber como inscrever os dispositivos deles e o que esperar quando passarem a ser geridos.
      - [O que dizer aos utilizadores finais sobre a utilização do Microsoft Intune](what-to-tell-your-end-users-about-using-microsoft-intune.md)
      - [Orientações para o utilizador final para dispositivos Windows](../enduser/using-your-windows-device-with-intune.md)

### Consulte também
[Prepare-se para inscrever dispositivos no Microsoft Intune](get-ready-to-enroll-devices-in-microsoft-intune.md)



<!--HONumber=Aug16_HO1-->


