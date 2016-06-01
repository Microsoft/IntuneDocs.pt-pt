---
# required metadata

title: Configurar a gestão de dispositivos Windows com o Microsoft Intune | Microsoft Intune
description:
keywords:
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 9a18c0fe-9f03-4e84-a4d0-b63821bf5d25

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Configurar a gestão de dispositivos Windows
Com o Intune, pode ativar BYOD ("bring your own device") na inscrição de dispositivos PC Windows para dar acesso às aplicações e ao e-mail da empresa. Utilizado com o Azure Active Directory, o BYOD também proporciona uma forma rápida e automática de adicionar novos dispositivos Windows 10 para gestão e de obter acesso a recursos da empresa sem ter de recriar a imagem do computador. Após a inscrição, os utilizadores podem iniciar sessão e pode ser utilizada a consola de administração do Intune para segmentar políticas, aplicações e definições para os dispositivos deles. Também poderá querer [configurar a gestão do Windows Phone com o Microsoft Intune](set-up-windows-phone-management-with-microsoft-intune.md) ou [gerir computadores com o software de cliente do Intune](manage-windows-pcs-with-microsoft-intune.md) com o cliente do Intune.

A criação de um CNAME DNS ajuda os utilizadores a ligar e a inscrever-se no Intune sem que seja necessário introduzir um nome de servidor.

### Configurar a gestão de dispositivos Windows

  1.  Crie um registo de recursos DNS **CNAME** para o domínio da sua empresa. Por exemplo, se o Web site da sua empresa fosse contoso.com, criaria um CNAME em DNS que redirecionaria EnterpriseEnrollment.contoso.com para EnterpriseEnrollment-s.manage.microsoft.com. Se existir mais do que um domínio verificado, crie um registo CNAME para cada domínio. Os registos de recursos CNAME têm de conter as seguintes informações:

  |TIPO|Nome do anfitrião|Aponta para|TTL|
  |--------|-------------|-------------|-------|
  |CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com |1 Hora|
  |CNAME|EnterpriseRegistration.company_domain.com|EnterpriseRegistration.windows.net|1 Hora|

    DNS record changes might take up to 72 hours to propagate. You cannot verify the DNS change in Intune until the DNS record propagates.

    **EnterpriseEnrollment-s.manage.microsoft.com** – Supports a redirect to the Intune service with domain recognition from the email’s domain name

    **EnterpriseRegistration.windows.net** – Supports Windows 8.1 and Windows 10 Mobile devices that will register with Azure Active Directory using their work or school account

  2.  Na [consola de administração do Intune](http://manage.microsoft.com), clique em **Administração** &gt; **Gestão de Dispositivos Móveis** &gt; **Windows**
  ![Caixa de diálogo da gestão de dispositivos Windows](../media/enroll-intune-winenr.png)
  3.  Introduza o URL do domínio verificado do Web site da empresa na caixa **Especificar o nome de um domínio verificado** e, em seguida, clique em **Testar Deteção Automática**.

### Consulte também
[Prepare-se para inscrever dispositivos no Microsoft Intune](get-ready-to-enroll-devices-in-microsoft-intune.md)


<!--HONumber=May16_HO2-->


