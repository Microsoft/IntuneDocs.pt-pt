---
title: "Configurar a gestão de dispositivos Windows com o Microsoft Intune"
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
ms.openlocfilehash: 9066414bcef1ba312db64aef077db8f8bfbbdb44
ms.sourcegitcommit: 79116d4c7f11bafc7c444fc9f5af80fa0b21224e
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/03/2017
---
# <a name="set-up-windows-device-management"></a>Configurar a gestão de dispositivos Windows

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Este tópico ajuda os administradores de TI a simplificar a inscrição de dispositivos Windows para os seus utilizadores.  Os dispositivos Windows podem ser inscritos sem passos adicionais, mas pode tornar a inscrição mais fácil para os utilizadores.

Dois fatores determinam como pode simplificar a inscrição de dispositivos do Windows:
- **Utiliza o Azure Active Directory Premium?** <br>O [Azure AD Premium](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) está incluído com o Enterprise Mobility + Security e outros planos de licenciamento.
- **Que versões de clientes do Windows serão inscritas?** <br>Os dispositivos Windows 10 podem ser inscritos automaticamente ao adicionar uma conta escolar ou profissional. As versões anteriores têm de ser inscritas através da aplicação Portal da Empresa.

||**Azure AD Premium**|**Outros AD**|
|----------|---------------|---------------|  
|**Windows 10**|[Inscrição automática](#enable-windows-10-automatic-enrollment) |[Inscrição de utilizadores](#enable-windows-enrollment-without-automatic-enrollment)|
|**Versões do Windows anteriores**|[Inscrição de utilizadores](#enable-windows-enrollment-without-automatic-enrollment)|[Inscrição de utilizadores](#enable-windows-enrollment-without-automatic-enrollment)|

[!INCLUDE[AAD-enrollment](../includes/win10-automatic-enrollment-aad.md)]

## <a name="enable-windows-enrollment-without-automatic-enrollment"></a>Permitir a inscrição de dispositivos Windows sem a inscrição automática
Pode permitir que os utilizadores inscrevam os dispositivos com a inscrição automática do Azure AD Premium. Após atribuir licenças, os utilizadores podem inscrever-se depois de adicionarem a conta profissional aos dispositivos pessoais ou de associarem os dispositivos pertencentes à empresa ao Azure AD. Criar um alias de DNS (tipo de registo CNAME) torna mais fácil para os utilizadores inscreverem os respetivos dispositivos. Se criar registos de recursos DNS CNAME, os utilizadores ligam-se e inscrevem-se no Intune sem ter de introduzir o nome do servidor do Intune.

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
Na [Consola de administração do Intune](https://manage.microsoft.com), selecione **Administração** &gt; **Gestão de Dispositivos Móveis** &gt; **Windows**. Introduza o URL do domínio verificado do site da empresa na caixa **Especificar o nome de um domínio verificado** e, em seguida, selecione **Testar Deteção Automática**.

## <a name="tell-users-how-to-enroll-windows-devices"></a>Informar os utilizadores sobre como inscrever dispositivos Windows
Informe os seus utilizadores sobre como inscrever os dispositivos Windows e o que esperar após começarem a ser geridos.
Para obter instruções de inscrição do utilizador final, veja [Inscrever o seu dispositivo Windows no Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-windows). Também pode encaminhar os utilizadores para [Que informações pode o administrador de TI ver no dispositivo](https://docs.microsoft.com/intune-user-help/what-can-your-it-administrator-see-when-you-enroll-your-device-in-intune-windows).

Para obter mais informações sobre as tarefas do utilizador final, consulte [Recursos sobre a experiência do utilizador final com o Microsoft Intune](/intune/end-user-educate).

### <a name="see-also"></a>Consulte também
[Pré-requisitos para a inscrição de dispositivos no Microsoft Intune](prerequisites-for-enrollment.md)
