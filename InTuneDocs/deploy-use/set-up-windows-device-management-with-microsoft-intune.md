---
title: "Configurar a gestão de dispositivos Windows com o Microsoft Intune | Documentos da Microsoft"
description: "Ative a gestão de dispositivos móveis (MDM) para dispositivos Windows com o Microsoft Intune."
keywords: 
author: NathBarn
manager: angrobe
ms.date: 02/26/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9a18c0fe-9f03-4e84-a4d0-b63821bf5d25
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 255c3e47464ac7670a971881cf399e8e2bb17044
ms.openlocfilehash: 4acbae2aba4cff21286d45cb7cb1691864c281dc
ms.lasthandoff: 02/28/2017


---

# <a name="set-up-windows-device-management"></a>Configurar a gestão de dispositivos Windows

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Utilize um dos seguintes métodos para configurar a inscrição para dispositivos Windows:

- [**Inscrição automática no Windows 10 e Windows 10 Mobile com o Azure Active Directory Premium**](#set-up-windows-10-and-windows-10-mobile-automatic-enrollment-with-azure-active-directory-premium)
 -  Este método é aplicável apenas para dispositivos com o Windows 10 e Windows 10 Mobile.
 -  Tem de ter o Azure Active Directory Premium para utilizar este método. Caso contrário, utilize o método de inscrição para Windows 8.1 e Windows Phone 8.1.
 -  Se optar por não ativar a inscrição automática, utilize o método de inscrição para Windows 8.1 e Windows Phone 8.1.


- [**Inscrição no Windows 8.1 e Windows Phone 8.1 através da configuração do CNAME**](#set-up-windows-81-and-windows-phone-81-enrollment-by-configuring-cname)
 - Tem de utilizar este método para inscrever dispositivos Windows 8.1 e Windows Phone 8.1.

[!INCLUDE[AAD-enrollment](../includes/win10-automatic-enrollment-aad.md)]

## <a name="set-up-windows-81-and-windows-phone-81-enrollment-by-configuring-cname"></a>Configurar a inscrição no Windows 8.1 e Windows Phone 8.1 através da configuração do CNAME
Pode permitir que os utilizadores instalem e inscrevam os dispositivos deles com o Portal da Empresa do Intune. Se criar registos de recursos CNAME DNS, os utilizadores ligam e inscrevem-se no Intune sem que seja necessário introduzir um nome de servidor.

### <a name="step-1-set-up-intune"></a>Passo 1: configurar o Intune

Se ainda não o fez, prepare a gestão de dispositivos móveis ao [definir a autoridade de gestão de dispositivos móveis (MDM)](prerequisites-for-enrollment.md#step-2-set-mdm-authority) como **Microsoft Intune** e ao configurar a MDM.

### <a name="step-2-create-cnames-optional"></a>Passo 2: criar CNAMEs (opcional)

Crie registos de recursos DNS **CNAME** para o domínio da sua empresa. Por exemplo, se o site da sua empresa for contoso.com, deverá criar um CNAME no DNS para redirecionar EnterpriseEnrollment.contoso.com para enterpriseenrollment-s.manage.microsoft.com.


   Apesar de a criação de entradas DNS CNAME ser opcional, os registos CNAME facilitam a inscrição para os utilizadores. Se não for encontrado nenhum registo CNAME de inscrição, os utilizadores receberão um pedido para introduzir manualmente o nome do servidor MDM, enrollment.manage.microsoft.com.

   Os registos de recursos CNAME têm de ter as seguintes informações:

  |TIPO|Nome do anfitrião|Aponta para|TTL|
  |--------|-------------|-------------|-------|
  |CNAME|EnterpriseEnrollment.dominio_empresa.com|EnterpriseEnrollment-s.manage.microsoft.com |1 Hora|
  |CNAME|EnterpriseRegistration.dominio_empresa.com|EnterpriseRegistration.windows.net|1 Hora|

  `EnterpriseEnrollment-s.manage.microsoft.com` – suporta o redirecionamento para o serviço Intune com reconhecimento de domínio a partir do nome de domínio do e-mail

  `EnterpriseRegistration.windows.net` – suporta os dispositivos com Windows 8.1 e com Windows 10 Mobile que serão registados no Azure Active Directory com a respetiva conta escolar ou profissional

  Se a sua empresa utilizar vários domínios para as credenciais do utilizador, crie os registos CNAME para cada domínio.

  Por exemplo, se o site da sua empresa for contoso.com, deverá criar um CNAME no DNS para redirecionar EnterpriseEnrollment.contoso.com para enterpriseenrollment-s.manage.microsoft.com. As alterações aos registos DNS podem demorar até 72 horas a serem propagadas. Não é possível verificar a alteração de DNS no Intune até o registo DNS ser propagado.

### <a name="step-3-verify-cname"></a>Passo 3: Verificar o CNAME

Na [Consola de administração do Intune](http://manage.microsoft.com), selecione **Administração** &gt; **Gestão de Dispositivos Móveis** &gt; **Windows**. Introduza o URL do domínio verificado do site da empresa na caixa **Especificar o nome de um domínio verificado** e, em seguida, selecione **Testar Deteção Automática**.

### <a name="step-4-tell-your-users-how-to-enroll-their-devices-and-what-to-expect-after-theyre-brought-into-management"></a>Passo 4: indique aos utilizadores como devem inscrever os dispositivos e o que esperar quando passarem a ser geridos.

   Para obter instruções de inscrição do utilizador final, veja [Inscrever o seu dispositivo Windows no Intune](https://docs.microsoft.com/intune/enduser/enroll-your-device-in-intune-windows).

   Para obter mais informações sobre as tarefas dos utilizadores finais, veja [Como dar formação aos seus utilizadores finais sobre o Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/what-to-tell-your-end-users-about-using-microsoft-intune) e [Orientações para o utilizador final para dispositivos Windows](../enduser/using-your-windows-device-with-intune.md).

### <a name="see-also"></a>Veja também
[Pré-requisitos para a inscrição de dispositivos no Microsoft Intune](prerequisites-for-enrollment.md)

