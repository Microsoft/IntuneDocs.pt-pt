---
title: "Configurar a gestão de dispositivos Windows com o Microsoft Intune | Documentos da Microsoft"
description: "Ative a gestão de dispositivos móveis (MDM) para dispositivos Windows com o Microsoft Intune."
keywords: 
author: NathBarn
manager: angrobe
ms.date: 03/20/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9a18c0fe-9f03-4e84-a4d0-b63821bf5d25
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 771aed4e1c57171183b9a9ea7d9e0f702dc1859c
ms.openlocfilehash: f6014c5500b05762d123b2285ef859d67382e402
ms.lasthandoff: 04/06/2017


---

# <a name="set-up-windows-device-management"></a>Configurar a gestão de dispositivos Windows

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Utilize um dos seguintes métodos para configurar a inscrição para dispositivos Windows:

- [**Inscrição automática de dispositivos Windows 10 com o Azure Active Directory Premium**](#set-up-windows-10-and-windows-10-mobile-automatic-enrollment-with-azure-active-directory-premium)
 -  Este método só está disponível para dispositivos Windows 10.
 -  Tem de ter o Azure Active Directory Premium para utilizar este método.
 -  Se optar por não ativar a inscrição automática, utilize o método de inscrição para Windows 8.1 e Windows Phone 8.1.

- [**Inscrição sem a inscrição automática do Azure AD Premium**](#enable-windows-enrollment-without-azure-ad-premium)
 - Tem de utilizar este método para inscrever dispositivos Windows 8.1 e Windows Phone 8.1.
 - Poderá utilizar este método para os dispositivos Windows 8.1 e posterior se não pretender utilizar o Azure Active Directory (AD) Premium.

[!INCLUDE[AAD-enrollment](../includes/win10-automatic-enrollment-aad.md)]

## <a name="enable-windows-enrollment-without-automatic-enrollment"></a>Permitir a inscrição de dispositivos Windows sem a inscrição automática
Pode permitir que os utilizadores instalem e inscrevam os dispositivos sem a inscrição automática do Azure AD Premium. Após atribuir uma licença à conta dos utilizadores, os mesmos poderão adicionar a conta a um dispositivo Windows e concordar em inscrevê-lo para ser gerido. Se criar registos de recursos DNS CNAME, os utilizadores ligam e inscrevem-se no Intune sem que seja necessário introduzir um nome de servidor.

**Passo 1: criar CNAMEs** (opcional)<br>
Crie registos de recursos DNS CNAME para o domínio da sua empresa. Por exemplo, se o site da sua empresa for contoso.com, deverá criar um CNAME no DNS para redirecionar EnterpriseEnrollment.contoso.com para enterpriseenrollment-s.manage.microsoft.com.

Apesar de a criação de entradas DNS CNAME ser opcional, os registos CNAME facilitam a inscrição para os utilizadores. Se não for encontrado nenhum registo CNAME de inscrição, os utilizadores receberão um pedido para introduzir manualmente o nome do servidor MDM, enrollment.manage.microsoft.com.

Se existir mais do que um domínio verificado, crie um registo CNAME para cada domínio. Os registos de recursos CNAME têm de conter as seguintes informações:

Os registos de recursos CNAME têm de ter as seguintes informações:

|TIPO|Nome do anfitrião|Aponta para|TTL|
|--------|-------------|-------------|-------|
|CNAME|EnterpriseEnrollment.dominio_empresa.com|EnterpriseEnrollment-s.manage.microsoft.com |1 Hora|
|CNAME|EnterpriseRegistration.dominio_empresa.com|EnterpriseRegistration.windows.net|1 Hora|

`EnterpriseEnrollment-s.manage.microsoft.com` – suporta o redirecionamento para o serviço Intune com reconhecimento de domínio a partir do nome de domínio do e-mail

Se a sua empresa utilizar vários domínios para as credenciais do utilizador, crie os registos CNAME para cada domínio.

Por exemplo, se o site da sua empresa for contoso.com, deverá criar um CNAME no DNS para redirecionar EnterpriseEnrollment.contoso.com para enterpriseenrollment-s.manage.microsoft.com. As alterações aos registos DNS podem demorar até 72 horas a serem propagadas. Não é possível verificar a alteração de DNS no Intune até o registo DNS ser propagado.

**Passo 2: verificar o CNAME** (opcional)<br>
Na [Consola de administração do Intune](http://manage.microsoft.com), selecione **Administração** &gt; **Gestão de Dispositivos Móveis** &gt; **Windows**. Introduza o URL do domínio verificado do site da empresa na caixa **Especificar o nome de um domínio verificado** e, em seguida, selecione **Testar Deteção Automática**.

## <a name="tell-users-how-to-enroll-windows-devices"></a>Informar os utilizadores sobre como inscrever dispositivos Windows
Informe os seus utilizadores sobre como inscrever os dispositivos Windows e o que esperar após começarem a ser geridos.
Para obter instruções de inscrição do utilizador final, veja [Inscrever o seu dispositivo Windows no Intune](https://docs.microsoft.com/intune/enduser/enroll-your-device-in-intune-windows). Também pode encaminhar os utilizadores para [Que informações pode o administrador de TI ver no dispositivo](https://docs.microsoft.com/intune/enduser/what-can-your-it-administrator-see-when-you-enroll-your-device-in-intune-windows).

Para obter mais informações sobre as tarefas do utilizador final, consulte [Recursos sobre a experiência do utilizador final com o Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/how-to-educate-your-end-users-about-microsoft-intune).

### <a name="see-also"></a>Consulte também
[Pré-requisitos para a inscrição de dispositivos no Microsoft Intune](prerequisites-for-enrollment.md)

