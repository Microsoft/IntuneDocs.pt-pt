---
title: "Configurar a gestão do Windows 10 Mobile e Windows Phone | Microsoft Intune"
description: "Ative a gestão de dispositivos móveis (MDM) para dispositivos Windows 10 Mobile ou Windows Phone com o Microsoft Intune."
keywords: 
author: staciebarker
manager: angrobe
ms.date: 11/10/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f5615051-2dd1-453b-9872-d3fdcefb2cb8
ms.reviewer: damionw
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 3f28cce75626df1115283dc98547adcb97ee1cb4
ms.openlocfilehash: ce460c1b87b4759dcdeed061c2342b68dd491820


---

<<<<<<< HEAD

# Configurar a gestão do Windows Phone e Windows 10 Mobile com o Microsoft Intune
||||||| merged common ancestors

# Configurar a gestão do Windows Phone e Windows 10 Mobile com o Microsoft Intune
=======

# <a name="set-up-windows-phone-and-windows-10-mobile-management-with-microsoft-intune"></a>Configurar a gestão do Windows Phone e Windows 10 Mobile com o Microsoft Intune
>>>>>>> 6851ab9d7bde3f80f14f27ebf43e5f2b265939e2

Como administrador do Intune, pode ativar a inscrição e gestão de dispositivos Windows 10 Mobile e Windows Phone de duas formas:

- **[Inscrição automática com o Azure Active Directory](#azure-active-directory-enrollment)** – os utilizadores do Windows 10 e Windows 10 Mobile inscrevem os respetivos dispositivos ao adicionarem uma conta escolar ou profissional ao dispositivo
- **[Inscrição no Portal da Empresa](#company-portal-app-enrollment)** – os utilizadores do Windows Phone 8.1 e posterior inscrevem os respetivos dispositivos ao transferir e instalar a aplicação Portal da Empresa e, em seguida, introduzir as respetivas credenciais da conta profissional ou escolar na aplicação.


[!INCLUDE[AAD-enrollment](../includes/win10-automatic-enrollment-aad.md)]

## <a name="company-portal-app-enrollment"></a>Inscrição de aplicações no Portal da Empresa
Pode permitir que os utilizadores instalem e inscrevam os respetivos dispositivos ao utilizar a aplicação Portal da Empresa do Intune. Se criar registos de recursos CNAME DNS, os utilizadores ligam e inscrevem-se no Intune sem que seja necessário introduzir um nome de servidor.

1.  **Configurar o Intune**<br>Se ainda não o fez, prepare a gestão de dispositivos móveis ao [definir a autoridade de gestão de dispositivos móveis (MDM)](prerequisites-for-enrollment.md#set-mobile-device-management-authority) como **Microsoft Intune** e ao configurar a MDM.

2.  **Criar CNAMEs** (opcional)<br>Crie registos de recursos DNS **CNAME** para o domínio da sua empresa. Por exemplo, se o site da sua empresa for contoso.com, deverá criar um CNAME no DNS para redirecionar EnterpriseEnrollment.contoso.com para enterpriseenrollment-s.manage.microsoft.com.

    Apesar de a criação de entradas DNS CNAME ser opcional, os registos CNAME facilitam a inscrição para os utilizadores. Se não for encontrado nenhum registo CNAME de inscrição, os utilizadores recebem um pedido para introduzir manualmente o nome do servidor MDM, https://manage.microsoft.com. 

    Se atualmente tiver um CNAME no DNS que redireciona EnterpriseEnrollment.contoso.com para manage.microsoft.com, sugerimos que o substitua por um CNAME no DNS que redirecione EnterpriseEnrollment.contoso.com para enterpriseenrollment-s.manage.microsoft.com. Esta alteração é recomendada, uma vez que o ponto final de manage.microsoft.com vai ser preterido para as inscrições numa versão futura.

    Se existir mais do que um domínio verificado, crie um registo CNAME para cada domínio. Os registos de recursos CNAME têm de conter as seguintes informações:

  |TIPO|Nome do anfitrião|Aponta para|TTL|
  |--------|-------------|-------------|-------|
  |CNAME|EnterpriseEnrollment.dominio_empresa.com|EnterpriseEnrollment-s.manage.microsoft.com |1 Hora|
  |CNAME|EnterpriseRegistration.dominio_empresa.com|EnterpriseRegistration.windows.net|1 Hora|

  `EnterpriseEnrollment-s.manage.microsoft.com` – suporta o redirecionamento para o serviço Intune com reconhecimento de domínio a partir do nome de domínio do e-mail

  `EnterpriseRegistration.windows.net` – suporta os dispositivos com Windows 8.1 e com Windows 10 Mobile que serão registados no Azure Active Directory com a respetiva conta escolar ou profissional

  Se a sua empresa utilizar vários domínios para as credenciais do utilizador, crie os registos CNAME para cada domínio.

  Por exemplo, se o Web site da sua empresa fosse contoso.com, criaria um CNAME em DNS que redirecionaria EnterpriseEnrollment.contoso.com para EnterpriseEnrollment-s.manage.microsoft.com. As alterações aos registos DNS podem demorar até 72 horas a serem propagadas. Não é possível verificar a alteração de DNS no Intune até o registo DNS ser propagado.

3.  **Verificar o CNAME**<br>Na [consola de administração do Intune](http://manage.microsoft.com), selecione **Admin** &gt; **Mobile Device Management** &gt; **Windows Phone**. Introduza o URL do domínio verificado do site da empresa na caixa **Especificar o nome de um domínio verificado** e, em seguida, selecione **Testar Deteção Automática**.

    ![Caixa de diálogo Configurar a gestão de dispositivos móveis do Windows](../media/windows-phone-enrollment.png)

4.  **Passos opcionais**<br>O passo **Adicionar as Chaves de Sideload** não é necessário para o Windows 10. O passo **Carregar o Certificado de Assinatura de Código** será preciso só se distribuir aplicações de linha de negócio (LOB) não disponíveis em dispositivos da Loja Windows.

5.  **Indique aos utilizadores como devem inscrever os respetivos dispositivos para poderem aceder aos recursos da empresa.**

    Para obter instruções de inscrição do utilizador final, veja [Inscrever o dispositivo Windows no Intune](../enduser/enroll-your-device-in-intune-windows.md). Também pode encaminhar os utilizadores para [O que pode o administrador de TI ver ao inscrever o dispositivo no Intune?](../enduser/what-can-your-it-administrator-see-when-you-enroll-your-device-in-intune-windows)

    Para obter informações sobre outras tarefas do utilizador final, veja estes artigos:
    - [O que dizer aos seus utilizadores finais sobre a utilização do Microsoft Intune](what-to-tell-your-end-users-about-using-microsoft-intune.md)
    - [Orientações para o utilizador final para dispositivos Windows](../enduser/using-your-windows-device-with-intune.md)

Não é necessário qualquer ação adicional, a não ser que pretenda implementar o Portal da Empresa nos dispositivos.  Os passos 2 e 3 na consola de administração podem ser ignorados em segurança.



<!--HONumber=Nov16_HO3-->


