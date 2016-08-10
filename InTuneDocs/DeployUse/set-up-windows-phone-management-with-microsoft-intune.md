---
title: "Configurar a gestão do Windows 10 Mobile e Windows Phone | Microsoft Intune"
description: "Ative a gestão de dispositivos móveis (MDM) para dispositivos Windows 10 Mobile ou Windows Phone com o Microsoft Intune."
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f5615051-2dd1-453b-9872-d3fdcefb2cb8
ms.reviewer: damionw
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 06d6c8ce97ba6a259055e94f0eba87f7c5a96531
ms.openlocfilehash: 344f1cf4367deb12288f9c361e043d345f9846bb


---


# Configurar a gestão do Windows Phone e Windows 10 Mobile com o Microsoft Intune
Para configurar o seu dispositivo Windows, pode encontrar ajuda [aqui](../enduser/using-your-windows-device-with-intune.md).

Antes de poder gerir dispositivos Windows 10 Mobile ou Windows Phone com o Intune, os dispositivos têm de conseguir comunicar com o Intune. Para simplificar isto, pode criar um registo DNS para que os utilizadores não tenham de introduzir o endereço do servidor. Os passos abaixo descrevem como simplificar a inscrição para os utilizadores.  

Para a maioria dos cenários, os utilizadores podem instalar a aplicação Portal da Empresa a partir da Loja Windows. Se gerir dispositivos Windows Phone 8.0 ou precisar de implementar o Portal da Empresa em dispositivos Windows Phone, também tem de transferir e assinar a aplicação Portal da Empresa. Consulte [Configurar a gestão do Windows Phone 8.0](set-up-windows-phone-8.0-management-with-microsoft-intune.md).

1.  **Configurar o Intune** Se ainda não o fez, prepare a gestão de dispositivos móveis, [definindo a autoridade de gestão de dispositivos móveis](get-ready-to-enroll-devices-in-microsoft-intune.md#set-mobile-device-management-authority) como **Microsoft Intune** e definindo o MDM.

2.  **Definir um alias DNS para o endereço do servidor de inscrição** (opcional)

    Criar um alias de DNS (tipo de registo CNAME) torna mais fácil para os utilizadores inscreverem os respetivos dispositivos. Embora a entrada DNS CNAME seja opcional para a inscrição de dispositivos Windows, recomenda-se que crie um ou mais registos quando for necessário, para facilitar o processo de inscrição destes dispositivos. Se não for encontrado nenhum registo CNAME, é pedido ao utilizador que introduza o nome do servidor de MDM manualmente.

  1.  Crie registos de recursos DNS **CNAME** para o domínio da sua empresa. Por exemplo, se o Web site da sua empresa fosse contoso.com, criaria um CNAME em DNS que redireciona EnterpriseEnrollment.contoso.com para manage.microsoft.com. Se existir mais do que um domínio verificado, crie um registo CNAME para cada domínio. Os registos de recursos CNAME têm de conter as seguintes informações:

      |TIPO|Nome do anfitrião|Aponta para|TTL|
      |--------|-------------|-------------|-------|
      |CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com |1 Hora|
      |CNAME|EnterpriseRegistration.company_domain.com|EnterpriseRegistration.windows.net|1 Hora|

      As alterações ao registo DNS podem demorar até 72 horas a serem propagadas. Não é possível verificar a alteração de DNS no Intune até o registo DNS ser propagado.

      **EnterpriseEnrollment-s.manage.microsoft.com** – Suporta o redirecionamento para o serviço Intune com reconhecimento de domínio a partir do nome de domínio do e-mail

      **EnterpriseRegistration.windows.net** – Suporta os dispositivos Windows 8.1 e Windows 10 Mobile que serão registados no Azure Active Directory utilizando a respetiva conta escolar ou profissional

    2.  Na [consola de administração do Intune](http://manage.microsoft.com), clique em **Administração** &gt; **Gestão de Dispositivos Móveis** &gt; **Windows Phone**.

      ![Caixa de diálogo Configurar a gestão de dispositivos móveis do Windows](../media/windows-device-enrollment.png)

    3.  Introduza o URL do domínio verificado do site da empresa na caixa **Especificar o nome de um domínio verificado** e, em seguida, clique em **Testar Deteção Automática**.

    4.  Os seus utilizadores terão de saber como inscrever os dispositivos deles e o que esperar quando passarem a ser geridos.
        - [O que dizer aos utilizadores finais sobre a utilização do Microsoft Intune](what-to-tell-your-end-users-about-using-microsoft-intune.md)
        - [Orientações para o utilizador final para dispositivos Windows](../enduser/using-your-windows-device-with-intune.md)



Não é necessário qualquer ação adicional, a não ser que pretenda implementar o Portal da Empresa nos dispositivos.  Os passos 2 e 3 na consola de administração podem ser ignorados em segurança.



<!--HONumber=Aug16_HO1-->


