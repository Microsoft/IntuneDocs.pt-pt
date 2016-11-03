---
title: "Configurar a gestão do Windows 10 Mobile e Windows Phone | Microsoft Intune"
description: "Ative a gestão de dispositivos móveis (MDM) para dispositivos Windows 10 Mobile ou Windows Phone com o Microsoft Intune."
keywords: 
author: NathBarn
manager: angrobe
ms.date: 08/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f5615051-2dd1-453b-9872-d3fdcefb2cb8
ms.reviewer: damionw
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: c880bd9dfb998355a18e78af898a96d4cee393f7
ms.openlocfilehash: d88405e913fe61cef2c297f9d50408e10674cf3f


---


# Configurar a gestão do Windows Phone e Windows 10 Mobile com o Microsoft Intune

Como administrador do Intune, pode ativar a inscrição e gestão de dispositivos Windows 10 Mobile e Windows Phone de duas formas:

- **[Inscrição automática com o Azure AD](#azure-active-directory-enrollment)** - os utilizadores do Windows 10 e Windows 10 Mobile inscrevem os dispositivos deles ao adicionarem uma conta profissional ou escolar ao dispositivo
- **[Inscrição no Portal da Empresa](#company-portal-app-enrollment)** - o Windows Phone 8.1 e dispositivos posteriores são inscritos ao transferir e instalar a aplicação Portal da Empresa e, em seguida, introduzindo as respetivas credenciais da conta profissional ou escolar na aplicação.


[!INCLUDE[AAD-enrollment](../includes/win10-automatic-enrollment-aad.md)]

## Inscrição de aplicações no Portal da Empresa
Pode permitir que os utilizadores inscrevam os dispositivos deles através da instalação e inscrição dos dispositivos com a aplicação Portal da Empresa do Intune. A criação de um CNAME DNS ajuda os utilizadores a ligar e a inscrever-se no Intune sem que seja necessário introduzir um nome de servidor. Se gerir dispositivos Windows Phone 8.0 ou precisar de implementar o Portal da Empresa em dispositivos Windows Phone, também tem de transferir e assinar a aplicação Portal da Empresa. Consulte [Configurar a gestão do Windows Phone 8.0](set-up-windows-phone-8.0-management-with-microsoft-intune.md).

1.  **Configurar o Intune**<br>Se ainda não o fez, prepare a gestão de dispositivos móveis ao [definir a autoridade de gestão de dispositivos móveis](prerequisites-for-enrollment.md#set-mobile-device-management-authority) como **Microsoft Intune** e ao configurar a MDM.

2.  **Criar CNAMEs** (opcional)<br>Crie registos de recursos DNS **CNAME** para o domínio da sua empresa. Por exemplo, se o Web site da sua empresa fosse contoso.com, criaria um CNAME em DNS que redireciona EnterpriseEnrollment.contoso.com para manage.microsoft.com. Se existir mais do que um domínio verificado, crie um registo CNAME para cada domínio. Os registos de recursos CNAME têm de conter as seguintes informações:

  |TIPO|Nome do anfitrião|Aponta para|TTL|
  |--------|-------------|-------------|-------|
  |CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com |1 Hora|
  |CNAME|EnterpriseRegistration.company_domain.com|EnterpriseRegistration.windows.net|1 Hora|
  As alterações ao registo DNS podem demorar até 72 horas a serem propagadas. Não é possível verificar a alteração de DNS no Intune até o registo DNS ser propagado.

  `EnterpriseEnrollment-s.manage.microsoft.com` – Suporta o redirecionamento para o serviço Intune com reconhecimento de domínio a partir do nome de domínio do e-mail

  `EnterpriseRegistration.windows.net` – Suporta os dispositivos Windows 8.1 e Windows 10 Mobile que serão registados no Azure Active Directory utilizando a respetiva conta profissional ou escolar

  Se a sua empresa utilizar vários domínios para as credenciais do utilizador, crie os registos CNAME para cada domínio.

  Por exemplo, se o Web site da sua empresa fosse contoso.com, criaria um CNAME em DNS que redirecionaria EnterpriseEnrollment.contoso.com para EnterpriseEnrollment-s.manage.microsoft.com. As alterações ao registo DNS podem demorar até 72 horas a serem propagadas. Não é possível verificar a alteração de DNS no Intune até o registo DNS ser propagado.

3.  **Verificar o CNAME**<br>Na [consola de administração do Intune](http://manage.microsoft.com), clique em **Administração** &gt; **Gestão de Dispositivos Móveis** &gt; **Windows Phone**. Introduza o URL do domínio verificado do site da empresa na caixa **Especificar o nome de um domínio verificado** e, em seguida, clique em **Testar Deteção Automática**.

    ![Caixa de diálogo Configurar a gestão de dispositivos móveis do Windows](../media/windows-phone-enrollment.png)

4.  **Passos opcionais**<br>O passo **Adicionar as Chaves de Sideload** não é necessário para o Windows 10. O passo **Carregar o Certificado de Assinatura de Código** só é necessário se distribuir aplicações de linha de negócio (LOB) para dispositivos que não estão disponíveis na Loja Windows. [Saiba mais](set-up-windows-phone-8.0-management-with-microsoft-intune.md)

5.  **Informar os utilizadores**<br>Os seus utilizadores terão de saber como inscrever os dispositivos deles e o que esperar quando passarem a ser geridos.
    - [O que dizer aos utilizadores finais sobre a utilização do Microsoft Intune](what-to-tell-your-end-users-about-using-microsoft-intune.md)
    - [Orientações para o utilizador final para dispositivos Windows](../enduser/using-your-windows-device-with-intune.md)

Não é necessário qualquer ação adicional, a não ser que pretenda implementar o Portal da Empresa nos dispositivos.  Os passos 2 e 3 na consola de administração podem ser ignorados em segurança.



<!--HONumber=Sep16_HO4-->


