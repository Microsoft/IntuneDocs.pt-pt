---
title: "Configurar a gestão de dispositivos Windows com o Microsoft Intune | Documentos da Microsoft"
description: "Ative a gestão de dispositivos móveis (MDM) para dispositivos Windows com o Microsoft Intune."
keywords: 
author: staciebarker
manager: stabar
ms.date: 02/09/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9a18c0fe-9f03-4e84-a4d0-b63821bf5d25
ms.reviewer: damionw
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 45c32cf08e4d6fd570af287ed64411edc9d9b394
ms.openlocfilehash: e020ac2a4f600a94e7409e04c4c48f0c405c56cf


---

# <a name="set-up-windows-device-management"></a>Configurar a gestão de dispositivos Windows

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Utilize um dos seguintes métodos para configurar a inscrição para dispositivos Windows:

- **[Inscrição automática no Windows 10 e Windows 10 Mobile com o Azure Active Directory Premium](#set-up-windows-10-and-windows-10-mobile-automatic-enrollment-with-azure-active-directory-premium)** 
 -  Este método é aplicável apenas para dispositivos Windows 10 e Windows 10 Mobile.
 -  Tem de ter o Azure Active Directory Premium para utilizar este método. Caso contrário, utilize o método de inscrição para Windows 8.1 e Windows Phone 8.1.
 -  Se optar por não ativar a inscrição automática, utilize o método de inscrição para Windows 8.1 e Windows Phone 8.1.


- **[Inscrição no Windows 8.1 e Windows Phone 8.1 através da configuração do CNAME](#set-up-windows-8--1-and-windows-phone-8--1-enrollment-by-configuring-cname)** 
 - Tem de utilizar este método para inscrever dispositivos Windows 8.1 e Windows Phone 8.1.

[!INCLUDE[AAD-enrollment](../includes/win10-automatic-enrollment-aad.md)]

## <a name="set-up-windows-81-and-windows-phone-81-enrollment-by-configuring-cname"></a>Configurar a inscrição no Windows 8.1 e Windows Phone 8.1 através da configuração do CNAME
Pode permitir que os utilizadores instalem e inscrevam os dispositivos deles com o Portal da Empresa do Intune. Se criar registos de recursos CNAME DNS, os utilizadores ligam e inscrevem-se no Intune sem que seja necessário introduzir um nome de servidor.

1. **Configurar o Intune**<br>
Se ainda não o fez, prepare a gestão de dispositivos móveis ao [definir a autoridade de gestão de dispositivos móveis (MDM)](prerequisites-for-enrollment.md#step-2-set-mdm-authority) como **Microsoft Intune** e ao configurar a MDM.

2. **Criar CNAMEs** (opcional)<br>
Crie registos de recursos DNS **CNAME** para o domínio da sua empresa. Por exemplo, se o site da sua empresa for contoso.com, deverá criar um CNAME no DNS para redirecionar EnterpriseEnrollment.contoso.com para enterpriseenrollment-s.manage.microsoft.com.

    Apesar de a criação de entradas DNS CNAME ser opcional, os registos CNAME facilitam a inscrição para os utilizadores. Se não for encontrado nenhum registo CNAME de inscrição, os utilizadores receberão um pedido para introduzir manualmente o nome do servidor MDM, enrollment.manage.microsoft.com.    

    Se atualmente tiver um CNAME no DNS que redireciona EnterpriseEnrollment.contoso.com para manage.microsoft.com, sugerimos que o substitua por um CNAME no DNS que redirecione EnterpriseEnrollment.contoso.com para enterpriseenrollment-s.manage.microsoft.com. Esta alteração é recomendada, uma vez que o ponto final de manage.microsoft.com vai ser preterido para as inscrições numa versão futura.

    Os registos de recursos CNAME têm de ter as seguintes informações:

  |TIPO|Nome do anfitrião|Aponta para|TTL|
  |--------|-------------|-------------|-------|
  |CNAME|EnterpriseEnrollment.dominio_empresa.com|EnterpriseEnrollment-s.manage.microsoft.com |1 Hora|
  |CNAME|EnterpriseRegistration.dominio_empresa.com|EnterpriseRegistration.windows.net|1 Hora|

  `EnterpriseEnrollment-s.manage.microsoft.com` – suporta o redirecionamento para o serviço Intune com reconhecimento de domínio a partir do nome de domínio do e-mail

  `EnterpriseRegistration.windows.net` – suporta os dispositivos com Windows 8.1 e com Windows 10 Mobile que serão registados no Azure Active Directory com a respetiva conta escolar ou profissional

  Se a sua empresa utilizar vários domínios para as credenciais do utilizador, crie os registos CNAME para cada domínio.

  Por exemplo, se o site da sua empresa for contoso.com, deverá criar um CNAME no DNS para redirecionar EnterpriseEnrollment.contoso.com para enterpriseenrollment-s.manage.microsoft.com. As alterações aos registos DNS podem demorar até 72 horas a serem propagadas. Não é possível verificar a alteração de DNS no Intune até o registo DNS ser propagado.

3.  **Verificar o CNAME**<br>Na [Consola de administração do Intune](http://manage.microsoft.com), selecione **Admin** &gt; **Mobile Device Management** &gt; **Windows**. Introduza o URL do domínio verificado do site da empresa na caixa **Especificar o nome de um domínio verificado** e, em seguida, selecione **Testar Deteção Automática**.

4.  **Indique aos utilizadores como devem inscrever os dispositivos e o que esperar quando passarem a ser geridos.**

    Para obter instruções de inscrição do utilizador final, veja [Inscrever o seu dispositivo Windows no Intune](https://docs.microsoft.com/intune/enduser/enroll-your-device-in-intune-windows).

    Para obter mais informações sobre as tarefas do utilizador final, consulte [Recursos sobre a experiência do utilizador final com o Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/what-to-tell-your-end-users-about-using-microsoft-intune).


### <a name="see-also"></a>Consulte também
[Pré-requisitos para a inscrição de dispositivos no Microsoft Intune](prerequisites-for-enrollment.md)



<!--HONumber=Feb17_HO2-->


