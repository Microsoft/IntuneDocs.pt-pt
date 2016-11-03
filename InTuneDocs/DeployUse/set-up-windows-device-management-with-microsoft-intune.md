---
title: "Configurar a gestão de dispositivos Windows com o Microsoft Intune | Microsoft Intune"
description: "Ative a gestão de dispositivos móveis (MDM) para PCs Windows, incluindo dispositivos Windows 10, com o Microsoft Intune."
keywords: 
author: NathBarn
manager: angrobe
ms.date: 08/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9a18c0fe-9f03-4e84-a4d0-b63821bf5d25
ms.reviewer: damionw
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: c880bd9dfb998355a18e78af898a96d4cee393f7
ms.openlocfilehash: 149508942b89b15308591e17723884add3ac78ae


---

# Configurar a gestão de dispositivos Windows

Como administrador do Intune, pode ativar a inscrição e gestão de PCs Windows de duas formas:

- **[Inscrição automática com o Azure AD](#azure-active-directory-enrollment)** - os utilizadores do Windows 10 e Windows 10 Mobile inscrevem os dispositivos deles ao adicionarem uma conta profissional ou escolar ao dispositivo
- **[Inscrição no Portal da Empresa](#company-portal-app-enrollment)** - o Windows 8.1 e dispositivos posteriores são inscritos ao transferir e instalar a aplicação Portal da Empresa e, em seguida, introduzindo as respetivas credenciais da conta profissional ou escolar na aplicação.

[!INCLUDE[AAD-enrollment](../includes/win10-automatic-enrollment-aad.md)]

## Configurar a inscrição de aplicações no Portal da Empresa
Pode permitir que os utilizadores inscrevam os dispositivos deles através da instalação e inscrição dos dispositivos com a aplicação Portal da Empresa do Intune. A criação de um CNAME DNS ajuda os utilizadores a ligar e a inscrever-se no Intune sem que seja necessário introduzir um nome de servidor.

1. **Configurar o Intune**<br>
Se ainda não o fez, prepare a gestão de dispositivos móveis ao [definir a autoridade de gestão de dispositivos móveis](prerequisites-for-enrollment.md#set-mobile-device-management-authority) como **Microsoft Intune** e ao configurar a MDM.

2. **Criar CNAMEs** (opcional)<br>Crie registos de recursos DNS **CNAME** para o domínio da sua empresa, para simplificar a inscrição. Apesar de a criação de entradas DNS CNAME ser opcional, a criação de registos CNAME facilita a inscrição para os utilizadores. Se não for encontrado nenhum registo CNAME de inscrição, os utilizadores recebem um pedido para introduzir manualmente o nome do servidor MDM, `https://manage.microsoft.com`.  Os registos de recursos CNAME têm de conter as seguintes informações:

  |TIPO|Nome do anfitrião|Aponta para|TTL|
  |--------|-------------|-------------|-------|
  |CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com |1 Hora|
  |CNAME|EnterpriseRegistration.company_domain.com|EnterpriseRegistration.windows.net|1 Hora|

  `EnterpriseEnrollment-s.manage.microsoft.com` – Suporta o redirecionamento para o serviço Intune com reconhecimento de domínio a partir do nome de domínio do e-mail

  `EnterpriseRegistration.windows.net` – Suporta os dispositivos Windows 8.1 e Windows 10 Mobile que serão registados no Azure Active Directory utilizando a respetiva conta profissional ou escolar

  Se a sua empresa utilizar vários domínios para as credenciais do utilizador, crie os registos CNAME para cada domínio.

  Por exemplo, se o Web site da sua empresa fosse contoso.com, criaria um CNAME em DNS que redirecionaria EnterpriseEnrollment.contoso.com para EnterpriseEnrollment-s.manage.microsoft.com. As alterações ao registo DNS podem demorar até 72 horas a serem propagadas. Não é possível verificar a alteração de DNS no Intune até o registo DNS ser propagado.

3.  **Verificar o CNAME**<br>Na [consola de administração do Intune](http://manage.microsoft.com), clique em **Administração** &gt; **Gestão de Dispositivos Móveis** &gt; **Windows**. Introduza o URL do domínio verificado do site da empresa na caixa **Especificar o nome de um domínio verificado** e, em seguida, clique em **Testar Deteção Automática**.

  ![Caixa de diálogo da gestão de dispositivos Windows](../media/enroll-intune-winenr.png)

4.  **Passos opcionais**<br>O passo **Adicionar as Chaves de Sideload** não é necessário para o Windows 10. O passo **Carregar o Certificado de Assinatura de Código** só é necessário se distribuir aplicações de linha de negócio (LOB) para dispositivos que não estão disponíveis na Loja Windows. [Saiba mais](set-up-windows-phone-8.0-management-with-microsoft-intune.md)

6.  **Informar os utilizadores**<br>Terá de dizer aos utilizadores com devem inscrever os dispositivos e o que esperar quando passarem a ser geridos:
      - [O que dizer aos utilizadores finais sobre a utilização do Microsoft Intune](what-to-tell-your-end-users-about-using-microsoft-intune.md)
      - [Orientações para o utilizador final para dispositivos Windows](../enduser/using-your-windows-device-with-intune.md)

### Consulte também
[Pré-requisitos para a inscrição de dispositivos no Microsoft Intune](prerequisites-for-enrollment.md)



<!--HONumber=Sep16_HO4-->


