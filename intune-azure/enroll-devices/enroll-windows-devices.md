---
title: Inscrever dispositivos Windows
titleSuffix: Intune Azure preview
description: "Pré-visualização do Azure no Intune: ative a gestão de dispositivos móveis (MDM) do Intune para dispositivos Windows."
keywords: 
author: nathbarn
manager: nathbarn
ms.date: 03/15/17
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f94dbc2e-a855-487e-af6e-8d08fabe6c3d
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: a95aca706a4996d40e268a80c7c334ebb9854df5
ms.openlocfilehash: 6cbaf8414452f11f0aa97616bbed2cf164b49ac0
ms.lasthandoff: 03/15/2017


---

# <a name="enroll-windows-devices"></a>Inscrever dispositivos Windows

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Utilize um dos seguintes métodos para configurar a inscrição para dispositivos Windows:

- [**Inscrição automática no Windows 10 e Windows 10 Mobile com o Azure Active Directory Premium**](#set-up-windows-10-and-windows-10-mobile-automatic-enrollment-with-azure-active-directory-premium)
 -  Este método é aplicável apenas para dispositivos com o Windows 10 e Windows 10 Mobile.
 -  Tem de ter o Azure Active Directory Premium para utilizar este método. Caso contrário, utilize o método de inscrição para Windows 8.1 e Windows Phone 8.1.
 -  Se optar por não ativar a inscrição automática, utilize o método de inscrição para Windows 8.1 e Windows Phone 8.1.

- [**Inscrição no Windows 8.1 e Windows Phone 8.1 através da configuração do CNAME**](#simplify-enrollment-by-configuring-cname)
 - Tem de utilizar este método para inscrever dispositivos Windows 8.1 e Windows Phone 8.1.
 - Também poderá utilizar este método se não tiver o Azure Active Directory (AD) Premium.


## <a name="prerequisites"></a>Pré-requisitos

Se alguns dos pré-requisitos seguintes ainda não estiverem na pré-visualização do Azure no Intune, terá de realizá-los na consola de administração clássica do Intune.

- [Configurar um nome de domínio personalizado](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-2)
- [Definir a autoridade de gestão de dispositivos móveis (MDM)](set-mdm-authority.md) como o **Microsoft Intune**
- [Configurar a aplicação Portal da Empresa](/intune-azure/manage-apps/company-portal-app.md)
- Atribuir licenças aos utilizadores

[!INCLUDE[AAD-enrollment](../includes/win10-automatic-enrollment-aad.md)]

## <a name="enable-windows-workplace-enrollment"></a>Ativar a inscrição na área de trabalho do Windows

Pode permitir que os utilizadores instalem e inscrevam os dispositivos sem a inscrição automática do Azure AD Premium. Se criar registos de recursos CNAME DNS, os utilizadores ligam e inscrevem-se no Intune sem que seja necessário introduzir um nome de servidor.

1. **Criar CNAMEs** (opcional)<br>
 Crie registos de recursos DNS **CNAME** para o domínio da sua empresa. Por exemplo, se o site da sua empresa for contoso.com, deverá criar um CNAME no DNS para redirecionar EnterpriseEnrollment.contoso.com para enterpriseenrollment-s.manage.microsoft.com.

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

2.  **Verificar o CNAME**<br>No portal do Azure, selecione **Mais Serviços** > **Monitorização + Gestão** > **Intune**. No painel Intune, escolha **Inscrever dispositivos** > **Inscrição do Windows**. Introduza o URL do domínio verificado do site da empresa na caixa **Especificar o nome de um domínio verificado** e, em seguida, selecione **Testar Deteção Automática**.

3.  **Indique aos utilizadores como devem inscrever os dispositivos e o que esperar quando estiverem a ser geridos.**

    Para obter instruções de inscrição do utilizador final, veja [Inscrever o seu dispositivo Windows no Intune](https://docs.microsoft.com/intune/enduser/enroll-your-device-in-intune-windows). Também pode encaminhar os utilizadores para [What can my IT admin see on my device (O que é que o meu administrador de TI pode ver no meu dispositivo)](https://docs.microsoft.com/intune/enduser/what-can-your-it-administrator-see-when-you-enroll-your-device-in-intune-windows).

    Para obter mais informações sobre as tarefas do utilizador final, consulte [Recursos sobre a experiência do utilizador final com o Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/what-to-tell-your-end-users-about-using-microsoft-intune).

Não é necessário qualquer ação adicional, a não ser que pretenda implementar o Portal da Empresa nos dispositivos.  Os passos 2 e 3 na consola de administração podem ser ignorados em segurança.

