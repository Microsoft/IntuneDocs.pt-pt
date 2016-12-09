---
title: "Configurar a gestão de dispositivos Windows com o Microsoft Intune | Microsoft Intune"
description: "Ative a gestão de dispositivos móveis (MDM) para PCs Windows, incluindo dispositivos Windows 10, com o Microsoft Intune."
keywords: 
author: staciebarker
manager: stabar
ms.date: 11/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9a18c0fe-9f03-4e84-a4d0-b63821bf5d25
ms.reviewer: damionw
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: eeb85a28ea6f99a0123ec5df3b0d476a678b85cb
ms.openlocfilehash: 13959c1456a0b160ce1fdcb76888d67cd13a5991


---

# <a name="set-up-windows-device-management"></a>Configurar a gestão de dispositivos Windows

Como administrador do Intune, pode ativar a inscrição e gestão de PCs Windows de duas formas:

- **[Inscrição automática com o Azure Active Directory](#azure-active-directory-enrollment)** – os utilizadores do Windows 10 e Windows 10 Mobile inscrevem os respetivos dispositivos ao adicionarem uma conta escolar ou profissional ao dispositivo
- **[Inscrição no Portal da Empresa](#company-portal-app-enrollment)** – os utilizadores do Windows 8.1 e posterior inscrevem os respetivos dispositivos ao transferir e instalar a aplicação Portal da Empresa e, em seguida, ao introduzir as respetivas credenciais da conta escolar ou profissional na aplicação.

[!INCLUDE[AAD-enrollment](../includes/win10-automatic-enrollment-aad.md)]

## <a name="set-up-company-portal-app-enrollment"></a>Configurar a inscrição na aplicação Portal da Empresa
Pode permitir que os utilizadores instalem e inscrevam os respetivos dispositivos ao utilizar a aplicação Portal da Empresa do Intune. Se criar registos de recursos CNAME DNS, os utilizadores ligam e inscrevem-se no Intune sem que seja necessário introduzir um nome de servidor.

1. **Configurar o Intune**<br>
Se ainda não o fez, prepare a gestão de dispositivos móveis ao [definir a autoridade de gestão de dispositivos móveis (MDM)](prerequisites-for-enrollment.md#set-mobile-device-management-authority) como **Microsoft Intune** e ao configurar a MDM.

2. **Criar CNAMEs** (opcional)<br>Crie registos de recursos DNS **CNAME** para o domínio da sua empresa. Por exemplo, se o site da empresa for contoso.com, criará um CNAME no DNS que redirecionará EnterpriseEnrollment.contoso.com para enterpriseenrollment.manage.microsoft.com.

    Se atualmente tiver um CNAME no DNS que redireciona EnterpriseEnrollment.contoso.com para manage.microsoft.com, sugerimos que o substitua por um CNAME no DNS que redirecione EnterpriseEnrollment.contoso.com para enterpriseenrollment-s.manage.microsoft.com. Esta alteração é recomendada, uma vez que o ponto final de manage.microsoft.com vai ser preterido para as inscrições numa versão futura.

    Os registos de recursos CNAME têm de ter as seguintes informações:

  |TIPO|Nome do anfitrião|Aponta para|TTL|
  |--------|-------------|-------------|-------|
  |CNAME|EnterpriseEnrollment.dominio_empresa.com|EnterpriseEnrollment-s.manage.microsoft.com |1 Hora|
  |CNAME|EnterpriseRegistration.dominio_empresa.com|EnterpriseRegistration.windows.net|1 Hora|

  `EnterpriseEnrollment-s.manage.microsoft.com` – suporta o redirecionamento para o serviço Intune com reconhecimento de domínio a partir do nome de domínio do e-mail

  `EnterpriseRegistration.windows.net` – suporta os dispositivos com Windows 8.1 e com Windows 10 Mobile que serão registados no Azure Active Directory com a respetiva conta escolar ou profissional

  Se a sua empresa utilizar vários domínios para as credenciais do utilizador, crie os registos CNAME para cada domínio.

  Por exemplo, se o Web site da sua empresa fosse contoso.com, criaria um CNAME em DNS que redirecionaria EnterpriseEnrollment.contoso.com para EnterpriseEnrollment-s.manage.microsoft.com. As alterações aos registos DNS podem demorar até 72 horas a serem propagadas. Não é possível verificar a alteração de DNS no Intune até o registo DNS ser propagado.

3.  **Verificar o CNAME**<br>Na [Consola de administração do Intune](http://manage.microsoft.com), selecione **Admin** &gt; **Mobile Device Management** &gt; **Windows**. Introduza o URL do domínio verificado do site da empresa na caixa **Especificar o nome de um domínio verificado** e, em seguida, selecione **Testar Deteção Automática**.

  ![Caixa de diálogo da gestão de dispositivos Windows](../media/enroll-intune-winenr.png)

4.  **Passos opcionais**<br>O passo **Adicionar as Chaves de Sideload** não é necessário para o Windows 10. O passo **Carregar o Certificado de Assinatura de Código** só é necessário se distribuir aplicações de linha de negócio (LOB) não disponíveis em dispositivos da Loja Windows.

6.  **Indique aos utilizadores como devem inscrever os dispositivos e o que esperar quando passarem a ser geridos.**

    Para obter instruções de inscrição do utilizador final, veja [Inscrever o dispositivo Windows no Intune](../enduser/enroll-your-device-in-intune-windows.md).

    Para obter mais informações sobre as tarefas do utilizador final, veja estes artigos:
      - [Recursos sobre a experiência do utilizador final com o Microsoft Intune](what-to-tell-your-end-users-about-using-microsoft-intune.md)
      - [Orientações para o utilizador final para dispositivos Windows](../enduser/using-your-windows-device-with-intune.md)

### <a name="see-also"></a>Consulte também
[Pré-requisitos para a inscrição de dispositivos no Microsoft Intune](prerequisites-for-enrollment.md)



<!--HONumber=Nov16_HO5-->


